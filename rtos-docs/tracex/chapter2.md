---
title: Capítulo 2 - Instalação e utilização do Azure RTOS TraceX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de análise do sistema Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827572"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="eab92-103">Capítulo 2 - Instalação e utilização do Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="eab92-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="eab92-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de análise do sistema Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="eab92-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="eab92-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="eab92-105">Product Distribution</span></span>

<span data-ttu-id="eab92-106">Pode obter a aplicação TraceX a partir da [Microsoft App Store,](https://microsoft.com/store/apps) procurando por TraceX, ou indo diretamente para [a página TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="eab92-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="eab92-107">Então faça o seguinte.</span><span class="sxs-lookup"><span data-stu-id="eab92-107">Then do the following.</span></span>

1. <span data-ttu-id="eab92-108">A partir da página TraceX na App Store, clique no botão **Get** ou **Install** para instalar o TraceX.</span><span class="sxs-lookup"><span data-stu-id="eab92-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="eab92-109">O seu navegador pode apresentar uma mensagem a perguntar se pretende abrir a Microsoft Store, como mostra a figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="eab92-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="eab92-110">Se o fizer, escolha o botão **Abrir.**</span><span class="sxs-lookup"><span data-stu-id="eab92-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="eab92-111">![Escolha Abrir para instalar o TraceX.](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="eab92-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="eab92-112">Quando a instalação terminar, escolha o botão **Iniciar.**</span><span class="sxs-lookup"><span data-stu-id="eab92-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="eab92-113">Usando tracex</span><span class="sxs-lookup"><span data-stu-id="eab92-113">Using TraceX</span></span>

<span data-ttu-id="eab92-114">A utilização do TraceX é tão fácil como abrir um ficheiro de traços dentro do TraceX!</span><span class="sxs-lookup"><span data-stu-id="eab92-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="eab92-115">Executar TraceX através do botão \***Iniciar** _ .</span><span class="sxs-lookup"><span data-stu-id="eab92-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="eab92-116">Neste ponto observará a interface gráfica do utilizador TraceX (GUI).</span><span class="sxs-lookup"><span data-stu-id="eab92-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="eab92-117">Está agora pronto a usar o TraceX para visualizar graficamente um tampão de traço de alvo existente.</span><span class="sxs-lookup"><span data-stu-id="eab92-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="eab92-118">Isto é facilmente feito clicando _ *_File -> Open,_* em seguida, insira o ficheiro de traço binário.</span><span class="sxs-lookup"><span data-stu-id="eab92-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="eab92-119">*Também pode clicar duas vezes em qualquer ficheiro de traço com uma extensão de **trx,** que lançará automaticamente o TraceX.*</span><span class="sxs-lookup"><span data-stu-id="eab92-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![Screenshot do TraceX GUI.](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="eab92-121">**FIGURA 1**</span><span class="sxs-lookup"><span data-stu-id="eab92-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="eab92-122">*Consulte o **Capítulo 5** para obter instruções sobre como gerar tampões de vestígios no alvo utilizando o ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="eab92-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="eab92-123">Exemplos TraceX</span><span class="sxs-lookup"><span data-stu-id="eab92-123">TraceX Examples</span></span>

<span data-ttu-id="eab92-124">A primeira vez que executar a aplicação TraceX, ou quando a aplicação TraceX for atualizada, será solicitado que instale os ficheiros de traços de exemplo TraceX e o ficheiro custom_events.trxc para um diretório definido pelo utilizador na sua máquina local.</span><span class="sxs-lookup"><span data-stu-id="eab92-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="eab92-125">Após esta instalação ter sido concluída, os ficheiros de traços de exemplo com o **trx** de extensão encontram-se no subdiretório **TraceFiles** da sua pasta de instalação.</span><span class="sxs-lookup"><span data-stu-id="eab92-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="eab92-126">Estes exemplos pré-construídos vão ajudá-lo a sentir-se confortável com a utilização do TraceX nos tampões de traço gerados pela ThreadX em execução com a sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="eab92-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="eab92-127">Um ficheiro de traço de exemplo sempre presente é o ficheiro \***demo_threadx.trx** _.</span><span class="sxs-lookup"><span data-stu-id="eab92-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="eab92-128">Este ficheiro de traços de exemplo mostra a execução da demonstração padrão da ThreadX, tal como descrito no Capítulo 6 do _ThreadX Manual do Utilizador\*.</span><span class="sxs-lookup"><span data-stu-id="eab92-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![Screenshot do diálogo aberto em TraceX.](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="eab92-130">**FIGURA 2**</span><span class="sxs-lookup"><span data-stu-id="eab92-130">**FIGURE 2**</span></span>
