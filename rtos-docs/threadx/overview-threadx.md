---
title: Compreenda Azure RTOS ThreadX
description: Azure ThreadX é um sistema operativo avançado em tempo real (RTOS) projetado especificamente para aplicações profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0fb861c2291046c2ac6edf1d03014996daa09a8e
ms.sourcegitcommit: c1b00341e0c5ab71372f3d9cc4ee3bdd3702b805
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111988367"
---
# <a name="overview-of-azure-rtos-threadx"></a>Visão geral do Azure RTOS ThreadX

Azure RTOS ThreadX é o avançado sistema operativo Real-Time de qualidade industrial da Microsoft (RTOS) projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT. A Azure RTOS ThreadX fornece horários avançados, comunicação, sincronização, temporizador, gestão de memória e instalações de gestão de interrupção. Além disso, o Azure RTOS ThreadX tem muitas funcionalidades avançadas, incluindo a sua arquitetura picokernel™, limiar de preemção™ agendamento, acorrentação de eventos™ perfis de execução, métricas de desempenho e rastreio de eventos do sistema. Combinado com a sua facilidade de utilização superior, o Azure RTOS ThreadX é a escolha ideal para as aplicações mais exigentes. A partir de 2017, a Azure RTOS ThreadX conta com mais de 6,2 mil milhões de implantações, numa grande variedade de produtos, incluindo dispositivos de consumo, eletrónica médica e equipamentos de controlo industrial.

## <a name="api-protocols"></a>Protocolos da API

### <a name="azure-rtos-threadx-services"></a>Serviços Azure RTOS ThreadX

* Criação dinâmica de fios
* Sem limites no número de fios
* As APIs do fio principal incluem:
  * tx_thread_create
  * tx_thread_delete
  * tx_thread_preemption_change
  * tx_thread_priority_change
  * tx_thread_relinquish
  * tx_thread_reset
  * tx_thread_resume
  * tx_thread_sleep
  * tx_thread_suspend
  * tx_thread_terminate
  * tx_thread_wait_abort
* APIs de informação adicional e desempenho

### <a name="message-queues"></a>Filas de mensagens

* Criação dinâmica de filas
* Sem limites no número de filas
* Mensagens copiadas por valor (ou por referência via ponteiro)
* Tamanhos de mensagem de 1 a 16 palavras de 32 bits
* Suspensão de fio opcional em vazio e cheio
* Tempo limite opcional em toda a suspensão
* As APIs principais da fila de mensagens incluem:
  * tx_queue_create
  * tx_queue_delete
  * tx_queue_flush
  * tx_queue_front_send
  * tx_queue_receive
  * tx_queue_send_notify
* APIs de informação adicional e desempenho

### <a name="counting-semaphores"></a>Contagem de Semáforos

* Criação de semáforos dinâmicos
* Não há limites para o número de semáforos
* Semáforos de contagem de 32 bits (0 a 4.294.967.295)
* Apoia o produtor-consumidor ou a proteção de recursos
* Suspensão de fio opcional quando semáforo indisponível
* Tempo limite opcional em toda a suspensão
* As PRINCIPAis APIs de semáforo incluem:
  * tx_semaphore_create
  * tx_semaphore_delete
  * tx_semaphore_get
  * tx_semaphore_put
  * tx_semaphore_put_notify
* APIs de informação adicional e desempenho

### <a name="mutexes"></a>Mutaxos

* Criação de mutex dinâmico
* Sem limites no número de mutantes
* Proteção de recursos aninhada suportada
* Herança prioritária opcional apoiada
* Suspensão de fio opcional quando mutex indisponível
* Tempo limite opcional em toda a suspensão
* As principais APIs mutex incluem:
  * tx_mutex_create
  * tx_mutex_delete
  * tx_mutex_get
  * tx_mutex_put
* APIs de informação adicional e desempenho

### <a name="event-flags"></a>Bandeiras do evento

* Criação dinâmica do grupo de bandeira de evento
* Não há limites para o número de grupos de bandeira de eventos
* Sincronização de um fio ou fios múltiplos
* Atómico obter e claro suporte
* Suspensão multilêssida opcional em conjunto de eventos E/OR
* Tempo limite opcional em toda a suspensão
* As APIs da bandeira do evento principal incluem:
  * tx_event_flags_create
  * tx_event_flags_delete
  * tx_event_flags_get
  * tx_event_flags_set
  * tx_event_flags_set_notify
* APIs de informação adicional e desempenho

### <a name="block-memory-pools"></a>Bloquear piscinas de memória

* Criação dinâmica de piscina de blocos
* Não há limites para o número de piscinas de blocos
* Sem limites de tamanho de blocos de tamanho fixo ou tamanho de piscina
* Alocação de memória/localização de negócio o mais rápido possível
* Suspensão de fio opcional na piscina vazia
* Tempo limite opcional em toda a suspensão
* As APIs da piscina principal incluem:
  * tx_block_pool_create
  * tx_block_pool_delete
  * tx_block_allocate
  * tx_block_release
* APIs de informação adicional e desempenho

### <a name="byte-memory-pools"></a>Piscinas de memória Byte

* Criação dinâmica da piscina byte
* Não há limites para o número de piscinas byte
* Sem limites no tamanho da piscina byte
* A atribuição/locação de memória de comprimento variável mais flexível
* Localidade de tamanho de alocação suportada
* Suspensão de fio opcional na piscina vazia
* Tempo limite opcional em toda a suspensão
* As APIs da piscina principal incluem:
  * tx_byte_pool_create
  * tx_byte_pool_delete
  * tx_byte_allocate
  * tx_byte_release
* APIs de informação adicional e desempenho

### <a name="application-timers"></a>Temporizadores de aplicação

* Criação de temporizador dinâmico
* Não há limites no número de temporizadores
* Temporizadores periódicos ou de um tiro suportados
* Temporizadores periódicos podem ter diferente valor inicial de expiração
* Sem pesquisa sobre ativação ou desativação do temporizador
* Todos os temporizadores conduzidos de um temporizador de hardware interrompem
* As APIs do temporizador principal incluem:
  * tx_timer_create
  * tx_timer_delete
  * tx_timer_activate
  * tx_timer_change
  * tx_timer_deactivate
* APIs de informação adicional e desempenho

### <a name="azure-rtos-threadx-core-scheduler"></a>Azure RTOS ThreadX Core Scheduler

* Pegada mínima de 2KB FLASH,1KB RAM
* Interruptor de contexto rápido e sub-microsegundo
* Totalmente determinístico independentemente do número de fios
* Agendamento prioritário e totalmente preventivo
* 32 níveis de prioridade padrão, opcionalmente até níveis de 1024
* Agendamento cooperativo dentro do nível prioritário (FIFO)
* Tecnologia limiar de pré-edição
* Serviços de temporizador opcional, incluindo:
  * Fatia de tempo opcional por thread
  * Tempo limite opcional em todos os bloqueios
  * APIs requer interrupção do temporizador de hardware
* Perfis de execução
* Vestígios de nível de sistema
* Segurança certificada para muitas normas

## <a name="most-deployed-rtos"></a>RTOS mais implantado

A Azure RTOS ThreadX tem mais de 6,2 mil milhões de implantações em todo o mundo, de acordo com a empresa líder de inteligência de mercado M2M, a VDC Research. A popularidade da Azure RTOS ThreadX é um testemunho da sua fiabilidade, qualidade, tamanho, desempenho, funcionalidades avançadas, facilidade de utilização e vantagens gerais de tempo para mercado.

> *"Temos acompanhado a trajetória de crescimento da THREADX nos mercados sem fios e IoT desde a fundação da empresa, e estamos cada vez mais impressionados com a adoção generalizada da THREADX pela indústria."* – Chris Rommel, Vice-Presidente Executivo, VDC Research

## <a name="small-footprint"></a>Pequena pegada

A Azure RTOS ThreadX requer uma área de instrução 2KB notavelmente pequena e 1KB de RAM para a sua pegada mínima. Isto deve-se, em grande parte, à sua arquitetura picokernel™ não em camadas e à escala automática. O dimensionamento automático significa que apenas os serviços (e infraestruturas de apoio) utilizados pela aplicação estão incluídos na imagem final no momento do link.

Aqui estão algumas características típicas do tamanho Azure RTOS ThreadX.

|Serviço Azure RTOS ThreadX  |Tamanho típico em bytes  |
|---------|---------|
|Serviços centrais (Exigir) |2.000  |
|Serviços de fila  |900  |
|Serviços de Bandeira de Eventos  |900  |
|Serviços Semáforos  |450  |
|Serviços Mutex  |1200  |
|Bloquear serviços de memória  |550  |
|Serviços de Memória Byte  |900  |

## <a name="fast-execution"></a>Execução rápida

O Azure RTOS ThreadX consegue um interruptor de contexto sub-microsegundo nos processadores mais populares e é significativamente mais rápido em termos globais do que outros RTOSes comerciais. Além de ser rápido, o Azure RTOS ThreadX também é altamente determinístico. Consegue o mesmo desempenho rápido, quer existam 200 fios prontos, ou apenas um.

Aqui estão algumas características típicas de desempenho da Azure RTOS ThreadX:

* Arranque Rápido: Botas Azure RTOS ThreadX em menos de 120 ciclos.
* Remoção opcional da verificação de erros básicos: A verificação de erros básicos de Azure RTOS ThreadX pode ser ignorada na hora da compilação. Isto pode ser útil quando o código de aplicação é verificado e já não requer verificação de erros em cada parâmetro. Note que isto pode ser feito numa unidade de compilação, em vez de em todo o sistema.
* Picokernel™ Design: Os serviços não estão em camadas uns sobre os outros, eliminando assim a sobrecarga de chamada de função desnecessária.
* *Processamento de interrupção otimizado: Apenas registos de risco são guardados/restaurados após a entrada/saída do ISR, a menos que seja necessário uma pré-colocação.
* Processamento otimizado da API:

    |Serviço Azure RTOS ThreadX  |Tempo de serviço em Microsegundos*  |
    |---------|---------|
    |Suspensão do fio  |0.6  |
    |Resumo da linha  |0.6  |
    |Enviar fila  |0.3  |
    |Receber fila  |0.3  |
    |Obter Semáforo  |0,2  |
    |Coloque o Semáforo  |0,2  |
    |Interruptor de contexto  |0,4  |
    |Interrupção da resposta  |0.0 – 0.6  |

    **Números de desempenho baseados no processador típico a funcionar a 200MHz*.

## <a name="advanced-technology"></a>Tecnologia avançada

Azure RTOS ThreadX é uma tecnologia avançada cuja característica mais notável é o agendamento do limiar de pré-edição. Esta funcionalidade é exclusiva da Azure RTOS ThreadX e tem sido alvo de uma extensa investigação académica. Por exemplo, ver [Agendar Fixed-Priority Tarefas com Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), por Yun Wang, Universidade de Concordia, e Manas Saksena, Universidade de Pittsburgh.

Considere as capacidades da Azure RTOS ThreadX.

* Instalações multitarefas completas e abrangentes
  * Threads, temporizadores de aplicação, filas de mensagens, semafores contando, mutantes, bandeiras de eventos, bloco e piscinas de memória byte
* Agendamento Preventivo Priority-Based
* Flexibilidade Prioritária - Até 1024 Níveis Prioritários
* Agendamento Cooperativo
* Preemption-Threshold™ – Exclusivo para Azure RTOS ThreadX, ajuda a reduzir os interruptores de contexto e ajuda a garantir agendabilidade (por investigação académica)
* Proteção da memória através de módulos Azure RTOS ThreadX
* Totalmente determinístico
* Trace de eventos – Capture os últimos eventos *do* sistema/aplicação n
* Chaining de Eventos™ – Registe uma função de chamada "notificação" específica para cada objeto de comunicação ou sincronização Azure RTOS ThreadX
* Módulos Azure RTOS ThreadX com Proteção Opcional de Memória
* Métricas de Desempenho Run-Time
  * Número de resuflações de fios
  * Número de suspensões por fios
  * Número de preemposições de fio solicitadas
  * Número de preemposições de interrupção de linha assíncrona
  * Número de inversões prioritárias de linha
  * Número de renúncias de fio
* Kit de perfil de execução (EPK)
* Pilha de interrupção separada
* Análise da pilha de Run-Time
* Processamento de interrupção de temporizador otimizado

## <a name="multicore-support-amp--smp"></a>Suporte multicore (AMP & SMP)

O Standard Azure RTOS ThreadX é frequentemente utilizado numa moda multiprocessa assimétrica (AMP), onde uma cópia separada do Azure RTOS ThreadX e a aplicação (ou Linux) executam em cada núcleo e comunicam entre si através de memória partilhada ou de um mecanismo de comunicação interprocessador, como o OpenAMP (Azure RTOS ThreadX suporta o OpenAMP). Esta é a configuração multicore mais típica usando o Azure RTOS ThreadX e pode ser a mais eficiente se a aplicação for capaz de carregar eficazmente os processadores.

Para ambientes onde o carregamento dos processadores é altamente dinâmico, o Azure RTOS ThreadX Symetric Multiprocessing (SMP) está disponível para as seguintes famílias de processadores:

* Cortex-Ax ARM
* Cortex-Rx ARM
* ARM Cortex-A5x 64-bit
* MIPS 34K, 1004K e interAptiv
* PowerPC
* Sinopsias ARC HS
* x86

A Azure RTOS ThreadX SMP executa o equilíbrio dinâmico da carga entre processadores *n* e permite que todos os recursos Azure RTOS ThreadX (filas, semáforos, bandeiras de eventos, piscinas de memória, etc.) sejam acedidos por qualquer fio em qualquer núcleo. A Azure RTOS ThreadX SMP permite a API API completa Azure RTOS ThreadX em todos os núcleos e introduz os seguintes novos API aplicáveis à operação SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Proteção da memória através de módulos Azure RTOS ThreadX

Um produto adicional chamado Azure RTOS ThreadX MODULES permite que um ou mais fios de aplicação sejam agregados num "Módulo" que pode ser carregado e executado dinamicamente (ou executado no lugar) no alvo.

Os módulos permitem a atualização de campo, a fixação de erros e a partição do programa para permitir que as grandes aplicações ocupem apenas a memória necessária através de fios ativos.

Os módulos também têm um espaço de endereço completamente separado do próprio Azure RTOS ThreadX. Isto permite que o Azure RTOS ThreadX coloque a proteção da memória (via MPU ou MMU) em torno do Módulo de modo a que o acesso acidental fora do módulo não seja capaz de corromper qualquer outro componente de software.

## <a name="misra-compliant"></a>Conformidade com o MISRA

O código de souce Azure RTOS ThreadX e Azure RTOS ThreadX SMP é compatível com MISRA-C:2004 e MISRA C:2012. MISRA C é um conjunto de diretrizes de programação para sistemas críticos utilizando a linguagem de programação C. As diretrizes originais do MISRA C destinavam-se principalmente a aplicações para automóveis; no entanto, o MISRA C é hoje amplamente reconhecido como sendo aplicável a qualquer aplicação crítica de segurança. O Azure RTOS ThreadX está em conformidade com todas as regras necessárias e obrigatórias de MISRA-C:2004 e MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificação Misra":::

## <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

O Azure RTOS ThreadX funciona em microprocessadores de 32/64 bits mais populares, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:

* Dispositivos Analógicos: SHARC, Blackfin, CM4xx
* Núcleo de Andes: RISC-V
* Ambiqmicro: Apollo MCUs
* ARM: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M
* Cadência: Xtensa, Diamante
* CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi
* Cipreste: RISC-V
* EnSilica: eSi-RISC
* Infineon: XMC1000, XMC4000, TriCore
* Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10
* Microchip: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32
* Microsemi: RISC-V
* NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4
* Renesas: SH, HS, V850, RX, RZ, Sinergia
* Laboratórios de Silício: EFM32
* Sinopses: ARC 600, 700, ARC EM, ARC HS
* ST: STM32, ARM7, ARM9, Córtex-M3/M4/M7
* Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C
* Computação de ondas: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M
* Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="supports-most-popular-tools"></a>Suporta as ferramentas mais populares

O Azure RTOS ThreadX suporta as ferramentas de desenvolvimento incorporadas mais populares, incluindo a bancada de trabalho incorporada da IAR™, que também tem a mais abrangente consciência de kernel Azure RTOS ThreadX disponível. A integração adicional de ferramentas inclui GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore e todos os dispositivos analógicos.

## <a name="adaptation-layer-for-threadx"></a>Camada de adaptação para ThreadX

O Azure RTOS ThreadX é um sistema operativo em tempo real (RTOS) avançado criado especificamente para aplicações profundamente incorporadas. Para facilitar a migração de aplicações para Auzre RTOS, a ThreadX fornece [camadas de adaptação](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) para várias APIs RTOS (FreeRTOS, POSIX, OSEK, etc.)
