---
title: Compreenda Azure RTOS TraceX
description: A Azure RTOS TraceX é a ferramenta de análise baseada em anfitriões da Microsoft que fornece aos desenvolvedores uma visão gráfica dos eventos do sistema em tempo real e permite-lhes visualizar e entender melhor o comportamento dos seus sistemas em tempo real.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 9fd33eec6da69e6dda421a125a2dde5eae93b46d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828627"
---
# <a name="overview-of-azure-rtos-tracex"></a>Visão geral do Azure RTOS TraceX

A Azure RTOS TraceX é a ferramenta de análise baseada em anfitriões da Microsoft que fornece aos desenvolvedores uma visão gráfica dos eventos do sistema em tempo real e permite-lhes visualizar e entender melhor o comportamento dos seus sistemas em tempo real. Com o Azure RTOS TraceX, os desenvolvedores podem ver claramente a ocorrência de eventos do sistema, como interrupções e interruptores de contexto que ocorrem fora da vista das ferramentas de depuração padrão. A capacidade de identificar e estudar estes eventos, e identificar o momento da sua ocorrência no contexto da operação global do sistema permite que os desenvolvedores resolvam problemas de programação, encontrando comportamentos inesperados e permitindo-lhes investigar áreas específicas mais informações Descondimento de informações mais rastreadas são armazenadas num tampão no sistema alvo, com a localização e tamanho do tampão determinados pela aplicação em tempo de execução. O Azure RTOS TraceX pode processar qualquer tampão construído da forma correta, não só a partir de Azure RTOS ThreadX, mas de qualquer aplicação ou RTOS. A informação de rastreio pode ser enviada para o anfitrião para análise a qualquer momento – ou post mortem ou em um ponto de rutura. O Azure RTOS ThreadX implementa um tampão circular, que permite que os eventos "N" mais recentes estejam disponíveis para inspeção em caso de mau funcionamento do sistema ou outro evento significativo.

![Azure RTOS TraceX Single-Core Display](./media/user-guide/screen_shot_33.png)

**Ecrã de Single-Core TraceX**

## <a name="key-capabilites"></a>Capacidades-chave

### <a name="azure-rtos-tracex-built-in-system-analysis"></a>Análise do sistema incorporado Azure RTOS TraceX

Azure RTOS TraceX é fornece relatórios de análise de sistema incorporados que estão disponíveis através de um único clique de botão da barra de ferramentas TraceX. Estes botões e relatórios incluem:

![Gerar relatório do perfil de execução](./media/overview-tracex/execution-profile-report-button.jpg) Gerar relatório do perfil de execução

![Gerar relatório de Estatísticas de Desempenho](./media/overview-tracex/performance-statistics-report-button.jpg) Gerar relatório de Estatísticas de Desempenho

![Gerar relatório de utilização da pilha de fio](./media/overview-tracex/thread-stack-usage-report-button.jpg) Gerar relatório de utilização da pilha de fio

### <a name="trace-data-collected-by-azure-rtos-threadx"></a>Vestígios de dados recolhidos pela Azure RTOS ThreadX

O Azure RTOS TraceX foi concebido para trabalhar com o Azure RTOS ThreadX, que constrói uma base de dados de sistemas e aplicações "eventos" no sistema alvo durante o tempo de funcionamento. Estes eventos incluem:

* interruptores de contexto de fio
* preempções
* suspensões
* rescisões
* sistema interrompe
* eventos específicos de aplicação
* todas as chamadas Azure RTOS ThreadX API
* todas as chamadas Azure RTOS NetX API
* todas as chamadas Azure RTOS FileX API
* todas as chamadas Azure RTOS USBX API
* ícones e informações definidos pela aplicação

Os eventos são registados sob controlo do programa, com a marcação de tempo e a identificação do fio ativo para que possam ser exibidos mais tarde na sequência de tempo adequada, e associados ao fio apropriado. A exploração madeireira de eventos pode ser interrompida e reiniciada pelo programa de aplicação dinamicamente, por exemplo, quando se encontra uma área de interesse. Isto evita desarrumar a base de dados e utilizar a memória-alvo quando o sistema está a funcionar corretamente.

### <a name="azure-rtos-tracex-is-like-a-software-logic-analyzer"></a>Azure RTOS TraceX é como um analisador de lógica de software

Uma vez que o registo do evento tenha sido carregado da memória-alvo para o anfitrião, o Azure RTOS TraceX exibe os eventos graficamente num eixo horizontal que representa o tempo, com os vários fios de aplicação e rotinas do sistema a que os eventos estão relacionados listados ao longo do eixo vertical. O Azure RTOS TraceX cria um "analisador de lógica de software" no hospedeiro, tornando os eventos do sistema claramente visíveis. Os eventos são representados por ícones codificados por cores, localizados no ponto de ocorrência ao longo da linha temporal horizontal, à direita da rotina do fio ou do sistema relevante. Quando um ícone do evento é selecionado, são apresentadas as informações correspondentes para esse evento, bem como as informações para os dois eventos anteriores e dois eventos subsequentes. Isto fornece acesso rápido e de clique à informação mais imediata sobre o evento e os seus eventos imediatamente circundantes. O Azure RTOS TraceX fornece um ecrã "Resumo" que mostra todos os eventos do sistema numa única linha horizontal para simplificar a análise de sistemas com muitos fios.

### <a name="sequential-view-mode"></a>Modo de visualização sequencial

O modo de visualização sequencial é selecionado clicando no separador "Vista Sequencial". Este é o modo predefinido. Neste modo, os eventos são mostrados imediatamente a seguir-se, independentemente do tempo decorrido entre eles. Note também a régua acima da área de visualização. Mostra o número relativo do evento desde o início do rastreio. Este modo é o modo padrão e é especialmente útil para obter uma boa visão geral do que se passa no sistema.

![Modo de visualização sequencial](./media/user-guide/screen_shot_10.png)

**Modo de visualização sequencial**

### <a name="time-view-mode"></a>Modo de visualização do tempo

Neste modo, os eventos são mostrados de forma relativa - com uma barra verde sólida sendo usada para mostrar execução entre eventos. Este modo é especialmente útil para ver onde a maior parte do processamento está a ocorrer no sistema, o que pode ajudar os desenvolvedores a afinar o seu sistema para um maior desempenho e/ou capacidade de resposta.

Note também a régua acima do visor do evento. Esta régua mostra carrapatos relativos desde o início do traço, derivado do carimbo de tempo instrumentado no caso de vestígios de registo no interior do Azure RTOS ThreadX. Se os selos de tempo estiverem demasiado próximos (temporizador de baixa frequência), os eventos serão executados em conjunto. Inversamente, se os selos de tempo estiverem demasiado afastados (temporizador de alta frequência), os eventos serão demasiado distantes. Escolher o carimbo de hora de frequência certo é uma consideração importante para tornar significativa a visão relativa do tempo.

![Modo de visualização do tempo](./media/user-guide/screen_shot_31.png)

### <a name="system-summary-line"></a>Linha de resumo do sistema

O Azure RTOS TraceX também fornece uma única linha de resumo que inclui todos os eventos na mesma linha. A linha de resumo contém um resumo do contexto, bem como o resumo do evento correspondente por baixo. Isto torna fácil ver uma visão geral de um sistema complexo. A barra de resumo é especialmente benéfica em sistemas que têm um grande número de fios. Sem uma linha de resumo, o utilizador teria de seguir interações complexas do sistema utilizando a barra de deslocação vertical para seguir o contexto de execução.

O Azure RTOS TraceX lista os contextos do sistema no lado esquerdo do visor.
Os eventos que ocorrem num determinado contexto são exibidos na linha horizontal à direita desse contexto. Desta forma, o utilizador pode facilmente verificar qual o contexto em que o evento ocorreu, bem como seguir essa linha de contexto para ver todos os eventos que ocorreram num determinado contexto.

![Linha Resumo do Sistema](./media/user-guide/screen_shot_32.png)

**Linha Resumo do Sistema**

As duas primeiras entradas de contexto são sempre os contextos "Interromper" e "Inicializar/Inativar". O contexto "Interrupção" representa todos os eventos do sistema feitos a partir de Rotinas de Serviço de Interrupção (ISRs). O contexto "Inicialize/Idle" representa dois contextos no Azure RTOS ThreadX. Os eventos que ocorrem durante tx_application_define, são eventos "Initialize" e são exibidos no contexto "Inicialize/Idle". Se o sistema estiver inativo e, portanto, não ocorrerem eventos, a barra verde que representa "Running" na vista do tempo é desenhada no contexto "Initialize/Idle".

## <a name="methods-of-navigation"></a>Métodos de navegação

O Azure RTOS TraceX permite ao desenvolvedor especificar como funcionam os botões de navegação "Next" e "Previous".

![Botões de navegação](./media/user-guide/event.png)

Se o "Evento" for selecionado, a navegação é feita no evento seguinte/anterior. Se o "Contexto" for selecionado, a navegação é feita no evento seguinte/anterior no mesmo contexto. Se o "Objeto" for selecionado, a navegação é feita no evento seguinte/anterior do objeto atual, por exemplo, eventos associados a uma fila específica. Se forem selecionados "Switches", a navegação é feita no próximo/anterior interruptor de contexto. Se for selecionado o "Same ID", a navegação é feita no evento seguinte/anterior para o mesmo ID do evento.

### <a name="event-information-display"></a>Exibição de informação do evento

A Azure RTOS TraceX fornece informações detalhadas sobre cerca de 300 eventos. Estes incluem seis eventos internos do Azure RTOS ThreadX, dois eventos ISR (entrar e sair), 14 eventos internos do Azure RTOS FileX, 42 eventos internos do Azure RTOS NetX e um evento definido pelo utilizador. Os restantes eventos correspondem diretamente aos serviços Azure RTOS ThreadX, Azure RTOS FileX e Azure RTOS NetX API.
Independentemente de ser selecionado o modo de exibição sequencial ou de visualização do tempo, uma vitrina em qualquer evento na área de visualização resulta em informações detalhadas do evento apresentadas perto do evento. O rato-over do evento 494 na demonstração demo_threadx.trx trace file é mostrado aqui:

![Mouse-Over exibe mais informações](./media/user-guide/screen_shot_37.png)

**Rato-Over exibe mais informações**

Cada evento apresentado contém informações padrão sobre o Contexto e o Tempo e o Tempo Relativo. O campo Contexto mostra em que contexto o evento teve lugar. Há exatamente quatro contextos: linha, ocioso, ISR e inicialização. Quando um evento ocorre num contexto de linha, o nome do fio e a sua prioridade nessa altura são recolhidos e exibidos como mostrado acima. O tempo relativo mostra o número relativo de carraças do temporizador desde o início do rastreio. O Selo do Tempo Bruto exibe a fonte de tempo bruto do evento. Finalmente, todas as informações específicas do evento são apresentadas.

### <a name="zooming-in-and-out"></a>Ampliação para dentro e para fora

Por padrão, o Azure RTOS TraceX exibe os eventos num tamanho fácil de visualizar, com um mapeamento de 1:1 pixel:tick. O utilizador pode ampliar ou ampliar conforme desejado. Fazer zoom até 100% é útil para ver todo o traço na vista atual do visor, enquanto o zoom in é útil em condições em que os eventos se sobrepõem devido à resolução da fonte de carimbo de tempo.

![Zoom-Out Para Ver ou Ampliar a 100% para detalhes](./media/user-guide/screen_shot_41.png)

**Zoom out para ver 100% ou zoom para detalhes**

Quando ampliado a 100% – mostrando todo o traço dentro da página de exibição atual – é fácil ver toda a execução de contexto capturada no vestígio, bem como os eventos gerais que ocorrem nesses contextos. Note que "thread 1" e "thread 2" executam com mais frequência. A coloração azul para os seus eventos também sugere que estes fios estão a fazer chamadas de serviço de fila (os eventos de fila são de cor azul).

Restaurar uma visão completa do ícone é igualmente fácil; O botão de zoom-in pode ser selecionado repetidamente ou pode ser introduzido algum fator de 100.

### <a name="delta-ticks-between-events"></a>Delta tiques entre eventos

Determinar o número de tiques entre vários eventos no Azure RTOS TraceX é fácil - basta clicar no evento inicial e arrastar o rato para o evento final.
O número delta de tiques entre os eventos aparecerá no canto superior direito do visor.

![Delta Ticks](./media/user-guide/screen_shot_42.png)

**Delta Ticks**

Os tiques delta mostram que 5032 carrapatos decorreram entre o evento 494 e o evento 496. Isto também poderia ser calculado manualmente olhando para os carimbos de tempo relativos em cada evento e subtraindo, mas usar o GUI é fácil e instantâneo.

### <a name="priority-inversions"></a>Inversões prioritárias

O Azure RTOS TraceX apresenta automaticamente inversões prioritárias detetadas no ficheiro de rastreio. As inversões prioritárias são definidas como condições em que um fio de maior prioridade é bloqueado tentando obter um mutex que é atualmente propriedade de um fio de menor prioridade. Esta condição é denominada "determinística", uma vez que o sistema foi configurado para funcionar desta forma. Para informar o utilizador, o Azure RTOS TraceX apresenta gamas de inversão prioritárias "determinísticas" como uma cor de salmão claro.

O Azure RTOS TraceX também apresenta inversões prioritárias "não determinísticas". Estas inversões prioritárias diferem das inversões prioritárias "determinísticas", na medida em que outro fio de um nível de prioridade diferente foi executado no meio do que era uma inversão de prioridade "determinística", tornando assim o tempo dentro da inversão prioritária um pouco "não-determinista". Esta condição é muitas vezes desconhecida do utilizador e pode ser muito grave. Para alertar o utilizador desta condição, o Azure RTOS TraceX apresenta inversões prioritárias "não determinísticas" como uma cor de salmão mais brilhante.

![Inversão de prioridade determinística e não determinística](./media/user-guide/screen_shot_43.png)

**Inversão de prioridade determinística e não determinística**

### <a name="execution-profile"></a>Perfil de execução

O Azure RTOS TraceX fornece um relatório de perfil de execução incorporado para todos os contextos de execução dentro do ficheiro de traços atualmente carregado.

![Perfil de execução](./media/user-guide/execution_profile.png)

### <a name="performance-statistics"></a>Estatísticas de desempenho

O Azure RTOS TraceX fornece um relatório de estatísticas de desempenho incorporado para o ficheiro de traços atualmente carregado.

![Estatísticas de desempenho](./media/user-guide/performance_statistics.png)

### <a name="thread-stack-usage"></a>Utilização da pilha de fio

O Azure RTOS TraceX fornece um relatório de utilização de pilhas incorporado para todos os fios que executam dentro do ficheiro de traços atualmente carregado.

![Uso de pilha](./media/user-guide/thread_stack_usage.png)

A Azure RTOS TraceX apresenta as estatísticas de desempenho do Ficheiro Azure RTOS do ficheiro de traços atualmente carregado. Esta informação é apresentada para todo o sistema em todos os objetos de mídia abertos.

![Estatísticas do FileX](./media/user-guide/filex_statistics.png)

### <a name="azure-rtos-netx-statistics"></a>Estatísticas Azure RTOS NetX

O Azure RTOS TraceX também apresenta as estatísticas de desempenho da NetX do arquivo de traços atualmente carregado. Esta informação é exibida para todo o sistema.

![Estatísticas netX](./media/user-guide/netx_statistics.png)

### <a name="raw-trace-dump"></a>Despejo de vestígios crus

O Azure RTOS TraceX pode construir um ficheiro de traços brutos em formato de texto e lançar o bloco de notas para o exibir.

![Despejo de vestígios crus](./media/user-guide/raw_trace_dump.png)

Por favor, note que todos os números de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento
