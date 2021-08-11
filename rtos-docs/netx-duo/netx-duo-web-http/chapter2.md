---
title: Capítulo 2 - Instalação e utilização de HTTP e HTTPS
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Web HTTP.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fd8ab093d15c5413b0d5dac6d35b080674c3a332ec7a028fc462237135880d34
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783429"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>Capítulo 2 - Instalação e utilização de HTTP e HTTPS

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Web HTTP.

## <a name="product-distribution"></a>Distribuição de Produtos

HTTP para NetX está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui três ficheiros de origem, dois ficheiros, e um ficheiro que contém este documento, da seguinte forma:

- **nx_web_http_common.h** Arquivo comum de cabeçalho para NetX Web HTTP
- **nx_web_http_client.h** Ficheiro de cabeçalho para cliente HTTP para NetX Web
- **nx_web_http_server.h** Ficheiro de cabeçalho para SERVIDOR HTTP para NetX Web
- **nx_web_http_client.c** C Ficheiro de origem para cliente HTTP para NetX Web
- **nx_web_http_server.c** C Ficheiro de origem para servidor HTTP para NetX Web
- **nx_tcpserver.c** Ficheiro de origem C para várias tomadas TCP
- **nx_tcpserver.h** Ficheiro de cabeçalho para definir símbolos do servidor HTTPS
- **nx_md5.c** Algoritmos de digestão MD5
- **filex_stub.h** Ficheiro de stub se o FileX não estiver presente
- **nx_web_http.pdf** Descrição de HTTP para NetX Web
- **demo_netx_web_http.c** Demonstração de NetX Web HTTP

## <a name="http-installation"></a>Instalação HTTP

Para utilizar o NetX Web HTTP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nx_web_http_client.h* e *nx_web_http_client.c para aplicações do Cliente NetX Web HTTP, e nx_web_http_server.h,* *nx_web_http_server.c, nx_tcpserver.c e nx_tcpserver.h para aplicações netX Web HTTP Server. Para aplicações de cliente e servidor, nx_web_http_common.h também deve estar neste diretório. nx_md5.c* também devem ser copiados para este diretório se estiver a ser utilizada a autenticação digestiva. Para a aplicação de demonstração 'ram driver' os ficheiros HTTP Cliente e Servidor devem ser copiados para o mesmo diretório.

Se utilizar o TLS, deverá ter um diretório NetX Secure separado contendo os ficheiros de origem TLS.

## <a name="using-http"></a>Utilizar HTTP

A utilização da NetX Web HTTP é fácil. Basicamente, o código de aplicação deve incluir *nx_web_http_client.h* e/ou *nx_web_http_server.h* depois de incluir *tx_api.h, fx_api.h e* *nx_api.h* *(nx_web_http_common.h* está automaticamente incluído). Estes cabeçalhos permitem que a aplicação utilize ThreadX, FileX e NetX Duo, respectivamente. Para o suporte HTTPS, os cabeçalhos devem ser incluídos após a inclusão do ficheiro *nx_secure_tls.h* para obter suporte TLS.

Uma vez incluídos os ficheiros do cabeçalho HTTP, o código de aplicação pode então então fazer as chamadas de função HTTP especificadas posteriormente neste guia. A aplicação também deve *ligar-se a nx_web_http_client.c para clientes HTTP(S),* *nx_web_http_server.c e nx_tcpserver.c para servidores HTTP(S)* e *nx_md5.c (para autenticação digestiva)* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX Web HTTP.

> [!NOTE]
> Se NX_WEB_HTTP_DIGEST_ENABLE não for especificado no processo de construção, o ficheiro *.c md5 não* precisa de ser adicionado ao pedido. Da mesma forma, se não forem necessárias capacidades do Cliente HTTP, o ficheiro *nx_web_http_client.c* poderá ser omitido e, se não forem necessárias capacidades do Servidor HTTP, poderá ser omitida *nx_web_http_server.c.*
>
> A menos NX_WEB_HTTPS_ENABLE seja definida para ativar HTTPS (em vez de utilizar apenas texto simples HTTP) então o NetX Secure TLS não precisa de estar na construção.
>
> Uma vez que http utiliza os serviços NetX TCP, o TCP deve ser ativado com a chamada *nx_tcp_enable()* antes de utilizar HTTP.
>
> Ao utilizar HTTPS com NetX Secure TLS, o TLS deve ser rubricado com *nx_secure_tls_initialize()* antes de ligar para as rotinas HTTPS.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como utilizar o NetX Web HTTP é descrito na Figura 1.1 abaixo.

> [!CAUTION]
> Isto está previsto apenas para fins de demonstração e não é garantido que compile e corra como está.
>
> Consulte a distribuição de código de lançamento do NetX Duo HTTPS para ficheiros de código de demonstração que serão devidamente construídos no ambiente express logic nativo.  Saiba também que estas demos são mantidas intencionalmente muito simples, uma vez que se destinam a introduzir a aplicação HTTPS e/ou NetX Duo HTTPS para novos utilizadores.

Neste exemplo, o HTTP inclui o ficheiro *nx_web_http_client.h e nx_web_http_server.h são trazidos* *(netx_web_http_common.h* é incluído automaticamente). Em seguida, o servidor HTTP é criado em "*tx_application_define*". Note que o bloco de controlo do servidor HTTP "*Servidor*" foi definido como uma variável global anteriormente. Após a criação bem sucedida, o SERVIDOR HTTPS é iniciado. O Cliente HTTPS é então criado. Escreve o ficheiro e lê o ficheiro de volta.

> [!NOTE]
> NX_WEB_HTTPS_ENABLE é definido neste sistema.

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
        "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

**Figura 1.1 Exemplo de utilização https com NetX e NetX Secure TLS**

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção HTTP para NetX. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe. Os valores predefinidos são listados, mas podem ser redefinidos antes da inclusão de *nx_web_http_client.h e nx_web_http_server.h:*

- **NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros HTTP. É normalmente usado após a depurada aplicação.
- **NX_WEB_HTTP_DIGEST_ENABLE** Se definido, a autenticação utilizando a digestão MD5 está ativada no servidor HTTPS. Por defeito não está definido.
- **NX_WEB_HTTP_SERVER_PRIORITY** A prioridade da linha do servidor HTTPS. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.
- **NX_WEB_HTTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX. O Cliente HTTPS funcionará sem qualquer alteração se esta opção for definida. O SERVIDOR HTTPS terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.
- **NX_WEB_HTTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos HTTPS TCP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** O número de marcações de temporizador que o fio do Servidor é permitido funcionar antes de ceder a fios da mesma prioridade. O valor predefinido é 2. Note que esta opção está depreciada.
- **NX_WEB_HTTP_FRAGMENT_OPTION** Fragmento ativar pedidos HTTP TCP. Por predefinição, este valor é NX_DONT_FRAGMENT para desativar a fragmentação HTTP TCP.
- **NX_WEB_HTTP_SERVER_WINDOW_SIZE** Tamanho da janela da tomada do servidor. Por padrão, este valor é 2048 bytes.
- **NX_WEB_HTTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.
- **NX_WEB_HTTP_SERVER_TIMEOUT** Especifica o número de carraças ThreadX que os serviços internos vão suspender. O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_server_socket_accept().* O valor predefinido é definido para (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_disconnect().* O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_receive().* O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_send().* O valor predefinido é definido para 10 segundos (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_MAX_HEADER_FIELD** **Especifica o tamanho máximo do campo de cabeçalho HTTP. O valor predefinido é de 256.**
- **NX_WEB_HTTP_MULTIPART_ENABLE ** **Se definido, permite que o SERVIDOR HTTPS suporte pedidos HTTP multipart. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING** Especifica o número de ligações que podem ser em fila para o servidor HTTPS. O valor predefinido é definido para o dobro do número máximo de sessões de servidor.
- **NX_WEB_HTTP_MAX_RESOURCE** Especifica o número de bytes permitidos num *nome de recurso* fornecido pelo cliente. O valor predefinido é definido para 40.
- **NX_WEB_HTTP_MAX_NAME** Especifica o número de bytes permitidos num nome *de utilizador* fornecido pelo cliente . O valor predefinido é definido para 20.
- **NX_WEB_HTTP_MAX_PASSWORD** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente. O valor predefinido é definido para 20.
- **NX_WEB_HTTP_SERVER_SESSION_MAX** Especifica o número de sessões simultâneas para um servidor HTTP ou HTTPS. Para cada sessão é atribuída uma tomada TCP e uma sessão TLS (se HTTPS estiver ativado). O valor predefinido é definido para 2.
- **NX_WEB_HTTPS_ENABLE** Se definido, este macro permite TLS e HTTPS. Deixe indefinidos para libertar recursos se apenas o texto simples HTTP for desejado. Por padrão, esta macro não está definida.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE** Se definido, esta macro desativa a funcionalidade HTTP Keep-alive. Por padrão, esta macro não está definida.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do servidor. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 600.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Cliente. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 600.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS** Desajuste o tempo limite de retransmissão da tomada do servidor em segundos. O valor predefinido é definido para 2.
- **NX_WEB_HTTP_ SERVER_RETRY_MAX** Isto define o número máximo de retransmissão na tomada do Servidor. O valor predefinido é definido para 10.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT** Este valor é utilizado para definir o próximo tempo limite de retransmissão. O tempo limite atual é multiplicado pelo número de retransmissão até agora, alterado pelo valor do intervalo de tempo da tomada. O valor predefinido é definido para 1 para duplicar o tempo limite.
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** Isto especifica o número máximo de pacotes que podem ser encadeados na fila de retransmissão da tomada do Servidor. Se o número de pacotes encadeados chegar a este número, não podem ser enviados mais pacotes até que um ou mais pacotes enqueados sejam libertados. O valor predefinido é definido para 20.
