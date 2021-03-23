---
title: Apêndice G - Estrutura de Fonte GUIX
description: Conheça a estrutura de fonte GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827266"
---
# <a name="appendix-g---guix-font-structure"></a>Apêndice G - Estrutura de Fonte GUIX

As fontes GUIX são normalmente produzidas pela aplicação GUIX Studio, e os glifos de fonte são renderizados pelo controlador de exibição GUIX. O software da aplicação só precisa de especificar o tipo de letra e as cores que cada widget de exibição de texto deve utilizar. As estruturas de dados de fonte GUIX são documentadas aqui para a completude, e para permitir que os desenvolvedores criem os seus próprios métodos para gerar ou converter outros tipos de letra no formato de fonte GUIX.

Cada fonte GUIX começa com uma estrutura GX_FONT. A estrutura GX_FONT define parâmetros globais de fonte, como o caráter incluído dentro da fonte e a altura da linha da fonte. A estrutura GX_FONT aponta para uma série de estruturas GX_GLYPH. Cada GX_GLYPH estrutura define a largura, altura e compensação de base de um glifo de carácter específico. A estrutura GX_GLYPH também aponta para os dados do bitmap do glifo real (que podem ser NUOS para caracteres do espaço branco).

A estrutura GX_FONT, contida em gx_api.h, é declarada da seguinte forma:

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

O campo gx_font_format define as bits de fonte por pixel e outras bandeiras, conforme definido no ficheiro de cabeçalho gx_api.h.

O gx_font_prespace define o espaço pixel para saltar acima de cada linha de texto num ecrã de texto multi-line.

O campo gx_font_postspace define o espaço do pixel para saltar abaixo de cada linha de texto num ecrã de texto multi-line.

O campo gx_font_line_height define a altura do glifo mais alto na fonte.

O campo gx_font_baseline define a distância, em pixels, da linha superior dos pixeis até à linha de base da fonte.

O campo gx_font_first_glyph define a primeira codificação de caracteres Unicode incluída nesta página de fonte.

O campo gx_font_last_glyph define a última codificação de caracteres Unicode incluída nesta página de fonte.

O ponteiro gx_font_glyphs aponta para uma série de estruturas GX_GLYPH. Esta matriz deve ser igual em tamanho ao número de caracteres contidos nesta página de fonte, ou seja, (gx_font_last_glyph – gx_font_first_glyph) + 1.

O membro gx_font_next_page é utilizado para fontes de várias páginas. Várias páginas são usadas para conjuntos de caracteres estendidos e para otimizar o tamanho dos conjuntos de estrutura GX_GLYPH. Se todos os caracteres do tipo de letra estiverem contidos numa página de letra, ou se esta for a última página do tipo de letra em questão, o membro gx_font_next_page está definido para GX_NULL.

Como referido acima, a estrutura GX_FONT acima contém um ponteiro para uma variedade de estruturas GX_GLYPHS. Deve haver uma estrutura GX_GLYPH para cada personagem na página do tipo de letra. A estrutura GX_GLYPH é definida como:

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

O ponteiro gx_glyph_map aponta para o mapa do glifo. Este ponteiro pode ser GX_NULL para caracteres do espaço branco. Os dados do bitmap são codificados como 1 bpp, 2 bpp, 4 bpp ou 8 bpp alfa valores. Para dados de 1 bit, um valor de 1 indica que o pixel deve ser escrito na cor de primeiro plano, e um valor de 0 indica que o pixel é transparente. Para dados de 8 bits, os valores variam de 0 (totalmente transparente) a 255 (totalmente opague). Todo o valor intermédio representa um valor de mistura para fontes anti-aliased. Os dados do mapa bitmap do glifo são sempre acolchoados ao alinhamento completo do byte para formatos que utilizam valores de dados inferiores a 8bpp.

Os valores gx_glyph_ascent e gx_glyph_descent posicionam o glifo verticalmente no que diz respeito à linha de base da fonte.

Os valores gx_glyph_width e gx_glyph_height especificam o tamanho dos dados do bitmap do glifo.

O valor gx_glyph_advance especifica a largura do pixel para avançar a posição de desenho após o desenho do glifo (isto pode não ser igual à largura do glifo).

O valor gx_glyph_leading especifica os pixels para avançar na direção x antes de renderizar o glifo.