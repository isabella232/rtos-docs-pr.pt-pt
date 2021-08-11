---
title: Capítulo 2 - Instalação de pilha de anfitriões USBX Azure RTOS
description: Saiba como instalar a pilha de anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 77df2c4e4bf4ef38403fe78eb98f18820de4325aadb941fc69275e4c77754212
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790971"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Capítulo 2 - Instalação de pilha de anfitriões USBX Azure RTOS

## <a name="host-considerations"></a>Considerações de Anfitrião

### <a name="computer-type"></a>Tipo de computador

O desenvolvimento incorporado é geralmente realizado em computadores de Windows PC ou unix anfitrião. Após a compilação da aplicação, ligada e localizada no anfitrião, é descarregada para o hardware alvo para execução.

### <a name="download-interfaces"></a>Baixar Interfaces

Normalmente, o download do alvo é feito através de uma interface de série RS-232, embora interfaces paralelas, USB e Ethernet estejam a tornar-se mais populares. Consulte a documentação da ferramenta de desenvolvimento para obter as opções disponíveis.

### <a name="debugging-tools"></a>Ferramentas de depurar

Depurar é feito normalmente sobre o mesmo link que o download de imagem do programa. Existe uma variedade de depureiros, desde pequenos programas de monitor que correm no alvo através de ferramentas Background Debug Monitor (BDM) e In-Circuit Emulator (ICE). A ferramenta ICE fornece a depuragem mais robusta do hardware alvo real.

### <a name="required-hard-disk-space"></a>Espaço de disco rígido necessário

O código-fonte do USBX é entregue em formato ASCII e requer aproximadamente 500 KBytes de espaço no disco rígido do computador anfitrião.

## <a name="target-considerations"></a>Considerações-alvo

USBX requer entre 24 KBytes e 64 KBytes de Read Only Memory (ROM) no alvo no modo anfitrião. A quantidade de memória necessária depende do tipo de controlador utilizado e das classes USB ligadas ao USBX. Outros 32 KBytes da Memória de Acesso Aleatório (RAM) do alvo são necessários para estruturas de dados globais USBX e piscina de memória. Este conjunto de memórias também pode ser ajustado dependendo do número esperado de dispositivos no USB e do tipo de controlador USB. O lado do dispositivo USBX requer aproximadamente 10-12 K de ROM dependendo do tipo de controlador do dispositivo. O uso da memória RAM depende do tipo de classe emulsionada pelo dispositivo.

A USBX também conta com semáforos ThreadX, mutexes e fios para proteção de múltiplos fios, e suspensão de I/O e processamento periódico para monitorizar a topologia do autocarro USB.

### <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS USBX pode ser obtido a partir do nosso repositório de código de fonte pública em <https://github.com/azure-rtos/usbx/> .

Segue-se uma lista de vários ficheiros importantes no repositório:

- ***ux_api.h:*** Este ficheiro de cabeçalho C contém todos os equacionares do sistema, estruturas de dados e protótipos de serviço.
- ***ux_port.h:*** Este ficheiro de cabeçalho C contém todas as definições e estruturas específicas da ferramenta de desenvolvimento.
- ***ux.lib***: Esta é a versão binária da biblioteca USBX C. É distribuído com o pacote padrão.
- ***demo_usbx.c***: O ficheiro C que contém uma demonstração USBX simples

Todos os ficheiros estão em minúsculas. Esta convenção de nomeação facilita a conversão dos comandos para plataformas de desenvolvimento Unix.

## <a name="usbx-installation"></a>Instalação USBX

O USBX é instalado clonando o repositório GitHub à sua máquina local. O seguinte é a sintaxe típica para criar um clone do repositório USBX no seu PC:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

Em alternativa, pode descarregar uma cópia do repositório utilizando o botão de descarregamento na página principal GitHub.

Também encontrará instruções para a construção da biblioteca USBX na primeira página do repositório online.

As seguintes instruções gerais aplicam-se a praticamente qualquer instalação:

1. Utilize o mesmo diretório em que instalou anteriormente o ThreadX no disco rígido do hospedeiro. Todos os nomes USBX são únicos e não interferirão com a instalação USBX anterior.
2. Adicione uma chamada a ***ux_system_initialize** _ no início ou perto de _ *_tx_application_define_.* * É aqui que os recursos USBX são inicializados.
3. Adicione uma chamada para ***ux_host_stack_initialize*.**
4. Adicione uma ou mais chamadas para inicializar o USBX necessário.
5. Adicione uma ou mais chamadas para inicializar os controladores hospedeiros disponíveis no sistema.
6. Pode ser necessário modificar o ficheiro tx_low_level_initialize.c para adicionar inicialização de hardware de baixo nível e interromper o encaminhamento do vetor. Isto é específico da plataforma de hardware e não será discutido aqui.
7. Compilar o código-fonte da aplicação e ligar-se às bibliotecas de tempo de funcionamento USBX e ThreadX (FileX e/ou Netx também podem ser necessários se a classe de armazenamento USB e/ou as classes de rede USB forem compiladas em), ux.a (ou ux.lib) e tx.a (ou tx.lib). O resultado pode ser descarregado para o alvo e executado.

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção da biblioteca USBX. Todas as opções estão localizadas no ***ux_user.h***.

A lista abaixo detalha cada opção de configuração.


- **UX_PERIODIC_RATE**: Este valor representa quantos tiques por segundo para uma plataforma de hardware específica. O padrão é 1000 indicando um carrapato por milissegundo.
- **UX_MAX_CLASS_DRIVER**: Este valor é o número máximo de classes que podem ser carregadas por USBX. Este valor representa o recipiente de classe e não o número de casos de uma classe. Por exemplo, se uma determinada implementação do USBX necessitar da classe hub, da classe de impressora e da classe de armazenamento, então o valor UX_MAX_CLASS_DRIVER pode ser definido para 3, independentemente do número de dispositivos que pertencem a estas classes.
- **UX_MAX_HCD**: Este valor representa o número de diferentes controladores de anfitrião disponíveis no sistema. Para suporte USB 1.1, este valor será principalmente 1. Para o suporte USB 2.0 este valor pode ser superior a 1. Este valor representa o número de controladores de anfitriões simultâneos em execução ao mesmo tempo. Se, por exemplo, existirem dois casos de OHCI em funcionamento ou de um EHCI e de um controlador OHCI em funcionamento, o UX_MAX_HCD deve ser definido para 2. 
- **UX_MAX_DEVICES**: Este valor representa o número máximo de dispositivos que podem ser ligados ao USB. Normalmente, o número máximo teórico numa única USB é de 127 dispositivos. Este valor pode ser reduzido para conservar a memória. Note-se que este valor representa o número total de dispositivos, independentemente do número de autocarros USB no sistema.
- **UX_MAX_ED**: Este valor representa o número máximo de EDs no conjunto do controlador. Este número é atribuído apenas a um controlador. Se estiverem presentes vários casos de controladores, este valor é utilizado por cada controlador individual.
- **UX_MAX_TD e UX_MAX_ISO_TD**: Este valor representa o número máximo de TDs regulares e isocronosos na piscina do controlador. Este número é atribuído apenas a um controlador. Se estiverem presentes vários casos de controladores, este valor é utilizado por cada controlador individual.
- **UX_THREAD_STACK_SIZE**: Este valor é o tamanho da stack in bytes para os fios USBX. Pode ser normalmente 1024 bytes ou bytes de 2048 dependendo do processador utilizado e do controlador anfitrião.
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: Este valor é o tamanho da pilha do fio de enumeração do hospedeiro USB. Se este símbolo não definir, o tamanho da pilha de linha de enumeração do anfitrião USBX está definido para **UX_THREAD_STACK_SIZE**. 
- **UX_HOST_HCD_THREAD_STACK_SIZE**: Este valor é o tamanho da pilha do fio HCD do anfitrião USB. Se este símbolo não definir, o tamanho da pilha de fio HCD do anfitrião USBX está definido para **UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM**: Este é o valor prioritário da ThreadX para os fios de enumeração USBX que monitorizam a topologia do autocarro.
- **UX_THREAD_PRIORITY_CLASS**: Este é o valor prioritário da ThreadX para as linhas USBX padrão.
- **UX_THREAD_PRIORITY_KEYBOARD**: Este é o valor prioritário da ThreadX para a classe de teclado USBX HID.
- **UX_THREAD_PRIORITY_HCD**: Este é o valor prioritário threadX para o fio do controlador anfitrião.
- **UX_NO_TIME_SLICE**: Este valor define efetivamente a fatia de tempo que será utilizada para os fios. Por exemplo, se definido para 0, a porta-alvo ThreadX não utiliza fatias de tempo.
- **UX_MAX_HOST_LUN**: Este valor representa o número máximo de unidades lógicas SCSI representadas no condutor da classe de armazenamento de hospedeiro.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: Se definido, este valor inclui código para manusear dispositivos de armazenamento que utilizam o protocolo CB ou CBI (como discos disquetes). Está desligado por padrão porque estes protocolos são obsoletos, sendo substituídos pelo Bulk Only Transport (protocolo BOT, que praticamente todos os dispositivos de armazenamento modernos usam.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: Se definido, este valor faz com que ux_host_class_hid_keyboard_key_get reporte apenas alterações de teclas, ou seja, premias de teclas e versões de teclas. Por defeito, só reporta quando uma chave está em baixo.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** for definido. Se definido, faz com que ux_host_class_hid_keyboard_key_get apenas reporte alterações da tecla pressionada/para baixo; as alterações libertadas/up não são reportadas.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** for definido. Se definido, faz com que ux_host_class_hid_keyboard_key_get reporte alterações na tecla de bloqueio (CapsLock/NumLock/ScrollLock).
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Só utilizado se **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** estiver definido. Se definido, faz com que ux_host_class_hid_keyboard_key_get reporte alterações na chave modificadora (Ctrl/Alt/Shift/GUI).
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: Se definido, este valor representa o número de pacotes na classe de anfitrião CDC-ECM. O padrão é 16.

## <a name="source-code-tree"></a>Árvore-código fonte

Os ficheiros USBX são fornecidos em vários diretórios.

![Árvore-código fonte](media/usbx-host-stack/source-code-tree.png)

A fim de tornar os ficheiros reconhecíveis pelos seus nomes, foi adotada a seguinte convenção:

| Nome do sufixo de arquivo | Descrição do arquivo                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | usbx host stack ficheiros de núcleo                |
| ux_host_class    | usbx host stack classes arquivos             |
| ux_hcd           | usbx host stack controladore de controladores   |
| ux_device_stack  | usbx dispositivo stack ficheiros de núcleo              |
| ux_device_class  | usbx pilha de ficheiros classes           |
| ux_dcd           | usbx dispositivo stack controladore de controladores |
| ux_otg           | usbx otg controladore ficheiros relacionados com o controlador  |
| ux_pictbridge    | usbx pictbridge arquivos                     |
| ux_utility       | funções de utilidade usbx                    |
| demo_usbx        | ficheiros de demonstração para USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicialização dos recursos USBX

A USBX tem o seu próprio gestor de memória. A memória precisa de ser atribuída ao USBX antes da inicialação do lado do anfitrião ou do dispositivo do USBX. O gestor de memória USBX pode acomodar sistemas onde a memória pode ser em cache.

A seguinte função inicializa os recursos de memória USBX com 128K de memória regular e nenhuma piscina separada para a memória segura da cache:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

O protótipo para a ux_system_initialize é o seguinte.

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>Parâmetros de entrada:

- **regular_memory_pool_start** Início da piscina de memórias regular.
- **regular_memory_size** Tamanho da piscina de memória regular.
- **cache_safe_memory_pool_start** Início da piscina de memória segura da cache.
- **cache_safe_memory_size** Tamanho da piscina de memória segura cache.    |

Nem todos os sistemas requerem a definição de memória segura da cache. Neste sistema, os valores passados durante a inicialização do ponteiro de memória serão definidos para UX_NULL e o tamanho da piscina para 0. A USBX utilizará então o pool de memória regular em vez da piscina segura da cache.

Num sistema em que a memória regular não é segura em cache e um controlador requer a realização da memória DMA (como OHCI, controladores EHCI entre outros) é necessário definir um pool de memória numa zona segura de cache.

## <a name="uninitialization-of-usbx-resources"></a>Uniinialização dos recursos USBX

O USBX pode ser encerrado libertando os seus recursos. Antes de terminar a usbx, todas as classes e recursos controladores devem ser encerrados corretamente. A seguinte função não iniializa os recursos de memória USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

O protótipo para a ux_system_initialize é o seguinte.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definição de controladores de anfitriões USB

É necessário definir pelo menos um controlador usb para o USBX operar no modo de anfitrião. O ficheiro de inicialização da aplicação deve conter esta definição. A seguinte linha executa a definição de um controlador de hospedeiro genérico.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

O ux_host_stack_hcd_register tem o seguinte protótipo.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

A função ux_host_stack_hcd_register tem os seguintes parâmetros.

- **hcd_name**: cadeia do nome do controlador
- **hcd_initialize_function**: função de inicialização do controlador
- **hcd_param1:** normalmente o valor IO ou memória utilizado pelo controlador
- **hcd_param2:** normalmente o IRQ utilizado pelo controlador

No nosso exemplo anterior:

- "ux_hcd_controller" é o nome do controlador
- "ux_hcd_controller_initialize" é a rotina de inicialização do controlador anfitrião
- 0xd0000 é o endereço em que os registos do controlador anfitrião são visíveis na memória
- e 0x0a é o IRQ usado pelo controlador hospedeiro.

Segue-se um exemplo da inicialização do USBX no modo hospedeiro com um controlador de anfitrião e várias classes.

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a>Definição de aulas de anfitrião

É necessário definir uma ou mais classes de anfitriões com USBX. É necessária uma classe USB para conduzir um dispositivo USB depois de a pilha USB ter configurado o dispositivo USB. Uma classe USB é específica do dispositivo. Uma ou mais classes podem ser necessárias para conduzir um dispositivo USB dependendo do número de interfaces contidas nos descritores do dispositivo USB.

Este é um exemplo do registo da classe HUB.

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

A função ux_host_class_register tem o seguinte protótipo.

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** é o nome da classe
- **class_entry_address** é o ponto de entrada da classe

No exemplo da inicialização da classe HUB:

- "ux_host_class_hub" é o nome da classe hub
- ux_host_class_hub_entry é o ponto de entrada da classe HUB.

## <a name="troubleshooting"></a>Resolução de problemas

USBX é entregue com um ficheiro de demonstração e um ambiente de simulação. É sempre uma boa ideia pôr a plataforma de demonstração em primeiro lugar - seja no hardware-alvo ou numa plataforma de demonstração específica.

Se o sistema de demonstração não funcionar, tente as seguintes coisas para reduzir o problema.

## <a name="usbx-version-id"></a>ID da versão USBX

A versão atual do USBX está disponível tanto para o utilizador como para o software da aplicação durante o tempo de funcionamento. O programador pode obter a versão USBX a partir do exame do ficheiro ***ux_port.h** _ Além disso, este ficheiro também contém um histórico de versão da porta correspondente. O software de aplicação pode obter a versão USBX examinando a cadeia global *_ __ ux_version_id_* _, que é definida em _*_ux_port.h**._
