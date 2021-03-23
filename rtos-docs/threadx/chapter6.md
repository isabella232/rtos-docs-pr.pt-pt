---
title: Capítulo 6 - Sistema de Demonstração para Azure RTOS ThreadX
description: Este capítulo contém uma descrição do sistema de demonstração que é entregue com todos os pacotes de suporte ao processador Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825453"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="550bd-103">Capítulo 6 - Sistema de Demonstração para Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="550bd-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="550bd-104">Este capítulo contém uma descrição do sistema de demonstração que é entregue com todos os pacotes de suporte ao processador Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="550bd-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="550bd-105">Descrição geral</span><span class="sxs-lookup"><span data-stu-id="550bd-105">Overview</span></span>

<span data-ttu-id="550bd-106">Cada distribuição de produto ThreadX contém um sistema de demonstração que funciona em todos os microprocessadores suportados.</span><span class="sxs-lookup"><span data-stu-id="550bd-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="550bd-107">Este sistema de exemplo é definido no ficheiro de distribuição ***demo_threadx.c*** e foi concebido para ilustrar como o ThreadX é usado num ambiente multi-liscado incorporado.</span><span class="sxs-lookup"><span data-stu-id="550bd-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="550bd-108">A demonstração consiste em inicialização, oito fios, uma piscina de byte, uma piscina de blocos, uma fila, um semáforo, um mutex e um grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="550bd-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="550bd-109">*Com exceção do tamanho da pilha do fio, a aplicação de demonstração é idêntica em todos os processadores suportados pela ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="550bd-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="550bd-110">A lista completa de ***demo_threadx.c,*** incluindo os números de linha referenciados ao longo do resto deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="550bd-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="550bd-111">Definição de aplicação</span><span class="sxs-lookup"><span data-stu-id="550bd-111">Application Define</span></span>

<span data-ttu-id="550bd-112">A função ***tx_application_define*** executa após a inicialização básica do ThreadX estar concluída.</span><span class="sxs-lookup"><span data-stu-id="550bd-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="550bd-113">É responsável pela criação de todos os recursos iniciais do sistema, incluindo fios, filas, semáforos, mutantes, bandeiras de eventos e piscinas de memória.</span><span class="sxs-lookup"><span data-stu-id="550bd-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="550bd-114">O sistema de demonstração ***tx_application_define** _ (_line números 60-164*) cria os objetos de demonstração na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="550bd-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="550bd-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="550bd-115">byte_pool_0</span></span>
- <span data-ttu-id="550bd-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="550bd-116">thread_0</span></span>
- <span data-ttu-id="550bd-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="550bd-117">thread_1</span></span>
- <span data-ttu-id="550bd-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="550bd-118">thread_2</span></span>
- <span data-ttu-id="550bd-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="550bd-119">thread_3</span></span>
- <span data-ttu-id="550bd-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="550bd-120">thread_4</span></span>
- <span data-ttu-id="550bd-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="550bd-121">thread_5</span></span>
- <span data-ttu-id="550bd-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="550bd-122">thread_6</span></span>
- <span data-ttu-id="550bd-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="550bd-123">thread_7</span></span>
- <span data-ttu-id="550bd-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="550bd-124">queue_0</span></span>
- <span data-ttu-id="550bd-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="550bd-125">semaphore_0</span></span>
- <span data-ttu-id="550bd-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="550bd-126">event_flags_0</span></span>
- <span data-ttu-id="550bd-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="550bd-127">mutex_0</span></span>
- <span data-ttu-id="550bd-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="550bd-128">block_pool_0</span></span>

<span data-ttu-id="550bd-129">O sistema de demonstração não cria quaisquer outros objetos ThreadX adicionais.</span><span class="sxs-lookup"><span data-stu-id="550bd-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="550bd-130">No entanto, uma aplicação real pode criar objetos do sistema durante o tempo de execução dentro dos fios de execução.</span><span class="sxs-lookup"><span data-stu-id="550bd-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="550bd-131">Execução Inicial</span><span class="sxs-lookup"><span data-stu-id="550bd-131">Initial Execution</span></span>

<span data-ttu-id="550bd-132">Todos os fios são criados com a opção **TX_AUTO_START.**</span><span class="sxs-lookup"><span data-stu-id="550bd-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="550bd-133">Isto os deixa inicialmente prontos para a execução.</span><span class="sxs-lookup"><span data-stu-id="550bd-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="550bd-134">Após ***tx_application_define*** completa, o controlo é transferido para o programador de linhas e daí para cada fio individual.</span><span class="sxs-lookup"><span data-stu-id="550bd-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="550bd-135">A ordem pela qual os fios executam é determinada pela sua prioridade e pela ordem que foram criadas.</span><span class="sxs-lookup"><span data-stu-id="550bd-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="550bd-136">No sistema de demonstração, ***thread_0*** executa primeiro porque tem a maior prioridade –*foi criado com uma prioridade de 1*).</span><span class="sxs-lookup"><span data-stu-id="550bd-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="550bd-137">Após ***thread_0*** suspensão, ***thread_5*** é executado, seguido da execução de ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _* _thread_7_\*\*, \***thread_1**_, e finalmente _\*_thread_2_\*\*.</span><span class="sxs-lookup"><span data-stu-id="550bd-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="550bd-138">*Apesar **de thread_3** e **thread_4** terem a mesma prioridade (ambas criadas com uma prioridade de 8), **thread_3** executa primeiro. Isto porque **thread_3** foi criado e pronto antes **de thread_4.** Fios de igual prioridade executam de forma FIFO.*</span><span class="sxs-lookup"><span data-stu-id="550bd-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="550bd-139">Fio 0</span><span class="sxs-lookup"><span data-stu-id="550bd-139">Thread 0</span></span>

<span data-ttu-id="550bd-140">A função ***thread_0_entry*** marca o ponto de entrada do fio *(linhas 167-190).*</span><span class="sxs-lookup"><span data-stu-id="550bd-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="550bd-141">***Thread_0*** é o primeiro fio no sistema de demonstração a executar.</span><span class="sxs-lookup"><span data-stu-id="550bd-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="550bd-142">O seu processamento é simples: incrementa o seu contador, dorme por 10 tiques temporizadores, define uma bandeira de evento para acordar ***thread_5,*** e depois repete a sequência.</span><span class="sxs-lookup"><span data-stu-id="550bd-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="550bd-143">***Thread_0*** é o fio de prioridade mais alto do sistema.</span><span class="sxs-lookup"><span data-stu-id="550bd-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="550bd-144">Quando o seu sono solicitado expirar, ele preempia qualquer outro fio de execução na demonstração.</span><span class="sxs-lookup"><span data-stu-id="550bd-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="550bd-145">Fio 1</span><span class="sxs-lookup"><span data-stu-id="550bd-145">Thread 1</span></span>

<span data-ttu-id="550bd-146">A função ***thread_1_entry** _ marca o ponto de entrada do fio _(linhas 193-216 *). ***Thread_1*** é o penúltimo fio do sistema de demonstração a executar. O seu processamento consiste em incrementar o seu contador, enviar uma mensagem para ***thread_2*** (através* de* ***queue_0),*** e repetir a sequência. Note que \***thread_1**_ suspende sempre _*_que queue_0_*_ fique cheio (_line 207\*).</span><span class="sxs-lookup"><span data-stu-id="550bd-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="550bd-147">Fio 2</span><span class="sxs-lookup"><span data-stu-id="550bd-147">Thread 2</span></span>

<span data-ttu-id="550bd-148">A função ***thread_2_entry*** marca o ponto de entrada do fio *(linhas 219-243).*</span><span class="sxs-lookup"><span data-stu-id="550bd-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="550bd-149">***Thread_2*** é o último fio no sistema de demonstração a executar.</span><span class="sxs-lookup"><span data-stu-id="550bd-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="550bd-150">O seu processamento consiste em incrementar o seu contador, receber uma mensagem de ***thread_1*** (através ***de queue_0),*** e repetir a sequência.</span><span class="sxs-lookup"><span data-stu-id="550bd-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="550bd-151">Note que ***thread_2** _ suspende sempre _*_que queue_0_*_ fique vazia (_line 233*).</span><span class="sxs-lookup"><span data-stu-id="550bd-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="550bd-152">Embora ***thread_1** _ e _ *_thread_2_** partilham a menor prioridade no sistema de demonstração (prioridade\* 16\*), eles *Threads 3 e 4*</span><span class="sxs-lookup"><span data-stu-id="550bd-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="550bd-153">são também os únicos fios que estão prontos para a execução a maior parte do tempo.</span><span class="sxs-lookup"><span data-stu-id="550bd-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="550bd-154">São também os únicos fios criados com corte de tempo *(linhas 87 e 93).*</span><span class="sxs-lookup"><span data-stu-id="550bd-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="550bd-155">Cada fio é autorizado a executar por um máximo de 4 carraças de temporizador antes que o outro fio seja executado.</span><span class="sxs-lookup"><span data-stu-id="550bd-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="550bd-156">Fios 3 e 4</span><span class="sxs-lookup"><span data-stu-id="550bd-156">Threads 3 and 4</span></span>

<span data-ttu-id="550bd-157">A função ***thread_3_and_4_entry*** marca o ponto de entrada de ambos ***thread_3** _ e _ *_thread_4_** (linhas 246-280).</span><span class="sxs-lookup"><span data-stu-id="550bd-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="550bd-158">Ambos os fios têm uma prioridade de 8, o que faz deles o terceiro e quarto fios no sistema de demonstração a executar.</span><span class="sxs-lookup"><span data-stu-id="550bd-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="550bd-159">O processamento para cada fio é o mesmo: incrementando o seu contador, ficando ***semaphore_0,*** dormindo por 2 carraças temporizador, libertando ***semaphore_0***, e repetindo a sequência.</span><span class="sxs-lookup"><span data-stu-id="550bd-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="550bd-160">Note que cada fio suspende sempre ***que semaphore_0*** não estiver disponível (linha 264).</span><span class="sxs-lookup"><span data-stu-id="550bd-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="550bd-161">Também ambos os fios utilizam a mesma função para o seu processamento principal.</span><span class="sxs-lookup"><span data-stu-id="550bd-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="550bd-162">Isto não apresenta problemas porque ambos têm a sua própria pilha única, e C é naturalmente reentrante.</span><span class="sxs-lookup"><span data-stu-id="550bd-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="550bd-163">Cada fio determina qual é por exame do parâmetro de entrada do fio (linha 258), que é configurado quando são criados (linhas 102 e 109).</span><span class="sxs-lookup"><span data-stu-id="550bd-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="550bd-164">*Também é razoável obter o ponto de linha atual durante a execução do fio e compará-lo com o endereço do bloco de controlo para determinar a identidade do fio.*</span><span class="sxs-lookup"><span data-stu-id="550bd-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="550bd-165">Fio 5</span><span class="sxs-lookup"><span data-stu-id="550bd-165">Thread 5</span></span>

<span data-ttu-id="550bd-166">A função ***thread_5_entry*** marca o ponto de entrada do fio (linhas 283-305).</span><span class="sxs-lookup"><span data-stu-id="550bd-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="550bd-167">***Thread_5*** é o segundo fio condutor do sistema de demonstração a executar.</span><span class="sxs-lookup"><span data-stu-id="550bd-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="550bd-168">O seu processamento consiste em incrementar o seu contador, obter uma bandeira de evento de ***thread_0*** (através ***de event_flags_0),*** e repetir a sequência.</span><span class="sxs-lookup"><span data-stu-id="550bd-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="550bd-169">Note que ***thread_5*** suspende sempre que a bandeira do evento em ***event_flags_0*** não estiver disponível (linha 298).</span><span class="sxs-lookup"><span data-stu-id="550bd-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="550bd-170">Fios 6 e 7</span><span class="sxs-lookup"><span data-stu-id="550bd-170">Threads 6 and 7</span></span>

<span data-ttu-id="550bd-171">A função ***thread_6_and_7_entry*** marca o ponto de entrada de ambos ***thread_6** _ e _ *_thread_7_** (linhas 307-358).</span><span class="sxs-lookup"><span data-stu-id="550bd-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="550bd-172">Ambos os fios têm uma prioridade de 8, o que faz deles o quinto e sexto fios do sistema de demonstração a executar.</span><span class="sxs-lookup"><span data-stu-id="550bd-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="550bd-173">O processamento para cada fio é o mesmo: incrementando o seu contador, ficando ***mutex_0*** duas vezes, dormindo por 2 carraças temporizador, libertando ***mutex_0*** duas vezes, e repetindo a sequência.</span><span class="sxs-lookup"><span data-stu-id="550bd-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="550bd-174">Note que cada fio suspende sempre ***que mutex_0*** não estiver disponível (linha 325).</span><span class="sxs-lookup"><span data-stu-id="550bd-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="550bd-175">Também ambos os fios utilizam a mesma função para o seu processamento principal.</span><span class="sxs-lookup"><span data-stu-id="550bd-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="550bd-176">Isto não apresenta problemas porque ambos têm a sua própria pilha única, e C é naturalmente reentrante.</span><span class="sxs-lookup"><span data-stu-id="550bd-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="550bd-177">Cada fio determina qual é por exame do parâmetro de entrada do fio (linha 319), que é configurado quando são criados (linhas 126 e 133).</span><span class="sxs-lookup"><span data-stu-id="550bd-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="550bd-178">Observando a Demonstração</span><span class="sxs-lookup"><span data-stu-id="550bd-178">Observing the Demonstration</span></span>

<span data-ttu-id="550bd-179">Cada um dos fios de demonstração incrementa o seu próprio contador único.</span><span class="sxs-lookup"><span data-stu-id="550bd-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="550bd-180">Podem ser examinados os seguintes contadores para verificar o funcionamento da demonstração:</span><span class="sxs-lookup"><span data-stu-id="550bd-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="550bd-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-181">thread_0_counter</span></span>
- <span data-ttu-id="550bd-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-182">thread_1_counter</span></span>
- <span data-ttu-id="550bd-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-183">thread_2_counter</span></span>
- <span data-ttu-id="550bd-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-184">thread_3_counter</span></span>
- <span data-ttu-id="550bd-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-185">thread_4_counter</span></span>
- <span data-ttu-id="550bd-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-186">thread_5_counter</span></span>
- <span data-ttu-id="550bd-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-187">thread_6_counter</span></span>
- <span data-ttu-id="550bd-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="550bd-188">thread_7_counter</span></span>

<span data-ttu-id="550bd-189">Cada um destes balcões deve continuar a aumentar à medida que a demonstração executa, com ***thread_1_counter** _ e _ *_thread_2_counter_** aumentando ao ritmo mais rápido.</span><span class="sxs-lookup"><span data-stu-id="550bd-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="550bd-190">Ficheiro de distribuição: demo_threadx.c</span><span class="sxs-lookup"><span data-stu-id="550bd-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="550bd-191">Esta secção apresenta a lista completa de ***demo_threadx.c,*** incluindo os números de linha referenciados ao longo deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="550bd-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
void thread_0_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {

        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}


void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}


void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;


    /* This function is executed from thread 3 and thread 4. As the loop
    below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;


    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
            &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
        below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
