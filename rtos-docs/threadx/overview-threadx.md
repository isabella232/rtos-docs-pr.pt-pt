---
title: Compreenda Azure RTOS ThreadX
description: Azure ThreadX é um sistema operativo avançado em tempo real (RTOS) projetado especificamente para aplicações profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 938619170ef51d354fa970134328c17407ae846a
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754867"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="47d04-103">Visão geral do Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="47d04-104">Azure RTOS ThreadX é o avançado sistema operativo Real-Time de qualidade industrial da Microsoft (RTOS) projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="47d04-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="47d04-105">A Azure RTOS ThreadX fornece horários avançados, comunicação, sincronização, temporizador, gestão de memória e instalações de gestão de interrupção.</span><span class="sxs-lookup"><span data-stu-id="47d04-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="47d04-106">Além disso, o Azure RTOS ThreadX tem muitas funcionalidades avançadas, incluindo a sua arquitetura picokernel™, limiar de preemção™ agendamento, acorrentação de eventos™ perfis de execução, métricas de desempenho e rastreio de eventos do sistema.</span><span class="sxs-lookup"><span data-stu-id="47d04-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="47d04-107">Combinado com a sua facilidade de utilização superior, o Azure RTOS ThreadX é a escolha ideal para as aplicações mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="47d04-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="47d04-108">A partir de 2017, a Azure RTOS ThreadX conta com mais de 6,2 mil milhões de implantações, numa grande variedade de produtos, incluindo dispositivos de consumo, eletrónica médica e equipamentos de controlo industrial.</span><span class="sxs-lookup"><span data-stu-id="47d04-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="47d04-109">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="47d04-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="47d04-110">Serviços Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="47d04-111">Criação dinâmica de fios</span><span class="sxs-lookup"><span data-stu-id="47d04-111">Dynamic thread creation</span></span>
* <span data-ttu-id="47d04-112">Sem limites no número de fios</span><span class="sxs-lookup"><span data-stu-id="47d04-112">No limits on the number of threads</span></span>
* <span data-ttu-id="47d04-113">As APIs do fio principal incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="47d04-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="47d04-114">tx_thread_create</span></span>
  * <span data-ttu-id="47d04-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-115">tx_thread_delete</span></span>
  * <span data-ttu-id="47d04-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="47d04-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="47d04-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="47d04-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="47d04-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="47d04-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="47d04-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="47d04-119">tx_thread_reset</span></span>
  * <span data-ttu-id="47d04-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="47d04-120">tx_thread_resume</span></span>
  * <span data-ttu-id="47d04-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="47d04-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="47d04-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="47d04-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="47d04-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="47d04-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="47d04-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="47d04-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="47d04-125">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="47d04-126">Filas de mensagens</span><span class="sxs-lookup"><span data-stu-id="47d04-126">Message Queues</span></span>

* <span data-ttu-id="47d04-127">Criação dinâmica de filas</span><span class="sxs-lookup"><span data-stu-id="47d04-127">Dynamic queue creation</span></span>
* <span data-ttu-id="47d04-128">Sem limites no número de filas</span><span class="sxs-lookup"><span data-stu-id="47d04-128">No limits on the number of queues</span></span>
* <span data-ttu-id="47d04-129">Mensagens copiadas por valor (ou por referência via ponteiro)</span><span class="sxs-lookup"><span data-stu-id="47d04-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="47d04-130">Tamanhos de mensagem de 1 a 16 palavras de 32 bits</span><span class="sxs-lookup"><span data-stu-id="47d04-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="47d04-131">Suspensão de fio opcional em vazio e cheio</span><span class="sxs-lookup"><span data-stu-id="47d04-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="47d04-132">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-133">As APIs principais da fila de mensagens incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="47d04-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="47d04-134">tx_queue_create</span></span>
  * <span data-ttu-id="47d04-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-135">tx_queue_delete</span></span>
  * <span data-ttu-id="47d04-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="47d04-136">tx_queue_flush</span></span>
  * <span data-ttu-id="47d04-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="47d04-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="47d04-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="47d04-138">tx_queue_receive</span></span>
  * <span data-ttu-id="47d04-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="47d04-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="47d04-140">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="47d04-141">Contagem de Semáforos</span><span class="sxs-lookup"><span data-stu-id="47d04-141">Counting Semaphores</span></span>

* <span data-ttu-id="47d04-142">Criação de semáforos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="47d04-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="47d04-143">Não há limites para o número de semáforos</span><span class="sxs-lookup"><span data-stu-id="47d04-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="47d04-144">Semáforos de contagem de 32 bits (0 a 4.294.967.295)</span><span class="sxs-lookup"><span data-stu-id="47d04-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="47d04-145">Apoia o produtor-consumidor ou a proteção de recursos</span><span class="sxs-lookup"><span data-stu-id="47d04-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="47d04-146">Suspensão de fio opcional quando semáforo indisponível</span><span class="sxs-lookup"><span data-stu-id="47d04-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="47d04-147">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-148">As PRINCIPAis APIs de semáforo incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="47d04-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="47d04-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="47d04-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="47d04-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="47d04-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="47d04-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="47d04-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="47d04-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="47d04-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="47d04-154">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="47d04-155">Mutaxos</span><span class="sxs-lookup"><span data-stu-id="47d04-155">Mutexes</span></span>

* <span data-ttu-id="47d04-156">Criação de mutex dinâmico</span><span class="sxs-lookup"><span data-stu-id="47d04-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="47d04-157">Sem limites no número de mutantes</span><span class="sxs-lookup"><span data-stu-id="47d04-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="47d04-158">Proteção de recursos aninhada suportada</span><span class="sxs-lookup"><span data-stu-id="47d04-158">Nested resource protection supported</span></span>
* <span data-ttu-id="47d04-159">Herança prioritária opcional apoiada</span><span class="sxs-lookup"><span data-stu-id="47d04-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="47d04-160">Suspensão de fio opcional quando mutex indisponível</span><span class="sxs-lookup"><span data-stu-id="47d04-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="47d04-161">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-162">As principais APIs mutex incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="47d04-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="47d04-163">tx_mutex_create</span></span>
  * <span data-ttu-id="47d04-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="47d04-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="47d04-165">tx_mutex_get</span></span>
  * <span data-ttu-id="47d04-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="47d04-166">tx_mutex_put</span></span>
* <span data-ttu-id="47d04-167">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="47d04-168">Bandeiras do evento</span><span class="sxs-lookup"><span data-stu-id="47d04-168">Event Flags</span></span>

* <span data-ttu-id="47d04-169">Criação dinâmica do grupo de bandeira de evento</span><span class="sxs-lookup"><span data-stu-id="47d04-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="47d04-170">Não há limites para o número de grupos de bandeira de eventos</span><span class="sxs-lookup"><span data-stu-id="47d04-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="47d04-171">Sincronização de um fio ou fios múltiplos</span><span class="sxs-lookup"><span data-stu-id="47d04-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="47d04-172">Atómico obter e claro suporte</span><span class="sxs-lookup"><span data-stu-id="47d04-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="47d04-173">Suspensão multilêssida opcional em conjunto de eventos E/OR</span><span class="sxs-lookup"><span data-stu-id="47d04-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="47d04-174">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-175">As APIs da bandeira do evento principal incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="47d04-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="47d04-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="47d04-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="47d04-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="47d04-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="47d04-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="47d04-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="47d04-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="47d04-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="47d04-181">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="47d04-182">Bloquear piscinas de memória</span><span class="sxs-lookup"><span data-stu-id="47d04-182">Block Memory Pools</span></span>

* <span data-ttu-id="47d04-183">Criação dinâmica de piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="47d04-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="47d04-184">Não há limites para o número de piscinas de blocos</span><span class="sxs-lookup"><span data-stu-id="47d04-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="47d04-185">Sem limites de tamanho de blocos de tamanho fixo ou tamanho de piscina</span><span class="sxs-lookup"><span data-stu-id="47d04-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="47d04-186">Alocação de memória/localização de negócio o mais rápido possível</span><span class="sxs-lookup"><span data-stu-id="47d04-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="47d04-187">Suspensão de fio opcional na piscina vazia</span><span class="sxs-lookup"><span data-stu-id="47d04-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="47d04-188">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-189">As APIs da piscina principal incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="47d04-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="47d04-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="47d04-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="47d04-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="47d04-192">tx_block_allocate</span></span>
  * <span data-ttu-id="47d04-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="47d04-193">tx_block_release</span></span>
* <span data-ttu-id="47d04-194">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="47d04-195">Piscinas de memória Byte</span><span class="sxs-lookup"><span data-stu-id="47d04-195">Byte Memory Pools</span></span>

* <span data-ttu-id="47d04-196">Criação dinâmica da piscina byte</span><span class="sxs-lookup"><span data-stu-id="47d04-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="47d04-197">Não há limites para o número de piscinas byte</span><span class="sxs-lookup"><span data-stu-id="47d04-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="47d04-198">Sem limites no tamanho da piscina byte</span><span class="sxs-lookup"><span data-stu-id="47d04-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="47d04-199">A atribuição/locação de memória de comprimento variável mais flexível</span><span class="sxs-lookup"><span data-stu-id="47d04-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="47d04-200">Localidade de tamanho de alocação suportada</span><span class="sxs-lookup"><span data-stu-id="47d04-200">Allocation size locality supported</span></span>
* <span data-ttu-id="47d04-201">Suspensão de fio opcional na piscina vazia</span><span class="sxs-lookup"><span data-stu-id="47d04-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="47d04-202">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="47d04-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="47d04-203">As APIs da piscina principal incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="47d04-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="47d04-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="47d04-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="47d04-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="47d04-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="47d04-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="47d04-207">tx_byte_release</span></span>
* <span data-ttu-id="47d04-208">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="47d04-209">Temporizadores de aplicação</span><span class="sxs-lookup"><span data-stu-id="47d04-209">Application Timers</span></span>

* <span data-ttu-id="47d04-210">Criação de temporizador dinâmico</span><span class="sxs-lookup"><span data-stu-id="47d04-210">Dynamic timer creation</span></span>
* <span data-ttu-id="47d04-211">Não há limites no número de temporizadores</span><span class="sxs-lookup"><span data-stu-id="47d04-211">No limits on the number of timers</span></span>
* <span data-ttu-id="47d04-212">Temporizadores periódicos ou de um tiro suportados</span><span class="sxs-lookup"><span data-stu-id="47d04-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="47d04-213">Temporizadores periódicos podem ter diferente valor inicial de expiração</span><span class="sxs-lookup"><span data-stu-id="47d04-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="47d04-214">Sem pesquisa sobre ativação ou desativação do temporizador</span><span class="sxs-lookup"><span data-stu-id="47d04-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="47d04-215">Todos os temporizadores conduzidos de um temporizador de hardware interrompem</span><span class="sxs-lookup"><span data-stu-id="47d04-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="47d04-216">As APIs do temporizador principal incluem:</span><span class="sxs-lookup"><span data-stu-id="47d04-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="47d04-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="47d04-217">tx_timer_create</span></span>
  * <span data-ttu-id="47d04-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="47d04-218">tx_timer_delete</span></span>
  * <span data-ttu-id="47d04-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="47d04-219">tx_timer_activate</span></span>
  * <span data-ttu-id="47d04-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="47d04-220">tx_timer_change</span></span>
  * <span data-ttu-id="47d04-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="47d04-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="47d04-222">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="47d04-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="47d04-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="47d04-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="47d04-224">Pegada mínima de 2KB FLASH,1KB RAM</span><span class="sxs-lookup"><span data-stu-id="47d04-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="47d04-225">Interruptor de contexto rápido e sub-microsegundo</span><span class="sxs-lookup"><span data-stu-id="47d04-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="47d04-226">Totalmente determinístico independentemente do número de fios</span><span class="sxs-lookup"><span data-stu-id="47d04-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="47d04-227">Agendamento prioritário e totalmente preventivo</span><span class="sxs-lookup"><span data-stu-id="47d04-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="47d04-228">32 níveis de prioridade padrão, opcionalmente até níveis de 1024</span><span class="sxs-lookup"><span data-stu-id="47d04-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="47d04-229">Agendamento cooperativo dentro do nível prioritário (FIFO)</span><span class="sxs-lookup"><span data-stu-id="47d04-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="47d04-230">Tecnologia limiar de pré-edição</span><span class="sxs-lookup"><span data-stu-id="47d04-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="47d04-231">Serviços de temporizador opcional, incluindo:</span><span class="sxs-lookup"><span data-stu-id="47d04-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="47d04-232">Fatia de tempo opcional por thread</span><span class="sxs-lookup"><span data-stu-id="47d04-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="47d04-233">Tempo limite opcional em todos os bloqueios</span><span class="sxs-lookup"><span data-stu-id="47d04-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="47d04-234">APIs requer interrupção do temporizador de hardware</span><span class="sxs-lookup"><span data-stu-id="47d04-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="47d04-235">Perfis de execução</span><span class="sxs-lookup"><span data-stu-id="47d04-235">Execution profiling</span></span>
* <span data-ttu-id="47d04-236">Vestígios de nível de sistema</span><span class="sxs-lookup"><span data-stu-id="47d04-236">System-level Trace</span></span>
* <span data-ttu-id="47d04-237">Segurança certificada para muitas normas</span><span class="sxs-lookup"><span data-stu-id="47d04-237">Safety certified to many standards</span></span>

## <a name="threadx-footprint"></a><span data-ttu-id="47d04-238">Pegada ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-238">ThreadX footprint</span></span>

<span data-ttu-id="47d04-239">A Azure RTOS ThreadX requer uma área de instrução 2KB notavelmente pequena e 1KB de RAM para a sua pegada mínima.</span><span class="sxs-lookup"><span data-stu-id="47d04-239">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="47d04-240">Isto deve-se, em grande parte, à sua arquitetura picokernel™ não em camadas e à escala automática.</span><span class="sxs-lookup"><span data-stu-id="47d04-240">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="47d04-241">O dimensionamento automático significa que apenas os serviços (e infraestruturas de apoio) utilizados pela aplicação estão incluídos na imagem final no momento do link.</span><span class="sxs-lookup"><span data-stu-id="47d04-241">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="47d04-242">Aqui estão algumas características típicas do tamanho Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="47d04-242">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="47d04-243">Serviço Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-243">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="47d04-244">Tamanho típico em bytes</span><span class="sxs-lookup"><span data-stu-id="47d04-244">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="47d04-245">Serviços centrais (Exigir)</span><span class="sxs-lookup"><span data-stu-id="47d04-245">Core Services (Require)</span></span> |<span data-ttu-id="47d04-246">2.000</span><span class="sxs-lookup"><span data-stu-id="47d04-246">2,000</span></span>  |
|<span data-ttu-id="47d04-247">Serviços de fila</span><span class="sxs-lookup"><span data-stu-id="47d04-247">Queue Services</span></span>  |<span data-ttu-id="47d04-248">900</span><span class="sxs-lookup"><span data-stu-id="47d04-248">900</span></span>  |
|<span data-ttu-id="47d04-249">Serviços de Bandeira de Eventos</span><span class="sxs-lookup"><span data-stu-id="47d04-249">Event Flag Services</span></span>  |<span data-ttu-id="47d04-250">900</span><span class="sxs-lookup"><span data-stu-id="47d04-250">900</span></span>  |
|<span data-ttu-id="47d04-251">Serviços Semáforos</span><span class="sxs-lookup"><span data-stu-id="47d04-251">Semaphore Services</span></span>  |<span data-ttu-id="47d04-252">450</span><span class="sxs-lookup"><span data-stu-id="47d04-252">450</span></span>  |
|<span data-ttu-id="47d04-253">Serviços Mutex</span><span class="sxs-lookup"><span data-stu-id="47d04-253">Mutex Services</span></span>  |<span data-ttu-id="47d04-254">1200</span><span class="sxs-lookup"><span data-stu-id="47d04-254">1,200</span></span>  |
|<span data-ttu-id="47d04-255">Bloquear serviços de memória</span><span class="sxs-lookup"><span data-stu-id="47d04-255">Block Memory Services</span></span>  |<span data-ttu-id="47d04-256">550</span><span class="sxs-lookup"><span data-stu-id="47d04-256">550</span></span>  |
|<span data-ttu-id="47d04-257">Serviços de Memória Byte</span><span class="sxs-lookup"><span data-stu-id="47d04-257">Byte Memory Services</span></span>  |<span data-ttu-id="47d04-258">900</span><span class="sxs-lookup"><span data-stu-id="47d04-258">900</span></span>  |

## <a name="threadx-execution-speed"></a><span data-ttu-id="47d04-259">Velocidade de execução ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-259">ThreadX execution speed</span></span>

<span data-ttu-id="47d04-260">O Azure RTOS ThreadX consegue um interruptor de contexto sub-microsegundo nos processadores mais populares e é significativamente mais rápido em termos globais do que outros RTOSes comerciais.</span><span class="sxs-lookup"><span data-stu-id="47d04-260">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="47d04-261">Além de ser rápido, o Azure RTOS ThreadX também é altamente determinístico.</span><span class="sxs-lookup"><span data-stu-id="47d04-261">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="47d04-262">Consegue o mesmo desempenho rápido, quer existam 200 fios prontos, ou apenas um.</span><span class="sxs-lookup"><span data-stu-id="47d04-262">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="47d04-263">Aqui estão algumas características típicas de desempenho da Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="47d04-263">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="47d04-264">Arranque Rápido: Botas Azure RTOS ThreadX em menos de 120 ciclos.</span><span class="sxs-lookup"><span data-stu-id="47d04-264">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="47d04-265">Remoção opcional da verificação de erros básicos: A verificação de erros básicos de Azure RTOS ThreadX pode ser ignorada na hora da compilação.</span><span class="sxs-lookup"><span data-stu-id="47d04-265">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="47d04-266">Isto pode ser útil quando o código de aplicação é verificado e já não requer verificação de erros em cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="47d04-266">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="47d04-267">Note que isto pode ser feito numa unidade de compilação, em vez de em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="47d04-267">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="47d04-268">Picokernel™ Design: Os serviços não estão em camadas uns sobre os outros, eliminando assim a sobrecarga de chamada de função desnecessária.</span><span class="sxs-lookup"><span data-stu-id="47d04-268">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="47d04-269">\*Processamento de interrupção otimizado: Apenas registos de risco são guardados/restaurados após a entrada/saída do ISR, a menos que seja necessário uma pré-colocação.</span><span class="sxs-lookup"><span data-stu-id="47d04-269">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="47d04-270">Processamento otimizado da API:</span><span class="sxs-lookup"><span data-stu-id="47d04-270">Optimized API Processing:</span></span>

    |<span data-ttu-id="47d04-271">Serviço Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-271">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="47d04-272">Tempo de serviço em Microsegundos\*</span><span class="sxs-lookup"><span data-stu-id="47d04-272">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="47d04-273">Suspensão do fio</span><span class="sxs-lookup"><span data-stu-id="47d04-273">Thread Suspend</span></span>  |<span data-ttu-id="47d04-274">0.6</span><span class="sxs-lookup"><span data-stu-id="47d04-274">0.6</span></span>  |
    |<span data-ttu-id="47d04-275">Resumo da linha</span><span class="sxs-lookup"><span data-stu-id="47d04-275">Thread Resume</span></span>  |<span data-ttu-id="47d04-276">0.6</span><span class="sxs-lookup"><span data-stu-id="47d04-276">0.6</span></span>  |
    |<span data-ttu-id="47d04-277">Enviar fila</span><span class="sxs-lookup"><span data-stu-id="47d04-277">Queue Send</span></span>  |<span data-ttu-id="47d04-278">0.3</span><span class="sxs-lookup"><span data-stu-id="47d04-278">0.3</span></span>  |
    |<span data-ttu-id="47d04-279">Receber fila</span><span class="sxs-lookup"><span data-stu-id="47d04-279">Queue Receive</span></span>  |<span data-ttu-id="47d04-280">0.3</span><span class="sxs-lookup"><span data-stu-id="47d04-280">0.3</span></span>  |
    |<span data-ttu-id="47d04-281">Obter Semáforo</span><span class="sxs-lookup"><span data-stu-id="47d04-281">Get Semaphore</span></span>  |<span data-ttu-id="47d04-282">0,2</span><span class="sxs-lookup"><span data-stu-id="47d04-282">0.2</span></span>  |
    |<span data-ttu-id="47d04-283">Coloque o Semáforo</span><span class="sxs-lookup"><span data-stu-id="47d04-283">Put Semaphore</span></span>  |<span data-ttu-id="47d04-284">0,2</span><span class="sxs-lookup"><span data-stu-id="47d04-284">0.2</span></span>  |
    |<span data-ttu-id="47d04-285">Interruptor de contexto</span><span class="sxs-lookup"><span data-stu-id="47d04-285">Context Switch</span></span>  |<span data-ttu-id="47d04-286">0,4</span><span class="sxs-lookup"><span data-stu-id="47d04-286">0.4</span></span>  |
    |<span data-ttu-id="47d04-287">Interrupção da resposta</span><span class="sxs-lookup"><span data-stu-id="47d04-287">Interrupt Response</span></span>  |<span data-ttu-id="47d04-288">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="47d04-288">0.0 – 0.6</span></span>  |

    <span data-ttu-id="47d04-289">\**Números de desempenho baseados no processador típico a funcionar a 200MHz*.</span><span class="sxs-lookup"><span data-stu-id="47d04-289">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="47d04-290">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="47d04-290">Advanced technology</span></span>

<span data-ttu-id="47d04-291">Azure RTOS ThreadX é uma tecnologia avançada cuja característica mais notável é o agendamento do limiar de pré-edição.</span><span class="sxs-lookup"><span data-stu-id="47d04-291">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="47d04-292">Esta funcionalidade é exclusiva da Azure RTOS ThreadX e tem sido alvo de uma extensa investigação académica.</span><span class="sxs-lookup"><span data-stu-id="47d04-292">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="47d04-293">Por exemplo, ver [Agendar Fixed-Priority Tarefas com Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), por Yun Wang, Universidade de Concordia, e Manas Saksena, Universidade de Pittsburgh.</span><span class="sxs-lookup"><span data-stu-id="47d04-293">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="47d04-294">Considere as capacidades da Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="47d04-294">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="47d04-295">Instalações multitarefas completas e abrangentes</span><span class="sxs-lookup"><span data-stu-id="47d04-295">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="47d04-296">Threads, temporizadores de aplicação, filas de mensagens, semafores contando, mutantes, bandeiras de eventos, bloco e piscinas de memória byte</span><span class="sxs-lookup"><span data-stu-id="47d04-296">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="47d04-297">Agendamento Preventivo Priority-Based</span><span class="sxs-lookup"><span data-stu-id="47d04-297">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="47d04-298">Flexibilidade Prioritária - Até 1024 Níveis Prioritários</span><span class="sxs-lookup"><span data-stu-id="47d04-298">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="47d04-299">Agendamento Cooperativo</span><span class="sxs-lookup"><span data-stu-id="47d04-299">Cooperative Scheduling</span></span>
* <span data-ttu-id="47d04-300">Preemption-Threshold™ – Exclusivo para Azure RTOS ThreadX, ajuda a reduzir os interruptores de contexto e ajuda a garantir agendabilidade (por investigação académica)</span><span class="sxs-lookup"><span data-stu-id="47d04-300">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="47d04-301">Proteção da memória através de módulos Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-301">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="47d04-302">Totalmente determinístico</span><span class="sxs-lookup"><span data-stu-id="47d04-302">Fully Deterministic</span></span>
* <span data-ttu-id="47d04-303">Trace de eventos – Capture os últimos eventos *do* sistema/aplicação n</span><span class="sxs-lookup"><span data-stu-id="47d04-303">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="47d04-304">Chaining de Eventos™ – Registe uma função de chamada "notificação" específica para cada objeto de comunicação ou sincronização Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-304">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="47d04-305">Módulos Azure RTOS ThreadX com Proteção Opcional de Memória</span><span class="sxs-lookup"><span data-stu-id="47d04-305">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="47d04-306">Métricas de Desempenho Run-Time</span><span class="sxs-lookup"><span data-stu-id="47d04-306">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="47d04-307">Número de resuflações de fios</span><span class="sxs-lookup"><span data-stu-id="47d04-307">Number of thread resumptions</span></span>
  * <span data-ttu-id="47d04-308">Número de suspensões por fios</span><span class="sxs-lookup"><span data-stu-id="47d04-308">Number of thread suspensions</span></span>
  * <span data-ttu-id="47d04-309">Número de preemposições de fio solicitadas</span><span class="sxs-lookup"><span data-stu-id="47d04-309">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="47d04-310">Número de preemposições de interrupção de linha assíncrona</span><span class="sxs-lookup"><span data-stu-id="47d04-310">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="47d04-311">Número de inversões prioritárias de linha</span><span class="sxs-lookup"><span data-stu-id="47d04-311">Number of thread priority inversions</span></span>
  * <span data-ttu-id="47d04-312">Número de renúncias de fio</span><span class="sxs-lookup"><span data-stu-id="47d04-312">Number of thread relinquishes</span></span>
* <span data-ttu-id="47d04-313">Kit de perfil de execução (EPK)</span><span class="sxs-lookup"><span data-stu-id="47d04-313">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="47d04-314">Pilha de interrupção separada</span><span class="sxs-lookup"><span data-stu-id="47d04-314">Separate Interrupt Stack</span></span>
* <span data-ttu-id="47d04-315">Análise da pilha de Run-Time</span><span class="sxs-lookup"><span data-stu-id="47d04-315">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="47d04-316">Processamento de interrupção de temporizador otimizado</span><span class="sxs-lookup"><span data-stu-id="47d04-316">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="47d04-317">Suporte multicore (AMP & SMP)</span><span class="sxs-lookup"><span data-stu-id="47d04-317">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="47d04-318">O Standard Azure RTOS ThreadX é frequentemente utilizado numa moda multiprocessa assimétrica (AMP), onde uma cópia separada do Azure RTOS ThreadX e a aplicação (ou Linux) executam em cada núcleo e comunicam entre si através de memória partilhada ou de um mecanismo de comunicação interprocessador, como o OpenAMP (Azure RTOS ThreadX suporta o OpenAMP).</span><span class="sxs-lookup"><span data-stu-id="47d04-318">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="47d04-319">Esta é a configuração multicore mais típica usando o Azure RTOS ThreadX e pode ser a mais eficiente se a aplicação for capaz de carregar eficazmente os processadores.</span><span class="sxs-lookup"><span data-stu-id="47d04-319">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="47d04-320">Para ambientes onde o carregamento dos processadores é altamente dinâmico, o Azure RTOS ThreadX Symetric Multiprocessing (SMP) está disponível para as seguintes famílias de processadores:</span><span class="sxs-lookup"><span data-stu-id="47d04-320">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="47d04-321">Cortex-Ax ARM</span><span class="sxs-lookup"><span data-stu-id="47d04-321">ARM Cortex-Ax</span></span>
* <span data-ttu-id="47d04-322">Cortex-Rx ARM</span><span class="sxs-lookup"><span data-stu-id="47d04-322">ARM Cortex-Rx</span></span>
* <span data-ttu-id="47d04-323">ARM Cortex-A5x 64-bit</span><span class="sxs-lookup"><span data-stu-id="47d04-323">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="47d04-324">MIPS 34K, 1004K e interAptiv</span><span class="sxs-lookup"><span data-stu-id="47d04-324">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="47d04-325">PowerPC</span><span class="sxs-lookup"><span data-stu-id="47d04-325">PowerPC</span></span>
* <span data-ttu-id="47d04-326">Sinopsias ARC HS</span><span class="sxs-lookup"><span data-stu-id="47d04-326">Synopsys ARC HS</span></span>
* <span data-ttu-id="47d04-327">x86</span><span class="sxs-lookup"><span data-stu-id="47d04-327">x86</span></span>

<span data-ttu-id="47d04-328">A Azure RTOS ThreadX SMP executa o equilíbrio dinâmico da carga entre processadores *n* e permite que todos os recursos Azure RTOS ThreadX (filas, semáforos, bandeiras de eventos, piscinas de memória, etc.) sejam acedidos por qualquer fio em qualquer núcleo.</span><span class="sxs-lookup"><span data-stu-id="47d04-328">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="47d04-329">A Azure RTOS ThreadX SMP permite a API API completa Azure RTOS ThreadX em todos os núcleos e introduz os seguintes novos API aplicáveis à operação SMP:</span><span class="sxs-lookup"><span data-stu-id="47d04-329">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="47d04-330">Proteção da memória através de módulos Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-330">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="47d04-331">Um produto adicional chamado Azure RTOS ThreadX MODULES permite que um ou mais fios de aplicação sejam agregados num "Módulo" que pode ser carregado e executado dinamicamente (ou executado no lugar) no alvo.</span><span class="sxs-lookup"><span data-stu-id="47d04-331">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="47d04-332">Os módulos permitem a atualização de campo, a fixação de erros e a partição do programa para permitir que as grandes aplicações ocupem apenas a memória necessária através de fios ativos.</span><span class="sxs-lookup"><span data-stu-id="47d04-332">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="47d04-333">Os módulos também têm um espaço de endereço completamente separado do próprio Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="47d04-333">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="47d04-334">Isto permite que o Azure RTOS ThreadX coloque a proteção da memória (via MPU ou MMU) em torno do Módulo de modo a que o acesso acidental fora do módulo não seja capaz de corromper qualquer outro componente de software.</span><span class="sxs-lookup"><span data-stu-id="47d04-334">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="47d04-335">Conformidade com o MISRA</span><span class="sxs-lookup"><span data-stu-id="47d04-335">MISRA compliant</span></span>

<span data-ttu-id="47d04-336">O código fonte Azure RTOS ThreadX e Azure RTOS ThreadX SMP é compatível com MISRA-C:2004 e MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="47d04-336">Azure RTOS ThreadX and Azure RTOS ThreadX SMP source code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="47d04-337">MISRA C é um conjunto de diretrizes de programação para sistemas críticos utilizando a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="47d04-337">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="47d04-338">As diretrizes originais do MISRA C destinavam-se principalmente a aplicações para automóveis; no entanto, o MISRA C é hoje amplamente reconhecido como sendo aplicável a qualquer aplicação crítica de segurança.</span><span class="sxs-lookup"><span data-stu-id="47d04-338">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="47d04-339">O Azure RTOS ThreadX está em conformidade com todas as regras necessárias e obrigatórias de MISRA-C:2004 e MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="47d04-339">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificação Misra":::

## <a name="supports-most-popular-tools"></a><span data-ttu-id="47d04-341">Suporta as ferramentas mais populares</span><span class="sxs-lookup"><span data-stu-id="47d04-341">Supports most popular tools</span></span>

<span data-ttu-id="47d04-342">O Azure RTOS ThreadX suporta as ferramentas de desenvolvimento incorporadas mais populares, incluindo a bancada de trabalho incorporada da IAR™, que também tem a mais abrangente consciência de kernel Azure RTOS ThreadX disponível.</span><span class="sxs-lookup"><span data-stu-id="47d04-342">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="47d04-343">A integração adicional de ferramentas inclui GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore e todos os dispositivos analógicos.</span><span class="sxs-lookup"><span data-stu-id="47d04-343">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="47d04-344">Camada de adaptação para ThreadX</span><span class="sxs-lookup"><span data-stu-id="47d04-344">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="47d04-345">O Azure RTOS ThreadX é um sistema operativo em tempo real (RTOS) avançado criado especificamente para aplicações profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="47d04-345">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="47d04-346">Para facilitar a migração de aplicações para Auzre RTOS, a ThreadX fornece [camadas de adaptação](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) para várias APIs RTOS (FreeRTOS, POSIX, OSEK, etc.)</span><span class="sxs-lookup"><span data-stu-id="47d04-346">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
