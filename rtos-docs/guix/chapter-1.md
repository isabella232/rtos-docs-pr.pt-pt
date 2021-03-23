---
title: Capítulo 1 - Introdução ao GUIX
description: GUIX é uma implementação em tempo real de alto desempenho de um (GUI) projetado exclusivamente para aplicações incorporadas baseadas em Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827205"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="a5659-103">Capítulo 1 - Introdução ao Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="a5659-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="a5659-104">Azure RTOS GUIX (GUIX) é uma implementação em tempo real de alto desempenho de uma estrutura de interface gráfica projetada exclusivamente para aplicações incorporadas baseadas em ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a5659-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="a5659-105">Este capítulo contém uma introdução ao GUIX e uma descrição das suas aplicações e benefícios.</span><span class="sxs-lookup"><span data-stu-id="a5659-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="a5659-106">Visão geral do recurso GUIX</span><span class="sxs-lookup"><span data-stu-id="a5659-106">GUIX Feature Overview</span></span>

<span data-ttu-id="a5659-107">Ao contrário de muitas outras implementações do GUI, o GUIX foi concebido para ser versátil — facilmente dimensionando de pequenas aplicações baseadas em microcontrolador para aquelas que utilizam poderosos processadores RISC e DSP.</span><span class="sxs-lookup"><span data-stu-id="a5659-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="a5659-108">Isto contrasta fortemente com o domínio público ou outras implementações comerciais originalmente destinadas a ambientes de estações de trabalho, mas depois espremidas em desenhos incorporados.</span><span class="sxs-lookup"><span data-stu-id="a5659-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="a5659-109">Segue-se uma visão geral das funcionalidades do GUIX:</span><span class="sxs-lookup"><span data-stu-id="a5659-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="a5659-110">Fácil de usar com ferramenta de design baseada em anfitrião GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="a5659-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="a5659-111">Win32 GUIX ambiente de tempo de execução para prototipagem completa hospedada</span><span class="sxs-lookup"><span data-stu-id="a5659-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="a5659-112">Suporta a maioria dos processadores suportados pela ThreadX</span><span class="sxs-lookup"><span data-stu-id="a5659-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="a5659-113">Escrito exclusivamente em ANSI C</span><span class="sxs-lookup"><span data-stu-id="a5659-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="a5659-114">Endian neutro</span><span class="sxs-lookup"><span data-stu-id="a5659-114">Endian neutral</span></span>

- <span data-ttu-id="a5659-115">GUI mais pequeno e embelho embutido</span><span class="sxs-lookup"><span data-stu-id="a5659-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="a5659-116">Tempo de execução configurável, número de objetos, tamanho do ecrã, etc.</span><span class="sxs-lookup"><span data-stu-id="a5659-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="a5659-117">Fácil de escrever interface do controlador de exibição</span><span class="sxs-lookup"><span data-stu-id="a5659-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="a5659-118">Cor (até 32 bpp profundidade de cor), monocromático e suporte à escala de cinza</span><span class="sxs-lookup"><span data-stu-id="a5659-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="a5659-119">Suporte multilinguístico através da codificação de cordas UTF8 e recursos de cordas</span><span class="sxs-lookup"><span data-stu-id="a5659-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="a5659-120">Fontes gratuitas padrão e fácil de adicionar novos tipos de letra</span><span class="sxs-lookup"><span data-stu-id="a5659-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="a5659-121">Telas de desenho múltipla suportadas, de vários tamanhos</span><span class="sxs-lookup"><span data-stu-id="a5659-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="a5659-122">Múltiplas exibições de diferentes tamanhos e profundidades de cor suportadas</span><span class="sxs-lookup"><span data-stu-id="a5659-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="a5659-123">Suporte para a transição do ecrã (desvanecer-se, desvanecer-se, passar, etc.)</span><span class="sxs-lookup"><span data-stu-id="a5659-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="a5659-124">Ecrã tátil, gesto e suporte virtual do teclado</span><span class="sxs-lookup"><span data-stu-id="a5659-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="a5659-125">Compressão bitmap</span><span class="sxs-lookup"><span data-stu-id="a5659-125">Bitmap compression</span></span>

- <span data-ttu-id="a5659-126">Suporte de mistura alfa</span><span class="sxs-lookup"><span data-stu-id="a5659-126">Alpha Blending Support</span></span>

- <span data-ttu-id="a5659-127">Apoio dither</span><span class="sxs-lookup"><span data-stu-id="a5659-127">Dither Support</span></span>

- <span data-ttu-id="a5659-128">Apoio Anti-Aliasing</span><span class="sxs-lookup"><span data-stu-id="a5659-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="a5659-129">Esfolar e Temas</span><span class="sxs-lookup"><span data-stu-id="a5659-129">Skinning and Themes</span></span>

- <span data-ttu-id="a5659-130">Mistura de tela</span><span class="sxs-lookup"><span data-stu-id="a5659-130">Canvas Blending</span></span>

- <span data-ttu-id="a5659-131">Gestão completa da janela</span><span class="sxs-lookup"><span data-stu-id="a5659-131">Complete Window Management</span></span>

  - <span data-ttu-id="a5659-132">Relação pai/filho</span><span class="sxs-lookup"><span data-stu-id="a5659-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="a5659-133">Criação dinâmica, eliminação, redimensionamento, movimento</span><span class="sxs-lookup"><span data-stu-id="a5659-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="a5659-134">Manipulação e desenho de eventos separados</span><span class="sxs-lookup"><span data-stu-id="a5659-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="a5659-135">Ordenação Z</span><span class="sxs-lookup"><span data-stu-id="a5659-135">Z-order</span></span>
  - <span data-ttu-id="a5659-136">Recortes e vistas</span><span class="sxs-lookup"><span data-stu-id="a5659-136">Clipping and views</span></span>

- <span data-ttu-id="a5659-137">Conjunto extensivo de widgets</span><span class="sxs-lookup"><span data-stu-id="a5659-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="a5659-138">Vários tipos de botões, sliders e mostradores</span><span class="sxs-lookup"><span data-stu-id="a5659-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="a5659-139">Lista de drop down</span><span class="sxs-lookup"><span data-stu-id="a5659-139">Drop Down List</span></span>
  
  - <span data-ttu-id="a5659-140">Prompt</span><span class="sxs-lookup"><span data-stu-id="a5659-140">Prompt</span></span>

  - <span data-ttu-id="a5659-141">Vista de texto multi-linha</span><span class="sxs-lookup"><span data-stu-id="a5659-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="a5659-142">Entrada de texto simples e multi-linha</span><span class="sxs-lookup"><span data-stu-id="a5659-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="a5659-143">Rodas de pergaminho numérico e textual</span><span class="sxs-lookup"><span data-stu-id="a5659-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="a5659-144">Janelas e barras de pergaminho</span><span class="sxs-lookup"><span data-stu-id="a5659-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="a5659-145">Barra de Progresso Radial</span><span class="sxs-lookup"><span data-stu-id="a5659-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="a5659-146">Sprite</span><span class="sxs-lookup"><span data-stu-id="a5659-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="a5659-147">Código Fonte ANSI C</span><span class="sxs-lookup"><span data-stu-id="a5659-147">ANSI C Source Code</span></span>

<span data-ttu-id="a5659-148">GUIX é escrito completamente em ANSI C e é portátil imediatamente para praticamente qualquer arquitetura de processador que tenha um compilador ANSI C e suporte ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a5659-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="a5659-149">Embora escrito em ANSI C, GUIX usa um modelo e herança orientados para objetos.</span><span class="sxs-lookup"><span data-stu-id="a5659-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="a5659-150">Não uma caixa preta</span><span class="sxs-lookup"><span data-stu-id="a5659-150">Not A Black Box</span></span>

<span data-ttu-id="a5659-151">A maioria das distribuições do GUIX incluem o código fonte C completo.</span><span class="sxs-lookup"><span data-stu-id="a5659-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="a5659-152">Isto elimina os problemas da "caixa preta" que ocorrem com muitas implementações comerciais do GUI.</span><span class="sxs-lookup"><span data-stu-id="a5659-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="a5659-153">Ao usar o GUIX, os desenvolvedores de aplicações podem ver exatamente o que o GUI está a fazer - não há mistérios!</span><span class="sxs-lookup"><span data-stu-id="a5659-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="a5659-154">Ter o código fonte também permite modificações específicas da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a5659-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="a5659-155">Embora não recomendado, é certamente benéfico ter a capacidade de modificar o GUI se for necessário.</span><span class="sxs-lookup"><span data-stu-id="a5659-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="a5659-156">Estas funcionalidades são especialmente reconfortantes para os desenvolvedores habituados a trabalhar com produtos de domínio interno ou público.</span><span class="sxs-lookup"><span data-stu-id="a5659-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="a5659-157">Esperam ter código fonte e a capacidade de modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="a5659-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="a5659-158">GUIX é o software GUI final para tais desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="a5659-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="a5659-159">Aplicações GUI incorporadas</span><span class="sxs-lookup"><span data-stu-id="a5659-159">Embedded GUI Applications</span></span>

<span data-ttu-id="a5659-160">As aplicações GUI incorporadas são aplicações que têm um requisito de interface de utilizador e executam em microprocessadores escondidos dentro de produtos como telemóveis, equipamentos de comunicação, motores automóveis, impressoras a laser, dispositivos médicos, etc.</span><span class="sxs-lookup"><span data-stu-id="a5659-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="a5659-161">Tais aplicações têm quase sempre algumas restrições de memória e desempenho.</span><span class="sxs-lookup"><span data-stu-id="a5659-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="a5659-162">Outra distinção do GUI incorporado é que o seu software e hardware têm um propósito dedicado.</span><span class="sxs-lookup"><span data-stu-id="a5659-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="a5659-163">Software GUI em tempo real</span><span class="sxs-lookup"><span data-stu-id="a5659-163">Real-time GUI Software</span></span>

<span data-ttu-id="a5659-164">Basicamente, o software GUI que deve realizar o seu processamento dentro de um período exato de tempo é chamado de software *GUI em tempo real,* e quando as restrições de tempo são impostas às aplicações GUI, são classificadas como aplicações em tempo real.</span><span class="sxs-lookup"><span data-stu-id="a5659-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="a5659-165">As aplicações GUI incorporadas são quase sempre em tempo real devido à sua interação inerente com o mundo externo.</span><span class="sxs-lookup"><span data-stu-id="a5659-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="a5659-166">Benefícios GUIX</span><span class="sxs-lookup"><span data-stu-id="a5659-166">GUIX Benefits</span></span>

<span data-ttu-id="a5659-167">Os principais benefícios da utilização do GUIX para aplicações incorporadas são os requisitos de alta performance, características ricas e muito pequenas necessidades de memória.</span><span class="sxs-lookup"><span data-stu-id="a5659-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="a5659-168">O GUIX também está completamente integrado com o sistema operativo de alto desempenho, multitasking Azure RTOS ThreadX em tempo real.</span><span class="sxs-lookup"><span data-stu-id="a5659-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="a5659-169">Melhor capacidade de resposta</span><span class="sxs-lookup"><span data-stu-id="a5659-169">Improved Responsiveness</span></span>

<span data-ttu-id="a5659-170">O produto GUIX de alto desempenho permite que as aplicações respondam mais rapidamente do que nunca.</span><span class="sxs-lookup"><span data-stu-id="a5659-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="a5659-171">Isto é especialmente importante para aplicações incorporadas que tenham um volume significativo de informações visuais ou requisitos rigorosos de tempo na exibição dessas informações.</span><span class="sxs-lookup"><span data-stu-id="a5659-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="a5659-172">Manutenção de Software</span><span class="sxs-lookup"><span data-stu-id="a5659-172">Software Maintenance</span></span>

<span data-ttu-id="a5659-173">A utilização do GUIX permite que os desenvolvedores partilhem facilmente os aspetos GUI da sua aplicação incorporada.</span><span class="sxs-lookup"><span data-stu-id="a5659-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="a5659-174">Esta partição torna todo o processo de desenvolvimento fácil e aumenta significativamente a manutenção futura do software.</span><span class="sxs-lookup"><span data-stu-id="a5659-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="a5659-175">Aumento da produção</span><span class="sxs-lookup"><span data-stu-id="a5659-175">Increased Throughput</span></span>

<span data-ttu-id="a5659-176">O GUIX fornece o GUI de maior desempenho disponível, que transfere diretamente para a aplicação incorporada.</span><span class="sxs-lookup"><span data-stu-id="a5659-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="a5659-177">As aplicações GUIX são capazes de processar informações de interface de utilizador mais rapidamente do que aplicações não GUIX!</span><span class="sxs-lookup"><span data-stu-id="a5659-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="a5659-178">Isolamento do processador</span><span class="sxs-lookup"><span data-stu-id="a5659-178">Processor Isolation</span></span>

<span data-ttu-id="a5659-179">O GUIX fornece uma interface robusta e independente entre a aplicação e o hardware de exibição e processador subjacente.</span><span class="sxs-lookup"><span data-stu-id="a5659-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="a5659-180">Isto permite que os desenvolvedores se concentrem nos aspetos de alto nível da interface do utilizador em vez de gastarem tempo extra a lidar com problemas de hardware de exibição.</span><span class="sxs-lookup"><span data-stu-id="a5659-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="a5659-181">Facilidade de utilização</span><span class="sxs-lookup"><span data-stu-id="a5659-181">Ease of Use</span></span>

<span data-ttu-id="a5659-182">O GUIX foi concebido tendo em mente o desenvolvedor de aplicações.</span><span class="sxs-lookup"><span data-stu-id="a5659-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="a5659-183">A arquitetura GUIX e a interface de chamada de serviço são fáceis de entender.</span><span class="sxs-lookup"><span data-stu-id="a5659-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="a5659-184">Como resultado, os desenvolvedores GUIX podem usar rapidamente as suas funcionalidades avançadas.</span><span class="sxs-lookup"><span data-stu-id="a5659-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="a5659-185">Melhorar o tempo para o mercado</span><span class="sxs-lookup"><span data-stu-id="a5659-185">Improve Time to Market</span></span>

<span data-ttu-id="a5659-186">As poderosas características do GUIX aceleram o processo de desenvolvimento de software.</span><span class="sxs-lookup"><span data-stu-id="a5659-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="a5659-187">O GUIX abstrata a maioria dos problemas de processador e de ecrã de hardware, removendo assim estas preocupações da maioria da implementação da interface do utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a5659-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="a5659-188">Esta funcionalidade, aliada à facilidade de utilização e ao conjunto de funcionalidades avançadas, resulta num tempo mais rápido para o mercado!</span><span class="sxs-lookup"><span data-stu-id="a5659-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="a5659-189">Proteger o Investimento em Software</span><span class="sxs-lookup"><span data-stu-id="a5659-189">Protecting the Software Investment</span></span>

<span data-ttu-id="a5659-190">O GUIX é escrito exclusivamente em ANSI C e está totalmente integrado com o sistema operativo Azure RTOS ThreadX em tempo real.</span><span class="sxs-lookup"><span data-stu-id="a5659-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="a5659-191">Isto significa que as aplicações GUIX são instantaneamente portáteis para todos os processadores suportados pela ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a5659-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="a5659-192">Melhor ainda, uma arquitetura de processador completamente nova pode ser suportada com a ThreadX em questão de semanas.</span><span class="sxs-lookup"><span data-stu-id="a5659-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="a5659-193">Como resultado, a utilização do GUIX garante a trajetória de migração da aplicação e protege o investimento original de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="a5659-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
