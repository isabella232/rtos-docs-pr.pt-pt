---
title: Definição de Flow de tela
description: O GUIX Studio suporta a geração automática e a execução da lógica de transição de ecrã.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 1df90acd86b4446d96a66ab3ee21545afcd9824e28efb40204c2966cb075c501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785614"
---
# <a name="chapter-7-defining-screen-flow"></a>Capítulo 7: Definição de Flow de tela

O GUIX Studio suporta a geração automática e a execução da lógica de transição de ecrã. O utilizador define a lógica de transição do ecrã criando e editando um diagrama de fluxo de ecrã gráfico. Quando um diagrama de fluxo de ecrã é adicionado ao projeto, permite duas características importantes: 1) A aplicação pode ser executada dentro do ambiente studio e 2) O estúdio gera automaticamente manipuladores de eventos e lógica de transição de ecrã para implementar o fluxo de ecrã designado dentro das especificações geradas.c ficheiro, removendo este fardo do programa de aplicação. 

Executar a aplicação no seu ambiente de desktop a partir do ambiente Studio é uma funcionalidade útil que poupa tempo na qual não é obrigado a passar por um ciclo de compilação/ligação para executar a sua aplicação. Existem, naturalmente, limitações ao que pode ser feito sem compilar a aplicação. As funções de desenho personalizadas, os manipuladores de eventos personalizados e o tratamento complexo de eventos não estão disponíveis quando executam a aplicação dentro do ambiente do ESTÚDIO GUIX. Ainda assim, esta capacidade permite-lhe gerar automaticamente a lógica de transição de ecrã, e as animações de programa a serem executadas para a transição de um ecrã para outro. Estes efeitos e animações podem ser observados diretamente a partir do ambiente do ESTÚDIO GUIX.

Note que quando define o fluxo de ecrã, os gatilhos e as ações que descreveremos nos parágrafos seguintes, não só está a permitir a execução da sua UI a partir do ambiente studio, como também está a permitir que o GUIX Studio gere lógica dentro do seu ficheiro de especificações que lidará com eventos e tomará ações com base nesses eventos,  como a transição de um ecrã para outro.

## <a name="configuring-screen-flow"></a>Flow de tela de configuração

Antes de uma aplicação poder ser executada dentro do ambiente studio algumas coisas devem ser definidas. Em primeiro lugar, o ecrã ou ecrãs de nível superior que devem ser exibidos no arranque do programa devem ser indicados selecionando a propriedade "Visível no Arranque" na vista propriedades do Estúdio. Esta bandeira indica que este ecrã deve ser apresentado inicialmente quando o programa começar. Mais de um ecrã pode ter esta designação se desejar.

Depois de definir os ecrãs que são visíveis no arranque, o utilizador pode definir como a aplicação UI fluirá de ecrã para ecrã. O GUIX Studio fornece um diagrama de fluxo de ecrã gráfico para definir a lógica de transição do ecrã. Basta selecionar a seleção do menu ***Configurar, Screen Flow** _ para aumentar o diálogo de edição de fluxo de ecrã, ver o ecrã filmado em _*_Figura 30_**.

![Screenshot do guix Studio Screen Flow diálogo.](./media/guix-studio/config_screen_flow.png)

**Figura 30**

Cada ecrã de nível superior definido no projeto será mostrado como uma caixa que mostra o nome do ecrã. Esta caixa é um espaço reservado que representa cada ecrã de nível superior definido no projeto. Estas caixas podem ser movidas e redimensionadas como desejado. Quando for definida uma transição de um ecrã de nível superior para outro, será mostrada uma linha de ligação com uma cabeça de seta entre dois ecrãs para indicar transições de um ecrã para outro.

A vista da árvore no lado esquerdo do diagrama de fluxo de ecrã mostra cada ecrã de nível superior e é capaz de selecionar quais os ecrãs de nível superior que devem ser desenhados no diagrama de fluxo de ecrã.

O diagrama de fluxo de ecrã é percável. É possível arrastar qualquer bloco de ecrã para baixo e para fora da área visível para ampliar a janela de scrollable. Uma vez ampliada a janela de deslocalizadora, é capaz de fazer zoom para fora para que se encaixe na área visível deslocando a roda do rato para baixo. Se a janela de scrollable for ampliada para fora, você é capaz de torná-lo grande o suficiente para segurar todos os blocos deslocando a roda do rato para cima.

Para definir transições para um ecrã, clique no espaço reservado para que o ecrã possa apresentar um diálogo da Lista de Gatilhos de Edição, consulte ***a Figura 31***.

![Screenshot do diálogo da Lista de Gatilhos de Edição de Estúdio GUIX.](./media/guix-studio/edit_trigger_list.png)

**Figura 31**

A lista de diálogo de edição de gatilhos lista os eventos que o utilizador definiu que irá desencadear uma transição de ecrã, razão pela qual chamamos estes desencadeadores de eventos. Os gatilhos são normalmente sinais gerados por um ou mais widgets infantis do ecrã selecionado.

Para definir um novo gatilho, selecione o botão ***Add New Trigger** _ no diálogo 'Edit Trigger List' para aumentar o diálogo do gatilho de adicionar mostrado em _* Figura _32_**.

![Screenshot do diálogo GUIX Studio Add Trigger.](./media/guix-studio/add_trigger_for.png)

**Figura 32**

Você é capaz de definir o tipo de evento que irá desencadear um novo conjunto de ações, e definir as ações que serão executadas quando esse evento de gatilho é recebido.

Assim que definir o tipo de evento que pretende utilizar para desencadear uma nova transição de ecrã de animação, guarde este novo gatilho e será exibido no diálogo 'EditAr'.

Pode modificar este evento (sem modificar as ações relacionadas a serem tomadas) selecionando o evento no diálogo 'Edit Trigger List' e selecionando o botão ***Edit Trigger Event.***

Da mesma forma, pode remover qualquer evento de gatilho da lista selecionando o evento e clicando no botão ***Eliminar O gatilho selecionado.***

Para especificar a transição de animação ou ecrã que deve ocorrer com base num determinado evento de gatilho, selecione o evento de gatilho e clique no botão ***Edit Action(s).*** Note que pode disparar mais do que uma ação com base em cada gatilho definido.

O botão **Editar Ação(s)** apresenta as ações de edição para o diálogo do gatilho, mostradas na Figura 33: 

![Screenshot das ações de edição do estúdio GUIX para o diálogo do gatilho.](./media/guix-studio/edit_actions_for_trigger.png)

**Figura 33**

Este diálogo permite-lhe definir qualquer número de ações para implementar com base neste evento de gatilho. Pode dar a cada ação um nome significativo para ajudá-lo a associar cada definição de ação a uma animação visual ou transição. No exemplo acima, definimos duas ações denominada "fade_in_text_screen" e "fade_out_button_screen".

Definir uma nova ação para implementar, clique no botão Add New Action, que eleva o diálogo Select Action, Figura 34:

![Screenshot do diálogo GUIX Studio Select Action.](./media/guix-studio/select_action.png)

**Figura 34**

Os tipos de ação disponíveis incluem:

- **Animação**: Inicie uma animação com informações especificadas.
- **Fixe:** Fixe o ecrã-alvo ao ecrã dos pais, se o ecrã dos pais não for especificado, o ecrã-alvo será fixado à janela raiz.
- **Separar:** Retire o ecrã do alvo do seu progenitor.
- **Ocultar:** Ocultar o ecrã do alvo.
- **Screen Stack Pop**: Coloque um ecrã a partir da pilha de ecrã interno.
- **Screen Stack Push**: Empurre um ponteiro de ecrã para a pilha interna do ecrã.
- **Reset da pilha de** ecrã : Remova todos os ponteiros do ecrã da pilha interna do ecrã.
- **Mostrar**: Mostrar o ecrã do alvo.
- **Toggle**: Fixe o ecrã-alvo ao progenitor do ecrã atual e retire o ecrã atual do progenitor.
- **Execução da janela**: Modally executa o ecrã alvo.
- **Paragem de execução da janela**: Saída modally execução do ecrã atual.

Uma vez definida uma ação a tomar com base no evento de gatilho selecionado, essa ação será exibida nas Ações de Edição para o diálogo Do gatilho. Pode selecionar esta ação para modificar os parâmetros dessa ação, tal como mostrado na Figura 35.

![Screenshot das ações de edição do estúdio GUIX para o diálogo do gatilho.](./media/guix-studio/edit_actions_for_trigger.png)

**Figura 35**

Se o tipo de ação for uma animação, é apresentado um conjunto de parâmetros de animação à direita para permitir definir uma animação do tipo slide e/ou desvanecimento a ser executada. Quando uma ação de animação é concluída, também pode determinar se a animação deve ser automaticamente separada do seu progenitor e/ou empurrada para a pilha de ecrã interno, o que é muitas vezes útil na definição de sistemas de menus de várias camadas.

Para animações de diapositivos e desvanecimento, também pode definir a Função de Flexibilização a utilizar selecionando o botão Easing Func Select. As funções de flexibilização são várias curvas projetadas para imitar mais de perto os eventos de movimento da vida real. A seleção deste botão eleva o diálogo **Select Easing Function,** Figura 36:

![Screenshot do diálogo GUIX Studio Select Easing Function.](./media/guix-studio/easing_function_select.png)

**Figura 36**

Se estiver a definir várias ações para associar a um evento de gatilho, pode ser útil atribuir a cada ação um nome significativo. Os nomes de ação devem seguir as regras de nomeação de sintaxe C, uma vez que estes nomes serão utilizados dentro do ficheiro de especificações geradas para definir as tabelas de eventos e de ação.

Quando define eventos e ações de desencadeamento dentro do GUIX Studio, os manipuladores automatizados de eventos são gerados dentro do seu ficheiro de especificações do projeto para lidar com estes eventos e executar as ações especificadas. Isto significa que NÃO precisa de lidar com estes eventos no seu código de aplicação, embora os eventos de gatilho ainda sejam transmitidos a quaisquer manipuladores de eventos personalizados que tenha definido. Por outras palavras, o Studio gerou manipuladores de eventos aumentando, em vez de substituir, os seus próprios manipuladores de eventos personalizados.

## <a name="running-the-application"></a>Executar a Aplicação

Uma vez criados ecrãs de arranque e um diagrama de fluxo de ecrã, pode executar a sua aplicação dentro do Estúdio selecionando a "Aplicação run"

![Screenshot do botão 'Aplicação de execução'.](./media/guix-studio/image68.jpg)

botão na barra de ferramentas, selecionando Editar | Executar a aplicação a partir do menu do projeto, ou selecionando o botão Executar na parte inferior do Flow diálogo do ecrã de edição.

Quando executar a aplicação, verá o(s) ecrã(s) que designou como ecrã "Visível no Arranque" dentro de uma nova janela. Os widgets da criança nestes ecrãs estão totalmente operacionais. Pode clicar em botões, operar sliders e rodas de deslocamento, etc.. Se tiver definido funções de desenho personalizado ou manuseamento de eventos do cliente para qualquer um destes widgets, é claro que não o verá ao executar a aplicação neste modo. Mas se definiu um diagrama de fluxo de ecrã com eventos e ações de gatilho, esses gatilhos estarão operacionais e os seus ecrãs irão transitar como definiu, incluindo quaisquer animações que possa ter definido.
