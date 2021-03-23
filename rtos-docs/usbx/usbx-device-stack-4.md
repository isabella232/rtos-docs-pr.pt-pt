---
title: Capítulo 4 - Descrição dos Serviços de Dispositivos USBX
description: Saiba mais sobre os Serviços de Dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828136"
---
# <a name="description-of-usbx-device-services"></a>Descrição dos Serviços de Dispositivos USBX

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Obtenha a definição alternativa atual para um valor de interface

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Descrição

Esta função é utilizada pelo anfitrião USB para obter a definição alternativa atual para um valor de interface específico. É chamado pelo controlador quando um **pedido de GET_INTERFACE** é recebido.

### <a name="input-parameter"></a>Parâmetro de entrada

- **Interface_value** Valor da interface para o qual a definição alternativa atual é consultada

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_ERROR** (0xFF) Valor errado da interface.

### <a name="example"></a>Exemplo

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Definir a definição alternativa de corrente para um valor de interface

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Descrição

Esta função é utilizada pelo anfitrião USB para definir a definição alternativa atual para um valor de interface específico. É chamado pelo controlador quando um **pedido de SET_INTERFACE** é recebido. Quando o **SET_INTERFACE** estiver concluído, os valores das definições alternativas são aplicados à classe.

A pilha de dispositivo emitirá um **UX_SLAVE_CLASS_COMMAND_CHANGE** para a classe que detém esta interface para refletir a mudança de configuração alternativa.

### <a name="parameters"></a>Parâmetros

- **interface_value**: Valor da interface para o qual a definição alternativa atual é definida.
- **alternate_setting_value**: O novo valor de regulação alternativo.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Nenhuma interface ligada.
- **UX_FUNCTION_NOT_SUPPORTED** dispositivo (0x54) não está configurado.
- **UX_ERROR** (0xFF) Valor errado da interface.

### <a name="example"></a>Exemplo

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Registar uma nova classe de dispositivo USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Descrição

Esta função é utilizada pela aplicação para registar uma nova classe de dispositivo USB. Esta inscrição inicia um contentor de classe e não um exemplo da classe. Uma classe deve ter um fio ativo e ser anexada a uma interface específica.

Algumas classes esperam uma lista de parâmetros ou parâmetros. Por exemplo, a classe de armazenamento do dispositivo esperaria a geometria do dispositivo de armazenamento que está a tentar imitar. O campo de parâmetros depende, portanto, da exigência de classe e pode ser um valor ou um ponteiro para uma estrutura preenchida com os valores de classe.

> [!NOTE]
> A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parâmetros

- **class_name** Nome da classe
- **class_entry_function** A função de entrada da classe.
- **configuration_number** O número de configuração a que esta classe está anexada.
- **interface_number** O número de interface a que esta classe está anexada.
- **parâmetro** Um ponteiro para uma lista de parâmetros específicos de classe.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A classe foi registada
- **UX_MEMORY_INSUFFICIENT** (0x12) Não há entradas na tabela de aulas.
- **UX_THREAD_ERROR** (0x16) Não pode criar um fio de classe.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Não registar uma classe de dispositivo USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Descrição

Esta função é utilizada pela aplicação para não registar uma classe de dispositivo USB.

> [!NOTE]
> A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parâmetros

- **class_name**: Nome da classe
- **class_entry_function**: A função de entrada da classe.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A aula não estava registada.
- **UX_NO_CLASS_MATCH** (0x57) A classe não está registada.

### <a name="example"></a>Exemplo

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

Obtenha a configuração atual

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Descrição

Esta função é utilizada pelo anfitrião para obter a configuração atual em execução no dispositivo.

### <a name="input-parameter"></a>Parâmetro de entrada

Nenhum

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Definir a configuração atual

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Descrição

Esta função é utilizada pelo anfitrião para definir a configuração atual em execução no dispositivo. Após a receção deste comando, a pilha de dispositivo USB ativará a definição alternativa 0 de cada interface ligada a esta configuração.

### <a name="input-parameter"></a>Parâmetro de entrada

- **configuration_value** O valor de configuração selecionado pelo anfitrião.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A configuração foi definida com sucesso.

### <a name="example"></a>Exemplo

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Envie um descritor para o anfitrião

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Descrição

Esta função é utilizada pelo lado do dispositivo para devolver um descritor ao hospedeiro. Este descritor pode ser um descritor de dispositivos, um descritor de configuração ou um descritor de cordas.

### <a name="parameters"></a>Parâmetros

- **descriptor_type:** O tipo de descritor. Deve ser um dos seguintes valores.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index:** O índice do descritor.
- **host_length**: O comprimento exigido pelo hospedeiro.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência de dados foi concluída.
- **UX_ERROR** (0xFF) A transferência não foi concluída.

### <a name="example"></a>Exemplo

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

Desconexão da pilha de dispositivos

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Descrição

O gestor VBUS chama a esta função quando há uma desconexão do dispositivo. A pilha do dispositivo informará todas as classes registadas neste dispositivo e, posteriormente, libertará todos os recursos do dispositivo.

### <a name="input-parameter"></a>Parâmetro de entrada

Nenhum

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) O aparelho foi desligado.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Pedido condição de paragem de ponto final

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Descrição

Esta função é chamada pela classe do dispositivo USB quando um ponto final deve devolver uma condição de Paragem ao anfitrião.

### <a name="input-parameter"></a>Parâmetro de entrada

- **ponto final** O ponto final sobre o qual é solicitada a condição de Stall.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) O aparelho encontra-se num estado inválido.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Acorde o anfitrião

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Descrição

Esta função é chamada quando o dispositivo quer acordar o hospedeiro. Este comando só é válido quando o dispositivo estiver em modo de suspensão. Cabe à aplicação do dispositivo decidir quando pretende acordar o anfitrião USB. Por exemplo, um modem USB pode acordar um hospedeiro quando deteta um sinal RING na linha telefónica.

### <a name="input-parameter"></a>Parâmetro de entrada

Nenhum

### <a name="return-values"></a>Valores de retorno

- **UX_SUCCESS** (0x00) A chamada foi bem sucedida.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) A chamada falhou (o aparelho provavelmente não estava no modo suspenso).

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Inicialize a pilha de dispositivo USB

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Descrição

Esta função é chamada pela aplicação para inicializar a pilha de dispositivo USB. Não inicializa nenhuma aula ou controlador. Isto deve ser feito com chamadas de função separadas. Esta chamada fornece principalmente a pilha com a estrutura do dispositivo para a função USB. Suporta velocidades altas e a toda a velocidade com a possibilidade de ter uma estrutura de dispositivo completamente separada para cada velocidade. A estrutura de cordas e várias línguas são suportadas.

### <a name="parameters"></a>Parâmetros

- **device_framework_high_speed**: Ponteiro para a estrutura de alta velocidade.
- **device_framework_length_high_speed**: Comprimento da estrutura de alta velocidade.
- **device_framework_full_speed**: Ponteiro para a estrutura de velocidade máxima.
- **device_framework_length_full_speed**: Comprimento da estrutura de velocidade máxima.
- **string_framework**: Ponteiro para a estrutura das cordas.
- **string_framework_length**: Comprimento da estrutura das cordas.
- **language_id_framework**: Ponteiro para a estrutura da linguagem das cordas.
- **language_id_framework_length**: Comprimento da estrutura da linguagem de cordas.
- **ux_system_slave_change_function**: Função a ser chamada quando o estado do dispositivo mudar.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para inicializar a pilha.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) O descritor é inválido.

### <a name="example"></a>Exemplo

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

O pedido pode solicitar uma chamada de volta quando o controlador alterar o seu estado. Os dois principais estados do controlador são:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Se a aplicação não necessitar de sinais de suspensão/retoma, fornecerá uma função UX_NULL.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

Excluir uma interface de pilha

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Descrição

Esta função é chamada quando uma interface deve ser removida. Uma interface é removida quando um dispositivo é extraído, ou após um reset do autocarro, ou quando há uma nova definição alternativa.

### <a name="input-parameter"></a>Parâmetro de entrada

- **interface**: Ponteiro para a interface a remover.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Obtenha o valor atual da interface

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Descrição

Esta função é chamada quando o anfitrião consulta a interface atual. O dispositivo devolve o valor atual da interface.

> [!NOTE]
> Esta função é prevadida. Está disponível para software antigo, mas o novo software deve utilizar a ***função ux_device_stack_alternate_setting_get.***

### <a name="input-parameter"></a>Parâmetro de entrada

- **interface_value** Valor da interface para devolver.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Não existe interface.

### <a name="example"></a>Exemplo

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Alterar a definição alternativa da interface

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Descrição

Esta função é chamada quando o anfitrião solicita uma alteração da definição alternativa para a interface.

### <a name="parameters"></a>Parâmetros

- **device_framework**: Endereço da estrutura do dispositivo para esta interface.
- **device_framework_length**: Comprimento da estrutura do dispositivo.
- **alternate_setting_value**: Valor de definição alternativo a utilizar por esta interface.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_ERROR** (0xFF) Não existe interface.

### <a name="example"></a>Exemplo

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

Comece a procurar uma classe para possuir uma instância de interface

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Descrição

Esta função é chamada quando uma interface foi selecionada pelo anfitrião e a pilha de dispositivos precisa de procurar uma classe de dispositivo para possuir esta instância de interface.

### <a name="input-parameter"></a>Parâmetro de entrada

- **interface**: Ponteiro para a interface criada.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_NO_CLASS_MATCH** (0x57) Não existe classe para esta interface.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Pedido de transferência de dados para o anfitrião

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Descrição

Esta função é chamada quando uma classe ou a stack quer transferir dados para o anfitrião. O anfitrião sempre sonda o dispositivo, mas o dispositivo pode preparar dados com antecedência.

### <a name="parameters"></a>Parâmetros

- **transfer_request**: Ponteiro para o pedido de transferência.
- **slave_length**: Comprimento o aparelho quer voltar.
- **host_length:** Comprimento solicitado pelo anfitrião.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
- **UX_TRANSFER_NOT_READY** (0x25) O dispositivo encontra-se num estado inválido; deve ser **fixado,** **configurado,** ou **endereçado**.
- **UX_ERROR** (0xFF) Erro de transporte.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

Cancelar um pedido de transferência

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Descrição

Esta função é chamada quando uma aplicação precisa cancelar um pedido de transferência ou quando a stack precisa abortar um pedido de transferência associado a um ponto final.

### <a name="parameters"></a>Parâmetros

- **transfer_request**: Ponteiro para o pedido de transferência.
- **completion_code:** Código de erro a devolver à classe à espera que este pedido de transferência seja concluído.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Esta operação foi bem sucedida.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Pilha de unitialização

### <a name="prototype"></a>Prototype

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Descrição

Esta função é chamada quando uma aplicação precisa de unitizar a pilha de dispositivos USBX – todos os recursos de pilha de dispositivos são libertados. Isto deve ser chamado depois de todas as aulas não terem sido registadas através de ux_device_stack_class_unregister.

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="return-value"></a>Devolver Valor

**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.
