---
title: Guia de utilizadores do anfitrião Azure RTOS USBX
description: Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827331"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a><span data-ttu-id="3eeb7-103">Guia de utilizadores do anfitrião Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="3eeb7-103">Azure RTOS USBX Host Stack User Guide</span></span>

<span data-ttu-id="3eeb7-104">Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-104">This guide provides comprehensive information about Azure RTOS USBX, the high-performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="3eeb7-105">Destina-se ao desenvolvedor de software incorporado em tempo real.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="3eeb7-106">O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real, a especificação USB e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="3eeb7-107">Para obter informações técnicas relacionadas com USB, consulte a especificação USB e as especificações da classe USB que podem ser descarregadas em [https://www.USB.org/developers](https://www.USB.org/developers)</span><span class="sxs-lookup"><span data-stu-id="3eeb7-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at [https://www.USB.org/developers](https://www.USB.org/developers)</span></span>

## <a name="organization"></a><span data-ttu-id="3eeb7-108">Organização</span><span class="sxs-lookup"><span data-stu-id="3eeb7-108">Organization</span></span>

- <span data-ttu-id="3eeb7-109">[**Capítulo 1**](usbx-host-stack-1.md) - contém uma introdução ao Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="3eeb7-109">[**Chapter 1**](usbx-host-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="3eeb7-110">[**Capítulo 2**](usbx-host-stack-2.md) - dá os passos básicos para instalar e utilizar o Azure RTOS USBX com a sua aplicação Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="3eeb7-110">[**Chapter 2**](usbx-host-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your Azure RTOS ThreadX application</span></span>

- <span data-ttu-id="3eeb7-111">[**Capítulo 3**](usbx-host-stack-3.md) - fornece uma visão geral funcional do Azure RTOS USBX e informações básicas sobre USB</span><span class="sxs-lookup"><span data-stu-id="3eeb7-111">[**Chapter 3**](usbx-host-stack-3.md) - provides a functional overview of Azure RTOS USBX and basic information about USB</span></span>

- <span data-ttu-id="3eeb7-112">[**Capítulo 4**](usbx-host-stack-4.md) - detalha a interface da aplicação com o Azure RTOS USBX no modo de anfitrião</span><span class="sxs-lookup"><span data-stu-id="3eeb7-112">[**Chapter 4**](usbx-host-stack-4.md) - details the application's interface to Azure RTOS USBX in host mode</span></span>

- <span data-ttu-id="3eeb7-113">[**Capítulo 5**](usbx-host-stack-5.md) - descreve as APIs das classes Azure RTOS USBX Host</span><span class="sxs-lookup"><span data-stu-id="3eeb7-113">[**Chapter 5**](usbx-host-stack-5.md) - describes the APIs of the Azure RTOS USBX Host classes</span></span>

- <span data-ttu-id="3eeb7-114">[**Capítulo 6**](usbx-host-stack-6.md) - descreve a classe Azure RTOS USBX CDC-ECM</span><span class="sxs-lookup"><span data-stu-id="3eeb7-114">[**Chapter 6**](usbx-host-stack-6.md) - describes the Azure RTOS USBX CDC-ECM class</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="3eeb7-115">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="3eeb7-115">Customer Support Center</span></span>

<span data-ttu-id="3eeb7-116">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-116">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="3eeb7-117">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-117">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="3eeb7-118">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-118">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="3eeb7-119">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-119">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="3eeb7-120">O conteúdo da cadeia *_tx_version_id* encontrado no ficheiro *tx_port.h* da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-120">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="3eeb7-121">Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-121">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="3eeb7-122">O conteúdo em RAM da *_tx_build_options* variável ULONG.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-122">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="3eeb7-123">Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.</span><span class="sxs-lookup"><span data-stu-id="3eeb7-123">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
