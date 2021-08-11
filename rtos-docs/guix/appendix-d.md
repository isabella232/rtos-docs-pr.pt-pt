---
title: Apêndice D - GuiX Brush, Lona e Atributos Gradiente
description: Saiba mais sobre os atributos guix, lona e gradiente.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9fbc98f1094cab6be4bc0826fef7c0feb77b50b066b22342cd52404bd85ff98e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784636"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a>Apêndice D - GuiX Brush, Lona e Atributos Gradiente

__**Estilos de escova:**__

**GX_BRUSH_OUTLINE**
- Valor: 0x0000
- Descrição: Este estilo de escova aplica-se a funções de desenho de formas como gx_canvas_rectangle_draw ou gx_canvas_polygon_draw. Este estilo indica que a forma deve ser delineada, além de ser opcionalmente preenchido. Se o estilo GX_BRUSH_OUTLINE estiver definido e o GX_BRSUH_SOLID_FILL estiver limpo, a forma é apenas delineada.

**GX_BRUSH_SOLID_FILL**
- Valor: 0x0001
- Descrição: Este estilo de escova aplica-se às funções de desenho de forma, e indica que a forma solicitada deve ser preenchida com uma cor sólida utilizando a cor de preenchimento da escova atual.

**GX_BRUSH_PIXELMAP_FILL**
- Valor: 0x0002
- Descrição: Este estilo de escova aplica-se às funções de desenho de forma, e indica que a forma solicitada deve ser preenchida com o pixelmap de escova atual.

**GX_BRUSH_ALIAS**
- Valor: 0x0004
- Descrição: Este estilo de escova aplica-se a todos os contornos de desenho e forma de linha. Se esta bandeira for definida, linhas e contornos estão a desenhar com os algoritmos de desenho anti-aliased mais precisos, mas também mais demorados. Esta bandeira de estilo é usada apenas para profundidades de cores de 16 bpp e mais alta.

**GX_BRUSH_UNDERLINE**
- Valor: 0x0008
- Descrição: Esta bandeira aplica-se ao desenho de texto e indica que o texto posterior desenhado deve ser sublinhado.

**GX_BRUSH_ROUND**
- Valor: 0x0010
- Descrição: Esta bandeira aplica-se ao desenho de linhas e indica que as extremidades da linha são desenhadas com uma forma redonda ou circular, em vez da forma quadrada padrão.

__**Bandeiras de lona:**__

**GX_CANVAS_SIMPLE**
- Valor: 0x01
- Descrição: Uma tela de memória que é usada para desenhar fora do ecrã.

**GX_CANVAS_MANAGED**
- Valor: 0x02
- Descrição: Uma tela que se despedace automaticamente para o visor ativo, quer como parte do processo de construção composta, quer como parte do funcionamento do tampão para arquiteturas de tela única.

**GX_CANVAS_VISIBLE**
- Valor: 0x04
- Descrição: Esta bandeira pode ser usada para ligar e sair de uma tela, sem perder o conteúdo de desenho de tela.

**GX_CANVAS_MODIFIED**
- Valor: 0x08
- Descrição: Reservado para uso futuro.

**GX_CANVAS_COMPOSITE**
- Valor: 0x20
- Descrição: Esta bandeira é utilizada pela aplicação ao configurar um sistema de múltiplas telas que compôs várias telas geridas na tela composta, e o composto é o acionado para o tampão de quadro de hardware.

__**Tipos de gradiente:**__

**GX_GRADIENT_TYPE_VERTICAL**
- Valor: 0x01
- Descrição: Cria um gradiente alfamap vertical.

**GX_GRADIENT_TYPE_ALPHA**
- Valor: 0x02
- Descrição: Creats um gradiente de estilo de mapa alfa. Este é atualmente o único estilo gradiente suportado.

**GX_GRADIENT_TYPE_MIRROR**
- Valor: 0x04
- Descrição: Esta bandeira indica que o gradiente deve atingir o pico no centro da gama largura/altura e voltar ao valor inicial à medida que atinge a borda direita/inferior. Sem esta bandeira de estilo, o gradiente será um gradiente linear de cima para baixo ou da esquerda para a direita, dependendo da bandeira GX_GRADIENT_TYPE_VERTICAL.