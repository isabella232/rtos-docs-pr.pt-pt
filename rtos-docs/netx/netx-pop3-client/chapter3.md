---
title: Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX POP3
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX POP3 (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f68d6ac942c829dbf6eb9be334328b1b58a47ea370a73d37f471ec32cd46a360
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782392"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX POP3

Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX POP3 (listados abaixo) por ordem alfabética.

Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

- nx_pop3_client_create: Criar *uma instância de cliente POP3*
- nx_pop3_client_delete: *Eliminar uma instância de cliente POP3*
- nx_pop3_client_ mail_item_get: *Eliminar um item de correio do Cliente a partir da gota de correio do Servidor*
- nx_pop3_client_mail_item_get: Recuperar *um tamanho específico de mensagem de correio*
- nx_pop3_client_mail_items_get: Obtenha *o número de artigos de correio em gota de correio*
- nx_pop3_client_mail_item_message _get: *Descarregue uma mensagem de correio específica*
- nx_pop3_client_mail_item_size_get: Obtenha *o tamanho de um item de correio específico*

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Criar uma instância de cliente POP3

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Description

Este serviço cria uma instância do Cliente POP3 e configura a sua configuração com os parâmetros de entrada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o Cliente para criar
- **APOP_authentication**: Ativar a autenticação APOP
- **ip_ptr**: Indicação para a instância IP
- **packet_pool_ptr**: Ponteiro para piscina de pacotes de clientes
- **server_ip_address**: endereço do servidor POP3
- **server_port**: Porta de servidor POP3
- **client_name**: Ponteiro para o nome do cliente
- **client_password**: Ponteiro para a senha do cliente

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Cliente criado com sucesso
- **estado**: Conclusão do estado das chamadas de serviço NetX e ThreadX
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido
- NX_POP3_PARAM_ERROR: (0xB1) Entrada inválida sem ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

Excluir uma instância de cliente POP3

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a>Description

Este serviço elimina um Cliente POP3 previamente criado. Não que este serviço não apague a piscina de pacotes do Cliente POP3. A aplicação do dispositivo deve eliminar este recurso separadamente se deixar de ter a sua utilização para o conjunto de pacotes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Ponteiro para o Cliente para eliminar

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Cliente eliminado com sucesso
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Excluir um item de correio especificado da gota de correio do Cliente

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>Description

Este serviço elimina o item de correio especificado da gota de correio do Cliente. Destina-se a depois de descarregar o item de correio, embora alguns servidores POP3 possam apagar automaticamente os itens de correio depois de terem sido solicitados pelo Cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Indicação à instância do cliente
- **mail_index**: Índice na gota de correio do cliente

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Eliminar pedido bem sucedido
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

Recuperar um item de correio especificado

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>Description

Este serviço faz um pedido DEMÁ para recuperar um item de correio da gota de correio do Cliente especificada pelo índice mail_item. Depois de estivar um pedido DEMS, e receber uma resposta positiva do Servidor, o Cliente pode começar a descarregar a mensagem de correio utilizando o serviço *nx_pop3_client_mail_item_message_get.* Note que o serviço também fornece o tamanho do item de correio solicitado extraído da resposta do Servidor.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Indicação à instância do cliente
- **mail_item**: Índice na gota de correio do cliente
- **item_size**: Ponteiro para o tamanho da mensagem de correio

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

Recuperar o número de artigos de correio na gota de correio

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>Description

Este serviço faz um pedido de STAT para recuperar o número de itens de correio e o tamanho total dos dados de mensagens de correio da gota de correio do Cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Indicação à instância do cliente
- **number_mail_item**: Número de correio na escuta do correio do cliente
- **maildrop_total_size**: Ponteiro para o tamanho de todas as mensagens de correio

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro 
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

Recuperar a mensagem de envio de correio especificado

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>Description

Este serviço recupera a mensagem de envio de correio, o tamanho da mensagem de correio e se for o último pacote na mensagem de correio. Se `final_packet` for NX_TRUE o pacote apontado é o pacote final na `recv_packet_ptr` mensagem de envio de correio.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Indicação à instância do cliente
- **recv_packet_ptr**: Recebeu pacote de dados de mensagens
- **number_mail_item**: Número de correio na escuta do correio do cliente
- **maildrop_total_size**: Ponteiro para o tamanho de todas as mensagens de correio

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

Recuperar o tamanho do item de correio especificado

### <a name="prototype"></a>Prototype

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>Description

Este serviço faz um pedido LIST para obter o tamanho do item de correio especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr**: Indicação à instância do cliente
- **mail_item**: Índice na gota de correio do cliente
- **tamanho**: Ponteiro para o tamanho da mensagem de correio

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido
- NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de aplicação

### <a name="example"></a>Exemplo

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
