---
title: Projeto Exemplo Simples
description: Este capítulo descreve como criar um projeto de exemplo no GUIX Studio e executar o exemplo no GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826426"
---
# <a name="chapter-10-example-project"></a><span data-ttu-id="c99a4-103">Capítulo 10: Exemplo Projeto</span><span class="sxs-lookup"><span data-stu-id="c99a4-103">Chapter 10: Example Project</span></span>

<span data-ttu-id="c99a4-104">Este capítulo descreve como criar um projeto de exemplo no GUIX Studio e executar o exemplo no GUIX.</span><span class="sxs-lookup"><span data-stu-id="c99a4-104">This chapter describes how to create an example project in GUIX Studio and execute the example on GUIX.</span></span>

## <a name="create-new-project"></a><span data-ttu-id="c99a4-105">Criar Novo Projeto</span><span class="sxs-lookup"><span data-stu-id="c99a4-105">Create New Project</span></span>

<span data-ttu-id="c99a4-106">O primeiro passo é criar um novo projeto e configurar os ecrãs e linguagens que o projeto irá apoiar.</span><span class="sxs-lookup"><span data-stu-id="c99a4-106">The first step is creating a new project and configuring the displays and languages that the project will support.</span></span> <span data-ttu-id="c99a4-107">Quando iniciar o GUIX Studio, verá o ecrã de ***Projetos Recentes:***</span><span class="sxs-lookup"><span data-stu-id="c99a4-107">When you first start GUIX Studio, you will see the ***Recent Projects*** screen:</span></span>

![Screenshot do diálogo guix Studio Recent Projects.](./media/guix-studio/recent_projects.png)

<span data-ttu-id="c99a4-109">**Figura 10.1**</span><span class="sxs-lookup"><span data-stu-id="c99a4-109">**Figure 10.1**</span></span>

<span data-ttu-id="c99a4-110">Clique no \***Criar Novo Projeto** _...</span><span class="sxs-lookup"><span data-stu-id="c99a4-110">Click on the \***Create New Project** _…</span></span> <span data-ttu-id="c99a4-111">botão para iniciar um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-111">button to begin a new project.</span></span> <span data-ttu-id="c99a4-112">Será apresentado com o _ *_Novo Projeto GUIX_*\* diálogo, mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="c99a4-112">You will be presented with the _ *_New GUIX Project_*\* dialog, shown here:</span></span>

![Screenshot do estúdio GUIX Criar novo diálogo de projeto.](./media/guix-studio/create_new_project.png)

<span data-ttu-id="c99a4-114">**Figura 10.2**</span><span class="sxs-lookup"><span data-stu-id="c99a4-114">**Figure 10.2**</span></span>

<span data-ttu-id="c99a4-115">Digite o nome "***new_example***" como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-115">Type the name "***new_example***" as the project name.</span></span> <span data-ttu-id="c99a4-116">Os nomes do projeto devem usar regras de nomeação variáveis C padrão, ou seja, sem caracteres especiais ou reservados.</span><span class="sxs-lookup"><span data-stu-id="c99a4-116">Project names should use standard C variable naming rules, that is, no special or reserved characters.</span></span> <span data-ttu-id="c99a4-117">Digite o caminho para o local onde o projeto deve ser guardado.</span><span class="sxs-lookup"><span data-stu-id="c99a4-117">Type the path to the location where the project should be saved.</span></span> <span data-ttu-id="c99a4-118">O caminho deve ser um diretório de sistema de ficheiros válido, ou seja, o GUIX Studio não criará o diretório se não existir.</span><span class="sxs-lookup"><span data-stu-id="c99a4-118">The path must be a valid file system directory, that is, GUIX Studio will not create the directory if it does not exist.</span></span> <span data-ttu-id="c99a4-119">Clique em "OK" para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-119">Click "OK" to create the project.</span></span>

<span data-ttu-id="c99a4-120">O próximo ecrã mostrado é o ecrã de Configuração do Projeto, mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="c99a4-120">The next screen shown is the Project Configuration screen, shown here:</span></span>

![Screenshot do diálogo do Guix Studio Configure Project.](./media/guix-studio/config_new_project.png)

<span data-ttu-id="c99a4-122">**Figura 10.3**</span><span class="sxs-lookup"><span data-stu-id="c99a4-122">**Figure 10.3**</span></span>

<span data-ttu-id="c99a4-123">Este diálogo permite especificar quantos ecrãs o seu projeto irá suportar e dar um nome a cada visualização.</span><span class="sxs-lookup"><span data-stu-id="c99a4-123">This dialog allows you to specify how many displays your project will support, and give a name to each display.</span></span> <span data-ttu-id="c99a4-124">Deve especificar o formato de cor suportado por cada ecrã e, opcionalmente, escrever um nome de pathname para os ficheiros de saída gerados pelo Studio para cada ecrã.</span><span class="sxs-lookup"><span data-stu-id="c99a4-124">You must specify the color format supported by each display, and optionally type a pathname for the output files generated by Studio for each display.</span></span> <span data-ttu-id="c99a4-125">O diretório predefinido para os ficheiros de saída é "***" ", \\*** o que significa que os ficheiros de saída C são escritos para o mesmo diretório que o próprio projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-125">The default directory for the output files is "***.\\***", meaning the C output files are written to the same directory as the project itself.</span></span>

<span data-ttu-id="c99a4-126">Para este exemplo, deixe o número ***de visualizações** _ definido para "1", escreva o nome "_*_main_display_*_" no campo do nome do visor, e verifique "_*_alocar a memória_\*_ de tela ".</span><span class="sxs-lookup"><span data-stu-id="c99a4-126">For this example, leave the ***Number of Displays** _ set to "1", type the name "_*_main_display_*_" in the display name field, and check "_*_allocate canvas memory_\*_".</span></span> <span data-ttu-id="c99a4-127">Deixe a resolução, o formato de cores e os campos de diretório nos seus valores predefinidos, e clique em _\*_OK_\*\*.</span><span class="sxs-lookup"><span data-stu-id="c99a4-127">Leave the resolution, color format, and directory fields at their default values, and click _\*_OK_\*\*.</span></span>

<span data-ttu-id="c99a4-128">Deverá agora ver o seu projeto aberto com o Studio IDE, como mostra a figura 10.4:</span><span class="sxs-lookup"><span data-stu-id="c99a4-128">You should now see your project open with the Studio IDE, as shown in figure 10.4:</span></span>

![Screenshot de um projeto aberto com o Studio IDE.](./media/guix-studio/initial_screen.png)

<span data-ttu-id="c99a4-130">**Figura 10.4**</span><span class="sxs-lookup"><span data-stu-id="c99a4-130">**Figure 10.4**</span></span>

<span data-ttu-id="c99a4-131">Ao criar um novo projeto, o GUIX Studio cria automaticamente uma janela padrão como ponto de partida para o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-131">When you create a new project, GUIX Studio automatically creates a default window as the starting point for your project.</span></span> <span data-ttu-id="c99a4-132">Esta caixa cinzenta é a janela padrão criada para si, centrada na *Vista Alvo*.</span><span class="sxs-lookup"><span data-stu-id="c99a4-132">This gray box is the default window created for you, centered within the *Target View*.</span></span>

<span data-ttu-id="c99a4-133">Se esta janela não for selecionada, clique na janela de modo a que a caixa de seleção tracejada seja desenhada à volta da janela.</span><span class="sxs-lookup"><span data-stu-id="c99a4-133">If this window is not selected, click on the window so that the dashed selection box is drawn around the window.</span></span> <span data-ttu-id="c99a4-134">Agora na ***Visualização de Propriedades** _, altere o _*_Nome Widget,_*_ _*_Widget Id_*_, _*_Esquerda,_*_ _*_Topo,_*_ _*_Largura,_*_ _*_Altura_*_ e _ *_Fronteira_** para combinar com as definições mostradas abaixo.</span><span class="sxs-lookup"><span data-stu-id="c99a4-134">Now in the ***Properties View** _, change the _*_Widget Name_*_, _*_Widget Id_*_, _*_Left_*_, _*_Top_*_, _*_Width_*_, _*_Height_*_, and _ *_Border_** to match those settings shown below.</span></span> <span data-ttu-id="c99a4-135">Ao efetuar estas alterações, deverá ver as suas alterações imediatamente a produzir efeito dentro da Vista Alvo.</span><span class="sxs-lookup"><span data-stu-id="c99a4-135">As you make these changes, you should see your changes immediately taking effect within the Target View.</span></span>

![Screenshot do diálogo Properties View.](./media/guix-studio/initial_window_properties.png)

<span data-ttu-id="c99a4-137">**Figura 10.5**</span><span class="sxs-lookup"><span data-stu-id="c99a4-137">**Figure 10.5**</span></span>

<span data-ttu-id="c99a4-138">Em seguida, adicionaremos um recurso pixelmap para ser usado dentro de um widget \***GX_ICON** _ .</span><span class="sxs-lookup"><span data-stu-id="c99a4-138">Next we will add a pixelmap resource to be used within a \***GX_ICON** _ widget.</span></span> <span data-ttu-id="c99a4-139">Vários ícones são fornecidos com a sua distribuição guix Studio que funcionará bem para este exemplo.</span><span class="sxs-lookup"><span data-stu-id="c99a4-139">Several icons are provided with your GUIX Studio distribution that will work fine for this example.</span></span> <span data-ttu-id="c99a4-140">Expanda a sua Visualização de Recursos _*_Pixelmaps_*_ e clique no botão _ *_Add New Pixelmap_*\* :</span><span class="sxs-lookup"><span data-stu-id="c99a4-140">Expand your _*_Pixelmaps_*_ Resource View and click the _ *_Add New Pixelmap_*\* button:</span></span>

![Screenshot do botão Add New Pixelmap.](./media/guix-studio/image74.jpg)

<span data-ttu-id="c99a4-142">Navegue na sua pasta de instalação GUIX Studio e na pasta ***./graphics/icons** _ selecione o ficheiro nomeado _*_i_history_lg.png_\*_.</span><span class="sxs-lookup"><span data-stu-id="c99a4-142">Browse to your GUIX Studio installation folder, and within the ***./graphics/icons** _ folder select the file named _*_i_history_lg.png_\*_.</span></span> <span data-ttu-id="c99a4-143">Clique _*_em Aberto_*_ para adicionar este recurso ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-143">Click _*_Open_*_ to add this resource to your project.</span></span> <span data-ttu-id="c99a4-144">A sua _ *_Pixelmaps_*\* Resource View deve agora mostrar uma pré-visualização da imagem do ícone recém-adicionada:</span><span class="sxs-lookup"><span data-stu-id="c99a4-144">Your _ *_Pixelmaps_*\* Resource View should now show a preview of the newly added icon image:</span></span>

![Screenshot da Visualização de Recursos pixelmaps.](./media/guix-studio/example_add_pixelmap.png)

<span data-ttu-id="c99a4-146">**Figura 10.6**</span><span class="sxs-lookup"><span data-stu-id="c99a4-146">**Figure 10.6**</span></span>

<span data-ttu-id="c99a4-147">Usaremos este novo recurso de imagem mais tarde como parte do nosso design de UI.</span><span class="sxs-lookup"><span data-stu-id="c99a4-147">We will use this new image resource later as part of our UI design.</span></span>

<span data-ttu-id="c99a4-148">Similares à adição de um recurso pixelmap, adicionamos um novo recurso de fonte à nossa caixa de ferramentas para que possamos usar este tipo de letra mais tarde no nosso design.</span><span class="sxs-lookup"><span data-stu-id="c99a4-148">Similar to adding a pixelmap resource, we will add a new font resource to our toolbox so that we can use this font later in our design.</span></span> <span data-ttu-id="c99a4-149">Expandir a ***Visualização de** recursos \* e clicar no botão _*_Adicionar Nova Fonte._\*_</span><span class="sxs-lookup"><span data-stu-id="c99a4-149">Expand the ***Fonts** _ Resource View and click on the _*_Add New Font_\*_ button.</span></span> <span data-ttu-id="c99a4-150">Esta ação invocará o diálogo de fonte _*_add/Edit._*_</span><span class="sxs-lookup"><span data-stu-id="c99a4-150">This action will invoke the _*_Add/Edit_*_ font dialog.</span></span> <span data-ttu-id="c99a4-151">Em seguida, navegue para as fontes GUIX fornecidas na pasta de instalação do GUIX Studio, _\*_ . \\ fontes \\ verasans_ *_, e selecione o ficheiro de fonte TrueType chamado _*_VeraIt.ttf_*_. Escreva o nome de fonte "_*_MEDIUM_ITALIC_" no campo de nome *_da fonte, e escreva "_*_30_\*\*" no campo de altura.</span><span class="sxs-lookup"><span data-stu-id="c99a4-151">Next, browse to the supplied GUIX fonts in the GUIX Studio installation folder, _\*_.\\fonts\\verasans_ *_, and select the TrueType font file named _*_VeraIt.ttf_*_. Type font the font name "_*_MEDIUM_ITALIC_*_" in the font name field, and type "_*_30_\*\*" in the height field.</span></span> <span data-ttu-id="c99a4-152">O seu diálogo deve agora ser assim:</span><span class="sxs-lookup"><span data-stu-id="c99a4-152">Your dialog should now look like this:</span></span>

![Screenshot do diálogo Edit Font.](./media/guix-studio/example_add_font.png)

<span data-ttu-id="c99a4-154">**Figura 10.7**</span><span class="sxs-lookup"><span data-stu-id="c99a4-154">**Figure 10.7**</span></span>

<span data-ttu-id="c99a4-155">Clique ***em OK*** para adicionar este tipo de letra ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c99a4-155">Click ***OK*** to add this font to your project.</span></span> <span data-ttu-id="c99a4-156">Deverá agora ver o tipo de letra na sua Visão de Recursos:</span><span class="sxs-lookup"><span data-stu-id="c99a4-156">You should now see the font in your Resource View:</span></span>

![Screenshot das fontes na vista de recursos.](./media/guix-studio/example_font_added.png)

<span data-ttu-id="c99a4-158">**Figura 10.8**</span><span class="sxs-lookup"><span data-stu-id="c99a4-158">**Figure 10.8**</span></span>

<span data-ttu-id="c99a4-159">Usaremos este novo tipo de letra mais tarde no nosso design de UI.</span><span class="sxs-lookup"><span data-stu-id="c99a4-159">We will use this new font later in our UI design.</span></span>

<span data-ttu-id="c99a4-160">Agora que temos novos recursos disponíveis, precisamos adicionar alguns widgets infantis ao nosso ecrã que possam utilizar estes recursos.</span><span class="sxs-lookup"><span data-stu-id="c99a4-160">Now that we have some new resources available, we need to add some child widgets to our screen that can utilize these resources.</span></span> <span data-ttu-id="c99a4-161">Selecione a janela previamente criada denominada "\***hello_world** _" clicando à direita na janela na Vista Alvo.</span><span class="sxs-lookup"><span data-stu-id="c99a4-161">Select the previously created window named "\***hello_world** _" by right-clicking on the window in the Target View.</span></span> <span data-ttu-id="c99a4-162">No menu pop-up que agora é apresentado, selecione o comando do menu _*_Insira, Texto, Prompt_*_ para inserir um novo widget _ *_GX_PROMPT_*\* e fixe o widget à janela de fundo.</span><span class="sxs-lookup"><span data-stu-id="c99a4-162">In the pop-up menu that is now displayed, select the menu command _*_Insert, Text, Prompt_*_ to insert a new _ *_GX_PROMPT_*\* widget and attach the widget to the background window.</span></span> <span data-ttu-id="c99a4-163">Sua janela deve agora ser assim:</span><span class="sxs-lookup"><span data-stu-id="c99a4-163">Your window should now look like this:</span></span>

![Screenshot de um menu pop-up com a seleção Prompt](./media/guix-studio/image78.jpg)

<span data-ttu-id="c99a4-165">**Figura 10.9**</span><span class="sxs-lookup"><span data-stu-id="c99a4-165">**Figure 10.9**</span></span>

<span data-ttu-id="c99a4-166">Clique na fonte denominada "\***MEDIUM_ITALIC** _" na _ *_Visualização_* de recursos \* e arraste e deixe cair o tipo de letra no widget de solicitação.</span><span class="sxs-lookup"><span data-stu-id="c99a4-166">Click on the font named "***MEDIUM_ITALIC** _" in the _ *_Fonts_** Resource View, and drag and drop the font on the prompt widget.</span></span> <span data-ttu-id="c99a4-167">Em seguida, edite as propriedades prontas como mostrado na figura 10.10 para redimensionar o pedido, definir a transparência rápida e alterar o texto e o estilo rápidos:</span><span class="sxs-lookup"><span data-stu-id="c99a4-167">Next, edit the prompt properties as shown in figure 10.10 to resize the prompt, set the prompt transparency, and change the prompt text and style:</span></span>

![Screenshot da visualização do imóvel para o pedido.](./media/guix-studio/image79.jpg)

<span data-ttu-id="c99a4-169">**Figura 10.10**</span><span class="sxs-lookup"><span data-stu-id="c99a4-169">**Figure 10.10**</span></span>

<span data-ttu-id="c99a4-170">Pode ser necessário deslocar-se verticalmente na Visualização de Propriedades para ver cada uma destas definições dependendo da resolução do ecrã.</span><span class="sxs-lookup"><span data-stu-id="c99a4-170">You may need to scroll vertically in the Properties View to see each of these settings depending on your screen resolution.</span></span> <span data-ttu-id="c99a4-171">Depois de es fazer estas alterações, a sua Visão alvo deve agora ser assim:</span><span class="sxs-lookup"><span data-stu-id="c99a4-171">After making these changes, your Target View should now look like this:</span></span>

![Screenshot de um menu pop-up com a seleção Hello World.](./media/guix-studio/image80.jpg)

<span data-ttu-id="c99a4-173">**Figura 10.11**</span><span class="sxs-lookup"><span data-stu-id="c99a4-173">**Figure 10.11**</span></span>

<span data-ttu-id="c99a4-174">Em seguida, colocaremos um widget estilo Icon Button no ecrã.</span><span class="sxs-lookup"><span data-stu-id="c99a4-174">Next we will place an Icon Button style widget on the screen.</span></span> <span data-ttu-id="c99a4-175">Selecione a janela de fundo clicando nela e use o menu de nível superior ou o menu pop-up de clique direito para selecionar ***Insira, Botão, Botão de Ícone** _ para adicionar um novo _*_GX_ICON_BUTTON_\*_ à janela.</span><span class="sxs-lookup"><span data-stu-id="c99a4-175">Select the background window by clicking on it, and use either the top-level menu or the right-click pop-up menu to select ***Insert, Button, Icon Button** _ to add a new _*_GX_ICON_BUTTON_\*_ to the window.</span></span> <span data-ttu-id="c99a4-176">Clique no Ícone nomeado _ *_I_HISTORY_LG_*\* que adicionamos anteriormente e arraste-o para o botão de ícone.</span><span class="sxs-lookup"><span data-stu-id="c99a4-176">Click on the Icon named _ *_I_HISTORY_LG_*\* that we added earlier and drag it to the icon button.</span></span> <span data-ttu-id="c99a4-177">Utilizando a vista de propriedades, ajuste a posição e o tamanho do ícone como mostra abaixo:</span><span class="sxs-lookup"><span data-stu-id="c99a4-177">Using the properties view, adjust the icon position and size as show below:</span></span>

![Screenshot do View Properties para o widget estilo botão do ícone.](./media/guix-studio/image81.jpg)

<span data-ttu-id="c99a4-179">**Figura 10.12**</span><span class="sxs-lookup"><span data-stu-id="c99a4-179">**Figure 10.12**</span></span>

<span data-ttu-id="c99a4-180">O seu ecrã deve agora ser assim:</span><span class="sxs-lookup"><span data-stu-id="c99a4-180">Your screen should now look like this:</span></span>

![Screenshot de um menu pop-up com o ícone Hello World e clipboard.](./media/guix-studio/image82.jpg)

<span data-ttu-id="c99a4-182">**Figura 10.13**</span><span class="sxs-lookup"><span data-stu-id="c99a4-182">**Figure 10.13**</span></span>

<span data-ttu-id="c99a4-183">Vamos chamar isto completo para o design de tela de exemplo simples.</span><span class="sxs-lookup"><span data-stu-id="c99a4-183">We will call this complete for the simple example screen design.</span></span> <span data-ttu-id="c99a4-184">Os ecrãs de aplicações reais serão provavelmente muito mais sofisticados, mas isto é suficiente para lhe mostrar como usar o GUIX Studio para criar os seus próprios ecrãs de aplicações.</span><span class="sxs-lookup"><span data-stu-id="c99a4-184">Your actual application screens will likely be much more sophisticated, but this is enough to show you how to use GUIX Studio to create your own application screens.</span></span>

## <a name="generate-resource-and-application-code"></a><span data-ttu-id="c99a4-185">Gerar Código de Recursos e Aplicação</span><span class="sxs-lookup"><span data-stu-id="c99a4-185">Generate Resource and Application Code</span></span>

<span data-ttu-id="c99a4-186">O próximo passo é gerar o ficheiro de recursos e o ficheiro de especificações que definem a UI embutida do TEMPO DE EXECUÇÃO GUIX.</span><span class="sxs-lookup"><span data-stu-id="c99a4-186">The next step is to generate the resource file and specification file that define the embedded GUIX run-time UI.</span></span> <span data-ttu-id="c99a4-187">Para gerar os seus ficheiros de saída, necessitará de clicar no nó ***main_display** _ no Visor do Projeto e selecione o comando _ *_Gerar Ficheiros de Recursos_**</span><span class="sxs-lookup"><span data-stu-id="c99a4-187">To generate your output files you will need right-click on the ***main_display** _ node in the Project View, and select the _ *_Generate Resource Files_** command.</span></span> <span data-ttu-id="c99a4-188">Observará uma janela de informação que indica que os seus ficheiros de recursos foram gerados, como mostra a figura 10.14:</span><span class="sxs-lookup"><span data-stu-id="c99a4-188">You will observe an information window that indicates your resource files have been generated, as shown in figure 10.14:</span></span>

![Screenshot de um diálogo de notificação.](./media/guix-studio/image83.jpg)

<span data-ttu-id="c99a4-190">**Figura 10.14**</span><span class="sxs-lookup"><span data-stu-id="c99a4-190">**Figure 10.14**</span></span>

<span data-ttu-id="c99a4-191">Clique **em**\* OK _ para rejeitar esta notificação e use o mesmo procedimento para clicar no nó _*_main_display_*_ e selecione o comando _ *_Gerar Ficheiros de Especificação_*\* .</span><span class="sxs-lookup"><span data-stu-id="c99a4-191">Click ***OK** _ to dismiss this notification, and use the same procedure to right-click on the _*_main_display_*_ node and select the _ *_Generate Specification Files_** command.</span></span> <span data-ttu-id="c99a4-192">Deve observar uma janela de notificação semelhante.</span><span class="sxs-lookup"><span data-stu-id="c99a4-192">You should observe a similar notification window.</span></span> <span data-ttu-id="c99a4-193">Agora gerou os seus ficheiros simples de aplicações uI.</span><span class="sxs-lookup"><span data-stu-id="c99a4-193">You have now generated your simple UI application files.</span></span>

## <a name="create-user-supplied-code"></a><span data-ttu-id="c99a4-194">Criar código fornecido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="c99a4-194">Create User Supplied Code</span></span>

<span data-ttu-id="c99a4-195">O próximo passo é criar o seu próprio ficheiro de aplicação que irá invocar o design de ecrã gerado pelo GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="c99a4-195">The next step is to create your own application file that will invoke the GUIX Studio-generated screen design.</span></span> <span data-ttu-id="c99a4-196">Utilizando o seu editor preferido, crie um ficheiro de origem denominado ***new_example.c***, e introduza o seguinte código fonte neste ficheiro:</span><span class="sxs-lookup"><span data-stu-id="c99a4-196">Using your preferred editor, create a source file named ***new_example.c***, and enter the following source code into this file:</span></span>

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

<span data-ttu-id="c99a4-197">O código de origem acima cria um fio ThreadX típico nomeado `GUIX New Example Thread` com um tamanho de pilha de bytes 4K.</span><span class="sxs-lookup"><span data-stu-id="c99a4-197">The source code above creates a typical ThreadX thread named `GUIX New Example Thread` with a stack size of 4K bytes.</span></span> <span data-ttu-id="c99a4-198">O trabalho interessante começa na função denominada ***new_example_thread_entry.***</span><span class="sxs-lookup"><span data-stu-id="c99a4-198">The interesting work begins in the function named ***new_example_thread_entry***.</span></span> <span data-ttu-id="c99a4-199">Esta função é onde o fio específico GUIX começa a funcionar.</span><span class="sxs-lookup"><span data-stu-id="c99a4-199">This function is where the GUIX specific thread begins to run.</span></span>

<span data-ttu-id="c99a4-200">A primeira chamada é para a função denominada ***gx_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="c99a4-200">The first call is to the function named ***gx_system_initialize***.</span></span> <span data-ttu-id="c99a4-201">Esta chamada é sempre necessária antes de serem invocadas quaisquer outras APIs GUIX para preparar a biblioteca GUIX para primeira utilização.</span><span class="sxs-lookup"><span data-stu-id="c99a4-201">This call is always required before any other GUIX APIs are invoked to prepare the GUIX library for first use.</span></span>

<span data-ttu-id="c99a4-202">Em seguida, o exemplo chama a função ***gx_studio_display_configure***.</span><span class="sxs-lookup"><span data-stu-id="c99a4-202">Next, the example calls the function ***gx_studio_display_configure***.</span></span> <span data-ttu-id="c99a4-203">Esta função cria a instância de visualização GUIX, instala o idioma solicitado da tabela de cordas de aplicação, instala o tema solicitado a partir dos recursos de exibição e devolve um ponteiro à janela raiz que foi criada para este visor.</span><span class="sxs-lookup"><span data-stu-id="c99a4-203">This function creates the GUIX display instance, installs the requested language of the application string table, installs the requested theme from the display resources, and returns a pointer to the root window that has been created for this display.</span></span> <span data-ttu-id="c99a4-204">A janela raiz é usada como o pai de todos os ecrãs de nível superior que a nossa aplicação irá exibir.</span><span class="sxs-lookup"><span data-stu-id="c99a4-204">The root window is used as the parent of all top-level screens that our application will display.</span></span>

<span data-ttu-id="c99a4-205">Em seguida, o exemplo chama ***gx_studio_named_widget_create** _ para criar um exemplo do nosso ecrã _ *_hello_world*_*</span><span class="sxs-lookup"><span data-stu-id="c99a4-205">Next the example calls ***gx_studio_named_widget_create** _ to create an instance of our _ *_hello_world_** screen.</span></span> <span data-ttu-id="c99a4-206">Esta função utiliza as estruturas de dados e os recursos produzidos pelo GUIX Studio para criar uma instância do ecrã tal como o definimos.</span><span class="sxs-lookup"><span data-stu-id="c99a4-206">This function uses the data structures and resource produces by GUIX Studio to create an instance of the screen as we have defined it.</span></span> <span data-ttu-id="c99a4-207">Passamos o ponteiro da janela raiz como o segundo parâmetro para esta chamada de função, o que significa que queremos que o ecrã seja imediatamente ligado à janela da raiz.</span><span class="sxs-lookup"><span data-stu-id="c99a4-207">We pass the root window pointer as the second parameter to this function call, meaning we want the screen to be immediately attached to the root window.</span></span> <span data-ttu-id="c99a4-208">O último parâmetro é um ponteiro de retorno opcional que pode ser usado se quisermos manter um ponteiro para o ecrã criado.</span><span class="sxs-lookup"><span data-stu-id="c99a4-208">The last parameter is an optional return pointer that can be used if we want to keep a pointer to the created screen.</span></span>

<span data-ttu-id="c99a4-209">Em **seguida**\* gx_widget_show _ é chamado, o que torna visível a janela da raiz e todas as suas crianças, incluindo o ecrã _ *_hello_world_*\* .</span><span class="sxs-lookup"><span data-stu-id="c99a4-209">Next ***gx_widget_show** _ is called, which makes the root window and all of its children, including the _ *_hello_world_** screen, visible.</span></span>

<span data-ttu-id="c99a4-210">Finalmente, o exemplo chama ***gx_system_start***.</span><span class="sxs-lookup"><span data-stu-id="c99a4-210">Finally, the example calls ***gx_system_start***.</span></span> <span data-ttu-id="c99a4-211">Esta função começa a executar o circuito de processamento de eventos do sistema GUIX.</span><span class="sxs-lookup"><span data-stu-id="c99a4-211">This function begins executing the GUIX system event processing loop.</span></span>

## <a name="build-and-run-the-example"></a><span data-ttu-id="c99a4-212">Construir e Executar o Exemplo</span><span class="sxs-lookup"><span data-stu-id="c99a4-212">Build and Run the Example</span></span>

<span data-ttu-id="c99a4-213">Construir e executar o exemplo é específico para as suas ferramentas de construção e ambiente.</span><span class="sxs-lookup"><span data-stu-id="c99a4-213">Building and running the example is specific to your build tools and environment.</span></span> <span data-ttu-id="c99a4-214">No entanto, podemos definir o processo geral:</span><span class="sxs-lookup"><span data-stu-id="c99a4-214">However we can define the general process:</span></span>

1. <span data-ttu-id="c99a4-215">Criar um novo diretório e projeto de candidatura</span><span class="sxs-lookup"><span data-stu-id="c99a4-215">Create a new directory and application project</span></span>
1. <span data-ttu-id="c99a4-216">Adicione estes ficheiros ao projeto:</span><span class="sxs-lookup"><span data-stu-id="c99a4-216">Add these files to the project:</span></span>

    <span data-ttu-id="c99a4-217">**new_example_resources.c**</span><span class="sxs-lookup"><span data-stu-id="c99a4-217">**new_example_resources.c**</span></span>

    <span data-ttu-id="c99a4-218">**new_example_specification.c**</span><span class="sxs-lookup"><span data-stu-id="c99a4-218">**new_example_specification.c**</span></span>

    <span data-ttu-id="c99a4-219">**new_example.c**</span><span class="sxs-lookup"><span data-stu-id="c99a4-219">**new_example.c**</span></span>

1. <span data-ttu-id="c99a4-220">Adicione os ficheiros de suporte ao tempo de execução Win32 do caminho de instalação do GUIX Studio ***./win32_runtime***.</span><span class="sxs-lookup"><span data-stu-id="c99a4-220">Add the Win32 run-time support files from the GUIX Studio installation path ***./win32_runtime***.</span></span> <span data-ttu-id="c99a4-221">Isto inclui o cabeçalho ThreadX e GUIX Win32 e os ficheiros da biblioteca de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c99a4-221">This includes the ThreadX and GUIX Win32 header and run-time library files.</span></span>
1. <span data-ttu-id="c99a4-222">Adicione a biblioteca GUIX Win32 ***(gx.lib)*** ao projeto</span><span class="sxs-lookup"><span data-stu-id="c99a4-222">Add the GUIX Win32 library (***gx.lib***) to the project</span></span>
1. <span data-ttu-id="c99a4-223">Adicione a biblioteca ThreadX Win32 ***(tx.lib)*** ao projeto</span><span class="sxs-lookup"><span data-stu-id="c99a4-223">Add the ThreadX Win32 library (***tx.lib***) to the project</span></span>
1. <span data-ttu-id="c99a4-224">Compilar, Ligar e Executar a aplicação!</span><span class="sxs-lookup"><span data-stu-id="c99a4-224">Compile, Link, and Run the application!</span></span>
