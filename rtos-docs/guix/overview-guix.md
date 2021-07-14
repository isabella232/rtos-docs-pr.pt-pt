---
title: Compreenda o Azure RTOS GUIX e o Azure RTOS RTOS GUIX Studio
description: O Azure RTOS GUIX é um pacote de qualidade profissional, criado para atender às necessidades dos desenvolvedores de sistemas incorporados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754935"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="65ab0-103">Visão geral do Azure RTOS GUIX e Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="65ab0-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="65ab0-104">Azure GUIX incorporado GUI é a solução GUI avançada e industrial da Microsoft projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="65ab0-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="65ab0-105">A Microsoft também fornece uma ferramenta de design de ambiente de trabalho WYSIWYG totalmente apresentada chamada Azure RTOS GUIX Studio, que permite que os desenvolvedores desenhem o seu GUI no ambiente de trabalho e gerem o código GUI ID incorporado Azure RTOS GUIX que pode ser exportado para o alvo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="65ab0-106">O Azure RTOS GUIX está totalmente integrado com o Azure RTOS ThreadX RTOS e está disponível para muitos dos mesmos processadores suportados pela Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="65ab0-107">Tudo isto combinado com uma pegada extremamente pequena, uma execução rápida e uma facilidade de utilização superior, fazem do Azure RTOS GUIX a escolha ideal para as aplicações IoT incorporadas mais exigentes que requerem uma interface de utilizador.</span><span class="sxs-lookup"><span data-stu-id="65ab0-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="65ab0-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="65ab0-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="65ab0-109">APIs poderosos</span><span class="sxs-lookup"><span data-stu-id="65ab0-109">Powerful APIs</span></span>

* <span data-ttu-id="65ab0-110">Suporte total para desenho de tela direta quando necessário</span><span class="sxs-lookup"><span data-stu-id="65ab0-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="65ab0-111">Simples de interagir com O Azure RTOS GUIX Studio gerou código</span><span class="sxs-lookup"><span data-stu-id="65ab0-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="65ab0-112">APIs para linha, retângulo, polígono, etc.</span><span class="sxs-lookup"><span data-stu-id="65ab0-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="65ab0-113">APIs para círculo, arco, torta, acorde, elipse, etc.</span><span class="sxs-lookup"><span data-stu-id="65ab0-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="65ab0-114">APIs para desenho de texto e posicionamento</span><span class="sxs-lookup"><span data-stu-id="65ab0-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="65ab0-115">Anti-aliasing, preenchimentos de textura e enchimentos sólidos</span><span class="sxs-lookup"><span data-stu-id="65ab0-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="65ab0-116">APIs para criar e modificar ecrãs e widgets</span><span class="sxs-lookup"><span data-stu-id="65ab0-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="65ab0-117">Arquivos gerados pelo estúdio Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="65ab0-118">Ficheiros de origem ANSI C gerados automaticamente</span><span class="sxs-lookup"><span data-stu-id="65ab0-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="65ab0-119">Isola o software de aplicação a partir de detalhes do layout</span><span class="sxs-lookup"><span data-stu-id="65ab0-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="65ab0-120">Inclui fontes e imagens necessárias pelo design da UI</span><span class="sxs-lookup"><span data-stu-id="65ab0-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="65ab0-121">Ficheiros gerados compilados com código de aplicação</span><span class="sxs-lookup"><span data-stu-id="65ab0-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="65ab0-122">O layout do ecrã pode ser atualizado sem afetar a lógica da aplicação</span><span class="sxs-lookup"><span data-stu-id="65ab0-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="65ab0-123">IDs de recursos criam independência linguística e temática</span><span class="sxs-lookup"><span data-stu-id="65ab0-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="65ab0-124">Funções de desenho personalizado e processamento de eventos fornecidas pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="65ab0-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="65ab0-125">Biblioteca Widget</span><span class="sxs-lookup"><span data-stu-id="65ab0-125">Widget library</span></span>

* <span data-ttu-id="65ab0-126">Conjunto pré-definido mas personalizável de elementos de interface comuns</span><span class="sxs-lookup"><span data-stu-id="65ab0-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="65ab0-127">Extremamente pequeno, compacto e eficiente</span><span class="sxs-lookup"><span data-stu-id="65ab0-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="65ab0-128">Biblioteca inclui botão, bitola, lista, janela, pergaminho, slider, barra de progresso, prompt e muito mais</span><span class="sxs-lookup"><span data-stu-id="65ab0-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="65ab0-129">Desenho e aparência totalmente personalizáveis</span><span class="sxs-lookup"><span data-stu-id="65ab0-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="65ab0-130">Funcionamento totalmente personalizável e tratamento de eventos</span><span class="sxs-lookup"><span data-stu-id="65ab0-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="65ab0-131">Apenas os widgets utilizados estão ligados ao software de aplicações</span><span class="sxs-lookup"><span data-stu-id="65ab0-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="65ab0-132">Matemática e utilidades</span><span class="sxs-lookup"><span data-stu-id="65ab0-132">Math and utilities</span></span>

* <span data-ttu-id="65ab0-133">Funções para o pecado, cos, arcsin, arccos, tangente, raiz quadrada</span><span class="sxs-lookup"><span data-stu-id="65ab0-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="65ab0-134">Funções para manipular regiões de tela</span><span class="sxs-lookup"><span data-stu-id="65ab0-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="65ab0-135">Configuração e arranque do sistema</span><span class="sxs-lookup"><span data-stu-id="65ab0-135">System configuration and startup</span></span>
* <span data-ttu-id="65ab0-136">Definição de piscina de memória (opcional)</span><span class="sxs-lookup"><span data-stu-id="65ab0-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="65ab0-137">Gestão do Temporizador</span><span class="sxs-lookup"><span data-stu-id="65ab0-137">Timer Management</span></span>
* <span data-ttu-id="65ab0-138">Gestão de Animação</span><span class="sxs-lookup"><span data-stu-id="65ab0-138">Animation Management</span></span>
* <span data-ttu-id="65ab0-139">Manutenção de listas sujas</span><span class="sxs-lookup"><span data-stu-id="65ab0-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="65ab0-140">Processamento de imagens</span><span class="sxs-lookup"><span data-stu-id="65ab0-140">Image processing</span></span>

* <span data-ttu-id="65ab0-141">Funções para descodificar tempo de execução de imagens jpeg e png</span><span class="sxs-lookup"><span data-stu-id="65ab0-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="65ab0-142">Aplicar dilatação e conversão de espaço de cor</span><span class="sxs-lookup"><span data-stu-id="65ab0-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="65ab0-143">Rotação de imagem</span><span class="sxs-lookup"><span data-stu-id="65ab0-143">Image rotation</span></span>
* <span data-ttu-id="65ab0-144">Dimensionamento de imagem</span><span class="sxs-lookup"><span data-stu-id="65ab0-144">Image scaling</span></span>
* <span data-ttu-id="65ab0-145">Mistura de imagem</span><span class="sxs-lookup"><span data-stu-id="65ab0-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="65ab0-146">Processamento de eventos</span><span class="sxs-lookup"><span data-stu-id="65ab0-146">Event processing</span></span>

* <span data-ttu-id="65ab0-147">Suspende automaticamente o fio Azure RTOS GUIX quando está inativo</span><span class="sxs-lookup"><span data-stu-id="65ab0-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="65ab0-148">Modelo de programação orientado por eventos popular em design de UI</span><span class="sxs-lookup"><span data-stu-id="65ab0-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="65ab0-149">Isola os condutores de entrada do fio de desenho Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="65ab0-150">Funções para envio e receção de eventos</span><span class="sxs-lookup"><span data-stu-id="65ab0-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="65ab0-151">Tipos de eventos pré-definidos para todos os tipos de widgetS Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="65ab0-152">Eventos personalizados definidos pelo utilizador suportados</span><span class="sxs-lookup"><span data-stu-id="65ab0-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="65ab0-153">Processamento de lona</span><span class="sxs-lookup"><span data-stu-id="65ab0-153">Canvas processing</span></span>

* <span data-ttu-id="65ab0-154">Manutenção de clipping e Z-Order</span><span class="sxs-lookup"><span data-stu-id="65ab0-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="65ab0-155">Isola a biblioteca widget a partir de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="65ab0-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="65ab0-156">Isola a aplicação a partir de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="65ab0-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="65ab0-157">Renovação automática de fundo de áreas sujas</span><span class="sxs-lookup"><span data-stu-id="65ab0-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="65ab0-158">Múltiplas telas com camadas e mistura suportadas</span><span class="sxs-lookup"><span data-stu-id="65ab0-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="65ab0-159">Pode ser invocado diretamente pelo software de aplicação</span><span class="sxs-lookup"><span data-stu-id="65ab0-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="65ab0-160">Controlador de dispositivos de entrada</span><span class="sxs-lookup"><span data-stu-id="65ab0-160">Input device driver(s)</span></span>

* <span data-ttu-id="65ab0-161">Suporte específico para hardware, Azure RTOS GUIX e aplicação isolada de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="65ab0-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="65ab0-162">Toque resistivo, toque de boné e teclado suportado</span><span class="sxs-lookup"><span data-stu-id="65ab0-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="65ab0-163">Eventos de entrada passados para a fila de eventos Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="65ab0-164">Controladores de exibição</span><span class="sxs-lookup"><span data-stu-id="65ab0-164">Display drivers</span></span>

* <span data-ttu-id="65ab0-165">Suporte específico para hardware</span><span class="sxs-lookup"><span data-stu-id="65ab0-165">Hardware-specific support</span></span>
* <span data-ttu-id="65ab0-166">Condutores genéricos fornecidos para toda a profundidade e formatos de cor</span><span class="sxs-lookup"><span data-stu-id="65ab0-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="65ab0-167">Personalizado para utilizar aceleradores gráficos disponíveis</span><span class="sxs-lookup"><span data-stu-id="65ab0-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="65ab0-168">Hardware-alvo</span><span class="sxs-lookup"><span data-stu-id="65ab0-168">Target hardware</span></span>

* <span data-ttu-id="65ab0-169">Quase todo o hardware capaz de saída gráfica é compatível com GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="65ab0-170">Múltiplas exibições físicas suportadas</span><span class="sxs-lookup"><span data-stu-id="65ab0-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="65ab0-171">Requisitos mínimos de RAM e Flash</span><span class="sxs-lookup"><span data-stu-id="65ab0-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="65ab0-172">Criar interfaces de utilizador elegantes</span><span class="sxs-lookup"><span data-stu-id="65ab0-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="65ab0-173">Azure RTOS GUIX e Azure RTOS GUIX Studio fornecem todas as funcionalidades necessárias para criar interfaces de utilizador exclusivamente elegantes.</span><span class="sxs-lookup"><span data-stu-id="65ab0-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="65ab0-174">O pacote padrão Azure RTOS GUIX inclui várias interfaces de utilizador de amostras, incluindo uma referência de dispositivo médico, uma referência de relógio inteligente, uma referência de domótica, uma referência de controlo industrial, uma referência automóvel, e vários exemplos de sprite e animação.</span><span class="sxs-lookup"><span data-stu-id="65ab0-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="65ab0-175">Clique nos exemplos de referência apresentados abaixo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="65ab0-176">Domótica</span><span class="sxs-lookup"><span data-stu-id="65ab0-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="65ab0-177">Médico</span><span class="sxs-lookup"><span data-stu-id="65ab0-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="65ab0-178">Consumidor</span><span class="sxs-lookup"><span data-stu-id="65ab0-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="65ab0-179">Bens Brancos</span><span class="sxs-lookup"><span data-stu-id="65ab0-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="65ab0-180">Automóvel</span><span class="sxs-lookup"><span data-stu-id="65ab0-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="65ab0-181">Industrial</span><span class="sxs-lookup"><span data-stu-id="65ab0-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="65ab0-182">Cada referência Azure RTOS GUIX tem um projeto correspondente do Azure RTOS GUIX Studio que define todos os elementos gráficos do design de referência.</span><span class="sxs-lookup"><span data-stu-id="65ab0-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="65ab0-183">Mudar um design de referência é fácil.</span><span class="sxs-lookup"><span data-stu-id="65ab0-183">Changing a reference design is easy.</span></span> <span data-ttu-id="65ab0-184">Basta abrir o projeto Azure RTOS GUIX correspondente, fazer as alterações desejadas, salvar o projeto e, em seguida, selecionar *Project*.</span><span class="sxs-lookup"><span data-stu-id="65ab0-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="65ab0-185">Gere todos os ficheiros de saída para gerar o código C para Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="65ab0-186">Em seguida, basta reconstruir a aplicação-alvo e correr para observar o design de referência modificado.</span><span class="sxs-lookup"><span data-stu-id="65ab0-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="guix-memory-footprint"></a><span data-ttu-id="65ab0-187">Pegada de memória GUIX</span><span class="sxs-lookup"><span data-stu-id="65ab0-187">GUIX Memory footprint</span></span>

<span data-ttu-id="65ab0-188">O Azure RTOS GUIX tem uma pegada mínima notável de 13.2KB de FLASH e 4KB RAM para suporte básico, sem incluir a memória necessária para uma tela.</span><span class="sxs-lookup"><span data-stu-id="65ab0-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="65ab0-189">Para um visor com gram interno e tecnologia de auto-atualização, não é necessária memória de lona.</span><span class="sxs-lookup"><span data-stu-id="65ab0-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="65ab0-190">No entanto, para melhorar o desempenho do desenho, ou para uma configuração do visor que não utilize o GRAM local para o visor, uma área de memória de tela é definida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="65ab0-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="65ab0-191">Os requisitos de memória de lona são uma função do tamanho da tela, bem como da profundidade de cor, e são definidos pela fórmula:</span><span class="sxs-lookup"><span data-stu-id="65ab0-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="65ab0-192"><i>RAM de lona (bytes) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="65ab0-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="65ab0-193">Onde "x" e "y" são as dimensões da tela (display).</span><span class="sxs-lookup"><span data-stu-id="65ab0-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="65ab0-194">A maioria das aplicações também utiliza recursos gráficos, que não estão incluídos nos requisitos de armazenamento da biblioteca Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="65ab0-195">Estes recursos incluem fontes, ícones gráficos (pixelmaps) e cordas estáticas.</span><span class="sxs-lookup"><span data-stu-id="65ab0-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="65ab0-196">Estes dados podem ser armazenados na secção de memória const (ou seja, FLASH).</span><span class="sxs-lookup"><span data-stu-id="65ab0-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="65ab0-197">O tamanho desta área de memória depende de uma série de fatores, incluindo o número e o tamanho de fontes únicas utilizadas, o número e o tamanho dos ícones gráficos utilizados, o formato de cor de saída, e se cada recurso está ou não a usar dados comprimidos, uma vez que o Azure RTOS GUIX suporta a compressão RLE tanto dos dados de fonte como de pixelmap.</span><span class="sxs-lookup"><span data-stu-id="65ab0-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="65ab0-198">Os requisitos de armazenamento de cada recurso são apresentados dentro da aplicação Azure RTOS GUIX Studio, permitindo ao utilizador rastrear e monitorizar a quantidade de memória flash que será consumida pelos recursos da aplicação.</span><span class="sxs-lookup"><span data-stu-id="65ab0-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="65ab0-199">Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS GUIX escala automaticamente com base nos serviços realmente utilizados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="65ab0-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="65ab0-200">Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="65ab0-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="65ab0-201">Simples e fácil de usar</span><span class="sxs-lookup"><span data-stu-id="65ab0-201">Simple, easy-to-use</span></span>

<span data-ttu-id="65ab0-202">O Azure RTOS GUIX é muito simples de usar e o Azure RTOS GUIX Studio torna ainda mais fácil, permitindo que os desenvolvedores desenhem visualmente no ambiente de trabalho e gerem código C que funciona no alvo real.</span><span class="sxs-lookup"><span data-stu-id="65ab0-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="65ab0-203">As aplicações podem então adicionar as suas próprias funções personalizadas de manuseamento e desenho de eventos para completar o seu GUI.</span><span class="sxs-lookup"><span data-stu-id="65ab0-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="65ab0-204">A utilização da API AZURE RTOS GUIX é simples.</span><span class="sxs-lookup"><span data-stu-id="65ab0-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="65ab0-205">A Azure RTOS GUIX API é simultaneamente intuitiva e altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="65ab0-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="65ab0-206">Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" e/ou dos nomes altamente abreviados que são tão comuns em outros produtos do sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="65ab0-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="65ab0-207">Todas as APIs Azure RTOS GUIX têm uma *gx_* líder e seguem uma convenção de nomeação de substantivos.</span><span class="sxs-lookup"><span data-stu-id="65ab0-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="65ab0-208">Além disso, existe uma consistência funcional em toda a API.</span><span class="sxs-lookup"><span data-stu-id="65ab0-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="65ab0-209">Por exemplo, todas as APIs que inicializam um bloco de controlo widget são &lt; nomeadas widget_type &gt; _create, e os parâmetros de função de criação para cada tipo de widget são sempre definidos na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="65ab0-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="65ab0-210">Conjunto abrangente de widgets incorporados</span><span class="sxs-lookup"><span data-stu-id="65ab0-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="65ab0-211">Azure RTOS GUIX fornece um rico conjunto de widgets incorporados, incluindo:</span><span class="sxs-lookup"><span data-stu-id="65ab0-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="65ab0-212">Menu de Acordeão</span><span class="sxs-lookup"><span data-stu-id="65ab0-212">Accordion Menu</span></span>
* <span data-ttu-id="65ab0-213">Botão</span><span class="sxs-lookup"><span data-stu-id="65ab0-213">Button</span></span>
* <span data-ttu-id="65ab0-214">Caixa de verificação</span><span class="sxs-lookup"><span data-stu-id="65ab0-214">Checkbox</span></span>
* <span data-ttu-id="65ab0-215">Bitola Circular</span><span class="sxs-lookup"><span data-stu-id="65ab0-215">Circular Gauge</span></span>
* <span data-ttu-id="65ab0-216">Lista de drop down</span><span class="sxs-lookup"><span data-stu-id="65ab0-216">Drop Down List</span></span>
* <span data-ttu-id="65ab0-217">Lista Horizontal</span><span class="sxs-lookup"><span data-stu-id="65ab0-217">Horizontal List</span></span>
* <span data-ttu-id="65ab0-218">Janela horizontal do travessa</span><span class="sxs-lookup"><span data-stu-id="65ab0-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="65ab0-219">Ícone</span><span class="sxs-lookup"><span data-stu-id="65ab0-219">Icon</span></span>
* <span data-ttu-id="65ab0-220">Botão de ícone</span><span class="sxs-lookup"><span data-stu-id="65ab0-220">Icon Button</span></span>
* <span data-ttu-id="65ab0-221">Gráfico de linha</span><span class="sxs-lookup"><span data-stu-id="65ab0-221">Line Chart</span></span>
* <span data-ttu-id="65ab0-222">Menu</span><span class="sxs-lookup"><span data-stu-id="65ab0-222">Menu</span></span>
* <span data-ttu-id="65ab0-223">Botão de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="65ab0-223">Multi Line Text Button</span></span>
* <span data-ttu-id="65ab0-224">Entrada de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="65ab0-224">Multi Line Text Input</span></span>
* <span data-ttu-id="65ab0-225">Vista de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="65ab0-225">Multi Line Text View</span></span>
* <span data-ttu-id="65ab0-226">Solicitação pixelmap numérica</span><span class="sxs-lookup"><span data-stu-id="65ab0-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="65ab0-227">Solicitação numérica</span><span class="sxs-lookup"><span data-stu-id="65ab0-227">Numeric Prompt</span></span>
* <span data-ttu-id="65ab0-228">Roda de pergaminho numérica</span><span class="sxs-lookup"><span data-stu-id="65ab0-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="65ab0-229">Botão Pixelmap</span><span class="sxs-lookup"><span data-stu-id="65ab0-229">Pixelmap Button</span></span>
* <span data-ttu-id="65ab0-230">Pixelmap Prompt</span><span class="sxs-lookup"><span data-stu-id="65ab0-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="65ab0-231">Pixelmap Slider</span><span class="sxs-lookup"><span data-stu-id="65ab0-231">Pixelmap Slider</span></span>
* <span data-ttu-id="65ab0-232">Pixelmap Sprite</span><span class="sxs-lookup"><span data-stu-id="65ab0-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="65ab0-233">Barra de Progresso</span><span class="sxs-lookup"><span data-stu-id="65ab0-233">Progress Bar</span></span>
* <span data-ttu-id="65ab0-234">Prompt</span><span class="sxs-lookup"><span data-stu-id="65ab0-234">Prompt</span></span>
* <span data-ttu-id="65ab0-235">Barra de Progresso Radial</span><span class="sxs-lookup"><span data-stu-id="65ab0-235">Radial Progress Bar</span></span>
* <span data-ttu-id="65ab0-236">Botão de rádio</span><span class="sxs-lookup"><span data-stu-id="65ab0-236">Radio Button</span></span>
* <span data-ttu-id="65ab0-237">Roda de pergaminho</span><span class="sxs-lookup"><span data-stu-id="65ab0-237">Scroll Wheel</span></span>
* <span data-ttu-id="65ab0-238">Entrada de texto de linha única</span><span class="sxs-lookup"><span data-stu-id="65ab0-238">Single Line Text Input</span></span>
* <span data-ttu-id="65ab0-239">Slider</span><span class="sxs-lookup"><span data-stu-id="65ab0-239">Slider</span></span>
* <span data-ttu-id="65ab0-240">Roda de pergaminho de corda</span><span class="sxs-lookup"><span data-stu-id="65ab0-240">String Scroll Wheel</span></span>
* <span data-ttu-id="65ab0-241">Botão de texto</span><span class="sxs-lookup"><span data-stu-id="65ab0-241">Text Button</span></span>
* <span data-ttu-id="65ab0-242">Vista de Árvore</span><span class="sxs-lookup"><span data-stu-id="65ab0-242">Tree View</span></span>
* <span data-ttu-id="65ab0-243">Lista Vertical</span><span class="sxs-lookup"><span data-stu-id="65ab0-243">Vertical List</span></span>
* <span data-ttu-id="65ab0-244">Barra de pergaminho vertical</span><span class="sxs-lookup"><span data-stu-id="65ab0-244">Vertical Scrollbar</span></span>

<span data-ttu-id="65ab0-245">É fácil para a aplicação criar os seus próprios widgets de cliente também.</span><span class="sxs-lookup"><span data-stu-id="65ab0-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="65ab0-246">API de desenho de baixo nível completo</span><span class="sxs-lookup"><span data-stu-id="65ab0-246">Complete low-level drawing API</span></span>

<span data-ttu-id="65ab0-247">O Azure RTOS GUIX fornece uma API de desenho de tela robusta, permitindo que a aplicação torne formas gráficas complexas.</span><span class="sxs-lookup"><span data-stu-id="65ab0-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="65ab0-248">Todas as funções suportam anti-aliasing em alvos de alta profundidade de cores, e todas as formas podem ser preenchidas o nosso delineado, incluindo preenchimentos sólidos e pixelmap padrão.</span><span class="sxs-lookup"><span data-stu-id="65ab0-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="65ab0-249">Todos os primitivos de desenho suportam a escova alfa quando correm a 16 bpp e a profundidade de cor mais alta.</span><span class="sxs-lookup"><span data-stu-id="65ab0-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="65ab0-250">As funções de desenho incluem:</span><span class="sxs-lookup"><span data-stu-id="65ab0-250">Drawing functions include:</span></span>

* <span data-ttu-id="65ab0-251">Desenho de arco</span><span class="sxs-lookup"><span data-stu-id="65ab0-251">Arc Draw</span></span>
* <span data-ttu-id="65ab0-252">Desenho de círculo</span><span class="sxs-lookup"><span data-stu-id="65ab0-252">Circle Draw</span></span>
* <span data-ttu-id="65ab0-253">Desenho de linha</span><span class="sxs-lookup"><span data-stu-id="65ab0-253">Line Draw</span></span>
* <span data-ttu-id="65ab0-254">Sorteio de Tortas</span><span class="sxs-lookup"><span data-stu-id="65ab0-254">Pie Draw</span></span>
* <span data-ttu-id="65ab0-255">Mistura pixelmap</span><span class="sxs-lookup"><span data-stu-id="65ab0-255">Pixelmap Blend</span></span>
* <span data-ttu-id="65ab0-256">Azulejo pixelmap</span><span class="sxs-lookup"><span data-stu-id="65ab0-256">Pixelmap Tile</span></span>
* <span data-ttu-id="65ab0-257">Desenho de Polígono</span><span class="sxs-lookup"><span data-stu-id="65ab0-257">Polygon Draw</span></span>
* <span data-ttu-id="65ab0-258">Desenho de texto</span><span class="sxs-lookup"><span data-stu-id="65ab0-258">Text Draw</span></span>
* <span data-ttu-id="65ab0-259">Desenho de acordes</span><span class="sxs-lookup"><span data-stu-id="65ab0-259">Chord Draw</span></span>
* <span data-ttu-id="65ab0-260">Desenho elipse</span><span class="sxs-lookup"><span data-stu-id="65ab0-260">Ellipse Draw</span></span>
* <span data-ttu-id="65ab0-261">Desenho de pixels</span><span class="sxs-lookup"><span data-stu-id="65ab0-261">Pixel Draw</span></span>
* <span data-ttu-id="65ab0-262">Pixelmap Draw</span><span class="sxs-lookup"><span data-stu-id="65ab0-262">Pixelmap Draw</span></span>
* <span data-ttu-id="65ab0-263">Rotação pixelmap</span><span class="sxs-lookup"><span data-stu-id="65ab0-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="65ab0-264">Desenho de retângulo</span><span class="sxs-lookup"><span data-stu-id="65ab0-264">Rectangle Draw</span></span>
* <span data-ttu-id="65ab0-265">Mistura de texto</span><span class="sxs-lookup"><span data-stu-id="65ab0-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="65ab0-266">Fontes gratuitas padrão e fácil de adicionar mais</span><span class="sxs-lookup"><span data-stu-id="65ab0-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="65ab0-267">Azure RTOS GUIX fornece um conjunto gratuito de fontes TrueType.</span><span class="sxs-lookup"><span data-stu-id="65ab0-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="65ab0-268">Os desenvolvedores podem adicionar fontes TrueType adicionais conforme desejado.</span><span class="sxs-lookup"><span data-stu-id="65ab0-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="65ab0-269">O formato de fonte Azure RTOS GUIX suporta fontes anti-aliasing 8bpp, 4bpp anti-aliasing e 1bpp de fontes monocromáticas.</span><span class="sxs-lookup"><span data-stu-id="65ab0-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="65ab0-270">Para as aplicações mais restritas a recursos, o Azure RTOS GUIX pré-torna as fontes TrueType num formato de bitmap comprimido utilizando a nossa ferramenta de desktop GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="65ab0-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="65ab0-271">Implementação personalizada do descodificador JPG e PNG</span><span class="sxs-lookup"><span data-stu-id="65ab0-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="65ab0-272">Implementação personalizada de descodificador JPG e PNG descodificador de ficheiros JPG e PNG implementação.</span><span class="sxs-lookup"><span data-stu-id="65ab0-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="65ab0-273">Esta implementação suporta a conversão de espaço de cores, dilatação e criação de tempo de execução de imagens de formato pixelmap compatíveis com Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="65ab0-274">Extenso suporte de ecrã e ecrã tátil</span><span class="sxs-lookup"><span data-stu-id="65ab0-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="65ab0-275">Azure RTOS GUIX fornece controladores de exibição genéricos para quase todos os formatos de cores, incluindo monocromático de 1bpp, paleta de 8 bpp, formato 8 bpp 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="65ab0-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="65ab0-276">Formato 16 bpp 565 rgb, 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b e 32 bpp a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="65ab0-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="65ab0-277">Além disso, o Azure RTOS GUIX está integrado com muitos dos controladores LCD mais populares e aceleradores de hardware (ST ChromeArt, Renesas Synergy, etc.).</span><span class="sxs-lookup"><span data-stu-id="65ab0-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="65ab0-278">O Azure RTOS GUIX suporta totalmente o ecrã tátil (incluindo suporte a gestos), caneta e dispositivos de entrada de teclado virtual.</span><span class="sxs-lookup"><span data-stu-id="65ab0-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="65ab0-279">Ferramenta Azure RTOS GUIX Studio WYSIWYG</span><span class="sxs-lookup"><span data-stu-id="65ab0-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="65ab0-280">O Azure RTOS GUIX Studio fornece um ambiente completo de design de ecrã WYSIWYG que permite ao utilizador arrastar e largar elementos gráficos usados para construir os ecrãs GUI.</span><span class="sxs-lookup"><span data-stu-id="65ab0-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="65ab0-281">O Azure RTOS GUIX Studio gera automaticamente código C compatível com a biblioteca Azure RTOS GUIX, pronta a ser compilada e executada no alvo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="65ab0-282">Os desenvolvedores podem produzir fontes pré-renderizadas para uso dentro de uma aplicação usando a ferramenta integrada de geração de fontes Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="65ab0-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="65ab0-283">As fontes podem ser geradas em formatos monocromáticos ou anti-aliased, e são otimizadas para economizar espaço no alvo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="65ab0-284">Os tipos de letra podem incluir qualquer conjunto de caracteres, incluindo caracteres Unicode para aplicações multilingues.</span><span class="sxs-lookup"><span data-stu-id="65ab0-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="65ab0-285">O Azure RTOS GUIX Studio facilita a importação de gráficos de ficheiros PNG ou JPG com conversão para Azure RTOS GUIX Pixelmaps para utilização no sistema-alvo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="65ab0-286">Muitos dos tipos de widgetS Azure RTOS GUIX são projetados para incorporar gráficos do utilizador para uma aparência e sensação personalizadas.</span><span class="sxs-lookup"><span data-stu-id="65ab0-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="65ab0-287">Além disso, o Azure RTOS GUIX Studio permite personalizar as cores padrão e os estilos de desenho usados pelos widgets Azure RTOS GUIX, permitindo aos desenvolvedores sintonizar muito facilmente a aparência do Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="65ab0-288">Geração e manutenção de cadeias de aplicações é outra instalação incorporada do Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="65ab0-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="65ab0-289">Isto permite que os desenvolvedores desenhem uma aplicação usando uma língua para desenvolver, e de forma rápida e fácil adicionar suporte para idiomas adicionais após o lançamento do produto.</span><span class="sxs-lookup"><span data-stu-id="65ab0-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="65ab0-290">Uma aplicação completa do Azure RTOS GUIX pode ser executada num ambiente de pc dentro do ambiente Azure RTOS GUIX Studio, permitindo uma geração rápida e fácil e demonstração de conceitos GUI, testes de fluxos de ecrã e observação de transições de ecrã e animações.</span><span class="sxs-lookup"><span data-stu-id="65ab0-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="65ab0-291">Quando concluído, um design pode ser exportado como estruturas de dados C prontas para o alvo, prontas a ser compiladas e ligadas às bibliotecas Azure RTOS GUIX e Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="65ab0-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="65ab0-292">Azure RTOS GUIX e Azure RTOS GUIX Studio suportam vários temas de recursos, permitindo que uma aplicação seja facilmente ressarsado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="65ab0-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="65ab0-293">Fontes, cores e pixelmaps podem ser alterados no tempo de execução com uma simples API.</span><span class="sxs-lookup"><span data-stu-id="65ab0-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="65ab0-294">Saiba mais sobre o GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="65ab0-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="65ab0-295">Simulação completa do Win32</span><span class="sxs-lookup"><span data-stu-id="65ab0-295">Complete Win32 simulation</span></span>

<span data-ttu-id="65ab0-296">O Azure RTOS GUIX funciona num PC Windows, utilizando exatamente a mesma biblioteca de desenho que funciona no quadro-alvo.</span><span class="sxs-lookup"><span data-stu-id="65ab0-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="65ab0-297">Com o Azure RTOS GUIX, pode construir e executar uma aplicação GUI no PC, e usar o mesmo código de aplicação no seu alvo para depuração rápida, prototipagem rápida, demonstração e operação alvo WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="65ab0-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="65ab0-298">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="65ab0-298">Advanced technology</span></span>

* <span data-ttu-id="65ab0-299">A tecnologia avançada da Azure RTOS GUIX incorpora:</span><span class="sxs-lookup"><span data-stu-id="65ab0-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="65ab0-300">Mistura alfa</span><span class="sxs-lookup"><span data-stu-id="65ab0-300">Alpha blending</span></span>
* <span data-ttu-id="65ab0-301">Anti-Aliasing</span><span class="sxs-lookup"><span data-stu-id="65ab0-301">Anti-Aliasing</span></span>
* <span data-ttu-id="65ab0-302">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="65ab0-302">Automatic scaling</span></span>
* <span data-ttu-id="65ab0-303">Compressão bitmap</span><span class="sxs-lookup"><span data-stu-id="65ab0-303">Bitmap compression</span></span>
* <span data-ttu-id="65ab0-304">Mistura de lona</span><span class="sxs-lookup"><span data-stu-id="65ab0-304">Canvas blending</span></span>
* <span data-ttu-id="65ab0-305">Suporte widget personalizado</span><span class="sxs-lookup"><span data-stu-id="65ab0-305">Custom widget support</span></span>
* <span data-ttu-id="65ab0-306">Suporte de desenho diferido</span><span class="sxs-lookup"><span data-stu-id="65ab0-306">Deferred drawing support</span></span>
* <span data-ttu-id="65ab0-307">Apoio dithering</span><span class="sxs-lookup"><span data-stu-id="65ab0-307">Dithering support</span></span>
* <span data-ttu-id="65ab0-308">Programação neutra endiana</span><span class="sxs-lookup"><span data-stu-id="65ab0-308">Endian neutral programming</span></span>
* <span data-ttu-id="65ab0-309">Suporte ao acelerador de hardware</span><span class="sxs-lookup"><span data-stu-id="65ab0-309">Hardware accelerator support</span></span>
* <span data-ttu-id="65ab0-310">Suporte multilinguístico e codificação UTF-8</span><span class="sxs-lookup"><span data-stu-id="65ab0-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="65ab0-311">Suporte de exibição e lona múltipla</span><span class="sxs-lookup"><span data-stu-id="65ab0-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="65ab0-312">Recortes otimizados, desenho e manipulação de eventos</span><span class="sxs-lookup"><span data-stu-id="65ab0-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="65ab0-313">Descodificador JPEG e PNG</span><span class="sxs-lookup"><span data-stu-id="65ab0-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="65ab0-314">Esfolar e Temas</span><span class="sxs-lookup"><span data-stu-id="65ab0-314">Skinning and Themes</span></span>
* <span data-ttu-id="65ab0-315">Suporta monocromático através de 32 bits de cor verdadeira com formatos gráficos alfa</span><span class="sxs-lookup"><span data-stu-id="65ab0-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="65ab0-316">Transições, Sprites e Suporte de Animação</span><span class="sxs-lookup"><span data-stu-id="65ab0-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="65ab0-317">Simulação Win32</span><span class="sxs-lookup"><span data-stu-id="65ab0-317">Win32 simulation</span></span>
* <span data-ttu-id="65ab0-318">Gestão de janelas, incluindo Viewports e manutenção de ordem Z</span><span class="sxs-lookup"><span data-stu-id="65ab0-318">Window management including Viewports and Z-order maintenance</span></span>
