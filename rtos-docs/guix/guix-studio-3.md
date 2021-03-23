---
title: Descrição do ESTÚDIO GUIX
description: Este capítulo contém uma descrição da ferramenta de análise do sistema GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826371"
---
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="a353d-103">Capítulo 3: Descrição do ESTÚDIO GUIX</span><span class="sxs-lookup"><span data-stu-id="a353d-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="a353d-104">Este capítulo contém uma descrição da ferramenta de análise do sistema GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="a353d-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="a353d-105">Neste capítulo encontra-se uma descrição da funcionalidade global do GUI.</span><span class="sxs-lookup"><span data-stu-id="a353d-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="a353d-106">Vistas do estúdio GUIX</span><span class="sxs-lookup"><span data-stu-id="a353d-106">GUIX Studio Views</span></span>

<span data-ttu-id="a353d-107">Existem cinco áreas principais do GUIX Studio UI, nomeadamente o ***Toolbar** _, _*_Project View,_*_ _*_Properties View,_*_ _*_Target View_*_ e _*_Resource View_\*_.</span><span class="sxs-lookup"><span data-stu-id="a353d-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="a353d-108">_ *_Figura 2_*\* mostra o básico GUIX Studio UI.</span><span class="sxs-lookup"><span data-stu-id="a353d-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="a353d-109">Cada um dos pontos de vista é discutido nas subsecções seguintes.</span><span class="sxs-lookup"><span data-stu-id="a353d-109">Each of the views is further discussed in the following sub-sections.</span></span>

![Screenshot do básico GUIX Studio UI.](./media/guix-studio/image_10.png)

<span data-ttu-id="a353d-111">**Figura 2**</span><span class="sxs-lookup"><span data-stu-id="a353d-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="a353d-112">Título</span><span class="sxs-lookup"><span data-stu-id="a353d-112">Title</span></span>

- <span data-ttu-id="a353d-113">GUIX Studio 18: O ***Title** _ exibe a versão GUIX Studio, bem como o projeto atualmente aberto, como mostrado no topo de _ *_Figura 2_** anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a353d-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="a353d-114">Barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="a353d-114">Toolbar</span></span>

<span data-ttu-id="a353d-115">A ***Toolbar** _ mostra os botões disponíveis para o desenvolvedor do ESTÚDIO GUIX, como mostrado em _*_Figura 3_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a353d-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![Screenshot da barra de ferramentas DO ESTÚDIO GUIX.](./media/guix-studio/image11.jpg)

<span data-ttu-id="a353d-117">**Figura 3**</span><span class="sxs-lookup"><span data-stu-id="a353d-117">**Figure 3**</span></span>

<span data-ttu-id="a353d-118">Os botões da barra de ferramentas são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a353d-118">The toolbar buttons are defined as follows:</span></span>

![Botão Novo](./media/guix-studio/new-button.png) <span data-ttu-id="a353d-120">Cria um novo projeto guix Studio</span><span class="sxs-lookup"><span data-stu-id="a353d-120">Creates a new GUIX Studio project</span></span>

![Botão aberto](./media/guix-studio/open-button.png) <span data-ttu-id="a353d-122">Abre um projeto do ESTÚDIO GUIX existente</span><span class="sxs-lookup"><span data-stu-id="a353d-122">Opens an existing GUIX Studio project</span></span>

![Botão Guardar](./media/guix-studio/save-button.png) <span data-ttu-id="a353d-124">Salva o projeto</span><span class="sxs-lookup"><span data-stu-id="a353d-124">Saves the project</span></span>

![Botão de corte](./media/guix-studio/cut-button.png) <span data-ttu-id="a353d-126">Widget de corte selecionado, incluindo crianças</span><span class="sxs-lookup"><span data-stu-id="a353d-126">Cut widget selected, including children</span></span>

![botão Copiar](./media/guix-studio/copy-button.png) <span data-ttu-id="a353d-128">Copiar widget selecionado, incluindo crianças</span><span class="sxs-lookup"><span data-stu-id="a353d-128">Copy selected widget, including children</span></span>

![Botão de pasta](./media/guix-studio/paste-button.png) <span data-ttu-id="a353d-130">Widget de pasta e crianças</span><span class="sxs-lookup"><span data-stu-id="a353d-130">Paste widget and children</span></span>

![Botão de alinhamento esquerdo](./media/guix-studio/left-align-button.png) <span data-ttu-id="a353d-132">Widgets selecionados de alinhamento esquerdo</span><span class="sxs-lookup"><span data-stu-id="a353d-132">Left-align selected widgets</span></span>

![Botão de alinhamento direito](./media/guix-studio/right-align-button.png) <span data-ttu-id="a353d-134">Widgets selecionados de alinhamento direito</span><span class="sxs-lookup"><span data-stu-id="a353d-134">Right-align selected widgets</span></span>

![Botão de alinhamento superior](./media/guix-studio/top-align-button.png) <span data-ttu-id="a353d-136">Widgets selecionados de topo</span><span class="sxs-lookup"><span data-stu-id="a353d-136">Top-align selected widgets</span></span>

![Botão de alinhamento inferior](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="a353d-138">Widgets selecionados de baixo</span><span class="sxs-lookup"><span data-stu-id="a353d-138">Bottom-align selected widgets</span></span>

![Botão vertical do espaço](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="a353d-140">Widgets igualmente selecionados em espaço verticalmente</span><span class="sxs-lookup"><span data-stu-id="a353d-140">Equally space selected widgets vertically</span></span>

![Botão horizontal do espaço](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="a353d-142">Widgets igualmente selecionados pelo espaço horizontalmente</span><span class="sxs-lookup"><span data-stu-id="a353d-142">Equally space selected widgets horizontally</span></span>

![Botão de largura igual](./media/guix-studio/equal-width-button.png) <span data-ttu-id="a353d-144">Faça widgets selecionados igual largura</span><span class="sxs-lookup"><span data-stu-id="a353d-144">Make selected widgets equal width</span></span>

![Botão de altura igual](./media/guix-studio/equal-height-button.png) <span data-ttu-id="a353d-146">Faça widgets selecionados igual altura</span><span class="sxs-lookup"><span data-stu-id="a353d-146">Make selected widgets equal height</span></span>

![Mover botão frontal](./media/guix-studio/move-front-button.png) <span data-ttu-id="a353d-148">Mova widgets selecionados para a frente</span><span class="sxs-lookup"><span data-stu-id="a353d-148">Move selected widgets to front</span></span>

![Mova-se para trás botão](./media/guix-studio/move-back-button.png) <span data-ttu-id="a353d-150">Mova widgets selecionados para trás</span><span class="sxs-lookup"><span data-stu-id="a353d-150">Move selected widgets to back</span></span>

![Botão de tamanho](./media/guix-studio/size-button.png) <span data-ttu-id="a353d-152">Tamanho do widget selecionado para conteúdo Zoom fora do ecrã alvo</span><span class="sxs-lookup"><span data-stu-id="a353d-152">Size selected widget to content Zoom out target screen</span></span>

![Botão de zoom para fora](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="a353d-154">Zoom fora do ecrã alvo</span><span class="sxs-lookup"><span data-stu-id="a353d-154">Zoom out target screen</span></span>

![Zoom no botão](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="a353d-156">Zoom no ecrã alvo</span><span class="sxs-lookup"><span data-stu-id="a353d-156">Zoom in target screen</span></span>

![Botão de gravação](./media/guix-studio/record-button.png) <span data-ttu-id="a353d-158">Record Macro</span><span class="sxs-lookup"><span data-stu-id="a353d-158">Record Macro</span></span>

![Botão de reprodução](./media/guix-studio/playback-button.png) <span data-ttu-id="a353d-160">Macro de reprodução</span><span class="sxs-lookup"><span data-stu-id="a353d-160">Playback Macro</span></span>

![Botão de execução](./media/guix-studio/run-button.png) <span data-ttu-id="a353d-162">Aplicação de execução</span><span class="sxs-lookup"><span data-stu-id="a353d-162">Run Application</span></span>

![Sobre o botão](./media/guix-studio/about-button.png) <span data-ttu-id="a353d-164">Sobre o ESTÚDIO GUIX</span><span class="sxs-lookup"><span data-stu-id="a353d-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="a353d-165">Vista do Projeto</span><span class="sxs-lookup"><span data-stu-id="a353d-165">Project View</span></span>

<span data-ttu-id="a353d-166">O \***Project View** _ mostra a lista hierárquica de objetos GUIX que compõem a UI incorporada.</span><span class="sxs-lookup"><span data-stu-id="a353d-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="a353d-167">Novos objetos GUIX podem ser adicionados clicando no objeto-mãe e, em seguida, selecionando um objeto a partir do menu _*_Inserção_*_ (ou clicando à direita no objeto e selecionando a partir do menu de clique à direita).</span><span class="sxs-lookup"><span data-stu-id="a353d-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="a353d-168">_*_Figura 4_*_ abaixo mostra o GUIX Studio _\*_Project View_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a353d-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![Screenshot do GUIX Studio Project View.](./media/guix-studio/image_35.png)

<span data-ttu-id="a353d-170">**Figura 4**</span><span class="sxs-lookup"><span data-stu-id="a353d-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="a353d-171">Vista de propriedades</span><span class="sxs-lookup"><span data-stu-id="a353d-171">Properties View</span></span>

<span data-ttu-id="a353d-172">O ***Properties View** _ mostra informações detalhadas sobre a propriedade do objeto GUIX atualmente selecionado, que podem ser selecionados através do _*_Project View_*_ ou clicando diretamente no objeto na _*_Vista Alvo._\*_</span><span class="sxs-lookup"><span data-stu-id="a353d-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="a353d-173">_*_A figura 5_*_ abaixo mostra o GUIX Studio _\*_Properties View_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a353d-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![Screenshot da visão do estúdio GUIX.](./media/guix-studio/image36.jpg)

<span data-ttu-id="a353d-175">**Figura 5**</span><span class="sxs-lookup"><span data-stu-id="a353d-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="a353d-176">Vista do alvo</span><span class="sxs-lookup"><span data-stu-id="a353d-176">Target View</span></span>

<span data-ttu-id="a353d-177">A \***Target View** _ é a área de design e layout do ecrã WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="a353d-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="a353d-178">Esta vista destina-se a representar o ecrã físico ou os ecrãs disponíveis no hardware do seu alvo.</span><span class="sxs-lookup"><span data-stu-id="a353d-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="a353d-179">Os objetos podem ser selecionados, movidos, redimensionados, etc. através de simples operações de rato.</span><span class="sxs-lookup"><span data-stu-id="a353d-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="a353d-180">Além disso, as operações de alinhamento e botão de ordem Z estão disponíveis em objetos selecionados na Vista Alvo.</span><span class="sxs-lookup"><span data-stu-id="a353d-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="a353d-181">A seleção de um objeto na _*_Vista Alvo_*_ também resultará nas propriedades para que o objeto seja exibido na Vista _*_de Propriedades_*_.</span><span class="sxs-lookup"><span data-stu-id="a353d-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="a353d-182">_*_A figura 6_*_ abaixo mostra o ESTÚDIO GUIX _\*_Target View_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a353d-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![Screenshot do GUIX Studio Target View.](./media/guix-studio/image_37.png)

<span data-ttu-id="a353d-184">**Figura 6**</span><span class="sxs-lookup"><span data-stu-id="a353d-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="a353d-185">Vista de Recursos</span><span class="sxs-lookup"><span data-stu-id="a353d-185">Resource View</span></span>

<span data-ttu-id="a353d-186">O \***Resource View** _ é utilizado para gerir os recursos (cores, fontes, pixelmaps e cordas) disponíveis para ecrãs de aplicações definidos para cada ecrã.</span><span class="sxs-lookup"><span data-stu-id="a353d-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="a353d-187">Pode clicar nos cabeçalhos do grupo de visualização de recursos para expandir cada grupo e examinar o conteúdo do grupo.</span><span class="sxs-lookup"><span data-stu-id="a353d-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="a353d-188">_*_A figura 7_*_ abaixo mostra o GUIX Studio _\*_Resource View_\*\*.</span><span class="sxs-lookup"><span data-stu-id="a353d-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![Screenshot da visão de recursos do estúdio GUIX.](./media/guix-studio/image38.jpg)

<span data-ttu-id="a353d-190">**Figura 7**</span><span class="sxs-lookup"><span data-stu-id="a353d-190">**Figure 7**</span></span>

<span data-ttu-id="a353d-191">O título dos grupos de recursos indica o nome temático atual.</span><span class="sxs-lookup"><span data-stu-id="a353d-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="a353d-192">Se vários temas disponíveis, é possível alternar entre temas clicando na seta para cima e para baixo.</span><span class="sxs-lookup"><span data-stu-id="a353d-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="a353d-193">Cada grupo de recursos na vista acima pode ser expandido ou colapsado clicando no cabeçalho de grupo.</span><span class="sxs-lookup"><span data-stu-id="a353d-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="a353d-194">Segue-se uma descrição mais pormenorizada de cada grupo de recursos no capítulo seguinte.</span><span class="sxs-lookup"><span data-stu-id="a353d-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="a353d-195">O PROJETO ESTÚDIO GUIX</span><span class="sxs-lookup"><span data-stu-id="a353d-195">The GUIX Studio Project</span></span>

<span data-ttu-id="a353d-196">Um projeto guix Studio mantém informações sobre o seu design de ecrã de UI e recursos de UI.</span><span class="sxs-lookup"><span data-stu-id="a353d-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="a353d-197">Os dados do projeto são guardados num ficheiro de formato XML com a extensão ". ***gxp***".</span><span class="sxs-lookup"><span data-stu-id="a353d-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="a353d-198">Uma vez que o ficheiro do projeto é um ficheiro de esquema XML, pode ser versão controlada e partilhada semelhante a qualquer outro ficheiro de origem.</span><span class="sxs-lookup"><span data-stu-id="a353d-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="a353d-199">Quando começar a usar o GUIX Studio, terá de abrir um dos projetos de exemplo fornecidos com a distribuição ou criar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="a353d-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="a353d-200">Todo o seu trabalho é guardado no ficheiro de dados do projeto.</span><span class="sxs-lookup"><span data-stu-id="a353d-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="a353d-201">O GUIX Studio também produz ficheiros de origem ANSI C.</span><span class="sxs-lookup"><span data-stu-id="a353d-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="a353d-202">Estes ficheiros de origem contêm os seus recursos de aplicação ou estruturas de dados que descrevem os seus ecrãs desenhados.</span><span class="sxs-lookup"><span data-stu-id="a353d-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="a353d-203">O GUIX Studio também escreve para estes ficheiros de origem gerados funções API que sabem utilizar as estruturas de dados geradas para criar dinamicamente os seus ecrãs de aplicação.</span><span class="sxs-lookup"><span data-stu-id="a353d-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="a353d-204">O seu software de aplicação irá simplesmente invocar as funções API fornecidas para criar os ecrãs que concebeu no ESTÚDIO GUIX.</span><span class="sxs-lookup"><span data-stu-id="a353d-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="a353d-205">À medida que progride na conceção da sua interface de utilizador, irá periodicamente querer utilizar o GUIX Studio para gerar os ficheiros de saída compatíveis com o GUIX que lhe permitirão construir e executar a interface que concebeu.</span><span class="sxs-lookup"><span data-stu-id="a353d-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="a353d-206">Pode compilar e executar os ficheiros de origem gerados para o hardware do seu alvo ou no seu ambiente de trabalho windows que simula ThreadX e GUIX.</span><span class="sxs-lookup"><span data-stu-id="a353d-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="a353d-207">GUIX Studio Project Organization</span><span class="sxs-lookup"><span data-stu-id="a353d-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="a353d-208">É útil ter algum conhecimento da organização básica de um projeto do GUIX Studio para entender como usar o GUIX Studio de forma eficaz e compreender a informação apresentada no Project View do GUIX Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="a353d-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="a353d-209">O Project View é uma representação visual sumária de toda a informação contida no seu projeto.</span><span class="sxs-lookup"><span data-stu-id="a353d-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="a353d-210">Antes de descrever o projeto, é necessário definir poucos termos.</span><span class="sxs-lookup"><span data-stu-id="a353d-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="a353d-211">Primeiro, usamos o termo **Display** para significar um dispositivo de exibição física.</span><span class="sxs-lookup"><span data-stu-id="a353d-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="a353d-212">Trata-se, na maioria das vezes, de um dispositivo de exibição LCD, mas pode estar a utilizar outras tecnologias.</span><span class="sxs-lookup"><span data-stu-id="a353d-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="a353d-213">O próximo termo é **Screen**, que significa um objeto GUIX de alto nível, geralmente uma janela GUIX, e todos os seus elementos infantis associados.</span><span class="sxs-lookup"><span data-stu-id="a353d-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="a353d-214">Um Ecrã é uma construção de software que pode ser definida e modificada no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a353d-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="a353d-215">Finalmente, um **tema** é uma coleção de recursos.</span><span class="sxs-lookup"><span data-stu-id="a353d-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="a353d-216">Um tema inclui uma tabela de definições de cores, definições de fontes e definições de pixelmap que são projetadas para trabalhar bem em conjunto e apresentar o seu utilizador final com um aspeto e sensação consistentes.</span><span class="sxs-lookup"><span data-stu-id="a353d-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="a353d-217">O projeto inclui primeiro um conjunto de informações globais, como o nome do projeto, o número de ecrãs suportados, a resolução e o formato de cores de cada ecrã, o número de idiomas suportados, o nome de cada idioma apoiada.</span><span class="sxs-lookup"><span data-stu-id="a353d-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="a353d-218">O nome do projeto é o primeiro nó exibido no Project View.</span><span class="sxs-lookup"><span data-stu-id="a353d-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="a353d-219">O projeto em seguida organiza toda a informação necessária para até 4 ecrãs físicos e os ecrãs e recursos disponíveis para cada ecrã.</span><span class="sxs-lookup"><span data-stu-id="a353d-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="a353d-220">Os nomes do visor são os próximos nós de nível na árvore Project View.</span><span class="sxs-lookup"><span data-stu-id="a353d-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="a353d-221">Uma característica única da aplicação guix Studio é suporte incorporado para múltiplos ecrãs físicos, cada um com a sua própria resolução x,y, formato de cores, ecrãs e recursos.</span><span class="sxs-lookup"><span data-stu-id="a353d-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="a353d-222">Embora a grande maioria das aplicações GUIX utilize apenas um ecrã físico, esta capacidade é importante para quem faz um produto que deve suportar múltiplos ecrãs físicos simultâneos.</span><span class="sxs-lookup"><span data-stu-id="a353d-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="a353d-223">Por baixo de cada definição de exibição encontram-se as janelas ou ecrãs de nível superior definidos para esse ecrã.</span><span class="sxs-lookup"><span data-stu-id="a353d-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="a353d-224">As definições do ecrã podem ser aninhadas a qualquer nível, dependendo do número e da nidificação de widgets infantis em cada ecrã.</span><span class="sxs-lookup"><span data-stu-id="a353d-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="a353d-225">Esta organização de widget infantil e de ecrã infantil é exibida de forma gráfica no Project View.</span><span class="sxs-lookup"><span data-stu-id="a353d-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="a353d-226">Também associados a cada ecrã estão os Temas suportados pelo visor e o conteúdo de recursos que compõem cada tema.</span><span class="sxs-lookup"><span data-stu-id="a353d-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="a353d-227">Se o seu projeto incluir vários ecrãs, notará que a Visualização de Recursos altera o seu conteúdo quando selecionar um ecrã e depois outro.</span><span class="sxs-lookup"><span data-stu-id="a353d-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="a353d-228">Isto porque o conteúdo do recurso está ligado a cada visualização.</span><span class="sxs-lookup"><span data-stu-id="a353d-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="a353d-229">Não só o formato de cores pode ser diferente, mas os pixelmaps, cores e fontes que escolhe utilizar podem variar de um ecrã físico para outro.</span><span class="sxs-lookup"><span data-stu-id="a353d-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="a353d-230">O componente final mantido pelo projeto são os dados da tabela de cordas associados a cada visor.</span><span class="sxs-lookup"><span data-stu-id="a353d-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="a353d-231">Uma vez que os ecrãs podem ser de resoluções x,y muito diferentes, os dados de cadeia são mantidos independentemente para cada ecrã definido no projeto.</span><span class="sxs-lookup"><span data-stu-id="a353d-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
