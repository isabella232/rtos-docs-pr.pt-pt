---
title: Capítulo 2 - Instalação de pilha de dispositivos USBX Azure RTOS
description: Saiba como instalar a pilha de dispositivos USBX Azure RTOS, bem como as considerações importantes do anfitrião que precisa de pensar antes de instalar.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549781"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Capítulo 2 - Instalação de pilha de dispositivos USBX Azure RTOS

## <a name="host-considerations"></a>Considerações de Anfitrião

### <a name="computer-type"></a>Tipo de computador

O desenvolvimento incorporado é geralmente realizado em computadores anfitriões Windows PC ou Unix. Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.

### <a name="download-interfaces"></a>Baixar Interfaces

Normalmente, o download do alvo é feito através de uma interface de série RS-232, embora interfaces paralelas, USB e Ethernet estejam a tornar-se mais populares. Consulte a documentação da ferramenta de desenvolvimento para obter as opções disponíveis.

### <a name="debugging-tools"></a>Ferramentas de depurar

Depurar é feito normalmente sobre o mesmo link que o download de imagem do programa. Existe uma variedade de depuradores, desde pequenos programas de monitor que correm no alvo através do Background Debug Monitor (BDM) e In-Circuit ferramentas emuladoras (ICE). A ferramenta ICE fornece a depuragem mais robusta do hardware alvo real.

### <a name="required-hard-disk-space"></a>Espaço de disco rígido necessário

O código-fonte do USBX é entregue em formato ASCII e requer aproximadamente 500 KBytes de espaço no disco rígido do computador anfitrião.

### <a name="target-considerations"></a>Considerações-alvo

USBX requer entre 24 KBytes e 64 KBytes de Read Only Memory (ROM) no alvo no modo anfitrião. A quantidade de memória necessária depende do tipo de controlador utilizado e das classes USB ligadas ao USBX. Outros 32 KBytes da Memória de Acesso Aleatório (RAM) do alvo são necessários para estruturas de dados globais USBX e piscina de memória. Este conjunto de memórias também pode ser ajustado dependendo do número esperado de dispositivos no USB e do tipo de controlador USB. O lado do dispositivo USBX requer aproximadamente 10-12 K de ROM dependendo do tipo de controlador do dispositivo. O uso da memória RAM depende do tipo de classe emulsionada pelo dispositivo.

A USBX também conta com semáforos ThreadX, mutexes e fios para proteção de múltiplos fios, e suspensão de I/O e processamento periódico para monitorizar a topologia do autocarro USB.

### <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS USBX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/usbx/> .

Segue-se uma lista de vários ficheiros importantes no repositório.

* ***ux_api.h:*** Este ficheiro de cabeçalho C contém todos os equacionares do sistema, estruturas de dados e protótipos de serviço.
* ***ux_port.h:*** Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas da ferramenta de desenvolvimento.
* ***ux.lib***: Esta é a versão binária da biblioteca USBX C. É distribuído com o pacote padrão.
* ***demo_usbx.c***: O ficheiro C que contém uma demonstração USBX simples

Todos os ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Unix.

## <a name="usbx-installation"></a>Instalação USBX

O USBX é instalado através da clonagem do repositório GitHub à sua máquina local. O seguinte é a sintaxe típica para criar um clone do repositório USBX no seu PC:

```c
    git clone https://github.com/azure-rtos/usbx
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal do GitHub.

Também encontrará instruções para a construção da biblioteca USBX na primeira página do repositório online.

As seguintes instruções gerais aplicam-se a praticamente qualquer instalação:

1. Utilize o mesmo diretório em que instalou anteriormente o ThreadX no disco rígido do hospedeiro. Todos os nomes USBX são únicos e não interferirão com a instalação USBX anterior.
1. Adicione uma chamada a ***ux_system_initialize** _ no ou perto do início de _*_tx_application_define_**. É aqui que os recursos USBX são inicializados.
1. Adicione uma chamada para ***ux_device_stack_initialize*.**
1. Adicione uma ou mais chamadas para inicializar as classes USBX necessárias (aulas de anfitrião e/ou dispositivos)
1. Adicione uma ou mais chamadas para inicializar o controlador do dispositivo disponível no sistema.
1. Pode ser necessário modificar o ficheiro tx_low_level_initialize.c para adicionar inicialização de hardware de baixo nível e interromper o encaminhamento do vetor. Isto é específico da plataforma de hardware e não será discutido aqui.|
1. Compilar o código-fonte da aplicação e ligar-se às bibliotecas de tempo de funcionamento USBX e ThreadX (FileX e/ou Netx também podem ser necessários se a classe de armazenamento USB e/ou as classes de rede USB forem compiladas em), ux.a (ou ux.lib) e tx.a (ou tx.lib). O resultado pode ser descarregado para o alvo e executado!

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção da biblioteca USBX. Todas as opções estão localizadas no ***ux_user.h***.

A lista abaixo detalha cada opção de configuração.

| Opção de configuração &nbsp; | Descrição |
| --- | --- |
| **UX_PERIODIC_RATE** | Este valor representa quantos tiques por segundo para uma plataforma de hardware específica. O padrão é 1000 indicando 1 carrapato por milissegundo. |
| **UX_THREAD_STACK_SIZE** | Este valor é o tamanho da stack in bytes para os fios USBX. Pode ser normalmente 1024 bytes ou bytes de 2048 dependendo do processador utilizado e do controlador anfitrião. |
| **UX_THREAD_PRIORITY_ENUM** | Este é o valor prioritário da ThreadX para os fios de enumeração USBX que monitorizam a topologia do autocarro. |
| **UX_THREAD_PRIORITY_CLASS** | Este é o valor prioritário threadX para os fios USBX padrão. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Este é o valor prioritário threadX para a classe de teclado USBX HID. |
| **UX_THREAD_PRIORITY_DCD** | Este é o valor prioritário threadX para o fio do controlador do dispositivo. |
| **UX_NO_TIME_SLICE** | Este valor define realmente a fatia de tempo que será usada para fios. Por exemplo, se definido para 0, a porta-alvo ThreadX não utiliza fatias de tempo. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Este é o número máximo de classes USBX que podem ser registadas através de ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Este valor representa o número atual de unidades lógicas SCSI representadas no controlador da classe de armazenamento do dispositivo. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | Se definido, a classe de armazenamento irá lidar com comandos multimédia (MMC) ou seja, DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Este valor representa o número de pacotes NetX na piscina de pacotes da classe CDC-ECM. O padrão é 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Este valor representa o número máximo de bytes recebidos num ponto final de controlo na pilha do dispositivo. O padrão é de 256 bytes, mas pode ser reduzido em ambientes de restrição de memória. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Este valor representa o comprimento máximo em bytes de um relatório HID. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Este valor representa o número máximo de relatórios HID que podem ser feito em fila imediatamente. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Este valor representa o número máximo de bytes recebidos num ponto final a granel na pilha do dispositivo. O padrão é 4096 bytes, mas pode ser reduzido em ambientes de restrição de memória. |

## <a name="source-code-tree"></a>Árvore-código fonte

Os ficheiros USBX são fornecidos em vários diretórios.

![Árvore-código fonte](media/usbx-device-stack/source-code-tree.png)

A fim de tornar os ficheiros reconhecíveis pelos seus nomes, foi adotada a seguinte convenção:

| Nome do sufixo de arquivo  | Descrição do arquivo                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | usbx host stack ficheiros de núcleo                |
| ux_host_class   | usbx host stack classes arquivos             |
| ux_hcd           | usbx host stack controladore de controladores   |
| ux_device_stack | usbx dispositivo stack ficheiros de núcleo              |
| ux_device_class | usbx pilha de ficheiros classes           |
| ux_dcd           | usbx dispositivo stack controladore de controladores |
| ux_otg           | usbx otg controladore ficheiros relacionados com o controlador  |
| ux_pictbridge    | usbx pictbridge arquivos                     |
| ux_utility       | funções de utilidade usbx                    |
| demo_usbx        | ficheiros de demonstração para USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicialização dos recursos USBX

A USBX tem o seu próprio gestor de memória. A memória precisa de ser atribuída ao USBX antes da inicialação do lado do anfitrião ou do dispositivo do USBX. O gestor de memória USBX pode acomodar sistemas onde a memória pode ser em cache.

A seguinte função inicializa os recursos de memória USBX com 128 K de memória regular e nenhuma piscina separada para a memória segura da cache:

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

O protótipo para a ux_system_initialize é o seguinte:

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

Parâmetros de entrada:

| Parâmetro                          | Descrição                             |
| ---------------------------------- | --------------------------------------- |
| VOID *regular_memory_pool_start    | Início da piscina de memória regular    |
| regular_memory_size da ULONG          | Tamanho da piscina de memória regular         |
| VOID *cache_safe_memory_pool_start | Início da piscina de memória segura da cache |
| cache_safe_memory_size da ULONG       | Tamanho da piscina de memória segura cache      |

Nem todos os sistemas requerem a definição de memória segura da cache. Neste sistema, os valores passados durante a inicialização do ponteiro de memória serão definidos para UX_NULL e o tamanho da piscina para 0. A USBX utilizará então o pool de memória regular em vez da piscina segura da cache.

Num sistema em que a memória regular não é segura em cache e um controlador requer que execute a memória DMA é necessário definir um conjunto de memórias numa zona segura de cache.

## <a name="uninitialization-of-usbx-resources"></a>Uniinialização dos recursos USBX

O USBX pode ser encerrado libertando os seus recursos. Antes de terminar a usbx, todas as classes e recursos controladores devem ser encerrados corretamente. A seguinte função não iniializa os recursos de memória USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

O protótipo para a ux_system_initialize é o seguinte:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definição de controlador de dispositivos USB

Apenas um controlador de dispositivo USB pode ser definido a qualquer momento para funcionar no modo de dispositivo. O ficheiro de inicialização da aplicação deve conter esta definição. A seguinte linha executa a definição de um controlador usb genérico:

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

A inicialização do dispositivo USB tem o seguinte protótipo:

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

com os seguintes parâmetros:

| Pararmeter               | Descrição                      |
| ------------------------ | -------------------------------- |
| dcd_io ULONG            | Endereço do controlador IO     |
| dcd_irq ULONG           | Interrupção utilizada pelo controlador |
| dcd_vbus_address da ULONG | Endereço do GPIO VBUS         |

Segue-se a inicialização do USBX no modo dispositivo com a classe do dispositivo de armazenamento e um controlador genérico:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>Resolução de problemas

USBX é entregue com um ficheiro de demonstração e um ambiente de simulação. É sempre uma boa ideia pôr a plataforma de demonstração em primeiro lugar - seja no hardware-alvo ou numa plataforma de demonstração específica.

## <a name="usbx-version-id"></a>ID da versão USBX

A versão atual do USBX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. O programador pode obter a versão USBX a partir do exame do ficheiro ***ux_port.h** _ Além disso, este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão USBX examinando a cadeia global *_ __ ux_version_id_* _, que é definida em _*_ux_port.h**._
