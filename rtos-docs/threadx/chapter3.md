---
title: Capítulo 3 - Componentes funcionais do Azure RTOS ThreadX
description: Este capítulo contém uma descrição do núcleo Azure RTOS ThreadX de alto desempenho de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: aa66ad392171958e5d2cc765992fd1a9e41250a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827373"
---
# <a name="chapter-3---functional-components-of-azure-rtos-threadx"></a>Capítulo 3 - Componentes funcionais do Azure RTOS ThreadX

Este capítulo contém uma descrição do núcleo Azure RTOS ThreadX de alto desempenho de uma perspetiva funcional. Cada componente funcional é apresentado de forma fácil de entender.

## <a name="execution-overview"></a>Visão geral da execução

Existem quatro tipos de execução de programas dentro de uma aplicação ThreadX: Inicialização, Execução de Fios, Rotinas de Serviço de Interrupção (ISRs) e Temporizadores de Aplicação.

A figura 2 mostra cada tipo diferente de execução do programa. Informações mais pormenorizadas sobre cada um destes tipos encontram-se nas secções subsequentes deste capítulo.

### <a name="initialization"></a>Inicialização

Como o nome indica, este é o primeiro tipo de execução do programa numa aplicação ThreadX. A inicialização inclui toda a execução do programa entre o reset do processador e o ponto de entrada do ciclo de agendamento do *fio.*

### <a name="thread-execution"></a>Execução de fios

Após a inicialização estar concluída, a ThreadX introduz o seu ciclo de agendamento de fios. O ciclo de agendamento procura um fio de aplicação pronto para a execução. Quando um fio pronto é encontrado, a ThreadX transfere o controlo para o mesmo. Depois de terminar o fio (ou se preparar outro fio de maior prioridade), a execução transfere-se de volta para o circuito de agendamento de linhas para encontrar o próximo fio pronto de prioridade máxima.

Este processo de execução contínua e agendamento de fios é o tipo mais comum de execução de programas em aplicações ThreadX.

### <a name="interrupt-service-routines-isr"></a>Interrupção de Rotinas de Serviço (ISR)

As interrupções são a pedra angular dos sistemas em tempo real. Sem interrupções seria extremamente difícil responder às mudanças no mundo externo em tempo oportuno. Ao detetar uma interrupção, o processador guarda informações chave sobre a execução do programa atual (normalmente na pilha), transferindo o controlo para uma área de programa predefinida. Esta área de programa predefinida é geralmente chamada de Rotina de Serviço de Interrupção. Na maioria dos casos, ocorrem interrupções durante a execução do fio (ou no ciclo de agendamento do fio). No entanto, podem também ocorrer interrupções no interior de um ISR de execução ou de um Temporizador de Aplicação.

![Tipos de Execução de Programas](./media/user-guide/types-program-execution.png)

**FIGURA 2. Tipos de Execução de Programas**

### <a name="application-timers"></a>Temporizadores de aplicação

Os Tempos de Aplicação são semelhantes aos ISRs, exceto que a implementação do hardware (normalmente é utilizada uma única interrupção de hardware periódico) está escondida da aplicação. Estes temporizadores são utilizados por aplicações para a realização de tempos de descanso, periódicos e/ou serviços de vigilância. Tal como os ISRs, os Temporizadores de Aplicação interrompem frequentemente a execução do fio. No entanto, ao contrário dos ISRs, os Temporizadores de Aplicação não podem interromper-se mutuamente.

## <a name="memory-usage"></a>Utilização de Memória

A ThreadX reside juntamente com o programa de aplicação. Como resultado, a utilização da memória estática (ou memória fixa) da ThreadX é determinada pelas ferramentas de desenvolvimento; por exemplo, o compilador, linker e localizador. A utilização da memória dinâmica (ou memória de tempo de execução) está sob controlo direto da aplicação.

### <a name="static-memory-usage"></a>Utilização da memória estática

A maioria das ferramentas de desenvolvimento divide a imagem do programa de aplicação em cinco áreas básicas: *instrução,* dados *constantes,* *inicializados,* *dados não ininitializados* e *pilha de sistemas.* A figura 3 mostra um exemplo destas áreas de memória.

É importante compreender que este é apenas um exemplo. O layout real da memória estática é específico para o processador, ferramentas de desenvolvimento e o hardware subjacente.

A área de instrução contém todas as instruções do processador do programa. Esta área é tipicamente a maior e está frequentemente localizada em ROM.

A área constante contém várias constantes compiladas, incluindo cordas definidas ou referenciadas dentro do programa. Além disso, esta área contém a "cópia inicial" da área de dados inicializada. Durante o processo de inicialização do compilador de utilização da *memória,* esta parte da área constante é usada para configurar a área de dados inicializada na RAM. A área constante segue geralmente a área de instrução e está frequentemente localizada em ROM.

Os dados inicializados e as áreas de dados não iniializadas contêm todas as variáveis globais e estáticas. Estas áreas estão sempre localizadas na RAM.

A pilha do sistema é geralmente configurada imediatamente após as áreas de dados inicializadas e não iniializadas.

A pilha do sistema é utilizada pelo compilador durante a inicialização, em seguida, pela ThreadX durante a inicialização e, posteriormente, no processamento do ISR.

![Exemplo da área da memória](./media/user-guide/memory-area-example.png)

**FIGURA 3. Exemplo da área da memória**

### <a name="dynamic-memory-usage"></a>Utilização dinâmica da memória

Como mencionado anteriormente, o uso dinâmico da memória está sob o controlo direto da aplicação. Os blocos de controlo e áreas de memória associadas a pilhas, filas e piscinas de memória podem ser colocados em qualquer lugar no espaço de memória do alvo. Esta é uma característica importante porque facilita a fácil utilização de diferentes tipos de memória física.

Por exemplo, suponha que um ambiente de hardware alvo tenha memória rápida e memória lenta. Se a aplicação necessitar de um desempenho extra para um fio de alta prioridade, o seu bloco de controlo (TX_THREAD) e a pilha podem ser colocadas na área da memória rápida, o que pode melhorar consideravelmente o seu desempenho.

## <a name="initialization"></a>Inicialização

Compreender o processo de inicialização é importante. O ambiente de hardware inicial é criado aqui. Além disso, é aqui que a aplicação é dada a sua personalidade inicial.

> [!NOTE]
> *A ThreadX tenta utilizar (sempre que possível) o processo de inicialização da ferramenta de desenvolvimento completo. Isto facilita o upgrade para novas versões das ferramentas de desenvolvimento no futuro.*

### <a name="system-reset-vector"></a>Vetor de reset do sistema

Todos os microprocessadores têm lógica de reset. Quando ocorre um reset (hardware ou software), o endereço do ponto de entrada da aplicação é recuperado a partir de um local de memória específico. Após a recuperação do ponto de entrada, o processador transfere o controlo para aquele local. O ponto de entrada da aplicação é muitas vezes escrito na língua de montagem nativa e é geralmente fornecido pelas ferramentas de desenvolvimento (pelo menos no modelo). Em alguns casos, uma versão especial do programa de entrada é fornecida com a ThreadX.

### <a name="development-tool-initialization"></a>Inicialização da ferramenta de desenvolvimento

Após a inicialização de baixo nível estar concluída, o controlo transfere-se para a inicialização de alto nível da ferramenta de desenvolvimento. Este é geralmente o lugar onde são criadas variáveis C globais e estáticas inicializadas. Lembre-se que os seus valores iniciais são recuperados da área constante. O processamento exato da inicialização é específico da ferramenta de desenvolvimento.

### <a name="main-function"></a>Função principal

Quando a inicialização da ferramenta de desenvolvimento estiver concluída, o controlo transfere-se para a função *principal* fornecida pelo utilizador. Neste momento, a aplicação controla o que acontece a seguir. Para a maioria das aplicações, a função principal simplesmente chama *tx_kernel_enter*, que é a entrada no ThreadX. No entanto, as aplicações podem realizar o processamento preliminar (geralmente para a inicialização de hardware) antes de entrar em ThreadX.

> [!IMPORTANT]
> *A chamada para tx_kernel_enter não regressa, por isso não faça nenhum processamento depois disso.*

### <a name="tx_kernel_enter"></a>tx_kernel_enter

A função de entrada coordena a inicialização de várias estruturas internas de dados threadX e, em seguida, chama a função de definição da aplicação ***tx_application_define***.

Quando ***tx_application_define*** retorna, o controlo é transferido para o circuito de agendamento de fios. Isto marca o fim da inicialização.

### <a name="application-definition-function"></a>Função de definição de aplicação

A função ***tx_application_define*** define todos os fios de aplicação iniciais, filas, semáforos, mutantes, bandeiras de eventos, piscinas de memória e temporizadores. Também é possível criar e eliminar recursos do sistema a partir de fios durante o funcionamento normal da aplicação. No entanto, todos os recursos de aplicação iniciais são definidos aqui.

A função ***tx_application_define** _ tem um único parâmetro de entrada e certamente vale a pena mencionar. O endereço RAM _first disponível* é o único parâmetro de entrada para esta função. É tipicamente usado como ponto de partida para alocações iniciais de memória de pilhas de fios, filas e piscinas de memória.

> [!NOTE]
> *Após a inicialização estar concluída, apenas um fio de execução pode criar e eliminar recursos do sistema, incluindo outros fios. Portanto, pelo menos um fio deve ser criado durante a inicialização.*

### <a name="interrupts"></a>Interrupções

As interrupções são deixadas desativadas durante todo o processo de inicialização. Se a aplicação de alguma forma permitir interrupções, pode ocorrer um comportamento imprevisível. A figura 4 mostra todo o processo de inicialização, desde o reset do sistema através da inicialização específica da aplicação.

## <a name="thread-execution"></a>Execução de fios

Agendar e executar fios de aplicação é a atividade mais importante da ThreadX. Um fio é tipicamente definido como um segmento de programa semi-independente com um propósito dedicado. O processamento combinado de todos os fios faz uma aplicação.

Os fios são criados dinamicamente chamando ***tx_thread_create** _ durante a inicialização ou durante a execução do fio. Os fios são criados num estado _ready* ou *suspenso.*

![Processo de inicialização](./media/user-guide/initialization-process.png)

**FIGURA 4. Processo de inicialização**

### <a name="thread-execution-states"></a>Estados de execução de fios

Compreender os diferentes estados de processamento dos fios é um ingrediente chave para entender todo o ambiente multi-liscado. Na ThreadX existem cinco estados de linha distintos: *prontos,* *suspensos,* *executados,* *encerrados* e *concluídos*. A figura 5 mostra o diagrama de transição do estado do fio para o ThreadX.

![Transição do Estado do Fio](./media/user-guide/thread-state-transition.png)

**FIGURA 5. Transição do Estado do Fio**

Um fio está em estado *de preparação* quando está pronto para a execução. Um fio pronto não é executado até que seja o fio de prioridade mais elevado em estado pronto. Quando isto acontece, a ThreadX executa o fio, que muda o seu estado para *executar*.

Se um fio de maior prioridade ficar pronto, o fio de execução volta para um estado *pronto.* O fio de alta prioridade recentemente pronto é executado, o que altera o seu estado lógico para *executar*. Esta transição entre estados *prontos* e *de execução* ocorre sempre que ocorre a preempção do fio.

A qualquer momento, apenas um fio está em estado *de execução.* Isto porque um fio no estado *de execução* tem o controlo do processador subjacente.

Os fios num estado *suspenso* não são elegíveis para execução. As razões para estar em estado *suspenso* incluem suspensão por tempo, mensagens de fila, semáforos, mutantes, bandeiras de eventos, memória e suspensão básica do fio. Depois de a causa da suspensão ser removida, a rosca é colocada de volta num estado *de preparação.*

Um fio num estado *completo* é um fio que completou o seu processamento e regressou da sua função de entrada. A função de entrada é especificada durante a criação do fio. Um fio num estado *completo* não pode ser executado novamente.

Um fio está em estado *de terminação* porque outro fio ou o próprio fio chamado *serviço tx_thread_terminate.* Um fio num estado *encerrado* não pode ser executado novamente.

> [!IMPORTANT]
> *Se desejar o reinsegroso fio concluído ou terminado, a aplicação deve primeiro eliminar o fio. Pode então ser recriada e reinicia.*

### <a name="thread-entryexit-notification"></a>Notificação de entrada/saída de linha

Algumas aplicações podem achar vantajoso ser notificado quando um fio específico é introduzido pela primeira vez, quando este completa, ou é terminado. A ThreadX fornece esta capacidade através do serviço ***tx_thread_entry_exit_notify.*** Este serviço regista uma função de notificação de aplicação para um fio específico, que é chamado pela ThreadX sempre que o fio começa a funcionar, completa ou é terminado. Depois de invocada, a função de notificação de aplicação pode realizar o processamento específico da aplicação. Isto normalmente envolve informar outro fio de aplicação do evento através de uma sincronização primitiva ThreadX.

### <a name="thread-priorities"></a>Prioridades do Fio

Como mencionado anteriormente, um fio é um segmento de programa semi-independente com um propósito dedicado. No entanto, todos os fios não são criados iguais! O propósito dedicado de alguns fios é muito mais importante do que outros. Este tipo heterogéneo de importância do fio é uma marca de aplicações em tempo real incorporadas.

A ThreadX determina a importância de um fio quando o fio é criado atribuindo um valor numérico que representa a sua *prioridade*. O número máximo de prioridades da ThreadX é configurável de 32 a 1024 em incrementos de 32. O número máximo real de prioridades é determinado pela **TX_MAX_PRIORITIES** constante durante a compilação da biblioteca ThreadX. Ter um maior número de prioridades não aumenta significativamente o processamento de despesas gerais. No entanto, para cada grupo de 32 níveis prioritários são necessários mais 128 bytes de RAM para os gerir. Por exemplo, 32 níveis prioritários requerem 128 bytes de RAM, 64 níveis prioritários requerem 256 bytes de RAM, e 96 níveis prioritários requer 384 bytes de RAM.

Por padrão, a ThreadX tem 32 níveis de prioridade, que vão desde a prioridade 0 até à prioridade 31. Valores numericamente menores implicam maior prioridade. Assim, a prioridade 0 representa a prioridade máxima, enquanto a prioridade **(TX_MAX_PRIORITIES**-1) representa a menor prioridade.

Múltiplos fios podem ter a mesma prioridade, dependendo do agendamento cooperativo ou do corte de tempo. Além disso, as prioridades dos fios podem ser alteradas durante o tempo de funcionaamento.

### <a name="thread-scheduling"></a>Agendamento de fios

ThreadX programa linhas com base na sua prioridade. O fio pronto com a maior prioridade é executado primeiro. Se várias linhas da mesma prioridade estiverem prontas, são executadas *de forma primeira no primeiro* lugar (FIFO).

### <a name="round-robin-scheduling"></a>Horário redondo

A ThreadX suporta o agendamento *de rodadas* de vários fios com a mesma prioridade. Isto é conseguido através de chamadas cooperativas para ***tx_thread_relinquish** _. Este serviço dá a todas as outras linhas prontas da mesma prioridade uma oportunidade de executar antes que o chamador _ *_tx_thread_relinquish_** execute novamente.

### <a name="time-slicing"></a>Time-Slicing

*Cortar o tempo* é outra forma de agendamento de rodapé. Uma fatia de tempo especifica o número máximo de carraças temporizador (o temporizador interrompe) que um fio pode executar sem abdicar do processador. No ThreadX, o corte de tempo está disponível numa base por fio. A fatia de tempo do fio é atribuída durante a criação e pode ser modificada durante o tempo de funcionação. Quando uma fatia de tempo expira, todos os outros fios prontos do mesmo nível de prioridade têm a oportunidade de executar antes que o fio cortado no tempo volte a ser executado.

Uma fatia de tempo de fio fresca é dada a um fio depois de suspender, renunciar, fazer uma chamada de serviço ThreadX que causa preempção, ou é em si mesmo fatiado do tempo.

Quando um fio cortado no tempo for previamente antecipado, ele retomará antes de outros fios prontos de igual prioridade para o restante da sua rodela temporal.

> [!NOTE]
> *A utilização de corte de tempo resulta numa ligeira quantidade de sobrecarga do sistema. Como o corte de tempo só é útil nos casos em que múltiplos fios partilham a mesma prioridade, os fios que têm uma prioridade única não devem ser atribuídos a uma fatia de tempo.*

### <a name="preemption"></a>Preempção

A preempção é o processo de interromper temporariamente um fio de execução em favor de um fio de maior prioridade. Este processo é invisível para o fio de execução. Quando o fio de maior prioridade estiver terminado, o controlo é transferido de volta para o local exato onde ocorreu a pré-substituição. Esta é uma característica muito importante nos sistemas em tempo real, pois facilita uma resposta rápida a importantes eventos de aplicação. Embora uma característica muito importante, a preempção também pode ser uma fonte de uma variedade de problemas, incluindo fome, sobrecarga excessiva e inversão prioritária.

### <a name="preemption-thresholdtrade"></a>Limiar de preempção&trade;

Para aliviar alguns dos problemas inerentes à preempção, a ThreadX fornece uma característica única e avançada chamada *limiar de pré-edição.*

Um limiar de pré-substituição permite que um fio especifique um *limite* prioritário para desativar a preempção. Os fios que têm prioridades mais elevadas do que o teto ainda podem ser preempeded, enquanto aqueles que não têm limites máximos não podem ser antecipados.

Por exemplo, suponha que um fio de prioridade 20 interage apenas com um grupo de fios que têm prioridades entre 15 e 20. Durante as suas secções críticas, o fio da prioridade 20 pode definir o seu limiar de prevenção para 15, evitando assim a preempção de todos os fios com os quais interage. Isto ainda permite que linhas realmente importantes (prioridades entre 0 e 14) preempam este fio durante o seu processamento de secção crítica, o que resulta num processamento muito mais responsivo.

É claro que ainda é possível que um fio desative todas as preempção, fixando o seu limiar de pré-deposição para 0. Além disso, o limiar de pré-substituição pode ser alterado durante o tempo de funcionaamento.

> [!NOTE]
> *A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.*

### <a name="priority-inheritance"></a>Herança Prioritária

A ThreadX também suporta a herança prioritária opcional dentro dos seus serviços de mutex descritos mais tarde neste capítulo. A herança prioritária permite que um fio de prioridade inferior assuma temporariamente a prioridade de um fio de alta prioridade que está à espera de um mutex propriedade do fio de menor prioridade. Esta capacidade ajuda a aplicação a evitar a inversão de prioridade não determinística, eliminando a preempção das prioridades do fio intermédio. É claro que o *limiar de pré-edição* pode ser utilizado para obter um resultado semelhante.

### <a name="thread-creation"></a>Criação de fios

Os fios de aplicação são criados durante a inicialização ou durante a execução de outros fios de aplicação. Não há limite para o número de fios que podem ser criados por uma aplicação.

### <a name="thread-control-block-tx_thread"></a>TX_THREAD do bloco de controlo de fios

As características de cada fio estão contidas no seu bloco de controlo. Esta estrutura é definida no ficheiro ***tx_api.h.***

O bloco de controlo de um fio pode ser localizado em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

Localizar o bloco de controlo noutras áreas requer um pouco mais de cuidado, assim como toda a memória dinamicamente alocada. Se um bloco de controlo for alocado dentro de uma função C, a memória associada a ele faz parte da pilha do fio de chamada. Em geral, evite usar o armazenamento local para blocos de controlo porque após o retorno da função, todo o seu espaço de pilha variável local é libertado , independentemente de outro fio estar a usá-lo para um bloco de controlo.

Na maioria dos casos, a aplicação é alheia ao conteúdo do bloco de controlo do fio. No entanto, existem algumas situações, especialmente durante o depurg, em que olhar para certos membros é útil. Seguem-se alguns dos membros mais úteis do bloco de controlo.

**tx_thread_run_count** contém um contador do número de muitas vezes que o fio foi programado. Um contador crescente indica que o fio está a ser programado e executado.

**tx_thread_state** contém o estado do fio associado. As seguintes listas são os possíveis estados de linha.

|  Estado do fio   | Valor |
| --------------- | ------ |
| TX_READY       | (0x00) |
| TX_COMPLETED   | (0x01) |
| TX_TERMINATED  | (0x02) |
| TX_SUSPENDED   | (0x03) |
| TX_SLEEP       | (0x04) |
| TX_QUEUE_SUSP | (0x05) |
| TX_SEMAPHORE_SUSP | (0x06) |
| TX_EVENT_FLAG   | (0x07) |
| TX_BLOCK_MEMORY | (0x08) |
| TX_BYTE_MEMORY  | (0x09) |
| TX_MUTEX_SUSP   | (0x0D) |

> [!NOTE]
> *Claro que há muitos outros campos interessantes no bloco de controlo de fios, incluindo o ponteiro da pilha, valor de corte de tempo, prioridades, etc. Os utilizadores são bem-vindos a rever os membros do bloco de controlo, mas as modificações são estritamente proibidas!*

> [!IMPORTANT]
> *Não há equiparia para o estado de "execução" mencionado anteriormente nesta secção. Não é necessário porque só há um fio de execução num dado momento. O estado de um fio de execução também é* **TX_READY**.

### <a name="currently-executing-thread"></a>Atualmente Executando fio

Como mencionado anteriormente, há apenas uma linha executando em qualquer momento. Existem várias formas de identificar o fio de execução, dependendo de qual fio está a fazer o pedido.
Um segmento de programa pode obter o endereço do bloco de controlo do fio de execução chamando ***tx_thread_identify***. Isto é útil em partes partilhadas do código de aplicação que são executados a partir de vários fios.

Nas sessões de depurar, os utilizadores podem examinar o ponteiro interno threadX ***_tx_thread_current_ptr***. Contém o endereço do bloco de controlo do fio atualmente executado. Se este ponteiro for NU, não está a executar nenhum fio de aplicação; ou seja, a ThreadX está à espera no seu ciclo de agendamento para que um fio se prepare.

### <a name="thread-stack-area"></a>Área de pilha de fio

Cada fio deve ter a sua própria pilha para salvar o contexto da sua última execução e utilização do compilador. A maioria dos compiladores C usa a pilha para fazer chamadas de função e para alocar temporariamente variáveis locais. A figura 6 mostra uma pilha típica de fio.

Onde uma pilha de fios está localizada na memória é até a aplicação. A área da pilha é especificada durante a criação do fio e pode ser localizada em qualquer lugar no espaço de endereço do alvo. Esta é uma característica importante porque permite que as aplicações melhorem o desempenho de fios importantes colocando a sua pilha em RAM de alta velocidade.

**Área de Memória de Stack** (exemplo)

![Pilha de fio típica](./media/user-guide/typical-thread-stack.png)

**FIGURA 6. Pilha de fio típica**

Quão grande deve ser uma pilha é uma das perguntas mais frequentes sobre fios. A área de pilha de um fio deve ser grande o suficiente para acomodar a pior fase de cartotação de função, alocação variável local, e salvar o seu último contexto de execução.

O tamanho mínimo da pilha, **TX_MINIMUM_STACK,** é definido pela ThreadX. Uma pilha deste tamanho suporta a poupança do contexto de um fio e a quantidade mínima de chamadas de função e alocação variável local.

No entanto, para a maioria dos fios, o tamanho mínimo da pilha é demasiado pequeno, e o utilizador deve verificar o requisito de tamanho do pior caso examinando o nidificação de chamada de função e a atribuição variável local. Claro, é sempre melhor começar com uma área de pilha maior.

Depois de depurada a aplicação, é possível sintonizar os tamanhos da pilha de fio se a memória for escassa. Um truque favorito é pré-definidor todas as áreas de pilha com um padrão de dados facilmente identificável como (0xEFEF) antes de criar os fios. Depois de a aplicação ter sido completamente submetida aos seus ritmos, as áreas de pilha podem ser examinadas para ver quanto stack foi realmente usado encontrando a área da pilha onde o padrão de dados ainda está intacto. A figura 7 mostra uma pilha predefinida para 0xEFEF após a execução completa do fio.

**Área de Memória de Stack** (outro exemplo)

![Stack Predefinição para 0xEFEF*](./media/user-guide/stack-preset.png)

**FIGURA 7. Stack Predefinição para 0xEFEF**

> [!IMPORTANT]
> *Por predefinição, a ThreadX inicializa cada byte de cada pilha de fios com um valor de 0xEF.*

### <a name="memory-pitfalls"></a>Armadilhas de memória

Os requisitos da pilha para fios podem ser grandes. Por isso, é importante conceber a aplicação para ter um número razoável de fios. Além disso, há que ter alguns cuidados para evitar uma utilização excessiva da pilha dentro dos fios. Devem ser evitados algoritmos recursivos e grandes estruturas de dados locais.

Na maioria dos casos, uma pilha transbordada causa a execução do fio para corromper a memória adjacente (geralmente antes) da sua área de pilha. Os resultados são imprevisíveis, mas muitas vezes resultam numa mudança não natural no balcão do programa. Isto é muitas vezes chamado de "saltar para as casas de fora". Claro que a única maneira de prevenir isto é garantir que todas as pilhas de fios são grandes o suficiente.

### <a name="optional-run-time-stack-checking"></a>Verificação opcional do tempo de execução

A ThreadX fornece a capacidade de verificar a pilha de cada fio por corrupção durante o tempo de funcionaamento. Por predefinição, a ThreadX preenche todos os bytes de pilhas de fios com um 0xEF padrão de dados durante a criação. Se a aplicação construir a biblioteca ThreadX com **TX_ENABLE_STACK_CHECKING** definida, a ThreadX examinará a pilha de cada fio por corrupção à medida que for suspensa ou retomada. Se for detetada corrupção de pilha, a ThreadX ligará para a rotina de tratamento de erros de pilha da aplicação, conforme especificado na chamada para **_tx_thread_stack_error_notify_*_. Caso contrário, se não for especificado nenhum manipulador de erros de pilha, a ThreadX chamará a* rotina de __ _ _ tx_thread_stack_error_handler._**

### <a name="reentrancy"></a>Reentrada

Uma das verdadeiras belezas da multi-leitura é que a mesma função C pode ser chamada de vários fios. Isto fornece uma grande potência e também ajuda a reduzir o espaço de código. No entanto, requer que as funções C chamadas de múltiplos fios sejam *reentrantes*.

Basicamente, uma função de reentrante armazena o endereço de retorno do chamador na pilha atual e não se baseia em variáveis C globais ou estáticas que previamente configura. A maioria dos compiladores coloca o endereço de retorno na pilha. Assim, os desenvolvedores de aplicações só devem preocupar-se com a utilização de *globais* e *estáticas.*

Um exemplo de uma função não-reentrante é a função de ***símbolo*** de corda encontrada na biblioteca C padrão. Esta função "lembra-se" do ponteiro de corda anterior em chamadas posteriores. Faz isto com um ponteiro estático de cordas. Se esta função for chamada de vários fios, provavelmente devolverá um ponteiro inválido.

### <a name="thread-priority-pitfalls"></a>Armadilhas prioritárias de linha

A seleção das prioridades de linha é um dos aspetos mais importantes da multi-leitura. Por vezes, é muito tentador atribuir prioridades baseadas numa noção percebida de importância do fio, em vez de determinar o que é exatamente necessário durante o período de tempo. O uso indevido das prioridades dos fios pode passar fome noutros fios, criar inversão prioritária, reduzir a largura de banda de processamento e dificultar a compreensão do comportamento da aplicação no tempo de execução.

Como mencionado anteriormente, a ThreadX fornece um algoritmo de agendamento preventivo baseado em prioridades. Os fios de prioridade inferior não executam até que não existam fios de prioridade mais elevados prontos para a execução. Se um fio de prioridade superior estiver sempre pronto, os fios de prioridade inferior nunca executam. Esta condição é chamada *de fome de fio.*

A maioria dos problemas de fome dos fios são detetados no início do depurar e podem ser resolvidos garantindo que os fios de maior prioridade não executam continuamente. Em alternativa, a lógica pode ser adicionada à aplicação que gradualmente aumenta a prioridade dos fios famintos até que tenham a oportunidade de executar.

Outra armadilha associada às prioridades do fio é *a inversão prioritária.* A inversão prioritária ocorre quando um fio de prioridade superior é suspenso porque um fio de prioridade inferior tem um recurso necessário. Naturalmente, em alguns casos, é necessário que dois fios de prioridade diferente partilhem um recurso comum. Se estes fios forem os únicos ativos, o tempo de inversão prioritário é limitado pelo momento em que o fio de prioridade inferior detém o recurso. Esta condição é determinística e normal. No entanto, se os fios de prioridade intermédia se tornarem ativos durante esta condição prioritária de inversão, o tempo de inversão prioritário já não é determinístico e pode causar uma falha de aplicação.

Existem principalmente três métodos distintos de prevenção da inversão de prioridade não determinística na ThreadX. Em primeiro lugar, as seleções prioritárias de aplicação e o comportamento em tempo de execução podem ser projetados de uma forma que impeça o problema de inversão prioritária. Em segundo lugar, os fios de prioridade inferior podem utilizar o limiar de *pré-venda* para bloquear a preempção dos fios intermédios, enquanto partilham recursos com fios de prioridade mais elevados. Finalmente, os fios que utilizam objetos mutex ThreadX para proteger os recursos do sistema podem utilizar a *herança prioritária* de mutex opcional para eliminar a inversão de prioridade não determinativa.

### <a name="priority-overhead"></a>Prioridade Overhead

Uma das formas mais negligenciadas de reduzir a sobrecarga em multi-leitura é reduzir o número de interruptores de contexto. Como mencionado anteriormente, ocorre um interruptor de contexto quando a execução de um fio de prioridade superior é favorecida em relação à do fio de execução. Vale a pena mencionar que os fios de prioridade mais elevados podem ficar prontos como resultado tanto de eventos externos (como interrupções) como de chamadas de serviço efetuadas pelo fio de execução.

Para ilustrar os efeitos que as prioridades do fio têm na sobrecarga do interruptor de contexto, assuma um ambiente de três fios com fios denominados *thread_1*, *thread_2* e *thread_3*. Assuma ainda que todos os fios estão em estado de suspensão à espera de uma mensagem. Quando thread_1 recebe uma mensagem, encaminha-a imediatamente para thread_2. Thread_2 reencaminha a mensagem para thread_3. Thread_3 apenas descarta a mensagem. Depois de cada fio processar a sua mensagem, ela volta e espera por outra mensagem.

O processamento necessário para executar estes três fios varia muito dependendo das suas prioridades. Se todos os fios tiverem a mesma prioridade, ocorre um único interruptor de contexto antes da execução de cada fio. O interruptor de contexto ocorre quando cada fio suspende numa fila de mensagens vazias.

No entanto, se thread_2 é maior prioridade do que thread_1 e thread_3 é maior prioridade do que thread_2, o número de interruptores de contexto duplica. Isto porque ocorre um outro interruptor de contexto dentro do serviço *tx_queue_send* quando deteta que um fio de prioridade superior está agora pronto.

O mecanismo de limiar de pré-substituição ThreadX pode evitar estes interruptores de contexto extra e ainda permitir as seleções prioritárias anteriormente mencionadas. Esta é uma característica importante porque permite várias prioridades de linha durante o agendamento, ao mesmo tempo que elimina parte do contexto indesejado que alterna entre eles durante a execução do fio.

### <a name="run-time-thread-performance-information"></a>Informações de desempenho do fio em tempo de execução

A ThreadX fornece informações opcionais de desempenho do fio de tempo de execução. Se a biblioteca e aplicação ThreadX forem construídas com **TX_THREAD_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - resuflações de fio

  - suspensões de fio

  - pré-pedidos de chamada de serviço

  - interromper as preventivas

  - inversões prioritárias

  - fatias de tempo

  - renuncia

  - intervalos de tempo de fio

  - suspensão aborta

  - retornos do sistema ocioso

  - devoluções de sistemas não ociosos

Número total de cada fio:

  - retomas

  - suspensões

  - pré-pedidos de chamada de serviço

  - interromper as preventivas

  - inversões prioritárias

  - fatias de tempo

  - fio renuncia

  - intervalos de tempo de fio

  - suspensão aborta

Esta informação está disponível no tempo de execução através dos serviços ***tx_thread_performance_info_get** _ e _*_tx_thread_performance_system_info_get_**. As informações sobre o desempenho do fio são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de pré-medidas de chamada de serviço pode sugerir que a prioridade do fio e/ou limiar de pré-substituição é demasiado baixa. Além disso, um número relativamente baixo de retornos do sistema inativos pode sugerir que os fios de prioridade mais baixos não estão a ser suspensos o suficiente.

### <a name="debugging-pitfalls"></a>Depurando armadilhas

Depurar aplicações multi-leituras é um pouco mais difícil porque o mesmo código de programa pode ser executado a partir de vários fios. Nesses casos, um ponto de rutura por si só pode não ser suficiente. O depurador também deve ver o ponteiro de fio atual **_tx_thread_current_ptr** usando um ponto de rutura condicional para ver se o fio de vocação é o único a depurar.

Grande parte disto está a ser tratado em pacotes de suporte multi-leitura oferecidos através de vários fornecedores de ferramentas de desenvolvimento. Devido ao seu design simples, integrar a ThreadX com diferentes ferramentas de desenvolvimento é relativamente fácil.

O tamanho da pilha é sempre um tópico importante de depurar em multi-leitura. Sempre que se observa um comportamento inexplicável, é geralmente um bom primeiro palpite para aumentar os tamanhos das pilhas para todos os fios - especialmente o tamanho da pilha do último fio a executar!

> [!TIP]
> *É também uma boa ideia construir a biblioteca ThreadX com **TX_ENABLE_STACK_CHECKING** definidas. Isto ajudará a isolar os problemas de corrupção o mais cedo possível no processamento.*

## <a name="message-queues"></a>Filas de mensagens

As filas de mensagens são o principal meio de comunicação entre fios no ThreadX. Uma ou mais mensagens podem residir numa fila de mensagens. Uma fila de mensagens que contém uma única mensagem é geralmente chamada de *caixa de correio*.

As mensagens são copiadas para uma fila por ***tx_queue_send** _ e são copiadas de uma fila por _*_tx_queue_receive_**. A única exceção a isso é quando um fio é suspenso enquanto se espera uma mensagem numa fila vazia. Neste caso, a próxima mensagem enviada para a fila é colocada diretamente na área de destino do fio.

Cada fila de mensagens é um recurso público. A ThreadX não coloca constrangimentos na forma como as filas de mensagens são utilizadas.

### <a name="creating-message-queues"></a>Criando filas de mensagens

As filas de mensagens são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. Não há limite para o número de filas de mensagens numa aplicação.

### <a name="message-size"></a>Tamanho da mensagem

Cada fila de mensagens suporta uma série de mensagens de tamanho fixo. Os tamanhos de mensagem disponíveis são de 1 a 16 palavras de 32 bits inclusive. O tamanho da mensagem é especificado quando a fila é criada. As mensagens de aplicação superiores a 16 palavras devem ser passadas por ponteiro. Isto é conseguido criando uma fila com um tamanho de mensagem de 1 palavra (o suficiente para segurar um ponteiro) e, em seguida, enviando e recebendo ponteiros de mensagens em vez de toda a mensagem.

### <a name="message-queue-capacity"></a>Capacidade de fila de mensagens

O número de mensagens que uma fila pode conter é uma função do tamanho da sua mensagem e do tamanho da área de memória fornecida durante a criação. A capacidade total de mensagem da fila é calculada dividindo o número de bytes em cada mensagem no número total de bytes na área de memória fornecida.

Por exemplo, se uma fila de mensagens que suporta um tamanho de mensagem de 1 32 bits de palavra (4 bytes) for criada com uma área de memória de 100 bytes, a sua capacidade é de 25 mensagens.

### <a name="queue-memory-area"></a>Área de memória de fila

Como mencionado anteriormente, a área de memória para mensagens de tamponamento é especificada durante a criação da fila. Como outras áreas de memória em ThreadX, pode ser localizado em qualquer lugar no espaço de endereço do alvo.

Esta é uma característica importante porque confere à aplicação uma flexibilidade considerável. Por exemplo, uma aplicação pode localizar a área de memória de uma fila importante em RAM de alta velocidade para melhorar o desempenho.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam enviar ou receber uma mensagem de uma fila. Normalmente, a suspensão do fio envolve esperar por uma mensagem de uma fila vazia. No entanto, também é possível que um fio suspenda a tentativa de enviar uma mensagem para uma fila completa.

Após a suspensão ser resolvida, o serviço solicitado é concluído e o fio de espera é retomado. Se várias linhas forem suspensas na mesma fila, são retomadas na ordem em que foram suspensas (FIFO).

No entanto, o reinício prioritário também é possível se a aplicação ligar ***tx_queue_prioritize*** antes do serviço de fila que levanta a suspensão do fio. A fila prioriza o serviço coloca o fio de prioridade mais elevado na parte da frente da lista de suspensão, deixando todos os outros fios suspensos na mesma ordem FIFO.

Os intervalos também estão disponíveis para todas as suspensões de fila. Basicamente, um tempo limite especifica o número máximo de marcações de temporizador que o fio permanecerá suspenso. Se ocorrer uma intemporádice, o fio é retomado e o serviço retorna com o código de erro apropriado.

### <a name="queue-send-notification"></a>Notificação de envio de fila

Algumas aplicações podem achar vantajoso ser notificado sempre que uma mensagem é colocada numa fila. A ThreadX fornece esta capacidade através do serviço ***tx_queue_send_notify.*** Este serviço regista a função de notificação de pedido fornecida com a fila especificada. A ThreadX irá posteriormente invocar esta função de notificação de aplicação sempre que uma mensagem for enviada para a fila. O processamento exato dentro da função de notificação de pedido é determinado pelo pedido; no entanto, consiste tipicamente em retomar o fio adequado para o processamento da nova mensagem.

### <a name="queue-event-chainingtrade"></a>Acorrentamento de eventos de fila&trade;

As capacidades de notificação no ThreadX podem ser usadas para acorrentar vários eventos de sincronização em conjunto. Isto é normalmente útil quando um único fio deve processar vários eventos de sincronização.

Por exemplo, suponha que um único fio é responsável pelo processamento de mensagens de cinco filas diferentes e também deve suspender quando não há mensagens disponíveis. Isto é facilmente conseguido registando uma função de notificação de aplicação para cada fila e introduzindo um semáforo de contagem adicional. Especificamente, a função de notificação de aplicação executa uma *tx_semaphore_put* sempre que é chamada (a contagem de semáforos representa o número total de mensagens em todas as cinco filas). O fio de processamento suspende este semáforo através do serviço *tx_semaphore_get.* Quando o semáforo estiver disponível (neste caso, quando uma mensagem está disponível!), o fio de processamento é retomado. Em seguida, interroga cada fila para uma mensagem, processa a mensagem encontrada, e executa outra ***tx_semaphore_get*** esperar pela próxima mensagem. Conseguir isto sem acorrentar eventos é bastante difícil e provavelmente exigiria mais fios e/ou código de aplicação adicional.

Em geral, *acorrentamento de eventos* resulta em menos fios, menos sobrecargas e menores requisitos de RAM. Também fornece um mecanismo altamente flexível para lidar com os requisitos de sincronização de sistemas mais complexos.

### <a name="run-time-queue-performance-information"></a>Informações de desempenho da fila de tempo de execução
A ThreadX fornece informações opcionais de desempenho da fila de tempo de execução. Se a biblioteca e aplicação ThreadX forem construídas com ***TX_QUEUE_ENABLE_PERFORMANCE_INFO*** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - mensagens enviadas

  - mensagens recebidas

  - suspensões vazias fila

  - suspensões completas fila

  - retornas de erros completos da fila (suspensão não especificada)

  - intervalos de fila

Número total de cada fila:

  - mensagens enviadas

  - mensagens recebidas

  - suspensões vazias fila

  - suspensões completas fila

  - retornas de erros completos da fila (suspensão não especificada)

  - intervalos de fila

Esta informação está disponível no tempo de execução através dos serviços ***tx_queue_performance_info_get** _ e _*_tx_queue_performance_system_info_get_**. As informações sobre o desempenho da fila são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de "suspensões completas da fila" sugere que um aumento do tamanho da fila pode ser benéfico.

### <a name="queue-control-block-tx_queue"></a>TX_QUEUE do Bloco de Controlo de Fila

As características de cada fila de mensagens encontram-se no seu bloco de controlo. Contém informações interessantes, como o número de mensagens na fila. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo da fila de mensagens também podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="message-destination-pitfall"></a>Pitfall do destino da mensagem

Como mencionado anteriormente, as mensagens são copiadas entre a área da fila e as áreas de dados de aplicação. É importante garantir que o destino de uma mensagem recebida é grande o suficiente para segurar toda a mensagem. Caso contrário, a memória que segue o destino da mensagem será provavelmente corrompida.

> [!NOTE]
> *Isto é especialmente letal quando um destino de mensagem muito pequeno está na pilha - nada como corromper o endereço de retorno de uma função!*

## <a name="counting-semaphores"></a>Contagem de Semáforos

A ThreadX fornece semáforos de contagem de 32 bits que variam de valor entre 0 e 4.294.967.295. Existem duas operações de contagem de semáforos: *tx_semaphore_get* e *tx_semaphore_put.* A operação diminui o semáforo por um. Se o semáforo for 0, a operação de get não é bem sucedida. O inverso da operação get é a operação de colocação.
Aumenta o semáforo por um.

Cada semáforo de contagem é um recurso público. A ThreadX não coloca constrangimentos na forma como são utilizados os semáforos de contagem.

Os semáforos de contagem são normalmente utilizados para *exclusão mútua.* No entanto, contar semáforos também pode ser usado como um método para a notificação de eventos.

### <a name="mutual-exclusion"></a>Exclusão Mútua

 A exclusão mútua diz respeito ao controlo do acesso dos fios a determinadas áreas de aplicação (também *designadas por secções críticas* ou *recursos de aplicação).* Quando utilizado para exclusão mútua, a "contagem atual" de um semáforo representa o número total de fios que são autorizados a aceder. Na maioria dos casos, contar semáforos utilizados para exclusão mútua terá um valor inicial de 1, o que significa que apenas um fio pode aceder ao recurso associado de cada vez. Contando semáforos que só têm valores de 0 ou 1 são vulgarmente *chamados de semáforos binários.*

> [!IMPORTANT]
> *Se estiver a ser utilizado um semáforo binário, o utilizador deve evitar que o mesmo fio efetue uma operação de get num semáforo que já possui. Uma segunda sê-lo não seria bem sucedida e poderia causar a suspensão indefinida do fio de chamada e a indisponibilidade permanente do recurso.*

### <a name="event-notification"></a>Notificação de eventos

É igualmente possível utilizar os semáforos de contagem como notificação de eventos, de forma produtora-consumidor. O consumidor tenta obter o semáforo de contagem enquanto o produtor aumenta o semáforo sempre que algo está disponível. Estes semáforos geralmente têm um valor inicial de 0 e não aumentarão até que o produtor tenha algo pronto para o consumidor. Os semáforos utilizados para notificação de eventos também podem beneficiar da utilização da chamada de serviço ***tx_semaphore_ceiling_put.*** Este serviço garante que a contagem de semáforos nunca exceda o valor fornecido na chamada.

### <a name="creating-counting-semaphores"></a>Criação de Semáforos Contando

Os semáforos de contagem são criados durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. A contagem inicial do semáforo é especificada durante a criação. Não há limite para o número de semáforos de contagem num pedido.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam executar uma operação de get num semáforo com uma contagem atual de 0.

Após a operação de colocação, a operação de get do fio suspenso é executada e o fio é retomado. Se várias linhas forem suspensas no mesmo semáforo de contagem, são retomadas na mesma ordem em que foram suspensas (FIFO).

No entanto, o reinício prioritário também é possível se a aplicação ligar ***tx_semaphore_prioritize*** antes da chamada de semáforo que levanta a suspensão do fio. O semáforo prioriza o serviço coloca o fio de prioridade mais elevado na parte da frente da lista de suspensão, deixando todos os outros fios suspensos na mesma ordem FIFO.

### <a name="semaphore-put-notification"></a>Aviso de colocação de semáforos

Algumas aplicações podem achar vantajoso ser notificado sempre que um semáforo é colocado. A ThreadX fornece esta capacidade através do serviço ***tx_semaphore_put_notify.*** Este serviço regista a função de notificação de pedido fornecida com o semáforo especificado. A ThreadX irá posteriormente invocar esta função de notificação de aplicação sempre que o semáforo for colocado. O processamento exato dentro da função de notificação de pedido é determinado pelo pedido; no entanto, consiste tipicamente em retomar o fio adequado para o processamento do novo evento de semáforo.

### <a name="semaphore-event-chainingtrade"></a>Acorrentamento do Evento Semáforo&trade;

As capacidades de notificação no ThreadX podem ser usadas para acorrentar vários eventos de sincronização em conjunto. Isto é normalmente útil quando um único fio deve processar vários eventos de sincronização.

Por exemplo, em vez de ter fios separados suspensos para uma mensagem de fila, bandeiras de eventos e um semáforo, a aplicação pode registar uma rotina de notificação para cada objeto. Quando invocado, a rotina de notificação de aplicação pode então retomar um único fio, que pode interrogar cada objeto para encontrar e processar o novo evento.

Em geral, *acorrentamento de eventos* resulta em menos fios, menos sobrecargas e menores requisitos de RAM. Também fornece um mecanismo altamente flexível para lidar com os requisitos de sincronização de sistemas mais complexos.

### <a name="run-time-semaphore-performance-information"></a>Informações de desempenho do semáforo em tempo de execução

A ThreadX fornece informações opcionais de desempenho semaphore em tempo de execução. Se a biblioteca e aplicação ThreadX forem construídas com **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - semáforo coloca

  - semáforo fica

  - semáforo obter suspensões

  - semáforo obter intervalos de tempo

Número total de cada semáforo:

  - semáforo coloca

  - semáforo fica

  - semáforo obter suspensões

  - semáforo obter intervalos de tempo

Esta informação está disponível no tempo de execução através dos serviços ***tx_semaphore_performance_info_get** _ e _*_tx_semaphore_performance_system_info_get_**. As informações sobre o desempenho do semáforo são úteis para determinar se a aplicação se está a comportar corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de "intervalos de tempo semaphore get" pode sugerir que outros fios estão a reter recursos demasiado longos.

### <a name="semaphore-control-block-tx_semaphore"></a>TX_SEMAPHORE do Bloco de Controlo de Semáforos

As características de cada semáforo de contagem encontram-se no seu bloco de controlo. Contém informações como a contagem atual de semáforos. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo de semáforos podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="deadly-embrace"></a>Abraço Mortal

Uma das armadilhas mais interessantes e perigosas associadas aos semáforos usados para a exclusão mútua é o *abraço mortal.* Um abraço mortal, ou *impasse,* é uma condição em que dois ou mais fios são suspensos indefinidamente enquanto tentam obter semáforos já pertencentes uns aos outros.

Esta condição é melhor ilustrada por um dois fios, dois exemplos de semáforo. Suponha que o primeiro fio é dono do primeiro semáforo e o segundo fio é dono do segundo semáforo. Se o primeiro fio tentar obter o segundo semáforo e, ao mesmo tempo, o segundo fio tentar obter o primeiro semáforo, ambos os fios entram numa condição de impasse. Além disso, se estes fios permanecerem suspensos para sempre, os seus recursos associados também estão bloqueados para sempre. A figura 8 ilustra este exemplo.

**Abraço Mortal** (exemplo)

![Exemplo de fios suspensos](./media/user-guide/example-suspended-threads.png)

**FIGURA 8. Exemplo de fios suspensos**

Para sistemas em tempo real, os abraços mortais podem ser evitados colocando certas restrições sobre como os fios obtêm semáforos. Os fios só podem ter um semáforo de cada vez. Alternativamente, os fios podem possuir vários semáforos se os recolherem na mesma ordem. No exemplo anterior, se o primeiro e o segundo fio obtiverem o primeiro e o segundo semáforo em ordem, o abraço mortal é evitado.

> [!TIP]
> *Também é possível utilizar o tempo de suspensão associado à operação get para recuperar de um abraço mortal.*

### <a name="priority-inversion"></a>Inversão prioritária

Outra armadilha associada aos semáforos de exclusão mútua é a inversão prioritária. Este tópico é discutido mais plenamente em "[Thread Priority Pitfalls](#thread-priority-pitfalls)".

O problema básico resulta de uma situação em que um fio de menor prioridade tem um semáforo de que um fio de prioridade mais elevado necessita. Isto por si só é normal. No entanto, os fios com prioridades entre eles podem fazer com que a inversão prioritária dure um tempo não desdeterminístico. Isto pode ser tratado através de uma seleção cuidadosa das prioridades do fio, utilizando o limiar de pré-edição, e aumentando temporariamente a prioridade do fio que detém o recurso para o do fio de alta prioridade.

## <a name="mutexes"></a>Mutaxos

Além dos semáforos, a ThreadX também fornece um objeto mutex. Um mutex é basicamente um semáforo binário, o que significa que só um fio pode possuir um mutex de cada vez. Além disso, o mesmo fio pode realizar uma operação mutex bem sucedida num mutex propriedade várias vezes, 4.294.967.295 para ser exato. Existem duas operações no objeto mutex: ***tx_mutex_get** _ e _*_tx_mutex_put_**. A operação get obtém um mutex não pertencente a outro fio, enquanto a operação de colocação liberta um mutex previamente obtido. Para que um fio liberte um mutex, o número de operações de colocação deve ser igual ao número de operações anteriores.

Cada mutex é um recurso público. A ThreadX não coloca constrangimentos na forma como os mutantes são usados.

Os mutantes ThreadX são utilizados exclusivamente para *exclusão mútua.* Ao contrário dos semáforos de contagem, os mutantes não têm uso como método para a notificação do evento.

### <a name="mutex-mutual-exclusion"></a>Exclusão Mútua Mutex

À semelhança da discussão na secção de semáforos de contagem, a exclusão mútua diz respeito ao controlo do acesso dos fios a determinadas áreas de aplicação (também *designadas por secções críticas* ou *recursos de aplicação).* Quando disponível, um mutex ThreadX terá uma contagem de propriedade de 0. Após o mutex ser obtido por um fio, a contagem de propriedade é incrementada uma vez para cada operação de obtenção bem sucedida realizada no mutex e decrementeda para cada operação de colocação bem sucedida.

### <a name="creating-mutexes"></a>Criar Mutaxos

Os mutamentos ThreadX são criados durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. A condição inicial de um mutex está sempre "disponível". Um mutex também pode ser criado com *herança prioritária* selecionada.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam executar uma operação de get num mutex já propriedade de outro fio.

Após o mesmo número de operações de colocação serem realizadas pelo fio próprio, a operação de get do fio suspenso é realizada, dando-lhe a propriedade do mutex, e o fio é retomado. Se várias linhas forem suspensas no mesmo mutex, são retomadas na mesma ordem em que foram suspensas (FIFO).

No entanto, o reinício prioritário é feito automaticamente se a herança de prioridade mutex foi selecionada durante a criação. O reinício prioritário também é possível se a aplicação ligar ***tx_mutex_prioritize*** antes da chamada de colocação mutex que levanta a suspensão do fio. O serviço de prioridades mutais coloca o fio de prioridade mais elevado na parte da frente da lista de suspensão, deixando todos os outros fios suspensos na mesma ordem FIFO.

### <a name="run-time-mutex-performance-information"></a>Informações de desempenho de Mutex em tempo de execução

A ThreadX fornece informações opcionais de desempenho de mutex em tempo de execução. Se a biblioteca e aplicação ThreadX forem construídas com **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

- mutex coloca

- mutex recebe

- mutex obter suspensões

- mutex obter intervalos de tempo

- inversões de prioridade mutex

- heranças de prioridade mutex

Número total de cada mutex:

  - mutex coloca

  - mutex recebe

  - mutex obter suspensões

  - mutex obter intervalos de tempo

  - inversões de prioridade mutex

  - heranças de prioridade mutex

Esta informação está disponível no tempo de execução através dos serviços ***tx_mutex_performance_info_get** _ e _*_tx_mutex_performance_system_info_get_**. As informações de desempenho da Mutex são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de "intervalos de tempo" de "mutex get timeouts" pode sugerir que outros fios estão a reter recursos demasiado longos.

### <a name="mutex-control-block-tx_mutex"></a>TX_MUTEX do Bloco de Controlo de Mutaxos

As características de cada mutex encontram-se no seu bloco de controlo. Contém informações como a atual contagem de propriedade de mutantes, juntamente com o ponteiro do fio que detém o mutex. Esta estrutura é definida no ficheiro ***tx_api.h.*** Os blocos de controlo mutex podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="deadly-embrace"></a>Abraço Mortal

Uma das armadilhas mais interessantes e perigosas associadas à propriedade de mutantes é o *abraço mortal.* Um abraço mortal, ou *impasse,* é uma condição em que dois ou mais fios são suspensos indefinidamente enquanto tentam obter um mutex já pertencente aos outros fios. A discussão do *abraço mortal* e dos seus remédios são completamente válidos para o objeto mutex também.

### <a name="priority-inversion"></a>Inversão prioritária

Como mencionado anteriormente, uma grande armadilha associada à exclusão mútua é a inversão prioritária. Este tópico é discutido mais plenamente em "[Thread Priority Pitfalls](#thread-priority-pitfalls)".

O problema básico resulta de uma situação em que um fio de prioridade inferior tem um semáforo de que um fio de prioridade mais elevado necessita. Isto por si só é normal. No entanto, os fios com prioridades entre eles podem fazer com que a inversão prioritária dure um tempo não desdeterminístico. Ao contrário dos semáforos discutidos anteriormente, o objeto mutex ThreadX tem *uma herança prioritária* opcional. A ideia básica por trás da herança prioritária é que um fio de prioridade inferior tem a sua prioridade levantada temporariamente para a prioridade de um fio de alta prioridade que quer o mesmo mutex propriedade do fio de menor prioridade. Quando o fio de menor prioridade liberta o mutex, a sua prioridade original é então restaurada e o fio de prioridade mais elevado é dado a propriedade do mutex. Esta característica elimina a inversão de prioridade não determinística, limitando a quantidade de inversão ao tempo que o fio de prioridade inferior detém o mutex. É claro que as técnicas discutidas no início deste capítulo para lidar com a inversão de prioridade não determinística também são válidas com mutantes.

## <a name="event-flags"></a>Bandeiras do evento

As bandeiras do evento fornecem uma ferramenta poderosa para a sincronização dos fios. Cada bandeira do evento é representada por um único pedaço. As bandeiras do evento estão dispostas em grupos de 32. Os fios podem operar em todas as 32 bandeiras de eventos de um grupo ao mesmo tempo. Os eventos são definidos por ***tx_event_flags_set** _ e são recuperados por _*_tx_event_flags_get_**.

A colocação de bandeiras de eventos é feita com uma operação lógica E/OR entre as bandeiras do evento atual e as novas bandeiras do evento. O tipo de operação lógica (ou um E ou OR) é especificado na ***chamada tx_event_flags_set.***

Existem opções lógicas semelhantes para a recuperação de bandeiras de eventos. Um pedido de obter pode especificar que todas as bandeiras de eventos especificadas são necessárias (um E lógico).

Em alternativa, um pedido de obter pode especificar que qualquer uma das bandeiras de eventos especificadas satisfará o pedido (um OR lógico). O tipo de operação lógica associada à recuperação de bandeiras de eventos é especificado na ***chamada tx_event_flags_get.***

> [!IMPORTANT]
> *As bandeiras de eventos que satisfaçam um pedido de ovação são consumidas, ou seja, a zero, se* **TX_OR_CLEAR** *ou* **TX_AND_CLEAR** *forem especificados pelo pedido.*

Cada grupo de bandeiras de eventos é um recurso público. A ThreadX não coloca constrangimentos na forma como são utilizados os grupos de bandeiras de eventos.

### <a name="creating-event-flags-groups"></a>Criação de grupos de bandeiras de eventos

Os grupos de bandeiras de eventos são criados durante a inicialização ou durante o tempo de execução por fios de aplicação. No momento da sua criação, todas as bandeiras do grupo estão definidas para zero. Não há limite para o número de grupos de bandeiras de eventos numa aplicação.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto tentam obter qualquer combinação lógica de bandeiras de eventos de um grupo. Depois de uma bandeira de evento ser definida, os pedidos de todos os fios suspensos são revistos. Todos os fios que agora têm as bandeiras de eventos necessárias são retomados.

> [!NOTE]
> *Todos os fios suspensos de um grupo de bandeira de evento são revistos quando as suas bandeiras de evento são definidas. Isto, naturalmente, introduz despesas adicionais. Por conseguinte, é uma boa prática limitar o número de fios que utilizam o mesmo grupo de bandeira de evento a um número razoável.*

### <a name="event-flags-set-notification"></a>Notificação de conjunto de bandeiras de evento

Algumas aplicações podem achar vantajoso ser notificado sempre que uma bandeira do evento é definida. A ThreadX fornece esta capacidade através do serviço ***tx_event_flags_set_notify.*** Este serviço regista a função de notificação de aplicação fornecida com o grupo de bandeiras de eventos especificado. A ThreadX irá posteriormente invocar esta função de notificação de aplicação sempre que for definida uma bandeira de evento no grupo. O processamento exato dentro da função de notificação de aplicação é determinado pela aplicação, mas normalmente consiste em retomar o fio adequado para o processamento da nova bandeira do evento.

### <a name="event-flags-event-chainingtrade"></a>Acorrentamento de eventos bandeiras de evento&trade;

As capacidades de notificação na ThreadX podem ser usadas para "acorrentar" vários eventos de sincronização em conjunto. Isto é normalmente útil quando um único fio deve processar vários eventos de sincronização.

Por exemplo, em vez de ter fios separados suspensos para uma mensagem de fila, bandeiras de eventos e um semáforo, a aplicação pode registar uma rotina de notificação para cada objeto. Quando invocado, a rotina de notificação de aplicação pode então retomar um único fio, que pode interrogar cada objeto para encontrar e processar o novo evento.

Em geral, *acorrentamento de eventos* resulta em menos fios, menos sobrecargas e menores requisitos de RAM. Também fornece um mecanismo altamente flexível para lidar com os requisitos de sincronização de sistemas mais complexos.

### <a name="run-time-event-flags-performance-information"></a>Informações de desempenho de bandeiras de eventos de tempo de execução

A ThreadX fornece informações opcionais de desempenho de bandeiras de eventos de execução. Se a biblioteca e aplicação ThreadX forem construídas com **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - conjuntos de bandeiras de evento

  - bandeiras de evento recebe

  - bandeiras de evento obter suspensões

  - bandeiras de evento obter intervalos

Número total de cada grupo de bandeiras de evento:

  - conjuntos de bandeiras de evento

  - bandeiras de evento recebe

  - bandeiras de evento obter suspensões

  - bandeiras de evento obter intervalos

Esta informação está disponível em tempo de execução através dos serviços ***tx_event_flags_performance_info_get** _ e _*_tx_event_flags_performance_system_info_get_*_. A informação de desempenho das bandeiras do evento é útil para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de intervalos no serviço _ *_tx_event_flags_get_** pode sugerir que o tempo de suspensão das bandeiras do evento é demasiado curto.

### <a name="event-flags-group-control-block-tx_event_flags_group"></a>Bloco de controlo de grupo de bandeiras de eventos TX_EVENT_FLAGS_GROUP

As características de cada grupo de bandeiras de eventos encontram-se no seu bloco de controlo. Contém informações como as definições atuais das bandeiras do evento e o número de fios suspensos para eventos. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo de grupo de eventos podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="memory-block-pools"></a>Piscinas de Blocos de Memória

Alocar a memória de forma rápida e determinística é sempre um desafio nas aplicações em tempo real. Com isto em mente, a ThreadX fornece a capacidade de criar e gerir várias piscinas de blocos de memória de tamanho fixo.

Como as piscinas de blocos de memória consistem em blocos de tamanho fixo, nunca há problemas de fragmentação. Claro, a fragmentação causa comportamentos que não são inerentemente indeterminados. Além disso, o tempo necessário para alocar e libertar um bloco de memória de tamanho fixo é comparável ao da simples manipulação da lista ligada. Além disso, a atribuição de blocos de memória e a deslocação são feitas no cabeça da lista disponível. Isto fornece o processamento de listas mais rápido possível e pode ajudar a manter o bloco de memória real em cache.

A falta de flexibilidade é a principal desvantagem dos pools de memória de tamanho fixo. O tamanho do bloco de uma piscina deve ser grande o suficiente para suportar os piores requisitos de memória dos seus utilizadores. Claro que a memória pode ser desperdiçada se muitos pedidos de memória de tamanhos diferentes forem feitos para a mesma piscina. Uma solução possível é fazer vários conjuntos de blocos de memória diferentes que contêm diferentes blocos de memória de tamanho.

Cada conjunto de blocos de memória é um recurso público. A ThreadX não coloca constrangimentos na forma como as piscinas são utilizadas.

### <a name="creating-memory-block-pools"></a>Criação de piscinas de blocos de memória

Os pools de blocos de memória são criados durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. Não há limite para o número de piscinas de blocos de memória numa aplicação.

### <a name="memory-block-size"></a>Tamanho do bloco de memória

Como mencionado anteriormente, as piscinas de blocos de memória contêm uma série de blocos de tamanho fixo. O tamanho do bloco, em bytes, é especificado durante a criação da piscina.

> [!NOTE]
> *A ThreadX adiciona uma pequena quantidade de sobrecarga - do tamanho de um ponteiro C - a cada bloco de memória na piscina. Além disso, a ThreadX poderá ter de remar o tamanho do bloco para manter o início de cada bloco de memória no alinhamento adequado.*

### <a name="pool-capacity"></a>Capacidade da Piscina

O número de blocos de memória numa piscina é uma função do tamanho do bloco e do número total de bytes na área de memória fornecida durante a criação. A capacidade de uma piscina é calculada dividindo o tamanho do bloco (incluindo o acolchoado e os bytes de ponteiro) no número total de bytes na área de memória fornecida.

### <a name="pools-memory-area"></a>Área de Memória da Piscina

Como mencionado anteriormente, a área de memória para o bloco pool é especificada durante a criação. Como outras áreas de memória em ThreadX, pode ser localizado em qualquer lugar no espaço de endereço do alvo.

Esta é uma característica importante devido à flexibilidade considerável que proporciona. Por exemplo, suponha que um produto de comunicação tem uma área de memória de alta velocidade para e/S. Esta área de memória é facilmente gerida transformando-a num bloco de memória ThreadX.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto esperam por um bloco de memória de uma piscina vazia. Quando um bloco é devolvido à piscina, o fio suspenso é dado este bloco e o fio é retomado.

Se várias linhas forem suspensas na mesma piscina de blocos de memória, são retomadas na ordem em que foram suspensas (FIFO).

No entanto, o reinício de prioridade também é possível se a aplicação ligar ***tx_block_pool_prioritize*** antes da chamada de desbloqueio do bloco que levanta a suspensão do fio. O bloco de prioridades de serviço coloca o fio de prioridade mais alto na parte da frente da lista de suspensão, deixando todos os outros fios suspensos na mesma ordem FIFO.

### <a name="run-time-block-pool-performance-information"></a>Informações de desempenho do bloco de tempo de execução

A ThreadX fornece informações opcionais de desempenho do bloco de tempo de execução. Se a biblioteca e aplicação ThreadX forem construídas com **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - blocos atribuídos

  - blocos libertados

  - suspensões de atribuição

  - intervalos de atribuição

Número total para cada bloco:

  - blocos atribuídos

  - blocos libertados

  - suspensões de atribuição

  - intervalos de atribuição

Esta informação está disponível no tempo de execução através dos serviços ***tx_block_pool_performance_info_get** _ e _*_tx_block_pool_performance_system_info_get_**. As informações de desempenho do pool de blocos são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de "suspensões de atribuição" pode sugerir que o bloco de piscina é demasiado pequeno.

### <a name="memory-block-pool-control-block-tx_block_pool"></a>Bloco de controlo de piscina de bloco de memória TX_BLOCK_POOL

As características de cada conjunto de blocos de memória encontram-se no seu bloco de controlo. Contém informações como o número de blocos de memória disponíveis e o tamanho do bloco de memória. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo da piscina também podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="overwriting-memory-blocks"></a>Sobreescrita de blocos de memória

É importante garantir que o utilizador de um bloco de memória atribuído não escreva fora dos seus limites. Se isso acontecer, a corrupção ocorre numa área de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes fatais para a aplicação.

## <a name="memory-byte-pools"></a>Piscinas De Memória Byte

As piscinas de byte de memória ThreadX são semelhantes a uma pilha C padrão. Ao contrário da pilha C padrão, é possível ter várias piscinas byte de memória. Além disso, os fios podem suspender-se numa piscina até que a memória solicitada esteja disponível.

As alocações das piscinas de bytes de memória são semelhantes às chamadas tradicionais ***malloc** _, que incluem a quantidade de memória desejada (in bytes). A memória é alotribuida da piscina de forma _first-fit*; ou seja, é utilizado o primeiro bloco de memória livre que satisfaz o pedido. A memória em excesso deste bloco é convertida num novo bloco e colocada de volta na lista de memórias gratuitas. Este processo chama-se *fragmentação.*

Os blocos de memória livre adjacentes são *fundidos* durante uma pesquisa subsequente de atribuição de um bloco de memória livre suficientemente grande. Este processo chama-se *desfragmentação.*

Cada piscina de byte de memória é um recurso público. A ThreadX não coloca constrangimentos na forma como as piscinas são utilizadas, exceto que os serviços de byte de memória não podem ser chamados de ISRs.

### <a name="creating-memory-byte-pools"></a>Criação de piscinas de byte de memória

As piscinas de byte de memória são criadas durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. Não há limite para o número de piscinas de byte de memória numa aplicação.

### <a name="pool-capacity"></a>Capacidade da Piscina

O número de bytes alocáveis numa piscina de bytes de memória é ligeiramente inferior ao especificado durante a criação. Isto porque a gestão da área da memória livre introduz algumas despesas gerais. Cada bloco de memória livre na piscina requer o equivalente a dois ponteiros C de sobrecarga. Além disso, a piscina é criada com dois blocos, um grande bloco livre e um pequeno bloco permanentemente alocado no final da área de memória. Este bloco atribuído é usado para melhorar o desempenho do algoritmo de atribuição. Elimina a necessidade de verificar continuamente o fim da área da piscina durante a fusão.

Durante o tempo de funcionação, a quantidade de sobrecarga na piscina normalmente aumenta. As alocações de um número ímpar de bytes são acolchoadas para garantir o alinhamento adequado do próximo bloco de memória. Além disso, a sobrecarga aumenta à medida que a piscina se torna mais fragmentada.

### <a name="pools-memory-area"></a>Área de Memória da Piscina

A área de memória para uma piscina de byte de memória é especificada durante a criação. Como outras áreas de memória em ThreadX, pode ser localizado em qualquer lugar no espaço de endereço do alvo. Esta é uma característica importante devido à flexibilidade considerável que proporciona. Por exemplo, se o hardware-alvo tiver uma área de memória de alta velocidade e uma área de memória de baixa velocidade, o utilizador pode gerir a alocação de memória para ambas as áreas criando uma piscina em cada uma delas.

### <a name="thread-suspension"></a>Suspensão do fio

Os fios de aplicação podem suspender enquanto aguardam bytes de memória de uma piscina. Quando a memória contígua suficiente fica disponível, os fios suspensos recebem a sua memória solicitada e os fios são retomados.

Se várias linhas forem suspensas na mesma piscina de byte de memória, são-lhes dadas memória (retomada) na ordem em que foram suspensas (FIFO).

No entanto, o reinício prioritário também é possível se a aplicação ligar ***tx_byte_pool_prioritize*** antes da chamada de lançamento byte que levanta a suspensão do fio. A piscina byte prioriza o serviço coloca o fio de prioridade mais alto na parte da frente da lista de suspensão, deixando todos os outros fios suspensos na mesma ordem FIFO.

### <a name="run-time-byte-pool-performance-information"></a>Informações de desempenho do byte pool em tempo de execução

A ThreadX fornece informações opcionais de desempenho do byte pool. Se a biblioteca e aplicação ThreadX forem construídas com ***TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO*** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

  - dotações

  - versões

  - fragmentos pesquisados

  - fragmentos fundidos

  - fragmentos criados

  - suspensões de atribuição

  - intervalos de atribuição

Número total para cada piscina byte:

  - dotações

  - versões

  - fragmentos pesquisados

  - fragmentos fundidos

  - fragmentos criados

  - suspensões de atribuição

  - intervalos de atribuição

Esta informação está disponível no tempo de execução através dos serviços ***tx_byte_pool_performance_info_get** _ e _*_tx_byte_pool_performance_system_info_get_**. As informações sobre o desempenho da piscina byte são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação. Por exemplo, um número relativamente elevado de "suspensões de atribuição" pode sugerir que o byte pool é demasiado pequeno.

### <a name="memory-byte-pool-control-block-tx_byte_pool"></a>TX_BYTE_POOL do bloco de controlo de piscinas Byte de memória

As características de cada piscina de byte de memória encontram-se no seu bloco de controlo. Contém informações úteis, como o número de bytes disponíveis na piscina. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo da piscina também podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="nondeterministic-behavior"></a>Comportamento não determinista

Embora as piscinas de byte de memória forneçam a alocação de memória mais flexível, também sofrem de um comportamento algo não determinista. Por exemplo, um byte de memória pode ter 2.000 bytes de memória disponíveis, mas pode não ser capaz de satisfazer um pedido de atribuição de 1.000 bytes. Isto porque não há garantias sobre quantos bytes gratuitos são contíguos. Mesmo que exista um bloco livre de 1.000 bytes, não há garantias sobre quanto tempo pode demorar a encontrar o bloco. É completamente possível que todo o pool de memórias tenha de ser pesquisado para encontrar o bloco de 1.000 bytes.

> [!TIP]
> *Como resultado do comportamento não determinado das piscinas byte de memória, é geralmente uma boa prática evitar o uso de serviços de byte de memória em áreas onde é necessário comportamento determinístico e em tempo real. Muitas aplicações pré-alocam a memória necessária durante a inicialização ou configuração do tempo de execução.*

### <a name="overwriting-memory-blocks"></a>Sobreescrita de blocos de memória

É importante garantir que o utilizador da memória atribuída não escreva fora dos seus limites. Se isso acontecer, a corrupção ocorre numa área de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes catastróficos para a execução do programa.

## <a name="application-timers"></a>Temporizadores de aplicação

A resposta rápida a eventos externos assíncronos é a função mais importante das aplicações em tempo real e incorporadas. No entanto, muitas destas aplicações também devem realizar determinadas atividades em intervalos de tempo pré-determinados.

Os temporizadores de aplicação ThreadX fornecem aplicações com a capacidade de executar funções de aplicação C em intervalos de tempo específicos. Também é possível que um temporizador de aplicação expire apenas uma vez. Este tipo de temporizador é chamado de *temporizador de um só tiro,* enquanto os temporizadores de intervalo repetidos são *chamados temporizadores periódicos*.

Cada temporizador de aplicação é um recurso público. A ThreadX não coloca constrangimentos na forma como os temporizadores de aplicação são utilizados.

### <a name="timer-intervals"></a>Intervalos de temporizador

Nos intervalos de tempo ThreadX são medidos por interrupções periódicas do temporizador. Cada interrupção do temporizador é chamada de *tique-taque do temporizador*. O tempo real entre os tiques temporizadores é especificado pela aplicação, mas 10ms é a norma para a maioria das implementações. A configuração do temporizador periódico é tipicamente encontrada no ficheiro de montagem ***tx_initialize_low_level.***

Vale a pena referir que o hardware subjacente deve ter a capacidade de gerar interrupções periódicas para que os temporizadores de aplicação funcionem. Em alguns casos, o processador tem uma capacidade de interrupção periódica incorporada. Se o processador não tiver esta capacidade, a placa do utilizador deve ter um dispositivo periférico que possa gerar interrupções periódicas.

> [!IMPORTANT]
> *O ThreadX ainda pode funcionar mesmo sem uma fonte de interrupção periódica. No entanto, todo o processamento relacionado com o temporizador é então desativado. Isto inclui a suspensão, os tempos de suspensão e os serviços de temporizador.*

### <a name="timer-accuracy"></a>Precisão do temporizador

As expirações do temporizador são especificadas em termos de carraças. O valor de expiração especificado é diminuído por um em cada tique-taque do temporizador. Como um temporizador de aplicação pode ser ativado pouco antes de uma interrupção do temporizador (ou marcação do temporizador), o tempo de validade real pode ser até um tique mais cedo.

Se a taxa de marcação do temporizador for de 10ms, os temporizadores de aplicação podem expirar até 10ms mais cedo. Isto é mais significativo para temporizadores de 10ms do que 1 segundo temporizadores. É claro que o aumento da frequência de interrupção do temporizador diminui esta margem de erro.

### <a name="timer-execution"></a>Execução do Temporizador

Os temporizadores de aplicação executam na ordem em que se tornam ativos. Por exemplo, se três temporizadores forem criados com o mesmo valor de expiração e ativados, as respetivas funções de expiração são garantidas para executar na ordem em que foram ativados.

### <a name="creating-application-timers"></a>Criação de Temporizadores de Aplicações

Os temporizadores de aplicação são criados durante a inicialização ou durante o tempo de funcionamento por fios de aplicação. Não existe limite para o número de temporizadores de aplicação num pedido.

### <a name="run-time-application-timer-performance-information"></a>Informações de desempenho do tempo de execução do tempo de aplicação

A ThreadX fornece informações opcionais de desempenho do tempo de execução da aplicação. Se a biblioteca e aplicação ThreadX forem construídas com **TX_TIMER_ENABLE_PERFORMANCE_INFO** definidas, a ThreadX acumula as seguintes informações.

Número total do sistema global:

- ativações

- desativações

- reativações (temporizadores periódicos)

- expirações

- ajustamentos de caducidade

Número total de cada temporizador de aplicação:

- ativações

- desativações

- reativações (temporizadores periódicos)

- expirações

- ajustamentos de caducidade

Esta informação está disponível no tempo de execução através dos serviços ***tx_timer_performance_info_get** _ e _*_tx_timer_performance_system_info_get_**. As informações de desempenho do Tempo de Aplicação são úteis para determinar se a aplicação está a comportar-se corretamente. Também é útil para otimizar a aplicação.

### <a name="application-timer-control-block-tx_timer"></a>TX_TIMER do bloco de controlo do temporizador de aplicação

As características de cada temporizador de aplicação encontram-se no seu bloco de controlo. Contém informações úteis, como o valor de identificação de 32 bits de validade. Esta estrutura é definida no ficheiro ***tx_api.h.***

Os blocos de controlo do temporizador de aplicação podem ser localizados em qualquer lugar da memória, mas é mais comum fazer do bloco de controlo uma estrutura global definindo-o fora do âmbito de qualquer função.

### <a name="excessive-timers"></a>Temporizadores excessivos

Por predefinição, os temporizadores de aplicação executam a partir de um fio de sistema oculto que funciona na prioridade zero, que é tipicamente maior do que qualquer fio de aplicação. Por isso, o processamento dos temporizadores de aplicação internos deve ser mantido ao mínimo.

Também é importante evitar, sempre que possível, temporizadores que expiram a cada tique-taque do temporizador. Tal situação pode induzir sobrecargas excessivas no pedido.

> [!IMPORTANT]
> *Como mencionado anteriormente, os temporizadores de aplicação são executados a partir de um fio de sistema oculto. Por isso, é importante não selecionar a suspensão em quaisquer chamadas de serviço ThreadX efetuadas dentro da função de expiração do temporizador da aplicação.*

## <a name="relative-time"></a>Tempo Relativo

Além dos temporizadores de aplicação mencionados anteriormente, a ThreadX fornece um único contador de tique-taque de 32 bits continuamente. O contador de tique-taque ou *o tempo* é aumentado por um em cada interrupção do temporizador.

A aplicação pode ler ou definir este contador de 32 bits através de chamadas para ***tx_time_get** _ e _*_tx_time_set_**, respectivamente. A utilização deste contador de carraças é determinada completamente pela aplicação. Não é utilizado internamente pela ThreadX.

## <a name="interrupts"></a>Interrupções

A resposta rápida a eventos assíncronos é a função principal das aplicações incorporadas em tempo real. A aplicação sabe que tal evento está presente através de interrupções de hardware.

Uma interrupção é uma mudança assíncronea na execução do processador. Normalmente, quando ocorre uma interrupção, o processador *Interrupts* guarda uma pequena parte da execução atual na pilha e transfere o controlo para o vetor de interrupção apropriado. O vetor de interrupção é basicamente apenas o endereço da rotina responsável pelo manuseamento do tipo específico de interrupção. O procedimento exato de manuseamento da interrupção é específico do processador.

### <a name="interrupt-control"></a>Controlo de Interrupção

O ***serviço tx_interrupt_control*** permite que as aplicações ativem e desativem as interrupções. A postura de ativação/desativação anterior é devolvida por este serviço. É importante mencionar que o controlo de interrupção só afeta o segmento do programa atualmente executado. Por exemplo, se um fio desativar interrompe, eles só permanecem desativadas durante a execução desse fio.

> [!NOTE]
> *Uma Interrupção Não Mascarada (NMI) é uma interrupção que não pode ser desativada pelo hardware. Tal interrupção pode ser utilizada por aplicações ThreadX. No entanto, a rotina de manuseamento do NMI da aplicação não está autorizada a utilizar a gestão de contexto da ThreadX ou quaisquer serviços de API.*

### <a name="threadx-managed-interrupts"></a>Interrupções geridas pela ThreadX

A ThreadX fornece aplicações com uma gestão completa da interrupção. Esta gestão inclui a poupança e restauro do contexto da execução interrompida. Além disso, a ThreadX permite que certos serviços sejam chamados a partir de rotinas de serviço de interrupção (ISRs). Segue-se uma lista de serviços ThreadX permitidos a partir de ISRs de aplicação.

```c
tx_block_allocate
tx_block_pool_info_get tx_block_pool_prioritize
tx_block_pool_performance_info_get
tx_block_pool_performance_system_info_get tx_block_release
tx_byte_pool_info_get tx_byte_pool_performance_info_get
tx_byte_pool_performance_system_info_get
tx_byte_pool_prioritize tx_event_flags_info_get
tx_event_flags_get tx_event_flags_set
tx_event_flags_performance_info_get
tx_event_flags_performance_system_info_get
tx_event_flags_set_notify tx_interrupt_control
tx_mutex_performance_info_get
tx_mutex_performance_system_info_get tx_queue_front_send
tx_queue_info_get tx_queue_performance_info_get
tx_queue_performance_system_info_get tx_queue_prioritize
tx_queue_receive tx_queue_send tx_semaphore_get
tx_queue_send_notify tx_semaphore_ceiling_put
tx_semaphore_info_get tx_semaphore_performance_info_get
tx_semaphore_performance_system_info_get
tx_semaphore_prioritize tx_semaphore_put tx_thread_identify
tx_semaphore_put_notify tx_thread_entry_exit_notify
tx_thread_info_get tx_thread_resume
tx_thread_performance_info_get
tx_thread_performance_system_info_get
tx_thread_stack_error_notify tx_thread_wait_abort tx_time_get
tx_time_set tx_timer_activate tx_timer_change
tx_timer_deactivate tx_timer_info_get
tx_timer_performance_info_get
tx_timer_performance_system_info_get
```

> [!IMPORTANT]
> *A suspensão não é permitida a partir de ISRs. Por isso, o parâmetro **wait_option** para todas as chamadas de serviço ThreadX efetuadas a partir de um ISR deve ser definido para **TX_NO_WAIT**.*

### <a name="isr-template"></a>Modelo ISR

Para gerir as interrupções de aplicação, vários utilitários ThreadX devem ser chamados no início e no fim da aplicação ISRs. O formato exato para interromper o manuseamento varia entre as portas.

O seguinte pequeno segmento de código é típico da maioria dos ISRs geridos pela ThreadX. Na maioria dos casos, este processamento está em linguagem de montagem.

```c
_application_ISR_vector_entry:

; Save context and prepare for

; ThreadX use by calling the ISR

; entry function.

CALL _tx_thread_context_save

; The ISR can now call ThreadX

; services and its own C functions

; When the ISR is finished, context

; is restored (or thread preemption)

; by calling the context restore ; function. Control does not return!

JUMP _tx_thread_context_restore
```

### <a name="high-frequency-interrupts"></a>Interrupções de alta frequência

Algumas interrupções ocorrem numa frequência tão alta que poupar e restaurar todo o contexto em cada interrupção consumiria uma largura de banda de processamento excessiva. Nestes casos, é comum que a aplicação tenha uma pequena linguagens de montagem ISR que faz uma quantidade limitada de processamento para a maioria destas interrupções de alta frequência.

Após um certo ponto no tempo, o pequeno ISR pode precisar de interagir com o ThreadX. Isto é conseguido através da chamada das funções de entrada e saída descritas no modelo acima.

### <a name="interrupt-latency"></a>Interromper a latência

A ThreadX bloqueia as interrupções durante breves períodos de tempo. A quantidade máxima de tempo desativada está na ordem do tempo necessária para guardar ou restaurar o contexto de um fio.
