---
title: Capítulo 11 - Formato do tampão de vestígios de evento
description: A ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços Azure RTOS ThreadX, alterações de estado de thread e eventos definidos pelo utilizador.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827577"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Capítulo 11 - Formato do tampão de vestígios de evento

O Azure RTOS ThreadX fornece suporte de rastreio de eventos incorporados para todos os serviços da ThreadX, alterações do estado do fio e eventos definidos pelo utilizador. Para utilizar vestígios de eventos, basta construir as bibliotecas ThreadX, NetX e FileX com **TX_ENABLE_EVENT_TRACE** definidas e ativar o rastreio, chamando a função **_tx_trace_enable._** Este capítulo descreve este processo.

## <a name="event-trace-format"></a>Formato de rastreio de eventos

O formato do tampão de rastreio de evento ThreadX é dividido em três secções, nomeadamente o cabeçalho de controlo, o registo de objetos e as entradas de vestígios. O seguinte descreve o layout geral do tampão de rastreio de evento ThreadX:

**Cabeçalho de controlo**

**Entrada do Registo de Objetos 0**

**…**

**Entrada de Registo de Objetos "n"**

**Entrada de rastreio de evento 0**

**…**

**Entrada de vestígios de evento "n"**

### <a name="event-trace-control-header"></a>Cabeçalho de controlo de vestígios de evento

O cabeçalho de controlo define o layout exato do tampão de vestígios do evento. Isto inclui quantos objetos ThreadX podem ser registados, bem como quantos eventos podem ser gravados. Além disso, o cabeçalho de controlo define onde reside cada um dos elementos do tampão de vestígios. A seguinte estrutura de dados define o cabeçalho de controlo:

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>ID do cabeçalho de controlo

O ID do cabeçalho de controlo consiste no valor HEX de 32 bits de 0x54585442, que corresponde aos caracteres ASCII ***TXTB***. Uma vez que este valor é escrito como uma variável não assinada de 32 bits, também pode ser usado para detetar a endianidade do tampão de traço de evento. Por exemplo, se o valor nos primeiros quatro byes da memória for 0x54, 0x58, 0x54, 0x42, o tampão de traço de evento foi escrito em grande formato endiano. Caso contrário, o tampão de traço do evento foi escrito em pequeno formato endiano.

### <a name="timer-valid-mask"></a>Máscara válida do temporizador

A máscara válida do temporizador define quantas bits do relógio de tempo nas entradas de vestígios de eventos reais são válidas. Por exemplo, se a fonte de carimbo de tempo tiver 16 bits, o valor neste campo deve ser 0xFFFF. Uma fonte de selo de 32 bits teria um valor de 0xFFFFFFFF. Este valor é definido pela ***TX_TRACE_TIME_MASK** _ constante em _*_tx_port.h_**.

### <a name="trace-base-address"></a>Endereço base de rastreio

O endereço da base de tampão de traços é o endereço que a aplicação especifica como o início do tampão de rastreio na chamada ***tx_trace_enable.*** Este endereço é mantido para a utilização exclusiva da ferramenta de análise para obter compensações bufferrelativas para os vários elementos do tampão. Por exemplo, a compensação relativa tampão do evento atual no tampão de vestígios é calculada por simples subtração do endereço de base a partir do endereço do evento atual.

### <a name="registry-start-and-end-pointers"></a>Ponteiros de início e fim do registo

O ponteiro de início do registo aponta para o endereço da primeira entrada de registo de objetos, enquanto o ponteiro final do registo aponta para o endereço im.. /mediativamente após a última entrada de registo. Estes valores são configurados durante o processamento *tx_trace_enable* e não são alterados durante a duração do rastreio.

### <a name="registry-name-size"></a>Tamanho do nome do registo

O tamanho do nome do registo define o tamanho máximo em bytes para cada nome de objeto na entrada do registo e é definido pelo símbolo ***TX_TRACE_OBJECT_REGISTRY_NAME** _. O valor predefinido é de 32 e é definido em _*_tx_trace.h_*_. O nome do objeto corresponde ao nome dado pela aplicação quando o objeto foi criado. Por exemplo, o nome do registo do objeto para um fio é o nome fornecido pela aplicação à chamada _*_tx_thread_create_**.

### <a name="buffer-start-and-end-pointers"></a>Ponteiros de início e fim do tampão

O ponto de partida do marcador do resultado aponta para o endereço da primeira entrada de vestígios, enquanto o ponteiro final do registo aponta para o endereço im. /mediativamente seguindo a última entrada de vestígios. Estes valores são configurados durante o ***tx_trace_enable</processamento*** e não são alterados durante toda a duração do rastreio.

### <a name="current-buffer-pointer"></a>Ponteiro-tampão atual

O ponto de marcação do ponto de corrente do evento aponta para o endereço da entrada de vestígios mais antigo. Uma vez que as entradas de vestígios são mantidas numa lista circular, o ponteiro-tampão atual também representa a próxima entrada de vestígios a ser escrita. |

## <a name="event-trace-object-registry"></a>Registo de objetos de rastreio de evento

O registo de objetos de rastreio de eventos contém ***n** _ entradas de registo de objetos que correspondem aos objetos criados pela aplicação. O principal objetivo do registo de objetos é que as ferramentas de análise externas correlacionem os nomes reais dos objetos com os endereços do objeto das entradas do tampão de traço. O número de entradas de registo é especificado pela aplicação na chamada _ *_tx_trace_enable_** .

Cada entrada de registo de objetos contém informações sobre um objeto ThreadX específico previamente criado pela aplicação. A seguinte estrutura de dados define cada entrada de registo de objetos:

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>Bandeira disponível de objeto

A bandeira disponível do objeto é definida para 1 se a entrada do registo do objeto estiver disponível. Caso contrário, se o valor não for 1, a entrada no registo do objeto não está disponível. Note que a entrada ainda pode conter informações válidas, mesmo estando disponível.

### <a name="object-entry-type"></a>Tipo de entrada de objeto

O tipo de entrada do objeto identifica o tipo de objeto nesta entrada. Segue-se uma lista dos tipos de objetos válidos:

| **Valor** | **Tipo de Objeto** |
|---------- | --------------- |
| 0         | Não é válido       |
| 1         | Fio          |
| 2         | Temporizador |
| 3         | Fila |
| 4         | Semáforo |
| 5         | Mutex |
| 6         | Grupo de Bandeiras de Eventos |
| 7         | Piscina de Blocos |
| 8         | Piscina Byte |
| 9         | .. /media |
| 10        | Ficheiro |
| 11        | IP |
| 12        | Piscina de Pacotes |
| 13        | Tomada TCP |
| 14        | Tomada UDP |
| 15-20     | Reservado |  
| 21        | Dispositivo usb host Stack |
| 22        | Interface de pilha de anfitrião USB |
| 23        | Ponto final do anfitrião USB |
| 24        | Classe de anfitrião USB |
| 25        | Dispositivo USB |
| 26        | Interface do dispositivo USB |
| 27        | Ponto de final do dispositivo USB |
| 28        | Classe de dispositivo USB |

### <a name="object-pointer"></a>Ponteiro de objetos

O ponteiro do objeto especifica o endereço do objeto que é utilizado para aceder ao objeto utilizando a API ThreadX.

### <a name="object-reserved-fields"></a>Campos Reservados a Objetos

Para todos os objetos que não sejam fios, estes campos reservados devem ser 0. Para os fios, a prioridade do fio no momento da sua entrada no registo é colocada nestes dois campos reservados.

### <a name="object-parameters"></a>Parâmetros de objeto

Os parâmetros do objeto contêm informações suplementares sobre o objeto. O seguinte descreve as informações suplementares para cada objeto ThreadX:

| **Tipo de Objeto**        | **Parâmetro 1**  | **Parâmetro 2** |
|----------------------- | ---------------- | --------------- |
| Fio                 | Início da Pilha      | Tamanho da pilha |
| Temporizador                  | Carrapatos Iniciais | Reagendar Carrapatos |
| Fila                  | Tamanho da fila | Tamanho da mensagem |
| Semáforo              | Instâncias Iniciais | - |
| Mutex                  | Bandeira da herança | - |
| Grupo de Bandeiras de Eventos      | - | - |
| Piscina de Blocos             | Total de Blocos | Tamanho do Bloco |
| Piscina Byte              | Total Bytes | - |
| .. /media                  | Tamanho da cache de gordura | Tamanho da cache do setor |
| Ficheiro                   | - | - |
| IP                     | Início da Pilha | Tamanho da pilha |
| Piscina de Pacotes            | Tamanho do pacote | Número de Pacotes |
| Tomada TCP             | Endereço IP | Tamanho da janela |
| Tomada UDP             | Endereço IP | RX Queue Max |

### <a name="object-name"></a>Nome do objeto

O nome do objeto contém o nome do objeto ThreadX. O nome é o nome fornecido à ThreadX no momento em que o objeto foi criado. Por predefinição, o nome do objeto tem um máximo de 32 caracteres. Nomes reais superiores a 32 caracteres são truncados.

## <a name="event-trace-entries"></a>Entradas de rastreio de eventos

As entradas de vestígios do evento são encontradas na parte inferior do tampão de vestígios do evento. As entradas são mantidas numa lista circular, com o ponteiro de entrada atual a apontar para a entrada mais antiga. O número de entradas na lista é calculado pela ***chamada tx_trace_enable.***

Cada entrada de registo de objetos contém informações sobre um evento específico de traços ThreadX. A seguinte estrutura de dados define cada entrada de evento de vestígios:

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>Ponteiro de fio

O ponteiro de linha contém o endereço do fio em execução no momento deste evento. Se o evento ocorreu durante a inicialização (sem linha em execução), o valor deste ponteiro é 0xF0F0F0F0. Se o evento ocorreu durante uma Rotina de Serviço de Interrupção (ISR), o valor deste ponteiro é 0xFFFFFFFF. Se a entrada ainda não tiver sido utilizada, o valor deste ponteiro é 0.

### <a name="thread-priority"></a>Prioridade do fio

O campo prioritário da linha contém a prioridade do fio e o limiar de preempção do fio que estava a ser em execução no momento deste evento. Se estiver presente um contexto de interrupção (o ponteiro de linha é 0xFFFFFFFF), o valor deste campo não é a prioridade, mas sim o valor de ***_tx_thread_current_ptr*** no momento do evento. Caso contrário, o valor deste campo é 0.

### <a name="event-id"></a>ID do Evento

O ID do evento especifica o evento que ocorreu. Os IDs válidos do evento ThreadX variam de 1 a 1024. Os valores a partir de 1025 e acima são reservados para eventos específicos do utilizador. Consulte o ficheiro ***tx_trace.h*** para a definição completa de IDs de eventos ThreadX.</td>

### <a name="information-fields-1-4"></a>Campos de Informação (1-4)

Os campos de informação contêm informações adicionais sobre o evento específico. Consulte o ficheiro ***tx_trace.h*** para obter a descrição completa dos campos de informação de cada um dos IDs de eventos definidos da ThreadX.