---
title: Descrição do ESTÚDIO GUIX
description: Este capítulo contém uma descrição da ferramenta de análise do sistema GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826371"
---
# <a name="chapter-3-description-of-guix-studio"></a>Capítulo 3: Descrição do ESTÚDIO GUIX

Este capítulo contém uma descrição da ferramenta de análise do sistema GUIX Studio. Neste capítulo encontra-se uma descrição da funcionalidade global do GUI. 

## <a name="guix-studio-views"></a>Vistas do estúdio GUIX

Existem cinco áreas principais do GUIX Studio UI, nomeadamente o ***Toolbar** _, _*_Project View,_*_ _*_Properties View,_*_ _*_Target View_*_ e _*_Resource View_*_. _ *_Figura 2_** mostra o básico GUIX Studio UI. Cada um dos pontos de vista é discutido nas subsecções seguintes.

![Screenshot do básico GUIX Studio UI.](./media/guix-studio/image_10.png)

**Figura 2**

### <a name="title"></a>Título

- GUIX Studio 18: O ***Title** _ exibe a versão GUIX Studio, bem como o projeto atualmente aberto, como mostrado no topo de _ *_Figura 2_** anteriormente.

### <a name="toolbar"></a>Barra de ferramentas

A ***Toolbar** _ mostra os botões disponíveis para o desenvolvedor do ESTÚDIO GUIX, como mostrado em _*_Figura 3_**.

![Screenshot da barra de ferramentas DO ESTÚDIO GUIX.](./media/guix-studio/image11.jpg)

**Figura 3**

Os botões da barra de ferramentas são definidos da seguinte forma:

![Botão Novo](./media/guix-studio/new-button.png) Cria um novo projeto guix Studio

![Botão aberto](./media/guix-studio/open-button.png) Abre um projeto do ESTÚDIO GUIX existente

![Botão Guardar](./media/guix-studio/save-button.png) Salva o projeto

![Botão de corte](./media/guix-studio/cut-button.png) Widget de corte selecionado, incluindo crianças

![botão Copiar](./media/guix-studio/copy-button.png) Copiar widget selecionado, incluindo crianças

![Botão de pasta](./media/guix-studio/paste-button.png) Widget de pasta e crianças

![Botão de alinhamento esquerdo](./media/guix-studio/left-align-button.png) Widgets selecionados de alinhamento esquerdo

![Botão de alinhamento direito](./media/guix-studio/right-align-button.png) Widgets selecionados de alinhamento direito

![Botão de alinhamento superior](./media/guix-studio/top-align-button.png) Widgets selecionados de topo

![Botão de alinhamento inferior](./media/guix-studio/bottom-align-button.png) Widgets selecionados de baixo

![Botão vertical do espaço](./media/guix-studio/space-vertically-button.png) Widgets igualmente selecionados em espaço verticalmente

![Botão horizontal do espaço](./media/guix-studio/space-horizontally-button.png) Widgets igualmente selecionados pelo espaço horizontalmente

![Botão de largura igual](./media/guix-studio/equal-width-button.png) Faça widgets selecionados igual largura

![Botão de altura igual](./media/guix-studio/equal-height-button.png) Faça widgets selecionados igual altura

![Mover botão frontal](./media/guix-studio/move-front-button.png) Mova widgets selecionados para a frente

![Mova-se para trás botão](./media/guix-studio/move-back-button.png) Mova widgets selecionados para trás

![Botão de tamanho](./media/guix-studio/size-button.png) Tamanho do widget selecionado para conteúdo Zoom fora do ecrã alvo

![Botão de zoom para fora](./media/guix-studio/zoom-out-button.png) Zoom fora do ecrã alvo

![Zoom no botão](./media/guix-studio/zoom-in-button.png) Zoom no ecrã alvo

![Botão de gravação](./media/guix-studio/record-button.png) Record Macro

![Botão de reprodução](./media/guix-studio/playback-button.png) Macro de reprodução

![Botão de execução](./media/guix-studio/run-button.png) Aplicação de execução

![Sobre o botão](./media/guix-studio/about-button.png) Sobre o ESTÚDIO GUIX

### <a name="project-view"></a>Vista do Projeto

O ***Project View** _ mostra a lista hierárquica de objetos GUIX que compõem a UI incorporada. Novos objetos GUIX podem ser adicionados clicando no objeto-mãe e, em seguida, selecionando um objeto a partir do menu _*_Inserção_*_ (ou clicando à direita no objeto e selecionando a partir do menu de clique à direita). _*_Figura 4_*_ abaixo mostra o GUIX Studio _*_Project View_**.

![Screenshot do GUIX Studio Project View.](./media/guix-studio/image_35.png)

**Figura 4**

### <a name="properties-view"></a>Vista de propriedades

O ***Properties View** _ mostra informações detalhadas sobre a propriedade do objeto GUIX atualmente selecionado, que podem ser selecionados através do _*_Project View_*_ ou clicando diretamente no objeto na _*_Vista Alvo._*_ _*_A figura 5_*_ abaixo mostra o GUIX Studio _*_Properties View_**.

![Screenshot da visão do estúdio GUIX.](./media/guix-studio/image36.jpg)

**Figura 5**

### <a name="target-view"></a>Vista do alvo

A ***Target View** _ é a área de design e layout do ecrã WYSIWYG. Esta vista destina-se a representar o ecrã físico ou os ecrãs disponíveis no hardware do seu alvo. Os objetos podem ser selecionados, movidos, redimensionados, etc. através de simples operações de rato. Além disso, as operações de alinhamento e botão de ordem Z estão disponíveis em objetos selecionados na Vista Alvo. A seleção de um objeto na _*_Vista Alvo_*_ também resultará nas propriedades para que o objeto seja exibido na Vista _*_de Propriedades_*_. _*_A figura 6_*_ abaixo mostra o ESTÚDIO GUIX _*_Target View_**.

![Screenshot do GUIX Studio Target View.](./media/guix-studio/image_37.png)

**Figura 6**

### <a name="resource-view"></a>Vista de Recursos

O ***Resource View** _ é utilizado para gerir os recursos (cores, fontes, pixelmaps e cordas) disponíveis para ecrãs de aplicações definidos para cada ecrã. Pode clicar nos cabeçalhos do grupo de visualização de recursos para expandir cada grupo e examinar o conteúdo do grupo. _*_A figura 7_*_ abaixo mostra o GUIX Studio _*_Resource View_**.

![Screenshot da visão de recursos do estúdio GUIX.](./media/guix-studio/image38.jpg)

**Figura 7**

O título dos grupos de recursos indica o nome temático atual. Se vários temas disponíveis, é possível alternar entre temas clicando na seta para cima e para baixo.

Cada grupo de recursos na vista acima pode ser expandido ou colapsado clicando no cabeçalho de grupo. Segue-se uma descrição mais pormenorizada de cada grupo de recursos no capítulo seguinte.

## <a name="the-guix-studio-project"></a>O PROJETO ESTÚDIO GUIX

Um projeto guix Studio mantém informações sobre o seu design de ecrã de UI e recursos de UI. Os dados do projeto são guardados num ficheiro de formato XML com a extensão ". ***gxp***". Uma vez que o ficheiro do projeto é um ficheiro de esquema XML, pode ser versão controlada e partilhada semelhante a qualquer outro ficheiro de origem.

Quando começar a usar o GUIX Studio, terá de abrir um dos projetos de exemplo fornecidos com a distribuição ou criar um novo projeto. Todo o seu trabalho é guardado no ficheiro de dados do projeto.

O GUIX Studio também produz ficheiros de origem ANSI C. Estes ficheiros de origem contêm os seus recursos de aplicação ou estruturas de dados que descrevem os seus ecrãs desenhados. O GUIX Studio também escreve para estes ficheiros de origem gerados funções API que sabem utilizar as estruturas de dados geradas para criar dinamicamente os seus ecrãs de aplicação. O seu software de aplicação irá simplesmente invocar as funções API fornecidas para criar os ecrãs que concebeu no ESTÚDIO GUIX.

À medida que progride na conceção da sua interface de utilizador, irá periodicamente querer utilizar o GUIX Studio para gerar os ficheiros de saída compatíveis com o GUIX que lhe permitirão construir e executar a interface que concebeu. Pode compilar e executar os ficheiros de origem gerados para o hardware do seu alvo ou no seu ambiente de trabalho windows que simula ThreadX e GUIX.

## <a name="guix-studio-project-organization"></a>GUIX Studio Project Organization

É útil ter algum conhecimento da organização básica de um projeto do GUIX Studio para entender como usar o GUIX Studio de forma eficaz e compreender a informação apresentada no Project View do GUIX Studio IDE. O Project View é uma representação visual sumária de toda a informação contida no seu projeto.

Antes de descrever o projeto, é necessário definir poucos termos. Primeiro, usamos o termo **Display** para significar um dispositivo de exibição física. Trata-se, na maioria das vezes, de um dispositivo de exibição LCD, mas pode estar a utilizar outras tecnologias. O próximo termo é **Screen**, que significa um objeto GUIX de alto nível, geralmente uma janela GUIX, e todos os seus elementos infantis associados. Um Ecrã é uma construção de software que pode ser definida e modificada no tempo de execução. Finalmente, um **tema** é uma coleção de recursos. Um tema inclui uma tabela de definições de cores, definições de fontes e definições de pixelmap que são projetadas para trabalhar bem em conjunto e apresentar o seu utilizador final com um aspeto e sensação consistentes.

O projeto inclui primeiro um conjunto de informações globais, como o nome do projeto, o número de ecrãs suportados, a resolução e o formato de cores de cada ecrã, o número de idiomas suportados, o nome de cada idioma apoiada. O nome do projeto é o primeiro nó exibido no Project View.

O projeto em seguida organiza toda a informação necessária para até 4 ecrãs físicos e os ecrãs e recursos disponíveis para cada ecrã. Os nomes do visor são os próximos nós de nível na árvore Project View.

Uma característica única da aplicação guix Studio é suporte incorporado para múltiplos ecrãs físicos, cada um com a sua própria resolução x,y, formato de cores, ecrãs e recursos. Embora a grande maioria das aplicações GUIX utilize apenas um ecrã físico, esta capacidade é importante para quem faz um produto que deve suportar múltiplos ecrãs físicos simultâneos.

Por baixo de cada definição de exibição encontram-se as janelas ou ecrãs de nível superior definidos para esse ecrã. As definições do ecrã podem ser aninhadas a qualquer nível, dependendo do número e da nidificação de widgets infantis em cada ecrã.

Esta organização de widget infantil e de ecrã infantil é exibida de forma gráfica no Project View.

Também associados a cada ecrã estão os Temas suportados pelo visor e o conteúdo de recursos que compõem cada tema. Se o seu projeto incluir vários ecrãs, notará que a Visualização de Recursos altera o seu conteúdo quando selecionar um ecrã e depois outro. Isto porque o conteúdo do recurso está ligado a cada visualização. Não só o formato de cores pode ser diferente, mas os pixelmaps, cores e fontes que escolhe utilizar podem variar de um ecrã físico para outro.

O componente final mantido pelo projeto são os dados da tabela de cordas associados a cada visor. Uma vez que os ecrãs podem ser de resoluções x,y muito diferentes, os dados de cadeia são mantidos independentemente para cada ecrã definido no projeto.
