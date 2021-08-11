---
title: Apêndice C - GUIX Widget Styles
description: Saiba mais sobre os estilos widget GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9519d68af64b777e34deb1bf11e6962e78a96b86bdbfd90f5b379c5b56c92268
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784653"
---
# <a name="appendix-c---guix-widget-styles"></a>Apêndice C - GUIX Widget Styles

__***Estilos Gerais (Usados com a maioria dos tipos de widget):***__

**GX_STYLE_BORDER_NONE**
  - Valor: 0x00000000
  - Descrição: Use este estilo para desenhar um widget sem fronteira.

**GX_STYLE_BORDER_RAISED**
  - Valor: 0x00000001
  - Descrição: Desenhe widget com uma borda elevada.

**GX_STYLE_BORDER_RECESSED**
  - Valor: 0x00000002
  - Descrição: Desenhe widget com uma borda embutida.

**GX_STYLE_BORDER_THIN**
  - Valor: 0x00000004
  - Descrição: Desenhe uma borda de largura de um pixel.

**GX_STYLE_BORDER_THICK** 
  - Valor: 0x00000008
  - Descrição: Desenhe widget com uma borda grossa.

**GX_STYLE_BORDER_MASK**
  - Valor: 0x0000000f
  - Descrição: Valor da máscara utilizado para testar apenas os campos de estilo do membro do estilo widget.

**GX_STYLE_TRANSPARENT**
  - Valor: 0x10000000
  - Descrição: Criar um widget que seja pelo menos parcialmente transparente. Este estilo deve ser usado quando um widget não se desenha totalmente opaco, incluindo widgets que desenham um pixelmap semi-transparente como o fundo do widget. Esta bandeira de estilo informa o GUIX que o progenitor do widget deve ser atraído para refrescar a área de fundo do widget.

**GX_STYLE_DRAW_SELECTED**
  - Valor: 0x20000000
  - Descrição: Especifique que o widget deve ser desenhado utilizando cores e tipos de letra selecionados. Diferentes tipos de widgets usam o estilo DRAW_SELECTED de diferentes maneiras para indicar que o widget está atualmente selecionado.

**GX_STYLE_ENABLED**
  - Valor: 0x40000000
  - Descrição: Marque o widget conforme ativado, o que permite ao widget aceitar eventos de entrada do utilizador e gerar sinais de saída.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Valor: 0x80000000
  - Descrição: Indica que a memória do bloco de controlo do widget é atribuída dinamicamente utilizando o serviço gx_system_memory_allocator quando o widget é criado, e a memória do bloco de controlo é libertada se o widget for destruído.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Valor: 0x01000000
  - Descrição: Instrui as funções de desenho GUIX a utilizar o valor alfa do widget local ao desenhar o widget. Esta bandeira é normalmente usada pela lógica interna do GUIX para implementar animações desvanecimento widget.


__***Estilos de alinhamento de texto (estilos aplicados a todos os widgets que desenham texto):***__

**GX_STYLE_TEXT_LEFT**
  - Valor: 0x00001000
  - Descrição: O texto é desenhado alinhado à esquerda dentro da área do cliente widget.

**GX_STYLE_TEXT_RIGHT** 
  - Valor: 0x00002000
  - Descrição: O texto é desenhado alinhado à direita dentro da área do cliente widget.

**GX_STYLE_TEXT_CENTER**
  - Valor: 0x00004000
  - Descrição: O texto é desenhado no centro alinhado dentro da área do cliente widget.

**GX_STYLE_TEXT_COPY**
  - Valor: 0x00008000
  - Descrição: Por predefinição, os widgets que desenham texto mantêm apenas um ponteiro para o texto que é transmitido pela aplicação. Para o texto estático definido que é definido dentro da tabela de cordas, não há razão para que o widget faça uma cópia privada do texto atribuído. No entanto, se o texto atribuído a um widget é criado dinamicamente usando funções como sprint() ou gx_utility_ltoa, então é muitas vezes conveniente dizer ao widget para manter a sua própria cópia privada de qualquer texto atribuído. Isto permite que a aplicação utilize variáveis automáticas ou temporárias ao definir a cadeia de texto, quando a aplicação seria necessária para definir matrizes de caracteres estáticais para cada widget de texto que está usando texto definido dinamicamente. Quando esta bandeira de estilo estiver definida, o widget utilizará a função gx_system_memory_allocator para alocar dinamicamente o bloco de memória necessário para segurar uma cópia privada da cadeia atribuída. Assim, a utilização desta bandeira de estilo baseia-se na aplicação que define funções memory_allocator e memory_deallocator. GX_STYLE_TEXT_COPY não devem ser apuradas depois de definidas, e fazê-lo provocará resultados imprevisíveis.

__***Estilos de botão (aplicar apenas aos tipos de widget de botão GUIX):***__

**GX_STYLE_BUTTON_PUSHED**
  - Valor 0x00000010
  - Descrição: Indica que o botão está no estado pressionado ou selecionado.

**GX_STYLE_BUTTON_TOGGLE**
  - Valor 0x00000020
  - Descrição: O botão mudará o estado entre pressionado e desinteressado em cada evento de clique. Este estilo é comumente usado com botões de estilo "checkbox".

**GX_STYLE_BUTTON_RADIO**
  - 0x00000040 de valor
  - Descrição: Este estilo indica que o botão será exclusivo e desmarcará quaisquer irmãos de botão quando selecionados. Este estilo é comumente usado com botões de estilo "botão de rádio".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Valor: 0x00000080
  - Descrição: Indica que o botão gera um evento de clique quando inicialmente pressionado. A operação predefinida é gerar um evento de clique quando o botão é libertado.

**GX_STYLE_BUTTON_REPEAT**
  - 0x00000100 de valor
  - Descrição: Indica que o botão deve enviar repetidos eventos de clique para o progenitor do botão quando o botão é mantido no estado de pressão.

__***Estilos de lista (aplica-se apenas aos tipos de widgets da lista GUIX):***__

**GX_STYLE_CENTER_SELECTED** 
  - Valor: 0x00000010
  - Descrição: Reservado

**GX_STYLE_WRAP**
  - Valor 0x00000020
  - Descrição: A lista de crianças embrulha do início ao fim quando a lista é arrastada ou deslocada para além do índice de lista inicial ou final.

**GX_STYLE_FLICKABLE**
  - Valor: 0x00000040
  - Descrição: Reservado

__***Estilos de botão pixelmap e botão de ícone:***__

**GX_STYLE_HALIGN_CENTER**
  - Valor: 0x00010000
  - Descrição: O mapa de pixels do botão deve estar alinhado no centro dentro do limite do botão no eixo horizontal.

**GX_STYLE_HALIGN_LEFT**
  - Valor: 0x00020000
  - Descrição: O mapa de pixels do botão deve ser deixado alinhado dentro do limite do botão no eixo horizontal.

**GX_STYLE_HALIGN_RIGHT**
  - Valor 0x00040000
  - Descrição: O mapa de pixels do botão deve estar alinhado dentro do limite do botão no eixo horizontal.

**GX_STYLE_VALIGN_CENTER**
  - Valor 0x00080000
  - Descrição: O mapa de pixels do botão deve estar alinhado no centro dentro do limite do botão no eixo vertical.

**GX_STYLE_VALIGN_TOP**
  - Valor: 0x00100000
  - Descrição: O mapa de pixels do botão deve estar alinhado no topo do limite do botão no eixo vertical.

**GX_STYLE_VALIGN_BOTTOM**
  - Valor: 0x00200000
  - Descrição: O mapa de pixels do botão deve estar alinhado no fundo dentro do limite do botão no eixo horizontal vertical.

__***Estilos de slider (Appy apenas para GX_SLIDER e tipos de widget derivado):***__

**GX_STYLE_SHOW_NEEDLE**
  - Valor: 0x00000200
  - Descrição: Este estilo deve ser incluído para que o deslizador desenhe o indicador da agulha. Este estilo pode ser desativado se a aplicação quiser desativar a agulha de slider ou desenhar um indicador de agulha personalizado.

**GX_STYLE_SHOW_TICKMARKS**
  - Valor: 0x00000400
  - Descrição: O widget de slider fará desenho de software de linhas de marca de carrapato tracejadas quando este estilo estiver ativado.

**GX_STYLE_SLIDER_VERTICAL**
  - valor 0x00000800
  - Descrição: Desata esta bandeira de estilo para criar um slider vertical e limpe esta bandeira de estilo para criar um slider horizontal.

__***Estilos Sprite (Aplica-se apenas a GX_SPRITE tipos de widget):***__

**GX_STYLE_SPRITE_AUTO**
  - Valor: 0x00000010
  - Descrição: Indica que a animação sprite funcionará automaticamente quando o widget sprite recebeu o evento GX_EVENT_SHOW.

**GX_STYLE_SPRITE_LOOP**
  - Valor: 0x00000020
  - Descrição: Com este estilo, o widget sprite irá continuamente circular através de quadros de animação sprite até que o sprite seja parado pela aplicação.

__***Estilos de slider Pixelmap:***__

**GX_STYLE_TILE_BACKGROUND**
  - 0x00001000 de valor
  - Descrição: A imagem de fundo deslizante é em azulejo para encher o retângulo de delimitação do sprite. Isto permite que uma pequena imagem de risca vertical ou horizontal seja usada para preencher o fundo do slider.

__***Estilos adicionais de barras de progresso:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Valor: 0x00000010
  - Descrição: Quando este estilo é definido, a barra de progresso irá desenhar o valor da barra em percentagem em vez de um valor bruto. O texto está centrado na barra de progresso que limita o retângulo.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Valor: 0x00000020
  - Descrição: Desenhe o valor atual da barra de progresso como texto decimal centrado na barra de progresso.

**GX_STYLE_PROGRESS_VERTICAL**
  - Valor: 0x0000040
  - Descrição: Indique que o progresso está orientado verticalmente. O padrão é orientação horizontal.

**GX_STYLE_PROGRESS_SEGMENT_FILL:**
  - **Valor**: 0x00000100
  - Descrição: O valor da barra de progresso é indicado com retângulos cheios segmentados, em vez de um enchimento sólido.

__***Estilos adicionais de barras de progresso radial:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Valor: 0x00000200
  - Descrição: Desenhe a barra de progresso radial utilizando estilos de escova anti-aliased. Isto requer mais largura de banda cpu, mas também produz uma aparência melhor. Para alvos de CPU de menor desempenho, limpar esta bandeira de estilo resultará numa velocidade de desenho mais rápida.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Valor: 0x00000400
  - Descrição: Utilize um estilo de escova final de linha redonda ao desenhar o arco da barra de progresso radial. O padrão é uma linha quadrada.

__***Estilos de entrada de texto adicionais:***__

**GX_STYLE_ CURSOR_BLINK**
  - Valor: 0x00000040
  - Descrição: O cursor widget de entrada de texto piscará ligado e desligado em vez de ser estável.

**GX_STYLE_ CURSOR_ALWAYS**
  - Valor: 0x00000080
  - Descrição. Normalmente, o cursor widget de entrada de texto só é apresentado quando o widget possui o foco de entrada. Esta bandeira de estilo tornará o cursor sempre visível independentemente do foco de entrada.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Valor: 0x00000100
  - Descrição: Com esta bandeira de estilo definir o evento GX_EVENT_TEXT_EDITED cada vez que o evento key down é recebido pelo widget de entrada de texto.

__***Estilos de janela adicionais:***__

**GX_STYLE_TILE_WALLPAPER**
  - Valor: 0x00040000
  - Descrição: A janela azulejorá qualquer imagem de papel de parede atribuída para encher o retângulo do cliente da janela.

**GX_STYLE_AUTO_HSCROLL**
  - Valor: 0x00100000
  - Descrição: Reservado para uso futuro.

**GX_STYLE_AUTO_VSCROLL**
  - Valor: 0x00200000
  - Descrição: Reservado para uso futuro.

__***Estilos de menu adicionais:***__

**GX_STYLE_MENU_EXPANDED**
  - Valor: 0x00000010
  - Descrição: O widget do menu de acordeão está inicialmente em estado expandido.

__***Estilos adicionais de vista de árvores:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Valor: 0x00000010
  - Descrição: O widget da vista da árvore deve desenhar linhas do ícone do nó para o nó de árvore de raiz.

__***Estilos adicionais de barra de deslocação:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Valor: 0x00010000
  - Descrição: Reservado para uso futuro.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Valor: 0x00020000
  - Descrição: A largura do polegar da barra de deslocação (para uma barra de deslocação horizontal) ou a altura (para uma barra de deslocação vertical) são calculadas com base na relação entre a área visível da janela dos pais e a gama de barras de deslocação de min e max.

**GX_SCROLLBAR_END_BUTTONS**
  - Valor: 0x00040000
  - Descrição: A barra de deslocação cria e fixa botões em cada extremidade da região da barra de deslocação.

**GX_SCROLLBAR_VERTICAL** 
  - Valor: 0x01000000
  - Descrição: A barra de deslocação está orientada verticalmente.

**GX_SCROLLBAR_HORIZONTAL**
  - Valor: 0x02000000
  - Descrição: A barra de deslocação está orientada horizontalmente.

__***Estilos de roda de deslocação de texto:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Valor: 0x00000200
  - Descrição: A roda de deslocação utiliza um algoritmo Sinusoidal para fazer com que a roda de deslocação pareça ter uma forma arredondada. Esta bandeira de estilo pode adicionar uma sobrecarga significativa ao desempenho do widget da roda de deslocação, mas também pode dar à roda uma aparência realista 3D.