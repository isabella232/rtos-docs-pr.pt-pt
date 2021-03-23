---
title: Guia de utilizadores da pilha de dispositivos USBX Azure RTOS
description: Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825429"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="825ad-103">Guia de utilizadores da pilha de dispositivos USBX Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="825ad-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="825ad-104">Este guia fornece informações completas sobre o Azure RTOS USBX, o software de fundação USB de alto desempenho da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="825ad-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="825ad-105">Destina-se ao desenvolvedor de software incorporado em tempo real.</span><span class="sxs-lookup"><span data-stu-id="825ad-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="825ad-106">O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real, a especificação USB e a linguagem de programação C.</span><span class="sxs-lookup"><span data-stu-id="825ad-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="825ad-107">Para obter informações técnicas relacionadas com USB, consulte a especificação USB e as especificações da classe USB que podem ser descarregadas em https://www.USB.org/developers</span><span class="sxs-lookup"><span data-stu-id="825ad-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="825ad-108">Organização</span><span class="sxs-lookup"><span data-stu-id="825ad-108">Organization</span></span>

- <span data-ttu-id="825ad-109">[**Capítulo 1**](usbx-device-stack-1.md) - contém uma introdução ao Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="825ad-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="825ad-110">[**Capítulo 2**](usbx-device-stack-2.md) - dá os passos básicos para instalar e utilizar o Azure RTOS USBX com a sua aplicação ThreadX</span><span class="sxs-lookup"><span data-stu-id="825ad-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="825ad-111">[**Capítulo 3**](usbx-device-stack-3.md) - descreve os componentes funcionais da pilha de dispositivos Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="825ad-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="825ad-112">[**Capítulo 4**](usbx-device-stack-4.md) - descreve os serviços de stack de dispositivos Azure RTOS USBX</span><span class="sxs-lookup"><span data-stu-id="825ad-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="825ad-113">[**Capítulo 5**](usbx-device-stack-5.md) - descreve cada classe de dispositivoS Azure RTOS USBX, incluindo as suas APIs</span><span class="sxs-lookup"><span data-stu-id="825ad-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="825ad-114">Centro de Apoio ao Cliente</span><span class="sxs-lookup"><span data-stu-id="825ad-114">Customer Support Center</span></span>

<span data-ttu-id="825ad-115">Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui.</span><span class="sxs-lookup"><span data-stu-id="825ad-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="825ad-116">Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:</span><span class="sxs-lookup"><span data-stu-id="825ad-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="825ad-117">Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.</span><span class="sxs-lookup"><span data-stu-id="825ad-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="825ad-118">Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.</span><span class="sxs-lookup"><span data-stu-id="825ad-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="825ad-119">O conteúdo da cadeia **_tx_version_id** encontrado no ficheiro **_tx_port.h_** da sua distribuição.</span><span class="sxs-lookup"><span data-stu-id="825ad-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="825ad-120">Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="825ad-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="825ad-121">O conteúdo em RAM da *_tx_build_options* variável **ULONG.**</span><span class="sxs-lookup"><span data-stu-id="825ad-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="825ad-122">Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.</span><span class="sxs-lookup"><span data-stu-id="825ad-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
