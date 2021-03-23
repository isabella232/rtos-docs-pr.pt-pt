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
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="49398-103">Capítulo 2 - Instalação e utilização do NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="49398-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="49398-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="49398-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="49398-105">Product Distribution</span></span>

<span data-ttu-id="49398-106">O Azure RTOS NetX pode ser obtido a partir do nosso repositório de código de fonte pública em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="49398-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="49398-107">**nx_http_client.h** Ficheiro de cabeçalho para cliente HTTP para NetX</span><span class="sxs-lookup"><span data-stu-id="49398-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="49398-108">**nx_http_server.h** Ficheiro de cabeçalho para servidor HTTP para NetX</span><span class="sxs-lookup"><span data-stu-id="49398-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="49398-109">**nx_http_client.c** C Ficheiro de origem para cliente HTTP para NetX</span><span class="sxs-lookup"><span data-stu-id="49398-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="49398-110">**nx_http_server.c** C Ficheiro de origem para servidor HTTP para NetX</span><span class="sxs-lookup"><span data-stu-id="49398-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="49398-111">**nx_md5.c** Algoritmos de digestão MD5</span><span class="sxs-lookup"><span data-stu-id="49398-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="49398-112">**filex_stub.h** Ficheiro de stub se o FileX não estiver presente</span><span class="sxs-lookup"><span data-stu-id="49398-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="49398-113">**nx_http.pdf** Descrição de HTTP para NetX</span><span class="sxs-lookup"><span data-stu-id="49398-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="49398-114">**demo_netx_http.c** Demonstração netx HTTP</span><span class="sxs-lookup"><span data-stu-id="49398-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="49398-115">Instalação HTTP</span><span class="sxs-lookup"><span data-stu-id="49398-115">HTTP Installation</span></span>

<span data-ttu-id="49398-116">Para utilizar HTTP para NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="49398-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="49398-117">Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então o *nx_http_client.h* e *nx_http_client.c* para aplicações do Cliente NetX HTTP, e *nx_http_server.h* e *nx_http_server.c* para aplicações do Servidor HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="49398-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="49398-118">*nx_md5.c* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="49398-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="49398-119">Para a aplicação de demonstração 'ram driver' os ficheiros netX HTTP cliente e servidor devem ser copiados para o mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="49398-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="49398-120">Utilizar HTTP</span><span class="sxs-lookup"><span data-stu-id="49398-120">Using HTTP</span></span>

<span data-ttu-id="49398-121">A utilização de HTTP para NetX é fácil.</span><span class="sxs-lookup"><span data-stu-id="49398-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="49398-122">Basicamente, o código de aplicação deve incluir *nx_http_client.h* e/ou *nx_http_server.h* depois de incluir *tx_api.h, fx_api.h* e *nx_api.h,* para utilizar ThreadX, FileX e NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="49398-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="49398-123">Uma vez incluídos os ficheiros do cabeçalho HTTP, o código de aplicação pode então então fazer as chamadas de função HTTP especificadas posteriormente neste guia.</span><span class="sxs-lookup"><span data-stu-id="49398-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="49398-124">O pedido deve também incluir *nx_http_client.c*, *nx_http_server.c* e *md5.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="49398-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="49398-125">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="49398-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="49398-126">Isto é tudo o que é necessário para usar o NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="49398-127">Se NX_HTTP_DIGEST_ENABLE não for especificado no processo de construção, o ficheiro *.c md5* não precisa de ser adicionado ao pedido.</span><span class="sxs-lookup"><span data-stu-id="49398-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="49398-128">Da mesma forma, se não forem necessárias capacidades do Cliente HTTP, o ficheiro *nx_http_client.c* poderá ser omitido.</span><span class="sxs-lookup"><span data-stu-id="49398-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="49398-129">Uma vez que http utiliza os serviços NetX TCP, o TCP deve ser ativado com a *chamada nx_tcp_enable* antes de utilizar HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="49398-130">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="49398-130">Small Example System</span></span>

<span data-ttu-id="49398-131">Um exemplo de como é fácil utilizar o NetX HTTP é descrito na Figura 1.1 que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="49398-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="49398-132">Neste exemplo, o HTTP inclui o ficheiro *nx_http_client.h e nx_http_server.h são trazidos* na linha 8.</span><span class="sxs-lookup"><span data-stu-id="49398-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="49398-133">Em seguida, o servidor HTTP é criado em "*tx_application_define*" na linha 131.</span><span class="sxs-lookup"><span data-stu-id="49398-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="49398-134">O bloco de controlo do servidor HTTP "*Server*" foi definido como uma variável global na linha 25 anteriormente.</span><span class="sxs-lookup"><span data-stu-id="49398-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="49398-135">Após a criação bem sucedida, um servidor HTTP é iniciado na linha 136.</span><span class="sxs-lookup"><span data-stu-id="49398-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="49398-136">Na linha 149 é criado o Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="49398-137">E finalmente, o Cliente escreve o ficheiro na linha 157 e lê o ficheiro na linha 195.</span><span class="sxs-lookup"><span data-stu-id="49398-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

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

<span data-ttu-id="49398-138">Figura 1.1 Exemplo de utilização HTTP com NetX</span><span class="sxs-lookup"><span data-stu-id="49398-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="49398-139">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="49398-139">Configuration Options</span></span>

<span data-ttu-id="49398-140">Existem várias opções de configuração para a construção HTTP para NetX.</span><span class="sxs-lookup"><span data-stu-id="49398-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="49398-141">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe.</span><span class="sxs-lookup"><span data-stu-id="49398-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="49398-142">Os valores predefinidos estão listados, mas podem ser redefinidos antes da inclusão de *nx_http_client.h e nx_http_server.h:*</span><span class="sxs-lookup"><span data-stu-id="49398-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="49398-143">**NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="49398-144">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="49398-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="49398-145">**NX_HTTP_SERVER_PRIORITY** A prioridade da linha do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="49398-146">Por predefinição, este valor é definido como 16 para especificar a prioridade 16.</span><span class="sxs-lookup"><span data-stu-id="49398-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="49398-147">**NX_HTTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX.</span><span class="sxs-lookup"><span data-stu-id="49398-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="49398-148">O Cliente HTTP funcionará sem qualquer alteração se esta opção for definida.</span><span class="sxs-lookup"><span data-stu-id="49398-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="49398-149">O Servidor HTTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="49398-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="49398-150">**NX_HTTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="49398-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="49398-151">Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="49398-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="49398-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** O número de marcações de temporizador que o fio do Servidor é permitido funcionar antes de ceder a fios da mesma prioridade.</span><span class="sxs-lookup"><span data-stu-id="49398-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="49398-153">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="49398-153">The default value is 2.</span></span>
- <span data-ttu-id="49398-154">**NX_HTTP_FRAGMENT_OPTION** Fragmento ativar pedidos HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="49398-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="49398-155">Por predefinição, este valor é NX_DONT_FRAGMENT para desativar a fragmentação HTTP TCP.</span><span class="sxs-lookup"><span data-stu-id="49398-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="49398-156">**NX_HTTP_SERVER_WINDOW_SIZE** Tamanho da janela da tomada do servidor.</span><span class="sxs-lookup"><span data-stu-id="49398-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="49398-157">Por padrão, este valor é 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="49398-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="49398-158">**NX_HTTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="49398-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="49398-159">O valor predefinido é definido para 0x80.</span><span class="sxs-lookup"><span data-stu-id="49398-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="49398-160">**NX_HTTP_SERVER_TIMEOUT** Especifica o número de carraças ThreadX que os serviços internos vão suspender.</span><span class="sxs-lookup"><span data-stu-id="49398-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="49398-161">O valor predefinido é definido para 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="49398-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="49398-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_server_socket_accept.*</span><span class="sxs-lookup"><span data-stu-id="49398-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="49398-163">O valor predefinido é definido para (10\* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="49398-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="49398-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_disconnect.*</span><span class="sxs-lookup"><span data-stu-id="49398-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="49398-165">O valor predefinido é definido para 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="49398-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="49398-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_receive.*</span><span class="sxs-lookup"><span data-stu-id="49398-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="49398-167">O valor predefinido é definido para 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="49398-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="49398-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Especifica o número de carraças threadX que os serviços internos suspenderão em chamadas internas *nx_tcp_socket_send.*</span><span class="sxs-lookup"><span data-stu-id="49398-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="49398-169">O valor predefinido é definido para 10 segundos (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="49398-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="49398-170">**NX_HTTP_MAX_HEADER_FIELD** Especifica o tamanho máximo do campo de cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="49398-171">O valor predefinido é de 256.</span><span class="sxs-lookup"><span data-stu-id="49398-171">The default value is 256.</span></span>
- <span data-ttu-id="49398-172">**NX_HTTP_MULTIPART_ENABLE** Se definido, permite que o SERVIDOR HTTP suporte pedidos HTTP multipart.</span><span class="sxs-lookup"><span data-stu-id="49398-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="49398-173">**NX_HTTP_SERVER_MAX_PENDING** Especifica o número de ligações que podem ser na fila para o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="49398-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="49398-174">O valor predefinido é definido para 5.</span><span class="sxs-lookup"><span data-stu-id="49398-174">The default value is set to 5.</span></span>
- <span data-ttu-id="49398-175">**NX_HTTP_MAX_RESOURCE** Especifica o número de bytes permitidos num *nome de recurso* fornecido pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="49398-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="49398-176">O valor predefinido é definido para 40.</span><span class="sxs-lookup"><span data-stu-id="49398-176">The default value is set to 40.</span></span>
- <span data-ttu-id="49398-177">**NX_HTTP_MAX_NAME** Especifica o número de bytes permitidos num nome *de utilizador* fornecido pelo cliente .</span><span class="sxs-lookup"><span data-stu-id="49398-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="49398-178">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="49398-178">The default value is set to 20.</span></span>
- <span data-ttu-id="49398-179">**NX_HTTP_MAX_PASSWORD** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="49398-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="49398-180">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="49398-180">The default value is set to 20.</span></span>
- <span data-ttu-id="49398-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Servidor.</span><span class="sxs-lookup"><span data-stu-id="49398-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="49398-182">O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote.</span><span class="sxs-lookup"><span data-stu-id="49398-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="49398-183">O valor predefinido é definido para 600.</span><span class="sxs-lookup"><span data-stu-id="49398-183">The default value is set to 600.</span></span>
- <span data-ttu-id="49398-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Especifica o tamanho mínimo dos pacotes na piscina especificado na criação do Cliente.</span><span class="sxs-lookup"><span data-stu-id="49398-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="49398-185">O tamanho mínimo é necessário para garantir que o cabeçalho HTTP completo pode ser contido num pacote.</span><span class="sxs-lookup"><span data-stu-id="49398-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="49398-186">O valor predefinido é definido para 300.</span><span class="sxs-lookup"><span data-stu-id="49398-186">The default value is set to 300.</span></span>
- <span data-ttu-id="49398-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Definir o tempo limite de retransmissão da tomada do servidor em segundos. O* valor predefinido é definido para 2.</span><span class="sxs-lookup"><span data-stu-id="49398-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="49398-188">**NX_HTTP_SERVER_RETRY_MAX** Isto define o número máximo de retransmissão na tomada do Servidor.</span><span class="sxs-lookup"><span data-stu-id="49398-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="49398-189">O valor predefinido é definido para 10.</span><span class="sxs-lookup"><span data-stu-id="49398-189">The default value is set to 10.</span></span>
- <span data-ttu-id="49398-190">**NX_HTTP_SERVER_RETRY_SHIFT** Este valor é utilizado para definir o próximo tempo limite de retransmissão.</span><span class="sxs-lookup"><span data-stu-id="49398-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="49398-191">O tempo limite atual é multiplicado pelo número de retransmissão até agora, alterado pelo valor do intervalo de tempo da tomada.</span><span class="sxs-lookup"><span data-stu-id="49398-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="49398-192">O valor predefinido é definido para 1 para duplicar o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="49398-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="49398-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** Isto especifica o número máximo de pacotes que podem ser encadeados na fila de retransmissão da tomada do Servidor.</span><span class="sxs-lookup"><span data-stu-id="49398-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="49398-194">Se o número de pacotes encadeados chegar a este número, não podem ser enviados mais pacotes até que um ou mais pacotes enqueados sejam libertados.</span><span class="sxs-lookup"><span data-stu-id="49398-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="49398-195">O valor predefinido é definido para 20.</span><span class="sxs-lookup"><span data-stu-id="49398-195">The default value is set to 20.</span></span>