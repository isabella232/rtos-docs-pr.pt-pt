---
title: Capítulo 4 - Descrição dos serviços Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX LWM2M (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826672"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Capítulo 4 - Descrição dos serviços Azure RTOS NetX LWM2M

Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX LWM2M (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

### <a name="lwm2m-client-management"></a>Gestão de Clientes LWM2M

- **nx_lwm2m_client_create**: *Criar cliente LWM2M*
- **nx_lwm2m_client_delete**: *Eliminar cliente LWM2M*
- **nx_lwm2m_client_lock**: *Bloquear cliente LWM2M*
- **nx_lwm2m_client_object_add**: *Adicionar implementação de objeto ao Cliente LWM2M*
- **nx_lwm2m_client_unlock**: *Desbloquear Cliente LWM2M*

### <a name="lwm2m-client-session-management"></a>Gestão de Sessão de Clientes LWM2M

- **nx_lwm2m_client_session_bootstrap**: *Inicie uma sessão com um Servidor Bootstrap*
- **nx_lwm2m_client_session_bootstrap_dtls**: *Inicie uma sessão segura com um Servidor Bootstrap*
- **nx_lwm2m_client_session_create**: *Criar sessão de clientes LWM2M*
- **nx_lwm2m_client_session_delete**: *Eliminar sessão de clientes LWM2M*
- **nx_lwm2m_client_session_deregister**: *Terminar uma sessão com um Servidor LWM2M*
- **nx_lwm2m_client_session_error_get**: *Obtenha o último erro de uma sessão*
- **nx_lwm2m_client_session_register**: *Inicie uma sessão com um Servidor LWM2M*
- **nx_lwm2m_client_session_register_dtls**: *Inicie uma sessão segura com um Servidor LWM2M*
- **nx_lwm2m_client_session_update**: *Atualizar uma sessão com um Servidor LWM2M*

### <a name="security-object-implementation"></a>Implementação de objetos de segurança

- **nx_lwm2m_client_security_key_callbacks_set**: *Definir chamadas de gestão de chaves de segurança*

### <a name="device-object-implementation"></a>Implementação de objetos de dispositivo

- **nx_lwm2m_client_device_callbacks_set**: *Definir chamadas de aplicação de objeto de dispositivo*
- **nx_lwm2m_client_device_error_push**: *Adicione código de erro ao objeto do dispositivo*
- **nx_lwm2m_client_device_error_reset**: *Redefinir códigos de erro do objeto do dispositivo*
- **nx_lwm2m_client_device_resource_changed**: Alteração *do sinal do recurso objeto de dispositivo*

### <a name="custom-objects-implementation"></a>Implementação de objetos personalizados

- **nx_lwm2m_object_resource_changed**: *Alteração do sinal de um valor de recurso de uma Instância de Objeto*

### <a name="local-device-management"></a>Gestão local de dispositivos

- **nx_lwm2m_client_object_create**: *Criar uma nova instância de objeto*
- **nx_lwm2m_client_object_delete**: *Eliminar uma instância de objeto*
- **nx_lwm2m_client_object_discover**: *Descubra os recursos de uma instância de objeto*
- **nx_lwm2m_client_object_execute**: *Executar recurso de uma instância de objeto*
- **nx_lwm2m_client_object_get_next**: *Obtenha a lista de Objetos implementados pelo Cliente LWM2M*
- **nx_lwm2m_client_object_instance_get_next**: *Obtenha a lista de instâncias de um objeto*
- **nx_lwm2m_client_object_read**: *Leia os valores dos recursos de uma Instância de Objeto*
- **nx_lwm2m_client_object_write**: *Alterar os valores de recursos de uma instância de objeto*

### <a name="resources-values-decoding"></a>Descodagem de Valores de Recursos

- **nx_lwm2m_resource_get_boolean**: *Obtenha o valor de um Recurso Boolean*
- **nx_lwm2m_resource_get_float32**: *Obtenha o valor de um recurso de ponto flutuante de 32 bits*
- **nx_lwm2m_resource_get_float64**: *Obtenha o valor de um recurso de ponto flutuante de 64 bits*
- **nx_lwm2m_resource_get_integer32**: *Obtenha o valor de um recurso inteiro de 32 bits*
- **nx_lwm2m_resource_get_integer64**: *Obtenha o valor de um recurso inteiro de 64 bits*
- **nx_lwm2m_resource_get_objlnk**: *Obtenha o valor de um recurso de ligação de objeto*
- **nx_lwm2m_resource_get_opaque**: *Obtenha o valor de um Recurso Opaco*
- **nx_lwm2m_resource_get_string**: *Obtenha o valor de um recurso de corda*
- **nx_lwm2m_resource_multiple_get_boolean**: *Obtenha o valor de uma instância de recursos múltiplos de recurso boolean*
- **nx_lwm2m_resource_multiple_get_float32**: *Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 32 bits*
- **nx_lwm2m_resource_multiple_get_float64**: *Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 64 bits*
- **nx_lwm2m_resource_multiple_get_integer32**: *Obtenha o valor de uma instância de recursos múltiplos de 32 bits*
- **nx_lwm2m_resource_multiple_get_integer64**: *Obtenha o valor de uma instância de recursos múltiplos de 64 bits*
- **nx_lwm2m_resource_multiple_get_objlnk**: *Obtenha o valor de uma instância de recursos múltiplos de ligação de objetos*
- **nx_lwm2m_resource_multiple_get_opaque**: *Obtenha o valor de uma instância de recursos múltiplos opaco*
- **nx_lwm2m_resource_multiple_get_string**: *Obtenha o valor de uma instância de recursos múltiplos de cordas*

### <a name="firmware-update-object"></a>Objeto de atualização de firmware

- **nx_lwm2m_firmware_create**: *Criar objeto de atualização de firmware*
- **nx_lwm2m_firmware_package_info_set**: Definir informações do *pacote de atualização de firmware*
- **nx_lwm2m_firmware_result_set**: *Definir resultado da atualização do firmware*
- **nx_lwm2m_firmware_state_set**: *Definir Estado de atualização de firmware*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Criar cliente LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância de cliente LWM2M, que funciona no contexto da sua própria linha ThreadX.

O Cliente LWM2M implementa os seguintes objetos OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3). As implementações dos outros objetos devem ser adicionadas pela aplicação.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **ip_ptr**: Ponteiro para instância IP previamente criada.
- **packet_pool_ptr**: Ponter para a piscina de pacotes predefinidos para este Cliente LWM2M.
- **local_port**: A porta UDP local utilizada para comunicação não segura.
- **name_ptr**: Ponteiro para o nome final do cliente LWM2M.
- **msisdn_ptr**: Ponte rumo ao MSISDN onde o Cliente LWM2M pode ser contactado para ser utilizado com a ligação SMS, pode ser NU SE a ligação SMS não for suportada.
- **binding_modes**: A encadernação e os modos suportados pelo Cliente LWM2M devem ser uma combinação de bandeiras de NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S e NX_LWM2M_BINDING_SQ.
- **stack_ptr**: Ponteiro para a área da pilha de fio do cliente LWM2M.
- **stack_size**: O tamanho da pilha de fio do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: O Cliente LWM2M foi criado com sucesso.
- **NX_LWM2M_ERROR**: O Cliente LWM2M cria erro.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Excluir cliente LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância de cliente LWM2M anteriormente criada.

Todas as sessões atualmente anexadas ao cliente também são eliminadas por esta chamada.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: O Cliente LWM2M foi eliminado com sucesso.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Definir chamadas de aplicação de objeto de dispositivo

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Descrição

Este serviço instala as chamadas de aplicação para implementação de operações nos recursos do Objeto de Dispositivo LWM2M que não são tratados pelo Cliente LWM2M.

O Cliente LWM2M implementa os seguintes recursos : Código de Erro (11), Código de Erro de Reset (12) e Ligação e Modos Suportados (16), as operações para os outros recursos são redirecionadas para a aplicação.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **read_callback**: O chamado 'Ler' do método .
- **discover_callback**: O chamado 'Descobrir'.
- **write_callback**: O chamado devolução do método 'Write'.
- **execute_callback**: O chamado 'Executar'.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Adicione código de erro ao objeto do dispositivo

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Descrição

Este serviço adiciona uma nova instância ao recurso Error Code (11) do Dispositivo Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **código**: O novo código de erro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BUFFER_TOO_SMALL**: O número máximo de códigos de erro armazenados foi atingido.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Redefinir códigos de erro do objeto do dispositivo

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina todas as instâncias de código de erro do Objeto do Dispositivo. Isto equivale a executar o código de erro de reposição de recursos (12).

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Alteração de sinal do recurso objeto do dispositivo

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Descrição

O serviço é utilizado pela aplicação para sinalizar ao Cliente LWM2M que um recurso do Dispositivo De Objeto mudou. O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **recurso**: Ponteiro para a estrutura que descreve o recurso que mudou.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Cliente Lock LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço bloqueia o Cliente LWM2M para evitar o acesso concutivo aos objetos LWM2M dos servidores ou de outro fio de aplicação.

Se o Cliente LWM2M estiver atualmente bloqueado por outro fio, a função bloqueará até que o Cliente LWM2M seja desbloqueado.

As chamadas para pares nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() podem ser aninhadas.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Adicionar implementação de objeto ao Cliente LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Descrição

Este serviço adiciona uma nova implementação de Objeto ao Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_ptr**: Ponteiro para a estrutura que define a implementação do Objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_ALREADY_EXIST:** O ID do objeto já existe.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Criar uma nova instância de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Criar' num Objeto do Cliente LWM2M para criar uma nova Instância de Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id_ptr**: O ponteiro para o ID da nova instância, pode ser NULO se o Cliente LWM2M tiver de atribuir um ID de instância. Se o ID for o valor reservado 65535, o Cliente LWM2M atribuirá um ID de instância. Se não não null, o ID atribuído é devolvido após a chamada.
- **num_values**: O número de valores a definir.
- **values_ptr**: Ponteize para uma matriz de valores de recursos para rubricar a nova Instância de Objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_ALREADY_EXIST**: O ID de instância de objeto já existe.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** O Objeto não suporta a criação de instâncias.
- **NX_LWM2M_NO_MEMORY**: Não é possível alocar a memória para armazenar o novo caso.
- **NX_LWM2M_NOT_FOUND:** O ID do objeto não existe.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Eliminar uma instância de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Eliminar' numa Instância de Objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id**: O ID da instância do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** O Objeto não suporta a eliminação de instâncias.
- **NX_LWM2M_NOT_FOUND:** O ID do objeto ou iD de instância de objeto não existe.
- NX_PTR_ERROR ponteiro inválido.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Descubra recursos de uma instância de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Discover' numa Instância de Objeto do Cliente LWM2M, esta devolve a lista de recursos implementados pelo Objeto.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id**: O ID da instância do objeto.
- **num_resources_ptr**: No tamanho do tampão de destino, na saída o número de elementos escritos para o tampão.
- **resources_ptr**: Ponteiro para o tampão de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BUFFER_TOO_SMALL**: O tampão de recursos é demasiado pequeno para armazenar a lista de recursos.
- **NX_LWM2M_NOT_FOUND:** O ID do objeto ou iD de instância de objeto não existe.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Executar recurso de uma instância de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Descrição

Este serviço executa a operação 'Executar' num recurso de instância de objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id**: O ID da instância do objeto.
- **resource_id:** O ID do recurso.
- **arguments_ptr**: Ponto a partir dos argumentos da operação de execução. Pode ser NULO se arguments_length for zero.
- **arguments_length:** A duração dos argumentos.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** O recurso não suporta a operação de execução.
- **NX_LWM2M_NOT_FOUND:** O ID do Objeto, o ID da Instância do Objeto ou o ID do recurso não existem.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Obtenha a lista de Objetos implementados pelo Cliente LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Descrição

Este serviço devolve o ID do próximo Objeto implementado pelo Cliente LWM2M. Se o ID do objeto atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o primeiro ID do objeto é devolvido.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id_ptr**: Ponteiro para o ID do objeto atual. Na devolução contém o próximo ID do Objeto implementado pelo Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: O ID dado objeto é o último da base de dados.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Obtenha a lista de instâncias de um objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Descrição

Este serviço devolve o ID da próxima Instância de Objeto do Objeto dado. Se o ID de instância atual estiver definido para NX_LWM2M_RESERVED_ID (65535) o ID da primeira instância é devolvido.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id_ptr**: Ponteiro para o ID de instância do objeto atual. No retorno contém o próximo ID de instância do objeto.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: O ID dado o caso é o último do objeto, ou o ID do objeto não é implementado.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Leia os valores de recursos de uma Instância de Objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Ler' numa Instância de Objeto do Cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id**: O ID da instância do objeto.
- **num_values:** O número de recursos a ler.
- **values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos para ler. Na volta, a matriz é preenchida com os tipos e valores correspondentes.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Um recurso não suporta a operação de leitura.
- **NX_LWM2M_NOT_FOUND**: O ID do objeto, o ID da instância do objeto ou um ID de recurso não existem.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Alterar os valores de recursos de uma instância de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação de 'Write' numa Instância de Objeto do Cliente LWM2M.

As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op:*

- **0** &mdash; Atualização Parcial: adição ou atualizações Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados,

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Instância de substituição: substitui a Instância do Objeto pelos novos valores de recursos fornecidos.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Substituir Recurso: substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indica uma chamada de uma sequência de Bootstrap.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **object_id:** O ID do objeto.
- **instance_id**: O ID da instância do objeto.
- **num_values:** O número de recursos para escrever.
- **values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos, os tipos e os valores a escrever.
- **write_op:** O tipo de operação de escrita.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O tipo de recurso não é válido.
- **NX_LWM2M_BUFFER_TOO_SMALL**: O comprimento de um valor é demasiado grande para ser armazenado no caso.
- **NX_LWM2M_METHOD_NOT_ALLOWED:** Um recurso não suporta a operação de escrita.
- **NX_LWM2M_NO_MEMORY**: Não é possível alocar a memória para armazenar um valor de recurso.
- **NX_LWM2M_NOT_ACCEPTABLE**: O valor de um recurso não é válido.
- **NX_LWM2M_NOT_FOUND**: O ID do objeto, o ID da instância do objeto ou um ID de recurso não existem.
- NX_OPTION_ERROR: Tipo inválido de operação de escrita.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Definir chamadas de gestão de chaves de objeto de segurança

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Descrição

Este serviço instala as chamadas de aplicação para implementação de operações nos recursos do LWM2M Security Object relacionados com as chaves de segurança.

O Cliente LWM2M delega a gestão da chave de segurança para a aplicação durante as sessões de Bootstrap, as chamadas serão chamadas quando o Servidor Bootstrap escrever ou eliminar os seguintes recursos numa Instância de Objeto de Segurança: Chave Pública ou Identidade (3), Chave Pública do Servidor (4), Chave Secreta (5).

A aplicação é responsável pelo armazenamento dos dados das chaves e pela configuração das sessões DTLS utilizadas pelo cliente LWM2M.

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.
- **write_callback**: O chamado devolução do método da chave 'Write'.
- **delete_callback**: O chamado devolução do método da chave 'Eliminar'.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Inicie uma sessão com um Servidor Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Descrição

Este serviço inicia uma sessão com um Servidor Bootstrap. O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.

Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.
- **security_id**: O ID de identificação do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.
- **ip_address**: O endereço IP do servidor.
- **porta**: A porta UDP do servidor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de segurança correspondente ao ID de instância de segurança.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Inicie uma sessão segura com um Servidor Bootstrap

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Descrição

Este serviço inicia uma sessão com um Servidor Bootstrap utilizando uma ligação DTLS segura. O servidor deve ter uma instância de segurança correspondente no Objeto de Segurança.

A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função. NX_SECURE_ENABLE_DTLS deve ser definido.

Se o recurso 'Hold Off' for diferente de zero na Instância de Segurança associada a este servidor, a sessão aguardará uma bota iniciada pelo servidor, se não for iniciada nenhuma bota pelo servidor após este período de tempo, será executada uma Boostrap iniciada pelo Cliente.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Bootstrap Server.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.
- **security_id**: O ID de identificação do Servidor Bootstrap deve ser definido para NX_LWM2M_RESERVED_ID (65535) se o Servidor Bootstrap não tiver nenhuma Instância de Segurança definida.
- **ip_address**: O endereço IP do servidor.
- **porta**: A porta UDP do servidor.
- **dtls_session_ptr**: A sessão DTLS para utilizar para a sessão Bootstrap.
- **dtls_local_port**: A porta UDP local utilizada para a sessão DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de segurança correspondente ao ID de instância de segurança.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Criar sessão de clientes LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Descrição

Este serviço cria uma nova Sessão de Cliente LWM2M anexada a um Cliente LWM2M existente. A sessão é utilizada pelo Cliente LWM2M para comunicar com um Servidor Bootstrap ou um Servidor LWM2M.

A aplicação deve fornecer uma função de retorno que será chamada quando o estado da sessão for atualizado.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.
- **client_ptr**: Ponteiro para o cliente LWM2M anteriormente criado.
- **state_callback**: Chamada de chamada quando o estado da sessão tiver mudado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Eliminar sessão de clientes LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma Sessão de Cliente LWM2M.

Quando um Cliente LWM2M é eliminado ligando nx_lwm2m_client_delete todas as sessões anexas ao cliente também são eliminadas.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Termine uma sessão com um Servidor LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'De-Register' para um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_REGISTERED:** O cliente não está registado no servidor.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Obtenha o último erro de uma sessão

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descrição

Este serviço devolve o código de erro da sessão quando a sessão está num estado de erro.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: A sessão não está em estado de erro.
- **NX_LWM2M_ADDRESS_ERROR:** Endereço do servidor inválido.
- **NX_LWM2M_BUFFER_TOO_SMALL:** A carga de pedido não se enquadra no tampão de rede.
- **NX_LWM2M_DTLS_ERROR:** Não conseguiu estabelecer uma ligação segura com o servidor.
- **NX_LWM2M_ERROR:** Erro não especificado.
- **NX_LWM2M_FORBIDDEN:** Registo recusado por servidor.
- **NX_LWM2M_NOT_FOUND**: Cliente não encontrado pelo servidor ao atualizar/desregistar.
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: A instância do objeto do servidor correspondente à sessão foi eliminada.
- **NX_LWM2M_TIMED_OUT:** Nenhuma resposta do servidor.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Inicie uma sessão com um Servidor LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Registar' para um Servidor LWM2M. O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.

Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.
- **server_id**: O ID do Servidor Curto do Servidor LWM2M.
- **ip_address**: O endereço IP do servidor.
- **porta**: A porta UDP do servidor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de servidor correspondente ao ID do servidor curto.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Inicie uma sessão segura com um Servidor LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Register' para um Servidor LWM2M utilizando uma ligação DTLS segura. O servidor deve ter uma instância de servidor correspondente no Objeto do Servidor.

A sessão DTLS deve ter sido configurada com as suites de cifra adequadas e material chave antes de chamar esta função. NX_SECURE_ENABLE_DTLS deve ser definido.

Cada sessão DTLS utiliza a sua própria tomada UDP para comunicação, pelo que o porto local dtls_local_port deve ser diferente para cada sessão se a aplicação criar várias sessões seguras.

Se o registo for bem sucedido, o Cliente LWM2M processará novas operações a partir do servidor e enviará periodicamente mensagens de 'Update' até que o cliente seja descista.

Qualquer sessão ativa atual é abortada por esta chamada e substituída pela nova sessão do Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.
- **server_id**: O ID do Servidor Curto do Servidor LWM2M.
- **ip_address**: O endereço IP do servidor.
- **porta**: A porta UDP do servidor.
- **dtls_session_ptr**: A sessão DTLS para utilizar para a sessão LWM2M.
- **dtls_local_port**: A porta UDP local utilizada para a sessão DTLS.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_FOUND**: Não existe nenhuma instância de objeto de servidor correspondente ao ID do servidor curto.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Atualize uma sessão com um Servidor LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Descrição

Este serviço executa uma operação 'Update' para um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **session_ptr**: Ponteiro para o bloco de controlo da Sessão de Cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_NOT_REGISTERED:** O cliente não está registado no servidor.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Desbloquear Cliente LWM2M

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço desbloqueia a previoulsy do Cliente LWM2M bloqueada por uma chamada para nx_lwm2m_client_unlock().

### <a name="parameters"></a>Parâmetros

- **client_ptr**: Ponteiro para o bloco de controlo do cliente LWM2M.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Criar objeto de atualização de firmware

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Descrição

Este serviço inicializa um Objeto de Atualização de Firmware e adiciona o Objeto a um Cliente LWM2M anteriormente criado. O Firmware Update Object implementa os recursos para comunicar com um Servidor LWM2M, mas a aplicação deve fornecer chamadas para implementar as operações reais no firmware (dowloading, armazenamento e atualização do firmware).

O parâmetro de protocolo indica quais os protocolos suportados pela aplicação de recuperação do firmware com o recurso 'Package URI', são definidas as seguintes bandeiras:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr**: Ponteiro para o bloco de controlo do objeto Firmware.
- **client_ptr**: Ponteiro para o cliente LWM2M criado previsivelmente.
- **protocolos**: Bandeiras que indicam quais os protocolos suportados pelo recurso Package URI.
- **package_callback**: Deve ser NU [TBD].
- **package_uri_callback**: Callback usado para implementar o recurso Package URI.
- **update_callback**: Callback usado para implementar o recurso Update.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Definir informações do pacote de atualização de firmware

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Descrição

Este serviço altera os valores dos recursos 'PkgName' (6) e 'PkgVersion' (7) do Firmware Update Object.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr**: Ponter para o objeto de atualização de firmware.
- **nome**: O novo valor do Nome do Pacote.
- **versão**: O novo valor da versão pacote.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Definir resultado da atualização do firmware

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Descrição

Este serviço altera o valor do recurso 'Resultado de actualização' (5) do Objeto de Atualização de Firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr**: Ponter para o objeto de atualização de firmware.
- **resultado**: O novo valor do recurso Resultado de Atualização.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Definir Estado de Atualização de Firmware

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Descrição

Este serviço altera o valor do recurso 'Estado' (3) do Objeto de Atualização de Firmware.

### <a name="parameters"></a>Parâmetros

- **firmware_ptr**: Ponter para o objeto de atualização de firmware.
- **estado**: O novo valor do recurso do Estado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Alteração de sinal de um valor de recurso de uma Instância de Objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Descrição

Este serviço é utilizado por uma implementação de Objeto para sinalizar o Cliente LWM2M que um dos seus valores de recursos mudou. O Cliente LWM2M enviará uma notificação se o recurso for observado por um Servidor LWM2M.

### <a name="parameters"></a>Parâmetros

- **object_ptr**: Ponteiro para a implementação do objeto.
- **instance_ptr**: Ponteiro para a Instância do Objeto.
- **recurso**: Ponteiro para a estrutura que descreve o recurso que mudou.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- NX_PTR_ERROR: Ponteiro inválido.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Obtenha o valor de um Recurso Boolean

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um Recurso Boolean.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **bool_ptr**: Ponte para o destino Valor Boolean.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Boolean.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Obtenha o valor de um recurso de ponto flutuante de 32 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um recurso flutuante de 32 bits.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **float32_ptr**: Ponte para o destino 32-Bit Floating Point valor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ponto Flutuante.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Obtenha o valor de um recurso de ponto flutuante de 64 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um recurso flutuante de 64 bits.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **float64_ptr**: Ponte para o destino 64-Bit Floating Point value.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ponto Flutuante.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Obtenha o valor de um recurso inteiro de 32 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um recurso inteiro de 32 bits.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **int32_ptr**: Ponte para o destino valor inteiro de 32 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Inteiro, ou o valor Inteiro não se encaixa num número de 32 Bits.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Obtenha o valor de um recurso inteiro de 64 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um recurso inteiro de 64 bits.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **int64_ptr**: Ponte para o destino 64-Bit Valor Inteiro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor Inteiro.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Obtenha o valor de um recurso de ligação de objeto

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um recurso de ligação de objetos.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **objlnk_ptr**: Ponter para o valor de Link do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de Ligação de Objeto.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Obtenha o valor de um Recurso Opaco

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um Recurso Opaco.

Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **opaque_ptr_ptr**: Ponteiro para o ponteiro tampão opaco de destino.
- **opaque_length_ptr**: Ponteiro para o comprimento do tampão opaco de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor opaco.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Obtenha o valor de um recurso de corda

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de um Recurso de Corda.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para descrição do valor do recurso.
- **string_ptr_ptr**: Ponteiro para o ponteiro de cadeia de destino.
- **string_length_ptr**: Ponte até ao comprimento da corda de destino. Pode ser NU SE a cadeia estiver nula.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_ENCODING**: O valor do recurso não é um valor de corda.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Obtenha o valor de uma Instância de Recursos Múltiplos de Recurso Boolean

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma Instância de Recursos Boolean de um Recurso Múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **bool_ptr**: Ponte para o destino Valor Boolean.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Boolean.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 32 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma instância de recursos flutuantes de 32 bits de um recurso múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **float32_ptr**: Ponte para o destino 32-Bit Floating Point valor.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ponto Flutuante.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Obtenha o valor de uma instância de recursos múltiplos de ponto flutuante de 64 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma instância de recursos flutuantes de 64 bits de um recurso múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **float64_ptr**: Ponte para o destino 64-Bit Floating Point value.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ponto Flutuante.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Obtenha o valor de uma instância de recursos múltiplos de 32 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma instância de recursos inteiros de 32 bits de um recurso múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **int32_ptr**: Ponte para o destino valor inteiro de 32 bits.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Inteiro, ou o valor Inteiro não se encaixa num número de 32 Bits.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Obtenha o valor de uma instância de recursos múltiplos de 64 bits

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma instância de recursos inteiros de 64 bits de um recurso múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **int64_ptr**: Ponte para o destino 64-Bit Valor Inteiro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor Inteiro.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Obtenha o valor de uma instância de recursos múltiplos de ligação de objetos

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma instância de recurso de ligação de objetos a partir de um recurso múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **objlnk_ptr**: Ponter para o valor de Link do objeto de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor de Ligação de Objeto.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Obtenha o valor de uma instância de recursos múltiplos opaco

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma Instância de Recursos Opacos a partir de um Recurso Múltiplo.

Um valor de recurso opaco consiste num ponteiro para um tampão e um comprimento.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **opaque_ptr_ptr**: Ponteiro para o ponteiro tampão opaco de destino.
- **opaque_length_ptr**: Ponteiro para o comprimento do tampão opaco de destino.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor do recurso não é um valor opaco.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Obtenha o valor de uma instância de recursos múltiplos de cordas

### <a name="prototype"></a>Prototype

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Descrição

O serviço recupera o valor de uma Instância de Recursos de Cadeia de um Recurso Múltiplo.

### <a name="parameters"></a>Parâmetros

- **valor**: Ponteiro para a descrição do valor de recursos múltiplos.
- **índice**: Índice da Instância para recuperar na matriz de valor de recurso.
- **instance_id_ptr**: Ponteiro para o destino Identificação de Exemplo.
- **string_ptr_ptr**: Ponteiro para o ponteiro de cadeia de destino.
- **string_length_ptr**: Ponte até ao comprimento da corda de destino. Pode ser NU SE a cadeia estiver nula.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS:** Operação bem sucedida.
- **NX_LWM2M_BAD_PARAMETER**: O índice está fora de alcance.
- **NX_LWM2M_BAD_ENCODING**: O recurso não é um recurso múltiplo, ou o valor da instância não é um valor de corda.
