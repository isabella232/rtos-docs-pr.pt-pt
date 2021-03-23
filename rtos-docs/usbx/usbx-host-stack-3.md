---
title: Capítulo 3 - Componentes funcionais da pilha de anfitriões USBX
description: Este capítulo contém uma descrição da pilha usb incorporada USBX de uma perspetiva funcional.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 17b8d884dd2c71d60e91f5fcec40c360060f4fe8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828369"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Capítulo 3 - Componentes funcionais da pilha de anfitriões USBX

Este capítulo contém uma descrição da pilha usb incorporada USBX de uma perspetiva funcional.

## <a name="execution-overview"></a>Visão geral da execução

USBX é composto por vários componentes:

- Inicialização
- Chamadas de interface de aplicação
- Centro de Raiz
- Classe Hub
- Aulas de acolhimento
- Pilha de anfitriões USB
- Controlador anfitrião

O diagrama seguinte ilustra a pilha de anfitriões USBX.

![Pilha de anfitriões USBX](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Inicialização

Para ativar o USBX, a função ***ux_system_initialize*** deve ser chamada. Esta função inicializa os recursos de memória do USBX.

Para ativar as instalações de anfitrião USBX, a função ***ux_host_stack_initialize*** deve ser chamada. Esta função, por sua vez, rubricará todos os recursos utilizados pela pilha de anfitriões USBX, tais como fios ThreadX, mutexes e semáforos.

Cabe à inicialização da aplicação ativar pelo menos um controlador usb e uma ou mais classes USB. Quando as classes estiverem registadas na stack e a função de inicialização do controlador de anfitrião tiver sido chamada, o autocarro está ativo e a descoberta do dispositivo pode começar. Se o eixo raiz do controlador hospedeiro detetar um dispositivo ligado, o fio de enumeração USB, encarregado da topologia USB, acordará e procederá à enumeração do dispositivo.

É possível, devido à natureza do hub raiz e dos hubs a jusante, que todos os dispositivos USB ligados possam não ter sido completamente configurados quando a função de inicialização do controlador do hospedeiro regressar. Pode levar vários segundos para enumerar todos os dispositivos USB, especialmente se houver um ou mais hubs entre o hub raiz e os dispositivos USB.

### <a name="application-interface-calls"></a>Chamadas de Interface de Aplicação

Há dois níveis de APIs em USBX.

- APIs de pilha de anfitriões USB
- APIs de classe de anfitrião USB

Normalmente, uma aplicação USBX não deve ter de ligar para nenhuma das funções de API da pilha de anfitriões USB. A maioria das aplicações só acederá às funções API da classe USB.

### <a name="usb-host-stack-apis"></a>APIs de pilha de anfitriões USB

As funções de API da pilha de anfitrião são responsáveis pelo registo de componentes USBX (classes de anfitrião e controladores de anfitrião), configuração de dispositivos e pedidos de transferência para os pontos finais do dispositivo disponíveis.

### <a name="usb-host-class-api"></a>API da classe de anfitrião USB

As APIs de classe são muito específicas de cada classe USB. A maioria das funções comuns de API para classes USB fornecem serviços como abrir/fechar um dispositivo e ler e escrever para um dispositivo.

### <a name="root-hub"></a>Centro de Raiz

Cada instância do controlador anfitrião tem um ou mais centros de raiz USB. O número de cubos de raiz é determinado pela natureza do controlador ou pode ser recuperado através da leitura de registos específicos do controlador.

### <a name="hub-class"></a>Classe Hub

A classe hub está encarregada de conduzir centros USB. Um hub USB pode ser um hub autónomo ou como parte de um dispositivo composto, como um teclado ou um monitor. Um hub pode ser autoalimentado ou movido a autocarros. Os hubs movidos a autocarros têm um máximo de quatro portas a jusante e só podem permitir a ligação de dispositivos que sejam dispositivos autoalimentados ou movidos a autocarros que utilizem menos de 100mA de potência. Os centros podem ser em cascata. Até cinco centros podem ser ligados uns aos outros.

### <a name="usb-host-stack"></a>Pilha de anfitriões USB

A pilha de anfitriões USB é a peça central do USBX. Tem três funções principais.

- Gerir a topologia do USB.
- Ligue um dispositivo USB a uma ou mais classes.
- Forneça uma API às aulas para realizar interrogatórios de descritor de dispositivos e transferências USB.

### <a name="topology-manager"></a>Gestor de Topologia

O fio topologia da pilha USB é despertado quando um novo dispositivo está ligado ou quando um dispositivo foi desligado. O hub raiz ou um hub regular podem aceitar ligações do dispositivo. Uma vez ligado um dispositivo ao USB, o gestor de topologia recuperará o descritor do dispositivo. Este descritor conterá o número de configurações possíveis disponíveis para este dispositivo. A maioria dos dispositivos tem apenas uma configuração. Alguns dispositivos podem funcionar de forma diferente de acordo com a energia disponível na porta onde está ligada. Se for esse o caso, o dispositivo terá múltiplas configurações que podem ser selecionadas dependendo da energia disponível. Quando o dispositivo é configurado pelo gestor de topologia, é então permitido extrair a quantidade de energia especificada no seu descritor de configuração.

## <a name="usb-class-binding"></a>Ligação de classe USB

Quando o dispositivo estiver configurado, o gestor de topologia permitirá que o gestor de classe continue a descoberta do dispositivo olhando para os descritores de interface do dispositivo. Um dispositivo pode ter um ou mais descritores de interface.

Uma interface representa uma função num dispositivo. Por exemplo, um altifalante USB tem três interfaces, uma para streaming de áudio, uma para controlo de áudio e outra para gerir os vários botões de altifalante.

O gestor de classe tem dois mecanismos para juntar a interface do dispositivo a uma ou mais classes. Pode utilizar a combinação de um PID/VID (ID do produto e ID do fornecedor) encontrado no descritor de interface ou na combinação de Classe/Subclasse/Protocolo.

A combinação PID/VID é válida para interfaces que não podem ser conduzidas por uma classe genérica. A combinação Classe/Subclasse/Protocolo é utilizada por interfaces que pertencem a uma classe certificada USB-IF, como impressora, hub, armazenamento, áudio ou HID.

O gestor da classe contém uma lista de classes registadas a partir da inicialização do USBX. O gestor de turma ligará para cada classe um de cada vez até que uma classe aceite gerir a interface para esse dispositivo. Uma classe só consegue gerir uma interface. Para o exemplo do altifalante de áudio USB, o gestor de classe irá ligar para todas as classes para cada uma das interfaces.

Uma vez que uma classe aceita uma interface, uma nova instância dessa classe é criada. O gestor de classe procurará então a definição alternativa predefinida para a interface. Um dispositivo pode ter uma ou mais configurações alternativas para cada interface. A definição alternativa 0 será a utilizada por predefinição até que uma classe decida alterá-la.

Para a definição alternativa predefinida, o gestor de classe montará todos os pontos finais contidos na definição alternativa. Se a montagem de cada ponto final for bem sucedida, o gestor de classe completará o seu trabalho devolvendo à classe que terminará a inicialização da interface.

### <a name="usbx-apis"></a>USBX APIs

A pilha USB exporta um certo número de APIs para as classes USB para realizar interrogatórios no dispositivo e transferências USB em pontos finais específicos. Estas funções API são descritas em detalhe neste manual de referência.

### <a name="host-controller"></a>Controlador anfitrião

O controlador de anfitrião é responsável pela condução de um tipo específico de controlador USB. Um controlador de anfitrião USB pode ter vários controladores no interior. Por exemplo, certos chipsets do Pc Intel contêm dois controladores UHCI. Alguns controladores USB 2.0 contêm múltiplas instâncias de um controlador OHCI, além de uma instância do controlador EHCI.

O controlador anfitrião gerirá várias instâncias apenas do mesmo controlador. Para conduzir a maioria dos controladores hospedeiros USB 2.0, será necessário inicializar tanto o controlador OCHI como o controlador EHCI durante a inicialização do USBX.

O controlador anfitrião é responsável pela gestão do seguinte.

- Centro de Raiz
- Gestão de Energia
- Pontos Finais
- Transferências

### <a name="root-hub"></a>Centro de Raiz

A gestão do hub raiz é responsável pela alimentação de cada porta do controlador e determinar se há um dispositivo inserido ou não. Esta funcionalidade é utilizada pelo hub genérico usbx para interrogar as portas a jusante do controlador.

### <a name="power-management"></a>Gestão de Energia

O processamento de gestão de energia prevê o manuseamento de sinais de suspensão/retoma, quer no modo gang, afetando assim todas as portas a jusante do controlador ao mesmo tempo, quer individualmente se o controlador oferecer esta funcionalidade.

### <a name="endpoints"></a>Pontos Finais

A gestão do ponto final prevê a criação ou destruição de pontos finais físicos para o controlador. Os pontos finais físicos são entidades de memória que são analisadas pelo controlador se o controlador suporta o DMA principal ou que estão escritos no controlador. Os pontos finais físicos contêm informações de transações a serem realizadas pelo controlador.

### <a name="transfers"></a>Transferências

A gestão de transferências prevê que uma classe efetue uma transação em cada um dos pontos finais que foram criados. Cada ponto final lógico contém um componente chamado TRANSFER REQUEST para pedidos de transferência USB. O PEDIDO DE TRANSFERÊNCIA é utilizado pela stack para descrever a transação. Este PEDIDO DE TRANSFERÊNCIA é então passado para a pilha e para o controlador, o que pode dividi-lo em várias sub-transacções dependendo das capacidades do controlador.

## <a name="usb-device-framework"></a>Estrutura do dispositivo USB

Um dispositivo USB é representado por uma árvore de descritores. Existem seis tipos principais de descritores.

- Descritores de dispositivos
- Descritores de configuração
- Descritores de interface
- Descritores de ponto final
- Descritores de cordas
- Descritores funcionais

Um dispositivo USB pode ter uma descrição muito simples e parece-se com isto.
![Dispositivo USB simples](./media/usbx-host-stack/usb-device-simple.png)

Na ilustração acima, o dispositivo tem apenas uma configuração. Uma única interface é anexada a esta configuração, indicando que o dispositivo tem apenas uma função, e tem apenas um ponto final. Anexado ao descritor do dispositivo está um descritor de cordas que fornece uma identificação visível do dispositivo.

No entanto, um dispositivo pode ser mais complexo e pode aparecer da seguinte forma.

![Dispositivo USB complexo](./media/usbx-host-stack/usb-device-complex.png)

Na ilustração acima, o dispositivo tem dois descritores de configuração ligados ao descritor do dispositivo. Este dispositivo pode indicar que tem dois modos de alimentação ou pode ser conduzido por classes padrão ou classes próprias.

Anexadas à primeira configuração estão duas interfaces que indicam que o dispositivo tem duas funções lógicas. A primeira função tem 3 descritores de ponto final e um descritor funcional. O descritor funcional pode ser utilizado pela classe responsável para conduzir a interface para obter mais informações sobre esta interface normalmente não encontradas por um descritor genérico.

### <a name="device-descriptors"></a>Descritores de dispositivos

Cada dispositivo USB tem um único descritor de dispositivos. Este descritor contém a identificação do dispositivo, o número de configurações suportadas e as características do ponto final de controlo predefinido utilizado para configurar o dispositivo.

| Desvio | Campo              | Tamanho | Valor    | Descrição                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | Rio BLength            | 1    | Número   | Tamanho deste descritor em bytes |
| 1      | bDescriptorType    | 1    | Constante | Tipo de descritor de dispositivo |
| 2      | bcdUSB             | 2    | BCD      | Número de desbloqueio de especificações USB em BinaryCoded Dec<br />Exemplo: 2.10 é equivalente a 0x210. Este campo identifica a libertação da Especificação USB com a que o dispositivo e os seus descritores estão em conformidade. |
| 4      | bDeviceClass       | 1    | Classe    | Código de classe (atribuído por USB-IF).<br />Se este campo for reiniciado para 0, cada interface dentro de uma configuração especifica as suas próprias informações de classe e as várias interfaces funcionam de forma independente.<br />Se este campo estiver definido para um valor entre 1 e 0xFE, o dispositivo suporta diferentes especificações de classe em diferentes interfaces e as interfaces podem não funcionar de forma independente. Este valor identifica a definição de classe utilizada para as interfaces agregadas.<br />Se este campo estiver definido para 0xFF, a classe do dispositivo é específica do fornecedor. |
| 5      | bDeviceSubClass    | 1    | Subclasse | Código de subclasse (atribuído por USB-IF).<br />Estes códigos são qualificados pelo valor do campo bDeviceClass. Se o campo bDeviceClass for reiniciado para 0, este campo também deve ser reposto para 0. Se o campo bDeviceClass não estiver definido para 0xFF, todos os valores são reservados para atribuição por USB. |
| 6      | bDeviceProtocol    | 1    | Protocolo | Código de protocolo (atribuído por USB-IF).<br />Estes códigos são qualificados pelo valor dos campos bDeviceClass e bDeviceSubClass. Se um dispositivo suporta protocolos específicos de classe numa base de dispositivo em oposição a uma base de interface, este código identifica os protocolos que o dispositivo utiliza conforme definido pela especificação da classe do dispositivo. Se este campo for reiniciado para 0, o dispositivo não utiliza protocolos específicos de classe numa base de dispositivo.<br />No entanto, pode utilizar protocolos específicos de classe numa base de interface.<br />Se este campo estiver definido para 0xFF, o dispositivo utiliza um protocolo específico do fornecedor numa base de dispositivo. |
| 7      | bMaxPacketSize0    | 1    | Número   | Tamanho máximo do pacote para ponto final zero (apenas os tamanhos byte de 8, 16, 32 ou 64 são válidos) |
| 8      | idVendor           | 2    | ID       | ID do fornecedor (atribuído por USB-IF) |
| 10     | idPro          | 2    | ID       | ID do produto (atribuído pelo Fabricante) |
| 12     | bcdDevice          | 2    | BCD      | Número de libertação do dispositivo em decimal codificado binário |
| 14     | iManufacturer      | 1    | Índice    | Índice do descritor de cordas que descreve o fabricante |
| 15     | iProduto           | 1    | Índice    | Índice do descritor de cordas que descreve o produto |
| 16     | iSerialNumbe       | 1    | Índice    | Índice do descritor de cordas descrevendo o número de série do dispositivo |
| 17     | bNumConfigurations | 1    | Número   | Número de configurações possíveis |

USBX define um descritor de dispositivos USB da seguinte forma:

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

O descritor do dispositivo USB faz parte de um recipiente de dispositivo descrito como:

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle:** Manuseie o aparelho. Este é tipicamente o endereço da instância desta estrutura para o dispositivo.
- **ux_device_type:** Valor obsoleto. Não é bem-de-suso.
- **ux_device_state**: Estado do Dispositivo, que pode ter um dos seguintes valores:
    - **UX_DEVICE_RESET**                0
    - **UX_DEVICE_ATTACHED**             1
    - **UX_DEVICE_ADDRESSED**            2
    - **UX_DEVICE_CONFIGURED**           3
    - **UX_DEVICE_SUSPENDED**            4
    - **UX_DEVICE_RESUMED**              5
    - **UX_DEVICE_SELF_POWERED_STATE**   6
    - **UX_DEVICE_SELF_POWERED_STATE**   7
    - **UX_DEVICE_REMOTE_WAKEUP**        8
    - **UX_DEVICE_BUS_RESET_COMPLETED**  9
    - **UX_DEVICE_REMOVED**              10
    - **UX_DEVICE_FORCE_DISCONNECT**     11
- **ux_device_address**: Endereço do dispositivo após a aceitação do comando **SET_ADDRESS** (de 1 a 127).
- **ux_device_speed**: Velocidade do dispositivo:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location**: Índice da porta do dispositivo-mãe (eixo de raiz ou hub).
- **ux_device_max_power**: Potência máxima em mA que o dispositivo pode ter na configuração selecionada.
- **ux_device_power_source**: Pode ser um dos dois valores seguintes:
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration**: Índice da configuração atual utilizada por este dispositivo.
- **ux_device_parent**: Ponteiro do recipiente do dispositivo do progenitor deste dispositivo. Se o ponteiro for nulo, o progenitor é o eixo principal do controlador.
- **ux_device_class**: Ponter para o tipo de classe que possui este dispositivo.
- **ux_device_class_instance**: Ponte para o caso da classe proprietária deste dispositivo.
- **ux_device_hcd**: Instância do controlador de anfitrião USB onde este dispositivo está ligado.
- **ux_device_first_configuration**: Ponteiro para o primeiro recipiente de configuração deste dispositivo.
- **ux_device_next_device**: Pontear para o próximo dispositivo na lista de dispositivos em qualquer um dos autocarros detetados por USBX.
- **ux_device_descriptor**: descritor de dispositivos USB.
- **ux_device_control_endpoint**: Descritor do ponto final de controlo predefinido utilizado por este dispositivo.
- **ux_device_hub_tt**: Matriz de TTs hub para o dispositivo

### <a name="configuration-descriptors"></a>Descritores de configuração

O descritor de configuração descreve informações sobre uma configuração específica do dispositivo. Um dispositivo USB pode conter um ou mais descritores de configuração. O campo **bNumConfigurations** no descritor do dispositivo indica o número de descritores de configuração. O descritor contém um campo **bConfigurationValue** com um valor que, quando utilizado como parâmetro para o pedido de Configuração de Conjunto, faz com que o dispositivo assuma a configuração descrita.

O descritor descreve o número de interfaces fornecidas pela configuração. Cada interface representa uma função lógica dentro do dispositivo e pode funcionar de forma independente. Por exemplo, um altifalante de áudio USB pode ter três interfaces, uma para streaming de áudio, uma para controlo de áudio e uma interface HID para gerir os botões do altifalante.

Quando o anfitrião emite um pedido GET_DESCRIPTOR para o descritor de configuração, todos os descritores de interface e ponto final relacionados são devolvidos.

| Desvio | Campo               | Tamanho | Valor    | Descrição                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | Número   | Tamanho deste descritor em bytes. |
| 1      | bDescriptorType     | 1    | Constante | CONFIGURAÇÃO                     |
| 2      | wTotalLength        | 2    | Número   | Comprimento total dos dados devolvidos para esta configuração. Inclui o comprimento combinado de todos os descritores (configuração, interface, ponto final e classe ou fornecedor específico) devolvidos para esta configuração. |
| 4      | bNumInterfaces      | 1    | Número   | Número de interfaces suportadas por esta configuração. |
| 5      | bConfigurationValue | 1    | Número   | Valor a usar como argumento para definir<br/>Configuração para selecionar esta configuração. |
| 6      | iConfiguration      | 1    | Índice    | Índice de descritor de cordas descrevendo esta configuração. |
| 7      | bMAttributes        | 1    | Bitmap   | Características de configuração D7 Bus Powered<br />D6 Autoalimentado<br />Despertar Remoto D5<br />D4. 0 Reservado (reset a 0)<br />Uma configuração do dispositivo que utiliza energia do autocarro e uma fonte local define tanto D7 como D6. A fonte de energia real no tempo de execução pode ser determinada usando o pedido do dispositivo Get Status.<br />Se uma configuração do dispositivo suportar o despertar remoto, o D5 está definido para 1. |
| 8      | MaxPower            | 1    | mA       | Consumo máximo de energia do dispositivo USB a partir do autocarro nesta configuração específica quando o dispositivo estiver totalmente operacional.<br />Expresso em 2 unidades mA (por exemplo, 50 = 100 mA).<br />Nota: Uma configuração do dispositivo informa se a configuração é alimentada por autocarro ou autoalimentada.<br />O estado do dispositivo informa se o dispositivo está atualmente autoalimentado. Se um dispositivo for desligado da sua fonte de alimentação externa, atualiza o estado do dispositivo para indicar que já não é alimentado por si próprio. |

USBX define um descritor de configuração USB da seguinte forma.

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

O descritor de configuração USB faz parte de um recipiente de configuração descrito como mostrado abaixo.

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle**: Manuseie a configuração. Este é tipicamente o endereço da instância desta estrutura para a configuração.
- **ux_configuration_state**: Estado da configuração.
- **ux_configuration_descriptor**: descritor de dispositivos USB.
- **ux_configuration_first_interface**: Ponteiro para a primeira interface para esta configuração.
- **ux_configuration_next_configuration**: Ponteiro para a próxima configuração para o mesmo dispositivo.
- **ux_configuration_device**: Pontear para o proprietário do dispositivo desta configuração.

### <a name="interface-descriptors"></a>Descritores de interface

O descritor de interface descreve uma interface específica dentro de uma configuração. Uma interface é uma função lógica dentro de um dispositivo USB. Uma configuração fornece uma ou mais interfaces, cada uma com descritores de ponto final zero ou mais descrevendo um conjunto único de pontos finais dentro da configuração. Quando uma configuração suporta mais de uma interface, os descritores de ponto final de uma determinada interface seguem o descritor de interface nos dados devolvidos pelo **GET_DESCRIPTOR** pedido para a configuração especificada.

Um descritor de interface é sempre devolvido como parte de um descritor de configuração. Um descritor de interface não pode ser diretamente acedededor por um pedido GET_DESCRIPTOR.

Uma interface pode incluir configurações alternativas que permitam que os pontos finais e/ou as suas características sejam variados após a configuração do dispositivo. A definição predefinição de uma interface é sempre a definição alternativa zero. Uma classe pode selecionar para alterar a definição alternativa atual para alterar o comportamento da interface e as características dos pontos finais associados. O pedido de SET_INTERFACE é utilizado para selecionar uma definição alternativa ou para voltar à definição predefinitiva.

As definições alternativas permitem que uma parte da configuração do dispositivo seja variada enquanto outras interfaces permanecem em funcionamento. Se uma configuração tiver configurações alternativas para uma ou mais das suas interfaces, um descritor de interface separado e os seus pontos finais associados estão incluídos para cada definição.

Se uma configuração do dispositivo contiver uma única interface com duas definições alternativas, o pedido de GET_DESCRIPTOR para a configuração devolveria o descritor de configuração, então o descritor de interface com os campos **bInterfaceNumber** e **bAlternateSetting** definidos para zero e, em seguida, os descritores de ponto final para essa definição, seguido de outro descritor de interface e seus descritores de ponto final associados. O segundo campo **bInterfaceNumber** do descritor de segunda interface também seria definido para zero, mas o campo **bAlternateSetting** do descritor de segunda interface seria definido para 1 indicando que esta definição alternativa pertence à primeira interface.

Uma interface pode não ter quaisquer pontos finais associados à mesma, caso em que apenas o ponto final de controlo predefinido é válido para essa interface.

As definições alternativas são utilizadas principalmente para alterar a largura de banda solicitada para pontos finais periódicos associados à interface. Por exemplo, uma interface de streaming de altifalantes USB deve ter a primeira definição alternativa com uma procura de largura de banda de 0 no seu ponto final isocronous. Outras definições alternativas podem selecionar diferentes requisitos de largura de banda dependendo da frequência de streaming de áudio.

O descritor USB para a interface é o seguinte:

| Desvio | Campo              | Tamanho | Valor     | Descritor                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | Número    | Tamanho deste descritor em bytes.       |
| 1      | bDescriptorType    | 1    | Constante  | Tipo de descritor interface               |
| 2      | bInterfaceNumber   | 1    | Número    | Número de interface. Valor baseado em zero identificando o índice na matriz de interfaces simultâneas suportadas por esta configuração. |
| 3      | bAltenateSetting   | 1    | Número    | Valor utilizado para selecionar definição alternativa para a interface identificada no campo anterior. |
| 4      | bNumEndpoints      | 1    | Número    | Número de pontos finais utilizados por esta interface (excluindo o ponto final zero). Se este valor for 0, esta interface utiliza apenas o ponto final zero. |
| 5      | bInterfaceClass    | 1    | Classe     | Código de classe (atribuído por USB)<br />Se este campo for reiniciado para 0, a interface não pertence a nenhuma classe de dispositivos especificados USB.<br />Se este campo estiver definido para 0xFF, a classe de interface é específica do fornecedor.<br />Todos os outros valores são reservados para atribuição por USB. |
| 6      | bInterfaceSubClass | 1    | Subclasse  | Código de subclasse (atribuído por USB).<br />Estes códigos são qualificados pelo valor do campo bInterfaceClass. Se o campo bInterfaceClass for reiniciado para 0, este campo também deve ser reposto para 0. Se o campo bInterfaceClass não estiver definido para 0xFF, todos os valores são reservados para atribuição por USB. |
| 7      | bInterfaceProtocol | 1    | Protocolo  | Código de protocolo (atribuído por USB). Estes códigos são qualificados pelo valor dos campos bInterfaceClass e bInterfaceSubClass. Se uma interface suporta pedidos específicos de classe, este código identifica os protocolos que o dispositivo utiliza conforme definido pela especificação da classe do dispositivo.<br />Se este campo for reiniciado para 0, o dispositivo não utiliza um protocolo específico de classe nesta interface. Se este campo estiver definido para 0xFF, o dispositivo utiliza um protocolo específico do fornecedor para esta interface. |
| 8      | iInterface         | 1    | Índice     | Índice de descritor de cordas descrevendo esta interface. |

USBX define um descritor de interface USB da seguinte forma.

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

O descritor de interface USB faz parte de um recipiente de interface descrito da seguinte forma.

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle:** Manuseie a interface. Este é tipicamente o endereço da instância desta estrutura para a interface.
- **ux_interface_state**: Estado da interface.
- **ux_interface_descriptor**: descritor de interface USB.
- **ux_interface_class**: Ponter para o tipo de classe que detém esta interface.
- **ux_interface_class_instance**: Ponteiro para o exemplo da classe que detém esta interface.
- **ux_interface_first_endpoint**: Ponteiro para o primeiro ponto final registado com esta interface.
- **ux_interface_next_interface**: Ponteiro para a interface seguinte associada à configuração.
- **ux_interface_configuration**: Ponteiro para o proprietário da configuração desta interface.

### <a name="endpoint-descriptors"></a>Descritores de ponto final

Cada ponto final associado a uma interface tem o seu próprio descritor de ponto final. Este descritor contém as informações necessárias pela pilha de anfitrião para determinar os requisitos de largura de banda de cada ponto final, a carga máxima associada ao ponto final, a sua periodicidade e a sua direção. Um descritor de ponto final é sempre devolvido por um GET_DESCRIPTOR comando para a configuração.

O ponto final de controlo predefinido associado ao descritor do dispositivo não é contabilizado como parte do ponto final associado à interface e, portanto, não devolvido neste descritor.

Quando o software anfitrião solicita uma alteração da definição alternativa para uma interface, todos os pontos finais associados e os seus recursos USB são modificados de acordo com a nova configuração alternativa.

Com exceção dos pontos finais de controlo predefinidos, os pontos finais não podem ser repartições entre interfaces.

| Desvio | Campo            | Tamanho | Valor    | Descrição                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | Número   | Tamanho deste descritor em bytes. |
| 1      | bDescriptorType  | 1    | Constante | Tipo de descritor ENDPOINT. |
| 2      | bEndpointAddress | 1    | Ponto final | O endereço do ponto final no dispositivo USB descrito por este descritor. O endereço está codificado da seguinte forma:<br />Bit 3...0: O número do ponto final<br />Bit 6...4: Reservado, reposto a zero<br />Bit 7: Direção, ignorada para pontos finais de controlo<br />0 = OUT endpoint<br />1 = ponto final |
| 3      | bmAttributes     | 1    | Bitmap   | Este campo descreve os atributos do ponto final quando é configurado usando o campo **bConfigurationValue.** Bits 1.0: Tipo de Transferência<br />00 = Controlo<br />01 = Isochronous<br />10 = Granel<br />11 = Interromper<br />Se não for um ponto final isocronous, os bits 5.2 estão reservados e devem ser definidos para zero. Se isocromous, são definidos da seguinte forma:<br />Bits 3.2: Tipo de sincronização<br />00 = Sem Sincronização<br />01 = Assíncronos<br />10 = Adaptável<br />11 = Sincronizado<br />Bits 5.4: Tipo de utilização<br />00 = Ponto final de dados<br />01 = Ponto final de feedback<br />10 = Ponto final de dados de feedback implícito<br />11 = Reservado |
| 4      | wMaxPacketSize   | 2    | Número   | O tamanho máximo do pacote este ponto final é capaz de enviar ou receber quando esta configuração é selecionada.<br />Para pontos finais isocronous, este valor é utilizado para reservar o tempo de autocarro no horário, necessário para as cargas de dados por fotogramas. O tubo pode, numa base contínua, utilizar de facto menos largura de banda do que a reservada. O dispositivo informa, se necessário, a largura de banda real utilizada através dos seus mecanismos normais não USB definidos.<br />Para todos os pontos finais, os bits 10.0 especificam o tamanho máximo do pacote (em bytes).<br />Para pontos finais isocronos e de alta velocidade:<br />Bits 12..11 especificam o número de oportunidades de transação adicionais por micro-quadro: 00 = Nenhuma (1 transação por microframe)<br />01 = 1 adicional (2 por microframe)<br />10 = 2 adicionais (3 por microframe)<br />11 = Reservado<br />Os bits 15.13 estão reservados e devem ser definidos a zero. |
| 6      | bInterval        | 1     | Número   | Intervalo de número para o ponto final das sondagens para transferências de dados.<br />Expressos em quadros ou micropartidos dependendo da velocidade de funcionamento do dispositivo (ou seja, 1 milissegundo ou 125 unidades de μs).<br />Para os pontos finais isocronos de alta velocidade, este valor deve estar na faixa de 1 a 16. O **bInterval** é utilizado como expoente para um valor 2bInterval-1; por exemplo, **bInterval** 4 significa um período de 8 (24-1).<br />Para pontos finais de interrupção a toda/baixa velocidade, o valor deste campo pode ser de 1 a 255.<br />Para pontos finais de interrupção de alta velocidade, o **bInterval** é usado como expoente para um valor 2bInterval-1; por exemplo, **bInterval** 4 significa um período de 8 (24-1). Este valor deve ser de 1 a 16.<br />Para pontos finais out a granel/controlo de alta velocidade, o **bInterval** especifica a taxa máxima de NAK do ponto final. Um valor de 0 indica que o ponto final nunca é NAKs. Outros valores indicam, no máximo, um NAK cada **bInterval** de micropartidos.<br />Este valor deve estar entre 0 e 255. |

USBX define um descritor de ponto final USB da seguinte forma:

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

O descritor de ponto final USB faz parte de um recipiente de ponto final, que é descrito da seguinte forma.

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle:** Manuseie o ponto final. Este é tipicamente o endereço da instância desta estrutura para o ponto final.
- **ux_endpoint_state:** Estado do ponto final.
- **ux_endpoint_ed**: Ponte até ao ponto final físico na camada do controlador do anfitrião.
- **ux_endpoint_descriptor**: descritor de ponto final USB.
- **ux_endpoint_next_endpoint**: Ponteiro para o próximo ponto final que pertence à mesma interface.
- **ux_endpoint_interface**: Ponteiro para a interface que detém esta interface de ponto final.
- **ux_endpoint_device:** Pontear para o recipiente do dispositivo principal.
- **ux_endpoint_transfer pedido:** pedido de transferência USB utilizado para enviar/receber dados de/para o dispositivo.

### <a name="string-descriptors"></a>Descritores de cordas

Os descritores de cordas são opcionais. Se um dispositivo não suporta descritores de cordas, todas as referências aos descritores de cordas dentro do dispositivo, configuração e descritores de interface devem ser reiniciadas para zero.

Os descritores de cordas utilizam codificação UNICODE, permitindo assim o suporte para vários conjuntos de caracteres. As cordas de um dispositivo USB podem suportar vários idiomas. Ao solicitar um descritor de cordas, o solicitador especifica a língua desejada utilizando um ID de idioma definido pelo USB-IF. A lista de LANGIDs USB atualmente definidos pode ser encontrada no apêndice USBX ??.
Índice de cadeia zero para todas as línguas devolve um descritor de cordas que contém uma matriz de códigos LANGID de dois bytes suportados pelo dispositivo. Note-se que a cadeia UNICODE não está terminada. Em vez disso, o tamanho da matriz de cordas é calculado subtraindo dois do tamanho da matriz contida no primeiro byte do descritor.

O descritor de cordas USB 0 está codificado da seguinte forma.

| Desvio | Campo           | Tamanho | Valor    | Descrição                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N+2      | Tamanho deste descritor em bytes |
| 1      | bDescriptorType | 1    | Constante | Tipo de descritor de cordas           |
| 2      | wLANGID[0]      | 2    | Número   | Código LANGID 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | Número   | Código LANGID n                    |

Outros descritores de cordas USB são codificados da seguinte forma.

| Desvio | Campo           | Tamanho | Valor    | Descrição                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | Número   | Tamanho deste descritor em bytes |
| 1      | bDescriptorType | 1    | Constante | Tipo de descritor de cordas           |
| 2      | bString         | n    | Número   | Cadeia codificada UNICODE           |

USBX define um descritor de cordas USB de comprimento não zero da seguinte forma:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Descritores funcionais

Os descritores funcionais também são conhecidos como descritores específicos da classe. Normalmente usam as mesmas estruturas básicas que descritores genéricos e permitem que informações adicionais estejam disponíveis para a classe. Por exemplo, no caso do altifalante de áudio USB, os descritores específicos da classe permitem que a classe de áudio recupere para cada definição alternativa o tipo de frequência de áudio suportada.

### <a name="usbx-device-descriptor-framework-in-memory"></a>Quadro de descritor de dispositivo USBX na memória

USBX mantém a maioria dos descritores de dispositivos na memória, isto é, todos os descritores, exceto os descritores de cadeia e funcional. O diagrama seguinte mostra como estes descritores são armazenados e relacionados.

![Quadro de descritor de dispositivo USBX na memória](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
