---
title: Instalação e Utilização do Estúdio GUIX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de design do sistema UI do ESTÚDIO GUIX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827169"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="b3b5c-103">Capítulo 2: Instalação e Utilização do Estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="b3b5c-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="b3b5c-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de design do sistema UI do ESTÚDIO GUIX.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="b3b5c-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="b3b5c-105">Product Distribution</span></span>

<span data-ttu-id="b3b5c-106">Pode obter a aplicação GUIX Studio a partir da [Microsoft App Store,](https://microsoft.com/store/apps) procurando o GUIX Studio, ou indo diretamente para [a página do ESTÚDIO GUIX](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="b3b5c-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="b3b5c-107">Então faça o seguinte.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-107">Then do the following.</span></span>

1. <span data-ttu-id="b3b5c-108">A partir da página do ESTÚDIO GUIX na App Store, clique no botão **Get** ou **Install** para descarregar o GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="b3b5c-109">O seu navegador pode apresentar uma mensagem a perguntar se pretende abrir a Microsoft Store, como mostra a figura abaixo.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="b3b5c-110">Se o fizer, escolha o botão **Abrir.**</span><span class="sxs-lookup"><span data-stu-id="b3b5c-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="b3b5c-111">![Escolha Abrir para instalar o GUIX Studio.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="b3b5c-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="b3b5c-112">Quando a instalação terminar, escolha o botão **Iniciar.**</span><span class="sxs-lookup"><span data-stu-id="b3b5c-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="b3b5c-113">A primeira vez que o GUIX Studio é lançado, exibe uma caixa de diálogo perguntando se deseja clonar o repo GUIX para o seu computador local.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="b3b5c-114">Pode optar por clonar o repositório, indicar onde já clonou o repo, ou optar por não clonar o repo (nesse caso, um projeto de exemplo está instalado no seu computador).</span><span class="sxs-lookup"><span data-stu-id="b3b5c-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="b3b5c-115">![Opte por clonar o repo, apontar para um repo já clonado, ou saltar.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="b3b5c-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="b3b5c-116">!</span><span class="sxs-lookup"><span data-stu-id="b3b5c-116">!</span></span>[!NOTE]
> <span data-ttu-id="b3b5c-117">Pode voltar a esta caixa de diálogo a qualquer momento, escolhendo o **Configure** do menu principal do GUIX Stuido, seguido do **Repositório GUIX.**</span><span class="sxs-lookup"><span data-stu-id="b3b5c-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="b3b5c-118">Depois de terminado o processo de arranque, estará pronto para utilizar o GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="b3b5c-119">Usando o ESTÚDIO GUIX</span><span class="sxs-lookup"><span data-stu-id="b3b5c-119">Using GUIX Studio</span></span>

<span data-ttu-id="b3b5c-120">A utilização do GUIX Studio é fácil - basta executar o ESTÚDIO GUIX através do botão "***Iniciar***".</span><span class="sxs-lookup"><span data-stu-id="b3b5c-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="b3b5c-121">Neste momento, observará o GUIX Studio UI.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="b3b5c-122">Está agora pronto a usar o GUIX Studio para criar graficamente a sua UI incorporada.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="b3b5c-123">A partir daqui cria-se um novo projeto ou abre um projeto existente, incluindo os projetos de exemplo GUIX.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="b3b5c-124">Também pode clicar duas vezes em qualquer ficheiro de projeto guix Studio com uma extensão de "**gxp**", que lançará automaticamente o GUIX Studio e abrirá o projeto referenciado.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="b3b5c-125">Amostras de projetos do estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="b3b5c-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="b3b5c-126">Uma série de ficheiros de projeto guix Studio com a extensão "\***gxp"**_encontram-se no_ \* sub-diretório "_Samples_\*\*" da sua instalação.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="b3b5c-127">Estes projetos de exemplo pré-construídos vão ajudá-lo a se sentir confortável com a utilização do GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="b3b5c-128">Um exemplo de ficheiro de projeto que está sempre presente é o ficheiro \***samples/demo_guix_simple/guix_simple.gxp** _.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="b3b5c-129">Este ficheiro de projeto exemplo mostra a definição de um simples UI GUIX, conforme descrito em _ *_Capítulo 7_*\* deste documento.</span><span class="sxs-lookup"><span data-stu-id="b3b5c-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![Screenshot do GUIX Studio UI.](./media/guix-studio/image_10.png)

<span data-ttu-id="b3b5c-131">**Figura 1**</span><span class="sxs-lookup"><span data-stu-id="b3b5c-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="b3b5c-132">Keyboard Shortcuts</span><span class="sxs-lookup"><span data-stu-id="b3b5c-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="b3b5c-133">**Ctrl + N:** Novo Projeto</span><span class="sxs-lookup"><span data-stu-id="b3b5c-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="b3b5c-134">**Ctrl + O:** Projeto Aberto</span><span class="sxs-lookup"><span data-stu-id="b3b5c-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="b3b5c-135">**CTRL + S:** Projeto Salvar</span><span class="sxs-lookup"><span data-stu-id="b3b5c-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="b3b5c-136">**CTRL + Shift + S:** Salvar projeto como</span><span class="sxs-lookup"><span data-stu-id="b3b5c-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="b3b5c-137">**Alt + F4:** Saída</span><span class="sxs-lookup"><span data-stu-id="b3b5c-137">**Alt + F4:** Exit</span></span>
