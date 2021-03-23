---
title: Capítulo 2 - Considerações da classe do dispositivo USBX
description: A classe RNDIS do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo ethernet. Esta classe baseia-se na implementação proprietária da Microsoft e é específica para as plataformas do Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8104f00e192486f57fe9c22b2c83aa9a22954739
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828412"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="1c2a2-104">Capítulo 2 - Considerações da classe do dispositivo USBX</span><span class="sxs-lookup"><span data-stu-id="1c2a2-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="1c2a2-105">Classe RNDIS de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="1c2a2-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="1c2a2-106">A classe RNDIS do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo ethernet.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="1c2a2-107">Esta classe baseia-se na implementação proprietária da Microsoft e é específica para as plataformas do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="1c2a2-108">Uma estrutura do dispositivo compatível com RNDIS tem de ser declarada pela pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="1c2a2-109">Um exemplo é encontrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="1c2a2-110">A classe RNDIS usa uma abordagem de descritor de dispositivos muito semelhante ao CDC-ACM e CDC-ECM e também requer um descritor de IAD.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="1c2a2-111">Consulte a classe CDC-ACM para definição e requisitos para o descritor do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="1c2a2-112">A ativação da classe RNDIS é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="1c2a2-113">Quanto ao CDC-ECM, a classe RNDIS requer 2 nós, um local e um remoto, mas não há necessidade de ter um descritor de cordas descrevendo o nó remoto.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="1c2a2-114">No entanto, devido ao mecanismo de mensagens proprietárias da Microsoft, são necessários alguns parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="1c2a2-115">Primeiro, a identificação do vendedor tem de ser aprovada.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="1c2a2-116">Da mesma forma, a versão condutora do RNDIS.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="1c2a2-117">Um fio de vendedor também deve ser dado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-117">A vendor string must also be given.</span></span>

<span data-ttu-id="1c2a2-118">A classe RNDIS tem APIs incorporados para transferir dados em ambos os sentidos, mas estão escondidos na aplicação, uma vez que a aplicação do utilizador comunicará com o dispositivo USB Ethernet através do NetX.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="1c2a2-119">A classe USBX RNDIS está intimamente ligada à pilha de rede Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="1c2a2-120">Uma aplicação utilizando a classe NetX e USBX RNDIS irá ativar a pilha de rede NetX da forma habitual, mas além disso precisa de ativar a pilha de rede USB da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="1c2a2-121">A pilha de rede USB precisa de ser ativada apenas uma vez e não é específica para o RNDIS, mas é exigida por qualquer classe USB que exija serviços NetX.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="1c2a2-122">A classe RNDIS não será reconhecida pelos anfitriões MAC OS e Linux, uma vez que é específica dos sistemas operativos da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="1c2a2-123">Nas plataformas do Windows, um ficheiro .inf tem de estar presente no anfitrião que corresponda ao descritor do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="1c2a2-124">A Microsoft fornece um modelo para a classe RNDIS e pode ser encontrado no diretório usbx_windows_host_files.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="1c2a2-125">Para a versão mais recente do Windows, o ficheiro RNDIS_Template.inf deve ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="1c2a2-126">Este ficheiro precisa de ser modificado para refletir o PID/VID utilizado pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="1c2a2-127">O PID/VID será específico para o cliente final quando a empresa e o produto estiverem registados no USB-IF.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="1c2a2-128">No ficheiro inf, os campos a modificar estão localizados aqui.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="1c2a2-129">Na estrutura do dispositivo do dispositivo RNDIS, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado)</span><span class="sxs-lookup"><span data-stu-id="1c2a2-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="1c2a2-130">Quando um sistema de anfitrião USB descobre o dispositivo USB RNDIS, irá montar uma interface de rede e o dispositivo pode ser utilizado com a pilha de protocolo de rede.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="1c2a2-131">Consulte o Sistema Operativo do anfitrião para obter referência.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="1c2a2-132">Classe DFU de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="1c2a2-132">USB Device DFU Class</span></span>

<span data-ttu-id="1c2a2-133">A classe DFU do dispositivo USB permite que um sistema de anfitriões USB atualize o firmware do dispositivo com base numa aplicação de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="1c2a2-134">A classe DFU é uma classe padrão USB-IF.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="1c2a2-135">A classe USBX DFU é relativamente simples.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="1c2a2-136">O descritor do dispositivo não requer nada além de um ponto final de controlo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="1c2a2-137">Na maior parte das vezes, esta classe será incorporada num dispositivo composto USB.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="1c2a2-138">O dispositivo pode ser qualquer coisa como um dispositivo de armazenamento ou um dispositivo de comunicação e a interface DFU adicionada pode informar o anfitrião de que o dispositivo pode ter o seu firmware atualizado no voo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="1c2a2-139">A classe DFU funciona em 3 passos.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="1c2a2-140">Primeiro, o dispositivo monta normalmente utilizando a classe exportada.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="1c2a2-141">Uma aplicação no anfitrião (Windows ou Linux) exercerá a classe DFU e enviará um pedido para reiniciar o dispositivo no modo DFU.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="1c2a2-142">O dispositivo desaparecerá do autocarro por um curto período de tempo (o suficiente para o anfitrião e o dispositivo detetarem uma sequência RESET) e, ao reiniciar, o dispositivo estará exclusivamente no modo DFU, aguardando que a aplicação do anfitrião envie uma atualização de firmware.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="1c2a2-143">Quando a atualização do firmware estiver concluída, a aplicação do anfitrião reinicia o dispositivo e, após a reenunciação, o dispositivo voltará ao seu funcionamento normal com o novo firmware.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="1c2a2-144">Uma estrutura de dispositivo DFU será assim.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="1c2a2-145">Neste exemplo, o descritor DFU não está associado a nenhuma outra classe.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="1c2a2-146">Tem um descritor de interface simples e nenhum outro ponto final ligado a ele.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="1c2a2-147">Existe um descritor funcional que descreve as especificidades das capacidades dfu do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="1c2a2-148">A descrição das capacidades da DFU é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="1c2a2-149">Name</span><span class="sxs-lookup"><span data-stu-id="1c2a2-149">Name</span></span>             | <span data-ttu-id="1c2a2-150">Desvio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-150">Offset</span></span>  | <span data-ttu-id="1c2a2-151">Tamanho</span><span class="sxs-lookup"><span data-stu-id="1c2a2-151">Size</span></span> | <span data-ttu-id="1c2a2-152">tipo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-152">type</span></span>      | <span data-ttu-id="1c2a2-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="1c2a2-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="1c2a2-154">bmAttributes</span></span>  | <span data-ttu-id="1c2a2-155">2</span><span class="sxs-lookup"><span data-stu-id="1c2a2-155">2</span></span>     | <span data-ttu-id="1c2a2-156">1</span><span class="sxs-lookup"><span data-stu-id="1c2a2-156">1</span></span>   | <span data-ttu-id="1c2a2-157">Campo de bits</span><span class="sxs-lookup"><span data-stu-id="1c2a2-157">Bit field</span></span> | <span data-ttu-id="1c2a2-158">Bit 3: o dispositivo executará uma sequência de desprendimento de autocarros quando receber um pedido de DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="1c2a2-159">O anfitrião não deve emitir um Reset USB.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="1c2a2-160">(bitWillDetach) 0 = no 1 = sim Bit 2: o dispositivo é capaz de comunicar via USB após a fase de Manifestação.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="1c2a2-161">(bitManifestationTolerant) 0 = não, deve ver reset de autocarro 1 = sim Bit 1: upload capaz (bitCanUpload) 0 = no 1 = sim Bit 0: download capaz (bitCanDnload) 0 = no 1 = sim</span><span class="sxs-lookup"><span data-stu-id="1c2a2-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="1c2a2-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="1c2a2-162">wDetachTimeOut</span></span>  | <span data-ttu-id="1c2a2-163">3</span><span class="sxs-lookup"><span data-stu-id="1c2a2-163">3</span></span>      | <span data-ttu-id="1c2a2-164">2</span><span class="sxs-lookup"><span data-stu-id="1c2a2-164">2</span></span>  | <span data-ttu-id="1c2a2-165">número</span><span class="sxs-lookup"><span data-stu-id="1c2a2-165">number</span></span>    | <span data-ttu-id="1c2a2-166">Tempo, em milissegundos, que o dispositivo aguardará após a receção do pedido de DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="1c2a2-167">Se este tempo decorrer sem um reset USB, o dispositivo terminará a fase de reconfiguração e voltará ao funcionamento normal.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="1c2a2-168">Isto representa o tempo máximo que o dispositivo pode esperar (dependendo dos temporizadores, etc.).</span><span class="sxs-lookup"><span data-stu-id="1c2a2-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="1c2a2-169">USBX define este valor para 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="1c2a2-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="1c2a2-170">wTransferSize</span></span>  | <span data-ttu-id="1c2a2-171">5</span><span class="sxs-lookup"><span data-stu-id="1c2a2-171">5</span></span>      | <span data-ttu-id="1c2a2-172">2</span><span class="sxs-lookup"><span data-stu-id="1c2a2-172">2</span></span>  | <span data-ttu-id="1c2a2-173">número</span><span class="sxs-lookup"><span data-stu-id="1c2a2-173">number</span></span>    | <span data-ttu-id="1c2a2-174">Número máximo de bytes que o dispositivo pode aceitar por operação de escrita de \- controlo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="1c2a2-175">USBX define este valor para 64 bytes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="1c2a2-176">A declaração da classe DFU é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="1c2a2-177">A classe DFU precisa de trabalhar com uma aplicação de firmware de dispositivo específica para o alvo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="1c2a2-178">Por isso, define várias chamadas de volta para ler e escrever blocos de firmware e para obter o estado da aplicação de atualização de firmware.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="1c2a2-179">A classe DFU também tem uma função de notificação de retorno para informar a aplicação quando ocorrer um início e fim de transferência do firmware.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="1c2a2-180">Segue-se a descrição de um fluxo típico de aplicação DFU.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-180">Following is the description of a typical DFU application flow.</span></span>

![Fluxo de aplicação DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="1c2a2-182">O grande desafio da classe DFU é obter a aplicação certa no anfitrião para realizar o download do firmware.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="1c2a2-183">Não existe nenhuma aplicação fornecida pela Microsoft ou pelo USB-IF.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="1c2a2-184">Existem alguns shareware e funcionam razoavelmente bem no Linux e em menor medida no Windows.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="1c2a2-185">No Linux, pode-se usar du-utils para ser encontrado aqui: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) Muita informação sobre os usos dfu também pode ser encontrada neste link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="1c2a2-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="1c2a2-186">A implementação do Linux da DFU executa corretamente a sequência de reset entre o hospedeiro e o dispositivo e, portanto, o dispositivo não necessita de o fazer.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="1c2a2-187">Linux pode aceitar que os bmAttributes *bitWillDetach* sejam 0.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="1c2a2-188">As janelas do outro lado requerem que o dispositivo execute o reset.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="1c2a2-189">No Windows, o registo USB deve ser capaz de associar o dispositivo USB ao seu PID/VID e à biblioteca USB que, por sua vez, será utilizado pela aplicação DFU.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="1c2a2-190">Isto pode ser feito facilmente com a utilidade gratuita Zadig que pode ser encontrada aqui: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .</span><span class="sxs-lookup"><span data-stu-id="1c2a2-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="1c2a2-191">Running Zadig pela primeira vez mostrará este ecrã:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-191">Running Zadig for the first time will show this screen:</span></span>

![Correr Zadig pela primeira vez](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="1c2a2-193">A partir da lista de dispositivos, encontre o seu dispositivo e associe-o ao controlador de janelas libusb.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="1c2a2-194">Isto ligará o PID/VID do dispositivo à biblioteca USB do Windows utilizada pelos utilitários DFU.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="1c2a2-195">Para operar o comando DFU, basta desempacotar os utilitários dfu zipped em um diretório, certificando-se de que o libusb dll também está presente no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="1c2a2-196">Os utilitários DFU devem ser executados a partir de uma caixa DOS na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="1c2a2-197">Em primeiro lugar, digite o comando **dfu-util – l** para determinar se o dispositivo está listado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="1c2a2-198">Caso contrário, corra zadig para se certificar de que o dispositivo está listado e associado à biblioteca USB.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="1c2a2-199">Deve ver um ecrã da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="1c2a2-200">O próximo passo será preparar o ficheiro para ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="1c2a2-201">A classe USBX DFU não realiza qualquer verificação neste ficheiro e é agnóstica do seu formato interno.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="1c2a2-202">Este ficheiro de firmware é muito específico para o alvo, mas não para a DFU nem para a USBX.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="1c2a2-203">Em seguida, o dfu-util pode ser instruído para enviar o ficheiro digitando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="1c2a2-204">O dfu-util deve exibir o processo de descarregamento do ficheiro até que o firmware tenha sido completamente descarregado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="1c2a2-205">Classe PIMA do dispositivo USB (PTP Responder)</span><span class="sxs-lookup"><span data-stu-id="1c2a2-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="1c2a2-206">A classe PIMA do dispositivo USB permite que um sistema de anfitriões USB (Iniciador) se conecte a um</span><span class="sxs-lookup"><span data-stu-id="1c2a2-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="1c2a2-207">Dispositivo PIMA (Resonder) para transferir ficheiros de mídia.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="1c2a2-208">A Classe USBX Pima está em conformidade com a classe USB-IF PIMA 15740 também conhecida como classe PTP (para protocolo de transferência de imagens).</span><span class="sxs-lookup"><span data-stu-id="1c2a2-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="1c2a2-209">O lado do dispositivo USBX PIMA suporta as seguintes operações.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="1c2a2-210">Código de operação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-210">Operation code</span></span>                                    | <span data-ttu-id="1c2a2-211">Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-211">Value</span></span> | <span data-ttu-id="1c2a2-212">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="1c2a2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="1c2a2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="1c2a2-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="1c2a2-214">0x1001</span></span>  | <span data-ttu-id="1c2a2-215">Obtenha o dispositivo suportado operações e eventos</span><span class="sxs-lookup"><span data-stu-id="1c2a2-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="1c2a2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="1c2a2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="1c2a2-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="1c2a2-217">0x1002</span></span>  | <span data-ttu-id="1c2a2-218">Abra uma sessão entre o anfitrião e o dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="1c2a2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="1c2a2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="1c2a2-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="1c2a2-220">0x1003</span></span>  | <span data-ttu-id="1c2a2-221">Feche uma sessão entre o anfitrião e o dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="1c2a2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="1c2a2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="1c2a2-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="1c2a2-223">0x1004</span></span>  | <span data-ttu-id="1c2a2-224">Devolve o ID de armazenamento para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="1c2a2-225">USBX PIMA usa apenas um ID de armazenamento</span><span class="sxs-lookup"><span data-stu-id="1c2a2-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="1c2a2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="1c2a2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="1c2a2-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="1c2a2-227">0x1005</span></span>  | <span data-ttu-id="1c2a2-228">Devolva informações sobre o objeto de armazenamento, como a capacidade máxima e o espaço livre</span><span class="sxs-lookup"><span data-stu-id="1c2a2-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="1c2a2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="1c2a2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="1c2a2-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="1c2a2-230">0x1006</span></span>  | <span data-ttu-id="1c2a2-231">Devolva o número de objetos contidos no dispositivo de armazenamento</span><span class="sxs-lookup"><span data-stu-id="1c2a2-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="1c2a2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="1c2a2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="1c2a2-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="1c2a2-233">0x1007</span></span>  | <span data-ttu-id="1c2a2-234">Devolva uma série de pegas dos objetos no dispositivo de armazenamento</span><span class="sxs-lookup"><span data-stu-id="1c2a2-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="1c2a2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="1c2a2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="1c2a2-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="1c2a2-236">0x1008</span></span>  | <span data-ttu-id="1c2a2-237">Devolva informações sobre um objeto como o nome do objeto, a data de criação, data de modificação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="1c2a2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="1c2a2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="1c2a2-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="1c2a2-239">0x1009</span></span>  | <span data-ttu-id="1c2a2-240">Devolver os dados relativos a um objeto específico</span><span class="sxs-lookup"><span data-stu-id="1c2a2-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="1c2a2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="1c2a2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="1c2a2-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="1c2a2-242">0x100A</span></span>  | <span data-ttu-id="1c2a2-243">Envie a miniatura se estiver disponível sobre um objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="1c2a2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="1c2a2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="1c2a2-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="1c2a2-245">0x100B</span></span>  | <span data-ttu-id="1c2a2-246">Apagar um objeto nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="1c2a2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="1c2a2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="1c2a2-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="1c2a2-248">0x100C</span></span>  | <span data-ttu-id="1c2a2-249">Enviar ao dispositivo informações sobre um objeto para a sua criação nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="1c2a2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="1c2a2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="1c2a2-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="1c2a2-251">0x100D</span></span>  | <span data-ttu-id="1c2a2-252">Enviar dados para um objeto para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="1c2a2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="1c2a2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="1c2a2-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="1c2a2-254">0x100F</span></span>  | <span data-ttu-id="1c2a2-255">Limpe os meios de comunicação do dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="1c2a2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="1c2a2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="1c2a2-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="1c2a2-257">0x0110</span></span>  | <span data-ttu-id="1c2a2-258">Redefinir o dispositivo-alvo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="1c2a2-259">Código de Operação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-259">Operation Code</span></span>                                         | <span data-ttu-id="1c2a2-260">Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-260">Value</span></span> | <span data-ttu-id="1c2a2-261">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="1c2a2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="1c2a2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="1c2a2-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="1c2a2-263">0x4001</span></span>  | <span data-ttu-id="1c2a2-264">Cancela a transação atual</span><span class="sxs-lookup"><span data-stu-id="1c2a2-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="1c2a2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="1c2a2-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="1c2a2-266">0x4002</span></span>  | <span data-ttu-id="1c2a2-267">Um objeto foi adicionado aos meios de comunicação do dispositivo e pode ser recuperado pelo hospedeiro..</span><span class="sxs-lookup"><span data-stu-id="1c2a2-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="1c2a2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="1c2a2-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="1c2a2-269">0x4003</span></span>  | <span data-ttu-id="1c2a2-270">Um objeto foi eliminado dos meios de dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="1c2a2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="1c2a2-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="1c2a2-272">0x4004</span></span>  | <span data-ttu-id="1c2a2-273">Um meio de comunicação foi adicionado ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="1c2a2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="1c2a2-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="1c2a2-275">0x4005</span></span>  | <span data-ttu-id="1c2a2-276">Um meio foi eliminado do dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="1c2a2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="1c2a2-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="1c2a2-278">0x4006</span></span>  | <span data-ttu-id="1c2a2-279">As propriedades do dispositivo mudaram</span><span class="sxs-lookup"><span data-stu-id="1c2a2-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="1c2a2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="1c2a2-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="1c2a2-281">0x4007</span></span>  | <span data-ttu-id="1c2a2-282">Uma informação de objeto mudou</span><span class="sxs-lookup"><span data-stu-id="1c2a2-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="1c2a2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="1c2a2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="1c2a2-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="1c2a2-284">0x4008</span></span>  | <span data-ttu-id="1c2a2-285">Um dispositivo mudou</span><span class="sxs-lookup"><span data-stu-id="1c2a2-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="1c2a2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="1c2a2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="1c2a2-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="1c2a2-287">0x4009</span></span>  | <span data-ttu-id="1c2a2-288">O dispositivo solicita a transferência de um objeto do anfitrião</span><span class="sxs-lookup"><span data-stu-id="1c2a2-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="1c2a2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="1c2a2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="1c2a2-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="1c2a2-290">0x400A</span></span>  | <span data-ttu-id="1c2a2-291">O dispositivo informa que os meios de comunicação estão cheios</span><span class="sxs-lookup"><span data-stu-id="1c2a2-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="1c2a2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="1c2a2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="1c2a2-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="1c2a2-293">0x400B</span></span>  | <span data-ttu-id="1c2a2-294">O dispositivo informa que foi reposto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="1c2a2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="1c2a2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="1c2a2-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="1c2a2-296">0x400C</span></span>  | <span data-ttu-id="1c2a2-297">A informação de armazenamento mudou no dispositivo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="1c2a2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="1c2a2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="1c2a2-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="1c2a2-299">0x400D</span></span>  | <span data-ttu-id="1c2a2-300">A captura está concluída</span><span class="sxs-lookup"><span data-stu-id="1c2a2-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="1c2a2-301">A classe de dispositivo USBX PIMA utiliza um Fio TX para ouvir comandos PIMA do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="1c2a2-302">Um comando PIMA é composto por um bloco de comando, um bloco de dados e uma fase de estado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="1c2a2-303">A função ux_device_class_pima_thread posta um pedido à pilha para receber um comando PIMA do lado anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="1c2a2-304">O comando PIMA é descodificado e verificado para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="1c2a2-305">Se o bloco de comando for válido, ramifica-se ao controlador de comando apropriado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="1c2a2-306">A maioria dos comandos PIMA só podem ser executados quando uma sessão foi aberta pelo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="1c2a2-307">A única exceção é o comando **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO.**</span><span class="sxs-lookup"><span data-stu-id="1c2a2-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="1c2a2-308">Com a implementação usbx PIMA, apenas uma sessão pode ser aberta entre um Iniciador e um Responder a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="1c2a2-309">Todas as transações dentro da sessão estão bloqueadas e nenhuma nova transação pode começar antes da anterior ter sido concluída.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="1c2a2-310">As transações de PIMA são compostas por 3 fases, uma fase de comando, uma fase de dados opcional e uma fase de resposta.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="1c2a2-311">Se uma fase de dados estiver presente, só pode ser numa direção.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="1c2a2-312">O Iniciador determina sempre o fluxo das operações do PIMA, mas o Respondente pode iniciar eventos de volta ao Iniciador para informar as alterações de estado que ocorreram durante uma sessão.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="1c2a2-313">O diagrama seguinte mostra a transferência de um objeto de dados entre o hospedeiro e a classe de dispositivoS PIMA.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![Transações PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="1c2a2-315">Inicialização da classe de dispositivoS PIMA</span><span class="sxs-lookup"><span data-stu-id="1c2a2-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="1c2a2-316">A classe de dispositivo PIMA necessita de alguns parâmetros fornecidos pela aplicação durante a inicialização.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="1c2a2-317">Os seguintes parâmetros descrevem o dispositivo e as informações de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="1c2a2-318">A classe PIMA também requer o registo de retorno de chamada no pedido para informar a aplicação de determinados eventos ou recuperar/armazenar dados de/para os meios de comunicação locais.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="1c2a2-319">As chamadas são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="1c2a2-320">O exemplo a seguir mostra como inicializar o lado cliente do PIMA.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="1c2a2-321">Este exemplo usa a Pictbridge como cliente da PIMA.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="1c2a2-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="1c2a2-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="1c2a2-323">Adicionar um objeto e enviar o evento ao anfitrião</span><span class="sxs-lookup"><span data-stu-id="1c2a2-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-324">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="1c2a2-325">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-325">Description</span></span>

<span data-ttu-id="1c2a2-326">Esta função é chamada quando a classe PIMA precisa adicionar um objeto e informar o anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-327">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-327">Parameters</span></span>

- <span data-ttu-id="1c2a2-328">**pima**: Ponteiro para a instância da classe pima</span><span class="sxs-lookup"><span data-stu-id="1c2a2-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="1c2a2-329">**object_handle:** Manuseie o objeto.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-330">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="1c2a2-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="1c2a2-332">Obtenção do número do objeto da aplicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="1c2a2-334">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-334">Description</span></span>

<span data-ttu-id="1c2a2-335">Esta função é chamada quando a classe PIMA precisa de recuperar o número de objetos no sistema local e enviá-lo de volta para o hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-336">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-336">Parameters</span></span>

- <span data-ttu-id="1c2a2-337">**pima**: Ponteiro para a instância da classe pima</span><span class="sxs-lookup"><span data-stu-id="1c2a2-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="1c2a2-338">**object_number**: Endereço do número de objetos a devolver</span><span class="sxs-lookup"><span data-stu-id="1c2a2-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-339">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="1c2a2-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="1c2a2-341">Devolva a matriz do manípulo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-342">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="1c2a2-343">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-343">Description</span></span>

<span data-ttu-id="1c2a2-344">Esta função é chamada quando a classe PIMA precisa de recuperar a matriz de pegas de objetos no sistema local e enviá-la de volta para o hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-345">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-345">Parameters</span></span>

- <span data-ttu-id="1c2a2-346">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1c2a2-347">**object_handles_format_code**: Código de formato para as pegas</span><span class="sxs-lookup"><span data-stu-id="1c2a2-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="1c2a2-348">**object_handles_association**: Código de associação de objetos</span><span class="sxs-lookup"><span data-stu-id="1c2a2-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="1c2a2-349">**object_handle_array**: Endereço onde guardar as pegas</span><span class="sxs-lookup"><span data-stu-id="1c2a2-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="1c2a2-350">**object_handles_max_number**: Número máximo de pegas na matriz</span><span class="sxs-lookup"><span data-stu-id="1c2a2-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-351">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="1c2a2-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="1c2a2-353">Devolva a informação do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-354">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="1c2a2-355">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-355">Description</span></span>

<span data-ttu-id="1c2a2-356">Esta função é chamada quando a classe PIMA precisa de recuperar a matriz de pegas de objetos no sistema local e enviá-la de volta para o hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-357">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-357">Parameters</span></span>

- <span data-ttu-id="1c2a2-358">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1c2a2-359">**object_handles**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="1c2a2-360">**objeto**: Endereço do ponteiro do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-361">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="1c2a2-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="1c2a2-363">Devolva os dados do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-365">Description</span></span>

<span data-ttu-id="1c2a2-366">Esta função é chamada quando a classe PIMA precisa de recuperar os dados do objeto no sistema local e enviá-los de volta para o hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-367">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-367">Parameters</span></span>

- <span data-ttu-id="1c2a2-368">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="1c2a2-369">**object_handle**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="1c2a2-370">**object_buffer**: Endereço tampão de objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="1c2a2-371">**object_length_requested**: Comprimento dos dados do objeto solicitado pelo cliente à aplicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="1c2a2-372">**object_atual_length**: Comprimento dos dados do objeto devolvido pela aplicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-373">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="1c2a2-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="1c2a2-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="1c2a2-375">Host envia a informação do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="1c2a2-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-377">Description</span></span>

<span data-ttu-id="1c2a2-378">Esta função é chamada quando a classe PIMA precisa de receber a informação do objeto no sistema local para armazenamento futuro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-379">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-379">Parameters</span></span>

- <span data-ttu-id="1c2a2-380">**pima**: Ponteiro para a instância da classe pima</span><span class="sxs-lookup"><span data-stu-id="1c2a2-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="1c2a2-381">**objeto**: Ponteiro para o objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="1c2a2-382">**object_handle**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-383">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="1c2a2-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="1c2a2-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="1c2a2-385">Host envia os dados do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-386">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-387">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-387">Description</span></span>

<span data-ttu-id="1c2a2-388">Esta função é chamada quando a classe PIMA precisa de receber os dados do objeto no sistema local para armazenamento.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-389">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-389">Parameters</span></span>

- <span data-ttu-id="1c2a2-390">**pima**: Ponteiro para a instância da classe pima</span><span class="sxs-lookup"><span data-stu-id="1c2a2-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="1c2a2-391">**object_handle**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="1c2a2-392">**fase**: fase da transferência (ativa ou completa)</span><span class="sxs-lookup"><span data-stu-id="1c2a2-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="1c2a2-393">**object_buffer**: Endereço tampão de objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="1c2a2-394">**object_offset**: Endereço de dados</span><span class="sxs-lookup"><span data-stu-id="1c2a2-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="1c2a2-395">**object_length**: Comprimento dos dados do objeto enviado por aplicação</span><span class="sxs-lookup"><span data-stu-id="1c2a2-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-396">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="1c2a2-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="1c2a2-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="1c2a2-398">Apagar um objeto local</span><span class="sxs-lookup"><span data-stu-id="1c2a2-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="1c2a2-400">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-400">Description</span></span>

<span data-ttu-id="1c2a2-401">Esta função é chamada quando a classe PIMA precisa de apagar um objeto no armazenamento local.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-402">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-402">Parameters</span></span>

- <span data-ttu-id="1c2a2-403">**pima**: Ponteiro para a instância da classe pima</span><span class="sxs-lookup"><span data-stu-id="1c2a2-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="1c2a2-404">**object_handle**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="1c2a2-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-405">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="1c2a2-406">Classe de áudio do dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="1c2a2-406">USB Device Audio Class</span></span>

<span data-ttu-id="1c2a2-407">A classe de áudio do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="1c2a2-408">Esta classe baseia-se na norma USB e na norma USB Audio Class 1.0 ou 2.0.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="1c2a2-409">Uma estrutura do dispositivo de conformidade com o áudio USB tem de ser declarada pela pilha do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="1c2a2-410">Segue-se um exemplo de um altifalante Audio 2.0:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="1c2a2-411">A classe Audio utiliza uma estrutura de dispositivo composto para interfaces de grupo (controlo e streaming).</span><span class="sxs-lookup"><span data-stu-id="1c2a2-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="1c2a2-412">Como resultado, deve ter-se cuidado ao definir o descritor do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="1c2a2-413">O USBX conta com o descritor da IAD para saber internamente como ligar interfaces.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="1c2a2-414">O descritor DAI deve ser declarado antes das interfaces (uma interface AudioControl seguida de uma ou mais interfaces AudioStreaming) e conter a primeira interface da classe Áudio (a interface AudioControl) e quantas interfaces estão ligadas.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="1c2a2-415">A forma como a classe de áudio funciona depende se o dispositivo está a enviar ou a receber áudio, mas ambos os casos utilizam um FIFO para armazenar tampões de fotogramas de áudio: se o dispositivo estiver a enviar áudio para o anfitrião, então a aplicação adiciona tampões de fotogramas de áudio ao FIFO que são posteriormente enviados ao anfitrião por USBX; se o dispositivo estiver a receber áudio do anfitrião, então o USBX adiciona os amortecedores de fotogramas de áudio recebidos do anfitrião ao FIFO, que são posteriormente lidos pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="1c2a2-416">Cada fluxo de áudio tem o seu próprio FIFO, e cada tampão de quadro de áudio é composto por múltiplas amostras.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="1c2a2-417">A inicialização da classe Audio espera as seguintes partes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="1c2a2-418">A classe de áudio espera os seguintes parâmetros de streaming:</span><span class="sxs-lookup"><span data-stu-id="1c2a2-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="1c2a2-419">A classe de áudio espera os seguintes parâmetros de função.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="1c2a2-420">A chamada de pedido de controlo definida pela aplicação ***(ux_device_class_audio_control_process***; definida no exemplo anterior) é invocada quando a pilha recebe um pedido de controlo do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="1c2a2-421">Se o pedido for aceite e tratado (reconhecido ou parado) a chamada deve devolver o sucesso, caso contrário, o erro deve ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="1c2a2-422">O processo de pedido de controlo específico da classe é definido como uma chamada definida pela aplicação porque os pedidos de controlo são muito diferentes entre as versões USB Audio e uma grande parte do processo de pedido diz respeito à estrutura do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="1c2a2-423">A aplicação deve lidar corretamente com os pedidos para tornar o dispositivo funcional.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="1c2a2-424">Uma vez que para um dispositivo de áudio, volume, silenciamento e frequência de amostragem são pedidos de controlo comuns, as chamadas simples e definidas internamente para diferentes versões de áudio USB são introduzidas em secções posteriores para aplicações a utilizar.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="1c2a2-425">Consulte ***ux_device_class_audio10_control_process** _ e _ *_ux_device_class_audio_control_request_** para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="1c2a2-426">Na estrutura do dispositivo do dispositivo Audio, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado).</span><span class="sxs-lookup"><span data-stu-id="1c2a2-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="1c2a2-427">Quando um sistema de anfitrião USB descobre o dispositivo USB Audio e monta a classe de áudio, o dispositivo pode ser utilizado com qualquer leitor de áudio ou gravador (dependendo da estrutura).</span><span class="sxs-lookup"><span data-stu-id="1c2a2-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="1c2a2-428">Consulte o Sistema Operativo do anfitrião para obter referência.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="1c2a2-429">As APIs de classe áudio são definidas abaixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="1c2a2-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="1c2a2-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="1c2a2-431">Entrada de fio para ler dados para a função Áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-432">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-433">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-433">Description</span></span>

<span data-ttu-id="1c2a2-434">Esta função é transmitida para o parâmetro de inicialização do fluxo de áudio se for desejado o áudio de leitura do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="1c2a2-435">Internamente, um fio é criado com esta função como função de entrada; o próprio fio lê dados áudio através do ponto final isocrono out na função Áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-436">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-436">Parameters</span></span>

- <span data-ttu-id="1c2a2-437">**audio_stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-438">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="1c2a2-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="1c2a2-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="1c2a2-440">Entrada de fio para escrever dados para a função Áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-442">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-442">Description</span></span>

<span data-ttu-id="1c2a2-443">Esta função é transmitida para o parâmetro de inicialização do fluxo de áudio se desejar escrever áudio para o anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="1c2a2-444">Internamente, um fio é criado com esta função como função de entrada; o próprio fio escreve dados áudio através do ponto final isocrono IN na função Áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-445">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-445">Parameters</span></span>

- <span data-ttu-id="1c2a2-446">**audio_stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-447">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="1c2a2-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="1c2a2-449">Obtenha uma instância de streaming específica para a função Áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-450">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-451">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-451">Description</span></span>

<span data-ttu-id="1c2a2-452">Esta função é usada para obter uma série de streaming de classe áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-453">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-453">Parameters</span></span>

- <span data-ttu-id="1c2a2-454">**áudio**: Ponteiro para a instância áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="1c2a2-455">**stream_index**: Índice de instância de fluxo baseado em 0</span><span class="sxs-lookup"><span data-stu-id="1c2a2-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="1c2a2-456">**stream**: Ponteiro para tampão para armazenar o ponteiro de instância de fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-457">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-457">Return Value</span></span>

- <span data-ttu-id="1c2a2-458">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida</span><span class="sxs-lookup"><span data-stu-id="1c2a2-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="1c2a2-459">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-460">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="1c2a2-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="1c2a2-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="1c2a2-462">Inicie a receção de dados áudio para o stream de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-463">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-464">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-464">Description</span></span>

<span data-ttu-id="1c2a2-465">Esta função é utilizada para iniciar a leitura de dados áudio em streams de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-466">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-466">Parameters</span></span>

- <span data-ttu-id="1c2a2-467">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-468">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-468">Return Value</span></span>

- <span data-ttu-id="1c2a2-469">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-471">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="1c2a2-472">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-473">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="1c2a2-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="1c2a2-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="1c2a2-475">Leia a amostra de 8 bits do fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-476">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="1c2a2-477">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-477">Description</span></span>

<span data-ttu-id="1c2a2-478">Esta função lê dados de amostra sonora de 8 bits a partir do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="1c2a2-479">Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="1c2a2-480">Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-481">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-481">Parameters</span></span>

- <span data-ttu-id="1c2a2-482">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-483">**tampão**: Ponteiro para o tampão para salvar o byte da amostra.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-484">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-484">Return Value</span></span>

- <span data-ttu-id="1c2a2-485">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-487">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-488">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-489">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="1c2a2-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="1c2a2-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="1c2a2-491">Leia a amostra de 16 bits do fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-492">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="1c2a2-493">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-493">Description</span></span>

<span data-ttu-id="1c2a2-494">Esta função lê dados de amostra sonora de 16 bits a partir do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="1c2a2-495">Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="1c2a2-496">Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-497">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-497">Parameters</span></span>

- <span data-ttu-id="1c2a2-498">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-499">**tampão**: Ponteiro para o tampão para salvar a amostra de 16 bits.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-500">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-500">Return Value</span></span>

- <span data-ttu-id="1c2a2-501">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-503">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-504">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-505">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="1c2a2-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="1c2a2-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="1c2a2-507">Leia a amostra de 24 bits do fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-508">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="1c2a2-509">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-509">Description</span></span>

<span data-ttu-id="1c2a2-510">Esta função lê dados de amostra sonora de 24 bits a partir do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="1c2a2-511">Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="1c2a2-512">Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-513">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-513">Parameters</span></span>

- <span data-ttu-id="1c2a2-514">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-515">**tampão**: Ponteiro para o tampão para salvar a amostra de 3 bytes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-516">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-516">Return Value</span></span>

- <span data-ttu-id="1c2a2-517">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-519">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-520">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-521">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="1c2a2-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="1c2a2-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="1c2a2-523">Leia a amostra de 32 bits do fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-524">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="1c2a2-525">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-525">Description</span></span>

<span data-ttu-id="1c2a2-526">Esta função lê dados de amostra de áudio de 32 bits a partir do fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="1c2a2-527">Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="1c2a2-528">Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-529">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-529">Parameters</span></span>

- <span data-ttu-id="1c2a2-530">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-531">**tampão**: Ponteiro para o tampão para guardar os dados de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-532">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-532">Return Value</span></span>

- <span data-ttu-id="1c2a2-533">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-535">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-536">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-537">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="1c2a2-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="1c2a2-539">Obtenha acesso ao quadro áudio no fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-541">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-541">Description</span></span>

<span data-ttu-id="1c2a2-542">Esta função devolve o primeiro tampão de quadro de áudio e o seu comprimento no FIFO do stream especificado.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="1c2a2-543">Quando a aplicação é feita o processamento dos dados, ux_device_class_audio_read_frame_free devem ser utilizados para libertar o tampão de fotogramas no FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-544">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-544">Parameters</span></span>

- <span data-ttu-id="1c2a2-545">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-546">**frame_data**: Ponteiro para o ponteiro de dados para devolver o ponteiro de dados.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="1c2a2-547">**frame_length**: Ponteiro para tampão para guardar o comprimento da armação em número de bytes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-548">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-548">Return Value</span></span>

- <span data-ttu-id="1c2a2-549">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-551">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-552">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-553">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="1c2a2-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="1c2a2-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="1c2a2-555">Livre um tampão de quadro de áudio no fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-557">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-557">Description</span></span>

<span data-ttu-id="1c2a2-558">Esta função liberta o tampão de quadro de áudio na parte frontal do FIFO do stream especificado para que possa receber dados do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-559">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-559">Parameters</span></span>

- <span data-ttu-id="1c2a2-560">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-561">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-561">Return Value</span></span>

- <span data-ttu-id="1c2a2-562">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-564">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-565">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-566">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="1c2a2-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="1c2a2-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="1c2a2-568">Inicie a transmissão de dados áudio para o fluxo áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-569">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="1c2a2-570">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-570">Description</span></span>

<span data-ttu-id="1c2a2-571">Esta função é utilizada para começar a enviar dados áudio escritos para o FIFO na classe de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-572">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-572">Parameters</span></span>

- <span data-ttu-id="1c2a2-573">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-574">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-574">Return Value</span></span>

- <span data-ttu-id="1c2a2-575">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-577">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="1c2a2-578">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-579">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="1c2a2-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="1c2a2-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="1c2a2-581">Escreva uma moldura áudio no fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-583">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-583">Description</span></span>

<span data-ttu-id="1c2a2-584">Esta função escreve uma moldura para o FIFO do stream de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="1c2a2-585">Os dados do quadro são copiados para o tampão disponível no FIFO para que possa ser enviado para o anfitrião.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-586">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-586">Parameters</span></span>

- <span data-ttu-id="1c2a2-587">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-588">**quadro**: Ponteiro para os dados de quadro.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="1c2a2-589">**frame_length** Comprimento do quadro em número de bytes.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-590">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-590">Return Value</span></span>

- <span data-ttu-id="1c2a2-591">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-593">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="1c2a2-594">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-595">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="1c2a2-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="1c2a2-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="1c2a2-597">Obtenha acesso ao quadro áudio no fluxo de áudio</span><span class="sxs-lookup"><span data-stu-id="1c2a2-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-598">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-599">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-599">Description</span></span>

<span data-ttu-id="1c2a2-600">Esta função recupera o endereço do último tampão de quadro áudio do FIFO; também recupera o comprimento do tampão de quadro de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="1c2a2-601">Depois de a aplicação preencher o tampão de quadro áudio com os dados pretendidos, ***ux_device_class_audio_write_frame_commit*** devem ser utilizados para adicionar/comprometer o tampão de fotogramas ao FIFO.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-602">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-602">Parameters</span></span>

- <span data-ttu-id="1c2a2-603">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-604">**frame_data**: Ponteiro para o ponteiro de dados de quadro para devolver o ponteiro de dados de quadro dentro</span><span class="sxs-lookup"><span data-stu-id="1c2a2-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="1c2a2-605">**frame_length** Ponteiro para o tampão para guardar o comprimento do quadro em número de bytes .</span><span class="sxs-lookup"><span data-stu-id="1c2a2-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-606">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-606">Return Value</span></span>

- <span data-ttu-id="1c2a2-607">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-609">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="1c2a2-610">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-611">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="1c2a2-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="1c2a2-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="1c2a2-613">Comprometa um tampão de quadro de áudio no fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="1c2a2-615">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-615">Description</span></span>

<span data-ttu-id="1c2a2-616">Esta função adiciona/compromete o último tampão de fotogramas de áudio ao FIFO para que o tampão esteja pronto para ser transferido para o hospedeiro; note que o último tampão de quadro de áudio deveria ter sido preenchido através de ux_device_class_write_frame_get.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-617">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-617">Parameters</span></span>

- <span data-ttu-id="1c2a2-618">**stream**: Ponteiro para a instância de fluxo de áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="1c2a2-619">**comprimento**: Número de bytes prontos no tampão.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-620">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-620">Return Value</span></span>

- <span data-ttu-id="1c2a2-621">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="1c2a2-623">**UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é fssull.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="1c2a2-624">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-625">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="1c2a2-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="1c2a2-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="1c2a2-627">Processar pedidos de controlo USB Audio 1.0</span><span class="sxs-lookup"><span data-stu-id="1c2a2-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-628">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="1c2a2-629">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-629">Description</span></span>

<span data-ttu-id="1c2a2-630">Esta função gere os pedidos básicos enviados pelo anfitrião no ponto final de controlo com um tipo específico USB Audio 1.0.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="1c2a2-631">As funcionalidades áudio 1.0 dos pedidos de volume e de silenciamento são processadas na função.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="1c2a2-632">Ao processar os pedidos, os dados pré-definidos passados pelo último parâmetro (grupo) são utilizados para responder a pedidos e alterações no controlo da loja.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-633">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-633">Parameters</span></span>

- <span data-ttu-id="1c2a2-634">**áudio**: Ponteiro para a instância áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="1c2a2-635">**transferência**: Ponteiro para a instância de pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="1c2a2-636">**grupo**: Grupo de dados para processo de pedido.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-637">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-637">Return Value</span></span>

- <span data-ttu-id="1c2a2-638">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-639">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-640">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="1c2a2-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="1c2a2-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="1c2a2-642">Processar pedidos de controlo USB Audio 1.0</span><span class="sxs-lookup"><span data-stu-id="1c2a2-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="1c2a2-643">Prototype</span><span class="sxs-lookup"><span data-stu-id="1c2a2-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="1c2a2-644">Descrição</span><span class="sxs-lookup"><span data-stu-id="1c2a2-644">Description</span></span>

<span data-ttu-id="1c2a2-645">Esta função gere os pedidos básicos enviados pelo anfitrião no ponto final de controlo com um tipo específico USB Audio 2.0.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="1c2a2-646">A taxa de amostragem áudio 2.0 (frequência fixa única assumida), as características dos pedidos de volume e de silenciamento são processadas na função.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="1c2a2-647">Ao processar os pedidos, os dados pré-definidos passados pelo último parâmetro (grupo) são utilizados para responder a pedidos e alterações no controlo da loja.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="1c2a2-648">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1c2a2-648">Parameters</span></span>

- <span data-ttu-id="1c2a2-649">**áudio**: Ponteiro para a instância áudio.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="1c2a2-650">**transferência**: Ponteiro para a instância de pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="1c2a2-651">**grupo**: Grupo de dados para processo de pedido.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="1c2a2-652">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="1c2a2-652">Return Value</span></span>

- <span data-ttu-id="1c2a2-653">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1c2a2-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="1c2a2-654">**UX_ERROR** (0xFF) Erro da função</span><span class="sxs-lookup"><span data-stu-id="1c2a2-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="1c2a2-655">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c2a2-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
