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
# <a name="chapter-2---usbx-device-class-considerations"></a>Capítulo 2 - Considerações da classe do dispositivo USBX

## <a name="usb-device-rndis-class"></a>Classe RNDIS de dispositivo USB

A classe RNDIS do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo ethernet. Esta classe baseia-se na implementação proprietária da Microsoft e é específica para as plataformas do Windows.

Uma estrutura do dispositivo compatível com RNDIS tem de ser declarada pela pilha do dispositivo. Um exemplo é encontrado abaixo.

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

A classe RNDIS usa uma abordagem de descritor de dispositivos muito semelhante ao CDC-ACM e CDC-ECM e também requer um descritor de IAD. Consulte a classe CDC-ACM para definição e requisitos para o descritor do dispositivo.

A ativação da classe RNDIS é a seguinte.

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

Quanto ao CDC-ECM, a classe RNDIS requer 2 nós, um local e um remoto, mas não há necessidade de ter um descritor de cordas descrevendo o nó remoto.

No entanto, devido ao mecanismo de mensagens proprietárias da Microsoft, são necessários alguns parâmetros adicionais. Primeiro, a identificação do vendedor tem de ser aprovada. Da mesma forma, a versão condutora do RNDIS. Um fio de vendedor também deve ser dado.

A classe RNDIS tem APIs incorporados para transferir dados em ambos os sentidos, mas estão escondidos na aplicação, uma vez que a aplicação do utilizador comunicará com o dispositivo USB Ethernet através do NetX.

A classe USBX RNDIS está intimamente ligada à pilha de rede Azure RTOS NetX. Uma aplicação utilizando a classe NetX e USBX RNDIS irá ativar a pilha de rede NetX da forma habitual, mas além disso precisa de ativar a pilha de rede USB da seguinte forma.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

A pilha de rede USB precisa de ser ativada apenas uma vez e não é específica para o RNDIS, mas é exigida por qualquer classe USB que exija serviços NetX.

A classe RNDIS não será reconhecida pelos anfitriões MAC OS e Linux, uma vez que é específica dos sistemas operativos da Microsoft. Nas plataformas do Windows, um ficheiro .inf tem de estar presente no anfitrião que corresponda ao descritor do dispositivo. A Microsoft fornece um modelo para a classe RNDIS e pode ser encontrado no diretório usbx_windows_host_files. Para a versão mais recente do Windows, o ficheiro RNDIS_Template.inf deve ser utilizado. Este ficheiro precisa de ser modificado para refletir o PID/VID utilizado pelo dispositivo. O PID/VID será específico para o cliente final quando a empresa e o produto estiverem registados no USB-IF. No ficheiro inf, os campos a modificar estão localizados aqui.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

Na estrutura do dispositivo do dispositivo RNDIS, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado)

Quando um sistema de anfitrião USB descobre o dispositivo USB RNDIS, irá montar uma interface de rede e o dispositivo pode ser utilizado com a pilha de protocolo de rede. Consulte o Sistema Operativo do anfitrião para obter referência.

## <a name="usb-device-dfu-class"></a>Classe DFU de dispositivo USB

A classe DFU do dispositivo USB permite que um sistema de anfitriões USB atualize o firmware do dispositivo com base numa aplicação de anfitrião. A classe DFU é uma classe padrão USB-IF.

A classe USBX DFU é relativamente simples. O descritor do dispositivo não requer nada além de um ponto final de controlo. Na maior parte das vezes, esta classe será incorporada num dispositivo composto USB. O dispositivo pode ser qualquer coisa como um dispositivo de armazenamento ou um dispositivo de comunicação e a interface DFU adicionada pode informar o anfitrião de que o dispositivo pode ter o seu firmware atualizado no voo.

A classe DFU funciona em 3 passos. Primeiro, o dispositivo monta normalmente utilizando a classe exportada. Uma aplicação no anfitrião (Windows ou Linux) exercerá a classe DFU e enviará um pedido para reiniciar o dispositivo no modo DFU. O dispositivo desaparecerá do autocarro por um curto período de tempo (o suficiente para o anfitrião e o dispositivo detetarem uma sequência RESET) e, ao reiniciar, o dispositivo estará exclusivamente no modo DFU, aguardando que a aplicação do anfitrião envie uma atualização de firmware. Quando a atualização do firmware estiver concluída, a aplicação do anfitrião reinicia o dispositivo e, após a reenunciação, o dispositivo voltará ao seu funcionamento normal com o novo firmware.

Uma estrutura de dispositivo DFU será assim.

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

Neste exemplo, o descritor DFU não está associado a nenhuma outra classe. Tem um descritor de interface simples e nenhum outro ponto final ligado a ele. Existe um descritor funcional que descreve as especificidades das capacidades dfu do dispositivo.

A descrição das capacidades da DFU é a seguinte.

| Name             | Desvio  | Tamanho | tipo      | Descrição |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Campo de bits | Bit 3: o dispositivo executará uma sequência de desprendimento de autocarros quando receber um pedido de DFU_DETACH. O anfitrião não deve emitir um Reset USB. (bitWillDetach) 0 = no 1 = sim Bit 2: o dispositivo é capaz de comunicar via USB após a fase de Manifestação. (bitManifestationTolerant) 0 = não, deve ver reset de autocarro 1 = sim Bit 1: upload capaz (bitCanUpload) 0 = no 1 = sim Bit 0: download capaz (bitCanDnload) 0 = no 1 = sim  |
| wDetachTimeOut  | 3      | 2  | número    | Tempo, em milissegundos, que o dispositivo aguardará após a receção do pedido de DFU_DETACH. Se este tempo decorrer sem um reset USB, o dispositivo terminará a fase de reconfiguração e voltará ao funcionamento normal. Isto representa o tempo máximo que o dispositivo pode esperar (dependendo dos temporizadores, etc.). USBX define este valor para 1000 ms.  |
| wTransferSize  | 5      | 2  | número    | Número máximo de bytes que o dispositivo pode aceitar por operação de escrita de \- controlo. USBX define este valor para 64 bytes. |

A declaração da classe DFU é a seguinte:

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

A classe DFU precisa de trabalhar com uma aplicação de firmware de dispositivo específica para o alvo. Por isso, define várias chamadas de volta para ler e escrever blocos de firmware e para obter o estado da aplicação de atualização de firmware. A classe DFU também tem uma função de notificação de retorno para informar a aplicação quando ocorrer um início e fim de transferência do firmware.

Segue-se a descrição de um fluxo típico de aplicação DFU.

![Fluxo de aplicação DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

O grande desafio da classe DFU é obter a aplicação certa no anfitrião para realizar o download do firmware. Não existe nenhuma aplicação fornecida pela Microsoft ou pelo USB-IF. Existem alguns shareware e funcionam razoavelmente bem no Linux e em menor medida no Windows.

No Linux, pode-se usar du-utils para ser encontrado aqui: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) Muita informação sobre os usos dfu também pode ser encontrada neste link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

A implementação do Linux da DFU executa corretamente a sequência de reset entre o hospedeiro e o dispositivo e, portanto, o dispositivo não necessita de o fazer. Linux pode aceitar que os bmAttributes *bitWillDetach* sejam 0. As janelas do outro lado requerem que o dispositivo execute o reset.

No Windows, o registo USB deve ser capaz de associar o dispositivo USB ao seu PID/VID e à biblioteca USB que, por sua vez, será utilizado pela aplicação DFU. Isto pode ser feito facilmente com a utilidade gratuita Zadig que pode ser encontrada aqui: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .

Running Zadig pela primeira vez mostrará este ecrã:

![Correr Zadig pela primeira vez](./media/usbx-device-stack-supplemental/zadig.png)

A partir da lista de dispositivos, encontre o seu dispositivo e associe-o ao controlador de janelas libusb. Isto ligará o PID/VID do dispositivo à biblioteca USB do Windows utilizada pelos utilitários DFU.

Para operar o comando DFU, basta desempacotar os utilitários dfu zipped em um diretório, certificando-se de que o libusb dll também está presente no mesmo diretório. Os utilitários DFU devem ser executados a partir de uma caixa DOS na linha de comando.

Em primeiro lugar, digite o comando **dfu-util – l** para determinar se o dispositivo está listado. Caso contrário, corra zadig para se certificar de que o dispositivo está listado e associado à biblioteca USB. Deve ver um ecrã da seguinte forma:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

O próximo passo será preparar o ficheiro para ser descarregado. A classe USBX DFU não realiza qualquer verificação neste ficheiro e é agnóstica do seu formato interno. Este ficheiro de firmware é muito específico para o alvo, mas não para a DFU nem para a USBX.

Em seguida, o dfu-util pode ser instruído para enviar o ficheiro digitando o seguinte comando:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

O dfu-util deve exibir o processo de descarregamento do ficheiro até que o firmware tenha sido completamente descarregado.

## <a name="usb-device-pima-class-ptp-responder"></a>Classe PIMA do dispositivo USB (PTP Responder)

A classe PIMA do dispositivo USB permite que um sistema de anfitriões USB (Iniciador) se conecte a um

Dispositivo PIMA (Resonder) para transferir ficheiros de mídia. A Classe USBX Pima está em conformidade com a classe USB-IF PIMA 15740 também conhecida como classe PTP (para protocolo de transferência de imagens).

O lado do dispositivo USBX PIMA suporta as seguintes operações.

| Código de operação                                    | Valor | Descrição                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Obtenha o dispositivo suportado operações e eventos                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Abra uma sessão entre o anfitrião e o dispositivo                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Feche uma sessão entre o anfitrião e o dispositivo                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Devolve o ID de armazenamento para o dispositivo. USBX PIMA usa apenas um ID de armazenamento |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Devolva informações sobre o objeto de armazenamento, como a capacidade máxima e o espaço livre                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Devolva o número de objetos contidos no dispositivo de armazenamento                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Devolva uma série de pegas dos objetos no dispositivo de armazenamento                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Devolva informações sobre um objeto como o nome do objeto, a data de criação, data de modificação |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Devolver os dados relativos a um objeto específico                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Envie a miniatura se estiver disponível sobre um objeto                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Apagar um objeto nos meios de comunicação                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Enviar ao dispositivo informações sobre um objeto para a sua criação nos meios de comunicação                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Enviar dados para um objeto para o dispositivo                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Limpe os meios de comunicação do dispositivo                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Redefinir o dispositivo-alvo                                                                                   |

| Código de Operação                                         | Valor | Descrição |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Cancela a transação atual                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Um objeto foi adicionado aos meios de comunicação do dispositivo e pode ser recuperado pelo hospedeiro.. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Um objeto foi eliminado dos meios de dispositivo                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Um meio de comunicação foi adicionado ao dispositivo                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Um meio foi eliminado do dispositivo                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | As propriedades do dispositivo mudaram                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Uma informação de objeto mudou                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | Um dispositivo mudou                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | O dispositivo solicita a transferência de um objeto do anfitrião                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | O dispositivo informa que os meios de comunicação estão cheios                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | O dispositivo informa que foi reposto                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | A informação de armazenamento mudou no dispositivo                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | A captura está concluída                                                            |

A classe de dispositivo USBX PIMA utiliza um Fio TX para ouvir comandos PIMA do anfitrião.

Um comando PIMA é composto por um bloco de comando, um bloco de dados e uma fase de estado.

A função ux_device_class_pima_thread posta um pedido à pilha para receber um comando PIMA do lado anfitrião. O comando PIMA é descodificado e verificado para o conteúdo. Se o bloco de comando for válido, ramifica-se ao controlador de comando apropriado.

A maioria dos comandos PIMA só podem ser executados quando uma sessão foi aberta pelo anfitrião. A única exceção é o comando **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO.** Com a implementação usbx PIMA, apenas uma sessão pode ser aberta entre um Iniciador e um Responder a qualquer momento. Todas as transações dentro da sessão estão bloqueadas e nenhuma nova transação pode começar antes da anterior ter sido concluída.

As transações de PIMA são compostas por 3 fases, uma fase de comando, uma fase de dados opcional e uma fase de resposta. Se uma fase de dados estiver presente, só pode ser numa direção.

O Iniciador determina sempre o fluxo das operações do PIMA, mas o Respondente pode iniciar eventos de volta ao Iniciador para informar as alterações de estado que ocorreram durante uma sessão.

O diagrama seguinte mostra a transferência de um objeto de dados entre o hospedeiro e a classe de dispositivoS PIMA.

![Transações PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Inicialização da classe de dispositivoS PIMA

A classe de dispositivo PIMA necessita de alguns parâmetros fornecidos pela aplicação durante a inicialização.

Os seguintes parâmetros descrevem o dispositivo e as informações de armazenamento.

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

A classe PIMA também requer o registo de retorno de chamada no pedido para informar a aplicação de determinados eventos ou recuperar/armazenar dados de/para os meios de comunicação locais. As chamadas são as seguintes.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

O exemplo a seguir mostra como inicializar o lado cliente do PIMA. Este exemplo usa a Pictbridge como cliente da PIMA.

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

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

Adicionar um objeto e enviar o evento ao anfitrião

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa adicionar um objeto e informar o anfitrião.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima
- **object_handle:** Manuseie o objeto.

### <a name="example"></a>Exemplo

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Obtenção do número do objeto da aplicação

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de recuperar o número de objetos no sistema local e enviá-lo de volta para o hospedeiro.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima
- **object_number**: Endereço do número de objetos a devolver

### <a name="example"></a>Exemplo

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

Devolva a matriz do manípulo do objeto

### <a name="prototype"></a>Prototype

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de recuperar a matriz de pegas de objetos no sistema local e enviá-la de volta para o hospedeiro.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **object_handles_format_code**: Código de formato para as pegas
- **object_handles_association**: Código de associação de objetos
- **object_handle_array**: Endereço onde guardar as pegas
- **object_handles_max_number**: Número máximo de pegas na matriz

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

Devolva a informação do objeto

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de recuperar a matriz de pegas de objetos no sistema local e enviá-la de volta para o hospedeiro.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **object_handles**: Cabo do objeto
- **objeto**: Endereço do ponteiro do objeto

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

Devolva os dados do objeto

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de recuperar os dados do objeto no sistema local e enviá-los de volta para o hospedeiro.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima.
- **object_handle**: Cabo do objeto
- **object_buffer**: Endereço tampão de objeto
- **object_length_requested**: Comprimento dos dados do objeto solicitado pelo cliente à aplicação
- **object_atual_length**: Comprimento dos dados do objeto devolvido pela aplicação

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

Host envia a informação do objeto

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de receber a informação do objeto no sistema local para armazenamento futuro.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima
- **objeto**: Ponteiro para o objeto
- **object_handle**: Cabo do objeto

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

Host envia os dados do objeto

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de receber os dados do objeto no sistema local para armazenamento.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima
- **object_handle**: Cabo do objeto
- **fase**: fase da transferência (ativa ou completa)
- **object_buffer**: Endereço tampão de objeto
- **object_offset**: Endereço de dados
- **object_length**: Comprimento dos dados do objeto enviado por aplicação

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

Apagar um objeto local

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>Descrição

Esta função é chamada quando a classe PIMA precisa de apagar um objeto no armazenamento local.

### <a name="parameters"></a>Parâmetros

- **pima**: Ponteiro para a instância da classe pima
- **object_handle**: Cabo do objeto

### <a name="example"></a>Exemplo

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Classe de áudio do dispositivo USB

A classe de áudio do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo de áudio. Esta classe baseia-se na norma USB e na norma USB Audio Class 1.0 ou 2.0.

Uma estrutura do dispositivo de conformidade com o áudio USB tem de ser declarada pela pilha do dispositivo. Segue-se um exemplo de um altifalante Audio 2.0:

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

A classe Audio utiliza uma estrutura de dispositivo composto para interfaces de grupo (controlo e streaming). Como resultado, deve ter-se cuidado ao definir o descritor do dispositivo. O USBX conta com o descritor da IAD para saber internamente como ligar interfaces. O descritor DAI deve ser declarado antes das interfaces (uma interface AudioControl seguida de uma ou mais interfaces AudioStreaming) e conter a primeira interface da classe Áudio (a interface AudioControl) e quantas interfaces estão ligadas.

A forma como a classe de áudio funciona depende se o dispositivo está a enviar ou a receber áudio, mas ambos os casos utilizam um FIFO para armazenar tampões de fotogramas de áudio: se o dispositivo estiver a enviar áudio para o anfitrião, então a aplicação adiciona tampões de fotogramas de áudio ao FIFO que são posteriormente enviados ao anfitrião por USBX; se o dispositivo estiver a receber áudio do anfitrião, então o USBX adiciona os amortecedores de fotogramas de áudio recebidos do anfitrião ao FIFO, que são posteriormente lidos pela aplicação. Cada fluxo de áudio tem o seu próprio FIFO, e cada tampão de quadro de áudio é composto por múltiplas amostras.

A inicialização da classe Audio espera as seguintes partes.

1. A classe de áudio espera os seguintes parâmetros de streaming:

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

2. A classe de áudio espera os seguintes parâmetros de função.

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

   A chamada de pedido de controlo definida pela aplicação ***(ux_device_class_audio_control_process***; definida no exemplo anterior) é invocada quando a pilha recebe um pedido de controlo do anfitrião. Se o pedido for aceite e tratado (reconhecido ou parado) a chamada deve devolver o sucesso, caso contrário, o erro deve ser devolvido.

   O processo de pedido de controlo específico da classe é definido como uma chamada definida pela aplicação porque os pedidos de controlo são muito diferentes entre as versões USB Audio e uma grande parte do processo de pedido diz respeito à estrutura do dispositivo. A aplicação deve lidar corretamente com os pedidos para tornar o dispositivo funcional.

   Uma vez que para um dispositivo de áudio, volume, silenciamento e frequência de amostragem são pedidos de controlo comuns, as chamadas simples e definidas internamente para diferentes versões de áudio USB são introduzidas em secções posteriores para aplicações a utilizar. Consulte ***ux_device_class_audio10_control_process** _ e _ *_ux_device_class_audio_control_request_** para mais detalhes.

Na estrutura do dispositivo do dispositivo Audio, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado).

Quando um sistema de anfitrião USB descobre o dispositivo USB Audio e monta a classe de áudio, o dispositivo pode ser utilizado com qualquer leitor de áudio ou gravador (dependendo da estrutura). Consulte o Sistema Operativo do anfitrião para obter referência.

As APIs de classe áudio são definidas abaixo.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Entrada de fio para ler dados para a função Áudio.

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Descrição

Esta função é transmitida para o parâmetro de inicialização do fluxo de áudio se for desejado o áudio de leitura do anfitrião. Internamente, um fio é criado com esta função como função de entrada; o próprio fio lê dados áudio através do ponto final isocrono out na função Áudio.

### <a name="parameters"></a>Parâmetros

- **audio_stream**: Ponteiro para a instância de fluxo de áudio.

### <a name="example"></a>Exemplo

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Entrada de fio para escrever dados para a função Áudio

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Descrição

Esta função é transmitida para o parâmetro de inicialização do fluxo de áudio se desejar escrever áudio para o anfitrião. Internamente, um fio é criado com esta função como função de entrada; o próprio fio escreve dados áudio através do ponto final isocrono IN na função Áudio.

### <a name="parameters"></a>Parâmetros

- **audio_stream**: Ponteiro para a instância de fluxo de áudio.

### <a name="example"></a>Exemplo

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Obtenha uma instância de streaming específica para a função Áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Descrição

Esta função é usada para obter uma série de streaming de classe áudio.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância áudio
- **stream_index**: Índice de instância de fluxo baseado em 0
- **stream**: Ponteiro para tampão para armazenar o ponteiro de instância de fluxo de áudio

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Inicie a receção de dados áudio para o stream de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descrição

Esta função é utilizada para iniciar a leitura de dados áudio em streams de áudio.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Leia a amostra de 8 bits do fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Descrição

Esta função lê dados de amostra sonora de 8 bits a partir do fluxo especificado.

Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO. Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **tampão**: Ponteiro para o tampão para salvar o byte da amostra.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Leia a amostra de 16 bits do fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Descrição

Esta função lê dados de amostra sonora de 16 bits a partir do fluxo especificado.

Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO. Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **tampão**: Ponteiro para o tampão para salvar a amostra de 16 bits.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Leia a amostra de 24 bits do fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Descrição

Esta função lê dados de amostra sonora de 24 bits a partir do fluxo especificado.

Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO. Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **tampão**: Ponteiro para o tampão para salvar a amostra de 3 bytes.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Leia a amostra de 32 bits do fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Descrição

Esta função lê dados de amostra de áudio de 32 bits a partir do fluxo especificado.

Especificamente, lê os dados da amostra do atual tampão de quadro de áudio no FIFO. Ao ler a última amostra num quadro áudio, a moldura será automaticamente libertada para que possa ser usada para aceitar mais dados do anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **tampão**: Ponteiro para o tampão para guardar os dados de 4 bytes.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Obtenha acesso ao quadro áudio no fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Descrição

Esta função devolve o primeiro tampão de quadro de áudio e o seu comprimento no FIFO do stream especificado. Quando a aplicação é feita o processamento dos dados, ux_device_class_audio_read_frame_free devem ser utilizados para libertar o tampão de fotogramas no FIFO.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **frame_data**: Ponteiro para o ponteiro de dados para devolver o ponteiro de dados.
- **frame_length**: Ponteiro para tampão para guardar o comprimento da armação em número de bytes.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Livre um tampão de quadro de áudio no fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descrição

Esta função liberta o tampão de quadro de áudio na parte frontal do FIFO do stream especificado para que possa receber dados do anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Inicie a transmissão de dados áudio para o fluxo áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Descrição

Esta função é utilizada para começar a enviar dados áudio escritos para o FIFO na classe de áudio.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é nulo.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Escreva uma moldura áudio no fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Descrição

Esta função escreve uma moldura para o FIFO do stream de áudio. Os dados do quadro são copiados para o tampão disponível no FIFO para que possa ser enviado para o anfitrião.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **quadro**: Ponteiro para os dados de quadro.
- **frame_length** Comprimento do quadro em número de bytes.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Obtenha acesso ao quadro áudio no fluxo de áudio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Descrição

Esta função recupera o endereço do último tampão de quadro áudio do FIFO; também recupera o comprimento do tampão de quadro de áudio. Depois de a aplicação preencher o tampão de quadro áudio com os dados pretendidos, ***ux_device_class_audio_write_frame_commit*** devem ser utilizados para adicionar/comprometer o tampão de fotogramas ao FIFO.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **frame_data**: Ponteiro para o ponteiro de dados de quadro para devolver o ponteiro de dados de quadro dentro
- **frame_length** Ponteiro para o tampão para guardar o comprimento do quadro em número de bytes .

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO está cheio.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Comprometa um tampão de quadro de áudio no fluxo de áudio.

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Descrição

Esta função adiciona/compromete o último tampão de fotogramas de áudio ao FIFO para que o tampão esteja pronto para ser transferido para o hospedeiro; note que o último tampão de quadro de áudio deveria ter sido preenchido através de ux_device_class_write_frame_get.

### <a name="parameters"></a>Parâmetros

- **stream**: Ponteiro para a instância de fluxo de áudio.
- **comprimento**: Número de bytes prontos no tampão.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A interface está em baixo.
- **UX_BUFFER_OVERFLOW** (0x5d) tampão FIFO é fssull.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Processar pedidos de controlo USB Audio 1.0

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Descrição

Esta função gere os pedidos básicos enviados pelo anfitrião no ponto final de controlo com um tipo específico USB Audio 1.0.

As funcionalidades áudio 1.0 dos pedidos de volume e de silenciamento são processadas na função. Ao processar os pedidos, os dados pré-definidos passados pelo último parâmetro (grupo) são utilizados para responder a pedidos e alterações no controlo da loja.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância áudio.
- **transferência**: Ponteiro para a instância de pedido de transferência.
- **grupo**: Grupo de dados para processo de pedido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

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

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

Processar pedidos de controlo USB Audio 1.0

### <a name="prototype"></a>Prototype
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Descrição

Esta função gere os pedidos básicos enviados pelo anfitrião no ponto final de controlo com um tipo específico USB Audio 2.0.

A taxa de amostragem áudio 2.0 (frequência fixa única assumida), as características dos pedidos de volume e de silenciamento são processadas na função. Ao processar os pedidos, os dados pré-definidos passados pelo último parâmetro (grupo) são utilizados para responder a pedidos e alterações no controlo da loja.

### <a name="parameters"></a>Parâmetros

- **áudio**: Ponteiro para a instância áudio.
- **transferência**: Ponteiro para a instância de pedido de transferência.
- **grupo**: Grupo de dados para processo de pedido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

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
