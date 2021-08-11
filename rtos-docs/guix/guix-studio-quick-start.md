---
title: Azure Real-Time Sistema Operativo (RTOS) GUIX Studio Quick Start Guide
description: Este guia fornece uma breve introdução à utilização da aplicação Azure RTOS GUIX Studio, o ambiente de desenvolvimento rápido de UI baseado na Microsoft Windows especificamente concebido para a biblioteca de tempo de execução Azure RTOS GUIX da Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ab4dfb2edd8990692ee3dc134207f43e4c757538dbc738f6f406bf40864bfb3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785429"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Guia de arranque rápido do estúdio Azure RTOS GUIX

Este guia fornece uma breve introdução ao uso do Azure RTOS GUIX Studio. O GUIX Studio é uma aplicação de design UI baseada em Windows projetada para ser utilizada com a biblioteca de tempo de execução Azure RTOS GUIX da Microsoft. 

Destina-se ao desenvolvedor de software incorporado em tempo real utilizando o Sistema Operativo Real-Time ThreadX (RTOS) e a biblioteca de tempo de execução Azure RTOS GUIX UI. O desenvolvedor deve estar familiarizado com os conceitos standard Azure RTOS ThreadX e Azure RTOS GUIX.

## <a name="summary"></a>Resumo

O Azure RTOS GUIX Studio inclui tudo o que precisa para criar, construir e executar o seu próprio design de interface gráfica. Se estiver a avaliar o GUIX Studio, o kit de avaliação foi concebido para permitir que construa e execute o seu design GUIX como uma aplicação autónoma Windows desktop para fins de teste e avaliação. Uma vez que o GUIX foi concebido para ser utilizado em quase qualquer alvo incorporado capaz de produzir gráfica, o trabalho que faz e os desenhos que cria no ambiente de trabalho podem sempre ser compilados e executados no seu alvo incorporado sem alterar nenhum dos seus softwares de aplicação.
O instalador do GUIX Studio coloca vários componentes no seu sistema de desenvolvimento:

- A aplicação do ESTÚDIO GUIX.
- Vários projetos de exemplo GUIX.
- Todos os recursos gráficos e fontes utilizadas nos projetos de exemplo.
- Ficheiros de solução e ficheiros de projeto para construir num ambiente de ambiente de trabalho Windows utilizando o Microsoft Visual Studio IDE.
- Bibliotecas GUIX e ThreadX pré-construídas para o Win32, permitindo-lhe construir e executar as suas próprias aplicações no seu PC.
- Ficheiros de cabeçalho aPI GUIX e ThreadX.

## <a name="prerequisites"></a>Pré-requisitos

O instalador do Azure RTOS GUIX Studio inclui vários projetos de exemplo simples, e esperamos que comece por modificar, construir e executar estes exemplos à medida que aprende a usar a aplicação do GUIX Studio. Para construir e executar os exemplos no ambiente de trabalho Windows, precisará de um compilador microsoft Visual Studio. Estas ferramentas podem ser descarregadas a partir do seguinte local:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Se não tiver as ferramentas de desenvolvimento da Microsoft instaladas, ainda pode chutar os pneus e utilizar a aplicação GUIX Studio para criar o seu próprio design de interface e examinar o código fonte produzido. No entanto, não será capaz de construir e executar o seu design como uma aplicação autónoma.

## <a name="running-the-examples"></a>Executar os Exemplos

Depois de executar o instalador do GUIX Studio, encontrará vários exemplos de projeto studio e os ficheiros de construção estão incluídos nos conteúdos instalados. Para verificar se as suas ferramentas de ambiente de trabalho estão instaladas e a funcionar corretamente, recomendamos que comece por construir e executar cada um dos exemplos fornecidos como está. Referimo-nos ao seu diretório de instalação como \<root> , caso em que deve utilizar o seu navegador de ficheiros e navegar para \<root> /GUIX_Studio_6.x/exemplos. Dentro deste diretório você deve ver vários programas de exemplo simples, como demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types, entre outros.

## <a name="building-an-example"></a>Construir um exemplo

Deve encontrar uma subdiretória denominada *construção* dentro de cada pasta de exemplo. Esta direção inclui projetos pré-configurados para cada ferramenta apoiada. Por exemplo, pode navegar para \<root> /GUIX_Studio_6.x/exemplos/termómetro/build/vs_2019 e encontrará um ficheiro de solução e ficheiro de projeto pré-configurado da Microsoft Visual Studio pronto para ser carregado e executado no Visual Studio IDE. Se desejar utilizar uma ferramenta diferente, contacte [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request).

Recomendamos que inicie o Microsoft Visual C++ IDE e abra pelo menos um destes exemplos. Pressione a \<F7> tecla para construir o projeto exemplo e pressione a \<F5> tecla para executar o programa depois de construir com sucesso. Deverá agora ver uma interface de utilizador GUIX a funcionar dentro de uma janela Windows Microsoft.

## <a name="designing-and-running-your-own-user-interface"></a>Projetar e executar a sua própria interface de utilizador

Este guia de arranque rápido não substitui o Guia do Utilizador do Estúdio GUIX ou o Guia do Utilizador guix, mas mostrar-lhe-emos o suficiente para começar e encorajá-lo a continuar, remetendo para o Guia do Utilizador do Estúdio GUIX para obter informações mais detalhadas.

Existem dois métodos para criar e modificar a sua própria interface de utilizador. Pode estudar o manual de programação da biblioteca GUIX e utilizar a API GUIX diretamente a partir do seu software de aplicação para implementar totalmente o seu design. Mais frequentemente, utilizará a aplicação GUIX Studio para fazer a maior parte do trabalho de design e layout dos seus elementos de ecrã e, em seguida, completará o tratamento do evento e outra lógica de aplicação necessária para fazer com que a sua interface de utilizador realize um verdadeiro trabalho.

Cada um dos exemplos fornecidos foi criado usando a aplicação de design de interface GUIX Studio. Deverá ter um ícone no seu ambiente de trabalho para GUIX Studio 6.x.x.x.x depois de executar o instalador do ESTÚDIO GUIX.  Inicie agora o GUIX Studio e abra o projeto denominado "demo_guix_widget_types\guix_widget_types.gxp". A *demonstração de widget_types* é um projeto de exemplo que demonstra várias variações dos tipos de widget GUIX mais comuns.

Agora que tem um projeto aberto, clique em "+" para abrir o nó de árvore denominado "Primário" no Project Ver no canto superior esquerdo do IDE, e clique na janela de nível superior dentro desta pasta chamada "Menu_Screen". O seu projeto não deve aparecer como mostrado abaixo:

![Screenshot do Estúdio com projeto aberto.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>Vistas do estúdio GUIX

O GUIX Studio IDE é composto por várias ***vistas.*** Cada vista é projetada para ajudá-lo a navegar através do seu design e fazer alterações nesse design.

### <a name="project-view"></a>Project Ver

A vista superior à esquerda chama-se Project View. Esta vista mostra-lhe cada um dos ecrãs físicos que estão incluídos no seu projeto (a maioria dos projetos tem apenas um ecrã), e os ecrãs e widgets infantis que foram projetados para serem executados nesse ecrã.

### <a name="properties-view"></a>Vista de propriedades

Abaixo da vista Project está a vista de propriedades. Como o nome Properties View implica, esta vista permite modificar widgets alterando várias propriedades associadas a eles.

### <a name="target-view"></a>Vista do alvo

A área central de exibição chama-se Target View. Esta vista é uma exibição WYSIWYG da sua interface de utilizador. Como a biblioteca GUIX está a desenhar dentro da vista do alvo, esta vista é uma representação precisa de pixels de como o seu design vai ficar ao executar o seu alvo incorporado. Se clicar em diferentes widgets quer no Project Ver ou na Vista Alvo central, verá os valores apresentados na alteração 'Visualização de Propriedades' para visualizar as propriedades do widget selecionado.

### <a name="resource-view"></a>Vista de Recursos

Finalmente, à direita, verá o que é chamado de Vista de Recursos. Esta vista permite-lhe selecionar, adicionar, excluir e modificar as cores, fontes, pixelmaps e cordas incluídas no seu projeto.

## <a name="modifying-the-example"></a>Modificar o Exemplo

O GUIX Studio foi concebido para ser intuitivo. Para mover um dos widgets acima mostrados, basta clicar nesse widget na Vista Alvo e arrastá-lo para um novo local. Para alterar as cores do widget, clique no widget desejado e altere as cores exibidas na Vista de Propriedades. Para alterar o tipo de letra utilizado por um widget de exibição de texto, basta clicar no tipo de letra pretendido dentro da Vista de Recursos e arrastar e largar o tipo de letra no widget alvo pretendido. Flutue o rato ao longo dos botões da barra de ferramentas para ver uma ajuda rápida no que diz respeito ao funcionamento que cada botão executa.

Experimente-se e faça algumas pequenas alterações no exemplo. Por exemplo, pode arrastar um widget para uma nova localização, alterar a cor de fundo da janela ou redimensionar um botão. Não recomendamos a eliminação de widgets do exemplo até ganhar mais experiência a trabalhar com o GUIX, uma vez que eliminar widgets pode exigir modificações associadas ao código fonte de aplicação.

## <a name="running-the-application-within-studio"></a>Executando a aplicação dentro do Estúdio

Pode utilizar o Edit | Executar o comando do menu de aplicação (ou executar o botão 'Executar' na barra de botões) para executar a aplicação imediatamente dentro de uma nova janela do ambiente de trabalho. As funções de desenho personalizado e outro código de aplicação não serão invocadas usando este método, mas permite-lhe navegar rapidamente através do seu design de UI e ter uma ideia geral do aspeto e sensação da aplicação, incluindo a navegação de um ecrã para o outro.

## <a name="generating-source-files"></a>Gerar ficheiros de origem

Depois de escoar as suas alterações, precisa de invocar comandos de menu GUIX Studio para gerar novos ficheiros de origem para o seu projeto. Em seguida, pode reconstruir o programa de exemplo para ver as suas alterações em ação. Para gerar ficheiros de origem, utilize os comandos do menu GUIX Studio Project| Gerar ficheiros de recursos e Project| Gere ficheiros de especificações (também pode clicar no ecrã no visor Project para executar estes comandos).

À medida que gera estes novos ficheiros de origem, deve observar uma mensagem de confirmação a dizer-lhe que os ficheiros de origem associados ao seu projeto foram atualizados. Se não observar esta mensagem de confirmação, verifique se tem permissões de escrita para o diretório em que o projeto reside. Pode agora fechar a aplicação guix Studio. Se fez alterações no projeto, o GUIX Studio perguntar-lhe-á se pretende guardar essas alterações. Vá em frente e guarde as suas alterações, estes exemplos destinam-se a usar e experimentar à medida que aprende a usar o GUIX Studio.

### <a name="building-and-running-the-application"></a>Construção e execução da aplicação

Agora que o GUIX Studio gerou os seus ficheiros de saída do projeto, pode compilar e ligar para criar um Win32 autónomo executável. Além disso, para incorporar qualquer desenho personalizado ou manipulação de eventos que tenha definido na sua aplicação, precisa de compilar e ligar os ficheiros de saída gerados pelo GUIX Studio com o seu próprio software de aplicação. Usaremos como exemplo a ferramenta Microsoft Visual C++, mas exatamente o mesmo procedimento é utilizado se estiver a construir e a correr para o alvo pretendido.

- Inicie o MSVC IDE e abra a solução \<root> /GUIX_Studio_5.x/exemplos/demo_guix_widget_types/build/vs_2019/guix_widget_types.sln.

- Utilize a \<F7> chave para reconstruir a solução.
- Use a \<F5> chave para executar o programa.
 
Deve agora ver o programa de execução, com as alterações que fez dentro do Estúdio!

### <a name="learning-more"></a>Saber Mais

O **Guix Studio User Guide** está disponível no [azrtos-guix-studio-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio). O GUIX Studio User Guide é um guia muito mais completo para a utilização do GUIX Studio.

Além disso, o Guia do **Utilizador GUIX** está disponível no [azrtos-guix-user-guide](https://docs.microsoft.com/azure/rtos/guix/about-guix).  Este guia dá-lhe informações muito mais detalhadas sobre o que está a acontecer "Under the Hood" quando a sua aplicação GUIX é executada. Terá de consultar ambos os guias para utilizar plenamente as capacidades da biblioteca de tempo de execução GUIX e do GUIX Studio.

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

- Uma descrição detalhada do problema, incluindo a frequência de ocorrência e como pode ser reproduzida de forma fiável.
- Prenda o ficheiro de rastreio que causa o problema.
- A versão do Azure RTOS GUIX Studio que está a utilizar (mostrada na parte superior esquerda do ecrã).
- A versão do Azure RTOS GUIX que está a usar incluindo a **variável _gx_version_idstring** e **_gx_build_options.**
