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
#  <a name="chapter-2--execution-profile-kit-api-references"></a><span data-ttu-id="df842-103">Referências API do Kit de Perfil de Execução capítulo 2</span><span class="sxs-lookup"><span data-stu-id="df842-103">Chapter 2  Execution Profile Kit API References</span></span>

<span data-ttu-id="df842-104">O ThreadX EPK fornece funções de acesso para obter as informações do perfil de execução, da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="df842-104">The ThreadX EPK provides access functions to get the execution profile information, as follows.</span></span>

| <span data-ttu-id="df842-105">Nome da função &nbsp;</span><span class="sxs-lookup"><span data-stu-id="df842-105">Function&nbsp;Name</span></span> | <span data-ttu-id="df842-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-106">Description</span></span> |
| --- | --- |
| <span data-ttu-id="df842-107">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-107">_tx_execution_thread_time_reset</span></span> | <span data-ttu-id="df842-108">Repor o tempo acumulado para um fio.</span><span class="sxs-lookup"><span data-stu-id="df842-108">Reset the accumulated time for a thread.</span></span> |
| <span data-ttu-id="df842-109">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-109">_tx_execution_thread_total_time_reset</span></span> | <span data-ttu-id="df842-110">Repor o tempo total de rosca acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-110">Reset the accumulated total thread time.</span></span> |
| <span data-ttu-id="df842-111">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-111">_tx_execution_isr_time_reset</span></span> | <span data-ttu-id="df842-112">Repor o tempo ISR acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-112">Reset the accumulated ISR time.</span></span> |
| <span data-ttu-id="df842-113">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-113">_tx_execution_idle_time_reset</span></span> | <span data-ttu-id="df842-114">Repôs o tempo de marcha lenta a acumular.</span><span class="sxs-lookup"><span data-stu-id="df842-114">Reset the accumulated idle time.</span></span> |
| <span data-ttu-id="df842-115">_tx_execution_thread_time_get Obtenha o tempo acumulado para um fio.</span><span class="sxs-lookup"><span data-stu-id="df842-115">_tx_execution_thread_time_get Get the accumulated time for a thread.</span></span> |
| <span data-ttu-id="df842-116">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-116">_tx_execution_thread_total_time_get</span></span> | <span data-ttu-id="df842-117">Obtenha o tempo total acumulado do fio.</span><span class="sxs-lookup"><span data-stu-id="df842-117">Get the accumulated total thread time.</span></span> |
| <span data-ttu-id="df842-118">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-118">_tx_execution_isr_time_get</span></span> | <span data-ttu-id="df842-119">Obtenha o tempo isr acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-119">Get the accumulated ISR time.</span></span> |
| <span data-ttu-id="df842-120">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-120">_tx_execution_idle_time_get</span></span> | <span data-ttu-id="df842-121">Obtenha o tempo de marcha lenta.</span><span class="sxs-lookup"><span data-stu-id="df842-121">Get the accumulated idle time.</span></span> |

##  <a name="_tx_execution_thread_time_reset"></a><span data-ttu-id="df842-122">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-122">_tx_execution_thread_time_reset</span></span>

<span data-ttu-id="df842-123">Repor o tempo acumulado para um fio.</span><span class="sxs-lookup"><span data-stu-id="df842-123">Reset the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-124">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-124">Prototype</span></span>

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="df842-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-125">Description</span></span>

<span data-ttu-id="df842-126">Este serviço define o tempo de execução do fio acumulado de volta a zero.</span><span class="sxs-lookup"><span data-stu-id="df842-126">This service sets the accumulated thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-127">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-127">Input Parameters</span></span>

- <span data-ttu-id="df842-128">**thread_ptr** Ponteiro para o fio.</span><span class="sxs-lookup"><span data-stu-id="df842-128">**thread_ptr** Pointer to thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-129">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-129">Return Values</span></span>

- <span data-ttu-id="df842-130">**TX_SUCCESS** (0x00) Reset EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-130">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-131">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-131">Allowed From</span></span>

<span data-ttu-id="df842-132">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-132">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-133">Example</span></span>

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-134">See Also</span></span>

- <span data-ttu-id="df842-135">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-135">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-136">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-136">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-137">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-137">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-138">tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-138">tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-139">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-139">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-140">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-140">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-141">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-141">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_reset"></a><span data-ttu-id="df842-142">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-142">_tx_execution_thread_total_time_reset</span></span>

<span data-ttu-id="df842-143">Repor o tempo total de rosca acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-143">Reset the total accumulated thread time.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-144">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-144">Prototype</span></span>
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="df842-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-145">Description</span></span>

<span data-ttu-id="df842-146">Este serviço define o tempo de execução total acumulado do fio de volta a zero.</span><span class="sxs-lookup"><span data-stu-id="df842-146">This service sets the accumulated total thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-147">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-147">Input Parameters</span></span>

<span data-ttu-id="df842-148">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df842-148">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-149">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-149">Return Values</span></span>

- <span data-ttu-id="df842-150">**TX_SUCCESS** (0x00) Reset EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-150">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-151">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-151">Allowed From</span></span>

- <span data-ttu-id="df842-152">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-152">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-153">Example</span></span>

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-154">See Also</span></span>

- <span data-ttu-id="df842-155">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-155">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-156">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-156">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-157">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-157">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-158">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-158">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-159">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-159">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-160">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-160">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-161">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-161">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_reset"></a><span data-ttu-id="df842-162">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-162">_tx_execution_isr_time_reset</span></span>

<span data-ttu-id="df842-163">Repor o tempo ISR acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-163">Reset the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-164">Prototype</span></span>

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="df842-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-165">Description</span></span>

<span data-ttu-id="df842-166">Este serviço define o tempo de execução total do ISR acumulado de volta a zero.</span><span class="sxs-lookup"><span data-stu-id="df842-166">This service sets the accumulated total ISR execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-167">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-167">Input Parameters</span></span>

<span data-ttu-id="df842-168">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df842-168">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-169">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-169">Return Values</span></span>

- <span data-ttu-id="df842-170">**TX_SUCCESS** (0x00) Reset EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-170">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

<span data-ttu-id="df842-171">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="df842-171">**Allowed From**</span></span>

- <span data-ttu-id="df842-172">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-172">Threads, timers, and ISRs</span></span>

<span data-ttu-id="df842-173">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="df842-173">**Example**</span></span>

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-174">See Also</span></span>

- <span data-ttu-id="df842-175">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-175">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-176">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-176">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-177">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-177">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-178">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-178">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-179">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-179">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-180">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-180">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-181">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-181">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_reset"></a><span data-ttu-id="df842-182">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-182">_tx_execution_idle_time_reset</span></span>

<span data-ttu-id="df842-183">Repôs o tempo de marcha lenta a acumular.</span><span class="sxs-lookup"><span data-stu-id="df842-183">Reset the accumulated idle time.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-184">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-184">Prototype</span></span>

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="df842-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-185">Description</span></span>

<span data-ttu-id="df842-186">Este serviço define o tempo de execução total acumulado de marcha lenta para zero.</span><span class="sxs-lookup"><span data-stu-id="df842-186">This service sets the accumulated total idle execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-187">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-187">Input Parameters</span></span>

<span data-ttu-id="df842-188">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df842-188">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-189">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-189">Return Values</span></span>

- <span data-ttu-id="df842-190">**TX_SUCCESS** (0x00) Reset EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-190">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-191">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-191">Allowed From</span></span>

- <span data-ttu-id="df842-192">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-192">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-193">Example</span></span>

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-194">See Also</span></span>

- <span data-ttu-id="df842-195">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-195">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-196">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-196">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-197">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-197">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-198">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-198">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-199">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-199">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-200">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-200">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-201">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-201">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_time_get"></a><span data-ttu-id="df842-202">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-202">_tx_execution_thread_time_get</span></span>

<span data-ttu-id="df842-203">Obtenha o tempo acumulado para um fio.</span><span class="sxs-lookup"><span data-stu-id="df842-203">Get the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-204">Prototype</span></span>

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="df842-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-205">Description</span></span>

<span data-ttu-id="df842-206">Este serviço obtém o tempo de execução acumulado por um fio.</span><span class="sxs-lookup"><span data-stu-id="df842-206">This service gets the accumulated execution time for a thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-207">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-207">Input Parameters</span></span>

- <span data-ttu-id="df842-208">**thread_ptr** Ponteiro para o fio.</span><span class="sxs-lookup"><span data-stu-id="df842-208">**thread_ptr** Pointer to thread.</span></span>

- <span data-ttu-id="df842-209">**total_time** Destino para \' o tempo de execução do thread.</span><span class="sxs-lookup"><span data-stu-id="df842-209">**total_time** Destination for thread\'s execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-210">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-210">Return Values</span></span>

- <span data-ttu-id="df842-211">**TX_SUCCESS** (0x00) tempo de EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-211">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-212">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-212">Allowed From</span></span>

<span data-ttu-id="df842-213">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-213">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-214">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-214">Example</span></span>

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-215">See Also</span></span>

- <span data-ttu-id="df842-216">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-216">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-217">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-217">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-218">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-218">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-219">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-219">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-220">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-220">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-221">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-221">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-222">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-222">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_get"></a><span data-ttu-id="df842-223">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-223">_tx_execution_thread_total_time_get</span></span>

<span data-ttu-id="df842-224">Obtenha o tempo total acumulado do fio.</span><span class="sxs-lookup"><span data-stu-id="df842-224">Get the accumulated thread total time.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-225">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-225">Prototype</span></span>

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="df842-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-226">Description</span></span>

<span data-ttu-id="df842-227">Este serviço obtém o tempo de execução total acumulado do fio.</span><span class="sxs-lookup"><span data-stu-id="df842-227">This service gets the accumulated total thread execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-228">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-228">Input Parameters</span></span>

- <span data-ttu-id="df842-229">**total_time** Destino para o tempo total de execução do fio.</span><span class="sxs-lookup"><span data-stu-id="df842-229">**total_time** Destination for total thread execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-230">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-230">Return Values</span></span>

- <span data-ttu-id="df842-231">**TX_SUCCESS** (0x00) tempo de EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-231">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-232">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-232">Allowed From</span></span>

- <span data-ttu-id="df842-233">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-233">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-234">Example</span></span>

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-235">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-235">See Also</span></span>

- <span data-ttu-id="df842-236">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-236">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-237">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-237">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-238">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-238">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-239">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-239">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-240">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-240">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-241">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-241">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="df842-242">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-242">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_get"></a><span data-ttu-id="df842-243">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-243">_tx_execution_isr_time_get</span></span>

<span data-ttu-id="df842-244">Obtenha o tempo isr acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-244">Get the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-245">Prototype</span></span>

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="df842-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-246">Description</span></span>

<span data-ttu-id="df842-247">Este serviço obtém o tempo de execução do ISR acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-247">This service gets the accumulated ISR execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-248">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-248">Input Parameters</span></span>

- <span data-ttu-id="df842-249">**total_time** Destino para o tempo total de execução do ISR.</span><span class="sxs-lookup"><span data-stu-id="df842-249">**total_time** Destination for total ISR execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-250">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-250">Return Values</span></span>

- <span data-ttu-id="df842-251">**TX_SUCCESS** (0x00) tempo de EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-251">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-252">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-252">Allowed From</span></span>

<span data-ttu-id="df842-253">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-253">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-254">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-254">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-255">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-255">See Also</span></span>

- <span data-ttu-id="df842-256">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-256">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-257">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-257">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-258">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-258">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-259">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-259">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-260">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-260">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-261">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-261">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-262">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-262">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_get"></a><span data-ttu-id="df842-263">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-263">_tx_execution_idle_time_get</span></span>

### <a name="get-the-accumulated-idle-time"></a><span data-ttu-id="df842-264">Obtenha o tempo de marcha lenta ociosa acumulado</span><span class="sxs-lookup"><span data-stu-id="df842-264">Get the accumulated idle time</span></span>

### <a name="prototype"></a><span data-ttu-id="df842-265">Prototype</span><span class="sxs-lookup"><span data-stu-id="df842-265">Prototype</span></span>

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="df842-266">Descrição</span><span class="sxs-lookup"><span data-stu-id="df842-266">Description</span></span>

<span data-ttu-id="df842-267">Este serviço obtém o tempo de execução ocioso acumulado.</span><span class="sxs-lookup"><span data-stu-id="df842-267">This service gets the accumulated idle execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df842-268">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df842-268">Input Parameters</span></span>

- <span data-ttu-id="df842-269">**total_time** Destino para o tempo total de execução ocioso.</span><span class="sxs-lookup"><span data-stu-id="df842-269">**total_time** Destination for total idle execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="df842-270">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df842-270">Return Values</span></span>

- <span data-ttu-id="df842-271">**TX_SUCCESS** (0x00) tempo de EPK bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="df842-271">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df842-272">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df842-272">Allowed From</span></span>

- <span data-ttu-id="df842-273">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="df842-273">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="df842-274">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df842-274">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="df842-275">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df842-275">See Also</span></span>

- <span data-ttu-id="df842-276">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-276">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="df842-277">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-277">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="df842-278">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-278">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="df842-279">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="df842-279">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="df842-280">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-280">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="df842-281">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-281">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="df842-282">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="df842-282">_tx_execution_isr_time_get</span></span>
