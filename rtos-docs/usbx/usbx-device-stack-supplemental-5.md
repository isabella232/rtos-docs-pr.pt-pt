---
title: Capítulo 5 - USBX OTG
description: Saiba como o USBX suporta as funcionalidades OTG do USB quando um controlador USB compatível com OTG estiver disponível no design de hardware.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 64a3c44f84b9ffca31d9e616d14d3d5d87c56bd7
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550325"
---
# <a name="chapter-5---usbx-otg"></a><span data-ttu-id="5699e-103">Capítulo 5 - USBX OTG</span><span class="sxs-lookup"><span data-stu-id="5699e-103">Chapter 5 - USBX OTG</span></span>

<span data-ttu-id="5699e-104">O USBX suporta as funcionalidades OTG de USB quando um controlador USB compatível com OTG está disponível no design de hardware.</span><span class="sxs-lookup"><span data-stu-id="5699e-104">USBX supports the OTG functionalities of USB when an OTG compliant USB controller is available in the hardware design.</span></span>

<span data-ttu-id="5699e-105">USBX suporta OTG na pilha USB do núcleo.</span><span class="sxs-lookup"><span data-stu-id="5699e-105">USBX supports OTG in the core USB stack.</span></span> <span data-ttu-id="5699e-106">Mas para que o OTG funcione, requer um controlador USB específico.</span><span class="sxs-lookup"><span data-stu-id="5699e-106">But for OTG to function, it requires a specific USB controller.</span></span> <span data-ttu-id="5699e-107">As funções do controlador USBX OTG podem ser encontradas no diretório usbx_otg.</span><span class="sxs-lookup"><span data-stu-id="5699e-107">USBX OTG controller functions can be found in the usbx_otg directory.</span></span> <span data-ttu-id="5699e-108">A versão USBX atual suporta apenas o NXP LPC3131 com todas as capacidades OTG.</span><span class="sxs-lookup"><span data-stu-id="5699e-108">The current USBX version only supports the NXP LPC3131 with full OTG capabilities.</span></span>

<span data-ttu-id="5699e-109">As funções regulares do controlador do controlador (anfitrião ou dispositivo) ainda podem ser encontradas na usbx_device_controllers USBX padrão e usbx_host_controllers mas o diretório usbx_otg contém as funções OTG específicas associadas ao controlador USB.</span><span class="sxs-lookup"><span data-stu-id="5699e-109">The regular controller driver functions (host or device) can still be found in the standard USBX usbx_device_controllers and usbx_host_controllers but the usbx_otg directory contains the specific OTG functions associated with the USB controller.</span></span>

<span data-ttu-id="5699e-110">Existem quatro categorias de funções para um controlador OTG, além das funções habituais de hospedeiro/dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5699e-110">There are four categories of functions for an OTG controller in addition to the usual host/device functions.</span></span>

- <span data-ttu-id="5699e-111">Funções específicas do VBUS</span><span class="sxs-lookup"><span data-stu-id="5699e-111">VBUS specific functions</span></span>
- <span data-ttu-id="5699e-112">Início e paragem do controlador</span><span class="sxs-lookup"><span data-stu-id="5699e-112">Start and Stop of the controller</span></span>
- <span data-ttu-id="5699e-113">Gestor de funções USB</span><span class="sxs-lookup"><span data-stu-id="5699e-113">USB role manager</span></span>
- <span data-ttu-id="5699e-114">Interromper manipuladores</span><span class="sxs-lookup"><span data-stu-id="5699e-114">Interrupt handlers</span></span>

## <a name="vbus-functions"></a><span data-ttu-id="5699e-115">Funções VBUS</span><span class="sxs-lookup"><span data-stu-id="5699e-115">VBUS functions</span></span>

<span data-ttu-id="5699e-116">Cada controlador precisa de ter um gestor VBUS para alterar o estado da VBUS com base nos requisitos de gestão de energia.</span><span class="sxs-lookup"><span data-stu-id="5699e-116">Each controller needs to have a VBUS manager to change the state of VBUS based on power management requirements.</span></span> <span data-ttu-id="5699e-117">Normalmente, esta função só funciona ligando ou desligando O VBUS.</span><span class="sxs-lookup"><span data-stu-id="5699e-117">Usually, this function only performs turning on or off VBUS.</span></span>

## <a name="start-and-stop-the-controller"></a><span data-ttu-id="5699e-118">Iniciar e parar o controlador</span><span class="sxs-lookup"><span data-stu-id="5699e-118">Start and Stop the controller</span></span>

<span data-ttu-id="5699e-119">Ao contrário de uma implementação USB regular, o OTG requer que o hospedeiro e/ou a pilha do dispositivo sejam ativados e desativados quando a função muda.</span><span class="sxs-lookup"><span data-stu-id="5699e-119">Unlike a regular USB implementation, OTG requires the host and/or the device stack to be activated and deactivated when the role changes.</span></span>

## <a name="usb-role-manager"></a><span data-ttu-id="5699e-120">Gestor de funções USB</span><span class="sxs-lookup"><span data-stu-id="5699e-120">USB role Manager</span></span>

<span data-ttu-id="5699e-121">O gestor de funções USB recebe comandos para alterar o estado do USB.</span><span class="sxs-lookup"><span data-stu-id="5699e-121">The USB role manager receives commands to change the state of the USB.</span></span> <span data-ttu-id="5699e-122">Há vários Estados que precisam de transições de e para:</span><span class="sxs-lookup"><span data-stu-id="5699e-122">There are several states that need transitions to and from:</span></span>

| <span data-ttu-id="5699e-123">Estado</span><span class="sxs-lookup"><span data-stu-id="5699e-123">State</span></span>                    | <span data-ttu-id="5699e-124">Valor</span><span class="sxs-lookup"><span data-stu-id="5699e-124">Value</span></span> | <span data-ttu-id="5699e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="5699e-125">Description</span></span>                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| <span data-ttu-id="5699e-126">UX_OTG_IDLE</span><span class="sxs-lookup"><span data-stu-id="5699e-126">UX_OTG_IDLE</span></span>            | <span data-ttu-id="5699e-127">0</span><span class="sxs-lookup"><span data-stu-id="5699e-127">0</span></span>     | <span data-ttu-id="5699e-128">O dispositivo está inativo.</span><span class="sxs-lookup"><span data-stu-id="5699e-128">The device is Idle.</span></span> <span data-ttu-id="5699e-129">Não está ligado a nada.</span><span class="sxs-lookup"><span data-stu-id="5699e-129">Not connected to anything</span></span> |
| <span data-ttu-id="5699e-130">UX_OTG_IDLE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="5699e-130">UX_OTG_IDLE_TO_HOST</span></span>  | <span data-ttu-id="5699e-131">1</span><span class="sxs-lookup"><span data-stu-id="5699e-131">1</span></span>     | <span data-ttu-id="5699e-132">O dispositivo está ligado ao conector do tipo A</span><span class="sxs-lookup"><span data-stu-id="5699e-132">Device is connected with type A connector</span></span>             |
| <span data-ttu-id="5699e-133">UX_OTG_IDLE_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="5699e-133">UX_OTG_IDLE_TO_SLAVE</span></span> | <span data-ttu-id="5699e-134">2</span><span class="sxs-lookup"><span data-stu-id="5699e-134">2</span></span>     | <span data-ttu-id="5699e-135">O dispositivo está ligado ao conector do tipo B</span><span class="sxs-lookup"><span data-stu-id="5699e-135">Device is connected with type B connector</span></span>             |
| <span data-ttu-id="5699e-136">UX_OTG_HOST_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="5699e-136">UX_OTG_HOST_TO_IDLE</span></span>  | <span data-ttu-id="5699e-137">3</span><span class="sxs-lookup"><span data-stu-id="5699e-137">3</span></span>     | <span data-ttu-id="5699e-138">Dispositivo de anfitrião foi desligado</span><span class="sxs-lookup"><span data-stu-id="5699e-138">Host device got disconnected</span></span>                          |
| <span data-ttu-id="5699e-139">UX_OTG_HOST_TO_SLAVE</span><span class="sxs-lookup"><span data-stu-id="5699e-139">UX_OTG_HOST_TO_SLAVE</span></span> | <span data-ttu-id="5699e-140">4</span><span class="sxs-lookup"><span data-stu-id="5699e-140">4</span></span>     | <span data-ttu-id="5699e-141">Troca de papéis de Hospedeiro para Escravo</span><span class="sxs-lookup"><span data-stu-id="5699e-141">Role swap from Host to Slave</span></span>                          |
| <span data-ttu-id="5699e-142">UX_OTG_SLAVE_TO_IDLE</span><span class="sxs-lookup"><span data-stu-id="5699e-142">UX_OTG_SLAVE_TO_IDLE</span></span> | <span data-ttu-id="5699e-143">5</span><span class="sxs-lookup"><span data-stu-id="5699e-143">5</span></span>     | <span data-ttu-id="5699e-144">O dispositivo escravo está desligado</span><span class="sxs-lookup"><span data-stu-id="5699e-144">Slave device is disconnected</span></span>                          |
| <span data-ttu-id="5699e-145">UX_OTG_SLAVE_TO_HOST</span><span class="sxs-lookup"><span data-stu-id="5699e-145">UX_OTG_SLAVE_TO_HOST</span></span> | <span data-ttu-id="5699e-146">6</span><span class="sxs-lookup"><span data-stu-id="5699e-146">6</span></span>     | <span data-ttu-id="5699e-147">Troca de papéis de Slave para Host</span><span class="sxs-lookup"><span data-stu-id="5699e-147">Role swap from Slave to Host</span></span>                          |

## <a name="interrupt-handlers"></a><span data-ttu-id="5699e-148">Interromper manipuladores</span><span class="sxs-lookup"><span data-stu-id="5699e-148">Interrupt handlers</span></span>

<span data-ttu-id="5699e-149">Tanto os controladores de hospedeiro como os controladores de dispositivos para o OTG precisam de diferentes manipuladores de interrupção para monitorizar os sinais para além das tradicionais interrupções USB, em particular os sinais devido ao SRP e vbus.</span><span class="sxs-lookup"><span data-stu-id="5699e-149">Both host and device controller drivers for OTG needs different interrupt handlers to monitor signals beyond traditional USB interrupts, in particular signals due to SRP and VBUS.</span></span>

<span data-ttu-id="5699e-150">Como inicializar um controlador USB OTG.</span><span class="sxs-lookup"><span data-stu-id="5699e-150">How to initialize a USB OTG controller.</span></span> <span data-ttu-id="5699e-151">Utilizamos o NXP LPC3131 como exemplo aqui.</span><span class="sxs-lookup"><span data-stu-id="5699e-151">We use the NXP LPC3131 as an example here.</span></span>

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

<span data-ttu-id="5699e-152">Neste exemplo, inicializamos o LPC3131 no modo OTG, passando uma função VBUS e uma chamada de mudança de modo (de hospedeiro a escravo ou vice-versa).</span><span class="sxs-lookup"><span data-stu-id="5699e-152">In this example, we initialize the LPC3131 in OTG mode by passing a VBUS function and a callback for mode change (from host to slave or vice versa).</span></span>

<span data-ttu-id="5699e-153">A função de retorno deve simplesmente gravar o novo modo e acordar um fio pendente para agir o estado novo.</span><span class="sxs-lookup"><span data-stu-id="5699e-153">The callback function should simply record the new mode and wake up a pending thread to act up the new state.</span></span>

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

<span data-ttu-id="5699e-154">O valor do modo que é passado pode ter os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="5699e-154">The mode value that is passed can have the following values.</span></span>

- <span data-ttu-id="5699e-155">**UX_OTG_MODE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="5699e-155">**UX_OTG_MODE_IDLE**</span></span>
- <span data-ttu-id="5699e-156">**UX_OTG_MODE_SLAVE**</span><span class="sxs-lookup"><span data-stu-id="5699e-156">**UX_OTG_MODE_SLAVE**</span></span>
- <span data-ttu-id="5699e-157">**UX_OTG_MODE_HOST**</span><span class="sxs-lookup"><span data-stu-id="5699e-157">**UX_OTG_MODE_HOST**</span></span>

<span data-ttu-id="5699e-158">A aplicação pode sempre verificar o que é o dispositivo olhando para a variável:</span><span class="sxs-lookup"><span data-stu-id="5699e-158">The application can always check what the device is by looking at the variable:</span></span>

```C
_ux_system_otg -> ux_system_otg_device_type
```

<span data-ttu-id="5699e-159">Os seus valores podem ser qualquer um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="5699e-159">Its values can be any of the following.</span></span>

- <span data-ttu-id="5699e-160">**UX_OTG_DEVICE_A**</span><span class="sxs-lookup"><span data-stu-id="5699e-160">**UX_OTG_DEVICE_A**</span></span>
- <span data-ttu-id="5699e-161">**UX_OTG_DEVICE_B**</span><span class="sxs-lookup"><span data-stu-id="5699e-161">**UX_OTG_DEVICE_B**</span></span>
- <span data-ttu-id="5699e-162">**UX_OTG_DEVICE_IDLE**</span><span class="sxs-lookup"><span data-stu-id="5699e-162">**UX_OTG_DEVICE_IDLE**</span></span>

<span data-ttu-id="5699e-163">Um dispositivo de anfitrião USB OTG pode sempre pedir uma troca de funções emitindo o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="5699e-163">A USB OTG host device can always ask for a role swap by issuing the following command.</span></span>

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

<span data-ttu-id="5699e-164">Para um dispositivo escravo, não há nenhuma ordem a emitir, mas o dispositivo escravo pode definir um estado para mudar o papel, que será recolhido pelo hospedeiro quando emitir um **GET_STATUS** e a troca será iniciada.</span><span class="sxs-lookup"><span data-stu-id="5699e-164">For a slave device, there is no command to issue but the slave device can set a state to change the role, which will be picked up by the host when it issues a **GET_STATUS** and the swap will then be initiated.</span></span>

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
