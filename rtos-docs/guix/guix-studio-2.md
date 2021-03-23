---
title: Instalação e Utilização do Estúdio GUIX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de design do sistema UI do ESTÚDIO GUIX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827169"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a>Capítulo 2: Instalação e Utilização do Estúdio GUIX

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de design do sistema UI do ESTÚDIO GUIX. 

## <a name="product-distribution"></a>Distribuição de Produtos

Pode obter a aplicação GUIX Studio a partir da [Microsoft App Store,](https://microsoft.com/store/apps) procurando o GUIX Studio, ou indo diretamente para [a página do ESTÚDIO GUIX](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab). Então faça o seguinte.

1. A partir da página do ESTÚDIO GUIX na App Store, clique no botão **Get** ou **Install** para descarregar o GUIX Studio.

1. O seu navegador pode apresentar uma mensagem a perguntar se pretende abrir a Microsoft Store, como mostra a figura abaixo. Se o fizer, escolha o botão **Abrir.**
![Escolha Abrir para instalar o GUIX Studio.](./media/guix-studio/open-ms-store.png)

1. Quando a instalação terminar, escolha o botão **Iniciar.**

1. A primeira vez que o GUIX Studio é lançado, exibe uma caixa de diálogo perguntando se deseja clonar o repo GUIX para o seu computador local. Pode optar por clonar o repositório, indicar onde já clonou o repo, ou optar por não clonar o repo (nesse caso, um projeto de exemplo está instalado no seu computador).
![Opte por clonar o repo, apontar para um repo já clonado, ou saltar.](./media/guix-studio/clone-repo.png)

> ![!NOTE]
> Pode voltar a esta caixa de diálogo a qualquer momento, escolhendo o **Configure** do menu principal do GUIX Stuido, seguido do **Repositório GUIX.**

Depois de terminado o processo de arranque, estará pronto para utilizar o GUIX Studio.

## <a name="using-guix-studio"></a>Usando o ESTÚDIO GUIX

A utilização do GUIX Studio é fácil - basta executar o ESTÚDIO GUIX através do botão "***Iniciar***". Neste momento, observará o GUIX Studio UI. Está agora pronto a usar o GUIX Studio para criar graficamente a sua UI incorporada. A partir daqui cria-se um novo projeto ou abre um projeto existente, incluindo os projetos de exemplo GUIX.

> [!NOTE]
> Também pode clicar duas vezes em qualquer ficheiro de projeto guix Studio com uma extensão de "**gxp**", que lançará automaticamente o GUIX Studio e abrirá o projeto referenciado.

## <a name="guix-studio-project-samples"></a>Amostras de projetos do estúdio GUIX

Uma série de ficheiros de projeto guix Studio com a extensão "***gxp"**_encontram-se no_ * sub-diretório "_Samples_**" da sua instalação. Estes projetos de exemplo pré-construídos vão ajudá-lo a se sentir confortável com a utilização do GUIX Studio.

Um exemplo de ficheiro de projeto que está sempre presente é o ficheiro ***samples/demo_guix_simple/guix_simple.gxp** _. Este ficheiro de projeto exemplo mostra a definição de um simples UI GUIX, conforme descrito em _ *_Capítulo 7_** deste documento.

![Screenshot do GUIX Studio UI.](./media/guix-studio/image_10.png)

**Figura 1**

## <a name="keyboard-shortcuts"></a>Keyboard Shortcuts

- **Ctrl + N:** Novo Projeto
- **Ctrl + O:** Projeto Aberto
- **CTRL + S:** Projeto Salvar
- **CTRL + Shift + S:** Salvar projeto como
- **Alt + F4:** Saída
