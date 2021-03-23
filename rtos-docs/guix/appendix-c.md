---
title: Apêndice C - GUIX Widget Styles
description: Saiba mais sobre os estilos widget GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827278"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="d27a2-103">Apêndice C - GUIX Widget Styles</span><span class="sxs-lookup"><span data-stu-id="d27a2-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="d27a2-104">__***Estilos Gerais (Usados com a maioria dos tipos de widget):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="d27a2-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="d27a2-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="d27a2-106">Valor: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="d27a2-107">Descrição: Use este estilo para desenhar um widget sem fronteira.</span><span class="sxs-lookup"><span data-stu-id="d27a2-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="d27a2-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="d27a2-109">Valor: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="d27a2-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="d27a2-110">Descrição: Desenhe widget com uma borda elevada.</span><span class="sxs-lookup"><span data-stu-id="d27a2-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="d27a2-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="d27a2-112">Valor: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="d27a2-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="d27a2-113">Descrição: Desenhe widget com uma borda embutida.</span><span class="sxs-lookup"><span data-stu-id="d27a2-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="d27a2-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="d27a2-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="d27a2-115">Valor: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="d27a2-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="d27a2-116">Descrição: Desenhe uma borda de largura de um pixel.</span><span class="sxs-lookup"><span data-stu-id="d27a2-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="d27a2-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="d27a2-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="d27a2-118">Valor: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="d27a2-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="d27a2-119">Descrição: Desenhe widget com uma borda grossa.</span><span class="sxs-lookup"><span data-stu-id="d27a2-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="d27a2-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="d27a2-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="d27a2-121">Valor: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="d27a2-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="d27a2-122">Descrição: Valor da máscara utilizado para testar apenas os campos de estilo do membro do estilo widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="d27a2-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="d27a2-124">Valor: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="d27a2-125">Descrição: Criar um widget que seja pelo menos parcialmente transparente.</span><span class="sxs-lookup"><span data-stu-id="d27a2-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="d27a2-126">Este estilo deve ser usado quando um widget não se desenha totalmente opaco, incluindo widgets que desenham um pixelmap semi-transparente como o fundo do widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="d27a2-127">Esta bandeira de estilo informa o GUIX que o progenitor do widget deve ser atraído para refrescar a área de fundo do widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="d27a2-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="d27a2-129">Valor: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="d27a2-130">Descrição: Especifique que o widget deve ser desenhado utilizando cores e tipos de letra selecionados.</span><span class="sxs-lookup"><span data-stu-id="d27a2-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="d27a2-131">Diferentes tipos de widgets usam o estilo DRAW_SELECTED de diferentes maneiras para indicar que o widget está atualmente selecionado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="d27a2-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="d27a2-133">Valor: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="d27a2-134">Descrição: Marque o widget conforme ativado, o que permite ao widget aceitar eventos de entrada do utilizador e gerar sinais de saída.</span><span class="sxs-lookup"><span data-stu-id="d27a2-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="d27a2-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="d27a2-136">Valor: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="d27a2-137">Descrição: Indica que a memória do bloco de controlo do widget é atribuída dinamicamente utilizando o serviço gx_system_memory_allocator quando o widget é criado, e a memória do bloco de controlo é libertada se o widget for destruído.</span><span class="sxs-lookup"><span data-stu-id="d27a2-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="d27a2-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="d27a2-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="d27a2-139">Valor: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="d27a2-140">Descrição: Instrui as funções de desenho GUIX a utilizar o valor alfa do widget local ao desenhar o widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="d27a2-141">Esta bandeira é normalmente usada pela lógica interna do GUIX para implementar animações desvanecimento widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="d27a2-142">__***Estilos de alinhamento de texto (estilos aplicados a todos os widgets que desenham texto):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="d27a2-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="d27a2-144">Valor: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="d27a2-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="d27a2-145">Descrição: O texto é desenhado alinhado à esquerda dentro da área do cliente widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="d27a2-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="d27a2-147">Valor: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="d27a2-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="d27a2-148">Descrição: O texto é desenhado alinhado à direita dentro da área do cliente widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="d27a2-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="d27a2-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="d27a2-150">Valor: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="d27a2-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="d27a2-151">Descrição: O texto é desenhado no centro alinhado dentro da área do cliente widget.</span><span class="sxs-lookup"><span data-stu-id="d27a2-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="d27a2-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="d27a2-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="d27a2-153">Valor: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="d27a2-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="d27a2-154">Descrição: Por predefinição, os widgets que desenham texto mantêm apenas um ponteiro para o texto que é transmitido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="d27a2-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="d27a2-155">Para o texto estático definido que é definido dentro da tabela de cordas, não há razão para que o widget faça uma cópia privada do texto atribuído.</span><span class="sxs-lookup"><span data-stu-id="d27a2-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="d27a2-156">No entanto, se o texto atribuído a um widget é criado dinamicamente usando funções como sprint() ou gx_utility_ltoa, então é muitas vezes conveniente dizer ao widget para manter a sua própria cópia privada de qualquer texto atribuído.</span><span class="sxs-lookup"><span data-stu-id="d27a2-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="d27a2-157">Isto permite que a aplicação utilize variáveis automáticas ou temporárias ao definir a cadeia de texto, quando a aplicação seria necessária para definir matrizes de caracteres estáticais para cada widget de texto que está usando texto definido dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="d27a2-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="d27a2-158">Quando esta bandeira de estilo estiver definida, o widget utilizará a função gx_system_memory_allocator para alocar dinamicamente o bloco de memória necessário para segurar uma cópia privada da cadeia atribuída.</span><span class="sxs-lookup"><span data-stu-id="d27a2-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="d27a2-159">Assim, a utilização desta bandeira de estilo baseia-se na aplicação que define funções memory_allocator e memory_deallocator.</span><span class="sxs-lookup"><span data-stu-id="d27a2-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="d27a2-160">GX_STYLE_TEXT_COPY não devem ser apuradas depois de definidas, e fazê-lo provocará resultados imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="d27a2-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="d27a2-161">__***Estilos de botão (aplicar apenas aos tipos de widget de botão GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="d27a2-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="d27a2-163">Valor 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-163">Value 0x00000010</span></span>
  - <span data-ttu-id="d27a2-164">Descrição: Indica que o botão está no estado pressionado ou selecionado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="d27a2-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="d27a2-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="d27a2-166">Valor 0x00000020</span><span class="sxs-lookup"><span data-stu-id="d27a2-166">Value 0x00000020</span></span>
  - <span data-ttu-id="d27a2-167">Descrição: O botão mudará o estado entre pressionado e desinteressado em cada evento de clique.</span><span class="sxs-lookup"><span data-stu-id="d27a2-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="d27a2-168">Este estilo é comumente usado com botões de estilo "checkbox".</span><span class="sxs-lookup"><span data-stu-id="d27a2-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="d27a2-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="d27a2-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="d27a2-170">0x00000040 de valor</span><span class="sxs-lookup"><span data-stu-id="d27a2-170">Value 0x00000040</span></span>
  - <span data-ttu-id="d27a2-171">Descrição: Este estilo indica que o botão será exclusivo e desmarcará quaisquer irmãos de botão quando selecionados.</span><span class="sxs-lookup"><span data-stu-id="d27a2-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="d27a2-172">Este estilo é comumente usado com botões de estilo "botão de rádio".</span><span class="sxs-lookup"><span data-stu-id="d27a2-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="d27a2-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="d27a2-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="d27a2-174">Valor: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="d27a2-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="d27a2-175">Descrição: Indica que o botão gera um evento de clique quando inicialmente pressionado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="d27a2-176">A operação predefinida é gerar um evento de clique quando o botão é libertado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="d27a2-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="d27a2-178">0x00000100 de valor</span><span class="sxs-lookup"><span data-stu-id="d27a2-178">Value 0x00000100</span></span>
  - <span data-ttu-id="d27a2-179">Descrição: Indica que o botão deve enviar repetidos eventos de clique para o progenitor do botão quando o botão é mantido no estado de pressão.</span><span class="sxs-lookup"><span data-stu-id="d27a2-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="d27a2-180">__***Estilos de lista (aplica-se apenas aos tipos de widgets da lista GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="d27a2-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="d27a2-182">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="d27a2-183">Descrição: Reservado</span><span class="sxs-lookup"><span data-stu-id="d27a2-183">Description: Reserved</span></span>

<span data-ttu-id="d27a2-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="d27a2-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="d27a2-185">Valor 0x00000020</span><span class="sxs-lookup"><span data-stu-id="d27a2-185">Value 0x00000020</span></span>
  - <span data-ttu-id="d27a2-186">Descrição: A lista de crianças embrulha do início ao fim quando a lista é arrastada ou deslocada para além do índice de lista inicial ou final.</span><span class="sxs-lookup"><span data-stu-id="d27a2-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="d27a2-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="d27a2-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="d27a2-188">Valor: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="d27a2-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="d27a2-189">Descrição: Reservado</span><span class="sxs-lookup"><span data-stu-id="d27a2-189">Description: Reserved</span></span>

<span data-ttu-id="d27a2-190">__***Estilos de botão pixelmap e botão de ícone:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="d27a2-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="d27a2-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="d27a2-192">Valor: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="d27a2-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="d27a2-193">Descrição: O mapa de pixels do botão deve estar alinhado no centro dentro do limite do botão no eixo horizontal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="d27a2-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="d27a2-195">Valor: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="d27a2-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="d27a2-196">Descrição: O mapa de pixels do botão deve ser deixado alinhado dentro do limite do botão no eixo horizontal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="d27a2-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="d27a2-198">Valor 0x00040000</span><span class="sxs-lookup"><span data-stu-id="d27a2-198">Value 0x00040000</span></span>
  - <span data-ttu-id="d27a2-199">Descrição: O mapa de pixels do botão deve estar alinhado dentro do limite do botão no eixo horizontal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="d27a2-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="d27a2-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="d27a2-201">Valor 0x00080000</span><span class="sxs-lookup"><span data-stu-id="d27a2-201">Value 0x00080000</span></span>
  - <span data-ttu-id="d27a2-202">Descrição: O mapa de pixels do botão deve estar alinhado no centro dentro do limite do botão no eixo vertical.</span><span class="sxs-lookup"><span data-stu-id="d27a2-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="d27a2-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="d27a2-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="d27a2-204">Valor: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="d27a2-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="d27a2-205">Descrição: O mapa de pixels do botão deve estar alinhado no topo do limite do botão no eixo vertical.</span><span class="sxs-lookup"><span data-stu-id="d27a2-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="d27a2-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="d27a2-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="d27a2-207">Valor: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="d27a2-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="d27a2-208">Descrição: O mapa de pixels do botão deve estar alinhado no fundo dentro do limite do botão no eixo horizontal vertical.</span><span class="sxs-lookup"><span data-stu-id="d27a2-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="d27a2-209">__***Estilos de slider (Appy apenas para GX_SLIDER e tipos de widget derivado):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="d27a2-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="d27a2-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="d27a2-211">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="d27a2-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="d27a2-212">Descrição: Este estilo deve ser incluído para que o deslizador desenhe o indicador da agulha.</span><span class="sxs-lookup"><span data-stu-id="d27a2-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="d27a2-213">Este estilo pode ser desativado se a aplicação quiser desativar a agulha de slider ou desenhar um indicador de agulha personalizado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="d27a2-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="d27a2-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="d27a2-215">Valor: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="d27a2-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="d27a2-216">Descrição: O widget de slider fará desenho de software de linhas de marca de carrapato tracejadas quando este estilo estiver ativado.</span><span class="sxs-lookup"><span data-stu-id="d27a2-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="d27a2-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="d27a2-218">valor 0x00000800</span><span class="sxs-lookup"><span data-stu-id="d27a2-218">Value 0x00000800</span></span>
  - <span data-ttu-id="d27a2-219">Descrição: Desata esta bandeira de estilo para criar um slider vertical e limpe esta bandeira de estilo para criar um slider horizontal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="d27a2-220">__***Estilos Sprite (Aplica-se apenas a GX_SPRITE tipos de widget):***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="d27a2-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="d27a2-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="d27a2-222">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="d27a2-223">Descrição: Indica que a animação sprite funcionará automaticamente quando o widget sprite recebeu o evento GX_EVENT_SHOW.</span><span class="sxs-lookup"><span data-stu-id="d27a2-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="d27a2-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="d27a2-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="d27a2-225">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="d27a2-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="d27a2-226">Descrição: Com este estilo, o widget sprite irá continuamente circular através de quadros de animação sprite até que o sprite seja parado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="d27a2-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="d27a2-227">__***Estilos de slider Pixelmap:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="d27a2-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="d27a2-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="d27a2-229">0x00001000 de valor</span><span class="sxs-lookup"><span data-stu-id="d27a2-229">Value 0x00001000</span></span>
  - <span data-ttu-id="d27a2-230">Descrição: A imagem de fundo deslizante é em azulejo para encher o retângulo de delimitação do sprite.</span><span class="sxs-lookup"><span data-stu-id="d27a2-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="d27a2-231">Isto permite que uma pequena imagem de risca vertical ou horizontal seja usada para preencher o fundo do slider.</span><span class="sxs-lookup"><span data-stu-id="d27a2-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="d27a2-232">__***Estilos adicionais de barras de progresso:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="d27a2-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="d27a2-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="d27a2-234">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="d27a2-235">Descrição: Quando este estilo é definido, a barra de progresso irá desenhar o valor da barra em percentagem em vez de um valor bruto.</span><span class="sxs-lookup"><span data-stu-id="d27a2-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="d27a2-236">O texto está centrado na barra de progresso que limita o retângulo.</span><span class="sxs-lookup"><span data-stu-id="d27a2-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="d27a2-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="d27a2-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="d27a2-238">Valor: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="d27a2-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="d27a2-239">Descrição: Desenhe o valor atual da barra de progresso como texto decimal centrado na barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="d27a2-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="d27a2-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="d27a2-241">Valor: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="d27a2-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="d27a2-242">Descrição: Indique que o progresso está orientado verticalmente.</span><span class="sxs-lookup"><span data-stu-id="d27a2-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="d27a2-243">O padrão é orientação horizontal.</span><span class="sxs-lookup"><span data-stu-id="d27a2-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="d27a2-244">**GX_STYLE_PROGRESS_SEGMENT_FILL:**</span><span class="sxs-lookup"><span data-stu-id="d27a2-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="d27a2-245">**Valor**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="d27a2-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="d27a2-246">Descrição: O valor da barra de progresso é indicado com retângulos cheios segmentados, em vez de um enchimento sólido.</span><span class="sxs-lookup"><span data-stu-id="d27a2-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="d27a2-247">__***Estilos adicionais de barras de progresso radial:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="d27a2-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="d27a2-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="d27a2-249">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="d27a2-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="d27a2-250">Descrição: Desenhe a barra de progresso radial utilizando estilos de escova anti-aliased.</span><span class="sxs-lookup"><span data-stu-id="d27a2-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="d27a2-251">Isto requer mais largura de banda cpu, mas também produz uma aparência melhor.</span><span class="sxs-lookup"><span data-stu-id="d27a2-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="d27a2-252">Para alvos de CPU de menor desempenho, limpar esta bandeira de estilo resultará numa velocidade de desenho mais rápida.</span><span class="sxs-lookup"><span data-stu-id="d27a2-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="d27a2-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="d27a2-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="d27a2-254">Valor: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="d27a2-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="d27a2-255">Descrição: Utilize um estilo de escova final de linha redonda ao desenhar o arco da barra de progresso radial. O padrão é uma linha quadrada.</span><span class="sxs-lookup"><span data-stu-id="d27a2-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="d27a2-256">__***Estilos de entrada de texto adicionais:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="d27a2-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="d27a2-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="d27a2-258">Valor: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="d27a2-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="d27a2-259">Descrição: O cursor widget de entrada de texto piscará ligado e desligado em vez de ser estável.</span><span class="sxs-lookup"><span data-stu-id="d27a2-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="d27a2-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="d27a2-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="d27a2-261">Valor: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="d27a2-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="d27a2-262">Descrição.</span><span class="sxs-lookup"><span data-stu-id="d27a2-262">Description.</span></span> <span data-ttu-id="d27a2-263">Normalmente, o cursor widget de entrada de texto só é apresentado quando o widget possui o foco de entrada.</span><span class="sxs-lookup"><span data-stu-id="d27a2-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="d27a2-264">Esta bandeira de estilo tornará o cursor sempre visível independentemente do foco de entrada.</span><span class="sxs-lookup"><span data-stu-id="d27a2-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="d27a2-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="d27a2-266">Valor: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="d27a2-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="d27a2-267">Descrição: Com esta bandeira de estilo definir o evento GX_EVENT_TEXT_EDITED cada vez que o evento key down é recebido pelo widget de entrada de texto.</span><span class="sxs-lookup"><span data-stu-id="d27a2-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="d27a2-268">__***Estilos de janela adicionais:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="d27a2-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="d27a2-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="d27a2-270">Valor: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="d27a2-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="d27a2-271">Descrição: A janela azulejorá qualquer imagem de papel de parede atribuída para encher o retângulo do cliente da janela.</span><span class="sxs-lookup"><span data-stu-id="d27a2-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="d27a2-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="d27a2-273">Valor: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="d27a2-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="d27a2-274">Descrição: Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="d27a2-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="d27a2-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="d27a2-276">Valor: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="d27a2-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="d27a2-277">Descrição: Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="d27a2-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="d27a2-278">__***Estilos de menu adicionais:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="d27a2-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="d27a2-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="d27a2-280">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="d27a2-281">Descrição: O widget do menu de acordeão está inicialmente em estado expandido.</span><span class="sxs-lookup"><span data-stu-id="d27a2-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="d27a2-282">__***Estilos adicionais de vista de árvores:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="d27a2-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="d27a2-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="d27a2-284">Valor: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="d27a2-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="d27a2-285">Descrição: O widget da vista da árvore deve desenhar linhas do ícone do nó para o nó de árvore de raiz.</span><span class="sxs-lookup"><span data-stu-id="d27a2-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="d27a2-286">__***Estilos adicionais de barra de deslocação:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="d27a2-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="d27a2-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="d27a2-288">Valor: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="d27a2-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="d27a2-289">Descrição: Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="d27a2-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="d27a2-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="d27a2-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="d27a2-291">Valor: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="d27a2-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="d27a2-292">Descrição: A largura do polegar da barra de deslocação (para uma barra de deslocação horizontal) ou a altura (para uma barra de deslocação vertical) são calculadas com base na relação entre a área visível da janela dos pais e a gama de barras de deslocação de min e max.</span><span class="sxs-lookup"><span data-stu-id="d27a2-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="d27a2-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="d27a2-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="d27a2-294">Valor: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="d27a2-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="d27a2-295">Descrição: A barra de deslocação cria e fixa botões em cada extremidade da região da barra de deslocação.</span><span class="sxs-lookup"><span data-stu-id="d27a2-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="d27a2-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="d27a2-297">Valor: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="d27a2-298">Descrição: A barra de deslocação está orientada verticalmente.</span><span class="sxs-lookup"><span data-stu-id="d27a2-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="d27a2-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="d27a2-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="d27a2-300">Valor: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="d27a2-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="d27a2-301">Descrição: A barra de deslocação está orientada horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="d27a2-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="d27a2-302">__***Estilos de roda de deslocação de texto:***__</span><span class="sxs-lookup"><span data-stu-id="d27a2-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="d27a2-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="d27a2-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="d27a2-304">Valor: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="d27a2-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="d27a2-305">Descrição: A roda de deslocação utiliza um algoritmo Sinusoidal para fazer com que a roda de deslocação pareça ter uma forma arredondada.</span><span class="sxs-lookup"><span data-stu-id="d27a2-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="d27a2-306">Esta bandeira de estilo pode adicionar uma sobrecarga significativa ao desempenho do widget da roda de deslocação, mas também pode dar à roda uma aparência realista 3D.</span><span class="sxs-lookup"><span data-stu-id="d27a2-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>