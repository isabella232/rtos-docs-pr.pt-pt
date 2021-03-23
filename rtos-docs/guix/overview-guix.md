---
title: Compreenda o Azure RTOS GUIX e o Azure RTOS RTOS GUIX Studio
description: O Azure RTOS GUIX é um pacote de qualidade profissional, criado para atender às necessidades dos desenvolvedores de sistemas incorporados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827092"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="ee9bf-103">Visão geral do Azure RTOS GUIX e Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="ee9bf-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="ee9bf-104">Azure GUIX incorporado GUI é a solução GUI avançada e industrial da Microsoft projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="ee9bf-105">A Microsoft também fornece uma ferramenta de design de ambiente de trabalho WYSIWYG totalmente apresentada chamada Azure RTOS GUIX Studio, que permite que os desenvolvedores desenhem o seu GUI no ambiente de trabalho e gerem o código GUI ID incorporado Azure RTOS GUIX que pode ser exportado para o alvo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="ee9bf-106">O Azure RTOS GUIX está totalmente integrado com o Azure RTOS ThreadX RTOS e está disponível para muitos dos mesmos processadores suportados pela Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="ee9bf-107">Tudo isto combinado com uma pegada extremamente pequena, uma execução rápida e uma facilidade de utilização superior, fazem do Azure RTOS GUIX a escolha ideal para as aplicações IoT incorporadas mais exigentes que requerem uma interface de utilizador.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="ee9bf-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="ee9bf-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="ee9bf-109">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="ee9bf-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="ee9bf-110">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="ee9bf-111">Todas as APIs têm *gx_* a identificar facilmente como Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="ee9bf-112">Modelo de programação orientado para eventos (API)</span><span class="sxs-lookup"><span data-stu-id="ee9bf-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="ee9bf-113">Suporte total para desenho de tela direta quando necessário</span><span class="sxs-lookup"><span data-stu-id="ee9bf-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="ee9bf-114">Simples de interagir com O Azure RTOS GUIX Studio gerou código</span><span class="sxs-lookup"><span data-stu-id="ee9bf-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="ee9bf-115">APIs para linha, retângulo, polígono, etc.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="ee9bf-116">APIs para círculo, arco, torta, acorde, elipse, etc.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="ee9bf-117">APIs para desenho de texto e posicionamento</span><span class="sxs-lookup"><span data-stu-id="ee9bf-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="ee9bf-118">Anti-aliasing, preenchimentos de textura e enchimentos sólidos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="ee9bf-119">APIs para criar e modificar ecrãs e widgets</span><span class="sxs-lookup"><span data-stu-id="ee9bf-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="ee9bf-120">Arquivos gerados pelo estúdio Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="ee9bf-121">Ficheiros de origem ANSI C gerados automaticamente</span><span class="sxs-lookup"><span data-stu-id="ee9bf-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="ee9bf-122">Isola o software de aplicação a partir de detalhes do layout</span><span class="sxs-lookup"><span data-stu-id="ee9bf-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="ee9bf-123">Inclui fontes e imagens necessárias pelo design da UI</span><span class="sxs-lookup"><span data-stu-id="ee9bf-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="ee9bf-124">Ficheiros gerados compilados com código de aplicação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="ee9bf-125">O layout do ecrã pode ser atualizado sem afetar a lógica da aplicação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="ee9bf-126">IDs de recursos criam independência linguística e temática</span><span class="sxs-lookup"><span data-stu-id="ee9bf-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="ee9bf-127">Funções de desenho personalizado e processamento de eventos fornecidas pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="ee9bf-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="ee9bf-128">Biblioteca Widget</span><span class="sxs-lookup"><span data-stu-id="ee9bf-128">Widget library</span></span>

* <span data-ttu-id="ee9bf-129">Conjunto pré-definido mas personalizável de elementos de interface comuns</span><span class="sxs-lookup"><span data-stu-id="ee9bf-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="ee9bf-130">Extremamente pequeno, compacto e eficiente</span><span class="sxs-lookup"><span data-stu-id="ee9bf-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="ee9bf-131">Biblioteca inclui botão, bitola, lista, janela, pergaminho, slider, barra de progresso, prompt e muito mais</span><span class="sxs-lookup"><span data-stu-id="ee9bf-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="ee9bf-132">Desenho e aparência totalmente personalizáveis</span><span class="sxs-lookup"><span data-stu-id="ee9bf-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="ee9bf-133">Funcionamento totalmente personalizável e tratamento de eventos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="ee9bf-134">Apenas os widgets utilizados estão ligados ao software de aplicações</span><span class="sxs-lookup"><span data-stu-id="ee9bf-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="ee9bf-135">Matemática e utilidades</span><span class="sxs-lookup"><span data-stu-id="ee9bf-135">Math and utilities</span></span>

* <span data-ttu-id="ee9bf-136">Funções para o pecado, cos, arcsin, arccos, tangente, raiz quadrada</span><span class="sxs-lookup"><span data-stu-id="ee9bf-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="ee9bf-137">Funções para manipular regiões de tela</span><span class="sxs-lookup"><span data-stu-id="ee9bf-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="ee9bf-138">Configuração e arranque do sistema</span><span class="sxs-lookup"><span data-stu-id="ee9bf-138">System configuration and startup</span></span>

* <span data-ttu-id="ee9bf-139">Definição de piscina de memória (opcional)</span><span class="sxs-lookup"><span data-stu-id="ee9bf-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="ee9bf-140">Gestão do Temporizador</span><span class="sxs-lookup"><span data-stu-id="ee9bf-140">Timer Management</span></span>

* <span data-ttu-id="ee9bf-141">Gestão de Animação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-141">Animation Management</span></span>

* <span data-ttu-id="ee9bf-142">Manutenção de listas sujas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="ee9bf-143">Processamento de imagens</span><span class="sxs-lookup"><span data-stu-id="ee9bf-143">Image processing</span></span>

* <span data-ttu-id="ee9bf-144">Funções para descodificar tempo de execução de imagens jpeg e png</span><span class="sxs-lookup"><span data-stu-id="ee9bf-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="ee9bf-145">Aplicar dilatação e conversão de espaço de cor</span><span class="sxs-lookup"><span data-stu-id="ee9bf-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="ee9bf-146">Rotação de imagem</span><span class="sxs-lookup"><span data-stu-id="ee9bf-146">Image rotation</span></span>

* <span data-ttu-id="ee9bf-147">Dimensionamento de imagem</span><span class="sxs-lookup"><span data-stu-id="ee9bf-147">Image scaling</span></span>

* <span data-ttu-id="ee9bf-148">Mistura de imagem</span><span class="sxs-lookup"><span data-stu-id="ee9bf-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="ee9bf-149">Processamento de eventos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-149">Event processing</span></span>

* <span data-ttu-id="ee9bf-150">Suspende automaticamente o fio Azure RTOS GUIX quando está inativo</span><span class="sxs-lookup"><span data-stu-id="ee9bf-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="ee9bf-151">Modelo de programação orientado por eventos popular em design de UI</span><span class="sxs-lookup"><span data-stu-id="ee9bf-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="ee9bf-152">Isola os condutores de entrada do fio de desenho Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="ee9bf-153">Funções para envio e receção de eventos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="ee9bf-154">Tipos de eventos pré-definidos para todos os tipos de widgetS Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="ee9bf-155">Eventos personalizados definidos pelo utilizador suportados</span><span class="sxs-lookup"><span data-stu-id="ee9bf-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="ee9bf-156">Processamento de lona</span><span class="sxs-lookup"><span data-stu-id="ee9bf-156">Canvas processing</span></span>

* <span data-ttu-id="ee9bf-157">Manutenção de clipping e Z-Order</span><span class="sxs-lookup"><span data-stu-id="ee9bf-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="ee9bf-158">Isola a biblioteca widget a partir de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="ee9bf-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="ee9bf-159">Isola a aplicação a partir de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="ee9bf-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="ee9bf-160">Renovação automática de fundo de áreas sujas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="ee9bf-161">Múltiplas telas com camadas e mistura suportadas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="ee9bf-162">Pode ser invocado diretamente pelo software de aplicação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="ee9bf-163">Controlador de dispositivos de entrada</span><span class="sxs-lookup"><span data-stu-id="ee9bf-163">Input device driver(s)</span></span>

* <span data-ttu-id="ee9bf-164">Suporte específico para hardware, Azure RTOS GUIX e aplicação isolada de detalhes de hardware</span><span class="sxs-lookup"><span data-stu-id="ee9bf-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="ee9bf-165">Toque resistivo, toque de boné e teclado suportado</span><span class="sxs-lookup"><span data-stu-id="ee9bf-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="ee9bf-166">Eventos de entrada passados para a fila de eventos Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="ee9bf-167">Controladores de exibição</span><span class="sxs-lookup"><span data-stu-id="ee9bf-167">Display drivers</span></span>

* <span data-ttu-id="ee9bf-168">Suporte específico para hardware</span><span class="sxs-lookup"><span data-stu-id="ee9bf-168">Hardware-specific support</span></span>

* <span data-ttu-id="ee9bf-169">Condutores genéricos fornecidos para toda a profundidade e formatos de cor</span><span class="sxs-lookup"><span data-stu-id="ee9bf-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="ee9bf-170">Personalizado para utilizar aceleradores gráficos disponíveis</span><span class="sxs-lookup"><span data-stu-id="ee9bf-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="ee9bf-171">Hardware-alvo</span><span class="sxs-lookup"><span data-stu-id="ee9bf-171">Target hardware</span></span>

* <span data-ttu-id="ee9bf-172">Quase todo o hardware capaz de saída gráfica é compatível com GUIX</span><span class="sxs-lookup"><span data-stu-id="ee9bf-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="ee9bf-173">Múltiplas exibições físicas suportadas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="ee9bf-174">Requisitos mínimos de RAM e Flash</span><span class="sxs-lookup"><span data-stu-id="ee9bf-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="ee9bf-175">Criar interfaces de utilizador elegantes</span><span class="sxs-lookup"><span data-stu-id="ee9bf-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="ee9bf-176">Azure RTOS GUIX e Azure RTOS GUIX Studio fornecem todas as funcionalidades necessárias para criar interfaces de utilizador exclusivamente elegantes.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="ee9bf-177">O pacote padrão Azure RTOS GUIX inclui várias interfaces de utilizador de amostras, incluindo uma referência de dispositivo médico, uma referência de relógio inteligente, uma referência de domótica, uma referência de controlo industrial, uma referência automóvel, e vários exemplos de sprite e animação.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="ee9bf-178">Clique nos exemplos de referência apresentados abaixo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="ee9bf-179">Domótica</span><span class="sxs-lookup"><span data-stu-id="ee9bf-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="ee9bf-180">Médico</span><span class="sxs-lookup"><span data-stu-id="ee9bf-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="ee9bf-181">Consumidor</span><span class="sxs-lookup"><span data-stu-id="ee9bf-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="ee9bf-182">Bens Brancos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="ee9bf-183">Automóvel</span><span class="sxs-lookup"><span data-stu-id="ee9bf-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="ee9bf-184">Industrial</span><span class="sxs-lookup"><span data-stu-id="ee9bf-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="ee9bf-185">Cada referência Azure RTOS GUIX tem um projeto correspondente do Azure RTOS GUIX Studio que define todos os elementos gráficos do design de referência.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="ee9bf-186">Mudar um design de referência é fácil.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-186">Changing a reference design is easy.</span></span> <span data-ttu-id="ee9bf-187">Basta abrir o projeto Azure RTOS GUIX correspondente, fazer as alterações desejadas, salvar o projeto e, em seguida, selecionar *o Projeto*.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="ee9bf-188">Gere todos os ficheiros de saída para gerar o código C para Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="ee9bf-189">Em seguida, basta reconstruir a aplicação-alvo e correr para observar o design de referência modificado.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="ee9bf-190">Pequena pegada</span><span class="sxs-lookup"><span data-stu-id="ee9bf-190">Small-footprint</span></span>

<span data-ttu-id="ee9bf-191">O Azure RTOS GUIX tem uma pegada mínima notável de 13.2KB de FLASH e 4KB RAM para suporte básico, sem incluir a memória necessária para uma tela.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="ee9bf-192">Para um visor com gram interno e tecnologia de auto-atualização, não é necessária memória de lona.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="ee9bf-193">No entanto, para melhorar o desempenho do desenho, ou para uma configuração do visor que não utilize o GRAM local para o visor, uma área de memória de tela é definida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="ee9bf-194">Os requisitos de memória de lona são uma função do tamanho da tela, bem como da profundidade de cor, e são definidos pela fórmula:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="ee9bf-195"><i>RAM de lona (bytes) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="ee9bf-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="ee9bf-196">Onde "x" e "y" são as dimensões da tela (display).</span><span class="sxs-lookup"><span data-stu-id="ee9bf-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="ee9bf-197">A maioria das aplicações também utiliza recursos gráficos, que não estão incluídos nos requisitos de armazenamento da biblioteca Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="ee9bf-198">Estes recursos incluem fontes, ícones gráficos (pixelmaps) e cordas estáticas.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="ee9bf-199">Estes dados podem ser armazenados na secção de memória const (ou seja, FLASH).</span><span class="sxs-lookup"><span data-stu-id="ee9bf-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="ee9bf-200">O tamanho desta área de memória depende de uma série de fatores, incluindo o número e o tamanho de fontes únicas utilizadas, o número e o tamanho dos ícones gráficos utilizados, o formato de cor de saída, e se cada recurso está ou não a usar dados comprimidos, uma vez que o Azure RTOS GUIX suporta a compressão RLE tanto dos dados de fonte como de pixelmap.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="ee9bf-201">Os requisitos de armazenamento de cada recurso são apresentados dentro da aplicação Azure RTOS GUIX Studio, permitindo ao utilizador rastrear e monitorizar a quantidade de memória flash que será consumida pelos recursos da aplicação.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="ee9bf-202">Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS GUIX escala automaticamente com base nos serviços realmente utilizados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="ee9bf-203">Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="ee9bf-204">Execução rápida</span><span class="sxs-lookup"><span data-stu-id="ee9bf-204">Fast execution</span></span>

<span data-ttu-id="ee9bf-205">Azure RTOS GUIX é escrito exclusivamente em C e é projetado para a velocidade.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="ee9bf-206">Azure RTOS GUIX tem camadas mínimas de chamada de função interna.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="ee9bf-207">Além disso, o Azure RTOS GUIX fornece recortes, desenho e manuseamento de eventos otimizados.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="ee9bf-208">Tudo isto e uma filosofia de design orientada para o desempenho ajudam o Azure RTOS GUIX a alcançar o desempenho mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="ee9bf-209">Pré-certificado pela TUV para muitas normas de segurança</span><span class="sxs-lookup"><span data-stu-id="ee9bf-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="ee9bf-210">O Azure RTOS GUIX foi certificado pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="ee9bf-211">A certificação confirma que o Azure RTOS GUIX pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade da segurança do IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional de sistemas de segurança electrónica, elétricos e programáveis".</span><span class="sxs-lookup"><span data-stu-id="ee9bf-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="ee9bf-212">A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="ee9bf-213">A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="ee9bf-214">Simples e fácil de usar</span><span class="sxs-lookup"><span data-stu-id="ee9bf-214">Simple, easy-to-use</span></span>

<span data-ttu-id="ee9bf-215">O Azure RTOS GUIX é muito simples de usar e o Azure RTOS GUIX Studio torna ainda mais fácil, permitindo que os desenvolvedores desenhem visualmente no ambiente de trabalho e gerem código C que funciona no alvo real.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="ee9bf-216">As aplicações podem então adicionar as suas próprias funções personalizadas de manuseamento e desenho de eventos para completar o seu GUI.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="ee9bf-217">A utilização da API AZURE RTOS GUIX é simples.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="ee9bf-218">A Azure RTOS GUIX API é simultaneamente intuitiva e altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="ee9bf-219">Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" e/ou dos nomes altamente abreviados que são tão comuns em outros produtos do sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="ee9bf-220">Todas as APIs Azure RTOS GUIX têm uma *gx_* líder e seguem uma convenção de nomeação de substantivos.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="ee9bf-221">Além disso, existe uma consistência funcional em toda a API.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="ee9bf-222">Por exemplo, todas as APIs que inicializam um bloco de controlo widget são &lt; nomeadas widget_type &gt; _create, e os parâmetros de função de criação para cada tipo de widget são sempre definidos na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="ee9bf-223">Conjunto abrangente de widgets incorporados</span><span class="sxs-lookup"><span data-stu-id="ee9bf-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="ee9bf-224">Azure RTOS GUIX fornece um rico conjunto de widgets incorporados, incluindo:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="ee9bf-225">Menu de Acordeão</span><span class="sxs-lookup"><span data-stu-id="ee9bf-225">Accordion Menu</span></span>

* <span data-ttu-id="ee9bf-226">Botão</span><span class="sxs-lookup"><span data-stu-id="ee9bf-226">Button</span></span>

* <span data-ttu-id="ee9bf-227">Caixa de verificação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-227">Checkbox</span></span>

* <span data-ttu-id="ee9bf-228">Bitola Circular</span><span class="sxs-lookup"><span data-stu-id="ee9bf-228">Circular Gauge</span></span>

* <span data-ttu-id="ee9bf-229">Lista de drop down</span><span class="sxs-lookup"><span data-stu-id="ee9bf-229">Drop Down List</span></span>

* <span data-ttu-id="ee9bf-230">Lista Horizontal</span><span class="sxs-lookup"><span data-stu-id="ee9bf-230">Horizontal List</span></span>

* <span data-ttu-id="ee9bf-231">Janela horizontal do travessa</span><span class="sxs-lookup"><span data-stu-id="ee9bf-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="ee9bf-232">Ícone</span><span class="sxs-lookup"><span data-stu-id="ee9bf-232">Icon</span></span>

* <span data-ttu-id="ee9bf-233">Botão de ícone</span><span class="sxs-lookup"><span data-stu-id="ee9bf-233">Icon Button</span></span>

* <span data-ttu-id="ee9bf-234">Gráfico de linha</span><span class="sxs-lookup"><span data-stu-id="ee9bf-234">Line Chart</span></span>

* <span data-ttu-id="ee9bf-235">Menu</span><span class="sxs-lookup"><span data-stu-id="ee9bf-235">Menu</span></span>

* <span data-ttu-id="ee9bf-236">Botão de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="ee9bf-236">Multi Line Text Button</span></span>

* <span data-ttu-id="ee9bf-237">Entrada de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="ee9bf-237">Multi Line Text Input</span></span>

* <span data-ttu-id="ee9bf-238">Vista de texto multi linha</span><span class="sxs-lookup"><span data-stu-id="ee9bf-238">Multi Line Text View</span></span>

* <span data-ttu-id="ee9bf-239">Solicitação pixelmap numérica</span><span class="sxs-lookup"><span data-stu-id="ee9bf-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="ee9bf-240">Solicitação numérica</span><span class="sxs-lookup"><span data-stu-id="ee9bf-240">Numeric Prompt</span></span>

* <span data-ttu-id="ee9bf-241">Roda de pergaminho numérica</span><span class="sxs-lookup"><span data-stu-id="ee9bf-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="ee9bf-242">Botão Pixelmap</span><span class="sxs-lookup"><span data-stu-id="ee9bf-242">Pixelmap Button</span></span>

* <span data-ttu-id="ee9bf-243">Pixelmap Prompt</span><span class="sxs-lookup"><span data-stu-id="ee9bf-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="ee9bf-244">Pixelmap Slider</span><span class="sxs-lookup"><span data-stu-id="ee9bf-244">Pixelmap Slider</span></span>

* <span data-ttu-id="ee9bf-245">Pixelmap Sprite</span><span class="sxs-lookup"><span data-stu-id="ee9bf-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="ee9bf-246">Barra de Progresso</span><span class="sxs-lookup"><span data-stu-id="ee9bf-246">Progress Bar</span></span>

* <span data-ttu-id="ee9bf-247">Prompt</span><span class="sxs-lookup"><span data-stu-id="ee9bf-247">Prompt</span></span>

* <span data-ttu-id="ee9bf-248">Barra de Progresso Radial</span><span class="sxs-lookup"><span data-stu-id="ee9bf-248">Radial Progress Bar</span></span>

* <span data-ttu-id="ee9bf-249">Botão de rádio</span><span class="sxs-lookup"><span data-stu-id="ee9bf-249">Radio Button</span></span>

* <span data-ttu-id="ee9bf-250">Roda de pergaminho</span><span class="sxs-lookup"><span data-stu-id="ee9bf-250">Scroll Wheel</span></span>

* <span data-ttu-id="ee9bf-251">Entrada de texto de linha única</span><span class="sxs-lookup"><span data-stu-id="ee9bf-251">Single Line Text Input</span></span>

* <span data-ttu-id="ee9bf-252">Slider</span><span class="sxs-lookup"><span data-stu-id="ee9bf-252">Slider</span></span>

* <span data-ttu-id="ee9bf-253">Roda de pergaminho de corda</span><span class="sxs-lookup"><span data-stu-id="ee9bf-253">String Scroll Wheel</span></span>

* <span data-ttu-id="ee9bf-254">Botão de texto</span><span class="sxs-lookup"><span data-stu-id="ee9bf-254">Text Button</span></span>

* <span data-ttu-id="ee9bf-255">Vista de Árvore</span><span class="sxs-lookup"><span data-stu-id="ee9bf-255">Tree View</span></span>

* <span data-ttu-id="ee9bf-256">Lista Vertical</span><span class="sxs-lookup"><span data-stu-id="ee9bf-256">Vertical List</span></span>

* <span data-ttu-id="ee9bf-257">Barra de pergaminho vertical</span><span class="sxs-lookup"><span data-stu-id="ee9bf-257">Vertical Scrollbar</span></span>

<span data-ttu-id="ee9bf-258">É fácil para a aplicação criar os seus próprios widgets de cliente também.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="ee9bf-259">API de desenho de baixo nível completo</span><span class="sxs-lookup"><span data-stu-id="ee9bf-259">Complete low-level drawing API</span></span>

<span data-ttu-id="ee9bf-260">O Azure RTOS GUIX fornece uma API de desenho de tela robusta, permitindo que a aplicação torne formas gráficas complexas.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="ee9bf-261">Todas as funções suportam anti-aliasing em alvos de alta profundidade de cores, e todas as formas podem ser preenchidas o nosso delineado, incluindo preenchimentos sólidos e pixelmap padrão.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="ee9bf-262">Todos os primitivos de desenho suportam a escova alfa quando correm a 16 bpp e a profundidade de cor mais alta.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="ee9bf-263">As funções de desenho incluem:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-263">Drawing functions include:</span></span>

* <span data-ttu-id="ee9bf-264">Desenho de arco</span><span class="sxs-lookup"><span data-stu-id="ee9bf-264">Arc Draw</span></span>

* <span data-ttu-id="ee9bf-265">Desenho de círculo</span><span class="sxs-lookup"><span data-stu-id="ee9bf-265">Circle Draw</span></span>

* <span data-ttu-id="ee9bf-266">Desenho de linha</span><span class="sxs-lookup"><span data-stu-id="ee9bf-266">Line Draw</span></span>

* <span data-ttu-id="ee9bf-267">Sorteio de Tortas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-267">Pie Draw</span></span>

* <span data-ttu-id="ee9bf-268">Mistura pixelmap</span><span class="sxs-lookup"><span data-stu-id="ee9bf-268">Pixelmap Blend</span></span>

* <span data-ttu-id="ee9bf-269">Azulejo pixelmap</span><span class="sxs-lookup"><span data-stu-id="ee9bf-269">Pixelmap Tile</span></span>

* <span data-ttu-id="ee9bf-270">Desenho de Polígono</span><span class="sxs-lookup"><span data-stu-id="ee9bf-270">Polygon Draw</span></span>

* <span data-ttu-id="ee9bf-271">Desenho de texto</span><span class="sxs-lookup"><span data-stu-id="ee9bf-271">Text Draw</span></span>

* <span data-ttu-id="ee9bf-272">Desenho de acordes</span><span class="sxs-lookup"><span data-stu-id="ee9bf-272">Chord Draw</span></span>

* <span data-ttu-id="ee9bf-273">Desenho elipse</span><span class="sxs-lookup"><span data-stu-id="ee9bf-273">Ellipse Draw</span></span>

* <span data-ttu-id="ee9bf-274">Desenho de pixels</span><span class="sxs-lookup"><span data-stu-id="ee9bf-274">Pixel Draw</span></span>

* <span data-ttu-id="ee9bf-275">Pixelmap Draw</span><span class="sxs-lookup"><span data-stu-id="ee9bf-275">Pixelmap Draw</span></span>

* <span data-ttu-id="ee9bf-276">Rotação pixelmap</span><span class="sxs-lookup"><span data-stu-id="ee9bf-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="ee9bf-277">Desenho de retângulo</span><span class="sxs-lookup"><span data-stu-id="ee9bf-277">Rectangle Draw</span></span>

* <span data-ttu-id="ee9bf-278">Mistura de texto</span><span class="sxs-lookup"><span data-stu-id="ee9bf-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="ee9bf-279">Fontes gratuitas padrão e fácil de adicionar mais</span><span class="sxs-lookup"><span data-stu-id="ee9bf-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="ee9bf-280">Azure RTOS GUIX fornece um conjunto gratuito de fontes TrueType.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="ee9bf-281">Os desenvolvedores podem adicionar fontes TrueType adicionais conforme desejado.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="ee9bf-282">O formato de fonte Azure RTOS GUIX suporta fontes anti-aliasing 8bpp, 4bpp anti-aliasing e 1bpp de fontes monocromáticas.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="ee9bf-283">Para as aplicações mais restritas a recursos, o Azure RTOS GUIX pré-torna as fontes TrueType num formato de bitmap comprimido utilizando a nossa ferramenta de desktop GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="ee9bf-284">Implementação personalizada do descodificador JPG e PNG</span><span class="sxs-lookup"><span data-stu-id="ee9bf-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="ee9bf-285">Implementação personalizada de descodificador JPG e PNG descodificador de ficheiros JPG e PNG implementação.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="ee9bf-286">Esta implementação suporta a conversão de espaço de cores, dilatação e criação de tempo de execução de imagens de formato pixelmap compatíveis com Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="ee9bf-287">Extenso suporte de ecrã e ecrã tátil</span><span class="sxs-lookup"><span data-stu-id="ee9bf-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="ee9bf-288">Azure RTOS GUIX fornece controladores de exibição genéricos para quase todos os formatos de cores, incluindo monocromático de 1bpp, paleta de 8 bpp, formato 8 bpp 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="ee9bf-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="ee9bf-289">Formato 16 bpp 565 rgb, 16 bpp 4:4:4:4, formato 32 bpp x:r:g:b e 32 bpp a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="ee9bf-290">Além disso, o Azure RTOS GUIX está integrado com muitos dos controladores LCD mais populares e aceleradores de hardware (ST ChromeArt, Renesas Synergy, etc.).</span><span class="sxs-lookup"><span data-stu-id="ee9bf-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="ee9bf-291">O Azure RTOS GUIX suporta totalmente o ecrã tátil (incluindo suporte a gestos), caneta e dispositivos de entrada de teclado virtual.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="ee9bf-292">Ferramenta Azure RTOS GUIX Studio WYSIWYG</span><span class="sxs-lookup"><span data-stu-id="ee9bf-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="ee9bf-293">O Azure RTOS GUIX Studio fornece um ambiente completo de design de ecrã WYSIWYG que permite ao utilizador arrastar e largar elementos gráficos usados para construir os ecrãs GUI.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="ee9bf-294">O Azure RTOS GUIX Studio gera automaticamente código C compatível com a biblioteca Azure RTOS GUIX, pronta a ser compilada e executada no alvo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="ee9bf-295">Os desenvolvedores podem produzir fontes pré-renderizadas para uso dentro de uma aplicação usando a ferramenta integrada de geração de fontes Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="ee9bf-296">As fontes podem ser geradas em formatos monocromáticos ou anti-aliased, e são otimizadas para economizar espaço no alvo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="ee9bf-297">Os tipos de letra podem incluir qualquer conjunto de caracteres, incluindo caracteres Unicode para aplicações multilingues.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="ee9bf-298">O Azure RTOS GUIX Studio facilita a importação de gráficos de ficheiros PNG ou JPG com conversão para Azure RTOS GUIX Pixelmaps para utilização no sistema-alvo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="ee9bf-299">Muitos dos tipos de widgetS Azure RTOS GUIX são projetados para incorporar gráficos do utilizador para uma aparência e sensação personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="ee9bf-300">Além disso, o Azure RTOS GUIX Studio permite personalizar as cores padrão e os estilos de desenho usados pelos widgets Azure RTOS GUIX, permitindo aos desenvolvedores sintonizar muito facilmente a aparência do Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="ee9bf-301">Geração e manutenção de cadeias de aplicações é outra instalação incorporada do Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="ee9bf-302">Isto permite que os desenvolvedores desenhem uma aplicação usando uma língua para desenvolver, e de forma rápida e fácil adicionar suporte para idiomas adicionais após o lançamento do produto.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="ee9bf-303">Uma aplicação completa do Azure RTOS GUIX pode ser executada num ambiente de pc dentro do ambiente Azure RTOS GUIX Studio, permitindo uma geração rápida e fácil e demonstração de conceitos GUI, testes de fluxos de ecrã e observação de transições de ecrã e animações.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="ee9bf-304">Quando concluído, um design pode ser exportado como estruturas de dados C prontas para o alvo, prontas a ser compiladas e ligadas às bibliotecas Azure RTOS GUIX e Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="ee9bf-305">Azure RTOS GUIX e Azure RTOS GUIX Studio suportam vários temas de recursos, permitindo que uma aplicação seja facilmente ressarsado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="ee9bf-306">Fontes, cores e pixelmaps podem ser alterados no tempo de execução com uma simples API.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="ee9bf-307">Saiba mais sobre o GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="ee9bf-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="ee9bf-308">Simulação completa do Win32</span><span class="sxs-lookup"><span data-stu-id="ee9bf-308">Complete Win32 simulation</span></span>

<span data-ttu-id="ee9bf-309">O Azure RTOS GUIX funciona num PC Windows, utilizando exatamente a mesma biblioteca de desenho que funciona no quadro-alvo.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="ee9bf-310">Com o Azure RTOS GUIX, pode construir e executar uma aplicação GUI no PC, e usar o mesmo código de aplicação no seu alvo para depuração rápida, prototipagem rápida, demonstração e operação alvo WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="ee9bf-311">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="ee9bf-311">Advanced technology</span></span>

* <span data-ttu-id="ee9bf-312">A tecnologia avançada da Azure RTOS GUIX incorpora:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="ee9bf-313">Mistura alfa</span><span class="sxs-lookup"><span data-stu-id="ee9bf-313">Alpha blending</span></span>

* <span data-ttu-id="ee9bf-314">Anti-Aliasing</span><span class="sxs-lookup"><span data-stu-id="ee9bf-314">Anti-Aliasing</span></span>

* <span data-ttu-id="ee9bf-315">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="ee9bf-315">Automatic scaling</span></span>

* <span data-ttu-id="ee9bf-316">Compressão bitmap</span><span class="sxs-lookup"><span data-stu-id="ee9bf-316">Bitmap compression</span></span>

* <span data-ttu-id="ee9bf-317">Mistura de lona</span><span class="sxs-lookup"><span data-stu-id="ee9bf-317">Canvas blending</span></span>

* <span data-ttu-id="ee9bf-318">Suporte widget personalizado</span><span class="sxs-lookup"><span data-stu-id="ee9bf-318">Custom widget support</span></span>

* <span data-ttu-id="ee9bf-319">Suporte de desenho diferido</span><span class="sxs-lookup"><span data-stu-id="ee9bf-319">Deferred drawing support</span></span>

* <span data-ttu-id="ee9bf-320">Apoio dithering</span><span class="sxs-lookup"><span data-stu-id="ee9bf-320">Dithering support</span></span>

* <span data-ttu-id="ee9bf-321">Programação neutra endiana</span><span class="sxs-lookup"><span data-stu-id="ee9bf-321">Endian neutral programming</span></span>

* <span data-ttu-id="ee9bf-322">Suporte ao acelerador de hardware</span><span class="sxs-lookup"><span data-stu-id="ee9bf-322">Hardware accelerator support</span></span>

* <span data-ttu-id="ee9bf-323">Suporte multilinguístico e codificação UTF-8</span><span class="sxs-lookup"><span data-stu-id="ee9bf-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="ee9bf-324">Suporte de exibição e lona múltipla</span><span class="sxs-lookup"><span data-stu-id="ee9bf-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="ee9bf-325">Recortes otimizados, desenho e manipulação de eventos</span><span class="sxs-lookup"><span data-stu-id="ee9bf-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="ee9bf-326">Descodificador JPEG e PNG</span><span class="sxs-lookup"><span data-stu-id="ee9bf-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="ee9bf-327">Esfolar e Temas</span><span class="sxs-lookup"><span data-stu-id="ee9bf-327">Skinning and Themes</span></span>

* <span data-ttu-id="ee9bf-328">Suporta monocromático através de 32 bits de cor verdadeira com formatos gráficos alfa</span><span class="sxs-lookup"><span data-stu-id="ee9bf-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="ee9bf-329">Transições, Sprites e Suporte de Animação</span><span class="sxs-lookup"><span data-stu-id="ee9bf-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="ee9bf-330">Simulação Win32</span><span class="sxs-lookup"><span data-stu-id="ee9bf-330">Win32 simulation</span></span>

* <span data-ttu-id="ee9bf-331">Gestão de janelas, incluindo Viewports e manutenção de ordem Z</span><span class="sxs-lookup"><span data-stu-id="ee9bf-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="ee9bf-332">O tempo de venda mais rápido</span><span class="sxs-lookup"><span data-stu-id="ee9bf-332">Fastest time-to-market</span></span>

<span data-ttu-id="ee9bf-333">O Azure RTOS GUIX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="ee9bf-334">O Azure RTOS GUIX Studio também ajuda a facilitar o design e implementação do GUI incorporados.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="ee9bf-335">Como resultado, o Azure RTOS GUIX é uma das soluções GUI mais populares para dispositivos IoT incorporados.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="ee9bf-336">A nossa vantagem consistente no mercado baseia-se em:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="ee9bf-337">Documentação de Qualidade – por favor, reveja [o nosso Guia de Utilizador Azure RTOS GUIX](about-guix.md) e veja por si mesmo!</span><span class="sxs-lookup"><span data-stu-id="ee9bf-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="ee9bf-338">Disponibilidade completa do Código Fonte</span><span class="sxs-lookup"><span data-stu-id="ee9bf-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="ee9bf-339">API de fácil utilização</span><span class="sxs-lookup"><span data-stu-id="ee9bf-339">Easy-to-use API</span></span>

* <span data-ttu-id="ee9bf-340">Conjunto de recursos abrangente e avançado</span><span class="sxs-lookup"><span data-stu-id="ee9bf-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="ee9bf-341">Uma licença simples</span><span class="sxs-lookup"><span data-stu-id="ee9bf-341">One Simple License</span></span>

<span data-ttu-id="ee9bf-342">Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="ee9bf-343">Código fonte completo e de alta qualidade</span><span class="sxs-lookup"><span data-stu-id="ee9bf-343">Full, highest-quality source code</span></span>

<span data-ttu-id="ee9bf-344">Ao longo dos anos, o código fonte Azure RTOS NetX definiu a fasquia em qualidade e facilidade de compreensão.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="ee9bf-345">Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.</span><span class="sxs-lookup"><span data-stu-id="ee9bf-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="ee9bf-346">Apoia as arquiteturas mais populares</span><span class="sxs-lookup"><span data-stu-id="ee9bf-346">Supports most popular architectures</span></span>

<span data-ttu-id="ee9bf-347">O Azure RTOS GUIX funciona com microprocessadores de 32/64 bits mais populares, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="ee9bf-348">Arquiteturas Avançadas:</span><span class="sxs-lookup"><span data-stu-id="ee9bf-348">Advanced Architectures:</span></span>

<span data-ttu-id="ee9bf-349">**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="ee9bf-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="ee9bf-350">**Núcleo de Andes**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ee9bf-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="ee9bf-351">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="ee9bf-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="ee9bf-352">**BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="ee9bf-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="ee9bf-353">**Cadência**: Xtensa, Diamante</span><span class="sxs-lookup"><span data-stu-id="ee9bf-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="ee9bf-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi</span><span class="sxs-lookup"><span data-stu-id="ee9bf-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="ee9bf-355">**Cipreste**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ee9bf-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="ee9bf-356">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="ee9bf-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="ee9bf-357">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="ee9bf-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="ee9bf-358">**Informação; Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="ee9bf-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="ee9bf-359">**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="ee9bf-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="ee9bf-360">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="ee9bf-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="ee9bf-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="ee9bf-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="ee9bf-362">**Renesas**: SH, HS, V850, RX, RZ, Sinergia</span><span class="sxs-lookup"><span data-stu-id="ee9bf-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="ee9bf-363">**Laboratórios de Silício**: EFM32</span><span class="sxs-lookup"><span data-stu-id="ee9bf-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="ee9bf-364">**Sinopses**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="ee9bf-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="ee9bf-365">**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="ee9bf-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="ee9bf-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="ee9bf-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="ee9bf-367">**Computação de ondas**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M</span><span class="sxs-lookup"><span data-stu-id="ee9bf-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="ee9bf-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="ee9bf-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
