---
title: Capítulo 11 - Formato do tampão de vestígios de evento
description: A ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços Azure RTOS ThreadX, alterações de estado de thread e eventos definidos pelo utilizador.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827577"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="6bd81-103">Capítulo 11 - Formato do tampão de vestígios de evento</span><span class="sxs-lookup"><span data-stu-id="6bd81-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="6bd81-104">O Azure RTOS ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços da ThreadX, alterações do estado do fio e eventos definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="6bd81-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="6bd81-105">Para utilizar vestígios de eventos, basta construir as bibliotecas ThreadX, NetX e FileX com **TX_ENABLE_EVENT_TRACE** definidas e ativar o rastreio, chamando a função **_tx_trace_enable._**</span><span class="sxs-lookup"><span data-stu-id="6bd81-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="6bd81-106">Este capítulo descreve este processo.</span><span class="sxs-lookup"><span data-stu-id="6bd81-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="6bd81-107">Formato de rastreio de eventos</span><span class="sxs-lookup"><span data-stu-id="6bd81-107">Event Trace Format</span></span>

<span data-ttu-id="6bd81-108">O formato do tampão de rastreio de evento ThreadX é dividido em três secções, nomeadamente o cabeçalho de controlo, o registo de objetos e as entradas de vestígios.</span><span class="sxs-lookup"><span data-stu-id="6bd81-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="6bd81-109">O seguinte descreve o layout geral do tampão de rastreio de evento ThreadX:</span><span class="sxs-lookup"><span data-stu-id="6bd81-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="6bd81-110">**Cabeçalho de controlo**</span><span class="sxs-lookup"><span data-stu-id="6bd81-110">**Control Header**</span></span>

<span data-ttu-id="6bd81-111">**Entrada do Registo de Objetos 0**</span><span class="sxs-lookup"><span data-stu-id="6bd81-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="6bd81-112">**…**</span><span class="sxs-lookup"><span data-stu-id="6bd81-112">**…**</span></span>

<span data-ttu-id="6bd81-113">**Entrada de Registo de Objetos "n"**</span><span class="sxs-lookup"><span data-stu-id="6bd81-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="6bd81-114">**Entrada de rastreio de evento 0**</span><span class="sxs-lookup"><span data-stu-id="6bd81-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="6bd81-115">**…**</span><span class="sxs-lookup"><span data-stu-id="6bd81-115">**…**</span></span>

<span data-ttu-id="6bd81-116">**Entrada de vestígios de evento "n"**</span><span class="sxs-lookup"><span data-stu-id="6bd81-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="6bd81-117">Cabeçalho de controlo de vestígios de evento</span><span class="sxs-lookup"><span data-stu-id="6bd81-117">Event Trace Control Header</span></span>

<span data-ttu-id="6bd81-118">O cabeçalho de controlo define o layout exato do tampão de vestígios do evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="6bd81-119">Isto inclui quantos objetos ThreadX podem ser registados, bem como quantos eventos podem ser gravados.</span><span class="sxs-lookup"><span data-stu-id="6bd81-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="6bd81-120">Além disso, o cabeçalho de controlo define onde reside cada um dos elementos do tampão de vestígios.</span><span class="sxs-lookup"><span data-stu-id="6bd81-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="6bd81-121">A seguinte estrutura de dados define o cabeçalho de controlo:</span><span class="sxs-lookup"><span data-stu-id="6bd81-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="6bd81-122">ID do cabeçalho de controlo</span><span class="sxs-lookup"><span data-stu-id="6bd81-122">Control Header ID</span></span>

<span data-ttu-id="6bd81-123">O ID do cabeçalho de controlo consiste no valor HEX de 32 bits de 0x54585442, que corresponde aos caracteres ASCII ***TXTB***.</span><span class="sxs-lookup"><span data-stu-id="6bd81-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="6bd81-124">Uma vez que este valor é escrito como uma variável não assinada de 32 bits, também pode ser usado para detetar a endianidade do tampão de traço de evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="6bd81-125">Por exemplo, se o valor nos primeiros quatro byes da memória for 0x54, 0x58, 0x54, 0x42, o tampão de traço de evento foi escrito em grande formato endiano.</span><span class="sxs-lookup"><span data-stu-id="6bd81-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="6bd81-126">Caso contrário, o tampão de traço do evento foi escrito em pequeno formato endiano.</span><span class="sxs-lookup"><span data-stu-id="6bd81-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="6bd81-127">Máscara válida do temporizador</span><span class="sxs-lookup"><span data-stu-id="6bd81-127">Timer Valid Mask</span></span>

<span data-ttu-id="6bd81-128">A máscara válida do temporizador define quantas bits do relógio de tempo nas entradas de vestígios de eventos reais são válidas.</span><span class="sxs-lookup"><span data-stu-id="6bd81-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="6bd81-129">Por exemplo, se a fonte de carimbo de tempo tiver 16 bits, o valor neste campo deve ser 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="6bd81-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="6bd81-130">Uma fonte de selo de 32 bits teria um valor de 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="6bd81-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="6bd81-131">Este valor é definido pela ***TX_TRACE_TIME_MASK** _ constante em _*_tx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="6bd81-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="6bd81-132">Endereço base de rastreio</span><span class="sxs-lookup"><span data-stu-id="6bd81-132">Trace Base Address</span></span>

<span data-ttu-id="6bd81-133">O endereço da base de tampão de traços é o endereço que a aplicação especifica como o início do tampão de rastreio na chamada ***tx_trace_enable.***</span><span class="sxs-lookup"><span data-stu-id="6bd81-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="6bd81-134">Este endereço é mantido para a utilização exclusiva da ferramenta de análise para obter compensações bufferrelativas para os vários elementos do tampão.</span><span class="sxs-lookup"><span data-stu-id="6bd81-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="6bd81-135">Por exemplo, a compensação relativa tampão do evento atual no tampão de vestígios é calculada por simples subtração do endereço de base a partir do endereço do evento atual.</span><span class="sxs-lookup"><span data-stu-id="6bd81-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="6bd81-136">Ponteiros de início e fim do registo</span><span class="sxs-lookup"><span data-stu-id="6bd81-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="6bd81-137">O ponteiro de início do registo aponta para o endereço da primeira entrada de registo de objetos, enquanto o ponteiro final do registo aponta para o endereço im.. /mediativamente após a última entrada de registo.</span><span class="sxs-lookup"><span data-stu-id="6bd81-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="6bd81-138">Estes valores são configurados durante o processamento *tx_trace_enable* e não são alterados durante a duração do rastreio.</span><span class="sxs-lookup"><span data-stu-id="6bd81-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="6bd81-139">Tamanho do nome do registo</span><span class="sxs-lookup"><span data-stu-id="6bd81-139">Registry Name Size</span></span>

<span data-ttu-id="6bd81-140">O tamanho do nome do registo define o tamanho máximo em bytes para cada nome de objeto na entrada do registo e é definido pelo símbolo \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span><span class="sxs-lookup"><span data-stu-id="6bd81-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="6bd81-141">O valor predefinido é de 32 e é definido em _*_tx_trace.h_*_.</span><span class="sxs-lookup"><span data-stu-id="6bd81-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="6bd81-142">O nome do objeto corresponde ao nome dado pela aplicação quando o objeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="6bd81-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="6bd81-143">Por exemplo, o nome do registo do objeto para um fio é o nome fornecido pela aplicação à chamada _\*_tx_thread_create_\*\*.</span><span class="sxs-lookup"><span data-stu-id="6bd81-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="6bd81-144">Ponteiros de início e fim do tampão</span><span class="sxs-lookup"><span data-stu-id="6bd81-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="6bd81-145">O ponto de partida do marcador do resultado aponta para o endereço da primeira entrada de vestígios, enquanto o ponteiro final do registo aponta para o endereço im. /mediativamente seguindo a última entrada de vestígios.</span><span class="sxs-lookup"><span data-stu-id="6bd81-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="6bd81-146">Estes valores são configurados durante o ***tx_trace_enable</processamento*** e não são alterados durante toda a duração do rastreio.</span><span class="sxs-lookup"><span data-stu-id="6bd81-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="6bd81-147">Ponteiro-tampão atual</span><span class="sxs-lookup"><span data-stu-id="6bd81-147">Current Buffer Pointer</span></span>

<span data-ttu-id="6bd81-148">O ponto de marcação do ponto de corrente do evento aponta para o endereço da entrada de vestígios mais antigo.</span><span class="sxs-lookup"><span data-stu-id="6bd81-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="6bd81-149">Uma vez que as entradas de vestígios são mantidas numa lista circular, o ponteiro-tampão atual também representa a próxima entrada de vestígios a ser escrita.</span><span class="sxs-lookup"><span data-stu-id="6bd81-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="6bd81-150">Registo de objetos de rastreio de evento</span><span class="sxs-lookup"><span data-stu-id="6bd81-150">Event Trace Object Registry</span></span>

<span data-ttu-id="6bd81-151">O registo de objetos de rastreio de eventos contém \***n** _ entradas de registo de objetos que correspondem aos objetos criados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="6bd81-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="6bd81-152">O principal objetivo do registo de objetos é que as ferramentas de análise externas correlacionem os nomes reais dos objetos com os endereços do objeto das entradas do tampão de traço.</span><span class="sxs-lookup"><span data-stu-id="6bd81-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="6bd81-153">O número de entradas de registo é especificado pela aplicação na chamada _ *_tx_trace_enable_*\* .</span><span class="sxs-lookup"><span data-stu-id="6bd81-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="6bd81-154">Cada entrada de registo de objetos contém informações sobre um objeto ThreadX específico previamente criado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="6bd81-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="6bd81-155">A seguinte estrutura de dados define cada entrada de registo de objetos:</span><span class="sxs-lookup"><span data-stu-id="6bd81-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="6bd81-156">Bandeira disponível de objeto</span><span class="sxs-lookup"><span data-stu-id="6bd81-156">Object Available Flag</span></span>

<span data-ttu-id="6bd81-157">A bandeira disponível do objeto é definida para 1 se a entrada do registo do objeto estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="6bd81-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="6bd81-158">Caso contrário, se o valor não for 1, a entrada no registo do objeto não está disponível.</span><span class="sxs-lookup"><span data-stu-id="6bd81-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="6bd81-159">Note que a entrada ainda pode conter informações válidas, mesmo estando disponível.</span><span class="sxs-lookup"><span data-stu-id="6bd81-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="6bd81-160">Tipo de entrada de objeto</span><span class="sxs-lookup"><span data-stu-id="6bd81-160">Object Entry Type</span></span>

<span data-ttu-id="6bd81-161">O tipo de entrada do objeto identifica o tipo de objeto nesta entrada.</span><span class="sxs-lookup"><span data-stu-id="6bd81-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="6bd81-162">Segue-se uma lista dos tipos de objetos válidos:</span><span class="sxs-lookup"><span data-stu-id="6bd81-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="6bd81-163">**Valor**</span><span class="sxs-lookup"><span data-stu-id="6bd81-163">**Value**</span></span> | <span data-ttu-id="6bd81-164">**Tipo de Objeto**</span><span class="sxs-lookup"><span data-stu-id="6bd81-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="6bd81-165">0</span><span class="sxs-lookup"><span data-stu-id="6bd81-165">0</span></span>         | <span data-ttu-id="6bd81-166">Não é válido</span><span class="sxs-lookup"><span data-stu-id="6bd81-166">Not Valid</span></span>       |
| <span data-ttu-id="6bd81-167">1</span><span class="sxs-lookup"><span data-stu-id="6bd81-167">1</span></span>         | <span data-ttu-id="6bd81-168">Fio</span><span class="sxs-lookup"><span data-stu-id="6bd81-168">Thread</span></span>          |
| <span data-ttu-id="6bd81-169">2</span><span class="sxs-lookup"><span data-stu-id="6bd81-169">2</span></span>         | <span data-ttu-id="6bd81-170">Temporizador</span><span class="sxs-lookup"><span data-stu-id="6bd81-170">Timer</span></span> |
| <span data-ttu-id="6bd81-171">3</span><span class="sxs-lookup"><span data-stu-id="6bd81-171">3</span></span>         | <span data-ttu-id="6bd81-172">Fila</span><span class="sxs-lookup"><span data-stu-id="6bd81-172">Queue</span></span> |
| <span data-ttu-id="6bd81-173">4</span><span class="sxs-lookup"><span data-stu-id="6bd81-173">4</span></span>         | <span data-ttu-id="6bd81-174">Semáforo</span><span class="sxs-lookup"><span data-stu-id="6bd81-174">Semaphore</span></span> |
| <span data-ttu-id="6bd81-175">5</span><span class="sxs-lookup"><span data-stu-id="6bd81-175">5</span></span>         | <span data-ttu-id="6bd81-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="6bd81-176">Mutex</span></span> |
| <span data-ttu-id="6bd81-177">6</span><span class="sxs-lookup"><span data-stu-id="6bd81-177">6</span></span>         | <span data-ttu-id="6bd81-178">Grupo de Bandeiras de Eventos</span><span class="sxs-lookup"><span data-stu-id="6bd81-178">Event Flags Group</span></span> |
| <span data-ttu-id="6bd81-179">7</span><span class="sxs-lookup"><span data-stu-id="6bd81-179">7</span></span>         | <span data-ttu-id="6bd81-180">Piscina de Blocos</span><span class="sxs-lookup"><span data-stu-id="6bd81-180">Block Pool</span></span> |
| <span data-ttu-id="6bd81-181">8</span><span class="sxs-lookup"><span data-stu-id="6bd81-181">8</span></span>         | <span data-ttu-id="6bd81-182">Piscina Byte</span><span class="sxs-lookup"><span data-stu-id="6bd81-182">Byte Pool</span></span> |
| <span data-ttu-id="6bd81-183">9</span><span class="sxs-lookup"><span data-stu-id="6bd81-183">9</span></span>         | <span data-ttu-id="6bd81-184">.. /media</span><span class="sxs-lookup"><span data-stu-id="6bd81-184">../media</span></span> |
| <span data-ttu-id="6bd81-185">10</span><span class="sxs-lookup"><span data-stu-id="6bd81-185">10</span></span>        | <span data-ttu-id="6bd81-186">Ficheiro</span><span class="sxs-lookup"><span data-stu-id="6bd81-186">File</span></span> |
| <span data-ttu-id="6bd81-187">11</span><span class="sxs-lookup"><span data-stu-id="6bd81-187">11</span></span>        | <span data-ttu-id="6bd81-188">IP</span><span class="sxs-lookup"><span data-stu-id="6bd81-188">IP</span></span> |
| <span data-ttu-id="6bd81-189">12</span><span class="sxs-lookup"><span data-stu-id="6bd81-189">12</span></span>        | <span data-ttu-id="6bd81-190">Piscina de Pacotes</span><span class="sxs-lookup"><span data-stu-id="6bd81-190">Packet Pool</span></span> |
| <span data-ttu-id="6bd81-191">13</span><span class="sxs-lookup"><span data-stu-id="6bd81-191">13</span></span>        | <span data-ttu-id="6bd81-192">Tomada TCP</span><span class="sxs-lookup"><span data-stu-id="6bd81-192">TCP Socket</span></span> |
| <span data-ttu-id="6bd81-193">14</span><span class="sxs-lookup"><span data-stu-id="6bd81-193">14</span></span>        | <span data-ttu-id="6bd81-194">Tomada UDP</span><span class="sxs-lookup"><span data-stu-id="6bd81-194">UDP Socket</span></span> |
| <span data-ttu-id="6bd81-195">15-20</span><span class="sxs-lookup"><span data-stu-id="6bd81-195">15-20</span></span>     | <span data-ttu-id="6bd81-196">Reservado</span><span class="sxs-lookup"><span data-stu-id="6bd81-196">Reserved</span></span> |  
| <span data-ttu-id="6bd81-197">21</span><span class="sxs-lookup"><span data-stu-id="6bd81-197">21</span></span>        | <span data-ttu-id="6bd81-198">Dispositivo usb host Stack</span><span class="sxs-lookup"><span data-stu-id="6bd81-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="6bd81-199">22</span><span class="sxs-lookup"><span data-stu-id="6bd81-199">22</span></span>        | <span data-ttu-id="6bd81-200">Interface de pilha de anfitrião USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="6bd81-201">23</span><span class="sxs-lookup"><span data-stu-id="6bd81-201">23</span></span>        | <span data-ttu-id="6bd81-202">Ponto final do anfitrião USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="6bd81-203">24</span><span class="sxs-lookup"><span data-stu-id="6bd81-203">24</span></span>        | <span data-ttu-id="6bd81-204">Classe de anfitrião USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-204">USB Host Class</span></span> |
| <span data-ttu-id="6bd81-205">25</span><span class="sxs-lookup"><span data-stu-id="6bd81-205">25</span></span>        | <span data-ttu-id="6bd81-206">Dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-206">USB Device</span></span> |
| <span data-ttu-id="6bd81-207">26</span><span class="sxs-lookup"><span data-stu-id="6bd81-207">26</span></span>        | <span data-ttu-id="6bd81-208">Interface do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-208">USB Device Interface</span></span> |
| <span data-ttu-id="6bd81-209">27</span><span class="sxs-lookup"><span data-stu-id="6bd81-209">27</span></span>        | <span data-ttu-id="6bd81-210">Ponto de final do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="6bd81-211">28</span><span class="sxs-lookup"><span data-stu-id="6bd81-211">28</span></span>        | <span data-ttu-id="6bd81-212">Classe de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="6bd81-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="6bd81-213">Ponteiro de objetos</span><span class="sxs-lookup"><span data-stu-id="6bd81-213">Object Pointer</span></span>

<span data-ttu-id="6bd81-214">O ponteiro do objeto especifica o endereço do objeto que é utilizado para aceder ao objeto utilizando a API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6bd81-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="6bd81-215">Campos Reservados a Objetos</span><span class="sxs-lookup"><span data-stu-id="6bd81-215">Object Reserved Fields</span></span>

<span data-ttu-id="6bd81-216">Para todos os objetos que não sejam fios, estes campos reservados devem ser 0.</span><span class="sxs-lookup"><span data-stu-id="6bd81-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="6bd81-217">Para os fios, a prioridade do fio no momento da sua entrada no registo é colocada nestes dois campos reservados.</span><span class="sxs-lookup"><span data-stu-id="6bd81-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="6bd81-218">Parâmetros de objeto</span><span class="sxs-lookup"><span data-stu-id="6bd81-218">Object Parameters</span></span>

<span data-ttu-id="6bd81-219">Os parâmetros do objeto contêm informações suplementares sobre o objeto.</span><span class="sxs-lookup"><span data-stu-id="6bd81-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="6bd81-220">O seguinte descreve as informações suplementares para cada objeto ThreadX:</span><span class="sxs-lookup"><span data-stu-id="6bd81-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="6bd81-221">**Tipo de Objeto**</span><span class="sxs-lookup"><span data-stu-id="6bd81-221">**Object Type**</span></span>        | <span data-ttu-id="6bd81-222">**Parâmetro 1**</span><span class="sxs-lookup"><span data-stu-id="6bd81-222">**Parameter 1**</span></span>  | <span data-ttu-id="6bd81-223">**Parâmetro 2**</span><span class="sxs-lookup"><span data-stu-id="6bd81-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="6bd81-224">Fio</span><span class="sxs-lookup"><span data-stu-id="6bd81-224">Thread</span></span>                 | <span data-ttu-id="6bd81-225">Início da Pilha</span><span class="sxs-lookup"><span data-stu-id="6bd81-225">Stack Start</span></span>      | <span data-ttu-id="6bd81-226">Tamanho da pilha</span><span class="sxs-lookup"><span data-stu-id="6bd81-226">Stack Size</span></span> |
| <span data-ttu-id="6bd81-227">Temporizador</span><span class="sxs-lookup"><span data-stu-id="6bd81-227">Timer</span></span>                  | <span data-ttu-id="6bd81-228">Carrapatos Iniciais</span><span class="sxs-lookup"><span data-stu-id="6bd81-228">Initial Ticks</span></span> | <span data-ttu-id="6bd81-229">Reagendar Carrapatos</span><span class="sxs-lookup"><span data-stu-id="6bd81-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="6bd81-230">Fila</span><span class="sxs-lookup"><span data-stu-id="6bd81-230">Queue</span></span>                  | <span data-ttu-id="6bd81-231">Tamanho da fila</span><span class="sxs-lookup"><span data-stu-id="6bd81-231">Queue Size</span></span> | <span data-ttu-id="6bd81-232">Tamanho da mensagem</span><span class="sxs-lookup"><span data-stu-id="6bd81-232">Message Size</span></span> |
| <span data-ttu-id="6bd81-233">Semáforo</span><span class="sxs-lookup"><span data-stu-id="6bd81-233">Semaphore</span></span>              | <span data-ttu-id="6bd81-234">Instâncias Iniciais</span><span class="sxs-lookup"><span data-stu-id="6bd81-234">Initial Instances</span></span> | - |
| <span data-ttu-id="6bd81-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="6bd81-235">Mutex</span></span>                  | <span data-ttu-id="6bd81-236">Bandeira da herança</span><span class="sxs-lookup"><span data-stu-id="6bd81-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="6bd81-237">Grupo de Bandeiras de Eventos</span><span class="sxs-lookup"><span data-stu-id="6bd81-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="6bd81-238">Piscina de Blocos</span><span class="sxs-lookup"><span data-stu-id="6bd81-238">Block Pool</span></span>             | <span data-ttu-id="6bd81-239">Total de Blocos</span><span class="sxs-lookup"><span data-stu-id="6bd81-239">Total Blocks</span></span> | <span data-ttu-id="6bd81-240">Tamanho do Bloco</span><span class="sxs-lookup"><span data-stu-id="6bd81-240">Block Size</span></span> |
| <span data-ttu-id="6bd81-241">Piscina Byte</span><span class="sxs-lookup"><span data-stu-id="6bd81-241">Byte Pool</span></span>              | <span data-ttu-id="6bd81-242">Total Bytes</span><span class="sxs-lookup"><span data-stu-id="6bd81-242">Total Bytes</span></span> | - |
| <span data-ttu-id="6bd81-243">.. /media</span><span class="sxs-lookup"><span data-stu-id="6bd81-243">../media</span></span>                  | <span data-ttu-id="6bd81-244">Tamanho da cache de gordura</span><span class="sxs-lookup"><span data-stu-id="6bd81-244">Fat Cache Size</span></span> | <span data-ttu-id="6bd81-245">Tamanho da cache do setor</span><span class="sxs-lookup"><span data-stu-id="6bd81-245">Sector Cache Size</span></span> |
| <span data-ttu-id="6bd81-246">Ficheiro</span><span class="sxs-lookup"><span data-stu-id="6bd81-246">File</span></span>                   | - | - |
| <span data-ttu-id="6bd81-247">IP</span><span class="sxs-lookup"><span data-stu-id="6bd81-247">IP</span></span>                     | <span data-ttu-id="6bd81-248">Início da Pilha</span><span class="sxs-lookup"><span data-stu-id="6bd81-248">Stack Start</span></span> | <span data-ttu-id="6bd81-249">Tamanho da pilha</span><span class="sxs-lookup"><span data-stu-id="6bd81-249">Stack Size</span></span> |
| <span data-ttu-id="6bd81-250">Piscina de Pacotes</span><span class="sxs-lookup"><span data-stu-id="6bd81-250">Packet Pool</span></span>            | <span data-ttu-id="6bd81-251">Tamanho do pacote</span><span class="sxs-lookup"><span data-stu-id="6bd81-251">Packet Size</span></span> | <span data-ttu-id="6bd81-252">Número de Pacotes</span><span class="sxs-lookup"><span data-stu-id="6bd81-252">Number of Packets</span></span> |
| <span data-ttu-id="6bd81-253">Tomada TCP</span><span class="sxs-lookup"><span data-stu-id="6bd81-253">TCP Socket</span></span>             | <span data-ttu-id="6bd81-254">Endereço IP</span><span class="sxs-lookup"><span data-stu-id="6bd81-254">IP address</span></span> | <span data-ttu-id="6bd81-255">Tamanho da janela</span><span class="sxs-lookup"><span data-stu-id="6bd81-255">Window Size</span></span> |
| <span data-ttu-id="6bd81-256">Tomada UDP</span><span class="sxs-lookup"><span data-stu-id="6bd81-256">UDP Socket</span></span>             | <span data-ttu-id="6bd81-257">Endereço IP</span><span class="sxs-lookup"><span data-stu-id="6bd81-257">IP address</span></span> | <span data-ttu-id="6bd81-258">RX Queue Max</span><span class="sxs-lookup"><span data-stu-id="6bd81-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="6bd81-259">Nome do objeto</span><span class="sxs-lookup"><span data-stu-id="6bd81-259">Object Name</span></span>

<span data-ttu-id="6bd81-260">O nome do objeto contém o nome do objeto ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6bd81-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="6bd81-261">O nome é o nome fornecido à ThreadX no momento em que o objeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="6bd81-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="6bd81-262">Por predefinição, o nome do objeto tem um máximo de 32 caracteres.</span><span class="sxs-lookup"><span data-stu-id="6bd81-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="6bd81-263">Nomes reais superiores a 32 caracteres são truncados.</span><span class="sxs-lookup"><span data-stu-id="6bd81-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="6bd81-264">Entradas de rastreio de eventos</span><span class="sxs-lookup"><span data-stu-id="6bd81-264">Event Trace Entries</span></span>

<span data-ttu-id="6bd81-265">As entradas de vestígios do evento são encontradas na parte inferior do tampão de vestígios do evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="6bd81-266">As entradas são mantidas numa lista circular, com o ponteiro de entrada atual a apontar para a entrada mais antiga.</span><span class="sxs-lookup"><span data-stu-id="6bd81-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="6bd81-267">O número de entradas na lista é calculado pela ***chamada tx_trace_enable.***</span><span class="sxs-lookup"><span data-stu-id="6bd81-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="6bd81-268">Cada entrada de registo de objetos contém informações sobre um evento específico de traços ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6bd81-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="6bd81-269">A seguinte estrutura de dados define cada entrada de evento de vestígios:</span><span class="sxs-lookup"><span data-stu-id="6bd81-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="6bd81-270">Ponteiro de fio</span><span class="sxs-lookup"><span data-stu-id="6bd81-270">Thread Pointer</span></span>

<span data-ttu-id="6bd81-271">O ponteiro de linha contém o endereço do fio em execução no momento deste evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="6bd81-272">Se o evento ocorreu durante a inicialização (sem linha em execução), o valor deste ponteiro é 0xF0F0F0F0.</span><span class="sxs-lookup"><span data-stu-id="6bd81-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="6bd81-273">Se o evento ocorreu durante uma Rotina de Serviço de Interrupção (ISR), o valor deste ponteiro é 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="6bd81-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="6bd81-274">Se a entrada ainda não tiver sido utilizada, o valor deste ponteiro é 0.</span><span class="sxs-lookup"><span data-stu-id="6bd81-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="6bd81-275">Prioridade do fio</span><span class="sxs-lookup"><span data-stu-id="6bd81-275">Thread Priority</span></span>

<span data-ttu-id="6bd81-276">O campo prioritário da linha contém a prioridade do fio e o limiar de preempção do fio que estava a ser em execução no momento deste evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="6bd81-277">Se estiver presente um contexto de interrupção (o ponteiro de linha é 0xFFFFFFFF), o valor deste campo não é a prioridade, mas sim o valor de ***_tx_thread_current_ptr*** no momento do evento.</span><span class="sxs-lookup"><span data-stu-id="6bd81-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="6bd81-278">Caso contrário, o valor deste campo é 0.</span><span class="sxs-lookup"><span data-stu-id="6bd81-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="6bd81-279">ID do Evento</span><span class="sxs-lookup"><span data-stu-id="6bd81-279">Event ID</span></span>

<span data-ttu-id="6bd81-280">O ID do evento especifica o evento que ocorreu.</span><span class="sxs-lookup"><span data-stu-id="6bd81-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="6bd81-281">Os IDs válidos do evento ThreadX variam de 1 a 1024.</span><span class="sxs-lookup"><span data-stu-id="6bd81-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="6bd81-282">Os valores a partir de 1025 e acima são reservados para eventos específicos do utilizador.</span><span class="sxs-lookup"><span data-stu-id="6bd81-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="6bd81-283">Consulte o ficheiro ***tx_trace.h*** para a definição completa de IDs de eventos ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6bd81-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="6bd81-284">Campos de Informação (1-4)</span><span class="sxs-lookup"><span data-stu-id="6bd81-284">Information Fields (1-4)</span></span>

<span data-ttu-id="6bd81-285">Os campos de informação contêm informações adicionais sobre o evento específico.</span><span class="sxs-lookup"><span data-stu-id="6bd81-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="6bd81-286">Consulte o ficheiro ***tx_trace.h*** para obter a descrição completa dos campos de informação de cada um dos IDs de eventos definidos da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="6bd81-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>