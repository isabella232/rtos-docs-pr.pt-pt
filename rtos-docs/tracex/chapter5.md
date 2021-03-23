---
title: Capítulo 5 - Criação de tampões de vestígios
description: Este capítulo contém uma descrição sobre como construir um tampão de evento Azure RTOS TraceX e também descreve o formato subjacente do tampão.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827523"
---
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="36c3d-103">Capítulo 5 - Criação de tampões de vestígios</span><span class="sxs-lookup"><span data-stu-id="36c3d-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="36c3d-104">Este capítulo contém uma descrição sobre como construir um tampão de evento Azure RTOS TraceX e também descreve o formato subjacente do tampão.</span><span class="sxs-lookup"><span data-stu-id="36c3d-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="36c3d-105">Suporte ao rastreio de eventos ThreadX</span><span class="sxs-lookup"><span data-stu-id="36c3d-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="36c3d-106">A ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços da ThreadX, alterações do estado dos fios e eventos definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="36c3d-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="36c3d-107">A capacidade de rastreio de eventos ThreadX foi concebida principalmente como uma ferramenta pós-morte para analisar as últimas atividades "n" na aplicação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="36c3d-108">A partir desta informação, o desenvolvedor pode detetar problemas e/ou potenciais alvos de otimização.</span><span class="sxs-lookup"><span data-stu-id="36c3d-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="36c3d-109">TraceX exibe graficamente o tampão de vestígios de evento construído pela ThreadX.</span><span class="sxs-lookup"><span data-stu-id="36c3d-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="36c3d-110">O seguinte descreve como construir o tampão e descreve o formato subjacente do tampão.</span><span class="sxs-lookup"><span data-stu-id="36c3d-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="36c3d-111">Habilitação de rastreio de eventos</span><span class="sxs-lookup"><span data-stu-id="36c3d-111">Enabling Event Trace</span></span>

<span data-ttu-id="36c3d-112">Para ativar o rastreio do evento, defina as constantes do carimbo temporal, construa a biblioteca ThreadX com **TX_ENABLE_EVENT_TRACE** definida e permita o rastreio chamando a função **tx_trace_enable.**</span><span class="sxs-lookup"><span data-stu-id="36c3d-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="36c3d-113">Definição de constantes Time-Stamp</span><span class="sxs-lookup"><span data-stu-id="36c3d-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="36c3d-114">As constantes do carimbo de tempo são concebidas para fornecer ao desenvolvedor o controlo sobre o carimbo de tempo utilizado nas entradas de vestígios do caso.</span><span class="sxs-lookup"><span data-stu-id="36c3d-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="36c3d-115">As duas constantes de carimbo temporal e os seus valores predefinidos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="36c3d-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="36c3d-116">As constantes acima são definidas em **tx_port.h** e criam um carimbo de tempo "falso" que simplesmente incrementa por um em cada evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="36c3d-117">Segue-se um exemplo de uma definição de tempotamos real:</span><span class="sxs-lookup"><span data-stu-id="36c3d-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="36c3d-118">As constantes acima especificam um temporizador de 32 bits que é obtido lendo o endereço 0x13000004.</span><span class="sxs-lookup"><span data-stu-id="36c3d-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="36c3d-119">A maioria dos selos de tempo específicos da aplicação devem ser configurados de forma semelhante.</span><span class="sxs-lookup"><span data-stu-id="36c3d-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="36c3d-120">Exportação do tampão de vestígios</span><span class="sxs-lookup"><span data-stu-id="36c3d-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="36c3d-121">A TraceX necessita do tampão de traços num formato binário, Intel HEX ou Motorola S-Record no anfitrião.</span><span class="sxs-lookup"><span data-stu-id="36c3d-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="36c3d-122">A maneira mais fácil de o conseguir é parar o alvo e instruir o seu depurgger a despejar a área de memória que forneceu para ***tx_trace_enable*** funcionar num ficheiro no anfitrião.</span><span class="sxs-lookup"><span data-stu-id="36c3d-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="36c3d-123">***Tenha cuidado para não parar o alvo dentro de um código de recolha de vestígios em si. Fazê-lo pode causar informações inválidas de vestígios. Se o programa for interrompido dentro do ThreadX, é melhor passar por cima de qualquer macro de inserção de vestígios antes de despejar o tampão de vestígios.***</span><span class="sxs-lookup"><span data-stu-id="36c3d-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-124">*O apêndice D mostra como despejar o tampão de vestígios dentro de uma variedade de ferramentas de desenvolvimento.*</span><span class="sxs-lookup"><span data-stu-id="36c3d-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="36c3d-125">API de rastreio de eventos estendidos</span><span class="sxs-lookup"><span data-stu-id="36c3d-125">Extended Event Trace API</span></span>

<span data-ttu-id="36c3d-126">Quando a ThreadX é construída com **TX_ENABLE_EVENT_TRACE** definida, os seguintes novos apis de evento estão disponíveis para a aplicação:</span><span class="sxs-lookup"><span data-stu-id="36c3d-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="36c3d-127">tx_trace_enable: *Ativar o rastreio do evento*</span><span class="sxs-lookup"><span data-stu-id="36c3d-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="36c3d-128">tx_trace_event_filter: *Filtrar eventos especificados*</span><span class="sxs-lookup"><span data-stu-id="36c3d-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="36c3d-129">tx_trace_event_unfilter: *Eventos especificados por não filtro*</span><span class="sxs-lookup"><span data-stu-id="36c3d-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="36c3d-130">tx_trace_disable: *Desativar o rastreio do evento*</span><span class="sxs-lookup"><span data-stu-id="36c3d-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="36c3d-131">tx_trace_isr_enter_insert: *Insira o evento de rastreio de entrada ISR*</span><span class="sxs-lookup"><span data-stu-id="36c3d-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="36c3d-132">tx_trace_isr_exit_insert: *Insira o evento de rastreio de saída DO ISR*</span><span class="sxs-lookup"><span data-stu-id="36c3d-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="36c3d-133">tx_trace_buffer_full_notify: Registar *o registo de chamadas completas de aplicação do tampão*</span><span class="sxs-lookup"><span data-stu-id="36c3d-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="36c3d-134">tx_trace_user_event_insert: Inserir *o evento do utilizador*</span><span class="sxs-lookup"><span data-stu-id="36c3d-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="36c3d-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="36c3d-135">tx_trace_enable</span></span>

<span data-ttu-id="36c3d-136">Ativar o rastreio do evento</span><span class="sxs-lookup"><span data-stu-id="36c3d-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="36c3d-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-138">Description</span></span>
<span data-ttu-id="36c3d-139">Este serviço permite rastrear o rastreio de eventos dentro da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="36c3d-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="36c3d-140">A aplicação fornece o tampão de vestígios e o número máximo de objetos ThreadX.</span><span class="sxs-lookup"><span data-stu-id="36c3d-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-141">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-142">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-142">Input Parameters</span></span>

- <span data-ttu-id="36c3d-143">**trace_buffer_start**: Ponteiro para o início do tampão de vestígios fornecido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="36c3d-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="36c3d-144">**trace_buffer_size:** Número total de bytes na memória para o tampão de vestígios.</span><span class="sxs-lookup"><span data-stu-id="36c3d-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="36c3d-145">Quanto maior for o tampão de vestígios, mais entradas é capaz de armazenar.</span><span class="sxs-lookup"><span data-stu-id="36c3d-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="36c3d-146">**registry_entries**: Número de aplicações Os objetos ThreadX devem manter no registo de vestígios.</span><span class="sxs-lookup"><span data-stu-id="36c3d-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="36c3d-147">O registo é utilizado para correlacionar endereços de objetos com nomes de objetos.</span><span class="sxs-lookup"><span data-stu-id="36c3d-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="36c3d-148">Isto é altamente útil para ferramentas de análise de vestígios GUI.</span><span class="sxs-lookup"><span data-stu-id="36c3d-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-149">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-149">Return Values</span></span>

- <span data-ttu-id="36c3d-150">**TX_SUCCESS** (0x00) O rastreio de eventos de sucesso ativa.</span><span class="sxs-lookup"><span data-stu-id="36c3d-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="36c3d-151">**TX_SIZE_ERROR** (0x05) O tamanho do tampão de vestígio especificado é demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="36c3d-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="36c3d-152">Deve ser grande o suficiente para o cabeçalho de vestígios, o registo do objeto, e pelo menos uma entrada de vestígios.</span><span class="sxs-lookup"><span data-stu-id="36c3d-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="36c3d-153">**TX_NOT_DONE** (0x20) já estava ativado.</span><span class="sxs-lookup"><span data-stu-id="36c3d-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="36c3d-154">**TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.</span><span class="sxs-lookup"><span data-stu-id="36c3d-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-155">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-155">Allowed From</span></span>

<span data-ttu-id="36c3d-156">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="36c3d-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-158">See Also</span></span>

<span data-ttu-id="36c3d-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="36c3d-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="36c3d-160">tx_trace_event_filter</span></span>

<span data-ttu-id="36c3d-161">Filtrar eventos especificados</span><span class="sxs-lookup"><span data-stu-id="36c3d-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-162">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="36c3d-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-163">Description</span></span>

<span data-ttu-id="36c3d-164">Este serviço filtra o(s) evento especificado de ser inserido no tampão de traço ativo.</span><span class="sxs-lookup"><span data-stu-id="36c3d-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="36c3d-165">Note que, por padrão, nenhum evento é filtrado após *tx_trace_enable* é chamado.</span><span class="sxs-lookup"><span data-stu-id="36c3d-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-166">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-167">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-167">Input Parameters</span></span>

- <span data-ttu-id="36c3d-168">**event_filter_bits**: Bits que correspondem a eventos para filtrar.</span><span class="sxs-lookup"><span data-stu-id="36c3d-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="36c3d-169">Vários eventos podem ser filtrados simplesmente juntando as constantes apropriadas.</span><span class="sxs-lookup"><span data-stu-id="36c3d-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="36c3d-170">As constantes válidas para esta variável são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="36c3d-170">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="36c3d-171">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-171">Return Values</span></span>

- <span data-ttu-id="36c3d-172">**TX_SUCCESS** filtro de eventos de sucesso (0x00).</span><span class="sxs-lookup"><span data-stu-id="36c3d-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="36c3d-173">**TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.</span><span class="sxs-lookup"><span data-stu-id="36c3d-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-174">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-174">Allowed From</span></span>

<span data-ttu-id="36c3d-175">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="36c3d-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-177">See Also</span></span>

<span data-ttu-id="36c3d-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="36c3d-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="36c3d-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="36c3d-180">Eventos especificados não filtrados</span><span class="sxs-lookup"><span data-stu-id="36c3d-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="36c3d-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-182">Description</span></span>

<span data-ttu-id="36c3d-183">Este serviço não filtra os eventos especificados de modo a que sejam inseridos no tampão de rastreio ativo.</span><span class="sxs-lookup"><span data-stu-id="36c3d-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-184">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-185">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-185">Input Parameters</span></span>

- <span data-ttu-id="36c3d-186">**event_unfilter_bits**: Bits que correspondem a eventos a unfilter.</span><span class="sxs-lookup"><span data-stu-id="36c3d-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="36c3d-187">Vários eventos podem não ser filtrados simplesmente ou juntando as constantes apropriadas.</span><span class="sxs-lookup"><span data-stu-id="36c3d-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="36c3d-188">As constantes válidas para esta variável são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="36c3d-188">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="36c3d-189">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-189">Return Values</span></span>

- <span data-ttu-id="36c3d-190">**TX_SUCCESS** (0x00) Evento de sucesso sem filtro.</span><span class="sxs-lookup"><span data-stu-id="36c3d-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="36c3d-191">**TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.</span><span class="sxs-lookup"><span data-stu-id="36c3d-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-192">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-192">Allowed From</span></span>

<span data-ttu-id="36c3d-193">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="36c3d-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-194">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-195">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-195">See Also</span></span>

<span data-ttu-id="36c3d-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="36c3d-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="36c3d-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="36c3d-198">Desativar o rastreio do evento</span><span class="sxs-lookup"><span data-stu-id="36c3d-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-199">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="36c3d-200">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-200">Description</span></span>

<span data-ttu-id="36c3d-201">Este serviço desativa o rastreio de eventos dentro da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="36c3d-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="36c3d-202">Isto pode ser útil se a aplicação quiser congelar o atual amortecedor de rastreio de eventos e possivelmente transportá-lo externamente durante o tempo de funcionamento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="36c3d-203">Uma vez desativado, o **tx_trace_enable** pode ser chamado para recomeçar a rastrear.</span><span class="sxs-lookup"><span data-stu-id="36c3d-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-204">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-205">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-205">Input Parameters</span></span>

<span data-ttu-id="36c3d-206">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="36c3d-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-207">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-207">Return Values</span></span>

- <span data-ttu-id="36c3d-208">**TX_SUCCESS** (0x00) Desativação de vestígios de eventos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="36c3d-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="36c3d-209">**TX_NOT_DONE** (0x20) O rastreio do evento não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="36c3d-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="36c3d-210">**TX_FEATURE_NOT_ENABLED** sistema (0xFF) não foi compilado com vestígios ativados.</span><span class="sxs-lookup"><span data-stu-id="36c3d-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-211">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-211">Allowed From</span></span>

<span data-ttu-id="36c3d-212">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="36c3d-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-213">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-214">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-214">See Also</span></span>

<span data-ttu-id="36c3d-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="36c3d-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="36c3d-217">Inserir evento de entrada ISR</span><span class="sxs-lookup"><span data-stu-id="36c3d-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-218">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="36c3d-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-219">Description</span></span>

<span data-ttu-id="36c3d-220">Este serviço insere o evento de entrada ISR no tampão de vestígios de evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="36c3d-221">Deve ser chamado pelo pedido no início do processamento da ISR.</span><span class="sxs-lookup"><span data-stu-id="36c3d-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="36c3d-222">O parâmetro fornecido deve identificar o ISR específico para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-223">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-224">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-224">Input Parameters</span></span> 
- <span data-ttu-id="36c3d-225">**isr_id**: Valor específico da aplicação para identificar o ISR.</span><span class="sxs-lookup"><span data-stu-id="36c3d-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-226">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-226">Return Values</span></span>

<span data-ttu-id="36c3d-227">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="36c3d-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-228">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-228">Allowed From</span></span> 

<span data-ttu-id="36c3d-229">ISRs</span><span class="sxs-lookup"><span data-stu-id="36c3d-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-231">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-231">See Also</span></span>

<span data-ttu-id="36c3d-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="36c3d-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="36c3d-234">Insira o evento de saída do ISR</span><span class="sxs-lookup"><span data-stu-id="36c3d-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="36c3d-236">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-236">Description</span></span>

<span data-ttu-id="36c3d-237">Este serviço insere o evento de entrada ISR no tampão de rastreio de eventos.</span><span class="sxs-lookup"><span data-stu-id="36c3d-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="36c3d-238">Deve ser chamado pelo pedido no início do processamento da ISR.</span><span class="sxs-lookup"><span data-stu-id="36c3d-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="36c3d-239">O parâmetro fornecido deve identificar o ISR na aplicação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-240">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-241">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-241">Input Parameters</span></span> 

- <span data-ttu-id="36c3d-242">**isr_id**: Valor específico da aplicação para identificar o ISR.</span><span class="sxs-lookup"><span data-stu-id="36c3d-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-243">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-243">Return Values</span></span>

<span data-ttu-id="36c3d-244">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="36c3d-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-245">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-245">Allowed From</span></span>

<span data-ttu-id="36c3d-246">ISRs</span><span class="sxs-lookup"><span data-stu-id="36c3d-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-247">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-248">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-248">See Also</span></span>

<span data-ttu-id="36c3d-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="36c3d-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="36c3d-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="36c3d-251">Registar o registo de chamadas completas de aplicação do tampão</span><span class="sxs-lookup"><span data-stu-id="36c3d-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-252">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="36c3d-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-253">Description</span></span>

<span data-ttu-id="36c3d-254">Este serviço regista uma função de chamada de chamada de aplicação que é chamada pela ThreadX quando o tampão de rastreio fica cheio.</span><span class="sxs-lookup"><span data-stu-id="36c3d-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="36c3d-255">A aplicação pode então optar por desativar o rastreio e/ou, possivelmente, configurar um novo tampão de traço.</span><span class="sxs-lookup"><span data-stu-id="36c3d-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-256">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-257">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-257">Input Parameters</span></span>

- <span data-ttu-id="36c3d-258">**full_buffer_callback**: Função de aplicação para ligar quando o tampão de rastreio estiver cheio.</span><span class="sxs-lookup"><span data-stu-id="36c3d-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="36c3d-259">Um valor de NU NULO desativa a chamada de notificação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-260">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-260">Return Values</span></span>

<span data-ttu-id="36c3d-261">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="36c3d-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-262">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-262">Allowed From</span></span>

<span data-ttu-id="36c3d-263">ISRs</span><span class="sxs-lookup"><span data-stu-id="36c3d-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-264">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-265">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-265">See Also</span></span>

<span data-ttu-id="36c3d-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="36c3d-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="36c3d-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="36c3d-268">Inserir evento de utilizador</span><span class="sxs-lookup"><span data-stu-id="36c3d-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="36c3d-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="36c3d-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="36c3d-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="36c3d-270">Description</span></span>

<span data-ttu-id="36c3d-271">Este serviço insere o evento do utilizador no tampão de vestígios.</span><span class="sxs-lookup"><span data-stu-id="36c3d-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="36c3d-272">Os IDs de eventos do utilizador devem ser maiores do que os **TX_TRACE_USER_EVENT_START** constantes, que é definido como 4096.</span><span class="sxs-lookup"><span data-stu-id="36c3d-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="36c3d-273">O evento máximo de utilizador é definido pela **TX_TRACE_USER_EVENT_END** constante, que é definida como 65535.</span><span class="sxs-lookup"><span data-stu-id="36c3d-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="36c3d-274">Todos os eventos dentro desta gama estão disponíveis para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-274">All events within this range are available to the application.</span></span> <span data-ttu-id="36c3d-275">Os campos de informação são específicos da aplicação.</span><span class="sxs-lookup"><span data-stu-id="36c3d-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36c3d-276">A biblioteca e aplicação ThreadX devem ser construídas com **TX_ENABLE_EVENT_TRACE** definidas para utilizar o rastreio do evento.</span><span class="sxs-lookup"><span data-stu-id="36c3d-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="36c3d-277">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="36c3d-277">Input Parameters</span></span>

- <span data-ttu-id="36c3d-278">**event_id**: Identificação específica do evento específica para aplicações e deve começar a ser superior **TX_TRACE_USER_EVENT_START** e inferior ou igual a **TX_TRACE_USER_EVENT_END**.</span><span class="sxs-lookup"><span data-stu-id="36c3d-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="36c3d-279">**info_field_1**: Campo de informação específico para aplicações.</span><span class="sxs-lookup"><span data-stu-id="36c3d-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="36c3d-280">**info_field_2**: Campo de informação específico para aplicações.</span><span class="sxs-lookup"><span data-stu-id="36c3d-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="36c3d-281">**info_field_3**: Campo de informação específico para aplicações.</span><span class="sxs-lookup"><span data-stu-id="36c3d-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="36c3d-282">**info_field_4**: Campo de informação específico para aplicações.</span><span class="sxs-lookup"><span data-stu-id="36c3d-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="36c3d-283">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="36c3d-283">Return Values</span></span>
- <span data-ttu-id="36c3d-284">**TX_SUCCESS** (0x00) Inserção de eventos de utilizador bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="36c3d-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="36c3d-285">**TX_NOT_DONE** (0x20) O rastreio do evento não está ativado.</span><span class="sxs-lookup"><span data-stu-id="36c3d-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="36c3d-286">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com vestígios ativados.</span><span class="sxs-lookup"><span data-stu-id="36c3d-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="36c3d-287">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="36c3d-287">Allowed From</span></span>

<span data-ttu-id="36c3d-288">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="36c3d-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="36c3d-289">Exemplo</span><span class="sxs-lookup"><span data-stu-id="36c3d-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="36c3d-290">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36c3d-290">See Also</span></span>

<span data-ttu-id="36c3d-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert tx_trace_isr_exit_insert tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="36c3d-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>