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
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="aaf8e-103">Capítulo 2 - Instalação e utilização do cliente NetX Duo SMTP</span><span class="sxs-lookup"><span data-stu-id="aaf8e-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="aaf8e-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX Duo SMTP Client.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="aaf8e-105">Instalação do cliente NetX Duo SMTP</span><span class="sxs-lookup"><span data-stu-id="aaf8e-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="aaf8e-106">O Cliente SMTP NetX Duo está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="aaf8e-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="aaf8e-107">O pacote inclui os seguintes ficheiros:</span><span class="sxs-lookup"><span data-stu-id="aaf8e-107">The package includes the following files:</span></span>

- <span data-ttu-id="aaf8e-108">**nxd_smtp_client.c** Arquivo C Fonte para NetX Duo SMTP Cliente API</span><span class="sxs-lookup"><span data-stu-id="aaf8e-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="aaf8e-109">**nxd_smtp_client.h** C Arquivo de cabeçalho para NetX Duo SMTP Cliente API</span><span class="sxs-lookup"><span data-stu-id="aaf8e-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="aaf8e-110">**demo_netxduo_smtp_client.c** Demonstração para Cliente SMTP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="aaf8e-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="aaf8e-111">**nxd_smtp_client.pdf Guia do Utilizador** Netx Duo SMTP Cliente API</span><span class="sxs-lookup"><span data-stu-id="aaf8e-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="aaf8e-112">Para utilizar a API do Cliente SMTP NetX Duo, toda a distribuição mencionada anteriormente pode ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="aaf8e-113">Por exemplo, se o NetX Duo estiver instalado no diretório "c:*\myproject"* então o *nxd_smtp_client.h e os* ficheiros nxd_smtp_client.c devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="aaf8e-114">Usando o Cliente SMTP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="aaf8e-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="aaf8e-115">Para criar a aplicação NetX Duo SMTP Client, tem primeiro de construir as bibliotecas ThreadX e NetX Duo e incluí-las no projeto de construção.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="aaf8e-116">O pedido deve então incluir o TX *_api.h* e *nx_api.h no seu código fonte de aplicação*.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="aaf8e-117">Isto permitirá os serviços ThreadX e NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="aaf8e-118">Deve também incluir *nxd_smtp_client.c* e *nxd_smtp_client.h* após *tx_api.h* e *nx_api.h para utilizar os serviços do SMTP Client.*</span><span class="sxs-lookup"><span data-stu-id="aaf8e-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="aaf8e-119">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e o código do objeto deve ser ligado juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="aaf8e-120">Isto é tudo o que é necessário para criar uma aplicação netX Duo SMTP Client.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="aaf8e-121">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="aaf8e-121">Small Example System</span></span>

<span data-ttu-id="aaf8e-122">Um exemplo de utilização do Cliente SMTP SMTP da NetX Duo é descrito na Figura 1 que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="aaf8e-123">O pacote de pacotes para a instância IP é criado usando o serviço nx_packet_pool_create, na linha 68 e tem uma carga útil de pacote muito pequena.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="aaf8e-124">Isto porque a instância IP apenas envia pacotes de controlo que não requerem muita carga útil.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="aaf8e-125">O conjunto de pacotes do Cliente SMTP criado na linha 84 e é utilizado para transmitir mensagens do Cliente SMTP para o servidor e dados de mensagens.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="aaf8e-126">A sua carga útil é muito maior.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-126">Its packet payload is much larger.</span></span> <span data-ttu-id="aaf8e-127">A instância IP é criada na linha 118 usando a mesma piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="aaf8e-128">A TCP, necessária para o protocolo SMTP, está ativada na instância IP na linha 130.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="aaf8e-129">Na linha de aplicação, o Cliente SMTP é criado utilizando o serviço *nxd_smtp_client_create,* na linha 170.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="aaf8e-130">O serviço *nxd_smtp_client_create* suporta ligações de servidores IPv4 e IPv6 SMTP, embora este exemplo esteja limitado a IPv4.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="aaf8e-131">Em seguida, a mensagem de correio é submetida ao Cliente SMTP para transmissão na linha 184 utilizando o serviço *nx_smtp_mail_send.*</span><span class="sxs-lookup"><span data-stu-id="aaf8e-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="aaf8e-132">Note que a linha de assunto com o cabeçalho do conteúdo do correio é criada separadamente do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="aaf8e-133">Note também que o pedido de envio de correio aceita apenas um endereço de correio destinatário que se presume ser sintáticamente correto.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="aaf8e-134">Em seguida, o pedido termina o Cliente SMTP na linha 200.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="aaf8e-135">O *serviço nx_smtp_client_delete* verifica se a ligação da tomada está fechada e a porta está desvinculada.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="aaf8e-136">Note que cabe à aplicação do Cliente SMTP apagar o conjunto de pacotes se já não tiver uso para o mesmo.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

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

<span data-ttu-id="aaf8e-137">**Figura 1. Exemplo de uso do cliente SMTP com o Duo NetX**</span><span class="sxs-lookup"><span data-stu-id="aaf8e-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="aaf8e-138">Opções de configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="aaf8e-138">Client Configuration Options</span></span>

<span data-ttu-id="aaf8e-139">Existem várias opções de configuração com a API do Cliente SMTP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="aaf8e-140">Segue-se uma lista de todas as opções descritas em detalhe:</span><span class="sxs-lookup"><span data-stu-id="aaf8e-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="aaf8e-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** Esta opção define o tamanho da janela de receção do Cliente TCP.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="aaf8e-142">Isto deve ser definido para abaixo do tamanho MTU do hardware Ethernet subjacente e permitir espaço para cabeçalhos IP e TCP.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="aaf8e-143">O tamanho padrão da janela TCP do Cliente NetX Duo SMTP é de 1460.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="aaf8e-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** Esta opção define o tempo limite na atribuição de pacotes NetX.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="aaf8e-145">O tempo limite de tempo do pacote do Cliente NetX Duo SMTP predefinido é de 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="aaf8e-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** Esta opção define o tempo limite de ligação da tomada TCP do cliente.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="aaf8e-147">O tempo limite de ligação padrão do Cliente NetX Duo SMTP é de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="aaf8e-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** Esta opção define o tempo limite de desconexão da tomada TCP do cliente.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="aaf8e-149">O tempo limite de desconexão do cliente NetX Duo SMTP predefinido é de 5 segundos\*.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="aaf8e-150">Note que se o Cliente SMTP encontrar um erro interno, como uma ligação partida, poderá terminar a ligação com um tempo de espera zero.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="aaf8e-151">**NX_SMTP_GREETING_TIMEOUT** Esta opção define o tempo limite para o Cliente receber a resposta do Servidor à sua saudação.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="aaf8e-152">O valor padrão do Cliente NetX Duo SMTP é de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="aaf8e-153">**NX_SMTP_ENVELOPE_TIMEOUT** Esta opção define o prazo para o Cliente receber a resposta do Servidor a um comando do Cliente.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="aaf8e-154">O valor padrão do Cliente NetX Duo SMTP é de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="aaf8e-155">**NX_SMTP_MESSAGE_TIMEOUT** Esta opção define o prazo para o Cliente receber a resposta do Servidor para receber os dados da mensagem de correio.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="aaf8e-156">O valor padrão do Cliente NetX Duo SMTP é de 30 segundos.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="aaf8e-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** Esta opção define a opção de espera do tampão para armazenar a palavra-passe do utilizador durante a autenticação SMTP com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="aaf8e-158">O valor predefinido é de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="aaf8e-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** Esta opção define o tamanho do tampão para extrair o desafio do Servidor durante a autenticação SMTP.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="aaf8e-160">O valor predefinido é de 200 bytes.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-160">The default value is 200 bytes.</span></span> <span data-ttu-id="aaf8e-161">Para a autenticação LOGIN e PLAIN, o Cliente SMTP pode provavelmente utilizar um tampão menor.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="aaf8e-162">**NX_SMTP_CLIENT_MAX_PASSWORD** Esta opção define o tamanho do tampão para armazenar a palavra-passe do utilizador durante a autenticação SMTP com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="aaf8e-163">O valor predefinido é de 20 bytes.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="aaf8e-164">**NX_SMTP_CLIENT_MAX_USERNAME** Esta opção define o tamanho do tampão para armazenar o nome de utilizador do anfitrião durante a autenticação SMTP com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="aaf8e-165">O valor predefinido é de 40 bytes.</span><span class="sxs-lookup"><span data-stu-id="aaf8e-165">The default value is 40 bytes.</span></span> 
