---
title: Capítulo 3 - Descrição dos Serviços de Servidores Azure RTOS NetX PPPoE
description: Este capítulo contém uma descrição de todos os serviços do Azure RTOS NETX PPPoE Server (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826600"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Capítulo 3 - Descrição dos Serviços de Servidores Azure RTOS NetX PPPoE

Este capítulo contém uma descrição de todos os serviços do Azure RTOS NETX PPPoE Server (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- **nx_pppoe_server_create**: *Criar uma instância ppPoE Server*

- **nx_pppoe_server_ac_name_set**: *Definir nome do concentrador de acesso*

- **nx_pppoe_server_delete**: *Eliminar uma instância do servidor PPPoE*

- **nx_pppoe_server_enable**: *Ativar os serviços do PPPoE Server*

- **nx_pppoe_server_disable**: *Desativar os serviços do PPPoE Server*

- **nx_pppoe_server_callback_notify_set**: *Definir as funções de chamada ppPoE Server notificam funções*

- **nx_pppoe_server_service_name_set**: *Definir o nome do serviço ppPoE Server*

- **nx_pppoe_server_session_send**: *Enviar dados do PPPoE Server para sessão especificada*

- **nx_pppoe_server_session_packet_send**: *Enviar pacote ppPoE Server para sessão especificada*

- **nx_pppoe_server_session_terminate**: *Terminar a sessão PPPoE especificada*

- **nx_pppoe_server_session_get**: *Obtenha as informações de sessão especificadas*

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

Criar uma instância ppPoE Server

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância ppPoE Server com o controlador de ligação fornecido pelo utilizador para a instância IP netX especificada. Se o controlador de ligação não tiver sido inicializado e ativado, o software de corte PPPoE é responsável por rubricar o controlador de ligação.

Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância ppPoE Server para usar para alocação interna de pacotes.

Note que geralmente é uma boa ideia criar o fio IP NetX com uma prioridade maior do que a prioridade do fio PPPoE Server. Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **nome**: Nome desta instância ppPoE Server.
- **ip_ptr**: Ponteiro para o bloco de controlo por exemplo IP.
- **interface_index:** Índice de interface.
- **pppoe_link_driver**: Controlador de ligação fornecido pelo utilizador.
- **pool_ptr**: Ponteiro para a piscina de pacotes.
- **stack_ptr**: Ponteiro para o início da área de pilha do ppPoE Server.
- **stack_size:** Tamanho dos bytes na pilha do fio.
- **prioridade**: Prioridade das linhas internas do Servidor PPPoE (1-31).

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Inválido PPPoE Server, IP, pool de pacotes ou ponteiro de pilha.
- NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Interface inválida.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Tamanho de carga inválida do pacote.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Tamanho da memória inválida.
- NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Prioridade inválida da linha PPPoE Server.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

Excluir uma instância do Servidor PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina a instância do Servidor PPPoE anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

Ativar o serviço PPPoE Server

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço permite os serviços ppPoE Server.

> [!NOTE]
> Esta função deve ser chamada após *nx_pppoe_server_create* e *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Desativar o serviço PPPoE Server

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Descrição

Este serviço desativa os serviços ppPoE Server.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Definir chamadas ppPoE Server notificam funções 

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Descrição

Este serviço define as funções de chamada PPPoE Server notificam as funções.

> [!NOTE]
> Esta função deve ser chamada antes *nx_pppoe_server_enabl, e* o ponteiro de função pppoe_data_receive_notify deve ser definido, se não, *nx_pppoe_server_enable* será falha.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **pppoe_discover_initiation_notify**: Função de aplicação que é chamada sempre que PPPoE descobre a mensagem de iniciação é recebida. Se este valor for NU, descubra que a função de retorno de iniciação está desativada.
- **pppoe_discover_request_notify**: Função de aplicação que é chamada sempre que PPPoE descobrir mensagem de pedido é recebida. Se este valor for NU, descubra que a função de retorno do pedido é desativada.
- **pppoe_discover_terminate_notify**: Função de aplicação que é chamada sempre que PPPoE descobre que a mensagem de terminação é recebida. Se este valor for NU, descubra que a função de retorno de terminação está desativada.
- **pppoe_discover_terminate_confirm**: Função de aplicação que é chamada sempre que PPPoE descobre que a mensagem de terminação é enviada. Se este valor for NU, descubra que a função de retorno de terminação está desativada.
- **pppoe_data_receive_notify**: Função de aplicação que é chamada sempre que a mensagem de dados PPPoE é recebida. Este valor não deve ser zero.
- **pppoe_data_send_notify**: Função de aplicação que é chamada sempre que a mensagem de dados PPPoE é enviada. Se este valor for NU, a função de retorno de envio de dados é desativada.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro ou ponteiro de função do PpPoE Inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

Definir nome do concentrador de acesso

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Descrição

Esta função definiu a chamada de função do nome do concentrador de acesso.

> [!NOTE]
> A cadeia de ac_name deve ser terminada sem nulo e a duração de ac_name corresponde ao comprimento especificado na lista de argumentos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **ac_name**: Aceda ao nome do Concentrador.
- **ac_name_length:** Comprimento de ac_ame.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Conjunto de servidor PPPoE bem sucedido.
- **NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Inválido PPPoE Server, IP, pool de pacotes ou ponteiro de pilha.
- **NX_SIZE_ERROR**: (0x09) Verifique name_length falha.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Definir nome de serviço do servidor PPPoE

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Descrição

Este serviço define o nome de serviço ppPoE Server.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

Enviar dados do PPPoE Server para sessão especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Descrição

Este serviço envia quadro PPPoE usando o ID de sessão especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **session_index**: O índice da sessão.
- **data_ptr**: Ponteiro para o início do quadro de dados do PPPoE Server.
- **data_length**: Duração do quadro de dados do PPPoE Server.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Envie o pacote do PPPoE Server para sessão especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Descrição

Este serviço envia o pacote PPPoE utilizando o ID de sessão especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **session_index**: O índice da sessão.
- **packet_ptr**: Ponteiro para pacote PPPoE.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Pacote inválido do PPPoE Server.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Termine a sessão PPPoE especificada

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Descrição

Este serviço termina a sessão PPPoE especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **session_index**: O índice da sessão.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.
- NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Obtenha as informações de sessão do PPPoE especificadas

### <a name="prototype"></a>Prototype

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Descrição

Este serviço obtém as informações de sessão PPPoE especificadas, endereço físico do cliente e id de sessão.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.
- **session_index**: O índice da sessão.
- **client_mac_msw**: Ponteiro MSW de endereço físico do cliente.
- **client_mac_lsw**: Ponteiro MSW de endereço físico do cliente.
- **session_id:** Ponteiro de identificação de sessão.

### <a name="return-values"></a>Valores de devolução

- **NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.
- NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.
- NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Configure o nome de serviço predefinido

### <a name="prototype"></a>Prototype

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que o software da TTP configuure o 'Nome de Serviço predefinido' que o PPPoE deve utilizar para filtrar os pedidos PADI de entrada. O software PPPoE deve lembrar-se desta informação, e se um pacote PADI for recebido contendo um nome de serviço que corresponda, então deve chamar PppDiscoverReq.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **comprimento**: Duração do nome de serviço predefinido.
- **aData**: Nome de serviço predefinido.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Defina o campo nome de serviço do pacote PADO

### <a name="prototype"></a>Prototype

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que o software da TTP defina o campo nome de serviço do pacote PADO. O software PPPoE não deve enviar o PADO até que o PppDiscoverCnf seja chamado.

O pacote PADO deve conter um nome de concentrador de acesso (utilizando o id de identificação de identificação 0x0102 de identificação de identificação definido no RFC2516), definido na inicialização do software PPPoE.

Vários nomes de serviço podem ser passados numData, com cada nome a ser anulado.

O carácter nulo é utilizado como separador para proporcionar a máxima flexibilidade no caso de outros comandos precisarem de ser transmitidos como parte do nome de serviço.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **comprimento**: Duração do nome de serviço predefinido.
- **aData**: Nome de serviço predefinido.
- **interfaceHandle**: Interface handle.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpencnf

Aceitar ou rejeitar a sessão do PPPoE

### <a name="prototype"></a>Prototype

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que o software da TTP aceite ou rejeite a sessão PPPoE.  Em resposta a isto, a stack PPPoE deve aceitar a ligação e atribuir um número único de PPPoE Session_ID número associado à interfaceHandle.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **aceitar:** NX_TRUE se a ligação for aceite.
- **interfaceHandle**: Interface handle.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

Fechar uma sessão ppPoE

### <a name="prototype"></a>Prototype

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que o software da TTP encerre uma sessão ppPoE.

O software PPPoE indicará a cadeia de código causa na etiqueta Generic-Error (0x0203) na mensagem PADT

### <a name="input-parameters"></a>Parâmetros de Entrada

- **interfaceHandle**: Interface handle.
- **causeCode**: Cadeia terminada nula para envio de informações sobre o motivo para fechar a ligação a partir do Servidor PPPoE.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Confirme que o cabo foi libertado.

### <a name="prototype"></a>Prototype

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que o software da TTP confirme que o cabo foi libertado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **interfaceHandle**: Interface handle.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Permitir que os dados de PPP anteriores sejam reconhecidos

### <a name="prototype"></a>Prototype

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Descrição

O software PPPoE exporá esta função para permitir que um PppTransmitDataReq anterior seja reconhecido.  Implica que o software da TTP está pronto para uma nova moldura de PPP do PPPoE.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **interfaceHandle**: Interface handle.
- **aData**: Ponter o tampão de dados de PPP que foi aceite.
- **Packet_id:** Identificador de pacotes.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Receber dados da transmissão através do Ethernet

### <a name="prototype"></a>Prototype

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Descrição

O software PPPoE irá expor esta função para receber dados para transmissão através do Ethernet

### <a name="input-parameters"></a>Parâmetros de Entrada

- **interfaceHandle**: Interface handle.
- **comprimento**: O número de bytes numData.
- **aData**: Tampão de dados contendo o quadro de dados de PPP.

### <a name="return-values"></a>Valores de devolução

**Nenhuma**

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios

### <a name="example"></a>Exemplo

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```