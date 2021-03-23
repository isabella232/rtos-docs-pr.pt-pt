---
title: Capítulo 3 - Visão geral funcional do GUIX
description: Este capítulo contém uma visão geral funcional do produto de interface de utilizador GUIX de alto desempenho.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2057b86e6f44912fe8ca349cdf0ad2cc10f5c4cd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827200"
---
# <a name="chapter-3---functional-overview-of-guix"></a>Capítulo 3 - Visão geral funcional do GUIX

Este capítulo contém uma visão geral funcional do produto de interface de utilizador GUIX de alto desempenho. 

## <a name="execution-overview"></a>Visão geral da execução

O GUIX implementa um modelo de programação orientado para eventos. Isto significa que o quadro GUIX é essencialmente impulsionado pela receção de eventos empurrados para a fila do evento GUIX. O processamento destes eventos ocorre no contexto da linha GUIX, que é um fio ThreadX criado durante a inicialização do sistema GUIX.

As aplicações GUIX definem a interface do utilizador chamando as funções de API GUIX para criar janelas e widgets infantis, e personalizam a aparência destes widgets, chamando funções API adicionais usadas para definir cores, estilos, tipos de letra e vários outros atributos de cada tipo de janela ou widget. Se estiver a utilizar o GUIX Studio para criar a aparência dos ecrãs de interface de utilizador, grande parte deste trabalho de chamar funções de API GUIX para criar o seu ecrã é feito por si pela aplicação GUIX Studio.

As aplicações GUIX interagem com o utilizador do sistema e com a lógica de negócio externa, manuseando eventos recuperados da fila de eventos GUIX.
Estes eventos são geralmente produzidos por widgets GUIX, mas também podem ser criados por fios externos. Quando um botão GUIX típico é premido, este botão envia um evento para a janela dos pais do botão. O seu programa de aplicação atuará nesse botão, fornecendo um manipulador para o evento de pressão do botão.

Fios GUIX adicionais são muitas vezes criados para coisas como controladores de entrada. Um controlador de entrada de ecrã tátil típico é executado como um fio autónomo externo ao fio GUIX principal. O controlador de entrada de toque envia informações de toque para a linha GUIX enviando eventos para a fila do evento GUIX.

Uma vez que muitas operações de interface de utilizador, como animações, requerem informações precisas sobre o tempo, o GUIX também implementa uma interface de temporizador simples e fácil de usar. Esta interface temporizador é construída sobre o serviço de temporizador ThreadX, e é configurada automaticamente no arranque do sistema.

A grande maioria do software GUIX é independente de quaisquer dependências de hardware. A estrutura requer controladores de entrada específicos de hardware e controladores gráficos específicos de hardware. Os detalhes de como estes controladores específicos de hardware são implementados são adiados para o capítulo 5.

## <a name="initialization"></a>Inicialização 

O ***serviço gx_system_initialize*** deve ser chamado antes de qualquer outro serviço GUIX ser chamado. A inicialização do sistema GUIX pode ser chamada a partir da rotina ***tx_application_define*** ThreadX (contexto de inicialização) ou a partir de fios de aplicação. A função ***gx_system_initialize*** cria a fila do evento GUIX, inicializa a instalação do temporizador GUIX, cria o fio principal do sistema GUIX e inicializa várias estruturas de dados mantidas pelo GUIX durante a execução da sua aplicação.

Após ***gx_system_initialize*** devoluções, a aplicação está pronta para criar ecrãs, telas, janelas, widgets e personalizar as propriedades de todos os objetos GUIX. Grande parte da criação de objetos GUIX API pode ser chamada a partir de ***tx_application_define*** ou de fios de aplicação.

## <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação 

As chamadas da aplicação são feitas em grande parte a partir de ***tx_application_define*** (contexto de inicialização) ou de threads de aplicação. Consulte a secção "Allowed From" de cada API GUIX descrita no Capítulo 4 para determinar de que contexto pode ser chamado.

Na maior parte das vezes, o processamento de atividades intensivas é adiado para o fio GUIX interno, incluindo todo o processamento de eventos e o desenho widget/janela.

As funções de API GUIX podem ser chamadas a partir de qualquer fio a qualquer momento.
No entanto, é geralmente considerado como melhor arquitetura para separar a sua lógica de negócio crítica do tempo da sua lógica de interface de utilizador. Uma vez que as operações de desenho da interface do utilizador podem, por vezes, demorar muito tempo, dependendo do tamanho do ecrã e do desempenho do CPU, normalmente não gostaria de ter fios críticos de tempo atrasados à espera que uma operação de desenho fosse concluída.

## <a name="internal-guix-thread"></a>Fio GUIX Interno 

Como mencionado, o GUIX tem um fio interno que executa a maior parte do processamento do GUI. Este fio é criado pelo software de aplicação chamando ***gx_system_initialize** _ seguido por _*_gx_system_start_**.

A prioridade da linha GUIX interna é determinada pelo `#define GX_SYSTEM_THREAD_PRIORITY` . Este valor desrescume a 16 (prioridade média), mas pode ser modificado especificando este valor no ficheiro de cabeçalho gx_port.h ou gx_user.h, sobreprimindo o valor predefinido.

A fatia de tempo do fio GUIX é igualmente definida pelo `#define GX_SYSTEM_THREAD_TIMESLICE` , que predefini ao valor 10 ms.

A pilha sie do fio do sistema é determinada pelo `#define GX_THREAD_STACK_SIZE` , que é encontrado no ficheiro cabeçalho ***gx_port.h,*** mas também pode ser ultrapassado especificando este valor no seu ficheiro de cabeçalho gx_user.h.

O laço interno de execução do fio GUIX é composto por três ações.
Em primeiro lugar, o GUIX recupera eventos da fila do evento GUIX e despacha esses eventos para processamento pelas janelas e widgets GUIX. Os eventos são normalmente empurrados para a fila do evento GUIX por temporizadores periódicos, dispositivos de entrada como um ecrã táctil ou teclado, e por widgets GUIX si mesmos à medida que processam a entrada do utilizador. Em seguida, depois de todos os eventos terem sido processados, o GUIX determina se é necessária uma atualização de ecrã e, se assim for, executa o processamento necessário para atualizar os dados gráficos do ecrã, principalmente chamando as funções de desenho dessas janelas e widgets que foram marcados como sujos. Finalmente, o GUIX suspende o fio GUIX até chegar um novo evento de entrada ou eventos.

## <a name="event-processing"></a>Processamento de eventos 

Os eventos de entrada de toque ou caneta são processados determinando a janela ou widget mais topo de gama sob a posição de pixel de entrada de toque ou caneta e chamando a função de processamento de eventos da janela/widget. Se o widget entender os eventos de entrada de canetas, irá processar o evento conforme apropriado para esse tipo de widget. Caso contrário, o widget mais topo de gama passará o evento de entrada de toque ou caneta para o progenitor do widget para processamento. Esta passagem do evento pela cadeia continua até que o evento seja tratado ou o evento chegue à janela raiz, caso em que o evento é descartado.

Os eventos do teclado são enviados para a janela/widget que tem foco de entrada. O estado de focagem de entrada é mantido pelo componente GUIX gx_system.

Os eventos temporizadores são sempre despachados para a janela ou widget que possui o temporizador para processamento.

Eventos gerados internamente, tais como eventos de clique de botão ou eventos de mudança de valor de slider, são sempre enviados para o progenitor do widget que gera o evento. Se o progenitor não processar o evento, é passado para cima da corrente semelhante a eventos de entrada de toque ou caneta.

## <a name="drawing"></a>Desenhar 

Uma vez concluído todo o processamento do evento, o fio interno GUIX determina se é necessária qualquer atualização do visor e, em caso afirmativo, são chamadas as funções de desenho de janela/widget apropriadas. Quando o desenho estiver completo, o fio interno GUIX simplesmente aguarda na sua fila de eventos para o próximo evento GUIX processar.

O GUIX implementa o conceito de *áreas sujas,* que são áreas que precisam de ser reenhagens, para cada widget e tela. Um widget só pode atrair para áreas que foram previamente marcadas como sujas. Quando uma função de desenho widget é chamada, todas as operações de desenho são internamente cortadas ao retângulo sujo previamente definido.
As tentativas de desenhar fora desta área são ignoradas.

Widgets e janelas marcam-se como sujos, chamando a função API ***gx_system_dirty_mark***. Esta função marca todo o widget ou janela como sendo necessário para ser redesenhado. Uma segunda função, ***gx_system_dirty_partial_add***, pode ser invocada como uma alternativa para marcar apenas uma parte de uma janela ou widget como sujo.

Este modelo de marcação widgets como sujo e, em seguida, redesenhar esses widgets apenas quando todos os eventos de entrada foram processados é referido como *desenho diferido*. O algoritmo de desenho diferido GUIX e a manutenção da lista suja são projetados para melhorar a eficiência do desenho. Uma vez que as operações de desenho são tipicamente caras, o GUIX trabalha arduamente para evitar o desenho desnecessário.

O desenho é feito para uma *tela* GUIX. Uma tela é uma área de memória reservada para conter dados gráficos. Uma tela pode ou não estar diretamente ligada ao tampão de moldura de hardware, dependendo da arquitetura do sistema e das restrições de memória. Antes de qualquer desenho, uma tela deve primeiro ser aberta para desenho, chamando a ***função API gx_canvas_drawing_initiate.*** Esta API prepara uma tela para o desenho e estabelece o contexto de *desenho* atual. Quando o GUIX executa uma atualização de tela de tela do sistema, a tela é aberta para desenho e o contexto de desenho estabelecido antes do desenho de nível widget APIs são invocados. Por isso, os widgets não precisam de iniciar o desenho de uma tela dentro da função de desenho widget.

No entanto, se uma aplicação pretender realizar o desenho imediato para uma tela, fora do fluxo do algoritmo de desenho diferido guix padrão, a aplicação deve invocar diretamente o ***gx_canvas_drawing_initiate*** antes de chamar quaisquer outras funções de API de desenho, e deve ***chamá gx_canvas_drawing_complete*** uma vez que o desenho imediato tenha sido concluído.

## <a name="user-input"></a>Entrada do utilizador 

O GUIX suporta dispositivos de ecrã tátil, rato e teclado com tipos de eventos predefinidos. Dispositivos de entrada adicionais podem ser utilizados definindo tipos de eventos personalizados, ou mapeando o dispositivo de entrada personalizado para os tipos de eventos predefinidos.

As ações associadas a estes dispositivos são traduzidas em eventos que são processados pela linha GUIX interna. O software de nível do condutor escrito para suportar um ecrã tátil deve preparar e enviar para os eventos de fila do evento GUIX para operações de pen-down, pen-up e pen-drag. Da mesma forma, um controlador de entrada de teclado deve gerar eventos para a entrada da tecla e da chave.

## <a name="modal-dialog-execution"></a>Execução do Diálogo Modal 

A execução do diálogo modal refere-se à apresentação de uma janela ao utilizador que deve ser fechada de alguma forma antes que quaisquer outras janelas guix ou widgets possam receber a entrada do utilizador. Os diálogos modais captam toda a entrada do utilizador enquanto a janela de diálogo é exibida, independentemente da posição x,y dos eventos de entrada de toque ou rato.

Os diálogos modais são desencadeados pelo software da aplicação, criando primeiro a janela da forma normal, chamando ***gx_window_create***, e depois chamando a função API guix ***gx_window_execute.***

Quando a função ***gx_window_execute*** é chamada, o GUIX entra num ciclo de processamento de eventos local. A função ***gx_window_execute*** não volta ao interlocutor até que a janela de diálogo esteja fechada, quer por entrada do utilizador, quer por chamada ***gx_window_close***. Por esta razão, é muito importante nunca chamar a ***função gx_window_execute*** de qualquer fio que não seja o fio interno GUIX.

## <a name="periodic-processing"></a>Processamento periódico 

Para fornecer efeitos de exibição, animação de sprite e suporte para pedidos periódicos de aplicação, o GUIX utiliza um temporizador ThreadX. Este temporizador único é utilizado para conduzir todas as necessidades relacionadas com o tempo DO GUIX. Por predefinição, a frequência do processamento do temporizador interno GUIX é definida em 20ms através do **GX_SYSTEM_TIMER_MS** constante , que é definido em **_gx_api.h_**, a menos que a constante seja previamente definida em gx_port.h ou gx_user.h cabeçalho. A frequência predefinida pode ser alterada pela aplicação através de uma opção de compilação ao construir a biblioteca GUIX ou redefinindo-a explicitamente em ***gx_user.h***.

> [!IMPORTANT]
> Note que a frequência do temporizador GUIX é expressa nos tiques do temporizador RTOS, e é definida pela **GX_SYSTEM_TIMER_TICKS** constante . O valor da **GX_SYSTEM_TIMER_TICKS** é calculado com **base GX_SYSTEM_TIMER_MS** e **TX_TIMER_TICKS_PER_SECOND**. O utilizador pode redefinir qualquer um destes valores no ***gx_port.h** _ ou _ *_gx_user.h_** para ajustar a frequência e resolução do temporizador GUIX.

## <a name="display-driver"></a>Controlador de exibição 

Os controladores de exibição são responsáveis por fornecer um conjunto de funções de desenho ao código GUIX central. A implementação de cada uma destas funções de desenho é determinada pelo controlador, e quando possível a implementação irá alavancar o suporte de aceleração do hardware. Em geral, a função de desenho funciona escrevendo dados de pixels para um tampão de memória, que pode ser o tampão de moldura física ou pode ser um tampão secundário dependendo da arquitetura do condutor. Muitos condutores implementam o tampão duplo usando dois tampão de armação, e estes tampão são alternados invocando a função de toggle buffer. O GUIX chama estas funções internamente nos momentos apropriados. Para sistemas constrangidos à memória, as funções de desenho só podem escrever para um único tampão de quadro de memória.

O GUIX fornece implementações de software predefinidos de cada função de desenho de baixo nível em todas as profundidades e formatos de cores de suporte. Estas funções são invocadas através de ponteiros de função mantidos dentro da estrutura **GX_DISPLAY.** Quando os controladores específicos do hardware são criados, normalmente substituem alguns destes ponteiros de função com funções específicas do hardware-alvo.

Um controlador típico de visualização de hardware é implementado primeiro criando o controlador de exibição GUIX padrão para a profundidade e formato de cor necessários.
Em seguida, o controlador de hardware substituirá as funções que precisam de ser otimizadas ou personalizadas para a implementação de hardware em particular.

Os formatos de cor de suporte GUIX variam entre o monocromático de 1-bpp e o formato 32-bpp a:r:g:b. O GUIX também suporta muitas variações dentro de cada categoria de profundidade de cores amplas, tais como r:g:b versus b:g:r byte order, pixel embalado versus formatos de pixel alinhados com palavras e canais alfa. Existem atualmente 25 formatos de cores distintos suportados, mas esta lista cresce à medida que os fornecedores de hardware oferecem novas variações.

## <a name="display-memory-architectures"></a>Exibir Arquiteturas de Memória

Vários alvos e ecrãs de hardware utilizam uma variedade de diferentes arquiteturas de memória de exibição, dependendo das restrições de memória do alvo e dos requisitos de funcionalidade da aplicação. Vamos delinear algumas das arquiteturas comuns da memória aqui com uma breve descrição de cada um.

Modelo 1) Sem tampão de quadro, dados gráficos mantidos em GRAM externos:

![Sem tampão de quadro, dados gráficos mantidos em GRAM externo](./media/guix/user-guide/no-frame-buffer.png)

No modelo acima, não existe memória para um tampão de moldura na memória local para o CPU. Todos os dados gráficos são armazenados num GRAM externo que é incorporado no próprio visor. A interface para o GRAM externo pode ser paralela ou em série. Este tipo de arquitetura é de custo muito baixo; no entanto, pode exibir um efeito de rasgo indesejado quando os dados gráficos são atualizados.

Modelo 2) Um tampão de moldura local:

![Um tampão de moldura local](./media/guix/user-guide/one-local-frame-buffer.png)

Neste modelo, a memória para os dados gráficos é atribuída a partir de uma memória de acesso aleatório que é diretamente acessível ao CPU. O hardware dedicado deve estar presente para transmitir repetidamente os dados gráficos (juntamente com os sinais de tempo) da memória local para o visor. Este modelo difere do modelo 1 na medida em que a memória gráfica é um bloco do SRAM local ou DRAM disponível para o CPU. Esta pode ser a mesma memória em que as variáveis de pilha e programa vivem.

Modelo 3) Tampão de moldura local + GRAM externo:

![Tampão de moldura local + GRAM externo](./media/guix/user-guide/local-frame-buffer-external-gram.png)

O Model 3 é uma combinação dos dois primeiros. Neste modelo, existe memória local suficiente para conter um tampão de moldura. Além disso, o dispositivo de exibição fornece um GRAM externo e refresca-se automaticamente utilizando os dados fornecidos no GRAM. Esta arquitetura beneficia de uma melhor eficiência de atualização porque podemos transferir a parte modificada do tampão de quadro local para o GRAM externo em uma transferência de bloco, muitas vezes utilizando canais DMA a bordo. Este modelo também elimina o rasgo e o cintilar que podem estar presentes em qualquer um dos dois primeiros modelos, uma vez que apenas os conteúdos gráficos concluídos são copiados para o GRAM externo.

Modelo 4) Tampão de quadro de pingue-pongue:

![Tampão de quadro de ping-pong](./media/guix/user-guide/ping-pong-frame-buffers.png)

No modelo 4, existe memória suficiente para fornecer dois tampão de moldura locais. Neste caso, o GUIX trata um tampão de quadro como o tampão de moldura ativo, e o outro como o tampão do quadro de trabalho. Quando uma atualização do visor ou uma operação de desenho está em andamento, ocorre no tampão de trabalho. Quando a operação de desenho termina, os tampão são toggled, e o tampão de trabalho torna-se o tampão ativo e o tampão ativo torna-se o tampão de funcionamento. Este modelo também elimina o cintilar e rasgar o ecrã que pode ser observado num único sistema tampão.

Modelo 5) Tampão de ping-pong com composição de lona:

![Tampão de ping-pong com composição de lona](./media/guix/user-guide/ping-pong-buffers-canvas-composting.png)

No modelo 5, podem ser criadas várias telas, até aos limites da memória disponível. As telas podem ser sobrepostas ou misturadas conforme definido pela aplicação para criar o compósito de lona. Quando um novo composto é criado após uma operação de atualização de ecrã, os amortecedores compósitos ativos e funcionais são alternados numa operação idêntica à arquitetura tampão de ping-pong padrão. O Model 5 adiciona a capacidade de realizar operações de desvanecimento e mistura de ecrã, misturando as telas no compósito de saída final.

Modelo 6) Tela composição com GRAM externo:

![Composição de lona com GRAM externo](./media/guix/user-guide/canvas-compositing-external-gram.png)

O Model 6 é uma ligeira variação no Model 5, no qual é necessário apenas um tampão composto e o tampão composto é então transferido para GRAM externo. Este modelo também suporta misturas e sobreposições de ecrã completo.

## <a name="string-encoding"></a>Codificação de cordas 

GUIX por predefinição suporta codificação de cadeia de formato UTF8. O suporte para codificação de cordas UTF8 pode ser desativado definindo **GX_DISABLE_UTF8_SUPPORT** no ficheiro de cabeçalho ***gx_user.h.*** Se a codificação utf8 for desativada, o GUIX utilizará internamente apenas a codificação de caracteres de página de página de código padrão de 8 bits mais a codificação do caracteres de página de código Latino-1. A codificação de cordas UTF8 desativada resulta numa pegada de biblioteca GUIX ligeiramente menor e uma execução ligeiramente mais rápida das funções de manuseamento de cordas e desenho de texto.

A codificação de cordas UTF8 tem os seguintes traços:

  - As cordas ASCII não têm mais espaço de armazenamento do que a codificação ASCII padrão de 7 bits.

  - A maioria das funções de corda ANSI-C funcionam com codificação de cordas UTF8 sem modificação.

Todos os conjuntos de caracteres ativos no mundo, incluindo conjuntos de caracteres Kanji, podem ser representados usando a codificação de cordas UTF8.

### <a name="static-and-dynamic-strings"></a>Cordas Estáticas e Dinâmicas 

As cordas atribuídas aos seus widgets GUIX que suportam o ecrã de texto podem ser constantes de cordas estáticas definidas, que normalmente são colocadas em armazenamento constante como parte da tabela de cordas GUIX descrita abaixo, e cordas dinâmicas definidas, que são cordas geradas em tempo de execução usando serviços como ***sprintf** _ ou _*_gx_utility_ltoa_**.

Exemplos de cordas dinâmicas podem incluir um valor apresentado como um número dentro de um widget de prompt GUIX, ou uma cadeia de "hora/data" que é formatada dinamicamente com base na localização do utilizador e nas preferências de formato. Se criar cordas em tempo de execução que serão atribuídas a widgets GUIX, tais como **widgets** **GX_PROMPT** ou GX_TEXT_BUTTON, deve optar por alocar estáticamente o armazenamento para estas cordas geradas em tempo de execução (i.e)
matrizes de caracteres globais), ou pode definir e instalar uma função dinâmica de alocador de memória e usar o estilo **GX_STYLE_TEXT_COPY,** que instrui esses widgets para criar uma cópia privada das cordas de texto atribuídas.

É um erro de programação usar armazenamento temporário, como uma matriz de caracteres automáticos, para segurar uma corda gerada dinamicamente e, em seguida, atribuir esta cadeia a um widget que não tem o estilo **GX_STYLE_TEXT_COPY.** Quando este estilo não estiver ativado, o widget simplesmente copia o ponteiro de cordas fornecido, e os dados de cadeia devem ser atribuídos estáticamente ou o ponteiro de cordas widget provavelmente acabará apontando para dados de lixo produzindo resultados imprevisíveis.

### <a name="passing-gx_string-arguments"></a>Aprovação de argumentos GX_STRING 

As funções de API GUIX que aceitam um parâmetro GX_STRING verificam sempre que o comprimento da corda apontada pelo campo **GX_STRING.gx_string_ptr** corresponde ao valor do campo **GX_STRING.gx_string_length.** Se os dois campos não forem consistentes, um erro **de GX_INVALID_STRING_LENGTH** é devolvido e a API ligou para devoluções sem aceitar a atribuição de cordas.

Por razões de segurança, o software GUIX nunca utiliza internamente as funções de corda C padrão, tais como ***strlen** _ ou _*_strcpy_**. Estas funções são conhecidas por serem suscetíveis a ataques maliciosos quando os dados de cadeia são adquiridos de forma dinâmica, o que acontece frequentemente com aplicações conectadas.

A biblioteca GUIX é lançada antes de lançar 5.6 funções API definidas que aceitaram ( `GX_CONST GX_CHAR *text` ) como parâmetro. Estas funções, embora ainda suportadas para retrocompatibilidade, foram obsoletas e substituídas pelas funções API preferidas que aceitam ( `GX_CONST GX_STRING *string` ) como um parâmetro de entrada.

Por predefinição, a API de manipulação de texto predefinida está ativada permitindo que todas as aplicações previamente escritas construam de forma limpa com as últimas atualizações para a biblioteca GUIX. Para desativar a API de manuseamento de textos predefinidos, a definição **GX_DISABLE_DEPRECATED_STRING_API** deve ser adicionada ao **ficheiro de cabeçalho _gx_user.h_*_ Todas as novas aplicações devem definir _* GX_DISABLE_DEPRECATED_STRING_API** e devem utilizar apenas as funções de API de substituição. Todos os ficheiros de saída gerados pelo GUIX Studio para a versão da biblioteca GUIX, 5.6 ou mais tarde utilizarão apenas as funções de API de substituição.

A tabela que se segue lista os nomes de funções de API de substituição precedida e recentemente definidos:

| **Nome da função precedida**              | **Substituído por**                              |
| ------------------------------------------ | ----------------------------------------------- |
| gx_binres_language_table_load          | gx_binres_language_table_load_ext          |
| gx_canvas_rotated_text_draw            | gx_canvas_rotated_text_draw_ext            |
| gx_canvas_text_draw                     | gx_canvas_text_draw_ext                     |
| gx_context_string_get                   | gx_context_string_get_ext                   |
| gx_display_language_table_get          | gx_display_language_table_get_ext          |
| gx_display_language_table_set          | gx_display_language_table_set_ext          |
| gx_display_string_get                   | gx_display_string_get_ext                   |
| gx_display_string_table_get            | gx_display_string_table_get_ext            |
| gx_multi_line_text_button_text_set   | gx_multi_line_text_button_text_set_ext   |
| gx_multi_line_text_input_char_insert | gx_multi_line_text_input_char_insert_ext |
| gx_multi_line_text_input_text_set    | gx_multi_line_text_input_text_set_ext    |
| gx_multi_line_text_view_text_set     | gx_multi_line_text_view_text_set_ext     |
| gx_prompt_text_get                      | gx_prompt_text_get_ext                      |
| gx_prompt_text_set                      | gx_prompt_text_set_ext                      |
| gx_single_line_text_input_text_set   | gx_single_line_text_input_text_set_ext   |
| gx_system_string_width_get             | gx_system_string_width_get_ext             |
| gx_system_version_string_get           | gx_system_version_string_get_ext           |
| gx_text_button_text_get                | gx_text_button_text_get_ext                |
| gx_text_button_text_set                | gx_text_button_text_set_ext                |
| gx_text_scroll_wheel_callback_set     | gx_text_scroll_wheel_callback_set_ext     |
| gx_utility_string_to_alphamap          | gx_utility_string_to_alphamap_ext          |
| gx_widget_string_get                    | gx_widget_string_get_ext                    |
| gx_widget_text_blend                    | gx_widget_text_blend_ext                    |
| gx_widget_text_draw                     | gx_widget_text_draw_ext                     |

### <a name="guix-string-table"></a>Tabela de cordas GUIX 

A tabela de cordas GUIX e os recursos de cordas estão registados com uma instância de exibição GUIX.

Cada ecrã de um sistema multi-display tem a sua própria tabela de cordas, e cada ecrã pode ser executado no seu próprio idioma selecionado. Os outros tipos de recursos GUIX (cores, fontes e pixelmaps) também são mantidos pelo componente GUIX Display, uma vez que estes tipos de recursos são específicos de cada formato de cor do ecrã e profundidade de cor.

Embora possa criar manualmente a sua tabela de cordas de aplicação, a tabela de cordas de exibição é definida pela aplicação GUIX Studio como parte do seu ficheiro de recursos do projeto. Os idiomas disponíveis também são definidos no ficheiro do cabeçalho de recursos. A tabela de cordas de exibição é uma tabela multi-coluna de ponteiros para as cordas de aplicação. Cada coluna da tabela de cordas representa uma língua suportada pela aplicação.
Se a sua aplicação suportar apenas um idioma, por exemplo inglês, então a sua tabela de cordas terá apenas uma coluna. Ainda assim, pode adicionar suporte para idiomas adicionais a qualquer momento sem modificar o seu software de aplicação.

A tabela de cordas ativa é atribuída através da função ***API gx_display_string_table_set.*** Esta função é chamada automaticamente pelo código de arranque gerado pelo GUIX Studio, mas também pode ser chamada diretamente pela aplicação para alterar a tabela de cordas ativa.

A linguagem ativa é atribuída através da chamada ***de função API gx_display_ative_language_set.*** Esta função determina qual a coluna da tabela de cordas do visor que está ativa.

Quando esta função é invocada, um evento **GX_EVENT_LANGUAGE_CHANGE** é enviado para todos os widgets GUIX visíveis, permitindo-lhes atualizar para exibir os dados de cadeias recentemente ativos.

Widgets e software de aplicação resolvem cordas estáticas definidas usando valores de ID de cadeia e as funções ***de API gx_display_string_get_ext*** ou ***gx_widget_string_get_ext.*** Estas funções devolvem o **GX_STRING** associado a um dado ID de corda e à linguagem atualmente ativa.

### <a name="bi-directional-text-display"></a>Exibição de texto bidirecional 

O GUIX fornece duas estratégias para suporte a texto bidirecional.

Uma opção é fazer reordenar texto bidi dentro da aplicação GUIX Studio. A utilização desta opção, o GUIX Studio é responsável por gerar texto bidi para o ficheiro de saída na sua ordem de exibição. Esta solução tem um impacto nulo no desempenho do tempo de execução e não requer adições à biblioteca de tempo de execução GUIX. Para permitir que o ESTÚDIO GUIX gere as cadeias de texto bidi do displayorder, deve selecionar o Texto Generate Bidi na caixa de **verificação 'Ordem de Visualização'** no diálogo de configuração do guix studio:

![Configurar idiomas](./media/guix/user-guide/configure-languages.png)

Com estas opções selecionadas, o ficheiro de recursos gerados conterá as cordas Bidi geradas por ordem de exibição, e não é necessário um processamento extra dentro da biblioteca de tempo de execução GUIX.

A segunda opção é fazer reordenar o texto bidi no tempo de execução. Esta opção é suportada para as aplicações que devem lidar com a cadeia de texto bidi que são definidas de forma dinâmica e não geradas pela aplicação GUIX Studio. Neste caso, a biblioteca de tempo de execução GUIX é responsável por reordenar o texto bidi antes de desenhar cada cadeia de texto. Esta solução tem um desempenho de tempo de execução e impacto na memória. Deve estar disponível memória dinâmica suficiente para o processo de reordenamento de texto bidi. Esta solução requer que o GX_DYNAMIC_BIDI_TEXT_SUPPORT condicional seja definido na construção da biblioteca GUIX. São fornecidas ***duas*** funções API gx_system_bidi_text_enable e ***gx_system_bidi_text_disable*** para permitir/desativar o suporte de texto bidi em tempo de execução.

Não deve utilizar **GX_DYNAMIC_BIDI_TEXT_SUPPORT** e configurar o GUIX Studio para gerar texto Bidi em ordem de exibição. Deve selecionar uma estratégia ou outra para o manuseamento de cadeias de texto bidi.

## <a name="memory-usage"></a>Utilização de Memória 

O GUIX reside juntamente com o programa de candidatura. Como resultado, a utilização da memória estática (ou memória fixa) do GUIX é determinada pelas ferramentas de desenvolvimento; por exemplo, o compilador, linker e localizador. A utilização da memória dinâmica (ou memória de tempo de execução) está sob controlo direto da aplicação.

### <a name="static-memory-usage"></a>Utilização da memória estática 

A maioria das ferramentas de desenvolvimento divide a imagem do programa de aplicação em cinco áreas básicas: *instrução,* dados *constantes,* *inicializados,* *dados não ininitializados* e a *pilha de fios GUIX.* A figura X na página X mostra um exemplo destas áreas de memória.

É importante compreender que este é apenas um exemplo. O layout real da memória estática é específico para o processador, ferramentas de desenvolvimento, hardware subjacente e a própria aplicação.

A área de instrução contém todas as instruções do processador do programa. Esta área está frequentemente localizada em ROM.

A área constante contém várias constantes compiladas, que no GUIX contém definições padrão e todos os recursos de aplicação (imagens, cordas, fontes e cores). Além disso, esta área contém a "cópia inicial" da área de dados inicializada. Durante o processo de inicialização do compilador, esta parte da área constante é usada para configurar os dados iniciais globais na RAM. A área constante é tipicamente a maior e geralmente segue a área de instrução e está frequentemente localizada em ROM.

Os pixelmaps e os tipos de letra GUIX normalmente requerem grandes quantidades de armazenamento constante de dados. Estas grandes áreas de dados estáticas são normalmente mantidas em ROM ou FLASH.

A pilha de fio GUIX é definida dentro da área de dados não iniializada (como uma variável global) no ficheiro ***gx_system.h*** da seguinte forma:

```C
_gx_system_thread_stack[GX_THREAD_STACK_SIZE];
```

**GX_THREAD_STACK_SIZE** é definido em **_gx_port.h,_** mas pode ser ultrapassado pela aplicação definindo este símbolo no ficheiro ***cabeçalho gx_user.h*** ou através de opções de projeto ou parâmetros de linha de comando. O tamanho da pilha deve ser grande o suficiente para lidar com o pior caso de manuseamento de eventos e chamadas de desenho aninhadas.

### <a name="dynamic-memory-usage"></a>Utilização dinâmica da memória 

Como mencionado anteriormente, o uso dinâmico da memória está sob o controlo direto da aplicação. Os blocos de controlo e a memória associados a telas, etc. podem ser colocados em qualquer lugar no espaço de memória do alvo. Esta é uma característica importante porque facilita a fácil utilização de diferentes tipos de memória física – em tempo de execução.

Por exemplo, suponha que um ambiente de hardware alvo tenha memória rápida e memória lenta. Se a aplicação necessitar de um desempenho extra para o desenho, a memória de tela pode ser colocada explicitamente na área de memória de alta velocidade para melhor desempenho.

Vários serviços e funcionalidades opcionais do GUIX requerem um mecanismo de alocação de memória dinâmica de tempo de execução, vulgarmente referido como um monte. Estes serviços e funcionalidades são completamente opcionais, e muitas aplicações GUIX não usam qualquer pilha e não definem um mecanismo de atribuição de memória em tempo de execução.

Se utilizar serviços que exijam a atribuição de memória em tempo de execução, tem de instalar funções a que o GUIX irá chamar quando a memória tiver de ser atribuída dinamicamente ou libertada. Pode implementar estas funções como preferir, de modo que, mesmo neste caso, a localização do pool de memória dinâmica esteja sob controlo de aplicações. Para instalar suporte para a atribuição dinâmica de memória, a aplicação deve invocar o serviço API ***gx_system_memory_allocator_set*** durante o arranque do programa para definir os serviços de atribuição de memória e de memória. Consulte a documentação desta API para obter um exemplo completo.

Os serviços GUIX que requerem uma atribuição de memória em tempo de execução e um serviço de desatribuição incluem:

  - Carregamento de recursos binários do armazenamento externo para o ambiente de tempo de execução GUIX.

  - O software executar o descodificador de imagem JPEG.

  - O descodificador de imagem de png de execução de software.

  - Utilizar widgets de texto com GX_STYLE_TEXT_COPY.

  - Funcionamento pixemap redimensionar e rotação funções de utilidade.
  - Tela de execução e alocação de bloco de controlo widget.

Para aplicações mais pequenas, os recursos GUIX são geralmente compilados e estáticos ligados como parte da imagem da aplicação, e a instalação de recursos binários não é necessária. Os recursos binários permitem uma aplicação para instalar recursos (fontes, imagens, idiomas) no tempo de execução carregados a partir de algum local de armazenamento, como uma pen drive ou um URL.

Os descodificam o jpeg e o png são componentes opcionais. A maioria das aplicações GUIX permitem que a ferramenta GUIX Studio pré-descodifique todos os ficheiros de imagem necessários e os armazene como recursos de dados guix Pixemap proprietários. Estes serviços são fornecidos para a completude para as aplicações que requerem conversão em tempo de execução de imagens jpeg e/ou PNG para o formato pixelmap.

**GX_STYLE_TEXT_COPY** permite ao utilizador especificar que um widget ou widgets específicos manterá a sua própria cópia privada de texto atribuído dinamicamente. A utilização desta opção requer que o mecanismo de atribuição de memória seja instalado antes da utilização. Se esta bandeira de estilo **<span class="underline">não</span>** for fornecida quando um widget do tipo de texto é criado, a aplicação deve atribuir áreas de armazenamento estática para todas as cordas de texto criadas e atribuídas dinamicamente. Neste caso, as variáveis automáticas não devem ser utilizadas para conter os dados de cadeia gerados pelo tempo de execução. Se o estilo **GX_STYLE_TEXT_COPY** estiver ativado, podem ser utilizadas variáveis automáticas para conter dados de cadeias atribuídos aos widgets GUIX, uma vez que cada widget criará a sua própria cópia do texto atribuído.

As funções de utilitário de redimensione e rotação da Pixelmap devolvem o pixelmap traduzido resultante como um novo pixelmap disponível para a aplicação.
Deve existir uma memória dinâmica suficiente para manter estes blocos de dados de pixelmap gerados em tempo de execução se estes serviços forem utilizados.

Finalmente, os blocos de controlo para os ecrãs guix e widgets podem ser atribuídos de forma estática ou dinâmica. Para aplicações mais pequenas, é comum criar todos os ecrãs de aplicações durante o arranque do programa e utilizar blocos de controlo estáticos. Para aplicações grandes, é comum criar controlos de ecrã e widget infantil dinamicamente em bases necessárias. Os blocos de controlo atribuídos dinamicamente são especificados selecionando a caixa de verificação **Runtime Allocate** na vista das propriedades do ESTÚDIO GUIX, ou passando na bandeira de estilo **GX_STYLE_DYNAMICALLY_ALLOCATED** ao criar um widget através da API padrão. A utilização de blocos de controlo widget atribuídos dinamicamente requer que os serviços de atribuição de memória e delocação sejam definidos como descrito acima.

## <a name="guix-components"></a>Componentes GUIX 

As APIs GUIX são divididas e organizadas em vários grupos básicos que correspondem a componentes fundamentais do sistema GUIX. Os componentes fundamentais incluem:

| <!-- -->    | <!-- -->    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GX_SYSTEM  | O componente do sistema GUIX, responsável pela inicialização, eventos, temporizadores, tabelas de cordas e gestão da hierarquia widget visível.                                                                                                                                                                                                                                                                      |
| GX_CANVAS  | Uma área de desenho. Uma Tela pode ser uma abstração fina do tampão de moldura de hardware, ou também pode ser uma tela de memória pura. O tipo de lona é determinado por parâmetros passados para a função API gx_canvas_create.                                                                                                                                                                                   |
| GX_CONTEXT | O componente de contexto de desenho. O contexto de desenho contém informações sobre o ecrã, tela e escova, e área de recorte para as operações de desenho atuais.                                                                                                                                                                                                                                      |
| GX_DISPLAY | Fornece as implementações apis e ao nível do condutor para permitir que a sua aplicação e os widgets GUIX realizem o desenho numa tela. GX_DISPLAY é implementado para renderizar corretamente gráficos em cada tela usando o formato de cores necessário para tela. O componente GX_DISPLAY também gere os recursos (cores, fontes e pixelmaps) disponíveis para widgets desenho para telas ligadas a cada ecrã. |
| GX_WIDGET  | O objeto widget visível básico e APIs associados. Todos os tipos de widget GUIX são baseados ou derivados do tipo GX_WIDGET básico.                                                                                                                                                                                                                                                                      |
| GX_UTILITY | As funções de utilidade para trabalhar com retângulos, funções para conversão de cordas e funções matemáticas não-ANSI estão incluídas neste grupo.                                                                                                                                                                                                                                                         |

Além destes componentes básicos, o GUIX inclui APIs exclusivos de cada tipo de widget fornecido na biblioteca. Estas APIs são descritas no Capítulo 4 deste Manual do Utilizador, "Descrição dos Serviços GUIX".

## <a name="guix-system-component"></a>Componente do sistema GUIX

A componente do sistema GUIX fornece vários serviços que são globais à aplicação UI. Estes serviços incluem: *inicialização, gestão de eventos, gestão de ecrãs, gestão de recursos, gestão de temporizadores* e *gestão de widgets.* Cada serviço é essencial para a organização do seu programa de candidatura, e estes serviços são descritos com mais detalhe nas seguintes sub-secções.

### <a name="initialization"></a>Inicialização 

A inicialização do GUIX é realizada pela aplicação que chama o ***serviço gx_system_initialize,*** que pode ser chamada pela aplicação da rotina ***tx_application_define*** ThreadX (contexto de inicialização) ou a partir de threads de aplicação. A função ***gx_system_initialize*** inicializa todas as estruturas globais de dados GUIX e cria o sistema GUIX mutex, fila de eventos, temporizador e linha. Uma vez ***retornas gx_system_initialize,*** a aplicação pode utilizar o GUIX.

### <a name="thread-processing"></a>Processamento de fios 

O fio GUIX interno – criado durante a inicialização – é responsável pela maior parte do processamento no GUIX. O processamento desta linha completa pela primeira vez qualquer inicialização adicional exigida pelo controlador de visualização subjacente. Uma vez concluído, o fio GUIX entra num loop que primeiro processa todos os eventos presentes na fila do evento GUIX e, em seguida, refresca o ecrã se necessário. A atualização do ecrã executa as funções de desenho guix necessárias, com base no que é visível e foi marcado como significado sujo que precisa de ser redesenhado. Quando não houver eventos e nada mais para refrescar no ecrã, o fio GUIX suspenderá, aguardando a chegada do próximo evento GUIX.

### <a name="rtos-binding"></a>Ligação RTOS 

O componente do sistema GUIX está configurado por padrão para utilizar o sistema operativo ThreadX em tempo real para serviços como serviços de thread, serviços de fila de eventos e serviços de temporizador. O GUIX pode ser facilmente portado para outros sistemas operativos utilizando a diretiva do pré-processor GX_DISABLE_THREADX_BINDING e reconstruindo a biblioteca GUIX. Isto remove as dependências da ThreadX do código fonte GUIX e permite que o desenvolvedor de aplicações implemente os serviços do sistema operativo necessários utilizando qualquer RTOS fornecido pelo sistema-alvo. [Apêndice F - GUIX RTOS Binding Services](appendix-f.md) descreve os serviços que precisam de ser implementados para portar GUIX para um sistema operativo diferente do sistema operativo ThreadX.

### <a name="multithread-safety"></a>Segurança Multi-Televisão 

A API GUIX está disponível a partir do contexto do fio GUIX, bem como de outros fios de aplicação. Os fios de aplicação podem interagir com o fio GUIX enviando e recebendo eventos, através do acesso a variáveis partilhadas, e através da utilização das funções de API GUIX. O GUIX utiliza um mutex ThreadX interno para proteção de recursos multi-fios. Além disso, o GUIX impede que a estrutura interna de widgets visíveis seja modificada uma vez iniciada uma operação de atualização do ecrã. As APIs que modificariam a árvore dos objetos visíveis são bloqueadas enquanto as operações de desenho estão em andamento, e libertadas assim que a atualização do ecrã estiver completa.

### <a name="system-timers"></a>Temporizadores de sistema 

O GUIX fornece a aplicação com temporizadores periódicos, que são frequentemente utilizados para a atualização periódica de dados exibidos nas janelas GUIX. Isto é realizado através de um temporizador periódico ThreadX, que também é usado para executar efeitos de nível do sistema GUIX como o desvanecimento do ecrã dentro/fora, etc.

A aplicação pode criar temporizadores e utilizar a mesma facilidade de temporizador que é usada internamente pelo GUIX. É claro que a aplicação também pode criar e utilizar diretamente os temporizadores ThreadX, se necessário. A vantagem dos temporizadores GUIX é que são muito fáceis de usar e estão pré-configurados para trabalhar dentro do sistema de processamento orientado por eventos GUIX.

Para criar e iniciar um temporizador GUIX, a aplicação deve invocar a função ***gx_system_timer_start***. Os parâmetros desta função incluem um ponteiro para o widget de chamada, o id do temporizador (permitindo que um widget inicie muitos temporizadores) e os valores de tempo limite inicial e reagendador. Se o valor de tempo de reagendamento for 0, o temporizador só funcionará uma vez e apagar-se-á da lista de temporizadores ativos assim que expirar.

Uma vez iniciado, o temporizador GUIX enviará eventos GX_EVENT_TIMEOUT ao proprietário do temporizador, uma vez ou periodicamente dependendo do valor de reagendamento do temporizador. Um temporizador GUIX pode ser interrompido chamando a função API ***gx_system_timer_stop***.

### <a name="pen-speed-configuration"></a>Configuração de velocidade da caneta 

O componente do sistema GUIX contém informações de configuração relacionadas com o rastreio da velocidade da caneta. GUIX gerou internamente **GX_EVENT_VERTICAL_FLICK** e **GX_EVENT_HORIZONTAL_FLICK** eventos baseados na velocidade e distância de eventos PEN_DOWN gerados pelo condutor de entrada de toque, se houver. A aplicação pode configurar a distância e velocidade mínima necessárias para desencadear estes eventos gerados internamente utilizando a função **_API gx_system_pen_configure._**

### <a name="screen-stack"></a>Pilha de tela 

O componente do sistema GUIX fornece serviços relacionados com a pilha de ecrã GUIX, que é uma funcionalidade opcional que suporta uma pilha de widgets virtuais na qual os ecrãs podem ser empurrados, estaladiços e recuperados em tempo de execução pela aplicação. A pilha de ecrã é útil para gerir sistemas de menus complexos, através dos quais a rota pela qual o utilizador pode chegar a vários estados do sistema de menus é variada. O regresso ao estado anterior no sistema de menus pode ser feito facilmente empurrando primeiro o estado do ecrã anterior, depois exibindo o novo ecrã, e permitindo que o novo ecrã apareça o estado anterior a partir da pilha de ecrã quando o ecrã atual é descartado.

### <a name="clipboard-maintenance"></a>Manutenção de Prancheta 

O GUIX suporta uma prancheta para copiar e colar texto durante a execução. Este suporte é fornecido pelo componente do Sistema GUIX.

### <a name="dirty-list-maintenance"></a>Manutenção de Listas Sujas 

O GUIX mantém uma lista de widgets sujos, o que significa widgets visíveis e precisam ser redesenhados devido a alterações de estado ou serem tornados recentemente visíveis. Esta lista suja melhora o desempenho do desenho, permitindo que o GUIX faça uma operação de atualização de tela para refletir todas as alterações atuais no estado de UI, em vez de fazer uma atualização de lona à medida que cada alteração de UI é feita.
Esta lista suja também é mantida pelo componente do sistema GUIX.

### <a name="animation-control-block-pool"></a>Piscina do Bloco de Controlo de Animação 

As aplicações muitas vezes desejam executar múltiplas sequências de animação, muitas vezes em paralelo. O GUIX mantém um conjunto de blocos de controlo de animação a partir dos quais a aplicação pode alocar e utilizar. Isto liberta a aplicação de definir estáticamente estes blocos de controlo e permite que sejam reutilizados em diferentes momentos, em vez de definir um bloco de controlo de animação único para cada animação que a aplicação possa definir. O conjunto do bloco de controlo de animação também é mantido pelo componente do sistema GUIX.

### <a name="system-error-handling"></a>Manipulação de erros do sistema 

O manipulador de erros do sistema GUIX destina-se a ajudar a aplicação a encontrar erros internos do sistema no GUIX que possam ser mais difíceis de determinar do ponto de vista da API. Sempre que ocorre um erro de sistema no interior do GUIX, a função ***de _gx_system_error_process*** interna é chamada. Esta função guarda o código de erro fornecido e incrementa o número total de erros do sistema detetados. As variáveis de erro do sistema são definidas da seguinte forma:

_gx_system_last_error **UINT;**

_gx_system_error_count **ULONG;**

Se a aplicação GUIX se comportar de forma estranha, é útil olhar para a variável de contagem de erros no depurar. Se estiver definido, uma boa maneira de resolver o problema é definir um ponto de rutura na função ***_gx_system_error_process*** e ver quando/de onde está a ser chamado.

## <a name="guix-canvas-component"></a>Componente de lona GUIX

O componente de lona é responsável por todo o processamento relacionado com tela. Uma tela é efetivamente um tampão de moldura virtual. A sua aplicação deve criar pelo menos uma tela para produzir uma saída gráfica.
Normalmente, criaria pelo menos uma tela para cada ecrã físico suportado pelo seu sistema.

Todo o desenho do GUIX tem lugar numa tela. Em sistemas mais simples ou limitados à memória, provavelmente haverá apenas uma tela que pode estar diretamente ligada ao tampão de quadro visível, enquanto sistemas com mais memória e requisitos gráficos mais avançados podem exigir múltiplas telas. Disponibilizar várias telas para um ecrã permite funcionalidades como o desvanecimento do ecrã e da janela e os efeitos de desvanecimento.
As telas podem ser um dos dois tipos principais, simples ou geridos.

Uma tela simples é uma área de desenho fora do ecrã usada pela aplicação.
O GUIX não faz nada diretamente com uma tela simples, mas a aplicação pode usar uma tela simples para tornar o desenho complexo para um tampão fora do ecrã e, em seguida, usar este tampão fora do ecrã para refrescar a tela visível quando necessário.

Uma tela gerida é exibida automaticamente dentro do tampão de quadro de hardware pelo GUIX. Uma tela gerida está incluída na construção de uma tela composta para esses sistemas com memória suficiente para suportar várias telas geridas. Telas geridas têm uma ordem Z mantida pelo GUIX, e o recorte de vista é aplicado em todas as telas geridas.

Uma tela difere de um tampão de moldura na medida em que é mais genérico. Nos sistemas constrangidos de memória, pode haver apenas uma tela e a memória para esta tela pode ser a memória visível do tampão do quadro. No entanto, para sistemas mais complexos que suportam sobreposições gráficas mais avançadas e múltiplas telas, as telas geridas são cada uma das suas áreas de memória que são distintas da memória tampão de quadro de hardware.
Estas telas geridas são renderizadas no tampão visível do quadro durante a atualização ou o funcionamento do tampão da moldura.

Para hardware que suporta várias camadas gráficas, ou seja, vários tampões de moldura sobrepostos, a aplicação pode ligar uma ou mais telas às camadas de gráficos de hardware utilizando a ***API gx_canvas_hardware_layer_bind.*** Este serviço informa a tela de que está ligado a uma determinada camada gráfica de hardware, e uma vez ligado esta tela tentará utilizar suporte de hardware para visibilidade de tela (i.e gx_canvas_show, gx_canvas_hide), mistura alfa de lona ***(isto é, gx_canvas_alpha_set)*** e lona compensada no visor ***(gx_canvas_offset_set).***

Para outras arquiteturas que não a mais simples organização tampão de tela única/quadro único, o tamanho de uma tela é determinado pela aplicação e pode ser diferente do tamanho fixo de um tampão de moldura.
Também pode estar numa compensação selecionada pela aplicação. Outras informações, como a ordem Z, são mantidas dentro da tela. Quando o desenho de tela estiver completo, o conteúdo da tela é transferido para o visor físico pelo controlador de visualização. Em alguns sistemas que não têm memória suficiente para uma tela separada e áreas de memória tampão de moldura, a atualização de lona é realmente feita diretamente para o ecrã físico através do controlador de exibição.

### <a name="canvas-creation"></a>Criação de Tela 

Um objeto de tela pode ser criado durante a inicialização ou a qualquer momento durante a execução dos fios de aplicação. Não há limite para o número de objetos de lona que podem ser criados por uma aplicação. A maioria das aplicações, no entanto, criará apenas um objeto de lona para todos os desenhos GUIX.

### <a name="canvas-control-block"></a>Bloco de Controlo de Lona 

As características de cada objeto de lona encontram-se no seu bloco de controlo **GX_CANVAS** e são definidas em **_gx_api.h_**. A memória necessária para um objeto de lona é fornecida pela aplicação e pode ser localizada em qualquer lugar na memória. No entanto, é mais comum fazer do bloco de controlo de objetos de lona e da área de desenho uma estrutura global, definindo-os fora do âmbito de qualquer função.

### <a name="canvas-alpha-channel"></a>Canal Alfa de Tela

O GUIX suporta a mistura alfa de cores de primeiro plano e de fundo em muitos níveis, incluindo o canal alfa bitmap, que especifica uma relação de mistura por pixel, a escova alfa que especifica a relação de mistura para uma escova a 16 bpp e profundidades de cor mais altas, e alfa de lona que especifica a relação de mistura para uma tela sobreposta.

O valor alfa de uma tela é usado quando existem múltiplas telas que são compostas em conjunto para visualização dentro do tampão de moldura. Se a tela Z-ordem é tal que uma tela está acima de outras telas, então o valor alfa de lona pode ser definido para misturar a tela com as que estão por trás. Modificar rapidamente o valor alfa de uma tela é usado para fornecer efeitos de transição de ecrã "desvanecendo", mas o alfa de tela pode ser usado de muitas maneiras.

Se uma tela estiver ligada a uma camada de gráficos de hardware utilizando gx_canvas_hardware_layer_bind(), o GUIX tentará implementar a mistura alfa de lona utilizando suporte de hardware, minimizando a sobrecarga do software associada à mistura de uma tela sobreposta.

Os valores alfa variam de 0 a 255, onde um valor de 0 significa que o pixel é totalmente transparente e valores superiores a 0 estão a aumentar o valor alfa de lona menos transparente só podem ser suportados para os condutores de ecrã que correm a 16-bpp e mais altos, a menos que seja fornecida assistência de hardware para mistura de lona.

### <a name="canvas-offset"></a>Compensação de Lona 

Uma tela pode ser compensada dentro do tampão de moldura visível invocando o ***serviço API gx_canvas_offset_set.*** As compensações de lona são geralmente usadas para implementar animações de sprite. Se uma tela estiver ligada a uma camada de gráficos de hardware invocando a função ***API gx_canvas_hardware_layer_bind,*** o GUIX tentará implementar alterações compensativas de lona utilizando o suporte de hardware, minimizando a sobrecarga do software associada à mudança da posição de tela.

### <a name="canvas-drawing"></a>Desenho de tela 

O componente de lona GUIX fornece uma API de desenho completo à aplicação. Antes de as APIs de desenho, tais como ***gx_canvas_line_draw*** ou ***gx_canvas_pixelmap_draw*** poderem ser invocadas, a tela-alvo deve ser aberta para desenho invocando a função ***API gx_canvas_drawing_initiate.*** Esta função prepara uma tela para o desenho e cria um ***contexto de desenho.***

As APIs de desenho que prestam à tela, tais como ***gx_canvas_line_draw** _ ou _*_gx_canvas_text_draw,_*_ utilizam parâmetros encontrados na escova de contexto de desenho atual para definir o estilo, largura e cores da linha. Estes parâmetros da escova são modificados chamando o _*_gx_context_brush_define_*_, _* _gx_context_brush_set_**, ***gx_context_brush_style_set**_, e funções API semelhantes após um contexto de desenho foi estabelecido chamando _*_gx_canvas_drawing_initiate_**.

Quando o GUIX invoca as funções de desenho da janela e do widget como parte de uma operação de atualização de lona diferida, a tela-alvo é aberta para desenho antes de chamar a função de desenho de widgets. Portanto, as funções padrão de desenho widget não são necessárias para abrir a tela-alvo, o que foi feito para eles.

Em alguns casos, o pedido pode querer forçar o desenho imediato a uma tela. Neste caso, a aplicação pode executar os seguintes passos.

1. Ligue para a função API ***gx_canvas_drawing_initiate,*** passando na tela-alvo e no retângulo dentro daquela tela em que a aplicação pretende desenhar. 

2. Ligue para qualquer número de APIs de desenho de tela para realizar o desenho desejado.

3. Ligue para a ***função*** API gx_canvas_drawing_complete para sinalizar que o desenho foi concluído. Isto coloca a lona no tampão visível do quadro e/ou aciona um funcionamento do tampão, dependendo da arquitetura da memória do sistema.

### <a name="drawing-apis"></a>APIs de desenho 

Existem vários primitivos principais de desenho que são necessários pelo GUIX para desenhar todos os elementos visuais no ecrã. Estes APIs de desenho também podem ser invocados pelo software da aplicação, geralmente como parte de uma função de desenho de widget personalizado. Estes APIs de desenho de tela GUIX executam a validação e recorte de parâmetros e, em seguida, passam as coordenadas de desenho cortadas para o controlador de exibição para implementações específicas de hardware e formato de cores. Estas funções de API de desenho são definidas da seguinte forma.

- gx_canvas_alpha_set
- gx_canvas_arc_draw
- gx_canvas_block_move
- gx_canvas_circle_draw
- gx_canvas_ellipse_draw
- gx_canvas_glyphs_draw
- gx_canvas_hardware_layer_bind
- gx_canvas_hide
- gx_canvas_line_draw
- gx_canvas_offset_set
- gx_canvas_pie_draw
- gx_canvas_pixel_draw
- gx_canvas_pixelmap_blend
- gx_canvas_pixelmap_rotate
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_rotated_text_draw
- gx_canvas_shift
- gx_canvas_show
- gx_canvas_text_draw

O desenho API é invocado através da API de Tela GUIX, e todo o desenho é feito usando funções de API gx_canvas_*. O desenho é feito usando a escova atual no contexto de desenho atual. Qualquer uma das funções de desenho de forma acima pode ser delineada, cor sólida preenchida, ou pixelmap preenchido como definido pela escova atual. Para modificar a largura, cor ou preenchimento do contorno da forma, utilize as funções de API gx_context_brush_* para definir a escova dentro do contexto de desenho atual.

As APIs de desenho de nível de aplicação acima não fazem desenho real para a tela, mas verificam os parâmetros do chamador antes de invocar a função de desenho do nível do controlador do visor. A função de desenho de nível do controlador realmente escreve dados de pixel na memória de tela.

O GUIX fornece funções de desenho do controlador de estoque ou de ecrã genérico para várias profundidades de cores, incluindo 1, 2, 4, 8, 16, 24 e 32 bits por pixel (bpp). Em alguns casos, a implementação de desenho de software padrão é substituída por implementações aceleradas por hardware para os alvos de hardware que fornecem um acelerador de desenho 2D.

### <a name="color-depth"></a>Profundidade da cor 

O GUIX suporta profundidades de cor até 32 bpp, bem como monocromáticos e em tons de cinza. O tipo de suporte de profundidade de cor em grande parte determinado pelas capacidades do ecrã físico subjacente e também tem um impacto na quantidade de memória necessária para a área de desenho de tela. Segue-se uma lista de suporte de profundidade de cor, juntamente com uma breve descrição das variações dentro dessa profundidade de cor.

| Formato de cor &nbsp;       | Descrição                                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| Monocromático de 1 bit   | Formato embalado de 1 bit por pixel.                                                                                                   |
| Escala de cinza de 2 bits    | 4 níveis cinzentos, embalados quatro píxeis por byte.                                                                                      |
| Escala de cinza de 4 bits    | 16 níveis cinzentos, embalados dois píxeis por byte.                                                                                      |
| Cor de 4 bits        | Uma organização de memória planar de formato VGA.                                                                                         |
| Escala de cinza de 8 bits    | 256 níveis cinzentos                                                                                                                  |
| Modo paleta de 8 bits | 1 byte por pixel usado como índice de paleta                                                                                           |
| Modo r:g:b de 8 bits   | Um formato menos comumente usado 2:3:2 r:g:b.                                                                                         |
| 16 bits             | Cada pixel requer dois bytes. Pode ser r:g:b ou b:g:r byte order. Normalmente 5:6:5 estrutura, mas também pode ser 5:5:5 estrutura ou 4:4:4:4 a:r:g:b estrutura. |
| 24 bits             | Cada pixel requer 3 bytes (embalsamados) ou 4 (formato desembalado). Pode ser em r:g:b ou b:g:r byte order, conforme exigido pelo hardware. |
| 32 bits             | Cada pixel requer 4 bytes com um canal alfa. Pode ser a:r:g:b ou b:g:r:a byte order e determinado por hardware.              |

### <a name="mouse-support"></a>Suporte ao rato 

O GUIX suporta desenhar um cursor de rato em qualquer tela desejada. O cursor do rato pode estar a desenhar em software ou pode ser suportado por sobreposição de cursores de hardware. Em qualquer dos casos, a API fornecida à aplicação relacionada com o suporte do cursor do rato é a mesma, quer se utilize o desenho do cursor de rato de hardware ou hardware.

O suporte do rato GUIX só é ativado se o `#define GX_MOUSE_SUPPORT` for definido no ficheiro de cabeçalho gx_user.h antes de construir a biblioteca GUIX.

A aplicação deve definir o cursor do rato e o hotspot utilizando a função ***API gx_canvas_mouse_define.*** Esta API aceita um ponteiro para a tela sobre a qual a imagem do cursor deve ser desenhada, e um ponteiro para uma estrutura **GX_MOUSE_CURSOR_INFO,** que define a imagem do cursor do rato e o hotspot da imagem do rato relativo ao canto superior esquerdo da imagem.

## <a name="guix-display-component"></a>Componente de exibição GUIX 

O componente de exibição é fundamental no GUIX, uma vez que gere o processamento de todos os objetos de exibição, que por si só contêm uma ou mais telas, widgets e janelas. O componente de exibição também interage com o controlador de ecrã de hardware subjacente associado a cada ecrã através de uma série de ponteiros de função.

### <a name="display-creation"></a>Criação de Exibição 

Um objeto de visualização pode ser criado durante a inicialização ou a qualquer momento durante a execução dos fios de aplicação. Normalmente, uma aplicação cria um objeto de exibição para gerir cada ecrã físico. Se utilizou o GUIX Studio para definir a sua aplicação e os ecrãs físicos disponíveis, utilizará a função API gx_studio_display_configure para criar e inicializar cada um dos seus ecrãs.

### <a name="display-control-block"></a>Bloco de controlo de exibição 

As características de cada objeto de visualização encontram-se no seu bloco de controlo ***GX_DISPLAY** _ e são definidas em _*_gx_api.h**._ A memória necessária para um objeto de visualização é fornecida pela aplicação e pode ser localizada em qualquer lugar da memória. No entanto, é mais comum fazer do bloco de controlo de ecrã uma estrutura global definindo-a fora do âmbito de qualquer função.

### <a name="resource-management"></a>Gestão de Recursos 

Os recursos são componentes de UI que são necessários pela aplicação, mas não são código de aplicação. Os recursos são dados de aplicação e são geralmente definidos estáticamente. Os tipos de recursos incluem pixelmaps, fontes, cores e cordas. Estes recursos podem ser alterados a qualquer momento, normalmente sem alterar qualquer software de aplicação. É importante manter o armazenamento e as referências aos recursos separados do software de aplicação para permitir a alteração da aparência de UI sem alterar o código de aplicação, uma vez que as alterações ao software de aplicação geralmente requerem o re-teste e verificação associados desse software.

O módulo ***de exibição*** GUIX fornece instalações de gestão de recursos para todos os recursos que dependem da profundidade de cor e do formato do ecrã. Estas instalações incluem a manutenção da tabela de pixelmap ativa, tabela de fontes ativa e mesa de cores ativa. O recurso da tabela de cordas é mantido pelo módulo do sistema GUIX, uma vez que os recursos de corda normalmente não precisam de ser alterados com base na profundidade e no formato da cor.

O software de aplicação refere recursos através do seu ID de recursos, que é um índice na tabela de recursos correspondente. Isto permite que a tabela seja alterada, por exemplo, a tabela de cores pode ser alterada quando um produto muda de "modo diurno" para "modo noturno", mas os valores de ID de cor permanecem os mesmos.

Os seus recursos de aplicação são escritos num ficheiro de recursos (ou conjunto de ficheiros de recursos) pela aplicação GUIX Studio. Cores predefinticas, pixelmaps e fontes são fornecidas automaticamente quando cria um novo projeto GUIX Studio, mas estes padrão são facilmente substituídos à medida que define o aspeto e a sensação da sua aplicação.

É importante notar que os IDs de recursos para cores, fontes e pixelmaps não podem ser resolvidos com os seus valores reais de cor, fonte ou pixelmap até que o componente ative Display seja conhecido. Uma vez que a arquitetura GUIX suporta vários ecrãs ativos, os IDs de recursos só podem ser resolvidos para valores de recursos quando um widget e o seu ID de recursos associados podem ser resolvidos para um ecrã específico. Esta propriedade é conhecida como ligação dinâmica. O ID de recurso para uma propriedade como uma cor de texto, por exemplo, o ID de recurso **GX_COLOR_ID_TEXT,** pode resolver-se com um valor R:G:B de 16 bits para branco quando usado num ecrã, mas o ID de mesma cor pode resolver-se a um valor monocromático de cor preta quando usado em outro ecrã.

Na prática, esta ligação dinâmica dos IDs de Recursos aos valores dos recursos significa que o software de aplicação e os componentes internos guix devem, na maioria das vezes, apenas resolver os IDs de Recursos para valores de recursos num contexto de desenho ativo. Um contexto de desenho ativo especifica o ecrã atualmente ativo, que permite ao GUIX resolver cada ID de recurso a um valor específico de recursos. Se o software de aplicação for necessário para encontrar um valor específico de recursos fora de um contexto de desenho, isso também pode ser feito para widgets visíveis. Os widgets visíveis estão ligados a uma janela de raiz que também pode ser usada para resolver a tela ativa e exibir para esse widget.

Se um widget tiver sido criado mas ainda não exibido (isto é, não foi ligado a nenhuma janela de raiz ou a outro progenitor visível), quaisquer IDs de recursos associados a esse widget não podem ser resolvidos a um valor específico de recursos que não seja indexando diretamente na tabela de recursos atribuída a um visor específico. Este acesso direto a uma tabela de recursos específica pode ser feito com segurança pelo software da aplicação, mas nunca é feito no software interno da biblioteca GUIX.

### <a name="widget-defaults"></a>Predefinições do Widget 

O componente de exibição GUIX também fornece definições padrão para vários atributos widget. Salvo especificação em contrário da aplicação, os widgets/janelas são criados com estes atributos do sistema. Estes atributos do sistema são maioritariamente compostos por fontes, cores e bitmaps mantidos nas tabelas de recursos do sistema. Os atributos adicionais para a aparência padrão da barra de deslocação também são mantidos pelo componente de exibição GUIX.

As definições de cor predefinidas são definidas pela tabela de cores atribuída a cada ecrã e pelos IDs de cor predefinidos pré-definidos. Estes ids de cores padrão incluem o seguinte.

| ID de cor | Descrição |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| GX_COLOR_ID_CANVAS | Tela padrão (ou seja, fundo de exibição) cor |
| GX_COLOR_ID_WIDGET_FILL | Cor de preenchimento de widget padrão |
| GX_COLOR_ID_WINDOW_FILL | Cor de preenchimento de janela padrão |
| GX_COLOR_ID_DISABLED_FILL | Cor de preenchimento de widget desativado preenchimento preenchimento padrão |
| GX_COLOR_ID_DEFAULT_BORDER | Cor de fronteira widget padrão |
| GX_COLOR_ID_WINDOW_BORDER | Cor de fronteira da janela padrão |
| GX_COLOR_ID_TEXT | Cor de texto padrão |
| GX_COLOR_ID_SELECTED_TEXT | Cor de texto selecionada por padrão |
| GX_COLOR_ID_DISABLED_TEXT | Cor de texto desativada predefinido |
| GX_COLOR_ID_SELECTED_TEXT_FILL | Cor de preenchimento de texto selecionado por padrão |
| GX_COLOR_ID_READONLY_TEXT | Cor de texto de readonly padrão |
| GX_COLOR_ID_READONLY_FILL | Cor de preenchimento de texto apenas padrão |
| GX_COLOR_ID_SCROLL_FILL |    Cor de preenchimento de barra de pergaminho |
| GX_COLOR_ID_SCROLL_BUTTON | Cor de preenchimento do botão de barra de deslocamento |
| GX_COLOR_ID_SHADOW | Cor de sombra padrão |
| GX_COLOR_ID_SHINE | Cor de realce padrão |
| GX_COLOR_ID_BUTTON_BORDER | Cor de fronteira widget botão |
| GX_COLOR_ID_BUTTON_UPPER | Cor superior de preenchimento widget |
| GX_COLOR_ID_BUTTON_LOWER | Botão widget menor preenchimento cor |
| GX_COLOR_ID_BUTTON_TEXT | Cor de texto widget de botão |
| GX_COLOR_ID_TEXT_INPUT_TEXT | Cor de texto widget de entrada de texto de texto de entrada de texto de texto |
| GX_COLOR_ID_TEXT_INPUT_FILL | Cor de preenchimento de entrada de texto |
| GX_COLOR_ID_SLIDER_TICK | Cor usada para desenhar marcas de tique-taque de slider. |
| GX_COLOR_ID_SLIDER_GROOVE_BOTTOM | Cor usada para desenhar ranhura de slider |
| GX_COLOR_ID_SLIDER_NEEDLE_OUTLINE | Cor usada para desenhar contorno de agulha |
| GX_COLOR_ID_SLIDER_NEEDLE_FILL | Cor usada para encher agulha de slider |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE1 | Cor usada para desenhar o destaque da agulha |
| GX_COLOR_ID_SLIDER_NEEDLE_LINE2 | Cor usada para desenhar sombra de agulha |

Estes valores de ID de cor são mapeados para um valor de cor específico, tal como definido pela tabela de cores atribuída a cada ecrã. Estes padrão podem ser alterados como um grupo para um display, chamando a ***função API gx_display_color_table_set.*** Se estiver a utilizar o GUIX Studio, a tabela de cores do visor é inicializada automaticamente quando a sua aplicação chama a função ***gx_studio_display_configure.***

O componente de visualização GUIX também mantém uma tabela de fontes predefinido. A tabela de fontes predefinida define o tipo de letra utilizado por cada tipo de widget, a menos que especificamente especificado pela aplicação. Os IDs de tabela de tipo de letra de exibição pré-definidos incluem os seguintes valores.

| &nbsp;ID de fonte | Descrição |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------|
| GX_FONT_ID_DEFAULT | Fonte padrão utilizada quando não é definida nenhuma fonte específica |
| GX_FONT_ID_BUTTON | Fonte padrão utilizada para todo o texto em botões |
| GX_FONT_ID_TEXT_INPUT | Fonte padrão utilizada para campos de edição de texto |

O ID de fonte utilizado por qualquer widget de tipo de texto pode ser retribuido utilizando a **API gx_<widget_type>_font_set** fornecida para cada tipo de widget relacionado com texto. Toda a tabela de fontes pode ser reatribuída chamando a **função API gx_display_font_table_set.**

### <a name="scrollbar-appearance"></a>Aparência da barra de pergaminho 

O ECRÃ GUIX também mantém as definições de aparência padrão da barra de deslocação para este visor. Estas definições são definidas pela estrutura **GX_SCROLLBAR_APPEARANCE** que é definida abaixo. O GUIX Display mantém uma estrutura de aparência de barra de deslocação para barras de deslocação verticais e uma segunda estrutura para barras de deslocação horizontais. A aplicação pode modificar a aparência padrão da barra de deslocamento para qualquer visualização, inicializando uma estrutura **GX_SCROLLBAR_APPEARANCE** e invocando a função API ***gx_display_scroll_appearance_set***.

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```
| Membro da Estrutura GX_SCROLLBAR_APPEARANCE | Descrição |
| --- | --- |
| gx_scroll_width | Largura de uma barra de deslocal vertical ou altura de uma barra de deslocação horizontal, em pixels. |
| gx_scroll_thumb_width | Largura do elevador e botões finais, em pixels. |
| gx_scroll_thumb_travel_max | Compensado a partir da extremidade da barra de deslocação para o ponto de viagem máximo do botão do polegar. |
| gx_scroll_fill_pixelmap | Pixelmap usado para preencher fundo de pergaminho. |
| gx_scroll_thumb_pixelmap | Pixelmap usado para desenhar o botão do polegar do deslocal. |
| gx_scroll_up_pixelmap | Pixelmap usado para desenhar o botão de deslocalismo para cima. |
| gx_scroll_down_pixelmap | Pixelmap usado para desenhar o botão de deslocalismo para baixo. |
| gx_scroll_fill_color | ID de cor de cor usado para preencher fundo de barra de pergaminho. |
| gx_scroll_button_color | ID de cor de cor usado para encher botão de polegar da barra de deslocamento. |

Além destas definições predefinidos para fontes, cores e estilos, a aplicação pode especificar qualquer um dos parâmetros caso a caso, conforme pretendido usando API fornecido por cada tipo de widget.

### <a name="skinning-and-themes"></a>Esfolar e Temas

A esfolada permite que os widgets e janelas guix mudem facilmente a sua aparência base, ou seja, mudar a "pele" num só local irá alterar a aparência base de todos os widgets e janelas associados.

A reformulação da sua aplicação GUIX requer que forneça uma nova cor, fonte e mesa pixelmap às tabelas de recursos do GUIX Display. Uma vez que todos os widgets GUIX se referem à sua cor, bitmap ou fonte por ID de recurso, fornecer uma nova tabela de recursos automaticamente faz com que todos os widgets GUIX comecem a usar as suas novas cores e pixelmaps quando se desenham para o ecrã pretendido.

Um novo conjunto de fontes, cores e pixelmaps projetados para trabalhar em conjunto para proporcionar uma aparência atraente é chamado de *tema.* Um tema define um conjunto de tabelas de recursos e o tamanho de cada tabela de recursos. Qualquer número de temas pode ser definido para qualquer ecrã usando a aplicação GUIX Studio. Tem de passar o índice de temática inicial para o GUIX Studio gerado ***gx_studio_display_configure***, que instala o tema inicial no ecrã criado. O tema ativo para qualquer visualização pode ser alterado a qualquer momento, chamando a função ***gx_display_theme_install***.

### <a name="root-window"></a>Janela raiz

Para cada tela visível criada por uma aplicação, a aplicação também deve criar uma Janela raiz para essa tela. Esta janela especial funciona basicamente como um recipiente para todas as janelas e widgets de aplicação de nível superior. A janela raiz desenha o fundo de lona, e uma vez que a janela da raiz é derivada da classe **GX_WINDOW** a janela raiz também pode ter papel de parede. Para alterar a cor de fundo do seu ecrã ou tela, basta alterar a cor de preenchimento da janela de raiz anexada a essa tela.

Se utilizar a função gerada pelo GUIX Studio com o nome ***gx_studio_display_configure*** configurar os seus ecrãs, então a tela e a janela de raiz para cada ecrã são criadas para si como parte desta função de inicialização.

### <a name="anti-aliasing"></a>Anti-Aliasing 

Anti-Aliasing é uma característica opcional no GUIX que é usada para suavizar linhas, curvas e fontes. O anti-aliasing só é suportado quando funciona com um controlador de ecrã utilizando uma profundidade de cor de 16-bpp ou superior.

O desenho de linha anti-aliased é ativado definindo o flash **GX_BRUSH_ALIAS** na escova ativa. Isto aplica-se às linhas traçadas diretamente, bem como às linhas traçadas como a fronteira de um polígono ou círculo.

O desenho de texto anti-aliased é ativado através de uma fonte anti-aliasada que é produzida pela aplicação do estúdio GUIX. Especifica se um tipo de letra deve ser gerado como antialiased ou binário quando cria o tipo de letra.
As fontes anti-aliasadas no GUIX utilizam 16 níveis de transparência para cada pixel.

### <a name="clipping"></a>Recorte 

O clipping é suportado internamente pelo componente de exibição GUIX, e nas camadas de janela e widget pela arquitetura pai-filho mantida por widgets GUIX. Nenhuma janela ou widget é permitido desenhar fora da área do widget, e um widget nunca é permitido desenhar fora da área do pai do widget.

Isto também impede que os widgets desenhem em coordenadas de pixel que se encontrem fora da memória de tela que provavelmente levam à corrupção da memória ou a uma falha do sistema. Os widgets não são permitidos desenhar fora da área do widget, da área principal do widget, ou além da extensão de lona.

Além disso, os widgets só podem atrair para áreas que foram previamente marcadas como sujas. Isto evita que uma janela inteira seja desenhada, por exemplo, quando apenas um canto da janela foi revelado. Apenas a parte da janela que realmente precisa de ser refrescada é marcada como suja, e assim a função de desenho da janela apenas realmente refresca os pixels na área suja.

O componente de visualização GUIX impõe estes algoritmos de recorte antes de invocar as funções de desenho do nível do condutor.

### <a name="views"></a>Vistas 

O GUIX mantém sempre um conjunto de vistas para cada janela de raiz e cada janela da criança da janela raiz. As vistas são uma área de corte dinâmica e determinada em tempo de execução que muda à medida que a posição da janela e a ordem Z são modificadas.
O GUIX usa vistas para evitar que uma janela ou widget no fundo se desenhem em cima de uma janela ou widget em primeiro plano. As vistas impõem a disciplina da ordem Z. Além disso, as vistas são importantes para a eficiência, na medida em que impedem que uma janela em segundo plano se desenhe para qualquer área da tela que não possa ser vista. Se uma janela estiver completamente coberta por outra janela, a janela coberta não será permitida a atrair para a tela, mesmo que esteja a tentar fazê-lo.

### <a name="display-driver-interface"></a>Interface do controlador de exibição 

Os controladores de exibição GUIX são responsáveis por toda a interação com o ecrã físico subjacente. Os controladores do visor têm três funções básicas: inicialização, desenho e visualização do tampão da moldura.
A inicialização é responsável pela preparação do hardware de exibição física, pela informação do GUIX sobre as propriedades do hardware de exibição física e pela informação do GUIX sobre quais as funções específicas de desenho que devem ser utilizadas. A inicialização do controlador de ecrã principal é chamada da função ***GUIX gx_display_create.*** Além disso, a linha GUIX também chamará uma inicialização do controlador de ecrã secundário a partir do contexto do fio. Este controlador de exibição secundário só é necessário se o condutor necessitar de serviços RTOS durante a sua inicialização, por exemplo, o dispositivo interrompe ou ***tx_thread_sleep*** pedidos de atraso entre etapas no processo de inicialização.

Uma vez concluída a inicialização, o controlador do visor é responsável por qualquer desenho direto que possa ser feito no hardware de exibição física.
Finalmente, o controlador de visualização é responsável por exibir o tampão da moldura.

## <a name="guix-widget-component"></a>Componente widget GUIX

Um widget GUIX é um elemento gráfico visível. Existem componentes GUIX que não são visíveis, tais como temporizadores e funções de utilidade matemática.
No entanto, todos os componentes visíveis são derivados do componente básico do widget GUIX. Um widget GUIX é o principal bloco de construção do ecrã GUIX – todos os outros elementos gráficos são derivados da funcionalidade de widget base.

Os widgets GUIX são implementados de forma orientada para objetos com total apoio à herança. Isto é conseguido usando ANSI C, o que resulta nos menores requisitos de memória e processamento possíveis. Quando falamos de um widget específico, como **GX_BUTTON,** sendo *derivado de* outro widget, como a base **GX_WIDGET**, o que queremos dizer é que a estrutura de controlo **GX_BUTTON** contém todas as variáveis e ponteiros de função dos membros de **GX_WIDGET,** com algumas variáveis adicionais específicas para **GX_BUTTON**. O GUIX constrói camadas de widgets desta forma, de modo que os widgets mais complexos são sempre baseados num widget mais simples antes deles. Este modelo hierárquico de derivação facilita a aprendizagem das APIs usadas para modificar parâmetros de widget. Se quiser modificar a cor de um botão, utilize a mesma API que utiliza para modificar a cor de um widget, nomeadamente ***gx_widget_fill_color_set***.

A organização de widgets visíveis é mantida de forma pai-filho usando listas estruturadas de árvores que ligam widgets infantis aos seus pais. As crianças herdam características dos pais, tais como as vistas em que podem desenhar e a tela em que desenham.
Os widgets infantis podem ter os seus próprios widgets infantis, herdando novamente várias características do progenitor. As características de qualquer widget podem ser explicitamente redefinidas através de várias chamadas de API GUIX.

### <a name="widget-creation"></a>Criação widget 

Um objeto widget pode ser criado durante a inicialização ou a qualquer momento durante a execução dos fios de aplicação. Não há limite para o número de objetos widget que podem ser criados por uma aplicação. Também não há limite para o número de crianças que qualquer widget pode ter, dentro dos limites de memória do seu hardware alvo.

Cada tipo de widget tem a sua própria função de criação, como ***gx_button_create** _ ou _*_gx_prompt_create_**. Os três primeiros parâmetros destas funções são sempre os mesmos, nomeadamente um ponteiro para a estrutura de controlo do widget, um ponteiro de cordas para o nome do widget, e um ponteiro para o progenitor do widget. Cada função de criação pode ter qualquer número de parâmetros adicionais dependendo dos requisitos desse tipo de widget específico.

### <a name="widget-control-block"></a>Bloco de Controlo widget 

As características de cada objeto widget encontram-se no seu GX_WIDGET **de** controlo e são definidas em **_gx_api.h_**. A memória necessária para um objeto widget é fornecida pela aplicação e pode ser localizada em qualquer lugar na memória. No entanto, é mais comum fazer o widget object control block uma estrutura global definindo-o fora do âmbito de qualquer função. Se estiver a utilizar o GUIX Studio, os seus blocos de controlo widget podem ser atribuídos estáticamente dentro do seu ficheiro de especificações gerados pelo Studio, ou podem ser atribuídos dinamicamente pela sua aplicação.

### <a name="dynamic-widget-control-block-allocation-and-de-allocation"></a>Alocação e deslocação de blocos de controlo dinâmicos do Widget 

Se estiver a utilizar uma alocação dinâmica do bloco de controlo, terá de definir duas funções que o GUIX utilizará para alocar e libertar a memória necessária para os seus blocos de controlo widget. As suas funções de gestão da memória são transmitidas para o componente do sistema GUIX através da função API ***gx_system_memory_allocator_set.*** Esta função permite-lhe passar dois ponteiros de função para GUIX: o primeiro é um ponteiro para uma função de atribuição de memória, e o segundo é um ponteiro para uma função sem memória. Na maioria das vezes, implementará estas funções usando piscinas de byte ThreadX, mas o design do GUIX permite-lhe implementar uma gestão dinâmica da memória da forma que preferir.

A alocação dinâmica de widget é mais frequentemente utilizada dentro do seu ficheiro de especificações de aplicação gerados pelo Studio, quando seleciona a opção "dynamicly allocated" no campo de propriedades widget studio. No entanto, também pode utilizar a atribuição de blocos de controlo dinâmicos dentro da sua aplicação. Se utilizar a atribuição de blocos de controlo dinâmicos dentro da sua aplicação, deverá invocar a função ***gx_widget_allocate** _ API para alocar o bloco de controlo widget. Em seguida, quando criar o widget, certifique-se de que passa a bandeira de estilo _ *GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** (juntamente com quaisquer outras bandeiras de estilo necessárias) para o widget criar função. Esta bandeira é usada para marcar o widget como sendo atribuído dinamicamente no campo de estado do widget. Quando e se o widget for posteriormente eliminado usando **_gx_widget_delete,_** o GUIX verificará este campo de estado e ligará automaticamente para a função de desatributor de memória para garantir que não existem fugas de memória.

> [!IMPORTANT]
> Um widget criado com um bloco de controlo dinamicamente atribuído deve ser criado com a bandeira de estilo **GX_WIDGET_STYLE_DYNAMICALLY_ALLOCATED** para evitar a perda de memória.

### <a name="types"></a>Tipos

O GUIX fornece um conjunto rico e totalmente funcional de widgets incorporados. Como mencionado anteriormente, todos os widgets especializados são derivados do widget base. Segue-se uma lista dos widgets incorporados no GUIX:

**GX_TYPE_WIDGET**

**GX_TYPE_BUTTON**

**GX_TYPE_TEXT_BUTTON**

**GX_TYPE_MULTI_LINE_TEXT_BUTTON**

**GX_TYPE_RADIO_BUTTON**

**GX_TYPE_CHECKBOX**

**GX_TYPE_PIXELMAP_BUTTON**

**GX_TYPE_ICON_BUTTON**

**GX_TYPE_ICON**

**GX_TYPE_SPRITE**

**GX_TYPE_SLIDER**

**GX_TYPE_PIXELMAP_SLIDER**

**GX_TYPE_VERTICAL_SCROLL**

**GX_TYPE_HORIZONTAL_SCROLL**

**GX_TYPE_PROGRESS_BAR**

**GX_TYPE_PROMPT**

**GX_TYPE_NUMERIC_PROMPT**

**GX_TYPE_PIXELMAP_PROMPT**

**GX_TYPE_NUMERIC_PIXELMAP_PROMPT**

**GX_TYPE_SINGLE_LINE_TEXT_INPUT**

**GX_TYPE_MULTI_LINE_TEXT_VIEW**

**GX_TYPE_MULTI_LINE_TEXT_INPUT**

**GX_TYPE_WINDOW**

**GX_TYPE_ROOT_WINDOW**

**GX_TYPE_VERTICAL_LIST**

**GX_TYPE_HORIZONTAL_LIST**

**GX_TYPE_POPUP_LIST**

**GX_TYPE_DROP_LIST**

**GX_TYPE_LINE_CHART**

**GX_TYPE_DIALOG**

**GX_TYPE_KEYBOARD**

**GX_TYPE_SCROLL_WHEEL**

**GX_TYPE_TEXT_SCROLL_WHEEL**

**GX_TYPE_STRING_SCROLL_WHEEL**

**GX_TYPE_NUMERIC_SCROLL_WHEEL**

**GX_TYPE_CIRCULAR_GAUGE**

**GX_TYPE_RADIAL_PROGRESS_BAR**

**GX_TYPE_RADIAL_SLIDER**

**GX_TYPE_MENU_LIST**

**GX_TYPE_MENU**

**GX_TYPE_ACCORDION_MENU**

**GX_TYPE_TREE_VIEW**


### <a name="styles"></a>Estilos

Os estilos Widget consistem em coisas como propriedades fronteiriças (elevadas, embutidas, finas, grossas ou nenhumas hóspedes) bem como propriedades para tipos de widget específicos, conforme listado anteriormente. As bandeiras de estilo widget oferecem o método mais simples para modificar a aparência de qualquer widget.
O estilo widget inicial é sempre um parâmetro passado para a função de criação específica do tipo widget.

### <a name="colors"></a>Cores 

Os widgets desenham-se usando cores definidas na tabela de cores do sistema.
Os IDs de cor são definidos para fundo de tela, cor de preenchimento de widget padrão, cor de preenchimento de botão, cor de preenchimento de widget de texto, cor de preenchimento de janela e vários outros valores de cor padrão. Além disso, **GX_WINDOW** objetos suportam exibir um mapa ou papel de parede à medida que o cliente da janela está cheio.

O método mais simples de alterar o esquema de cores padrão é usar o GUIX Studio e criar ou definir um esquema de cores que satisfaça os seus requisitos.
Também pode definir manualmente o seu esquema de cores criando uma série de valores GX_COLOR e invocando a função API gx_system_color_table_set.

### <a name="event-notification"></a>Notificação de eventos 

Os eventos GUIX são pedidos feitos a um ou mais widgets para executar uma determinada ação e notificações para notificar widgets de entrada do utilizador e alterações de estado do sistema interno. Por exemplo, quando um widget ganha foco, o **GX_EVENT_FOCUS_GAINED** é enviado para o widget através do serviço ***API gx_system_event_send.***

Os eventos são transmitidos através da fila do evento GUIX, e cada evento é um exemplo da estrutura de dados **GX_EVENT.** A estrutura de dados **GX_EVENT** é definida em ***gx_api.h,*** no entanto, os campos mais importantes da estrutura são os **gx_event_type**, **gx_event_sender,** **gx_event_target** e **gx_event_payload.**

O **campo gx_event_type** é usado para identificar a classe de eventos em particular. O tipo de evento indica se este é, por exemplo, um evento **GX_EVENT_PEN_DOWN** ou um evento **GX_EVENT_TIMER.** O **gx_event_payload** é uma união de vários campos de dados, e nem todos são válidos para todos os tipos de eventos.
Utilize primeiro o campo do tipo de evento, antes de examinar os outros campos de dados do evento.

O campo **gx_event_sender** contém o ID do widget que gerou o evento se o evento for uma notificação de widget infantil.

O **campo gx_event_target** pode ser usado para encaminhar eventos definidos pelo utilizador para uma determinada janela ou widget. Se quiser enviar um evento para uma determinada janela, deve dar à janela um valor de ID único (para que possa ser positivamente identificado), e ao construir o evento coloque o valor de ID da janela no campo **gx_event_target.** Se não conhece o ID do alvo ou se apenas quer que o evento seja encaminhado para o widget que tem foco de entrada, certifique-se de definir o campo **gx_event_target** para 0.

Finalmente, o **campo gx_event_payload** é uma união de vários tipos de dados. Para **eventos GX_EVENT_PEN_DOWN** e **GX_EVENT_PEN_UP,** o campo **gx_event_pointdata** contém a coordenada x,y pixel da posição da caneta. Para eventos temporizadores, o campo **gx_event_timer_id** contém a identificação do temporizador expirado. Outros campos de dados de carga útil são utilizados para outros tipos de eventos. A lista completa dos tipos de eventos pré-definidos e dos seus campos de carga útil é definida no [Apêndice E - DESCRIÇÕES do Evento GUIX](appendix-e.md).

A aplicação também pode adicionar os seus próprios eventos personalizados, começando numericamente após a **GX_FIRST_APP_EVENT** constante. Todos os números de eventos após esta constante são reservados para uso da aplicação. É claro que o manipulador de eventos widget da aplicação deve ter processamento para tais eventos de aplicação.

### <a name="event-processing"></a>Processamento de eventos 

Existe uma função de processamento de eventos widget predefinidos para cada widget, nomeado ***gx_<>_event_process do tipo widget***. Na maioria dos casos, a aplicação não precisará de se preocupar com o tratamento do evento de qualquer widget. No entanto, nas situações em que a aplicação requer processamento personalizado ou suplementar de eventos, a aplicação pode sobrepor-se à função de processamento predefinido através da ***API*** GUIX gx_widget_event_process_set . Esta função substitui a função de processamento de eventos predefinido com a função de processamento da função do evento especificada na API.

> [!IMPORTANT]
> As funções de processamento de eventos de aplicação podem tirar partido (isto é, não duplicar o processamento) do processamento predefinido, simplesmente chamando o processamento ***de gx_widget_event_process*** padrão diretamente.

O processamento de eventos é chamado exclusivamente a partir do contexto do fio interno do sistema GUIX. Desta forma, os requisitos da stack para processar o manuseamento do evento aplicam-se apenas ao fio GUIX.

### <a name="implementing-custom-event-processing-example"></a>Implementação de Processamento personalizado de Eventos (exemplo) 

Pode fornecer a sua própria função de processamento de eventos para qualquer widget ou janela no sistema GUIX. Se estiver a criar o seu próprio tipo de widget personalizado, normalmente instalará o seu manipulador de eventos personalizado na função de criação de widgets. Se estiver apenas a prolongar ou modificar o funcionamento de um widget ou janela existente, pode chamar a função API gx_widget_event_process_set após a criação do widget ou janela. Você irá quase sempre fornecer o seu próprio manuseamento de eventos para as suas janelas de nível superior (também chamado screens) para processar eventos gerados pelos controlos do seu filho. O evento de processamento gerado pelos controlos infantis de um ecrã é a principal forma de adicionar funcionalidade à sua aplicação GUIX.

Como exemplo, suponha que defina um ecrã de alto nível chamado "main_menu".
Este ecrã pode ser definido usando o GUIX Studio, ou pode criar este ecrã no seu código de aplicação. Se definir o ecrã dentro do GUIX Studio, basta escrever o nome do seu manipulador de eventos no campo de propriedades do Studio para esse ecrã, e o código de especificações gerado pelo Estúdio instalará automaticamente o seu manipulador de eventos. Neste caso, chamaremos o manipulador de eventos personalizado ***main_menu_event_handler*** e deve ser codificado assim:

```C
int main_menu_item; /* example: variable to keep track of selected item */

UINT main_menu_event_handler(GX_WINDOW *main_screen, GX_EVENT *event_ptr)
{
    UINT status = GX_SUCCESS;

    switch(event_ptr->gx_event_type)
    {
    /* this is an example for catching events from a child button */
    case GX_SIGNAL(IDB_CHILD_BUTTON, GX_EVENT_CLICKED):
        /* insert your button handler code here */
        break;

    case GX_EVENT_SHOW:
        /* add functionality to the show event handler */
        /* first, do default processing */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */

        /* now add my own processing */
        main_menu_item = 0;
        break;

    default:
        /* pass all other events to base processing function */
        status = gx_window_event_process(main_screen, event_ptr); /* note 1 */
        break;
    }
    return status;
}
```

No exemplo acima, é importante notar que para eventos do sistema como **GX_EVENT_SHOW** (eventos gerados internamente para notificar um widget de uma mudança de estado), a aplicação deve passar esses eventos para a função de processamento de eventos widget base para garantir que o processamento normal ocorre. A aplicação pode então adicionar lógica adicional como desejado. Todos os eventos que não são tratados pela aplicação (o caso padrão acima) também devem ser transmitidos para a função de processamento de eventos base. Uma vez que este exemplo foi para um ecrã de alto nível baseado em **GX_WINDOW,** a função de processamento de eventos padrão é gx_window_event_process.

### <a name="drawing-function"></a>Função de desenho 

Todo o desenho widget é realizado separadamente do manuseamento do evento. Isto é mais eficiente porque o desenho é geralmente caro em termos de ciclos de CPU. Ao implementar um algoritmo de desenho diferido, todos os eventos pendentes e alterações de exibição associadas podem ser concluídos antes de qualquer desenho ser feito, eliminando assim o desenho desperdiçado. Semelhante ao processamento de eventos, existe uma função de desenho de widget padrão para a maioria dos widgets, nomeado ***gx_<>_draw tipo widget***, onde xxx é o tipo widget. Na maioria dos casos, a aplicação não precisará de se preocupar com a função de desenho de qualquer widget dado. No entanto, nas situações em que a aplicação requer desenho personalizado ou suplementar, a aplicação pode sobrepor-se à função de desenho predefinido através da ***API*** GUIX gx_widget_draw_set . Esta função permite que a aplicação forneça a sua própria função de desenho personalizado para qualquer widget. Isto permite ainda que a aplicação defina novos tipos de widgets inteiros.

> [!IMPORTANT]
> As funções de desenho de aplicações podem tirar partido (isto é, não duplicar a codificação) do desenho padrão, chamando-o simplesmente diretamente da função de desenho ultrapassado.

O desenho widget é chamado exclusivamente a partir do contexto do fio interno do sistema GUIX. Desta forma, os requisitos de tempo e pilha para executar o desenho aplicam-se apenas ao fio GUIX.

### <a name="implementing-custom-drawing-example"></a>Implementação de desenho personalizado (exemplo) 

A função de desenho de qualquer widget é referenciada através de um ponteiro de função indireta que é um membro do GX_WIDGET bloco de controlo. Se utilizar o GUIX Studio para definir o seu widget, pode instalar o seu próprio ponteiro de função simplesmente digitando o nome da sua função no parâmetro "Função de Desenho" das propriedades do widget, e o Studio instalará o seu ponteiro de função para si quando o widget for criado. Se criar o widget no seu código de aplicação, deve utilizar a função ***API gx_widget_draw_set*** para instalar a sua função de desenho personalizado após a criação do widget.

Para este exemplo, vamos supor que quer personalizar a aparência de um botão. O botão será muito parecido com um **GX_TEXT_BUTTON**, mas adicionaremos um pequeno mapa verde "LED_ON" na parte média-direita do botão quando o botão é premido, e um pequeno mapa de "LED_OFF" quando o botão não é premido. Queremos criar um botão que se pareça com as ilustrações abaixo.

![Screenshot do botão verde para On.](./media/guix/image4.jpg) botão personalizado "ligado"

![Screenshot do botão vermelho para desligar.](./media/guix/image5.jpg) botão personalizado "off"

Neste caso, escreveríamos uma função de desenho de botões que se parece com o seguinte.

```C
UINT my_button_draw(GX_TEXT_BUTTON *button)
{
    GX_PIXELMAP *map;
    ULONG button_style;
    INT xpos;
    INT ypos;

    /* first, do the normal text button drawing */
    gx_text_button_draw(button);

    /* now add our extra pixelmap */

    gx_widget_style_get(button, &button_style);

    if (button_style & GX_STYLE_BUTTON_PUSHED)
    {
        /* use the ON pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_ON, &map);
    }
    else
    {
        /* use the OFF pixelmap */
        gx_context_pixelmap_get(GX_PIXELMAP_ID_LED_OFF, &map);
    }
    if (map)
    {
        /* draw it 20 pixels in from right edge */
        xpos = button->gx_widget_size.gx_rectangle_right;
        xpos -= map->gx_pixelmap_width + 20;

        /* and draw 10 pixels from the top edge */
        ypos = button->gx_widget_size.gx_rectangle_top + 10;

        /* draw the extra pixelmap on top of the button */
        gx_canvas_pixelmap_draw(xpos, ypos, map);
    }
}
```

## <a name="guix-drawing-context-component"></a>Componente de contexto de desenho GUIX 

O contexto de desenho é criado dinamicamente, em tempo de execução, à medida que o GUIX realiza cada operação de atualização de tela. O contexto de desenho une a tela, o controlador de tela e a escova que estão sendo usadas para executar as operações de desenho atuais.

O contexto de desenho é definido pela estrutura **GX_DRAW_CONTEXT.**
Esta estrutura contém variáveis que definem o recorte e a visão da operação de desenho atual, definem a tela atual e definem o atual controlador de ecrã em uso. A estrutura **GX_DRAW_CONTEXT** também mantém a escova sendo usada para o desenho. A escova de contexto de desenho é o membro com o qual trabalhará diretamente nas suas funções de desenho personalizado. A estrutura da escova é definida como mostrado no código abaixo.

```C
typedef struct GX_BRUSH_STRUCT
{
    GX_PIXELMAP *gx_brush_pixelmap;
    GX_FONT     *gx_brush_font;
    ULONG        gx_brush_line_pattern;
    ULONG        gx_brush_pattern_mask;
    GX_COLOR     gx_brush_fill_color;  
    GX_COLOR     gx_brush_line_color;  
    UINT         gx_brush_style;
    GX_VALUE     gx_brush_width;
    UCHAR        gx_brush_alpha;  
} GX_BRUSH;
```

O campo **gx_brush_pixelmap** define um mapa de pixels para usar para retângulos e enchimentos de polígono. Este membro não é utilizado a menos que o **gx_brush_style** inclua o estilo **GX_BRUSH_PIXELMAP.**

O **membro gx_brush_font** define o tipo de letra utilizado para o desenho de texto.
O **membro gx_brush_line_pattern** define o padrão usado para linhas tracejadas.
O **membro gx_brush_style** é um conjunto de bandeiras de estilo que podem ser OR'd juntos para definir completamente os atributos do pincel. As bandeiras de estilo pincel disponíveis incluem o seguinte.

**GX_BRUSH_OUTLINE**  
**GX_BRUSH_SOLID_FILL**  
**GX_BRUSH_PIXELMAP_FILL**  
**GX_BRUSH_ALIAS**  
**GX_BRUSH_UNDERLINE**  
**GX_BRUSH_ROUND**

O **membro gx_brush_width** define a linha com para desenho de linha, ou a largura do contorno para desenho de forma delineado.

O **membro gx_brush_line_color** define a cor de primeiro plano para o desenho de linha e para o desenho de texto.

O **membro gx_brush_fill_color** define a cor de enchimento sólida utilizada para o enchimento de formas. O componente de contexto GUIX fornece um conjunto de APIs projetados para tornar muito fácil modificar a escova atual dentro do contexto ativo. Estas APIs incluem **gx_context_brush_define**, **gx_context_line_color_set**, **gx_context_fill_color_set**, **gx_context_font_set**, e muitos outros.

O contexto de desenho de um objeto-mãe é herdado pelos objetos crianças. Na verdade, um clone do contexto de desenho dos pais é herdado pelos objetos da criança quando as suas funções de desenho são invocadas. A criança pode modificar o contexto sem afetar o desenho dos pais, mas também pode herdar informações do progenitor, como a cor da escova e o estilo, se desejar.

## <a name="guix-window-component"></a>Componente da janela GUIX 

O componente da janela é responsável por todo o processamento de janelas no GUIX. Uma janela GUIX é fundamentalmente uma área de exibição distinta que pode conter um ou mais widgets infantis. No GUIX, a janela é na verdade apenas uma forma especial do objeto widget fundamental.

As janelas GUIX são implementadas de forma orientada para objetos com total suporte de herança. Isto é conseguido usando ANSI C, o que resulta nos menores requisitos de memória e processamento possíveis.

As janelas GUIX alargam a funcionalidade do widget GUIX, principalmente adicionando suporte para deslocamento horizontal e vertical. Os objetos da janela GUIX podem criar e exibir automaticamente barras de deslocação e responder à entrada da barra de deslocação. Janelas móveis também construíram no manuseamento de eventos para permitir que a janela seja movida ou arrastada com base em eventos de entrada de canetas.
Finalmente, a janela GUIX responde ao foco de entrada recebendo movendo a janela para a frente da ordem Z da janela.

A janela GUIX mantém o conceito de área de *cliente,* que é a parte interna da janela uma vez que as bordas da janela e objetos não clientes, como barras de deslocamento, são removidos da área disponível. Os widgets para crianças da área do cliente são cortados na área do cliente da janela, enquanto crianças não clientes, como barras de deslocação, são autorizadas a desenhar fora da área do cliente, mas ainda são cortadas às dimensões exteriores da janela.

As janelas são mantidas de forma pai-filho, onde as crianças herdam características dos pais. As janelas das crianças podem ter as suas próprias janelas de filhos, herdando novamente várias características do progenitor. As características de qualquer janela podem ser explicitamente redefinidas através de várias chamadas DE API GUIX.

### <a name="window-creation"></a>Criação de janelas 

Um objeto de janela pode ser criado durante a inicialização ou a qualquer momento durante a execução dos fios de aplicação. Não há limite para o número de objetos de janela que podem ser criados por uma aplicação. Também não há limite para o número de crianças que qualquer janela pode ter.

### <a name="window-control-block"></a>Bloco de Controlo de Janelas 

As características de cada objeto de janela encontram-se no seu bloco de controlo **GX_WINDOW** e são definidas em **_gx_api.h_**. A memória necessária para um objeto de janela é fornecida pela aplicação e pode ser localizada em qualquer lugar na memória. No entanto, é mais comum fazer o bloqueio de controlo de objetos de janela uma estrutura global definindo-a fora do âmbito de qualquer função.

### <a name="root-window"></a>Janela raiz 

GUIX requer o que é chamado uma janela de raiz para cada tela. A janela de raiz é sem fronteiras e tem as mesmas dimensões que a tela à qual está ligada. É usado principalmente como um recipiente para todos os widgets e janelas de primeiro nível. A janela raiz é tipicamente criada pela aplicação através da função API ***gx_window_root_create***, pouco depois da criação do ecrã e da tela. Se utilizar a função gerada pelo Estúdio gx_studio_display_configure, o endereço da janela raiz pode ser devolvido no local passado como o último parâmetro para esta função.

Uma janela de raiz não é movevel, e no caso mais simples a janela raiz é do tamanho da tela. A janela raiz de facto desenha o fundo do visor, de modo a alterar a cor de fundo do ecrã ou a exibir papel de parede de fundo, atribuiria uma cor ou papel de parede à janela raiz.

Se uma janela de raiz for móvel, ela move-se não mudando a sua posição sobre a tela como uma janela de criança faria, mas movendo a própria tela.
Esta funcionalidade permite que a janela raiz GUIX aproveite o hardware que suporta vários tampões de quadro com registos de compensação de hardware.

### <a name="background"></a>Fundo 

Os fundos da janela são cores sólidas ou imagens de mapas bitmap. Existe um fundo de janela predefinido ao nível do sistema que fornece o padrão para o conjunto inicial de janelas. É claro que qualquer fundo de janela pode ser alterado através da API GUIX.

Para alterar o fundo de cor sólida de uma janela, utilize a ***API gx_widget_fill_color_set.*** Para atribuir um papel de parede de fundo a uma janela, utilize a ***API gx_window_wallpaper_set.***

### <a name="scrolling"></a>Scrolling 

O GUIX suporta o deslocamento padrão da janela quando a área necessária para visualizar a janela as crianças excedem o tamanho atual da janela – horizontal e/ou verticalmente. Para ativar a deslocação, a aplicação deve criar as barras de deslocamento desejadas e fixá-las à janela.

O componente da janela GUIX fornece uma implementação de deslocamento padrão com base no tamanho da área do cliente da janela e na extensão de todos os widgets infantis. As aplicações também podem fornecer a sua própria implementação e interpretação de scrolling, sobrenunciando a função ***gx_window_scroll_info_get*** para uma determinada janela.

### <a name="event-notification"></a>Notificação de eventos 

A função de processamento de eventos de janela padrão difere do processamento de eventos GX_WIDGET principalmente no manuseamento de eventos de deslocação e dimensionamento. GX_WINDOW forneceu manipuladores defalt para eventos de scrolling e dimensionamento.

A aplicação também pode adicionar os seus próprios eventos personalizados, começando numericamente após a **GX_FIRST_APP_EVENT** constante. Todos os números de eventos após esta constante são reservados para uso da aplicação. É claro que o manipulador de eventos da janela da aplicação deve ter processamento para tais eventos de aplicação.

### <a name="event-processing"></a>Processamento de eventos 

Tal como todos os outros tipos de widgets, existe uma função de processamento de eventos de janela padrão para cada janela, denominada ***gx_window_event_process***. Normalmente, irá substituir esta função de manuseamento de eventos com o seu próprio manipulador de eventos nas janelas que cria. É assim que vai responder aos acontecimentos e tomar medidas com base em eventos gerados pelos controlos da janela infantil.

É importante lembrar que invoca a função ***base gx_window_event_process*** para eventos do sistema GUIX se você anular esse manipulador de eventos, para permitir que o manuseamento de eventos padrão ocorra para além de qualquer ação que você está adicionando ao manipulador de eventos. Por exemplo, se fornecer um manipulador personalizado para o evento **GX_EVENT_SHOW,** e não passar este evento para ***gx_window_event_process,*** a sua janela nunca ficará visível.
Para fornecer um manipulador de eventos personalizado para uma janela, utilize a função ***gx_widget_event_process_set*** para definir o endereço do seu manipulador de eventos. Esta função substitui a função de processamento de eventos predefinido com a função de processamento da função do evento especificada na API.

> [!IMPORTANT]
> As funções de processamento de eventos de aplicação podem tirar partido (isto é, não duplicar o processamento) do processamento predefinido, simplesmente chamando o ***padrão gx_window_event_process*** diretamente.

O processamento de eventos é chamado exclusivamente a partir do contexto do fio interno do sistema GUIX. Desta forma, os requisitos da stack para processar o manuseamento do evento aplicam-se apenas ao fio GUIX.

## <a name="guix-image-reader-component"></a>Componente do leitor de imagem GUIX 

O componente do leitor de imagens fornece utilitários e funções de API para descomprimir imagens comprimidas cruas para o formato DE pixelmap GUIX. Os dados de imagem em bruto do formato JPEG e PNG são suportados, com formatos adicionais reservados para futuras versões.

Note que para a grande maioria das aplicações GUIX, o componente GUIX Image Reader não é necessário. A maioria das aplicações baseia-se na aplicação GUIX Studio para converter os ativos gráficos do formato JPEG e PNG em recursos **de GX_PIXELMAP** compatíveis com GUIX. O componente do leitor de imagem GUIX é utilizado quando os ativos gráficos brutos são conhecidos apenas em tempo de execução, ou quando as restrições de armazenamento do sistema impedem o armazenamento de recursos em **formato GX_PIXELMAP.** Os dados de imagem do formato JPEG e PNG são geralmente mais compactos do que **GX_PIXELMAP** formato, no entanto existe uma sobrecarga considerável de tempo de execução associada à realização de descompressão e conversão de espaço de cores destes tipos de imagem dinamicamente.

Se as imagens JPEG ou PNG em formato bruto forem passadas para a função API gx_canvas_pixelmap_draw, o GUIX descomprimia e desenha os dados JPEG ou PNG. Note que isto terá um impacto negativo significativo na velocidade de desenho do tempo de execução, e a passagem de dados de imagem em formato RAW para a função gx_canvas_pixelmap_draw não é recomendada a menos que esteja a usar um alvo de hardware que suporte a descompressão assistida por hardware JPEG ou PNG.

> [!IMPORTANT]
> Passando imagens em formatos jpeg ou PNG para o gx_canvas_pixelmap_draw API incorre em sobrecarga de tempo de execução significativa para a maioria do hardware alvo.

Como alternativa, os dados brutos do JPEG e do PNG podem ser convertidos para GX_PIXELMAP formato em tempo de execução utilizando o componente Image Reader.
Os Pixelmaps produzidos desta forma podem ser utilizados e desenhados tal como os pixelmaps produzidos pelo Studio e contidos no seu ficheiro de recursos. Isto permite que a sua aplicação execute a descompressão de imagem, dilatação e conversão do espaço de cor uma vez (geralmente durante o arranque do programa) em vez de realizar estas operações cada vez que a imagem é desenhada.

As funções do componente do Leitor de Imagem incluem:

***gx_image_reader_create***  
***gx_image_reader_palette_set***  
***gx_image_reader_start***

## <a name="guix-animation-component"></a>Componente de animação GUIX 

O componente de animação GUIX é um conjunto de funções e serviços utilizados para automatizar automatizações de ecrã e de transição widget. O componente de animação GUIX suporta o desvanecimento, o desvanecimento e as animações do tipo movimento ou de diapositivos de qualquer tipo de widget.

As animações do tipo Fade podem ser suportadas quer variando o valor alfa interno do widget desvanecido (se **GX_BRUSH_ALPHA_SUPPORT** estiver ativado), quer desenhando qualquer coleção de widgets para uma tela de memória separada quando é então misturado com o fundo. Para alvos de hardware que suportam várias camadas de gráficos de hardware, o suporte para efeitos de desvanecimento suave é melhor realizado usando esta abordagem de mistura de lona, muitas vezes com muito pouca largura de banda cpu central necessária. Para alvos de hardware que não suportam várias camadas gráficas, a mistura utilizando o valor alfa da escova GUIX é suportada quando funciona a 16 bpp e profundidades de cor mais altas.

Se uma animação deve utilizar uma tela de desenho separada, o componente de animação GUIX fornece o serviço API gx_animation_canvas_define para o efeito. Outros tipos de animação não requerem uma tela separada, mas irão utilizá-la se estiver disponível. Isto faz o melhor uso possível de qualquer suporte de hardware subjacente para várias superfícies de hardware.

As variáveis que controlam uma animação são definidas por dois blocos de controlo. Primeiro, o **GX_ANIMATION** bloco de controlo que define o controlador de animação. O controlador de animação é o motor de condução que executa a sequência de animação que define. Um único controlador de animação pode ser reutilizada muitas vezes para executar muitas sequências de animação diferentes. Se precisar de executar várias sequências de animação simultaneamente, pode criar múltiplos controladores de animação **GX_ANIMATION.**

O componente do sistema GUIX pode fornecer um bloco reutilizável de estruturas de controlo **GX_ANIMATION,** que pode ser solicitado pela aplicação quando e a animação é necessária e são automaticamente devolvidas ao pool do sistema quando a sequência de animação estiver concluída. Isto liberta a aplicação de definir estáticamente uma estrutura **GX_ANIMATION** para cada animação que possa ser implementada. O tamanho deste conjunto de estruturas **GX_ANIMATION** é definido pela **GX_ANIMATION_POOL_SIZE** constante, que por defeito de 6, o que significa que por padrão 6 animações simultâneas podem ser atribuídas a partir do pool do sistema. Esta constante pode, naturalmente, ser re-definida no ficheiro de cabeçalho gx_user.h é mais animações simultâneas são necessárias. Se **GX_ANIMATION_POOL_SIZE** estiver definido para zero, então o componente do sistema GUIX não fornece um pool de animação ou serviços relacionados.

O segundo bloco de controlo ou estrutura usado para definir uma animação é a estrutura **GX_ANIMATION_INFO.** Esta estrutura é usada para definir uma sequência de animação particular. Você passa esta estrutura de informação para o seu controlador de animação para iniciar uma sequência de animação usando o serviço API gx_animation_start. A estrutura **GX_ANIMATION_INFO** contém os seguintes campos:

```C
typedef struct GX_ANIMATION_INFO_STRUCT
{
    GX_WIDGET *gx_animation_target;
    GX_WIDGET *gx_animation_parent;
    GX_WIDGET *gx_animation_screen_list;
    USHORT gx_animation_style;
    USHORT gx_animation_id;
    USHORT gx_animation_start_delay;
    USHORT gx_animation_frame_interval;
    GX_POINT gx_animation_start_position;
    GX_POINT gx_animation_end_position;
    GX_UBYTE gx_animation_start_alpha;
    GX_UBYTE gx_animation_end_alpha;
    GX_UBYTE gx_animation_steps;
} GX_ANIMATION_INFO;
```

O **membro gx_animation_target** define o widget alvo em que o controlador de animação irá agir.

O **membro gx_animation_parent** define o widget dos pais, se houver, ao qual o widget-alvo será ligado quando a sequência de animação estiver completa. O gx_animation_parent é também o destinatário do evento GX_ANIMATION_COMPLETE que é gerado quando uma animação é concluída.

O **membro gx_animation_screen_list** define uma lista widget para animações de slide de ecrã orientadas por canetas. A lista widge deve ser terminada com GX_NULL ponteiro, e cada widget na lista deve ter as mesmas dimensões x,y que o gx_animation_parent.

O **gx_animation_style** é um bitmask que define o tipo de animação a ser realizado e opções associadas. As bandeiras de estilo de animação incluem o seguinte.

| &nbsp;Bandeira de estilo de &nbsp; animação | Descrição |
| --- | --- |
| GX_ANIMATION_TRANSLATE | Solicite uma animação do tipo slide ou desvaneça. |
| GX_ANIMATION_SCREEN_DRAG | Solicite uma animação de arrasto de tela orientada por canetas. |

As seguintes bandeiras podem ser usadas em combinação com **SCREEN_DRAG** animações do tipo.

| &nbsp;Bandeiras de arrasto &nbsp; de tela | Descrição |
| --- | --- |
| GX_ANIMATION_WRAP | A lista de ecrã deve ser embrulhada de trás para a ponta. |
| GX_ANIMATION_HORIZONTAL | Arrasto de tela permitido na direção horizontal.  |
| GX_ANIMATION_VERTICAL | Arrasto de tela permitido na direção vertical. |

A seguinte bandeira pode ser usada em combinação com animações de tradução.

| Traduzir &nbsp; bandeiras de &nbsp; animações | Descrição |
| --- | --- |
| GX_ANIMATION_DETACH | Retire o alvo de animação do progenitor de animação quando a animação estiver concluída. Se o alvo foi dinamicamente atribuído e criado pelo GUIX Studio gerou manuseamento automatizado de eventos, o alvo será eliminado após a sua desconexão. |
| GX_ANIMATION_TRANSLATE | Os tipos de animação são animações orientadas por temporizadores. A aplicação define a posição inicial e final e o valor alfa inicial e final para o widget alvo, e o gestor de animação cria um temporizador para servir e como a força motriz para executar a animação.
| GX_ANIMATION_SCREEN_DRAG | Difere das animações **DO TRADUZIR** na medida em que este tipo de animação é conduzido por eventos de entrada de canetas. Este tipo de animação acompanha juntamente com a entrada do ecrã tátil para passar o widget do alvo à medida que o utilizador arrasta uma caneta ou estilete através do ecrã tátil de entrada. Para utilizar este tipo de animação, a aplicação deve chamar a **_API gx_animation_drag_enable_** para ativar esta animação. |

O **valor gx_animation_id** é passado para o progenitor de animação no campo event.gx_event_sender do evento **GX_ANIMATION_COMPLETE.** Este valor é usado pelo progenitor de animação para determinar qual das várias animações infantis está reportando conclusão. Este valor pode ser 0, e uma animação com valor de ID 0 não gerará um **evento ANIMATION_COMPLETE.**

O **valor gx_animation_start_delay** é uma contagem de tiquetaque GUIX indicando o número de carraças do temporizador para atrasar após **_gx_animation_start_ _ é chamado antes de executar realmente a *animação. O valor pode ser 0 para iniciar a animação imediatamente após chamar _*_gx_animation_start_**.

O campo **gx_animation_frame_interval** define o número de tiques de temporizador GUIX (um múltiplo da taxa de tique-taque do SO) subjacentes para atrasar entre cada quadro da sequência de animação. O valor mínimo é 1.

O **gx_animation_start_position** define o ponto de partida de cima para a esquerda para o widget alvo para animações de tradução.

O **gx_animation_end_position** define a posição final superior à esquerda para o widget alvo para animações tipo de tradução.

O campo **gx_animation_start_alpha** define o valor alfa de tela inicial para animações tipo de tradução.

O campo **gx_animation_end_alpha** define o valor alfa de tela final para animações tipo de tradução.

O campo **gx_animation_steps** define quantos passos ou quadros o controlador deve executar para animações de tradução. Um maior número de passos produz um slide mais suave e/ou aparência desvanecimento, mas também requer maior largura de banda do sistema.

Para implementar efeitos de animação na sua aplicação, tem primeiro de ligar ***para gx_animation_create*** para rubricar o seu controlador de animação. Se a sua animação estiver a utilizar uma tela secundária, inicialize esta tela chamando gx_animation_canvas_define. Em seguida, deve rubricar a estrutura **GX_ANIMATION_INFO** para definir o tipo específico de animação a realizar e os outros parâmetros de animação. Finalmente, ligue gx_animation_start para desencadear a sequência de animação.

Quando o controlador de animação completa uma sequência de animação, envia um evento **GX_ANIMATION_COMPLETE** para o widget dos pais, permitindo que qualquer limpeza desejada da tela de animação seja feita nessa altura.

## <a name="guix-utility-component"></a>Componente de utilitário GUIX 

O componente de utilidade é responsável por todas as funções de utilidade comum no GUIX. Estas são funções comuns que são utilidades úteis e podem ser invocadas de qualquer lugar na aplicação ou no código GUIX interno. As funções do componente de utilidade incluem as seguintes.

***gx_utility_canvas_to_bmp***

***gx_utility_circle_point_get***

***gx_utility_alphamap_create***

***gx_utility_gradient_create***

***gx_utility_gradient_delete***

***gx_utlity_ltoa***

***gx_utility_math_acos***

***gx_utility_math_asin***

***gx_utility_math_cos***

***gx_utility_math_sin***

***gx_utility_math_sqrt***

***gx_utility_pixelmap_resize***

***gx_utility_pixelmap_rotate***

***gx_utility_pixelmap_simple_rotate***

***gx_utility_rectangle_center***

***gx_utility_rectangle_center_find***

***gx_utility_rectangle_combine***

***gx_utility_rectangle_compare***

***gx_utility_rectangle_define***

***gx_utility_rectangle_overlap_detect***

***gx_utility_rectangle_point_detect***

***gx_utility_rectangle_resize***

***gx_utility_rectangle_shift***

***gx_utility_string_to_alphamap***
