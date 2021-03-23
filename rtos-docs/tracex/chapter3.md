---
title: Capítulo 3 - Descrição do Azure RTOS TraceX
description: Este capítulo descreve a funcionalidade geral da ferramenta de análise do sistema Azure RTOS TraceX, incluindo a funcionalidade geral do seu GUI.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 1c974b353c92e0a3cf51c92818794197cf999582
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827625"
---
# <a name="chapter-3---description-of-azure-rtos-tracex"></a>Capítulo 3 - Descrição do Azure RTOS TraceX

Este capítulo descreve a funcionalidade geral da ferramenta de análise do sistema Azure RTOS TraceX, incluindo a funcionalidade geral do seu GUI. 

## <a name="display-overview"></a>Visão geral do ecrã

**A figura 4** mostra a janela de visualização principal da ferramenta de análise do sistema TraceX. O layout é simples — os contextos de execução são representados pelos elementos verticais do lado esquerdo; por exemplo, inicialização, interrupção, inatividade e as várias entradas de rosca. Os eventos que ocorrem em cada contexto são exibidos horizontalmente na mesma linha de contexto. Por exemplo, os eventos **QR** mostrados abaixo mostram que **_o fio 2_*_ está a fazer chamadas sucessivas para _*_tx_queue_receive_**.

![Screenshot da janela de visualização principal da ferramenta de análise do sistema TraceX.](./media/user-guide/screen_shot_10.png)


**FIGURA 5**

As alterações de contexto são representadas pelas linhas pretas verticais que ligam as linhas de contexto. O evento atualmente selecionado é representado por uma linha vertical vermelha sólida. Neste exemplo, o evento 494 é selecionado.

## <a name="title-bar"></a>Barra de Título

A barra de título TraceX fornece várias informações úteis. Primeiro é a versão atual do TraceX. Em segundo lugar, o caminho completo do arquivo de vestígios atualmente aberto. O exemplo na **Figura 6** mostra a versão **_TraceX_*_ _*_6.0.0_ _ está a exibir o ficheiro *de traços _*_demo_threadx.trx._**

![Screenshot da barra de título TraceX.](./media/user-guide/screen_shot_11.png)

**FIGURA 6**

## <a name="tool-bar"></a>Barra de Ferramentas

A barra de ferramentas TraceX fornece vários botões para abrir ficheiros de traços e elementos de controlo do seu ecrã.

![Screenshot da barra de ferramentas TraceX.](./media/user-guide/screen_shot_12.png)


**FIGURA 7**

Os botões de barra de ferramentas TraceX - da esquerda para a direita - são definidos da seguinte forma:
                                             
| **Botão**                         | **Function** |
| ---------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![Abra o botão de arquivo de traços](./media/user-guide/screen_shot_13.png)      | Abra um arquivo de vestígios |
| ![Abrir o botão do guia do utilizador](./media/user-guide/screen_shot_14.png)      | Abra este Guia do Utilizador |
| ![Gerar botão de perfil de execução](./media/user-guide/screen_shot_15.png)       | Gerar perfil de execução |
| ![ Gerar botão de estatísticas de desempenho](./media/user-guide/screen_shot_16.png)       | Gerar estatísticas de desempenho |
| ![Gerei o botão de utilização da Pilha de Fio](./media/user-guide/screen_shot_17.png)       | Gerar utilização de Thread Stack |
| ![Mostrar botão de evento selecionado](./media/user-guide/screen_shot_18.png)       | Display evento atualmente selecionado |
| ![Botão Procurar](./media/user-guide/screen_shot_19.png)      | Pesquisa de eventos |
| ![Zoom no botão](./media/user-guide/screen_shot_20.png)      | Aproxime-se. |
| ![Botão de zoom de exibição](./media/user-guide/screen_shot_21.png)      | Selecione percentagem de zoom do visor, onde 100% significa que todo o ficheiro de traços é apresentado dentro da vista atual. |
| ![Botão de zoom para fora](./media/user-guide/screen_shot_22.png)      | Zoom para fora. |
| ![Selecione o primeiro botão de evento](./media/user-guide/screen_shot_23.png)      | Selecione o primeiro evento. |
| ![Mostrar botão de página de evento anterior](./media/user-guide/screen_shot_24.png)      | Mostrar a página do evento anterior. |
| ![Mostrar botão de evento anterior](./media/user-guide/screen_shot_25.png)      | Exibir evento anterior. |
| ![Botão de navegação seguinte/anterior](./media/user-guide/screen_shot_26.png)      | Determinar como funcionam os seguintes/anteriores botões de navegação. Se ***Evento** _ for selecionado, a navegação é feita no evento seguinte/anterior. Se _*_o Contexto_*_ for selecionado, a navegação é feita no evento seguinte/anterior no contexto especificado. Se _*_o Objeto_*_ for selecionado, a navegação é feita no próximo/anterior evento do objeto especificado; por exemplo, eventos associados a uma fila específica. Se os Switches forem _*_selecionados,_*_ a navegação é feita na próxima/anterior alteração de contexto. Se _ *_ID_** for selecionado, a navegação é feita no evento seguinte/anterior do ID do evento especificado. |
| ![Mostrar o próximo botão de evento](./media/user-guide/screen_shot_27.png)      | Exibir o próximo evento. |
| ![Mostrar o próximo botão da página do evento](./media/user-guide/screen_shot_28.png)      | Mostrar a próxima página do evento. |
| ![Selecione o último botão de evento](./media/user-guide/screen_shot_29.png)      | Selecione o último evento. |

## <a name="display-mode-tabs"></a>Separadores do modo de exibição

O TraceX exibe eventos do sistema de duas maneiras diferentes: *sequencial* e *relativo temporal*. O modo predefinido é sequencial e é esse o modo indicado na **Figura 8**.

Mudar o modo é tão simples como selecionar os separadores ***Sequencial** _ ou _*_Time View_*_ na janela TraceX. _*A figura 8** mostra a *_* Vista Sequencial_*_ e _ *_Pontos de Visualização do Tempo_**

![Screenshot dos separadores Sequenciais View e Time View.](./media/user-guide/screen_shot_30.png)

**FIGURA 8**

## <a name="sequential-view-mode"></a>Modo de visualização sequencial

O modo de visualização sequencial é selecionado pelo separador ***Sequencial Ver** _ mostrado em _*Figura 8**. Este é o modo predefinido. Neste modo, os eventos são mostrados im.. /mediativamente a seguirem-se mutuamente, independentemente do tempo decorrido entre eles. Note também a régua acima da área de visualização na **Figura 8**. Mostra o número relativo do evento desde o início do rastreio.

Este modo é o modo padrão e é útil para obter uma boa visão geral do que se passa no sistema.

## <a name="time-view-mode"></a>Modo de visualização do tempo

O modo de visualização do tempo é selecionado pelo botão ***Time View** _ . _ *Figura 9** mostra o mesmo traço de evento **que a Figura 8,** exceto no modo de visualização do tempo. Neste modo, os eventos são mostrados de forma relativa, com a barra verde sólida sendo usada para mostrar execução entre eventos. Este modo é útil para ver onde a maior parte do processamento está a ocorrer no sistema, o que pode ajudar os desenvolvedores a afinar o seu sistema para um maior desempenho e/ou capacidade de resposta.

![Screenshot do separador Time View.](./media/user-guide/screen_shot_31.png)

**FIGURA 9**

Note também a régua acima do display do evento na **Figura 9**. Esta régua mostra carrapatos relativos desde o início do traço, derivado do carimbo de tempo instrumentado no caso de vestígios de registo no interior de ThreadX. Se os carimbos de tempo estiverem demasiado próximos (temporizador de baixa frequência), os eventos serão executados em conjunto. Inversamente, se os carimbos de tempo estiverem demasiado distantes (temporizador de alta frequência), os eventos serão demasiado distantes. Escolher o carimbo de hora de frequência certo é uma consideração importante para tornar significativa a visão relativa do tempo.

## <a name="system-summary-line"></a>Linha Resumo do Sistema

O TraceX também fornece uma única linha de resumo (o contexto superior na **Figura 10**) que inclui todos os eventos na mesma linha. Isto torna fácil ver uma visão geral de um sistema complexo. A barra de resumo é especialmente benéfica em sistemas que têm muitos fios. Sem uma linha tão resumida, teria de seguir interações complexas do sistema utilizando a barra de deslocação vertical para seguir o contexto de execução.

![Screenshot da Linha Sumária do Sistema no separador Visualização Sequencial.](./media/user-guide/screen_shot_32.png)


**FIGURA 10**

A linha de resumo contém um resumo do contexto, bem como o resumo do evento correspondente por baixo. No exemplo mostrado na **Figura 10,** é fácil ver que o **_fio 2_*_ está a executar e a ser interrompido. A interrupção resulta em preempção por _*_thread 3_**, ***thread 6** _, _*_thread 4_*_, e _*_thread 7_*_, after which _ *_thread 2_** retoma a execução.

## <a name="system-contexts"></a>Contextos do sistema

O TraceX lista os contextos do sistema no lado esquerdo do visor, como mostra a **Figura 11**. Os eventos que ocorrem num determinado contexto são exibidos na linha horizontal à direita desse contexto. Desta forma, você pode facilmente verificar que contexto o evento ocorreu, bem como seguir essa linha de contexto para ver todos os eventos que ocorreram em um determinado contexto.

As primeiras entradas de contexto de reboque são sempre os contextos ***Interrupção** _ e _*_Initialize/Idle._*_ _*_O_*_ contexto de interrupção representa todos os eventos do sistema feitos a partir de Rotinas de Serviço de Interrupção (IRS). O contexto _*_inicializado/inativo_*_ representa dois contextos na ThreadX. Os eventos que ocorrem durante _*_tx_application_define,_*_ são o contexto _*_Inicialize/Idle._*_ Se o sistema estiver inativo e, portanto, não ocorrerem eventos, a barra verde que representa _*_a execução_*_ na vista do tempo é desenhada no contexto _ *_Initialize/Idle*_*

![Screenshot dos contextos do sistema no lado esquerdo do visor.](./media/user-guide/screen_shot_33.png)

**FIGURA 11**

No exemplo da **Figura 11,** existem nove contextos de linha, a partir do contexto **_System Timer Thread_*_. Informações adicionais sobre um contexto individual estão disponíveis colocando o rato nesse contexto. As informações adicionais incluem o endereço inicial da pilha do fio, endereço de pilha final, tamanho total, por cento usado, percentagem de execução relativa, número de suspensão, retomas, e sua maior e menor prioridade durante o rastreio. _* Figura 12** mostra informações para **_o fio 0_**.

![Screenshot da informação para o fio 0.](./media/user-guide/screen_shot_34.png)


**FIGURA 12**

Os contextos podem também ser movidos para agrupar os de maior interesse. Isto é conseguido arrastando e largando o contexto ou clicando à direita no contexto. Clicar à direita no contexto produz um diálogo para mover o contexto para cima ou para baixo. 

Selecionando ***Mova-se para** o topo _ resulta no contexto do _*_thread 3_*_ sendo movido para o topo da lista de contexto, como mostrado em _*Figura 13**.

![Screenshot do contexto sendo movido para o topo da lista de contexto.](./media/user-guide/screen_shot_35.png)


**FIGURA 13**

## <a name="thread-status-information"></a>Informações sobre o estado do fio

Quando ativado, o TraceX exibe o estado de cada fio através de uma linha colorida no contexto do fio. Uma linha verde indica que o fio está num estado "pronto", enquanto uma linha de qualquer outra cor indica que o fio está suspenso. Para fios suspensos, a cor da linha indica o tipo de objeto ThreadX em que o fio está suspenso. Por exemplo, na **Figura 13,** a linha verde no contexto _ do sistema **_Timer Thread_ a partir do evento *147 mostra que o _* Thread do _Temporizador do Sistema_ _ está *pronto. Antes do evento 147 e depois do evento 154, a ausência da linha verde indica que o _* Thread de _temporizador do sistema_ _ está *pronto. Antes do evento 147 e depois do evento 154, a ausência da linha verde indica que o _* Thread do _temporizador do sistema_** está suspenso.

![Screenshot do estado de cada fio através de uma linha colorida no contexto do fio.](./media/user-guide/screen_shot_36.png)

**FIGURA 14**

Existem três modos de visualização do estado do fio, disponíveis através do menu ***Opções -> Status Lines** _ . A opção _*_Ready Only_*_ apenas mostra as linhas de estado prontas (verdes), mas não apresenta quaisquer linhas de estado de suspensão. Esta é a opção padrão para TraceX. A opção _ *_All On_** permite a visualização de todas as linhas de estado (prontas e suspensas).

Finalmente, a opção ***All Off*** desativa a exibição de todas as linhas de estado.

## <a name="event-information-display"></a>Display de informação do evento

A TraceX fornece informações detalhadas sobre cerca de 600 eventos em tempo de execução, incluindo threadX, FileX, NetX, NetX Duo e USBX API e eventos internos. O TraceX também suporta mais 61.439 eventos exclusivos definidos pelo utilizador.

Independentemente de ser selecionado o modo de exibição sequencial ou de visualização do tempo, uma vitrina em qualquer evento na área de visualização resulta em informações detalhadas do evento apresentadas perto do evento. O rato-over do evento 143 na demonstração ***demo_threadx.trx** _ trace file é mostrado em _*Figura 15**:

![Screenshot do rato-over do evento 143 em um arquivo de traço de amostra](./media/user-guide/screen_shot_37.png)

**FIGURA 15**

Cada evento apresentado contém informações padrão sobre ***Contexto** _ e tanto o _*_tempo relativo_*_ como o _*_carimbo de tempo._*_ O campo Contexto mostra em que contexto o evento teve lugar. Há exatamente quatro contextos: linha, ocioso, ISR e inicialização. Quando um evento ocorre num contexto de linha, o nome do fio e a sua prioridade nessa altura são recolhidos e exibidos como mostrado acima. O _*_tempo relativo_*_ mostra o número relativo de carraças do temporizador desde o início do rastreio. O _ *_Raw Time Stamp_** exibe a fonte de tempo bruto do evento. Finalmente, todas as informações específicas do evento são apresentadas. Estas informações são detalhadas ao longo do resto deste capítulo.

Informações detalhadas sobre o evento também estão disponíveis clicando duas vezes em qualquer evento. O duplo clique no evento 143 é mostrado na **Figura 16**:

![Screenshot das informações detalhadas do evento quando um evento é clicado duas vezes.](./media/user-guide/screen_shot_38.png)

**FIGURA 16**

Ser capaz de ver vários eventos ao mesmo tempo dá ao utilizador uma visão muito mais rica do que aconteceu. Vê-los lado a lado é bastante útil, uma vez que muitos eventos estão interligados. Isto é conseguido clicando duas vezes em vários eventos.

## <a name="current-event-display"></a>Exibição atual do evento

O TraceX exibe o evento atual — numa janela separada — quando selecionado pelo utilizador via ***View -> Current Event*** ou clicando no botão de evento atual na barra de ferramentas. Depois de selecionado, o TraceX exibe o evento atualmente selecionado numa janela autónoma e atualiza esta janela sempre que for selecionado outro evento.

## <a name="event-searching"></a>Pesquisa de eventos

O TraceX fornece uma extensa capacidade de pesquisa de eventos. O ID do evento e os campos de informação de cada evento são os parâmetros de pesquisa primários. Não especificar um valor para um parâmetro de pesquisa indica que o parâmetro remove eficazmente esse parâmetro da pesquisa. Além disso, a pesquisa pode ser feita de modo que qualquer parâmetro encontrado satisfaça a pesquisa ou todos os parâmetros devem ser encontrados para satisfazer a pesquisa. A pesquisa também pode ser restrita a um determinado contexto ou abranger todos os contextos do vestígio. A invocação da procura do evento é feita selecionando o botão ***Search by Value** _ na barra de ferramentas, como mostrado em _*Figura 17**. Quando selecionado, é apresentado o diálogo de pesquisa, que especifica todos os parâmetros para a pesquisa. Os **_ botões * Next and _*_Previous_*_ no diálogo de pesquisa podem então ser utilizados para encontrar os eventos seguintes e anteriores que correspondam aos critérios de pesquisa especificados. _ *Figura 17** mostra o diálogo de pesquisa.

![Screenshot da pesquisa do evento.](./media/user-guide/screen_shot_39.png)

**FIGURA 17**

![Screenshot do diálogo de pesquisa.](./media/user-guide/screen_shot_40.png)

**FIGURA 18**

## <a name="zooming-in-and-out"></a>Zooming Dentro e Fora

Por predefinição, a TraceX exibe os eventos no seu tamanho completo. Pode ampliar ou ampliar conforme desejado. Fazer zoom out é útil para ver os eventos globais capturados no vestígio, enquanto o zoom in é útil em condições em que os eventos se sobrepõem devido à resolução da fonte de selo de tempo. **A figura 19** mostra o ficheiro **_demo_threadx.trx_** ampliado para fora de modo a que 100% do ficheiro de rastreio seja mostrado.

![Screenshot de um ficheiro de amostra ampliado para que 100% do ficheiro de rastreio seja mostrado.](./media/user-guide/screen_shot_41.png)

**FIGURA 19**

Quando ampliado a 100% para mostrar todo o traço dentro da página de exibição atual, é fácil ver toda a execução de contexto capturada no traço, bem como os eventos gerais que ocorrem nesses contextos. Note na **Figura 16** que **_o fio 1_*_ e _*_thread 2_** executam com mais frequência. A coloração azul para os seus eventos também sugere que estes fios estão a fazer chamadas de serviço de fila (os eventos de fila são de cor azul).

Restaurar uma visão completa do ícone é igualmente fácil; O botão de zoom-in pode ser selecionado repetidamente ou pode ser introduzido algum fator de 100.

## <a name="delta-ticks-between-events"></a>Delta Ticks entre eventos

Determinar o número de tiques entre vários eventos no TraceX é fácil - clique no evento inicial e arraste o rato para o evento final. O número delta de tiques entre os eventos aparece no canto superior direito do visor, como mostra a **Figura 17**.

![Screenshot do número delta de carrapatos entre os eventos.](./media/user-guide/screen_shot_42.png)

**FIGURA 17**

Os tiques delta mostrados na **Figura 17** mostram que 5032 carrapatos decorreram entre o evento 125 e o evento 154. Isto também poderia ser calculado manualmente olhando para os carimbos de tempo relativos em cada evento e subtraindo, mas usar o GUI é fácil e instantâneo.

## <a name="actual-time-display"></a>Exibição do tempo real

Quando ativado, o TraceX exibe o tempo real em microsegundos em ***Vista de Tempo** _ e para as várias informações do tempo delta exibidas pela TraceX. Por predefinição, o visor de tempo real é desativado. Para ativar o visor de tempo real, o número de carraças por microsegundo deve ser introduzido através da duração do menu _ *_Opções -> Ticks per Microsecond_** (o valor a introduzir é determinado pela fonte do temporizador de hardware utilizada para o registo do evento TraceX no alvo).

## <a name="priority-inversions"></a>Inversões prioritárias

O TraceX apresenta automaticamente inversões prioritárias detetadas no ficheiro de rastreio. As inversões prioritárias são definidas como condições em que um fio de maior prioridade é bloqueado tentando obter um mutex que é atualmente propriedade de um fio de menor prioridade. Esta condição é denominada *determinística,* porque o sistema foi criado para funcionar desta forma. Para informar o utilizador, o TraceX mostra gamas de inversão *prioritárias como* uma cor de salmão claro.

O TraceX também apresenta inversões *prioritárias não determinísticas.* Estas inversões prioritárias diferem das inversões prioritárias *determinísticas,* na medida em que outro fio de um nível de prioridade diferente foi executado no meio do que era uma inversão de prioridade *determinística,* tornando assim o tempo dentro da inversão prioritária um pouco *não determinista.* Esta condição é muitas vezes desconhecida do utilizador e pode ser muito grave. Para alertar o utilizador desta condição, o TraceX mostra inversões prioritárias *não determinísticas* como uma cor de salmão mais brilhante. **A figura 18** mostra inversões prioritárias *determinísticas* e *não determinantes.*

![Screenshot da inversão prioritária num ficheiro de rastreio.](./media/user-guide/screen_shot_43.png)

**FIGURA 18**

**A Figura 18** mostra uma inversão de prioridade *determinística* do evento 398 até ao evento 402. Nesta gama, o fio de maior prioridade ***thread 0** _ bloqueia num mutex propriedade de um fio de menor prioridade _*_1_*_. No evento 402, _ *_thread 1_** liberta o mutex e assim termina a inversão prioritária.

A área sombreada mais brilhante mostra uma inversão de prioridade *não determinística* entre o evento 408 através do evento 420. O que torna isto *não determinístico* é que enquanto ***thread 1** _ mantém o mutex em que o fio de maior prioridade _*_0_*_ é bloqueado, ocorre uma interrupção que retoma _*_thread 2_**, que então executa e alonga o tempo em que o sistema está em inversão prioritária. Esta condição pode ser bastante grave e difícil de identificar; no entanto, com traceX é facilmente identificado.
