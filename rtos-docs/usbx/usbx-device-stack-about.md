---
title: Guia de utilizadores da pilha de dispositivos USBX Azure RTOS
description: Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 042398377766a3e73f72d4dbba0478ba707d378a379fd33de7808675eb96f257
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788767"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a>Guia de utilizadores da pilha de dispositivos USBX Azure RTOS

Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft.

Destina-se ao desenvolvedor de software incorporado em tempo real. O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real, a especificação USB e a linguagem de programação C.

Para obter informações técnicas relacionadas com USB, consulte a especificação USB e as especificações da classe USB que podem ser descarregadas em https://www.USB.org/developers

## <a name="organization"></a>Organização

- [**Capítulo 1**](usbx-device-stack-1.md) - contém uma introdução ao Azure RTOS USBX

- [**Capítulo 2**](usbx-device-stack-2.md) - dá os passos básicos para instalar e utilizar o Azure RTOS USBX com a sua aplicação ThreadX

- [**Capítulo 3**](usbx-device-stack-3.md) - descreve os componentes funcionais da pilha de dispositivos Azure RTOS USBX

- [**Capítulo 4**](usbx-device-stack-4.md) - descreve os serviços de stack de dispositivos Azure RTOS USBX

- [**Capítulo 5**](usbx-device-stack-5.md) - descreve cada classe de dispositivoS Azure RTOS USBX, incluindo as suas APIs

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.
3. O conteúdo da cadeia **_tx_version_id** encontrado no ficheiro **_tx_port.h_** da sua distribuição. Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM da *_tx_build_options* variável **ULONG.** Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.
