---
title: Capítulo 3 - Descrição do cliente dos serviços do Cliente SMTP
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SMTP (listados abaixo) por ordem de utilização numa aplicação típica do Cliente SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825789"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Capítulo 3 - Descrição do cliente dos serviços do Cliente SMTP

Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SMTP (listados abaixo) por ordem de utilização numa aplicação típica do Cliente SMTP.

> [!NOTE]
> Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **_NX_DISABLE_ERROR_CHECKING_** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Criar uma instância de cliente SMTP

### <a name="prototype"></a>Prototype

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Descrição

Este serviço cria uma instância do Cliente SMTP na instância IP especificada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para o bloco de controlo do cliente SMTP;
- **ip_ptr** Indicação para a instância IP;
- **packet_pool_ptr** Ponteiro para piscina de pacotes de clientes;
- **nome de utilizador** Nome de utilizador rescindido nulo** para autenticação
- **senha** Senha terminada com nulo para autenticação
- **from_address** Endereço do remetente sem efeito de nulidade
- **client_domain** Nome de domínio rescindido nulo
- **authentication_type** Tipo de autenticação do cliente. Os tipos suportados são:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address** Ponteiro para o endereço IP do servidor SMTP
- **server_port** Porta TCP do servidor SMTP

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) SMTP Client criado com sucesso. Estado de criação da tomada TCP
- NX_SMTP_INVALID_PARAM (0xA5) Entrada inválida sem ponteiro
- NX_IP_ADDRESS_ERROR (0x21) Tipo de endereço IP inválido
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Código de Aplicação

### <a name="example"></a>Exemplo

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

Eliminar uma instância de cliente SMTP

### <a name="prototype"></a>Prototype

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Descrição

Este serviço elimina uma instância do Cliente SMTP anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para a instância do cliente SMTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Cliente eliminado com sucesso
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

Criar e enviar um artigo de correio SMTP

### <a name="prototype"></a>Prototype

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Descrição

Este serviço cria e envia um artigo de correio SMTP. O Cliente SMTP estabelece uma ligação TCP com o SMTP Server e envia uma série de comandos SMTP. Se não forem encontrados erros, transmitirá a mensagem de correio para o Servidor. Independentemente de o correio ser enviado com sucesso, terminará a ligação TCP e devolverá um estado indicando o resultado da transmissão de correio. A aplicação pode ligar para este serviço para o número de mensagens de correio que precisar de enviar sem limite.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para cliente SMTP
- **recipient_address** Endereço do destinatário rescindido nulo.
- **assunto** Texto de linha de assunto sem efeito nulo;.
- **prioridade** Nível prioritário em que o correio é entregue
- **mail_body** Ponteiro para mensagem de correio
- **mail_body_length** Tamanho da mensagem de correio

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Mail enviado com sucesso
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) Exemplo de cliente SMTP não inicializado para estado de sessão SMTP Resultado da sessão SMTP
- NX_PTR_ERROR (0x07) Parâmetro de ponteiro inválido
- NX_SMTP_INVALID_PARAM (0xA5) Entrada inválida sem ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
