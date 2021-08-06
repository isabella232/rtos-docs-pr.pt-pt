---
title: Apêndice H - GUIX Build-Time Bandeiras de configuração
description: Saiba mais sobre as bandeiras de configuração do tempo de construção DO GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2b48491e3c601aeb68ecef00fd0f25d93cda6e64
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115177767"
---
# <a name="appendix-h---guix-build-time-configuration-flags"></a>Apêndice H - GUIX Build-Time Bandeiras de configuração

O GUIX suporta várias opções de compilação condicional e valores de configuração. A definição predefinitiva destes valores de condicional e configuração pode ser ultrapassada, definindo o valor, quer no ficheiro de cabeçalho gx_user.h, quer na linha de comando do compilador.

**GX_DISABLE_THREADX_BINDING**
- Padrão: Indefinido
- Descrição: Esta condicional pode ser utilizada para desativar a ligação RTOS padrão ThreadX. Se pretender executar o GUIX com um RTOS diferente da ThreadX, deve #define GX_DISABLE_THREADX_BINDING e fornecer os seus próprios serviços de ligação RTOS.

GX_SYSTEM_TIMER_MS
- Predefinição: 20
- Descrição: Este valor define o intervalo ou precisão do temporizador GUIX pretendido.

TX_TIMER_TICKS_PER_SECOND
- Predefinição: 100
- Descrição: Este valor define o número de frequências de interrupção do temporizador TX. Uma vez que o temporizador de intervalo threadx predefinido é de 10 ms, este valor desresídeo para uma frequência de 100-Hz.

GX_DISABLE_MULTITHREAD_SUPPORT
- Padrão: Não definido
- Descrição: Esta compilação condicionada pode ser usada para desativar o suporte da API GUIX para múltiplos fios invocando a API GUIX simultaneamente. Se apenas um fio de aplicação utilizar a API GUIX, deverá definir esta bandeira para reduzir a sobrecarga do sistema associada à proteção de secções de código críticas.

GX_DISABLE_UTF8_SUPPORT
- Padrão: Não Definido.
- Descrição: Esta compilação condicionada pode ser usada para remover o suporte interno GUIX para codificação de cordas de formato UTF8. Se estiver a utilizar apenas os valores de caracteres M-0xff na sua aplicação, ligar este #define reduzirá o tamanho do código e a sobrecarga associada ao suporte da codificação de cadeias de formato UTF8.

GX_DISABLE_ARC_DRAWING_SUPPORT
- Padrão: Não definido.
- Descrição: Este condicional pode ser usado para reduzir o tamanho do código da biblioteca GUIX e GX_DISPLAY tamanho da estrutura, removendo o suporte para o círculo, arco, tarte e elipse das funções de desenho de arco. Estas funções não são exigidas pelo conjunto de widgets GUIX predefinido.

GX_DISABLE_SOFTWARE_DECODER_SUPPORT
- Padrão: Não definido.
- Descrição: Este condicional pode ser definido para remover o suporte de descodificador de software da biblioteca GUIX. Se a sua aplicação não necessitar de descodificar o tempo de funcionamento dos ficheiros JPG ou PNG, o que significa que a sua aplicação não utiliza pixelmaps de formato RAW produzidos pelo Studio e não lê ficheiros de imagem de um sistema de ficheiros externos, pode ligar esta #define para reduzir a pegada da biblioteca GUIX.

GX_DISABLE_BINARY_RESOURCE_SUPPORT
- Padrão: Não definido
- Descrição: Este condicional pode ser utilizado para remover o suporte da biblioteca GUIX para o carregamento de dados de recursos binários. Os recursos binários podem ser utilizados para fazer a ligação de tempo de execução dos dados de recursos com a sua aplicação GUIX. Se estiver a utilizar apenas ficheiros de recursos de código fonte C, pode definir este condicional para reduzir a sua pegada de biblioteca GUIX.

GX_DISABLE_BRUSH_ALPHA_SUPPORT
- Padrão: Não definido.
- Descrição: Ao correr a 16 bpp e profundidades de cor mais altas, o GUIX suporta opcionalmente o desenho de gráficos não-arco, pixelmaps e tipos de letra com um valor alfa definido pela escova de contexto de desenho. O suporte a este modo de desenho introduz um pequeno aumento de sobrecarga e pegada da biblioteca, que pode ser eliminado definindo esta bandeira se não necessitar de suporte de desenho de mistura alfa. Note que os pixelmaps com canal alfa, fontes anti-aliased e outros modos de desenho anti-aliasing ainda são suportados independentemente desta definição condicional.

GX_DISABLE_THREADX_TIMER_SOURCE
- Padrão: Não definido.
- Descrição: Esta condição pode ser utilizada para desativar a fonte do temporizador ThreadX. Deve defini GX_DISABLE_THREADX_TIMER_SOURCE se pretender utilizar uma fonte de temporizador diferente.

GX_REPEAT_BUTTON_INITIAL_TICS
- Padrão: 10.
- Descrição: Se um botão tiver GX_STYLE_BUTTON_REPEAT de estilo, este valor define quanto tempo o botão espera antes de começar a enviar eventos repetidos GX_EVENT_CLICKED.

GX_MAX_QUEUE_EVENTS
- Predefinição: 48.
- Descrição: Define o tamanho da fila do evento GUIX em unidades de entradas de estrutura de eventos. Se a fila do evento transbordar, os eventos que são empurrados para a fila são descartados e GX_SYSTEM_ERROR é devolvido pela função gx_system_event_send().

GX_MAX_DIRTY_AREAS
- Padrão: 64.
- Descrição: Define o número máximo de entradas de listas sujas únicas que podem ser mantidas por uma tela. Quando a lista suja transbordar, o GUIX não conseguirá marcar a janela da raiz de lona como suja, o que é menos eficiente do que desenhar widgets individuais para crianças.

GX_MAX_CONTEXT_NESTING
- Predefinição: 8.
- Descrição: Define o nidificação máximo da pilha de contexto de desenho. Isto equivale ao nidificação máximo de widgets pai/filho/criança dentro da definição de UI.

GX_MAX_INPUT_CAPTURE_NESTING
- Predefinição: 4.
- Descrição: Define o tamanho da pilha utilizada para manter a lista de widgets que capturaram a entrada do utilizador (rato e teclado).

GX_SYSTEM_THREAD_PRIORITY
- Padrão: 16.
- Descrição: Define a prioridade do fio GUIX criado durante gx_system_initialize().

GX_SYSTEM_THREAD_TIMESLICE
- Padrão: 10.
- Descrição: Define o tempolice de fio GUIX em termos de carraças do temporizador RTOS. Se outros fios forem definidos com a mesma prioridade que o fio GUIX, este valor determina a frequência com que esses fios concorrentes recebem controlo CPU.

GX_CURSOR_BLINK_INTERVAL
- Padrão: 20.
- Descrição: Define a velocidade a que o cursor de entrada pisca para os widgets de entrada de texto. Este valor é em termos de tiques de temporizador GUIX, que por padrão é definido como 50 ms, pelo que um valor de 20 indica que o cursor de entrada pisca uma vez por segundo.

GX_MULTI_LINE_INDEX_CACHE_SIZE
- Predefinição: 32.
- Descrição: Define o tamanho da cache do índice de arranque de lista mantido pela visão de texto multi-linha e widgets de entrada de texto multi-line. Esta cache é usada para realizar um deslocamento vertical rápido de widgets de texto de várias linhas. Para um melhor desempenho, o tamanho da cache deve ser definido mais do que o número de linhas visíveis do maior widget de texto multi-linha definido pela aplicação. Por exemplo, se as linhas mais visíveis para qualquer widget de texto forem de 20 linhas, a aplicação pode definir um tamanho de cache de 32 (o padrão), o que permite que o GUIX percorra verticalmente sem recalcular todos os índices de início de linha.

GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES
- Predefinição: 4.
- Descrição: O bloco de controlo do botão de texto multi-linha mantém um ponteiro para cada linha de texto a visualizar pelo botão. Este valor determina o número de ponteiros de texto necessários pelo pior dos casos do botão de texto multi-linha.

GX_POLYGON_MAX_EDGE_NUM
- Padrão: 10.
- Descrição: Este valor determina o polígono mais complexo que pode ser desenhado pelo GUIX. O algoritmo de desenho do polígono determina as linhas necessárias para definir as bordas do polígono, e esta definição define o número máximo de bordas que podem ser suportadas.

GX_NUMERIC_SCROLL_WHEEL_STRING_BUFFER_SIZE
- Padrão: 16.
- Descrição: Para uma roda de deslocação numéria, o widget da roda de deslocação converte valores inteiros em cordas ascii. Este valor determina o comprimento máximo da cadeia necessária para exibir os valores inteiros atribuídos.

GX_DEFAULT_CIRCULAR_GAUGE_ANIMATION_DELAY
- Predefinição: 5.
- Descrição: Define o número de carraças do temporizador GUIX (50 ms) entre atualizações de um calibre circular configurado para animar o movimento da agulha entre a posição angular última e atual.

GX_NUMERIC_PROMPT_BUFFER_SIZE
- Padrão: 16.
- Descrição: Um pedido numérico atribui um tampão para converter um valor inteiro atribuído à solicitação a uma cadeia ascii. Esta definição define o tamanho deste tampão de caracteres.

GX_ANIMATION_POOL_SIZE
- Predefinição: 6.
- Descrição: GUIX define um conjunto de animação a partir do qual as estruturas de informação de animação podem ser atribuídas e devolvidas dinamicamente, utilizando gx_system_animation_get e gx_system_animation_free() APIs. Esta definição define o tamanho deste conjunto de blocos de controlo de animação.

GX_MOUSE_SUPPORT
- Padrão: Não definido.
- Descrição: Esta definição permite o suporte para a entrada do rato. O rato de software requer que o controlador de visualização desenhe e rastree o cursor do rato, o que adiciona uma sobrecarga extra ao controlador de visualização. Esta definição só deve ser definida quando um rato (e não um ecrã tátil) deve ser suportado.

GX_HARDWARE_MOUSE_SUPPORT
- Padrão: Não definido.
- Descrição: Quando esta definição é definida, o controlador de visor GUIX utiliza suporte de desenho do cursor do rato de hardware. Isto reduz a memória necessária para capturar a memória de lona por baixo do cursor do rato e melhora o desempenho do sistema para que os alvos de hardware suportem uma camada gráfica sobreposta de rato.

GX_FONT_KERNING_SUPPORT
- Padrão: Não definido.
- Descrição: Esta definição pode ser definida para permitir o suporte de kerning de fonte. O kerning da fonte melhora o espaçamento do glifo para certas combinações de glifos. Este suporte adiciona uma pequena quantidade de sobrecarga às funções de desenho de cadeias de execução, e também adiciona uma pequena quantidade de tamanho às estruturas de dados de fonte.

GX_WIDGET_USER_DATA
- Padrão: Não definido.
- Descrição: Se definido, isto adiciona um campo de dados definido pelo utilizador ao bloco de controlo GX_WIDGET. Este campo de dados pode ser atribuído usando a vista de propriedades dentro do GUIX Studio. Este campo de dados é ignorado internamente pelo GUIX, mas pode ser utilizado pelo software de aplicações para muitos fins.

GUIX_5_4_0_COMPATIBILITY
- Padrão: Não definido.
- Descrição: Certas APIs gui foram modificadas após o lançamento 5.4.0 para adicionar suporte para cores de texto desativadas e para melhorar a precisão de certas funções matemáticas utilizando parâmetros de correspondência de ponto fixo. Estas alterações tornam as versões da biblioteca GUIX incompatíveis com as versões anteriores. No entanto, ao ligar esta #define, a biblioteca pode ser construída de modo a que as APIs sejam totalmente compatíveis com as versões <= 5.4.0, o que significa que não são necessárias alterações nas aplicações existentes para compilar com a mais recente versão da biblioteca GUIX.

GX_MAX_STRING_LENGTH
- Padrão: 102400
- Descrição: Define o comprimento máximo de uma corda, que é usada para testar cordas inválidas. Se a cadeia de entrada exceder o comprimento máximo da corda, será considerada inválida.