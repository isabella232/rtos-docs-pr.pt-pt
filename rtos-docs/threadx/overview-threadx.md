---
title: Compreenda Azure RTOS ThreadX
description: Saiba mais sobre o Azure ThreadX, um avançado sistema operativo em tempo real (RTOS) projetado especificamente para aplicações profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2021
ms.service: rtos
ms.topic: overview
ms.custom: contperf-fy21q4
ms.openlocfilehash: 300307a82cfde9c74ec0a2499528898b384076676f75bd592fa2840bc5ac53a8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796309"
---
# <a name="overview-of-azure-rtos-threadx"></a>Visão geral do Azure RTOS ThreadX

AZure RTOS ThreadX é o avançado sistema operativo Real-Time industrial da Microsoft (RTOS). É projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT. A Azure RTOS ThreadX fornece horários avançados, comunicação, sincronização, temporizador, gestão de memória e instalações de gestão de interrupção. Além disso, o Azure RTOS ThreadX tem muitas características avançadas: incluindo a sua arquitetura picokernel™, limiar de preemção™ agendamento, acorrentação de eventos™ perfis de execução, métricas de desempenho e rastreio de eventos do sistema. Combinado com a sua facilidade de utilização superior, o Azure RTOS ThreadX é a escolha ideal para as aplicações mais exigentes. O Azure RTOS ThreadX tem milhares de milhões de implantações em uma grande variedade de produtos, incluindo dispositivos de consumo, eletrónica médica e equipamentos de controlo industrial.

## <a name="threadx-footprint"></a>Pegada ThreadX

A Azure RTOS ThreadX tem uma área de instrução de 2 KB notavelmente pequena e 1 KB de pegada mínima RAM. Este pequeno tamanho deve-se em grande parte à sua arquitetura picokernel não em camadas e ao escalonamento automático. O dimensionamento automático significa que apenas os serviços (e infraestruturas de apoio) utilizados pela aplicação estão incluídos na imagem final no momento do link.

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

## <a name="threadx-execution-speed"></a>Velocidade de execução ThreadX

O Azure RTOS ThreadX consegue um interruptor de contexto sub-microsegundo nos processadores mais populares e é mais rápido em geral do que outros RTOS comerciais. Além de ser rápido, o Azure RTOS ThreadX também é altamente determinístico. Consegue o mesmo desempenho rápido, quer existam 200 fios prontos, ou apenas um.

Aqui estão algumas características típicas de desempenho da Azure RTOS ThreadX:

* Arranque rápido: Botas Azure RTOS ThreadX em menos de 120 ciclos.
* Remoção opcional da verificação de erros básicos: A verificação de erros básicos de Azure RTOS ThreadX pode ser ignorada na hora da compilação. Isto pode ser útil quando o código de aplicação é verificado e já não requer verificação de erros em cada parâmetro. A verificação de erros pode ser feita numa unidade de compilação, em vez de ser feita em todo o sistema.
* Design picokernel: Os serviços não são em camadas uns sobre os outros, eliminando a sobrecarga de chamada de função desnecessária.
* Processamento de interrupção otimizado: Apenas as verificações de risco são guardadas/restauradas após a entrada/saída do ISR, a menos que seja necessária uma pré-colocação.
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

    **Números de desempenho baseados no processador típico a funcionar a 200 MHz*.

## <a name="advanced-technology"></a>Tecnologia avançada

A Azure RTOS ThreadX é notável pelo seu agendamento de limiar de pré-edição. Esta funcionalidade é exclusiva da Azure RTOS ThreadX e tem sido alvo de uma extensa investigação académica. Você pode aprender mais com o trabalho [Agendando Fixed-Priority Tarefas com Preemption Threshold](https://ieeexplore.ieee.org/document/811269), por Yun Wang (Universidade de Concordia) e Manas Saksena (Universidade de Pittsburgh).

Principais capacidades da Azure RTOS ThreadX:

* Instalações multitarefas completas e abrangentes
  * Threads, temporizadores de aplicação, filas de mensagens, semafores contando, mutantes, bandeiras de eventos, bloco e piscinas de memória byte
* Agendamento Preventivo Priority-Based
* Flexibilidade Prioritária - Até 1024 Níveis Prioritários
* Agendamento Cooperativo
* Preemption-Threshold – Exclusivo para Azure RTOS ThreadX, ajuda a reduzir os interruptores de contexto e ajuda a garantir a agendabilidade (por investigação académica)
* Proteção da memória através de módulos Azure RTOS ThreadX
* Totalmente determinístico
* Trace de eventos – Capture os últimos eventos *do* sistema/aplicação n
* Chaining de Eventos – Registe uma função de chamada "notificação" específica para cada objeto de comunicação ou sincronização Azure RTOS ThreadX
* Módulos Azure RTOS ThreadX com Proteção Opcional de Memória
* Métricas de Desempenho Run-Time
  * Número de resuflações de fios
  * Número de suspensões por fios
  * Número de pré-esvaziações de fio solicitado
  * Número de linhas assíncronos interrompem pré-esvaziadas
  * Número de inversões prioritárias de linha
  * Número de renúncias de fio
* Kit de perfil de execução (EPK)
* Pilha de interrupção separada
* Análise da pilha de Run-Time
* Processamento de interrupção de temporizador otimizado

## <a name="multicore-support-amp--smp"></a>Suporte multicore (AMP & SMP)

O Standard Azure RTOS ThreadX é frequentemente utilizado numa moda multiprocessa assimétrica (AMP), onde uma cópia separada do Azure RTOS ThreadX e a aplicação (ou Linux) executa em cada núcleo e comunica entre si através de memória partilhada ou de um mecanismo de comunicação interprocessador como o OpenAMP (Azure RTOS ThreadX suporta OpenAMP).

Em ambientes onde os processadores de carregamento são altamente dinâmicos, o Azure RTOS ThreadX Symmetric Multiprocessing (SMP) está disponível para as seguintes famílias de processadores:

* Cortex-Ax ARM
* Cortex-Rx ARM
* ARM Cortex-A5x 64-bit
* MIPS 34 K, 1004 K e interAptiv
* PowerPC
* Sinopsias ARC HS
* x86

A Azure RTOS ThreadX SMP realiza um equilíbrio dinâmico de carga entre *processadores n.* Permite que todos os recursos Azure RTOS ThreadX (filas, semáforos, bandeiras de eventos, piscinas de memória, etc.) sejam acedidos por qualquer fio em qualquer núcleo. O Azure RTOS ThreadX SMP permite a API API completa Azure RTOS ThreadX em todos os núcleos e introduz as seguintes novas APIs aplicáveis à operação SMP:

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a>Proteção da memória através de módulos Azure RTOS ThreadX

Um produto adicional chamado Azure RTOS ThreadX Modules permite que um ou mais fios de aplicação sejam agregados num "Módulo" que pode ser carregado e executado dinamicamente (ou executado no lugar) no alvo.

Os módulos permitem a atualização de campo, a fixação de erros e a partição do programa para permitir que as grandes aplicações ocupem apenas a memória necessária através de fios ativos.

Os módulos também têm um espaço de endereço separado do próprio Azure RTOS ThreadX. Isto permite que o Azure RTOS ThreadX coloque a proteção da memória (via MPU ou MMU) em torno do Módulo de modo a que o acesso acidental fora do módulo não seja capaz de corromper qualquer outro componente de software.

## <a name="misra-compliant"></a>Conformidade com o MISRA

O código fonte Azure RTOS ThreadX e Azure RTOS ThreadX SMP é compatível com MISRA-C: 2004 e MISRA C:2012. MISRA C é um conjunto de diretrizes de programação para sistemas críticos utilizando a linguagem de programação C. As diretrizes originais do MISRA C destinavam-se principalmente a aplicações para automóveis; no entanto, o MISRA C é hoje amplamente reconhecido como sendo aplicável a qualquer aplicação crítica de segurança. A Azure RTOS ThreadX está em conformidade com todas as regras necessárias e obrigatórias da MISRA-C: 2004 e MISRA C:2012.

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificação Misra":::

## <a name="supports-most-popular-tools"></a>Suporta as ferramentas mais populares

O Azure RTOS ThreadX suporta as ferramentas de desenvolvimento incorporadas mais populares, incluindo a Bancada de Trabalho Incorporada da IAR, que também tem a mais abrangente consciência de kernel Azure RTOS ThreadX disponível. Outras integrações de ferramentas incluem GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench, Imagination Codescape, Renesas e2studio, Metaware SeeCode, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore e todos os dispositivos analógicos.

## <a name="adaptation-layer-for-threadx"></a>Camada de adaptação para ThreadX

Pode facilitar os problemas de migração de aplicações para o Azure RTOS utilizando [camadas de adaptação](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) ThreadX para várias APIs RTOS (FreeRTOS, POSIX, OSEK, etc.)

> [!div class="nextstepaction"]
> [Introdução ao Azure RTOS ThreadX](chapter1.md)