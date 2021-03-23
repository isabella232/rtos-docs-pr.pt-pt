---
title: Notas sobre edição de tipos específicos de widget
description: Comentários detalhados que descrevem métodos de edição para certos tipos complexos de widgets.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3194a1b8c8965bf821631a8c34ac5e9961f8c8ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827127"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Capítulo 8: Notas sobre edição de tipos específicos de widgets

O GUIX Studio permite ao utilizador criar e modificar facilmente widgets GUIX que componham os ecrãs UI da aplicação. A maioria destes métodos de edição são intuitivos e óbvios. Por exemplo, para redimensionar um widget pode selecionar o widget com o rato e arrastar as bordas do widget. Também pode digitar diretamente nos campos de propriedade esquerda/topo/largura/altura do widget selecionado.

Certos tipos de widgets requerem um processo de edição mais avançado, porque estes widgets são eles próprios um pouco mais sofisticados no seu suporte de funcionalidade.

Este capítulo fornece notas sobre as funcionalidades de edição mais avançadas para estes tipos de widget mais complexos. Estas notas expandir-se-ão à medida que as características do GUIX Studio avançam juntamente com os tipos de widget fornecidos dentro da biblioteca GUIX.

## <a name="rich-text-view"></a>Vista de texto rico

Este widget é utilizado para exibir textos ricos que suporta códigos de formatação de texto inline. Estes códigos de formatação incluem negrito, itálico, e vários outros. Para começar, clique com o pai selecionado a partir do *Project View* ou *Target View* e selecione o menu **Inserir/Texto/Vista de Texto Rico** para inserir um widget de visualização de texto rico.

Além do conjunto padrão de propriedades suportadas por todos os tipos de widgets, o tipo de widget Rich Text View suporta propriedades adicionais.

### <a name="additional-properties"></a>Propriedades Adicionais

| Propriedade | Significado |
|----------|---------|
| Alinhamento de texto | Alinhamento de texto predefinido |
| Fonte normal| Fonte de texto predefinido |
| Fonte arrojada  | Fonte de texto para texto marcado como arrojado |
| Fonte itálica| Fonte de texto para texto marcado como itálico|
| Fonte itálica ousada| Fonte de texto para texto marcado como arrojado e itálico |
| Cópia de texto privada | Deve ser verificado se o widget é para manter a sua própria cópia privada de qualquer texto atribuído |
| Espaço em branco | Largura de margem entre o widget e o texto apresentado, em pixels. |
| Espaço linha | Espaço entre duas linhas do texto, em pixels. |
|||

### <a name="the-rich-text-formatting-codes"></a>Os códigos de formatação do Texto Rico

Os seguintes códigos de formato são suportados para formatação de texto.

|Etiqueta|Significado|
|---|---|
|\<b>\</b> | Renderizar fonte de texto com iD de fonte em negrito especificado pelo utilizador|
|\<i>\</i> | Entregar fonte de texto com iD de fonte itálica especificado do utilizador|
|\<u>\</u> | Texto sublinhado por renderização|
|\<f GX_FONT_ID>\</f> | Rendere texto utilizando o ID de letra especificado. |
|\<c GX_COLOR_ID>\</c> | Renderizar texto usando o ID de cor especificado|
|\<hc GX_COLOR_ID>\</hc> | Renderizar texto usando o ID de cor de fundo especificado|
|\<align left/right/center>\</align> | Atribuir alinhamento de texto|
|||

Existem duas maneiras de editar a rica cadeia de texto de dentro do GUIX Studio:

- Utilize o diálogo Editar Texto Rico, que é o método de edição recomendado e mais simples.
- Utilize o diálogo do Editor de Tabela de Cordas, que lhe permite inserir manualmente as etiquetas de formatação mostradas na tabela anterior.

Depois de selecionar um widget Rich Text View na *Vista Alvo,* selecione o botão **Editar Texto Rico** na Vista *Propriedades* para invocar o diálogo de edição de texto rico, mostrado na Figura 8.1.

![Screenshot do diálogo de texto rico do estúdio GUIX Edit.](./media/guix-studio/edit_rich_text_dialog.png)

**Figura 8.1**

O painel esquerdo é o rico campo de edição de texto. Pode utilizar os ícones da barra de ferramentas para ajudar a inserir as etiquetas que necessita. Selecione qualquer bloco de texto no campo de edição e, em seguida, selecione os botões da barra de ferramentas para aplicar os estilos e cores necessários no bloco de texto selecionado. O diálogo Editar Texto Rico é uma maneira fácil de inserir os códigos de formatação na cadeia de teste. Também pode inserir estas etiquetas manualmente ou até mesmo gere-las em tempo de execução, se necessário.

O painel de direita é a pré-visualização do widget para mostrar como o texto é renderizado na vista alvo. A cor de fundo da pré-visualização do widget é fixada, o que pode não corresponder à cor de fundo atribuída pelo widget na vista do alvo.

Os nomes de ID de recursos são usados em texto rico para referenciar recursos específicos de fonte ou cor. Se o nome de recurso de um tipo de letra ou cor for alterado depois de ter sido referenciado pela cadeia de texto rica, o GUIX Studio atualizará automaticamente a cadeia de texto rica para refletir as alterações no nome do recurso. Por outro lado, se eliminar um recurso de letra ou cor que seja referenciado por um widget de texto rico, deve editar manualmente o texto rico afetado para remover ou alterar os nomes de identificação de recursos que foram eliminados.

Quando selecionar o botão Guardar neste diálogo, a cadeia de texto rica que definiu é adicionada à tabela de cordas do projeto.

## <a name="string-scroll-wheel"></a>Roda de pergaminho de corda

Um widget de roda de roda de roda de fio suporta a exibição de uma variedade de cordas. Estas cordas podem ser atribuídas dinamicamente, ou, no caso de a aplicação suportar várias línguas, as cordas atribuídas podem ser retiradas da tabela de cordas ativa.

O widget da roda de rolo de corda suporta uma variedade de cordas. O diálogo de edição de roda de deslocação de cordas, apresentado na Figura 8.2, é fornecido para permitir ao utilizador atribuir esta matriz de cordas.

![Screenshot do diálogo guix Studio String Scroll Wheel Edit.](./media/guix-studio/string_scroll_wheel_edit.png)

**Figura 8.2**

Para invocar este diálogo, selecione um widget de roda de deslocação de cordas dentro da *Vista Alvo* ou da Vista do *Projeto*. Uma vez selecionado este tipo de widget, o *View Propriedades* incluirá um botão **editar cordas.** Selecione este botão para invocar o diálogo de edição de roda de deslocação de cordas.

Para atribuir uma cadeia para cada índice de texto, pode selecionar um ID de cadeia da lista de recuos ou pode digitar um novo valor de corda no campo Texto à direita. Quando terminar as alterações, quaisquer cordas novas ou modificadas são guardadas na tabela de cordas ativa.

## <a name="sprite"></a>Sprite

Um widget sprite é usado para exibir uma sequência de imagens para fornecer um efeito de animação. Um widget sprite requer uma lista de quadros, que é uma matriz de IDs de imagem e parâmetros únicos aplicados a cada imagem no quadro. Para construir esta lista de quadros para o widget sprite, o diálogo Edit Sprite Frames, mostrado na figura 8.3, é fornecido:

![Screenshot do diálogo GUIX Studio Edit Sprite Frames.](./media/guix-studio/edit_sprite_frames.png)

**Figura 8.3**

Para invocar este diálogo, selecione um widget sprite dentro da *Vista Alvo* ou da Vista do *Projeto*. Uma vez selecionado este tipo de widget, o *'View' Properties* incluirá um botão **Editar Framelist.** Selecione este botão para invocar o diálogo de edição de roda de deslocação de cordas.

O *número total de quadros sprite* é um campo de entrada que lhe permite introduzir o número total inteiro de quadros a exibir pelo widget sprite. As imagens podem ser reutilizadas dentro da lista de quadros, o que significa que nem todas as imagens devem ser únicas.

O campo de ID do quadro sprite é um valor de seleção de índice de quadro que varia de 1 a número total de Quadros. Incrementar e Decrement este valor para passar de uma moldura sprite para a seguinte.

Cada armação sprite tem vários parâmetros. A primeira é a Operação de Fundo. Este campo imita as capacidades do popular formato de animação GIF. As escolhas aqui incluem:

- Nenhuma operação, o que significa que a imagem do quadro atual é desenhada sobre a imagem do quadro anterior.
- Restaurar o primeiro pixel-mapa, o que significa que o índice 1 pixel-map é desenhado antes do mapa de pixels atual e
- Enchimento de cor sólida, o que significa que o fundo do sprite é preenchido com a cor de fundo do sprite antes da moldura atual ser desenhada.

O campo ID do mapa Pixel permite-lhe selecionar qualquer mapa de pixels previamente adicionado aos recursos do projeto. O mesmo ID do mapa de pixels pode ser usado para vários quadros. Por exemplo, a sua animação sprite pode utilizar o movimento da imagem (utilizando os campos x e y offset) em vez de ou para além de usar diferentes imagens de sprite.

O campo de valor Alfa é aplicado a todo o desenho do mapa de pixels. Este campo só tem um efeito quando funciona a 8 bpp de profundidade de cor e superior. O valor alfa 0 é totalmente transparente, e o valor alfa 255 é opaco.

Pode especificar uma compensação dentro do quadro de sprite em que o mapa de pixels atual será desenhado utilizando os campos Frame x-offset e Frame y-offset. Por outras palavras, cada imagem desenhada não tem de ser o tamanho total do widget sprite.

O período de atraso especifica o tempo a atrasar antes de passar para a próxima armação do sprite. Este valor está em tiques, que para a configuração padrão do temporizador GUIX/ThreadX cada carrapato representa 50 ms.

Quando guarda as alterações no diálogo Editar Sprite Frames, o GUIX Studio é capaz de gerar o conjunto completo da lista de quadros como parte da geração de ficheiros de especificações de saída.
