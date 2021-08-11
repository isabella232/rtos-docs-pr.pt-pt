---
title: Capítulo 1 - Introdução a HTTP e HTTPS
description: Este capítulo introduz o Azure RTOS NetX Duo HTTP/HTTPS para módulo Web.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5f50419be3171d3df8544d1b34d603822f339785923f8a8199dc5b5ddcac281
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801760"
---
# <a name="chapter-1---introduction-to-http-and-https"></a>Capítulo 1 - Introdução a HTTP e HTTPS

O Protocolo de Transferência de Hipertextos (HTTP) é um protocolo concebido para transferir conteúdo na Web. HTTP é um protocolo simples que utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de conteúdo. Por isso, HTTP é um protocolo de transferência de conteúdo altamente fiável. HTTP é um dos protocolos de aplicação mais utilizados. Todas as operações na Web utilizam o protocolo HTTP.

HTTPS é a versão segura do protocolo HTTP, que implementa HTTP utilizando a Segurança da Camada de Transporte (TLS) para garantir a ligação TCP subjacente. Para além da configuração adicional necessária para configurar o TLS, https é basicamente idêntico ao HTTP em uso.

## <a name="general-http-requirements"></a>Requisitos Gerais HTTP

Para funcionar corretamente, o pacote NetX Web HTTP requer que o NetX Duo (versão 5.10 ou posterior) seja instalado. Além disso, deve ser criada uma instância IP e a TCP deve ser ativada nessa mesma instância de PI. Para o suporte a HTTPS, o NetX Secure TLS (versão 5.11 ou posterior) também deve ser instalado (ver secção seguinte). O ficheiro de demonstração na secção "Small Example System" **do Capítulo 2** demonstra como isto é feito.

A parte do cliente HTTP do pacote NetX Web HTTP não tem outros requisitos.

A parte do servidor HTTP do pacote NetX Web HTTP tem vários requisitos adicionais. Em primeiro lugar, requer acesso total à *porta 80 bem conhecida* da TCP para o tratamento de todos os pedidos HTTP do Cliente (isto pode ser alterado pela aplicação para qualquer outra porta TCP válida). O servidor HTTP também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX. Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente. Isto é discutido em secções posteriores deste guia.

## <a name="https-requirements"></a>Requisitos HTTPS

Para que https funcione corretamente, o pacote NetX Web HTTP requer que o NetX Duo (versão 5.10 ou posterior) e o NetX Secure TLS (versão 5.11 ou posterior) estejam ambos instalados. Além disso, deve ser criada uma instância IP e a TCP deve ser ativada nesse mesmo caso DEP para utilização com TLS. A sessão TLS terá de ser inicializada com rotinas criptográficas apropriadas, um certificado ca fidedigno, e o espaço deve ser atribuído para certificados que serão fornecidos por anfitriões de servidores remotos durante o aperto de mão TLS. O ficheiro de demonstração na secção "Small Example HTTPS System" **do Capítulo 2** demonstrará como isto é feito.

A parte do cliente HTTPS do pacote NetX Web HTTP não tem mais requisitos.

A parte https server do pacote NetX Web HTTP tem vários requisitos adicionais. Em primeiro lugar, requer acesso total à *conhecida porta 443* da TCP para o tratamento de todos os pedidos https do Cliente (como com o texto simples HTTP, esta porta pode ser alterada pela aplicação). Em segundo lugar, a sessão TLS terá de ser inicializada com rotinas criptográficas adequadas e um certificado de identidade do servidor (ou Chave Pré-Partilhada). O SERVIDOR HTTPS também foi concebido para ser utilizado com o sistema de ficheiros incorporado FileX. Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente. A utilização do FileX é discutida em secções posteriores deste guia.

Consulte a documentação NetX Secure para obter mais informações sobre as opções de configuração para TLS.

A menos que seja notado, todas as funcionalidades HTTP descritas neste documento também se aplicam a HTTPS.

## <a name="http-and-https-constraints"></a>Constrangimentos HTTP e HTTPS

NetX Web HTTP implementa a norma HTTP 1.1. No entanto, aqui estão os seguintes constrangimentos:

1. Solicitação de pipelining não é suportado
1. O SERVIDOR HTTP suporta a autenticação básica e mD5, mas não mD5-sess. Atualmente, o Cliente HTTP suporta apenas a autenticação básica. Ao utilizar o TLS para HTTPS, a autenticação HTTP ainda pode ser utilizada.
1. Não é suportada qualquer compressão de conteúdo.
1. Os pedidos TRACE, OPTIONS e CONNECT não são suportados.
1. O conjunto de pacotes associado ao servidor http ou cliente deve ser grande o suficiente para segurar o cabeçalho HTTP completo.
1. HTTP Os serviços do cliente são apenas para transferência de conteúdos - não existem utilitários de exibição fornecidos neste pacote.

## <a name="http-url-resource-names"></a>URL HTTP (Nomes de Recursos)

O protocolo HTTP foi concebido para transferir conteúdo na Web. O conteúdo solicitado é especificado pelo Localizador de Recursos Universais (URL). Este é o componente principal de cada pedido HTTP. Os URLs começam sempre com um caracteres "/" e normalmente correspondem a ficheiros no servidor HTTP. As extensões de ficheiros HTTP comuns são apresentadas abaixo:

- **.htm** (ou **.html)** Linguagem de marcação de hipertexto (HTML)
- **.txt** Texto simples ASCII
- **.gif** Imagem binária do GIF
- **.xbm** Imagem binária de Xbitmap

## <a name="http-client-requests"></a>Pedidos de clientes HTTP

O HTTP tem um mecanismo simples para solicitar conteúdo web. Existe um conjunto de comandos HTTP padrão que são emitidos pelo Cliente depois de uma ligação ter sido estabelecida com sucesso na *porta 80 (porta 443 para HTTPS)*. O seguinte mostra alguns dos comandos HTTP básicos:

- **RECURSO  GET HTTP/1.1** Obtenha o recurso especificado
- **RECURSO *POST* HTTP/1.1** Obtenha o recurso especificado e passe a entrada anexa ao Servidor HTTP
- **Recurso *DE CABEÇA* HTTP/1.1** Tratado como um GET mas não conteúdo é devolvido pelo Servidor HTTP
- **RECURSO  PUT HTTP/1.1** Coloque o recurso no servidor HTTP
- **EXCLUIR *recurso* HTTP/1.1** Eliminar recurso no Servidor

Estes comandos ASCII são gerados internamente pelos navegadores Web e pelos serviços do Cliente NetX Web HTTP para realizar operações HTTP com um Servidor HTTP.

Note que a aplicação do Cliente HTTP deve utilizar a porta 80, ou a porta 443 se HTTPS for utilizado. Tanto as APIs http clientes como do servidor tomam a porta como um parâmetro – as macros NX_WEB_HTTP_SERVER_PORT (porta 80) e NX_WEB_HTTPS_SERVER_PORT (porta 443) são definidas por conveniência. A porta http server também pode ser alterada em tempo de execução utilizando o serviço *nx_web_http_client_set_connect_port().* Consulte o Capítulo 4 para mais detalhes sobre este serviço.

## <a name="http-server-responses"></a>RESPOSTAS HTTP Servidor

O Servidor HTTP utiliza a mesma *conhecida porta TCP 80 (443 para HTTPS)* para enviar respostas de comando do Cliente. Uma vez que o servidor HTTP processa o comando do Cliente, retorna uma cadeia de resposta ASCII que inclui um código de estado numérico de 3 dígitos. A resposta numérica é utilizada pelo software HTTP Client para determinar se a operação foi bem sucedida ou falhou. Segue-se uma lista de várias respostas do servidor HTTP aos comandos do Cliente:

- **200** Pedido foi bem sucedido
- **400** Pedido não foi formado corretamente
- **401** Pedido não autorizado, o cliente precisa enviar autenticação
- **404** Não foi encontrado recurso especificado a pedido
- **500** Erro interno do servidor HTTP
- **501** Pedido não implementado pelo SERVIDOR HTTP
- Serviço **502** não está disponível

Por exemplo, um pedido bem sucedido do Cliente para colocar o ficheiro "test.htm" é respondido com a mensagem "HTTP/1.1 200 OK".

## <a name="http-communication"></a>Comunicação HTTP

Como mencionado anteriormente, o SERVIDOR HTTP utiliza a *conhecida porta TCP 80 (443 para HTTPS)* para fazer os pedidos do Cliente. HTTP Os clientes podem utilizar qualquer porta TCP disponível para ligações de saída. A sequência geral dos eventos HTTP é a seguinte:

**HTTP GET Request**:

1. O cliente emite ligação TCP à porta do Servidor 80 (ou 443 para HTTPS).
1. Se o HTTPS estiver a ser utilizado, a ligação TCP é seguida por um aperto de mão TLS para autenticar o servidor e estabelecer um canal seguro.
1. O cliente envia o pedido **de *recurso* GET HTTP/1.1**" (juntamente com outras informações do cabeçalho).
1. O servidor constrói uma mensagem "**HTTP/1.1 200 OK**" com informações adicionais seguidas imediatamente pelo conteúdo do recurso (se houver).
1. O servidor desliga-se do cliente (o TLS é desligado se o HTTPS estiver a ser utilizado).
1. O cliente desliga-se da tomada (o TLS é desligado após o alerta de desconexão do servidor).

**HTTP PUT Request**:

1. O cliente emite ligação TCP à porta do Servidor 80 (ou 443).
1. Se o HTTPS estiver a ser utilizado, a ligação TCP é seguida por um aperto de mão TLS para autenticar o servidor e estabelecer um canal seguro.
1. O cliente envia o pedido "PUT Resource HTTP/1.1", juntamente com outras informações do cabeçalho, e seguido do conteúdo do recurso.
1. O servidor constrói uma mensagem "HTTP/1.1 200 OK" com informações adicionais seguidas imediatamente pelo conteúdo do recurso.
1. O servidor executa uma desconexão.
1. O cliente realiza uma desconexão.

> [!NOTE]
> Como mencionado anteriormente, o SERVIDOR HTTP pode alterar a porta de ligação predefinido (80 ou 443) em tempo de execução outra porta utilizando o *nx_web_http_client_set_connect_port()* para servidores web que utilizam portas alternativas para se conectarem aos clientes.

## <a name="http-authentication"></a>Autenticação HTTP

A autenticação HTTP é opcional e não é necessária para todos os pedidos da Web. Existem dois sabores de autenticação, nomeadamente *básicos* e *digeridos.* A autenticação básica é equivalente ao *nome* e autenticação *de senha* encontrado em muitos protocolos. Na autenticação básica HTTP, o nome e as palavras-passe são concatenados e codificados no formato base64. A principal desvantagem da autenticação básica é o nome e a palavra-passe são transmitidas abertamente no pedido. Isto torna um pouco fácil para o nome e a senha serem roubados. A autenticação digestiva aborda este problema nunca transmitindo o nome e a palavra-passe no pedido. Em vez disso, um algoritmo é usado para obter uma digestão de 128 bits a partir do nome, palavra-passe e outras informações. O Servidor Web HTTP NetX suporta o algoritmo padrão de digestão MD5.

Quando é necessária a autenticação? O SERVIDOR HTTP decide se um recurso solicitado requer autenticação. Se for necessária a autenticação e o pedido do Cliente não incluir a autenticação adequada, é enviada ao Cliente uma resposta "HTTP/1.1 401 Não Autorizada" com o tipo de autenticação necessária. Espera-se então que o Cliente forme um novo pedido com a autenticação adequada.

Quando o HTTPS é utilizado, o SERVIDOR HTTPS ainda pode utilizar a autenticação HTTP. Neste caso, o TLS é utilizado para encriptar todo o tráfego HTTP, pelo que a utilização de autenticação *HTTP básica* não representa um risco de segurança. A autenticação *digestão* também é permitida, mas não proporciona melhorias significativas de segurança em relação à autenticação básica em relação ao TLS.

## <a name="http-authentication-callback"></a>Chamada de autenticação HTTP

Como mencionado anteriormente, a autenticação HTTP é opcional e não é necessária em todas as transferências web. Além disso, a autenticação é normalmente dependente de recursos. O acesso de alguns recursos no Servidor requer autenticação, enquanto outros não. O pacote NetX Web HTTP Server permite que a aplicação especifique (através da chamada ***nx_web_http_server_create)*** uma rotina de chamada de autenticação que é chamada no início do tratamento de cada pedido do Cliente HTTP.

A rotina de chamada fornece ao NetX Web HTTP Server o nome de utilizador, palavra-passe e cadeias de reinos associadas ao recurso e devolve o tipo de autenticação necessária. Se não for necessária qualquer autenticação para o recurso, a chamada de autenticação deve devolver o valor de **NX_WEB_HTTP_DONT_AUTHENTICATE**. Caso contrário, se for necessária uma autenticação básica para o recurso especificado, a rotina deverá voltar **NX_WEB_HTTP_BASIC_AUTHENTICATE**. E, finalmente, se a autenticação da digestão MD5 for necessária, a rotina de retorno deve voltar **NX_WEB_HTTP_DIGEST_AUTHENTICATE**. Se não for necessária qualquer autenticação para qualquer recurso fornecido pelo Servidor HTTP, a chamada não é necessária e um ponteiro NULO pode ser fornecido à chamada de criação do SERVIDOR HTTP.

O formato da rotina de chamada autenticada da aplicação é muito simples e é definido abaixo:

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

Os parâmetros de entrada são definidos da seguinte forma:

- **request_type** Especifica o pedido do cliente HTTP, os pedidos válidos são definidos como:
  - **NX_WEB_HTTP_SERVER_GET_REQUEST**
  - **NX_WEB_HTTP_SERVER_POST_REQUEST**
  - **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
  - **NX_WEB_HTTP_SERVER_PUT_REQUEST**
  - **NX_WEB_HTTP_SERVER_DELETE_REQUEST**
- **recurso** Recurso específico solicitado.
- **nome** Destino para o ponteiro para o nome de utilizador necessário.
- **senha** Destino para o ponteiro para a senha necessária.
- **reino** Destino para o ponteiro para o reino para esta autenticação.

O valor de devolução da rotina de autenticação especifica se for necessária autenticação. os ponteiros de nome, palavra-passe e de reino não são utilizados se **NX_WEB_HTTP_DONT_AUTHENTICATE** for devolvido pela rotina de chamada de autenticação. Caso contrário, o desenvolvedor do servidor HTTP deve **certificar-se** de que NX_WEB_HTTP_MAX_USERNAME e **NX_WEB_HTTP_MAX_PASSWORD** definidos em *nx_web_http_server.h* são suficientemente grandes para o nome de utilizador e palavra-passe especificados na chamada de autenticação. Ambos têm um tamanho padrão de 20 caracteres.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP Nome de utilizador/password inválido

A chamada opcional de nome de utilizador/palavra-passe inválida no Servidor HTTP NetX web é invocada se o servidor HTTP receber um nome de utilizador inválido e uma combinação de palavra-passe num pedido do Cliente. Se a aplicação do servidor HTTP registar uma chamada com o servidor HTTP, será invocada se a autenticação básica ou digestão falhar *em nx_web_http_server_get_process()* em *nx_web_http_server_put_process()* ou *em nx_web_http_server_delete_process().*

Para registar uma chamada com o servidor HTTP, o seguinte serviço é definido para o servidor HTTP Web NetX.

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

Os tipos de pedidos são definidos da seguinte forma:

- **NX_WEB_HTTP_SERVER_GET_REQUEST**
- **NX_WEB_HTTP_SERVER_POST_REQUEST**
- **NX_WEB_HTTP_SERVER_HEAD_REQUEST**
- **NX_WEB_HTTP_SERVER_PUT_REQUEST**
- **NX_WEB_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP Insira a chamada do cabeçalho de data GMT

Existe uma chamada opcional no Servidor HTTP NetX web para inserir um cabeçalho de data nas suas mensagens de resposta. Esta chamada é invocada quando o Servidor HTTP está a responder a um pedido de colocação ou de obter

Para registar uma chamada de data GMT com o servidor HTTP, é definido o seguinte serviço.

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

O tipo de dados NX_WEB_HTTP_SERVER_DATE é definido da seguinte forma:

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP Cache Info Obter Callback

O SERVIDOR HTTP tem uma chamada de retorno para solicitar a idade máxima e data a partir da aplicação HTTP para um recurso específico. Estas informações são utilizadas para determinar se o servidor HTTP envia uma página inteira em resposta a um pedido do Cliente Obter. Se o "se modificado desde" no pedido do Cliente não for encontrado ou não corresponder à data "última modificada" devolvida pela chamada de cache, toda a página é enviada.

Para registar a chamada com o servidor HTTP é definido o seguinte serviço:

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a>SUPORTE DE Codificação de Transferências HTTP

Quando o comprimento total da mensagem HTTP não puder ser determinado antes de a enviar, a função de codificação de transferências em pedaços pode ser utilizada para enviar mensagens como série de pedaços sem o campo de cabeçalho "Content-Length". Esta funcionalidade é suportada em todas as mensagens de pedido e resposta HTTP. Como recetor, esta função é suportada e o cabeçalho do pedaço é processado de forma transparente pela lógica interna. Como remetente, a *API nx_web_http_client_request_chunked_set* e *nx_web_http_server_response_chunked_set* devem ser invocadas pelo cliente e pelo servidor, respectivamente.

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

Para mais informações sobre estes serviços, consulte as suas descrições no Capítulo 3 "Descrição dos Serviços HTTP".

## <a name="http-multipart-support"></a>APOIO HTTP Multipart

As extensões multiusos de correio de Internet (MIME) destinavam-se originalmente ao protocolo SMTP, mas a sua utilização espalhou-se para HTTP. O MIME permite que as mensagens contenham tipos de mensagens mistas (por exemplo, imagem/jpg e texto/planície) dentro da mesma mensagem. O Servidor Web HTTP NetX tem serviços para determinar o tipo de conteúdo em mensagens HTTP que contenham MIME do Cliente. Para permitir o suporte e utilização de http multipartes, a opção de configuração **NX_WEB_HTTP_MULTIPART_ENABLE** deve ser definida.

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

Para obter mais informações sobre a utilização destes serviços, consulte a sua descrição no capítulo 3 "Descrição dos Serviços HTTP".

## <a name="http-multi-thread-support"></a>SUPORTE HTTP Multi-Thread

Os serviços do cliente NetX Web HTTP podem ser chamados a partir de vários fios simultaneamente. No entanto, ler ou escrever pedidos para uma determinada instância http cliente deve ser feito em sequência a partir do mesmo fio.

Se utilizar HTTPS, os serviços do cliente NetX Web HTTP podem ser chamados a partir de múltiplos fios, mas devido à complexidade acrescida da funcionalidade TLS subjacente, cada fio deve ter uma única instância http cliente independente (NX_WEB_HTTP_CLIENT estrutura de controlo).

## <a name="http-rfcs"></a>HTTP RFCs

O NetX Web HTTP está em conformidade com o RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2616 "Hypertext Transfer Protocol – HTTP/1.1", RFC 2581 "TCP Congestion Control", RFC 1122 "Requirements for Internet Hosts", e RFCs relacionados.

Para HTTPS, o NetX Web HTTP está em conformidade com o RFC 2818 "HTTP over TLS".
