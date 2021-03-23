---
title: Capítulo 4 - Implementação USBX Pictbridge
description: A UBSX suporta a implementação completa do Pictbridge tanto no hospedeiro como no dispositivo. Pictbridge fica no topo da classe USBX PIMA em ambos os lados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2ef1809dac046d49b15aba000cabed6c9fd458a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828555"
---
# <a name="chapter-4---usbx-pictbridge-implementation"></a><span data-ttu-id="aa315-104">Capítulo 4 - Implementação USBX Pictbridge</span><span class="sxs-lookup"><span data-stu-id="aa315-104">Chapter 4 - USBX Pictbridge implementation</span></span>

<span data-ttu-id="aa315-105">A UBSX suporta a implementação completa do Pictbridge tanto no hospedeiro como no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aa315-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="aa315-106">Pictbridge fica no topo da classe USBX PIMA em ambos os lados.</span><span class="sxs-lookup"><span data-stu-id="aa315-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span>

<span data-ttu-id="aa315-107">As normas PictBridge permitem a ligação de uma câmara digital imóvel ou de um telefone inteligente diretamente a uma impressora sem PC, permitindo a impressão direta a certas impressoras conscientes de Pictbridge.</span><span class="sxs-lookup"><span data-stu-id="aa315-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="aa315-108">Quando uma câmara ou telefone está ligado a uma impressora, a impressora é o anfitrião USB e a câmara é o dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="aa315-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="aa315-109">No entanto, com Pictbridge, a câmara aparecerá como sendo o anfitrião e os comandos são expulsos da câmara.</span><span class="sxs-lookup"><span data-stu-id="aa315-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="aa315-110">A câmara é o servidor de armazenamento, a impressora o cliente de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="aa315-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="aa315-111">A câmara é o cliente de impressão e a impressora é, naturalmente, o servidor de impressão.</span><span class="sxs-lookup"><span data-stu-id="aa315-111">The camera is the print client and the printer is of course the print server.</span></span>

<span data-ttu-id="aa315-112">Pictbridge usa USB como camada de transporte, mas depende de PTP (Protocolo de Transferência de Imagem) para o protocolo de comunicação.</span><span class="sxs-lookup"><span data-stu-id="aa315-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="aa315-113">Segue-se um diagrama dos comandos/respostas entre o cliente DPS e o servidor DPS quando ocorre uma tarefa de impressão:</span><span class="sxs-lookup"><span data-stu-id="aa315-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs:</span></span>

![Comandos e respostas DPS](./media/usbx-device-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="aa315-115">Implementação do cliente de Pictbridge</span><span class="sxs-lookup"><span data-stu-id="aa315-115">Pictbridge client implementation</span></span>

<span data-ttu-id="aa315-116">O Pictbridge no cliente requer que a pilha de dispositivos USBX e a classe PIMA sejam primeiramente funcionando.</span><span class="sxs-lookup"><span data-stu-id="aa315-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="aa315-117">Uma estrutura do dispositivo descreve a classe PIMA da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="aa315-117">A device framework describes the PIMA class in the following way.</span></span>

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
    0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,
    /* Configuration descriptor */
    0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

<span data-ttu-id="aa315-118">A classe Pima está a usar o campo de ID 0x06 e tem a sua subclasse é 0x01 para Still Image e o protocolo é 0x01 para PIMA 15740.</span><span class="sxs-lookup"><span data-stu-id="aa315-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="aa315-119">Três pontos finais são definidos nesta classe; duas massas para envio/receção de dados e uma interrupção para eventos.</span><span class="sxs-lookup"><span data-stu-id="aa315-119">Three endpoints are defined in this class; two bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="aa315-120">Ao contrário de outras implementações de dispositivos USBX, a aplicação Pictbridge não precisa de definir uma classe em si.</span><span class="sxs-lookup"><span data-stu-id="aa315-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="aa315-121">Pelo contrário, invoca a função ***ux_pictbridge_dpsclient_start.***</span><span class="sxs-lookup"><span data-stu-id="aa315-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="aa315-122">Um exemplo está abaixo.</span><span class="sxs-lookup"><span data-stu-id="aa315-122">An example is below.</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "ExpressLogic",13);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);

ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="aa315-123">Os parâmetros passados para o cliente pictbridge são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="aa315-123">The parameters passed to the pictbridge client are as follows.</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no
    : String of serial number
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="aa315-124">O próximo passo é que o dispositivo e o hospedeiro sincronizam e estejam prontos para trocar informações.</span><span class="sxs-lookup"><span data-stu-id="aa315-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="aa315-125">Isto é feito esperando uma bandeira de evento como se segue.</span><span class="sxs-lookup"><span data-stu-id="aa315-125">This is done by waiting on an event flag as follows.</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get(&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR,
    &actual_flags, UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="aa315-126">Se a máquina estatal estiver no estado **DISCOVERY_COMPLETE,** o lado da câmara (o cliente DPS) recolherá informações sobre a impressora e as suas capacidades.</span><span class="sxs-lookup"><span data-stu-id="aa315-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="aa315-127">Se o cliente DPS estiver pronto para aceitar um trabalho de impressão, o seu estado será definido para **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="aa315-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="aa315-128">Pode ser verificado abaixo.</span><span class="sxs-lookup"><span data-stu-id="aa315-128">It can be checked below.</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)
/* We can print something … */
```

<span data-ttu-id="aa315-129">Em seguida, alguns descritores de joib de impressão precisam ser preenchidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="aa315-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo -> ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo -> ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo -> ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo -> ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo -> ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */
printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object -> ux_device_class_pima_object_compressed_size = IMAGE_LEN;
object -> ux_device_class_pima_object_offset = 0;
object -> ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object -> ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="aa315-130">O cliente pictbridge tem agora um trabalho de impressão a fazer e irá buscar os blocos de imagem de cada vez a partir da aplicação através da chamada definida no campo</span><span class="sxs-lookup"><span data-stu-id="aa315-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field</span></span>

```C
jobinfo -> ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="aa315-131">O protótipo dessa função é definido como:</span><span class="sxs-lookup"><span data-stu-id="aa315-131">The prototype of that function is defined as:</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="aa315-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="aa315-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="aa315-133">Copiar um bloco de dados do espaço do utilizador para impressão</span><span class="sxs-lookup"><span data-stu-id="aa315-133">Copying a block of data from user space for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="aa315-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa315-134">Prototype</span></span>

```C
UINT ux_pictbridge_jobinfo_object_data_read( 
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,  
    ULONG object_offset,  
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="aa315-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa315-135">Description</span></span>

<span data-ttu-id="aa315-136">Esta função é chamada quando o cliente DPS precisa de recuperar um bloco de dados para imprimir na impressora Pictbridge alvo.</span><span class="sxs-lookup"><span data-stu-id="aa315-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa315-137">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa315-137">Parameters</span></span>

- <span data-ttu-id="aa315-138">**pictbridge**: Ponte para a instância da classe pictbridge.</span><span class="sxs-lookup"><span data-stu-id="aa315-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="aa315-139">**object_buffer**: Ponteiro para tampão de objeto</span><span class="sxs-lookup"><span data-stu-id="aa315-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="aa315-140">**object_offset**: Onde estamos começando a ler o bloco de dados</span><span class="sxs-lookup"><span data-stu-id="aa315-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="aa315-141">**object_length**: Comprimento a devolver</span><span class="sxs-lookup"><span data-stu-id="aa315-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="aa315-142">**atual_length**: Comprimento real devolvido</span><span class="sxs-lookup"><span data-stu-id="aa315-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="aa315-143">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="aa315-143">Return Value</span></span>

- <span data-ttu-id="aa315-144">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="aa315-144">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="aa315-145">**UX_ERROR** (0x01) A aplicação não conseguiu obter dados.</span><span class="sxs-lookup"><span data-stu-id="aa315-145">**UX_ERROR** (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="aa315-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa315-146">Example</span></span>

```C
/* Copy the object data. */
UINT ux_demo_object_data_copy(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);
    /* Update the actual length. */
    *actual_length = object_length;
    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="aa315-147">Implementação do anfitrião pictbridge</span><span class="sxs-lookup"><span data-stu-id="aa315-147">Pictbridge host implementation</span></span>

<span data-ttu-id="aa315-148">A implementação do hospedeiro de Pictbridge é diferente do cliente.</span><span class="sxs-lookup"><span data-stu-id="aa315-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="aa315-149">A primeira coisa a fazer num ambiente de acolhimento de Pictbridge é registar a classe Pima como o exemplo abaixo mostra:</span><span class="sxs-lookup"><span data-stu-id="aa315-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(_ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="aa315-150">Esta classe é a camada de PTP genérica sentada entre a pilha USB e a camada de Pictbridge.</span><span class="sxs-lookup"><span data-stu-id="aa315-150">This class is the generic PTP layer sitting between the USB stack and the Pictbridge layer.</span></span>

<span data-ttu-id="aa315-151">O próximo passo é inicializar os valores padrão de Pictbridge para os serviços de impressão da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="aa315-151">The next step is to initialize the Pictbridge default values for print services as follows:</span></span>

| <span data-ttu-id="aa315-152">Campo de Pictbridge</span><span class="sxs-lookup"><span data-stu-id="aa315-152">Pictbridge field</span></span>       | <span data-ttu-id="aa315-153">Valor</span><span class="sxs-lookup"><span data-stu-id="aa315-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="aa315-154">DpsVersion[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-154">DpsVersion[0]</span></span>          | <span data-ttu-id="aa315-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="aa315-155">0x00010000</span></span>                             |
| <span data-ttu-id="aa315-156">DpsVersão[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-156">DpsVersion[1]</span></span>          | <span data-ttu-id="aa315-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="aa315-157">0x00010001</span></span>                             |
| <span data-ttu-id="aa315-158">DpsVersão[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-158">DpsVersion[2]</span></span>          | <span data-ttu-id="aa315-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="aa315-159">0x00000000</span></span>                             |
| <span data-ttu-id="aa315-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="aa315-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="aa315-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="aa315-161">0x00010000</span></span>                             |
| <span data-ttu-id="aa315-162">Serviço de Impressão Disponível</span><span class="sxs-lookup"><span data-stu-id="aa315-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="aa315-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="aa315-163">0x30010000</span></span>                             |
| <span data-ttu-id="aa315-164">Qualidades[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-164">Qualities[0]</span></span>           | <span data-ttu-id="aa315-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="aa315-166">Qualidades[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-166">Qualities[1]</span></span>           | <span data-ttu-id="aa315-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="aa315-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="aa315-168">Qualidades[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-168">Qualities[2]</span></span>           | <span data-ttu-id="aa315-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="aa315-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="aa315-170">Qualidades[3]</span><span class="sxs-lookup"><span data-stu-id="aa315-170">Qualities[3]</span></span>           | <span data-ttu-id="aa315-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="aa315-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="aa315-172">PaperSizes[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-172">PaperSizes[0]</span></span>          | <span data-ttu-id="aa315-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="aa315-174">PaperSizes[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-174">PaperSizes[1]</span></span>          | <span data-ttu-id="aa315-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="aa315-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="aa315-176">PapelSizes[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-176">PaperSizes[2]</span></span>          | <span data-ttu-id="aa315-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="aa315-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="aa315-178">PapelSizes[3]</span><span class="sxs-lookup"><span data-stu-id="aa315-178">PaperSizes[3]</span></span>          | <span data-ttu-id="aa315-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="aa315-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="aa315-180">PapelSizes[4]</span><span class="sxs-lookup"><span data-stu-id="aa315-180">PaperSizes[4]</span></span>          | <span data-ttu-id="aa315-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="aa315-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="aa315-182">Tipos de Papel[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-182">PaperTypes[0]</span></span>          | <span data-ttu-id="aa315-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="aa315-184">Tipos de Papel[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-184">PaperTypes[1]</span></span>          | <span data-ttu-id="aa315-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="aa315-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="aa315-186">Tipos de Papel[2)</span><span class="sxs-lookup"><span data-stu-id="aa315-186">PaperTypes[2</span></span>           | <span data-ttu-id="aa315-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="aa315-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="aa315-188">FileTypes[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-188">FileTypes[0]</span></span>           | <span data-ttu-id="aa315-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="aa315-190">FileTypes[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-190">FileTypes[1]</span></span>           | <span data-ttu-id="aa315-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="aa315-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="aa315-192">FileTypes[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-192">FileTypes[2]</span></span>           | <span data-ttu-id="aa315-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="aa315-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="aa315-194">FileTypes[3]</span><span class="sxs-lookup"><span data-stu-id="aa315-194">FileTypes[3]</span></span>           | <span data-ttu-id="aa315-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="aa315-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="aa315-196">DataPrints[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-196">DatePrints[0]</span></span>          | <span data-ttu-id="aa315-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="aa315-198">DataPrints[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-198">DatePrints[1]</span></span>          | <span data-ttu-id="aa315-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="aa315-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="aa315-200">DataPrints[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-200">DatePrints[2]</span></span>          | <span data-ttu-id="aa315-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="aa315-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="aa315-202">FileNamePrints[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="aa315-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="aa315-204">FileNamePrints[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="aa315-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="aa315-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="aa315-206">FileNamePrints[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="aa315-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="aa315-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="aa315-208">ImageOptimize[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="aa315-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="aa315-210">ImageOptimize[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="aa315-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="aa315-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="aa315-212">ImageOptimize[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="aa315-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="aa315-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="aa315-214">Layouts[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-214">Layouts[0]</span></span>             | <span data-ttu-id="aa315-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="aa315-216">Layouts[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-216">Layouts[1]</span></span>             | <span data-ttu-id="aa315-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="aa315-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="aa315-218">Layouts[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-218">Layouts[2]</span></span>             | <span data-ttu-id="aa315-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="aa315-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="aa315-220">Layouts[3]</span><span class="sxs-lookup"><span data-stu-id="aa315-220">Layouts[3]</span></span>             | <span data-ttu-id="aa315-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="aa315-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="aa315-222">Tamanho fixo[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-222">FixedSizes[0]</span></span>          | <span data-ttu-id="aa315-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="aa315-224">Tamanho fixo[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-224">FixedSizes[1]</span></span>          | <span data-ttu-id="aa315-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="aa315-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="aa315-226">Tamanho fixo[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-226">FixedSizes[2]</span></span>          | <span data-ttu-id="aa315-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="aa315-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="aa315-228">Tamanho fixo[3]</span><span class="sxs-lookup"><span data-stu-id="aa315-228">FixedSizes[3]</span></span>          | <span data-ttu-id="aa315-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="aa315-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="aa315-230">Tamanho fixo[4]</span><span class="sxs-lookup"><span data-stu-id="aa315-230">FixedSizes[4]</span></span>          | <span data-ttu-id="aa315-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="aa315-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="aa315-232">Tamanho fixo[5]</span><span class="sxs-lookup"><span data-stu-id="aa315-232">FixedSizes[5]</span></span>          | <span data-ttu-id="aa315-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="aa315-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="aa315-234">Tamanho fixo[6]</span><span class="sxs-lookup"><span data-stu-id="aa315-234">FixedSizes[6]</span></span>          | <span data-ttu-id="aa315-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="aa315-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="aa315-236">Colheitas[0]</span><span class="sxs-lookup"><span data-stu-id="aa315-236">Croppings[0]</span></span>           | <span data-ttu-id="aa315-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="aa315-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="aa315-238">Culturas[1]</span><span class="sxs-lookup"><span data-stu-id="aa315-238">Croppings[1]</span></span>           | <span data-ttu-id="aa315-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="aa315-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="aa315-240">Culturas[2]</span><span class="sxs-lookup"><span data-stu-id="aa315-240">Croppings[2]</span></span>           | <span data-ttu-id="aa315-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="aa315-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="aa315-242">A máquina estatal do anfitrião DPS estará pronta para ficar inativa e pronta para aceitar um novo trabalho de impressão.</span><span class="sxs-lookup"><span data-stu-id="aa315-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="aa315-243">A parte hospedeira de Pictbridge pode agora ser iniciada como o exemplo abaixo mostra:</span><span class="sxs-lookup"><span data-stu-id="aa315-243">The host portion of Pictbridge can now be started as the example below shows:</span></span>

```C
/* Activate the pictbridge dpshost. */
status = ux_pictbridge_dpshost_start(&pictbridge, pima);

if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="aa315-244">A função de anfitrião Pictbridge requer uma chamada quando os dados estão prontos para serem impressos.</span><span class="sxs-lookup"><span data-stu-id="aa315-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="aa315-245">Isto é conseguido passando um ponteiro de função na estrutura do hospedeiro pictbridge da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="aa315-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */
pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="aa315-246">Esta função tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="aa315-246">This function has the following properties.</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="aa315-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="aa315-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="aa315-248">Escrever um bloco de dados para impressão</span><span class="sxs-lookup"><span data-stu-id="aa315-248">Writing a block of data for printing</span></span>

### <a name="prototype"></a><span data-ttu-id="aa315-249">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa315-249">Prototype</span></span>

```C
UINT ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge, 
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="aa315-250">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa315-250">Description</span></span>

<span data-ttu-id="aa315-251">Esta função é chamada quando o servidor DPS precisa de recuperar um bloco de dados do cliente DPS para imprimir na impressora local.</span><span class="sxs-lookup"><span data-stu-id="aa315-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="aa315-252">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa315-252">Parameters</span></span>

- <span data-ttu-id="aa315-253">**pictbridge**: Ponte para a instância da classe pictbridge.</span><span class="sxs-lookup"><span data-stu-id="aa315-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="aa315-254">**object_buffer**: Ponteiro para tampão de objeto</span><span class="sxs-lookup"><span data-stu-id="aa315-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="aa315-255">**object_offset**: Onde estamos começando a ler o bloco de dados</span><span class="sxs-lookup"><span data-stu-id="aa315-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="aa315-256">**total_length**: Todo o comprimento do objeto</span><span class="sxs-lookup"><span data-stu-id="aa315-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="aa315-257">**comprimento**: Comprimento deste tampão</span><span class="sxs-lookup"><span data-stu-id="aa315-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="aa315-258">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="aa315-258">Return Value</span></span>

- <span data-ttu-id="aa315-259">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="aa315-259">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="aa315-260">**UX_ERROR** (0x01) A aplicação não conseguiu imprimir dados.</span><span class="sxs-lookup"><span data-stu-id="aa315-260">**UX_ERROR** (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="aa315-261">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa315-261">Example</span></span>

```C
/* Copy the object data. */
UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;
    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
