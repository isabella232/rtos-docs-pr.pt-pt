---
title: Capítulo 6 - Azure RTOS ThreadX trace eventos
description: Este capítulo descreve os eventos Azure RTOS ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827554"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="2ac79-103">Capítulo 6 - Azure RTOS ThreadX trace eventos</span><span class="sxs-lookup"><span data-stu-id="2ac79-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="2ac79-104">Este capítulo descreve os eventos Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="2ac79-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="2ac79-105">Lista de eventos e ícones</span><span class="sxs-lookup"><span data-stu-id="2ac79-105">List of Events and Icons</span></span>

<span data-ttu-id="2ac79-106">Segue-se uma lista de eventos Da ThreadX apresentados pela TraceX:</span><span class="sxs-lookup"><span data-stu-id="2ac79-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="2ac79-107">**Ícone**</span><span class="sxs-lookup"><span data-stu-id="2ac79-107">**Icon**</span></span>                         | <span data-ttu-id="2ac79-108">**Significado**</span><span class="sxs-lookup"><span data-stu-id="2ac79-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![Ícone de retoma de fio interno](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="2ac79-110">Currículo interno da linha</span><span class="sxs-lookup"><span data-stu-id="2ac79-110">Internal thread resume</span></span>  |
| ![Ícone de suspensão de fio interno](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="2ac79-112">Suspensão do fio interno</span><span class="sxs-lookup"><span data-stu-id="2ac79-112">Internal thread suspend</span></span> |
| ![Interrupção de função rotina introduzir ícone](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="2ac79-114">Interrupção rotina de serviço (ISR) Entrar</span><span class="sxs-lookup"><span data-stu-id="2ac79-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![Ícone de saída de rotina de serviço de interrupção](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="2ac79-116">Interrupção de rotina de serviço (ISR) saída</span><span class="sxs-lookup"><span data-stu-id="2ac79-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![Ícone de fatia de tempo interna](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="2ac79-118">Corte de tempo interna</span><span class="sxs-lookup"><span data-stu-id="2ac79-118">Internal time-slice</span></span> |
| ![Ícone de execução](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="2ac79-120">Em Execução</span><span class="sxs-lookup"><span data-stu-id="2ac79-120">Running</span></span> |
| ![Ícone de atribuição de piscina de bloco](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="2ac79-122">**Atribuição de piscina de blocos** *(tx_block_allocate)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![Bloco de piscina criar ícone](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="2ac79-124">**Criação de piscina de** blocos *(tx_block_pool_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![Ícone de excluir piscina de bloco](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="2ac79-126">**Excluir de piscina de blocos** *(tx_block_pool_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![Informações de piscina de blocos obter ícone](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="2ac79-128">**Informações de piscina de blocos obtêm** *(tx_block_pool_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![Informações de desempenho da piscina de blocos obter con](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="2ac79-130">**Informações de desempenho do pool de blocos obtêm** *(tx_block_pool_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema de piscina de blocos obtenham ícone](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="2ac79-132">**Informações de desempenho do sistema de piscina de blocos obtêm** *(tx_block_pool_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![Ícone de prioridade de piscina de bloco](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="2ac79-134">**Prioridades de piscina de blocos** *(tx_block_pool_prioritize)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![Desbloqueio de bloco para ícone de piscina](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="2ac79-136">**Desbloqueio do bloco para piscina** *(tx_block_release)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![Byte pool alocar ícone de memória](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="2ac79-138">**Byte pool alocar memória** *(tx_byte_allocate)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![Byte pool criar ícone](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="2ac79-140">**Byte pool create** *(tx_byte_pool_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![Ícone de exclusão da piscina byte](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="2ac79-142">**Byte pool delete** *(tx_byte_pool_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![Informações de piscina byte obter ícone](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="2ac79-144">**Informações da piscina byte obtêm** *(tx_byte_pool_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![Informações de desempenho da piscina byte obter ícone](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="2ac79-146">**Byte pool informações de desempenho get** *(tx_byte_pool_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema de piscina byte recebem ícone](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="2ac79-148">**Informações de desempenho do sistema de piscina byte obtêm** *(tx_byte_pool_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\*Byte pool priorizar ícone](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="2ac79-150">**Prioridades da piscina byte** *(tx_byte_pool_prioritize)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![Byte memory release para ícone de piscina](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="2ac79-152">**Byte memory release para piscina** *(tx_byte_release)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![Bandeiras do evento criam ícone](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="2ac79-154">**Bandeiras de eventos criam** *(tx_event_flags_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![Bandeiras do evento apagam ícone](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="2ac79-156">**Bandeiras do evento apagam** *(tx_event_flags_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![Bandeiras do evento recebem ícone](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="2ac79-158">**Bandeiras do evento recebem** *(tx_event_flags_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![Informações de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="2ac79-160">**Informações de bandeiras de eventos obtêm** *(tx_event_flags_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![Informações de desempenho de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="2ac79-162">**As informações de desempenho das bandeiras do evento obtêm** *(tx_event_flags_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema de bandeiras de eventos obtenham ícone](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="2ac79-164">**As informações de desempenho do sistema de bandeiras de eventos obtêm** *(tx_event_flags_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![Ícone de conjunto de bandeiras de evento](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="2ac79-166">**Conjunto de bandeiras de eventos** *(tx_event_flags_set)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![Conjunto de bandeiras de eventos ícone de notificação](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="2ac79-168">**As bandeiras do evento notificam** *(tx_event_flags_set_notify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![Interromper o ícone de ativação/desativação](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="2ac79-170">**Interromper ativar/desativar** *(tx_interrupt_control)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![Mutex criar ícone](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="2ac79-172">**Criação mutex** *(tx_mutex_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![Ícone de exclusão de mutex](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="2ac79-174">**Eliminação de mutaxos** *(tx_mutex_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![Mutex obter ícone](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="2ac79-176">**Mutex get** *(tx_mutex_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![Informações mutex obtêm ícone](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="2ac79-178">**Informações mutex obtêm** *(tx_mutex_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![Informações de desempenho de Mutex obtêm ícone](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="2ac79-180">**Informações de desempenho mutex obtêm** *(tx_mutex_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema mutex obtêm ícone](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="2ac79-182">**Informações de desempenho do sistema Mutex obtêm** *(tx_mutex_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![Ícone de prioridades de Mutex](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="2ac79-184">**Prioridades mutex** *(tx_mutex_prioritize)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![Mutex colocar ícone](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="2ac79-186">**Mutex colocado** *(tx_mutex_put)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![Fila criar ícone](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="2ac79-188">**Criação de fila** *(tx_queue_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![Ícone de exclusão de fila](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="2ac79-190">**Excluir de filas** *(tx_queue_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![Ícone de descarga de fila](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="2ac79-192">**Flush de fila** *(tx_queue_flush)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![Ícone de envio de fila frontal](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="2ac79-194">**Envio frontal de fila** *(tx_queue_front_send)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![Informações de fila recebem ícone](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="2ac79-196">**Informações de fila obtêm** *(tx_queue_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![Informações de desempenho da fila obtêm ícone](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="2ac79-198">**Informações de desempenho da fila obtêm** *(tx_queue_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema de fila recebem ícone](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="2ac79-200">**Informações de desempenho do sistema de fila obtêm** *(tx_queue_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![Ícone de prioridade de fila](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="2ac79-202">**Prioridades de fila** *(tx_queue_prioritize)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![Ícone de mensagem de receção de fila](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="2ac79-204">**Mensagem de receção de fila** *(tx_queue_receive)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![Ícone de mensagem de envio de fila](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="2ac79-206">**Mensagem de envio de fila** *(tx_queue_send)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![Fila enviar ícone de notificação](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="2ac79-208">**Fila enviar notificação** *(tx_queue_send_notify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![Teto de semáforo colocar ícone](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="2ac79-210">**Teto de semáforo colocado** *(tx_semaphore_ceiling_put)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![Semáforo criar ícone](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="2ac79-212">**Criação de semáforos** *(tx_semaphore_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![Ícone de exclusão de semáforo](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="2ac79-214">**Eliminação de semáforos** *(tx_semaphore_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![Semáforo obter ícone](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="2ac79-216">**Semaphore get** *(tx_semaphore_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![Informações de semáforo recebem ícone](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="2ac79-218">**Informações de semáforos obtêm** *(tx_semaphore_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![Informações de desempenho de semáforo obtêm ícone](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="2ac79-220">**Informações de desempenho de semáforos obtêm** *(tx_semaphroe_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![Informações de desempenho do sistema de semáforos recebem ícone](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="2ac79-222">**Informações de desempenho do sistema semáforo obtêm** *(tx_semaphore_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![Semáforo prioriza ícone](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="2ac79-224">**Prioridades de semáforo** *(tx_semaphore_prioritize)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![Semáforo colocar ícone](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="2ac79-226">**Semaphore put** *(tx_semaphore_put)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![Semáforo colocar ícone de notificação](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="2ac79-228">**Semáforo colocar notificação** *(tx_semaphore_put_notify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![Ícone de criação de fio](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="2ac79-230">**Criação de fios** *(tx_thread_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![Ícone de exclusão de fio](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="2ac79-232">**Eliminação de fios** *(tx_thread_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![Ícone de notificação de saída/entrada de fio](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="2ac79-234">**Notificação de saída/entrada de fio** *(tx_thread_entry_exit_notify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![Ícone de identificação de fio](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="2ac79-236">**Identificação de** fios *(tx_thread_identify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![Informações de fio obter ícone](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="2ac79-238">**Informações sobre fios obtêm** *(tx_thread_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![Informações de desempenho do fio obter ícone](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="2ac79-240">**Informações de desempenho do fio obtêm** *(tx_thread_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![Informações do sistema de desempenho do fio obtêm ícone](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="2ac79-242">**Informações do sistema de desempenho de fio obtêm** *(tx_thread_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![Ícone de mudança de mudança de preempção de fio](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="2ac79-244">**Alteração da preempção do fio** *(tx_thread_preemption_change)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![Ícone de mudança de prioridade de fio](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="2ac79-246">**Alteração prioritária do fio** *(tx_thread_priority_change)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![Ícone de renúncia de fio](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="2ac79-248">**Renúncia à linha** *(tx_thread_relinquish)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![Ícone de reset de fio](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="2ac79-250">**Reset de fio** *(tx_thread_reset)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\*Ícone de currículo de fio](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="2ac79-252">**Resumo do fio** (\**tx_thread_resume)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![Ícone de sono de fio](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="2ac79-254">**Thread Sleep** *(tx_thread_sleep)*\*</span><span class="sxs-lookup"><span data-stu-id="2ac79-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![Ícone de notificação de erro de pilha de fio](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="2ac79-256">**Notificação de erro de pilha de fio** *(tx_thread_stack_error_notify)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![Ícone de suspensão de fio](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="2ac79-258">**Suspensão do** fio *(tx_thread_suspend)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![Ícone de terminação de fio](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="2ac79-260">**Fim da linha** *(tx_thread_terminate)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![Ícone de mudança de fatia de tempo de fio](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="2ac79-262">**Alteração da fatia de tempo** do fio *(tx_thread_time_slice_change)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![Ícone de aborto de espera de fio](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="2ac79-264">**Thread wait abort** *(tx_thread_wait_abort)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![Tempo obter ícone](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="2ac79-266">**Time get** *(tx_time_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-266">**Time get** (*tx_time_get*)</span></span> |
| ![Ícone de conjunto de tempo](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="2ac79-268">**Tempo definido** *(tx_time_set)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-268">**Time set** (*tx_time_set*)</span></span> |
| ![\*Ícone de ativação do temporizador](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="2ac79-270">**Ativador de temporizador** *(tx_timer_activate)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![Ícone de mudança de temporizador](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="2ac79-272">**Alteração do temporizador** *(tx_timer_change)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![Ícone de criação de temporizador](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="2ac79-274">**Criação do temporizador** *(tx_timer_create)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![Ícone de desativado temporizador](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="2ac79-276">**Temporizador desativado** *(tx_timer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![Ícone de eliminação do temporizador](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="2ac79-278">**Apagador do temporizador** *(tx_timer_delete)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![Informação de temporizador obter ícone](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="2ac79-280">**Informações de temporizador obtêm** *(tx_timer_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![Informações de desempenho do temporizador obtêm ícone](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="2ac79-282">**Informações de desempenho do temporizador obtêm** *(tx_timer_performance_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\*Informação do sistema de desempenho temporizador obter ícone](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="2ac79-284">**Informações do sistema de desempenho do temporizador obtêm** *(tx_timer_performance_system_info_get)*</span><span class="sxs-lookup"><span data-stu-id="2ac79-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="2ac79-286">**Evento definido pelo utilizador** (ver capítulo 10)</span><span class="sxs-lookup"><span data-stu-id="2ac79-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="2ac79-287">Descrições do evento</span><span class="sxs-lookup"><span data-stu-id="2ac79-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="2ac79-288">Currículo interno da linha</span><span class="sxs-lookup"><span data-stu-id="2ac79-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="2ac79-289">Currículo interno da linha</span><span class="sxs-lookup"><span data-stu-id="2ac79-289">Internal thread resume</span></span>

<span data-ttu-id="2ac79-290">**Ícone** ![ Ícone de retoma de fio interno](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="2ac79-291">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-291">**Description**</span></span>

<span data-ttu-id="2ac79-292">Este evento representa o processamento interno na ThreadX que retoma um fio para execução.</span><span class="sxs-lookup"><span data-stu-id="2ac79-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="2ac79-293">Se o fio especificado for a maior prioridade e o limiar de pré-substituição não bloquear a sua execução, o sistema começará a executar este fio recém-pronto.</span><span class="sxs-lookup"><span data-stu-id="2ac79-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="2ac79-294">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-294">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-295">Info Campo 1: Ponteiro para o fio que está a ser retomado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="2ac79-296">Info Field 2: Estado anterior da linha a ser retomada, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2ac79-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="2ac79-297">Estado do fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-297">Thread state</span></span>                     | <span data-ttu-id="2ac79-298">Valor</span><span class="sxs-lookup"><span data-stu-id="2ac79-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="2ac79-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="2ac79-299">TX_READY</span></span>                         | <span data-ttu-id="2ac79-300">0</span><span class="sxs-lookup"><span data-stu-id="2ac79-300">0</span></span>       |
  |  <span data-ttu-id="2ac79-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="2ac79-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="2ac79-302">1</span><span class="sxs-lookup"><span data-stu-id="2ac79-302">1</span></span>       |
  |  <span data-ttu-id="2ac79-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="2ac79-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="2ac79-304">2</span><span class="sxs-lookup"><span data-stu-id="2ac79-304">2</span></span>       |
  |  <span data-ttu-id="2ac79-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="2ac79-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="2ac79-306">3</span><span class="sxs-lookup"><span data-stu-id="2ac79-306">3</span></span>       |
  |  <span data-ttu-id="2ac79-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="2ac79-307">TX_SLEEP</span></span>                         | <span data-ttu-id="2ac79-308">4</span><span class="sxs-lookup"><span data-stu-id="2ac79-308">4</span></span>       |
  |  <span data-ttu-id="2ac79-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="2ac79-310">5</span><span class="sxs-lookup"><span data-stu-id="2ac79-310">5</span></span>       |
  |  <span data-ttu-id="2ac79-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="2ac79-312">6</span><span class="sxs-lookup"><span data-stu-id="2ac79-312">6</span></span>       |
  |  <span data-ttu-id="2ac79-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="2ac79-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="2ac79-314">7</span><span class="sxs-lookup"><span data-stu-id="2ac79-314">7</span></span>       |
  |  <span data-ttu-id="2ac79-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="2ac79-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="2ac79-316">8</span><span class="sxs-lookup"><span data-stu-id="2ac79-316">8</span></span>       |
  |  <span data-ttu-id="2ac79-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="2ac79-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="2ac79-318">9</span><span class="sxs-lookup"><span data-stu-id="2ac79-318">9</span></span>       |
  |  <span data-ttu-id="2ac79-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="2ac79-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="2ac79-320">12</span><span class="sxs-lookup"><span data-stu-id="2ac79-320">12</span></span>      |
  |  <span data-ttu-id="2ac79-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="2ac79-322">13</span><span class="sxs-lookup"><span data-stu-id="2ac79-322">13</span></span>      |

- <span data-ttu-id="2ac79-323">Info Field 3: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="2ac79-324">Info Field 4: Ponteiro para o próximo fio de prioridade máxima a executar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="2ac79-325">Suspensão do fio interno</span><span class="sxs-lookup"><span data-stu-id="2ac79-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="2ac79-326">Suspensão do fio interno</span><span class="sxs-lookup"><span data-stu-id="2ac79-326">Internal thread suspend</span></span>

<span data-ttu-id="2ac79-327">**Ícone** ![ Ícone de suspensão de fio interno](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="2ac79-328">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-328">**Description**</span></span>

<span data-ttu-id="2ac79-329">Este evento representa o processamento interno na ThreadX que suspende a execução de um fio.</span><span class="sxs-lookup"><span data-stu-id="2ac79-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="2ac79-330">O próximo fio prioritário pronto para a execução é colocado no quarto campo de informação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="2ac79-331">Se este valor for NU, não há outro fio pronto para a execução e o sistema está inativo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="2ac79-332">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-332">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-333">Info Campo 1: Ponteiro para a linha suspensa.</span><span class="sxs-lookup"><span data-stu-id="2ac79-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="2ac79-334">Info Field 2: Estado novo da linha suspensa, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2ac79-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="2ac79-335">Estado do fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-335">Thread state</span></span>                     | <span data-ttu-id="2ac79-336">Valor</span><span class="sxs-lookup"><span data-stu-id="2ac79-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="2ac79-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="2ac79-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="2ac79-338">1</span><span class="sxs-lookup"><span data-stu-id="2ac79-338">1</span></span>       |
  |  <span data-ttu-id="2ac79-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="2ac79-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="2ac79-340">2</span><span class="sxs-lookup"><span data-stu-id="2ac79-340">2</span></span>       |
  |  <span data-ttu-id="2ac79-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="2ac79-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="2ac79-342">3</span><span class="sxs-lookup"><span data-stu-id="2ac79-342">3</span></span>       |
  |  <span data-ttu-id="2ac79-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="2ac79-343">TX_SLEEP</span></span>                         | <span data-ttu-id="2ac79-344">4</span><span class="sxs-lookup"><span data-stu-id="2ac79-344">4</span></span>       |
  |  <span data-ttu-id="2ac79-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="2ac79-346">5</span><span class="sxs-lookup"><span data-stu-id="2ac79-346">5</span></span>       |
  |  <span data-ttu-id="2ac79-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="2ac79-348">6</span><span class="sxs-lookup"><span data-stu-id="2ac79-348">6</span></span>       |
  |  <span data-ttu-id="2ac79-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="2ac79-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="2ac79-350">7</span><span class="sxs-lookup"><span data-stu-id="2ac79-350">7</span></span>       |
  |  <span data-ttu-id="2ac79-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="2ac79-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="2ac79-352">8</span><span class="sxs-lookup"><span data-stu-id="2ac79-352">8</span></span>       |
  |  <span data-ttu-id="2ac79-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="2ac79-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="2ac79-354">9</span><span class="sxs-lookup"><span data-stu-id="2ac79-354">9</span></span>       |
  |  <span data-ttu-id="2ac79-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="2ac79-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="2ac79-356">12</span><span class="sxs-lookup"><span data-stu-id="2ac79-356">12</span></span>      |
  |  <span data-ttu-id="2ac79-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="2ac79-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="2ac79-358">13</span><span class="sxs-lookup"><span data-stu-id="2ac79-358">13</span></span>      |

- <span data-ttu-id="2ac79-359">Info Field 3: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="2ac79-360">Info Field 4: Ponteiro para o próximo fio de prioridade máxima a executar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="2ac79-361">Se o NU, o sistema está inativo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="2ac79-362">Interrupção De Rotina de Serviço (ISR) insira</span><span class="sxs-lookup"><span data-stu-id="2ac79-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="2ac79-363">Insira ISR</span><span class="sxs-lookup"><span data-stu-id="2ac79-363">Enter ISR</span></span> 

<span data-ttu-id="2ac79-364">**Ícone** ![ Insira o ícone I S R](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="2ac79-365">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-365">**Description**</span></span>

<span data-ttu-id="2ac79-366">Este evento representa a entrada de uma Rotina de Serviço de Interrupção (ISR) na aplicação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="2ac79-367">A execução de rotina de serviço de interrupção continua até que o evento de saída do ISR ocorra.</span><span class="sxs-lookup"><span data-stu-id="2ac79-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="2ac79-368">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-368">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-369">Info Field 1: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="2ac79-370">Info Field 2: Número ISR definido pela aplicação (opcional).</span><span class="sxs-lookup"><span data-stu-id="2ac79-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="2ac79-371">Info Field 3: Contagem de interrupção aninhada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="2ac79-372">Info Campo 4: Preempção interna desativa bandeira.</span><span class="sxs-lookup"><span data-stu-id="2ac79-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="2ac79-373">Interrupção de rotina de serviço (ISR) saída</span><span class="sxs-lookup"><span data-stu-id="2ac79-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="2ac79-374">Saída ISR</span><span class="sxs-lookup"><span data-stu-id="2ac79-374">Exit ISR</span></span>

<span data-ttu-id="2ac79-375">**Ícone** ![ Ícone de saída I S R](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="2ac79-376">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-376">**Description**</span></span>

<span data-ttu-id="2ac79-377">Este evento representa a saída de uma Rotina de Serviço de Interrupção (ISR) na aplicação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="2ac79-378">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-378">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-379">Info Field 1: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="2ac79-380">Info Field 2: Número ISR definido pela aplicação (opcional).</span><span class="sxs-lookup"><span data-stu-id="2ac79-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="2ac79-381">Info Field 3: Contagem de interrupção aninhada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="2ac79-382">Info Campo 4: Preempção interna desativa bandeira.</span><span class="sxs-lookup"><span data-stu-id="2ac79-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="2ac79-383">Corte de tempo interna</span><span class="sxs-lookup"><span data-stu-id="2ac79-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="2ac79-384">Corte de tempo interna</span><span class="sxs-lookup"><span data-stu-id="2ac79-384">Internal time-slice</span></span>

<span data-ttu-id="2ac79-385">**Ícone** ![ Ícone de fatia de tempo interna](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="2ac79-386">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-386">**Description**</span></span>

<span data-ttu-id="2ac79-387">Este evento representa o processamento interno na ThreadX que realiza a operação de corte de tempo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="2ac79-388">O próximo fio da mesma prioridade é colocado no primeiro campo de informação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="2ac79-389">Se este valor for o mesmo que o fio atual, não foi realizada nenhuma fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="2ac79-390">Info Field 1: Ponteiro para o próximo fio a executar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="2ac79-391">Info Field 2: Contagem de interrupção aninhada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="2ac79-392">Info Campo 3: Preempção interna desativa bandeira.</span><span class="sxs-lookup"><span data-stu-id="2ac79-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="2ac79-393">Info Field 4: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="2ac79-394">Em Execução</span><span class="sxs-lookup"><span data-stu-id="2ac79-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="2ac79-395">Correndo em contexto</span><span class="sxs-lookup"><span data-stu-id="2ac79-395">Running in context</span></span>

<span data-ttu-id="2ac79-396">**Ícone** ![ Ícone de execução](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="2ac79-397">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-397">**Description**</span></span>

<span data-ttu-id="2ac79-398">Este evento representa correr dentro de um contexto de fio ou sistema ocioso.</span><span class="sxs-lookup"><span data-stu-id="2ac79-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="2ac79-399">É utilizado para ilustrar as alterações subsequentes no contexto como resultado de uma interrupção.</span><span class="sxs-lookup"><span data-stu-id="2ac79-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="2ac79-400">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-400">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-401">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-402">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-403">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-404">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="2ac79-405">Atribuição de Blocos</span><span class="sxs-lookup"><span data-stu-id="2ac79-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="2ac79-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="2ac79-406">tx_block_allocate</span></span>

<span data-ttu-id="2ac79-407">**Ícone** ![ Ícone de atribuição de bloco](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="2ac79-408">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-408">**Description**</span></span>

<span data-ttu-id="2ac79-409">Este evento representa a atribuição de um bloco de memória através de tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="2ac79-410">Se for bem sucedido, o endereço do bloco atribuído é devolvido no segundo campo de informação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="2ac79-411">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-411">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-412">Info Campo 1: Ponteiro para o bloco correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="2ac79-413">Info Campo 2: Ponteiro para o bloco de memória devolvido (se for bem sucedido).</span><span class="sxs-lookup"><span data-stu-id="2ac79-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="2ac79-414">Info Field 3: A opção de espera fornecida à chamada tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="2ac79-415">Info Field 4: Blocos restantes disponíveis na piscina após esta atribuição.</span><span class="sxs-lookup"><span data-stu-id="2ac79-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="2ac79-416">Criar piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="2ac79-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="2ac79-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-417">tx_block_pool_create</span></span>

<span data-ttu-id="2ac79-418">**Ícone** ![ Bloco de piscina criar ícone](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="2ac79-419">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-419">**Description**</span></span>

<span data-ttu-id="2ac79-420">Este evento representa a criação de um pool de blocos de memória através de tx_block_pool_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="2ac79-421">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-421">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-422">Info Campo 1: Ponteiro para o bloco de controlo correspondente da piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="2ac79-423">Info Campo 2: Ponteiro para a área de memória inicial da piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="2ac79-424">Info Field 3: O número de blocos na piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="2ac79-425">Info Field 4: O tamanho de cada bloco na piscina em bytes.</span><span class="sxs-lookup"><span data-stu-id="2ac79-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="2ac79-426">Excluir de piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="2ac79-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="2ac79-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-427">tx_block_pool_delete</span></span>

<span data-ttu-id="2ac79-428">**Ícone** ![ Ícone de excluir piscina de bloco](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="2ac79-429">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-429">**Description**</span></span>

<span data-ttu-id="2ac79-430">Este evento representa a eliminação de um conjunto de blocos de memória através de tx_block_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="2ac79-431">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-431">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-432">Info Field 1: Ponteiro para o bloco de controlo da piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="2ac79-433">Info Field 2: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="2ac79-434">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-435">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="2ac79-436">Informações de piscina de blocos obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="2ac79-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="2ac79-438">**Ícone** ![ Informações de piscina de blocos obter ícone](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="2ac79-439">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-439">**Description**</span></span>

<span data-ttu-id="2ac79-440">Este evento representa obter informações sobre um conjunto de blocos de memória através de tx_block_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="2ac79-441">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-441">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-442">Info Field 1: Ponteiro para o bloco de controlo da piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="2ac79-443">Info Field 2: Empilhar o valor do ponteiro durante a chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="2ac79-444">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-445">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="2ac79-446">Informações de desempenho do pool de blocos obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="2ac79-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="2ac79-448">**Ícone** ![ Informações de desempenho do pool de blocos obter ícone](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="2ac79-449">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-449">**Description**</span></span>

<span data-ttu-id="2ac79-450">Este evento representa obter informações de desempenho sobre um conjunto de blocos de memória através de tx_block_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="2ac79-451">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-451">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-452">Info Field 1: Ponteiro para o bloco de controlo da piscina.</span><span class="sxs-lookup"><span data-stu-id="2ac79-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="2ac79-453">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-454">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-455">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="2ac79-456">Bloquear informações do sistema de desempenho da piscina obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="2ac79-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-458">**Ícone** ![ Bloquear informações do sistema de desempenho do pool obter ícone](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="2ac79-459">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-459">**Description**</span></span>

<span data-ttu-id="2ac79-460">Este evento representa obter informações de desempenho sobre todos os pools de blocos de memória através de tx_block_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-461">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-461">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-462">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-463">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-464">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-465">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="2ac79-466">Priorização do Pool Block</span><span class="sxs-lookup"><span data-stu-id="2ac79-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="2ac79-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="2ac79-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="2ac79-468">**Ícone** ![ Ícone de prioridade de piscina de bloco](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="2ac79-469">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-469">**Description**</span></span>

<span data-ttu-id="2ac79-470">Este evento representa a colocação da linha suspensa de maior prioridade na parte da frente da lista de suspensão da piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="2ac79-471">Se isto for feito antes de chamar tx_block_release, a linha suspensa de maior prioridade receberá o bloco libertado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="2ac79-472">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-472">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-473">Info Field 1: Ponteiro de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="2ac79-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="2ac79-474">Info Campo 2: Número de fios suspensos nesta piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="2ac79-475">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="2ac79-476">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="2ac79-477">Lançamento do bloco</span><span class="sxs-lookup"><span data-stu-id="2ac79-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="2ac79-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="2ac79-478">tx_block_release</span></span>

<span data-ttu-id="2ac79-479">**Ícone** ![ Ícone de libertação de bloco](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="2ac79-480">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-480">**Description**</span></span>

<span data-ttu-id="2ac79-481">Este evento representa a libertação de um bloco previamente atribuído de volta ao bloco pool.</span><span class="sxs-lookup"><span data-stu-id="2ac79-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="2ac79-482">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-482">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-483">Info Field 1: Ponteiro de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="2ac79-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="2ac79-484">Info Field 2: Ponteiro para bloquear para soltar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="2ac79-485">Info Campo 3: Número de fios suspensos nesta piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="2ac79-486">Info Field 4: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="2ac79-487">Byte Alocado</span><span class="sxs-lookup"><span data-stu-id="2ac79-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="2ac79-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="2ac79-488">tx_byte_allocate</span></span>

<span data-ttu-id="2ac79-489">**Ícone** ![ Byte alocar ícone](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="2ac79-490">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-490">**Description**</span></span>

<span data-ttu-id="2ac79-491">Este evento representa a atribuição de memória através de tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="2ac79-492">Se for bem sucedido, o endereço da memória atribuída é devolvido no segundo campo de informação.</span><span class="sxs-lookup"><span data-stu-id="2ac79-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="2ac79-493">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-493">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-494">Info Campo 1: Ponteiro para a piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-495">Info Campo 2: Ponteiro para a memória devolvido (se for bem sucedido).</span><span class="sxs-lookup"><span data-stu-id="2ac79-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="2ac79-496">Info Campo 3: Número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="2ac79-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="2ac79-497">Info Field 4: A opção de espera fornecida à chamada tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="2ac79-498">Byte Pool Criar</span><span class="sxs-lookup"><span data-stu-id="2ac79-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="2ac79-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-499">tx_byte_pool_create</span></span>

<span data-ttu-id="2ac79-500">**Ícone** ![ Byte pool criar ícone](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="2ac79-501">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-501">**Description**</span></span>

<span data-ttu-id="2ac79-502">Este evento representa a criação de uma piscina byte via tx_byte_pool_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="2ac79-503">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-503">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-504">Info Campo 1: Ponteiro para a piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-505">Info Campo 2: Ponteiro para o início da área de memória.</span><span class="sxs-lookup"><span data-stu-id="2ac79-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="2ac79-506">Info Field 3: Número de bytes na piscina byte.</span><span class="sxs-lookup"><span data-stu-id="2ac79-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="2ac79-507">Info Field 4: O ponteiro da pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="2ac79-508">Byte Pool Delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="2ac79-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="2ac79-510">**Ícone** ![ Ícone de exclusão da piscina byte](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="2ac79-511">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-511">**Description**</span></span>

<span data-ttu-id="2ac79-512">Este evento representa a eliminação de uma piscina byte via tx_byte_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="2ac79-513">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-513">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-514">Info Campo 1: Ponteiro para a piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-515">Info Field 2: O ponteiro da pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="2ac79-516">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-517">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="2ac79-518">Informações da Piscina Byte Obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="2ac79-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="2ac79-520">**Ícone** ![ Informações de piscina byte obter ícone](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="2ac79-521">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-521">**Description**</span></span>

<span data-ttu-id="2ac79-522">Este evento representa obter informações de byte pool através de tx_byte_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="2ac79-523">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-523">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-524">Info Campo 1: Ponteiro para a piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-525">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-526">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-527">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="2ac79-528">Byte Pool Performance Info Get</span><span class="sxs-lookup"><span data-stu-id="2ac79-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="2ac79-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="2ac79-530">**Ícone** ![ Byte pool performance info obter ícone](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="2ac79-531">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-531">**Description**</span></span>

<span data-ttu-id="2ac79-532">Este evento representa obter informações de desempenho da piscina byte através de tx_byte_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="2ac79-533">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-533">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-534">Info Campo 1: Ponteiro para a piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-535">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-536">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-537">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="2ac79-538">Byte Pool Performance System Info Get</span><span class="sxs-lookup"><span data-stu-id="2ac79-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="2ac79-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-540">**Ícone** ![ Byte pool performance info obter ícone](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="2ac79-541">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-541">**Description**</span></span>

<span data-ttu-id="2ac79-542">Este evento representa obter informações do sistema de desempenho da piscina byte através de tx_byte_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-543">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-543">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-544">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-545">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-546">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-547">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="2ac79-548">Prioridades byte Pool</span><span class="sxs-lookup"><span data-stu-id="2ac79-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="2ac79-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="2ac79-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="2ac79-550">**Ícone** ![ Byte pool priorizar ícone](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="2ac79-551">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-551">**Description**</span></span>

<span data-ttu-id="2ac79-552">Este evento representa priorizar a lista de suspensão do byte pool através de tx_byte_pool_prioritize.</span><span class="sxs-lookup"><span data-stu-id="2ac79-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="2ac79-553">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-553">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-554">Info Field 1: Ponteiro para piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-555">Info Field 2: Número de fios atualmente suspensos na piscina byte.</span><span class="sxs-lookup"><span data-stu-id="2ac79-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="2ac79-556">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-557">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="2ac79-558">Lançamento byte</span><span class="sxs-lookup"><span data-stu-id="2ac79-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="2ac79-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="2ac79-559">tx_byte_release</span></span>

<span data-ttu-id="2ac79-560">**Ícone** ![ Ícone de lançamento byte](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="2ac79-561">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-561">**Description**</span></span>

<span data-ttu-id="2ac79-562">Este evento representa a libertação de um bloco de memória alocado a partir de uma piscina byte via tx_byte_release.</span><span class="sxs-lookup"><span data-stu-id="2ac79-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="2ac79-563">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-563">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-564">Info Field 1: Ponteiro para piscina byte correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="2ac79-565">Info Field 2: Ponteiro para memória de piscina byte previamente atribuída.</span><span class="sxs-lookup"><span data-stu-id="2ac79-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="2ac79-566">Info Campo 3: Número de fios suspensos nesta piscina byte.</span><span class="sxs-lookup"><span data-stu-id="2ac79-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="2ac79-567">Info Campo 4: Número de bytes de memória disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2ac79-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="2ac79-568">Bandeiras de eventos criar</span><span class="sxs-lookup"><span data-stu-id="2ac79-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="2ac79-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-569">tx_event_flags_create</span></span>

<span data-ttu-id="2ac79-570">**Ícone** ![ Bandeiras do evento criam ícone](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="2ac79-571">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-571">**Description**</span></span>

<span data-ttu-id="2ac79-572">Este evento representa a criação de um novo grupo de bandeiras de eventos através de tx_event_flags_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="2ac79-573">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-573">**Information Fields**</span></span> 
- <span data-ttu-id="2ac79-574">Info Field 1: Ponteiro para o bloco de controlo de grupo de bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="2ac79-575">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-576">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-577">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="2ac79-578">Bandeiras de eventos Eliminam</span><span class="sxs-lookup"><span data-stu-id="2ac79-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="2ac79-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-579">tx_event_flags_delete</span></span>

<span data-ttu-id="2ac79-580">**Ícone** ![ Bandeiras do evento apagam ícone](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="2ac79-581">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-581">**Description**</span></span>

<span data-ttu-id="2ac79-582">Este evento representa a eliminação de um grupo de bandeiras de eventos através de tx_event_flags_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="2ac79-583">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-583">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-584">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-585">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-586">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-587">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="2ac79-588">Bandeiras do evento obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="2ac79-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-589">tx_event_flags_get</span></span>

<span data-ttu-id="2ac79-590">**Ícone** ![ Ícone de bandeiras de evento gt](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="2ac79-591">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-591">**Description**</span></span>

<span data-ttu-id="2ac79-592">Este evento representa a recuperação de bandeiras de eventos de um grupo de bandeiras de eventos existentes através de tx_event_flags_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="2ac79-593">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-593">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-594">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-595">Info Field 2: Bandeiras de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="2ac79-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="2ac79-596">Info Field 3: Bandeiras de eventos atualmente definidas no grupo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="2ac79-597">Info Field 4: Opção solicitada nas bandeiras do evento recebe.</span><span class="sxs-lookup"><span data-stu-id="2ac79-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="2ac79-598">Informações de bandeiras de eventos obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="2ac79-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="2ac79-600">**Ícone** ![ Informações de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="2ac79-601">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-601">**Description**</span></span>

<span data-ttu-id="2ac79-602">Este evento representa a recuperação de informações sobre um grupo de bandeiras de eventos existente através de tx_event_flags_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="2ac79-603">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-603">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-604">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-605">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-606">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-607">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="2ac79-608">Informações de desempenho de bandeiras de eventos obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="2ac79-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="2ac79-610">**Ícone** ![ Informações de desempenho de bandeiras de evento recebem ícone](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="2ac79-611">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-611">**Description**</span></span>

<span data-ttu-id="2ac79-612">Este evento representa a recuperação de informações de desempenho relativas a um grupo de bandeiras de eventos existente através de tx_event_flags_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="2ac79-613">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-613">**Information Fields**</span></span> 
- <span data-ttu-id="2ac79-614">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-615">Info Field 2: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="2ac79-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="2ac79-616">Info Field 3: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="2ac79-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="2ac79-617">Info Field 4: Não utilizado</span><span class="sxs-lookup"><span data-stu-id="2ac79-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="2ac79-618">Informações do sistema de desempenho de bandeiras de eventos obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="2ac79-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-620">**Ícone** ![ Informações do sistema de desempenho de bandeiras de eventos recebem ícone](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="2ac79-621">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-621">**Description**</span></span>

<span data-ttu-id="2ac79-622">Este evento representa a recuperação de informações de desempenho relativas a um grupo de bandeiras de eventos existente através de tx_event_flags_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-623">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-623">**Information Fields**</span></span>
- <span data-ttu-id="2ac79-624">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-625">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-626">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-627">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="2ac79-628">Conjunto de bandeiras de evento</span><span class="sxs-lookup"><span data-stu-id="2ac79-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="2ac79-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="2ac79-629">tx_event_flags_set</span></span>

<span data-ttu-id="2ac79-630">**Ícone** ![ Ícone de conjunto de bandeiras de evento](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="2ac79-631">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-631">**Description**</span></span>

<span data-ttu-id="2ac79-632">Este evento representa a definição (ou desminagem) de bandeiras de eventos num grupo de bandeiras de eventos existente através de tx_event_flags_set.</span><span class="sxs-lookup"><span data-stu-id="2ac79-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="2ac79-633">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-633">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-634">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-635">Info Field 2: Bandeiras de evento a definir (ou claras).</span><span class="sxs-lookup"><span data-stu-id="2ac79-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="2ac79-636">Informação Campo 3: E ou ou a bandeira do evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="2ac79-637">Info Field 4: Número de fios suspensos no grupo de bandeira de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="2ac79-638">Conjunto de bandeiras de eventos notificar</span><span class="sxs-lookup"><span data-stu-id="2ac79-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="2ac79-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="2ac79-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="2ac79-640">**Ícone** ![ Conjunto de bandeiras de eventos ícone de notificação](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="2ac79-641">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-641">**Description**</span></span>

<span data-ttu-id="2ac79-642">Este evento representa o registo de uma chamada de notificação para qualquer operação de bandeira de evento num grupo de bandeiras de eventos existente através de tx_event_flags_set_notify.</span><span class="sxs-lookup"><span data-stu-id="2ac79-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="2ac79-643">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-643">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-644">Info Field 1: Ponteiro para grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="2ac79-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="2ac79-645">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-646">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-647">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="2ac79-648">Controlo de Interrupção</span><span class="sxs-lookup"><span data-stu-id="2ac79-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="2ac79-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="2ac79-649">tx_interrupt_control</span></span>

<span data-ttu-id="2ac79-650">**Ícone** ![ Ícone de controlo de interrupção](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="2ac79-651">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-651">**Description**</span></span>

<span data-ttu-id="2ac79-652">Este evento representa a alteração da postura de bloqueio de interrupção do processador através de tx_interrupt_control.</span><span class="sxs-lookup"><span data-stu-id="2ac79-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="2ac79-653">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-653">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-654">Info Field 1: Nova postura de interrupção.</span><span class="sxs-lookup"><span data-stu-id="2ac79-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="2ac79-655">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-656">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-657">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="2ac79-658">Criação Mutex</span><span class="sxs-lookup"><span data-stu-id="2ac79-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="2ac79-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-659">tx_mutex_create</span></span>

<span data-ttu-id="2ac79-660">**Ícone** ![ Mutex criar ícone](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="2ac79-661">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-661">**Description**</span></span>

<span data-ttu-id="2ac79-662">Este evento representa a criação de um mutex através de tx_mutex_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="2ac79-663">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-663">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-664">Info Field 1: Ponteiro para bloco de controlo de mutantes.</span><span class="sxs-lookup"><span data-stu-id="2ac79-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="2ac79-665">Info Field 2: Opção de herança prioritária</span><span class="sxs-lookup"><span data-stu-id="2ac79-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="2ac79-666">(TX_INHERIT ou TX_NO_INHERIT).</span><span class="sxs-lookup"><span data-stu-id="2ac79-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="2ac79-667">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-668">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="2ac79-669">Exclusão de mutex</span><span class="sxs-lookup"><span data-stu-id="2ac79-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="2ac79-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-670">tx_mutex_delete</span></span>

<span data-ttu-id="2ac79-671">**Ícone** ![ Ícone de exclusão de mutex](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="2ac79-672">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-672">**Description**</span></span>

<span data-ttu-id="2ac79-673">Este evento representa a eliminação de um mutex através de tx_mutex_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="2ac79-674">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-674">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-675">Info Field 1: Ponteiro para mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="2ac79-676">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-677">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-678">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="2ac79-679">Mutex Get</span><span class="sxs-lookup"><span data-stu-id="2ac79-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="2ac79-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-680">tx_mutex_get</span></span>

<span data-ttu-id="2ac79-681">**Ícone** ![ Mutex obter ícone](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="2ac79-682">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-682">**Description**</span></span>

<span data-ttu-id="2ac79-683">Este evento representa a obtenção de um mutex via tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="2ac79-684">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-684">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-685">Info Field 1: Ponteiro para mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="2ac79-686">Info Field 2: A opção de espera fornecida à chamada tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="2ac79-687">Info Field 3: Ponteiro para fio que detém o mutex (NULL implica que o mutex não é propriedade).</span><span class="sxs-lookup"><span data-stu-id="2ac79-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="2ac79-688">Info Field 4: Número de vezes que o fio de propriedade chamou tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="2ac79-689">Informação Mutex Obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="2ac79-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-690">tx_mutex_info_get</span></span>

<span data-ttu-id="2ac79-691">**Ícone** ![ Informações mutex obtêm ícone](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="2ac79-692">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-692">**Description**</span></span>

<span data-ttu-id="2ac79-693">Este evento representa a recuperação de informações de mutex através de tx_mutex_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="2ac79-694">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-694">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-695">Info Field 1: Ponteiro para mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="2ac79-696">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-697">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-698">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="2ac79-699">Informações de desempenho mutex obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="2ac79-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="2ac79-701">**Ícone** ![ Informações de desempenho de Mutex obtêm ícone](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="2ac79-702">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-702">**Description**</span></span>

<span data-ttu-id="2ac79-703">Este evento representa a recuperação de informações de desempenho de mutex através de tx_mutex_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="2ac79-704">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-704">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-705">Info Field 1: Ponteiro para mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="2ac79-706">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-707">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-708">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="2ac79-709">Informações do sistema de desempenho mutex obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="2ac79-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-711">**Ícone** ![ Informações do sistema de desempenho mutex obtêm ícone](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="2ac79-712">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-712">**Description**</span></span>

<span data-ttu-id="2ac79-713">Este evento representa a recuperação de informações de desempenho do sistema mutex através de tx_mutex_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-714">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-714">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-715">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-716">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-717">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-718">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="2ac79-719">Prioridades Mutex</span><span class="sxs-lookup"><span data-stu-id="2ac79-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="2ac79-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="2ac79-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="2ac79-721">**Ícone** ![ Ícone de prioridades de Mutex](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="2ac79-722">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-722">**Description**</span></span>

<span data-ttu-id="2ac79-723">Este evento representa dar prioridade à lista de suspensão do mutex através de tx_mutex_prioritize.</span><span class="sxs-lookup"><span data-stu-id="2ac79-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="2ac79-724">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-724">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-725">Info Field 1: Ponteiro para o mutex correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="2ac79-726">Info Field 2: Número de fios atualmente suspensos no mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="2ac79-727">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-728">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="2ac79-729">Mutex Put</span><span class="sxs-lookup"><span data-stu-id="2ac79-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="2ac79-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="2ac79-730">tx_mutex_put</span></span>

<span data-ttu-id="2ac79-731">**Ícone** ![ Mutex colocar ícone](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="2ac79-732">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-732">**Description**</span></span>

<span data-ttu-id="2ac79-733">Este evento representa a libertação de um mutex anteriormente propriedade através de tx_mutex_put.</span><span class="sxs-lookup"><span data-stu-id="2ac79-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="2ac79-734">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-734">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-735">Info Field 1: Ponteiro para o mutex correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="2ac79-736">Info Field 2: Ponteiro da linha proprietária do mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="2ac79-737">Info Field 3: Número de pedidos pendentes de mutex.</span><span class="sxs-lookup"><span data-stu-id="2ac79-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="2ac79-738">Info Field 4: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="2ac79-739">Criar fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="2ac79-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-740">tx_queue_create</span></span>

<span data-ttu-id="2ac79-741">**Ícone** ![ Fila criar ícone](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="2ac79-742">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-742">**Description**</span></span>

<span data-ttu-id="2ac79-743">Este evento representa a criação de uma fila de mensagens através de tx_queue_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="2ac79-744">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-744">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-745">Info Field 1: Ponteiro para o bloco de controlo da fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="2ac79-746">Info Field 2: Tamanho da mensagem – em termos de palavras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="2ac79-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="2ac79-747">Info Campo 3: Ponteiro para o início da área de memória da fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="2ac79-748">Info Campo 4: Número de bytes na área da memória da fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="2ac79-749">Excluir de fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="2ac79-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-750">tx_queue_delete</span></span>

<span data-ttu-id="2ac79-751">**Ícone** ![ Ícone de exclusão de fila](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="2ac79-752">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-752">**Description**</span></span>

<span data-ttu-id="2ac79-753">Este evento representa a eliminação de uma fila através de tx_queue_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="2ac79-754">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-754">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-755">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-756">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-757">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-758">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="2ac79-759">Flush de fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="2ac79-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="2ac79-760">tx_queue_flush</span></span>

<span data-ttu-id="2ac79-761">**Ícone** ![ Ícone de descarga de fila](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="2ac79-762">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-762">**Description**</span></span>

<span data-ttu-id="2ac79-763">Este evento representa o flushing (limpar todos os conteúdos da fila) de uma fila através de tx_queue_flush.</span><span class="sxs-lookup"><span data-stu-id="2ac79-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="2ac79-764">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-764">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-765">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-766">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-767">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-768">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="2ac79-769">Envio frontal de fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="2ac79-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="2ac79-770">tx_queue_front_send</span></span>

<span data-ttu-id="2ac79-771">**Ícone** ![ Ícone de envio de fila frontal](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="2ac79-772">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-772">**Description**</span></span>

<span data-ttu-id="2ac79-773">Este evento representa o envio de uma mensagem para a frente de uma fila via tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="2ac79-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="2ac79-774">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-774">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-775">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-776">Info Field 2: Ponteiro para o início da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2ac79-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="2ac79-777">Info Field 3: Opção de espera fornecida ao</span><span class="sxs-lookup"><span data-stu-id="2ac79-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="2ac79-778">tx_queue_front_send chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="2ac79-779">Info Campo 4: Número de mensagens já encostodas.</span><span class="sxs-lookup"><span data-stu-id="2ac79-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="2ac79-780">Informação de fila Obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="2ac79-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-781">tx_queue_info_get</span></span>

<span data-ttu-id="2ac79-782">**Ícone** ![ Informações de fila recebem ícone](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="2ac79-783">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-783">**Description**</span></span>

<span data-ttu-id="2ac79-784">Este evento representa obter informações sobre uma fila via tx_queue_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="2ac79-785">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-785">**Information Fields**</span></span> 
- <span data-ttu-id="2ac79-786">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-787">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-788">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-789">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="2ac79-790">Informações de desempenho de fila obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="2ac79-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="2ac79-792">**Ícone** ![ Informações de desempenho da fila recebem ícone](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="2ac79-793">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-793">**Description**</span></span>

<span data-ttu-id="2ac79-794">Este evento representa obter informações de desempenho sobre uma fila via tx_queue_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="2ac79-795">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-795">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-796">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-797">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-798">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-799">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="2ac79-800">Informações do sistema de desempenho da fila obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="2ac79-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-802">**Ícone** ![ Informações do sistema de desempenho da fila recebem ícone](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="2ac79-803">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-803">**Description**</span></span>

<span data-ttu-id="2ac79-804">Este evento representa obter informações sobre o desempenho do sistema sobre todas as filas do sistema.</span><span class="sxs-lookup"><span data-stu-id="2ac79-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="2ac79-805">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-805">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-806">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-807">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-808">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-809">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="2ac79-810">Prioridades de fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="2ac79-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="2ac79-811">tx_queue_prioritize</span></span>

<span data-ttu-id="2ac79-812">**Ícone** ![ Ícone de prioridade de fila](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="2ac79-813">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-813">**Description**</span></span>

<span data-ttu-id="2ac79-814">Este evento representa priorizar a lista de suspensão da fila através de tx_queue_prioritize.</span><span class="sxs-lookup"><span data-stu-id="2ac79-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="2ac79-815">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-815">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-816">Info Field 1: Ponteiro para a fila correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="2ac79-817">Info Field 2: Número de fios atualmente suspensos na fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="2ac79-818">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-819">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="2ac79-820">Receber fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="2ac79-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="2ac79-821">tx_queue_receive</span></span>

<span data-ttu-id="2ac79-822">**Ícone** ![ Ícone de receção de fila](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="2ac79-823">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-823">**Description**</span></span>

<span data-ttu-id="2ac79-824">Este evento representa receber uma mensagem de uma fila via tx_queue_receive.</span><span class="sxs-lookup"><span data-stu-id="2ac79-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="2ac79-825">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-825">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-826">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-827">Info Field 2: Ponteiro para destino para mensagem.</span><span class="sxs-lookup"><span data-stu-id="2ac79-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="2ac79-828">Info Field 3: Opção de espera fornecida à chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="2ac79-829">Info Campo 4: Número de mensagens atualmente em fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="2ac79-830">Enviar fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="2ac79-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="2ac79-831">tx_queue_send</span></span>

<span data-ttu-id="2ac79-832">**Ícone** ![ Fila enviar ícone](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="2ac79-833">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-833">**Description**</span></span>

<span data-ttu-id="2ac79-834">Este evento representa o envio de uma mensagem para uma fila via tx_queue_send.</span><span class="sxs-lookup"><span data-stu-id="2ac79-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="2ac79-835">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-835">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-836">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-837">Info Field 2: Ponteiro para mensagem.</span><span class="sxs-lookup"><span data-stu-id="2ac79-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="2ac79-838">Info Field 3: Opção de espera fornecida à chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="2ac79-839">Info Campo 4: Número de mensagens atualmente em fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="2ac79-840">Notificação de envio de fila</span><span class="sxs-lookup"><span data-stu-id="2ac79-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="2ac79-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="2ac79-841">tx_queue_send_notify</span></span>

<span data-ttu-id="2ac79-842">**Ícone** ![ Fila enviar ícone de notificação](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="2ac79-843">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-843">**Description**</span></span>

<p><span data-ttu-id="2ac79-844">Este evento representa o registo de uma chamada através de tx_queue_send_notify que é chamada sempre que uma mensagem é enviada para uma fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="2ac79-845">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-845">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-846">Info Field 1: Ponteiro para fila.</span><span class="sxs-lookup"><span data-stu-id="2ac79-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="2ac79-847">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-848">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-849">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="2ac79-850">Teto de semáforo colocado</span><span class="sxs-lookup"><span data-stu-id="2ac79-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="2ac79-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="2ac79-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="2ac79-852">**Ícone** ![ Teto de semáforo colocar ícone](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="2ac79-853">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-853">**Description**</span></span>

<span data-ttu-id="2ac79-854">Este evento representa a colocação de um semáforo através de tx_semaphore_ceiling_put.</span><span class="sxs-lookup"><span data-stu-id="2ac79-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="2ac79-855">Isto difere de tx_semaphore_put na medida em que o valor máximo do semáforo é examinado de modo a que a operação de colocação não seja permitida a exceder o valor máximo ou o limite máximo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="2ac79-856">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-856">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-857">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-858">Info Field 2: Contagem de semáforos atuais.</span><span class="sxs-lookup"><span data-stu-id="2ac79-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="2ac79-859">Info Campo 3: Número de fios suspensos no semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="2ac79-860">Info Campo 4: Limite de teto fornecido à chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="2ac79-861">Criação de Semáforos</span><span class="sxs-lookup"><span data-stu-id="2ac79-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="2ac79-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-862">tx_semaphore_create</span></span>

<span data-ttu-id="2ac79-863">**Ícone** ![ Semáforo criar ícone](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="2ac79-864">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-864">**Description**</span></span>

<span data-ttu-id="2ac79-865">Este evento representa a criação de um semáforo através de tx_semaphore_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="2ac79-866">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-866">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-867">Info Campo 1: Ponteiro para o bloco de controlo de semáforos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="2ac79-868">Info Field 2: Contagem inicial de semáforos.</span><span class="sxs-lookup"><span data-stu-id="2ac79-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="2ac79-869">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-870">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="2ac79-871">Semáforo Eliminar</span><span class="sxs-lookup"><span data-stu-id="2ac79-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="2ac79-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-872">tx_semaphore_delete</span></span>

<span data-ttu-id="2ac79-873">**Ícone** ![ Ícone de exclusão de semáforo](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="2ac79-874">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-874">**Description**</span></span>

<span data-ttu-id="2ac79-875">Este evento representa a eliminação de um semáforo através de tx_semaphore_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="2ac79-876">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-876">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-877">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-878">nfo Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-879">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-880">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="2ac79-881">Semáforo</span><span class="sxs-lookup"><span data-stu-id="2ac79-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="2ac79-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-882">tx_semaphore_get</span></span>

<span data-ttu-id="2ac79-883">**Ícone** ![ Semáforo obter ícone](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="2ac79-884">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-884">**Description**</span></span>

<span data-ttu-id="2ac79-885">Este evento representa a obtenção de um semáforo via tx_semaphore_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="2ac79-886">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-886">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-887">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-888">Info Field 2: Opção de espera fornecida à chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="2ac79-889">Info Field 3: Contagem de semáforos atuais.</span><span class="sxs-lookup"><span data-stu-id="2ac79-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="2ac79-890">Info Field 4: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="2ac79-891">Informações de semáforos Obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="2ac79-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="2ac79-893">**Ícone** ![ Informações de semáforo recebem ícone](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="2ac79-894">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-894">**Description**</span></span>

<span data-ttu-id="2ac79-895">Este evento representa a obtenção de informação sobre um semáforo via tx_semaphore_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="2ac79-896">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-896">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-897">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-898">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-899">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-900">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="2ac79-901">Informações de desempenho de semáforos obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="2ac79-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="2ac79-903">**Ícone** ![ Informações de desempenho de semáforo recebem ícone](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="2ac79-904">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-904">**Description**</span></span>

<span data-ttu-id="2ac79-905">Este evento representa a obtenção de informações de desempenho sobre um semáforo via tx_semaphore_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="2ac79-906">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-906">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-907">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-908">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-909">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-910">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="2ac79-911">Informações do Sistema de Desempenho de Semáforos</span><span class="sxs-lookup"><span data-stu-id="2ac79-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="2ac79-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-913">**Ícone** ![ Ícone de informação do sistema de desempenho de semáforo](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="2ac79-914">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-914">**Description**</span></span>

<span data-ttu-id="2ac79-915">Este evento representa a obtenção de informações de desempenho sobre todos os semáforos do sistema através de tx_semaphore_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-916">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-916">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-917">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-918">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-919">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-920">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="2ac79-921">Priorização do Semáforo</span><span class="sxs-lookup"><span data-stu-id="2ac79-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="2ac79-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="2ac79-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="2ac79-923">**Ícone** ![ Semáforo prioriza ícone](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="2ac79-924">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-924">**Description**</span></span>

<span data-ttu-id="2ac79-925">Este evento representa priorizar a lista de suspensão do semáforo através de tx_semaphore_prioritize.</span><span class="sxs-lookup"><span data-stu-id="2ac79-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="2ac79-926">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-926">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-927">Info Campo 1: Ponteiro para o semáforo correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="2ac79-928">Info Campo 2: Número de fios atualmente suspensos no semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="2ac79-929">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-930">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="2ac79-931">Semáforo colocado</span><span class="sxs-lookup"><span data-stu-id="2ac79-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="2ac79-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="2ac79-932">tx_semaphore_put</span></span>

<span data-ttu-id="2ac79-933">**Ícone** ![ Semáforo colocar ícone](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="2ac79-934">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-934">**Description**</span></span>

<span data-ttu-id="2ac79-935">Este evento representa a libertação de um caso de semáforo via tx_semaphore_put.</span><span class="sxs-lookup"><span data-stu-id="2ac79-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="2ac79-936">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-936">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-937">Info Campo 1: Ponteiro para o semáforo correspondente.</span><span class="sxs-lookup"><span data-stu-id="2ac79-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="2ac79-938">Info Field 2: Contagem de semáforos atuais.</span><span class="sxs-lookup"><span data-stu-id="2ac79-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="2ac79-939">Info Campo 3: Número de fios suspensos no semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="2ac79-940">Info Field 4: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="2ac79-941">Semáforo colocar notificação</span><span class="sxs-lookup"><span data-stu-id="2ac79-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="2ac79-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="2ac79-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="2ac79-943">**Ícone** ![ Semáforo colocar ícone de notificação](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="2ac79-944">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-944">**Description**</span></span>

<span data-ttu-id="2ac79-945">Este evento representa o registo de uma chamada através de tx_semaphore_put_notify que é chamado sempre que um caso de semáforo é colocado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="2ac79-946">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-946">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-947">Info Field 1: Ponteiro para semáforo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="2ac79-948">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-949">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-950">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="2ac79-951">Criar fios</span><span class="sxs-lookup"><span data-stu-id="2ac79-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="2ac79-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-952">tx_thread_create</span></span>

<span data-ttu-id="2ac79-953">**Ícone** ![ Ícone de criação de fio](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="2ac79-954">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-954">**Description**</span></span>

<span data-ttu-id="2ac79-955">Este evento representa a criação de um fio através de tx_thread_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="2ac79-956">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-956">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-957">Info Campo 1: Ponteiro para o bloco de controlo da rosca.</span><span class="sxs-lookup"><span data-stu-id="2ac79-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="2ac79-958">Info Field 2: Prioridade do fio.</span><span class="sxs-lookup"><span data-stu-id="2ac79-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="2ac79-959">Info Field 3: Ponteiro de pilha para fio.</span><span class="sxs-lookup"><span data-stu-id="2ac79-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="2ac79-960">nfo Field 4: Tamanho da pilha em bytes.</span><span class="sxs-lookup"><span data-stu-id="2ac79-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="2ac79-961">Eliminar fios</span><span class="sxs-lookup"><span data-stu-id="2ac79-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="2ac79-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-962">tx_thread_delete</span></span>

<span data-ttu-id="2ac79-963">**Ícone** ![ Ícone de exclusão de fio](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="2ac79-964">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-964">**Description**</span></span>

<span data-ttu-id="2ac79-965">Este evento representa a eliminação de um fio através de tx_thread_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="2ac79-966">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-966">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-967">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-968">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-969">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-970">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="2ac79-971">Notificação de entrada/saída de linha</span><span class="sxs-lookup"><span data-stu-id="2ac79-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="2ac79-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="2ac79-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="2ac79-973">**Ícone** ![ Ícone de notificação de entrada/saída de fio](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="2ac79-974">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-974">**Description**</span></span>

<span data-ttu-id="2ac79-975">Este evento representa o registo de uma chamada através de tx_thread_entry_exit_notify que é chamada sempre que um fio é introduzido ou sai.</span><span class="sxs-lookup"><span data-stu-id="2ac79-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="2ac79-976">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-976">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-977">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-978">Info Field 2: Estado de rosca no momento da inscrição.</span><span class="sxs-lookup"><span data-stu-id="2ac79-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="2ac79-979">Info Field 3: Ponteiro para empilhar no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="2ac79-980">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="2ac79-981">Identificar o fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="2ac79-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="2ac79-982">tx_thread_identify</span></span>

<span data-ttu-id="2ac79-983">**Ícone** ![ Ícone de identificação de fio](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="2ac79-984">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-984">**Description**</span></span>

<span data-ttu-id="2ac79-985">Este evento representa obter o ponteiro de linha atual através de tx_thread_identify.</span><span class="sxs-lookup"><span data-stu-id="2ac79-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="2ac79-986">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-986">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-987">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-988">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-989">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-990">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="2ac79-991">Informação de fio obter</span><span class="sxs-lookup"><span data-stu-id="2ac79-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="2ac79-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-992">tx_thread_info_get</span></span>

<span data-ttu-id="2ac79-993">**Ícone** ![ Informações de fio obter ícone](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="2ac79-994">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-994">**Description**</span></span>

<span data-ttu-id="2ac79-995">Este evento representa obter informações sobre o fio especificado através de tx_thread_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="2ac79-996">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-996">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-997">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-998">Info Field 2: Estado do fio no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="2ac79-999">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1000">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="2ac79-1001">Informações de desempenho do fio obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="2ac79-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="2ac79-1003">**Ícone** ![ Informações de desempenho do fio obter ícone](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="2ac79-1004">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1004">**Description**</span></span>

<span data-ttu-id="2ac79-1005">Este evento representa obter informações de desempenho sobre o fio especificado através de tx_thread_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="2ac79-1006">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1006">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1007">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1008">Info Field 2: Estado do fio no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="2ac79-1009">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1010">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="2ac79-1011">Informações do sistema de desempenho do fio obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="2ac79-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-1013">**Ícone** ![ Informações do sistema de desempenho do fio obter ícone](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="2ac79-1014">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1014">**Description**</span></span>

<span data-ttu-id="2ac79-1015">Este evento representa obter informações de desempenho sobre todos os fios através de tx_thread_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-1016">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1016">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1017">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-1018">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1019">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1020">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="2ac79-1021">Alteração da Preempção do Fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="2ac79-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="2ac79-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="2ac79-1023">**Ícone** ![ Ícone de mudança de mudança de preempção de fio](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="2ac79-1024">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1024">**Description**</span></span>

<span data-ttu-id="2ac79-1025">Este evento representa a alteração do limiar de preempção de um fio através de tx_thread_preemption_change.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="2ac79-1026">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1026">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1027">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1028">Info Field 2: Novo limiar de pré-detenção.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="2ac79-1029">Info Field 3: Limite de pré-detenção anterior.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="2ac79-1030">Info Field 4: Estado da Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="2ac79-1031">Alteração da prioridade do fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="2ac79-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="2ac79-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="2ac79-1033">**Ícone** ![ Ícone de mudança de prioridade de fio](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="2ac79-1034">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1034">**Description**</span></span>

<span data-ttu-id="2ac79-1035">Este evento representa mudar a prioridade de um fio através de tx_thread_priority_change.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="2ac79-1036">Campos de Informação</span><span class="sxs-lookup"><span data-stu-id="2ac79-1036">Information Fields</span></span> 
- <span data-ttu-id="2ac79-1037">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1038">Info Field 2: Nova prioridade.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="2ac79-1039">Info Campo 3: Prioridade anterior.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="2ac79-1040">Info Field 4: Estado da Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="2ac79-1041">Renúncia de fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="2ac79-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="2ac79-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="2ac79-1043">**Ícone** ![ Ícone de renúncia de fio](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="2ac79-1044">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1044">**Description**</span></span>

<span data-ttu-id="2ac79-1045">Este evento representa a renúncia ao processador de um fio através de tx_thread_relinquish.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="2ac79-1046">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1046">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1047">Info Field 1: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1048">Info Field 2: Ponteiro para o próximo fio a executar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="2ac79-1049">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1050">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="2ac79-1051">Reset de fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="2ac79-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="2ac79-1052">tx_thread_reset</span></span>

<span data-ttu-id="2ac79-1053">**Ícone** ![ Ícone de reset de fio](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="2ac79-1054">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1054">**Description**</span></span>

<span data-ttu-id="2ac79-1055">Este evento representa a reposição de um fio completo ou terminado através de tx_thread_reset.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="2ac79-1056">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1056">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1057">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1058">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1059">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1060">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="2ac79-1061">Resumo da linha</span><span class="sxs-lookup"><span data-stu-id="2ac79-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="2ac79-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="2ac79-1062">tx_thread_resume</span></span>

<span data-ttu-id="2ac79-1063">**Ícone** ![ Ícone de retoma de fio](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="2ac79-1064">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1064">**Description**</span></span>

<span data-ttu-id="2ac79-1065">Este evento representa o reinício de um fio suspenso através de tx_thread_resume.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="2ac79-1066">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1066">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1067">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1068">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1069">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1070">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="2ac79-1071">Thread Sleep</span><span class="sxs-lookup"><span data-stu-id="2ac79-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="2ac79-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="2ac79-1072">tx_thread_sleep</span></span>

<span data-ttu-id="2ac79-1073">**Ícone** ![ Ícone de sono de fio](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="2ac79-1074">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1074">**Description**</span></span>

<span data-ttu-id="2ac79-1075">Este evento representa a suspensão do fio atual para um número especificado de carraças do temporizador através de tx_thread_sleep.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="2ac79-1076">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1076">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1077">Info Field 1: Número de carraças a suspender.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="2ac79-1078">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1079">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1080">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="2ac79-1081">Notificação de erro de pilha de fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="2ac79-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="2ac79-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="2ac79-1083">**Ícone** ![ Ícone de notificação de erro de pilha de fio](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="2ac79-1084">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1084">**Description**</span></span>

<span data-ttu-id="2ac79-1085">Este evento representa o registo de uma rotina de notificação de erro de pilha de fio através de tx_thread_stack_error_notify_event.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="2ac79-1086">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1086">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1087">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-1088">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1089">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1090">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="2ac79-1091">Suspensão do fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="2ac79-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="2ac79-1092">tx_thread_suspend</span></span>

<span data-ttu-id="2ac79-1093">**Ícone** ![ Ícone de suspensão de fio](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="2ac79-1094">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1094">**Description**</span></span>

<span data-ttu-id="2ac79-1095">Este evento representa a suspensão de um fio através de tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="2ac79-1096">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1096">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1097">Info Field 1: Ponteiro para a linha para suspender.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="2ac79-1098">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1099">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1100">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="2ac79-1101">Fim de fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="2ac79-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="2ac79-1102">tx_thread_terminate</span></span>

<span data-ttu-id="2ac79-1103">**Ícone** ![ Ícone de terminação de fio](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="2ac79-1104">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1104">**Description**</span></span>

<span data-ttu-id="2ac79-1105">Este evento representa o fim de um fio através de tx_thread_terminate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="2ac79-1106">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1106">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1107">Info Campo 1: Ponteiro para linha para terminar.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="2ac79-1108">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1109">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1110">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="2ac79-1111">Mudança de Time-Slice de fio</span><span class="sxs-lookup"><span data-stu-id="2ac79-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="2ac79-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="2ac79-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="2ac79-1113">**Ícone** ![ Ícone de mudança de fatia de tempo de fio](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="2ac79-1114">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1114">**Description**</span></span>

<span data-ttu-id="2ac79-1115">Este evento representa a alteração da rodela temporal de um fio através de tx_thread_time_slice_change.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="2ac79-1116">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1116">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1117">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1118">Info Field 2: Nova fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="2ac79-1119">Info Campo 3: Corte de tempo anterior.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="2ac79-1120">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="2ac79-1121">Thread Wait Abort</span><span class="sxs-lookup"><span data-stu-id="2ac79-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="2ac79-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="2ac79-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="2ac79-1123">**Ícone** ![ Ícone de aborto de espera de fio](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="2ac79-1124">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1124">**Description**</span></span>

<span data-ttu-id="2ac79-1125">Este evento representa abortar a suspensão de um fio através de tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="2ac79-1126">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1126">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1127">Info Campo 1: Ponteiro para linha.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="2ac79-1128">Info Field 2: Estado de Thread no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="2ac79-1129">Info Field 3: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1130">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="2ac79-1131">Tempo Get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="2ac79-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1132">tx_time_get</span></span>

<span data-ttu-id="2ac79-1133">**Ícone** ![ Tempo obter ícone](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="2ac79-1134">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1134">**Description**</span></span>

<span data-ttu-id="2ac79-1135">Este evento representa obter o número atual de tiques temporizadores através de tx_time_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="2ac79-1136">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1136">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1137">Info Campo 1: Número atual de carraças temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="2ac79-1138">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1139">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1140">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="2ac79-1141">Conjunto de tempo</span><span class="sxs-lookup"><span data-stu-id="2ac79-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="2ac79-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="2ac79-1142">tx_time_set</span></span>

<span data-ttu-id="2ac79-1143">**Ícone** ![ Ícone de conjunto de tempo](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="2ac79-1144">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1144">**Description**</span></span>

<span data-ttu-id="2ac79-1145">Este evento representa a definição do número atual de carraças temporais através de tx_time_set.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="2ac79-1146">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1146">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1147">Info Field 1: Novo número de carraças temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="2ac79-1148">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1149">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1150">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="2ac79-1151">Ativador de temporizador</span><span class="sxs-lookup"><span data-stu-id="2ac79-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="2ac79-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="2ac79-1152">tx_timer_activate</span></span>

<span data-ttu-id="2ac79-1153">**Ícone** ![ Ícone de ativação do temporizador](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="2ac79-1154">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1154">**Description**</span></span>

<span data-ttu-id="2ac79-1155">Este evento representa a ativação do temporizador especificado através de tx_timer_activate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="2ac79-1156">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1156">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1157">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1158">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1159">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1160">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="2ac79-1161">Alteração do temporizador</span><span class="sxs-lookup"><span data-stu-id="2ac79-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="2ac79-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="2ac79-1162">tx_timer_change</span></span>

<span data-ttu-id="2ac79-1163">**Ícone** ![ Ícone de mudança de temporizador](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="2ac79-1164">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1164">**Description**</span></span>

<span data-ttu-id="2ac79-1165">Este evento representa a alteração do temporizador especificado através de tx_timer_change.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="2ac79-1166">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1166">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1167">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1168">Info Field 2: Tiques de expiração iniciais.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="2ac79-1169">Info Field 3: Reagendar os tiques de expiração.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="2ac79-1170">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="2ac79-1171">Criar temporizador</span><span class="sxs-lookup"><span data-stu-id="2ac79-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="2ac79-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="2ac79-1172">tx_timer_create</span></span>

<span data-ttu-id="2ac79-1173">**Ícone** ![ Ícone de criação de temporizador](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="2ac79-1174">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1174">**Description**</span></span>

<span data-ttu-id="2ac79-1175">Este evento representa a criação de um temporizador através de tx_timer_create.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="2ac79-1176">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1176">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1177">Info Campo 1: Ponteiro para o bloco de controlo do temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="2ac79-1178">Info Field 2: Tiques de expiração iniciais.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="2ac79-1179">Info Field 3: Reagendar os tiques de expiração.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="2ac79-1180">Info Field 4: Ativar automaticamente o valor — TX_AUTO_ACTIVATE (1) ou TX_NO_ACTIVATE (0).</span><span class="sxs-lookup"><span data-stu-id="2ac79-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="2ac79-1181">Temporizador Desativar</span><span class="sxs-lookup"><span data-stu-id="2ac79-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="2ac79-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="2ac79-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="2ac79-1183">**Ícone** ![ Ícone de desativado temporizador](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="2ac79-1184">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1184">**Description**</span></span>

<span data-ttu-id="2ac79-1185">Este evento representa a desativar um temporizador através de tx_timer_deactivate.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="2ac79-1186">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1186">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1187">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1188">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1189">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1190">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="2ac79-1191">Apagar temporizador</span><span class="sxs-lookup"><span data-stu-id="2ac79-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="2ac79-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="2ac79-1192">tx_timer_delete</span></span>

<span data-ttu-id="2ac79-1193">**Ícone** ![ Ícone de eliminação do temporizador](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="2ac79-1194">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1194">**Description**</span></span>

<span data-ttu-id="2ac79-1195">Este evento representa a eliminação de um temporizador através de tx_timer_delete.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="2ac79-1196">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1196">**Information Fields**</span></span> 

- <span data-ttu-id="2ac79-1197">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1198">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1199">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1200">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="2ac79-1201">Informação de temporizador Obtém</span><span class="sxs-lookup"><span data-stu-id="2ac79-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="2ac79-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1202">tx_timer_info_get</span></span>

<span data-ttu-id="2ac79-1203">**Ícone** ![ Temporizador obter ícone de informação](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="2ac79-1204">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1204">**Description**</span></span>

<span data-ttu-id="2ac79-1205">Este evento representa a obtenção de informações de temporizador através de tx_timer_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="2ac79-1206">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1206">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1207">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1208">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1209">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1210">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="2ac79-1211">Informações de desempenho do temporizador obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="2ac79-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="2ac79-1213">**Ícone** ![ Informações de desempenho do temporizador obtêm ícone](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="2ac79-1214">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1214">**Description**</span></span> 

<span data-ttu-id="2ac79-1215">Este evento representa obter informações de desempenho do temporizador através de tx_timer_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="2ac79-1216">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1216">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1217">Info Field 1: Ponteiro para temporizador.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="2ac79-1218">Info Field 2: Ponteiro de pilha no momento da chamada.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="2ac79-1219">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1220">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="2ac79-1221">Informações de desempenho do sistema temporizador obtêm</span><span class="sxs-lookup"><span data-stu-id="2ac79-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="2ac79-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="2ac79-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="2ac79-1223">**Ícone** ![ Informações de desempenho do sistema temporizador recebem ícone](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="2ac79-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="2ac79-1224">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1224">**Description**</span></span> 

<span data-ttu-id="2ac79-1225">Este evento representa obter todas as informações de desempenho do temporizador através de tx_timer_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="2ac79-1226">**Campos de Informação**</span><span class="sxs-lookup"><span data-stu-id="2ac79-1226">**Information Fields**</span></span>

- <span data-ttu-id="2ac79-1227">Info Field 1: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="2ac79-1228">Info Field 2: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="2ac79-1229">Info Field 3: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="2ac79-1230">Info Field 4: Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="2ac79-1230">Info Field 4: Not used.</span></span>