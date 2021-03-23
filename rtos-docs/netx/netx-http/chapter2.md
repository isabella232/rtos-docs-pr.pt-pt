---
title: Capítulo 2 - Instalação e utilização do NetX HTTP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX HTTP.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826714"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>Capítulo 2 - Instalação e utilização do NetX HTTP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX HTTP.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX pode ser obtido a partir do nosso repositório de código de fonte pública em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .

- **nx_http_client.h** Ficheiro de cabeçalho para cliente HTTP para NetX
- **nx_http_server.h** Ficheiro de cabeçalho para servidor HTTP para NetX
- **nx_http_client.c** C Ficheiro de origem para cliente HTTP para NetX
- **nx_http_server.c** C Ficheiro de origem para servidor HTTP para NetX
- **nx_md5.c** Algoritmos de digestão MD5
- **filex_stub.h** Ficheiro de stub se o FileX não estiver presente
- **nx_http.pdf** Descrição de HTTP para NetX
- **demo_netx_http.c** Demonstração netx HTTP

## <a name="http-installation"></a>Instalação HTTP

Para utilizar HTTP para NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então o *nx_http_client.h* e *nx_http_client.c* para aplicações do Cliente NetX HTTP, e *nx_http_server.h* e *nx_http_server.c* para aplicações do Servidor HTTP NetX. *nx_md5.c* devem ser copiados para este diretório. Para a aplicação de demonstração 'ram driver' os ficheiros netX HTTP cliente e servidor devem ser copiados para o mesmo diretório.

## <a name="using-http"></a>Utilizar HTTP

A utilização de HTTP para NetX é fácil. Basicamente, o código de aplicação deve incluir *nx_http_client.h* e/ou *nx_http_server.h* depois de incluir *tx_api.h, fx_api.h* e *nx_api.h,* para utilizar ThreadX, FileX e NetX, respectivamente. Uma vez incluídos os ficheiros do cabeçalho HTTP, o código de aplicação pode então então fazer as chamadas de função HTTP especificadas posteriormente neste guia. O pedido deve também incluir *nx_http_client.c*, *nx_http_server.c* e *md5.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX HTTP.

>[!NOTE] 
> Se NX_HTTP_DIGEST_ENABLE não for especificado no processo de construção, o ficheiro *.c md5* não precisa de ser adicionado ao pedido. Da mesma forma, se não forem necessárias capacidades do Cliente HTTP, o ficheiro *nx_http_client.c* poderá ser omitido.

>[!NOTE] 
> Uma vez que http utiliza os serviços NetX TCP, o TCP deve ser ativado com a *chamada nx_tcp_enable* antes de utilizar HTTP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o NetX HTTP é descrito na Figura 1.1 que aparece abaixo. Neste exemplo, o HTTP inclui o ficheiro *nx_http_client.h e nx_http_server.h são trazidos* na linha 8. Em seguida, o servidor HTTP é criado em "*tx_application_define*" na linha 131.

>[!NOTE] 
> O bloco de controlo do servidor HTTP "*Server*" foi definido como uma variável global na linha 25 anteriormente.

Após a criação bem sucedida, um servidor HTTP é iniciado na linha 136. Na linha 149 é criado o Cliente HTTP. E finalmente, o Cliente escreve o ficheiro na linha 157 e lê o ficheiro na linha 195.

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
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

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

Figura 1.1 Exemplo de utilização HTTP com NetX

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção HTTP para NetX. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe. Os valores predefinidos estão listados, mas podem ser redefinidos antes da inclusão de *nx_http_client.h e nx_http_server.h:*

- **NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros HTTP. É normalmente usado após a depurada aplicação.
- **NX_HTTP_SERVER_PRIORITY** A prioridade da linha do servidor HTTP. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.
- **NX_HTTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX. O Cliente HTTP funcionará sem qualquer alteração se esta opção for definida. O Servidor HTTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.
- **NX_HTTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos HTTP TCP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** O número de marcações de temporizador que o fio do Servidor é permitido funcionar antes de ceder a fios da mesma prioridade. O valor predefinido é 2.
- **NX_HTTP_FRAGMENT_OPTION** Fragmento ativar pedidos HTTP TCP. Por predefinição, este valor é NX_DONT_FRAGMENT para desativar a fragmentação HTTP TCP.
- **NX_HTTP_SERVER_WINDOW_SIZE** Tamanho da janela da tomada do servidor. Por padrão, este valor é 2048 bytes.
- **NX_HTTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.
- **NX_HTTP_SERVER_TIMEOUT** Especifica o número de carraças ThreadX que os serviços internos vão suspender. O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_server_socket_accept.* O valor predefinido é definido para (10* NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_disconnect.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_receive.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_SEND** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_send.* O valor predefinido é definido para 10 segundos (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_MAX_HEADER_FIELD** Especifica o tamanho máximo do campo de cabeçalho HTTP. O valor predefinido é de 256.
- **NX_HTTP_MULTIPART_ENABLE** Se definido, permite que o SERVIDOR HTTP suporte pedidos HTTP multipart.
- **NX_HTTP_SERVER_MAX_PENDING** Especifica o número de ligações que podem ser na fila para o servidor HTTP. O valor predefinido é definido para 5.
- **NX_HTTP_MAX_RESOURCE** Especifica o número de bytes permitidos num *nome de recurso* fornecido pelo cliente. O valor predefinido é definido para 40.
- **NX_HTTP_MAX_NAME** Especifica o número de bytes permitidos num nome *de utilizador* fornecido pelo cliente . O valor predefinido é definido para 20.
- **NX_HTTP_MAX_PASSWORD** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente. O valor predefinido é definido para 20.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Servidor. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 600.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Cliente. O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote. O valor predefinido é definido para 300.
- **NX_HTTP_SERVER_RETRY_SECONDS** *Definir o tempo limite de retransmissão da tomada do servidor em segundos. O* valor predefinido é definido para 2.
- **NX_HTTP_SERVER_RETRY_MAX** Isto define o número máximo de retransmissão na tomada do Servidor. O valor predefinido é definido para 10.
- **NX_HTTP_SERVER_RETRY_SHIFT** Este valor é utilizado para definir o próximo tempo limite de retransmissão. O tempo limite atual é multiplicado pelo número de retransmissão até agora, alterado pelo valor do intervalo de tempo da tomada. O valor predefinido é definido para 1 para duplicar o tempo limite.
- **NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Isto especifica o número máximo de pacotes que podem ser encadeados na fila de retransmissão da tomada do Servidor. Se o número de pacotes encadeados chegar a este número, não podem ser enviados mais pacotes até que um ou mais pacotes enqueados sejam libertados. O valor predefinido é definido para 20.