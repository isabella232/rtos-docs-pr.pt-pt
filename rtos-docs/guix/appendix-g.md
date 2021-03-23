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
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="51209-103">Apêndice G - Estrutura de Fonte GUIX</span><span class="sxs-lookup"><span data-stu-id="51209-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="51209-104">As fontes GUIX são normalmente produzidas pela aplicação GUIX Studio, e os glifos de fonte são renderizados pelo controlador de exibição GUIX.</span><span class="sxs-lookup"><span data-stu-id="51209-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="51209-105">O software da aplicação só precisa de especificar o tipo de letra e as cores que cada widget de exibição de texto deve utilizar.</span><span class="sxs-lookup"><span data-stu-id="51209-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="51209-106">As estruturas de dados de fonte GUIX são documentadas aqui para a completude, e para permitir que os desenvolvedores criem os seus próprios métodos para gerar ou converter outros tipos de letra no formato de fonte GUIX.</span><span class="sxs-lookup"><span data-stu-id="51209-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="51209-107">Cada fonte GUIX começa com uma estrutura GX_FONT.</span><span class="sxs-lookup"><span data-stu-id="51209-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="51209-108">A estrutura GX_FONT define parâmetros globais de fonte, como o caráter incluído dentro da fonte e a altura da linha da fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="51209-109">A estrutura GX_FONT aponta para uma série de estruturas GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="51209-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="51209-110">Cada GX_GLYPH estrutura define a largura, altura e compensação de base de um glifo de carácter específico.</span><span class="sxs-lookup"><span data-stu-id="51209-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="51209-111">A estrutura GX_GLYPH também aponta para os dados do bitmap do glifo real (que podem ser NUOS para caracteres do espaço branco).</span><span class="sxs-lookup"><span data-stu-id="51209-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="51209-112">A estrutura GX_FONT, contida em gx_api.h, é declarada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="51209-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

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

<span data-ttu-id="51209-113">O campo gx_font_format define as bits de fonte por pixel e outras bandeiras, conforme definido no ficheiro de cabeçalho gx_api.h.</span><span class="sxs-lookup"><span data-stu-id="51209-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="51209-114">O gx_font_prespace define o espaço pixel para saltar acima de cada linha de texto num ecrã de texto multi-line.</span><span class="sxs-lookup"><span data-stu-id="51209-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="51209-115">O campo gx_font_postspace define o espaço do pixel para saltar abaixo de cada linha de texto num ecrã de texto multi-line.</span><span class="sxs-lookup"><span data-stu-id="51209-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="51209-116">O campo gx_font_line_height define a altura do glifo mais alto na fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="51209-117">O campo gx_font_baseline define a distância, em pixels, da linha superior dos pixeis até à linha de base da fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="51209-118">O campo gx_font_first_glyph define a primeira codificação de caracteres Unicode incluída nesta página de fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="51209-119">O campo gx_font_last_glyph define a última codificação de caracteres Unicode incluída nesta página de fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="51209-120">O ponteiro gx_font_glyphs aponta para uma série de estruturas GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="51209-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="51209-121">Esta matriz deve ser igual em tamanho ao número de caracteres contidos nesta página de fonte, ou seja,</span><span class="sxs-lookup"><span data-stu-id="51209-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="51209-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span><span class="sxs-lookup"><span data-stu-id="51209-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="51209-123">O membro gx_font_next_page é utilizado para fontes de várias páginas.</span><span class="sxs-lookup"><span data-stu-id="51209-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="51209-124">Várias páginas são usadas para conjuntos de caracteres estendidos e para otimizar o tamanho dos conjuntos de estrutura GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="51209-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="51209-125">Se todos os caracteres do tipo de letra estiverem contidos numa página de letra, ou se esta for a última página do tipo de letra em questão, o membro gx_font_next_page está definido para GX_NULL.</span><span class="sxs-lookup"><span data-stu-id="51209-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="51209-126">Como referido acima, a estrutura GX_FONT acima contém um ponteiro para uma variedade de estruturas GX_GLYPHS.</span><span class="sxs-lookup"><span data-stu-id="51209-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="51209-127">Deve haver uma estrutura GX_GLYPH para cada personagem na página do tipo de letra.</span><span class="sxs-lookup"><span data-stu-id="51209-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="51209-128">A estrutura GX_GLYPH é definida como:</span><span class="sxs-lookup"><span data-stu-id="51209-128">The GX_GLYPH structure is defined as:</span></span>

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

<span data-ttu-id="51209-129">O ponteiro gx_glyph_map aponta para o mapa do glifo.</span><span class="sxs-lookup"><span data-stu-id="51209-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="51209-130">Este ponteiro pode ser GX_NULL para caracteres do espaço branco.</span><span class="sxs-lookup"><span data-stu-id="51209-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="51209-131">Os dados do bitmap são codificados como 1 bpp, 2 bpp, 4 bpp ou 8 bpp alfa valores.</span><span class="sxs-lookup"><span data-stu-id="51209-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="51209-132">Para dados de 1 bit, um valor de 1 indica que o pixel deve ser escrito na cor de primeiro plano, e um valor de 0 indica que o pixel é transparente.</span><span class="sxs-lookup"><span data-stu-id="51209-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="51209-133">Para dados de 8 bits, os valores variam de 0 (totalmente transparente) a 255 (totalmente opague).</span><span class="sxs-lookup"><span data-stu-id="51209-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="51209-134">Todo o valor intermédio representa um valor de mistura para fontes anti-aliased.</span><span class="sxs-lookup"><span data-stu-id="51209-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="51209-135">Os dados do mapa bitmap do glifo são sempre acolchoados ao alinhamento completo do byte para formatos que utilizam valores de dados inferiores a 8bpp.</span><span class="sxs-lookup"><span data-stu-id="51209-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="51209-136">Os valores gx_glyph_ascent e gx_glyph_descent posicionam o glifo verticalmente no que diz respeito à linha de base da fonte.</span><span class="sxs-lookup"><span data-stu-id="51209-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="51209-137">Os valores gx_glyph_width e gx_glyph_height especificam o tamanho dos dados do bitmap do glifo.</span><span class="sxs-lookup"><span data-stu-id="51209-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="51209-138">O valor gx_glyph_advance especifica a largura do pixel para avançar a posição de desenho após o desenho do glifo (isto pode não ser igual à largura do glifo).</span><span class="sxs-lookup"><span data-stu-id="51209-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="51209-139">O valor gx_glyph_leading especifica os pixels para avançar na direção x antes de renderizar o glifo.</span><span class="sxs-lookup"><span data-stu-id="51209-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>