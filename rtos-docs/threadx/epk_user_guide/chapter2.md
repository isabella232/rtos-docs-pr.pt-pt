---
title: Capítulo 2 - Referências API do Kit de Perfil de Execução
description: Este capítulo documenta as funções de API fornecidas pela EPK.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a198e48bdacbc141fb3de4670cc7ea5ba079612d
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377634"
---
#  <a name="chapter-2--execution-profile-kit-api-references"></a>Referências API do Kit de Perfil de Execução capítulo 2

O ThreadX EPK fornece funções de acesso para obter as informações do perfil de execução, da seguinte forma.

| Nome da função &nbsp; | Descrição |
| --- | --- |
| _tx_execution_thread_time_reset | Repor o tempo acumulado para um fio. |
| _tx_execution_thread_total_time_reset | Repor o tempo total de rosca acumulado. |
| _tx_execution_isr_time_reset | Repor o tempo ISR acumulado. |
| _tx_execution_idle_time_reset | Repôs o tempo de marcha lenta a acumular. |
| _tx_execution_thread_time_get Obtenha o tempo acumulado para um fio. |
| _tx_execution_thread_total_time_get | Obtenha o tempo total acumulado do fio. |
| _tx_execution_isr_time_get | Obtenha o tempo isr acumulado. |
| _tx_execution_idle_time_get | Obtenha o tempo de marcha lenta. |

##  <a name="_tx_execution_thread_time_reset"></a>_tx_execution_thread_time_reset

Repor o tempo acumulado para um fio.

### <a name="prototype"></a>Prototype

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Descrição

Este serviço define o tempo de execução do fio acumulado de volta a zero.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **thread_ptr** Ponteiro para o fio.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reset EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_reset"></a>_tx_execution_thread_total_time_reset

Repor o tempo total de rosca acumulado.

### <a name="prototype"></a>Prototype
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a>Descrição

Este serviço define o tempo de execução total acumulado do fio de volta a zero.

### <a name="input-parameters"></a>Parâmetros de Entrada

Nenhum.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reset EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

- Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_reset"></a>_tx_execution_isr_time_reset

Repor o tempo ISR acumulado.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a>Descrição

Este serviço define o tempo de execução total do ISR acumulado de volta a zero.

### <a name="input-parameters"></a>Parâmetros de Entrada

Nenhum.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reset EPK bem sucedido.

**Permitido a partir de**

- Fios, temporizadores e ISRs

**Exemplo**

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_reset"></a>_tx_execution_idle_time_reset

Repôs o tempo de marcha lenta a acumular.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a>Descrição

Este serviço define o tempo de execução total acumulado de marcha lenta para zero.

### <a name="input-parameters"></a>Parâmetros de Entrada

Nenhum.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reset EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

- Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_time_get"></a>_tx_execution_thread_time_get

Obtenha o tempo acumulado para um fio.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a>Descrição

Este serviço obtém o tempo de execução acumulado por um fio.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **thread_ptr** Ponteiro para o fio.

- **total_time** Destino para \' o tempo de execução do thread.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) tempo de EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_thread_total_time_get"></a>_tx_execution_thread_total_time_get

Obtenha o tempo total acumulado do fio.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Descrição

Este serviço obtém o tempo de execução total acumulado do fio.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **total_time** Destino para o tempo total de execução do fio.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) tempo de EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

- Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_isr_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_isr_time_get"></a>_tx_execution_isr_time_get

Obtenha o tempo isr acumulado.

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Descrição

Este serviço obtém o tempo de execução do ISR acumulado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **total_time** Destino para o tempo total de execução do ISR.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) tempo de EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_idle_time_get

## <a name="_tx_execution_idle_time_get"></a>_tx_execution_idle_time_get

### <a name="get-the-accumulated-idle-time"></a>Obtenha o tempo de marcha lenta ociosa acumulado

### <a name="prototype"></a>Prototype

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a>Descrição

Este serviço obtém o tempo de execução ocioso acumulado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **total_time** Destino para o tempo total de execução ocioso.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) tempo de EPK bem sucedido.

### <a name="allowed-from"></a>Permitido a partir de

- Fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a>Consulte também

- _tx_execution_thread_time_reset
- _tx_execution_thread_total_time_reset
- _tx_execution_isr_time_reset
- _tx_execution_idle_time_reset
- _tx_execution_thread_time_get
- _tx_execution_thread_total_time_get
- _tx_execution_isr_time_get
