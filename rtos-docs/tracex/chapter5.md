---
title: Capítulo 5 - Criação de tampões de vestígios
description: Este capítulo contém uma descrição sobre como construir um tampão de evento Azure RTOS TraceX e também descreve o formato subjacente do tampão.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801789"
---
# <a name="chapter-5---generating-trace-buffers"></a>Capítulo 5 - Criação de tampões de vestígios

Este capítulo contém uma descrição sobre como construir um tampão de evento Azure RTOS TraceX e também descreve o formato subjacente do tampão.

## <a name="threadx-event-trace-support"></a>Suporte ao rastreio de eventos ThreadX

A ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços da ThreadX, alterações do estado dos fios e eventos definidos pelo utilizador. A capacidade de rastreio de eventos ThreadX foi concebida principalmente como uma ferramenta pós-morte para analisar as últimas atividades "n" na aplicação. A partir desta informação, o desenvolvedor pode detetar problemas e/ou potenciais alvos de otimização.

TraceX exibe graficamente o tampão de vestígios de evento construído pela ThreadX. O seguinte descreve como construir o tampão e descreve o formato subjacente do tampão.

## <a name="enabling-event-trace"></a>Habilitação de rastreio de eventos

Para ativar o rastreio do evento, defina as constantes do carimbo temporal, construa a biblioteca ThreadX com **TX_ENABLE_EVENT_TRACE** definida e permita o rastreio chamando a função **tx_trace_enable.**

## <a name="defining-time-stamp-constants"></a>Definição de constantes Time-Stamp

As constantes do carimbo de tempo são concebidas para fornecer ao desenvolvedor o controlo sobre o carimbo de tempo utilizado nas entradas de vestígios do caso. As duas constantes de carimbo temporal e os seus valores predefinidos são os seguintes:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

As constantes acima são definidas em **tx_port.h** e criam um carimbo de tempo "falso" que simplesmente incrementa por um em cada evento. Segue-se um exemplo de uma definição de tempotamos real:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

As constantes acima especificam um temporizador de 32 bits que é obtido lendo o endereço 0x13000004. A maioria dos selos de tempo específicos da aplicação devem ser configurados de forma semelhante.

## <a name="exporting-the-trace-buffer"></a>Exportação do tampão de vestígios

A TraceX necessita do tampão de traços num formato binário, Intel HEX ou Motorola S-Record no anfitrião. A maneira mais fácil de o conseguir é parar o alvo e instruir o seu depurgger a despejar a área de memória que forneceu para ***tx_trace_enable*** funcionar num ficheiro no anfitrião.

> [!WARNING]
>***Tenha cuidado para não parar o alvo dentro de um código de recolha de vestígios em si. Fazê-lo pode causar informações inválidas de vestígios. Se o programa for interrompido dentro do ThreadX, é melhor passar por cima de qualquer macro de inserção de vestígios antes de despejar o tampão de vestígios.***

> [!IMPORTANT]
> *O apêndice D mostra como despejar o tampão de vestígios dentro de uma variedade de ferramentas de desenvolvimento.*

## <a name="extended-event-trace-api"></a>API de rastreio de eventos estendidos

Quando a ThreadX é construída com **TX_ENABLE_EVENT_TRACE** definida, os seguintes novos apis de evento estão disponíveis para a aplicação:

- tx_trace_enable: *Ativar o rastreio do evento*
- tx_trace_event_filter: *Filtrar eventos especificados*
- tx_trace_event_unfilter: *Eventos especificados por não filtro*
- tx_trace_disable: *Desativar o rastreio do evento*
- tx_trace_isr_enter_insert: *Insira o evento de rastreio de entrada ISR*
- tx_trace_isr_exit_insert: *Insira o evento de rastreio de saída DO ISR*
- tx_trace_buffer_full_notify: Registar *o registo de chamadas completas de aplicação do tampão*
- tx_trace_user_event_insert: Inserir *o evento do utilizador*

### <a name="tx_trace_enable"></a>tx_trace_enable

Ativar o rastreio do evento

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Description
Este serviço permite rastrear o rastreio de eventos dentro da ThreadX. A aplicação fornece o tampão de vestígios e o número máximo de objetos ThreadX.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

- **trace_buffer_start**: Ponteiro para o início do tampão de vestígios fornecido pelo utilizador.
- **trace_buffer_size:** Número total de bytes na memória para o tampão de vestígios. Quanto maior for o tampão de vestígios, mais entradas é capaz de armazenar.
- **registry_entries**: Número de aplicações Os objetos ThreadX devem manter no registo de vestígios. O registo é utilizado para correlacionar endereços de objetos com nomes de objetos. Isto é altamente útil para ferramentas de análise de vestígios GUI.

#### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) O rastreio de eventos de sucesso ativa.
- **TX_SIZE_ERROR** (0x05) O tamanho do tampão de vestígio especificado é demasiado pequeno. Deve ser grande o suficiente para o cabeçalho de vestígios, o registo do objeto, e pelo menos uma entrada de vestígios.
- **TX_NOT_DONE** (0x20) já estava ativado.
- **TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.

#### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

#### <a name="example"></a>Exemplo

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

Filtrar eventos especificados

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Description

Este serviço filtra o(s) evento especificado de ser inserido no tampão de traço ativo. Note que, por padrão, nenhum evento é filtrado após *tx_trace_enable* é chamado.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

- **event_filter_bits**: Bits que correspondem a eventos para filtrar. Vários eventos podem ser filtrados simplesmente juntando as constantes apropriadas. As constantes válidas para esta variável são definidas da seguinte forma:

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** filtro de eventos de sucesso (0x00).
- **TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.

#### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

#### <a name="example"></a>Exemplo

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Eventos especificados não filtrados

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Description

Este serviço não filtra os eventos especificados de modo a que sejam inseridos no tampão de rastreio ativo.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

- **event_unfilter_bits**: Bits que correspondem a eventos a unfilter. Vários eventos podem não ser filtrados simplesmente ou juntando as constantes apropriadas. As constantes válidas para esta variável são definidas da seguinte forma:

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Evento de sucesso sem filtro.
- **TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.

#### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

#### <a name="example"></a>Exemplo

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>Desativar o rastreio do evento

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Description

Este serviço desativa o rastreio de eventos dentro da ThreadX. Isto pode ser útil se a aplicação quiser congelar o atual amortecedor de rastreio de eventos e possivelmente transportá-lo externamente durante o tempo de funcionamento. Uma vez desativado, o **tx_trace_enable** pode ser chamado para recomeçar a rastrear.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

Nenhum.

#### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desativação de vestígios de eventos bem sucedidos.
- **TX_NOT_DONE** (0x20) O rastreio do evento não foi ativado.
- **TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.

#### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

#### <a name="example"></a>Exemplo 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Inserir evento de entrada ISR

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

Este serviço insere o evento de entrada ISR no tampão de vestígios de evento. Deve ser chamado pelo pedido no início do processamento da ISR. O parâmetro fornecido deve identificar o ISR específico para a aplicação.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada 
- **isr_id**: Valor específico da aplicação para identificar o ISR.

#### <a name="return-values"></a>Valores de devolução

**Nenhuma**

#### <a name="allowed-from"></a>Permitido a partir de 

ISRs

#### <a name="example"></a>Exemplo

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Insira o evento de saída do ISR

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Description

Este serviço insere o evento de entrada ISR no tampão de rastreio de eventos. Deve ser chamado pelo pedido no início do processamento da ISR. O parâmetro fornecido deve identificar o ISR na aplicação.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada 

- **isr_id**: Valor específico da aplicação para identificar o ISR.

#### <a name="return-values"></a>Valores de devolução

**Nenhuma**

#### <a name="allowed-from"></a>Permitido a partir de

ISRs

#### <a name="example"></a>Exemplo

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Registar o registo de chamadas completas de aplicação do tampão

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Description

Este serviço regista uma função de chamada de chamada de aplicação que é chamada pela ThreadX quando o tampão de rastreio fica cheio. A aplicação pode então optar por desativar o rastreio e/ou, possivelmente, configurar um novo tampão de traço.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

- **full_buffer_callback**: Função de aplicação para ligar quando o tampão de rastreio estiver cheio. Um valor de NU NULO desativa a chamada de notificação.

#### <a name="return-values"></a>Valores de devolução

**Nenhuma**

#### <a name="allowed-from"></a>Permitido a partir de

ISRs

#### <a name="example"></a>Exemplo

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>Inserir evento de utilizador

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Description

Este serviço insere o evento do utilizador no tampão de vestígios. Os IDs de eventos do utilizador devem ser maiores do que os **TX_TRACE_USER_EVENT_START** constantes, que é definido como 4096. O evento máximo de utilizador é definido pela **TX_TRACE_USER_EVENT_END** constante, que é definida como 65535. Todos os eventos dentro desta gama estão disponíveis para a aplicação. Os campos de informação são específicos da aplicação.

> [!IMPORTANT]
> A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.

#### <a name="input-parameters"></a>Parâmetros de Entrada

- **event_id**: Identificação específica do evento específica para aplicações e deve começar a ser superior **TX_TRACE_USER_EVENT_START** e inferior ou igual a **TX_TRACE_USER_EVENT_END**.
- **info_field_1**: Campo de informação específico para aplicações.
- **info_field_2**: Campo de informação específico para aplicações.
- **info_field_3**: Campo de informação específico para aplicações.
- **info_field_4**: Campo de informação específico para aplicações.

#### <a name="return-values"></a>Valores de devolução
- **TX_SUCCESS** (0x00) Inserção de eventos de utilizador bem sucedidos.
- **TX_NOT_DONE** (0x20) O rastreio do evento não está ativado.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com vestígios ativados.

#### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

#### <a name="example"></a>Exemplo

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Consulte também

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert tx_trace_isr_exit_insert tx_trace_buffer_full_notify