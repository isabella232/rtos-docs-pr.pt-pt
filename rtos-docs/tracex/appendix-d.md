---
title: Apêndice D - Dumping e tampão de vestígios
description: Despejar o tampão de traços criado pela Azure RTOS ThreadX num ficheiro no computador anfitrião é feito através de comandos e/ou utilitários fornecidos pela ferramenta de desenvolvimento específica que está a ser utilizada.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827722"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="7ac6d-103">Apêndice D - Dumping e tampão de vestígios</span><span class="sxs-lookup"><span data-stu-id="7ac6d-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="7ac6d-104">Despejar o tampão de traços criado pela Azure RTOS ThreadX num ficheiro no computador anfitrião é feito através de comandos e/ou utilitários fornecidos pela ferramenta de desenvolvimento específica que está a ser utilizada.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="7ac6d-105">Este apêndice contém exemplos de despejo de um tampão de traços para um ficheiro de hospedeiro em algumas das ferramentas de desenvolvimento mais populares usadas com a ThreadX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="7ac6d-106">Ferramentas BenchX</span><span class="sxs-lookup"><span data-stu-id="7ac6d-106">BenchX Tools</span></span>

<span data-ttu-id="7ac6d-107">O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas BenchX selecionando o botão ***Store Memory To File** _ dentro do _* Memory _View_\*\*, como mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![Screenshot da Vista de Memória nas ferramentas BenchX.](./media/user-guide/image642.jpg)

<span data-ttu-id="7ac6d-109">Neste ponto, especifique o endereço do tampão de rastreamento, tamanho, nome do ficheiro de destino (incluindo o caminho) e selecione o botão ***Guardar*** como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="7ac6d-110">Isto criará o ficheiro binário de rastreio para visualização dentro do TraceX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-110">This will create the binary trace file for viewing within TraceX.</span></span>

![Screenshot das ferramentas BenchX economize o diálogo.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="7ac6d-112">Ferramentas RealView</span><span class="sxs-lookup"><span data-stu-id="7ac6d-112">RealView Tools</span></span>

<span data-ttu-id="7ac6d-113">O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas ARM RealView, introduzindo o seguinte comando na linha de comando em RealView:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="7ac6d-114">Após a conclusão, o ficheiro ***trace_file.trx*** conterá o tampão de traço que está localizado a partir do endereço 0x6860 e vai até endereçar 0xE560.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="7ac6d-115">Este ficheiro está pronto para ser visualizado pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="7ac6d-116">Ferramentas IAR</span><span class="sxs-lookup"><span data-stu-id="7ac6d-116">IAR Tools</span></span>

<span data-ttu-id="7ac6d-117">O tampão de rastreio pode ser despejado facilmente num ficheiro de anfitrião com as ferramentas IAR clicando simplesmente na vista de memória e selecionando o ***Memory Save...***</span><span class="sxs-lookup"><span data-stu-id="7ac6d-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="7ac6d-118">opção, como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-118">option, as shown below.</span></span>

![Screenshot da opção Memória Guardar nas ferramentas IAR.](./media/user-guide/image0_311.jpg)

<span data-ttu-id="7ac6d-120">Isto resulta no diálogo \***Memory Save** _ a ser apresentado.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="7ac6d-121">Introduza o endereço inicial e final e o nome do ficheiro de rastreio e, em seguida, selecione o botão _*_Guardar._*_</span><span class="sxs-lookup"><span data-stu-id="7ac6d-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="7ac6d-122">No exemplo apresentado abaixo, as ferramentas IAR guardam o tampão de traço especificado nos registos intel HEX no ficheiro _\*_trace_file.hex_\*\*.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![Screenshot das ferramentas IAR Memória Guardar o diálogo.](./media/user-guide/image648.jpg)

<span data-ttu-id="7ac6d-124">Neste momento, temos o tampão de vestígios guardado no ficheiro ***trace_file.hex*** no hospedeiro e está pronto para ser visualizado com o TraceX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="7ac6d-125">Ferramentas CodeWarrior</span><span class="sxs-lookup"><span data-stu-id="7ac6d-125">CodeWarrior Tools</span></span>

<span data-ttu-id="7ac6d-126">O tampão de vestígios pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas CodeWarrior, introduzindo o comando \***save** _ na Janela de Comando.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="7ac6d-127">O seguinte exemplo _ *_save_*\* comando assume que o tampão de traços começa em 0x102200 e termina em 0x109F00:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="7ac6d-128">Isto resulta na guarda do tampão de vestígios no ficheiro ***trace_file.trx*** no hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="7ac6d-129">Ferramentas MPLAB</span><span class="sxs-lookup"><span data-stu-id="7ac6d-129">MPLAB Tools</span></span>

<span data-ttu-id="7ac6d-130">O MPLAB pode criar um ficheiro de traços compatíveis com o TraceX através do seu utilitário de Tabela de Exportação, que permite a exportação de qualquer gama de memória para um ficheiro de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="7ac6d-131">Para utilizar este utilitário para criar um ficheiro de rastreio para a TraceX, proceda da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="7ac6d-132">**Passo 1** Abra uma janela de memória selecionando a Memória de >.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![Screenshot da Memória selecionada no menu Ver.](./media/user-guide/image0_316.jpg)

<span data-ttu-id="7ac6d-134">**Passo 2** Clique com o botão direito dentro da **Visualização de Memória** para mostrar uma lista de opções.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="7ac6d-135">Especifique **o formato do display -1 Byte** para selecionar o byte display..</span><span class="sxs-lookup"><span data-stu-id="7ac6d-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![Screenshot da visualização da memória com a opção 'Display' Format selecionada.](./media/user-guide/image650.png)

![Screenshot do diálogo Go To.](./media/user-guide/image651.jpg)

<span data-ttu-id="7ac6d-138">**Passo 3** Clique novamente no botão direito dentro da Janela **visualização** da memória e selecione **Go To**, que abre uma caixa de diálogo que lhe permite especificar o endereço do tampão do evento.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="7ac6d-139">Este exemplo mostra **_event_buffer_** a ser exibido.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-139">This example shows **_event_buffer_** being displayed.</span></span>

![Screenshot da visualização da memória com a opção Go To selecionada.](./media/user-guide/image0_312.jpg)

![Screenshot de um exemplo que mostra o event_buffer a ser exibido.](./media/user-guide/image653.png)

<span data-ttu-id="7ac6d-142">**Passo 4** Isto destaca o conteúdo da primeira localização do tampão de traço, que é sempre a cadeia BTXT....</span><span class="sxs-lookup"><span data-stu-id="7ac6d-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![Screenshot da primeira localização do tampão de vestígios.](./media/user-guide/image0_313.jpg)

<span data-ttu-id="7ac6d-144">**Passo 5** Agora, clique com o botão direito novamente para trazer o menu de opções e selecione **Tabela de Exportação**.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![Screenshot da Vista de Memória com a opção Tabela de Exportação selecionada.](./media/user-guide/image0_314.jpg)

<span data-ttu-id="7ac6d-146">**Passo 6** Isto eleva o diálogo da tabela de **exportação,** como mostra.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="7ac6d-147">Especifique a gama de endereços para exportação.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="7ac6d-148">Para um tampão de traço de 8K, como é o caso neste exemplo, especifique o alcance 0xA00006AC para 0xA00026AC e introduza um nome para o ficheiro anfitrião a ser criado (demo_threadx.trx neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="7ac6d-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="7ac6d-149">! [[Screenshot do Export As dialog.](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ac6d-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="7ac6d-150">**Passo 7** Um ficheiro chamado **demo_threadx.trx** será criado no anfitrião, e este ficheiro pode ser aberto pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="7ac6d-151">Ferramentas GHS</span><span class="sxs-lookup"><span data-stu-id="7ac6d-151">GHS Tools</span></span>

<span data-ttu-id="7ac6d-152">O tampão de rastreio pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas GHS, introduzindo o seguinte comando na linha de comando na janela de comando do depurg:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="7ac6d-153">Após a conclusão, o ficheiro **demo_threadx.trx** conterá o tampão de vestígios localizado no event_buffer com um tamanho de 32.768 bytes e está pronto para ser visualizado pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="7ac6d-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="7ac6d-154">Renesas HEW</span></span>

<span data-ttu-id="7ac6d-155">O tampão de rastreio pode ser despejado facilmente num ficheiro de hospedeiro com as ferramentas HEW da Renasas seguindo os três passos (e subpassos) abaixo:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="7ac6d-156">**Passo 1** Abrir a janela de memória.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="7ac6d-157">! [[Screenshot da Janela de Memória.](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="7ac6d-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="7ac6d-158">**Passo 2** Coloque o cursor dentro da janela da memória e clique à direita.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-158">**Step 2** Place cursor within memory window and right click.</span></span>

![Screenshot da Janela memória com a opção Guardar selecionada.](./media/user-guide/image0_315.jpg)

<span data-ttu-id="7ac6d-160">**Passo 3** Selecione Guardar e, em seguida, na Memória Guardar Como janela fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7ac6d-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="7ac6d-161">Selecione formato de ficheiro: Binário.</span><span class="sxs-lookup"><span data-stu-id="7ac6d-161">Select File format: Binary.</span></span>
- <span data-ttu-id="7ac6d-162">Especificar o nome de ficheiro: Como Desejado</span><span class="sxs-lookup"><span data-stu-id="7ac6d-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="7ac6d-163">Especificar endereço de início: trace_buffer</span><span class="sxs-lookup"><span data-stu-id="7ac6d-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="7ac6d-164">Especificar endereço final: (trace_buffer+tamanho)</span><span class="sxs-lookup"><span data-stu-id="7ac6d-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="7ac6d-165">Especificar tamanho de acesso: 1</span><span class="sxs-lookup"><span data-stu-id="7ac6d-165">Specify Access size: 1</span></span>
- <span data-ttu-id="7ac6d-166">Clicar em Guardar</span><span class="sxs-lookup"><span data-stu-id="7ac6d-166">Click Save</span></span>

![Screenshot do Save Memory Como diálogo.](./media/user-guide/image659.jpg)