---
title: Capítulo 4 - Análise de desempenho do Azure RTOS TraceX
description: Este capítulo descreve a ferramenta de análise de desempenho Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827536"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="649c0-103">Capítulo 4 - Análise de desempenho do Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="649c0-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="649c0-104">Este capítulo descreve a ferramenta de análise de desempenho Azure RTOS TraceX:</span><span class="sxs-lookup"><span data-stu-id="649c0-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="649c0-105">Análise de Desempenho</span><span class="sxs-lookup"><span data-stu-id="649c0-105">Performance Analysis</span></span>

<span data-ttu-id="649c0-106">O TraceX fornece uma análise de desempenho incorporada de ficheiros de vestígios.</span><span class="sxs-lookup"><span data-stu-id="649c0-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="649c0-107">Informações como o perfil de *execução,* *serviços populares,* *utilização de pilhas de fio,* e várias *estatísticas de desempenho,* incluindo as estatísticas do FileX e netX, estão prontamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="649c0-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="649c0-108">Estas informações estão disponíveis através do item do menu ***Ver.***</span><span class="sxs-lookup"><span data-stu-id="649c0-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="649c0-109">Perfil de execução</span><span class="sxs-lookup"><span data-stu-id="649c0-109">Execution Profile</span></span>

<span data-ttu-id="649c0-110">Selecionando o **botão**\* Generate Execution Profile _ ou _*_View -Execution Profile_*_ apresenta o perfil de execução TraceX para o ficheiro de traços atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="649c0-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="649c0-111">O perfil de execução associado à amostra ThreadX é mostrado em _\*Figura 19\*\*.</span><span class="sxs-lookup"><span data-stu-id="649c0-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![Screenshot do perfil de execução associado à amostra threadx traço de demonstração.](./media/user-guide/execution_profile.png)

<span data-ttu-id="649c0-113">**FIGURA 19**</span><span class="sxs-lookup"><span data-stu-id="649c0-113">**FIGURE 19**</span></span>

<span data-ttu-id="649c0-114">O exemplo mostrado na **Figura 19** indica que quase 45% do tempo de processamento está dentro do **_fio 2_*_ e quase 51% do tempo de processamento está dentro do _\* thread _1_*\* Isto é lógico, uma vez que a maior parte dos vestígios mostra estas linhas enviando e recebendo mensagens.</span><span class="sxs-lookup"><span data-stu-id="649c0-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="649c0-115">Os restantes contextos de execução têm apenas um pequeno tempo de execução neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="649c0-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="649c0-116">Serviços Populares</span><span class="sxs-lookup"><span data-stu-id="649c0-116">Popular Services</span></span>

<span data-ttu-id="649c0-117">Selecionando \***Ver ->Serviços Populares** _ apresenta os serviços populares no arquivo de traços atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="649c0-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="649c0-118">Por padrão, esta informação é apresentada para todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="649c0-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="649c0-119">No entanto, os serviços populares para fios específicos também estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="649c0-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="649c0-120">Os serviços populares na amostra ThreadX mostram vestígios de demonstração em _\*Figura 20\*\*.</span><span class="sxs-lookup"><span data-stu-id="649c0-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![Screenshot dos serviços populares na amostra ThreadX traço de demonstração.](./media/user-guide/popular_services.png)

<span data-ttu-id="649c0-122">**FIGURA 20**</span><span class="sxs-lookup"><span data-stu-id="649c0-122">**FIGURE 20**</span></span>

<span data-ttu-id="649c0-123">O exemplo mostrado na **Figura 20** indica que **_tx_queue_send_*_ e _*_tx_queue_receive_** são os dois serviços mais populares neste rastreio.</span><span class="sxs-lookup"><span data-stu-id="649c0-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="649c0-124">Isto é consistente com o comportamento da demonstração padrão da ThreadX a partir da qual este vestígio foi capturado.</span><span class="sxs-lookup"><span data-stu-id="649c0-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="649c0-125">Os fios específicos podem ser selecionados para esta análise utilizando a lista de seleção drop-down no topo desta janela.</span><span class="sxs-lookup"><span data-stu-id="649c0-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="649c0-126">**A figura 21** mostra esta análise para **_o fio 3_**.</span><span class="sxs-lookup"><span data-stu-id="649c0-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![Screenshot da análise para um serviço popular TraceX.](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="649c0-128">**FIGURA 21**</span><span class="sxs-lookup"><span data-stu-id="649c0-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="649c0-129">Utilização da pilha de fio</span><span class="sxs-lookup"><span data-stu-id="649c0-129">Thread Stack Usage</span></span> ![Análise para o fio 3.](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="649c0-131">Selecionar o botão ***Generate Thread Stack Use** _ ou View _*_-> Thread Stack Usage_\*_ apresenta o uso da pilha para cada fio no ficheiro de traços.</span><span class="sxs-lookup"><span data-stu-id="649c0-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="649c0-132">Isto é realizado pela ThreadX, incluindo o ponteiro de pilha de fio atual em muitas das entradas de vestígios no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="649c0-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="649c0-133">Uma utilização de pilha de 100% indica que a pilha transbordou e deve ser corrigida na aplicação.</span><span class="sxs-lookup"><span data-stu-id="649c0-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="649c0-134">Se não houver execução de fio dentro deste ficheiro de vestígios, a utilização da pilha para esse fio é mostrada a 0%.</span><span class="sxs-lookup"><span data-stu-id="649c0-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="649c0-135">A utilização da pilha de fio na amostra ThreadX é mostrada em _\*Figura 22\*\*.</span><span class="sxs-lookup"><span data-stu-id="649c0-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![Screenshot do uso da pilha de fio TraceX.](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="649c0-137">**FIGURA 22**</span><span class="sxs-lookup"><span data-stu-id="649c0-137">**FIGURE 22**</span></span>

<span data-ttu-id="649c0-138">O exemplo mostrado na **Figura 22** indica que a maioria dos fios neste vestígio têm entre 9% e 12% de utilização da pilha.</span><span class="sxs-lookup"><span data-stu-id="649c0-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="649c0-139">Estatísticas de Desempenho</span><span class="sxs-lookup"><span data-stu-id="649c0-139">Performance Statistics</span></span>

<span data-ttu-id="649c0-140">Selecionar o botão \***Gerar Estatísticas de Desempenho** _ ou _ Ver *_-> Estatísticas_* de Desempenho \* apresenta as estatísticas de desempenho do ficheiro de traços atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="649c0-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="649c0-141">Por padrão, esta informação é apresentada para todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="649c0-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="649c0-142">No entanto, as estatísticas de desempenho também estão disponíveis para cada fio específico.</span><span class="sxs-lookup"><span data-stu-id="649c0-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="649c0-143">As estatísticas de desempenho da amostra ThreadX mostram os vestígios de demonstração da threadX na **figura 23**.</span><span class="sxs-lookup"><span data-stu-id="649c0-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![Screenshot das estatísticas de desempenho do TraceX.](./media/user-guide/performance_statistics.png)

<span data-ttu-id="649c0-145">**FIGURA 23**</span><span class="sxs-lookup"><span data-stu-id="649c0-145">**FIGURE 23**</span></span>

<span data-ttu-id="649c0-146">O exemplo mostrado na **Figura 23** indica que havia 18 interruptores de contexto neste ficheiro de traços, bem como cinco preemposições de fio, 16 suspensões de roscas, 19 reposições de roscas e três interrupções.</span><span class="sxs-lookup"><span data-stu-id="649c0-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="649c0-147">Não foram encontradas inversões prioritárias neste ficheiro.</span><span class="sxs-lookup"><span data-stu-id="649c0-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="649c0-148">Note que existem duas categorias de inversões prioritárias, nomeadamente, *determinísticas* e *não determinísticas.*</span><span class="sxs-lookup"><span data-stu-id="649c0-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="649c0-149">Inversões prioritárias determinísticas são inversão prioritária em que um fio é bloqueado num mutex propriedade de um fio de menor prioridade.</span><span class="sxs-lookup"><span data-stu-id="649c0-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="649c0-150">Uma inversão de prioridade não determinística é onde um fio de prioridade inferior diferente corre durante uma inversão de prioridade determinística.</span><span class="sxs-lookup"><span data-stu-id="649c0-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="649c0-151">O posterior pode causar um comportamento de tempo imprevisto na aplicação e deve ser estudado cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="649c0-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="649c0-152">Estatísticas do FileX</span><span class="sxs-lookup"><span data-stu-id="649c0-152">FileX Statistics</span></span>

<span data-ttu-id="649c0-153">Selecionando \***Ver -> FileX Statistics** _ apresenta as estatísticas de desempenho do FileX do ficheiro de traços atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="649c0-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="649c0-154">Esta informação é exibida para todo o sistema, em todos os abertos .. /objetos mediáticos.</span><span class="sxs-lookup"><span data-stu-id="649c0-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="649c0-155">As estatísticas de desempenho do traço de demonstração filex da amostra são mostradas em _\*Figura 24\*\*.</span><span class="sxs-lookup"><span data-stu-id="649c0-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![Screenshot das Estatísticas do FileX.](./media/user-guide/filex_statistics.png)

<span data-ttu-id="649c0-157">**FIGURA 24**</span><span class="sxs-lookup"><span data-stu-id="649c0-157">**FIGURE 24**</span></span>

<span data-ttu-id="649c0-158">O exemplo mostrado na **Figura 27** indica que foram 19 .. /media abre, 19 .. /media fecha, 19 .. /media flushes, 18 leituras de diretório, 19 escritos de diretório, e 18 cache de diretório falha.</span><span class="sxs-lookup"><span data-stu-id="649c0-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="649c0-159">As informações additonais podem ser vistas deslocando-se para baixo na janela de estatísticas.</span><span class="sxs-lookup"><span data-stu-id="649c0-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="649c0-160">Estatísticas NetX</span><span class="sxs-lookup"><span data-stu-id="649c0-160">NetX Statistics</span></span>

<span data-ttu-id="649c0-161">Selecionando \***Ver -NetX Statistics** _ apresenta as estatísticas de desempenho netX do ficheiro de traços atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="649c0-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="649c0-162">Esta informação é exibida para todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="649c0-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="649c0-163">As estatísticas de desempenho da amostra do traço de demonstração netX são mostradas em _\*Figura 25\*\*.</span><span class="sxs-lookup"><span data-stu-id="649c0-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![Screenshot das Estatísticas NetX.](./media/user-guide/netx_statistics.png)

<span data-ttu-id="649c0-165">**FIGURA 25**</span><span class="sxs-lookup"><span data-stu-id="649c0-165">**FIGURE 25**</span></span>

<span data-ttu-id="649c0-166">O exemplo mostrado na **Figura 25** indica que não houve eventos ARP, Ping ou UDP, mas foram enviados 30 pacotes IP, 1.368 bytes IP enviados, 30 pacotes IP recebidos e 1.360 bytes IP recebidos.</span><span class="sxs-lookup"><span data-stu-id="649c0-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="649c0-167">Informação de arquivo de traços</span><span class="sxs-lookup"><span data-stu-id="649c0-167">Trace File Information</span></span>

<span data-ttu-id="649c0-168">Selecionando \***Ver -> Trace File Information** _ apresenta algumas informações básicas sobre o ficheiro de rastreio aberto.</span><span class="sxs-lookup"><span data-stu-id="649c0-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="649c0-169">Esta informação inclui a ordem byte do ficheiro, o tamanho da fonte de tempo, o número máximo de bytes para cada nome do objeto e o endereço base de todos os ponteiros de arquivo de traços.</span><span class="sxs-lookup"><span data-stu-id="649c0-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="649c0-170">_ *Figura 26*\* mostra as informações do ficheiro de traços para o ficheiro de **_traços padrão demo_threadx.trx._**</span><span class="sxs-lookup"><span data-stu-id="649c0-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![Screenshot da informação do ficheiro TraceX.](./media/user-guide/trace_file_info.png)

<span data-ttu-id="649c0-172">**FIGURA 26**</span><span class="sxs-lookup"><span data-stu-id="649c0-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="649c0-173">Despejo de vestígios crus</span><span class="sxs-lookup"><span data-stu-id="649c0-173">Raw Trace Dump</span></span>

<span data-ttu-id="649c0-174">Selecionando \***Ver -> Despejá-traços brutos** _ apresenta um diálogo para nomear o ficheiro que contém o despejo de vestígios brutos.</span><span class="sxs-lookup"><span data-stu-id="649c0-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="649c0-175">Após a entrada do nome e caminho do ficheiro, o TraceX constrói o ficheiro de traços brutos em formato de texto e lança _*_notepad.exe_*_ para o exibir.</span><span class="sxs-lookup"><span data-stu-id="649c0-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="649c0-176">_ *Figura 27*\* mostra o depósito de ficheiros de traços brutos para o ficheiro de **_traços de demo_threadx.trx_** padrão.</span><span class="sxs-lookup"><span data-stu-id="649c0-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![Screenshot do depósito de vestígios brutos.](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="649c0-178">**FIGURA 27**</span><span class="sxs-lookup"><span data-stu-id="649c0-178">**FIGURE 27**</span></span>
