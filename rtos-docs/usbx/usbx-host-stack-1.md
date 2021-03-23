---
title: Capítulo 1 - Introdução à Pilha de Anfitriões USBX Azure RTOS
description: USBX é uma pilha USB completa para aplicações profundamente incorporadas. Este capítulo introduz USBX, descrevendo as suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ee49903e764e20316438be16b47d2d9208b1363
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828544"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="82fba-104">Capítulo 1 - Introdução à Pilha de Anfitriões USBX Azure RTOS</span><span class="sxs-lookup"><span data-stu-id="82fba-104">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="82fba-105">USBX é uma pilha USB completa para aplicações profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="82fba-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="82fba-106">Este capítulo introduz USBX, descrevendo as suas aplicações e benefícios.</span><span class="sxs-lookup"><span data-stu-id="82fba-106">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="82fba-107">Recursos USBX</span><span class="sxs-lookup"><span data-stu-id="82fba-107">USBX features</span></span>

<span data-ttu-id="82fba-108">USBX suporta as três especificações USB existentes: 1.1, 2.0 e OTG.</span><span class="sxs-lookup"><span data-stu-id="82fba-108">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="82fba-109">Foi projetado para ser escalável e irá acomodar as simples topologias USB com apenas um dispositivo conectado, bem como topologias complexas com múltiplos dispositivos e centros em cascata.</span><span class="sxs-lookup"><span data-stu-id="82fba-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="82fba-110">O USBX suporta todos os tipos de transferência de dados dos protocolos USB: controlo, granel, interrupção e isocronous.</span><span class="sxs-lookup"><span data-stu-id="82fba-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="82fba-111">O USBX suporta tanto o lado do anfitrião como o lado do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="82fba-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="82fba-112">Cada lado é composto por três camadas.</span><span class="sxs-lookup"><span data-stu-id="82fba-112">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="82fba-113">Camada do controlador</span><span class="sxs-lookup"><span data-stu-id="82fba-113">Controller layer</span></span>
- <span data-ttu-id="82fba-114">Camada de pilha</span><span class="sxs-lookup"><span data-stu-id="82fba-114">Stack layer</span></span>
- <span data-ttu-id="82fba-115">Camada de classe</span><span class="sxs-lookup"><span data-stu-id="82fba-115">Class layer</span></span>

<span data-ttu-id="82fba-116">A relação entre as camadas USB é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="82fba-116">The relationship between the USB layers is as follows.</span></span>

![Camadas USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="82fba-118">Destaques do produto</span><span class="sxs-lookup"><span data-stu-id="82fba-118">Product Highlights</span></span>

- <span data-ttu-id="82fba-119">Suporte completo do processador ThreadX</span><span class="sxs-lookup"><span data-stu-id="82fba-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="82fba-120">Sem royalties</span><span class="sxs-lookup"><span data-stu-id="82fba-120">No royalties</span></span>
- <span data-ttu-id="82fba-121">Complete o código fonte ANSI C</span><span class="sxs-lookup"><span data-stu-id="82fba-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="82fba-122">Desempenho em tempo real</span><span class="sxs-lookup"><span data-stu-id="82fba-122">Real-time performance</span></span>
- <span data-ttu-id="82fba-123">Suporte técnico responsivo</span><span class="sxs-lookup"><span data-stu-id="82fba-123">Responsive technical support</span></span>
- <span data-ttu-id="82fba-124">Suporte de controlador de vários anfitriões</span><span class="sxs-lookup"><span data-stu-id="82fba-124">Multiple host controller support</span></span>
- <span data-ttu-id="82fba-125">Suporte de classe múltipla</span><span class="sxs-lookup"><span data-stu-id="82fba-125">Multiple class support</span></span>
- <span data-ttu-id="82fba-126">Múltiplas instâncias de classe</span><span class="sxs-lookup"><span data-stu-id="82fba-126">Multiple class instances</span></span>
- <span data-ttu-id="82fba-127">Integração de classes com ThreadX, FileX e NetX</span><span class="sxs-lookup"><span data-stu-id="82fba-127">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="82fba-128">Suporte para dispositivos USB com múltiplas configurações</span><span class="sxs-lookup"><span data-stu-id="82fba-128">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="82fba-129">Suporte para dispositivos compostos USB</span><span class="sxs-lookup"><span data-stu-id="82fba-129">Support for USB composite devices</span></span>
- <span data-ttu-id="82fba-130">Apoio aos centros em cascata</span><span class="sxs-lookup"><span data-stu-id="82fba-130">Support for cascading hubs</span></span>
- <span data-ttu-id="82fba-131">Suporte para gestão de energia USB</span><span class="sxs-lookup"><span data-stu-id="82fba-131">Support for USB power management</span></span>
- <span data-ttu-id="82fba-132">Suporte para OTG USB</span><span class="sxs-lookup"><span data-stu-id="82fba-132">Support for USB OTG</span></span>
- <span data-ttu-id="82fba-133">Eventos de rastreio de exportação para TraceX</span><span class="sxs-lookup"><span data-stu-id="82fba-133">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="82fba-134">Serviços Poderosos da USBX</span><span class="sxs-lookup"><span data-stu-id="82fba-134">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="82fba-135">Suporte ao controlador de vários anfitriões</span><span class="sxs-lookup"><span data-stu-id="82fba-135">Multiple Host Controller Support</span></span>

<span data-ttu-id="82fba-136">USBX pode suportar vários controladores de anfitriões USB em execução em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="82fba-136">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="82fba-137">Esta funcionalidade permite que o USBX suporte a norma USB 2.0 utilizando o esquema de retrocompatibilidade associado à maioria dos controladores anfitriões USB 2.0 no mercado.</span><span class="sxs-lookup"><span data-stu-id="82fba-137">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="82fba-138">Programador de software USB</span><span class="sxs-lookup"><span data-stu-id="82fba-138">USB Software Scheduler</span></span>

<span data-ttu-id="82fba-139">USBX contém um programador de software USB necessário para suportar controladores USB que não têm processamento de lista de hardware.</span><span class="sxs-lookup"><span data-stu-id="82fba-139">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="82fba-140">O programador de software USBX organizará transferências USB com a frequência correta de serviço e prioridade, e instruirá o controlador USB a executar cada transferência.</span><span class="sxs-lookup"><span data-stu-id="82fba-140">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="82fba-141">Suporte completo do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="82fba-141">Complete USB Device Framework Support</span></span>

<span data-ttu-id="82fba-142">O USBX pode suportar os dispositivos USB mais exigentes, incluindo múltiplas configurações, múltiplas interfaces e múltiplas configurações alternativas.</span><span class="sxs-lookup"><span data-stu-id="82fba-142">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="82fba-143">APIs fáceis de usar</span><span class="sxs-lookup"><span data-stu-id="82fba-143">Easy-To-Use APIs</span></span>

<span data-ttu-id="82fba-144">A USBX fornece a melhor pilha USB profundamente incorporada de uma forma que é fácil de entender e usar.</span><span class="sxs-lookup"><span data-stu-id="82fba-144">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="82fba-145">A API USBX torna os serviços intuitivos e consistentes.</span><span class="sxs-lookup"><span data-stu-id="82fba-145">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="82fba-146">Ao utilizar as APIs de classe USBX fornecidas, a aplicação do utilizador não precisa de compreender a complexidade dos protocolos USB.</span><span class="sxs-lookup"><span data-stu-id="82fba-146">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
