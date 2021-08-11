---
title: Capítulo 4 - Descrição dos serviços de anfitrião USBX
description: Saiba mais sobre os Serviços de Anfitrião USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6cbeff83d8e3812f13aa3f8f66d4013b70490d556911939186b4b43840aac50d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790688"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Capítulo 4 - Descrição dos serviços de anfitrião USBX

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Inicialize o USBX para a operação do anfitrião.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Description

Esta função irá inicializar a pilha de anfitriões USB. A área de memória fornecida será configurada para utilização interna USBX. Se UX_SUCCESS for devolvido, o USBX está pronto para o controlador de anfitrião e para o registo da classe.

### <a name="input-parameter"></a>Parâmetro de entrada

- **system_change_function** Ponteiro para a rotina de retorno opcional para notificar a aplicação de alterações do dispositivo.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) Inicialização bem sucedida.
- **UX_MEMORY_INSUFFICIENT** (0x12) Uma atribuição de memória falhou.

### <a name="example"></a>Exemplo

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Abortar todas as transações anexas a um pedido de transferência para um ponto final.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

Esta função irá cancelar todas as transações ativas ou pendentes para um pedido de transferência específico anexado a um ponto final. O pedido de transferência tem uma função de retorno anexada, a função de retorno será chamada com o estado de UX_TRANSACTION_ABORTED.

### <a name="input-parameter"></a>Parâmetro de entrada

- **ponto final** Apontador para um ponto final.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Sem erros.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) A pega endpoint não é válida.

### <a name="example"></a>Exemplo

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

Pegue o ponteiro para um recipiente de classe.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Description

Esta função devolve um ponteiro ao recipiente de classe. Uma classe precisa de obter o seu recipiente a partir da pilha USB para procurar casos em que uma classe ou uma aplicação quer abrir um dispositivo.

> [!NOTE]
> A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Parâmetros

- **class_name** Apontador para o nome da classe.
- **classe** Um ponteiro atualizado pela chamada de função que contém o recipiente de classe para o nome da classe.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Sem erros, no retorno o campo de aula é arquivado com o ponteiro para o recipiente de classe.
- **UX_HOST_CLASS_UNKNOWN** classe (0x59) é desconhecida pela pilha.

### <a name="example"></a>Exemplo

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Registe uma classe USB na pilha USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Description

Esta função regista uma classe USB para a pilha USB. A classe deve especificar um ponto de entrada para a pilha USB enviar comandos como o seguinte.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> A cadeia C de *class_name* deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Parâmetros

- **class_name** Ponteiros do nome da classe, as entradas válidas encontram-se no ficheiro ux_system_initialize.c nas classes USBX.
- **class_entry_address** Endereço da função de entrada da classe.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) Classe instalada com sucesso.
- **UX_MEMORY_ARRAY_FULL** (0x1a) Não há mais memória para armazenar esta classe.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Classe de anfitrião já instalada.

### <a name="example"></a>Exemplo:

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Crie uma nova instância de classe para um recipiente de classe.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

Esta função cria uma nova instância de classe para um recipiente de classe. O caso de uma classe não está contido no código de classe para reduzir a complexidade da classe. Em vez disso, cada instância de classe é anexada ao recipiente de classe localizado na pilha principal.

### <a name="parameters"></a>Parâmetros

- **classe** Ponteiro para o recipiente da classe.
- **class_instance** Ponteiro para a instância de classe a criar.

### <a name="return-value"></a>Devolver Valor

- **UX_SUCCESS** (0x00) A instância de classe foi anexada ao recipiente da classe.

### <a name="example"></a>Exemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

Destrua uma instância de classe para um recipiente de classe.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Description

Esta função destrói uma instância de classe para um recipiente de classe.

### <a name="parameters"></a>Parâmetros

- **classe** Ponteiro para o recipiente da classe.
- **class_instance** Apontando para o caso para destruir.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A instância de classe foi destruída.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A instância de classe não está ligada ao recipiente de classe.

### <a name="example"></a>Exemplo

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

Arranja um ponteiro de exemplo de turma para uma aula específica.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Description

Esta função devolve um ponteiro de instância de classe para uma classe específica. O caso de uma classe não está contido no código de classe para reduzir a complexidade da classe. Pelo contrário, cada instância de classe é anexada ao recipiente de classe. Esta função é utilizada para procurar casos de classe dentro de um recipiente de classe.

### <a name="parameters"></a>Parâmetros

- **classe** Ponteiro para o recipiente da classe.
- **class_index** Um índice a utilizar pela chamada de função dentro da lista de classes anexadas ao recipiente.
- **class_instance** Ponteiro para o caso a ser devolvido pela chamada de função.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A instância de classe foi encontrada.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Não existem mais casos de classe ligados ao recipiente de classe.

### <a name="example"></a>Exemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

Obtenha um ponteiro para um recipiente de configuração.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

Esta função devolve um recipiente de configuração com base numa pega do dispositivo e num índice de configuração.

### <a name="parameters"></a>Parâmetros

- **dispositivo** Ponteiro para o recipiente do dispositivo que possui a configuração solicitada.
- **configuration_index** Índice da configuração a ser pesquisado.
- **configuração** Endereço do ponteiro para o recipiente de configuração a devolver.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A configuração foi encontrada.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) O recipiente do dispositivo não existe.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A pega de configuração do índice não existe.

### <a name="example"></a>Exemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

Selecione uma configuração específica para um dispositivo.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Description

Esta função seleciona uma configuração específica para um dispositivo. Quando esta configuração é definida para o dispositivo, por padrão, cada interface do dispositivo e a sua configuração alternativa associada 0 são ativadas no dispositivo. Se a classe dispositivo/interface pretende alterar a configuração de uma determinada interface, tem de emitir uma chamada de serviço **ux_host_stack_interface_setting_select.**

### <a name="parameters"></a>Parâmetros

- **configuração** Ponteiro para o recipiente de configuração que deve ser ativado para este dispositivo.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A seleção de configuração foi bem sucedida.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A pega de configuração não existe.
- **UX_OVER_CURRENT_CONDITION** (0x43) Existe uma condição acima da atual existente no autocarro para esta configuração.

### <a name="example"></a>Exemplo

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

Arranja um ponteiro para um contentor de dispositivos.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Description

Esta função devolve um recipiente do dispositivo com base no seu índice. O índice do dispositivo começa com 0. Note que o índice é um ULONG porque poderíamos ter vários controladores e um índice byte pode não ser suficiente. O índice do dispositivo não deve ser confundido com o endereço do dispositivo específico para o autocarro.

### <a name="parameters"></a>Parâmetros

- **device_index** Índice do dispositivo.
- **dispositivo** Endereço do ponteiro para o recipiente do dispositivo regressar.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O recipiente do dispositivo existe e é devolvido
- **dispositivo UX_DEVICE_HANDLE_UNKNOWN** (0x50) desconhecido

### <a name="example"></a>Exemplo

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Arranja um contentor de ponto final.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Description

Esta função devolve um recipiente de ponto final baseado no manípulo da interface e num índice de ponto final. Presume-se que a definição alternativa para a interface foi selecionada ou que a definição predefinida está a ser utilizada antes do ponto final ser pesquisado.

### <a name="parameters"></a>Parâmetros

- **interface** Ponteiro para o recipiente de interface que contém o ponto final solicitado.
- **endpoint_index** Índice do ponto final nesta interface.
- **ponto final** Endereço do recipiente de ponto final a devolver.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O recipiente de ponto final existe e é devolvido.
- **UX_INTERFACE_HANDLE_UNKNOWN** interface (0x52) especificada não existe.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Índice de ponto final não existe.

### <a name="example"></a>Exemplo

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

Registe um controlador USB na pilha USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Description

Esta função regista um controlador USB na pilha USB. Aloca principalmente a memória utilizada por este controlador e passa o comando de inicialização para o controlador.

### <a name="parameters"></a>Parâmetros

- **hcd_name** Nome do controlador anfitrião
- **hcd_function** A função no controlador de anfitrião responsável pela inicialização.
- **hcd_param1** O IO ou o recurso de memória utilizado pelo hcd.
- **hcd_param2** O IRQ usado pelo controlador hospedeiro.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O controlador foi inicializado corretamente.
- **UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para este controlador.
- **UX_PORT_RESET_FAILED** (0x31) O reset do controlador falhou.
- **UX_CONTROLLER_INIT_FAILED** (0x32) O controlador não iniciais corretamente.

### <a name="example"></a>Exemplo

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

Arranja um ponteiro de contentor de interface.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Description

Esta função devolve um recipiente de interface com base num cabo de configuração, num índice de interface e num índice de definição alternativo.

### <a name="parameters"></a>Parâmetros

- **configuração** Ponteiro para o recipiente de configuração que possui a interface.
- **interface_index** Índice de interface a ser pesquisado.
- **alternate_setting_index** Definição alternativa dentro da interface para pesquisar.
- **interface** Endereço do ponteiro do recipiente de interface a ser devolvido.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) O recipiente de interface para o índice de interface e a definição alternativa foi encontrado e devolvido.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A configuração não existe.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) A interface não existe.

### <a name="example"></a>Exemplo

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Selecione uma definição alternativa para uma interface.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Description

Esta função seleciona uma definição alternativa específica para uma determinada interface pertencente à configuração selecionada. Esta função é utilizada para alterar da definição alternativa predefinida para uma nova definição ou para voltar à definição alternativa predefinida. Quando uma nova definição alternativa é selecionada, as características do ponto final anterior são inválidas e devem ser recarregadas.

### <a name="input-parameter"></a>Parâmetro de entrada

- **interface** Ponteiro para o recipiente de interface cuja definição alternativa deve ser selecionada.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A definição alternativa para esta interface foi selecionada com sucesso.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) A interface não existe.

### <a name="example"></a>Exemplo

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Abortar um pedido de transferência pendente.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

Esta função aborta um pedido de transferência pendente que foi previamente apresentado. Esta função apenas cancela um pedido de transferência específico. A chamada de volta para a função terá o estado de UX_TRANSFER REQUEST_STATUS_ABORT.

### <a name="parameters"></a>Parâmetros

- **pedido de transferência** Ponteiro para o pedido de transferência a ser abortado.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência USB para este pedido de transferência foi cancelada.

### <a name="example"></a>Exemplo

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

Solicite uma transferência USB.

### <a name="prototype"></a>Prototype

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Description

Esta função executa uma transação USB. À entrada, o pedido de transferência dá o tubo de ponto final selecionado para esta transação e os parâmetros associados à transferência (carga útil de dados, duração da transação). Para o tubo de controlo, a transação está bloqueada e só regressará quando as três fases da transferência de controlo estiverem concluídas ou se houver um erro anterior. Para outros tubos, a pilha USB irá agendar a transação na USB, mas não esperará pela sua conclusão. Cada pedido de transferência de tubos não bloqueados tem de especificar um manipulador de rotina de conclusão.

Quando a chamada de função retornar, o estado do pedido de transferência deve ser examinado, uma vez que contém o resultado da transação.

### <a name="input-parameter"></a>Parâmetro de entrada

- **transfer_request** Ponteiro para o pedido de transferência. O pedido de transferência contém todas as informações necessárias para a transferência.

### <a name="return-values"></a>Valores de devolução

- **UX_SUCCESS** (0x00) A transferência USB para este pedido de transferência foi devidamente agendada. O código de estado do pedido de transferência deve ser examinado quando o pedido de transferência estiver concluído.
- **UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para alocar os recursos controladores necessários.
- **UX_TRANSFER_NOT_READY** (0x25) O aparelho encontrava-se num estado inválido – deve ser anexado, endereçado ou configurado.

### <a name="example"></a>Exemplo:

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
