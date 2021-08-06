---
title: Capítulo 5 - Considerações da classe do dispositivo USBX
description: Saiba mais sobre as considerações da Classe dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: ea348d94e83863c0e2652df29f92d952f2242661
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178022"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Capítulo 5 - Considerações da classe do dispositivo USBX

## <a name="device-class-registration"></a>Registo da classe do dispositivo

Cada classe de dispositivo segue o mesmo princípio para o registo. Uma estrutura que contenha parâmetros de classe específicos é passada para a função de inicialização da classe.

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

Cada classe pode registar-se, opcionalmente, numa função de retorno quando uma instância da classe é ativada. O retorno é então chamado pela pilha do dispositivo para informar a aplicação de que um caso foi criado.

A aplicação teria no seu corpo as 2 funções de ativação e desativação, como mostra o exemplo seguinte.

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

Não é aconselhável fazer nada dentro destas funções, mas memorizar a instância da classe e sincronizar com o resto da aplicação.

## <a name="general-considerations-for-bulk-transfer"></a>Considerações Gerais para transferência a granel

De acordo com a especificação USB 2.0, um ponto final deve sempre transmitir cargas de dados com um campo de dados inferior ou igual ao valor reportado wMaxPacketSize do ponto final. O tamanho de um pacote de dados é limitado ao bMaxPacketSize. A transferência pode ser concluída com os seguintes casos
1. O ponto final transferiu exatamente a quantidade de dados esperados
2. Quando um dispositivo ou ponto final do anfitrião reveste um pacote com tamanho inferior ao tamanho máximo do pacote (wMaxPacketSize). Este pacote curto indica que já não há mais pacote de dados e a transferência está completa ou quando os pacotes de dados a transmitir são todos iguais ao wMaxPacketSize, então o fim da transferência não pode ser determinado. Para a conclusão da transferência, um pacote de comprimento zero (ZLP) deve ser enviado pacotes curtos e pacotes de comprimento zero significam o fim de uma transferência de dados a granel. As considerações acima referidas aplicam-se às API de transferência de dados a granel brutos, por exemplo, ux_device_class_cdc_acm_read().

## <a name="usb-device-storage-class"></a>Classe Armazenamento de dispositivo USB

A classe de armazenamento de dispositivos USB permite que um dispositivo de armazenamento incorporado no sistema seja tornado visível para um hospedeiro USB.

A classe de armazenamento de dispositivos USB não fornece, por si só, uma solução de armazenamento. Apenas aceita e interpreta pedidos scsi vindos do anfitrião. Quando um destes pedidos é um comando de leitura ou de escrita, invoca uma chamada pré-definida para um manipulador de dispositivos de armazenamento real, como um controlador de dispositivo ATA ou um controlador de dispositivo Flash.

Ao inicializar a classe de armazenamento do dispositivo, é dada uma estrutura de ponteiro à classe que contém todas as informações necessárias. Um exemplo é dado abaixo.

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

Neste exemplo, as cordas de armazenamento do controlador são personalizadas atribuindo ponteiros de corda ao parâmetro correspondente. Se um dos ponteiros de corda for deixado para UX_NULL, é utilizada a cadeia Azure RTOS padrão.

Neste exemplo, o último endereço de bloco da unidade ou LBA é dado, bem como o tamanho do sector lógico. A LBA é o número de sectores disponíveis nos meios de comunicação social –1. O comprimento do bloco é definido para 512 em meios de armazenamento regulares. Pode ser definido para 2048 para unidades óticas.

A aplicação precisa de passar três ponteiros de função de retorno para permitir que a classe de armazenamento leia, escreva e obtenha o estado para os meios de comunicação.

Os protótipos para as funções de leitura e escrita são mostrados no exemplo abaixo.

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

Em que:

- *armazenamento* é o exemplo da classe de armazenamento.
- *lun* é o LUN o comando é direcionado para.
- *data_pointer* é o endereço do tampão a ser usado para ler ou escrever.
- *number_blocks* é o número de sectores para ler/escrever.
- *LBA* é o endereço do sector para ler.
- *media_status* deve ser preenchido exatamente como o valor de retorno do estado de retorno dos meios de comunicação.

O valor de retorno pode ter o valor UX_SUCCESS ou UX_ERROR indicando uma operação bem sucedida ou mal sucedida. Estas operações não necessitam de devolver quaisquer outros códigos de erro. Se houver um erro em qualquer operação, a classe de armazenamento invocará a função de chamada de estado de volta.

Esta função tem o seguinte protótipo.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

O parâmetro de chamada media_id não é atualmente utilizado e deve ser sempre 0. No futuro, poderá ser utilizado para distinguir vários dispositivos de armazenamento ou dispositivos de armazenamento com vários SCSI LUNs. Esta versão da classe de armazenamento não suporta múltiplas instâncias da classe de armazenamento ou dispositivos de armazenamento com vários SCSI LUNs.

O valor de retorno é um código de erro SCSI que pode ter o seguinte formato.

- **Bits 0-7** Sense_key
- **Bits 8-15** Código de Sentido Adicional
- **Bits 16-23** Qualificação adicional do Código de Sentido

A tabela a seguir fornece as possíveis combinações Sense/ASC/ASCQ.

| Chave do sentido | ASC | ASCQ | Description                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | SEM SENTIDO                                          |
| 01        | 17  | 01   | DADOS RECUPERADOS COM RETRÓSCA                       |
| 01        | 18  | 00   | DADOS RECUPERADOS COM ECC                           |
| 02        | 04  | 01   | UNIDADE LÓGICA NÃO PRONTA - FICANDO PRONTA          |
| 02        | 04  | 02   | UNIDADE LÓGICA NÃO PRONTA - INICIALIZAÇÃO NECESSÁRIA |
| 02        | 04  | 04   | UNIDADE LÓGICA NÃO PRONTA - FORMATO EM CURSO       |
| 02        | 04  | FF   | UNIDADE LÓGICA NÃO ESTÁ PRONTA - DISPOSITIVO ESTÁ OCUPADO          |
| 02        | 06  | 00   | NENHUMA POSIÇÃO DE REFERÊNCIA ENCONTRADA                       |
| 02        | 08  | 00   | FALHA DE COMUNICAÇÃO DA UNIDADE LÓGICA                |
| 02        | 08  | 01   | TEMPO DE TEMPO DE COMUNICAÇÃO DA UNIDADE LÓGICA               |
| 02        | 08  | 80   | FALHA DE COMUNICAÇÃO DA UNIDADE LÓGICA                |
| 02        | 3A  | 00   | MEIO NÃO PRESENTE                                |
| 02        | 54  | 00   | USB PARA HOSPEDAR FALHA NA INTERFACE DO SISTEMA              |
| 02        | 80  | 00   | RECURSOS INSUFICIENTES                            |
| 02        | FF  | FF   | ERRO DESCONHECIDO                                     |
| 03        | 02  | 00   | SEM PROCURAR COMPLETO                                  |
| 03        | 03  | 00   | CULPA DE ESCREVER                                       |
| 03        | 10  | 00   | Erro de ID CRC                                      |
| 03        | 11  | 00   | ERRO DE LEITURA NÃO DESCOBERTO                            |
| 03        | 12  | 00   | MARCA DE ENDEREÇO NÃO ENCONTRADA PARA CAMPO DE ID               |
| 03        | 13  | 00   | MARCA DE ENDEREÇO NÃO ENCONTRADA PARA CAMPO DE DADOS             |
| 03        | 14  | 00   | ENTIDADE GRAVADA NÃO ENCONTRADA                         |
| 03        | 30  | 01   | NÃO PODE LER MEIO - FORMATO DESCONHECIDO               |
| 03        | 31  | 01   | O COMANDO DO FORMATO FALHOU                             |
| 04        | 40  | NN   | FALHA DE DIAGNÓSTICO NO COMPONENTE NN (80H-FFH)      |
| 05        | 1A  | 00   | ERRO DE COMPRIMENTO DA LISTA DE PARÂMETROS                       |
| 05        | 20  | 00   | CÓDIGO DE FUNCIONAMENTO DO COMANDO INVÁLIDO                    |
| 05        | 21  | 00   | ENDEREÇO DE BLOCO LÓGICO FORA DO ALCANCE                |
| 05        | 24  | 00   | CAMPO INVÁLIDO NO PACOTE DE COMANDO                   |
| 05        | 25  | 00   | UNIDADE LÓGICA NÃO SUPORTADA                        |
| 05        | 26  | 00   | CAMPO INVÁLIDO NA LISTA DE PARÂMETROS                   |
| 05        | 26  | 01   | PARÂMETRO NÃO SUPORTADO                           |
| 05        | 26  | 02   | VALOR DO PARÂMETRO INVÁLIDO                           |
| 05        | 39  | 00   | PARÂMETROS DE POUPANÇA NÃO SUPORTE                     |
| 06        | 28  | 00   | NÃO PRONTO PARA A TRANSIÇÃO PRONTA - MEDIA ALTERADO     |
| 06        | 29  | 00   | POTÊNCIA NO RESET OU RESET DO DISPOSITIVO DE AUTOCARRO OCORREU       |
| 06        | 2F  | 00   | COMANDOS APURADOS POR OUTRO INICIADOR             |
| 07        | 27  | 00   | ESCREVER MEIOS PROTEGIDOS                             |
| 0B        | 4E  | 00   | COMANDO SOBREPOSTO TENTADO                      |

Existem duas chamadas adicionais e opcionais que a aplicação pode implementar; um é para responder a um comando **GET_STATUS_NOTIFICATION** e o outro é para responder ao **comando SYNCHRONIZE_CACHE.**

Se a aplicação quiser lidar com o comando GET_STATUS_NOTIFICATION do anfitrião, deverá implementar uma chamada com o seguinte protótipo.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

Em que:

- *armazenamento* é o exemplo da classe de armazenamento.
- *media_id* não é atualmente utilizada. notification_class especifica a classe de notificação.
- *media_notification* deve ser definido pelo pedido ao tampão que contém a resposta para a notificação.
- *media_notification_length* deve ser definido pela aplicação para conter o comprimento do tampão de resposta.

O valor de retorno indica se o comando foi ou não bem sucedido – deve ser **UX_SUCCESS** ou **UX_ERROR**.

Se a aplicação não implementar esta chamada, então ao receber o comando **GET_STATUS_NOTIFICATION,** a USBX notificará o anfitrião de que o comando não é implementado.

O **comando SYNCHRONIZE_CACHE** deve ser manuseado se a aplicação estiver a utilizar uma cache para escritas do anfitrião. Um anfitrião pode enviar este comando se souber que o dispositivo de armazenamento está prestes a ser desligado, por exemplo, em Windows, se clicar corretamente num ícone de pen na barra de ferramentas e selecionar "Ejetar o \[ nome do dispositivo de \] armazenamento", Windows emitirá o comando **SYNCHRONIZE_CACHE** para esse dispositivo.

Se a aplicação quiser lidar com o comando **GET_STATUS_NOTIFICATION** do anfitrião, deverá implementar uma chamada com o seguinte protótipo.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Em que:

- *armazenamento* é o exemplo da classe de armazenamento.
- o parâmetro *lun* especifica a que LUN o comando é dirigido.
- *number_blocks* especifica o número de blocos para sincronizar.
- *LBA* é o endereço do sector do primeiro bloco para sincronizar.
- *media_status* deve ser preenchido exatamente como o valor de retorno do estado de retorno dos meios de comunicação.

O valor de retorno indica se o comando foi ou não bem sucedido – deve ser **UX_SUCCESS** ou **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Vários SCSI LUN

A classe de armazenamento de dispositivos USBX suporta vários LUNs. É, portanto, possível criar um dispositivo de armazenamento que atue como UM CD-ROM e um disco Flash ao mesmo tempo. Neste caso, a inicialização seria ligeiramente diferente. Aqui está um exemplo para um Flash Disk e CD-ROM:

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>Classe CDC-ACM do dispositivo USB

A classe CDC-ACM do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como dispositivo de série. Esta classe baseia-se na norma USB e é um subconjunto da norma CDC.

Uma estrutura do dispositivo em conformidade CDC-ACM tem de ser declarada pela pilha do dispositivo. Um exemplo é encontrado aqui em baixo.

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

A classe CDC-ACM utiliza uma estrutura de dispositivo composto para interfaces de grupo (controlo e dados). Como resultado, deve ter-se cuidado ao definir o descritor do dispositivo. O USBX conta com o descritor da IAD para saber internamente como ligar interfaces. O descritor da IAD deve ser declarado antes das interfaces e conter a primeira interface da classe CDC-ACM e quantas interfaces estão anexadas.

A classe CDC-ACM também usa um descritor funcional da união que desempenha a mesma função que o descritor mais recente da IAD. Embora um descritor funcional da União deva ser declarado por razões históricas e compatibilidade com o lado anfitrião, este não é utilizado pela USBX.

A inicialização da classe CDC-ACM espera os seguintes parâmetros.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

Os 2 parâmetros definidos são os ponteiros de retorno nas aplicações do utilizador que serão chamados quando a stack ativar ou desativar esta classe.

O terceiro parâmetro definido é um ponteiro de retorno para a aplicação do utilizador que será chamado quando houver codificação de linha ou mudança de parâmetro de linha. Por exemplo, quando há pedido do anfitrião para alterar o estado DTR para **TRUE,** a chamada é invocada, na sua aplicação o utilizador pode verificar os estados da linha através da função IOCTL para o anfitrião kow está pronto para comunicação.

O CDC-ACM baseia-se numa norma USB-IF e é automaticamente reconhecido pelos sistemas operativos MACOs e Linux. Nas plataformas Windows, esta classe requer um ficheiro .inf para Windows versão antes de 10. Windows 10 não requer ficheiros .inf. Fornecemos um modelo para a classe CDC-ACM e pode ser encontrado no ***diretório usbx_windows_host_files.*** Para uma versão mais recente de Windows o ficheiro CDC_ACM_Template_Win7_64bit.inf deve ser usado (exceto Win10). Este ficheiro precisa de ser modificado para refletir o PID/VID utilizado pelo dispositivo. O PID/VID será específico para o cliente final quando a empresa e o produto estiverem registados no USB-IF. No ficheiro inf, os campos a modificar estão localizados aqui.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

Na estrutura do dispositivo do dispositivo CDC-ACM, o PID/VID é armazenado no descritor do dispositivo (ver descritor do dispositivo acima declarado).

Quando um sistema de anfitrião USB descobrir o dispositivo USB CDC-ACM, montará uma classe de série e o dispositivo pode ser utilizado com qualquer programa de terminal de série. Consulte o Sistema Operativo do anfitrião para obter referência.

As funções API da classe CDC-ACM são definidas abaixo.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Execute o IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa executar várias chamadas ioctl para a interface cdc acm

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: Função ioctl a desempenhar.
- **parâmetro**: Ponteiro para um parâmetro específico da chamada do ioctl.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Erro da função

### <a name="example"></a>Exemplo

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Funções ioctl:

| Função                                        | Valor |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

Executar codificação de linha de conjunto IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de definir os parâmetros de codificação da linha.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Devolver Valor

**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

Executar codificação de linha DO IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de obter os parâmetros de codificação da linha.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

Executar o Estado de Linha DO IOCTL na interface CDC-ACM

## <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de obter os parâmetros do Estado da Linha.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

Execute o Estado da linha de fixação do IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de obter os parâmetros do Estado da Linha

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parâmetro**: Ponteiro para uma estrutura de parâmetro de linha:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Executar TUBO ABORTO IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de abortar um tubo. Por exemplo, para abortar uma escrita em curso, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT deve ser passado como parâmetro.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parâmetro**: A direção do tubo:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Direção do tubo inválido.

### <a name="example"></a>Exemplo

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Executar início de transmissão IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação quer utilizar a transmissão com retorno.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parâmetro**: Ponteiro para a estrutura do parâmetro de transmissão inicial:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) A transmissão já começou.
- **UX_MEMORY_INSUFFICIENT** (0x12) Uma atribuição de memória falhou.

### <a name="example"></a>Exemplo

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

Execute a paragem de transmissão do IOCTL na interface CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação quer parar de usar a transmissão com retorno.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parâmetro**: Não utilizado

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Nenhuma transmissão em curso.

### <a name="example"></a>Exemplo

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Leia do tubo CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de ser lida a partir do tubo de dados OUT (OUT do anfitrião, IN do dispositivo). Está a bloquear.

> [!Note]
> Esta função lê dados em massa brutos do hospedeiro, pelo que continua pendente até que o tampão esteja cheio ou o anfitrião termine a transferência por um pacote curto (incluindo pacote de comprimento zero). Para mais detalhes, consulte a secção [**Considerações Gerais para transferência a granel**](#general-considerations-for-bulk-transfer).

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **tampão**: Endereço tampão onde os dados serão armazenados.
- **requested_length:** O comprimento máximo que esperamos.
- **atual_length:** O comprimento devolvido ao tampão.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo. O dispositivo deve ter sido desligado enquanto a transferência estava pendente.

### <a name="example"></a>Exemplo

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Escreva para um tubo CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de escrever para o tubo de dados IN (IN do anfitrião, OUT do dispositivo). Está a bloquear.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **tampão**: Endereço tampão onde os dados são armazenados.
- **requested_length:** O comprimento do tampão para escrever.
- **atual_length**: O comprimento devolvido ao tampão após a escrita é executado.

### <a name="return-value"></a>Devolver Valor
- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo. O dispositivo deve ter sido desligado enquanto a transferência estava pendente.

### <a name="example"></a>Exemplo

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Escrever para um tubo CDC-ACM com retorno

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa de escrever para o tubo de dados IN (IN do anfitrião, OUT do dispositivo). Esta função não bloqueia e a conclusão será feita através de um revés definido em UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parâmetros

- **cdc_acm**: Ponte para a instância da classe CDC.
- **tampão**: Endereço tampão onde os dados são armazenados.
- **requested_length:** O comprimento do tampão para escrever.
- **atual_length**: O comprimento devolvido ao tampão após a escrita é realizado

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** dispositivo (0x51) já não se encontra no estado configurado.
- **UX_TRANSFER_NO_ANSWER** (0x22) Nenhuma resposta do dispositivo. O dispositivo deve ter sido desligado enquanto a transferência estava pendente.

### <a name="example"></a>Exemplo

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>Classe CDC-ECM do dispositivo USB

A classe CDC-ECM do dispositivo USB permite que um sistema de anfitriões USB comunique com o dispositivo como um dispositivo ethernet. Esta classe baseia-se na norma USB e é um subconjunto da norma CDC.

Uma estrutura do dispositivo em conformidade CDC-ACM tem de ser declarada pela pilha do dispositivo. Um exemplo é encontrado aqui em baixo.

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

A classe CDC-ECM utiliza uma abordagem de descritor de dispositivos muito semelhante ao CDC-ACM e também requer um descritor de IAD. Consulte a classe CDC-ACM para definição.

Além da estrutura regular do dispositivo, o CDC-ECM requer descritores especiais de cordas. Um exemplo é dado abaixo.

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

O descritor de cordas de endereço MAC é utilizado pela classe CDC-ECM para responder às perguntas do anfitrião sobre o endereço MAC a que o dispositivo está a responder no protocolo TCP/IP. Pode ser definido para a escolha do dispositivo, mas deve ser definido aqui.

A inicialização da classe CDC-ECM é a seguinte.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

A inicialização desta classe espera a mesma função de retorno para ativação e desativação, embora aqui como um exercício eles estão definidos para NU PARA que não seja realizada nenhuma chamada.

Os próximos parâmetros são para a definição dos IDs do nó. 2 Os nós são necessários para o CDC-ECM, um nó local e um nó remoto. O nó local especifica o endereço MAC do dispositivo, enquanto o nó remoto especifica o endereço MAC do anfitrião. O nó remoto deve ser o mesmo que o declarado no descritor de cordas de estrutura do dispositivo.

A classe CDC-ECM tem APIs incorporados para transferir dados em ambos os sentidos, mas estão escondidos à aplicação, uma vez que a aplicação do utilizador comunicará com o dispositivo USB Ethernet através do NetX.

A classe USBX CDC-ECM está intimamente ligada à pilha de rede Azure RTOS NetX. Uma aplicação utilizando a classe NetX e USBX CDC-ECM irá ativar a pilha de rede NetX da forma habitual, mas além disso precisa de ativar a pilha de rede USB da seguinte forma.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

A pilha de rede USB precisa de ser ativada apenas uma vez e não é específica da CDCECM, mas é exigida por qualquer classe USB que exija serviços NetX.

A classe CDC-ECM será reconhecida pelos anfitriões MAC OS e Linux. Mas não há nenhum condutor fornecido pela Microsoft Windows para reconhecer o CDC-ECM de forma nativa. Alguns produtos comerciais existem para Windows plataformas e fornecem o seu próprio ficheiro .inf. Este ficheiro terá de ser modificado da mesma forma que o modelo inf CDC-ACM para corresponder ao PID/VID do dispositivo de rede USB.

## <a name="usb-device-hid-class"></a>Classe HID dispositivo USB

A classe HID do dispositivo USB permite que um sistema de anfitrião USB se conecte a um dispositivo HID com capacidades específicas do cliente HID.

A classe do dispositivo USBX HID é relativamente simples em comparação com o lado do hospedeiro. Está intimamente ligado ao comportamento do dispositivo e do seu descritor HID.

Qualquer cliente HID requer primeiro definir uma estrutura do dispositivo HID como o exemplo abaixo.

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

A estrutura HID contém um descritor de interface que descreve a classe HID e a subclasse do dispositivo HID. A interface HID pode ser uma classe autónoma ou parte de um dispositivo composto.

Atualmente, a classe USBX HID não suporta múltiplos IDs de relatório, uma vez que a maioria das aplicações requer apenas um ID (ID zero). Se várias IDs de relatório forem uma funcionalidade que lhe interessa, contacte-nos.

A inicialização da classe HID é a seguinte, usando um teclado USB como exemplo.

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

A aplicação tem de passar para a classe HID um descritor de relatório HID e seu comprimento. O descritor de relatórios é uma coleção de itens que descrevem o dispositivo. Para obter mais informações sobre a gramática HID consulte a especificação da classe USB HID.

Além do descritor de relatórios, a aplicação passa uma chamada de volta quando um evento HID acontece.

A classe USBX HID suporta os seguintes comandos HID padrão do anfitrião.

| Nome de comando                             | Valor | Descrição                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Obtenha um relatório do dispositivo                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Obtenha a frequência ociosa do ponto final de interrupção |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Obter o protocolo em funcionamento no dispositivo           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Desa estação de relatório para o dispositivo                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | Desaponte a frequência ociosa do ponto final de interrupção |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Obter o protocolo em funcionamento no dispositivo           |

O relatório Get and set são os comandos mais utilizados pela HID para transferir dados de um lado para o outro entre o anfitrião e o dispositivo. Mais frequentemente, o hospedeiro envia dados sobre o ponto final de controlo, mas pode receber dados quer no ponto final de interrupção, quer emitindo um comando GET_REPORT para obter os dados no ponto final de controlo.

A classe HID pode enviar dados de volta ao anfitrião no ponto de terminação de interrupção utilizando a função ux_device_class_hid_event_set.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Definição de um evento para a classe HID

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

Esta função é chamada quando uma aplicação precisa enviar um evento HID de volta para o anfitrião. A função não é bloquear, apenas coloca o relatório numa fila circular e regressa à aplicação.

### <a name="parameters"></a>Parâmetros

- **escondido:** Ponteiro para a instância de classe escondida.
- **hid_event**: Ponteiro para a estrutura do evento escondido.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Erro nenhum espaço disponível na fila circular.

### <a name="example"></a>Exemplo

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

A chamada definida na inicialização da classe HID realiza o oposto de enviar um evento. Obtém-se como entrada o evento enviado pelo anfitrião. O protótipo da chamada é o seguinte.

### <a name="hid_callback"></a>hid_callback

Obtenção de um evento da classe HID

### <a name="prototype"></a>Prototype

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Description

Esta função é chamada quando o anfitrião envia um relatório HID para a aplicação.

### <a name="parameters"></a>Parâmetros

- **escondido:** Ponteiro para a instância de classe escondida.
- **hid_event**: Ponteiro para a estrutura do evento escondido.

### <a name="example"></a>Exemplo

O exemplo a seguir mostra como interpretar um evento para um teclado HID:

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
