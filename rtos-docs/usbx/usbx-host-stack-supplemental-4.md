---
title: Implementação USBX Pictbridge
description: A UBSX suporta a implementação completa do Pictbridge tanto no hospedeiro como no dispositivo. Pictbridge fica no topo da classe USBX PIMA em ambos os lados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9f4ba97741d2fc5f93afe6866b9ae6e9dc1e98a977eb3d6050c4a7489804c93c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790726"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a>Capítulo 4: Implementação USBX Pictbridge

A UBSX suporta a implementação completa do Pictbridge tanto no hospedeiro como no dispositivo. Pictbridge fica no topo da classe USBX PIMA em ambos os lados. 

As normas PictBridge permitem a ligação de uma câmara digital imóvel ou de um telefone inteligente diretamente a uma impressora sem PC, permitindo a impressão direta a certas impressoras conscientes de Pictbridge.

Quando uma câmara ou telefone está ligado a uma impressora, a impressora é o anfitrião USB e a câmara é o dispositivo USB. No entanto, com Pictbridge, a câmara aparecerá como sendo o anfitrião e os comandos são expulsos da câmara. A câmara é o servidor de armazenamento, a impressora o cliente de armazenamento. A câmara é o cliente de impressão e a impressora é, claro, o servidor de impressão.

Pictbridge usa USB como camada de transporte, mas depende de PTP (Protocolo de Transferência de Imagem) para o protocolo de comunicação.

Segue-se um diagrama dos comandos/respostas entre o cliente DPS e o servidor DPS quando ocorre uma tarefa de impressão.

![Diagrama dos comandos/respostas entre o cliente D P S e o servidor D P S quando ocorre uma tarefa de impressão.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Implementação do cliente de Pictbridge

O Pictbridge no cliente requer que a pilha de dispositivos USBX e a classe PIMA sejam primeiramente funcionando.

Uma estrutura do dispositivo descreve a classe PIMA da seguinte forma.

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

A classe Pima está a usar o campo de ID 0x06 e tem a sua subclasse é 0x01 para Still Image e o protocolo é 0x01 para PIMA 15740.

3 pontos finais são definidos nesta classe, 2 massas para envio/receção de dados e uma interrupção para eventos.

Ao contrário de outras implementações de dispositivos USBX, a aplicação Pictbridge não precisa de definir uma classe em si. Pelo contrário, invoca a função ***ux_pictbridge_dpsclient_start.*** Um exemplo está abaixo:

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

Os parâmetros passados para o cliente pictbridge são os seguintes:

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

O próximo passo é que o dispositivo e o hospedeiro sincronizam e estejam prontos para trocar informações.

Isto é feito esperando uma bandeira do evento da seguinte forma:

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

Se a máquina estatal estiver no estado **DISCOVERY_COMPLETE,** o lado da câmara (o cliente DPS) recolherá informações sobre a impressora e as suas capacidades.

Se o cliente DPS estiver pronto para aceitar um trabalho de impressão, o seu estado será definido para **UX_PICTBRIDGE_NEW_JOB_TRUE**. Pode ser verificado abaixo:

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

Em seguida, alguns descritores de joib de impressão precisam ser preenchidos da seguinte forma:

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
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
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

O cliente pictbridge tem agora um trabalho de impressão a fazer e irá buscar os blocos de imagem de cada vez a partir da aplicação através da chamada definida no campo.

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

O protótipo dessa função é definido da seguinte forma.

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

Copiar um bloco de dados do espaço do utilizador para impressão.

### <a name="prototype"></a>Prototype

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>Description

Esta função é chamada quando o cliente DPS precisa de recuperar um bloco de dados para imprimir na impressora Pictbridge alvo.

### <a name="parameters"></a>Parâmetros

- **pictbridge**: Ponte para a instância da classe pictbridge.
- **object_buffer**: Ponteiro para tampão de objeto
- **object_offset**: Onde estamos começando a ler o bloco de dados
- **object_length**: Comprimento a devolver
- **atual_length**: Comprimento real devolvido

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) Esta operação foi bem sucedida.
- **UX_ERROR**: (0x01) A aplicação não conseguiu obter dados.

### <a name="example"></a>Exemplo

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
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

## <a name="pictbridge-host-implementation"></a>Implementação do anfitrião pictbridge

A implementação do hospedeiro de Pictbridge é diferente do cliente.

A primeira coisa a fazer num ambiente de acolhimento de Pictbridge é registar a classe Pima como o exemplo abaixo mostra:

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

Esta classe é a camada de PTP genérica sentada entre a pilha de hospedeiro USB e a camada de Pictbridge.

O próximo passo é inicializar os valores padrão de Pictbridge para os serviços de impressão da seguinte forma.

| Campo de Pictbridge       | Valor                                  |
|------------------------|----------------------------------------|
| DpsVersion[0]          | 0x00010000                             |
| DpsVersão[1]          | 0x00010001                             |
| DpsVersão[2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| Serviço de Impressão Disponível  | 0x30010000                             |
| Qualidades[0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Qualidades[1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Qualidades[2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Qualidades[3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes[0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes[1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PapelSizes[2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PapelSizes[3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PapelSizes[4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| Tipos de Papel[0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| Tipos de Papel[1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| Tipos de Papel[2]          | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| FileTypes[0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| FileTypes[1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| FileTypes[2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| FileTypes[3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DataPrints[0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DataPrints[1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DataPrints[2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints[0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints[1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints[2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimize[0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimize[1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimize[2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouts[0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouts[1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouts[2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouts[3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| Tamanho fixo[0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| Tamanho fixo[1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| Tamanho fixo[2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| Tamanho fixo[3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| Tamanho fixo[4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| Tamanho fixo[5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| Tamanho fixo[6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Colheitas[0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Culturas[1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Culturas[2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

A máquina estatal do anfitrião DPS estará pronta para ficar inativa e pronta para aceitar um novo trabalho de impressão.

A parte hospedeira de Pictbridge pode agora ser iniciada como o exemplo abaixo mostra.

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

A função de anfitrião Pictbridge requer uma chamada quando os dados estão prontos para serem impressos. Isto é conseguido passando um ponteiro de função na estrutura do hospedeiro pictbridge da seguinte forma.

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

Esta função tem as seguintes propriedades:

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

Escrevendo um bloco de dados para impressão.

### <a name="prototype"></a>Prototype

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>Description

Esta função é chamada quando o servidor DPS precisa de recuperar um bloco de dados do cliente DPS para imprimir na impressora local.

### <a name="parameters"></a>Parâmetros

- **pictbridge**: Ponte para a instância da classe pictbridge.
- **object_buffer**: Ponteiro para tampão de objeto
- **object_offset**: Onde estamos começando a ler o bloco de dados
- **total_length**: Todo o comprimento do objeto
- **comprimento**: Comprimento deste tampão

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS**: (0x00) Esta operação foi bem sucedida.
- **UX_ERROR**: (0x01) A aplicação não pôde imprimir dados.

### <a name="example"></a>Exemplo

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
