---
title: Apêndice I - ESTRUTURAS DE Informação GUIX
description: Saiba mais sobre as estruturas de informação guix.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc7775cdde8f1aa89ca650561713f54ac6c069eb
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550223"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="70720-103">Apêndice I - ESTRUTURAS DE Informação GUIX</span><span class="sxs-lookup"><span data-stu-id="70720-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="70720-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-105">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| <span data-ttu-id="70720-106">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-106">Members</span></span> | <span data-ttu-id="70720-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-107">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="70720-108">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="70720-108">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="70720-109">Texto para reordenamento</span><span class="sxs-lookup"><span data-stu-id="70720-109">Text for reordering</span></span> |
| <span data-ttu-id="70720-110">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="70720-110">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="70720-111">Fonte usada para exibir texto, defini-lo para GX_NULL se não for necessário quebrar a linha</span><span class="sxs-lookup"><span data-stu-id="70720-111">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="70720-112">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="70720-112">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="70720-113">Largura disponível para exibição, desalinhá-la para -1 se não for necessária rutura de linha</span><span class="sxs-lookup"><span data-stu-id="70720-113">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="70720-114">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-114">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-115">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-115">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| <span data-ttu-id="70720-116">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-116">Members</span></span> | <span data-ttu-id="70720-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-117">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="70720-118">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="70720-118">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="70720-119">Ponteiro para a matriz de texto bidi reordenado</span><span class="sxs-lookup"><span data-stu-id="70720-119">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="70720-120">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="70720-120">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="70720-121">Linhas totais de texto bidi resolvido para um parágrafo</span><span class="sxs-lookup"><span data-stu-id="70720-121">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="70720-122">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="70720-122">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="70720-123">Informações de texto de bidi resolvidas para o parágrafo seguinte</span><span class="sxs-lookup"><span data-stu-id="70720-123">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="70720-124">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-124">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="70720-125">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-125">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```

| <span data-ttu-id="70720-126">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-126">Members</span></span> | <span data-ttu-id="70720-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-127">Description</span></span> |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="70720-128">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="70720-128">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="70720-129">Passos totais que a agulha irá percorrer ao mover-se do ângulo da agulha atual para um ângulo de agulha recém-atribuído</span><span class="sxs-lookup"><span data-stu-id="70720-129">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="70720-130">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="70720-130">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="70720-131">O número de relógio GUIX assinala-se entre etapas de animação</span><span class="sxs-lookup"><span data-stu-id="70720-131">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="70720-132">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="70720-132">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="70720-133">A distância da esquerda do widget de bitola para o centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="70720-133">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="70720-134">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="70720-134">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="70720-135">A distância do topo do widget de bitola até ao centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="70720-135">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="70720-136">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="70720-136">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="70720-137">A distância da esquerda da imagem da agulha para o centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="70720-137">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="70720-138">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="70720-138">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="70720-139">A distância do topo da imagem da agulha ao centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="70720-139">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="70720-140">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-140">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="70720-141">Identificação de recursos do mapa pixel que será utilizado para desenhar a agulha de bitola.</span><span class="sxs-lookup"><span data-stu-id="70720-141">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="70720-142">Esta imagem será girada conforme necessário pelo widget de bitola para exibir a agulha de bitola em qualquer posição</span><span class="sxs-lookup"><span data-stu-id="70720-142">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="70720-143">O diagrama abaixo ilustra os xpos, ypos e xcor, coordenadas ycor:</span><span class="sxs-lookup"><span data-stu-id="70720-143">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagrama das coordenadas Needle Y e X](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="70720-145">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-145">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="70720-146">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-146">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

| <span data-ttu-id="70720-147">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-147">Members</span></span> | <span data-ttu-id="70720-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-148">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="70720-149">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="70720-149">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="70720-150">O valor mínimo de dados, que é usado para calcular a escala</span><span class="sxs-lookup"><span data-stu-id="70720-150">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="70720-151">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="70720-151">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="70720-152">O valor máximo dos dados, que é usado para calcular a escala</span><span class="sxs-lookup"><span data-stu-id="70720-152">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="70720-153">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="70720-153">**gx_line_chart_data**</span></span>             | <span data-ttu-id="70720-154">Ponteiro para uma variedade de valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="70720-154">Pointer to an array of integer values.</span></span> <span data-ttu-id="70720-155">Estes são os valores inteiros traçados pelo widget gráfico de linha</span><span class="sxs-lookup"><span data-stu-id="70720-155">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="70720-156">**gx_line_ <side> _margin**</span><span class="sxs-lookup"><span data-stu-id="70720-156">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="70720-157">A compensação da janela do gráfico está ligada à área real de renderização do gráfico.</span><span class="sxs-lookup"><span data-stu-id="70720-157">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="70720-158">O eixo do gráfico e a linha de dados estão sempre traçados dentro deste limite interno, o que permite que a aplicação desenhe etiquetas e outras informações dentro da janela do gráfico, mas fora da área de gráfico de carvão</span><span class="sxs-lookup"><span data-stu-id="70720-158">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="70720-159">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="70720-159">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="70720-160">O número de valores de dados que podem estar presentes.</span><span class="sxs-lookup"><span data-stu-id="70720-160">The number of data values which may be present.</span></span> <span data-ttu-id="70720-161">Este parâmetro é utilizado para calcular a escala ou intervalo do eixo x para a trama de pontos de dados.</span><span class="sxs-lookup"><span data-stu-id="70720-161">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="70720-162">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="70720-162">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="70720-163">O número de valores de dados que realmente apresentam na matriz de dados.</span><span class="sxs-lookup"><span data-stu-id="70720-163">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="70720-164">Um gráfico de linha pode ser dimensionado para desenhar um máximo de 100 valores (por exemplo), mas em qualquer atualização particular um número menor de valores de dados pode realmente estar presente.</span><span class="sxs-lookup"><span data-stu-id="70720-164">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="70720-165">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="70720-165">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="70720-166">Largura da linha utilizada para desenhar o eixo horizontal e vertical</span><span class="sxs-lookup"><span data-stu-id="70720-166">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="70720-167">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="70720-167">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="70720-168">Largura da linha de dados traçada</span><span class="sxs-lookup"><span data-stu-id="70720-168">Width of the plotted data line</span></span> |
| <span data-ttu-id="70720-169">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="70720-169">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="70720-170">ID de recursos da cor usada para desenhar as linhas do eixo</span><span class="sxs-lookup"><span data-stu-id="70720-170">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="70720-171">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="70720-171">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="70720-172">ID de recursos da cor usada para desenhar a linha de dados do gráfico</span><span class="sxs-lookup"><span data-stu-id="70720-172">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="70720-173">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-173">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-174">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-174">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| <span data-ttu-id="70720-175">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-175">Members</span></span> | <span data-ttu-id="70720-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-176">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="70720-177">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="70720-177">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="70720-178">ID de recurso da imagem do rato</span><span class="sxs-lookup"><span data-stu-id="70720-178">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="70720-179">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="70720-179">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="70720-180">A compensação da esquerda da imagem do rato para o hotspot de imagem do rato</span><span class="sxs-lookup"><span data-stu-id="70720-180">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="70720-181">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="70720-181">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="70720-182">A compensação do topo da imagem do rato para o hotspot de imagem do rato</span><span class="sxs-lookup"><span data-stu-id="70720-182">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="70720-183">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="70720-183">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-184">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-184">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| <span data-ttu-id="70720-185">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-185">Members</span></span> | <span data-ttu-id="70720-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-186">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="70720-187">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="70720-187">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="70720-188">A distância mínima de arrasto por temporizador GUIX para desencadear um evento FLICK.</span><span class="sxs-lookup"><span data-stu-id="70720-188">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="70720-189">Ligue GX_FIXED_VAL_MAKE para fazer um valor de tipo de dados de ponto fixo</span><span class="sxs-lookup"><span data-stu-id="70720-189">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="70720-190">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="70720-190">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="70720-191">A velocidade máxima de arrasto no temporizador GUIX assinala-se para desencadear um evento FLICK</span><span class="sxs-lookup"><span data-stu-id="70720-191">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="70720-192">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-192">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-193">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-193">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| <span data-ttu-id="70720-194">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-194">Members</span></span> | <span data-ttu-id="70720-195">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-195">Description</span></span> |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="70720-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="70720-197">Identificação de recursos do mapa de pixels para encher o fundo antes da agulha.</span><span class="sxs-lookup"><span data-stu-id="70720-197">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="70720-198">Se o pixelmap de fundo superior não estiver definido, é usado para encher o fundo antes e depois da agulha</span><span class="sxs-lookup"><span data-stu-id="70720-198">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="70720-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="70720-200">ID de recurso do mapa de pixels para o enchimento de fundo após a agulha</span><span class="sxs-lookup"><span data-stu-id="70720-200">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="70720-201">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-201">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="70720-202">ID de recurso do pixelmap da agulha</span><span class="sxs-lookup"><span data-stu-id="70720-202">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="70720-203">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-203">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-204">**Definição**</span><span class="sxs-lookup"><span data-stu-id="70720-204">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="70720-205">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-205">Members</span></span> | <span data-ttu-id="70720-206">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-206">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="70720-207">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="70720-207">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="70720-208">Valor mínimo reportado</span><span class="sxs-lookup"><span data-stu-id="70720-208">Minimum reported value</span></span> |
| <span data-ttu-id="70720-209">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="70720-209">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="70720-210">Valor máximo reportado</span><span class="sxs-lookup"><span data-stu-id="70720-210">Maximum reported value</span></span> |
| <span data-ttu-id="70720-211">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="70720-211">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="70720-212">Valor atual</span><span class="sxs-lookup"><span data-stu-id="70720-212">Current value</span></span> |
| <span data-ttu-id="70720-213">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="70720-213">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="70720-214">ID de recurso da fonte, usado para desenhar o valor de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-214">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="70720-215">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-215">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="70720-216">ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-216">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-217">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-217">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="70720-218">ID de recurso da cor do texto quando o widget ganha o foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-218">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-219">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-219">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="70720-220">ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-220">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-221">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-221">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="70720-222">ID de recurso do pixelmap para preenchimento de fundo</span><span class="sxs-lookup"><span data-stu-id="70720-222">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="70720-223">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-223">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="70720-224">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-224">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="70720-225">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-225">Members</span></span> | <span data-ttu-id="70720-226">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-226">Description</span></span> |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="70720-227">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="70720-227">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="70720-228">Posição widget na coordenada x</span><span class="sxs-lookup"><span data-stu-id="70720-228">Widget position in x coordinate</span></span> |
| <span data-ttu-id="70720-229">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="70720-229">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="70720-230">Posição widget na coordenada y</span><span class="sxs-lookup"><span data-stu-id="70720-230">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="70720-231">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="70720-231">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="70720-232">Raio do círculo de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-232">Radius of the progress circle</span></span> |
| <span data-ttu-id="70720-233">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="70720-233">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="70720-234">O valor atual, limitado ao intervalo [-360, 360], indica o delta angular entre a posição da âncora e o ponto final do arco superior. O valor negativo faz com que o arco seja desenhado no sentido dos ponteiros do relógio, a partir da posição de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="70720-234">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="70720-235">O valor positivo faz com que o arco seja desenhado no sentido contrário ao dos ponteiros do relógio, a partir da posição de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="70720-235">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="70720-236">A aplicação deve escalar o valor da palavra real indicada para atribuir um valor angular ao widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-236">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="70720-237">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="70720-237">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="70720-238">Ângulo inicial do arco de progresso superior. O valor é definido em termos de grau inteiro com 0 graus apontando para a direita e 90 graus indicando posição direta.</span><span class="sxs-lookup"><span data-stu-id="70720-238">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="70720-239">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="70720-239">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="70720-240">ID de recursos da fonte utilizada para desenhar o valor de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-240">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="70720-241">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-241">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="70720-242">ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-242">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-243">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-243">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="70720-244">ID de recurso da cor do texto quando widget ganhar foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-244">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-245">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="70720-245">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="70720-246">ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="70720-246">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="70720-247">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="70720-247">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="70720-248">Largura do círculo de menor progresso</span><span class="sxs-lookup"><span data-stu-id="70720-248">Width of the lower progress circle</span></span> |
| <span data-ttu-id="70720-249">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="70720-249">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="70720-250">Largura do arco de progressão superior, o arco superior pode ser mais estreito, o mesmo que, ou mais largo que o círculo inferior</span><span class="sxs-lookup"><span data-stu-id="70720-250">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="70720-251">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="70720-251">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="70720-252">ID de recursos da cor para preencher o círculo de menor progresso</span><span class="sxs-lookup"><span data-stu-id="70720-252">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="70720-253">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="70720-253">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="70720-254">ID de recurso da cor para preencher o arco superior do progresso</span><span class="sxs-lookup"><span data-stu-id="70720-254">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="70720-255">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-255">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-256">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-256">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

| <span data-ttu-id="70720-257">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-257">Members</span></span> | <span data-ttu-id="70720-258">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-258">Description</span></span> |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="70720-259">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="70720-259">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="70720-260">Distância da esquerda do widget deslizante para o centro de rotação da agulha deslizante</span><span class="sxs-lookup"><span data-stu-id="70720-260">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="70720-261">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="70720-261">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="70720-262">Distância do topo do widget de slider para o centro de rotação da agulha deslizante</span><span class="sxs-lookup"><span data-stu-id="70720-262">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="70720-263">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="70720-263">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="70720-264">Raio do círculo de deslizamento radial</span><span class="sxs-lookup"><span data-stu-id="70720-264">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="70720-265">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="70720-265">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="70720-266">Largura da pista de slider radial</span><span class="sxs-lookup"><span data-stu-id="70720-266">Width of radial slider track</span></span> |
| <span data-ttu-id="70720-267">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="70720-267">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="70720-268">Ângulo de deslizamento de corrente</span><span class="sxs-lookup"><span data-stu-id="70720-268">Current slider angle</span></span> |
| <span data-ttu-id="70720-269">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="70720-269">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="70720-270">Ângulo de deslizamento mínimo</span><span class="sxs-lookup"><span data-stu-id="70720-270">Minimum slider angle</span></span> |
| <span data-ttu-id="70720-271">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="70720-271">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="70720-272">Ângulo de deslizamento máximo</span><span class="sxs-lookup"><span data-stu-id="70720-272">Maximum slider angle</span></span> |
| <span data-ttu-id="70720-273">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="70720-273">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="70720-274">Lista de valores de ângulo, define ângulos de ancoragem, se definidos, ângulo de deslizamento só pode ser um dos ângulos de âncora definidos</span><span class="sxs-lookup"><span data-stu-id="70720-274">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="70720-275">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="70720-275">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="70720-276">Número de ângulos de âncora</span><span class="sxs-lookup"><span data-stu-id="70720-276">Number of anchor angles</span></span> |
| <span data-ttu-id="70720-277">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-277">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="70720-278">ID de recursos de pixelmap de fundo</span><span class="sxs-lookup"><span data-stu-id="70720-278">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="70720-279">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-279">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="70720-280">ID de recurso do pixelmap da agulha</span><span class="sxs-lookup"><span data-stu-id="70720-280">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="70720-281">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="70720-281">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="70720-282">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-282">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| <span data-ttu-id="70720-283">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-283">Members</span></span> | <span data-ttu-id="70720-284">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-284">Description</span></span> |
| -------------------------------- | ------------------------|
| <span data-ttu-id="70720-285">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="70720-285">**gx_rectangle_left**</span></span>            | <span data-ttu-id="70720-286">Esquerda do retângulo</span><span class="sxs-lookup"><span data-stu-id="70720-286">Left of the rectangle</span></span>   |  
| <span data-ttu-id="70720-287">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="70720-287">**gx_rectangle_top**</span></span>             | <span data-ttu-id="70720-288">Topo do retângulo</span><span class="sxs-lookup"><span data-stu-id="70720-288">Top of the rectangle</span></span>    | 
| <span data-ttu-id="70720-289">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="70720-289">**gx_rectangle_right**</span></span>           | <span data-ttu-id="70720-290">Direito do retângulo</span><span class="sxs-lookup"><span data-stu-id="70720-290">Right of the rectangle</span></span>  |
| <span data-ttu-id="70720-291">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="70720-291">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="70720-292">Fundo do retângulo</span><span class="sxs-lookup"><span data-stu-id="70720-292">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="70720-293">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="70720-293">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-294">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-294">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| <span data-ttu-id="70720-295">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-295">Members</span></span> | <span data-ttu-id="70720-296">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-296">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="70720-297">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="70720-297">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="70720-298">ID de recurso de fonte de texto normal</span><span class="sxs-lookup"><span data-stu-id="70720-298">Resource ID of normal text font</span></span> |
| <span data-ttu-id="70720-299">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="70720-299">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="70720-300">ID de recurso de fonte de texto arrojado</span><span class="sxs-lookup"><span data-stu-id="70720-300">Resource ID of bold text font</span></span> |
| <span data-ttu-id="70720-301">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="70720-301">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="70720-302">ID de recurso de fonte de texto itálico</span><span class="sxs-lookup"><span data-stu-id="70720-302">Resource ID of italic text font</span></span> |
| <span data-ttu-id="70720-303">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="70720-303">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="70720-304">ID de recurso de fonte de texto itálico arrojado</span><span class="sxs-lookup"><span data-stu-id="70720-304">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="70720-305">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-305">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="70720-306">**Definição**</span><span class="sxs-lookup"><span data-stu-id="70720-306">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

| <span data-ttu-id="70720-307">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-307">Members</span></span> | <span data-ttu-id="70720-308">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-308">Description</span></span> |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="70720-309">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="70720-309">**gx_scroll_value**</span></span>     | <span data-ttu-id="70720-310">Posição atual do pergaminho</span><span class="sxs-lookup"><span data-stu-id="70720-310">Current scroll position</span></span>       |
| <span data-ttu-id="70720-311">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="70720-311">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="70720-312">Posição mínima reportada</span><span class="sxs-lookup"><span data-stu-id="70720-312">Minimum reported position</span></span>     |
| <span data-ttu-id="70720-313">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="70720-313">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="70720-314">Posição máxima reportada</span><span class="sxs-lookup"><span data-stu-id="70720-314">Maximum reported position</span></span>     |
| <span data-ttu-id="70720-315">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="70720-315">**gx_scroll_visible**</span></span>   | <span data-ttu-id="70720-316">Intervalo visível da janela dos pais</span><span class="sxs-lookup"><span data-stu-id="70720-316">Parent window visible range</span></span>   |
| <span data-ttu-id="70720-317">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="70720-317">**gx_scroll_increment**</span></span> | <span data-ttu-id="70720-318">Valor delta mínimo da barra de pergaminho</span><span class="sxs-lookup"><span data-stu-id="70720-318">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="70720-319">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="70720-319">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="70720-320">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-320">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

| <span data-ttu-id="70720-321">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-321">Members</span></span> | <span data-ttu-id="70720-322">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-322">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="70720-323">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="70720-323">**gx_scroll_width**</span></span>                      | <span data-ttu-id="70720-324">Largura do widget da barra de deslocação, em pixels</span><span class="sxs-lookup"><span data-stu-id="70720-324">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="70720-325">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="70720-325">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="70720-326">Largura do botão do polegar que desliza na barra de deslocação, em pixels.</span><span class="sxs-lookup"><span data-stu-id="70720-326">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="70720-327">Este valor é geralmente um número de pixels menos do que a largura total da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="70720-327">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="70720-328">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="70720-328">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="70720-329">Compensado a partir da extremidade da barra de deslocação para o ponto de viagem mínimo do botão do polegar.</span><span class="sxs-lookup"><span data-stu-id="70720-329">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="70720-330">Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="70720-330">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="70720-331">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="70720-331">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="70720-332">Compensado a partir da extremidade da barra de deslocação para o ponto de viagem máximo do botão do polegar.</span><span class="sxs-lookup"><span data-stu-id="70720-332">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="70720-333">Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="70720-333">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="70720-334">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="70720-334">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="70720-335">Estilos de fronteira do botão do polegar</span><span class="sxs-lookup"><span data-stu-id="70720-335">Border styles of thumb button</span></span> |
| <span data-ttu-id="70720-336">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-336">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="70720-337">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="70720-337">Optional pixelmap ID.</span></span> <span data-ttu-id="70720-338">Se este ID pixelmap não for zero, a barra de deslocação usa este mapa pixel para desenhar o fundo da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="70720-338">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="70720-339">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-339">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="70720-340">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="70720-340">Optional pixelmap ID.</span></span> <span data-ttu-id="70720-341">Se este ID pixelmap não for zero, o botão do polegar da barra de deslocação usa este pixelmap para desenhar-se</span><span class="sxs-lookup"><span data-stu-id="70720-341">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="70720-342">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-342">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="70720-343">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="70720-343">Optional pixelmap ID.</span></span> <span data-ttu-id="70720-344">Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão de extremidade esquerda/up da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="70720-344">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="70720-345">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-345">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="70720-346">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="70720-346">Optional pixelmap ID.</span></span> <span data-ttu-id="70720-347">Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão final da barra de deslocação para a direita/para baixo</span><span class="sxs-lookup"><span data-stu-id="70720-347">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="70720-348">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="70720-348">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="70720-349">ID de recursos de cor usado para encher botão de polegar</span><span class="sxs-lookup"><span data-stu-id="70720-349">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="70720-350">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="70720-350">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="70720-351">ID de recurso de cor usado para desenhar a borda do botão polegar</span><span class="sxs-lookup"><span data-stu-id="70720-351">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="70720-352">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="70720-352">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="70720-353">ID de recursos de cor usado para encher botões finais da barra de deslocamento</span><span class="sxs-lookup"><span data-stu-id="70720-353">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="70720-354">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="70720-354">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="70720-355">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-355">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

| <span data-ttu-id="70720-356">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-356">Members</span></span> | <span data-ttu-id="70720-357">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-357">Description</span></span> |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="70720-358">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="70720-358">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="70720-359">Valor mínimo reportado</span><span class="sxs-lookup"><span data-stu-id="70720-359">Minimum reported value</span></span> |
| <span data-ttu-id="70720-360">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="70720-360">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="70720-361">Valor máximo reportado</span><span class="sxs-lookup"><span data-stu-id="70720-361">Maximum reported value</span></span> |
| <span data-ttu-id="70720-362">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="70720-362">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="70720-363">Valor atual</span><span class="sxs-lookup"><span data-stu-id="70720-363">Current value</span></span> |
| <span data-ttu-id="70720-364">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="70720-364">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="70720-365">Limite de viagem de agulha</span><span class="sxs-lookup"><span data-stu-id="70720-365">Needle travel limit</span></span> |
| <span data-ttu-id="70720-366">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="70720-366">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="70720-367">Limite de viagem de agulha</span><span class="sxs-lookup"><span data-stu-id="70720-367">Needle travel limit</span></span> |
| <span data-ttu-id="70720-368">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="70720-368">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="70720-369">Largura da agulha em pixel</span><span class="sxs-lookup"><span data-stu-id="70720-369">Needle width in pixel</span></span> |
| <span data-ttu-id="70720-370">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="70720-370">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="70720-371">Altura da agulha em pixel</span><span class="sxs-lookup"><span data-stu-id="70720-371">Needle height in pixel</span></span> |
|<span data-ttu-id="70720-372">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="70720-372">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="70720-373">Posição de desenho da agulha.</span><span class="sxs-lookup"><span data-stu-id="70720-373">Needle draw position.</span></span> <span data-ttu-id="70720-374">Se estiver definido GX_STYLE_SLIDER_VERTICAL, é utilizado para especificar a compensação da posição de arranque da agulha para a esquerda do deslizador.</span><span class="sxs-lookup"><span data-stu-id="70720-374">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="70720-375">Caso contrário, usado para especificar o offset da posição inicial de desenho da agulha para a parte superior do slider.</span><span class="sxs-lookup"><span data-stu-id="70720-375">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="70720-376">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="70720-376">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="70720-377">Agulha hotpot_offset, utilizada para especificar o offset da posição inicial de desenho da agulha para o hotspot de slider.</span><span class="sxs-lookup"><span data-stu-id="70720-377">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="70720-378">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="70720-378">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="70720-379">Definição</span><span class="sxs-lookup"><span data-stu-id="70720-379">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

| <span data-ttu-id="70720-380">Membros</span><span class="sxs-lookup"><span data-stu-id="70720-380">Members</span></span> | <span data-ttu-id="70720-381">Descrição</span><span class="sxs-lookup"><span data-stu-id="70720-381">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="70720-382">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="70720-382">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="70720-383">ID de recurso do pixelmap a ser apresentado para esta moldura.</span><span class="sxs-lookup"><span data-stu-id="70720-383">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="70720-384">A identificação pode ser 0.</span><span class="sxs-lookup"><span data-stu-id="70720-384">The ID can be 0.</span></span> |
| <span data-ttu-id="70720-385">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="70720-385">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="70720-386">Compensado do widget sprite à esquerda para exibir o pixelmap</span><span class="sxs-lookup"><span data-stu-id="70720-386">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="70720-387">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="70720-387">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="70720-388">Compensado a partir do topo do widget sprite para exibir o pixelmap</span><span class="sxs-lookup"><span data-stu-id="70720-388">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="70720-389">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="70720-389">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="70720-390">Valor de atraso, em marcador GUIX, depois de exibir este quadro antes de avançar para o próximo quadro de sprite</span><span class="sxs-lookup"><span data-stu-id="70720-390">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="70720-391">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="70720-391">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="70720-392">Defina como o fundo deve ser apagado.</span><span class="sxs-lookup"><span data-stu-id="70720-392">Define how the background should be erased.</span></span> <span data-ttu-id="70720-393">Os valores possíveis para este campo são:</span><span class="sxs-lookup"><span data-stu-id="70720-393">Possible values for this field are:</span></span><br /><span data-ttu-id="70720-394">GX_SPRITE_BACKGROUND_NO_ACTION: Não há preenchimento entre quadros</span><span class="sxs-lookup"><span data-stu-id="70720-394">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="70720-395">GX_SPRITE_BACKGROUND_SOLID_FILL: Redeseguihar fundo de sprite</span><span class="sxs-lookup"><span data-stu-id="70720-395">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="70720-396">GX_SPRITE_BACKGROUND_RESTORE: Restaurar o pixelmap anterior</span><span class="sxs-lookup"><span data-stu-id="70720-396">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="70720-397">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="70720-397">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="70720-398">Valor alfa a ser adicionado ao mapa pixel apresentado.</span><span class="sxs-lookup"><span data-stu-id="70720-398">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="70720-399">O valor 255 especifica que não deve ser imposto nenhum valor alfa extra.</span><span class="sxs-lookup"><span data-stu-id="70720-399">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="70720-400">Se o mapa de pixels incluir um canal alfa, este canal alfa será adicionado ao valor alfa do quadro.</span><span class="sxs-lookup"><span data-stu-id="70720-400">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
