---
title: Apêndice I - ESTRUTURAS DE Informação GUIX
description: Saiba mais sobre as estruturas de informação guix.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827211"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="b52d5-103">Apêndice I - ESTRUTURAS DE Informação GUIX</span><span class="sxs-lookup"><span data-stu-id="b52d5-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="b52d5-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-105">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b52d5-106">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b52d5-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b52d5-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="b52d5-108">Texto para reordenamento</span><span class="sxs-lookup"><span data-stu-id="b52d5-108">Text for reordering</span></span> |
| <span data-ttu-id="b52d5-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="b52d5-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="b52d5-110">Fonte usada para exibir texto, defini-lo para GX_NULL se não for necessário quebrar a linha</span><span class="sxs-lookup"><span data-stu-id="b52d5-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="b52d5-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="b52d5-112">Largura disponível para exibição, desalinhá-la para -1 se não for necessária rutura de linha</span><span class="sxs-lookup"><span data-stu-id="b52d5-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="b52d5-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-114">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b52d5-115">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b52d5-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b52d5-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="b52d5-117">Ponteiro para a matriz de texto bidi reordenado</span><span class="sxs-lookup"><span data-stu-id="b52d5-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="b52d5-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="b52d5-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="b52d5-119">Linhas totais de texto bidi resolvido para um parágrafo</span><span class="sxs-lookup"><span data-stu-id="b52d5-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="b52d5-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="b52d5-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="b52d5-121">Informações de texto de bidi resolvidas para o parágrafo seguinte</span><span class="sxs-lookup"><span data-stu-id="b52d5-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="b52d5-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-123">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-123">Definition</span></span>

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
### <a name="members"></a><span data-ttu-id="b52d5-124">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="b52d5-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="b52d5-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="b52d5-126">Passos totais que a agulha irá percorrer ao mover-se do ângulo da agulha atual para um ângulo de agulha recém-atribuído</span><span class="sxs-lookup"><span data-stu-id="b52d5-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="b52d5-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="b52d5-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="b52d5-128">O número de relógio GUIX assinala-se entre etapas de animação</span><span class="sxs-lookup"><span data-stu-id="b52d5-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="b52d5-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="b52d5-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="b52d5-130">A distância da esquerda do widget de bitola para o centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="b52d5-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b52d5-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="b52d5-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="b52d5-132">A distância do topo do widget de bitola até ao centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="b52d5-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b52d5-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="b52d5-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="b52d5-134">A distância da esquerda da imagem da agulha para o centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="b52d5-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b52d5-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="b52d5-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="b52d5-136">A distância do topo da imagem da agulha ao centro de rotação da agulha de bitola</span><span class="sxs-lookup"><span data-stu-id="b52d5-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b52d5-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="b52d5-138">Identificação de recursos do mapa pixel que será utilizado para desenhar a agulha de bitola.</span><span class="sxs-lookup"><span data-stu-id="b52d5-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="b52d5-139">Esta imagem será girada conforme necessário pelo widget de bitola para exibir a agulha de bitola em qualquer posição</span><span class="sxs-lookup"><span data-stu-id="b52d5-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="b52d5-140">O diagrama abaixo ilustra os xpos, ypos e xcor, coordenadas ycor:</span><span class="sxs-lookup"><span data-stu-id="b52d5-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagrama das coordenadas Needle Y e X](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="b52d5-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-143">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-143">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-144">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b52d5-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="b52d5-146">O valor mínimo de dados, que é usado para calcular a escala</span><span class="sxs-lookup"><span data-stu-id="b52d5-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="b52d5-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="b52d5-148">O valor máximo dos dados, que é usado para calcular a escala</span><span class="sxs-lookup"><span data-stu-id="b52d5-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="b52d5-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="b52d5-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="b52d5-150">Ponteiro para uma variedade de valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="b52d5-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="b52d5-151">Estes são os valores inteiros traçados pelo widget gráfico de linha</span><span class="sxs-lookup"><span data-stu-id="b52d5-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="b52d5-152">**gx_line_ <side> _margin**</span><span class="sxs-lookup"><span data-stu-id="b52d5-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="b52d5-153">A compensação da janela do gráfico está ligada à área real de renderização do gráfico.</span><span class="sxs-lookup"><span data-stu-id="b52d5-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="b52d5-154">O eixo do gráfico e a linha de dados estão sempre traçados dentro deste limite interno, o que permite que a aplicação desenhe etiquetas e outras informações dentro da janela do gráfico, mas fora da área de gráfico de carvão</span><span class="sxs-lookup"><span data-stu-id="b52d5-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="b52d5-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="b52d5-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="b52d5-156">O número de valores de dados que podem estar presentes.</span><span class="sxs-lookup"><span data-stu-id="b52d5-156">The number of data values which may be present.</span></span> <span data-ttu-id="b52d5-157">Este parâmetro é utilizado para calcular a escala ou intervalo do eixo x para a trama de pontos de dados.</span><span class="sxs-lookup"><span data-stu-id="b52d5-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="b52d5-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="b52d5-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="b52d5-159">O número de valores de dados que realmente apresentam na matriz de dados.</span><span class="sxs-lookup"><span data-stu-id="b52d5-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="b52d5-160">Um gráfico de linha pode ser dimensionado para desenhar um máximo de 100 valores (por exemplo), mas em qualquer atualização particular um número menor de valores de dados pode realmente estar presente.</span><span class="sxs-lookup"><span data-stu-id="b52d5-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="b52d5-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="b52d5-162">Largura da linha utilizada para desenhar o eixo horizontal e vertical</span><span class="sxs-lookup"><span data-stu-id="b52d5-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="b52d5-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="b52d5-164">Largura da linha de dados traçada</span><span class="sxs-lookup"><span data-stu-id="b52d5-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="b52d5-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="b52d5-166">ID de recursos da cor usada para desenhar as linhas do eixo</span><span class="sxs-lookup"><span data-stu-id="b52d5-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="b52d5-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="b52d5-168">ID de recursos da cor usada para desenhar a linha de dados do gráfico</span><span class="sxs-lookup"><span data-stu-id="b52d5-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="b52d5-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-170">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="b52d5-171">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b52d5-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="b52d5-173">ID de recurso da imagem do rato</span><span class="sxs-lookup"><span data-stu-id="b52d5-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="b52d5-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="b52d5-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="b52d5-175">A compensação da esquerda da imagem do rato para o hotspot de imagem do rato</span><span class="sxs-lookup"><span data-stu-id="b52d5-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="b52d5-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="b52d5-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="b52d5-177">A compensação do topo da imagem do rato para o hotspot de imagem do rato</span><span class="sxs-lookup"><span data-stu-id="b52d5-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="b52d5-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="b52d5-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-179">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="b52d5-180">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b52d5-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="b52d5-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="b52d5-182">A distância mínima de arrasto por temporizador GUIX para desencadear um evento FLICK.</span><span class="sxs-lookup"><span data-stu-id="b52d5-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="b52d5-183">Ligue GX_FIXED_VAL_MAKE para fazer um valor de tipo de dados de ponto fixo</span><span class="sxs-lookup"><span data-stu-id="b52d5-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="b52d5-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="b52d5-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="b52d5-185">A velocidade máxima de arrasto no temporizador GUIX assinala-se para desencadear um evento FLICK</span><span class="sxs-lookup"><span data-stu-id="b52d5-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="b52d5-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-187">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="b52d5-188">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="b52d5-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="b52d5-190">Identificação de recursos do mapa de pixels para encher o fundo antes da agulha.</span><span class="sxs-lookup"><span data-stu-id="b52d5-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="b52d5-191">Se o pixelmap de fundo superior não estiver definido, é usado para encher o fundo antes e depois da agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="b52d5-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="b52d5-193">ID de recurso do mapa de pixels para o enchimento de fundo após a agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="b52d5-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="b52d5-195">ID de recurso do pixelmap da agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="b52d5-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-197">**Definição**</span><span class="sxs-lookup"><span data-stu-id="b52d5-197">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-198">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b52d5-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="b52d5-200">Valor mínimo reportado</span><span class="sxs-lookup"><span data-stu-id="b52d5-200">Minimum reported value</span></span> |
| <span data-ttu-id="b52d5-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="b52d5-202">Valor máximo reportado</span><span class="sxs-lookup"><span data-stu-id="b52d5-202">Maximum reported value</span></span> |
| <span data-ttu-id="b52d5-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="b52d5-204">Valor atual</span><span class="sxs-lookup"><span data-stu-id="b52d5-204">Current value</span></span> |
| <span data-ttu-id="b52d5-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="b52d5-206">ID de recurso da fonte, usado para desenhar o valor de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="b52d5-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="b52d5-208">ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="b52d5-210">ID de recurso da cor do texto quando o widget ganha o foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="b52d5-212">ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="b52d5-214">ID de recurso do pixelmap para preenchimento de fundo</span><span class="sxs-lookup"><span data-stu-id="b52d5-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="b52d5-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-216">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-216">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-217">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="b52d5-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b52d5-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="b52d5-219">Posição widget na coordenada x</span><span class="sxs-lookup"><span data-stu-id="b52d5-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="b52d5-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b52d5-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="b52d5-221">Posição widget na coordenada y</span><span class="sxs-lookup"><span data-stu-id="b52d5-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="b52d5-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b52d5-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="b52d5-223">Raio do círculo de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="b52d5-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="b52d5-225">O valor atual, limitado ao intervalo [-360, 360], indica o delta angular entre a posição da âncora e o ponto final do arco superior. O valor negativo faz com que o arco seja desenhado no sentido dos ponteiros do relógio, a partir da posição de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="b52d5-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b52d5-226">O valor positivo faz com que o arco seja desenhado no sentido contrário ao dos ponteiros do relógio, a partir da posição de ancoragem.</span><span class="sxs-lookup"><span data-stu-id="b52d5-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b52d5-227">A aplicação deve escalar o valor da palavra real indicada para atribuir um valor angular ao widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="b52d5-229">Ângulo inicial do arco de progresso superior. O valor é definido em termos de grau inteiro com 0 graus apontando para a direita e 90 graus indicando posição direta.</span><span class="sxs-lookup"><span data-stu-id="b52d5-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="b52d5-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="b52d5-231">ID de recursos da fonte utilizada para desenhar o valor de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="b52d5-233">ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="b52d5-235">ID de recurso da cor do texto quando widget ganhar foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="b52d5-237">ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b52d5-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="b52d5-239">Largura do círculo de menor progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="b52d5-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="b52d5-241">Largura do arco de progressão superior, o arco superior pode ser mais estreito, o mesmo que, ou mais largo que o círculo inferior</span><span class="sxs-lookup"><span data-stu-id="b52d5-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="b52d5-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="b52d5-243">ID de recursos da cor para preencher o círculo de menor progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="b52d5-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="b52d5-245">ID de recurso da cor para preencher o arco superior do progresso</span><span class="sxs-lookup"><span data-stu-id="b52d5-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="b52d5-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-247">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-247">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-248">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="b52d5-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b52d5-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="b52d5-250">Distância da esquerda do widget deslizante para o centro de rotação da agulha deslizante</span><span class="sxs-lookup"><span data-stu-id="b52d5-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b52d5-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b52d5-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="b52d5-252">Distância do topo do widget de slider para o centro de rotação da agulha deslizante</span><span class="sxs-lookup"><span data-stu-id="b52d5-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b52d5-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b52d5-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="b52d5-254">Raio do círculo de deslizamento radial</span><span class="sxs-lookup"><span data-stu-id="b52d5-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="b52d5-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="b52d5-256">Largura da pista de slider radial</span><span class="sxs-lookup"><span data-stu-id="b52d5-256">Width of radial slider track</span></span> |
| <span data-ttu-id="b52d5-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="b52d5-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="b52d5-258">Ângulo de deslizamento de corrente</span><span class="sxs-lookup"><span data-stu-id="b52d5-258">Current slider angle</span></span> |
| <span data-ttu-id="b52d5-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="b52d5-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="b52d5-260">Ângulo de deslizamento mínimo</span><span class="sxs-lookup"><span data-stu-id="b52d5-260">Minimum slider angle</span></span> |
| <span data-ttu-id="b52d5-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="b52d5-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="b52d5-262">Ângulo de deslizamento máximo</span><span class="sxs-lookup"><span data-stu-id="b52d5-262">Maximum slider angle</span></span> |
| <span data-ttu-id="b52d5-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="b52d5-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="b52d5-264">Lista de valores de ângulo, define ângulos de ancoragem, se definidos, ângulo de deslizamento só pode ser um dos ângulos de âncora definidos</span><span class="sxs-lookup"><span data-stu-id="b52d5-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="b52d5-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="b52d5-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="b52d5-266">Número de ângulos de âncora</span><span class="sxs-lookup"><span data-stu-id="b52d5-266">Number of anchor angles</span></span> |
| <span data-ttu-id="b52d5-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="b52d5-268">ID de recursos de pixelmap de fundo</span><span class="sxs-lookup"><span data-stu-id="b52d5-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="b52d5-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="b52d5-270">ID de recurso do pixelmap da agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="b52d5-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="b52d5-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-272">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="b52d5-273">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="b52d5-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="b52d5-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="b52d5-275">Esquerda do retângulo</span><span class="sxs-lookup"><span data-stu-id="b52d5-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="b52d5-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="b52d5-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="b52d5-277">Topo do retângulo</span><span class="sxs-lookup"><span data-stu-id="b52d5-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="b52d5-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="b52d5-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="b52d5-279">Direito do retângulo</span><span class="sxs-lookup"><span data-stu-id="b52d5-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="b52d5-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="b52d5-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="b52d5-281">Fundo do retângulo</span><span class="sxs-lookup"><span data-stu-id="b52d5-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="b52d5-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="b52d5-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-283">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="b52d5-284">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b52d5-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="b52d5-286">ID de recurso de fonte de texto normal</span><span class="sxs-lookup"><span data-stu-id="b52d5-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="b52d5-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="b52d5-288">ID de recurso de fonte de texto arrojado</span><span class="sxs-lookup"><span data-stu-id="b52d5-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="b52d5-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="b52d5-290">ID de recurso de fonte de texto itálico</span><span class="sxs-lookup"><span data-stu-id="b52d5-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="b52d5-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b52d5-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="b52d5-292">ID de recurso de fonte de texto itálico arrojado</span><span class="sxs-lookup"><span data-stu-id="b52d5-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="b52d5-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="b52d5-294">**Definição**</span><span class="sxs-lookup"><span data-stu-id="b52d5-294">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-295">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="b52d5-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="b52d5-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="b52d5-297">Posição atual do pergaminho</span><span class="sxs-lookup"><span data-stu-id="b52d5-297">Current scroll position</span></span>       |
| <span data-ttu-id="b52d5-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="b52d5-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="b52d5-299">Posição mínima reportada</span><span class="sxs-lookup"><span data-stu-id="b52d5-299">Minimum reported position</span></span>     |
| <span data-ttu-id="b52d5-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="b52d5-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="b52d5-301">Posição máxima reportada</span><span class="sxs-lookup"><span data-stu-id="b52d5-301">Maximum reported position</span></span>     |
| <span data-ttu-id="b52d5-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="b52d5-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="b52d5-303">Intervalo visível da janela dos pais</span><span class="sxs-lookup"><span data-stu-id="b52d5-303">Parent window visible range</span></span>   |
| <span data-ttu-id="b52d5-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="b52d5-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="b52d5-305">Valor delta mínimo da barra de pergaminho</span><span class="sxs-lookup"><span data-stu-id="b52d5-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="b52d5-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="b52d5-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="b52d5-307">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-307">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-308">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b52d5-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="b52d5-310">Largura do widget da barra de deslocação, em pixels</span><span class="sxs-lookup"><span data-stu-id="b52d5-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="b52d5-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="b52d5-312">Largura do botão do polegar que desliza na barra de deslocação, em pixels.</span><span class="sxs-lookup"><span data-stu-id="b52d5-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="b52d5-313">Este valor é geralmente um número de pixels menos do que a largura total da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="b52d5-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="b52d5-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="b52d5-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="b52d5-315">Compensado a partir da extremidade da barra de deslocação para o ponto de viagem mínimo do botão do polegar.</span><span class="sxs-lookup"><span data-stu-id="b52d5-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="b52d5-316">Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="b52d5-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b52d5-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="b52d5-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="b52d5-318">Compensado a partir da extremidade da barra de deslocação para o ponto de viagem máximo do botão do polegar.</span><span class="sxs-lookup"><span data-stu-id="b52d5-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="b52d5-319">Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="b52d5-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b52d5-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="b52d5-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="b52d5-321">Estilos de fronteira do botão do polegar</span><span class="sxs-lookup"><span data-stu-id="b52d5-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="b52d5-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="b52d5-323">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="b52d5-323">Optional pixelmap ID.</span></span> <span data-ttu-id="b52d5-324">Se este ID pixelmap não for zero, a barra de deslocação usa este mapa pixel para desenhar o fundo da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="b52d5-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="b52d5-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="b52d5-326">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="b52d5-326">Optional pixelmap ID.</span></span> <span data-ttu-id="b52d5-327">Se este ID pixelmap não for zero, o botão do polegar da barra de deslocação usa este pixelmap para desenhar-se</span><span class="sxs-lookup"><span data-stu-id="b52d5-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="b52d5-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="b52d5-329">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="b52d5-329">Optional pixelmap ID.</span></span> <span data-ttu-id="b52d5-330">Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão de extremidade esquerda/up da barra de deslocação</span><span class="sxs-lookup"><span data-stu-id="b52d5-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="b52d5-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="b52d5-332">ID de pixelmap opcional.</span><span class="sxs-lookup"><span data-stu-id="b52d5-332">Optional pixelmap ID.</span></span> <span data-ttu-id="b52d5-333">Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão final da barra de deslocação para a direita/para baixo</span><span class="sxs-lookup"><span data-stu-id="b52d5-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="b52d5-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="b52d5-335">ID de recursos de cor usado para encher botão de polegar</span><span class="sxs-lookup"><span data-stu-id="b52d5-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="b52d5-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="b52d5-337">ID de recurso de cor usado para desenhar a borda do botão polegar</span><span class="sxs-lookup"><span data-stu-id="b52d5-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="b52d5-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="b52d5-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="b52d5-339">ID de recursos de cor usado para encher botões finais da barra de deslocamento</span><span class="sxs-lookup"><span data-stu-id="b52d5-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="b52d5-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b52d5-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-341">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-341">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-342">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b52d5-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="b52d5-344">Valor mínimo reportado</span><span class="sxs-lookup"><span data-stu-id="b52d5-344">Minimum reported value</span></span> |
| <span data-ttu-id="b52d5-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b52d5-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="b52d5-346">Valor máximo reportado</span><span class="sxs-lookup"><span data-stu-id="b52d5-346">Maximum reported value</span></span> |
| <span data-ttu-id="b52d5-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="b52d5-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="b52d5-348">Valor atual</span><span class="sxs-lookup"><span data-stu-id="b52d5-348">Current value</span></span> |
| <span data-ttu-id="b52d5-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="b52d5-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="b52d5-350">Limite de viagem de agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-350">Needle travel limit</span></span> |
| <span data-ttu-id="b52d5-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="b52d5-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="b52d5-352">Limite de viagem de agulha</span><span class="sxs-lookup"><span data-stu-id="b52d5-352">Needle travel limit</span></span> |
| <span data-ttu-id="b52d5-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="b52d5-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="b52d5-354">Largura da agulha em pixel</span><span class="sxs-lookup"><span data-stu-id="b52d5-354">Needle width in pixel</span></span> |
| <span data-ttu-id="b52d5-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="b52d5-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="b52d5-356">Altura da agulha em pixel</span><span class="sxs-lookup"><span data-stu-id="b52d5-356">Needle height in pixel</span></span> |
|<span data-ttu-id="b52d5-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="b52d5-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="b52d5-358">Posição de desenho da agulha.</span><span class="sxs-lookup"><span data-stu-id="b52d5-358">Needle draw position.</span></span> <span data-ttu-id="b52d5-359">Se estiver definido GX_STYLE_SLIDER_VERTICAL, é utilizado para especificar a compensação da posição de arranque da agulha para a esquerda do deslizador.</span><span class="sxs-lookup"><span data-stu-id="b52d5-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="b52d5-360">Caso contrário, usado para especificar o offset da posição inicial de desenho da agulha para a parte superior do slider.</span><span class="sxs-lookup"><span data-stu-id="b52d5-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="b52d5-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="b52d5-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="b52d5-362">Agulha hotpot_offset, utilizada para especificar o offset da posição inicial de desenho da agulha para o hotspot de slider.</span><span class="sxs-lookup"><span data-stu-id="b52d5-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="b52d5-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b52d5-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="b52d5-364">Definição</span><span class="sxs-lookup"><span data-stu-id="b52d5-364">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b52d5-365">Membros</span><span class="sxs-lookup"><span data-stu-id="b52d5-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b52d5-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b52d5-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="b52d5-367">ID de recurso do pixelmap a ser apresentado para esta moldura.</span><span class="sxs-lookup"><span data-stu-id="b52d5-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="b52d5-368">A identificação pode ser 0.</span><span class="sxs-lookup"><span data-stu-id="b52d5-368">The ID can be 0.</span></span> |
| <span data-ttu-id="b52d5-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="b52d5-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="b52d5-370">Compensado do widget sprite à esquerda para exibir o pixelmap</span><span class="sxs-lookup"><span data-stu-id="b52d5-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="b52d5-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="b52d5-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="b52d5-372">Compensado a partir do topo do widget sprite para exibir o pixelmap</span><span class="sxs-lookup"><span data-stu-id="b52d5-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="b52d5-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="b52d5-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="b52d5-374">Valor de atraso, em marcador GUIX, depois de exibir este quadro antes de avançar para o próximo quadro de sprite</span><span class="sxs-lookup"><span data-stu-id="b52d5-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="b52d5-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="b52d5-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="b52d5-376">Defina como o fundo deve ser apagado.</span><span class="sxs-lookup"><span data-stu-id="b52d5-376">Define how the background should be erased.</span></span> <span data-ttu-id="b52d5-377">Os valores possíveis para este campo são:</span><span class="sxs-lookup"><span data-stu-id="b52d5-377">Possible values for this field are:</span></span><br /><span data-ttu-id="b52d5-378">GX_SPRITE_BACKGROUND_NO_ACTION: Não há preenchimento entre quadros</span><span class="sxs-lookup"><span data-stu-id="b52d5-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="b52d5-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redeseguihar fundo de sprite</span><span class="sxs-lookup"><span data-stu-id="b52d5-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="b52d5-380">GX_SPRITE_BACKGROUND_RESTORE: Restaurar o pixelmap anterior</span><span class="sxs-lookup"><span data-stu-id="b52d5-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="b52d5-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="b52d5-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="b52d5-382">Valor alfa a ser adicionado ao mapa pixel apresentado.</span><span class="sxs-lookup"><span data-stu-id="b52d5-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="b52d5-383">O valor 255 especifica que não deve ser imposto nenhum valor alfa extra.</span><span class="sxs-lookup"><span data-stu-id="b52d5-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="b52d5-384">Se o mapa de pixels incluir um canal alfa, este canal alfa será adicionado ao valor alfa do quadro.</span><span class="sxs-lookup"><span data-stu-id="b52d5-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
