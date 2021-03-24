---
title: Apêndice B - Azure RTOS ThreadX SMP Constants
description: ThreadX SMP Constants
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7245b53e78e657ce8059ee8f013a8d2faa4f7b14
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825442"
---
# <a name="appendix-b---azure-rtos-threadx-smp-constants"></a>Apêndice B - Azure RTOS ThreadX SMP Constants

## <a name="alphabetic-listings"></a>Listagens alfabéticas

```C
TX_1_ULONG                 1
TX_2_ULONG                 2
TX_4_ULONG                 4
TX_8_ULONG                 8
TX_16_ULONG                16
TX_ACTIVATE_ERROR          0x17
TX_AND                     2
TX_AND_CLEAR               3
TX_AUTO_ACTIVATE           1
TX_AUTO_START              1
TX_BLOCK_MEMORY            8
TX_BYTE_MEMORY             9
TX_CALLER_ERROR            0x13
TX_CEILING_EXCEEDED        0x21
TX_COMPLETED               1
TX_DELETE_ERROR            0x11
TX_DELETED                 0x01
TX_DONT_START              0
TX_EVENT_FLAG              7
TX_FALSE                   0
TX_FEATURE_NOT_ENABLED     0xFF
TX_FILE                    11
TX_GROUP_ERROR             0x06
TX_INHERIT                 1
TX_INHERIT_ERROR           0x1F
TX_INVALID_CEILING         0x22
TX_IO_DRIVER               10
TX_LOOP_FOREVER            1
TX_MUTEX_ERROR             0x1C
TX_MUTEX_SUSP              13
TX_NO_ACTIVATE             0
TX_NO_EVENTS               0x07
TX_NO_INHERIT              0
TX_NO_INSTANCE             0x0D
TX_NO_MEMORY               0x10
TX_NO_TIME_SLICE           0
TX_NO_WAIT                 0
TX_NOT_AVAILABLE           0x1D
TX_NOT_DONE                0x20
TX_NOT_OWNED               0x1E
TX_NULL                    0
TX_OPTION_ERROR            0x08
TX_OR                      0
TX_OR_CLEAR                1
TX_POOL_ERROR              0x02
TX_PRIORITY_ERROR          0x0F
TX_PTR_ERROR               0x03
TX_QUEUE_EMPTY             0x0A
TX_QUEUE_ERROR             0x09
TX_QUEUE_FULL              0x0B
TX_QUEUE_SUSP              5
TX_READY                   0
TX_RESUME_ERROR            0x12
TX_SEMAPHORE_ERROR         0x0C
TX_SEMAPHORE_SUSP          6
TX_SIZE_ERROR              0x05
TX_SLEEP                   4
TX_STACK_FILL
0xEFEFEFEFUL
TX_START_ERROR             0x10
TX_SUCCESS                 0x00
TX_SUSPEND_ERROR           0x14
TX_SUSPEND_LIFTED          0x19
TX_SUSPENDED               3
TX_TCP_IP                  12
TX_TERMINATED              2
TX_THREAD_ENTRY            0
TX_THREAD_ERROR            0x0E
TX_THREAD_EXIT             1
TX_THRESH_ERROR            0x18
TX_TICK_ERROR              0x16
TX_TIMER_ERROR             0x15
TX_TRUE                    1
TX_WAIT_ABORT_ERROR        0x1B
TX_WAIT_ABORTED            0x1A
TX_WAIT_ERROR              0x04
TX_WAIT_FOREVER
0xFFFFFFFFUL
```
## <a name="listing-by-value"></a>Listagem por Valor

```C
TX_DONT_START              0
TX_FALSE                   0
TX_NO_ACTIVATE             0
TX_NO_INHERIT              0
TX_NO_TIME_SLICE           0
TX_NO_WAIT                 0
TX_NULL                    0
TX_OR                      0
TX_READY                   0
TX_SUCCESS                 0x00
TX_THREAD_ENTRY            0
TX_1_ULONG                 1
TX_AUTO_ACTIVATE           1
TX_AUTO_START              1
TX_COMPLETED               1
TX_INHERIT                 1
TX_LOOP_FOREVER            1
TX_DELETED                 0x01
TX_OR_CLEAR                1
TX_THREAD_EXIT             1
TX_TRUE                    1
TX_2_ULONG                 2
TX_AND                     2
TX_POOL_ERROR              0x02
TX_TERMINATED              2
TX_AND_CLEAR               3
TX_PTR_ERROR               0x03
TX_SUSPENDED               3
TX_4_ULONG                 4
TX_SLEEP                   4
TX_WAIT_ERROR              0x04
TX_QUEUE_SUSP              5
TX_SIZE_ERROR              0x05
TX_GROUP_ERROR             0x06
TX_SEMAPHORE_SUSP          6
TX_EVENT_FLAG              7
TX_NO_EVENTS               0x07
TX_8_ULONG                 8
TX_BLOCK_MEMORY            8
TX_OPTION_ERROR            0x08
TX_BYTE_MEMORY             9
TX_QUEUE_ERROR             0x09
TX_IO_DRIVER               10
TX_QUEUE_EMPTY             0x0A
TX_FILE                    11
TX_QUEUE_FULL              0x0B
TX_TCP_IP                  12
TX_SEMAPHORE_ERROR         0x0C
TX_MUTEX_SUSP              13
TX_NO_INSTANCE             0x0D
TX_THREAD_ERROR            0x0E
TX_PRIORITY_ERROR          0x0F
TX_16_ULONG                16
TX_NO_MEMORY               0x10
TX_START_ERROR             0x10
TX_DELETE_ERROR            0x11
TX_RESUME_ERROR            0x12
TX_CALLER_ERROR            0x13
TX_SUSPEND_ERROR           0x14
TX_TIMER_ERROR             0x15
TX_TICK_ERROR              0x16
TX_ACTIVATE_ERROR          0x17
TX_THRESH_ERROR            0x18
TX_SUSPEND_LIFTED          0x19
TX_WAIT_ABORTED            0x1A
TX_WAIT_ABORT_ERROR        0x1B
TX_MUTEX_ERROR             0x1C
TX_NOT_AVAILABLE           0x1D
TX_NOT_OWNED               0x1E
TX_INHERIT_ERROR           0x1F
TX_NOT_DONE                0x20
TX_CEILING_EXCEEDED        0x21
TX_INVALID_CEILING         0x22
TX_FEATURE_NOT_ENABLED     0xFF
TX_STACK_FILL
0xEFEFEFEFUL
TX_WAIT_FOREVER
0xFFFFFFFFUL
```