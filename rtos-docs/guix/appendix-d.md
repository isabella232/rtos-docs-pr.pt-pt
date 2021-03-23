---
title: Apêndice D - GuiX Brush, Lona e Atributos Gradiente
description: Saiba mais sobre os atributos guix, lona e gradiente.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827277"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="64ecd-103">Apêndice D - GuiX Brush, Lona e Atributos Gradiente</span><span class="sxs-lookup"><span data-stu-id="64ecd-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="64ecd-104">__**Estilos de escova:**__</span><span class="sxs-lookup"><span data-stu-id="64ecd-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="64ecd-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="64ecd-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="64ecd-106">Valor: 0x0000</span><span class="sxs-lookup"><span data-stu-id="64ecd-106">Value: 0x0000</span></span>
- <span data-ttu-id="64ecd-107">Descrição: Este estilo de escova aplica-se a funções de desenho de formas como gx_canvas_rectangle_draw ou gx_canvas_polygon_draw.</span><span class="sxs-lookup"><span data-stu-id="64ecd-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="64ecd-108">Este estilo indica que a forma deve ser delineada, além de ser opcionalmente preenchido.</span><span class="sxs-lookup"><span data-stu-id="64ecd-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="64ecd-109">Se o estilo GX_BRUSH_OUTLINE estiver definido e o GX_BRSUH_SOLID_FILL estiver limpo, a forma é apenas delineada.</span><span class="sxs-lookup"><span data-stu-id="64ecd-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="64ecd-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="64ecd-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="64ecd-111">Valor: 0x0001</span><span class="sxs-lookup"><span data-stu-id="64ecd-111">Value: 0x0001</span></span>
- <span data-ttu-id="64ecd-112">Descrição: Este estilo de escova aplica-se às funções de desenho de forma, e indica que a forma solicitada deve ser preenchida com uma cor sólida utilizando a cor de preenchimento da escova atual.</span><span class="sxs-lookup"><span data-stu-id="64ecd-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="64ecd-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="64ecd-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="64ecd-114">Valor: 0x0002</span><span class="sxs-lookup"><span data-stu-id="64ecd-114">Value: 0x0002</span></span>
- <span data-ttu-id="64ecd-115">Descrição: Este estilo de escova aplica-se às funções de desenho de forma, e indica que a forma solicitada deve ser preenchida com o pixelmap de escova atual.</span><span class="sxs-lookup"><span data-stu-id="64ecd-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="64ecd-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="64ecd-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="64ecd-117">Valor: 0x0004</span><span class="sxs-lookup"><span data-stu-id="64ecd-117">Value: 0x0004</span></span>
- <span data-ttu-id="64ecd-118">Descrição: Este estilo de escova aplica-se a todos os contornos de desenho e forma de linha.</span><span class="sxs-lookup"><span data-stu-id="64ecd-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="64ecd-119">Se esta bandeira for definida, linhas e contornos estão a desenhar com os algoritmos de desenho anti-aliased mais precisos, mas também mais demorados.</span><span class="sxs-lookup"><span data-stu-id="64ecd-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="64ecd-120">Esta bandeira de estilo é usada apenas para profundidades de cores de 16 bpp e mais alta.</span><span class="sxs-lookup"><span data-stu-id="64ecd-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="64ecd-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="64ecd-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="64ecd-122">Valor: 0x0008</span><span class="sxs-lookup"><span data-stu-id="64ecd-122">Value: 0x0008</span></span>
- <span data-ttu-id="64ecd-123">Descrição: Esta bandeira aplica-se ao desenho de texto e indica que o texto posterior desenhado deve ser sublinhado.</span><span class="sxs-lookup"><span data-stu-id="64ecd-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="64ecd-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="64ecd-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="64ecd-125">Valor: 0x0010</span><span class="sxs-lookup"><span data-stu-id="64ecd-125">Value: 0x0010</span></span>
- <span data-ttu-id="64ecd-126">Descrição: Esta bandeira aplica-se ao desenho de linhas e indica que as extremidades da linha são desenhadas com uma forma redonda ou circular, em vez da forma quadrada padrão.</span><span class="sxs-lookup"><span data-stu-id="64ecd-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="64ecd-127">__**Bandeiras de lona:**__</span><span class="sxs-lookup"><span data-stu-id="64ecd-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="64ecd-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="64ecd-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="64ecd-129">Valor: 0x01</span><span class="sxs-lookup"><span data-stu-id="64ecd-129">Value: 0x01</span></span>
- <span data-ttu-id="64ecd-130">Descrição: Uma tela de memória que é usada para desenhar fora do ecrã.</span><span class="sxs-lookup"><span data-stu-id="64ecd-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="64ecd-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="64ecd-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="64ecd-132">Valor: 0x02</span><span class="sxs-lookup"><span data-stu-id="64ecd-132">Value: 0x02</span></span>
- <span data-ttu-id="64ecd-133">Descrição: Uma tela que se despedace automaticamente para o visor ativo, quer como parte do processo de construção composta, quer como parte do funcionamento do tampão para arquiteturas de tela única.</span><span class="sxs-lookup"><span data-stu-id="64ecd-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="64ecd-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="64ecd-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="64ecd-135">Valor: 0x04</span><span class="sxs-lookup"><span data-stu-id="64ecd-135">Value: 0x04</span></span>
- <span data-ttu-id="64ecd-136">Descrição: Esta bandeira pode ser usada para ligar e sair de uma tela, sem perder o conteúdo de desenho de tela.</span><span class="sxs-lookup"><span data-stu-id="64ecd-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="64ecd-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="64ecd-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="64ecd-138">Valor: 0x08</span><span class="sxs-lookup"><span data-stu-id="64ecd-138">Value: 0x08</span></span>
- <span data-ttu-id="64ecd-139">Descrição: Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="64ecd-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="64ecd-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="64ecd-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="64ecd-141">Valor: 0x20</span><span class="sxs-lookup"><span data-stu-id="64ecd-141">Value: 0x20</span></span>
- <span data-ttu-id="64ecd-142">Descrição: Esta bandeira é utilizada pela aplicação ao configurar um sistema de múltiplas telas que compôs várias telas geridas na tela composta, e o composto é o acionado para o tampão de quadro de hardware.</span><span class="sxs-lookup"><span data-stu-id="64ecd-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="64ecd-143">__**Tipos de gradiente:**__</span><span class="sxs-lookup"><span data-stu-id="64ecd-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="64ecd-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="64ecd-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="64ecd-145">Valor: 0x01</span><span class="sxs-lookup"><span data-stu-id="64ecd-145">Value: 0x01</span></span>
- <span data-ttu-id="64ecd-146">Descrição: Cria um gradiente alfamap vertical.</span><span class="sxs-lookup"><span data-stu-id="64ecd-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="64ecd-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="64ecd-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="64ecd-148">Valor: 0x02</span><span class="sxs-lookup"><span data-stu-id="64ecd-148">Value: 0x02</span></span>
- <span data-ttu-id="64ecd-149">Descrição: Creats um gradiente de estilo de mapa alfa.</span><span class="sxs-lookup"><span data-stu-id="64ecd-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="64ecd-150">Este é atualmente o único estilo gradiente suportado.</span><span class="sxs-lookup"><span data-stu-id="64ecd-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="64ecd-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="64ecd-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="64ecd-152">Valor: 0x04</span><span class="sxs-lookup"><span data-stu-id="64ecd-152">Value: 0x04</span></span>
- <span data-ttu-id="64ecd-153">Descrição: Esta bandeira indica que o gradiente deve atingir o pico no centro da gama largura/altura e voltar ao valor inicial à medida que atinge a borda direita/inferior.</span><span class="sxs-lookup"><span data-stu-id="64ecd-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="64ecd-154">Sem esta bandeira de estilo, o gradiente será um gradiente linear de cima para baixo ou da esquerda para a direita, dependendo da bandeira GX_GRADIENT_TYPE_VERTICAL.</span><span class="sxs-lookup"><span data-stu-id="64ecd-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>