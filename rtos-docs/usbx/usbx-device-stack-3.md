---
title: Capítulo 3 - Componentes funcionais da pilha de dispositivos USBX
description: Este capítulo contém uma descrição da pilha de dispositivo USB USB incorporada de alto desempenho de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827427"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="0cc4b-103">Capítulo 3 - Componentes funcionais da pilha de dispositivos USBX</span><span class="sxs-lookup"><span data-stu-id="0cc4b-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="0cc4b-104">Este capítulo contém uma descrição da pilha de dispositivo USB USB incorporada de alto desempenho de uma perspetiva funcional.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="0cc4b-105">Visão geral da execução</span><span class="sxs-lookup"><span data-stu-id="0cc4b-105">Execution Overview</span></span>

<span data-ttu-id="0cc4b-106">USBX para o dispositivo é composto por vários componentes.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="0cc4b-107">Inicialização</span><span class="sxs-lookup"><span data-stu-id="0cc4b-107">Initialization</span></span>
- <span data-ttu-id="0cc4b-108">Chamadas de interface de aplicação</span><span class="sxs-lookup"><span data-stu-id="0cc4b-108">Application interface calls</span></span>
- <span data-ttu-id="0cc4b-109">Classes de Dispositivos</span><span class="sxs-lookup"><span data-stu-id="0cc4b-109">Device Classes</span></span>
- <span data-ttu-id="0cc4b-110">Pilha de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="0cc4b-110">USB Device Stack</span></span>
- <span data-ttu-id="0cc4b-111">Controlador de dispositivos</span><span class="sxs-lookup"><span data-stu-id="0cc4b-111">Device controller</span></span>
- <span data-ttu-id="0cc4b-112">Gestor VBUS</span><span class="sxs-lookup"><span data-stu-id="0cc4b-112">VBUS manager</span></span>

<span data-ttu-id="0cc4b-113">O diagrama seguinte ilustra a pilha de dispositivo USBX.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-113">The following diagram illustrates the USBX Device stack.</span></span>

![Pilha de dispositivo USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="0cc4b-115">Inicialização</span><span class="sxs-lookup"><span data-stu-id="0cc4b-115">Initialization</span></span>

<span data-ttu-id="0cc4b-116">Para ativar o USBX, a função ***ux_system_initialize*** deve ser chamada.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="0cc4b-117">Esta função inicializa os recursos de memória do USBX.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="0cc4b-118">Para ativar as instalações do dispositivo USBX, a função ***ux_device_stack_initialize*** deve ser chamada.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="0cc4b-119">Esta função irá, por sua vez, inicializar todos os recursos utilizados pela pilha de dispositivos USBX, tais como fios ThreadX, mutexes e semáforos.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="0cc4b-120">Cabe à inicialização da aplicação ativar o controlador do dispositivo USB e uma ou mais classes USB.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="0cc4b-121">Ao contrário do lado do anfitrião USB, o lado do dispositivo pode ter apenas um controlador USB a funcionar a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="0cc4b-122">Quando as classes estiverem registadas na stack e a função de inicialização do controlador do dispositivo tiver sido chamada, o autocarro está ativo e a pilha responderá aos comandos de reposição de autocarros e de enumeração do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="0cc4b-123">Chamadas de Interface de Aplicação</span><span class="sxs-lookup"><span data-stu-id="0cc4b-123">Application Interface Calls</span></span>

<span data-ttu-id="0cc4b-124">Há dois níveis de APIs em USBX.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="0cc4b-125">APIs de pilha de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="0cc4b-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="0cc4b-126">APIs classe de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="0cc4b-126">USB Device Class APIs</span></span>

<span data-ttu-id="0cc4b-127">Normalmente, uma aplicação USBX não deve ter de chamar apis de pilha de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="0cc4b-128">A maioria das aplicações só acederá às APIs da classe USB.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="0cc4b-129">APIs de pilha de dispositivos USB</span><span class="sxs-lookup"><span data-stu-id="0cc4b-129">USB Device Stack APIs</span></span>

<span data-ttu-id="0cc4b-130">As APIs da pilha de dispositivos são responsáveis pelo registo de componentes do dispositivo USBX, tais como classes e a estrutura do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="0cc4b-131">APIs classe de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="0cc4b-131">USB Device Class APIs</span></span>

<span data-ttu-id="0cc4b-132">As APIs de classe são muito específicas de cada classe USB.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="0cc4b-133">A maioria das APIs comuns para classes USB forneceu serviços como abrir/fechar um dispositivo e ler e escrever para um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="0cc4b-134">As APIs são semelhantes na natureza ao lado hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="0cc4b-135">Estrutura do Dispositivo</span><span class="sxs-lookup"><span data-stu-id="0cc4b-135">Device Framework</span></span>

<span data-ttu-id="0cc4b-136">O lado do dispositivo USB é responsável pela definição da estrutura do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="0cc4b-137">A estrutura do dispositivo é dividida em três categorias, conforme descrito nas seguintes secções.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="0cc4b-138">Definição dos componentes da estrutura do dispositivo</span><span class="sxs-lookup"><span data-stu-id="0cc4b-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="0cc4b-139">A definição de cada componente da estrutura do dispositivo está relacionada com a natureza do dispositivo e com os recursos utilizados pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="0cc4b-140">Seguem-se as principais categorias.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-140">Following are the main categories.</span></span>

- <span data-ttu-id="0cc4b-141">Descritor de dispositivos</span><span class="sxs-lookup"><span data-stu-id="0cc4b-141">Device Descriptor</span></span>
- <span data-ttu-id="0cc4b-142">Descritor de configuração</span><span class="sxs-lookup"><span data-stu-id="0cc4b-142">Configuration Descriptor</span></span>
- <span data-ttu-id="0cc4b-143">Descritor de interface</span><span class="sxs-lookup"><span data-stu-id="0cc4b-143">Interface Descriptor</span></span>
- <span data-ttu-id="0cc4b-144">Descritor de ponto final</span><span class="sxs-lookup"><span data-stu-id="0cc4b-144">Endpoint Descriptor</span></span>

<span data-ttu-id="0cc4b-145">USBX suporta a definição de componente do dispositivo para alta e a velocidade máxima (sendo tratada a baixa velocidade da mesma forma que a velocidade máxima).</span><span class="sxs-lookup"><span data-stu-id="0cc4b-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="0cc4b-146">Isto permite que o dispositivo funcione de forma diferente quando ligado a um hospedeiro de alta velocidade ou a toda a velocidade.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="0cc4b-147">As diferenças típicas são o tamanho de cada ponto final e a energia consumida pelo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="0cc4b-148">A definição do componente do dispositivo assume a forma de uma cadeia byte que segue a especificação USB.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="0cc4b-149">A definição é contígua e a ordem em que o quadro está representado na memória será a mesma que a devolvida ao hospedeiro durante a enumeração.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="0cc4b-150">Segue-se um exemplo de uma estrutura do dispositivo para um disco FLASH USB de alta velocidade.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="0cc4b-151">Definição das cordas da estrutura do dispositivo</span><span class="sxs-lookup"><span data-stu-id="0cc4b-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="0cc4b-152">As cordas são opcionais num dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-152">Strings are optional in a device.</span></span> <span data-ttu-id="0cc4b-153">O seu objetivo é informar o anfitrião USB sobre o fabricante do dispositivo, o nome do produto e o número de revisão através das cordas Unicode.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="0cc4b-154">As cordas principais são índices incorporados nos descritores do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="0cc4b-155">Índices de cordas adicionais podem ser incorporados em interfaces individuais.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="0cc4b-156">Assumindo que a estrutura do dispositivo acima tem três índices de cadeia incorporados no descritor do dispositivo, a definição de estrutura de cadeia pode parecer este código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="0cc4b-157">Se tiverem de ser utilizadas diferentes cordas para cada velocidade, devem ser utilizados diferentes índices, uma vez que os índices são agnósticos de velocidade.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="0cc4b-158">A codificação da cadeia é baseada em UNICODE.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="0cc4b-159">Para obter mais informações sobre a norma de codificação UNICODE consulte a seguinte publicação:</span><span class="sxs-lookup"><span data-stu-id="0cc4b-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="0cc4b-160">*O Unicode Standard, Worldwide Character Encoding, Versão 1., Volumes 1 e 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span><span class="sxs-lookup"><span data-stu-id="0cc4b-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="0cc4b-161">Definição dos idiomas suportados pelo dispositivo para cada cadeia</span><span class="sxs-lookup"><span data-stu-id="0cc4b-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="0cc4b-162">USBX tem a capacidade de suportar vários idiomas, embora o inglês seja o padrão.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="0cc4b-163">A definição de cada idioma para os descritores de cordas é na forma de uma variedade de definições de línguas definidas da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="0cc4b-164">Para suportar idiomas adicionais, basta adicionar a definição de código de idioma de duplo byte após o código inglês predefinido.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="0cc4b-165">O código de idioma foi definido pela Microsoft no documento.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="0cc4b-166">*Desenvolvimento de Software Internacional para Windows 95 e Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span><span class="sxs-lookup"><span data-stu-id="0cc4b-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="0cc4b-167">Gestor VBUS</span><span class="sxs-lookup"><span data-stu-id="0cc4b-167">VBUS Manager</span></span>

<span data-ttu-id="0cc4b-168">Na maioria dos desenhos de dispositivos USB, o VBUS não faz parte do núcleo do dispositivo USB, mas sim está ligado a um GPIO externo, que monitoriza o sinal de linha.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="0cc4b-169">Como resultado, a VBUS tem de ser gerida separadamente do controlador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="0cc4b-170">Cabe à aplicação fornecer ao controlador do dispositivo o endereço do VBUS IO.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="0cc4b-171">O VBUS deve ser inicializado antes da inicialização do controlador do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="0cc4b-172">Dependendo da especificação da plataforma de monitorização do VBUS, é possível permitir que o controlador manuseie os sinais VBUS após a inicializada VBUS IO ou, se tal não for possível, a aplicação tem de fornecer o código de manuseamento do VBUS.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="0cc4b-173">Se a aplicação pretender manusear o VBUS por si só, o seu único requisito é chamar a função ***ux_device_stack_disconnect*** quando detetar que um dispositivo foi extraído.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="0cc4b-174">Não é necessário informar o controlador quando um dispositivo é inserido porque o controlador acordará quando for detetado o sinal de assert/deassert do BUS RESET.</span><span class="sxs-lookup"><span data-stu-id="0cc4b-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
