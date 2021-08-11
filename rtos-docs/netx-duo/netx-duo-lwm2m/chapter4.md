---
title: Capítulo 4 - Descrição dos Serviços LWM2M CLIENTE
description: Este capítulo contém uma descrição de todos os serviços do Cliente LWM2M por ordem alfabética.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0956cb43f4fcd87d5bd4d90b2288ce6f8d5295ee0be8b8a9f4719ad842e00b2a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783446"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Capítulo 4 Descrição dos serviços LWM2M CLIENTE

Este capítulo contém uma descrição de todos os serviços do Cliente LWM2M listados abaixo por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo  **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

**Gestão de Clientes LWM2M:**

- nx_lwm2m_client_create: *Criar cliente LWM2M*

- nx_lwm2m_client_delete: *Eliminar cliente LWM2M*

- nx_lwm2m_client_lock: Bloquear *cliente LWM2M*

- nx_lwm2m_client_unlock: Desbloquear *Cliente LWM2M*

**Gestão de Sessão de Clientes LWM2M:**

- nx_lwm2m_client_session_create: *Criar sessão de clientes LWM2M*

- nx_lwm2m_client_session_delete: Eliminar *sessão de clientes LWM2M*

- nx_lwm2m_client_session_bootstrap: Inicie *uma sessão com um Servidor Bootstrap*

- nx_lwm2m_client_session_bootstrap_dtls: Inicie *uma sessão segura com um Servidor Bootstrap*

- nx_lwm2m_client_session_register_info_get: Obtenha *informações de registo do servidor LWM2M*

- nx_lwm2m_client_session_register: Inicie *uma sessão com um Servidor LWM2M*

- nx_lwm2m_client_session_register_dtls: Inicie *uma sessão segura com um Servidor LWM2M*

- nx_lwm2m_client_session_update: Atualizar *uma sessão com um Servidor LWM2M*

- nx_lwm2m_client_session_deregister: Terminar *uma sessão com um servidor LWM2M*

- nx_lwm2m_client_session_error_get: Obtenha *o último erro de uma sessão*

**Implementação do objeto do dispositivo:**

- nx_lwm2m_client_device_callbacks_set: *Definir chamadas de aplicação de objeto de dispositivo*

- nx_lwm2m_client_device_error_push: Adicionar *código de erro ao objeto do dispositivo*

- nx_lwm2m_client_device_error_reset: Redefinir *códigos de erro do objeto do dispositivo*

- nx_lwm2m_client_device_resource_changed: *Alteração do sinal do recurso objeto do dispositivo*

**Implementação do objeto de atualização de firmware:**

- nx_lwm2m_firmware_create: Criar *objeto de atualização de firmware*

- nx_lwm2m_firmware_package_info_set: Definir *informações do pacote de atualização de firmware*

- nx_lwm2m_firmware_result_set: Definir *resultado da atualização do firmware*

- nx_lwm2m_firmware_state_set: Definir *Estado de Atualização de Firmware*

**Implementação de objetos personalizados:**

- nx_lwm2m_client_object_add: Adicionar *implementação de objeto ao cliente LWM2M*

- nx_lwm2m_client_object_remove: Remover *a implementação do objeto do cliente LWM2M*

- nx_lwm2m_client_object_instance_add: Adicionar *instância de objeto ao cliente LWM2M*

- nx_lwm2m_client_object_instance_remove: Remover *a instância do objeto do cliente LWM2M*

- nx_lwm2m_object_resource_changed: Alteração *do sinal de um valor de recurso de uma Instância de Objeto*

**Gestão local de dispositivos**

- nx_lwm2m_client_object_create: Criar *uma nova instância de objeto*

- nx_lwm2m_client_object_delete: Eliminar *uma instância de objeto*

- nx_lwm2m_client_object_discover: Descubra *os recursos de uma instância de objeto*

- nx_lwm2m_client_object_execute: Executar *recurso de uma instância de objeto*

- nx_lwm2m_client_object_next_get: *Obtenha a lista de Objetos implementados pelo Cliente LWM2M*

- nx_lwm2m_client_object_instance_next_get: *Obtenha a lista de instâncias de um objeto*

- nx_lwm2m_client_object_read: Ler *os valores dos recursos de uma Instância de Objeto*

- nx_lwm2m_client_object_write: Alterar *os valores de recursos de uma instância de objeto*

**Definição de Informações e Valores de Recursos:**

- nx_lwm2m_client_resource_info_set: Definir *a informação de recursos*

- nx_lwm2m_client_resource_string_set: *Definir o valor do recurso como cadeia*

- nx_lwm2m_client_resource_integer32_set: *Desaprote o valor do recurso como inteiro de 32 Bits*

- nx_lwm2m_client_resource_integer64_set: *Desaprote o valor do recurso como inteiro de 64 Bits*

- nx_lwm2m_client_resource_float32_set: *Desaprova o valor do recurso como boia de 32 Bits*

- nx_lwm2m_client_resource_float64_set: *Desaprova o valor do recurso como boia de 64 Bits*

- nx_lwm2m_client_resource_boolean_set: *Desaprova o valor do recurso como boolean*

- nx_lwm2m_client_resource_objlnk_set: Definir *o valor do recurso como ligação de objeto*

- nx_lwm2m_client_resource_opaque_set: Definir *o valor do recurso como opaco*

- nx_lwm2m_client_resource_instance_set: Definir *o valor do recurso como exemplo para vários recursos*
-
- nx_lwm2m_client_resource_dim_set: *Deslote a dimensão do recurso para recursos múltiplos.*

**Informação de Recursos e Valores Obtenção:**

- nx_lwm2m_client_resource_info_get: Obtenha *a informação de recursos*

- nx_lwm2m_client_resource_string_get: Obtenha *o valor de um recurso de corda*

- nx_lwm2m_client_resource_integer32_get: Obtenha *o valor de um recurso inteiro de 32 Bits*

- nx_lwm2m_client_resource_integer64_get: *Obtenha o valor de um recurso inteiro de 64 Bits*

- nx_lwm2m_client_resource_float32_get: Obtenha *o valor de um recurso flutuante de 32 Bits*

- nx_lwm2m_client_resource_float64_get: *Obtenha o valor de um recurso flutuante de 64 Bits*

- nx_lwm2m_client_resource_boolean_get: *Obtenha o valor de um recurso booleano*

- nx_lwm2m_client_resource_objlnk_get: Obtenha *o valor de um recurso de ligação de objeto*

- nx_lwm2m_client_resource_opaque_get: Obtenha *o valor de um recurso opaco*

- nx_lwm2m_client_resource_instance_get: Obtenha *a instância de recursos para vários recursos*

- nx_lwm2m_client_resource_dim_get: Obtenha *a dimensão do recurso para recursos múltiplos.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Cria um cliente LWM2M.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Description

Este serviço cria uma instância de cliente LWM2M, que funciona no contexto da sua própria linha ThreadX.

O Cliente LWM2M implementa os seguintes objetos OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3). As implementações dos outros objetos devem ser adicionadas pela aplicação.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **ip_ptr** Ponteiro para instância IP previamente criada.
- **packet_pool_ptr** Ponteiro para a piscina de pacotes predefinidos para este Cliente LWM2M.
- **name_ptr** Ponteiro para o nome do ponto final do cliente LWM2M.
- **name_length** Comprimento do nome do ponto final do cliente LWM2M.
- **msisdn_ptr** O ponteiro para o MSISDN onde o Cliente LWM2M pode ser contactado para ser utilizado com a ligação SMS, pode ser NULO se a ligação SMS não for suportada.
- **msisdn_length** Comprimento do número MSISDN.
- **binding_modes** A encadernação e os modos suportados pelo Cliente LWM2M devem ser uma combinação de NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S e bandeiras NX_LWM2M_BINDING_SQ.
- **stack_ptr** Ponteiro para a área de pilha de fio do cliente LWM2M.
- **stack_size** O tamanho da pilha de fio do cliente LWM2M.
- **prioridade** Prioridade do Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** O Cliente LWM2M foi criado com sucesso.
- **NX_LWM2M_CLIENT_ERROR** O Cliente LWM2M cria erro.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.
- **NX_PTR_ERROR** Ponteiro inválido.
- **NX_SIZE_ERROR** Tamanho da pilha inválida.
- **NX_OPTION_ERROR** Prioridade inválida.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Elimina um Cliente LWM2M.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância de cliente LWM2M anteriormente criada.

Todas as sessões atualmente anexadas ao cliente também são eliminadas por esta chamada.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** O Cliente LWM2M foi eliminado com sucesso.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

Define a chamada de aplicação de um objeto do dispositivo.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Description

Este serviço instala a chamada de aplicação para implementação de operações nos recursos do Objeto de Dispositivo LWM2M que não são tratados pelo Cliente LWM2M.

O Cliente LWM2M implementa os seguintes recursos: Código de Erro (11), Código de Erro de Reset (12) e Ligação e Modos Suportados (16), as operações para os outros recursos são redirecionadas para a aplicação.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **operation_callback** A operação de chamada para "Ler", "Descobrir", "Escrever" e "Executar".

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** A chamada de operação foi definida com sucesso.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Adiciona um código de erro a um objeto do dispositivo.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Description

Este serviço adiciona uma nova instância ao recurso Error Code (11) do Dispositivo Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **código** O novo código de erro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

O número máximo de códigos de erro armazenados tem

foi alcançado.

NX_PTR_ERROR ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Reinicia os códigos de erro do Objeto do Dispositivo.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina todas as instâncias de código de erro do Objeto do Dispositivo. Isto equivale a executar o código de erro de reposição de recursos (12).

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Sinaliza uma alteração para um recurso de objeto de dispositivo.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Dispositivo De Objeto mudou. O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **recurso** Ponteiro para a estrutura descrevendo o recurso que mudou.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Crie um objeto de firmware de cliente LWM2M. 

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para criar objeto firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.
- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **protocolos** Os protocolos apoiados.
- **package_callback** A chamada do pacote.
- **package_uri_callback** O pacote uri callback.
- **update_callback** A chamada de atualização.

### <a name="return-values"></a>Valores de devolução

**NX_SUCCESS** Operação bem sucedida.
**NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

Define as informações do pacote LWM2M Client Firmware.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para definir os recursos de informação do pacote do objeto de atualização do firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.
- **nome** O nome do pacote firmware.
- **name_length** O comprimento do nome.
- **versão** A versão do pacote firmware.
- **version_length** O comprimento da versão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Define o recurso de resultado de atualização do objeto de atualização do firmware.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para definir o recurso de resultado de atualização do objeto de atualização do firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.
- **resultado** O resultado da atualização.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Define o recurso de resultado de atualização do objeto de atualização do firmware.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para definir o estado do objeto de atualização do firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr** Ponteiro para o objeto LWM2M Client Firmware.
- **estado** O estado do objeto do firmware.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Bloqueia o Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço bloqueia o Cliente LWM2M para evitar o acesso simultâneo aos objetos LWM2M dos servidores ou de outro fio de aplicação.

Se o Cliente LWM2M estiver atualmente bloqueado por outro fio, a função bloqueará até que o Cliente LWM2M seja desbloqueado.

As chamadaspara os pares _/_ *_nx_lwm2m_client_lock nx_lwm2m_client_unlock_** podem ser aninhadas.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Adiciona uma implementação de objeto ao Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Description

Este serviço adiciona uma nova implementação de Objeto ao Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.
- **object_id** O objeto identifica.
- **object_operation** A função de retorno de operação do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Cria uma nova instância de objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'Criar' num Objeto do Cliente LWM2M para criar uma nova Instância de Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id_ptr** O ponteiro para o ID da nova instância, pode ser **NULO** se o Cliente LWM2M tiver de atribuir um ID de instância. Se o ID for o valor reservado 65535, o Cliente LWM2M atribuirá um ID de instância. Se não não null, o ID atribuído é devolvido após a chamada.
- **num_values** O número de valores a definir.
- **values_ptr** Ponteiro para uma matriz de valores de recursos para inicializar a nova Instância de Objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** O ID da instância do objeto já existe.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** O Objeto não suporta a criação de exemplos.
- **NX_LWM2M_CLIENT_NO_MEMORY** Não é possível alocar memória para armazenar o novo caso.
- **NX_LWM2M_CLIENT_NOT_FOUND** A identificação do objeto não existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Elimina uma Instância de Objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'Eliminar' numa Instância de Objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id** A identificação do caso do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** O Objeto não suporta a eliminação de exemplos.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Descobre recursos de uma Instância de Objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Description

Este serviço executa uma operação 'Discover' numa Instância de Objeto do Cliente LWM2M, esta devolve a lista de recursos implementados pelo Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id** A identificação do caso do objeto.
- **num_resources** Na entrada do tamanho do tampão de destino, na saída o número de elementos escritos no tampão.
- **recursos** Ponteiro para o tampão de destino.

### <a name="return-values"></a>Valores de devolução

- *NX_SUCCESS* operação bem sucedida.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O amortecedor de recursos é muito pequeno para armazenar a lista de recursos.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Executa uma operação 'Executar' num recurso de uma Instância de Objeto.

### <a name="prototype"></a>Prototype

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Description

Este serviço executa a operação 'Executar' num recurso de instância de objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id** A identificação do caso do objeto.
- **resource_id** A identificação de recursos.
- **arguments_ptr** Apontando para os argumentos da operação de execução. Pode ser NULO se arguments_length for zero.
- **arguments_length** A duração dos argumentos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O amortecedor de recursos é muito pequeno para armazenar a lista de recursos.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto ou iD de instância de objeto não existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Adiciona uma implementação de instância de objeto a um objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

Este serviço adiciona uma nova implementação de instância de objeto ao Cliente LWM2M. Se o valor do instance_id_ptr for **NX_LWM2M_CLIENT_RESERVED_ID**, o Cliente LWM2M atribuirá automaticamente um id de instância não utilizado, caso contrário, o Cliente LWM2M utilizará o conjunto de aplicações de valor. Uma vez que a nova instância foi adicionada com sucesso, o instance_id será preenchido em instance_id_ptr para voltar à aplicação.

### <a name="parameters"></a>Parâmetros

- **object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.
- **instance_ptr** Ponteiro para a estrutura que define a implementação do caso Objeto.
- **instance_id_ptr** Ponteiro para o id da instância do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** O ID do objeto já existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

Obtém a próxima instância de um objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Description

Este serviço devolve o ID da próxima Instância de Objeto do Objeto dado. Se o ID de instância atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o ID da primeira instância é devolvido.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id_ptr** Ponteiro para o ID de instância de objeto atual. No retorno contém o próximo ID de instância do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_CLIENT_LWM2M_NOT_FOUND** O ID de instância dado é o último do objeto, ou o ID do objeto não é implementado.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Remove a implementação de uma instância de objeto de um objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Description

Este serviço remove uma instância de objeto de um objeto.

### <a name="parameters"></a>Parâmetros

- ***object_ptr*** Ponteiro para a estrutura que define a implementação do Objeto.
- **instance_ptr** Ponteiro para a estrutura que define a implementação do caso Objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Obtém o próximo objeto do Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Description

Este serviço devolve o ID do próximo Objeto implementado pelo Cliente LWM2M. Se o ID do objeto atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o primeiro ID do objeto é devolvido.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id_ptr** Ponteiro para o ID do objeto atual. Na devolução contém o próximo ID do Objeto implementado pelo Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID dado objeto é o último da base de dados.
**NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Lê os valores dos recursos de uma instância de objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'Ler' numa Instância de Objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id** A identificação do caso do objeto.
- **num_values** O número de recursos para ler.
- **values_ptr** Ponteiro para uma série de NX_LWM2M_RESOURCE contendo as identificações dos recursos para ler. Na volta, a matriz é preenchida com os tipos e valores correspondentes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Um recurso não suporta a operação de leitura.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto, iD de instância de objeto ou um ID de recurso não existe.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Remove a implementação de uma instância de objeto de um objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Description

Este serviço remove um Objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** O ID do objeto já existe.
- **NX_PTR_ERROR** Ponteiro inválido.
- **NX_LWM2M_CLIENT_FORBIDDEN** A remoção do objeto interno é proibida.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Sinaliza uma mudança de recurso de objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Description

O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Objeto mudou. O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **object_ptr** Ponteiro para a estrutura que define a implementação do Objeto.
- ***instance_ptr*** Ponteiro para a estrutura que define a implementação do caso Objeto.
- **recurso** Ponteiro para a estrutura descrevendo o recurso que mudou.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Altera os valores do recurso de uma instância do Objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Description

Este serviço executa uma operação de 'Write' numa Instância de Objeto do Cliente LWM2M.

As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op.*

| Valor | &nbsp;Escrever Operação | Descrição |
| --- | ---| --- |
| 0 | Atualização Parcial | Adiciona ou atualiza Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Substituir Instância | Substitui a Instância do Objeto pelos novos valores de recursos fornecidos. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Substituir recursos | Substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Escrita de Bootstrap | Indica uma chamada de uma sequência de Bootstrap. |

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id** A identificação do objeto.
- **instance_id** A identificação do caso do objeto.
- **num_values** O número de recursos para escrever.
- **values_ptr** Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos, os tipos e os valores para escrever.
- **write_op** O tipo de operação de escrita.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O tipo de recurso não é válido.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** O comprimento de um valor é demasiado grande para ser armazenado no caso.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Um recurso não suporta a operação de escrita.
- **NX_LWM2M_CLIENT_NO_MEMORY** Não é possível alocar memória para armazenar um valor de recurso.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** O valor de um recurso não é válido.
- **NX_LWM2M_CLIENT_NOT_FOUND** O ID do objeto, iD de instância de objeto ou um ID de recurso não existe.
- **NX_OPTION_ERROR** Tipo inválido de operação de escrita. 
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Obtém o valor de um Recurso Boolean.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Description

O serviço recupera o valor de um Recurso Boolean.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para descrição do valor do recurso.
- **bool_ptr** Ponteiro para o destino Valor Boolean.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Define o valor de um Recurso Boolean.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Description

O serviço define o valor de um Recurso Boolean.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **bool_data** Dados boolean.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Obtém a dimensão de recursos para vários recursos

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Description

O serviço recupera a dimensão do recurso para recursos múltiplos.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **ponteiro dim** para a dimensão do destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Define a dimensão do recurso para recursos múltiplos.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Description

O serviço define a dimensão do recurso para recursos múltiplos.

### <a name="parameters"></a>Parâmetros

- **valor** Ponteiro para descrição do valor do recurso.
- dim **valor** de dimensão.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Obtém o valor de um recurso **flutuante** de 32 Bits

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Description

O serviço recupera o valor de um recurso **flutuante** de 32 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **float32_ptr** Ponteiro para o destino 32-Bit **valor flutuante.**

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Define o valor de um recurso **flutuante** de 32 bits

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Description

O serviço define o valor de um recurso **flutuante** de 32 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **float32_data** dados **flutuantes** de 32 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Obtém o valor de um recurso flutuante de 64 Bits.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Description

O serviço recupera o valor de um recurso **flutuante** de 64 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **float64_ptr** Ponteiro para o destino 64-Bit **valor flutuante.**

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor flutuante.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Define o valor de um recurso **flutuante** de 64 bits.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

O serviço define o valor de um recurso **flutuante** de 64 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **float64_data** dados **flutuantes** de 64 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Obtém a informação de recursos.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Description

O serviço recupera a informação de recursos do Recurso.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **resource_id** Ponteiro para o ID do recurso de destino.
- **operação** Ponteiro para a operação de recursos de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Define a informação de recursos.

### <a name="prototype"></a>Prototype

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Description

O serviço define a informação do recurso.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **resource_id** Identificação do recurso.
- **operação** Operação do recurso.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

Obtém a instância de vários recursos.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Description

O serviço recupera a informação de recursos do Recurso.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **resource_instances** Ponteiro para o ID do recurso de destino.
- **contar** Ponteiro para a contagem.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor Boolean.
- **NX_LWM2M_CLIENT_NO_MEMORY** Sem memória para preencher casos.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Define as instâncias de recursos.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Description

O serviço define as instâncias de recursos para vários recursos.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **resource_instance** Ponteiro para instâncias de recursos.
- **contar** Contagem de casos de recursos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Obtém o valor de um recurso inteiro de 32 Bits.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Description

O serviço recupera o valor de um recurso inteiro de 32 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **integer32_ptr** Ponteiro para o valor inteiro de 32 Bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é valor inteiro.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Define o valor de um recurso inteiro de 32 Bits.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Description

O serviço define o valor de um recurso inteiro de 32 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **integer32_data** dados inteiros de 32 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Obtém o valor de um recurso inteiro de 64 Bits.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Description

O serviço recupera o valor de um recurso inteiro de 64 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **integer64_ptr** Ponteiro para o valor inteiro de 64 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é o valor inteiro de 64 Bits.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Desajei o valor de um recurso inteiro de 64 Bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Description

O serviço define o valor de um recurso inteiro de 64 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **integer64_data** inteiro de 64 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Obtém o valor de um recurso de ligação de objeto.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Description

O serviço recupera o valor da ligação de objetos.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **object_id** Ponteiro para a identificação do objeto.
- **instance_id** Ponteiro para o iD da instância do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor de ligação de objeto.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Define as instâncias de recursos

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Description

O serviço define o valor do recurso de ligação de objeto.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **object_id** Identificação de objeto.
- **instance_id** Identificação de instância de objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Obtém o valor de um recurso opaco.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Description

O serviço recupera o valor de um Recurso opaco. Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **opaque_ptr** Ponteiro para os dados opacos.
- **opaque_length** Ponteiro para o comprimento de dados opacos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor dos recursos não é um recurso opaco.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Define o valor de um recurso opaco.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Description

O serviço define o valor de um Recurso opaco.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **opaque_ptr** Ponteiro para os dados opacos.
- **opaque_length** Comprimento dos dados opacos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Obtém o valor de um recurso de corda.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Description

O serviço recupera o valor de um recurso de corda.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **string_ptr** Ponteiro para o ponteiro de corda de destino.
- **string_length** Ponteiro para o comprimento da corda de destino. Pode ser **NU SE** a cadeia estiver nula.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_BAD_ENCODING** O valor do recurso não é um valor de corda.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Define o valor de um recurso de corda.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Description

O serviço define o valor de um recurso inteiro de 64 Bits.

### <a name="parameters"></a>Parâmetros

- **recurso** Ponteiro para recurso.
- **string_ptr** Ponteiro para a corda.
- **string_length** Comprimento da corda.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Inicia uma sessão com um Servidor Bootstrap.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Description

Este serviço inicia uma sessão com um Servidor Bootstrap. O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.

Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **security_id** O ID de Instância de Segurança do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.
- **ip_address** O endereço IP do servidor.
- **porto** A porta UDP do servidor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ERROR** Erro de botas.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Inicia uma sessão segura com um Servidor Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

Este serviço inicia uma sessão com um Servidor Bootstrap utilizando uma ligação DTLS segura. O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.

A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função. **NX_SECURE_ENABLE_DTLS** deve ser definido.

Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente. 

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **security_id** O ID de Instância de Segurança do Servidor Bootstrap deve ser definido para **NX_LWM2M_RESERVED_ID** (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.
- **ip_address** O endereço IP do servidor.
- **porto** A porta UDP do servidor.
- **dtls_session_ptr** A sessão DTLS para utilizar para a sessão Bootstrap.
- **dtls_local_port** A porta UDP local utilizada para a sessão DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ERROR** Erro de botas.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Cria uma Sessão de Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Description

Este serviço cria uma nova Sessão de Cliente LWM2M anexada a um Cliente LWM2M existente. A sessão é utilizada pelo Cliente LWM2M para comunicar com um Servidor Bootstrap ou um Servidor LWM2M. 

A aplicação deve fornecer uma função de retorno que será chamada quando o estado da sessão for atualizado.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **client_ptr** Ponteiro para o cliente LWM2M anteriormente criado.
- **state_callback** Chamada de chamada de chamada que é chamada quando o estado da sessão mudou.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Elimina uma Sessão de Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma Sessão de Cliente LWM2M.

Quando um Cliente LWM2M é eliminado ligando nx_lwm2m_client_delete todas as sessões anexas ao cliente também são eliminadas.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Termina uma sessão com um Servidor LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'De-Register' para um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** O cliente não está registado no servidor.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Obtém o último erro de uma sessão.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço devolve o código de erro da sessão quando a sessão está num estado de erro.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** A sessão não está em estado de erro.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Endereço de servidor inválido.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** A carga de pedido não se encaixa no tampão da rede.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Não conseguiu estabelecer uma ligação segura com o servidor.
- **NX_LWM2M_ CLIENT_ERROR** Erro não especificado.
- **NX_LWM2M_ CLIENT_FORBIDDEN** Registo recusado pelo servidor.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Cliente não encontrado pelo servidor ao atualizar/desregissar.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** A instância do objeto do servidor correspondente à sessão foi eliminada.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Sem resposta do servidor.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Inicia uma sessão com um Servidor LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Description

Este serviço executa uma operação 'Registar' para um Servidor LWM2M. O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.

Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **server_id** O ID do Servidor Curto do Servidor LWM2M.
- **ip_address** O endereço IP do servidor.
- **porto** A porta UDP do servidor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ERROR** Erro de botas.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Inicia uma sessão segura com um Servidor LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'Register' para um Servidor LWM2M utilizando uma ligação DTLS segura. O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.

A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função. **NX_SECURE_ENABLE_DTLS** deve ser definido.

Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **server_id** O ID do Servidor Curto do Servidor LWM2M.
- **ip_address** O endereço IP do servidor.
- **porto** A porta UDP do servidor.
- **dtls_session_ptr** A sessão DTLS para utilizar para a sessão LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_ERROR** Erro de botas.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** A porta não está disponível.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Inicia uma sessão segura com um Servidor LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Description

Uma vez estabelecida uma sessão de comunicação com um servidor Bootstrap. A aplicação pode ligar para esta api para obter o servidor e informações de segurança para o próximo passo de registo.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.
- **security_instance_id** Identificação de instância de segurança.
- **server_id** Ponteiro para o ID do servidor de destino.
- **server_uri** Ponteiro para o servidor de destino uri.
- **server_uri_len** Ponteiro para o destino servidor uri comprimento.
- **security_mode** Ponteiro para o modo de segurança de destino.
- **pub_key_or_id** Ponteiro para destino chave ou identidade pública de destino.
- **pub_key_or_id_len** Ponteiro para destino chave pública ou comprimento de identidade.
- **server_pub_key** Ponteiro para a chave pública do servidor de destino.
- **server_pub_key_len** Ponteiro para o comprimento da chave pública do servidor de destino.
- **secret_key** Ponteiro para a chave secreta do destino.
- **secret_key_len** Ponteiro para o comprimento da chave secreta do destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_NOT_FOUND** Não há nenhuma instância de segurança.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Atualiza uma sessão com um Servidor LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Description

Este serviço executa uma operação 'Update' para um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr** Ponteiro para o bloco de controlo de sessão de cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** O cliente não está registado no servidor.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Desbloqueia um Cliente LWM2M.

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço desbloqueia o Cliente LWM2M previamente bloqueado por uma chamada para ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Parâmetros

- **client_ptr** Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** Operação bem sucedida.
- **NX_PTR_ERROR** Ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Threads, Inicialização

### <a name="example"></a>Exemplo

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```