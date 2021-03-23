---
title: Guia do Utilizador do Azure RTOS GUIX
description: Este guia contém informações completas sobre o Azure RTOS GUIX, o produto GUI de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827290"
---
# <a name="about-guix-user-guide"></a><span data-ttu-id="721de-103">Sobre o Guia do Utilizador GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-103">About GUIX User Guide</span></span>

<span data-ttu-id="721de-104">Este guia contém informações completas sobre o Azure RTOS GUIX, o produto GUI de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="721de-104">This guide contains comprehensive information about Azure RTOS GUIX, the high-performance GUI product from Microsoft.</span></span> <span data-ttu-id="721de-105">Destina-se a desenvolvedores de software embutidos em tempo real familiarizados com conceitos básicos de GUI, Azure RTOS ThreadX e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="721de-105">It is intended for embedded real-time software developers familiar with basic GUI concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="721de-106">Organização</span><span class="sxs-lookup"><span data-stu-id="721de-106">Organization</span></span>

[<span data-ttu-id="721de-107">Capítulo 1 - Introdução ao Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-107">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>](chapter-1.md)

[<span data-ttu-id="721de-108">Capítulo 2 - Instalação e utilização do Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-108">Chapter 2 - Installation and use of Azure RTOS GUIX</span></span>](chapter-2.md)

[<span data-ttu-id="721de-109">Capítulo 3 - Visão geral funcional do Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-109">Chapter 3 - Functional Overview of Azure RTOS GUIX</span></span>](chapter-3.md)

[<span data-ttu-id="721de-110">Capítulo 4 - Descrição dos Serviços Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-110">Chapter 4 - Description of Azure RTOS GUIX Services</span></span>](chapter-4.md)

[<span data-ttu-id="721de-111">Capítulo 5 - Azure RTOS GUIX Display Drivers</span><span class="sxs-lookup"><span data-stu-id="721de-111">Chapter 5 - Azure RTOS GUIX Display Drivers</span></span>](chapter-5.md)  

[<span data-ttu-id="721de-112">Exemplo Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-112">Azure RTOS GUIX Example</span></span>](guix-example.md)

[<span data-ttu-id="721de-113">Apêndice A - Azure RTOS GUIX Definições de cor</span><span class="sxs-lookup"><span data-stu-id="721de-113">Appendix A - Azure RTOS GUIX Color Definitions</span></span>](appendix-a.md)

[<span data-ttu-id="721de-114">Apêndice B - Azure RTOS GUIX Formais de cores</span><span class="sxs-lookup"><span data-stu-id="721de-114">Appendix B - Azure RTOS GUIX Color Formats</span></span>](appendix-b.md)

[<span data-ttu-id="721de-115">Apêndice C - Azure RTOS GUIX Widget Styles</span><span class="sxs-lookup"><span data-stu-id="721de-115">Appendix C - Azure RTOS GUIX Widget Styles</span></span>](appendix-c.md)

[<span data-ttu-id="721de-116">Apêndice D - Azure RTOS GUIX Brush, Canvas and Gradient Atributos</span><span class="sxs-lookup"><span data-stu-id="721de-116">Appendix D - Azure RTOS GUIX Brush, Canvas and Gradient Attributes</span></span>](appendix-d.md)

[<span data-ttu-id="721de-117">Apêndice E - Descrição do evento Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-117">Appendix E - Azure RTOS GUIX Event Description</span></span>](appendix-e.md)

[<span data-ttu-id="721de-118">Apêndice F - Azure RTOS GUIX RTOS Serviços de Ligação</span><span class="sxs-lookup"><span data-stu-id="721de-118">Appendix F - Azure RTOS GUIX RTOS Binding Services</span></span>](appendix-f.md)

[<span data-ttu-id="721de-119">Apêndice G - Estrutura de FonteS DE FONTE Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-119">Appendix G - Azure RTOS GUIX Font Structure</span></span>](appendix-g.md)

[<span data-ttu-id="721de-120">Apêndice H - Azure RTOS GUIX Build-Time Bandeiras de configuração</span><span class="sxs-lookup"><span data-stu-id="721de-120">Appendix H - Azure RTOS GUIX Build-Time Configuration flags</span></span>](appendix-h.md)

[<span data-ttu-id="721de-121">Apêndice I - Azure RTOS GUIX Estruturas de Informação</span><span class="sxs-lookup"><span data-stu-id="721de-121">Appendix I - Azure RTOS GUIX Information Structures</span></span>](appendix-i.md)

## <a name="guide-conventions"></a><span data-ttu-id="721de-122">Convenções-Guia</span><span class="sxs-lookup"><span data-stu-id="721de-122">Guide Conventions</span></span>

<span data-ttu-id="721de-123">*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.</span><span class="sxs-lookup"><span data-stu-id="721de-123">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="721de-124">**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.</span><span class="sxs-lookup"><span data-stu-id="721de-124">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="721de-125">Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.</span><span class="sxs-lookup"><span data-stu-id="721de-125">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

## <a name="azure-rtos-guix-data-types"></a><span data-ttu-id="721de-126">Tipos de dados Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="721de-126">Azure RTOS GUIX Data Types</span></span>

<span data-ttu-id="721de-127">Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS GUIX, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="721de-127">In addition to the custom Azure RTOS GUIX control structure data types, there are several special data types that are used in Azure RTOS GUIX service call interfaces.</span></span> <span data-ttu-id="721de-128">Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente.</span><span class="sxs-lookup"><span data-stu-id="721de-128">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="721de-129">Isto é feito para garantir a portabilidade entre diferentes compiladores C.</span><span class="sxs-lookup"><span data-stu-id="721de-129">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="721de-130">A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.</span><span class="sxs-lookup"><span data-stu-id="721de-130">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="721de-131">Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS GUIX e os seus significados associados:</span><span class="sxs-lookup"><span data-stu-id="721de-131">The following is a list of Azure RTOS GUIX service call data types and their associated meanings:</span></span>

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="721de-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="721de-132">**UINT**</span></span>             | <span data-ttu-id="721de-133">Número inteiro básico não assinado.</span><span class="sxs-lookup"><span data-stu-id="721de-133">Basic unsigned integer.</span></span> <span data-ttu-id="721de-134">Este tipo é mapeado para o mais conveniente tipo de dados não assinado.</span><span class="sxs-lookup"><span data-stu-id="721de-134">This type is mapped to the most convenient unsigned data type.</span></span>                                |
| <span data-ttu-id="721de-135">**INT**</span><span class="sxs-lookup"><span data-stu-id="721de-135">**INT**</span></span>              | <span data-ttu-id="721de-136">Inteiro assinado básico.</span><span class="sxs-lookup"><span data-stu-id="721de-136">Basic signed integer.</span></span> <span data-ttu-id="721de-137">Este tipo é mapeado para o tipo de dados assinado mais conveniente.</span><span class="sxs-lookup"><span data-stu-id="721de-137">This type is mapped to the most convenient signed data type.</span></span>                                    |
| <span data-ttu-id="721de-138">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="721de-138">**ULONG**</span></span>            | <span data-ttu-id="721de-139">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="721de-139">Unsigned long type.</span></span> <span data-ttu-id="721de-140">Este tipo deve suportar dados não assinados de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="721de-140">This type must support 32-bit unsigned data.</span></span>                                                      |
| <span data-ttu-id="721de-141">**VAZIO**</span><span class="sxs-lookup"><span data-stu-id="721de-141">**VOID**</span></span>             | <span data-ttu-id="721de-142">Quase sempre equivalente ao tipo vazio do compilador.</span><span class="sxs-lookup"><span data-stu-id="721de-142">Almost always equivalent to the compiler’s void type.</span></span>                                                                 |
| <span data-ttu-id="721de-143">**GX_CHAR**</span><span class="sxs-lookup"><span data-stu-id="721de-143">**GX_CHAR**</span></span>         | <span data-ttu-id="721de-144">Na maioria das vezes, dactilografado como o compilador definido tipo de char.</span><span class="sxs-lookup"><span data-stu-id="721de-144">Most often typedefed as the compiler defined char type.</span></span>                                                               |
| <span data-ttu-id="721de-145">**GX_BYTE**</span><span class="sxs-lookup"><span data-stu-id="721de-145">**GX_BYTE**</span></span>          | <span data-ttu-id="721de-146">Tipo assinado de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="721de-146">8-bit signed type.</span></span>                                                                                                    |
| <span data-ttu-id="721de-147">**GX_UBYTE**</span><span class="sxs-lookup"><span data-stu-id="721de-147">**GX_UBYTE**</span></span>         | <span data-ttu-id="721de-148">Tipo não assinado de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="721de-148">8-bit unsigned type.</span></span>                                                                                                  |
| <span data-ttu-id="721de-149">**GX_VALUE**</span><span class="sxs-lookup"><span data-stu-id="721de-149">**GX_VALUE**</span></span>        | <span data-ttu-id="721de-150">Tipo assinado de 16 ou 32 bits.</span><span class="sxs-lookup"><span data-stu-id="721de-150">16 or 32 bit signed type.</span></span> <span data-ttu-id="721de-151">Definido como necessário para o melhor desempenho no sistema alvo.</span><span class="sxs-lookup"><span data-stu-id="721de-151">Defined as needed for best performance on the target system.</span></span>                                |
| <span data-ttu-id="721de-152">**GX_FIXED_VAL**</span><span class="sxs-lookup"><span data-stu-id="721de-152">**GX_FIXED_VAL**</span></span>   | <span data-ttu-id="721de-153">Tipo de dados numéricos de ponto fixo.</span><span class="sxs-lookup"><span data-stu-id="721de-153">Fixed point numeric data type.</span></span>                                                                                        |
| <span data-ttu-id="721de-154">**GX_RESOURCE_ID**</span><span class="sxs-lookup"><span data-stu-id="721de-154">**GX_RESOURCE_ID**</span></span> | <span data-ttu-id="721de-155">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="721de-155">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="721de-156">**GX_COLOR**</span><span class="sxs-lookup"><span data-stu-id="721de-156">**GX_COLOR**</span></span>        | <span data-ttu-id="721de-157">Tipo longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="721de-157">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="721de-158">**GX_STRING**</span><span class="sxs-lookup"><span data-stu-id="721de-158">**GX_STRING**</span></span>       | <span data-ttu-id="721de-159">Estrutura que contém \* GX_CHAR gx_string_ptr e gx_string_length UINT.</span><span class="sxs-lookup"><span data-stu-id="721de-159">Structure containing GX_CHAR \*gx_string_ptr and UINT gx_string_length.</span></span>                                          |
| <span data-ttu-id="721de-160">**GX_POINT**</span><span class="sxs-lookup"><span data-stu-id="721de-160">**GX_POINT**</span></span>        | <span data-ttu-id="721de-161">Estrutura que contém gx_point_x e gx_point_y.</span><span class="sxs-lookup"><span data-stu-id="721de-161">Structure containing gx_point_x and gx_point_y.</span></span>                                                                   |
| <span data-ttu-id="721de-162">**GX_RECTANGLE**</span><span class="sxs-lookup"><span data-stu-id="721de-162">**GX_RECTANGLE**</span></span>    | <span data-ttu-id="721de-163">Estrutura que contém campos de gx_rectangle_left, gx_rectangle_top, gx_rectangle_right e gx_rectangle_bottom.</span><span class="sxs-lookup"><span data-stu-id="721de-163">Structure containing gx_rectangle_left, gx_rectangle_top, gx_rectangle_right, and gx_rectangle_bottom fields.</span></span> |
| <span data-ttu-id="721de-164">**GX_GLYPH**</span><span class="sxs-lookup"><span data-stu-id="721de-164">**GX_GLYPH**</span></span>        | <span data-ttu-id="721de-165">Estrutura que contém métricas de glifo.</span><span class="sxs-lookup"><span data-stu-id="721de-165">Structure containing glyph metrics.</span></span>                                                                                   |
| <span data-ttu-id="721de-166">**GX_FONT**</span><span class="sxs-lookup"><span data-stu-id="721de-166">**GX_FONT**</span></span>         | <span data-ttu-id="721de-167">Estrutura que contém métricas de fonte.</span><span class="sxs-lookup"><span data-stu-id="721de-167">Structure containing font metrics.</span></span>                                                                                    |
| <span data-ttu-id="721de-168">**GX_BRUSH**</span><span class="sxs-lookup"><span data-stu-id="721de-168">**GX_BRUSH**</span></span>        | <span data-ttu-id="721de-169">Estrutura que contém métricas de pincel.</span><span class="sxs-lookup"><span data-stu-id="721de-169">Structure containing brush metrics.</span></span>                                                                               |
<span data-ttu-id="721de-170">**GX_PIXELMAP**</span><span class="sxs-lookup"><span data-stu-id="721de-170">**GX_PIXELMAP**</span></span>       | <span data-ttu-id="721de-171">Estrutura que contém métricas de pixelmap.</span><span class="sxs-lookup"><span data-stu-id="721de-171">Structure containing pixelmap metrics.</span></span>

<span data-ttu-id="721de-172">Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="721de-172">Additional data types are used within the Azure RTOS GUIX source.</span></span> <span data-ttu-id="721de-173">Estão localizados nos ficheiros ***tx_port.h_** ou _ *_gx_port.h*_*</span><span class="sxs-lookup"><span data-stu-id="721de-173">They are located in either the ***tx_port.h** _ or _ *_gx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="721de-174">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="721de-174">Customer Support Center</span></span>

<span data-ttu-id="721de-175">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="721de-175">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="721de-176">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="721de-176">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="721de-177">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="721de-177">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="721de-178">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS GUIX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="721de-178">A detailed description of any changes to the application and/or Azure RTOS GUIX that preceded the problem.</span></span>

3. <span data-ttu-id="721de-179">O conteúdo das cordas _tx_version_id e _gx_version_id encontradas nos ficheiros \***tx_port.h**_ e _ *_gx_port.h*_\* da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="721de-179">The contents of the _tx_version_id and _gx_version_id strings found in the \***tx_port.h**_ and _ *_gx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="721de-180">Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="721de-180">These strings will provide us valuable Information regarding your run-time environment.</span></span>

4. <span data-ttu-id="721de-181">O conteúdo em RAM das seguintes variáveis ULONG:</span><span class="sxs-lookup"><span data-stu-id="721de-181">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="721de-182">**_tx_build_options** **_gx_system_build_options**</span><span class="sxs-lookup"><span data-stu-id="721de-182">**_tx_build_options** **_gx_system_build_options**</span></span>

    <span data-ttu-id="721de-183">Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS GUIX foram construídas.</span><span class="sxs-lookup"><span data-stu-id="721de-183">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS GUIX libraries were built.</span></span>

5. <span data-ttu-id="721de-184">O conteúdo em RAM das seguintes variáveis ULONG:</span><span class="sxs-lookup"><span data-stu-id="721de-184">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="721de-185">**_gx_system_last_error** **_gx_system_error_count**</span><span class="sxs-lookup"><span data-stu-id="721de-185">**_gx_system_last_error** **_gx_system_error_count**</span></span>

    <span data-ttu-id="721de-186">Estas variáveis acompanham os erros internos do sistema no Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="721de-186">These variables keep track of internal system errors in Azure RTOS GUIX.</span></span> <span data-ttu-id="721de-187">Se o _gx_system_error_count for maior do que um, por favor, desaponte um ponto de rutura na revolução da função na função _gx_system_error_process e forneça o valor de _gx_system_last_error neste ponto.</span><span class="sxs-lookup"><span data-stu-id="721de-187">If the _gx_system_error_count is greater than one, please set a breakpoint on the function return in the _gx_system_error_process function and provide the value of _gx_system_last_error at this point.</span></span> <span data-ttu-id="721de-188">Isto irá produzir o primeiro erro interno do sistema Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="721de-188">This will yield the first internal Azure RTOS GUIX system error.</span></span>

6. <span data-ttu-id="721de-189">Um tampão de vestígio capturado imediatamente após o problema ter sido detetado.</span><span class="sxs-lookup"><span data-stu-id="721de-189">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="721de-190">Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS GUIX com TX_ENABLE_EVENT_TRACE e chamando tx_trace_enable com a informação do tampão de traços.</span><span class="sxs-lookup"><span data-stu-id="721de-190">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS GUIX libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>

7. <span data-ttu-id="721de-191">O projeto Azure RTOS GUIX Studio que está a utilizar, se aplicável, ou no mínimo um pequeno projeto suficiente para demonstrar a deficiência que está a reportar.</span><span class="sxs-lookup"><span data-stu-id="721de-191">The Azure RTOS GUIX Studio project you are using, if applicable, or at a minimum a small project sufficient to demonstrate the deficiency you are reporting.</span></span>
