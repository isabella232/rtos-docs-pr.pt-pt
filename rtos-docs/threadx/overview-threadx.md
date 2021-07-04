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
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="05b68-103">Visão geral do Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="05b68-104">Azure RTOS ThreadX é o avançado sistema operativo Real-Time de qualidade industrial da Microsoft (RTOS) projetado especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="05b68-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="05b68-105">A Azure RTOS ThreadX fornece horários avançados, comunicação, sincronização, temporizador, gestão de memória e instalações de gestão de interrupção.</span><span class="sxs-lookup"><span data-stu-id="05b68-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="05b68-106">Além disso, o Azure RTOS ThreadX tem muitas funcionalidades avançadas, incluindo a sua arquitetura picokernel™, limiar de preemção™ agendamento, acorrentação de eventos™ perfis de execução, métricas de desempenho e rastreio de eventos do sistema.</span><span class="sxs-lookup"><span data-stu-id="05b68-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="05b68-107">Combinado com a sua facilidade de utilização superior, o Azure RTOS ThreadX é a escolha ideal para as aplicações mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="05b68-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="05b68-108">A partir de 2017, a Azure RTOS ThreadX conta com mais de 6,2 mil milhões de implantações, numa grande variedade de produtos, incluindo dispositivos de consumo, eletrónica médica e equipamentos de controlo industrial.</span><span class="sxs-lookup"><span data-stu-id="05b68-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="05b68-109">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="05b68-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="05b68-110">Serviços Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="05b68-111">Criação dinâmica de fios</span><span class="sxs-lookup"><span data-stu-id="05b68-111">Dynamic thread creation</span></span>
* <span data-ttu-id="05b68-112">Sem limites no número de fios</span><span class="sxs-lookup"><span data-stu-id="05b68-112">No limits on the number of threads</span></span>
* <span data-ttu-id="05b68-113">As APIs do fio principal incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="05b68-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="05b68-114">tx_thread_create</span></span>
  * <span data-ttu-id="05b68-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-115">tx_thread_delete</span></span>
  * <span data-ttu-id="05b68-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="05b68-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="05b68-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="05b68-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="05b68-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="05b68-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="05b68-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="05b68-119">tx_thread_reset</span></span>
  * <span data-ttu-id="05b68-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="05b68-120">tx_thread_resume</span></span>
  * <span data-ttu-id="05b68-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="05b68-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="05b68-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="05b68-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="05b68-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="05b68-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="05b68-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="05b68-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="05b68-125">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="05b68-126">Filas de mensagens</span><span class="sxs-lookup"><span data-stu-id="05b68-126">Message Queues</span></span>

* <span data-ttu-id="05b68-127">Criação dinâmica de filas</span><span class="sxs-lookup"><span data-stu-id="05b68-127">Dynamic queue creation</span></span>
* <span data-ttu-id="05b68-128">Sem limites no número de filas</span><span class="sxs-lookup"><span data-stu-id="05b68-128">No limits on the number of queues</span></span>
* <span data-ttu-id="05b68-129">Mensagens copiadas por valor (ou por referência via ponteiro)</span><span class="sxs-lookup"><span data-stu-id="05b68-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="05b68-130">Tamanhos de mensagem de 1 a 16 palavras de 32 bits</span><span class="sxs-lookup"><span data-stu-id="05b68-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="05b68-131">Suspensão de fio opcional em vazio e cheio</span><span class="sxs-lookup"><span data-stu-id="05b68-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="05b68-132">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-133">As APIs principais da fila de mensagens incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="05b68-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="05b68-134">tx_queue_create</span></span>
  * <span data-ttu-id="05b68-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-135">tx_queue_delete</span></span>
  * <span data-ttu-id="05b68-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="05b68-136">tx_queue_flush</span></span>
  * <span data-ttu-id="05b68-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="05b68-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="05b68-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="05b68-138">tx_queue_receive</span></span>
  * <span data-ttu-id="05b68-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="05b68-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="05b68-140">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="05b68-141">Contagem de Semáforos</span><span class="sxs-lookup"><span data-stu-id="05b68-141">Counting Semaphores</span></span>

* <span data-ttu-id="05b68-142">Criação de semáforos dinâmicos</span><span class="sxs-lookup"><span data-stu-id="05b68-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="05b68-143">Não há limites para o número de semáforos</span><span class="sxs-lookup"><span data-stu-id="05b68-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="05b68-144">Semáforos de contagem de 32 bits (0 a 4.294.967.295)</span><span class="sxs-lookup"><span data-stu-id="05b68-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="05b68-145">Apoia o produtor-consumidor ou a proteção de recursos</span><span class="sxs-lookup"><span data-stu-id="05b68-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="05b68-146">Suspensão de fio opcional quando semáforo indisponível</span><span class="sxs-lookup"><span data-stu-id="05b68-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="05b68-147">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-148">As PRINCIPAis APIs de semáforo incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="05b68-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="05b68-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="05b68-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="05b68-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="05b68-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="05b68-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="05b68-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="05b68-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="05b68-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="05b68-154">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="05b68-155">Mutaxos</span><span class="sxs-lookup"><span data-stu-id="05b68-155">Mutexes</span></span>

* <span data-ttu-id="05b68-156">Criação de mutex dinâmico</span><span class="sxs-lookup"><span data-stu-id="05b68-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="05b68-157">Sem limites no número de mutantes</span><span class="sxs-lookup"><span data-stu-id="05b68-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="05b68-158">Proteção de recursos aninhada suportada</span><span class="sxs-lookup"><span data-stu-id="05b68-158">Nested resource protection supported</span></span>
* <span data-ttu-id="05b68-159">Herança prioritária opcional apoiada</span><span class="sxs-lookup"><span data-stu-id="05b68-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="05b68-160">Suspensão de fio opcional quando mutex indisponível</span><span class="sxs-lookup"><span data-stu-id="05b68-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="05b68-161">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-162">As principais APIs mutex incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="05b68-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="05b68-163">tx_mutex_create</span></span>
  * <span data-ttu-id="05b68-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="05b68-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="05b68-165">tx_mutex_get</span></span>
  * <span data-ttu-id="05b68-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="05b68-166">tx_mutex_put</span></span>
* <span data-ttu-id="05b68-167">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="05b68-168">Bandeiras do evento</span><span class="sxs-lookup"><span data-stu-id="05b68-168">Event Flags</span></span>

* <span data-ttu-id="05b68-169">Criação dinâmica do grupo de bandeira de evento</span><span class="sxs-lookup"><span data-stu-id="05b68-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="05b68-170">Não há limites para o número de grupos de bandeira de eventos</span><span class="sxs-lookup"><span data-stu-id="05b68-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="05b68-171">Sincronização de um fio ou fios múltiplos</span><span class="sxs-lookup"><span data-stu-id="05b68-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="05b68-172">Atómico obter e claro suporte</span><span class="sxs-lookup"><span data-stu-id="05b68-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="05b68-173">Suspensão multilêssida opcional em conjunto de eventos E/OR</span><span class="sxs-lookup"><span data-stu-id="05b68-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="05b68-174">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-175">As APIs da bandeira do evento principal incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="05b68-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="05b68-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="05b68-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="05b68-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="05b68-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="05b68-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="05b68-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="05b68-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="05b68-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="05b68-181">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="05b68-182">Bloquear piscinas de memória</span><span class="sxs-lookup"><span data-stu-id="05b68-182">Block Memory Pools</span></span>

* <span data-ttu-id="05b68-183">Criação dinâmica de piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="05b68-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="05b68-184">Não há limites para o número de piscinas de blocos</span><span class="sxs-lookup"><span data-stu-id="05b68-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="05b68-185">Sem limites de tamanho de blocos de tamanho fixo ou tamanho de piscina</span><span class="sxs-lookup"><span data-stu-id="05b68-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="05b68-186">Alocação de memória/localização de negócio o mais rápido possível</span><span class="sxs-lookup"><span data-stu-id="05b68-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="05b68-187">Suspensão de fio opcional na piscina vazia</span><span class="sxs-lookup"><span data-stu-id="05b68-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="05b68-188">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-189">As APIs da piscina principal incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="05b68-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="05b68-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="05b68-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="05b68-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="05b68-192">tx_block_allocate</span></span>
  * <span data-ttu-id="05b68-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="05b68-193">tx_block_release</span></span>
* <span data-ttu-id="05b68-194">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="05b68-195">Piscinas de memória Byte</span><span class="sxs-lookup"><span data-stu-id="05b68-195">Byte Memory Pools</span></span>

* <span data-ttu-id="05b68-196">Criação dinâmica da piscina byte</span><span class="sxs-lookup"><span data-stu-id="05b68-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="05b68-197">Não há limites para o número de piscinas byte</span><span class="sxs-lookup"><span data-stu-id="05b68-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="05b68-198">Sem limites no tamanho da piscina byte</span><span class="sxs-lookup"><span data-stu-id="05b68-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="05b68-199">A atribuição/locação de memória de comprimento variável mais flexível</span><span class="sxs-lookup"><span data-stu-id="05b68-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="05b68-200">Localidade de tamanho de alocação suportada</span><span class="sxs-lookup"><span data-stu-id="05b68-200">Allocation size locality supported</span></span>
* <span data-ttu-id="05b68-201">Suspensão de fio opcional na piscina vazia</span><span class="sxs-lookup"><span data-stu-id="05b68-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="05b68-202">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="05b68-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="05b68-203">As APIs da piscina principal incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="05b68-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="05b68-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="05b68-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="05b68-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="05b68-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="05b68-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="05b68-207">tx_byte_release</span></span>
* <span data-ttu-id="05b68-208">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="05b68-209">Temporizadores de aplicação</span><span class="sxs-lookup"><span data-stu-id="05b68-209">Application Timers</span></span>

* <span data-ttu-id="05b68-210">Criação de temporizador dinâmico</span><span class="sxs-lookup"><span data-stu-id="05b68-210">Dynamic timer creation</span></span>
* <span data-ttu-id="05b68-211">Não há limites no número de temporizadores</span><span class="sxs-lookup"><span data-stu-id="05b68-211">No limits on the number of timers</span></span>
* <span data-ttu-id="05b68-212">Temporizadores periódicos ou de um tiro suportados</span><span class="sxs-lookup"><span data-stu-id="05b68-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="05b68-213">Temporizadores periódicos podem ter diferente valor inicial de expiração</span><span class="sxs-lookup"><span data-stu-id="05b68-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="05b68-214">Sem pesquisa sobre ativação ou desativação do temporizador</span><span class="sxs-lookup"><span data-stu-id="05b68-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="05b68-215">Todos os temporizadores conduzidos de um temporizador de hardware interrompem</span><span class="sxs-lookup"><span data-stu-id="05b68-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="05b68-216">As APIs do temporizador principal incluem:</span><span class="sxs-lookup"><span data-stu-id="05b68-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="05b68-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="05b68-217">tx_timer_create</span></span>
  * <span data-ttu-id="05b68-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="05b68-218">tx_timer_delete</span></span>
  * <span data-ttu-id="05b68-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="05b68-219">tx_timer_activate</span></span>
  * <span data-ttu-id="05b68-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="05b68-220">tx_timer_change</span></span>
  * <span data-ttu-id="05b68-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="05b68-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="05b68-222">APIs de informação adicional e desempenho</span><span class="sxs-lookup"><span data-stu-id="05b68-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="05b68-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="05b68-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="05b68-224">Pegada mínima de 2KB FLASH,1KB RAM</span><span class="sxs-lookup"><span data-stu-id="05b68-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="05b68-225">Interruptor de contexto rápido e sub-microsegundo</span><span class="sxs-lookup"><span data-stu-id="05b68-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="05b68-226">Totalmente determinístico independentemente do número de fios</span><span class="sxs-lookup"><span data-stu-id="05b68-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="05b68-227">Agendamento prioritário e totalmente preventivo</span><span class="sxs-lookup"><span data-stu-id="05b68-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="05b68-228">32 níveis de prioridade padrão, opcionalmente até níveis de 1024</span><span class="sxs-lookup"><span data-stu-id="05b68-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="05b68-229">Agendamento cooperativo dentro do nível prioritário (FIFO)</span><span class="sxs-lookup"><span data-stu-id="05b68-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="05b68-230">Tecnologia limiar de pré-edição</span><span class="sxs-lookup"><span data-stu-id="05b68-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="05b68-231">Serviços de temporizador opcional, incluindo:</span><span class="sxs-lookup"><span data-stu-id="05b68-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="05b68-232">Fatia de tempo opcional por thread</span><span class="sxs-lookup"><span data-stu-id="05b68-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="05b68-233">Tempo limite opcional em todos os bloqueios</span><span class="sxs-lookup"><span data-stu-id="05b68-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="05b68-234">APIs requer interrupção do temporizador de hardware</span><span class="sxs-lookup"><span data-stu-id="05b68-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="05b68-235">Perfis de execução</span><span class="sxs-lookup"><span data-stu-id="05b68-235">Execution profiling</span></span>
* <span data-ttu-id="05b68-236">Vestígios de nível de sistema</span><span class="sxs-lookup"><span data-stu-id="05b68-236">System-level Trace</span></span>
* <span data-ttu-id="05b68-237">Segurança certificada para muitas normas</span><span class="sxs-lookup"><span data-stu-id="05b68-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="05b68-238">RTOS mais implantado</span><span class="sxs-lookup"><span data-stu-id="05b68-238">Most deployed RTOS</span></span>

<span data-ttu-id="05b68-239">A Azure RTOS ThreadX tem mais de 6,2 mil milhões de implantações em todo o mundo, de acordo com a empresa líder de inteligência de mercado M2M, a VDC Research.</span><span class="sxs-lookup"><span data-stu-id="05b68-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="05b68-240">A popularidade da Azure RTOS ThreadX é um testemunho da sua fiabilidade, qualidade, tamanho, desempenho, funcionalidades avançadas, facilidade de utilização e vantagens gerais de tempo para mercado.</span><span class="sxs-lookup"><span data-stu-id="05b68-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="05b68-241">*"Temos acompanhado a trajetória de crescimento da THREADX nos mercados sem fios e IoT desde a fundação da empresa, e estamos cada vez mais impressionados com a adoção generalizada da THREADX pela indústria."*</span><span class="sxs-lookup"><span data-stu-id="05b68-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="05b68-242">– Chris Rommel, Vice-Presidente Executivo, VDC Research</span><span class="sxs-lookup"><span data-stu-id="05b68-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="05b68-243">Pequena pegada</span><span class="sxs-lookup"><span data-stu-id="05b68-243">Small footprint</span></span>

<span data-ttu-id="05b68-244">A Azure RTOS ThreadX requer uma área de instrução 2KB notavelmente pequena e 1KB de RAM para a sua pegada mínima.</span><span class="sxs-lookup"><span data-stu-id="05b68-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="05b68-245">Isto deve-se, em grande parte, à sua arquitetura picokernel™ não em camadas e à escala automática.</span><span class="sxs-lookup"><span data-stu-id="05b68-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="05b68-246">O dimensionamento automático significa que apenas os serviços (e infraestruturas de apoio) utilizados pela aplicação estão incluídos na imagem final no momento do link.</span><span class="sxs-lookup"><span data-stu-id="05b68-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="05b68-247">Aqui estão algumas características típicas do tamanho Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="05b68-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="05b68-248">Serviço Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="05b68-249">Tamanho típico em bytes</span><span class="sxs-lookup"><span data-stu-id="05b68-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="05b68-250">Serviços centrais (Exigir)</span><span class="sxs-lookup"><span data-stu-id="05b68-250">Core Services (Require)</span></span> |<span data-ttu-id="05b68-251">2.000</span><span class="sxs-lookup"><span data-stu-id="05b68-251">2,000</span></span>  |
|<span data-ttu-id="05b68-252">Serviços de fila</span><span class="sxs-lookup"><span data-stu-id="05b68-252">Queue Services</span></span>  |<span data-ttu-id="05b68-253">900</span><span class="sxs-lookup"><span data-stu-id="05b68-253">900</span></span>  |
|<span data-ttu-id="05b68-254">Serviços de Bandeira de Eventos</span><span class="sxs-lookup"><span data-stu-id="05b68-254">Event Flag Services</span></span>  |<span data-ttu-id="05b68-255">900</span><span class="sxs-lookup"><span data-stu-id="05b68-255">900</span></span>  |
|<span data-ttu-id="05b68-256">Serviços Semáforos</span><span class="sxs-lookup"><span data-stu-id="05b68-256">Semaphore Services</span></span>  |<span data-ttu-id="05b68-257">450</span><span class="sxs-lookup"><span data-stu-id="05b68-257">450</span></span>  |
|<span data-ttu-id="05b68-258">Serviços Mutex</span><span class="sxs-lookup"><span data-stu-id="05b68-258">Mutex Services</span></span>  |<span data-ttu-id="05b68-259">1200</span><span class="sxs-lookup"><span data-stu-id="05b68-259">1,200</span></span>  |
|<span data-ttu-id="05b68-260">Bloquear serviços de memória</span><span class="sxs-lookup"><span data-stu-id="05b68-260">Block Memory Services</span></span>  |<span data-ttu-id="05b68-261">550</span><span class="sxs-lookup"><span data-stu-id="05b68-261">550</span></span>  |
|<span data-ttu-id="05b68-262">Serviços de Memória Byte</span><span class="sxs-lookup"><span data-stu-id="05b68-262">Byte Memory Services</span></span>  |<span data-ttu-id="05b68-263">900</span><span class="sxs-lookup"><span data-stu-id="05b68-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="05b68-264">Execução rápida</span><span class="sxs-lookup"><span data-stu-id="05b68-264">Fast execution</span></span>

<span data-ttu-id="05b68-265">O Azure RTOS ThreadX consegue um interruptor de contexto sub-microsegundo nos processadores mais populares e é significativamente mais rápido em termos globais do que outros RTOSes comerciais.</span><span class="sxs-lookup"><span data-stu-id="05b68-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="05b68-266">Além de ser rápido, o Azure RTOS ThreadX também é altamente determinístico.</span><span class="sxs-lookup"><span data-stu-id="05b68-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="05b68-267">Consegue o mesmo desempenho rápido, quer existam 200 fios prontos, ou apenas um.</span><span class="sxs-lookup"><span data-stu-id="05b68-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="05b68-268">Aqui estão algumas características típicas de desempenho da Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="05b68-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="05b68-269">Arranque Rápido: Botas Azure RTOS ThreadX em menos de 120 ciclos.</span><span class="sxs-lookup"><span data-stu-id="05b68-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="05b68-270">Remoção opcional da verificação de erros básicos: A verificação de erros básicos de Azure RTOS ThreadX pode ser ignorada na hora da compilação.</span><span class="sxs-lookup"><span data-stu-id="05b68-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="05b68-271">Isto pode ser útil quando o código de aplicação é verificado e já não requer verificação de erros em cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="05b68-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="05b68-272">Note que isto pode ser feito numa unidade de compilação, em vez de em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="05b68-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="05b68-273">Picokernel™ Design: Os serviços não estão em camadas uns sobre os outros, eliminando assim a sobrecarga de chamada de função desnecessária.</span><span class="sxs-lookup"><span data-stu-id="05b68-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="05b68-274">\*Processamento de interrupção otimizado: Apenas registos de risco são guardados/restaurados após a entrada/saída do ISR, a menos que seja necessário uma pré-colocação.</span><span class="sxs-lookup"><span data-stu-id="05b68-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="05b68-275">Processamento otimizado da API:</span><span class="sxs-lookup"><span data-stu-id="05b68-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="05b68-276">Serviço Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="05b68-277">Tempo de serviço em Microsegundos\*</span><span class="sxs-lookup"><span data-stu-id="05b68-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="05b68-278">Suspensão do fio</span><span class="sxs-lookup"><span data-stu-id="05b68-278">Thread Suspend</span></span>  |<span data-ttu-id="05b68-279">0.6</span><span class="sxs-lookup"><span data-stu-id="05b68-279">0.6</span></span>  |
    |<span data-ttu-id="05b68-280">Resumo da linha</span><span class="sxs-lookup"><span data-stu-id="05b68-280">Thread Resume</span></span>  |<span data-ttu-id="05b68-281">0.6</span><span class="sxs-lookup"><span data-stu-id="05b68-281">0.6</span></span>  |
    |<span data-ttu-id="05b68-282">Enviar fila</span><span class="sxs-lookup"><span data-stu-id="05b68-282">Queue Send</span></span>  |<span data-ttu-id="05b68-283">0.3</span><span class="sxs-lookup"><span data-stu-id="05b68-283">0.3</span></span>  |
    |<span data-ttu-id="05b68-284">Receber fila</span><span class="sxs-lookup"><span data-stu-id="05b68-284">Queue Receive</span></span>  |<span data-ttu-id="05b68-285">0.3</span><span class="sxs-lookup"><span data-stu-id="05b68-285">0.3</span></span>  |
    |<span data-ttu-id="05b68-286">Obter Semáforo</span><span class="sxs-lookup"><span data-stu-id="05b68-286">Get Semaphore</span></span>  |<span data-ttu-id="05b68-287">0,2</span><span class="sxs-lookup"><span data-stu-id="05b68-287">0.2</span></span>  |
    |<span data-ttu-id="05b68-288">Coloque o Semáforo</span><span class="sxs-lookup"><span data-stu-id="05b68-288">Put Semaphore</span></span>  |<span data-ttu-id="05b68-289">0,2</span><span class="sxs-lookup"><span data-stu-id="05b68-289">0.2</span></span>  |
    |<span data-ttu-id="05b68-290">Interruptor de contexto</span><span class="sxs-lookup"><span data-stu-id="05b68-290">Context Switch</span></span>  |<span data-ttu-id="05b68-291">0,4</span><span class="sxs-lookup"><span data-stu-id="05b68-291">0.4</span></span>  |
    |<span data-ttu-id="05b68-292">Interrupção da resposta</span><span class="sxs-lookup"><span data-stu-id="05b68-292">Interrupt Response</span></span>  |<span data-ttu-id="05b68-293">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="05b68-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="05b68-294">\**Números de desempenho baseados no processador típico a funcionar a 200MHz*.</span><span class="sxs-lookup"><span data-stu-id="05b68-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="05b68-295">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="05b68-295">Advanced technology</span></span>

<span data-ttu-id="05b68-296">Azure RTOS ThreadX é uma tecnologia avançada cuja característica mais notável é o agendamento do limiar de pré-edição.</span><span class="sxs-lookup"><span data-stu-id="05b68-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="05b68-297">Esta funcionalidade é exclusiva da Azure RTOS ThreadX e tem sido alvo de uma extensa investigação académica.</span><span class="sxs-lookup"><span data-stu-id="05b68-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="05b68-298">Por exemplo, ver [Agendar Fixed-Priority Tarefas com Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), por Yun Wang, Universidade de Concordia, e Manas Saksena, Universidade de Pittsburgh.</span><span class="sxs-lookup"><span data-stu-id="05b68-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="05b68-299">Considere as capacidades da Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="05b68-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="05b68-300">Instalações multitarefas completas e abrangentes</span><span class="sxs-lookup"><span data-stu-id="05b68-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="05b68-301">Threads, temporizadores de aplicação, filas de mensagens, semafores contando, mutantes, bandeiras de eventos, bloco e piscinas de memória byte</span><span class="sxs-lookup"><span data-stu-id="05b68-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="05b68-302">Agendamento Preventivo Priority-Based</span><span class="sxs-lookup"><span data-stu-id="05b68-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="05b68-303">Flexibilidade Prioritária - Até 1024 Níveis Prioritários</span><span class="sxs-lookup"><span data-stu-id="05b68-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="05b68-304">Agendamento Cooperativo</span><span class="sxs-lookup"><span data-stu-id="05b68-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="05b68-305">Preemption-Threshold™ – Exclusivo para Azure RTOS ThreadX, ajuda a reduzir os interruptores de contexto e ajuda a garantir agendabilidade (por investigação académica)</span><span class="sxs-lookup"><span data-stu-id="05b68-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="05b68-306">Proteção da memória através de módulos Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="05b68-307">Totalmente determinístico</span><span class="sxs-lookup"><span data-stu-id="05b68-307">Fully Deterministic</span></span>
* <span data-ttu-id="05b68-308">Trace de eventos – Capture os últimos eventos *do* sistema/aplicação n</span><span class="sxs-lookup"><span data-stu-id="05b68-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="05b68-309">Chaining de Eventos™ – Registe uma função de chamada "notificação" específica para cada objeto de comunicação ou sincronização Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="05b68-310">Módulos Azure RTOS ThreadX com Proteção Opcional de Memória</span><span class="sxs-lookup"><span data-stu-id="05b68-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="05b68-311">Métricas de Desempenho Run-Time</span><span class="sxs-lookup"><span data-stu-id="05b68-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="05b68-312">Número de resuflações de fios</span><span class="sxs-lookup"><span data-stu-id="05b68-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="05b68-313">Número de suspensões por fios</span><span class="sxs-lookup"><span data-stu-id="05b68-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="05b68-314">Número de preemposições de fio solicitadas</span><span class="sxs-lookup"><span data-stu-id="05b68-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="05b68-315">Número de preemposições de interrupção de linha assíncrona</span><span class="sxs-lookup"><span data-stu-id="05b68-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="05b68-316">Número de inversões prioritárias de linha</span><span class="sxs-lookup"><span data-stu-id="05b68-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="05b68-317">Número de renúncias de fio</span><span class="sxs-lookup"><span data-stu-id="05b68-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="05b68-318">Kit de perfil de execução (EPK)</span><span class="sxs-lookup"><span data-stu-id="05b68-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="05b68-319">Pilha de interrupção separada</span><span class="sxs-lookup"><span data-stu-id="05b68-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="05b68-320">Análise da pilha de Run-Time</span><span class="sxs-lookup"><span data-stu-id="05b68-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="05b68-321">Processamento de interrupção de temporizador otimizado</span><span class="sxs-lookup"><span data-stu-id="05b68-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="05b68-322">Suporte multicore (AMP & SMP)</span><span class="sxs-lookup"><span data-stu-id="05b68-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="05b68-323">O Standard Azure RTOS ThreadX é frequentemente utilizado numa moda multiprocessa assimétrica (AMP), onde uma cópia separada do Azure RTOS ThreadX e a aplicação (ou Linux) executam em cada núcleo e comunicam entre si através de memória partilhada ou de um mecanismo de comunicação interprocessador, como o OpenAMP (Azure RTOS ThreadX suporta o OpenAMP).</span><span class="sxs-lookup"><span data-stu-id="05b68-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="05b68-324">Esta é a configuração multicore mais típica usando o Azure RTOS ThreadX e pode ser a mais eficiente se a aplicação for capaz de carregar eficazmente os processadores.</span><span class="sxs-lookup"><span data-stu-id="05b68-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="05b68-325">Para ambientes onde o carregamento dos processadores é altamente dinâmico, o Azure RTOS ThreadX Symetric Multiprocessing (SMP) está disponível para as seguintes famílias de processadores:</span><span class="sxs-lookup"><span data-stu-id="05b68-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="05b68-326">Cortex-Ax ARM</span><span class="sxs-lookup"><span data-stu-id="05b68-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="05b68-327">Cortex-Rx ARM</span><span class="sxs-lookup"><span data-stu-id="05b68-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="05b68-328">ARM Cortex-A5x 64-bit</span><span class="sxs-lookup"><span data-stu-id="05b68-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="05b68-329">MIPS 34K, 1004K e interAptiv</span><span class="sxs-lookup"><span data-stu-id="05b68-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="05b68-330">PowerPC</span><span class="sxs-lookup"><span data-stu-id="05b68-330">PowerPC</span></span>
* <span data-ttu-id="05b68-331">Sinopsias ARC HS</span><span class="sxs-lookup"><span data-stu-id="05b68-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="05b68-332">x86</span><span class="sxs-lookup"><span data-stu-id="05b68-332">x86</span></span>

<span data-ttu-id="05b68-333">A Azure RTOS ThreadX SMP executa o equilíbrio dinâmico da carga entre processadores *n* e permite que todos os recursos Azure RTOS ThreadX (filas, semáforos, bandeiras de eventos, piscinas de memória, etc.) sejam acedidos por qualquer fio em qualquer núcleo.</span><span class="sxs-lookup"><span data-stu-id="05b68-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="05b68-334">A Azure RTOS ThreadX SMP permite a API API completa Azure RTOS ThreadX em todos os núcleos e introduz os seguintes novos API aplicáveis à operação SMP:</span><span class="sxs-lookup"><span data-stu-id="05b68-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="05b68-335">Proteção da memória através de módulos Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="05b68-336">Um produto adicional chamado Azure RTOS ThreadX MODULES permite que um ou mais fios de aplicação sejam agregados num "Módulo" que pode ser carregado e executado dinamicamente (ou executado no lugar) no alvo.</span><span class="sxs-lookup"><span data-stu-id="05b68-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="05b68-337">Os módulos permitem a atualização de campo, a fixação de erros e a partição do programa para permitir que as grandes aplicações ocupem apenas a memória necessária através de fios ativos.</span><span class="sxs-lookup"><span data-stu-id="05b68-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="05b68-338">Os módulos também têm um espaço de endereço completamente separado do próprio Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="05b68-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="05b68-339">Isto permite que o Azure RTOS ThreadX coloque a proteção da memória (via MPU ou MMU) em torno do Módulo de modo a que o acesso acidental fora do módulo não seja capaz de corromper qualquer outro componente de software.</span><span class="sxs-lookup"><span data-stu-id="05b68-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="05b68-340">Conformidade com o MISRA</span><span class="sxs-lookup"><span data-stu-id="05b68-340">MISRA compliant</span></span>

<span data-ttu-id="05b68-341">O código de souce Azure RTOS ThreadX e Azure RTOS ThreadX SMP é compatível com MISRA-C:2004 e MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="05b68-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="05b68-342">MISRA C é um conjunto de diretrizes de programação para sistemas críticos utilizando a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="05b68-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="05b68-343">As diretrizes originais do MISRA C destinavam-se principalmente a aplicações para automóveis; no entanto, o MISRA C é hoje amplamente reconhecido como sendo aplicável a qualquer aplicação crítica de segurança.</span><span class="sxs-lookup"><span data-stu-id="05b68-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="05b68-344">O Azure RTOS ThreadX está em conformidade com todas as regras necessárias e obrigatórias de MISRA-C:2004 e MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="05b68-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certificação Misra":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="05b68-346">Apoia as arquiteturas mais populares</span><span class="sxs-lookup"><span data-stu-id="05b68-346">Supports most popular architectures</span></span>

<span data-ttu-id="05b68-347">O Azure RTOS ThreadX funciona em microprocessadores de 32/64 bits mais populares, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:</span><span class="sxs-lookup"><span data-stu-id="05b68-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="05b68-348">Dispositivos Analógicos: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="05b68-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="05b68-349">Núcleo de Andes: RISC-V</span><span class="sxs-lookup"><span data-stu-id="05b68-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="05b68-350">Ambiqmicro: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="05b68-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="05b68-351">ARM: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="05b68-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="05b68-352">Cadência: Xtensa, Diamante</span><span class="sxs-lookup"><span data-stu-id="05b68-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="05b68-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="05b68-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="05b68-354">Cipreste: RISC-V</span><span class="sxs-lookup"><span data-stu-id="05b68-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="05b68-355">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="05b68-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="05b68-356">Infineon: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="05b68-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="05b68-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="05b68-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="05b68-358">Microchip: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="05b68-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="05b68-359">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="05b68-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="05b68-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="05b68-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="05b68-361">Renesas: SH, HS, V850, RX, RZ, Sinergia</span><span class="sxs-lookup"><span data-stu-id="05b68-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="05b68-362">Laboratórios de Silício: EFM32</span><span class="sxs-lookup"><span data-stu-id="05b68-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="05b68-363">Sinopses: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="05b68-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="05b68-364">ST: STM32, ARM7, ARM9, Córtex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="05b68-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="05b68-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="05b68-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="05b68-366">Computação de ondas: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M</span><span class="sxs-lookup"><span data-stu-id="05b68-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="05b68-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="05b68-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="05b68-368">Suporta as ferramentas mais populares</span><span class="sxs-lookup"><span data-stu-id="05b68-368">Supports most popular tools</span></span>

<span data-ttu-id="05b68-369">O Azure RTOS ThreadX suporta as ferramentas de desenvolvimento incorporadas mais populares, incluindo a bancada de trabalho incorporada da IAR™, que também tem a mais abrangente consciência de kernel Azure RTOS ThreadX disponível.</span><span class="sxs-lookup"><span data-stu-id="05b68-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="05b68-370">A integração adicional de ferramentas inclui GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore e todos os dispositivos analógicos.</span><span class="sxs-lookup"><span data-stu-id="05b68-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="05b68-371">Camada de adaptação para ThreadX</span><span class="sxs-lookup"><span data-stu-id="05b68-371">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="05b68-372">O Azure RTOS ThreadX é um sistema operativo em tempo real (RTOS) avançado criado especificamente para aplicações profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="05b68-372">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="05b68-373">Para facilitar a migração de aplicações para Auzre RTOS, a ThreadX fornece [camadas de adaptação](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) para várias APIs RTOS (FreeRTOS, POSIX, OSEK, etc.)</span><span class="sxs-lookup"><span data-stu-id="05b68-373">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
