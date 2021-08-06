---
title: Capítulo 3 - Descrição dos serviços HTTP
description: Este capítulo contém uma descrição de todos os serviços NetX Web HTTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0357afe7f997c84a5d031ca71dc524e381734b4a
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178192"
---
# <a name="chapter-3---description-of-http-services"></a>Capítulo 3 - Descrição dos serviços HTTP

Este capítulo contém uma descrição de todos os serviços NetX Web HTTP (listados abaixo) por ordem alfabética.

> [!NOTE]
> Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.

## <a name="http-and-https-client-api"></a>API do cliente HTTP E HTTPS

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Abra uma tomada de texto simples para um servidor HTTP para pedidos personalizados

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço abre uma tomada TCP de texto simples para um servidor HTTP, mas não envia nenhum pedido. Os pedidos são criados com *n x_web_http_client_request_initialize()* e enviados *através nx_web_http_client_request_send()*. Os cabeçalhos HTTP personalizados podem ser adicionados ao pedido utilizando *nx_web_http_client_request_header_add()*.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido. **Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**

> [!NOTE]
> Os métodos nx_web_http_client_*_start são fornecidos por conveniência (por *exemplo, nx_web_http_client_get_start*()) e manuseam a geração de pedidos e a ligação da tomada. Pode utilizar esses serviços em vez de *nx_web_http_client_connect()* e as rotinas relacionadas se não precisar de cabeçalhos HTTP personalizados nos seus pedidos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **server_ip** Endereço IP do servidor HTTP remoto.
- **server_port** Porta no servidor HTTP remoto (por exemplo, 80 para HTTP).
- **wait_option** Define quanto tempo o serviço vai esperar pelas operações subjacentes à rede. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação bem sucedida da tomada TCP.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_WEB_HTTP_NOT_READY (0x3000A) Outro pedido já está em curso.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Criar uma instância de cliente HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Description

Este serviço cria uma instância http cliente na instância IP especificada. A instância do Cliente pode ser usada para HTTP ou HTTPS. Consulte os serviços *nx_web_http_client_connect()* e *nx_web_http_client_secure_connect()* para obter mais informações sobre o início de um caso HTTP ou HTTPS. Consulte também a API para *nx_web_http_client_get_**, *nx_web_http_client_put_*** *nx_web_http_client_post_** para simples invocações de métodos GET, PUT e POST.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **client_name** Nome da instância do cliente HTTP.
- **ip_ptr** Ponteiro para a instância IP.
- **pool_ptr** Ponteiro para piscina de pacote padrão. Note que os pacotes desta piscina devem ter uma carga útil suficientemente grande para manusear o cabeçalho de resposta completo. Isto é definido por *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* em *nx_web_http_client.h*.
- **window_size** O tamanho da tomada TCP do Cliente recebe a janela.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Sucesso http cliente criar
- NX_PTR_ERROR (0x16) Inválido HTTP, ip_ptr ou ponteiro de piscina de pacotes
- NX_WEB_HTTP_POOL_ERROR (0x30009) Tamanho da carga útil inválida na piscina de pacotes

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Excluir uma instância de cliente HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do cliente HTTP previamente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso HTTP Cliente delete
- NX_PTR_ERROR (0x16) Ponteiro HTTP inválido
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

Inicie um pedido de exclusão httptext simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Esta API está prevadida. Os desenvolvedores são encorajados a usar *nx_web_http_client_delete_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

Inicie um pedido de exclusão httptext simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_delete_start* (). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

Inicie um pedido de ELIMINAÇÃO HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_delete_secure_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado. o recurso deve ser anulado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Inicie um pedido de ELIMINAÇÃO HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_delete_secure_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado. o recurso deve ser anulado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.


### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

Inicie um pedido http GET de texto simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_get_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

Inicie um pedido http GET de texto simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_get_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

Inicie um pedido HTTPS GET encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_get_secure_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

Inicie um pedido HTTPS GET encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_secure_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

Inicie um pedido de cabeça HTTP texto simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então chamar *nx_web_http_client_response_body_get para* recuperar a resposta.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_head_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

Inicie um pedido de cabeça HTTP texto simples

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então chamar *nx_web_http_client_response_body_get para* recuperar a resposta.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_head_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

Inicie um pedido de CABEÇA HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *nx_web_http_client_response_body_get para* recuperar a resposta do servidor correspondente ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_head_secure_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

Inicie um pedido de CABEÇA HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada. Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *nx_web_http_client_response_body_get para* recuperar a resposta do servidor correspondente ao conteúdo de recursos solicitado.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_head_secure_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD
- **NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

Alocar um pacote HTTP(S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço tenta alocar um pacote para o Cliente HTTP(S).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **packet_ptr** Ponteiro para pacote atribuído.
- **wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes. As opções de espera são definidas da seguinte forma:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **tempo limite em tiques** (0x00000001 através de 0xFFFFFFFE)

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos
- **NX_NO_PACKET** (0x01) Sem pacote disponível
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

Inicie um pedido HTTP POST

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_post_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso para enviar para Server.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

Inicie um pedido HTTP POST

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_post_start* (). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

Inicie um pedido de HTTPS POST encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_post_secure_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso para enviar para Server.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_post_secure_start_extended

Inicie um pedido de HTTPS POST encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_post_secure_start* (). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

Inicie um pedido HTTP PUT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_put_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso para enviar para Server.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso pedido PUT
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

Inicie um pedido HTTP PUT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Description

Este método é para **texto simples** HTTP.

Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_put_start* (). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso pedido PUT
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

Inicie um pedido DE PD HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_put_secure_start_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso para enviar para Server.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso pedido PUT
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

Inicie um pedido DE PD HTTPS encriptado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta. Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.

Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_put_secure_start*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **ip_address** Endereço IP do servidor HTTP.
- **server_port** Porta TCP no servidor HTTP remoto.
- **recurso** Ponteiro para cadeia URL para recurso solicitado.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **total_bytes** Total de bytes de recursos sendo enviados. Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso pedido PUT
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

Enviar o próximo pacote de dados de recursos

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço tenta enviar o próximo pacote de conteúdo de recursos para o servidor HTTP para operações PUT e POST. Note que esta rotina deve ser chamada repetitivamente até que o comprimento combinado dos pacotes enviados seja igual ao "total_bytes" especificado na chamada *nx_web_http_client_put_start* ou *nx_web_http_client_post_start anteriores* (ou nas respetivas versões seguras).

Este serviço também verifica uma resposta do servidor no caso de haver algum problema no estabelecimento da ligação HTTP (ou HTTPS).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **packet_ptr** Ponteiro para o próximo conteúdo do recurso a ser enviado para o Servidor HTTP.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso o pacote do cliente HTTP.
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Recebeu código de erro do Servidor**
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Comprimento do pacote inválido
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) O servidor responde antes de o PUT estar completo.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_INVALID_PACKET (0x12) Pacote demasiado pequeno para cabeçalho TCP
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Definir transferência em pedaços para pedido HTTP(S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Este serviço utiliza códigos de transferência em pedaços para enviar um pedido http(S) personalizado para o servidor especificado na chamada *nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect()* que previamente estabeleceu a ligação da tomada ao anfitrião remoto.

> [!NOTE]
> Se a aplicação utilizar códigos de transferência em pedaços para enviar um pacote de dados de pedido, deve ligar para este serviço depois de ligar para *nx_web_http_client_request_packet_allocate*() e antes de ligar *nx_web_http_client_reqeust_packet_send* ().

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **chunk_size** Tamanho dos dados dos pedaços em octetos.
- **packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) com sucesso.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Adicione um cabeçalho personalizado a um pedido HTTP personalizado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Description

Este serviço adiciona um cabeçalho personalizado (sob a forma de nome de campo e valor) a um pedido HTTP personalizado criado com n *x_web_http_client_request_initialize()*.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido. **Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**

> [!NOTE]
> Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência. Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **field_name** Cadeia de nomes de campo (por exemplo, "Tipo de Conteúdo").
- **name_length** Comprimento da corda de nome de campo em bytes.
- **field_value** Cadeia de valor de campo (por exemplo, "aplicação/fluxo de octetos").
- **value_length** Comprimento da cadeia de valor em bytes.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Adição bem sucedida do cabeçalho a pedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

Inicialize um pedido HTTP personalizado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Description

Este serviço cria um pedido HTTP personalizado e associa-o à instância do Cliente HTTP. Ao contrário do nx_web_http_client_get_start mais *simples()* (juntamente com os métodos de PUT, POST e as versões seguras associadas dessas API), o pedido personalizado não é enviado até que o serviço *nx_web_http_client_request_send()* seja chamado.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().*** Isto permite pedidos HTTP personalizados destinados a aplicações específicas.

> [!NOTE]
> Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência. Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_send))* para criar e enviar pedidos HTTP.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_client_request_initialize_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **método** O método de pedido HTTP para usar. As opções são definidas da seguinte forma:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **recurso** Nome do recurso a ser transferido.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **input_size** Tamanho dos dados de entrada para PUT e POST. Passe 0 para outras operações.
- **transfer_encoding_trunked** Parâmetro reservado para futuro suporte de transferência com tronco.
- **nome de utilizador** Nome de utilizador para recursos protegidos.
- **senha** Senha para recursos protegidos.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida do pedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltavam algumas informações necessárias (por exemplo, input_size para PUT ou POST).

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

Inicialize um pedido HTTP personalizado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a>Description

Este serviço cria um pedido HTTP personalizado e associa-o à instância do Cliente HTTP. Ao contrário do nx_web_http_client_get_start mais *simples()* (juntamente com os métodos de PUT, POST e as versões seguras associadas dessas API), o pedido personalizado não é enviado até que o serviço *nx_web_http_client_request_send()* seja chamado.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().*** Isto permite pedidos HTTP personalizados destinados a aplicações específicas.

> [!NOTE]
> Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência. Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_send))* para criar e enviar pedidos HTTP.

As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_client_request_initialize*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **método** O método de pedido HTTP para usar. As opções são definidas da seguinte forma:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **recurso** Nome do recurso a ser transferido.
- **resource_length** Comprimento de cadeia do recurso solicitado.
- **hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor. Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP. A corda do hospedeiro não pode ser nULA.
- **host_length** Comprimento de corda do hospedeiro.
- **input_size** Tamanho dos dados de entrada para PUT e POST. Passe 0 para outras operações.
- **transfer_encoding_trunked** Parâmetro reservado para futuro suporte de transferência com tronco.
- **nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.
- **username_length** Comprimento da corda do nome de utilizador para autenticação.
- **senha** Ponteiro para senha opcional para autenticação.
- **password_length** Comprimento da palavra-passe para autenticação.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida do pedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltavam algumas informações necessárias (por exemplo, input_size para PUT ou POST).

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Enviar pacote de dados de pedido HTTP(S) para servidor remoto

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia um pacote de dados de pedido HTTP(S) personalizado criado com *nx_web_http_client_request_packet_allocate* () para o servidor especificado na *chamada nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect,* que previamente estabeleceu a ligação da tomada ao anfitrião remoto.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio bem sucedido do pacote de dados de pedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

Envie um pedido HTTP personalizado

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Description

Este serviço envia um pedido HTTP personalizado criado com *nx_web_http_client_request_initialize()* para o servidor especificado no *nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect()* ambos já estabeleceram previamente a ligação da tomada ao anfitrião remoto.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().*** Isto permite pedidos HTTP personalizados destinados a aplicações específicas.

> [!NOTE]
> Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência. Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Envio bem sucedido de pedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Obtenha o próximo pacote de dados de recursos

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Description

Este serviço recupera o próximo pacote de conteúdo do recurso solicitado pelo pedido anterior. Devem ser feitas sucessivas chamadas para esta rotina até que seja recebida a situação de devolução do NX_WEB_HTTP_GET_DONE.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **packet_ptr** Destino para ponteiro de pacotes que contenha conteúdo parcial de recursos.
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) obter com sucesso do pacote do cliente HTTP.
- **NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP O pacote de obter do cliente está feito
- **NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está em modo get.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Comprimento do pacote inválido
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) CÓDIGO DE ESTADO HTTP 100 Continuar
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP código de estado 101 Protocolos de comutação
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) CÓDIGO DE ESTADO HTTP 201 Criado
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP código de estado 202 Aceite
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) CÓDIGO DE Estado HTTP 203 Informação Não Autorizada
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) CÓDIGO DE Estado HTTP 204 Sem Conteúdo
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) CÓDIGO DE Estado HTTP 205 Redefinir Conteúdo
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) CÓDIGO DE Estado HTTP 206 Conteúdo parcial
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) CÓDIGO DE ESTADO HTTP 300 Escolhas Múltiplas
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) CÓDIGO DE ESTADO HTTP 301 Movido Permanentemente
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) CÓDIGO DE ESTADO HTTP 302 Encontrado
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) CÓDIGO DE Estado HTTP 303 Ver Outros
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) CÓDIGO de Estado HTTP 304 Não Modificado
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) CÓDIGO de Estado HTTP 305 Use Proxy
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) CÓDIGO DE Estado HTTP 307 Reorientação Temporária
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) CÓDIGO DE Estado HTTP 400 Mau Pedido
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) CÓDIGO DE Estado HTTP 401 Não Autorizado
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) CÓDIGO DE ESTADO HTTP 402 Pagamento necessário
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) CÓDIGO DE Estado HTTP 403 Proibido
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) CÓDIGO DE ESTADO HTTP 404 Não Encontrado
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) CÓDIGO DE Estado HTTP 405 Método não permitido
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) CÓDIGO de Estado HTTP 406 Não Aceitável
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) CÓDIGO DE ESTADO HTTP 408 Prazo de saída
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) CÓDIGO DE ESTADO HTTP 409 Conflito
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) CÓDIGO de Estado HTTP 410 Desaparecido
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) CÓDIGO DE ESTADO HTTP 411 Comprimento necessário
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) CÓDIGO de Estado HTTP 412 Pré-condição falhou
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP código de estado 413 Entidade de pedido demasiado grande
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP código de estado 414 Solicitar URL demasiado grande
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) CÓDIGO DE ESTADO HTTP 415 Tipo de Mídia Não Suportado
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP código de estado 416 Intervalo solicitado não é satisfatório
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP código de estado 417 Expectativa falhou
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) CÓDIGO DE Estado HTTP 500 Erro interno do servidor
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) CÓDIGO de Estado HTTP 501 Não implementado
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) CÓDIGO DE ESTADO HTTP 502 Bad Gateway
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) CÓDIGO DE ESTADO HTTP 503 Serviço Indisponível
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) CÓDIGO DE ESTADO HTTP 504 Gateway Time-out
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) VERSÃO HTTP 505 HTTP não suportada
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

Desateia a chamada para invocar ao processar os cabeçalhos HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Description

Este serviço atribui uma chamada que será invocada sempre que o Cliente NetX Web HTTP processa um cabeçalho HTTP numa resposta recebida a partir de um servidor HTTP remoto. A chamada é invocada uma vez para cada cabeçalho na resposta à medida que é processada. O retorno permite que uma aplicação http cliente aceda a cada um dos cabeçalhos na resposta do servidor HTTP para tomar quaisquer ações desejadas para além do processamento básico que o Cliente Web HTTP NetX faz.

### <a name="input-parameters"></a>Parâmetros de Entrada

**client_ptr** Ponteiro para http bloco de controlo do cliente.

**callback_function** Chamada invocada durante o processamento do cabeçalho de resposta. O retorno é invocado com o nome de campo e valor como cordas (e seus comprimentos). Por exemplo, o cabeçalho "Content-Length: 100" faria com que a função fosse invocada com "Content-Length" para *field_name* e a cadeia "100" para *field_value*.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição bem sucedida de chamadas.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

Abra uma sessão de TLS para um servidor HTTPS para pedidos personalizados

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Description

Este método **destina-se a HTTPS protegidos por TLS.**

Este serviço abre uma sessão de TLS segura para um servidor HTTPS, mas não envia quaisquer pedidos. Os pedidos são criados com *n x_web_http_client_request_initialize()* e enviados *através nx_web_http_client_request_send()*. Os cabeçalhos HTTP personalizados podem ser adicionados ao pedido utilizando *nx_web_http_client_request_header_add()*.

A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido. **Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**

> [!NOTE]
> Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência. Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **server_ip** Endereço IP do servidor HTTPS remoto.
- **server_port** Porta no servidor HTTPS remoto (por exemplo, 443 para HTTPS).
- **tls_setup** Callback usado para configurar a configuração TLS. A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).
- **wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP. As opções de espera são definidas da seguinte forma:
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Ligação bem sucedida da sessão TLS.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_WEB_HTTP_NOT_READY (0x3000A) Outro pedido já está em curso.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>API http e https servidor

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Desa esta hora de chamada para recuperar a idade máxima e a data do URL

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Description

Este serviço define o serviço de retorno invocado para obter a idade máxima e última data modificada do recurso especificado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **cache_info_get** Ponteiro para a chamada
- **max_age** Ponteiro para a idade máxima de um recurso
- **dados** Ponteiro para a última data modificada devolvida.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definiu com sucesso a chamada
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização

### <a name="example"></a>Exemplo

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

Enviar dados da função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Description

Este serviço envia os dados no pacote fornecido da rotina de chamada da aplicação. Isto é normalmente usado para enviar dados dinâmicos associados a pedidos GET/POST. Note que se esta função for utilizada, a rotina de retorno é responsável pelo envio de toda a resposta no formato adequado. Além disso, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **data_ptr** Ponteiro para os dados a enviar.
- **data_length** Número de bytes para enviar.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso dados do Servidor
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

Criar um cabeçalho de resposta numa função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Description

Este serviço é utilizado na rotina de chamada do servidor HTTP(S) (definida pela aplicação) para gerar um cabeçalho de resposta HTTP. A rotina de chamada do servidor é invocada quando o servidor HTTP responde a pedidos de OBTER, PUT e DELETE do Cliente que requerem uma resposta HTTP. Esta função retira a informação de resposta da aplicação e gera o cabeçalho de resposta apropriado. Consulte o *nx_web_http_server_create de* serviço para obter mais informações sobre a rotina de chamada do pedido do servidor.

Esta API está prevadida. Os desenvolvedores são encorajados a usar *nx_web_http_server_callback_generate_response_header_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem
- **status_code** Indicar o estado do recurso. Exemplos:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length** Tamanho do conteúdo em bytes
- **content_type** Tipo de HTTP, por exemplo, "texto/planície"
- **additional_header** Ponteiro para texto adicional do cabeçalho

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso criado cabeçalho HTML
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

Criar um cabeçalho de resposta numa função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Description

Este serviço é utilizado na rotina de chamada do servidor HTTP(S) (definida pela aplicação) para gerar um cabeçalho de resposta HTTP. A rotina de chamada do servidor é invocada quando o servidor HTTP responde a pedidos de OBTER, PUT e DELETE do Cliente que requerem uma resposta HTTP. Esta função retira a informação de resposta da aplicação e gera o cabeçalho de resposta apropriado. Consulte o *nx_web_http_server_create de* serviço para obter mais informações sobre a rotina de chamada do pedido do servidor.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem
- **status_code** Indicar o estado do recurso. Exemplos:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code_length** Comprimento da cadeia do código de estado
- **content_length** Tamanho do conteúdo em bytes
- **content_type** Tipo de HTTP, por exemplo, "texto/planície"
- **content_type_length** Comprimento de corda do tipo de conteúdo
- **additional_header** Ponteiro para texto adicional do cabeçalho
- **additional_header_length** Comprimento do texto adicional do cabeçalho

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso criado cabeçalho HTML
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

Envie um pacote HTTP da função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Este serviço envia uma resposta completa do servidor HTTP a partir de uma chamada HTTP. O servidor HTTP enviará o pacote com o NX_WEB_HTTP_SERVER _TIMEOUT_SEND. O cabeçalho HTTP e os dados devem ser anexados ao pacote. Se o estado de devolução indicar um erro, a aplicação HTTP deve libertar o pacote.

A chamada deve voltar NX_WEB_HTTP_CALLBACK_COMPLETED.

Consulte *nx_web_http_server_callback_generate_response_header para* um exemplo mais detalhado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para bloco de controlo do servidor HTTP
- **packet_ptr** Ponteiro para o pacote para enviar

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso o pacote do servidor HTTP
- **NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

Enviar resposta da função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Description

Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação. Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST. Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

Este serviço é precotado. Os desenvolvedores são encorajados a usar *nx_web_http_server_callback_response_send_extended()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **cabeçalho** Ponteiro para a corda do cabeçalho de resposta.
- **informação** Ponteiro para a cadeia de informação.
- **additional_info** Ponteiro para a cadeia de informações adicionais.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso a resposta do servidor HTTP

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

Enviar resposta da função de retorno

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Description

Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação. Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST. Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.

As cadeias de cabeçalho, informação e additional_info devem ser terminadas com nulos e o comprimento de cada corda corresponde ao comprimento especificado na lista de argumentos.

Este serviço substitui *nx_web_http_server_callback_response_send*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **cabeçalho** Ponteiro para a corda do cabeçalho de resposta.
- **header_length** Comprimento da corda do cabeçalho de resposta.
- **informação** Ponteiro para a cadeia de informação.
- **Information_length** Comprimento da cadeia de informação.
- **additional_info** Ponteiro para a cadeia de informações adicionais.
- **additional_info_length** Comprimento da cadeia de informações adicionais.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) enviou com sucesso a resposta do servidor HTTP

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

Obtenha conteúdo do pedido

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Description

Este serviço tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP. Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP. Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.
- **byte_offset** Número de bytes para compensar na área de conteúdo.
- **destination_ptr** Ponteiro para a área de destino para o conteúdo.
- **destination_size** Número máximo de bytes disponíveis na área de destino.
- **atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conteúdo satisfatório do servidor HTTP Obter
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP Erro interno do servidor
- **NX_WEB_HTTP_DATA_END** (0x30007) Conteúdo de fim do pedido
- **NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Servidor tempo limite para obter o próximo pacote de conteúdo
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

Obtenha conteúdo a partir do pedido/suporta comprimento de conteúdo zero comprimento

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Description

Este serviço é quase idêntico ao *nx_web_http_server_content_get;;* tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP. No entanto, trata os pedidos com contentamento comprimento de valor zero ('pedido vazio') como um pedido válido. Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).

Este serviço substitui *nx_web_http_server_content_get*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP. Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.
- **byte_offset** Número de bytes para compensar na área de conteúdo.
- **destination_ptr** Ponteiro para a área de destino para o conteúdo.
- **destination_size** Número máximo de bytes disponíveis na área de destino.
- **atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conteúdo HTTP bem sucedido obtém
- **NX_WEB_HTTP_ERROR** (0x30000) HTTP Erro interno do servidor
- **NX_WEB_HTTP_DATA_END** (0x30007) Conteúdo de fim do pedido
- **NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Servidor tempo limite na obtenção do próximo pacote
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

Obtenha o comprimento do conteúdo no pedido/suporta o comprimento do conteúdo de valor zero

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

Este serviço tenta recuperar o comprimento do conteúdo HTTP no pacote fornecido. O valor de retorno indica o estado de conclusão bem-sucedido e o valor real do comprimento é devolvido no ponteiro de entrada content_length. Se não houver conteúdo/comprimento de conteúdo HTTP = 0, esta rotina ainda devolve um estado de conclusão bem-sucedido e o ponteiro de entrada content_length aponta para um comprimento válido (zero). Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).

### <a name="input-parameters"></a>Parâmetros de Entrada

- **packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP. Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.
- **content_length** Ponteiro para valor recuperado do campo Content Length

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) sucesso http servidor comprimento de conteúdo obter
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Formato de cabeçalho HTTP impróprio
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

Criar uma instância do servidor HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Description

Este serviço cria uma instância http server, que funciona no contexto da sua própria linha ThreadX. As rotinas de *chamada de authentication_check* e *request_notify* de aplicações opcionais dão ao software de aplicação controlo sobre as operações básicas do Servidor HTTP.

Este serviço é utilizado para criar servidores HTTP de texto simples e servidores HTTPS protegidos por TLS. Para ativar o HTTPS utilizando o TLS, consulte o *serviço nx_web_http_server_secure_configure()*.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **http_server_name** Ponteiro para o nome do servidor HTTP.
- **ip_ptr** Ponteiro para instância IP previamente criada.
- **server_port** Porta de escuta TCP para a instância do servidor.
- **media_ptr** Ponteiro para a instância de media filex previamente criada.
- **stack_ptr** Ponteiro para a área da pilha de fio do servidor HTTP.
- **stack_size** Ponteiro para o tamanho da pilha de fio do servidor HTTP.
- **authentication_check** Função ponteiro para a rotina de verificação de autenticação da aplicação. Se especificado, esta rotina é chamada para cada pedido do Cliente HTTP. Se este parâmetro for NU, não será efetuada qualquer autenticação. Este parâmetro está precotado. Chame *nx_web_http_server_authenticate_check_set* em vez disso.
- **request_notify** Ponteiro de função para pedido de pedido de aplicação notificar rotina. Se especificado, esta rotina é chamada antes do processamento do servidor HTTP do pedido. Isto permite que o nome do recurso seja redirecionado ou campos dentro de um recurso a ser atualizado antes de completar o pedido do Cliente HTTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) o servidor HTTP com sucesso cria.
- NX_PTR_ERROR (0x07) Inválido HTTP Servidor, IP, meios de comunicação, stack ou ponteiro de piscina de pacotes.
- NX_WEB_HTTP_POOL_ERROR (0x30009) A carga útil do pacote não é suficientemente grande para conter o pedido HTTP completo.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

Excluir uma instância do servidor HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Este serviço elimina uma instância do servidor HTTP anteriormente criada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Com sucesso no servidor HTTP
- NX_PTR_ERROR (0x07) Ponteiro do servidor HTTP Inválido
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Recuperar a localização e a duração dos dados da entidade

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Description

Este serviço determina a localização do início dos dados dentro da atual entidade multipartidária nas mensagens do Cliente recebidas e o comprimento dos dados que não incluem a cadeia de limites. Internamente, o servidor HTTP atualiza as suas próprias compensações para que esta função possa ser novamente chamada no mesmo datagrama do Cliente para mensagens com várias entidades. O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.

Note que NX_WEB_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço. Note também que o pedido não deve libertar o pacote apontado por packet_pptr. Isto é feito internamente pelo servidor HTTP.

Consulte *nx_web_http_server_get_entity_header para* mais detalhes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o servidor HTTP
- **packet_pptr** Ponteiro para a localização do ponteiro do pacote. Note que o pedido não deve lançar este pacote
- **available_offset** Ponteiro para compensar os dados da entidade a partir do ponteiro pré-final do pacote
- **available_length** Ponteiro para o comprimento dos dados da entidade

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) recuperou com sucesso o tamanho e localização do conteúdo da entidade
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) O conteúdo dos marcadores multipartais internos do servidor HTTP já está encontrado
- NX_WEB_HTTP_ERROR (0x30000) HTTP Erro interno do servidor
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

Recuperar o conteúdo do cabeçalho da entidade

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Description

Este serviço recupera o cabeçalho da entidade no tampão especificado. Internamente HTTP Server atualiza os seus próprios ponteiros para localizar a próxima entidade multipartida num datagrama do Cliente com vários cabeçalhos de entidade. O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.

Note que NX_WEB_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço. Note também que o pedido não deve libertar o pacote apontado por packet_pptr.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o servidor HTTP
- **packet_pptr** Ponteiro para a localização do ponteiro do pacote. Note que o pedido não deve lançar este pacote
- **entity_header_buffer** Ponteiro para localização para armazenar cabeçalho da entidade
- **buffer_size** Tamanho do tampão de entrada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) entidade recuperada com sucesso
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Campo de cabeçalho de entidade não encontrado
- **NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou para receber o próximo pacote para mensagem de cliente multipacket
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço
- NX_WEB_HTTP_ERROR (0x30000) Erro interno HTTP

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

Desa esta hora de chamada para obter a data e hora de GMT

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Description

Este serviço define a chamada para obter data e hora DE GMT com um servidor HTTP previamente criado. Este serviço é invocado com o servidor HTTP está a criar um cabeçalho em respostas do servidor HTTP ao Cliente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o servidor HTTP
- **gmt_get** Ponteiro para retorno GMT
- **data** Ponteiro para a data recuperada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definiu com sucesso a chamada
- NX_PTR_ERROR (0x07) Pacote inválido ou ponteiro de parâmetros.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

Desloque a chamada para lidar com o utilizador/senha inválido

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Description

Este serviço define a chamada invocada quando um nome de utilizador e palavra-passe inválidos é recebido num Pedido de Cliente obter, colocar ou apagar, seja por digestão ou autenticação básica. O servidor HTTP deve ser previamente criado.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o servidor HTTP
- **invalid_username_password_callback** Ponteiro para chamada inválida do utilizador/passe
- **recurso** Ponteiro para o recurso especificado pelo cliente
- **client_address** Endereço do cliente
- **request_type** Indica o tipo de pedido do cliente. Pode ser:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definiu com sucesso a chamada
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

Definir mapas MIME adicionais para HTML

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Description

Este serviço permite ao desenvolvedor de aplicações HTTP adicionar tipos de MIME adicionais dos tipos de MIME predefinidos fornecidos pelo Servidor WEB HTTP NetX. Consulte *nx_web_http_server_get_type para lista* de tipos definidos.

Quando um pedido de cliente é recebido, por exemplo, um pedido GET, o servidor HTTP analisa o tipo de ficheiro solicitado a partir do cabeçalho HTTP utilizando preferencialmente o conjunto de mapas MIME adicional e se não for encontrado, procura uma correspondência no mapa padrão do servidor HTTP. Se não for encontrado qualquer correspondência, o tipo MIME predefine para "texto/planície".

Se a função de notificação de pedido estiver registada no servidor HTTP, o pedido de notificação de chamada pode ligar *nx_web_http_server_type_get_extended()* para analisar o tipo de ficheiro.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiros para a instância do servidor HTTP
- **mime_maps** Ponteiro para uma matriz de mapa MIME
- **mime_map_num** Número de mapas MIME na matriz

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) conjunto de mapas MIME do servidor HTTP Server
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

Alocar um pacote HTTP(S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço tenta atribuir um pacote para o servidor HTTP(S).

Note que se uma API do Servidor NetX ou HTTP subsequente utilizar este pacote como **entrada falhar**, como nx_packet_data_append ou **nx_web_http_server_callback_packet_send, a aplicação é responsável pela libertação do pacote. **

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.
- **packet_ptr** Ponteiro para pacote atribuído.
- **wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes. As opções de espera são definidas da seguinte forma:
  - **NX_NO_WAIT** (0x00000000) A seleção NX_NO_WAIT faz com que o fio de chamada regresse imediatamente se o pedido não puder ser cumprido.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.
  - **O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos
- **NX_NO_PACKET** (0x01) Sem pacote disponível
- **NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Extrair o comprimento do conteúdo e definir o ponteiro para o início dos dados

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Description

Este serviço extrai o comprimento do conteúdo do cabeçalho HTTP. Também atualiza o pacote fornecido da seguinte forma: o ponteiro pré-final do pacote (início da localização do tampão do pacote para escrever) é definido para o conteúdo HTTP (dados) acabado de passar o cabeçalho HTTP.

Se o início do conteúdo não for encontrado no pacote atual, a função aguarda que o próximo pacote seja recebido utilizando a opção de espera NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Note que isto não deve ser chamado antes de chamar *nx_web_http_server_get_entity_header()* porque modifica o ponteiro pré-final do pacote para além do cabeçalho da entidade.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para a instância do servidor HTTP
- **packet_ptr** Ponteiro para ponter pacote para devolver o pacote com ponteiro pré-final atualizado
- **content_length** Ponteiro para content_length extraído

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) comprimento de conteúdo HTTP encontrado e pacote atualizado com sucesso
- **NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou à espera do próximo Pacote
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

Receba o próximo pacote HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Description

Este serviço devolve o próximo pacote recebido na tomada do servidor HTTP. A opção de espera para receber um pacote é NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Note que, se for bem sucedido, a aplicação é responsável pela libertação do pacote.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **server_ptr** Ponteiro para a instância do servidor HTTP
- **packet_ptr** Ponteiro para pacote recebido

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) recebeu com sucesso o próximo pacote HTTP
- **NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou à espera do próximo Pacote
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Obtenha o parâmetro do pedido

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Description

Este serviço tenta recuperar o parâmetro HTTP URL especificado no pacote de pedido fornecido. Se o parâmetro HTTP solicitado não estiver presente, esta rotina devolve um estado de NX_WEB_HTTP_NOT_FOUND. Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create).).*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **packet_ptr** Ponteiro para pacote de pedido do cliente HTTP. Note que o pedido não deve libertar este pacote.
- **param_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de parâmetros.
- **param_ptr** Área de destino para copiar o parâmetro.
- **param_size** Devolva o comprimento total dos dados do parâmetro (em bytes).
- **max_param_size** Tamanho máximo da área de destino do parâmetro.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) O parâmetro do servidor HTTP com sucesso obtém
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Parâmetro especificado não encontrado
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parâmetro de pedido não devidamente terminado
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

Obtenha consulta a partir do pedido

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Description

Este serviço tenta recuperar a consulta de URL HTTP especificada no pacote de pedido fornecido. Se a consulta HTTP solicitada não estiver presente, esta rotina devolve um estado de NX_WEB_HTTP_NOT_FOUND. Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create).).*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **packet_ptr** Ponteiro para pacote de pedido do cliente HTTP. Note que o pedido não deve libertar este pacote.
- **query_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de consultas.
- **query_ptr** Área de destino para copiar a consulta.
- **query_size** Devolução do tamanho dos dados de consulta (em bytes).
- **max_query_size** Tamanho máximo do destino de consulta

área.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Consulta de servidor HTTP com sucesso obter
- **NX_WEB_HTTP_FAILED** (0x30002) Tamanho da consulta muito pequeno.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006) Consulta especificada não encontrada
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) Sem consulta no pedido do Cliente
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

Definir transferência em pedaços para resposta HTTP(S)

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Description

Este serviço utiliza códigos de transferência em pedaços para enviar um pacote de dados de resposta HTTP(S) personalizado criado com *nx_web_http_server_response_packet_allocate*() ao cliente.

> [!NOTE]
> Se a aplicação utilizar códigos de transferência em pedaços para enviar um pacote de dados de resposta, deve ligar para este serviço depois de ligar para *nx_web_http_server_response_packet_allocate*() e antes de ligar *para nx_web_http_server_callback_packet_send*().

### <a name="input-parameters"></a>Parâmetros de Entrada

- **client_ptr** Ponteiro para http bloco de controlo do cliente.
- **chunk_size** Tamanho dos dados dos pedaços em octetos.
- **packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Conjunto bem sucedido.
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

Configure um servidor HTTP para utilizar O TLS para HTTPS seguro

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Description

Este serviço configura uma instância do servidor NetX Web HTTP previamente criada para utilizar TLS para comunicações HTTPS seguras. Os parâmetros são usados para configurar todas as sessões TLS possíveis com estado idêntico para que cada cliente HTTPS que chega experimente um comportamento consistente. O número de sessões TLS é controlado utilizando o NX_WEB_HTTP_SESSION_MAX macro.

A tabela de rotina criptográfica (tabela cifrasumita) é partilhada entre todas as sessões de TLS, uma vez que contém apenas ponteiros de função.

Os amortecedores de metadados e de montagem de pacotes são divididos igualmente entre todas as sessões de TLS. Se o tamanho do tampão não for igualmente divisível pelo número de sessões, o restante não será reutilizado.

O certificado de identidade aprovado é utilizado por todas as sessões. Durante a operação TLS, o certificado de identidade do servidor é lido apenas de modo a não ser necessárias cópias para cada sessão.

Os certificados fidedignos são adicionados a cada sessão de TLS no Servidor HTTPS. Estes são utilizados para a autenticação do certificado cliente que é automaticamente ativado quando o espaço do certificado remoto é fornecido.

O conjunto de certificados remotos e o tampão são partilhados por padrão entre todas as sessões TLS. Os certificados remotos são utilizados para a autenticação do certificado cliente que é automaticamente ativado quando a contagem de certificados remotos não é zero. Devido à partilha do tampão, algumas sessões podem bloquear durante a validação do certificado.

Para desativar a autenticação do certificado do cliente, passe NX_NULL para o parâmetro remote_certificates e um valor de 0 para o parâmetro remote_certs_num.

Os valores de retorno incluirão quaisquer códigos de erro TLS resultantes de problemas na configuração das sessões TLS.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Indicação para a instância do servidor HTTP.
- **crypto_table** Ponteiro para a mesa de cifrasumita TLS.
- **metadata_buffer** Ponteiro para tampão de metadados criptográfico.
- **metadata_size** Tamanho do tampão de metadados criptográficos.
- **packet_buffer** Tampão de remontagem do pacote TLS.
- **packet_buffer** Tamanho do tampão de pacote TLS – deve ser igual a (<tamanho do tampão TLS desejado* NX_WEB_HTTP_SESSION_MAX).
- **identity_certificate** Certificado de identidade do servidor TLS – será utilizado para todas as sessões do servidor HTTPS.
- **trusted_certificates** Ponteiro para a matriz de objetos NX_SECURE_X509_CERT, utilizados para validar certificados de clientes recebidos se a autenticação do certificado do cliente for ativada através da passagem de um valor não zero para o parâmetro *remote_certs_num.*
- **trusted_certs_num** Número de certificados de confiança no conjunto *trusted_certificates.*
- **remote_certificates** Ponteiro para a matriz de objetos NX_SECURE_X509_CERT, utilizados para os certificados de cliente de entrada.
- **remote_certs_num** Número de certificados remotos. Deve ser o número máximo de certificados esperados dos clientes. A autenticação do certificado do cliente é ativada automaticamente quando esta não é zero.
- **remote_certificate_buffer** Tampão para conter certificados remotos de entrada de clientes se a autenticação do certificado do cliente estiver ativada. remote_cert_buffer_size Tamanho do tampão de certificados remotos. Deve ser igual a (<tamanho máximo esperado do certificado \* remote_certs_num).


### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.
- **NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS recebido está incorreto.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.
- **NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Falhou um envio de tomadaS TCP subjacentes.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.
- **NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.
- **NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor TLS remoto.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem TLS recebida tinha uma versão TLS desconhecida no seu cabeçalho.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem TLS recebida tinha uma versão TLS conhecida mas não suportada no seu cabeçalho.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.
- **NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

Inicie o servidor HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Este serviço inicia uma instância http ou https anteriormente criada.

Os servidores HTTPS partilham a mesma API que HTTP. Para ativar o HTTPS utilizando o TLS num servidor HTTP, consulte o *serviço nx_web_http_server_secure_configure().*

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Indicação para a instância do servidor HTTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Início do servidor HTTP Com sucesso
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

Parar o servidor HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Description

Este serviço para a instância do servidor HTTP anteriormente criado. Esta rotina deve ser chamada antes de eliminar uma instância do servidor HTTP.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Indicação para a instância do servidor HTTP.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Paragem de servidor HTTP bem sucedida
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_CALLER_ERROR (0x11) Inválido deste serviço

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Extrair o tipo de ficheiro do pedido do Cliente HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Description

> [!NOTE]
> Este serviço é precotado. Os utilizadores são encorajados a utilizar o serviço *nx_web_http_server_type_get_extended()*.

Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento em *string_size* a partir do *nome* do tampão de entrada , normalmente o URL. Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície". Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência. Os mapas MIME padrão no Servidor HTTP Web NetX são:

- html texto/html
- texto/html
- texto txt/planície
- gif imagem/gif
- jpg imagem/jpeg
- ico imagem/x-ícone

Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais. Consulte *nx_web_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiros para a instância do servidor HTTP
- **nome** Ponteiro para tampão para pesquisar
- **http_type_string** Ponteiro para a cadeia do tipo HTML extraída
- **string_size** Ponteiro para devolver comprimento de cadeia do tipo HTML extraído.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Extração bem sucedida do tipo
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Padrão "texto/planície" devolvido.

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

Extrair o tipo de ficheiro do pedido do Cliente HTTP

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Description

Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento em *string_size* a partir do *nome* do tampão de entrada , normalmente o URL. Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície". Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência. Os mapas MIME padrão no Servidor HTTP Web NetX são:

- html texto/html
- texto/html
- texto txt/planície
- gif imagem/gif
- jpg imagem/jpeg
- ico imagem/x-ícone

Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais. Consulte *nx_web_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.

Este serviço substitui *nx_web_http_server_type_get*(). Esta versão requer que os chamadores forneçam informações de comprimento à função.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiros para a instância do servidor HTTP
- **nome** Ponteiro para tampão para pesquisar
- **name_length** Comprimento do nome
- **http_type_string** Ponteiro para a cadeia do tipo HTML extraída
- **http_type_string_max_size** Tamanho do http_type_string tamanho do tampão
- **string_size** Ponteiro para devolver a cadeia do tipo HTML extraída

comprimento.

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) Extração bem sucedida do tipo
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Padrão "texto/planície" devolvido.

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

Detenda a função de retorno autenticado da digestão

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Description

Este serviço define a chamada invocada quando a digestão autenticada é realizada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiros para a instância do servidor HTTP
- **digest_authenticate_callback** Ponteiro para digerir chamada autenticada

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definiu com sucesso a chamada
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro
- NX_NOT_SUPPORTED (0x4B) Digerir autenticado não habilitado

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

Detenda a função de retorno autenticado da digestão

### <a name="prototype"></a>Prototype

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Description

Este serviço define a chamada invocada quando é efetuada uma verificação autenticada.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **http_server_ptr** Ponteiros para a instância do servidor HTTP
- **authenticate_check_externded** Ponteiro para autenticar retorno de verificação

### <a name="return-values"></a>Valores de devolução

- **NX_SUCCESS** (0x00) definiu com sucesso a chamada
- NX_PTR_ERROR (0x07) Entrada inválida do ponteiro

### <a name="allowed-from"></a>Permitido a partir de

Aplicação

### <a name="example"></a>Exemplo

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
