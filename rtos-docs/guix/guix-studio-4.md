---
title: Recursos do Estúdio GUIX
description: O GUIX Studio fornece gestão de todos os recursos de UI que a aplicação usará para cores, fontes, pixel-maps e cordas. As secções que se seguem descrevem como adicionar, modificar e eliminar recursos dentro do seu design de ecrã de UI.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd694cb7d34df7ecae206c3dcaf7d75a20bd4bd4e26471bb94da4129897ef727
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786149"
---
# <a name="chapter-4-guix-studio-resources"></a>Capítulo 4: GUIX Studio Resources

O GUIX Studio fornece gestão de todos os recursos de UI que a aplicação usará para cores, fontes, pixel-maps e cordas. As secções que se seguem descrevem como adicionar, modificar e eliminar recursos dentro do seu design de ecrã de UI. 

Toda a gestão de recursos é feita dentro da ***Vista de Recursos** _ do GUIX Studio UI, como mostrado abaixo em _* Figura _8_**.

![Screenshot da visão de recursos do estúdio GUIX.](./media/guix-studio/image38.jpg)

**Figura 8**

## <a name="color-resources"></a>Recursos de Cor

A secção ***Cores** _ da Vista de _*_Recursos_*_ permite-lhe gerir os seus recursos coloridos. Pode expandir esta vista clicando no campo _ *+* * no cabeçalho de vista, resultando na vista mostrada abaixo na **_Figura 9_**:

![Screenshot da secção Cores da Vista de Recursos](./media/guix-studio/image_39.png)

**Figura 9**

Os recursos de cor consistem de uma ou mais cores, cada uma com um nome lógico único. Por exemplo, na **Figura 9** o nome lógico **CANVAS,** que é o ID de cor do sistema para a cor de preenchimento de fundo do ecrã, está associado com a cor física preta. Este recurso de cor é utilizado sempre que a aplicação especifica **GX_COLOR_ID_CANVAS** como a cor nas propriedades do objeto.

A cor "swatch" indicando o valor RGB de cor é mostrada à esquerda, seguida pelo nome de ID de cor. Pode alterar o valor RGB associado a qualquer nome de ID a qualquer momento. Não é possível alterar os nomes de identificação de cores do sistema pré-definidos porque estes são utilizados internamente pela biblioteca GUIX. No entanto, pode alterar qualquer um dos valores de cor. Alterar o valor da cor do sistema é uma **mudança global.** Isto significa que qualquer widget que não tenha uma atribuição de cores específica assumirá o novo valor de cor do sistema.

Pode alterar tanto o nome de cor como o valor de cor para cores personalizadas que adicionou ao Tema.

Para modificar um recurso de cor, clique duas vezes (ou clique à direita e selecione menu) no recurso de cor. Esta ação traz o diálogo de definição de cores. A partir deste diálogo, o recurso de cor pode ser modificado para corresponder às necessidades de UI da aplicação. ***Figura 10** _ mostra o diálogo de modificação quando _ *CANVAS** é clicado duas vezes. O aparecimento deste diálogo mudará com base nas definições de formato de cores do visor alvo.

![Screenshot do diálogo Editar Cor.](./media/guix-studio/edit_color.png)

**Figura 10**

O aparecimento do diálogo Editar Color mudará dependendo da profundidade de cor e da configuração do formato de cor do ecrã atual.

Para adicionar um novo recurso de cor, a partir da secção ***Cores** _ da *_Visão de Recurso_** selecione o seguinte botão:

![Adicione botão New Color](./media/guix-studio/image41.jpg)

Utilize o diálogo de cor resultante para adicionar um novo recurso de cor, como mostrado abaixo em ***Figura 11**:*

![Screenshot da nova cor no diálogo Editar Cor.](./media/guix-studio/new_color.png)

**Figura 11**

Depois de completar estes passos, selecione **Salvar** um novo recurso de cor com o nome **NEW_COLOR** com a cor física verde estará disponível para a aplicação a utilizar.

**Considerações especiais ao alterar as definições do formato de cor do ecrã:**

Quando cria um novo projeto, é automaticamente solicitado a configurar os ecrãs do projeto e o formato de cores de cada ecrã. Na maioria das vezes, fará estas seleções uma vez e não precisaria de modificar essas definições de configuração.

Pode determinar se é necessário alterar as definições do formato de cor do ecrã numa altura posterior. Nesse caso, o GUIX Studio fará uma melhor conversão do seu sistema atual e valores RGB da cor antiga para o novo formato de cores. Esta conversão segue algumas regras lógicas.

Para cores definidas pelo utilizador, o GUIX Studio tenta sempre converter a cor anterior para a cor mais próxima do novo formato de cores. Se estiver a converter de uma profundidade de cor elevada, como 16 bpp 5:6:5 formato de cor para um formato de cor em escala cinzenta ou monocromática, esta alteração pode resultar em conversões de cores não desejadas. Ao fazer uma grande alteração nas definições de profundidade de cor do visor, podem ser necessárias algumas atualizações manuais para a nova tabela de cores definida pelo utilizador.

Para as cores do sistema pré-definidas, o GUIX Studio define internamente três tabelas de cores padrão únicas. Uma tabela de cores padrão é usada para todas as profundidades de cores superiores a 4 bpp de escala cinzenta, uma segunda tabela de cores padrão é usada para formatos de cor à escala cinzenta (1 bpp < display_color_format <= 4bpp) e, finalmente, uma terceira tabela de cores do sistema padrão é usada para formato de cor monocromática.

Quando muda o formato de cor do visor utilizando Project diálogo de configuração, aplicam-se as seguintes regras:

1) Se os formatos de cores de ecrã antigo e novo utilizarem diferentes tabelas de cores do sistema definidas como definidas acima, as cores do sistema são cada uma reiniciada para as cores predefinidos pré-definidas. Por outras palavras, se mudar de cor para escala cinzenta, ou da escala cinzenta para a profundidade de cor monocromática, as cores do seu sistema serão reiniciadas para os valores padrão definidos internamente para a nova profundidade de cor. Embora isto possa causar a perda de algumas informações de cores personalizadas, esta solução dá-lhe um ponto de partida razoável quando faz uma alteração dramática nas definições do formato de cor do ecrã.

2) Se os formatos de cores antigos e novos usarem a mesma tabela de cores padrão, o que significa que está a fazer uma alteração de formato de cor menos dramática, o GUIX Studio irá testar cada cor do sistema para determinar se modificou o valor RGB da cor do sistema a partir do seu valor padrão. Se o valor RGB de cor do sistema tiver sido modificado, o GUIX Studio fará uma conversão de melhor correspondência do formato de cores antiga para o novo formato de cores. Se a cor do sistema não tiver sido modificada, será reposta para a cor padrão para o novo formato de cores.

**Considerações especiais para o funcionamento do modo de paleta:**

Quando um projeto é configurado para o formato de cores 256 cores do modo paleta de cores, o utilizador pode configurar como a paleta a ser instalada e usada é definida. Pode aceder e editar a definição da paleta através da utilização do Configure| Diálogo de temas, e se o seu projeto estiver definido para 8 bpp, deve ver o botão "Editar Paleta". Clique neste botão para elevar o diálogo da Paleta de Edição:

![Screenshot do diálogo da Paleta de Edição.](./media/guix-studio/edit_palette.png)

O GUIX Studio divide a paleta em duas secções: a secção "definido pelo utilizador" e a secção "autogerado". O GUIX Studio executa um algoritmo de geração de paleta ideal sofisticado para criar a melhor paleta para exibir as imagens que estão incluídas em cada tema. Pode esculpir qualquer número de entradas de paleta que precisa de definir digitando um número no campo "Entradas de Paletas Predefinidas" e insira qualquer valor RGB que goste para qualquer uma destas ranhuras. As ranhuras restantes serão atribuídas ao Studio para criar uma paleta de cores ideal para exibir as suas imagens.

Ao correr neste modo, se pretender editar uma cor definida na vista de recursos, o editor de cores permitir-lhe-á selecionar apenas a partir das entradas de paletas predefinidas que definiu. Isto porque as restantes entradas de paleta são geradas automaticamente pelo GUIX Studio e mudarão à medida que as imagens adicionadas ao seu projeto forem modificadas.

Se necessitar da visualização de tipos de letra anti-aliased ao executar no modo paleta de 8bpp, deve definir uma série de entradas de paleta que criam um gradiente para cada utilização de cor de primeiro plano/fundo para exibir o seu texto anti-aliased. Pode utilizar 8 entradas de paleta para o gradiente para cada combinação de cores, ou 16 entradas de paleta para um gradiente mais suave. Este número de entradas de paletas utilizadas é determinado pela caixa de verificação "Número de Cores de Texto Anti-Aliased Do Modo de Paleta" no diálogo de configuração Project. Pode utilizar um gradiente com apenas oito entradas para minimizar as entradas de paleta utilizadas para cada combinação de cores, ou utilizar 16 gradientes de entrada para fornecer a aparência de texto anti-aliased mais suave.

Para simplificar a definição de um gradiente de cor para exibir texto anti-aliased, ou para gerar um gradiente de cor para o seu próprio uso, o diálogo de paleta de edição fornece um botão Gerar Gradiente. Para utilizar esta função, deve primeiro atribuir os valores r:g:b das cores de gradiente inicial e final.

Por exemplo, se quisesse exibir texto vermelho anti-aliasado num fundo cinzento médio usando oito entradas de paleta a partir do índice 50, atribuiria o valor r:g:b de 255:0:0:0 ao índice de paleta 50, e o valor r:g:b 128:128:128 ao índice de paleta 57. Introduza estes valores de índice de paleta nos campos do índice inicial e do índice final neste diálogo e clique no botão Gerar Gradiente. As entradas de paleta 51 a 56 serão inicializadas para definir uma transição suave de gradiente entre as suas cores delimitadoras.

## <a name="font-resources"></a>Recursos de Fonte

Para gerir os recursos de letra, a secção ***Fontes** _ da _*_Vista_*_ de Recursos deve primeiro ser expandida clicando no campo _ *+* * , resultando no diálogo apresentado abaixo na **_Figura 12_**:

![Screenshot da secção De Fontes na Vista de Recursos.](./media/guix-studio/image44.jpg)

**Figura 12**

Os recursos de fonte consistem de uma ou mais fontes, cada uma com um nome lógico único. Por exemplo, na **Figura 12** o **sistema** de nome lógico está associado a um tipo de letra específico. Este recurso de fonte é utilizado sempre que a aplicação especifica **o SISTEMA** como o tipo de letra nas propriedades do objeto. O grupo de fontes mostra-lhe uma pré-visualização WYSIWYG dos glifos de fonte à esquerda, a altura da fonte em pixels, o nome de ID da fonte e o tamanho da fonte (em kb).

Na vista acima, os quatro primeiros tipos de letra são os tipos de letra predefinidos pré-definidos que são exigidos pela biblioteca GUIX. Pode alterar os dados de tipo de letra associados a estes tipos de letra, no entanto não é possível alterar estes nomes de identificação de tipo de letra.

A última fonte mostrada acima, denominada "Itálica", é uma fonte personalizada que foi adicionada ao projeto pelo utilizador.

Para modificar um recurso de fonte, clique duas vezes (ou clique à direita e selecione o menu) no recurso de fonte. A partir deste diálogo, o recurso de fonte pode ser modificado de forma a corresponder às necessidades de UI da aplicação. ***Figura 13** _ mostra o diálogo de modificação quando _ *SYSTEM** é clicado duas vezes.

! [[Screenshot do diálogo de modificação quando o SYSTEM é clicado duas vezes.](./media/guix-studio/edit_system_font.png)

**Figura 13**

Para adicionar um novo recurso de fonte, a partir da secção ***Fontes** _ da *_Visão de Recursos_* _ * selecione o seguinte botão:

![Adicionar novo botão de fonte](./media/guix-studio/image46.jpg)

Isto invocará o `Font Edit` diálogo para adicionar um novo recurso de fonte, como mostra a figura ***14:***

![Screenshot do diálogo de modificação para adicionar um novo recurso de fonte.](./media/guix-studio/add_new_font.png)

**Figura 14**

As novas fontes GUIX são criadas pelo GUIX Studio, transformando uma fonte TrueType escolhida com um tamanho específico. Portanto, o diálogo acima primeiro requer um caminho de letra TrueType. Pode utilizar o botão de navegação para navegar para um diretório que contenha ficheiros de fontes no seu sistema de desenvolvimento. Várias fontes TrueType também estão incluídas na sub-pasta GUIX/fontes onde quer que tenha instalado o GUIX Studio.

Se possível, a localização do ficheiro de fonte TrueType é armazenada internamente utilizando um caminho relativo ao projeto. Por esta razão, é importante manter todos os seus ficheiros de fontes num local comum e utilizar uma estrutura comum de árvores de diretório para os seus projetos e ficheiros de fontes, de modo a permitir-lhe mover projetos do GUIX Studio de uma estação de desenvolvimento para outra.

O campo Nome de Fonte permite especificar o nome de identificação do recurso de fonte. Este é o ID de recursos que será usado no código gerado pelo GUIX Studio e também utilizado pela sua aplicação ao fazer referência à fonte. Este nome deve seguir os requisitos de sintaxe de nomeação variável C.

Uma vez escolhido um ficheiro de letra TrueType para usar como entrada, insira um nome lógico de fonte.

A caixa de verificação "**Generate Kerning Info**" instrui o GUIX Studio a incluir informações de kerning dentro da fonte gerada, que é usada para ajustar as posições relativas de glifos sucessivos numa corda. Se pretender aplicar o kerning com as suas cordas, terá de utilizar um tipo de letra que contenha informações de kerning e ligue esta caixa de verificação. Também terá de definir a opção de construção da biblioteca GUIX "GX_FONT_KERNING_SUPPORT" para suportar o texto de renderização com informações de kerning.

A caixa de verificação "**Incluir conjunto de caracteres definido por String Table**" instrui o GUIX Studio a incluir os glifos referenciados pela sua tabela de cordas estática dentro da fonte gerada. Pode incluir glifos adicionais selecionando e editando as gamas de caracteres listadas abaixo, mas esta opção pode ser selecionada para gerar rapidamente o conjunto de caracteres mínimos necessário para exibir as cordas definidas dentro da sua tabela de cordas. É claro que se a sua tabela de cordas utilizar glifos que não estão presentes no seu tipo de letra TrueType, esses caracteres não estarão disponíveis na sua fonte GUIX e não serão exibidos no seu sistema-alvo.

Para gerar um tipo de letra mais completo, ou um tipo de letra que inclua caracteres que não podem ser usados dentro da sua tabela de cordas estática, também pode selecionar intervalos de caracteres da lista abaixo. Note que pode selecionar qualquer número de intervalos de caracteres e pode editar o código de caracteres inicial e final real a ser incluído dentro de cada intervalo selecionado.

As gamas de caracteres pré-definidas e os nomes de página são apenas sugestões que permitem selecionar facilmente o conjunto de caracteres necessário para os idiomas ativos em uso hoje em dia. Os nomes de idiomas listados não têm qualquer efeito na fonte GUIX gerada, e você é livre de digitar em qualquer intervalo de caracteres Hex que você gosta para qualquer intervalo de caracteres ativado ou selecionado.

Por exemplo, se quiser gerar um tipo de letra que contenha apenas os caracteres numéricos, pode selecionar a página de código "Ascii", mas introduzir o valor inicial 0030 e o valor final 0039 para gerar um tipo de letra que contenha apenas os caracteres numéricos. Note que a gama de caracteres valores codificados em Hexadecimal, que é a notação normal para tabelas de caracteres Unicode.

Por padrão, o GUIX Studio e a biblioteca GUIX suportam códigos de caracteres 0x0000 através de 0xffff, que abrange todas as línguas ativas, formas matemáticas e outros símbolos em uso hoje em dia. Se necessitar da utilização de códigos de caracteres acima do valor 0xffff, incluindo certas Áreas de Utilização Privada, terá de ligar a caixa de verificação "Support Extended Character Range". Quando esta caixa de verificação é selecionada, o GUIX Studio permite ao utilizador especificar as gamas de caracteres de 0x0000 a 0x10ffff, que inclui as gamas de caracteres Unicode Private Use. Se necessitar desta gama de caracteres alargada, também terá de definir a opção de construção da biblioteca GUIX "GX_EXTENDED_UNICODE_SUPPORT" para que a biblioteca GUIX suporte internamente códigos de caracteres de 32 bits, em vez da configuração padrão que suporta códigos de caracteres de 16 bits.

Se selecionar tanto a caixa de verificação "Incluir o conjunto de caracteres definido por Table string" como uma ou mais das gamas de caracteres na lista abaixo, o GUIX Studio combinará estas seleções no superconjunto das gamas selecionadas e dos caracteres utilizados dentro da sua tabela de cordas. É claro que a fonte de origem TrueType selecionada também deve conter os caracteres necessários para que o GUIX Studio produza glifos significativos para cada valor de caracteres solicitado.

Uma vez determinada a gama de caracteres, especifique a altura da fonte nos pixels e o formato de fonte. Ambos os tipos de letra anti-aliased e binários são suportados. As fontes binárias requerem menos área de armazenamento de dados estático, no entanto as fontes anti-aliasadas produzem a melhor aparência em alvos que correm a 4-bpp em tons de cinza ou profundidades de cor mais altas.

>[!NOTE]  
> *A "altura da fonte" refere-se à praça EM da fonte. No tipo metálico tradicional, a Praça EM era igual à altura da linha do corpo metálico a partir do qual cada letra sobe, e cada corpo metálico tinha o mesmo tamanho. Em tipo metálico, o tamanho físico de uma letra não poderia normalmente exceder o Quadrado EM. No tipo digital, o EM é uma grelha de resolução arbitrária que é usada como espaço de design de uma fonte digital. Para estas fontes digitais é comum que algumas características do glifo, como acentos e descidas, possam estender-se para além dos limites da praça EM. O resultado final é que a altura do widget necessária para exibir totalmente uma fonte específica terá muitas vezes de ser ligeiramente maior do que a altura do pixel de fonte solicitada.*

Uma vez concluídos todos os campos de configuração da fonte, clique no botão OK para criar um novo recurso de fonte. O GUIX Studio gerará uma fonte compatível com GUIX com as propriedades escolhidas, adicionará esse tipo de letra aos recursos do projeto e disponibilizará a fonte para a aplicação a utilizar.

## <a name="pixel-map-resources"></a>Recursos do mapa de pixels

Para gerir os recursos do mapa de pixels, a secção ***Pixel-maps** _ da Vista de _*_Recursos_*_ deve primeiro ser expandida clicando no campo _ *+* * , resultando no diálogo apresentado abaixo na **_Figura 15_**:

Quando o `Pixelmap` grupo é expandido, deve ver uma pré-visualização semelhante a esta:

![Screenshot da secção pixel-maps na vista de recursos.](./media/guix-studio/pixelmap_view.png)

**Figura 15**

Os recursos do mapa de pixels consistem num ou mais mapas de pixels, cada um com uma pré-visualização da imagem do mapa de pixels à esquerda, as dimensões do mapa de pixels em pixels, um nome lógico único e o tamanho de armazenamento do mapa de pixels no ficheiro de recursos de saída (em kb).

O primeiro grupo de pixel-maps compreende os pixel-maps do sistema pré-definidos exigidos por widgets GUIX, tais como botões de rádio e caixas de verificação. Pode alterar os dados do mapa de pixels associados aos mapas de pixels do sistema, no entanto não é possível alterar estes nomes de ID do mapa de pixels. Também mostrado acima estão vários pixel-maps personalizados com nomes como "BACKGROUND" e "BUTTON_ATIVE". Estes são exemplos de pixel-maps que um utilizador adicionou ao projeto que pode ser usado para tornar um widget GX_PIXELMAP_BUTTON.

Uma vez que muitos projetos contêm um grande número de mapas de pixels, a vista do mapa de pixels permite definir qualquer número de pastas de mapa de pixels para organizar as suas imagens de mapa de pixels. 

A adição de uma nova pasta de mapa de pixels é feita clicando à direita no `Pixelmaps` cabeçalho da secção da Vista de ***Recursos*** selecionando "Adicionar Pasta".

Para modificar um recurso de mapa de pixels, clique duas vezes (ou clique à direita e selecione menu) no recurso pixel-map. A partir deste diálogo, o recurso pixel-map pode ser modificado para corresponder às necessidades de UI da aplicação. ***Figura 16** _ mostra o diálogo de modificação quando _ *RADIO_ON** é clicado duas vezes.

![Screenshot do diálogo Edit Pixel-maps.](./media/guix-studio/image49.jpg)

**Figura 16**

O `Edit Pixelmap` diálogo permite-lhe definir um novo mapa de pixels ou modificar o conteúdo de um pixel-map existente. Nos bastidores, o GUIX Studio lê a imagem de entrada e converte a imagem no `GUIX GX_PIXELMAP` formato que pode ser usado pela biblioteca GUIX. O GUIX Studio também converte o espaço de cores da imagem de entrada para o espaço de cores do ecrã no qual este pixel-mapa será usado.

O primeiro campo deste diálogo é o caminho para a imagem de origem. O GUIX Studio suporta a entrada de ficheiros de imagem de formato PNG (.png) ou JPEG (.jpg). Pode utilizar o botão "navegar" para encontrar o ficheiro de entrada pretendido no seu sistema de ficheiros local.

Se possível, a localização do ficheiro de imagem de entrada é armazenada internamente utilizando um caminho relativo ao projeto. Por esta razão, é importante manter todos os seus ficheiros de imagem num local comum e utilizar uma estrutura comum de árvores de diretório para os seus projetos e ficheiros de imagem, de modo a permitir-lhe mover projetos do GUIX Studio de uma estação de desenvolvimento para outra e não perder a noção dos dados de imagem de entrada.

Os `Pixelmap ID` campos permitem especificar o nome lógico do recurso pixel-map. Este nome aqui dactilografado deve ser único e deve seguir as regras de sintaxe de nomeação variável C.

A caixa de verificação do Ficheiro de Saída Especifica permite especificar um ficheiro de saída único para cada mapa de pixels. Se esta caixa de verificação não for selecionada, os dados do mapa de pixels são escritos no ficheiro de recursos predefinidos para este ecrã. Se a caixa de verificação for selecionada, pode escrever um nome de ficheiro específico no qual os dados deste mapa de pixels serão escritos. O objetivo desta opção é permitir-lhe dividir os dados do mapa de pixels, que podem ser matrizes C muito grandes, em vários ficheiros de saída. Certos compiladores lutam para lidar com ficheiros C que são centenas de milhares de linhas de origem.

A caixa de verificação "Compress Output" permite especificar se a saída do mapa de pixels é um algoritmo de compressão GUIX proprietário. Os ficheiros de saída comprimidos são geralmente menores, mas também requerem tempo de processador para renderizar o alvo. Na maioria das vezes, escolherá a compressão para os seus grandes mapas de pixels e utilizará o formato não comprimido para os seus mapas de pixels mais pequenos.

A `Include Alpha Channel` caixa de verificação determina como o GUIX Studio utiliza informações de canal alfa por vezes presentes nos ficheiros de entrada de .png formato. Se esta caixa de verificação for verificada e o visor estiver a funcionar a uma profundidade de cor de 16 bpp ou superior, o GUIX Studio preservará os dados alfa de entrada completos no ficheiro de saída. Se esta caixa de verificação não for verificada, o GUIX produzirá um ficheiro de saída ligeiramente menor. Este ficheiro de saída pode incluir transparência, mas não incluirá informações completas de mistura alfa.

A `Dither` caixa de verificação instrui o GUIX Studio a aplicar um algoritmo de dilatação avançado ao converter a imagem de entrada para utilização com um ecrã de profundidade de cor inferior. A dithering é geralmente ativada, mas pode causar ficheiros de saída maiores se a compressão for usada porque haverá menos pixels repetindo.

Uma vez definidas todas as opções conforme desejado, clique no botão OK para produzir um novo recurso de mapa de pixels. O GUIX Studio irá ler o ficheiro de imagem de entrada, descomprimê-lo, realizar conversão de espaço de cores e dithering, re-comprimir opcionalmente os dados e guardar os dados em formato compatível com `GX_PIXELMAP` GUIX. O novo pixel-map é adicionado aos recursos do projeto e disponibilizado para a aplicação a utilizar.

Para adicionar um novo recurso de mapa de pixels, a partir da `Pixelmaps` secção do Ponto de Vista de ***Recursos*** selecione o seguinte botão:

![Adicione o novo botão de mapa pixel.](./media/guix-studio/image50.jpg)

**Edição de Pixelmap de Lote**

Para modificar as propriedades de um conjunto de pixelmaps, clique no grupo ou pasta pixelmap e selecione editar o menu **Edit Pixelmap(s)** para invocar o diálogo **Edit Pixelmap(s).**

![Screenshot do diálogo Edit multi pixel-maps.](./media/guix-studio/batch_pixelmap_edit.jpg)

Descrição do estado da caixa de verificação:

![Botão verificado.](./media/guix-studio/checkbox_checked.jpg)
Este estado significa que todos os pixelmaps têm a propriedade verificada, você pode desmarcar o botão para mudar a propriedade para todos os pixelmaps.

![Botão descontrolado.](./media/guix-studio/checkbox_unchecked.jpg)
Este estado significa que todos os pixelmaps têm a propriedade desmarcada, você pode verificar o botão para mudar a propriedade para todos os pixelmaps.

![Botão indeterminado.](./media/guix-studio/checkbox_undetermined.jpg)
Este estado significa que os pixelmaps têm um estado diferente para a propriedade, você pode verificar ou desmarcar o botão para alterar a propriedade para todos os pixelmaps, caso contrário, a propriedade permanece inalterada.


## <a name="string-resources"></a>Recursos de Cordas

Quando o grupo Strings for expandido, deverá ver uma pré-visualização da tabela de cordas do projeto, como mostra abaixo:

![Screenshot do grupo strings expandido.](./media/guix-studio/string_res_view.png)

**Figura 17**

Os recursos de corda consistem de uma ou mais cordas, cada uma com um nome lógico único. Por exemplo, na **Figura 17** o nome lógico "PATIENT_LIST" está associado à cadeia "Lista de Pacientes" mostrada à sua direita. Este recurso de cadeia é utilizado sempre que a aplicação especifica PATIENT_LIST como o fio nas propriedades do objeto.

Lembre-se sempre que os seus nomes de identificação para todos os tipos de recursos devem ser nomes variáveis compatíveis com a sintaxe C. Estes nomes serão utilizados extensivamente quando os ficheiros de recursos do seu projeto e ficheiros de especificações forem produzidos pelo Studio.

Para modificar um recurso de corda, clique duas vezes (ou clique à direita e selecione menu) no recurso de cadeia para invocar o diálogo ***String Table Editor** _ . A partir do diálogo _*_do Editor de Tabela de Cordas,_*_ o recurso de corda pode ser modificado de modo a corresponder às necessidades de UI da aplicação. _*_A figura 18_*_ mostra o diálogo de modificação quando _ *STRING_13** é clicado duas vezes.

Neste caso, o nome de identificação da cadeia é mostrado à esquerda, que o conteúdo da corda para o primeiro ou o idioma de referência é mostrado à direita. É claro que o conteúdo exato das cordas é muito específico da sua aplicação, no entanto o layout da pré-visualização do grupo String é consistente.

O GUIX Studio suporta texto estático e aplicação multilingue, definindo e mantendo uma Tabela de Cordas. A Tabela de Cordas define um ID de corda para cada registo, e uma constante de corda para cada registo para cada idioma suportado.

Os idiomas a suportar pela sua aplicação são definidos através do Diálogo de Configuração de Idiomas, mostrando aqui:

![Screenshot do diálogo de configuração de idioma.](./media/guix-studio/config_languages.png)

**Figura 18**

O Diálogo de Configuração de Idiomas é invocado utilizando o | configuração O comando de idiomas no menu de inscrição. Este diálogo permite definir o número de idiomas a suportar pela sua aplicação e o nome ou idioma idioma a ser associado a cada idioma. As línguas suportadas podem ser modificadas após a criação do seu projeto, no entanto, se um idioma for removido, deve estar ciente de que os dados de cadeia associados a essa língua também são removidos e não podem ser recuperados.

A caixa de verificação "**Staticly Defined**" indica que o idioma selecionado será definido estáticamente no formato código fonte no ficheiro de recursos gerado. Se nenhuma língua estiver definida estáticamente, o ponteiro de tabela de idiomas será definido como NULO na tabela de exibição gerada e um idioma deve ser carregado e instalado pela aplicação utilizando as APIs de carregadores de recursos binários fornecidas pela biblioteca GUIX.

A caixa de verificação "**Support Bidi Text**" instrui o GUIX Studio para permitir o suporte de renderização de texto bidirecional. Deve ligar esta caixa de verificação se as cordas que vai introduzir para este idioma requererem a renderização de texto bidirecional.

A caixa de verificação "**Generate Bidi Text in Display Order**" instrui o GUIX Studio a gerar texto bidirecional para o ficheiro de saída na sua ordem de exibição. Se esta opção for selecionada, não é necessário um processamento de tempo de execução na biblioteca GUIX para tornar corretamente o texto bidirecional. Quando esta opção for selecionada, a renderização de textos bidirecionais NÃO deve ser ativada na biblioteca GUIX. Esta configuração produz o melhor desempenho em tempo de execução, mas não suporta a renderização de cordas de texto bidirecional dinâmicamente definidas.

A primeira língua ou língua "Index 1" é referida como a sua "língua de referência". Esta é a linguagem que o GUIX Studio usará quando estiver a definir e editar o seu design de UI. Todas as outras línguas da sua tabela de cordas são referidas como Línguas de Tradução. O GUIX Studio suporta a exportação e importação dos dados de tabelas de cordas nos ficheiros de dados de formato XLIFF ou CSV padrão da indústria, convenientes para o intercâmbio de informações de cordas com tradutores que possam ajudar o desenvolvedor de aplicações a adicionar traduções para que as línguas sejam suportadas para além da língua de referência. Quando exporta a tabela de cordas GUIX para um ficheiro XLIFF ou CSV, o idioma de referência juntamente com uma língua de tradução estão incluídos no ficheiro de troca de dados de cadeias XLIFF ou CSV. Da mesma forma, quando importa um ficheiro XLIFF ou CSV, os dados importados são utilizados para preencher uma língua de tradução na sua tabela de cordas GUIX.

![Screenshot do editor da mesa de cordas.](./media/guix-studio/image53.jpg)

**Figura 19**

O diálogo do Editor de Tabela de Cordas apresenta pela primeira vez uma lista de IDs de corda à esquerda, seguidos dos dados de cadeia de linguagem de referência. Se for definida mais de uma língua, uma terceira coluna mostra qualquer uma das línguas de tradução suportadas. Pode abrir e fechar a terceira coluna clicando na pequena seta no canto superior direito da coluna de língua de referência.

Quando a coluna de linguagem de tradução é visível, pode pedalar através das línguas de tradução contidas no projeto clicando nas pequenas setas no canto superior direito da coluna de linguagem de tradução da lista de cordas.

Pode editar um registo de cordas clicando no registo da tabela para selecioná-lo. Quando um registo é selecionado, o registo String ID e o conteúdo de cordas são mostrados nos campos abaixo da vista da tabela. Pode digitar novos valores nestes campos para modificar o ID da cadeia e o conteúdo das cordas.

A caixa no lado direito da vista de mesa mostra pré-visualizações de widgets que referenciam a cadeia selecionada. Isto é útil para dizer se uma cadeia editada excederá uma área de widget específica.

Os campos à direita do conteúdo das cordas incluem:

- "Número de referências": Este campo indica quantas vezes um determinado ID de cadeia é usado no âmbito do projeto GUIX Studio. Se a contagem de referência for 0, esta cadeia pode ser obsoleta e pode ser removida opcionalmente pelo utilizador.
- A largura da corda (pixels) indica a largura do visor da corda utilizando o tipo de letra indicado.
- O campo "Notas" é um campo de comentários opcional que lhe permite adicionar informações sobre a finalidade ou utilização de cada cadeia. Estas notas estão incluídas em quaisquer ficheiros de dados de cadeias XLIFF exportados para ajudar os tradutores a fazer traduções precisas e significativas de cordas.

Sempre que tiver o diálogo ***do Editor de Tabela de Cordas*** aberto, pode adicionar cordas adicionais ao seu projeto clicando no botão Add String na parte superior do diálogo. As cordas obsoletas ou não-reutilizadas podem ser removidas do projeto selecionando primeiro a cadeia e, em seguida, clicando no botão Descodução de Cordas na parte superior do diálogo.

Além de adicionar manualmente novas cordas ao seu projeto utilizando o diálogo Do Editor de Mesa de Cordas, também pode adicionar novas cordas indiretamente, simplesmente digitando conteúdo de cordas no campo "Text" da Visão de Propriedades de qualquer widget que suporte texto. Por outras palavras, quando está a adicionar novos widgets na visão alvo ou a digitar informações de texto na vista de propriedades, estas ações estão automaticamente a criar novas entradas na tabela de cordas do projeto.

## <a name="adding-language-translations"></a>Adicionar traduções linguísticas

O editor de tabela de cordas GUIX Studio suporta um fluxo de trabalho de definição de linguagem que permite ao desenvolvedor criar uma aplicação usando a sua linguagem primária, em seguida, exportar os dados de cadeia para um ficheiro padrão de esquema XML ou CSV para ser enviado para um especialista em tradução de idioma. O ficheiro de tradução é então devolvido ao desenvolvedor, que pode importar as traduções linguísticas de volta para o seu projeto Studio, adicionando assim suporte para uma nova linguagem à sua aplicação.

Esta facilidade é invocada utilizando os botões Export (para escrever os dados de cadeia para um ficheiro) e a Import (para ler as cordas traduzidas) no topo do Editor de Tabela de Cordas. O botão Exportação é utilizado para criar um ficheiro XML ou CSV de esquema XLIFF que contém as suas cordas linguísticas de referência. Este ficheiro pode ser utilizado por um tradutor utilizando ferramentas e editores que suportem o formato de ficheiro XLIFF ou CSV padrão.

Quando um especialista em tradução lhe devolve o ficheiro XLIFF com as novas traduções de cadeias, pode utilizar o botão Import para ler os dados deste ficheiro XLIFF ou CSV. Se o ficheiro XLIFF ou CSV contiver um novo idioma, o novo idioma é adicionado ao seu projeto. Se o ficheiro XLIFF contiver novos dados de cadeia para uma língua existente, estes novos dados são importados para o seu projeto. As cordas linguísticas de referência não são modificadas pela operação Import.

Quando clica no botão Exportação, é apresentado o diálogo XLIFF/CSV Export Control, apresentado abaixo:

![Screenshot do diálogo XLIFF/CSV Export Control.](./media/guix-studio/image54.jpg)

**Figura 20**

Os campos de língua de origem e linguagem-alvo especificam quais colunas de tabela de cordas serão escritas para o ficheiro XLIFF ou CSV como a língua de referência e a língua de tradução. A língua Origem são as cadeias de referência, e a Língua Alvo é a língua para a qual o seu tradutor fornecerá dados de cadeias traduzidos.

O campo de versão XLIFF especifica uma das duas principais versões de formato de ficheiro XLIFF, quer versão 1.2, quer versão 2.0 (e posterior). Estas normas de formato de ficheiro XLIFF são incompatíveis e precisa de saber qual a versão que as suas ferramentas utilizam antes de utilizar os comandos XLIFF Export/Import. Mais informações sobre os padrões XLIFF e XLIFF podem ser consultados aqui:

- versão 1.2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- versão 2.0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Os campos de nome de ficheiro de saída e de saída permitem especificar o nome de ficheiro e o local para o qual o ficheiro de saída será escrito. O nome de ficheiros depende inteiramente do utilizador, no entanto sugerimos que utilize nomes que indiquem as línguas de origem e alvo contidas no ficheiro exportado.
