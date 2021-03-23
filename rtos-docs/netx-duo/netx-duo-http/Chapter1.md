---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo HTTP HTTP
description: Este capítulo introduz o módulo Azure RTOS NetX Duo HTTP.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 442149536ac6847808fbba183b96ac78832a82c0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825970"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-http"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo HTTP HTTP

O Protocolo de Transferência de Hipertextos (HTTP) é um protocolo concebido para transferir conteúdo na Web. HTTP é um protocolo simples que utiliza serviços fiáveis de Protocolo de Controlo de Transmissão (TCP) para executar a sua função de transferência de conteúdo. Por isso, HTTP é um protocolo de transferência de conteúdo altamente fiável. HTTP é um dos protocolos de aplicação mais utilizados. Todas as operações na Web utilizam o protocolo HTTP. Azure RTOS NetX Duo HTTP acomoda as redes IPv4 e IPv6. O IPv6 não altera diretamente o protocolo HTTP, embora sejam necessárias algumas alterações no Azure RTOS NetX HTTP API para acomodar o IPv6 e serão descritas neste documento.

## <a name="http-requirements"></a>Requisitos HTTP

Para funcionar corretamente, o pacote NetX Duo HTTP requer a instalação de um Duo NetX (versão 5.2 ou posterior). Além disso, já deve ser criada uma instância IP e a TCP deve ser ativada nesse mesmo caso de PI. Uma aplicação de anfitrião IPv6 deve definir o seu endereço IPv6 local e global de ligação utilizando a API IPv6 e/ou DHCPv6. O ficheiro de demonstração na secção "Small Example System" **do Capítulo 2** demonstrará como isto é feito.

A parte http cliente do pacote NetX Duo HTTP não tem mais requisitos.

A parte do servidor HTTP do pacote NetX Duo HTTP tem vários requisitos adicionais. Em primeiro lugar, requer acesso completo à porta 80 bem conhecida da TCP para o tratamento de todos os pedidos HTTP do Cliente. O servidor HTTP também foi concebido para ser utilizado com o sistema de ficheiros incorporado em Ficheiros. Se o FileX não estiver disponível, o utilizador pode apresentar as porções do FileX utilizadas para o seu próprio ambiente. Isto é discutido em secções posteriores deste guia.

## <a name="http-constraints"></a>Restrições HTTP

O protocolo NetX Duo HTTP implementa a norma HTTP 1.0. No entanto, existem os seguintes constrangimentos:

1.  As ligações persistentes não são suportadas
2.  Solicitação de pipelining não é suportado
3.  O SERVIDOR HTTP suporta a autenticação básica e mD5, mas não mD5-sess. Atualmente, o Cliente HTTP suporta apenas a autenticação básica.
4.  Não é suportada qualquer compressão de conteúdo.
5.  Os pedidos TRACE, OPTIONS e CONNECT não são suportados.
6.  O conjunto de pacotes associado ao servidor http ou cliente deve ser grande o suficiente para segurar o cabeçalho HTTP completo.
7.  HTTP Os serviços do cliente são apenas para transferência de conteúdos - não existem utilitários de exibição fornecidos neste pacote.

## <a name="http-url-resource-names"></a>URL HTTP (Nomes de Recursos)

O protocolo HTTP foi concebido para transferir conteúdo na Web. O conteúdo solicitado é especificado pelo Localizador de Recursos Universais (URL). Este é o componente principal de cada pedido HTTP. Os URLs começam sempre com um caracteres *"/"* e normalmente correspondem a ficheiros no servidor HTTP. As extensões de ficheiros HTTP comuns são apresentadas abaixo:

| Extensão | Significado |
| --------- | ------- |
| .htm (ou .html) | HTML (Hypertext Markup Language) |
| .txt | Texto simples ASCII |
| .gif | Imagem binária do GIF |
| .xbm | Imagem binária de Xbitmap |

## <a name="http-client-requests"></a>Pedidos de clientes HTTP

O HTTP tem um mecanismo simples para solicitar conteúdo web. Existe basicamente um conjunto de comandos HTTP padrão que são emitidos pelo Cliente depois de uma ligação ter sido estabelecida com sucesso na *porta 80 bem conhecida* da TCP . O seguinte mostra alguns dos comandos HTTP básicos:

| Comando HTTP | Significado |
| ------------ | ------- |
| RECURSO GET HTTP/1.0 | *Obtenha o recurso especificado* |
| RECURSO POST HTTP/1.0 | *Obtenha o recurso especificado e passe a entrada anexa ao SERVIÇO HTTP* |
| Recurso DE CABEÇA HTTP/1.0 | *Tratado como um GET mas não conteúdo é devolvido pelo Servidor HTTP* |
| RECURSO PUT HTTP/1.0 | *Coloque o recurso no servidor HTTP* |
| EXCLUIR recurso HTTP/1.0 | *Eliminar recurso no Servidor* |

Estes comandos ASCII são gerados internamente pelos navegadores Web e pelos serviços do Cliente NetX HTTP para realizar operações HTTP com um Servidor HTTP.

> [!NOTE]
> A aplicação http cliente padrão para a porta de ligação de 80. No entanto, pode alterar a porta de ligação para o servidor HTTP em tempo de execução utilizando o serviço nx_http_client_set_connect_port. Consulte o Capítulo 4 para mais detalhes sobre este serviço. Isto é para acomodar servidores web que ocasionalmente usam portas alternativas para ligações ao Cliente.

## <a name="http-server-responses"></a>RESPOSTAS HTTP Servidor

O Servidor HTTP utiliza a mesma *conhecida porta TCP 80* para enviar respostas de comando do Cliente. Uma vez que o servidor HTTP processa o comando do Cliente, retorna uma cadeia de resposta ASCII que inclui um código de estado numérico de 3 dígitos. A resposta numérica é utilizada pelo software HTTP Client para determinar se a operação foi bem sucedida ou falhou. Segue-se uma lista de várias respostas do servidor HTTP aos comandos do Cliente:

| Campo Numérico | Significado |
| ------------- | ------- |
| *200* | *O pedido foi bem sucedido* |
| *400* |   *Pedido não foi formado corretamente* |
| *401* | *Pedido não autorizado, o cliente precisa enviar autenticação* |
| *404* | *Não foi encontrado recurso especificado a pedido* |
| *500* | *Erro interno do servidor HTTP* |
| *501* | *Pedido não implementado pelo SERVIDOR HTTP* |
| *502* | *O serviço não está disponível* |

Por exemplo, um pedido bem sucedido do Cliente para colocar o ficheiro "test.htm" é respondido com a mensagem "HTTP/1.0 200 OK".

## <a name="http-communication"></a>Comunicação HTTP

Como mencionado anteriormente, o SERVIDOR HTTP utiliza a conhecida porta TCP 80 para fazer os pedidos do Cliente em campo. HTTP Os clientes podem utilizar qualquer porta TCP disponível. A sequência geral dos eventos HTTP é a seguinte:

### <a name="http-get-request"></a>HTTP GET Request:

1.  O cliente emite A TCP liga-se à porta do Servidor 80.
2.  O cliente envia o pedido **de " GET resource HTTP/1.0**" (juntamente com outras informações do cabeçalho).
3.  O servidor constrói uma mensagem "**HTTP/1.0 200 OK**" com informações adicionais seguidas imediatamente pelo conteúdo do recurso (se houver).
4.  O servidor executa uma desconexão.
5.  O cliente realiza uma desconexão.

### <a name="http-put-request"></a>HTTP PUT Request:

1.  O cliente emite A TCP liga-se à porta do Servidor 80.
2.  O cliente envia o pedido de "**PUT Resource HTTP/1.0**", juntamente com outras informações do cabeçalho, e seguido pelo conteúdo do recurso.
3.  O servidor constrói uma mensagem "**HTTP/1.0 200 OK**" com informações adicionais seguidas imediatamente pelo conteúdo do recurso.
4.  O servidor executa uma desconexão.
5.  O cliente realiza uma desconexão.

> [!NOTE]
>Como mencionado anteriormente, o Cliente HTTP pode alterar a porta de ligação padrão de 80 para outra porta usando o *nx_http_client_set_connect_port* para servidores web que usam portas alternativas para se conectarem aos clientes.

## <a name="http-authentication"></a>Autenticação HTTP

A autenticação HTTP é opcional e não é necessária para todos os pedidos da Web. Existem dois sabores de autenticação, nomeadamente básicos e digeridos. A autenticação básica é equivalente ao nome e autenticação de senha encontrado em muitos protocolos. Na autenticação básica HTTP, o nome e as palavras-passe são concatenados e codificados no formato base64. A principal desvantagem da autenticação básica é o nome e a palavra-passe são transmitidas abertamente no pedido. Isto torna um pouco fácil para o nome e a senha serem roubados. A autenticação digestiva aborda este problema nunca transmitindo o nome e a palavra-passe no pedido. Em vez disso, um algoritmo é usado para obter uma chave de 128 bits ou digerir a partir do nome, palavra-passe e outras informações. O Servidor NetX HTTP suporta o algoritmo padrão de digestão MD5.

Quando é necessária a autenticação? Basicamente, o SERVIDOR HTTP decide se um recurso solicitado requer autenticação. Se for necessária a autenticação e o pedido do Cliente não incluir a autenticação adequada, é enviada ao Cliente uma resposta "HTTP/1.0 401 Não Autorizada" com o tipo de autenticação necessária. Espera-se então que o Cliente forme um novo pedido com a autenticação adequada.

## <a name="http-authentication-callback"></a>Chamada de autenticação HTTP

Como mencionado anteriormente, a autenticação HTTP é opcional e não é necessária em todas as transferências web. Além disso, a autenticação é normalmente dependente de recursos. O acesso de alguns recursos no Servidor requer autenticação, enquanto outros não. O pacote do Servidor NetX HTTP permite que a aplicação especifique (através da chamada *nx_http_server_create)* uma rotina de chamada de autenticação que é chamada no início do tratamento de cada pedido do Cliente HTTP.

A rotina de retorno fornece ao Servidor HTTP NetX o nome de utilizador, palavra-passe e cadeias de reinos associadas ao recurso e devolve o tipo de autenticação necessária. Se não for necessária qualquer autenticação para o recurso, a chamada de autenticação deve devolver o valor de **NX_HTTP_DONT_AUTHENTICATE**. Caso contrário, se for necessária uma autenticação básica para o recurso especificado, a rotina deve voltar **NX_HTTP_BASIC_AUTHENTICATE**. E, finalmente, se a autenticação da digestão MD5 for necessária, a rotina de retorno deve voltar **NX_HTTP_DIGEST_AUTHENTICATE**. Se não for necessária qualquer autenticação para qualquer recurso fornecido pelo Servidor HTTP, a chamada não é necessária e um ponteiro NULO pode ser fornecido à chamada de criação do SERVIDOR HTTP.

O formato da rotina de chamada autenticada da aplicação é muito simples e é definido abaixo:

```c
UINT nx_http_server_authentication_check(NX_HTTP_SERVER *server_ptr,
                                          UINT request_type, CHAR *resource,
                                          CHAR **name, CHAR **password,
                                          CHAR **realm);
```
Os parâmetros de entrada são definidos da seguinte forma:

| Parâmetro | Significado |
| --------- | --------|
| *request_type* | Especifica o pedido do cliente HTTP, os pedidos válidos são definidos como: <br/> **NX_HTTP_SERVER_GET_REQUEST**<br/>**NX_HTTP_SERVER_POST_REQUEST**<br/>**NX_HTTP_SERVER_HEAD_REQUEST**<br/>**NX_HTTP_SERVER_PUT_REQUEST**<br/>**NX_HTTP_SERVER_DELETE_REQUEST** |
| *recurso* | Recurso específico solicitado. |
| *nome* | Destino para o ponteiro para o nome de utilizador necessário. |
| *palavra-passe* | Destino para o ponteiro para a senha necessária. |
| *reino* | Destino para o ponteiro para o reino para esta autenticação. |

O valor de devolução da rotina de autenticação especifica se for necessária autenticação. ```name, password, and realm``` os ponteiros não são utilizados se **NX_HTTP_DONT_AUTHENTICATE** for devolvido pela rotina de chamada de autenticação. Caso contrário, o desenvolvedor do servidor HTTP deve garantir que **NX_HTTP_MAX_USERNAME** e **NX_HTTP_MAX_PASSWORD** definidos em *nxd_http_server.h* sejam suficientemente grandes para o nome de utilizador e palavra-passe especificados na chamada de autenticação. Estes estão ambos em incumprimento do tamanho de 20 chars.

## <a name="http-invalid-usernamepassword-callback"></a>HTTP Nome de utilizador/password inválido

A chamada opcional de nome de utilizador/palavra-passe inválida no NetX HTTP Server é invocada se o servidor HTTP receber um nome de utilizador inválido e uma combinação de palavra-passe num pedido do Cliente. Se a aplicação do servidor HTTP registar uma chamada com o servidor HTTP, será invocada se a autenticação básica ou digestão falhar em *nx_http_server_get_process*, *em nx_http_server_put_process*, ou em *nx_http_server_delete_process*.

Para registar uma chamada com o servidor HTTP, o seguinte serviço é definido no servidor HTTP Duo Netx.

```c
UINT nx_http_server_invalid_userpassword_notify_set(
                   NX_HTTP_SERVER *http_server_ptr,
                   UINT *invalid_username_password_callback)
                            (CHAR *resource,
                             NXD_ADDRESS *client_nxd_address,
                             UINT request_type))
```

Os tipos de pedidos são definidos da seguinte forma:
 - **NX_HTTP_SERVER_GET_REQUEST**
 - **NX_HTTP_SERVER_POST_REQUEST**
 - **NX_HTTP_SERVER_HEAD_REQUEST**
 - **NX_HTTP_SERVER_PUT_REQUEST**
 - **NX_HTTP_SERVER_DELETE_REQUEST**

## <a name="http-insert-gmt-date-header-callback"></a>HTTP Insira a chamada do cabeçalho de data GMT

Existe uma chamada opcional no NetX Duo HTTP Server para inserir um cabeçalho de data nas suas mensagens de resposta. Esta chamada é invocada quando o Servidor HTTP está a responder a um pedido de colocação ou de obter

Existe uma chamada opcional no NetX Duo HTTP Server para inserir um cabeçalho de data nas suas mensagens de resposta. Esta chamada é invocada quando o Servidor HTTP está a responder a um pedido de colocação ou de obter

Para registar uma chamada de data GMT com o servidor HTTP, o seguinte serviço é definido no servidor HTTP Duo NetX.

```c
UINT  _nx_http_server_gmt_callback_set(
                    NX_HTTP_SERVER *server_ptr,
                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date)
```

O tipo de dados NX_HTTP_SERVER_DATE é definido da seguinte forma:

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT          nx_http_server_year;           /* Year                 */
    UCHAR           nx_http_server_month;          /* Month                */
    UCHAR           nx_http_server_day;            /* Day                  */
    UCHAR           nx_http_server_hour;           /* Hour              */
    UCHAR           nx_http_server_minute;         /* Minute               */
    UCHAR           nx_http_server_second;         /* Second               */
    UCHAR           nx_http_server_weekday;        /* Weekday              */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a>HTTP Cache Info Obter Callback

O SERVIDOR HTTP tem uma chamada de retorno para solicitar a idade máxima e data da aplicação HTTP para um recurso específico. Estas informações são utilizadas para determinar se o servidor HTTP envia toda a página em resposta a um pedido do Cliente Obter. Se o "se modificado desde" no pedido do Cliente não for encontrado ou não corresponder à data "última modificada" devolvida pela chamada de cache, toda a página é enviada.

Para registar a chamada com o servidor HTTP é definido o seguinte serviço:

```c
UINT  _nx_http_server_cache_info_callback_set(
                              NX_HTTP_SERVER *server_ptr,
                              UINT (*cache_info_get)
                                    (CHAR *, UINT *, NX_HTTP_SERVER_DATE *))
```

## <a name="http-multipart-support"></a>APOIO HTTP Multipart

As extensões multiusos de correio de Internet (MIME) destinavam-se originalmente ao protocolo SMTP, mas a sua utilização espalhou-se para HTTP. O MIME permite que as mensagens contenham tipos de mensagens mistas (por exemplo, imagem/jpg e texto/planície) dentro da mesma mensagem. O NetX Duo HTTP Server adicionou serviços para determinar o tipo de conteúdo em mensagens HTTP que contenham MIME do Cliente. Para permitir o suporte e utilização de http multipartes, a opção de configuração **NX_HTTP_MULTIPART_ENABLE** deve ser definida.

```c
UINT  nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       UCHAR *entity_header_buffer,
                                       ULONG buffer_size);

UINT  nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_pptr,
                                        ULONG *available_offset,
                                        ULONG *available_length)
```

Para obter mais informações sobre a utilização destes serviços, consulte a sua descrição no capítulo 3 "Descrição dos Serviços HTTP".

## <a name="http-multi-thread-support"></a>SUPORTE HTTP Multi-Thread

Os serviços do Cliente NetX HTTP podem ser chamados a partir de várias linhas simultaneamente. No entanto, ler ou escrever pedidos para uma determinada instância http cliente deve ser feito em sequência a partir do mesmo fio.

## <a name="http-rfcs"></a>HTTP RFCs

O NetX HTTP está em conformidade com o RFC1945 "Hypertext Transfer Protocol/1.0, RFC 2581 "TCP Congestion Control", RFC 1122 "Requirements for Internet Hosts", e RFCs relacionados.
