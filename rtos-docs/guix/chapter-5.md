---
title: Capítulo 5 - Condutores de exibição GUIX
description: Os controladores do GUIX Display definem a interface de software entre a tela de desenho abstrato e o hardware de exibição física.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 804187ce8562e274205e97448da77d29f99016072c137cb3c4f1f42dac58c432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788546"
---
# <a name="chapter-5---guix-display-drivers"></a>Capítulo 5 - Condutores de exibição GUIX

Os controladores do GUIX Display definem a interface de software entre a tela de desenho abstrato e o hardware de exibição física. O controlador de visualização GUIX implementa as funções de desenho de nível mais baixo que realmente alteram a informação de cor de pixel na memória de tela e transferem a memória de tela para o tampão de moldura de exibição física em sistemas com tampão duplo.

Os controladores do VISOR GUIX são definidos por uma estrutura que contém os parâmetros de visualização física e um conjunto de ponteiros de função para as funções do controlador de baixo nível. Ao utilizar estes ponteiros de função indireto, as funções de desenho de tela abstrata e widget são completamente independentes dos detalhes do hardware.

O GUIX fornece um conjunto completo, totalmente funcional, de funções de desenho para cada formato de profundidade e cor suportado. Ao implementar um controlador de ecrã sem capacidade específica de aceleração de hardware ou outras considerações específicas do hardware, estas funções de desenho predefinido são normalmente suficientes para a implementação final do controlador. Para estes condutores mais simples, a única função que normalmente precisa de ser implementada no software do condutor é uma função para configurar o dispositivo de hardware. Isto envolve frequentemente a inicialização de vários registos de hardware para definir o relógio de exibição LCD, as dimensões do ecrã, etc. Para todas as outras funções, a implementação do controlador simplesmente inicializa os ponteiros de função GX_DISPLAY para as implementações da função predefinido para a profundidade e formato de cor desejados.

Ao implementar um controlador de exibição personalizado, a melhor prática é primeiro inicializar os ponteiros da função de design do controlador de ecrã com a implementação padrão do software para a profundidade de cor que pretende suportar e, em seguida, substituir os ponteiros de função sempre que pretenda ligar para as implementações da função personalizada (se houver). Para ajudar com isto, existe uma função de configuração predefinida disponível para cada profundidade e formato de cor suportados. Por exemplo, se estiver a escrever um controlador de ecrã RGB de formato 5:6:5 bit 5:5, a primeira coisa que o seu controlador personalizado normalmente faria é invocar a rotina de configuração genérica para esta profundidade de cor:

UINT my_custom_565_display_driver(GX_DISPLAY *display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

O parâmetro my_buffer_toggle acima é um ponteiro para a função de tampão do controlador do controlador de visualização (que pode ser GX_NULL se o seu condutor estiver limitado e se desenhar diretamente para o tampão da moldura do hardware).

Se estiver a escrever um controlador de exibição personalizado, terá de incluir o ficheiro de cabeçalho gx_display.h na sua fonte personalizada do controlador, que é um ficheiro de cabeçalho de utilização interna que não está disponível para o software de nível de aplicação.

As funções de desenho do nível de visualização GUIX recebem como entrada um ponteiro para uma estrutura **GX_DRAW_CONTEXT.** A estrutura **GX_DRAW_CONTEXT** define as coordenadas de recorte para a operação de desenho atual, juntamente com a escova e as cores que estão sendo usadas. Cada função de desenho recebe como parâmetros adicionais de entrada específicos dos requisitos de função.

A assinatura do ponto de entrada do condutor **GX_DISPLAY** é definida como

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

Embora o nome desta função esteja completamente à altura do implementor, a convenção para os controladores fornecidos com GUIX é utilizar um nome específico do dispositivo de hardware no campo e formato de cor para o <device> <format> campo acima.

Esta função deve inicializar a estrutura **GX_DISPLAY** fornecida como entrada e executar qualquer configuração de hardware que seja necessária. A estrutura **GX_DISPLAY** contém os seguintes campos.

| &nbsp; |
| --- | --- |
| gx_display_id ULONG <br/> Este é um campo para utilização pela aplicação, nos casos em que é criado mais de um caso de um determinado condutor. |
| CHAR *gx_display_name <br/> Um nome opcional usado para identificar o motorista. |
| GX_DISPLAY *gx_display_created_next <br/> Este campo é inicializado pelo GUIX, e é usado para criar e manter uma lista de todos os GX_DISPLAY instâncias. |
| GX_DISPLAY *gx_display_created_previous <br/> Este campo é inicializado pelo GUIX, e é usado para criar e manter uma lista de todos os GX_DISPLAY instâncias. |
| GX_VALUE gx_display_color_format <br/> Este campo deve refletir o formato de dados gráficos suportado por este controlador. Os tipos de formato de cor são definidos no ficheiro cabeçalho gx_api.h. |
| GX_VALUE gx_display_width <br/> Este campo deve ser inicializado para manter a largura de exibição física em pixels. |
| GX_VALUE gx_display_height <br/> Este campo deve ser inicializado para manter a altura de visualização física, em pixels. |
| GX_COLOR *gx_display_color_table <br/> Este é um ponteiro para uma tabela usada para converter valores de identificação de cor para valores de cor específicos do formato. |
| GX_PIXELMAP *gx_display_pixelmap_table <br/> Este é um ponteiro para a tabela de mapas de pixels ativos para este visor. |
| GX_FONT *gx_display_font_table <br/> Este é um ponteiro para a tabela de fontes ativa para este visor. |
| GX_COLOR *gx_display_palette <br/> Para os controladores do modo paleta, este é um ponteiro para a paleta de cores ativa. Para condutores que não usam uma paleta de cores, este ponteiro é GX_NULL. |
| gx_display_pixelmap_table_size UINT <br/> Número de entradas na tabela de mapas de pixels ativos. |
| gx_display_font_table_size UINT <br/> Número de entradas na tabela de fontes ativa. |
| gx_display_palette_size UINT <br/> Número de entradas na paleta de cores (se houver). |
| gx_display_handle da ULONG <br/> Um identificador único, ou *pega,* que especifica o visor.
| gx_display_driver_ready UINT <br/> Este campo é utilizado para sinalizar o GUIX quando o controlador estiver pronto para funcionar. Em alguns casos, o condutor pode necessitar de vários níveis de inicialização e configuração, período durante o qual o GUIX não deve tentar utilizar o condutor. Esta bandeira deve ser definida para 1 quando o condutor estiver pronto para atender os pedidos de desenho. |
| VOID *gx_display_driver_data <br/> Este campo destina-se a ser utilizado pela implementação do condutor. Se o condutor precisar de criar e fazer referência a informações adicionais não disponíveis na estrutura GX_DISPLAY, o condutor deverá atribuir espaço e apontar para estes dados adicionais utilizando este campo de estrutura. Um exemplo de dados extra específicos do condutor pode incluir o canal DMA a ser utilizado pelo condutor ou pelo canal SPI ao qual o tampão do quadro do visor está ligado. |
| VOID (*gx_display_driver_drawing_initiate)(estrutura GX_DISPLAY_STRUCT *display, struct GX_CANVAS_STRUCT *tela) <br/> Este é um ponteiro de função que, se não NU, é invocado pela função gx_canvas_drawing_initiate. Para os controladores de exibição que utilizam uma lista de visualizações de gráficos de acelerador gráficos ou de hardware, esta função pode ser usada para iniciar uma nova lista de visualizações. Este ponteiro de função pode ser NU. |
| VOID (*gx_display_driver_palette_set)(struct GX_DISPLAY_STRUCT *display, GX_COLOR *paleta, contagem INT) <br/> Este é um ponteiro para uma função para instalar uma paleta de cores. Esta função é NU, a menos que o condutor opere em modo paleta (também chamada de tabela de procuração de cores ou CLUT). |
| VOID (*gx_display_driver_simple_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INTy1, INT x2, INT y2) <br/> Este é um ponteiro para uma função para implementar o desenho de linha genérica, sem anti-aliasing. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_simple_wide_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INTy1, INT x2, INT y2) <br/> Este é um ponteiro para uma função para implementar desenho de linha larga genérica, sem anti-aliasing. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INTy1, INT x2, INT y2) <br/> Este é um ponteiro para uma função para implementar desenho de linha anti-aliased genérico. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_wide_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INTy1, INT x2, INT y2) <br/> Este é um ponteiro para uma função para implementar o desenho de linha larga anti-aliased genérica. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_horizonal_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INT x2, INT y) <br/> Este é um ponteiro para uma função para implementar o caso especial de desenho de linha horizontal. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_horizonal_pixelmap_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INT x2, INT y, GX_PIXELMAP *mapa) <br/> Este é um ponteiro para uma função para implementar o desenho de uma única linha de pixelmap. Esta função é utilizada internamente para formas de enchimento de padrões. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_vertical_line_draw)(GX_DRAW_CONTECT *contexto, INT y1, INT y2, INT x) <br/> Este é um ponteiro para uma função para implementar o caso especial de desenho de linha horizontal. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_horizonal_pattern_line_draw)(GX_DRAW_CONTECT *contexto, INT x1, INT x2, INT y) <br/> Este é um ponteiro para uma função para implementar o desenho da linha de padrão horizontal. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_vertical_pattern_line_draw)(GX_DRAW_CONTECT *contexto, INT y1, INT y2, INT x) <br/> Este é um ponteiro para uma função para implementar o desenho de linha de padrão vertical. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_canvas_copy)(estrutura GX_CANVAS_STRUCT *fonte, estrutura GX_CANVAS_STRUCT *dest) <br/> Este é um ponteiro para uma função para copiar dados de tela de uma tela para outra. O retângulo inválido de lona de origem é utilizado para definir a área de cópia. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_canvas_blend)(estrutura GX_CANVAS_STRUCT *fonte, estrutura GX_CANVAS_STRUCT *dest) <br/> Este é um ponteiro para uma função de alfa-blend dados de tela da tela de origem com os dados existentes na tela de destino. O retângulo inválido de lona de origem é utilizado para definir a área de mistura. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_pixelmap_blend)(GX_DRAW_CONTEXT *contexto, INT xpos, INT ypos, GX_PIXELMAP *pmp, GX_UBYTE alfa) <br/> Este é um ponteiro para uma função para misturar um mapa de pixels na tela de fundo definida pelo contexto de desenho. O valor alfa fornecido pode ser além de um canal alfa contido nos dados do pixelmap. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_pixelmap_draw)(GX_DRAW_CONTEXT *contexto, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Este é um ponteiro para uma função para desenhar um pixelmap na tela definida pelo contexto de sorteio. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_jpeg_draw)(GX_DRAW_CONTEXT *contexto, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Este é um ponteiro para uma função para descodificar uma imagem jpg e torná-la diretamente para a tela. Esta função só é fornecida se GX_SOFTWARE_DECODER_SUPPORT for definida. Este ponteiro de função um SER NU. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_png_draw)(GX_DRAW_CONTEXT *contexto, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Este é um ponteiro para uma função para descodificar uma imagem de png e torná-la diretamente para a tela. Esta função só é fornecida se GX_SOFTWARE_DECODER_SUPPORT for definida. Este ponteiro de função um SER NU. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_pixelmap_rotate)(GX_DRAW_CONTEXT *contexto, INT xpos, INT ypos, GX_PIXELMAP *pmp INT angle, INT rot_cx, INT rot_cy) <br/> Este é um ponteiro para uma função para rodar um pixemap e tornar o resultado diretamente para a tela. Esta função é invocada pela gx_canvas_pixelmap_rotate as implementações da APIDefault desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID *gx_display_driver_pixel_write)(GX_DRAW_CONTEXT *contexto, INT x, INT y, GX_COLOR cor) <br/> Este é um ponteiro para uma função para escrever um pixel na memória de tela. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. <br/>
| VOID *gx_display_driver_block_move)(GX_DRAW_CONTEXT *context,GX_RECTANGLE *bloco, INT xshift, INT yshift) <br/> Este é um ponteiro para uma função para mover ou deslocar um bloco de pixels dentro de uma tela. Esta função é utilizada principalmente para deslocar rapidamente um conteúdo da janela. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_pixel_blend)(GX_DRAW_CONTEXT *contexto, INT x, INT y, GX_COLOR cor, GX_UBYTE alfa) <br/> Esta função é usada para misturar alfa-blend o valor de cor do pixel de entrada com o valor de cor existente na memória de tela na posição x,y. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| GX_COLOR (*gx_display_driver_native_color_get)(GX_COLOR crucão) <br/> Esta função converte uma cor do formato de cor A:R:G:B de 32 bits utilizado internamente pelo GUIX para o formato de cor nativa da tela e do ecrã. Espera-se alguma perda de informação de cor para os controladores de exibição que correm a profundidades de cores mais baixas. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| USHORT (*gx_display_driver_row_pitch_get)(largura USHORT) <br/> Devolve a contagem de byte ou passo de uma linha de dados gráficos dada a largura de lona solicitada. Esta função é usada para calcular o tamanho da área de memória necessária para criar uma tela. O tom e a largura da linha nem sempre são os mesmos devido às restrições de alinhamento da linha de hardware. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_buffer_toggle)(struct GX_CANVAS_STRUCT *tela, GX_RECTANGLE *dirty_area) <br/> Este é um ponteiro para uma função de alternar entre os buffers de moldura funcional e visível para sistemas de memória com tampão duplo. Esta função deve primeiro instruir o hardware a começar a utilizar o novo tampão de armação e, em seguida, copiar a parte modificada do novo tampão visível para o tampão de companhia, para garantir que os dois tampão permaneçam sincronizados. | 
| VOID (*gx_display_driver_polygon_draw)(GX_DRAW_CONTEXT *contexto, INT num_points, GX_POINT *vértices <br/> Ponteiro para uma função para desenhar um polígono. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_polygon_fill)(GX_DRAW_CONTEXT *contexto, INT num_points, GX_POINT *vértices <br/> Ponteiro para uma função para desenhar um polígono preenchido. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_circle_draw)(GX_DRAW_CONTEXT *contexto, int xcenter, INT ycenter, UINT r) <br/> Ponteiro para uma função para desenhar um círculo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r) <br/> Ponteiro para uma função para desenhar um círculo anti-aliased. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_wide_circle_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r) <br/> Ponteiro para uma função para desenhar um círculo com um esboço largo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *contexto, int xcenter, INT ycenter, UINT r) <br/> Ponteiro para uma função para desenhar um círculo anti-aliased com um contorno largo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_circle_fill)(GX_DRAW_CONTEXT *contexto, int xcenter, INT ycenter, UINT r) <br/> Ponteiro para uma função para desenhar um círculo preenchido. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_arc_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Ponteiro para uma função para desenhar um arco. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_arc_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Ponteiro para uma função para desenhar um arco anti-aliased. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_wide_arc_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Ponteiro para uma função para desenhar um arco com um contorno largo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_wide_arc_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Ponteiro para uma função para desenhar um arco anti-aliased. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_arc_fill)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Ponteiro para uma função para desenhar um arco cheio. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_pie_fill)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Ponteiro para uma função para desenhar uma tarte cheia. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_ellipse_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, INT a, INT b) <br/> Ponteiro para uma função para desenhar uma elipse. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_ellipse_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, INT a, INT b) <br/> Ponteiro para uma função para desenhar uma elipse. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_wide_ellipse_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, INT a, INT b) <br/> Ponteiro para uma função para desenhar uma elipse com um esboço largo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_anti_aliased_wide_ellipse_draw)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, INT a, INT b) <br/> Ponteiro para uma função para desenhar uma elipse com um esboço largo. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_ellipse_fill)(GX_DRAW_CONTEXT *contexto, INT xcenter, INT ycenter, INT a, INT b) <br/> Ponteiro para uma função para desenhar uma elipse preenchida. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_8bit_glyph_draw)(GX_DRAW_CONTEXT *contexto, GX_RECTANGLE *draw_area, GX_POINT *map_offset, constGX_GLYPH *glifo) <br/> Ponteiro para funcionar para desenhar um glifo de texto de 8 bits para a tela usando a escova do contexto de desenho atual. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_4bit_glyph_draw)(GX_DRAW_CONTEXT *contexto, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glifo) <br/> Ponteiro para funcionar para desenhar um glifo de texto de 4 bits para a tela usando a escova do contexto de desenho atual. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |
| VOID (*gx_display_driver_1bit_glyph_draw)(GX_DRAW_CONTEXT *contexto, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glifo) <br/> Ponteiro para funcionar para desenhar um glifo de texto monocromático de 1 bit para a tela usando a escova do contexto de desenho atual. As implementações predefinidas desta função são fornecidas para cada formato de profundidade e cor suportado. |


