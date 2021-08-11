---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX PPPoE
description: Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NETX PPPoE (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790212"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX PPPoE

Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NETX PPPoE (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_pppoe_client_create** *Criar uma instância de cliente PPPoE*
- **nx_pppoe_client_delete Eliminar** *uma instância do cliente PPPoE*
- **nx_pppoe_client_host_uniq_set** *Definir o anfitrião único para cliente PPPoE*
- **nx_pppoe_client_host_uniq_set_extended** *Definir o anfitrião único para cliente PPPoE*
- **nx_pppoe_client_service_name_set** *Definir o nome de serviço para ppPoe Cliente*
- **nx_pppoe_client_service_name_set_extended** *Definir o nome de serviço para cliente PPPoE*
- **nx_pppoe_client_session_connect** *Ligação sessão de clientes PPPoE para o PPPoE Server*
- **nx_pppoe_client_session_packet_send** *Enviar pacote de sessão PPPoE*
- **nx_pppoe_client_session_terminate** *encerrar a sessão do PPPoE*
- **nx_pppoe_client_session_get** *Obtenha a sessão PPPoE especificada inf*

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Criar uma instância ppPoE cliente

### <a name="prototype"></a>Prototype

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

Este serviço cria uma instância ppPoE Client com o controlador de ligação fornecido pelo utilizador para a instância IP NetX especificada. Se o controlador de ligação não tiver sido inicializado e ativado, o software ppPoE Client é responsável por rubricar o controlador de ligação.

Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância ppPoe Cliente para usar para alocação interna de pacotes.

> [!NOTE]
> Geralmente uma boa ideia para criar o fio IP NetX com uma prioridade maior do que a prioridade do fio ppPoE Client. Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **nome** Nome desta instância ppPoe Cliente.
 - **ip_ptr** Ponteiro para bloquear por exemplo IP.
 - **interface_index** Índice de interface.
 - **pool_ptr** Ponteiro para a piscina de pacotes.
 - **stack_ptr** Ponteiro para o início da área de pilha do ppPoE Client thread.
 - **stack_size** Tamanho em bytes na pilha do fio.
 - **prioridade** Prioridade das linhas internas do Cliente PPPoE (1-31).
 - **pppoe_link_driver** Controlador de ligação fornecido pelo utilizador.
 - **pppoe_packet_receive** Função de receção do pacote fornecido pelo utilizador.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Cliente PPPoE inválido, IP, piscina de pacotes ou ponteiro de pilha.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Interface inválida.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Tamanho de carga útil inválido da piscina de pacotes.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Tamanho da memória inválida.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Prioridade inválida da linha ppPoe Client.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

Excluir uma instância do cliente PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina a instância do Cliente PPPoE anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para bloco de controlo do cliente PPPoE

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Conjunto PPPoE Cliente anfitrião único

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Description

Este serviço define o anfitrião ppPoE Client único. Host-Uniq é usado por um anfitrião para associar exclusivamente um Concentrador de Acesso a um determinado pedido de anfitrião.
Podem ser dados binários de qualquer valor e comprimento que o Anfitrião escolha.

> [!NOTE]
> hospedeiro único deve ser cadeia sem fim.

> [!NOTE]
> Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_pppoe_client_host_uniq_set_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **host_uniq** Ponteiro para um hospedeiro único. Hospedeiro único deve ser corda sem fim.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido hospeda conjunto único.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Conjunto PPPoE Cliente anfitrião único

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Description

Este serviço define o anfitrião ppPoE Client único. Host-Uniq é usado por um anfitrião para associar exclusivamente um Concentrador de Acesso a um determinado pedido de anfitrião.
Podem ser dados binários de qualquer valor e comprimento que o Anfitrião escolha.

> [!NOTE]
> hospedeiro único deve ser cadeia sem fim.

> [!NOTE]
> Este serviço substitui *nx_pppoe_client_host_uniq_set()*. Esta versão fornece informações adicionais de comprimento ao serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **host_uniq** Ponteiro para um hospedeiro único. Hospedeiro único deve ser corda sem fim.
 - **host_uniq_length** Comprimento de host_uniq

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido hospeda conjunto único.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.
 - **NX_SIZE_ERROR** (0x09) Verifique host_uniq_length falhar

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Definir nome de serviço do cliente PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Description

Este serviço define o nome de serviço ppPoE Cliente. O Service-Name indicando o serviço que o Anfitrião está a solicitar. Se Service-Name não estiver definido, indicando que o Host aceitará qualquer número de serviços.

> [!NOTE]
> nome de serviço deve ser cadeia sem efeito

> [!NOTE]
> Este serviço é precotado. Os desenvolvedores são encorajados a migrar para *nx_pppoe_client_service_name_set_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **service_name** Ponteiro para um nome de serviço. O nome de serviço deve ser a corda terminada sem efeito.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Conjunto de nomes de serviço pppoe bem sucedido.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Definir nome de serviço do cliente PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Description

Este serviço define o nome de serviço ppPoE Cliente. O Service-Name indicando o serviço que o Anfitrião está a solicitar. Se Service-Name não estiver definido, indicando que o Host aceitará qualquer número de serviços.

> [!NOTE]
> o nome de serviço deve ser cadeia sem efeito.

> [!NOTE]
> Este serviço substitui *nx_pppoe_client_service_name_set()*. Esta versão fornece informações adicionais sobre o comprimento do nome de serviço para a função.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **service_name** Ponteiro para um nome de serviço. O nome de serviço deve ser a corda terminada sem efeito.
 - **service_name_length** Comprimento de service_name

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Conjunto de nomes de serviço pppoe bem sucedido.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.
 - **NX_SIZE_ERROR** (0x09) Verifique service_name_length falhar

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Ligação Sessão de clientes PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço faz a ligação de sessão PPPoE utilizando um Cliente PPPoE previamente criado para o Servidor PPPoE especificado.

> [!NOTE]
> Esta função deve ser chamada após *nx_pppoe_client_create,* *nx_pppoe_client_host_uniq_set* e *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **wait_option** Opção de espera enquanto a ligação está a ser estabelecida.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) sessão de clientes PPPoE bem sucedida.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Envie o pacote do Cliente PPPoE para sessão especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Este serviço envia o pacote PPPoE utilizando o ID de sessão especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **packet_ptr** Ponteiro para pacote PPPoE.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) pacote de cliente PPPoE bem sucedido enviar.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Pacote de Cliente PPPoE inválido.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Sessão de clientes PPPoE encerrada

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Description

Este serviço termina a sessão PPPoE especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) Sessão de clientes PPPoE bem sucedida termina.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_get

Obtenha as informações de sessão do PPPoE especificadas

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Description

Este serviço obtém as informações de sessão PPPoE especificadas, endereço físico do servidor e id de sessão.

### <a name="input-parameters"></a>Parâmetros de Entrada

 - **pppoe_server_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.
 - **server_mac_msw** Endereço físico do endereço do servidor ponto MSW.
 - **server_mac_lsw** Endereço físico do endereço do servidor ponto MSW.
 - **session_id** Ponteiro de identificação de sessão.

### <a name="return-values"></a>Valores de devolução

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) sessão de clientes PPPoE bem sucedida obtém.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.
 - NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
