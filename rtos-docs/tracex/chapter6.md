---
title: Capítulo 6 - Azure RTOS ThreadX trace eventos
description: Este capítulo descreve os eventos Azure RTOS ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 9fefc43002d4e0d6df817ad56d79b3e41a3d649504be50f5a39f67c1896b2e9a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116800336"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a>Capítulo 6 - Azure RTOS ThreadX trace eventos

Este capítulo descreve os eventos Azure RTOS ThreadX. 

## <a name="list-of-events-and-icons"></a>Lista de eventos e ícones

Segue-se uma lista de eventos Da ThreadX apresentados pela TraceX:

| **Ícone**                         | **Significado** |
| -------------------------------- | ------------------------------------- |
| ![Ícone de retoma de fio interno](./media/user-guide/tx-events/image1.png)    | Currículo interno da linha  |
| ![Ícone de suspensão de fio interno](./media/user-guide/tx-events/image2.png)    | Suspensão do fio interno |
| ![Interrupção de função rotina introduzir ícone](./media/user-guide/tx-events/image3.png)    | Interrupção rotina de serviço (ISR) Entrar |
| ![Ícone de saída de rotina de serviço de interrupção](./media/user-guide/tx-events/image4.png)    | Interrupção de rotina de serviço (ISR) saída  |
| ![Ícone de fatia de tempo interna](./media/user-guide/tx-events/image5.png)    | Corte de tempo interna |
| ![Ícone de execução](./media/user-guide/tx-events/image6.png)    | Em Execução |
| ![Ícone de atribuição de piscina de bloco](./media/user-guide/tx-events/image7.png)    | **Atribuição de piscina de blocos** *(tx_block_allocate)*  |
| ![Bloco de piscina criar ícone](./media/user-guide/tx-events/image8.png)    | **Criação de piscina de** blocos *(tx_block_pool_create)* |
| ![Ícone de excluir piscina de bloco](./media/user-guide/tx-events/image9.png)    | **Excluir de piscina de blocos** *(tx_block_pool_delete)* |
| ![Informações de piscina de blocos obter ícone](./media/user-guide/tx-events/image10.png)    | **Informações de piscina de blocos obtêm** *(tx_block_pool_info_get)* |
| ![Informações de desempenho da piscina de blocos obter con](./media/user-guide/tx-events/image11.png)    | **Informações de desempenho do pool de blocos obtêm** *(tx_block_pool_performance_info_get)* |
| ![Informações de desempenho do sistema de piscina de blocos obtenham ícone](./media/user-guide/tx-events/image12.png)    | **Informações de desempenho do sistema de piscina de blocos obtêm** *(tx_block_pool_performance_system_info_get)* |
| ![Ícone de prioridade de piscina de bloco](./media/user-guide/tx-events/image13.png)    | **Prioridades de piscina de blocos** *(tx_block_pool_prioritize)* |
| ![Desbloqueio de bloco para ícone de piscina](./media/user-guide/tx-events/image14.png)    | **Desbloqueio do bloco para piscina** *(tx_block_release)* |
| ![Byte pool alocar ícone de memória](./media/user-guide/tx-events/image15.png)    | **Byte pool alocar memória** *(tx_byte_allocate)* |
| ![Byte pool criar ícone](./media/user-guide/tx-events/image16.png)    | **Byte pool create** *(tx_byte_pool_create)* |
| ![Ícone de exclusão da piscina byte](./media/user-guide/tx-events/image17.png)    | **Byte pool delete** *(tx_byte_pool_delete)* |
| ![Informações de piscina byte obter ícone](./media/user-guide/tx-events/image18.png)    | **Informações da piscina byte obtêm** *(tx_byte_pool_info_get)* |
| ![Informações de desempenho da piscina byte obter ícone](./media/user-guide/tx-events/image19.png)    | **Byte pool informações de desempenho get** *(tx_byte_pool_performance_info_get)* |
| ![Informações de desempenho do sistema de piscina byte recebem ícone](./media/user-guide/tx-events/image20.png)    | **Informações de desempenho do sistema de piscina byte obtêm** *(tx_byte_pool_performance_system_info_get)* |
| ![*Byte pool priorizar ícone](./media/user-guide/tx-events/image21.png)    | **Prioridades da piscina byte** *(tx_byte_pool_prioritize)* |
| ![Byte memory release para ícone de piscina](./media/user-guide/tx-events/image22.png)    | **Byte memory release para piscina** *(tx_byte_release)* |
| ![Bandeiras do evento criam ícone](./media/user-guide/tx-events/image23.png)    | **Bandeiras de eventos criam** *(tx_event_flags_create)* |
| ![Bandeiras do evento apagam ícone](./media/user-guide/tx-events/image24.png)    | **Bandeiras do evento apagam** *(tx_event_flags_delete)* |
| ![Bandeiras do evento recebem ícone](./media/user-guide/tx-events/image25.png)    | **Bandeiras do evento recebem** *(tx_event_flags_get)* |
| ![Informações de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image26.png)    | **Informações de bandeiras de eventos obtêm** *(tx_event_flags_info_get)* |
| ![Informações de desempenho de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image27.png)    | **As informações de desempenho das bandeiras do evento obtêm** *(tx_event_flags_performance_info_get)* |
| ![Informações de desempenho do sistema de bandeiras de eventos obtenham ícone](./media/user-guide/tx-events/image28.png)    | **As informações de desempenho do sistema de bandeiras de eventos obtêm** *(tx_event_flags_performance_system_info_get)* |
| ![Ícone de conjunto de bandeiras de evento](./media/user-guide/tx-events/image29.png)    | **Conjunto de bandeiras de eventos** *(tx_event_flags_set)* |
| ![Conjunto de bandeiras de eventos ícone de notificação](./media/user-guide/tx-events/image30.png)    | **As bandeiras do evento notificam** *(tx_event_flags_set_notify)* |
| ![Interromper o ícone de ativação/desativação](./media/user-guide/tx-events/image31.png)    | **Interromper ativar/desativar** *(tx_interrupt_control)* |
| ![Mutex criar ícone](./media/user-guide/tx-events/image32.png)    | **Criação mutex** *(tx_mutex_create)* |
| ![Ícone de exclusão de mutex](./media/user-guide/tx-events/image33.png)    | **Eliminação de mutaxos** *(tx_mutex_delete)* |
| ![Mutex obter ícone](./media/user-guide/tx-events/image34.png)    | **Mutex get** *(tx_mutex_get)* |
| ![Informações mutex obtêm ícone](./media/user-guide/tx-events/image35.png)    | **Informações mutex obtêm** *(tx_mutex_info_get)* |
| ![Informações de desempenho de Mutex obtêm ícone](./media/user-guide/tx-events/image36.png)    | **Informações de desempenho mutex obtêm** *(tx_mutex_performance_info_get)* |
| ![Informações de desempenho do sistema mutex obtêm ícone](./media/user-guide/tx-events/image37.png)    | **Informações de desempenho do sistema Mutex obtêm** *(tx_mutex_performance_system_info_get)* |
| ![Ícone de prioridades de Mutex](./media/user-guide/tx-events/image38.png)    | **Prioridades mutex** *(tx_mutex_prioritize)* |
| ![Mutex colocar ícone](./media/user-guide/tx-events/image39.png)    | **Mutex colocado** *(tx_mutex_put)* |
| ![Fila criar ícone](./media/user-guide/tx-events/image40.png)    | **Criação de fila** *(tx_queue_create)* |
| ![Ícone de exclusão de fila](./media/user-guide/tx-events/image41.png)    | **Excluir de filas** *(tx_queue_delete)* |
| ![Ícone de descarga de fila](./media/user-guide/tx-events/image42.png)    | **Flush de fila** *(tx_queue_flush)* |
| ![Ícone de envio de fila frontal](./media/user-guide/tx-events/image43.png)    | **Envio frontal de fila** *(tx_queue_front_send)* |
| ![Informações de fila recebem ícone](./media/user-guide/tx-events/image44.png)    | **Informações de fila obtêm** *(tx_queue_info_get)* |
| ![Informações de desempenho da fila obtêm ícone](./media/user-guide/tx-events/image45.png)    | **Informações de desempenho da fila obtêm** *(tx_queue_performance_info_get)* |
| ![Informações de desempenho do sistema de fila recebem ícone](./media/user-guide/tx-events/image46.png)    | **Informações de desempenho do sistema de fila obtêm** *(tx_queue_performance_system_info_get)* |
| ![Ícone de prioridade de fila](./media/user-guide/tx-events/image47.png)    | **Prioridades de fila** *(tx_queue_prioritize)* |
| ![Ícone de mensagem de receção de fila](./media/user-guide/tx-events/image48.png)    | **Mensagem de receção de fila** *(tx_queue_receive)* |
| ![Ícone de mensagem de envio de fila](./media/user-guide/tx-events/image49.png)    | **Mensagem de envio de fila** *(tx_queue_send)* |
| ![Fila enviar ícone de notificação](./media/user-guide/tx-events/image50.png)    | **Fila enviar notificação** *(tx_queue_send_notify)* |
| ![Teto de semáforo colocar ícone](./media/user-guide/tx-events/image51.png)    | **Teto de semáforo colocado** *(tx_semaphore_ceiling_put)* |
| ![Semáforo criar ícone](./media/user-guide/tx-events/image52.png)    | **Criação de semáforos** *(tx_semaphore_create)* |
| ![Ícone de exclusão de semáforo](./media/user-guide/tx-events/image53.png)    | **Eliminação de semáforos** *(tx_semaphore_delete)* |
| ![Semáforo obter ícone](./media/user-guide/tx-events/image54.png)    | **Semaphore get** *(tx_semaphore_get)* |
| ![Informações de semáforo recebem ícone](./media/user-guide/tx-events/image55.png)    | **Informações de semáforos obtêm** *(tx_semaphore_info_get)* |
| ![Informações de desempenho de semáforo obtêm ícone](./media/user-guide/tx-events/image56.png)    | **Informações de desempenho de semáforos obtêm** *(tx_semaphroe_performance_info_get)* |
| ![Informações de desempenho do sistema de semáforos recebem ícone](./media/user-guide/tx-events/image57.png)    | **Informações de desempenho do sistema semáforo obtêm** *(tx_semaphore_performance_system_info_get)* |
| ![Semáforo prioriza ícone](./media/user-guide/tx-events/image58.png)    | **Prioridades de semáforo** *(tx_semaphore_prioritize)* |
| ![Semáforo colocar ícone](./media/user-guide/tx-events/image59.png)    | **Semaphore put** *(tx_semaphore_put)* |
| ![Semáforo colocar ícone de notificação](./media/user-guide/tx-events/image60.png)    | **Semáforo colocar notificação** *(tx_semaphore_put_notify)* |
| ![Ícone de criação de fio](./media/user-guide/tx-events/image61.png)    | **Criação de fios** *(tx_thread_create)* |
| ![Ícone de exclusão de fio](./media/user-guide/tx-events/image62.png)    | **Eliminação de fios** *(tx_thread_delete)* |
| ![Ícone de notificação de saída/entrada de fio](./media/user-guide/tx-events/image63.png)    | **Notificação de saída/entrada de fio** *(tx_thread_entry_exit_notify)* |
| ![Ícone de identificação de fio](./media/user-guide/tx-events/image64.png)    | **Identificação de** fios *(tx_thread_identify)* |
| ![Informações de fio obter ícone](./media/user-guide/tx-events/image65.png)    | **Informações sobre fios obtêm** *(tx_thread_info_get)* |
| ![Informações de desempenho do fio obter ícone](./media/user-guide/tx-events/image66.png)    | **Informações de desempenho do fio obtêm** *(tx_thread_performance_info_get)* |
| ![Informações do sistema de desempenho do fio obtêm ícone](./media/user-guide/tx-events/image67.png)    | **Informações do sistema de desempenho de fio obtêm** *(tx_thread_performance_system_info_get)* |
| ![Ícone de mudança de mudança de preempção de fio](./media/user-guide/tx-events/image68.png)    | **Alteração da preempção do fio** *(tx_thread_preemption_change)* |
| ![Ícone de mudança de prioridade de fio](./media/user-guide/tx-events/image69.png)    | **Alteração prioritária do fio** *(tx_thread_priority_change)* |
| ![Ícone de renúncia de fio](./media/user-guide/tx-events/image70.png)    | **Renúncia à linha** *(tx_thread_relinquish)* |
| ![Ícone de reset de fio](./media/user-guide/tx-events/image71.png)    | **Reset de fio** *(tx_thread_reset)* |
| ![*Ícone de currículo de fio](./media/user-guide/tx-events/image72.png)    | **Resumo do fio** (**tx_thread_resume)* |
| ![Ícone de sono de fio](./media/user-guide/tx-events/image73.png)    | **Thread Sleep** *(tx_thread_sleep)** |
| ![Ícone de notificação de erro de pilha de fio](./media/user-guide/tx-events/image74.png)    | **Notificação de erro de pilha de fio** *(tx_thread_stack_error_notify)* |
| ![Ícone de suspensão de fio](./media/user-guide/tx-events/image75.png)    | **Suspensão do** fio *(tx_thread_suspend)* |
| ![Ícone de terminação de fio](./media/user-guide/tx-events/image76.png)    | **Fim da linha** *(tx_thread_terminate)* |
| ![Ícone de mudança de fatia de tempo de fio](./media/user-guide/tx-events/image77.png)    | **Alteração da fatia de tempo** do fio *(tx_thread_time_slice_change)* |
| ![Ícone de aborto de espera de fio](./media/user-guide/tx-events/image78.png)    | **Thread wait abort** *(tx_thread_wait_abort)* |
| ![Tempo obter ícone](./media/user-guide/tx-events/image79.png)    | **Time get** *(tx_time_get)* |
| ![Ícone de conjunto de tempo](./media/user-guide/tx-events/image80.png)    | **Tempo definido** *(tx_time_set)* |
| ![*Ícone de ativação do temporizador](./media/user-guide/tx-events/image81.png)    | **Ativador de temporizador** *(tx_timer_activate)* |
| ![Ícone de mudança de temporizador](./media/user-guide/tx-events/image82.png)    | **Alteração do temporizador** *(tx_timer_change)* |
| ![Ícone de criação de temporizador](./media/user-guide/tx-events/image83.png)    | **Criação do temporizador** *(tx_timer_create)* |
| ![Ícone de desativado temporizador](./media/user-guide/tx-events/image84.png)    | **Temporizador desativado** *(tx_timer_deactivate)* |
| ![Ícone de eliminação do temporizador](./media/user-guide/tx-events/image85.png)    | **Apagador do temporizador** *(tx_timer_delete)* |
| ![Informação de temporizador obter ícone](./media/user-guide/tx-events/image86.png)    | **Informações de temporizador obtêm** *(tx_timer_info_get)* |
| ![Informações de desempenho do temporizador obtêm ícone](./media/user-guide/tx-events/image87.png)    | **Informações de desempenho do temporizador obtêm** *(tx_timer_performance_info_get)* |
| ![*Informação do sistema de desempenho temporizador obter ícone](./media/user-guide/tx-events/image88.png)    | **Informações do sistema de desempenho do temporizador obtêm** *(tx_timer_performance_system_info_get)* |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | **Evento definido pelo utilizador** (ver capítulo 10)    |

## <a name="event-descriptions"></a>Descrições do evento

### <a name="internal-thread-resume"></a>Currículo interno da linha

#### <a name="internal-thread-resume"></a>Currículo interno da linha

**Ícone** ![ Ícone de retoma de fio interno](./media/user-guide/tx-events/image1.png)

**Descrição**

Este evento representa o processamento interno na ThreadX que retoma um fio para execução. Se o fio especificado for a maior prioridade e o limiar de pré-substituição não bloquear a sua execução, o sistema começará a executar este fio recém-pronto.

**Campos de Informação**

- Info Campo 1: Ponteiro para o fio que está a ser retomado.
- Info Field 2: Estado anterior da linha a ser retomada, da seguinte forma:

  |  Estado do fio                     | Valor        |
  |---------------------------------- | --------|
  |  TX_READY                         | 0       |
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Info Field 3: Empilhar o valor do ponteiro durante a chamada. 
- Info Field 4: Ponteiro para o próximo fio de prioridade máxima a executar.

### <a name="internal-thread-suspend"></a>Suspensão do fio interno

#### <a name="internal-thread-suspend"></a>Suspensão do fio interno

**Ícone** ![ Ícone de suspensão de fio interno](./media/user-guide/tx-events/image2.png)

**Descrição**

Este evento representa o processamento interno na ThreadX que suspende a execução de um fio. O próximo fio prioritário pronto para a execução é colocado no quarto campo de informação. Se este valor for NU, não há outro fio pronto para a execução e o sistema está inativo.

**Campos de Informação**

- Info Campo 1: Ponteiro para a linha suspensa.
- Info Field 2: Estado novo da linha suspensa, da seguinte forma:

  |  Estado do fio                     | Valor        |
  |---------------------------------- | --------|
  |  TX_COMPLETED                     | 1       |
  |  TX_TERMINATED                    | 2       |
  |  TX_SUSPENDED                     | 3       |
  |  TX_SLEEP                         | 4       |
  |  TX_QUEUE_SUSP                    | 5       |
  |  TX_SEMAPHORE_SUSP                | 6       |
  |  TX_EVENT_FLAG                    | 7       |
  |  TX_BLOCK_MEMORY                  | 8       |
  |  TX_BYTE_MEMORY                   | 9       |
  |  TX_TCP_IP                        | 12      |
  |  TX_MUTEX_SUSP                    | 13      |

- Info Field 3: Empilhar o valor do ponteiro durante a chamada. Info Field 4: Ponteiro para o próximo fio de prioridade máxima a executar. Se o NU, o sistema está inativo.

### <a name="interrupt-service-routine-isr-enter"></a>Interrupção De Rotina de Serviço (ISR) insira 

#### <a name="enter-isr"></a>Insira ISR 

**Ícone** ![ Insira o ícone I S R](./media/user-guide/tx-events/image3.png)

**Descrição**

Este evento representa a entrada de uma Rotina de Serviço de Interrupção (ISR) na aplicação. A execução de rotina de serviço de interrupção continua até que o evento de saída do ISR ocorra.

**Campos de Informação**

- Info Field 1: Empilhar o valor do ponteiro durante a chamada.
- Info Field 2: Número ISR definido pela aplicação (opcional).
- Info Field 3: Contagem de interrupção aninhada.
- Info Campo 4: Preempção interna desativa bandeira.

### <a name="interrupt-service-routine-isr-exit"></a>Interrupção de rotina de serviço (ISR) saída 

#### <a name="exit-isr"></a>Saída ISR

**Ícone** ![ Ícone de saída I S R](./media/user-guide/tx-events/image4.png)

**Descrição**

Este evento representa a saída de uma Rotina de Serviço de Interrupção (ISR) na aplicação.

**Campos de Informação**

- Info Field 1: Empilhar o valor do ponteiro durante a chamada.
- Info Field 2: Número ISR definido pela aplicação (opcional).
- Info Field 3: Contagem de interrupção aninhada.
- Info Campo 4: Preempção interna desativa bandeira.

### <a name="internal-time-slice"></a>Corte de tempo interna

#### <a name="internal-time-slice"></a>Corte de tempo interna

**Ícone** ![ Ícone de fatia de tempo interna](./media/user-guide/tx-events/image5.png)

**Descrição**

Este evento representa o processamento interno na ThreadX que realiza a operação de corte de tempo. O próximo fio da mesma prioridade é colocado no primeiro campo de informação. Se este valor for o mesmo que o fio atual, não foi realizada nenhuma fatia de tempo.

- Info Field 1: Ponteiro para o próximo fio a executar.
- Info Field 2: Contagem de interrupção aninhada.
- Info Campo 3: Preempção interna desativa bandeira.
- Info Field 4: Empilhar o valor do ponteiro durante a chamada.

### <a name="running"></a>Em Execução

#### <a name="running-in-context"></a>Correndo em contexto

**Ícone** ![ Ícone de execução](./media/user-guide/tx-events/image6.png)

**Descrição**

Este evento representa correr dentro de um contexto de fio ou sistema ocioso. É utilizado para ilustrar as alterações subsequentes no contexto como resultado de uma interrupção.

**Campos de Informação**
- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="block-allocate"></a>Atribuição de Blocos 

#### <a name="tx_block_allocate"></a>tx_block_allocate

**Ícone** ![ Ícone de atribuição de bloco](./media/user-guide/tx-events/image7.png)

**Descrição**

Este evento representa a atribuição de um bloco de memória através de tx_block_allocate. Se for bem sucedido, o endereço do bloco atribuído é devolvido no segundo campo de informação.

**Campos de Informação**
- Info Campo 1: Ponteiro para o bloco correspondente.
- Info Campo 2: Ponteiro para o bloco de memória devolvido (se for bem sucedido).
- Info Field 3: A opção de espera fornecida à chamada tx_block_allocate.
- Info Field 4: Blocos restantes disponíveis na piscina após esta atribuição.

### <a name="block-pool-create"></a>Criar piscina de blocos

#### <a name="tx_block_pool_create"></a>tx_block_pool_create

**Ícone** ![ Bloco de piscina criar ícone](./media/user-guide/tx-events/image8.png)

**Descrição**

Este evento representa a criação de um pool de blocos de memória através de tx_block_pool_create.

**Campos de Informação**

- Info Campo 1: Ponteiro para o bloco de controlo correspondente da piscina.
- Info Campo 2: Ponteiro para a área de memória inicial da piscina.
- Info Field 3: O número de blocos na piscina. Info Field 4: O tamanho de cada bloco na piscina em bytes.

### <a name="block-pool-delete"></a>Excluir de piscina de blocos

#### <a name="tx_block_pool_delete"></a>tx_block_pool_delete

**Ícone** ![ Ícone de excluir piscina de bloco](./media/user-guide/tx-events/image9.png)

**Descrição**

Este evento representa a eliminação de um conjunto de blocos de memória através de tx_block_pool_delete.

**Campos de Informação**

- Info Field 1: Ponteiro para o bloco de controlo da piscina.
- Info Field 2: Empilhar o valor do ponteiro durante a chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="block-pool-information-get"></a>Informações de piscina de blocos obter 

#### <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

**Ícone** ![ Informações de piscina de blocos obter ícone](./media/user-guide/tx-events/image10.png)

**Descrição**

Este evento representa obter informações sobre um conjunto de blocos de memória através de tx_block_pool_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para o bloco de controlo da piscina.
- Info Field 2: Empilhar o valor do ponteiro durante a chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="block-pool-performance-information-get"></a>Informações de desempenho do pool de blocos obter

#### <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

**Ícone** ![ Informações de desempenho do pool de blocos obter ícone](./media/user-guide/tx-events/image11.png)

**Descrição**

Este evento representa obter informações de desempenho sobre um conjunto de blocos de memória através de tx_block_pool_performance_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para o bloco de controlo da piscina.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="block-pool-performance-system-information-get"></a>Block Pool Performance Informações do Sistema Get

#### <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

**Ícone** ![ Bloquear informações do sistema de desempenho do pool obter ícone](./media/user-guide/tx-events/image12.png)

**Descrição**

Este evento representa obter informações de desempenho sobre todos os pools de blocos de memória através de tx_block_pool_performance_system_info_get.

**Campos de Informação**
- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="block-pool-prioritize"></a>Priorização do Pool Block

#### <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

**Ícone** ![ Ícone de prioridade de piscina de bloco](./media/user-guide/tx-events/image13.png)

**Descrição**

Este evento representa a colocação da linha suspensa de maior prioridade na parte da frente da lista de suspensão da piscina de blocos. Se isto for feito antes de chamar tx_block_release, a linha suspensa de maior prioridade receberá o bloco libertado.

**Campos de Informação**
- Info Field 1: Ponteiro de piscina de bloco de memória.
- Info Campo 2: Número de fios suspensos nesta piscina de blocos.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="block-release"></a>Lançamento do bloco 

#### <a name="tx_block_release"></a>tx_block_release

**Ícone** ![ Ícone de libertação de bloco](./media/user-guide/tx-events/image14.png)

**Descrição**

Este evento representa a libertação de um bloco previamente atribuído de volta ao bloco pool.

**Campos de Informação**

- Info Field 1: Ponteiro de piscina de bloco de memória.
- Info Field 2: Ponteiro para bloquear para soltar.
- Info Campo 3: Número de fios suspensos nesta piscina de blocos.
- Info Field 4: Ponteiro de pilha no momento da chamada.

### <a name="byte-allocate"></a>Byte Alocado 

#### <a name="tx_byte_allocate"></a>tx_byte_allocate

**Ícone** ![ Byte alocar ícone](./media/user-guide/tx-events/image15.png)

**Descrição**

Este evento representa a atribuição de memória através de tx_byte_allocate. Se for bem sucedido, o endereço da memória atribuída é devolvido no segundo campo de informação.

**Campos de Informação**
- Info Campo 1: Ponteiro para a piscina byte correspondente.
- Info Campo 2: Ponteiro para a memória devolvido (se for bem sucedido).
- Info Campo 3: Número de bytes solicitados. Info Field 4: A opção de espera fornecida à chamada tx_byte_allocate.

### <a name="byte-pool-create"></a>Byte Pool Criar

#### <a name="tx_byte_pool_create"></a>tx_byte_pool_create

**Ícone** ![ Byte pool criar ícone](./media/user-guide/tx-events/image16.png)

**Descrição**

Este evento representa a criação de uma piscina byte via tx_byte_pool_create.

**Campos de Informação**

- Info Campo 1: Ponteiro para a piscina byte correspondente.
- Info Campo 2: Ponteiro para o início da área de memória. Info Field 3: Número de bytes na piscina byte.
- Info Field 4: O ponteiro da pilha no momento da chamada.

### <a name="byte-pool-delete"></a>Byte Pool Delete 

#### <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

**Ícone** ![ Ícone de exclusão da piscina byte](./media/user-guide/tx-events/image17.png)

**Descrição**

Este evento representa a eliminação de uma piscina byte via tx_byte_pool_delete.

**Campos de Informação**

- Info Campo 1: Ponteiro para a piscina byte correspondente.
- Info Field 2: O ponteiro da pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="byte-pool-information-get"></a>Informações da Piscina Byte Obtêm

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ícone** ![ Informações de piscina byte obter ícone](./media/user-guide/tx-events/image18.png)

**Descrição**

Este evento representa obter informações de byte pool através de tx_byte_pool_info_get.

**Campos de Informação**

- Info Campo 1: Ponteiro para a piscina byte correspondente.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="byte-pool-performance-info-get"></a>Byte Pool Performance Info Get 

#### <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

**Ícone** ![ Byte pool performance info obter ícone](./media/user-guide/tx-events/image19.png)

**Descrição**

Este evento representa obter informações de desempenho da piscina byte através de tx_byte_pool_performance_info_get.

**Campos de Informação**

- Info Campo 1: Ponteiro para a piscina byte correspondente.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="byte-pool-performance-system-info-get"></a>Byte Pool Performance System Info Get 

#### <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

**Ícone** ![ Byte pool performance info obter ícone](./media/user-guide/tx-events/image20.png)

**Descrição**

Este evento representa obter informações do sistema de desempenho da piscina byte através de tx_byte_pool_performance_system_info_get.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="byte-pool-prioritize"></a>Prioridades byte Pool

#### <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

**Ícone** ![ Byte pool priorizar ícone](./media/user-guide/tx-events/image21.png)

**Descrição**

Este evento representa priorizar a lista de suspensão do byte pool através de tx_byte_pool_prioritize.

**Campos de Informação**

- Info Field 1: Ponteiro para piscina byte correspondente.
- Info Field 2: Número de fios atualmente suspensos na piscina byte.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="byte-release"></a>Lançamento byte

#### <a name="tx_byte_release"></a>tx_byte_release

**Ícone** ![ Ícone de lançamento byte](./media/user-guide/tx-events/image22.png)

**Descrição**

Este evento representa a libertação de um bloco de memória alocado a partir de uma piscina byte via tx_byte_release.

**Campos de Informação**

- Info Field 1: Ponteiro para piscina byte correspondente.
- Info Field 2: Ponteiro para memória de piscina byte previamente atribuída.
- Info Campo 3: Número de fios suspensos nesta piscina byte.
- Info Campo 4: Número de bytes de memória disponíveis.

### <a name="event-flags-create"></a>Bandeiras de eventos criar 

#### <a name="tx_event_flags_create"></a>tx_event_flags_create

**Ícone** ![ Bandeiras do evento criam ícone](./media/user-guide/tx-events/image23.png)

**Descrição**

Este evento representa a criação de um novo grupo de bandeiras de eventos através de tx_event_flags_create.

**Campos de Informação** 
- Info Field 1: Ponteiro para o bloco de controlo de grupo de bandeiras de eventos.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="event-flags-delete"></a>Bandeiras de eventos Eliminam 

#### <a name="tx_event_flags_delete"></a>tx_event_flags_delete

**Ícone** ![ Bandeiras do evento apagam ícone](./media/user-guide/tx-events/image24.png)

**Descrição**

Este evento representa a eliminação de um grupo de bandeiras de eventos através de tx_event_flags_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="event-flags-get"></a>Bandeiras do evento obter 

#### <a name="tx_event_flags_get"></a>tx_event_flags_get

**Ícone** ![ Ícone de bandeiras de evento gt](./media/user-guide/tx-events/image25.png)

**Descrição**

Este evento representa a recuperação de bandeiras de eventos de um grupo de bandeiras de eventos existentes através de tx_event_flags_get.

**Campos de Informação**

- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Bandeiras de eventos solicitadas.
- Info Field 3: Bandeiras de eventos atualmente definidas no grupo.
- Info Field 4: Opção solicitada nas bandeiras do evento recebe.

### <a name="event-flags-information-get"></a>Informações de bandeiras de eventos obtêm

#### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

**Ícone** ![ Informações de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image26.png)

**Descrição**

Este evento representa a recuperação de informações sobre um grupo de bandeiras de eventos existente através de tx_event_flags_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="event-flags-performance-information-get"></a>Informações de desempenho de bandeiras de eventos obtêm 

#### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

**Ícone** ![ Informações de desempenho de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image27.png)

**Descrição**

Este evento representa a recuperação de informações de desempenho relativas a um grupo de bandeiras de eventos existente através de tx_event_flags_performance_info_get.

**Campos de Informação** 
- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Não utilizado
- Info Field 3: Não utilizado
- Info Field 4: Não utilizado

### <a name="event-flags-performance-system-info-get"></a>Informações do sistema de desempenho de bandeiras de eventos obtêm

#### <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

**Ícone** ![ Informações do sistema de desempenho de bandeiras de eventos recebem ícone](./media/user-guide/tx-events/image28.png)

**Descrição**

Este evento representa a recuperação de informações de desempenho relativas a um grupo de bandeiras de eventos existente através de tx_event_flags_performance_system_info_get.

**Campos de Informação**
- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="event-flags-set"></a>Conjunto de bandeiras de evento 

#### <a name="tx_event_flags_set"></a>tx_event_flags_set

**Ícone** ![ Ícone de conjunto de bandeiras de evento](./media/user-guide/tx-events/image29.png)

**Descrição**

Este evento representa a definição (ou desminagem) de bandeiras de eventos num grupo de bandeiras de eventos existente através de tx_event_flags_set.

**Campos de Informação**

- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Bandeiras de evento a definir (ou claras).
- Informação Campo 3: E ou ou a bandeira do evento.
- Info Field 4: Número de fios suspensos no grupo de bandeira de evento.

### <a name="event-flags-set-notify"></a>Conjunto de bandeiras de eventos notificar

#### <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

**Ícone** ![ Conjunto de bandeiras de eventos ícone de notificação](./media/user-guide/tx-events/image30.png)

**Descrição**

Este evento representa o registo de uma chamada de notificação para qualquer operação de bandeira de evento num grupo de bandeiras de eventos existente através de tx_event_flags_set_notify.

**Campos de Informação**

- Info Field 1: Ponteiro para grupo de bandeiras de evento.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="interrupt-control"></a>Controlo de Interrupção 

#### <a name="tx_interrupt_control"></a>tx_interrupt_control

**Ícone** ![ Ícone de controlo de interrupção](./media/user-guide/tx-events/image31.png)

**Descrição**

Este evento representa a alteração da postura de bloqueio de interrupção do processador através de tx_interrupt_control.

**Campos de Informação**

- Info Field 1: Nova postura de interrupção.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="mutex-create"></a>Criação Mutex 

#### <a name="tx_mutex_create"></a>tx_mutex_create

**Ícone** ![ Mutex criar ícone](./media/user-guide/tx-events/image32.png)

**Descrição**

Este evento representa a criação de um mutex através de tx_mutex_create.

**Campos de Informação**

- Info Field 1: Ponteiro para bloco de controlo de mutantes.
- Info Field 2: Opção de herança prioritária
- (TX_INHERIT ou TX_NO_INHERIT).
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="mutex-delete"></a>Exclusão de mutex 

#### <a name="tx_mutex_delete"></a>tx_mutex_delete

**Ícone** ![ Ícone de exclusão de mutex](./media/user-guide/tx-events/image33.png)

**Descrição**

Este evento representa a eliminação de um mutex através de tx_mutex_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para mutex.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="mutex-get"></a>Mutex Get 

#### <a name="tx_mutex_get"></a>tx_mutex_get

**Ícone** ![ Mutex obter ícone](./media/user-guide/tx-events/image34.png)

**Descrição**

Este evento representa a obtenção de um mutex via tx_mutex_get.

**Campos de Informação**

- Info Field 1: Ponteiro para mutex.
- Info Field 2: A opção de espera fornecida à chamada tx_mutex_get.
- Info Field 3: Ponteiro para fio que detém o mutex (NULL implica que o mutex não é propriedade).
- Info Field 4: Número de vezes que o fio de propriedade chamou tx_mutex_get.

### <a name="mutex-information-get"></a>Informação Mutex Obter

#### <a name="tx_mutex_info_get"></a>tx_mutex_info_get

**Ícone** ![ Informações mutex obtêm ícone](./media/user-guide/tx-events/image35.png)

**Descrição**

Este evento representa a recuperação de informações de mutex através de tx_mutex_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para mutex.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="mutex-performance-information-get"></a>Informações de desempenho mutex obtêm 

#### <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

**Ícone** ![ Informações de desempenho de Mutex obtêm ícone](./media/user-guide/tx-events/image36.png)

**Descrição**

Este evento representa a recuperação de informações de desempenho de mutex através de tx_mutex_performance_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para mutex.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="mutex-performance-system-info-get"></a>Informações do sistema de desempenho mutex obtêm

#### <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

**Ícone** ![ Informações do sistema de desempenho mutex obtêm ícone](./media/user-guide/tx-events/image37.png)

**Descrição**

Este evento representa a recuperação de informações de desempenho do sistema mutex através de tx_mutex_performance_system_info_get.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="mutex-prioritize"></a>Prioridades Mutex 

#### <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

**Ícone** ![ Ícone de prioridades de Mutex](./media/user-guide/tx-events/image38.png)

**Descrição**

Este evento representa dar prioridade à lista de suspensão do mutex através de tx_mutex_prioritize.

**Campos de Informação**

- Info Field 1: Ponteiro para o mutex correspondente.
- Info Field 2: Número de fios atualmente suspensos no mutex.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="mutex-put"></a>Mutex Put 

#### <a name="tx_mutex_put"></a>tx_mutex_put

**Ícone** ![ Mutex colocar ícone](./media/user-guide/tx-events/image39.png)

**Descrição**

Este evento representa a libertação de um mutex anteriormente propriedade através de tx_mutex_put.

**Campos de Informação**

- Info Field 1: Ponteiro para o mutex correspondente.
- Info Field 2: Ponteiro da linha proprietária do mutex.
- Info Field 3: Número de pedidos pendentes de mutex.
- Info Field 4: Ponteiro de pilha no momento da chamada.

### <a name="queue-create"></a>Criar fila 

#### <a name="tx_queue_create"></a>tx_queue_create

**Ícone** ![ Fila criar ícone](./media/user-guide/tx-events/image40.png)

**Descrição**

Este evento representa a criação de uma fila de mensagens através de tx_queue_create.

**Campos de Informação**

- Info Field 1: Ponteiro para o bloco de controlo da fila.
- Info Field 2: Tamanho da mensagem – em termos de palavras de 32 bits.
- Info Campo 3: Ponteiro para o início da área de memória da fila.
- Info Campo 4: Número de bytes na área da memória da fila.

### <a name="queue-delete"></a>Excluir de fila 

#### <a name="tx_queue_delete"></a>tx_queue_delete

**Ícone** ![ Ícone de exclusão de fila](./media/user-guide/tx-events/image41.png)

**Descrição**

Este evento representa a eliminação de uma fila através de tx_queue_delete.

**Campos de Informação**

- Info Field 1: Ponteiro para fila.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="queue-flush"></a>Flush de fila 

#### <a name="tx_queue_flush"></a>tx_queue_flush

**Ícone** ![ Ícone de descarga de fila](./media/user-guide/tx-events/image42.png)

**Descrição**

Este evento representa o flushing (limpar todos os conteúdos da fila) de uma fila através de tx_queue_flush.

**Campos de Informação**

- Info Field 1: Ponteiro para fila.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="queue-front-send"></a>Envio frontal de fila 

#### <a name="tx_queue_front_send"></a>tx_queue_front_send

**Ícone** ![ Ícone de envio de fila frontal](./media/user-guide/tx-events/image43.png)

**Descrição**

Este evento representa o envio de uma mensagem para a frente de uma fila via tx_queue_front_send.

**Campos de Informação**

- Info Field 1: Ponteiro para fila.
- Info Field 2: Ponteiro para o início da mensagem.
- Info Field 3: Opção de espera fornecida ao
- tx_queue_front_send chamada.
- Info Campo 4: Número de mensagens já encostodas.

### <a name="queue-information-get"></a>Informação de fila Obter 

#### <a name="tx_queue_info_get"></a>tx_queue_info_get

**Ícone** ![ Informações de fila recebem ícone](./media/user-guide/tx-events/image44.png)

**Descrição**

Este evento representa obter informações sobre uma fila via tx_queue_info_get.

**Campos de Informação** 
- Info Field 1: Ponteiro para fila.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="queue-performance-info-get"></a>Informações de desempenho de fila obter 

#### <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

**Ícone** ![ Informações de desempenho da fila recebem ícone](./media/user-guide/tx-events/image45.png)

**Descrição**

Este evento representa obter informações de desempenho sobre uma fila via tx_queue_performance_info_get.

**Campos de Informação** 

- Info Field 1: Ponteiro para fila.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="queue-performance-system-info-get"></a>Informações do sistema de desempenho da fila obtêm 

#### <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

**Ícone** ![ Informações do sistema de desempenho da fila recebem ícone](./media/user-guide/tx-events/image46.png)

**Descrição**

Este evento representa obter informações sobre o desempenho do sistema sobre todas as filas do sistema.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="queue-prioritize"></a>Prioridades de fila 

#### <a name="tx_queue_prioritize"></a>tx_queue_prioritize

**Ícone** ![ Ícone de prioridade de fila](./media/user-guide/tx-events/image47.png)

**Descrição**

Este evento representa priorizar a lista de suspensão da fila através de tx_queue_prioritize.

**Campos de Informação** 

- Info Field 1: Ponteiro para a fila correspondente.
- Info Field 2: Número de fios atualmente suspensos na fila.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

#### <a name="queue-receive"></a>Receber fila 

##### <a name="tx_queue_receive"></a>tx_queue_receive

**Ícone** ![ Ícone de receção de fila](./media/user-guide/tx-events/image48.png)

**Descrição**

Este evento representa receber uma mensagem de uma fila via tx_queue_receive.

**Campos de Informação** 

- Info Field 1: Ponteiro para fila.
- Info Field 2: Ponteiro para destino para mensagem. Info Field 3: Opção de espera fornecida à chamada.
- Info Campo 4: Número de mensagens atualmente em fila.

### <a name="queue-send"></a>Enviar fila 

#### <a name="tx_queue_send"></a>tx_queue_send

**Ícone** ![ Fila enviar ícone](./media/user-guide/tx-events/image49.png)

**Descrição**

Este evento representa o envio de uma mensagem para uma fila via tx_queue_send.

**Campos de Informação** 

- Info Field 1: Ponteiro para fila.
- Info Field 2: Ponteiro para mensagem.
- Info Field 3: Opção de espera fornecida à chamada.
- Info Campo 4: Número de mensagens atualmente em fila.

### <a name="queue-send-notify"></a>Notificação de envio de fila 

#### <a name="tx_queue_send_notify"></a>tx_queue_send_notify

**Ícone** ![ Fila enviar ícone de notificação](./media/user-guide/tx-events/image50.png)

**Descrição**

<p>Este evento representa o registo de uma chamada através de tx_queue_send_notify que é chamada sempre que uma mensagem é enviada para uma fila.

**Campos de Informação** 

- Info Field 1: Ponteiro para fila.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="semaphore-ceiling-put"></a>Teto de semáforo colocado 

#### <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

**Ícone** ![ Teto de semáforo colocar ícone](./media/user-guide/tx-events/image51.png)

**Descrição**

Este evento representa a colocação de um semáforo através de tx_semaphore_ceiling_put. Isto difere de tx_semaphore_put na medida em que o valor máximo do semáforo é examinado de modo a que a operação de colocação não seja permitida a exceder o valor máximo ou o limite máximo.

**Campos de Informação**

- Info Field 1: Ponteiro para semáforo.
- Info Field 2: Contagem de semáforos atuais.
- Info Campo 3: Número de fios suspensos no semáforo.
- Info Campo 4: Limite de teto fornecido à chamada.

#### <a name="semaphore-create"></a>Criação de Semáforos 

##### <a name="tx_semaphore_create"></a>tx_semaphore_create

**Ícone** ![ Semáforo criar ícone](./media/user-guide/tx-events/image52.png)

**Descrição**

Este evento representa a criação de um semáforo através de tx_semaphore_create.

**Campos de Informação**

- Info Campo 1: Ponteiro para o bloco de controlo de semáforos.
- Info Field 2: Contagem inicial de semáforos.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="semaphore-delete"></a>Semáforo Eliminar 

#### <a name="tx_semaphore_delete"></a>tx_semaphore_delete

**Ícone** ![ Ícone de exclusão de semáforo](./media/user-guide/tx-events/image53.png)

**Descrição**

Este evento representa a eliminação de um semáforo através de tx_semaphore_delete.

**Campos de Informação**

- Info Field 1: Ponteiro para semáforo.
- nfo Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="semaphore-get"></a>Semáforo 

#### <a name="tx_semaphore_get"></a>tx_semaphore_get

**Ícone** ![ Semáforo obter ícone](./media/user-guide/tx-events/image54.png)

**Descrição**

Este evento representa a obtenção de um semáforo via tx_semaphore_get.

**Campos de Informação**

- Info Field 1: Ponteiro para semáforo.
- Info Field 2: Opção de espera fornecida à chamada.
- Info Field 3: Contagem de semáforos atuais.
- Info Field 4: Ponteiro de pilha no momento da chamada.

### <a name="semaphore-information-get"></a>Informações de semáforos Obtêm 

#### <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

**Ícone** ![ Informações de semáforo recebem ícone](./media/user-guide/tx-events/image55.png)

**Descrição**

Este evento representa a obtenção de informação sobre um semáforo via tx_semaphore_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para semáforo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="semaphore-performance-info-get"></a>Informações de desempenho de semáforos obtêm 

#### <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

**Ícone** ![ Informações de desempenho de semáforo recebem ícone](./media/user-guide/tx-events/image56.png)

**Descrição**

Este evento representa a obtenção de informações de desempenho sobre um semáforo via tx_semaphore_performance_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para semáforo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="semaphore-performance-system-info"></a>Informações do Sistema de Desempenho de Semáforos 

#### <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

**Ícone** ![ Ícone de informação do sistema de desempenho de semáforo](./media/user-guide/tx-events/image57.png)

**Descrição**

Este evento representa a obtenção de informações de desempenho sobre todos os semáforos do sistema através de tx_semaphore_performance_system_info_get.

**Campos de Informação** 

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="semaphore-prioritize"></a>Priorização do Semáforo 

#### <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

**Ícone** ![ Semáforo prioriza ícone](./media/user-guide/tx-events/image58.png)

**Descrição**

Este evento representa priorizar a lista de suspensão do semáforo através de tx_semaphore_prioritize.

**Campos de Informação**

- Info Campo 1: Ponteiro para o semáforo correspondente.
- Info Campo 2: Número de fios atualmente suspensos no semáforo.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="semaphore-put"></a>Semáforo colocado 

#### <a name="tx_semaphore_put"></a>tx_semaphore_put

**Ícone** ![ Semáforo colocar ícone](./media/user-guide/tx-events/image59.png)

**Descrição**

Este evento representa a libertação de um caso de semáforo via tx_semaphore_put.

**Campos de Informação** 

- Info Campo 1: Ponteiro para o semáforo correspondente. Info Field 2: Contagem de semáforos atuais.
- Info Campo 3: Número de fios suspensos no semáforo.
- Info Field 4: Ponteiro de pilha no momento da chamada.

### <a name="semaphore-put-notify"></a>Semáforo colocar notificação 

#### <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

**Ícone** ![ Semáforo colocar ícone de notificação](./media/user-guide/tx-events/image60.png)

**Descrição**

Este evento representa o registo de uma chamada através de tx_semaphore_put_notify que é chamado sempre que um caso de semáforo é colocado.

**Campos de Informação** 

- Info Field 1: Ponteiro para semáforo.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-create"></a>Criar fios 

#### <a name="tx_thread_create"></a>tx_thread_create

**Ícone** ![ Ícone de criação de fio](./media/user-guide/tx-events/image61.png)

**Descrição**

Este evento representa a criação de um fio através de tx_thread_create.

**Campos de Informação**

- Info Campo 1: Ponteiro para o bloco de controlo da rosca.
- Info Field 2: Prioridade do fio.
- Info Field 3: Ponteiro de pilha para fio.
- nfo Field 4: Tamanho da pilha em bytes.

### <a name="thread-delete"></a>Eliminar fios 

#### <a name="tx_thread_delete"></a>tx_thread_delete

**Ícone** ![ Ícone de exclusão de fio](./media/user-guide/tx-events/image62.png)

**Descrição**

Este evento representa a eliminação de um fio através de tx_thread_delete.

**Campos de Informação** 

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-entryexit-notify"></a>Notificação de entrada/saída de linha 

#### <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

**Ícone** ![ Ícone de notificação de entrada/saída de fio](./media/user-guide/tx-events/image63.png)

**Descrição**

Este evento representa o registo de uma chamada através de tx_thread_entry_exit_notify que é chamada sempre que um fio é introduzido ou sai.

**Campos de Informação** 

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado de rosca no momento da inscrição.
- Info Field 3: Ponteiro para empilhar no momento da chamada.
- Info Field 4: Não utilizado.

#### <a name="thread-identify"></a>Identificar o fio 

##### <a name="tx_thread_identify"></a>tx_thread_identify

**Ícone** ![ Ícone de identificação de fio](./media/user-guide/tx-events/image64.png)

**Descrição**

Este evento representa obter o ponteiro de linha atual através de tx_thread_identify.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-information-get"></a>Informação de fio obter 

#### <a name="tx_thread_info_get"></a>tx_thread_info_get

**Ícone** ![ Informações de fio obter ícone](./media/user-guide/tx-events/image65.png)

**Descrição**

Este evento representa obter informações sobre o fio especificado através de tx_thread_info_get.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado do fio no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

#### <a name="thread-performance-information-get"></a>Informações de desempenho do fio obtêm 

##### <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

**Ícone** ![ Informações de desempenho do fio obter ícone](./media/user-guide/tx-events/image66.png)

**Descrição**

Este evento representa obter informações de desempenho sobre o fio especificado através de tx_thread_performance_info_get.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado do fio no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-performance-system-info-get"></a>Informações do sistema de desempenho do fio obtêm 

#### <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

**Ícone** ![ Informações do sistema de desempenho do fio obter ícone](./media/user-guide/tx-events/image67.png)

**Descrição**

Este evento representa obter informações de desempenho sobre todos os fios através de tx_thread_performance_system_info_get.

**Campos de Informação** 

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-preemption-change"></a>Alteração da Preempção do Fio 

#### <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

**Ícone** ![ Ícone de mudança de mudança de preempção de fio](./media/user-guide/tx-events/image68.png)

**Descrição**

Este evento representa a alteração do limiar de preempção de um fio através de tx_thread_preemption_change.

**Campos de Informação** 

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Novo limiar de pré-detenção.
- Info Field 3: Limite de pré-detenção anterior.
- Info Field 4: Estado da Thread no momento da chamada.

### <a name="thread-priority-change"></a>Alteração da prioridade do fio 

#### <a name="tx_thread_priority_change"></a>tx_thread_priority_change

**Ícone** ![ Ícone de mudança de prioridade de fio](./media/user-guide/tx-events/image69.png)

**Descrição**

Este evento representa mudar a prioridade de um fio através de tx_thread_priority_change.

- Campos de Informação 
- Info Campo 1: Ponteiro para linha.
- Info Field 2: Nova prioridade.
- Info Campo 3: Prioridade anterior.
- Info Field 4: Estado da Thread no momento da chamada.

### <a name="thread-relinquish"></a>Renúncia de fio 

#### <a name="tx_thread_relinquish"></a>tx_thread_relinquish

**Ícone** ![ Ícone de renúncia de fio](./media/user-guide/tx-events/image70.png)

**Descrição**

Este evento representa a renúncia ao processador de um fio através de tx_thread_relinquish.

**Campos de Informação**

- Info Field 1: Ponteiro de pilha no momento da chamada.
- Info Field 2: Ponteiro para o próximo fio a executar.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-reset"></a>Reset de fio 

#### <a name="tx_thread_reset"></a>tx_thread_reset

**Ícone** ![ Ícone de reset de fio](./media/user-guide/tx-events/image71.png)

**Descrição**

Este evento representa a reposição de um fio completo ou terminado através de tx_thread_reset.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

#### <a name="thread-resume"></a>Resumo da linha 

##### <a name="tx_thread_resume"></a>tx_thread_resume

**Ícone** ![ Ícone de retoma de fio](./media/user-guide/tx-events/image72.png)

**Descrição**

Este evento representa o reinício de um fio suspenso através de tx_thread_resume.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="thread-sleep"></a>Thread Sleep 

#### <a name="tx_thread_sleep"></a>tx_thread_sleep

**Ícone** ![ Ícone de sono de fio](./media/user-guide/tx-events/image73.png)

**Descrição**

Este evento representa a suspensão do fio atual para um número especificado de carraças do temporizador através de tx_thread_sleep.

**Campos de Informação**

- Info Field 1: Número de carraças a suspender.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="thread-stack-error-notify"></a>Notificação de erro de pilha de fio 

#### <a name="tx_thread_stack_error_notify_event"></a>tx_thread_stack_error_notify_event

**Ícone** ![ Ícone de notificação de erro de pilha de fio](./media/user-guide/tx-events/image74.png)

**Descrição**

Este evento representa o registo de uma rotina de notificação de erro de pilha de fio através de tx_thread_stack_error_notify_event.

**Campos de Informação** 

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="thread-suspend"></a>Suspensão do fio 

#### <a name="tx_thread_suspend"></a>tx_thread_suspend

**Ícone** ![ Ícone de suspensão de fio](./media/user-guide/tx-events/image75.png)

**Descrição**

Este evento representa a suspensão de um fio através de tx_thread_suspend.

**Campos de Informação** 

- Info Field 1: Ponteiro para a linha para suspender.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="thread-terminate"></a>Fim de fio 

#### <a name="tx_thread_terminate"></a>tx_thread_terminate

**Ícone** ![ Ícone de terminação de fio](./media/user-guide/tx-events/image76.png)

**Descrição**

Este evento representa o fim de um fio através de tx_thread_terminate.

**Campos de Informação** 

- Info Campo 1: Ponteiro para linha para terminar.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="thread-time-slice-change"></a>Mudança de Time-Slice de fio 

#### <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

**Ícone** ![ Ícone de mudança de fatia de tempo de fio](./media/user-guide/tx-events/image77.png)

**Descrição**

Este evento representa a alteração da rodela temporal de um fio através de tx_thread_time_slice_change.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Nova fatia de tempo.
- Info Campo 3: Corte de tempo anterior.
- Info Field 4: Não utilizado.

### <a name="thread-wait-abort"></a>Thread Wait Abort 

#### <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

**Ícone** ![ Ícone de aborto de espera de fio](./media/user-guide/tx-events/image78.png)

**Descrição**

Este evento representa abortar a suspensão de um fio através de tx_thread_wait_abort.

**Campos de Informação**

- Info Campo 1: Ponteiro para linha.
- Info Field 2: Estado de Thread no momento da chamada.
- Info Field 3: Ponteiro de pilha no momento da chamada.
- Info Field 4: Não utilizado.

### <a name="time-get"></a>Tempo Get 

#### <a name="tx_time_get"></a>tx_time_get

**Ícone** ![ Tempo obter ícone](./media/user-guide/tx-events/image79.png)

**Descrição**

Este evento representa obter o número atual de tiques temporizadores através de tx_time_get.

**Campos de Informação**

- Info Campo 1: Número atual de carraças temporizador.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="time-set"></a>Conjunto de tempo 

#### <a name="tx_time_set"></a>tx_time_set

**Ícone** ![ Ícone de conjunto de tempo](./media/user-guide/tx-events/image80.png)

**Descrição**

Este evento representa a definição do número atual de carraças temporais através de tx_time_set.

**Campos de Informação**

- Info Field 1: Novo número de carraças temporizador.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-activate"></a>Ativador de temporizador 

#### <a name="tx_timer_activate"></a>tx_timer_activate

**Ícone** ![ Ícone de ativação do temporizador](./media/user-guide/tx-events/image81.png)

**Descrição**

Este evento representa a ativação do temporizador especificado através de tx_timer_activate.

**Campos de Informação**

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-change"></a>Alteração do temporizador 

#### <a name="tx_timer_change"></a>tx_timer_change

**Ícone** ![ Ícone de mudança de temporizador](./media/user-guide/tx-events/image82.png)

**Descrição**

Este evento representa a alteração do temporizador especificado através de tx_timer_change.

**Campos de Informação**

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Tiques de expiração iniciais.
- Info Field 3: Reagendar os tiques de expiração.
- Info Field 4: Não utilizado.

### <a name="timer-create"></a>Criar temporizador 

#### <a name="tx_timer_create"></a>tx_timer_create

**Ícone** ![ Ícone de criação de temporizador](./media/user-guide/tx-events/image83.png)

**Descrição**

Este evento representa a criação de um temporizador através de tx_timer_create.

**Campos de Informação**

- Info Campo 1: Ponteiro para o bloco de controlo do temporizador.
- Info Field 2: Tiques de expiração iniciais.
- Info Field 3: Reagendar os tiques de expiração.
- Info Field 4: Ativar automaticamente o valor — TX_AUTO_ACTIVATE (1) ou TX_NO_ACTIVATE (0).

### <a name="timer-deactivate"></a>Temporizador Desativar 

#### <a name="tx_timer_deactivate"></a>tx_timer_deactivate

**Ícone** ![ Ícone de desativado temporizador](./media/user-guide/tx-events/image84.png)

**Descrição**

Este evento representa a desativar um temporizador através de tx_timer_deactivate.

**Campos de Informação**

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-delete"></a>Apagar temporizador 

#### <a name="tx_timer_delete"></a>tx_timer_delete

**Ícone** ![ Ícone de eliminação do temporizador](./media/user-guide/tx-events/image85.png)

**Descrição**

Este evento representa a eliminação de um temporizador através de tx_timer_delete.

**Campos de Informação** 

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-information-get"></a>Informação de temporizador Obtém 

#### <a name="tx_timer_info_get"></a>tx_timer_info_get

**Ícone** ![ Temporizador obter ícone de informação](./media/user-guide/tx-events/image86.png)

**Descrição**

Este evento representa a obtenção de informações de temporizador através de tx_timer_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-performance-information-get"></a>Informações de desempenho do temporizador obtêm 

#### <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

**Ícone** ![ Informações de desempenho do temporizador obtêm ícone](./media/user-guide/tx-events/image87.png)

**Descrição** 

Este evento representa obter informações de desempenho do temporizador através de tx_timer_performance_info_get.

**Campos de Informação**

- Info Field 1: Ponteiro para temporizador.
- Info Field 2: Ponteiro de pilha no momento da chamada.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.

### <a name="timer-system-performance-info-get"></a>Informações de desempenho do sistema temporizador obtêm 

#### <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

**Ícone** ![ Informações de desempenho do sistema temporizador recebem ícone](./media/user-guide/tx-events/image88.png)


**Descrição** 

Este evento representa obter todas as informações de desempenho do temporizador através de tx_timer_performance_system_info_get.

**Campos de Informação**

- Info Field 1: Não utilizado.
- Info Field 2: Não utilizado.
- Info Field 3: Não utilizado.
- Info Field 4: Não utilizado.