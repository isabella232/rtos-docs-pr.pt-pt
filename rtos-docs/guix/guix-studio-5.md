---
title: Designer de tela de estúdio GUIX
description: Desenhar ecrãs de aplicações é o principal objetivo do GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 318e68ab5ab7d841057d65565dfda263597d03e4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826330"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Capítulo 5: GUIX Studio Screen Designer

Desenhar ecrãs de aplicações é o principal objetivo do GUIX Studio. O design do ecrã é realizado através de todas as várias vistas descritas anteriormente no Capítulo 3. No entanto, o principal elemento do design do ecrã no GUIX Studio é o ***Target View***, que é onde todos os elementos do ecrã são mostrados visualmente e da mesma forma que aparecerão no ecrã alvo incorporado. Estes elementos de ecrã podem ser selecionados, movidos, redimensionados, etc. através de simples operações de rato e botão. Além disso, as operações de alinhamento e botão de ordem Z estão disponíveis em objetos selecionados. As sub-secções seguintes descrevem várias características do design do ecrã do GUIX Studio. 

## <a name="creatingconfiguring-projects"></a>Criação/Configuração de Projetos

Criar projetos no GUIX Studio é simples – basta selecionar o botão ***Novo Projeto** _ ou o Projeto de Seleção de _*_Menus, Novo Projeto_*_. Em seguida, o GUIX Studio apresenta o diálogo _ *_Configure Project_** A partir deste diálogo, são especificadas as definições básicas do visor, bem como informações sobre o caminho para onde localizar o código gerado pelo GUIX Studio.

Quando um novo projeto é criado, o diálogo do projeto de configuração é apresentado. É aqui que o desenvolvedor especifica o número de ecrãs de hardware disponíveis no alvo e as propriedades de cada ecrã. As propriedades incluem o nome lógico do visor, resolução x/y, profundidade de cor e formato, e outras propriedades do ecrã. O GUIX Studio suporta vários ecrãs no mesmo projeto. Se forem necessários visores adicionais, o campo ***Número de Visualizações** _ deve ser alterado para corresponder ao número de visualizações no dispositivo incorporado. O número máximo de exibições num projeto é de 4. _ *_Figura 21_** mostra o diálogo do Projeto Configure.

A modificação das definições de projeto e/ou exibição é realizada quer pela opção menu ***Configurar, Project/Display** _ ou selecionando o projeto ou ecrã, clicando à direita e selecionando _*_Configure, Project/Display_*_. Em qualquer dos casos, é apresentado o diálogo _ *_Configure Project_** para facilitar as alterações nas definições e/ou exibição do projeto.

![Screenshot do diálogo do Projeto Configurar.](./media/guix-studio/config_project.png)

**Figura 21**

O grupo Diretório é onde pode especificar os diretórios de saída padrão para a fonte C e os ficheiros de cabeçalho produzidos pelo Studio. Estes diretórios são normalmente guardados relativos à localização do projeto para facilitar a deslocação de projetos de um computador para outro ou de um sistema de ficheiros para outro.

O campo Cabeçalhos Adicionais é onde pode especificar ficheiros de cabeçalho personalizados. Se for necessário mais do que um ficheiro de cabeçalho, utilize os pontos de selimite para delimitar a lista.

Quando invoca os comandos "Gerar Aplicação" ou "Gerar Recursos", estes são os diretórios padrão em que esses ficheiros de origem serão escritos. É claro que pode sobrepor-se a estas localizações de diretório a qualquer momento, introduzindo novos locais no diálogo do Diretório de Saída.

## <a name="selecting-widgets"></a>Seleção de Widgets

A seleção de widgets é feita clicando no widget na ***Project View** _ widget tree ou clicando no widget visível na área _*_'Target View'._*_ Quando um único widget é selecionado, as suas propriedades são exibidas na área _*_de Visualização de Propriedade._*_ _*_A figura 22_*_ mostra o _botão_ widget "_* **" selecionado.

![Screenshot do widget selecionado.](./media/guix-studio/select_button.png)

**Figura 22**

## <a name="using-properties"></a>Usando propriedades

Como mencionado anteriormente, as propriedades de um widget selecionado são apresentadas no ***Visualização de Propriedades** _. Todos os widgets têm um conjunto comum de propriedades, bem como algumas propriedades que são específicas para o tipo de widget particular. Por exemplo, um widget de botão tem uma propriedade _ *_Pushed_** enquanto um widget de janela não. Seguem-se o conjunto comum de propriedades widget:

| Propriedade         | Significado                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Tipo Widget    | Tipo de widget, para referência                                                                               |
| Nome Widget      | Nome do widget, passado para o widget criar função e usado para nomear variável nos ficheiros de origem gerados.               |
| Widget ID        | Identificação de widget. Este valor de ID é usado para gerar sinais de widgets infantis para os seus ecrãs dos pais.                            |
| Esquerda             | A mais à esquerda coordena o widget                                                                                                 |
| Parte Superior              | A mais alta coordenada do widget                                                                                                  |
| Width            | Largura do widget em pixels                                                                                                      |
| Height           | Altura do widget em pixels                                                                                                     |
| Limite           | Tipo de fronteira widget                                                                                                          |
| Transparente      | Deve ser verificado se o widget é parcialmente transparente                                                                       |
| Sorteio Selecionado    | Deve ser verificado se o widget deve inicialmente desenhar-se no estado selecionado.                                            |
| Ativar           | Deve ser verificado se o widget pode ser selecionado ou clicado pelo utilizador final.                                                    |
| Aceita O Foco    | Deve ser verificado se o widget aceita o foco.                                                                                 |
| Atribuição de tempo de execução | Deve ser verificado se o bloco de controlo widget deve ser atribuído de forma dinâmica.                                                 |
| Enchimento normal      | Id de recurso de cor de preenchimento normal                                                                                                  |
| Preenchimento selecionado    | Id de recurso de cor de preenchimento selecionado                                                                                                |
| Função de desenhar    | Função de desenho personalizado definida pelo utilizador Nome. Se este campo estiver em branco, é utilizada a função de desenho padrão para esse tipo de widget. |
| Função do evento   | Nome da função de tratamento de eventos personalizado definido pelo utilizador. Se estiver em branco, utiliza-se o manuseamento padrão do evento para este tipo de widget.          |

***A figura 23*** mostra as propriedades de um simples widget de janela.

![Screenshot das propriedades de um simples widget de janela.](./media/guix-studio/image57.jpg)

**Figura 23**

Muitos tipos de widgets têm propriedades adicionais específicas de cada tipo de widget.

Por exemplo, na Figura 23 acima, o tipo de widget janela suporta um Id pixelmap de papel de parede, e uma definição de estilo indicando se o papel de parede deve ser centrado ou em azulejo.

Os widgets de texto suportam um campo de ID de cadeia, juntamente com estilos de alinhamento de texto e uma especificação de fonte. As propriedades adicionais do widget são normalmente muito intuitivas depois de ter lido a descrição de cada tipo de widget e os estilos disponíveis e criar parâmetros de função para esse tipo de widget.

## <a name="manipulating-widgets"></a>Manipulação de Widgets

Para manipular um widget, é primeiro deve ser selecionado. Isto é feito clicando diretamente no widget no ***Target View** _ ou selecionando-o na _ *_Project View_** widget tree. Uma vez selecionado, o widget terá um esboço tracejado. Neste estado, pode ser movido simplesmente clicando no widget e arrastando-o para a localização desejada no seu progenitor. Se o widget for um widget de alto nível, arrastar o widget está a definir eficazmente a posição inicial do widget no visor do alvo. É claro que é sempre possível mover ou redimensionar qualquer widget a qualquer momento usando a API GUIX.

Para redimensionar a altura do widget, posicione o rato na borda superior do widget e aguarde que o ponteiro do rato mude para uma seta para cima para baixo. Neste ponto, a altura do widget pode ser alterada movendo simplesmente o rato enquanto o botão do rato direito está premido. A largura do rato pode ser redimensionada de forma semelhante, posicionando o ponteiro do rato na extremidade esquerda do widget. ***Figura 24** _ mostra o widget "_*_botão_**" redimensionado e movido para a área esquerda/superior da janela dos pais.

![Screenshot do widget do botão.](./media/guix-studio/resize_button.png)

**Figura 24**

## <a name="manipulating-multiple-widgets"></a>Manipular múltiplos widgets

A seleção de vários widgets é realizada clicando em vários widgets na vista alvo enquanto segura a tecla ***Ctrl*** para baixo. Ao fazê-lo, cada um dos widgets selecionados com um contorno tracejado à sua volta. Note que ao selecionar vários widgets cada widget no grupo de seleção deve ter um filho do mesmo progenitor.

Uma vez selecionados vários widgets, podem ser simultaneamente movidos clicando dentro de um nos widgets selecionados e movendo o rato com o botão do rato direito premido. Além disso, os botões de alinhamento na barra de **ferramentas*** podem ser utilizados para alinhar o grupo de widgets selecionados. _*_A figura 25_*_ mostra os widgets selecionados pelo _*_botão_*_" e o "_*_novo botão_*_" e a _*_Figura 26_*_ mostra o resultado da seleção _ *_Align-Left_** enquanto estes widgets são selecionados.

![Screenshot do botão e novos widgets de botão selecionados](./media/guix-studio/multiple_select.png)

**Figura 25**

![Screenshot do resultado da seleção de botões Align-Left.](./media/guix-studio/align_left.png)

**Figura 26**

## <a name="cutcopypaste-operations"></a>Operações de corte/cópia/pasta

Um widget selecionado no ***Target View** _ pode ser cortado, copiado e colado de forma padrão. Widgets e ecrãs podem ser copiados dentro de um projeto, ou copiados de um projeto e colados em outro. A _*_Barra de Ferramentas_*_ tem botões para corte, cópia e pasta. Existem também as mesmas opções na opção menu Edit. Note que ao colar um widget, o widget principal deve ser selecionado antes de colar o novo widget. _*_A figura 27_*_ mostra o resultado da seleção do widget "_*_botão_**", copiando-o e colando a cópia na mesma janela.

![Screenshot das operações de corte/cópia/pasta.](./media/guix-studio/copy_paste_button.png)

**Figura 27**

Copiar/Colar dentro de um projeto é geralmente simples porque os recursos que podem ser exigidos pelo widget(s) copiado estão sempre presentes quando você está trabalhando dentro de um projeto. No entanto, se copiar um widget do projeto A e colar que se widget no projeto B, alguns problemas com dependências de recursos podem surgir.

Quando copia widgets(s) dentro do Studio, a aplicação Studio faz uma lista dos recursos necessários pelos widgets copiados, e gera uma tabela de dependência de recursos portáteis sob a forma de XML que é copiada para a área de transferência de janelas, juntamente com as informações reais do widget copiado. Quando colou o widget(s) em um projeto diferente, o Studio examina primeiro a lista de dependência de recursos e adiciona os recursos necessários ao projeto aberto se eles já não existirem. O estúdio identifica recursos correspondentes pelos nomes de identificação de recursos, e para recursos de cordas o Studio também compara o conteúdo de cordas. Se forem encontrados recursos correspondentes, o Studio atualiza os IDs de recursos dos widgets colados para utilizar adequadamente os recursos do novo projeto. Se os recursos não forem encontrados, são adicionados.

Quando o Studio adiciona um recurso ao seu projeto como parte de uma operação de pasta widget, o Studio está realmente adicionando uma ligação ao recurso no caso de recursos de fonte e pixelmap. Esta ligação é gerada a partir do projeto de origem, e receberá mensagens de aviso se esses recursos não forem encontrados em relação à localização do projeto do projeto em que está a colar. As ligações de recursos serão adicionadas ao projeto independentemente, mas pode ser necessário copiar manualmente fontes e ficheiros de imagem para os locais adequados sob a sua nova árvore de projeto para eliminar erros de carregamento de recursos. O estúdio não copia .ttf, .png ou .jpg ficheiros de um local para outro.

A maneira mais fácil de evitar quaisquer problemas a este respeito é manter uma estrutura de diretório consistente entre projetos que você quer partilhar. Se quiser mover as coisas do Projeto A para o Projeto B facilmente, então guarde as imagens e tipos de letra gráficos utilizados por ambos os projetos num sub-directório consistente de cada pasta de projeto.

## <a name="changing-z-order"></a>Alteração da Ordem Z

Os widgets podem ser facilmente movidos na frente ou atrás de outros widgets. Isto é conseguido selecionando o widget e selecionando os botões ***Move to Front** _ ou Move to _*_Back_*_ na _*_Tool Bar_*_. _ *_Figura 28_** mostra o movimento do segundo botão para trás.

![Screenshot do botão z-order.](./media/guix-studio/change_z_order.png)

**Figura 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Atribuição de Cores, Fontes e Pixelmaps

Além de selecionar cores, fontes e pixelmaps no View de Propriedades para um widget selecionado, também é suportado um método de arrastar e largar de abreviatura de recursos para widgets. Para utilizar esta função, basta deixar clicar num recurso como uma cor de letra na vista do recurso e arrastar o recurso sobre o widget desejado na vista alvo. Largue o recurso libertando o botão do rato esquerdo sobre o widget.

Os recursos de cor são sempre atribuídos à cor de fundo normal do widget quando se utiliza o método de arrastar e largar. Outras cores, como a cor selecionada ou a cor de texto selecionada, devem ser atribuídas usando a Vista de Propriedades.

Da mesma forma, os recursos pixelmap são atribuídos ao campo pixelmap "normal" ou "preenchimento" de um widget que suporta o ecrã pixelmap. Para atribuir outros campos a um widget que suporte várias pixelmaps, tem de utilizar a Vista de Propriedades.

## <a name="using-templates"></a>Utilizar modelos

Qualquer ecrã ou coleção de widgets infantis que você desenha no Studio pode ser usado como um modelo para novos ecrãs e novos controlos para crianças. A utilização de um modelo é semelhante à cópia e colagem de um widget, exceto que qualquer coisa derivada de um modelo é automaticamente modificada quando o modelo em que se baseia é modificado. Não está autorizado a modificar as propriedades do widget do modelo ao trabalhar com um ecrã derivado ou com uma instância herdada do modelo. No entanto, quando modifica as propriedades do modelo de qualquer forma, todos os casos que referenciam esse modelo são automaticamente atualizados, uma vez que são derivados desse modelo.

Outra vantagem de usar modelos para itens repetidos é que o ficheiro de especificações gerados pelo Studio será geralmente menor em tamanho do que se recriasse os itens repetidores cada vez que são usados.

Para designar que um ecrã ou coleção de widgets para crianças deve ser usado como um modelo, você liga a caixa de verificação "Modelo" na vista de propriedades widget. Assim que ligar a caixa de verificação "Modelo", o widget do modelo aparecerá no ***Insert| O modelo*** puxa para baixo o menu(s).

Como exemplo de utilização de um modelo, pode definir uma janela que é usada como uma barra de botões. Esta janela pode conter vários botões para crianças, e esta barra de botões é usada frequentemente em vários ecrãs. Pode definir uma pequena janela autónoma dentro do seu projeto Studio que contém os botões necessários para crianças e dar a esta janela o nome "button_bar". Em seguida, selecione esta janela e ligue a propriedade "Modelo". Em seguida, selecione um ecrã no qual deseja adicionar esta barra de botões. Utilize o Inserção| Modelo|button_bar comando do menu para inserir uma instância da janela button_bar no seu ecrã. Note que pode reposicionar a barra de botões, mas não está autorizado a alterar a maioria das propriedades. No entanto, pode utilizar o widget button_bar (e qualquer criança) como qualquer outro tipo de widget GUIX pré-definido. Para modificar o button_bar, tem de selecionar o modelo de button_bar para escoar as alterações.

Outro exemplo de um uso típico do modelo é uma aplicação que inclui muitos ecrãs semelhantes. Por exemplo, a aplicação pode ter 10 ecrãs diferentes que todos partilham uma barra de título comum, preencha a cor, o tamanho, etc. Neste caso, você pode definir um ecrã de modelo que inclui widgets para crianças da barra de título e configura o tamanho do ecrã, a cor do preenchimento e outras propriedades. Uma vez definido este ecrã de modelo, pode então derivar os seus 10 ecrãs diferentes deste modelo. Quando utilizar o Inserção| Modelo| \<base_screen> comando do menu, o seu ecrã começará com todos os widgets e configurações do seu ecrã de modelo. Note que cada ecrã que obtém do ecrã do modelo não é uma cópia do modelo, mas é verdadeiramente uma instância derivada do ecrã do modelo. Em seguida, pode personalizar cada ecrã derivado para conter qualquer conteúdo adicional necessário.

Note que além de poupar tamanho o ficheiro de especificações geradas, a utilização de modelos pode facilitar a gestão das alterações à aparência da sua aplicação. No exemplo acima, suponha que você é obrigado a alterar a cor de fundo dos seus 10 ecrãs semelhantes. Em vez de ser obrigado a selecionar cada ecrã e alterar as definições de cor de preenchimento, basta selecionar o modelo de base e alterar a cor de preenchimento, e esta alteração será imediatamente refletida em todos os ecrãs derivados.

Um outro comentário sobre os modelos: deve assegurar-se de que o fluxo de processamento do evento é mantido, o que significa que se fornecer um manipulador de eventos tanto para um ecrã base (para manusear os eventos widget comuns) como para um ecrã derivado, o manipulador de eventos de ecrã derivado deve chamar o manipulador de eventos base_screen no caso padrão. Isto permitirá ao manipulador de eventos de ecrã base processar eventos gerados por widgets comuns a todos os ecrãs derivados desta base de modelo.

## <a name="record-and-playback-macro"></a>Macro de Gravação e Reprodução

As funções de gravação e reprodução macro ajudam-no a gravar e a reproduzir teclas e eventos de rato.

A gravação num ficheiro macro é realizada selecionando o botão ***Gravação Macro** _ ou o menu que seleciona _*_Editar, Gravar Macro_*_. O GUIX Studio apresentará o diálogo _*_Record Macro_*_ que lhe permite especificar o nome de pathname para o seu ficheiro macro. Depois de escamar esta seleção, clique no botão _*_Gravar_*_ para começar a gravar. Depois de ter terminado a gravação, selecione novamente o botão de barra de ferramentas _*_Record Macro_*_ ou utilize o menu de puxar para baixo selecionando _ *_Edit, End Macro_** para terminar a gravação macro.

A reprodução de um ficheiro macro é realizada selecionando o botão ***Reversão Macro** _ usando o menu de pull-down principal para selecionar o comando _*_Edit, Reprodução Macro._*_ O GUIX Studio apresenta o diálogo _ *_Playback Macro_** que lhe permite especificar o ficheiro macro previamente gravado a ser executado.

Ao gravar macros que escolhem ficheiros de entrada ou saída, como adicionar um tipo de letra ou imagem, é importante usar o teclado para escrever o nome do ficheiro, em vez de usar o rato para selecionar a partir do navegador de ficheiros. Uma vez que o gravador macro regista eventos de rato e teclado, e uma vez que o seu navegador de ficheiros pode mudar ao longo do tempo, é mais fiável escrever o nome de ficheiro do que selecionar o ficheiro graficamente.

## <a name="zooming-target-view"></a>Vista de alvo de zooming

Zoom In função ajuda-o a ter uma visão de perto do ecrã alvo.

É capaz de escolher a definição de zoom percentual que deseja em ***Configurar| Vista do alvo| Opção** de menu Zoom _ . A _ *_Tool Bar_** também tem botões para fazer zoom dentro e fora.

## <a name="gridsnap-settings"></a>Definições de grelha/encaixe

As **definições*** Grelha e Definições de Encaixe _ o diálogo contêm algumas definições e opções para grelhar e estalar. _*_A figura 29_*_ mostra o diálogo _*_de definição de grelha e de encaixe_*_ no menu _ *_Congigure| Vista do alvo| A grelha/encaixe_** está selecionada.

![Screenshot das definições de grelha e de encaixe.](./media/guix-studio/image63.jpg)

**Figura 29**

Ligue * A opção **Show Grid** _ apresentará grelha no ecrã alvo, podendo especificar o incremento da grelha (em pixels) no campo de _*_espaçamento da grelha._*_ A opção _ *_Snap to Grid_** ajuda-o a obter a posição adequada de um widget, ligue esta opção irá ativar os encaixes.

Quando a opção ***Grid e Snap*** estiver ativada:

- Se arrastar um objeto com o rato na vista do alvo, o objeto move-se-ia por incremento da grelha.
- Se arrastar a borda de um objeto para redimensionar, a borda que está a arrastar encaixar-se-ia na posição da grelha.
- Se selecionar um objeto e utilizar teclas para cima/esquerda/para baixo/direita, o widget selecionado move-se-ia por incremento de encaixe, podendo especificar o incremento de encaixe (em pixels) no campo ***de espaçamento do Snap.***
