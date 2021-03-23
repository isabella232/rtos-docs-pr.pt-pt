---
title: Capítulo 2 - Instalação e utilização do Azure RTOS TraceX
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de análise do sistema Azure RTOS TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827572"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a>Capítulo 2 - Instalação e utilização do Azure RTOS TraceX

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da ferramenta de análise do sistema Azure RTOS TraceX. 

## <a name="product-distribution"></a>Distribuição de Produtos

Pode obter a aplicação TraceX a partir da [Microsoft App Store,](https://microsoft.com/store/apps) procurando por TraceX, ou indo diretamente para [a página TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab). Então faça o seguinte.

1. A partir da página TraceX na App Store, clique no botão **Get** ou **Install** para instalar o TraceX.

1. O seu navegador pode apresentar uma mensagem a perguntar se pretende abrir a Microsoft Store, como mostra a figura abaixo. Se o fizer, escolha o botão **Abrir.**
![Escolha Abrir para instalar o TraceX.](../guix/media/guix-studio/open-ms-store.png)

1. Quando a instalação terminar, escolha o botão **Iniciar.** 

## <a name="using-tracex"></a>Usando tracex

A utilização do TraceX é tão fácil como abrir um ficheiro de traços dentro do TraceX! Executar TraceX através do botão ***Iniciar** _ . Neste ponto observará a interface gráfica do utilizador TraceX (GUI). Está agora pronto a usar o TraceX para visualizar graficamente um tampão de traço de alvo existente. Isto é facilmente feito clicando _ *_File -> Open,_* em seguida, insira o ficheiro de traço binário.

>[!IMPORTANT]
>*Também pode clicar duas vezes em qualquer ficheiro de traço com uma extensão de **trx,** que lançará automaticamente o TraceX.*

![Screenshot do TraceX GUI.](./media/user-guide/screen_shot_8.png)

**FIGURA 1**

>[!IMPORTANT]
>*Consulte o **Capítulo 5** para obter instruções sobre como gerar tampões de vestígios no alvo utilizando o ThreadX.*

## <a name="tracex-examples"></a>Exemplos TraceX

A primeira vez que executar a aplicação TraceX, ou quando a aplicação TraceX for atualizada, será solicitado que instale os ficheiros de traços de exemplo TraceX e o ficheiro custom_events.trxc para um diretório definido pelo utilizador na sua máquina local.

Após esta instalação ter sido concluída, os ficheiros de traços de exemplo com o **trx** de extensão encontram-se no subdiretório **TraceFiles** da sua pasta de instalação. Estes exemplos pré-construídos vão ajudá-lo a sentir-se confortável com a utilização do TraceX nos tampões de traço gerados pela ThreadX em execução com a sua aplicação.

Um ficheiro de traço de exemplo sempre presente é o ficheiro ***demo_threadx.trx** _. Este ficheiro de traços de exemplo mostra a execução da demonstração padrão da ThreadX, tal como descrito no Capítulo 6 do _ThreadX Manual do Utilizador*.

![Screenshot do diálogo aberto em TraceX.](./media/user-guide/screen_shot_9.png)

**FIGURA 2**
