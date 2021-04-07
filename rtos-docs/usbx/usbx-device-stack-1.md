---
title: Capítulo 1 - Introdução à Pilha de Dispositivos USBX Azure RTOS
description: USBX é uma pilha USB completa para aplicações profundamente incorporadas. Este capítulo introduz USBX, descrevendo os seus benefícios e aplicações.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8b1e08130d4531fd82629378761cd5b1752f0a07
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550291"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="99407-104">Capítulo 1 - Introdução à Pilha de Dispositivos USBX Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="99407-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="99407-105">USBX é uma pilha USB completa para aplicações profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="99407-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="99407-106">Este capítulo introduz USBX, descrevendo as suas aplicações e benefícios</span><span class="sxs-lookup"><span data-stu-id="99407-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="99407-107">Recursos USBX</span><span class="sxs-lookup"><span data-stu-id="99407-107">USBX features</span></span>

<span data-ttu-id="99407-108">A USBX suporta as três especificações USB existentes: 1.1, 2.0 e OTG.</span><span class="sxs-lookup"><span data-stu-id="99407-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="99407-109">Foi projetado para ser escalável e irá acomodar as simples topologias USB com apenas um dispositivo conectado, bem como topologias complexas com múltiplos dispositivos e centros em cascata.</span><span class="sxs-lookup"><span data-stu-id="99407-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="99407-110">O USBX suporta todos os tipos de transferência de dados dos protocolos USB: controlo, granel, interrupção e isocronous.</span><span class="sxs-lookup"><span data-stu-id="99407-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="99407-111">O USBX suporta tanto o lado do anfitrião como o lado do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99407-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="99407-112">Cada lado é composto por três camadas.</span><span class="sxs-lookup"><span data-stu-id="99407-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="99407-113">Camada do controlador</span><span class="sxs-lookup"><span data-stu-id="99407-113">Controller layer</span></span>
- <span data-ttu-id="99407-114">Camada de pilha</span><span class="sxs-lookup"><span data-stu-id="99407-114">Stack layer</span></span>
- <span data-ttu-id="99407-115">Camada de classe</span><span class="sxs-lookup"><span data-stu-id="99407-115">Class layer</span></span>

<span data-ttu-id="99407-116">A relação entre as camadas USB é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="99407-116">The relationship between the USB layers is as follows:</span></span>

![Camadas USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="99407-118">Destaques do produto</span><span class="sxs-lookup"><span data-stu-id="99407-118">Product Highlights</span></span>

- <span data-ttu-id="99407-119">Suporte completo do processador ThreadX</span><span class="sxs-lookup"><span data-stu-id="99407-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="99407-120">Sem royalties</span><span class="sxs-lookup"><span data-stu-id="99407-120">No royalties</span></span>
- <span data-ttu-id="99407-121">Complete o código fonte ANSI C</span><span class="sxs-lookup"><span data-stu-id="99407-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="99407-122">Desempenho em tempo real</span><span class="sxs-lookup"><span data-stu-id="99407-122">Real-time performance</span></span>
- <span data-ttu-id="99407-123">Suporte técnico responsivo</span><span class="sxs-lookup"><span data-stu-id="99407-123">Responsive technical support</span></span>
- <span data-ttu-id="99407-124">Suporte de classe múltipla</span><span class="sxs-lookup"><span data-stu-id="99407-124">Multiple class support</span></span>
- <span data-ttu-id="99407-125">Múltiplas instâncias de classe</span><span class="sxs-lookup"><span data-stu-id="99407-125">Multiple class instances</span></span>
- <span data-ttu-id="99407-126">Integração de classes com ThreadX, FileX e NetX</span><span class="sxs-lookup"><span data-stu-id="99407-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="99407-127">Suporte para dispositivos USB com múltiplas configurações</span><span class="sxs-lookup"><span data-stu-id="99407-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="99407-128">Suporte para dispositivos compostos USB</span><span class="sxs-lookup"><span data-stu-id="99407-128">Support for USB composite devices</span></span>
- <span data-ttu-id="99407-129">Suporte para gestão de energia USB</span><span class="sxs-lookup"><span data-stu-id="99407-129">Support for USB power management</span></span>
- <span data-ttu-id="99407-130">Suporte para OTG USB</span><span class="sxs-lookup"><span data-stu-id="99407-130">Support for USB OTG</span></span>
- <span data-ttu-id="99407-131">Eventos de rastreio de exportação para TraceX</span><span class="sxs-lookup"><span data-stu-id="99407-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="99407-132">Serviços Poderosos da USBX</span><span class="sxs-lookup"><span data-stu-id="99407-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="99407-133">Suporte completo do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="99407-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="99407-134">O USBX pode suportar os dispositivos USB mais exigentes, incluindo múltiplas configurações, múltiplas interfaces e múltiplas configurações alternativas.</span><span class="sxs-lookup"><span data-stu-id="99407-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="99407-135">APIs fáceis de usar</span><span class="sxs-lookup"><span data-stu-id="99407-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="99407-136">A USBX fornece a melhor pilha USB profundamente incorporada de uma forma que é fácil de entender e usar.</span><span class="sxs-lookup"><span data-stu-id="99407-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="99407-137">A API USBX torna os serviços intuitivos e consistentes.</span><span class="sxs-lookup"><span data-stu-id="99407-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="99407-138">Ao utilizar as APIs de classe USBX fornecidas, a aplicação do utilizador não precisa de compreender a complexidade dos protocolos USB.</span><span class="sxs-lookup"><span data-stu-id="99407-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
