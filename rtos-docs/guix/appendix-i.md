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
# <a name="appendix-i---guix-information-structures"></a>Apêndice I - ESTRUTURAS DE Informação GUIX 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>Definição

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a>Membros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Texto para reordenamento |
| **gx_bidi_text_info_font**               | Fonte usada para exibir texto, defini-lo para GX_NULL se não for necessário quebrar a linha |
| **gx_bidi_text_info_display_width**      | Largura disponível para exibição, desalinhá-la para -1 se não for necessária rutura de linha |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>Definição

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a>Membros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Ponteiro para a matriz de texto bidi reordenado |
| **gx_bidi_resolved_text_info_total_lines**      | Linhas totais de texto bidi resolvido para um parágrafo |
| **gx_bidi_resolved_text_info_next**             | Informações de texto de bidi resolvidas para o parágrafo seguinte |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>Definição

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
### <a name="members"></a>Membros

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Passos totais que a agulha irá percorrer ao mover-se do ângulo da agulha atual para um ângulo de agulha recém-atribuído |
| **gx_circular_gauge_info_animation_delay**       | O número de relógio GUIX assinala-se entre etapas de animação |
| **gx_circular_gauge_info_needle_xpos**           | A distância da esquerda do widget de bitola para o centro de rotação da agulha de bitola |
| **gx_circular_gauge_info_needle_ypos**           | A distância do topo do widget de bitola até ao centro de rotação da agulha de bitola |
| **gx_circular_gauge_info_needle_xcor**           | A distância da esquerda da imagem da agulha para o centro de rotação da agulha de bitola |
| **gx_circular_gauge_info_needle_ycor**           | A distância do topo da imagem da agulha ao centro de rotação da agulha de bitola |
| **gx_circular_gauge_info_needle_pixelmap**       | Identificação de recursos do mapa pixel que será utilizado para desenhar a agulha de bitola. Esta imagem será girada conforme necessário pelo widget de bitola para exibir a agulha de bitola em qualquer posição |

O diagrama abaixo ilustra os xpos, ypos e xcor, coordenadas ycor:

![Diagrama das coordenadas Needle Y e X](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | O valor mínimo de dados, que é usado para calcular a escala
| **gx_line_chart_max_val**          | O valor máximo dos dados, que é usado para calcular a escala |
| **gx_line_chart_data**             | Ponteiro para uma variedade de valores inteiros. Estes são os valores inteiros traçados pelo widget gráfico de linha |
| **gx_line_ <side> _margin**          | A compensação da janela do gráfico está ligada à área real de renderização do gráfico. O eixo do gráfico e a linha de dados estão sempre traçados dentro deste limite interno, o que permite que a aplicação desenhe etiquetas e outras informações dentro da janela do gráfico, mas fora da área de gráfico de carvão |
| **gx_line_chart_max_data_count**   | O número de valores de dados que podem estar presentes. Este parâmetro é utilizado para calcular a escala ou intervalo do eixo x para a trama de pontos de dados. |
| **gx_line_active_data_count**      | O número de valores de dados que realmente apresentam na matriz de dados. Um gráfico de linha pode ser dimensionado para desenhar um máximo de 100 valores (por exemplo), mas em qualquer atualização particular um número menor de valores de dados pode realmente estar presente. |
| **gx_line_axis_line_width**        | Largura da linha utilizada para desenhar o eixo horizontal e vertical |
| **gx_line_data_line_width**        | Largura da linha de dados traçada |
| **gx_line_chart_axis_color**       | ID de recursos da cor usada para desenhar as linhas do eixo |
| **gx_line_chart_line_color**       | ID de recursos da cor usada para desenhar a linha de dados do gráfico |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>Definição

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a>Membros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | ID de recurso da imagem do rato |
| **gx_mouse_cursor_hotspot_x**      | A compensação da esquerda da imagem do rato para o hotspot de imagem do rato |
| **gx_mouse_cursor_hotspot_y**      | A compensação do topo da imagem do rato para o hotspot de imagem do rato |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Definição

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a>Membros

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | A distância mínima de arrasto por temporizador GUIX para desencadear um evento FLICK. Ligue GX_FIXED_VAL_MAKE para fazer um valor de tipo de dados de ponto fixo |
| **gx_pen_configuration_max_pen_speed_ticks** | A velocidade máxima de arrasto no temporizador GUIX assinala-se para desencadear um evento FLICK | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>Definição

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a>Membros

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Identificação de recursos do mapa de pixels para encher o fundo antes da agulha. Se o pixelmap de fundo superior não estiver definido, é usado para encher o fundo antes e depois da agulha |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | ID de recurso do mapa de pixels para o enchimento de fundo após a agulha |
| **gx_pixelmap_slider_info_needle_pixelmap**           | ID de recurso do pixelmap da agulha |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**Definição**

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

### <a name="members"></a>Membros

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Valor mínimo reportado |
| **gx_progress_bar_info_max_val**             | Valor máximo reportado |
| **gx_progress_bar_info_current_val**         | Valor atual |
| **gx_progress_bar_info_font_id**             | ID de recurso da fonte, usado para desenhar o valor de texto opcional dentro do widget da barra de progresso      |
| **gx_progress_bar_normal_text_color**        | ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_progress_bar_selected_text_color**      | ID de recurso da cor do texto quando o widget ganha o foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_progress_bar_disabled_text_color**      | ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_progress_bar_fill_pixelmap**            | ID de recurso do pixelmap para preenchimento de fundo|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Posição widget na coordenada x |
| **gx_radial_progress_bar_info_ycenter**           | Posição widget na coordenada y  |
| **gx_radial_progress_bar_info_radius**            | Raio do círculo de progresso |
| **gx_radial_progress_bar_info_current_val**       | O valor atual, limitado ao intervalo [-360, 360], indica o delta angular entre a posição da âncora e o ponto final do arco superior. O valor negativo faz com que o arco seja desenhado no sentido dos ponteiros do relógio, a partir da posição de ancoragem. O valor positivo faz com que o arco seja desenhado no sentido contrário ao dos ponteiros do relógio, a partir da posição de ancoragem. A aplicação deve escalar o valor da palavra real indicada para atribuir um valor angular ao widget da barra de progresso |
| **gx_radial_progress_bar_anchor_val**             | Ângulo inicial do arco de progresso superior. O valor é definido em termos de grau inteiro com 0 graus apontando para a direita e 90 graus indicando posição direta. |
| **gx_radial_progress_bar_font_id**                | ID de recursos da fonte utilizada para desenhar o valor de texto opcional dentro do widget da barra de progresso |
| **gx_radial_progress_bar_normal_text_color**      | ID de recurso da cor do texto em estado normal, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_radial_progress_bar_selected_text_color**    |ID de recurso da cor do texto quando widget ganhar foco, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_radial_progress_bar_disabled_text_color**    | ID de recurso da cor do texto quando GX_STYLE_ENABLED não está ativa, usado para definir o desenho de texto opcional dentro do widget da barra de progresso |
| **gx_radial_progress_bar_normal_brush_width**     | Largura do círculo de menor progresso |
| **gx_radial_progress_bar_selected_brush_width**   | Largura do arco de progressão superior, o arco superior pode ser mais estreito, o mesmo que, ou mais largo que o círculo inferior |
| **gx_radial_progress_bar_normal_brush_color**     | ID de recursos da cor para preencher o círculo de menor progresso |
| **gx_radial_progress_bar_selected_brush_color**   | ID de recurso da cor para preencher o arco superior do progresso |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Distância da esquerda do widget deslizante para o centro de rotação da agulha deslizante |
| **gx_radial_slider_info_ycenter**             | Distância do topo do widget de slider para o centro de rotação da agulha deslizante |
| **gx_radial_slider_info_radius**              | Raio do círculo de deslizamento radial |
| **gx_radial_slider_info_track_width**         | Largura da pista de slider radial |
| **gx_radial_slider_info_current_angle**       | Ângulo de deslizamento de corrente |
| **gx_radial_slider_info_min_angle**           | Ângulo de deslizamento mínimo |
| **gx_radial_slider_info_max_angle**           | Ângulo de deslizamento máximo |
| **gx_radial_slider_info_angle_list**          | Lista de valores de ângulo, define ângulos de ancoragem, se definidos, ângulo de deslizamento só pode ser um dos ângulos de âncora definidos |
| **gx_radial_slider_info_list_count**          | Número de ângulos de âncora |
| **gx_radial_slider_info_background_pixelmap** | ID de recursos de pixelmap de fundo |
| **gx_radial_slider_info_needle_pixelmap**     | ID de recurso do pixelmap da agulha |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>Definição

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a>Membros

|                                  |                         |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Esquerda do retângulo   |  
| **gx_rectangle_top**             | Topo do retângulo    | 
| **gx_rectangle_right**           | Direito do retângulo  |
| **gx_rectangle_bottom**          | Fundo do retângulo |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>Definição

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a>Membros

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | ID de recurso de fonte de texto normal |
| **gx_rich_text_fonts_bold_id**     | ID de recurso de fonte de texto arrojado |
| **gx_rich_text_fonts_italic_id**   | ID de recurso de fonte de texto itálico |
| **gx_rich_text_fonts_bold_italic_id** | ID de recurso de fonte de texto itálico arrojado |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**Definição**

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

### <a name="members"></a>Membros

|                         |                               |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Posição atual do pergaminho       |
| **gx_scroll_minimum**   | Posição mínima reportada     |
| **gx_scroll_maximum**   | Posição máxima reportada     |
| **gx_scroll_visible**   | Intervalo visível da janela dos pais   |
| **gx_scroll_increment** | Valor delta mínimo da barra de pergaminho |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Largura do widget da barra de deslocação, em pixels |
| **gx_scroll_thumb_width**                | Largura do botão do polegar que desliza na barra de deslocação, em pixels. Este valor é geralmente um número de pixels menos do que a largura total da barra de deslocação |
| **gx_scroll_thumb_travel_min**           | Compensado a partir da extremidade da barra de deslocação para o ponto de viagem mínimo do botão do polegar. Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação |
| **gx_scroll_thumb_travel_max**           | Compensado a partir da extremidade da barra de deslocação para o ponto de viagem máximo do botão do polegar. Este limite pode ser usado para evitar que o botão do polegar viaje até ao fim da barra de deslocação |
| **gx_scroll_thumb_border_style**         | Estilos de fronteira do botão do polegar |
| **gx_scroll_fill_pixelmap**              | ID de pixelmap opcional. Se este ID pixelmap não for zero, a barra de deslocação usa este mapa pixel para desenhar o fundo da barra de deslocação |
| **gx_scroll_thumb_pixelmap**             | ID de pixelmap opcional. Se este ID pixelmap não for zero, o botão do polegar da barra de deslocação usa este pixelmap para desenhar-se |
| **gx_scroll_up_pixelmap**                | ID de pixelmap opcional. Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão de extremidade esquerda/up da barra de deslocação |
| **gx_scroll_down_pixelmap**              | ID de pixelmap opcional. Se este ID do pixelmap não for zero, a barra de deslocação utiliza este ID pixelmap para desenhar o botão final da barra de deslocação para a direita/para baixo |
| **gx_scroll_thumb_color**                | ID de recursos de cor usado para encher botão de polegar |
| **gx_scroll_thumb_border_color**         | ID de recurso de cor usado para desenhar a borda do botão polegar | 
| **gx_scroll_button_color**               | ID de recursos de cor usado para encher botões finais da barra de deslocamento |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Valor mínimo reportado |
| **gx_slider_info_max_val**              | Valor máximo reportado |
| **gx_slider_info_current_value**        | Valor atual |
| **gx_slider_info_min_travel**           | Limite de viagem de agulha |
| **gx_slider_info_max_travel**           | Limite de viagem de agulha |
| **gx_slider_info_needle_width**         | Largura da agulha em pixel |
| **gx_slider_info_needle_height**        | Altura da agulha em pixel |
|**gx_slider_info_needle_inset**          | Posição de desenho da agulha. Se estiver definido GX_STYLE_SLIDER_VERTICAL, é utilizado para especificar a compensação da posição de arranque da agulha para a esquerda do deslizador. Caso contrário, usado para especificar o offset da posição inicial de desenho da agulha para a parte superior do slider. |
| **gx_slider_info_needle_hotspot_offset** | Agulha hotpot_offset, utilizada para especificar o offset da posição inicial de desenho da agulha para o hotspot de slider. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>Definição

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

### <a name="members"></a>Membros

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | ID de recurso do pixelmap a ser apresentado para esta moldura. A identificação pode ser 0. |
| **gx_sprite_frame_x_offset**             | Compensado do widget sprite à esquerda para exibir o pixelmap |
| **gx_sprite_frame_y_offset**             | Compensado a partir do topo do widget sprite para exibir o pixelmap |
| **gx_sprite_frame_delay**                | Valor de atraso, em marcador GUIX, depois de exibir este quadro antes de avançar para o próximo quadro de sprite |
| **gx_sprite_frame_background_operation** | Defina como o fundo deve ser apagado. Os valores possíveis para este campo são:<br />GX_SPRITE_BACKGROUND_NO_ACTION: Não há preenchimento entre quadros<br />GX_SPRITE_BACKGROUND_SOLID_FILL: Redeseguihar fundo de sprite<br />GX_SPRITE_BACKGROUND_RESTORE: Restaurar o pixelmap anterior |
| **gx_sprite_frame_alpha**                | Valor alfa a ser adicionado ao mapa pixel apresentado. O valor 255 especifica que não deve ser imposto nenhum valor alfa extra. Se o mapa de pixels incluir um canal alfa, este canal alfa será adicionado ao valor alfa do quadro. |
