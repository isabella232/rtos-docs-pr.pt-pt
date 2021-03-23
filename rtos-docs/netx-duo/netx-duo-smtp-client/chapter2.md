---
title: Capítulo 2 - Instalação e utilização do cliente NetX Duo SMTP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Duo SMTP Client.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825784"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Capítulo 2 - Instalação e utilização do cliente NetX Duo SMTP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Duo SMTP Client.

## <a name="netx-duo-smtp-client-installation"></a>Instalação do cliente NetX Duo SMTP

O Cliente SMTP NetX Duo está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui os seguintes ficheiros:

- **nxd_smtp_client.c** Arquivo C Fonte para NetX Duo SMTP Cliente API
- **nxd_smtp_client.h** C Arquivo de cabeçalho para NetX Duo SMTP Cliente API
- **demo_netxduo_smtp_client.c** Demonstração para Cliente SMTP da NetX Duo
- **nxd_smtp_client.pdf Guia do Utilizador** Netx Duo SMTP Cliente API

Para utilizar a API do Cliente SMTP NetX Duo, toda a distribuição mencionada anteriormente pode ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo estiver instalado no diretório "c:*\myproject"* então o *nxd_smtp_client.h e os* ficheiros nxd_smtp_client.c devem ser copiados para este diretório.

## <a name="using-netx-duo-smtp-client"></a>Usando o Cliente SMTP da NetX Duo

Para criar a aplicação NetX Duo SMTP Client, tem primeiro de construir as bibliotecas ThreadX e NetX Duo e incluí-las no projeto de construção. O pedido deve então incluir o TX *_api.h* e *nx_api.h no seu código fonte de aplicação*. Isto permitirá os serviços ThreadX e NetX Duo. Deve também incluir *nxd_smtp_client.c* e *nxd_smtp_client.h* após *tx_api.h* e *nx_api.h para utilizar os serviços do SMTP Client.*

Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e o código do objeto deve ser ligado juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para criar uma aplicação netX Duo SMTP Client.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de utilização do Cliente SMTP SMTP da NetX Duo é descrito na Figura 1 que aparece abaixo. O pacote de pacotes para a instância IP é criado usando o serviço nx_packet_pool_create, na linha 68 e tem uma carga útil de pacote muito pequena. Isto porque a instância IP apenas envia pacotes de controlo que não requerem muita carga útil. O conjunto de pacotes do Cliente SMTP criado na linha 84 e é utilizado para transmitir mensagens do Cliente SMTP para o servidor e dados de mensagens. A sua carga útil é muito maior. A instância IP é criada na linha 118 usando a mesma piscina de pacotes. A TCP, necessária para o protocolo SMTP, está ativada na instância IP na linha 130.

Na linha de aplicação, o Cliente SMTP é criado utilizando o serviço *nxd_smtp_client_create,* na linha 170. O serviço *nxd_smtp_client_create* suporta ligações de servidores IPv4 e IPv6 SMTP, embora este exemplo esteja limitado a IPv4. Em seguida, a mensagem de correio é submetida ao Cliente SMTP para transmissão na linha 184 utilizando o serviço *nx_smtp_mail_send.* Note que a linha de assunto com o cabeçalho do conteúdo do correio é criada separadamente do corpo da mensagem. Note também que o pedido de envio de correio aceita apenas um endereço de correio destinatário que se presume ser sintáticamente correto.

Em seguida, o pedido termina o Cliente SMTP na linha 200. O *serviço nx_smtp_client_delete* verifica se a ligação da tomada está fechada e a porta está desvinculada. Note que cabe à aplicação do Cliente SMTP apagar o conjunto de pacotes se já não tiver uso para o mesmo.

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

**Figura 1. Exemplo de uso do cliente SMTP com o Duo NetX**

## <a name="client-configuration-options"></a>Opções de configuração do cliente

Existem várias opções de configuração com a API do Cliente SMTP NetX Duo. Segue-se uma lista de todas as opções descritas em detalhe:

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Esta opção define o tamanho da janela de receção do Cliente TCP. Isto deve ser definido para abaixo do tamanho MTU do hardware Ethernet subjacente e permitir espaço para cabeçalhos IP e TCP. O tamanho padrão da janela TCP do Cliente NetX Duo SMTP é de 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** Esta opção define o tempo limite na atribuição de pacotes NetX. O tempo limite de tempo do pacote do Cliente NetX Duo SMTP predefinido é de 2 segundos.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Esta opção define o tempo limite de ligação da tomada TCP do cliente. O tempo limite de ligação padrão do Cliente NetX Duo SMTP é de 10 segundos.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Esta opção define o tempo limite de desconexão da tomada TCP do cliente. O tempo limite de desconexão do cliente NetX Duo SMTP predefinido é de 5 segundos*. Note que se o Cliente SMTP encontrar um erro interno, como uma ligação partida, poderá terminar a ligação com um tempo de espera zero.
- **NX_SMTP_GREETING_TIMEOUT** Esta opção define o tempo limite para o Cliente receber a resposta do Servidor à sua saudação. O valor padrão do Cliente NetX Duo SMTP é de 10 segundos.
- **NX_SMTP_ENVELOPE_TIMEOUT** Esta opção define o prazo para o Cliente receber a resposta do Servidor a um comando do Cliente. O valor padrão do Cliente NetX Duo SMTP é de 10 segundos.
- **NX_SMTP_MESSAGE_TIMEOUT** Esta opção define o prazo para o Cliente receber a resposta do Servidor para receber os dados da mensagem de correio. O valor padrão do Cliente NetX Duo SMTP é de 30 segundos.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** Esta opção define a opção de espera do tampão para armazenar a palavra-passe do utilizador durante a autenticação SMTP com o Servidor. O valor predefinido é de 20 bytes.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Esta opção define o tamanho do tampão para extrair o desafio do Servidor durante a autenticação SMTP. O valor predefinido é de 200 bytes. Para a autenticação LOGIN e PLAIN, o Cliente SMTP pode provavelmente utilizar um tampão menor.
- **NX_SMTP_CLIENT_MAX_PASSWORD** Esta opção define o tamanho do tampão para armazenar a palavra-passe do utilizador durante a autenticação SMTP com o Servidor. O valor predefinido é de 20 bytes. 
- **NX_SMTP_CLIENT_MAX_USERNAME** Esta opção define o tamanho do tampão para armazenar o nome de utilizador do anfitrião durante a autenticação SMTP com o Servidor. O valor predefinido é de 40 bytes. 
