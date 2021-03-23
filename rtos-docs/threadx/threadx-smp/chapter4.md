---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX SMP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX SMP por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828022"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="669f3-103">Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX SMP</span><span class="sxs-lookup"><span data-stu-id="669f3-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="669f3-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX SMP por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="669f3-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="669f3-105">Os seus nomes são concebidos para que todos os serviços semelhantes sejam agrupados.</span><span class="sxs-lookup"><span data-stu-id="669f3-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="669f3-106">Na secção "Valores de Retorno" nas seguintes descrições, os valores em **BOLD** não são afetados pela **TX_DISABLE_ERROR_CHECKING** definem utilizados para desativar a verificação de erros da API; enquanto os valores mostrados em nãobold são completamente desativados.</span><span class="sxs-lookup"><span data-stu-id="669f3-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="669f3-107">Além disso, um "**Sim**" listado sob a rubrica "**Preemption Possible**" indica que ligar para o serviço pode retomar um fio de maior prioridade, antecipando assim o fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="669f3-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="669f3-108">**tx_block_allocate**: *Atribuir bloco de memória de tamanho fixo*</span><span class="sxs-lookup"><span data-stu-id="669f3-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="669f3-109">**tx_block_pool_create**: *Criar um conjunto de blocos de memória de tamanho fixo*</span><span class="sxs-lookup"><span data-stu-id="669f3-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="669f3-110">**tx_block_pool_delete**: *Eliminar o conjunto de blocos de memória*</span><span class="sxs-lookup"><span data-stu-id="669f3-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="669f3-111">**tx_block_pool_info_get**: *Recuperar informações sobre a piscina de blocos*</span><span class="sxs-lookup"><span data-stu-id="669f3-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="669f3-112">**tx_block_pool_performance_info_get**: *Obtenha informações sobre desempenho do bloco de piscina*</span><span class="sxs-lookup"><span data-stu-id="669f3-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="669f3-113">**tx_block_pool_performance_system_info_get**: *Obtenha informações sobre o desempenho do sistema de piscinas de blocos*</span><span class="sxs-lookup"><span data-stu-id="669f3-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="669f3-114">**tx_block_pool_prioritize**: *Priorize lista de suspensão de piscina de bloco*</span><span class="sxs-lookup"><span data-stu-id="669f3-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="669f3-115">**tx_block_release**: *Liberte o bloco de memória de tamanho fixo*</span><span class="sxs-lookup"><span data-stu-id="669f3-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="669f3-116">**tx_byte_allocate**: *Aloque bytes de memória*</span><span class="sxs-lookup"><span data-stu-id="669f3-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="669f3-117">**tx_byte_pool_create**: *Criar piscina de memória de bytes*</span><span class="sxs-lookup"><span data-stu-id="669f3-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="669f3-118">**tx_byte_pool_delete**: *Apagar a piscina byte de memória*</span><span class="sxs-lookup"><span data-stu-id="669f3-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="669f3-119">**tx_byte_pool_info_get**: *Recuperar informações sobre a piscina byte*</span><span class="sxs-lookup"><span data-stu-id="669f3-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="669f3-120">**tx_byte_pool_performance_info_get**: *Obter informações sobre o desempenho da piscina byte*</span><span class="sxs-lookup"><span data-stu-id="669f3-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="669f3-121">**tx_byte_pool_performance_system_info_get**: *Obter informações sobre o desempenho do sistema de piscina byte*</span><span class="sxs-lookup"><span data-stu-id="669f3-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="669f3-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span><span class="sxs-lookup"><span data-stu-id="669f3-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="669f3-123">**tx_byte_release**: *Liberte bytes de volta à piscina da memória*</span><span class="sxs-lookup"><span data-stu-id="669f3-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="669f3-124">**tx_event_flags_create**: *Criar grupo de bandeiras de eventos*</span><span class="sxs-lookup"><span data-stu-id="669f3-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="669f3-125">**tx_event_flags_delete**: *Eliminar grupo de bandeiras de eventos*</span><span class="sxs-lookup"><span data-stu-id="669f3-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="669f3-126">**tx_event_flags_get**: *Obtenha bandeiras de eventos do grupo de bandeiras de eventos*</span><span class="sxs-lookup"><span data-stu-id="669f3-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="669f3-127">**tx_event_flags_info_get**: *Recuperar informações sobre o grupo de bandeiras de eventos*</span><span class="sxs-lookup"><span data-stu-id="669f3-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="669f3-128">**tx_event_flags_performance_info_get**: *Obtenha informações de desempenho do grupo de bandeiras de eventos*</span><span class="sxs-lookup"><span data-stu-id="669f3-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="669f3-129">**tx_event_flags_performance_system_info_get**: *Recuperar informações do sistema de desempenho*</span><span class="sxs-lookup"><span data-stu-id="669f3-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="669f3-130">**tx_event_flags_set**: *Coloque bandeiras de evento em um grupo de bandeiras de evento*</span><span class="sxs-lookup"><span data-stu-id="669f3-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="669f3-131">**tx_event_flags_set_notify**: *Notifique a aplicação quando as bandeiras do evento forem definidas*</span><span class="sxs-lookup"><span data-stu-id="669f3-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="669f3-132">**tx_interrupt_control**: *Ativar e desativar interrupções*</span><span class="sxs-lookup"><span data-stu-id="669f3-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="669f3-133">**tx_mutex_create**: *Criar mutex de exclusão mútua*</span><span class="sxs-lookup"><span data-stu-id="669f3-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="669f3-134">**tx_mutex_delete**: *Eliminar o mutex de exclusão mútua*</span><span class="sxs-lookup"><span data-stu-id="669f3-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="669f3-135">**tx_mutex_get**: *Obter a propriedade do mutex*</span><span class="sxs-lookup"><span data-stu-id="669f3-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="669f3-136">**tx_mutex_info_get**: *Recuperar informações sobre o mutex*</span><span class="sxs-lookup"><span data-stu-id="669f3-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="669f3-137">**tx_mutex_performance_info_get**: *Obtenha informações sobre desempenho de mutex*</span><span class="sxs-lookup"><span data-stu-id="669f3-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="669f3-138">**tx_mutex_performance_system_info_get**: *Obtenha informações sobre desempenho do sistema mutex*</span><span class="sxs-lookup"><span data-stu-id="669f3-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="669f3-139">**tx_mutex_prioritize**: *Prioritize lista de suspensão de mutantes*</span><span class="sxs-lookup"><span data-stu-id="669f3-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="669f3-140">**tx_mutex_put**: *Libertar a propriedade do mutex*</span><span class="sxs-lookup"><span data-stu-id="669f3-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="669f3-141">**tx_queue_create**: *Criar fila de mensagens*</span><span class="sxs-lookup"><span data-stu-id="669f3-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="669f3-142">**tx_queue_delete**: *Apagar fila de mensagens*</span><span class="sxs-lookup"><span data-stu-id="669f3-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="669f3-143">**tx_queue_flush**: *Mensagens vazias na fila da mensagem*</span><span class="sxs-lookup"><span data-stu-id="669f3-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="669f3-144">**tx_queue_front_send**: *Enviar mensagem para a frente da fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="669f3-145">**tx_queue_info_get**: *Recuperar informações sobre a fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="669f3-146">**tx_queue_performance_info_get**: *Obtenha informações sobre desempenho da fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="669f3-147">**tx_queue_performance_system_info_get**: *Obtenha informações sobre o desempenho do sistema de fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="669f3-148">**tx_queue_prioritize**: *Priorize a lista de suspensão da fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="669f3-149">**tx_queue_receive**: *Receba mensagem da fila da mensagem*</span><span class="sxs-lookup"><span data-stu-id="669f3-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="669f3-150">**tx_queue_send**: *Enviar mensagem para a fila da mensagem*</span><span class="sxs-lookup"><span data-stu-id="669f3-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="669f3-151">**tx_queue_send_notify**: *Notifique o pedido quando a mensagem é enviada para a fila*</span><span class="sxs-lookup"><span data-stu-id="669f3-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="669f3-152">**tx_semaphore_ceiling_put**: *Coloque um caso na contagem de semáforos com teto*</span><span class="sxs-lookup"><span data-stu-id="669f3-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="669f3-153">**tx_semaphore_create**: *Criar semáforo de contagem*</span><span class="sxs-lookup"><span data-stu-id="669f3-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="669f3-154">**tx_semaphore_delete**: *Eliminar o semáforo de contagem*</span><span class="sxs-lookup"><span data-stu-id="669f3-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="669f3-155">**tx_semaphore_get**: *Obtenha a ocorrência da contagem do semáforo*</span><span class="sxs-lookup"><span data-stu-id="669f3-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="669f3-156">**tx_semaphore_info_get**: *Recuperar informações sobre semáforos*</span><span class="sxs-lookup"><span data-stu-id="669f3-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="669f3-157">**tx_semaphore_performance_info_get**: *Obtenha informações sobre desempenho de semáforos*</span><span class="sxs-lookup"><span data-stu-id="669f3-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="669f3-158">**tx_semaphore_performance_system_info_get**: *Obtenha informações sobre o desempenho do sistema de semáforos*</span><span class="sxs-lookup"><span data-stu-id="669f3-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="669f3-159">**tx_semaphore_prioritize**: *Priorizar lista de suspensão de semáforos*</span><span class="sxs-lookup"><span data-stu-id="669f3-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="669f3-160">**tx_semaphore_put**: *Coloque um caso na contagem de semáforos*</span><span class="sxs-lookup"><span data-stu-id="669f3-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="669f3-161">**tx_semaphore_put_notify**: *Notifique o pedido quando o semáforo for colocado*</span><span class="sxs-lookup"><span data-stu-id="669f3-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="669f3-162">**tx_thread_create**: *Criar fio de aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="669f3-163">**tx_thread_delete**: *Eliminar o fio da aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="669f3-164">**tx_thread_entry_exit_notify**: *Notifique o pedido após a entrada e saída do fio*</span><span class="sxs-lookup"><span data-stu-id="669f3-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="669f3-165">**tx_thread_identify**: *Recupera o ponteiro para a execução do fio*</span><span class="sxs-lookup"><span data-stu-id="669f3-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="669f3-166">**tx_thread_info_get**: *Recuperar informações sobre o fio*</span><span class="sxs-lookup"><span data-stu-id="669f3-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="669f3-167">**tx_thread_performance_info_get**: *Obtenha informações sobre desempenho de thread*</span><span class="sxs-lookup"><span data-stu-id="669f3-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="669f3-168">**tx_thread_performance_system_info_get**: *Obtenha informações sobre desempenho do sistema de fios*</span><span class="sxs-lookup"><span data-stu-id="669f3-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="669f3-169">**tx_thread_preemption_change**: *Alterar limiar de preempção do fio de aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="669f3-170">**tx_thread_priority_change**: *Alterar prioridade do fio de aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="669f3-171">**tx_thread_relinquish**: *Renunciar ao controlo a outros fios de aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="669f3-172">**tx_thread_reset**: *Linha de reset*</span><span class="sxs-lookup"><span data-stu-id="669f3-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="669f3-173">**tx_thread_resume**: *Retomar o fio de aplicação suspenso*</span><span class="sxs-lookup"><span data-stu-id="669f3-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="669f3-174">**tx_thread_sleep**: *Suspender o fio de corrente por tempo especificado*</span><span class="sxs-lookup"><span data-stu-id="669f3-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="669f3-175">**tx_thread_smp_core_exclude**: *Exclua a execução de fios num conjunto de núcleos*</span><span class="sxs-lookup"><span data-stu-id="669f3-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="669f3-176">**tx_thread_smp_core_exclude_get**: *Obtém a exclusão atual do núcleo do fio*</span><span class="sxs-lookup"><span data-stu-id="669f3-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="669f3-177">**tx_thread_smp_core_get**: *Recupere atualmente o núcleo de execução do chamador*</span><span class="sxs-lookup"><span data-stu-id="669f3-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="669f3-178">**tx_thread_stack_error_notify**: *Registar chamada de notificação de erro de pilha de fio*</span><span class="sxs-lookup"><span data-stu-id="669f3-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="669f3-179">**tx_thread_suspend**: *Suspender o fio da aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="669f3-180">**tx_thread_terminate**: *Termina o fio da aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="669f3-181">**tx_thread_time_slice_change**: *Altera a fatia de tempo do fio de aplicação*</span><span class="sxs-lookup"><span data-stu-id="669f3-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="669f3-182">**tx_thread_wait_abort**: *Abortar suspensão de fio especificado*</span><span class="sxs-lookup"><span data-stu-id="669f3-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="669f3-183">**tx_time_get**: *Recupera a hora atual*</span><span class="sxs-lookup"><span data-stu-id="669f3-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="669f3-184">**tx_time_set**: *Define a hora atual*</span><span class="sxs-lookup"><span data-stu-id="669f3-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="669f3-185">**tx_timer_activate**: *Ativar o temporizador de aplicações*</span><span class="sxs-lookup"><span data-stu-id="669f3-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="669f3-186">**tx_timer_change**: *Alterar o temporizador de aplicações*</span><span class="sxs-lookup"><span data-stu-id="669f3-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="669f3-187">**tx_timer_create**: *Criar temporizador de aplicações*</span><span class="sxs-lookup"><span data-stu-id="669f3-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="669f3-188">**tx_timer_deactivate**: *Temporizador de aplicação desativado*</span><span class="sxs-lookup"><span data-stu-id="669f3-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="669f3-189">**tx_timer_delete**: *Eliminar o temporizador de aplicações*</span><span class="sxs-lookup"><span data-stu-id="669f3-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="669f3-190">**tx_timer_info_get**: *Recuperar informações sobre um temporizador de aplicações*</span><span class="sxs-lookup"><span data-stu-id="669f3-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="669f3-191">**tx_timer_performance_info_get**: *Obtenha informações sobre desempenho do temporizador*</span><span class="sxs-lookup"><span data-stu-id="669f3-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="669f3-192">**tx_timer_performance_system_info_get**: *Obtenha informações sobre o desempenho do sistema do sistema temporizador*</span><span class="sxs-lookup"><span data-stu-id="669f3-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="669f3-193">**tx_timer_smp_core_exclude**: *Excluir a execução do temporizador num conjunto de núcleos*</span><span class="sxs-lookup"><span data-stu-id="669f3-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="669f3-194">**tx_timer_smp_core_exclude_get**: *Obtém a exclusão atual do núcleo do temporizador*</span><span class="sxs-lookup"><span data-stu-id="669f3-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="669f3-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-195">tx_block_allocate</span></span>
<span data-ttu-id="669f3-196">Alocar bloco de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="669f3-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-197">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-198">Description</span></span>

<span data-ttu-id="669f3-199">Este serviço aloca um bloco de memória de tamanho fixo a partir do conjunto de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="669f3-200">O tamanho real do bloco de memória é determinado durante a criação do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="669f3-201">É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído.</span><span class="sxs-lookup"><span data-stu-id="669f3-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="669f3-202">Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente).</span><span class="sxs-lookup"><span data-stu-id="669f3-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="669f3-203">Os resultados são imprevisíveis e muitas vezes fatais!</span><span class="sxs-lookup"><span data-stu-id="669f3-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-204">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-204">Parameters</span></span>

- <span data-ttu-id="669f3-205">**pool_ptr**: Ponteiro para um conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="669f3-206">**block_ptr**: Ponter para um ponteiro de bloco de destino.</span><span class="sxs-lookup"><span data-stu-id="669f3-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="669f3-207">Na atribuição bem sucedida, o endereço do bloco de memória atribuído é colocado onde este parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="669f3-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="669f3-208">**wait_option**: Define como o serviço se comporta se não houver blocos de memória disponíveis.</span><span class="sxs-lookup"><span data-stu-id="669f3-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="669f3-209">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-210">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-211">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-212">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="669f3-213">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido bem sucedida ou não.</span><span class="sxs-lookup"><span data-stu-id="669f3-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="669f3-214">Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="669f3-215">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um bloco de memória esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="669f3-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="669f3-216">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se espera por um bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-217">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-217">Return Values</span></span>

- <span data-ttu-id="669f3-218">**TX_SUCCESS**: (0x00) Atribuição bem sucedida do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="669f3-219">**TX_DELETED**: (0x01) A piscina do bloco de memória foi eliminada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-220">**TX_NO_MEMORY**: (0x10) O serviço não pôde atribuir um bloco de memória dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="669f3-221">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="669f3-222">TX_POOL_ERROR: (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="669f3-223">TX_PTR_ERROR: (0x03) Ponteiro inválido para ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="669f3-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="669f3-224">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-225">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-225">Allowed From</span></span>

<span data-ttu-id="669f3-226">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-227">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-227">Preemption Possible</span></span>

<span data-ttu-id="669f3-228">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="669f3-230">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-230">See Also</span></span>

- <span data-ttu-id="669f3-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-231">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="669f3-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="669f3-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-238">tx_block_pool_create</span></span>
<span data-ttu-id="669f3-239">Criar piscina de blocos de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="669f3-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="669f3-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-241">Description</span></span>

<span data-ttu-id="669f3-242">Este serviço cria uma piscina de blocos de memória de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="669f3-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="669f3-243">A área de memória especificada é dividida em tantos blocos de memória de tamanho fixo quanto possível utilizando a fórmula:</span><span class="sxs-lookup"><span data-stu-id="669f3-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="669f3-244">**blocos totais** =**(bytes totais)**/**(tamanho do bloco** + tamanho (vazio \*))</span><span class="sxs-lookup"><span data-stu-id="669f3-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-245">Cada bloco de memória contém um ponteiro de sobrecarga que é invisível para o utilizador e é representado pelo "tamanho (vazio \*)" na fórmula anterior.</span><span class="sxs-lookup"><span data-stu-id="669f3-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-246">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-246">Parameters</span></span>

- <span data-ttu-id="669f3-247">**pool_ptr**: Pontear para um bloco de controlo de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="669f3-248">**name_ptr**: Pontear o nome do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="669f3-249">**block_size**: Número de bytes em cada bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="669f3-250">**pool_start**: Endereço inicial do conjunto do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="669f3-251">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG..</span><span class="sxs-lookup"><span data-stu-id="669f3-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="669f3-252">**pool_size**: Número total de bytes disponíveis para o conjunto do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-253">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-253">Return Values</span></span>

- <span data-ttu-id="669f3-254">**TX_SUCCESS**: (0x00) Criação de piscina de blocos de memória bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="669f3-255">TX_POOL_ERROR: (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="669f3-256">Ou o ponteiro é NULO ou a piscina já está criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="669f3-257">TX_PTR_ERROR: (0x03) Endereço inicial inválido da piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="669f3-258">TX_SIZE_ERROR: (0x05) O tamanho da piscina é inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="669f3-259">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-260">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-260">Allowed From</span></span>

<span data-ttu-id="669f3-261">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-262">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-262">Preemption Possible</span></span>

<span data-ttu-id="669f3-263">No</span><span class="sxs-lookup"><span data-stu-id="669f3-263">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-264">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-265">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-265">See Also</span></span>

- <span data-ttu-id="669f3-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-266">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="669f3-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="669f3-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-273">tx_block_pool_delete</span></span>

<span data-ttu-id="669f3-274">Apagar o conjunto de blocos de memória</span><span class="sxs-lookup"><span data-stu-id="669f3-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-276">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-276">Description</span></span>

<span data-ttu-id="669f3-277">Este serviço elimina o conjunto de memória de bloco especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="669f3-278">Todos os fios suspensos à espera de um bloco de memória desta piscina são retomados e dado um estado de retorno TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="669f3-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-279">É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="669f3-280">Além disso, a aplicação deve impedir a utilização de uma piscina eliminada ou dos seus antigos blocos de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-281">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-281">Parameters</span></span>

- <span data-ttu-id="669f3-282">**pool_ptr**: Ponteiro para um conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-283">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-283">Return Values</span></span>

- <span data-ttu-id="669f3-284">**TX_SUCCESS**: (0x00) Eliminação bem sucedida do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="669f3-285">TX_POOL_ERROR: (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="669f3-286">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-287">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-287">Allowed From</span></span>

<span data-ttu-id="669f3-288">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-289">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-289">Preemption Possible</span></span>

<span data-ttu-id="669f3-290">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-291">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-292">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-292">See Also</span></span>

- <span data-ttu-id="669f3-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-293">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-294">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="669f3-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="669f3-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="669f3-301">Recuperar informações sobre a piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="669f3-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-302">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="669f3-303">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-303">Description</span></span>

<span data-ttu-id="669f3-304">Este serviço obtém informações sobre o conjunto de memórias de bloco especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-305">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-305">Parameters</span></span>

- <span data-ttu-id="669f3-306">**pool_ptr**: Ponteiro para o conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="669f3-307">**nome**: Ponteiro para destino para o ponteiro para o nome do pool do bloco.</span><span class="sxs-lookup"><span data-stu-id="669f3-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="669f3-308">**disponível**: Ponteiro para o destino para o número de blocos disponíveis na piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="669f3-309">**total_blocks**: Ponte para o destino para o número total de blocos na piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="669f3-310">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste bloco pool.</span><span class="sxs-lookup"><span data-stu-id="669f3-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="669f3-311">**suspended_count**: Ponter para o destino para o número de fios atualmente suspensos neste bloco.</span><span class="sxs-lookup"><span data-stu-id="669f3-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="669f3-312">**next_pool**: Ponter para o destino para o ponteiro do próximo conjunto de blocos criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-313">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-314">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-314">Return Values</span></span>

- <span data-ttu-id="669f3-315">**TX_SUCCESS**: (0x00) Recuperar informações de piscina de blocos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="669f3-316">TX_POOL_ERROR: (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-317">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-317">Allowed From</span></span>

<span data-ttu-id="669f3-318">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-319">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-320">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-320">See Also</span></span>

- <span data-ttu-id="669f3-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-321">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-322">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="669f3-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="669f3-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="669f3-330">Obtenha informações de desempenho da piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="669f3-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-331">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="669f3-332">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-332">Description</span></span>

<span data-ttu-id="669f3-333">Este serviço obtém informações de desempenho sobre o conjunto de blocos de memória especificados.</span><span class="sxs-lookup"><span data-stu-id="669f3-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-334">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-335">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-335">Parameters</span></span>

- <span data-ttu-id="669f3-336">**pool_ptr**: Ponteiro para o conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="669f3-337">**atribuições**: Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-338">**lançamentos**: Ponteiro para o destino para o número de pedidos de libertação realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-339">**suspensões**: Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="669f3-340">**intervalos :** Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-341">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-342">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-342">Return Values</span></span>

- <span data-ttu-id="669f3-343">**TX_SUCCESS**: (0x00) Desempenho bem sucedido da piscina do bloco obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="669f3-344">**TX_PTR_ERROR**: (0x03) Ponteiro de piscina de bloco inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="669f3-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-346">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-346">Allowed From</span></span>

<span data-ttu-id="669f3-347">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-348">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-349">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-349">See Also</span></span>

- <span data-ttu-id="669f3-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-350">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-351">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="669f3-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="669f3-358">Obtenha informações de desempenho do sistema de piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="669f3-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-360">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-360">Description</span></span>

<span data-ttu-id="669f3-361">Este serviço obtém informações de desempenho sobre todos os conjuntos de blocos de memória na aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-362">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-363">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-363">Parameters</span></span>

- <span data-ttu-id="669f3-364">**atribuições**: Ponteiro para destino para o número total de pedidos de atribuição realizados em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="669f3-365">**lançamentos**: Ponteiro para destino para o número total de pedidos de libertação realizados em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="669f3-366">**suspensões**: Ponteiro para o destino para o número total de suspensões de atribuição de fios em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="669f3-367">**intervalos :** Ponte para o destino para o número total de intervalos de suspensão atribuídos em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="669f3-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-368">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-369">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-369">Return Values</span></span>

- <span data-ttu-id="669f3-370">**TX_SUCCESS**: (0x00) O desempenho do sistema de piscina de blocos bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="669f3-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-372">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-372">Allowed From</span></span>

<span data-ttu-id="669f3-373">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-374">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-375">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-375">See Also</span></span>

- <span data-ttu-id="669f3-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-376">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-377">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="669f3-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="669f3-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="669f3-384">Priorizar lista de suspensão de piscina de bloco</span><span class="sxs-lookup"><span data-stu-id="669f3-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-386">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-386">Description</span></span>

<span data-ttu-id="669f3-387">Este serviço coloca o fio de prioridade mais elevado suspenso por um bloco de memória nesta piscina na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="669f3-388">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-389">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-389">Parameters</span></span> 

- <span data-ttu-id="669f3-390">**pool_ptr**: Pontear para um bloco de controlo de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-391">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-391">Return Values</span></span>

- <span data-ttu-id="669f3-392">**TX_SUCCESS**: (0x00) Prioridades de piscina de blocos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="669f3-393">TX_POOL_ERROR: (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-394">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-394">Allowed From</span></span>

<span data-ttu-id="669f3-395">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-396">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-396">Preemption Possible</span></span>

<span data-ttu-id="669f3-397">No</span><span class="sxs-lookup"><span data-stu-id="669f3-397">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-398">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-399">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-399">See Also</span></span>

- <span data-ttu-id="669f3-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-400">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-401">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="669f3-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="669f3-407">tx_block_release</span></span>

<span data-ttu-id="669f3-408">Liberte o bloco de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="669f3-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-410">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-410">Description</span></span>

<span data-ttu-id="669f3-411">Este serviço liberta um bloco previamente atribuído de volta ao seu pool de memória associado.</span><span class="sxs-lookup"><span data-stu-id="669f3-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="669f3-412">Se houver um ou mais fios suspensos à espera de blocos de memória desta piscina, o primeiro fio suspenso é dado a este bloco de memória e retomado.</span><span class="sxs-lookup"><span data-stu-id="669f3-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-413">A aplicação deve evitar a utilização de uma área de bloco de memória depois de ter sido libertada de volta à piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-414">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-414">Parameters</span></span>

- <span data-ttu-id="669f3-415">**block_ptr**: Ponter para o bloco de memória previamente atribuído.</span><span class="sxs-lookup"><span data-stu-id="669f3-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-416">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-416">Return Values</span></span>

- <span data-ttu-id="669f3-417">**TX_SUCCESS**: (0x00) Desbloqueio do bloco de memória bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="669f3-418">TX_PTR_ERROR: (0x03) Ponteiro inválido para o bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-419">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-419">Allowed From</span></span>

<span data-ttu-id="669f3-420">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-421">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-421">Preemption Possible</span></span>

<span data-ttu-id="669f3-422">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-423">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-424">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-424">See Also</span></span>

- <span data-ttu-id="669f3-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-425">tx_block_allocate</span></span>
- <span data-ttu-id="669f3-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-426">tx_block_pool_create</span></span>
- <span data-ttu-id="669f3-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="669f3-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="669f3-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="669f3-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-432">tx_byte_allocate</span></span>

<span data-ttu-id="669f3-433">Alocar bytes de memória</span><span class="sxs-lookup"><span data-stu-id="669f3-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-434">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-435">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-435">Description</span></span>

<span data-ttu-id="669f3-436">Este serviço atribui o número especificado de bytes da piscina de bytes de memória especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="669f3-437">É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído.</span><span class="sxs-lookup"><span data-stu-id="669f3-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="669f3-438">Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente).</span><span class="sxs-lookup"><span data-stu-id="669f3-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="669f3-439">Os resultados são imprevisíveis e muitas vezes fatais!</span><span class="sxs-lookup"><span data-stu-id="669f3-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-440">O desempenho deste serviço é uma função do tamanho do bloco e da quantidade de fragmentação na piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="669f3-441">Por conseguinte, este serviço não deve ser utilizado durante os fios críticos de execução.</span><span class="sxs-lookup"><span data-stu-id="669f3-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-442">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-442">Parameters</span></span>

- <span data-ttu-id="669f3-443">**pool_ptr**: Ponteiro para um conjunto de memórias previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="669f3-444">**memory_ptr**: Ponteiro para um ponteiro de memória de destino.</span><span class="sxs-lookup"><span data-stu-id="669f3-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="669f3-445">Na atribuição bem sucedida, o endereço da área de memória atribuída é colocado onde este parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="669f3-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="669f3-446">**memory_size**: Número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="669f3-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="669f3-447">**wait_option**: Define como o serviço se comporta se não houver memória suficiente disponível.</span><span class="sxs-lookup"><span data-stu-id="669f3-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="669f3-448">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-449">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-450">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-451">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-452">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-453">*Esta é a única opção válida se o serviço for chamado de inicialização.*</span><span class="sxs-lookup"><span data-stu-id="669f3-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="669f3-454">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que a memória esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="669f3-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="669f3-455">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pela memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-456">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-456">Return Values</span></span>

- <span data-ttu-id="669f3-457">**TX_SUCCESS:**(0x00) Atribuição de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="669f3-458">**TX_DELETED**: (0x01) O pool de memória foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-459">**TX_NO_MEMORY**: (0x10) O serviço não pôde alocar a memória dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="669f3-460">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-461">TX_POOL_ERROR: (0x02) Ponteiro do piscina de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="669f3-462">TX_PTR_ERROR: (0x03) Ponteiro inválido para ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="669f3-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="669f3-463">TX_SIZE_ERROR: (0X05) O tamanho solicitado é zero ou maior do que a piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="669f3-464">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="669f3-465">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-466">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-466">Allowed From</span></span>

<span data-ttu-id="669f3-467">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-468">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-468">Preemption Possible</span></span>

<span data-ttu-id="669f3-469">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-470">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-471">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-471">See Also</span></span>

- <span data-ttu-id="669f3-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="669f3-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-479">tx_byte_pool_create</span></span>

<span data-ttu-id="669f3-480">Criar piscina de memória de bytes</span><span class="sxs-lookup"><span data-stu-id="669f3-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-481">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="669f3-482">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-482">Description</span></span>

<span data-ttu-id="669f3-483">Este serviço cria uma piscina de byte de memória na área especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="669f3-484">Inicialmente, a piscina é composta por basicamente um bloco livre muito grande.</span><span class="sxs-lookup"><span data-stu-id="669f3-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="669f3-485">No entanto, a piscina é dividida em blocos menores à medida que as dotações são feitas.</span><span class="sxs-lookup"><span data-stu-id="669f3-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-486">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-486">Parameters</span></span>

- <span data-ttu-id="669f3-487">**pool_ptr**: Ponteiro para um bloco de controlo da piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="669f3-488">**name_ptr**: Pontear o nome do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="669f3-489">**pool_start**: Endereço inicial do pool de memórias.</span><span class="sxs-lookup"><span data-stu-id="669f3-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="669f3-490">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="669f3-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="669f3-491">**pool_size**: Número total de bytes disponíveis para o pool de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-492">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-492">Return Values</span></span>

- <span data-ttu-id="669f3-493">**TX_SUCCESS**: (0x00) Criação de piscina de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="669f3-494">TX_POOL_ERROR: (0x02) Ponteiro do piscina de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="669f3-495">Ou o ponteiro é NULO ou a piscina já está criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="669f3-496">TX_PTR_ERROR: (0x03) Endereço inicial inválido da piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="669f3-497">TX_SIZE_ERROR: (0x05) O tamanho da piscina é inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="669f3-498">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-499">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-499">Allowed From</span></span>

<span data-ttu-id="669f3-500">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-501">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-501">Preemption Possible</span></span>

<span data-ttu-id="669f3-502">No</span><span class="sxs-lookup"><span data-stu-id="669f3-502">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-503">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-504">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-504">See Also</span></span>

- <span data-ttu-id="669f3-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-505">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="669f3-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="669f3-513">Apagar piscina de byte de memória</span><span class="sxs-lookup"><span data-stu-id="669f3-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-514">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-515">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-515">Description</span></span>

<span data-ttu-id="669f3-516">Este serviço elimina o conjunto de bytes de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="669f3-517">Todos os fios suspensos à espera de memória desta piscina são retomados e dado um estado de retorno TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="669f3-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-518">É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="669f3-519">Além disso, a aplicação deve impedir a utilização de um pool ou memória eliminados previamente atribuídos a partir do mesmo.</span><span class="sxs-lookup"><span data-stu-id="669f3-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-520">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-520">Parameters</span></span> 

- <span data-ttu-id="669f3-521">**pool_ptr**: Ponteiro para um conjunto de memórias previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-522">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-522">Return Values</span></span>

- <span data-ttu-id="669f3-523">**TX_SUCCESS**: (0x00) Eliminação bem sucedida do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="669f3-524">TX_POOL_ERROR: (0x02) Ponteiro do piscina de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="669f3-525">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-526">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-526">Allowed From</span></span>

<span data-ttu-id="669f3-527">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-528">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-528">Preemption Possible</span></span>

<span data-ttu-id="669f3-529">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-530">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-531">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-531">See Also</span></span>

- <span data-ttu-id="669f3-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-532">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="669f3-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="669f3-540">Recuperar informações sobre a piscina byte</span><span class="sxs-lookup"><span data-stu-id="669f3-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-541">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="669f3-542">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-542">Description</span></span>

<span data-ttu-id="669f3-543">Este serviço obtém informações sobre o byte de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-544">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-544">Parameters</span></span>

- <span data-ttu-id="669f3-545">**pool_ptr**: Ponteiro para piscina de memória previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="669f3-546">**nome**: Ponteiro para destino para o ponteiro para o nome da piscina byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="669f3-547">**disponível**: Ponteiro para destino para o número de bytes disponíveis na piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="669f3-548">**fragmentos**: Ponteiro para o destino para o número total de fragmentos de memória na piscina byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="669f3-549">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste byte pool.</span><span class="sxs-lookup"><span data-stu-id="669f3-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="669f3-550">**suspended_count**: Ponter para o destino para o número de fios atualmente suspensos nesta piscina byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="669f3-551">**next_pool**: Ponte para o destino para o ponteiro da próxima piscina byte criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-552">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-553">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-553">Return Values</span></span>

- <span data-ttu-id="669f3-554">**TX_SUCCESS:**(0x00) Recuperação de informações de piscinas bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="669f3-555">TX_POOL_ERROR: (0x02) Ponteiro do piscina de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-556">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-556">Allowed From</span></span>

<span data-ttu-id="669f3-557">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-558">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-558">Preemption Possible</span></span>

<span data-ttu-id="669f3-559">No</span><span class="sxs-lookup"><span data-stu-id="669f3-559">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-560">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-561">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-561">See Also</span></span>

- <span data-ttu-id="669f3-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-562">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="669f3-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="669f3-570">Obter informações sobre desempenho da piscina byte</span><span class="sxs-lookup"><span data-stu-id="669f3-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-572">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-572">Description</span></span>

<span data-ttu-id="669f3-573">Este serviço obtém informações de desempenho sobre a piscina de byte de memória especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-574">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-575">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-575">Parameters</span></span>

- <span data-ttu-id="669f3-576">**pool_ptr**: Ponteiro para piscina byte de memória previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="669f3-577">**atribuições**: Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-578">**lançamentos**: Ponteiro para o destino para o número de pedidos de libertação realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-579">**fragments_searched**: Ponte rumo ao destino para o número de fragmentos de memória internos pesquisados durante os pedidos de atribuição nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="669f3-580">**fusões**: Ponteiro para destino para o número de blocos de memória internos fundidos durante os pedidos de atribuição neste pool.</span><span class="sxs-lookup"><span data-stu-id="669f3-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="669f3-581">**divisões**: Ponteiro para o destino para o número de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="669f3-582">**suspensões**: Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="669f3-583">**intervalos :** Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-584">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-585">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-585">Return Values</span></span>

- <span data-ttu-id="669f3-586">TX_SUCCESS: (0x00) Desempenho da piscina byte bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="669f3-587">**TX_PTR_ERROR**: (0x03) Ponteiro de piscina inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="669f3-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-589">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-589">Allowed From</span></span>

<span data-ttu-id="669f3-590">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-591">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-592">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-592">See Also</span></span>

- <span data-ttu-id="669f3-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-593">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="669f3-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="669f3-601">Obtenha informações sobre o desempenho do sistema de piscinas byte</span><span class="sxs-lookup"><span data-stu-id="669f3-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-602">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="669f3-603">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-603">Description</span></span>

<span data-ttu-id="669f3-604">Este serviço obtém informações de desempenho sobre todas as piscinas de byte de memória no sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-605">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-606">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-606">Parameters</span></span>

- <span data-ttu-id="669f3-607">**atribuições**: Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-608">**lançamentos**: Ponteiro para o destino para o número de pedidos de libertação realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="669f3-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="669f3-609">**fragments_searched**: Ponte rumo ao destino para o número total de fragmentos de memória internos pesquisados durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="669f3-610">**fusões**: Ponteiro para destino para o número total de blocos de memória internos fundidos durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="669f3-611">**divisões**: Ponteiro para destino para o número total de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="669f3-612">**suspensões**: Ponteiro para o destino para o número total de suspensões de atribuição de fios em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="669f3-613">**intervalos :** Ponteiro para o destino para o número total de intervalos de suspensão atribuídos em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="669f3-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-614">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-615">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-615">Return Values</span></span>

- <span data-ttu-id="669f3-616">**TX_SUCCESS**: (0x00) Desempenho de byte de piscina bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="669f3-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-618">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-618">Allowed From</span></span>

<span data-ttu-id="669f3-619">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-620">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-621">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-621">See Also</span></span>

- <span data-ttu-id="669f3-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-622">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="669f3-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="669f3-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="669f3-630">Lista de suspensão de piscina de byte priorize</span><span class="sxs-lookup"><span data-stu-id="669f3-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-631">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-632">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-632">Description</span></span>

<span data-ttu-id="669f3-633">Este serviço coloca o fio de prioridade mais elevado suspenso para memória nesta piscina na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="669f3-634">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-635">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-635">Parameters</span></span> 

- <span data-ttu-id="669f3-636">**pool_ptr**: Ponteiro para um bloco de controlo da piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-637">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-637">Return Values</span></span>

- <span data-ttu-id="669f3-638">**TX_SUCCESS**: (0x00) Prioridades de memória bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="669f3-639">TX_POOL_ERROR: (0x02) Ponteiro do piscina de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-640">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-640">Allowed From</span></span>

<span data-ttu-id="669f3-641">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-642">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-642">Preemption Possible</span></span>

<span data-ttu-id="669f3-643">No</span><span class="sxs-lookup"><span data-stu-id="669f3-643">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-644">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-645">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-645">See Also</span></span>

- <span data-ttu-id="669f3-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-646">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="669f3-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="669f3-653">tx_byte_release</span></span>

<span data-ttu-id="669f3-654">Liberte bytes de volta à piscina de memória</span><span class="sxs-lookup"><span data-stu-id="669f3-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-655">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-656">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-656">Description</span></span>

<span data-ttu-id="669f3-657">Este serviço liberta uma área de memória previamente atribuída à sua piscina associada.</span><span class="sxs-lookup"><span data-stu-id="669f3-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="669f3-658">Se houver um ou mais fios suspensos à espera da memória desta piscina, cada fio suspenso é dado memória e retomado até que a memória esteja esgotada ou até que não haja mais fios suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="669f3-659">Este processo de atribuição de memória a fios suspensos começa sempre com o primeiro fio suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-660">A aplicação deve evitar a utilização da área de memória após a sua libertação.</span><span class="sxs-lookup"><span data-stu-id="669f3-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-661">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-661">Parameters</span></span>

- <span data-ttu-id="669f3-662">**memory_ptr**: Ponte para a área de memória previamente atribuída.</span><span class="sxs-lookup"><span data-stu-id="669f3-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-663">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-663">Return Values</span></span>

- <span data-ttu-id="669f3-664">**TX_SUCCESS**: (0x00) Libertação de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="669f3-665">TX_PTR_ERROR: (0x03) Ponteiro da área da memória inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="669f3-666">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-667">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-667">Allowed From</span></span>

<span data-ttu-id="669f3-668">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-669">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-669">Preemption Possible</span></span>

<span data-ttu-id="669f3-670">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-671">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-672">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-672">See Also</span></span>

- <span data-ttu-id="669f3-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="669f3-673">tx_byte_allocate</span></span>
- <span data-ttu-id="669f3-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="669f3-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="669f3-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="669f3-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="669f3-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="669f3-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="669f3-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-680">tx_event_flags_create</span></span>

<span data-ttu-id="669f3-681">Criar grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="669f3-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-682">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-683">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-683">Description</span></span>

<span data-ttu-id="669f3-684">Este serviço cria um grupo de 32 bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="669f3-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="669f3-685">Todas as 32 bandeiras do grupo estão inicializadas a zero.</span><span class="sxs-lookup"><span data-stu-id="669f3-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="669f3-686">Cada bandeira do evento é representada por um único pedaço.</span><span class="sxs-lookup"><span data-stu-id="669f3-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-687">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-687">Parameters</span></span>

- <span data-ttu-id="669f3-688">**group_ptr**: Ponteiro para um bloco de controlo de grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="669f3-689">**name_ptr**: Ponteiro para o nome do grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-690">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-690">Return Values</span></span>

- <span data-ttu-id="669f3-691">**TX_SUCCESS**: (0x00) Criação de grupo de eventos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="669f3-692">TX_GROUP_ERROR: (0x06) Ponteiro do grupo de eventos inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="669f3-693">Ou o ponteiro é NU OU o grupo de eventos já está criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="669f3-694">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-695">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-695">Allowed From</span></span>

<span data-ttu-id="669f3-696">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-697">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-697">Preemption Possible</span></span>

<span data-ttu-id="669f3-698">No</span><span class="sxs-lookup"><span data-stu-id="669f3-698">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-699">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-700">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-700">See Also</span></span>

- <span data-ttu-id="669f3-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-702">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-706">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="669f3-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-708">tx_event_flags_delete</span></span>

<span data-ttu-id="669f3-709">Apagar grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="669f3-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-710">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-711">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-711">Description</span></span>

<span data-ttu-id="669f3-712">Este serviço elimina o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="669f3-713">Todos os fios suspensos à espera de eventos deste grupo são retomados e dado um TX_DELETED estatuto de devolução.</span><span class="sxs-lookup"><span data-stu-id="669f3-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-714">O pedido deve garantir que um conjunto de chamadas notificantes para este grupo de bandeiras de evento seja concluído (ou desativado) antes de eliminar o grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="669f3-715">Além disso, a aplicação deve impedir a utilização futura de um grupo de bandeiras de eventos eliminado.</span><span class="sxs-lookup"><span data-stu-id="669f3-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-716">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-716">Parameters</span></span> 

- <span data-ttu-id="669f3-717">**group_ptr**: Pontear para um grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-718">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-718">Return Values</span></span>

- <span data-ttu-id="669f3-719">**TX_SUCCESS**: (0x00) Eliminação de bandeiras de eventos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="669f3-720">TX_GROUP_ERROR: (0x06) Inválido sinaliza ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="669f3-721">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-722">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-722">Allowed From</span></span>

<span data-ttu-id="669f3-723">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-724">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-724">Preemption Possible</span></span>

<span data-ttu-id="669f3-725">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-726">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-727">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-727">See Also</span></span>

- <span data-ttu-id="669f3-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-728">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-729">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-733">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="669f3-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-735">tx_event_flags_get</span></span>

<span data-ttu-id="669f3-736">Receba bandeiras de evento do grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="669f3-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-737">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-738">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-738">Description</span></span>

<span data-ttu-id="669f3-739">Este serviço recupera bandeiras de eventos do grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="669f3-740">Cada grupo de bandeiras de evento contém 32 bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="669f3-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="669f3-741">Cada bandeira é representada por um único pedaço.</span><span class="sxs-lookup"><span data-stu-id="669f3-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="669f3-742">Este serviço pode recuperar uma variedade de combinações de bandeira de evento, como selecionado pelos parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="669f3-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-743">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-743">Parameters</span></span>

- <span data-ttu-id="669f3-744">**group_ptr**: Pontear para um grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="669f3-745">**requested_flags:** variável não assinada de 32 bits que representa as bandeiras do evento solicitadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="669f3-746">**get_option**: Especifica se são necessárias todas ou quaisquer das bandeiras de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="669f3-747">Seguem-se as seguintes seleções válidas:</span><span class="sxs-lookup"><span data-stu-id="669f3-747">The following are valid selections:</span></span>
    - <span data-ttu-id="669f3-748">**TX_AND:**(0x02)</span><span class="sxs-lookup"><span data-stu-id="669f3-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="669f3-749">**TX_AND_CLEAR:**(0x03)</span><span class="sxs-lookup"><span data-stu-id="669f3-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="669f3-750">**TX_OR:**(0x00)</span><span class="sxs-lookup"><span data-stu-id="669f3-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="669f3-751">**TX_OR_CLEAR:**(0x01)</span><span class="sxs-lookup"><span data-stu-id="669f3-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="669f3-752">A seleção de TX_AND ou TX_AND_CLEAR especifica que todas as bandeiras do evento devem estar presentes no grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="669f3-753">Selecionar TX_OR ou TX_OR_CLEAR especifica que qualquer bandeira de evento é satisfatória.</span><span class="sxs-lookup"><span data-stu-id="669f3-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="669f3-754">As bandeiras do evento que satisfaçam o pedido são apuradas (definidas para zero) se forem especificadas TX_AND_CLEAR ou TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="669f3-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="669f3-755">**atual_flags_ptr**: Ponteiro para o destino de onde são colocadas as bandeiras do evento recuperado.</span><span class="sxs-lookup"><span data-stu-id="669f3-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="669f3-756">Note-se que as bandeiras obtidas podem conter bandeiras que não foram solicitadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="669f3-757">**wait_option**: Define como o serviço se comporta se as bandeiras de eventos selecionadas não estiverem definidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="669f3-758">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-759">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-760">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-761">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-762">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-763">Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="669f3-764">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que as bandeiras do evento estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="669f3-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="669f3-765">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda pelas bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-766">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-766">Return Values</span></span>

- <span data-ttu-id="669f3-767">**TX_SUCCESS**: (0x00) Bandeiras de eventos bem sucedidas recebem.</span><span class="sxs-lookup"><span data-stu-id="669f3-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="669f3-768">**TX_DELETED**: (0x01) O grupo de bandeiras de eventos foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-769">**TX_NO_EVENTS**: (0x07) O serviço não conseguiu obter os eventos especificados dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="669f3-770">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-771">TX_GROUP_ERROR: (0x06) Inválido sinaliza ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="669f3-772">TX_PTR_ERROR: (0x03) Ponteiro inválido para bandeiras de eventos reais.</span><span class="sxs-lookup"><span data-stu-id="669f3-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="669f3-773">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="669f3-774">TX_OPTION_ERROR: (0x08) Foi especificada a opção de opção de saída inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-775">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-775">Allowed From</span></span>

<span data-ttu-id="669f3-776">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-777">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-777">Preemption Possible</span></span>

<span data-ttu-id="669f3-778">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-779">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-780">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-780">See Also</span></span>

- <span data-ttu-id="669f3-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-781">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-786">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="669f3-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="669f3-789">Recuperar informações sobre o grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="669f3-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="669f3-791">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-791">Description</span></span>

<span data-ttu-id="669f3-792">Este serviço obtém informações sobre o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-793">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-793">Parameters</span></span>

- <span data-ttu-id="669f3-794">**group_ptr**: Ponteiro para um bloco de controlo de grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="669f3-795">**nome**: Ponteiro para o destino para o ponteiro para o nome do grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="669f3-796">**current_flags**: Ponteiro para o destino para as bandeiras atuais do grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="669f3-797">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="669f3-798">**suspended_count**: Ponteiro para o destino para o número de fios atualmente suspensos neste grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="669f3-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="669f3-799">**next_group**: Ponter para o destino para o ponteiro do próximo grupo de bandeiras de eventos criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-800">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-801">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-801">Return Values</span></span>

- <span data-ttu-id="669f3-802">**TX_SUCCESS**: (0x00) Recuperação de informação de grupo de eventos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="669f3-803">TX_GROUP_ERROR: (0x06) Ponteiro do grupo de eventos inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-804">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-804">Allowed From</span></span>

<span data-ttu-id="669f3-805">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-806">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-806">Preemption Possible</span></span>

<span data-ttu-id="669f3-807">No</span><span class="sxs-lookup"><span data-stu-id="669f3-807">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-808">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-809">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-809">See Also</span></span>

- <span data-ttu-id="669f3-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-810">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-812">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-815">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="669f3-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="669f3-818">Obtenha informações de desempenho do grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="669f3-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-819">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-820">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-820">Description</span></span>

<span data-ttu-id="669f3-821">Este serviço obtém informações de desempenho sobre o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-822">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-823">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-823">Parameters</span></span>

- <span data-ttu-id="669f3-824">**group_ptr**: Ponteiro para grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="669f3-825">**conjuntos**: Ponteiro para destino para o número de bandeiras de eventos definir pedidos realizados neste grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="669f3-826">**recebe:** Ponteiro para destino para o número de bandeiras de eventos obter pedidos realizados neste grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="669f3-827">**suspensões**: Ponteiro para o destino para o número de bandeiras de eventos thread obter suspensões neste grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="669f3-828">**intervalos :** Ponteiro para o destino para o número de bandeiras de eventos obter intervalos de suspensão neste grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-829">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-830">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-830">Return Values</span></span>

- <span data-ttu-id="669f3-831">**TX_SUCCESS**: (0x00) O desempenho do grupo de bandeiras de eventos bem sucedidos obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="669f3-832">**TX_PTR_ERROR**: (0x03) Inválido sinaliza o ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="669f3-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-834">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-834">Allowed From</span></span>

<span data-ttu-id="669f3-835">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-836">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-837">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-837">See Also</span></span>

- <span data-ttu-id="669f3-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-838">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-840">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-843">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="669f3-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="669f3-846">Recuperar informações do sistema de desempenho</span><span class="sxs-lookup"><span data-stu-id="669f3-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-847">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-848">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-848">Description</span></span>

<span data-ttu-id="669f3-849">Este serviço obtém informações de desempenho sobre todos os grupos de bandeiras de eventos no sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-850">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-851">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-851">Parameters</span></span>

- <span data-ttu-id="669f3-852">**conjuntos**: Ponteiro para destino para o número total de pedidos de conjunto de bandeiras de eventos realizados em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="669f3-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="669f3-853">**recebe:** Ponteiro para destino para o número total de bandeiras de eventos obter pedidos realizados em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="669f3-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="669f3-854">**suspensões**: Ponteiro para destino para o número total de bandeiras de eventos de fio obter suspensões em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="669f3-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="669f3-855">**intervalos :** Ponteiro para o destino para o número total de bandeiras de eventos obtém intervalos de suspensão em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="669f3-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-856">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-857">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-857">Return Values</span></span>

- <span data-ttu-id="669f3-858">**TX_SUCCESS**: (0x00) O desempenho do sistema de bandeiras de eventos bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="669f3-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-860">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-860">Allowed From</span></span>

<span data-ttu-id="669f3-861">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-862">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-863">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-863">See Also</span></span>

- <span data-ttu-id="669f3-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-864">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-866">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-869">tx_event_flags_set</span></span>
- <span data-ttu-id="669f3-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="669f3-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-871">tx_event_flags_set</span></span>

<span data-ttu-id="669f3-872">Definir bandeiras de evento em um grupo de bandeiras de evento</span><span class="sxs-lookup"><span data-stu-id="669f3-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-873">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="669f3-874">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-874">Description</span></span>

<span data-ttu-id="669f3-875">Este serviço define ou limpa bandeiras de eventos num grupo de bandeiras de eventos, dependendo da opção definida especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="669f3-876">Todos os fios suspensos cujo pedido de bandeiras de evento é agora preenchido são retomados.</span><span class="sxs-lookup"><span data-stu-id="669f3-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-877">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-877">Parameters</span></span>

- <span data-ttu-id="669f3-878">**group_ptr**: Ponteiro para o bloco de controlo de grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="669f3-879">**flags_to_set**: Especifica as bandeiras do evento para definir ou limpar com base na opção definida selecionada.</span><span class="sxs-lookup"><span data-stu-id="669f3-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="669f3-880">**set_option**: Especifica se as bandeiras do evento especificadas são ANDed ou ORed nas atuais bandeiras do grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="669f3-881">Seguem-se as seguintes seleções válidas:</span><span class="sxs-lookup"><span data-stu-id="669f3-881">The following are valid selections:</span></span>
    - <span data-ttu-id="669f3-882">**TX_AND:**(0x02)</span><span class="sxs-lookup"><span data-stu-id="669f3-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="669f3-883">**TX_OR**: (0x00) A seleção TX_AND especifica que as bandeiras de eventos especificadas são **especadas** nas atuais bandeiras do evento no grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="669f3-884">Esta opção é frequentemente usada para limpar bandeiras de eventos em um grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="669f3-885">Caso contrário, se TX_OR for especificado, as bandeiras de eventos especificadas são **ORed** com o evento atual no grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-886">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-886">Return Values</span></span>

- <span data-ttu-id="669f3-887">**TX_SUCCESS**: (0x00) Conjunto de bandeiras de eventos bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="669f3-888">TX_GROUP_ERROR: (0x06) Ponteiro inválido para grupo de bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="669f3-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="669f3-889">TX_OPTION_ERROR: (0x08) A opção de set inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-890">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-890">Allowed From</span></span>

<span data-ttu-id="669f3-891">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-892">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-892">Preemption Possible</span></span>

<span data-ttu-id="669f3-893">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-894">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-895">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-895">See Also</span></span>

- <span data-ttu-id="669f3-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-896">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-898">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="669f3-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="669f3-904">Notifique a aplicação quando as bandeiras do evento forem definidas</span><span class="sxs-lookup"><span data-stu-id="669f3-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-905">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="669f3-906">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-906">Description</span></span>

<span data-ttu-id="669f3-907">Este serviço regista uma função de chamada de chamada de notificação que é chamada sempre que uma ou mais bandeiras de eventos são definidas no grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="669f3-908">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-909">As bandeiras de evento da aplicação configuram a chamada de notificação não é permitida a chamada de API da ThreadX SMP com uma opção de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-910">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-910">Parameters</span></span> 
- <span data-ttu-id="669f3-911">**group_ptr**: Ponteiro para grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="669f3-912">**events_set_notify**: Ponteiro para as bandeiras de eventos da aplicação definir função de notificação.</span><span class="sxs-lookup"><span data-stu-id="669f3-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="669f3-913">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="669f3-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-914">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-914">Return Values</span></span>

- <span data-ttu-id="669f3-915">**TX_SUCCESS**: (0x00) Registo bem sucedido de bandeiras de eventos de notificação definida.</span><span class="sxs-lookup"><span data-stu-id="669f3-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="669f3-916">TX_GROUP_ERROR: (0x06) Inválido sinaliza ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="669f3-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="669f3-917">TX_FEATURE_NOT_ENABLED: (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-918">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-918">Allowed From</span></span>

<span data-ttu-id="669f3-919">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-920">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="669f3-921">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-921">See Also</span></span>

- <span data-ttu-id="669f3-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="669f3-922">tx_event_flags_create</span></span>
- <span data-ttu-id="669f3-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="669f3-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="669f3-924">tx_event_flags_get</span></span>
- <span data-ttu-id="669f3-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="669f3-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="669f3-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="669f3-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="669f3-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="669f3-929">tx_interrupt_control</span></span>

<span data-ttu-id="669f3-930">Ativar e desativar interrupções</span><span class="sxs-lookup"><span data-stu-id="669f3-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-931">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="669f3-932">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-932">Description</span></span>

<span data-ttu-id="669f3-933">Este serviço permite ou desativa as interrupções conforme especificado pelo parâmetro de entrada **new_posture**.</span><span class="sxs-lookup"><span data-stu-id="669f3-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-934">Se este serviço for chamado de um fio de aplicação, a postura de interrupção permanece parte do contexto desse fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="669f3-935">Por exemplo, se o fio chamar esta rotina para desativar as interrupções e, em seguida, suspender, quando é retomado, as interrupções são novamente desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="669f3-936">Este serviço não deve ser utilizado para permitir interrupções durante a inicialização!</span><span class="sxs-lookup"><span data-stu-id="669f3-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="669f3-937">Fazê-lo pode causar resultados imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="669f3-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-938">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-938">Parameters</span></span>

- <span data-ttu-id="669f3-939">**new_posture**: Este parâmetro especifica se as interrupções estão desativadas ou ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="669f3-940">Os valores legais incluem **TX_INT_DISABLE e TX_INT_ENABLE.**</span><span class="sxs-lookup"><span data-stu-id="669f3-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="669f3-941">Os valores reais para estes parâmetros são específicos do porto.</span><span class="sxs-lookup"><span data-stu-id="669f3-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="669f3-942">Além disso, algumas arquiteturas de processamento podem suportar posturas adicionais de interrupção de desativação.</span><span class="sxs-lookup"><span data-stu-id="669f3-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="669f3-943">Consulte as **_informaçõesreadme_threadx.txt_** fornecidas no disco de distribuição para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="669f3-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-944">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-944">Return Values</span></span>

- <span data-ttu-id="669f3-945">postura anterior: Este serviço devolve a postura de interrupção anterior ao chamador.</span><span class="sxs-lookup"><span data-stu-id="669f3-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="669f3-946">Isto permite que os utilizadores do serviço restaurem a postura anterior após as interrupções serem desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-947">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-947">Allowed From</span></span>

<span data-ttu-id="669f3-948">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-949">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-949">Preemption Possible</span></span>

<span data-ttu-id="669f3-950">No</span><span class="sxs-lookup"><span data-stu-id="669f3-950">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-951">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="669f3-952">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-952">See Also</span></span>

<span data-ttu-id="669f3-953">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="669f3-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-954">tx_mutex_create</span></span>

<span data-ttu-id="669f3-955">Criar mutex de exclusão mútua</span><span class="sxs-lookup"><span data-stu-id="669f3-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-956">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="669f3-957">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-957">Description</span></span>
    
<span data-ttu-id="669f3-958">Este serviço cria um mutex para exclusão mútua inter-roscada para proteção de recursos.</span><span class="sxs-lookup"><span data-stu-id="669f3-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-959">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-959">Parameters</span></span>

- <span data-ttu-id="669f3-960">**mutex_ptr**: Ponter para um bloco de controlo de mutantes.</span><span class="sxs-lookup"><span data-stu-id="669f3-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="669f3-961">**name_ptr**: Ponteiro para o nome do mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="669f3-962">**priority_inherit**: Especifica se este mutex suporta ou não a herança prioritária.</span><span class="sxs-lookup"><span data-stu-id="669f3-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="669f3-963">Se este valor for TX_INHERIT, então a herança prioritária é apoiada.</span><span class="sxs-lookup"><span data-stu-id="669f3-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="669f3-964">No entanto, se TX_NO_INHERIT for especificada, a herança prioritária não é apoiada por este mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-965">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-965">Return Values</span></span>

- <span data-ttu-id="669f3-966">**TX_SUCCESS**: (0x00) Criação mutex bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="669f3-967">TX_MUTEX_ERROR: (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="669f3-968">Ou o ponteiro é NULO ou o mutex já está criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="669f3-969">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="669f3-970">TX_INHERIT_ERROR: (0x1F) Parâmetro de herdade de prioridade inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-971">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-971">Allowed From</span></span>

<span data-ttu-id="669f3-972">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-973">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-973">Preemption Possible</span></span>

<span data-ttu-id="669f3-974">No</span><span class="sxs-lookup"><span data-stu-id="669f3-974">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-975">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-976">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-976">See Also</span></span>

- <span data-ttu-id="669f3-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-977">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-978">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="669f3-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-984">tx_mutex_delete</span></span>

<span data-ttu-id="669f3-985">Eliminar o mutex de exclusão mútua</span><span class="sxs-lookup"><span data-stu-id="669f3-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-986">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-987">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-987">Description</span></span>

<span data-ttu-id="669f3-988">Este serviço elimina o mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="669f3-989">Todos os fios suspensos à espera do mutex são retomados e dado um TX_DELETED estatuto de devolução.</span><span class="sxs-lookup"><span data-stu-id="669f3-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-990">É da responsabilidade da aplicação impedir a utilização de um mutex apagado.</span><span class="sxs-lookup"><span data-stu-id="669f3-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-991">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-991">Parameters</span></span>

- <span data-ttu-id="669f3-992">**mutex_ptr**: Ponteiro para um mutex previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-993">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-993">Return Values</span></span>

- <span data-ttu-id="669f3-994">**TX_SUCCESS**: (0x00) Eliminação mutex bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="669f3-995">TX_MUTEX_ERROR: (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="669f3-996">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-997">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-997">Allowed From</span></span>

<span data-ttu-id="669f3-998">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-999">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-999">Preemption Possible</span></span>

<span data-ttu-id="669f3-1000">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1001">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1002">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1002">See Also</span></span>

- <span data-ttu-id="669f3-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1003">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1004">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="669f3-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1010">tx_mutex_get</span></span>

<span data-ttu-id="669f3-1011">Obter a propriedade do mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1012">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-1013">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1013">Description</span></span>

<span data-ttu-id="669f3-1014">Este serviço tenta obter a propriedade exclusiva do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="669f3-1015">Se o fio de chamamento já possuir o mutex, um contador interno é incrementado e um estado de sucesso é devolvido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="669f3-1016">Se o mutex for propriedade de outro fio e este fio for de maior prioridade e a herança prioritária foi especificada na criação de mutex, a prioridade do fio de menor prioridade será temporariamente elevada à do fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1017">A prioridade do fio de menor prioridade que possui um mutex com prioridade nunca deve ser modificada por um fio externo durante a propriedade do mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1018">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1018">Parameters</span></span>

- <span data-ttu-id="669f3-1019">**mutex_ptr**: Ponteiro para um mutex previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="669f3-1020">**wait_option**: Define como o serviço se comporta se o mutex já é propriedade de outro fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="669f3-1021">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-1022">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-1023">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-1024">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-1025">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-1026">*Esta é a única opção válida se o serviço for chamado da Initialization.*</span><span class="sxs-lookup"><span data-stu-id="669f3-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="669f3-1027">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o mutex esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="669f3-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="669f3-1028">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pelo mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1029">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1029">Return Values</span></span>

- <span data-ttu-id="669f3-1030">**TX_SUCCESS:**(0x00) Operação mutex com sucesso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="669f3-1031">**TX_DELETED**: (0x01) A Mutex foi eliminada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-1032">**TX_NOT_AVAILABLE**: (0x1D) O serviço não foi capaz de obter a propriedade do mutex dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="669f3-1033">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-1034">TX_MUTEX_ERROR: (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="669f3-1035">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="669f3-1036">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1037">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1037">Allowed From</span></span>

<span data-ttu-id="669f3-1038">Inicialização e fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1039">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1039">Preemption Possible</span></span>

<span data-ttu-id="669f3-1040">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1041">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="669f3-1042">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1042">See Also</span></span>

- <span data-ttu-id="669f3-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1043">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="669f3-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="669f3-1051">Recuperar informações sobre o mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1052">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="669f3-1053">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1053">Description</span></span>

<span data-ttu-id="669f3-1054">Este serviço obtém informações do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1055">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1055">Parameters</span></span>

- <span data-ttu-id="669f3-1056">**mutex_ptr**: Ponteiro para bloco de controlo de mutantes.</span><span class="sxs-lookup"><span data-stu-id="669f3-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="669f3-1057">**nome**: Ponteiro para destino para o ponteiro para o nome do mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="669f3-1058">**contagem**: Ponteiro para destino para a contagem de propriedade do mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="669f3-1059">**proprietário**: Ponteiro para destino para o ponteiro do fio proprietário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="669f3-1060">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="669f3-1061">**suspended_count**: Ponter para o destino para o número de fios atualmente suspensos neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="669f3-1062">**next_mutex**: Ponte para o destino para o ponteiro do mutex criado seguinte.</span><span class="sxs-lookup"><span data-stu-id="669f3-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1063">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1064">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1064">Return Values</span></span>

- <span data-ttu-id="669f3-1065">**TX_SUCCESS**: (0x00) Recuperação bem sucedida de informação sobre mutantes.</span><span class="sxs-lookup"><span data-stu-id="669f3-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="669f3-1066">TX_MUTEX_ERROR: (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1067">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1067">Allowed From</span></span>

<span data-ttu-id="669f3-1068">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1069">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1069">Preemption Possible</span></span>

<span data-ttu-id="669f3-1070">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1071">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1072">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1072">See Also</span></span>

- <span data-ttu-id="669f3-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1073">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1075">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="669f3-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="669f3-1081">Obtenha informações sobre desempenho de mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1082">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="669f3-1083">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1083">Description</span></span>

<span data-ttu-id="669f3-1084">Este serviço recupera informações de desempenho sobre o mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1085">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1086">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1086">Parameters</span></span>

- <span data-ttu-id="669f3-1087">**mutex_ptr**: Ponteiro para o mutex previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="669f3-1088">**coloca:** Ponteiro para destino para o número de pedidos de colocação realizados neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="669f3-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="669f3-1090">**suspensões**: Ponteiro para o destino para o número de mutex thread obter suspensões neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="669f3-1091">**intervalos :** Ponte para o destino para o número de mutaex obter intervalos de suspensão neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="669f3-1092">**inversões**: Ponteiro para o destino para o número de inversões prioritárias de linha neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="669f3-1093">**heranças**: Ponteiro para o destino para o número de operações de herança prioritária de linha neste mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1094">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1095">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1095">Return Values</span></span>

- <span data-ttu-id="669f3-1096">**TX_SUCCESS**: (0x00) Desempenho mutex bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="669f3-1097">**TX_PTR_ERROR**: (0x03) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="669f3-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1099">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1099">Allowed From</span></span>

<span data-ttu-id="669f3-1100">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1101">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1102">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1102">See Also</span></span>

- <span data-ttu-id="669f3-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1103">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1105">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="669f3-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="669f3-1111">Obtenha informações sobre desempenho do sistema mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1112">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="669f3-1113">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1113">Description</span></span>

<span data-ttu-id="669f3-1114">Este serviço obtém informações de desempenho sobre todos os mutaxos do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1115">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_MUTEX_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1116">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1116">Parameters</span></span>

- <span data-ttu-id="669f3-1117">**colocações**: Ponteiro para destino para o número total de pedidos de colocação realizados em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="669f3-1118">**recebe:** Ponteiro para destino para o número total de pedidos de get realizados em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="669f3-1119">**suspensões**: Ponteiro para destino para o número total de mutantes de fio obter suspensões em todos os mutais.</span><span class="sxs-lookup"><span data-stu-id="669f3-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="669f3-1120">**intervalos :** Ponteiro para o destino para o número total de mutantes obtenha intervalos de suspensão em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="669f3-1121">**inversões**: Ponteiro para o destino para o número total de inversões prioritárias de linha em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="669f3-1122">**heranças**: Ponteiro para destino para o número total de operações de herança prioritária de fio em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1123">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1124">Return Values</span></span>

- <span data-ttu-id="669f3-1125">**TX_SUCCESS**: (0x00) O desempenho do sistema mutex com sucesso obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="669f3-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1127">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1127">Allowed From</span></span>

<span data-ttu-id="669f3-1128">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1130">See Also</span></span>

- <span data-ttu-id="669f3-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1131">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1133">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="669f3-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="669f3-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="669f3-1139">Priorizar lista de suspensão de mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1140">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1141">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1141">Description</span></span>

<span data-ttu-id="669f3-1142">Este serviço coloca o fio de prioridade mais elevado suspenso para a propriedade do mutex na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="669f3-1143">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1144">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1144">Parameters</span></span> 

- <span data-ttu-id="669f3-1145">**mutex_ptr**: Ponte para o mutex previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1146">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1146">Return Values</span></span>

- <span data-ttu-id="669f3-1147">**TX_SUCCESS**: (0x00) Prioridades de mutex bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="669f3-1148">TX_MUTEX_ERROR: (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1149">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1149">Allowed From</span></span>

<span data-ttu-id="669f3-1150">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1151">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1151">Preemption Possible</span></span>

<span data-ttu-id="669f3-1152">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1154">See Also</span></span>

- <span data-ttu-id="669f3-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1155">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1157">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="669f3-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1162">tx_mutex_put</span></span>

<span data-ttu-id="669f3-1163">Libertar a propriedade do mutex</span><span class="sxs-lookup"><span data-stu-id="669f3-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1164">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1165">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1165">Description</span></span>

<span data-ttu-id="669f3-1166">Este serviço desvaloriza a contagem de propriedade do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="669f3-1167">Se a contagem de propriedade for zero, o mutex é disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1168">Se a herança prioritária foi selecionada durante a criação de mutaxos, a prioridade do fio de libertação será restaurada à prioridade que tinha quando obteve inicialmente a propriedade do mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="669f3-1169">Quaisquer outras alterações prioritárias efetuadas no fio de libertação durante a propriedade do mutex podem ser desfeitas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1170">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1170">Parameters</span></span>

- <span data-ttu-id="669f3-1171">**mutex_ptr**: Ponte para o mutex previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1172">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1172">Return Values</span></span>

- <span data-ttu-id="669f3-1173">**TX_SUCCESS**: (0x00) Libertação de mutex bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="669f3-1174">**TX_NOT_OWNED**: (0x1E) A Mutex não é propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="669f3-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="669f3-1175">TX_MUTEX_ERROR: (0x1C) Ponteiro inválido para mutex.</span><span class="sxs-lookup"><span data-stu-id="669f3-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="669f3-1176">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1177">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1177">Allowed From</span></span>

<span data-ttu-id="669f3-1178">Inicialização e fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1179">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1179">Preemption Possible</span></span>

<span data-ttu-id="669f3-1180">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1181">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1182">See Also</span></span>

- <span data-ttu-id="669f3-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1183">tx_mutex_create</span></span>
- <span data-ttu-id="669f3-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="669f3-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1185">tx_mutex_get</span></span>
- <span data-ttu-id="669f3-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="669f3-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="669f3-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="669f3-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1190">tx_queue_create</span></span>

<span data-ttu-id="669f3-1191">Criar fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="669f3-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1192">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="669f3-1193">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1193">Description</span></span>

<span data-ttu-id="669f3-1194">Este serviço cria uma fila de mensagens que é normalmente usada para comunicação interligada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="669f3-1195">O número total de mensagens é calculado a partir do tamanho da mensagem especificada e do número total de bytes na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1196">Se o número total de bytes especificados na área de memória da fila não for igualmente divisível pelo tamanho da mensagem especificada, os bytes restantes na área da memória não são utilizados.</span><span class="sxs-lookup"><span data-stu-id="669f3-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1197">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1197">Parameters</span></span>

- <span data-ttu-id="669f3-1198">**queue_ptr**: Pontear para um bloco de controlo da fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="669f3-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="669f3-1199">**name_ptr**: Pontear o nome da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="669f3-1200">**message_size**: Especifica o tamanho de cada mensagem na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="669f3-1201">Os tamanhos da mensagem variam de 1 32 bits de palavras a 16 palavras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="669f3-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="669f3-1202">As opções de tamanho de mensagem válidas são valores numéricos de 1 a 16, inclusive.</span><span class="sxs-lookup"><span data-stu-id="669f3-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="669f3-1203">**queue_start**: Endereço inicial da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="669f3-1204">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="669f3-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="669f3-1205">**queue_size**: Número total de bytes disponíveis para a fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1206">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1206">Return Values</span></span>

- <span data-ttu-id="669f3-1207">**TX_SUCCESS**: (0x00) Criação de fila de mensagens bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="669f3-1208">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="669f3-1209">Ou o ponteiro é NU OU a fila já está criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="669f3-1210">TX_PTR_ERROR: (0x03) Endereço inicial inválido da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="669f3-1211">TX_SIZE_ERROR: (0x05) O tamanho da fila da mensagem é inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="669f3-1212">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1213">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1213">Allowed From</span></span>

<span data-ttu-id="669f3-1214">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1215">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1215">Preemption Possible</span></span>

<span data-ttu-id="669f3-1216">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1217">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1218">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1218">See Also</span></span>

- <span data-ttu-id="669f3-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1219">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1220">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1226">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1227">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="669f3-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1229">tx_queue_delete</span></span>

<span data-ttu-id="669f3-1230">Apagar fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="669f3-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1231">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1232">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1232">Description</span></span>

<span data-ttu-id="669f3-1233">Este serviço elimina a fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="669f3-1234">Todos os fios suspensos à espera de uma mensagem desta fila são retomados e dado um estado de devolução TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="669f3-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1235">O pedido deve certificar-se de que qualquer pedido de notificação para esta fila está concluído (ou desativado) antes de apagar a fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="669f3-1236">Além disso, a aplicação deve impedir qualquer utilização futura de uma fila eliminada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="669f3-1237">*É também da responsabilidade da aplicação gerir a área de memória associada à fila, que está disponível após a conclusão deste serviço.*</span><span class="sxs-lookup"><span data-stu-id="669f3-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1238">Parameters</span></span> 

- <span data-ttu-id="669f3-1239">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1240">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1240">Return Values</span></span>

- <span data-ttu-id="669f3-1241">**TX_SUCCESS**: (0x00) Eliminação bem sucedida da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="669f3-1242">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="669f3-1243">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1244">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1244">Allowed From</span></span>

<span data-ttu-id="669f3-1245">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1246">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1246">Preemption Possible</span></span>

<span data-ttu-id="669f3-1247">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1248">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1249">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1249">See Also</span></span>

- <span data-ttu-id="669f3-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1250">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1251">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1257">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1258">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="669f3-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1260">tx_queue_flush</span></span>

<span data-ttu-id="669f3-1261">Mensagens vazias na fila da mensagem</span><span class="sxs-lookup"><span data-stu-id="669f3-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1262">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1263">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1263">Description</span></span>

<span data-ttu-id="669f3-1264">Este serviço elimina todas as mensagens armazenadas na fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="669f3-1265">Se a fila estiver cheia, as mensagens de todos os fios suspensos são descartadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="669f3-1266">Cada fio suspenso é então retomado com um estado de retorno que indica que o envio da mensagem foi bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="669f3-1267">Se a fila estiver vazia, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1268">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1268">Parameters</span></span> 

- <span data-ttu-id="669f3-1269">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1270">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1270">Return Values</span></span>

- <span data-ttu-id="669f3-1271">**TX_SUCCESS**: (0x00) Flush de fila de mensagens bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="669f3-1272">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1273">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1273">Allowed From</span></span>

<span data-ttu-id="669f3-1274">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1275">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1275">Preemption Possible</span></span>

<span data-ttu-id="669f3-1276">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1277">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1278">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1278">See Also</span></span>

- <span data-ttu-id="669f3-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1279">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1280">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1286">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1287">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="669f3-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1289">tx_queue_front_send</span></span>

<span data-ttu-id="669f3-1290">Enviar mensagem para a frente da fila</span><span class="sxs-lookup"><span data-stu-id="669f3-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1291">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-1292">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1292">Description</span></span>

<span data-ttu-id="669f3-1293">Este serviço envia uma mensagem para a localização frontal da fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="669f3-1294">A mensagem é **copiada** para a frente da fila a partir da área de memória especificada pelo ponteiro de origem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1295">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1295">Parameters</span></span>

- <span data-ttu-id="669f3-1296">**queue_ptr**: Pontear para um bloco de controlo da fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="669f3-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="669f3-1297">**source_ptr**: Ponte para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="669f3-1298">**wait_option**: Define como o serviço se comporta se a fila da mensagem estiver cheia.</span><span class="sxs-lookup"><span data-stu-id="669f3-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="669f3-1299">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-1300">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-1301">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-1302">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-1303">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-1304">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="669f3-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="669f3-1305">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="669f3-1306">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera por espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1307">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1307">Return Values</span></span>

- <span data-ttu-id="669f3-1308">**TX_SUCCESS:**(0x00) Envio bem sucedido de mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="669f3-1309">**TX_DELETED**: (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-1310">**TX_QUEUE_FULL**: (0x0B) O serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="669f3-1311">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-1312">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="669f3-1313">TX_PTR_ERROR: (0x03) Ponteiro de origem inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="669f3-1314">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1315">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1315">Allowed From</span></span>

<span data-ttu-id="669f3-1316">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1317">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1317">Preemption Possible</span></span>

<span data-ttu-id="669f3-1318">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1319">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1320">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1320">See Also</span></span>

- <span data-ttu-id="669f3-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1321">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1322">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1323">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1328">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1329">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="669f3-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1331">tx_queue_info_get</span></span>

<span data-ttu-id="669f3-1332">Recuperar informações sobre a fila</span><span class="sxs-lookup"><span data-stu-id="669f3-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1333">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="669f3-1334">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1334">Description</span></span>

<span data-ttu-id="669f3-1335">Este serviço obtém informações sobre a fila de mensagens especificadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1336">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1336">Parameters</span></span>

- <span data-ttu-id="669f3-1337">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="669f3-1338">**nome**: Ponteiro para destino para o ponteiro para o nome da fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="669f3-1339">**encadeado**: Ponteiro para destino para o número de mensagens atualmente na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="669f3-1340">**available_storage**: Ponte para o destino para o número de mensagens para as seguintes.</span><span class="sxs-lookup"><span data-stu-id="669f3-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="669f3-1341">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão desta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="669f3-1342">**suspended_count**: Ponter para o destino para o número de fios atualmente suspensos nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="669f3-1343">**next_queue**: Ponte para o destino para o ponteiro da próxima fila criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1344">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1345">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1345">Return Values</span></span>

- <span data-ttu-id="669f3-1346">**TX_SUCCESS:**(0x00) Obter informações de fila bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="669f3-1347">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1348">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1348">Allowed From</span></span>

<span data-ttu-id="669f3-1349">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1350">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1350">Preemption Possible</span></span>

<span data-ttu-id="669f3-1351">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1352">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1353">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1353">See Also</span></span>

- <span data-ttu-id="669f3-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1354">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1355">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1356">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1361">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1362">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="669f3-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="669f3-1365">Obtenha informações sobre desempenho da fila</span><span class="sxs-lookup"><span data-stu-id="669f3-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1366">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-1367">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1367">Description</span></span>

<span data-ttu-id="669f3-1368">Este serviço recupera informações de desempenho sobre a fila especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1369">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_QUEUE_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1370">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1370">Parameters</span></span>

- <span data-ttu-id="669f3-1371">**queue_ptr**: Ponteiro para fila previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="669f3-1372">**messages_sent**: Ponte para o destino para o número de pedidos de envio realizados nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="669f3-1373">**messages_received**: Ponteiro para o destino para o número de pedidos de receção realizados nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="669f3-1374">**empty_suspensions**: Ponte para o destino para o número de suspensões vazias de fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="669f3-1375">**full_suspensions**: Ponte para o destino para o número de suspensões completas da fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="669f3-1376">**full_errors**: Ponte para o destino para o número de erros completos da fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="669f3-1377">**intervalos :** Ponte para o destino para o número de intervalos de suspensão de fio nesta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1378">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1379">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1379">Return Values</span></span>

- <span data-ttu-id="669f3-1380">**TX_SUCCESS**: (0x00) Desempenho de fila bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="669f3-1381">**TX_PTR_ERROR**: (0x03) Ponteiro de fila inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="669f3-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1383">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1383">Allowed From</span></span>

<span data-ttu-id="669f3-1384">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1385">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1386">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1386">See Also</span></span>

- <span data-ttu-id="669f3-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1387">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1388">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1389">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1394">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1395">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="669f3-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="669f3-1398">Obtenha informações sobre desempenho do sistema de fila</span><span class="sxs-lookup"><span data-stu-id="669f3-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1399">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-1400">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1400">Description</span></span>

<span data-ttu-id="669f3-1401">Este serviço obtém informações de desempenho sobre todas as filas do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1402">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_QUEUE_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1403">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1403">Parameters</span></span>

- <span data-ttu-id="669f3-1404">**messages_sent**: Ponter para o destino para o número total de pedidos de envio realizados em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="669f3-1405">**messages_received**: Ponteiro para o destino para o número total de pedidos de receção realizados em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="669f3-1406">**empty_suspensions**: Ponte para o destino para o número total de suspensões vazias de fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="669f3-1407">**full_suspensions**: Ponte para o destino para o número total de suspensões completas da fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="669f3-1408">**full_errors**: Ponte para o destino para o número total de erros completos da fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="669f3-1409">**intervalos :** Ponte para o destino para o número total de intervalos de suspensão de fio em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1410">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1411">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1411">Return Values</span></span>

- <span data-ttu-id="669f3-1412">**TX_SUCCESS**: (0x00) O desempenho do sistema de fila bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="669f3-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1414">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1414">Allowed From</span></span>

<span data-ttu-id="669f3-1415">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1416">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1417">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1417">See Also</span></span>

- <span data-ttu-id="669f3-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1418">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1419">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1420">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1425">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1426">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="669f3-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="669f3-1429">Priorizar lista de suspensão de filas</span><span class="sxs-lookup"><span data-stu-id="669f3-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1430">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="669f3-1431">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1431">Description</span></span>

<span data-ttu-id="669f3-1432">Este serviço coloca o fio de prioridade mais elevado suspenso para uma mensagem (ou para colocar uma mensagem) nesta fila na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="669f3-1433">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1434">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1434">Parameters</span></span> 

- <span data-ttu-id="669f3-1435">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1436">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1436">Return Values</span></span>

- <span data-ttu-id="669f3-1437">**TX_SUCCESS**: (0x00) Prioridades de fila bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="669f3-1438">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1439">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1439">Allowed From</span></span>

<span data-ttu-id="669f3-1440">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1441">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1441">Preemption Possible</span></span>

<span data-ttu-id="669f3-1442">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1443">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1444">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1444">See Also</span></span>

- <span data-ttu-id="669f3-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1445">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1446">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1447">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1452">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1453">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="669f3-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1455">tx_queue_receive</span></span>

<span data-ttu-id="669f3-1456">Receba mensagem da fila da mensagem</span><span class="sxs-lookup"><span data-stu-id="669f3-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1457">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-1458">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1458">Description</span></span>

<span data-ttu-id="669f3-1459">Este serviço recupera uma mensagem da fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="669f3-1460">A mensagem recuperada é **copiada** da fila para a área de memória especificada pelo ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="669f3-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="669f3-1461">Essa mensagem é então removida da fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="669f3-1462">A área de memória de destino especificada deve ser suficientemente grande para conter a mensagem; ou seja, o destino da mensagem apontada por **destination_ptr** deve ser pelo menos tão grande quanto o tamanho da mensagem para esta fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="669f3-1463">Caso contrário, se o destino não for suficientemente grande, a corrupção da memória ocorre na seguinte área de memória.</span><span class="sxs-lookup"><span data-stu-id="669f3-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1464">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1464">Parameters</span></span>

- <span data-ttu-id="669f3-1465">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="669f3-1466">**destination_ptr:** Local de onde copiar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="669f3-1467">**wait_option**: Define como o serviço se comporta se a fila da mensagem estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="669f3-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="669f3-1468">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-1469">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="669f3-1470">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="669f3-1471">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-1472">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-1473">Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="669f3-1474">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que uma mensagem esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="669f3-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="669f3-1475">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1476">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1476">Return Values</span></span>

- <span data-ttu-id="669f3-1477">**TX_SUCCESS**: (0x00) Recuperação bem sucedida da mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="669f3-1478">**TX_DELETED**: (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-1479">**TX_QUEUE_EMPTY**: (0x0A) O serviço não conseguiu recuperar uma mensagem porque a fila estava vazia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="669f3-1480">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-1481">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="669f3-1482">TX_PTR_ERROR: (0x03) Ponteiro de destino inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="669f3-1483">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1484">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1484">Allowed From</span></span>

<span data-ttu-id="669f3-1485">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1486">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1486">Preemption Possible</span></span>

<span data-ttu-id="669f3-1487">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1488">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1489">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1489">See Also</span></span>

- <span data-ttu-id="669f3-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1490">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1491">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1492">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1498">tx_queue_send</span></span>
- <span data-ttu-id="669f3-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="669f3-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1500">tx_queue_send</span></span>

<span data-ttu-id="669f3-1501">Enviar mensagem para a fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="669f3-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="669f3-1503">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1503">Description</span></span>

<span data-ttu-id="669f3-1504">Este serviço envia uma mensagem para a fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="669f3-1505">A mensagem enviada é **copiada** para a fila a partir da área de memória especificada pelo ponteiro de origem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1506">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1506">Parameters</span></span>

- <span data-ttu-id="669f3-1507">**queue_ptr**: Pontear para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="669f3-1508">**source_ptr**: Ponte para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="669f3-1509">**wait_option**: Define como o serviço se comporta se a fila da mensagem estiver cheia.</span><span class="sxs-lookup"><span data-stu-id="669f3-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="669f3-1510">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-1511">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-1512">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-1513">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-1514">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-1515">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="669f3-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="669f3-1516">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="669f3-1517">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera por espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1518">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1518">Return Values</span></span>

- <span data-ttu-id="669f3-1519">**TX_SUCCESS:**(0x00) Envio bem sucedido de mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="669f3-1520">**TX_DELETED**: (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-1521">**TX_QUEUE_FULL**: (0x0B) O serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="669f3-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="669f3-1522">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-1523">TX_QUEUE_ERROR: (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="669f3-1524">TX_PTR_ERROR: (0x03) Ponteiro de origem inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="669f3-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="669f3-1525">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="669f3-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1526">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1526">Allowed From</span></span>

<span data-ttu-id="669f3-1527">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1528">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1528">Preemption Possible</span></span>

<span data-ttu-id="669f3-1529">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1530">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1531">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1531">See Also</span></span>

- <span data-ttu-id="669f3-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1532">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1533">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1534">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1540">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="669f3-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="669f3-1543">Notifique o pedido quando a mensagem é enviada para a fila</span><span class="sxs-lookup"><span data-stu-id="669f3-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1544">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="669f3-1545">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1545">Description</span></span>

<span data-ttu-id="669f3-1546">Este serviço regista uma função de chamada de notificação que é chamada sempre que uma mensagem é enviada para a fila especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="669f3-1547">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-1548">A chamada de notificação de envio de fila da aplicação não está autorizada a ligar para qualquer API ThreadX SMP com uma opção de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1549">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1549">Parameters</span></span> 

- <span data-ttu-id="669f3-1550">**queue_ptr**: Ponteiro para fila previamente criada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="669f3-1551">**queue_send_notify**: Ponteiro para a função de notificação de envio de fila da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="669f3-1552">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1553">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1553">Return Values</span></span>

- <span data-ttu-id="669f3-1554">**TX_SUCCESS:**(0x00) Registo bem sucedido da notificação de envio de fila.</span><span class="sxs-lookup"><span data-stu-id="669f3-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="669f3-1555">TX_QUEUE_ERROR: (0x09) Ponteiro de fila inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="669f3-1556">TX_FEATURE_NOT_ENABLED: (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1557">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1557">Allowed From</span></span>

<span data-ttu-id="669f3-1558">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1559">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a><span data-ttu-id="669f3-1560">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1560">See Also</span></span>

- <span data-ttu-id="669f3-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1561">tx_queue_create</span></span>
- <span data-ttu-id="669f3-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1562">tx_queue_delete</span></span>
- <span data-ttu-id="669f3-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="669f3-1563">tx_queue_flush</span></span>
- <span data-ttu-id="669f3-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="669f3-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="669f3-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="669f3-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="669f3-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="669f3-1569">tx_queue_receive</span></span>
- <span data-ttu-id="669f3-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="669f3-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="669f3-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="669f3-1572">Coloque um caso na contagem de semáforos com teto</span><span class="sxs-lookup"><span data-stu-id="669f3-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1573">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="669f3-1574">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1574">Description</span></span>

<span data-ttu-id="669f3-1575">Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um.</span><span class="sxs-lookup"><span data-stu-id="669f3-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="669f3-1576">Se o valor atual do semáforo de contagem for superior ou igual ao teto especificado, o caso não será colocado e será devolvido um erro de TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="669f3-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1577">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1577">Parameters</span></span> 

- <span data-ttu-id="669f3-1578">**semaphore_ptr**: Ponteiro para semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="669f3-1579">**teto**: Limite máximo permitido para o semáforo (valores válidos variam de 1 a 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="669f3-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1580">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1580">Return Values</span></span>

- <span data-ttu-id="669f3-1581">**TX_SUCCESS:**(0x00) Teto de semáforo bem sucedido colocado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="669f3-1582">**TX_CEILING_EXCEEDED**: (0x21) O pedido de colocação excede o limite máximo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="669f3-1583">TX_INVALID_CEILING: (0x22) Foi fornecido um valor inválido de zero para o teto.</span><span class="sxs-lookup"><span data-stu-id="669f3-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="669f3-1584">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1585">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1585">Allowed From</span></span>

<span data-ttu-id="669f3-1586">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1587">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="669f3-1588">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1588">See Also</span></span>

- <span data-ttu-id="669f3-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="669f3-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1598">tx_semaphore_create</span></span>

<span data-ttu-id="669f3-1599">Criar semáforo de contagem</span><span class="sxs-lookup"><span data-stu-id="669f3-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1600">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="669f3-1601">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1601">Description</span></span>

<span data-ttu-id="669f3-1602">Este serviço cria um semáforo de contagem para sincronização inter-thread.</span><span class="sxs-lookup"><span data-stu-id="669f3-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="669f3-1603">A contagem inicial de semáforos é especificada como um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1604">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1604">Parameters</span></span> 

- <span data-ttu-id="669f3-1605">**semaphore_ptr**: Ponter para um bloco de controlo de semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="669f3-1606">**name_ptr**: Ponte para o nome do semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="669f3-1607">**initial_count**: Especifica a contagem inicial para este semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="669f3-1608">Os valores legais vão de 0x00000000 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1609">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1609">Return Values</span></span>

- <span data-ttu-id="669f3-1610">**TX_SUCCESS:**(0x00) Criação de semáforos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="669f3-1611">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="669f3-1612">Ou o ponteiro é NU OU o semáforo já está criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="669f3-1613">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1614">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1614">Allowed From</span></span>

<span data-ttu-id="669f3-1615">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1616">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1616">Preemption Possible</span></span>

<span data-ttu-id="669f3-1617">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1618">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1619">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1619">See Also</span></span>

- <span data-ttu-id="669f3-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="669f3-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="669f3-1630">Eliminar semáforo de contagem</span><span class="sxs-lookup"><span data-stu-id="669f3-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1631">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1632">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1632">Description</span></span>

<span data-ttu-id="669f3-1633">Este serviço elimina o semáforo de contagem especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="669f3-1634">Todos os fios suspensos à espera de uma instância de semáforo são retomados e dado um estado de retorno TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="669f3-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1635">O pedido deve assegurar-se de que uma chamada de notificação colocada para este semáforo seja concluída (ou desativada) antes de eliminar o semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="669f3-1636">Além disso, o pedido deve impedir qualquer utilização futura de um semáforo eliminado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1637">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1637">Parameters</span></span> 

- <span data-ttu-id="669f3-1638">**semaphore_ptr**: Ponte para um semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1639">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1639">Return Values</span></span>

- <span data-ttu-id="669f3-1640">**TX_SUCCESS**: (0x00) Eliminação de semáforos de contagem bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="669f3-1641">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="669f3-1642">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1643">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1643">Allowed From</span></span>

<span data-ttu-id="669f3-1644">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1645">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1645">Preemption Possible</span></span>

<span data-ttu-id="669f3-1646">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1647">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1648">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1648">See Also</span></span>

- <span data-ttu-id="669f3-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="669f3-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1658">tx_semaphore_get</span></span>

<span data-ttu-id="669f3-1659">Obtenha o exemplo da contagem de semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1660">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="669f3-1661">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1661">Description</span></span>

<span data-ttu-id="669f3-1662">Este serviço recupera uma instância (uma contagem única) do semáforo de contagem especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="669f3-1663">Como resultado, a contagem de semáforos especificados é diminuída por um.</span><span class="sxs-lookup"><span data-stu-id="669f3-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1664">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1664">Parameters</span></span>

- <span data-ttu-id="669f3-1665">**semaphore_ptr**: Ponteiro para um semáforo de contagem previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="669f3-1666">**wait_option**: Define como o serviço se comporta se não houver casos do semáforo disponível; ou seja, a contagem de semáforos é zero.</span><span class="sxs-lookup"><span data-stu-id="669f3-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="669f3-1667">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="669f3-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="669f3-1668">**TX_NO_WAIT:**(0x00000000)</span><span class="sxs-lookup"><span data-stu-id="669f3-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="669f3-1669">**TX_WAIT_FOREVER:**(0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="669f3-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="669f3-1670">valor de tempo limite: (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="669f3-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="669f3-1671">A seleção TX_NO_WAIT resulta numa devolução imediata deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="669f3-1672">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="669f3-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="669f3-1673">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que esteja disponível uma instância de semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="669f3-1674">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda por uma instância de semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1675">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1675">Return Values</span></span>

- <span data-ttu-id="669f3-1676">**TX_SUCCESS**: (0x00) Recuperação bem sucedida de um caso de semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="669f3-1677">**TX_DELETED**: (0x01) O semáforo de contagem foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="669f3-1678">**TX_NO_INSTANCE**: (0x0D) O serviço não conseguiu recuperar um caso do semáforo de contagem (a contagem de semáforos é zero dentro do tempo especificado para esperar).</span><span class="sxs-lookup"><span data-stu-id="669f3-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="669f3-1679">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-1680">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="669f3-1681">TX_WAIT_ERROR: (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1682">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1682">Allowed From</span></span>

<span data-ttu-id="669f3-1683">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1684">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1684">Preemption Possible</span></span>

<span data-ttu-id="669f3-1685">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1686">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1687">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1687">See Also</span></span>

- <span data-ttu-id="669f3-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="669f3-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="669f3-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="669f3-1697">Recuperar informações sobre semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1698">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="669f3-1699">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1699">Description</span></span>

<span data-ttu-id="669f3-1700">Este serviço obtém informações sobre o semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1701">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1701">Parameters</span></span>

- <span data-ttu-id="669f3-1702">**semaphore_ptr**: Ponteiro para o bloco de controlo de semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="669f3-1703">**nome**: Ponteiro para destino para o ponteiro para o nome do semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="669f3-1704">**current_value**: Ponte para o destino para a contagem atual do semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="669f3-1705">**first_suspended**: Ponter para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="669f3-1706">**suspended_count**: Ponter para o destino para o número de fios atualmente suspensos neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="669f3-1707">**next_semaphore**: Ponte para o destino para o ponteiro do próximo semáforo criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1708">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1709">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1709">Return Values</span></span>

- <span data-ttu-id="669f3-1710">**TX_SUCCESS**: (0x00) Recuperação de informações de semáforos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="669f3-1711">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1712">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1712">Allowed From</span></span>

<span data-ttu-id="669f3-1713">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1714">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1714">Preemption Possible</span></span>

<span data-ttu-id="669f3-1715">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1716">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1717">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1717">See Also</span></span>

- <span data-ttu-id="669f3-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="669f3-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="669f3-1728">Obtenha informações de desempenho de semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1729">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-1730">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1730">Description</span></span>

<span data-ttu-id="669f3-1731">Este serviço recupera informações de desempenho sobre o semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-1732">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1733">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1733">Parameters</span></span>

- <span data-ttu-id="669f3-1734">**semaphore_ptr**: Ponteiro para semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="669f3-1735">**coloca:** Ponteiro para destino para o número de pedidos de colocação realizados neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="669f3-1736">**recebe:** Ponteiro para destino para o número de pedidos de get realizados neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="669f3-1737">**suspensões**: Ponteiro para o destino para o número de suspensões de rosca neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="669f3-1738">**intervalos :** Ponte para o destino para o número de intervalos de suspensão de fio neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1739">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1740">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1740">Return Values</span></span>

- <span data-ttu-id="669f3-1741">**TX_SUCCESS**: (0x00) Desempenho do semáforo bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="669f3-1742">**TX_PTR_ERROR**: (0x03) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="669f3-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1744">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1744">Allowed From</span></span>

<span data-ttu-id="669f3-1745">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1746">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1747">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1747">See Also</span></span>

- <span data-ttu-id="669f3-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="669f3-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="669f3-1758">Obtenha informações sobre desempenho do sistema de semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1759">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="669f3-1760">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1760">Description</span></span>

<span data-ttu-id="669f3-1761">Este serviço obtém informações de desempenho sobre todos os semáforos do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1762">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1763">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1763">Parameters</span></span>

- <span data-ttu-id="669f3-1764">**colocações**: Ponteiro para destino para o número total de pedidos de colocação realizados em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="669f3-1765">**recebe:** Ponteiro para destino para o número total de pedidos de get realizados em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="669f3-1766">**suspensões**: Ponteiro para o destino para o número total de suspensões de roscas em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="669f3-1767">**intervalos :** Ponte para o destino para o número total de intervalos de suspensão de fio em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1768">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1769">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1769">Return Values</span></span>

- <span data-ttu-id="669f3-1770">TX_SUCCESS: (0x00) O desempenho do sistema de semáforos bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="669f3-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1772">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1772">Allowed From</span></span>

<span data-ttu-id="669f3-1773">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1774">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1775">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1775">See Also</span></span>

- <span data-ttu-id="669f3-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="669f3-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="669f3-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="669f3-1786">Priorizar lista de suspensão de semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1787">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1788">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1788">Description</span></span>

<span data-ttu-id="669f3-1789">Este serviço coloca o fio de prioridade mais elevado suspenso por uma instância do semáforo na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="669f3-1790">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1791">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1791">Parameters</span></span> 

- <span data-ttu-id="669f3-1792">**semaphore_ptr**: Ponte para um semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1793">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1793">Return Values</span></span>

- <span data-ttu-id="669f3-1794">**TX_SUCCESS**: (0x00) Priorização do semáforo bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="669f3-1795">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1796">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1796">Allowed From</span></span>

<span data-ttu-id="669f3-1797">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1798">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1798">Preemption Possible</span></span>

<span data-ttu-id="669f3-1799">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1800">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1801">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1801">See Also</span></span>

- <span data-ttu-id="669f3-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="669f3-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1807">tx_semaphore_put</span></span>

<span data-ttu-id="669f3-1808">Coloque um caso na contagem de semáforos</span><span class="sxs-lookup"><span data-stu-id="669f3-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1809">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1810">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1810">Description</span></span>

<span data-ttu-id="669f3-1811">Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um.</span><span class="sxs-lookup"><span data-stu-id="669f3-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1812">Se este serviço for chamado quando o semáforo for todos (OxFFFFFFFF), a nova operação de colocação fará com que o semáforo seja reposto a zero.</span><span class="sxs-lookup"><span data-stu-id="669f3-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1813">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1813">Parameters</span></span>

- <span data-ttu-id="669f3-1814">**semaphore_ptr**: Ponte para o bloco de controlo de semáforos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1815">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1815">Return Values</span></span>

- <span data-ttu-id="669f3-1816">**TX_SUCCESS:**(0x00) Semaphore bem sucedido colocado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="669f3-1817">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro inválido à contagem de semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1818">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1818">Allowed From</span></span>

<span data-ttu-id="669f3-1819">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1820">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1820">Preemption Possible</span></span>

<span data-ttu-id="669f3-1821">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1822">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1823">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1823">See Also</span></span>

- <span data-ttu-id="669f3-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="669f3-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="669f3-1834">Notificar o pedido quando o semáforo for colocado</span><span class="sxs-lookup"><span data-stu-id="669f3-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1835">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="669f3-1836">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1836">Description</span></span>

<span data-ttu-id="669f3-1837">Este serviço regista uma função de chamada de notificação que é chamada sempre que o semáforo especificado é colocado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="669f3-1838">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-1839">A chamada de notificação de semáforo da aplicação não está autorizada a ligar para a API da ThreadX SMP com uma opção de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1840">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1840">Parameters</span></span> 

- <span data-ttu-id="669f3-1841">**semaphore_ptr**: Ponteiro para semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="669f3-1842">**semaphore_put_notify**: Ponteiro para a função de notificação de semáforo da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="669f3-1843">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1844">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1844">Return Values</span></span>

- <span data-ttu-id="669f3-1845">**TX_SUCCESS:**(0x00) Registo bem sucedido da notificação de semáforos.</span><span class="sxs-lookup"><span data-stu-id="669f3-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="669f3-1846">TX_SEMAPHORE_ERROR: (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="669f3-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1848">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1848">Allowed From</span></span>

<span data-ttu-id="669f3-1849">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1850">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="669f3-1851">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1851">See Also</span></span>

- <span data-ttu-id="669f3-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="669f3-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="669f3-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="669f3-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="669f3-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="669f3-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="669f3-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="669f3-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="669f3-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="669f3-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="669f3-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1861">tx_thread_create</span></span>

<span data-ttu-id="669f3-1862">Criar linha de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1863">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="669f3-1864">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1864">Description</span></span>

<span data-ttu-id="669f3-1865">Este serviço cria um fio de aplicação que inicia a execução na função de entrada de tarefa especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="669f3-1866">A pilha, prioridade, limiar de pré-escamação e corte de tempo estão entre os atributos especificados pelos parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="669f3-1867">Além disso, o estado de execução inicial do fio também é especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1868">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1868">Parameters</span></span>

- <span data-ttu-id="669f3-1869">**thread_ptr**: Ponteiro para um bloco de controlo de rosca.</span><span class="sxs-lookup"><span data-stu-id="669f3-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="669f3-1870">**name_ptr**: Ponter o nome do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="669f3-1871">**entry_function**: Especifica a função C inicial para a execução do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="669f3-1872">Quando um fio regressa desta função de entrada, é colocado num estado completo e suspenso indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="669f3-1873">**entry_input**: Um valor de 32 bits que é passado para a função de entrada do fio quando executa pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="669f3-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="669f3-1874">A utilização para esta entrada é determinada exclusivamente pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="669f3-1875">**stack_start**: Endereço inicial da área de memória da pilha.</span><span class="sxs-lookup"><span data-stu-id="669f3-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="669f3-1876">**stack_size**: Bytes de números na área da memória da pilha.</span><span class="sxs-lookup"><span data-stu-id="669f3-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="669f3-1877">A área da pilha do fio deve ser grande o suficiente para lidar com a sua pior função de nidificação de chamadas e uso variável local.</span><span class="sxs-lookup"><span data-stu-id="669f3-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="669f3-1878">**prioridade**: Prioridade numérica do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="669f3-1879">Os valores legais variam entre 0 e TX_MAX_PRIORITES-1, onde o valor de 0 representa a maior prioridade.</span><span class="sxs-lookup"><span data-stu-id="669f3-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="669f3-1880">**preempt_threshold**: Nível de prioridade mais elevado (0 a TX_MAX_PRIORITIES-1)) de preempção deficiente.</span><span class="sxs-lookup"><span data-stu-id="669f3-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="669f3-1881">Apenas prioridades superiores a este nível são permitidas para antecipar este fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="669f3-1882">Este valor deve ser inferior ou igual à prioridade especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="669f3-1883">Um valor igual à prioridade do fio desativa o limiar de pré-substituição.</span><span class="sxs-lookup"><span data-stu-id="669f3-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="669f3-1884">**time_slice**: O número de carraças-temporizador que este fio pode ser executado antes que outros fios prontos da mesma prioridade sejam autorizados a correr.</span><span class="sxs-lookup"><span data-stu-id="669f3-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="669f3-1885">Note que a utilização do limiar de pré-substituição desativa o corte de tempo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="669f3-1886">Os valores legais de corte de tempo variam de 1 a 0xFFFFFFFF (inclusive).</span><span class="sxs-lookup"><span data-stu-id="669f3-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="669f3-1887">Um valor de **TX_NO_TIME_SLICE** (um valor de 0) desativa o corte de tempo deste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="669f3-1888">A utilização de corte de tempo resulta numa ligeira quantidade de sobrecarga do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="669f3-1889">Uma vez que o corte de tempo só é útil nos casos em que múltiplos fios partilham a mesma prioridade, os fios que têm uma prioridade única não devem ser atribuídos a uma fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="669f3-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="669f3-1890">**auto_start**: Especifica se o fio começa imediatamente ou se é colocado num estado suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="669f3-1891">As opções legais são **TX_AUTO_START** (0x01) e **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="669f3-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="669f3-1892">Se TX_DONT_START for especificado, o pedido deve ligar mais tarde tx_thread_resume para que o fio seja executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1893">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1893">Return Values</span></span>

- <span data-ttu-id="669f3-1894">**TX_SUCCESS**: (0x00) Criação de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="669f3-1895">TX_THREAD_ERROR: (0x0E) Ponteiro de controlo de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="669f3-1896">Ou o ponteiro é NULO ou o fio já está criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="669f3-1897">TX_PTR_ERROR: (0x03) Endereço inicial inválido do ponto de entrada ou da área da pilha é inválido, normalmente NULO.</span><span class="sxs-lookup"><span data-stu-id="669f3-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="669f3-1898">TX_SIZE_ERROR: (0x05) O tamanho da área da pilha é inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="669f3-1899">Os fios devem ter pelo menos **TX_MINIMUM_STACK** bytes para executar.</span><span class="sxs-lookup"><span data-stu-id="669f3-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="669f3-1900">TX_PRIORITY_ERROR: (0x0F) Prioridade do fio inválido, que é um valor fora do intervalo de (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="669f3-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="669f3-1901">TX_THRESH_ERROR: (0x18) Retenção de preempção inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="669f3-1902">Este valor deve ser uma prioridade válida inferior ou igual à prioridade inicial do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="669f3-1903">TX_START_ERROR: (0x10) Seleção de arranque automático inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="669f3-1904">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1905">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1905">Allowed From</span></span>

<span data-ttu-id="669f3-1906">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1907">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1907">Preemption Possible</span></span>

<span data-ttu-id="669f3-1908">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1909">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a><span data-ttu-id="669f3-1910">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1910">See Also</span></span>

- <span data-ttu-id="669f3-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1911">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-1913">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-1920">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-1921">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="669f3-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1928">tx_thread_delete</span></span>

<span data-ttu-id="669f3-1929">Eliminar o fio da aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1930">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-1931">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1931">Description</span></span>

<span data-ttu-id="669f3-1932">Este serviço elimina o fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="669f3-1933">Uma vez que o fio especificado deve estar num estado encerrado ou concluído, este serviço não pode ser chamado de um fio que tenta apagar-se.</span><span class="sxs-lookup"><span data-stu-id="669f3-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-1934">É da responsabilidade da aplicação gerir a área de memória associada à pilha do fio, que está disponível após a conclusão deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="669f3-1935">Além disso, a aplicação deve impedir a utilização de um fio eliminado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1936">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1936">Parameters</span></span>

- <span data-ttu-id="669f3-1937">**thread_ptr**: Pontear para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1938">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1938">Return Values</span></span>

- <span data-ttu-id="669f3-1939">**TX_SUCCESS**: (0x00) Supressão de rosca bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="669f3-1940">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-1941">**TX_DELETE_ERROR**: (0x11) O fio especificado não se encontra num estado encerrado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="669f3-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="669f3-1942">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1943">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1943">Allowed From</span></span>

<span data-ttu-id="669f3-1944">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-1945">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-1945">Preemption Possible</span></span>

<span data-ttu-id="669f3-1946">No</span><span class="sxs-lookup"><span data-stu-id="669f3-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1947">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-1948">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1948">See Also</span></span>

- <span data-ttu-id="669f3-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1949">tx_thread_create</span></span>
- <span data-ttu-id="669f3-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-1951">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-1958">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-1959">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="669f3-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="669f3-1967">Notificar o pedido após a entrada e saída do fio</span><span class="sxs-lookup"><span data-stu-id="669f3-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-1968">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="669f3-1969">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-1969">Description</span></span>

<span data-ttu-id="669f3-1970">Este serviço regista uma função de chamada de notificação que é chamada sempre que o fio especificado é introduzido ou sai.</span><span class="sxs-lookup"><span data-stu-id="669f3-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="669f3-1971">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-1972">A chamada de notificação de entrada/saída da aplicação não está autorizada a ligar para a API da ThreadX SMP com uma opção de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-1973">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-1973">Parameters</span></span>

- <span data-ttu-id="669f3-1974">**thread_ptr**: Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="669f3-1975">**entry_exit_notify**: Ponteiro para a função de notificação de entrada/saída da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="669f3-1976">O segundo parâmetro da função de notificação de entrada/saída designa se estiver presente uma entrada ou saída.</span><span class="sxs-lookup"><span data-stu-id="669f3-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="669f3-1977">O valor TX_THREAD_ENTRY (0x00) indica que o fio foi introduzido, enquanto o valor TX_THREAD_EXIT (0x01) indica que o fio foi saído.</span><span class="sxs-lookup"><span data-stu-id="669f3-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="669f3-1978">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="669f3-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-1979">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-1979">Return Values</span></span>

- <span data-ttu-id="669f3-1980">**TX_SUCCESS**: (0x00) Registo bem sucedido da função de notificação de entrada/saída do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="669f3-1981">TX_THREAD_ERROR: (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="669f3-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-1983">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-1983">Allowed From</span></span>

<span data-ttu-id="669f3-1984">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-1985">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="669f3-1986">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-1986">See Also</span></span>

- <span data-ttu-id="669f3-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-1987">tx_thread_create</span></span>
- <span data-ttu-id="669f3-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-1988">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-1990">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-1997">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-1998">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="669f3-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2005">tx_thread_identify</span></span>

<span data-ttu-id="669f3-2006">Recupera o ponteiro para a atual execução do fio</span><span class="sxs-lookup"><span data-stu-id="669f3-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2007">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="669f3-2008">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2008">Description</span></span>

<span data-ttu-id="669f3-2009">Este serviço devolve um ponteiro ao fio atualmente executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="669f3-2010">Se não houver fio, este serviço devolve um ponteiro nulo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2011">Se este serviço for chamado de um ISR, o valor de retorno representa o fio em execução antes do manipulador de interrupção de execução.</span><span class="sxs-lookup"><span data-stu-id="669f3-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2012">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2012">Parameters</span></span>

<span data-ttu-id="669f3-2013">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2014">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2014">Return Values</span></span>

- <span data-ttu-id="669f3-2015">ponteiro de linha: Ponteiro para o fio atualmente executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="669f3-2016">Se não houver fio, o valor de retorno é TX_NULL.</span><span class="sxs-lookup"><span data-stu-id="669f3-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2017">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2017">Allowed From</span></span>

<span data-ttu-id="669f3-2018">Fios e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2019">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2019">Preemption Possible</span></span>

<span data-ttu-id="669f3-2020">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2021">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2022">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2022">See Also</span></span>

- <span data-ttu-id="669f3-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2023">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2024">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2032">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2033">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="669f3-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2040">tx_thread_info_get</span></span>

<span data-ttu-id="669f3-2041">Recuperar informações sobre o fio</span><span class="sxs-lookup"><span data-stu-id="669f3-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2042">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="669f3-2043">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2043">Description</span></span>

<span data-ttu-id="669f3-2044">Este serviço recupera informações sobre o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2045">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2045">Parameters</span></span> 

- <span data-ttu-id="669f3-2046">**thread_ptr**: Ponteiro para o bloco de controlo da rosca.</span><span class="sxs-lookup"><span data-stu-id="669f3-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="669f3-2047">**nome**: Ponteiro para destino para o ponteiro para o nome do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="669f3-2048">**estado**: Ponteiro para destino para o estado de execução atual do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="669f3-2049">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="669f3-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="669f3-2050">**TX_READY:**(0x00)</span><span class="sxs-lookup"><span data-stu-id="669f3-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="669f3-2051">**TX_COMPLETED:**(0x01)</span><span class="sxs-lookup"><span data-stu-id="669f3-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="669f3-2052">**TX_TERMINATED:**(0x02)</span><span class="sxs-lookup"><span data-stu-id="669f3-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="669f3-2053">**TX_SUSPENDED:**(0x03)</span><span class="sxs-lookup"><span data-stu-id="669f3-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="669f3-2054">**TX_SLEEP:**(0x04)</span><span class="sxs-lookup"><span data-stu-id="669f3-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="669f3-2055">**TX_QUEUE_SUSP:**(0x05)</span><span class="sxs-lookup"><span data-stu-id="669f3-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="669f3-2056">**TX_SEMAPHORE_SUSP:**(0x06)</span><span class="sxs-lookup"><span data-stu-id="669f3-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="669f3-2057">**TX_EVENT_FLAG:**(0x07)</span><span class="sxs-lookup"><span data-stu-id="669f3-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="669f3-2058">**TX_BLOCK_MEMORY:**(0x08)</span><span class="sxs-lookup"><span data-stu-id="669f3-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="669f3-2059">**TX_BYTE_MEMORY:**(0x09)</span><span class="sxs-lookup"><span data-stu-id="669f3-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="669f3-2060">**TX_MUTEX_SUSP:**(0x0D)</span><span class="sxs-lookup"><span data-stu-id="669f3-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="669f3-2061">**run_count**: Ponter para o destino para a contagem de corridas do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="669f3-2062">**prioridade**: Ponter para o destino para a prioridade da linha.</span><span class="sxs-lookup"><span data-stu-id="669f3-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="669f3-2063">**preemption_threshold**: Ponter para o destino para o limiar de pré-substituição do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="669f3-2064">**time_slice**: Ponter para o destino para a fatia de tempo do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="669f3-2065">**next_thread**: Ponteiro para destino para o próximo ponteiro de linha criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="669f3-2066">**suspended_thread**: Ponter para o destino para ponter o próximo fio na lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="669f3-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2067">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2068">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2068">Return Values</span></span>

- <span data-ttu-id="669f3-2069">**TX_SUCCESS**: (0x00) Recuperação de informações de fio bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="669f3-2070">TX_THREAD_ERROR: (0x0E) Ponteiro de controlo de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2071">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2071">Allowed From</span></span>

<span data-ttu-id="669f3-2072">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2073">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2073">Preemption Possible</span></span>

<span data-ttu-id="669f3-2074">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2075">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2075">Example</span></span>

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2076">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2076">See Also</span></span>

- <span data-ttu-id="669f3-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2077">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2078">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2080">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2086">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2087">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="669f3-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="669f3-2095">Obtenha informações sobre desempenho de thread</span><span class="sxs-lookup"><span data-stu-id="669f3-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2096">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="669f3-2097">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2097">Description</span></span>

<span data-ttu-id="669f3-2098">Este serviço recupera informações de desempenho sobre o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2099">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_THREAD_ENABLE_PERFORMANCE_INFO** definidas para que este serviço devolva informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2100">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2100">Parameters</span></span> 

- <span data-ttu-id="669f3-2101">**thread_ptr**: Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="669f3-2102">**resturações**: Ponteiro para o destino para o número de resturações deste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="669f3-2103">**suspensões**: Ponteiro para o destino para o número de suspensões deste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="669f3-2104">**solicited_preemptions**: Ponter para o destino para o número de preventivas como resultado de uma chamada de serviço API threadX feita por este fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="669f3-2105">**interrupt_preemptions**: Ponter para o destino para o número de preventivas deste fio como resultado do processamento de interrupção.</span><span class="sxs-lookup"><span data-stu-id="669f3-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="669f3-2106">**priority_inversions**: Ponteiro para o destino para o número de inversões prioritárias deste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="669f3-2107">**time_slices**: Ponte para o destino para o número de tempolices deste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="669f3-2108">**renuncia:** Ponteiro para destino para o número de renúncias de fio realizadas por este fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="669f3-2109">**intervalos :** Ponte para o destino para o número de intervalos de suspensão neste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="669f3-2110">**wait_aborts**: Ponter para o destino para o número de abortos de espera realizados neste fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="669f3-2111">**last_preempted_by**: Ponter para o destino para o ponteiro de linha que por último preemptou este fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2112">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2113">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2113">Return Values</span></span>

- <span data-ttu-id="669f3-2114">**TX_SUCCESS**: (0x00) Desempenho de fio bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="669f3-2115">**TX_PTR_ERROR:**(0x03) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="669f3-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2117">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2117">Allowed From</span></span>

<span data-ttu-id="669f3-2118">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2120">See Also</span></span>

- <span data-ttu-id="669f3-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2121">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2122">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2124">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2130">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2131">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="669f3-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="669f3-2139">Obtenha informações sobre desempenho do sistema de fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2140">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="669f3-2141">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2141">Description</span></span>

<span data-ttu-id="669f3-2142">Este serviço obtém informações de desempenho sobre todos os fios do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2143">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_THREAD_ENABLE_PERFORMANCE_INFO** definidas para que este serviço devolva informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2144">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2144">Parameters</span></span>

- <span data-ttu-id="669f3-2145">**resturações**: Ponteiro para o destino para o número total de reposições de roscas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="669f3-2146">**suspensões**: Ponteiro para o destino para o número total de suspensões de rosca.</span><span class="sxs-lookup"><span data-stu-id="669f3-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="669f3-2147">**solicited_preemptions**: Ponter para o destino para o número total de preempções de fio como resultado de um fio que chama um serviço API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="669f3-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="669f3-2148">**interrupt_preemptions**: Ponter para o destino para o número total de preemposições de rosca como resultado do processamento de interrupção.</span><span class="sxs-lookup"><span data-stu-id="669f3-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="669f3-2149">**priority_inversions**: Ponteiro para o destino para o número total de inversões prioritárias de linha.</span><span class="sxs-lookup"><span data-stu-id="669f3-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="669f3-2150">**time_slices**: Ponter para o destino para o número total de fatias de tempo de fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="669f3-2151">**renuncia:** Ponteiro para destino para o número total de renúncias de fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="669f3-2152">**intervalos :** Ponteiro para o destino para o número total de intervalos de suspensão de fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="669f3-2153">**wait_aborts**: Ponter para o destino para o número total de abortos de espera de fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="669f3-2154">**non_idle_returns**: Ponter para o destino para o número de vezes que um fio retorna ao sistema quando outro fio estiver pronto para ser executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="669f3-2155">**idle_returns**: Ponter para o destino para o número de vezes que um fio retorna ao sistema quando nenhum outro fio está pronto para ser executado (sistema inativo).</span><span class="sxs-lookup"><span data-stu-id="669f3-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2156">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2157">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2157">Return Values</span></span>

- <span data-ttu-id="669f3-2158">**TX_SUCCESS**: (0x00) Obtém-se um desempenho bem sucedido do sistema de fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="669f3-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2160">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2160">Allowed From</span></span>

<span data-ttu-id="669f3-2161">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2163">See Also</span></span>

- <span data-ttu-id="669f3-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2164">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2165">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2167">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2173">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2174">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="669f3-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="669f3-2182">Alterar limiar de preempção do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2183">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="669f3-2184">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2184">Description</span></span>

<span data-ttu-id="669f3-2185">Este serviço altera o limiar de pré-substituição do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="669f3-2186">O limiar de prevenção previne a preempção do fio especificado por roscas iguais ou inferiores ao valor do limiar de prevenção.</span><span class="sxs-lookup"><span data-stu-id="669f3-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2187">A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2188">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2188">Parameters</span></span>

- <span data-ttu-id="669f3-2189">**thread_ptr**: Pontear para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="669f3-2190">**new_threshold**: Novo nível de prioridade do limiar de pré-edição (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="669f3-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="669f3-2191">**old_threshold**: Ponter para um local para devolver o limiar de pré-substituição anterior.</span><span class="sxs-lookup"><span data-stu-id="669f3-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2192">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2192">Return Values</span></span>

- <span data-ttu-id="669f3-2193">**TX_SUCCESS**: (0x00) Alteração do limiar de pré-edição bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="669f3-2194">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2195">**TX_THRESH_ERROR**: (0x18) O novo limiar de pré-substituição especificado não é uma prioridade de linha válida (um valor diferente (0 a TX_MAX_PRIORITIES-1)) ou é maior do que (prioridade inferior) do que a prioridade atual do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="669f3-2196">TX_PTR_ERROR: (0x03) Ponteiro inválido para o local de armazenamento de retenção preventiva anterior.</span><span class="sxs-lookup"><span data-stu-id="669f3-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="669f3-2197">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2198">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2198">Allowed From</span></span>

<span data-ttu-id="669f3-2199">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2200">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2200">Preemption Possible</span></span>

<span data-ttu-id="669f3-2201">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2203">See Also</span></span>

- <span data-ttu-id="669f3-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2204">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2205">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2207">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2213">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2214">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="669f3-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="669f3-2222">Alterar prioridade do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2223">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="669f3-2224">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2224">Description</span></span>

<span data-ttu-id="669f3-2225">Este serviço altera a prioridade do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="669f3-2226">As prioridades válidas variam entre 0 e TX_MAX_PRIORITES-1, onde 0 representa o nível de maior prioridade.</span><span class="sxs-lookup"><span data-stu-id="669f3-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2227">O limiar de pré-substituição do fio especificado é automaticamente definido para a nova prioridade.</span><span class="sxs-lookup"><span data-stu-id="669f3-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="669f3-2228">Se for desejado um novo limiar, o serviço **tx_thread_preemption_change** deve ser utilizado após esta chamada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2229">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2229">Parameters</span></span>

- <span data-ttu-id="669f3-2230">**thread_ptr**: Pontear para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="669f3-2231">**new_priority**: Novo nível de prioridade do fio (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="669f3-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="669f3-2232">**old_priority**: Ponter para um local para devolver a prioridade anterior da linha.</span><span class="sxs-lookup"><span data-stu-id="669f3-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2233">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2233">Return Values</span></span>

- <span data-ttu-id="669f3-2234">**TX_SUCCESS**: (0x00) Alteração prioritária bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="669f3-2235">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2236">TX_PRIORITY_ERROR: (0x0F) A nova prioridade especificada não é válida (um valor diferente (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="669f3-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="669f3-2237">TX_PTR_ERROR: (0x03) Ponteiro inválido para localização de armazenamento prioritário anterior.</span><span class="sxs-lookup"><span data-stu-id="669f3-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="669f3-2238">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2239">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2239">Allowed From</span></span>

<span data-ttu-id="669f3-2240">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2241">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2241">Preemption Possible</span></span>

<span data-ttu-id="669f3-2242">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2243">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2244">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2244">See Also</span></span>

- <span data-ttu-id="669f3-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2245">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2246">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2248">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2254">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2255">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="669f3-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="669f3-2263">Renunciar ao controlo a outros fios de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2264">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="669f3-2265">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2265">Description</span></span>

<span data-ttu-id="669f3-2266">Este serviço renuncia ao controlo do processador a outras linhas prontas a executar na mesma prioridade ou maior.</span><span class="sxs-lookup"><span data-stu-id="669f3-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2267">Além de renunciar ao controlo a fios da mesma prioridade, este serviço também renuncia ao controlo ao fio de maior prioridade impedido de ser executado devido à definição do limiar de prevenção da linha atual.</span><span class="sxs-lookup"><span data-stu-id="669f3-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2268">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2268">Parameters</span></span>

<span data-ttu-id="669f3-2269">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2270">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2270">Return Values</span></span>

<span data-ttu-id="669f3-2271">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2272">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2272">Allowed From</span></span>

<span data-ttu-id="669f3-2273">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2274">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2274">Preemption Possible</span></span>

<span data-ttu-id="669f3-2275">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2276">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a><span data-ttu-id="669f3-2277">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2277">See Also</span></span>

- <span data-ttu-id="669f3-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2278">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2279">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2281">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2287">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2288">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="669f3-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2295">tx_thread_reset</span></span>

<span data-ttu-id="669f3-2296">Linha de reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2297">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2298">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2298">Description</span></span>

<span data-ttu-id="669f3-2299">Este serviço reinicia o fio especificado para executar no ponto de entrada definido na criação do fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="669f3-2300">O fio deve estar em um **estado TX_COMPLETED** ou **TX_TERMINATED** para que seja reposto</span><span class="sxs-lookup"><span data-stu-id="669f3-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2301">O fio deve ser retomado para que volte a ser executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2302">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2302">Parameters</span></span> 

- <span data-ttu-id="669f3-2303">**thread_ptr**: Pontear para um fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2304">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2304">Return Values</span></span>

- <span data-ttu-id="669f3-2305">**TX_SUCCESS**: (0x00) Reset de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="669f3-2306">**TX_NOT_DONE**: (0x20) O fio especificado não se encontra num estado TX_COMPLETED ou TX_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="669f3-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="669f3-2307">TX_THREAD_ERROR: (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="669f3-2308">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2309">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2309">Allowed From</span></span>

<span data-ttu-id="669f3-2310">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2311">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2312">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2312">See Also</span></span>

- <span data-ttu-id="669f3-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2313">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2314">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2316">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2323">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="669f3-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2330">tx_thread_resume</span></span>

<span data-ttu-id="669f3-2331">Retomar linha de aplicação suspensa</span><span class="sxs-lookup"><span data-stu-id="669f3-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2333">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2333">Description</span></span>

<span data-ttu-id="669f3-2334">Este serviço retoma ou prepara para a execução um fio que foi previamente suspenso por uma ***chamada tx_thread_suspend.***</span><span class="sxs-lookup"><span data-stu-id="669f3-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="669f3-2335">Além disso, este serviço retoma os fios que foram criados sem um arranque automático.</span><span class="sxs-lookup"><span data-stu-id="669f3-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2336">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2336">Parameters</span></span>

- <span data-ttu-id="669f3-2337">**thread_ptr**: Ponter para um fio de aplicação suspenso.</span><span class="sxs-lookup"><span data-stu-id="669f3-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2338">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2338">Return Values</span></span>

- <span data-ttu-id="669f3-2339">**TX_SUCCESS:**(0x00) Currículo de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="669f3-2340">**TX_SUSPEND_LIFTED**: (0x19) A suspensão adiada previamente definida foi levantada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="669f3-2341">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2342">**TX_RESUME_ERROR**: (0x12) O fio especificado não está suspenso ou foi previamente suspenso por um serviço que não **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="669f3-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2343">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2343">Allowed From</span></span>

<span data-ttu-id="669f3-2344">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2345">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2345">Preemption Possible</span></span>

<span data-ttu-id="669f3-2346">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2347">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2348">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2348">See Also</span></span>

- <span data-ttu-id="669f3-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2349">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2350">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2352">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2359">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="669f3-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2366">tx_thread_sleep</span></span>

<span data-ttu-id="669f3-2367">Suspender o fio de corrente por tempo especificado</span><span class="sxs-lookup"><span data-stu-id="669f3-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2368">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="669f3-2369">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2369">Description</span></span>

<span data-ttu-id="669f3-2370">Este serviço faz com que o fio de chamada suspenda o número especificado de carraças temporais.</span><span class="sxs-lookup"><span data-stu-id="669f3-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="669f3-2371">A quantidade de tempo físico associado a um tique-taque do temporizador é específica da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="669f3-2372">Este serviço só pode ser chamado a partir de um fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2373">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2373">Parameters</span></span>

- <span data-ttu-id="669f3-2374">**timer_ticks**: O número de carraças do temporizador para suspender o fio da aplicação de chamada, que varia de 0 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="669f3-2375">Se 0 for especificado, o serviço retorna imediatamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2376">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2376">Return Values</span></span>

- <span data-ttu-id="669f3-2377">**TX_SUCCESS:**(0x00) Sono de rosca bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="669f3-2378">**TX_WAIT_ABORTED:**(0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="669f3-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="669f3-2379">**TX_CALLER_ERROR**: (0x13) Serviço chamado de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="669f3-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2380">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2380">Allowed From</span></span>

<span data-ttu-id="669f3-2381">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2382">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2382">Preemption Possible</span></span>

<span data-ttu-id="669f3-2383">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2384">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2385">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2385">See Also</span></span>

- <span data-ttu-id="669f3-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2386">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2387">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2389">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2396">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2397">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="669f3-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="669f3-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="669f3-2404">Exclua a execução de fios num conjunto de núcleos</span><span class="sxs-lookup"><span data-stu-id="669f3-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2405">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="669f3-2406">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2406">Description</span></span>

<span data-ttu-id="669f3-2407">Esta função exclui a linha especificada de execução no núcleo(s) especificado no mapa de bits chamado "*exclusion_map*."</span><span class="sxs-lookup"><span data-stu-id="669f3-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="669f3-2408">Cada bit em "*exclusion_map*" representa um núcleo (bit 0 representa núcleo 0, etc.).</span><span class="sxs-lookup"><span data-stu-id="669f3-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="669f3-2409">Se a broca estiver definida, o núcleo correspondente é excluído da execução do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2410">A utilização da exclusão do processador pode causar um processamento adicional na linha para a lógica de mapeamento do núcleo, a fim de encontrar a correspondência ideal.</span><span class="sxs-lookup"><span data-stu-id="669f3-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="669f3-2411">Este processamento é limitado pelo número de fios prontos.</span><span class="sxs-lookup"><span data-stu-id="669f3-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2412">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2412">Parameters</span></span> 

- <span data-ttu-id="669f3-2413">**thread_ptr**: Ponteiro para roscar para alterar a exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="669f3-2414">**exclusion_map:** Mapa de bits onde um pouco de assento indica que esse núcleo está excluído.</span><span class="sxs-lookup"><span data-stu-id="669f3-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="669f3-2415">O fornecimento de um valor de 0 permite que o fio seja executado em qualquer núcleo (predefinição).</span><span class="sxs-lookup"><span data-stu-id="669f3-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2416">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2416">Return Values</span></span>

- <span data-ttu-id="669f3-2417">TX_SUCCESS: (0x00) Exclusão do núcleo bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="669f3-2418">TX_THREAD_ERROR: (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2419">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2419">Allowed From</span></span>

<span data-ttu-id="669f3-2420">Inicialização, ISRs, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2421">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="669f3-2422">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2422">See Also</span></span>

- <span data-ttu-id="669f3-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="669f3-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="669f3-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="669f3-2426">Obtém a exclusão atual do núcleo do fio</span><span class="sxs-lookup"><span data-stu-id="669f3-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2427">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2428">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2428">Description</span></span>

<span data-ttu-id="669f3-2429">Esta função devolve a lista de exclusão do núcleo atual.</span><span class="sxs-lookup"><span data-stu-id="669f3-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2430">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2430">Parameters</span></span>

- <span data-ttu-id="669f3-2431">**thread_ptr**: Ponteiro para roscar a partir do qual recuperar a exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="669f3-2432">**exclusion_map_ptr**: Destino para o mapa atual do bit de exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2433">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2433">Return Values</span></span>

- <span data-ttu-id="669f3-2434">TX_SUCCESS: (0x00) Recuperação bem sucedida da exclusão do núcleo do thread.</span><span class="sxs-lookup"><span data-stu-id="669f3-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="669f3-2435">TX_THREAD_ERROR: (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="669f3-2436">TX_PTR_ERROR: (0x03) Ponteiro de destino de exclusão inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2437">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2437">Allowed From</span></span>

<span data-ttu-id="669f3-2438">Inicialização, ISRs, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2439">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="669f3-2440">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2440">See Also</span></span>

- <span data-ttu-id="669f3-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="669f3-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="669f3-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="669f3-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="669f3-2444">Recupere atualmente o núcleo de execução do chamador</span><span class="sxs-lookup"><span data-stu-id="669f3-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2445">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="669f3-2446">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2446">Description</span></span>

<span data-ttu-id="669f3-2447">Esta função devolve o ID central do núcleo que executa este serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2448">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2448">Parameters</span></span>

<span data-ttu-id="669f3-2449">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2450">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2450">Return Values</span></span>

- <span data-ttu-id="669f3-2451">core_id: ID de execução atual do núcleo(0 a TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="669f3-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2452">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2452">Allowed From</span></span>

<span data-ttu-id="669f3-2453">Inicialização, ISRs, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2454">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2455">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2455">See Also</span></span>

- <span data-ttu-id="669f3-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="669f3-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="669f3-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="669f3-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="669f3-2459">Registar chamada de notificação de erro de pilha de fio</span><span class="sxs-lookup"><span data-stu-id="669f3-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2460">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="669f3-2461">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2461">Description</span></span>

<span data-ttu-id="669f3-2462">Este serviço regista uma função de chamada de notificação para lidar com erros de pilha de fios.</span><span class="sxs-lookup"><span data-stu-id="669f3-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="669f3-2463">Quando a ThreadX SMP detetar um erro de pilha de fio durante a execução, chamará esta função de notificação para processar o erro.</span><span class="sxs-lookup"><span data-stu-id="669f3-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="669f3-2464">O processamento do erro é completamente definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="669f3-2465">Qualquer coisa desde suspender o fio de violação até reiniciar todo o sistema pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="669f3-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2466">A biblioteca ThreadX SMP deve ser construída com **TX_ENABLE_STACK_CHECKING** definidas para que este serviço devolva informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2467">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2467">Parameters</span></span>

- <span data-ttu-id="669f3-2468">**error_handler**: Ponteiro para a função de manuseamento de erros de pilha da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="669f3-2469">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2470">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2470">Return Values</span></span>

- <span data-ttu-id="669f3-2471">**TX_SUCCESS**: (0x00) Reset de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="669f3-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2473">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2473">Allowed From</span></span>

<span data-ttu-id="669f3-2474">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2475">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="669f3-2476">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2476">See Also</span></span>

- <span data-ttu-id="669f3-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2477">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2478">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2480">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2487">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2488">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="669f3-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2494">tx_thread_suspend</span></span>

<span data-ttu-id="669f3-2495">Suspender o fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2496">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2497">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2497">Description</span></span>

<span data-ttu-id="669f3-2498">Este serviço suspende o fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="669f3-2499">Um fio pode chamar este serviço para se suspender.</span><span class="sxs-lookup"><span data-stu-id="669f3-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2500">Se o fio especificado já estiver suspenso por outro motivo, esta suspensão é mantida internamente até que a suspensão prévia seja levantada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="669f3-2501">Quando isso acontece, esta suspensão incondicional do fio especificado é executada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="669f3-2502">Outros pedidos de suspensão incondicional não têm efeito.</span><span class="sxs-lookup"><span data-stu-id="669f3-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="669f3-2503">Depois de suspensa, o fio deve ser retomado por ***tx_thread_resume*** para ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="669f3-2504">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2504">Parameters</span></span>

- <span data-ttu-id="669f3-2505">**thread_ptr**: Ponteiro para um fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2506">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2506">Return Values</span></span>

- <span data-ttu-id="669f3-2507">**TX_SUCCESS**: (0x00) Suspensão de fio bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="669f3-2508">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2509">**TX_SUSPEND_ERROR**: (0x14) O fio especificado encontra-se num estado encerrado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="669f3-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="669f3-2510">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2511">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2511">Allowed From</span></span>

<span data-ttu-id="669f3-2512">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2513">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2513">Preemption Possible</span></span>

<span data-ttu-id="669f3-2514">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2515">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2516">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2516">See Also</span></span>

- <span data-ttu-id="669f3-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2517">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2518">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2520">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2527">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2528">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="669f3-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2534">tx_thread_terminate</span></span>

<span data-ttu-id="669f3-2535">Termina linha de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2536">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2537">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2537">Description</span></span>

<span data-ttu-id="669f3-2538">Este serviço termina o fio de aplicação especificado, independentemente de o fio estar suspenso ou não.</span><span class="sxs-lookup"><span data-stu-id="669f3-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="669f3-2539">Um fio pode chamar este serviço para terminar sozinho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2540">Depois de ter sido encerrado, o fio deve ser reiniciado para que volte a ser executado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="669f3-2541">É da responsabilidade da aplicação assegurar que o fio está num estado adequado para a rescisão.</span><span class="sxs-lookup"><span data-stu-id="669f3-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="669f3-2542">Por exemplo, um fio não deve ser terminado durante o processamento crítico da aplicação ou no interior de outros componentes do middleware onde possa deixar esse processamento num estado desconhecido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2543">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2543">Parameters</span></span>

- <span data-ttu-id="669f3-2544">**thread_ptr**: Ponteiro para o fio da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2545">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2545">Return Values</span></span>

- <span data-ttu-id="669f3-2546">**TX_SUCCESS:**(0x00) Fim de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="669f3-2547">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2548">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2549">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2549">Allowed From</span></span>

<span data-ttu-id="669f3-2550">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2551">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2551">Preemption Possible</span></span>

<span data-ttu-id="669f3-2552">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2553">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2554">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2554">See Also</span></span>

- <span data-ttu-id="669f3-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2555">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2556">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2558">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2565">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2566">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="669f3-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="669f3-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="669f3-2573">Altera a fatia de tempo do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2574">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="669f3-2575">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2575">Description</span></span>

<span data-ttu-id="669f3-2576">Este serviço altera a fatia de tempo do fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="669f3-2577">Selecionar uma fatia de tempo para um fio assegura que não executará mais do que o número especificado de carraças de temporizador antes que outros fios das mesmas prioridades ou mais altas tenham a oportunidade de executar.</span><span class="sxs-lookup"><span data-stu-id="669f3-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2578">A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2579">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2579">Parameters</span></span>

- <span data-ttu-id="669f3-2580">**thread_ptr**: Ponteiro para o fio da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="669f3-2581">**new_time_slice**: Novo valor de fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="669f3-2582">Os valores legais incluem valores TX_NO_TIME_SLICE e numéricos de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="669f3-2583">**old_time_slice**: Ponteiro para a localização para armazenar o valor de 200 horas anteriores do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2584">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2584">Return Values</span></span>

- <span data-ttu-id="669f3-2585">**TX_SUCCESS**: (0x00) Oportunidade de corte de tempo bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="669f3-2586">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2587">TX_PTR_ERROR: (0x03) Ponteiro inválido para o local de armazenamento da fatia de tempo anterior.</span><span class="sxs-lookup"><span data-stu-id="669f3-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="669f3-2588">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2589">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2589">Allowed From</span></span>

<span data-ttu-id="669f3-2590">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2591">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2591">Preemption Possible</span></span>

<span data-ttu-id="669f3-2592">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2593">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2594">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2594">See Also</span></span>

- <span data-ttu-id="669f3-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2595">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2596">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2598">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2605">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2606">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="669f3-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="669f3-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="669f3-2613">Abortar suspensão do fio especificado</span><span class="sxs-lookup"><span data-stu-id="669f3-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2614">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="669f3-2615">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2615">Description</span></span>

<span data-ttu-id="669f3-2616">Este serviço aborta o sono ou qualquer outro objeto suspenso do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="669f3-2617">Se a espera for abortada, um valor TX_WAIT_ABORTED é devolvido do serviço que o fio estava à espera.</span><span class="sxs-lookup"><span data-stu-id="669f3-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2618">Este serviço não liberta suspensão explícita que é feita pelo serviço tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="669f3-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2619">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2619">Parameters</span></span>

- <span data-ttu-id="669f3-2620">**thread_ptr**: Pontear para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2621">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2621">Return Values</span></span>

- <span data-ttu-id="669f3-2622">**TX_SUCCESS**: (0x00) Abortar a espera de fio bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="669f3-2623">TX_THREAD_ERROR: (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="669f3-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) O fio especificado não está em estado de espera.</span><span class="sxs-lookup"><span data-stu-id="669f3-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2625">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2625">Allowed From</span></span>

<span data-ttu-id="669f3-2626">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2627">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2627">Preemption Possible</span></span>

<span data-ttu-id="669f3-2628">Sim</span><span class="sxs-lookup"><span data-stu-id="669f3-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2629">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2630">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2630">See Also</span></span>

- <span data-ttu-id="669f3-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2631">tx_thread_create</span></span>
- <span data-ttu-id="669f3-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2632">tx_thread_delete</span></span>
- <span data-ttu-id="669f3-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="669f3-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="669f3-2634">tx_thread_identify</span></span>
- <span data-ttu-id="669f3-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="669f3-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="669f3-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="669f3-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="669f3-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="669f3-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="669f3-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="669f3-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="669f3-2641">tx_thread_reset</span></span>
- <span data-ttu-id="669f3-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="669f3-2642">tx_thread_resume</span></span>
- <span data-ttu-id="669f3-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="669f3-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="669f3-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="669f3-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="669f3-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="669f3-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="669f3-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="669f3-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="669f3-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="669f3-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2648">tx_time_get</span></span>

<span data-ttu-id="669f3-2649">Recupera o tempo atual</span><span class="sxs-lookup"><span data-stu-id="669f3-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2650">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="669f3-2651">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2651">Description</span></span>

<span data-ttu-id="669f3-2652">Este serviço devolve o conteúdo do relógio interno do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="669f3-2653">Cada timertick aumenta o relógio do sistema interno por um.</span><span class="sxs-lookup"><span data-stu-id="669f3-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="669f3-2654">O relógio do sistema está definido para zero durante a inicialização e pode ser alterado para um valor específico pelo ***serviço tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="669f3-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2655">O tempo real que cada temporizador representa é específico da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2656">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2656">Parameters</span></span>

<span data-ttu-id="669f3-2657">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2658">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2658">Return Values</span></span>

- <span data-ttu-id="669f3-2659">tiques do relógio do sistema: Valor do relógio interno, livre, do sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2660">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2660">Allowed From</span></span>

<span data-ttu-id="669f3-2661">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2662">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2662">Preemption Possible</span></span>

<span data-ttu-id="669f3-2663">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2664">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2665">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2665">See Also</span></span>

- <span data-ttu-id="669f3-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="669f3-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="669f3-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="669f3-2667">tx_time_set</span></span>

<span data-ttu-id="669f3-2668">Define a hora atual</span><span class="sxs-lookup"><span data-stu-id="669f3-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2669">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="669f3-2670">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2670">Description</span></span>

<span data-ttu-id="669f3-2671">Este serviço define o relógio do sistema interno ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="669f3-2672">Cada temporizador aumenta o relógio do sistema interno por um.</span><span class="sxs-lookup"><span data-stu-id="669f3-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2673">O tempo real que cada temporizador representa é específico da aplicação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2674">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2674">Parameters</span></span>

- <span data-ttu-id="669f3-2675">**new_time**: Nova hora para colocar no relógio do sistema, os valores legais variam de 0 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2676">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2676">Return Values</span></span>

<span data-ttu-id="669f3-2677">Nenhum</span><span class="sxs-lookup"><span data-stu-id="669f3-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2678">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2678">Allowed From</span></span>

<span data-ttu-id="669f3-2679">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2680">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2680">Preemption Possible</span></span>

<span data-ttu-id="669f3-2681">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2682">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2683">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2683">See Also</span></span>

- <span data-ttu-id="669f3-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="669f3-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2685">tx_timer_activate</span></span>

<span data-ttu-id="669f3-2686">Ativar o temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="669f3-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2687">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2688">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2688">Description</span></span>

<span data-ttu-id="669f3-2689">Este serviço ativa o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="669f3-2690">As rotinas de expiração dos temporizadores que expiram ao mesmo tempo são executadas na ordem em que foram ativados.</span><span class="sxs-lookup"><span data-stu-id="669f3-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-2691">Que um temporizador de um tiro expirado deve ser reiniciado através **de tx_timer_change** antes de poder ser ativado novamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2692">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2692">Parameters</span></span>

- <span data-ttu-id="669f3-2693">**timer_ptr**: Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2694">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2694">Return Values</span></span>

- <span data-ttu-id="669f3-2695">**TX_SUCCESS:**(0x00) Ativação do temporizador de aplicação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="669f3-2696">**TX_TIMER_ERROR**: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="669f3-2697">**TX_ACTIVATE_ERROR**: (0x17) O temporizador já estava ativo ou é um temporizador de um tiro que já expirou.</span><span class="sxs-lookup"><span data-stu-id="669f3-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2698">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2698">Allowed From</span></span>

<span data-ttu-id="669f3-2699">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2700">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2700">Preemption Possible</span></span>

<span data-ttu-id="669f3-2701">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2702">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2703">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2703">See Also</span></span>

- <span data-ttu-id="669f3-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2704">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2705">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2707">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="669f3-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2711">tx_timer_change</span></span>

<span data-ttu-id="669f3-2712">Alterar temporizador de aplicação</span><span class="sxs-lookup"><span data-stu-id="669f3-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2713">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="669f3-2714">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2714">Description</span></span>

<span data-ttu-id="669f3-2715">Este serviço altera as características de expiração do temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="669f3-2716">O temporizador deve ser desativado antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2717">É necessária uma chamada para o serviço **tx_timer_activate** após este serviço para repor o temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2718">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2718">Parameters</span></span>

- <span data-ttu-id="669f3-2719">**timer_ptr**: Ponteiro para um bloco de controlo do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="669f3-2720">**initial_ticks**: Especifica o número inicial de carraças para a expiração do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="669f3-2721">Os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="669f3-2722">**reschedule_ticks**: Especifica o número de carraças para todos os expiradores do temporizador após o primeiro.</span><span class="sxs-lookup"><span data-stu-id="669f3-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="669f3-2723">Um zero para este parâmetro faz do temporizador um temporizador de um tiro.</span><span class="sxs-lookup"><span data-stu-id="669f3-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="669f3-2724">Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="669f3-2725">Que um temporizador de um tiro expirado deve ser reiniciado através **de tx_timer_change** antes de poder ser ativado novamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2726">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2726">Return Values</span></span>

- <span data-ttu-id="669f3-2727">**TX_SUCCESS:**(0x00) Alteração do temporizador de aplicação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="669f3-2728">TX_TIMER_ERROR: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="669f3-2729">TX_TICK_ERROR: (0x16) Valor inválido (a zero) fornecido para os tiques iniciais.</span><span class="sxs-lookup"><span data-stu-id="669f3-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="669f3-2730">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2731">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2731">Allowed From</span></span>

<span data-ttu-id="669f3-2732">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2733">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2733">Preemption Possible</span></span>

<span data-ttu-id="669f3-2734">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2735">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="669f3-2736">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2736">See Also</span></span>

- <span data-ttu-id="669f3-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2737">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2738">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2740">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="669f3-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2744">tx_timer_create</span></span>

<span data-ttu-id="669f3-2745">Criar temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="669f3-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2746">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="669f3-2747">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2747">Description</span></span>

<span data-ttu-id="669f3-2748">Este serviço cria um temporizador de aplicação com a função de expiração especificada e periódico.</span><span class="sxs-lookup"><span data-stu-id="669f3-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2749">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2749">Parameters</span></span>

- <span data-ttu-id="669f3-2750">**timer_ptr**: Ponteiro para um bloco de controlo do temporizador</span><span class="sxs-lookup"><span data-stu-id="669f3-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="669f3-2751">**name_ptr**: Ponter o nome do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="669f3-2752">**expiration_function**: Função de aplicação para ligar quando o temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="669f3-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="669f3-2753">**expiration_input:** Inserir para passar para a função de expiração quando o temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="669f3-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="669f3-2754">**initial_ticks**: Especifica o número inicial de carraças para a expiração do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="669f3-2755">Os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="669f3-2756">**reschedule_ticks**: Especifica o número de carraças para todos os expiradores do temporizador após o primeiro.</span><span class="sxs-lookup"><span data-stu-id="669f3-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="669f3-2757">Um zero para este parâmetro faz do temporizador um temporizador de um tiro.</span><span class="sxs-lookup"><span data-stu-id="669f3-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="669f3-2758">Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="669f3-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="669f3-2759">Depois de expirar um temporizador de uma única vez, deve ser reiniciado através de tx_timer_change antes de poder ser ativado novamente.</span><span class="sxs-lookup"><span data-stu-id="669f3-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="669f3-2760">**auto_activate**: Determina se o temporizador é ativado automaticamente durante a criação.</span><span class="sxs-lookup"><span data-stu-id="669f3-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="669f3-2761">Se este valor for **TX_AUTO_ACTIVATE** (0x01), o temporizador torna-se ativo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="669f3-2762">Caso contrário, se o valor **TX_NO_ACTIVATE** (0x00) for selecionado, o temporizador é criado num estado não ativo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="669f3-2763">Neste caso, é necessária uma chamada de serviço **_tx_timer_activate_** subsequente para iniciar o temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2764">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2764">Return Values</span></span>

- <span data-ttu-id="669f3-2765">**TX_SUCCESS**: (0x00) Criação de temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="669f3-2766">TX_TIMER_ERROR: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="669f3-2767">Ou o ponteiro é NULO ou o temporizador já está criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="669f3-2768">TX_TICK_ERROR: (0x16) Valor inválido (a zero) fornecido para os tiques iniciais.</span><span class="sxs-lookup"><span data-stu-id="669f3-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="669f3-2769">TX_ACTIVATE_ERROR: (0x17) Ativação inválida selecionada.</span><span class="sxs-lookup"><span data-stu-id="669f3-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="669f3-2770">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2771">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2771">Allowed From</span></span>

<span data-ttu-id="669f3-2772">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2773">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2773">Preemption Possible</span></span>

<span data-ttu-id="669f3-2774">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2775">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2776">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2776">See Also</span></span>

- <span data-ttu-id="669f3-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2777">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2778">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2780">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="669f3-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="669f3-2785">Temporizador de aplicação desativado</span><span class="sxs-lookup"><span data-stu-id="669f3-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2786">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="669f3-2787">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2787">Description</span></span>

<span data-ttu-id="669f3-2788">Este serviço desativa o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="669f3-2789">Se o temporizador já estiver desativado, este serviço não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="669f3-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2790">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2790">Parameters</span></span> 

- <span data-ttu-id="669f3-2791">**timer_ptr**: Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2792">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2792">Return Values</span></span>

- <span data-ttu-id="669f3-2793">**TX_SUCCESS**: (0x00) Desativação do temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="669f3-2794">TX_TIMER_ERROR: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2795">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2795">Allowed From</span></span>

<span data-ttu-id="669f3-2796">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2797">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2797">Preemption Possible</span></span>

<span data-ttu-id="669f3-2798">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2799">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2800">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2800">See Also</span></span>

- <span data-ttu-id="669f3-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2801">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2802">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2803">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2804">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="669f3-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2808">tx_timer_delete</span></span>

<span data-ttu-id="669f3-2809">Eliminar temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="669f3-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2810">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2811">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2811">Description</span></span>

<span data-ttu-id="669f3-2812">Este serviço elimina o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2813">É da responsabilidade da aplicação impedir a utilização de um temporizador eliminado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2814">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2814">Parameters</span></span> 

- <span data-ttu-id="669f3-2815">**timer_ptr**: Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2816">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2816">Return Values</span></span>

- <span data-ttu-id="669f3-2817">**TX_SUCCESS**: (0x00) Eliminação do temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="669f3-2818">TX_TIMER_ERROR: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="669f3-2819">TX_CALLER_ERROR: (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="669f3-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2820">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2820">Allowed From</span></span>

<span data-ttu-id="669f3-2821">Fios</span><span class="sxs-lookup"><span data-stu-id="669f3-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2822">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2822">Preemption Possible</span></span>

<span data-ttu-id="669f3-2823">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2824">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2825">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2825">See Also</span></span>

- <span data-ttu-id="669f3-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2826">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2827">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2828">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="669f3-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2833">tx_timer_info_get</span></span>

<span data-ttu-id="669f3-2834">Recuperar informações sobre um temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="669f3-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2835">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="669f3-2836">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2836">Description</span></span>

<span data-ttu-id="669f3-2837">Este serviço obtém informações sobre o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2838">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2838">Parameters</span></span>

- <span data-ttu-id="669f3-2839">**timer_ptr**: Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="669f3-2840">**nome**: Ponteiro para destino para o ponteiro para o nome do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="669f3-2841">**ativo**: Ponteiro para destino para a indicação ativa do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="669f3-2842">Se o temporizador estiver inativo ou este serviço for chamado do temporizador em si, é devolvido um valor TX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="669f3-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="669f3-2843">Caso contrário, se o temporizador estiver ativo, é devolvido um valor TX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="669f3-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="669f3-2844">**remaining_ticks**: Ponter para o destino para o número de carraças de temporizador que sobrou antes do temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="669f3-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="669f3-2845">**reschedule_ticks**: Ponter para o destino para o número de carraças tempores que serão usadas para reagendar automaticamente este temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="669f3-2846">Se o valor for zero, então o temporizador é um tiro e não será reagendado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="669f3-2847">**next_timer**: Ponter para o destino para o ponteiro do temporizador de aplicação criado seguinte.</span><span class="sxs-lookup"><span data-stu-id="669f3-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="669f3-2848">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2849">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2849">Return Values</span></span>

- <span data-ttu-id="669f3-2850">**TX_SUCCESS**: (0x00) Recuperação de informações de temporizador bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="669f3-2851">TX_TIMER_ERROR: (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2852">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2852">Allowed From</span></span>

<span data-ttu-id="669f3-2853">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="669f3-2854">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="669f3-2854">Preemption Possible</span></span>

<span data-ttu-id="669f3-2855">No</span><span class="sxs-lookup"><span data-stu-id="669f3-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2856">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2857">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2857">See Also</span></span>

- <span data-ttu-id="669f3-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2858">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2859">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2860">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2862">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="669f3-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="669f3-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="669f3-2867">Obtenha informações de desempenho do temporizador</span><span class="sxs-lookup"><span data-stu-id="669f3-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2868">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="669f3-2869">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2869">Description</span></span>

<span data-ttu-id="669f3-2870">Este serviço recupera informações de desempenho sobre o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2871">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_TIMER_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2872">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2872">Parameters</span></span> 

- <span data-ttu-id="669f3-2873">**timer_ptr**: Ponteiro para temporizador previamente criado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="669f3-2874">**activa-** Ponteiro para destino para o número de pedidos de ativação realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="669f3-2875">**reativa:** Ponteiro para o destino para o número de reativações automáticas efetuadas neste temporizador periódico.</span><span class="sxs-lookup"><span data-stu-id="669f3-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="669f3-2876">**desativa**: Ponteiro para o destino para o número de pedidos de desativação realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="669f3-2877">**expirações**: Ponteiro para o destino para o número de expirações deste temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="669f3-2878">**expiration_adjusts**: Ponteiro para o destino para o número de ajustes internos de validade realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="669f3-2879">Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).</span><span class="sxs-lookup"><span data-stu-id="669f3-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2880">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2881">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2881">Return Values</span></span>

- <span data-ttu-id="669f3-2882">**TX_SUCCESS**: (0x00) Desempenho do temporizador de sucesso obtém.</span><span class="sxs-lookup"><span data-stu-id="669f3-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="669f3-2883">**TX_PTR_ERROR:**(0x03) Ponteiro temporizador inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="669f3-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2885">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2885">Allowed From</span></span>

<span data-ttu-id="669f3-2886">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2887">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2888">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2888">See Also</span></span>

- <span data-ttu-id="669f3-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2889">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2890">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2891">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2893">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="669f3-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="669f3-2897">Obtenha informações sobre o desempenho do sistema do temporizador</span><span class="sxs-lookup"><span data-stu-id="669f3-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2898">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="669f3-2899">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2899">Description</span></span>

<span data-ttu-id="669f3-2900">Este serviço obtém informações de desempenho sobre todos os temporizadores de aplicação no sistema.</span><span class="sxs-lookup"><span data-stu-id="669f3-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2901">A biblioteca e aplicação ThreadX SMP devem ser construídas com **TX_TIMER_ENABLE_PERFORMANCE_INFO** definidas para este serviço devolver informações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="669f3-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2902">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2902">Parameters</span></span>

- <span data-ttu-id="669f3-2903">**activa-** Ponteiro para destino para o número total de pedidos de ativação realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="669f3-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="669f3-2904">**reativa:** Ponteiro para o destino para o número total de reativação automática efetuada em todos os temporizadores periódicos.</span><span class="sxs-lookup"><span data-stu-id="669f3-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="669f3-2905">**desativa**: Ponteiro para destino para o número total de pedidos de desativação realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="669f3-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="669f3-2906">**expirações**: Ponteiro para o destino para o número total de expirações em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="669f3-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="669f3-2907">**expiration_adjusts**: Ponter para o destino para o número total de ajustes internos de validade realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="669f3-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="669f3-2908">Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).</span><span class="sxs-lookup"><span data-stu-id="669f3-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2909">O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.</span><span class="sxs-lookup"><span data-stu-id="669f3-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2910">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2910">Return Values</span></span>

- <span data-ttu-id="669f3-2911">**TX_SUCCESS**: (0x00) Obtém-se um desempenho do sistema do sistema do temporizador de sucesso.</span><span class="sxs-lookup"><span data-stu-id="669f3-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="669f3-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="669f3-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2913">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2913">Allowed From</span></span>

<span data-ttu-id="669f3-2914">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="669f3-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2915">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="669f3-2916">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2916">See Also</span></span>

- <span data-ttu-id="669f3-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="669f3-2917">tx_timer_activate</span></span>
- <span data-ttu-id="669f3-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="669f3-2918">tx_timer_change</span></span>
- <span data-ttu-id="669f3-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="669f3-2919">tx_timer_create</span></span>
- <span data-ttu-id="669f3-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="669f3-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="669f3-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="669f3-2921">tx_timer_delete</span></span>
- <span data-ttu-id="669f3-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="669f3-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="669f3-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="669f3-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="669f3-2925">Excluir a execução do temporizador num conjunto de núcleos</span><span class="sxs-lookup"><span data-stu-id="669f3-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2926">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="669f3-2927">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2927">Description</span></span>

<span data-ttu-id="669f3-2928">Esta função exclui o temporizador especificado de executar no núcleo(s) especificado no mapa de bits chamado "*exclusion_map*."</span><span class="sxs-lookup"><span data-stu-id="669f3-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="669f3-2929">Cada bit em "*exclusion_map*" representa um núcleo (bit 0 representa núcleo 0, etc.).</span><span class="sxs-lookup"><span data-stu-id="669f3-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="669f3-2930">Se a broca estiver definida, o núcleo correspondente é excluído da execução do temporizador especificado.</span><span class="sxs-lookup"><span data-stu-id="669f3-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="669f3-2931">A utilização da exclusão do processador pode causar um processamento adicional na linha para a lógica de mapeamento do núcleo, a fim de encontrar a correspondência ideal.</span><span class="sxs-lookup"><span data-stu-id="669f3-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="669f3-2932">Este processamento é limitado pelo número de fios prontos.</span><span class="sxs-lookup"><span data-stu-id="669f3-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2933">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2933">Parameters</span></span>

- <span data-ttu-id="669f3-2934">**timer_ptr**: Ponteiro para temporizador para alterar a exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="669f3-2935">**exclusion_map:** Mapa de bits onde um pouco de assento indica que esse núcleo está excluído.</span><span class="sxs-lookup"><span data-stu-id="669f3-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="669f3-2936">O fornecimento de um valor de 0 permite que o temporizador execute em qualquer núcleo (predefinição).</span><span class="sxs-lookup"><span data-stu-id="669f3-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2937">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2937">Return Values</span></span>

- <span data-ttu-id="669f3-2938">**TX_SUCCESS** (0x00) Exclusão do núcleo bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="669f3-2939">**TX_TIMER_ERROR** (0x0E) Ponteiro temporizador inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2940">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2940">Allowed From</span></span>

<span data-ttu-id="669f3-2941">Inicialização, ISRs, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2942">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="669f3-2943">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2943">See Also</span></span>

- <span data-ttu-id="669f3-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="669f3-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="669f3-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="669f3-2946">Obtém a exclusão atual do núcleo do temporizador</span><span class="sxs-lookup"><span data-stu-id="669f3-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="669f3-2947">Prototype</span><span class="sxs-lookup"><span data-stu-id="669f3-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="669f3-2948">Descrição</span><span class="sxs-lookup"><span data-stu-id="669f3-2948">Description</span></span>

<span data-ttu-id="669f3-2949">Esta função devolve a lista de exclusão do núcleo atual.</span><span class="sxs-lookup"><span data-stu-id="669f3-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="669f3-2950">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669f3-2950">Parameters</span></span>

- <span data-ttu-id="669f3-2951">**timer_ptr**: Ponteiro para temporizador a partir do qual recuperar a exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="669f3-2952">**exclusion_map_ptr**: Destino para o mapa atual do bit de exclusão do núcleo.</span><span class="sxs-lookup"><span data-stu-id="669f3-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="669f3-2953">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="669f3-2953">Return Values</span></span>

- <span data-ttu-id="669f3-2954">TX_SUCCESS: (0x00) Recuperação bem sucedida da exclusão do núcleo do temporizador.</span><span class="sxs-lookup"><span data-stu-id="669f3-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="669f3-2955">TX_TIMER_ERROR: (0x0E) Ponteiro temporizador inválido.</span><span class="sxs-lookup"><span data-stu-id="669f3-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="669f3-2956">TX_PTR_ERROR: (0x03) Ponteiro de destino de exclusão inválida.</span><span class="sxs-lookup"><span data-stu-id="669f3-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="669f3-2957">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="669f3-2957">Allowed From</span></span>

<span data-ttu-id="669f3-2958">Inicialização, ISRs, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="669f3-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="669f3-2959">Exemplo</span><span class="sxs-lookup"><span data-stu-id="669f3-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="669f3-2960">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669f3-2960">See Also</span></span>

- <span data-ttu-id="669f3-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="669f3-2961">tx_timer_smp_core_exclude</span></span>