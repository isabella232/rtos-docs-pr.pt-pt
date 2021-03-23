---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo TFTP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo TFTP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ffb0c433bf1a5665e07da3cc6c240f1d0d8c87d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826996"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="d58b9-103">Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="d58b9-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo TFTP</span></span>

<span data-ttu-id="d58b9-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo TFTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="d58b9-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="d58b9-105">Product Distribution</span></span>

<span data-ttu-id="d58b9-106">O Azure RTOS NetX Duo pode ser obtido a partir do nosso repositório de código fonte pública em https://github.com/azure-rtos/netxduo/ .</span><span class="sxs-lookup"><span data-stu-id="d58b9-106">Azure RTOS NetX Duo can be obtained from our public source code repository at https://github.com/azure-rtos/netxduo/.</span></span> <span data-ttu-id="d58b9-107">O pacote inclui os seguintes ficheiros:</span><span class="sxs-lookup"><span data-stu-id="d58b9-107">The package includes the following files:</span></span>


- <span data-ttu-id="d58b9-108">**nxd_tftp_client.h** Arquivo de cabeçalho para Cliente TFTP Da Dupla NetX</span><span class="sxs-lookup"><span data-stu-id="d58b9-108">**nxd_tftp_client.h** Header file for NetX Duo TFTP Client</span></span>

- <span data-ttu-id="d58b9-109">**nxd_tftp_client.c** Arquivo C Fonte para Cliente TFTP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d58b9-109">**nxd_tftp_client.c** C Source file for NetX Duo TFTP Client</span></span>

- <span data-ttu-id="d58b9-110">**nxd_tftp_server.h** Arquivo de cabeçalho para NetX Duo TFTP Server</span><span class="sxs-lookup"><span data-stu-id="d58b9-110">**nxd_tftp_server.h** Header file for NetX Duo TFTP Server</span></span>

- <span data-ttu-id="d58b9-111">**nxd_tftp_server.c** C Arquivo de origem para NetX Duo TFTP Server</span><span class="sxs-lookup"><span data-stu-id="d58b9-111">**nxd_tftp_server.c** C Source file for NetX Duo TFTP Server</span></span>

- <span data-ttu-id="d58b9-112">**filex_stub.h** Ficheiro de stub se o FileX não estiver presente</span><span class="sxs-lookup"><span data-stu-id="d58b9-112">**filex_stub.h** Stub file if FileX is not present</span></span>

- <span data-ttu-id="d58b9-113">**nxd_tftp.pdf** Descrição em PDF do NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="d58b9-113">**nxd_tftp.pdf** PDF description of NetX Duo TFTP</span></span>

- <span data-ttu-id="d58b9-114">**demo_netxduo_tftp.c** Demonstração de TFTP da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d58b9-114">**demo_netxduo_tftp.c** NetX Duo TFTP demonstration</span></span>

## <a name="tftp-installation"></a><span data-ttu-id="d58b9-115">Instalação TFTP</span><span class="sxs-lookup"><span data-stu-id="d58b9-115">TFTP Installation</span></span>

<span data-ttu-id="d58b9-116">Para utilizar o NetX Duo TFTP, toda a distribuição mencionada anteriormente pode ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="d58b9-116">To use NetX Duo TFTP, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="d58b9-117">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* e *nxd_tftp_server.c* ficheiros podem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="d58b9-117">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* and *nxd_tftp_server.c* files could be copied into this directory.</span></span>

## <a name="using-tftp"></a><span data-ttu-id="d58b9-118">Utilização de TFTP</span><span class="sxs-lookup"><span data-stu-id="d58b9-118">Using TFTP</span></span>

<span data-ttu-id="d58b9-119">Para executar uma aplicação TFTP, o código de aplicação deve incluir *nxd_tftp_client.h* e/ou nxd_tftp_server.h depois de incluir *tx_api.h, fx_api.h* e *nx_api.h,* para utilizar ThreadX, FileX e NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d58b9-119">To run a TFTP application, the application code must include *nxd_tftp_client.h* and/or nxd_tftp_server.h after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="d58b9-120">O projeto de candidatura deve também incluir *nxd_tftp_client.c* e/ou *nxd_tftp_server.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="d58b9-120">The application project must also include *nxd_tftp_client.c* and/or *nxd_tftp_server.c* in the build process.</span></span> <span data-ttu-id="d58b9-121">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="d58b9-121">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="d58b9-122">Isto é tudo o que é necessário para usar o NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-122">This is all that is required to use NetX Duo TFTP.</span></span> <span data-ttu-id="d58b9-123">Uma vez incluído *o(s) ficheiro de cabeçalho,* o código de aplicação pode então utilizar os serviços TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-123">Once *the header file(s) is* included, the application code is then able to use TFTP services.</span></span>

> [!NOTE]
> <span data-ttu-id="d58b9-124">Uma vez que a TFTP utiliza os serviços netx Duo UDP, a UDP deve ser ativada com a *chamada nx_udp_enable* antes de utilizar o TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-124">Since TFTP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using TFTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="d58b9-125">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="d58b9-125">Small Example System</span></span>

<span data-ttu-id="d58b9-126">Um exemplo de como é fácil utilizar o NetX Duo TFTP é descrito na Figura 1.1 que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="d58b9-126">An example of how easy it is to use NetX Duo TFTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="d58b9-127">Neste exemplo, o TFTP inclui *ficheiros nxd_tftp_client.h* e *nxd_tftp_server.h* são trazidos nas linhas 19 e 20.</span><span class="sxs-lookup"><span data-stu-id="d58b9-127">In this example, the TFTP include file *nxd_tftp_client.h* and *nxd_tftp_server.h* are brought in at line 19 and 20.</span></span> <span data-ttu-id="d58b9-128">Em seguida, o SftP Server é criado em "*tx_application_define*" na linha 179.</span><span class="sxs-lookup"><span data-stu-id="d58b9-128">Next, the TFTP Server is created in “*tx_application_define*” at line 179.</span></span> 

> [!NOTE]
> <span data-ttu-id="d58b9-129">O bloco de controlo do servidor TFTP "*foi* definido como uma variável global na linha 45 anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d58b9-129">The TFTP Server control block “*server*” was defined as a global variable at line 45 previously.</span></span> <span data-ttu-id="d58b9-130">Esta demonstração opta por utilizar o IPv4 para a sua comunicação TFTP na linha 14.</span><span class="sxs-lookup"><span data-stu-id="d58b9-130">This demo chooses to use IPv4 for its TFTP communication in line 14.</span></span> <span data-ttu-id="d58b9-131">Após a criação bem sucedida, o Servidor TFTP é iniciado na linha 304.</span><span class="sxs-lookup"><span data-stu-id="d58b9-131">After successful creation, the TFTP Server is started at line 304.</span></span> <span data-ttu-id="d58b9-132">Na linha 411 é criado o Cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-132">At line 411 the TFTP Client is created.</span></span> <span data-ttu-id="d58b9-133">E finalmente, o Cliente escreve o ficheiro na linha 450 e lê o ficheiro na linha 485.</span><span class="sxs-lookup"><span data-stu-id="d58b9-133">And finally, the Client writes the file at line 450 and reads the file back at line 485.</span></span>

<span data-ttu-id="d58b9-134">A tarefa de linha do servidor TFTP é interrompida e o Servidor TFTP é eliminado na linha 324.</span><span class="sxs-lookup"><span data-stu-id="d58b9-134">The TFTP server thread task is stopped and the TFTP Server is deleted on line 324.</span></span> <span data-ttu-id="d58b9-135">A aplicação deve chamar fx_media_close (linha 331) para fechar todos os ficheiros e atualizar ficheiros e dados de diretório para os meios USB.</span><span class="sxs-lookup"><span data-stu-id="d58b9-135">The application should call fx_media_close (line 331) to close all files and update file and directory data to the USB media.</span></span>

> [!NOTE]
> <span data-ttu-id="d58b9-136">Este exemplo utiliza o FileX para o tratamento do Servidor TFTP de receber e descarregar pedidos de ficheiros do Cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-136">This example uses FileX for the TFTP Server handling of receiving and downloading TFTP Client file requests.</span></span> <span data-ttu-id="d58b9-137">No entanto, se NX_TFTP_NO_FILEX estiver definido, a aplicação pode incluir file_stub.h em vez de fx_api.h.</span><span class="sxs-lookup"><span data-stu-id="d58b9-137">However, if NX_TFTP_NO_FILEX is defined, the application can include file_stub.h instead of fx_api.h.</span></span>
>
> <span data-ttu-id="d58b9-138">Note também que as aplicações existentes do cliente e servidor NetX TFTP funcionarão com o NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-138">Also note that existing NetX TFTP client and server applications will work with NetX Duo TFTP.</span></span> <span data-ttu-id="d58b9-139">No entanto, o desenvolvedor de aplicações é encorajado a apresentar as suas aplicações NetX TFTP para o NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d58b9-139">However, the application developer is encouraged to port their NetX TFTP applications to NetX Duo.</span></span> <span data-ttu-id="d58b9-140">Os serviços TFTP netx equivalentes são:</span><span class="sxs-lookup"><span data-stu-id="d58b9-140">The equivalent NetX TFTP services are:</span></span>

- <span data-ttu-id="d58b9-141">*nxd_tftp_server_start*</span><span class="sxs-lookup"><span data-stu-id="d58b9-141">*nxd_tftp_server_start*</span></span>

- <span data-ttu-id="d58b9-142">*nxd_tftp_server_stop*</span><span class="sxs-lookup"><span data-stu-id="d58b9-142">*nxd_tftp_server_stop*</span></span>

- <span data-ttu-id="d58b9-143">*nxd_tftp_client_file_read*</span><span class="sxs-lookup"><span data-stu-id="d58b9-143">*nxd_tftp_client_file_read*</span></span>

- <span data-ttu-id="d58b9-144">*nxd_tftp_client_file_write*</span><span class="sxs-lookup"><span data-stu-id="d58b9-144">*nxd_tftp_client_file_write*</span></span>

- <span data-ttu-id="d58b9-145">*nxd_tftp_client_file_open*</span><span class="sxs-lookup"><span data-stu-id="d58b9-145">*nxd_tftp_client_file_open*</span></span>

```C
/* This is a small demo of TFTP on the high-performance NetX TCP/IP stack. This demo
   relies on ThreadX and NetX Duo, to show a simple file transfer from the client
   and then back to the server. */



/* Indicate if using IPv6. */
#define USE_DUO

/* If the host application is using NetX Duo, determine which IP version to use.
   Make sure IPv6 in NetX Duo is enabled if planning to use TFTP over IPv6 */
#ifdef USE_DUO
#define     IP_TYPE     6
#endif /* USE_DUO        */

#include    "tx_api.h"
#include    "nx_api.h"
#include    "nxd_tftp_client.h"
#include    "nxd_tftp_server.h"
#ifndef     NX_TFTP_NO_FILEX
#include    "fx_api.h"
#endif


#define     DEMO_STACK_SIZE         4096

/* To use another file storage utility define this symbol:
#define NX_TFTP_NO_FILEX
*/

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;

/* Define the NetX TFTP object control blocks. */

NX_TFTP_CLIENT          client;
NX_TFTP_SERVER          server;

/* Define the application global variables */

#define                 CLIENT_ADDRESS  IP_ADDRESS(1, 2, 3, 5)
#define                 SERVER_ADDRESS  IP_ADDRESS(1, 2, 3, 4)

NXD_ADDRESS             server_ip_address;
NXD_ADDRESS             client_ip_address;

UINT                    error_counter = 0;

/* Define buffer used in the demo application. */
UCHAR                   buffer[255];
ULONG                   data_length;


/* Define the memory area for the FileX RAM disk. */
#ifndef NX_TFTP_NO_FILEX
UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];
#endif


/* Define function prototypes. */

VOID    _fx_ram_driver(FX_MEDIA *media_ptr);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
void    client_thread_entry(ULONG thread_input);
void    server_thread_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;
UCHAR   *pointer;


    /* Setup the working pointer. */
    pointer =  (UCHAR *) first_unused_memory;


    /* Create the main TFTP server thread. */
    status = tx_thread_create(&server_thread, "TFTP Server Thread", server_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              4,4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the main TFTP client thread at a slightly lower priority. */
    status = tx_thread_create(&client_thread, "TFTP Client Thread", client_thread_entry, 0,
                              pointer, DEMO_STACK_SIZE,
                              5, 5, TX_NO_TIME_SLICE, TX_DONT_START);

    pointer += DEMO_STACK_SIZE ;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&server_pool, "TFTP Server Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the TFTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&server_ip);

    /* Check for errors. */
    if (status)
        error_counter++;


    /* Create the TFTP server. */
#ifdef USE_DUO
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
    /* Specify the tftp server global address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x102;
#endif
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_ADDRESS;

#endif

    status =  nxd_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#else
    status =  nx_tftp_server_create(&server, "TFTP Server Instance", &server_ip, &ram_disk,
                                      pointer, DEMO_STACK_SIZE, &server_pool);
#endif

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for errors for the server. */
    if (status)
        error_counter++;

    /* Create a packet pool for the TFTP client. */

    /* Note: The data portion of a packet is exactly 512 bytes, but the packet payload size must
       be at least 580 bytes. The remaining bytes are used for the UDP, IP, and Ethernet
       headers and byte alignment requirements. */

    status =  nx_packet_pool_create(&client_pool, "TFTP Client Packet Pool", NX_TFTP_PACKET_SIZE, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the TFTP client. */
    status = nx_ip_create(&client_ip, "TFTP Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable UDP for client IP instance. */
    status |=  nx_udp_enable(&client_ip);
    status |= nx_icmp_enable(&client_ip);

    tx_thread_resume(&client_thread);
}

void server_thread_entry(ULONG thread_input)
{

UINT        status, running;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#ifndef  NX_TFTP_NO_FILEX

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry             */
                            ram_disk_memory,                 /* RAM disk memory pointer  */
                            ram_disk_sector_cache,           /* Media buffer pointer     */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size        */
                            "MY_RAM_DISK",                   /* Volume Name              */
                            1,                               /* Number of FATs           */
                            32,                              /* Directory Entries        */
                            0,                               /* Hidden sectors           */
                            256,                            /* Total sectors            */
                            128,                             /* Sector size              */
                            1,                               /* Sectors per cluster      */
                            1,                               /* Heads                    */
                            1);                              /* Sectors per track        */

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory, ram_disk_sector_cache,
                               sizeof(ram_disk_sector_cache));

    /* Check for errors. */
    if (status != FX_SUCCESS)
    {
        return;
    }

#endif /*  NX_TFTP_NO_FILEX */

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ICMPv6 services. */
    status |= nxd_icmp_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the server. */
    status = nxd_ipv6_enable(&server_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for DAD to validate the address. */
    tx_thread_sleep(500);
#endif

#endif /* IP_TYPE == 6 */

    /* Start the NetX TFTP server. */
#ifdef USE_DUO
    status =  nxd_tftp_server_start(&server);
#else
    status =  nx_tftp_server_start(&server);
#endif

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Run for a while */
    running = NX_TRUE;
    while(running)
        tx_thread_sleep(200);


    /* Stop and delete the TFTP server. */
#ifdef USE_DUO
    nxd_tftp_server_delete(&server);
#else
    nx_tftp_server_delete(&server);
#endif

    /* Close all open files and ensure directory information is also written out to the media.
    This will also flush the file data to USB media*/
    status = fx_media_close(&ram_disk);

    if (status)
    {
        error_counter++;
    }

    return;

}


/* Define the TFTP client thread. */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
UINT        all_done = NX_FALSE;
#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6
UINT        address_index;
UINT        iface_index;
#endif
#endif


    /* Allow time for the network driver and NetX to get initialized. */
    tx_thread_sleep(100);

#if (IP_TYPE == 6)
#ifdef FEATURE_NX_IPV6

    /* Enable ECMPv6 services for the client. */
    status = nxd_icmp_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 services for the client. */
    status = nxd_ipv6_enable(&client_ip);
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the Client IPv6 address */
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_address.v6[1] = 0xf101;
    client_ip_address.nxd_ip_address.v6[2] = 0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;

    /* This assumes the primary interface. See the NetX Duo
       User Guide for more information on address configuration. */
    iface_index = 0;
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);
    status += nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Wait for the link local and global addresses to be validated. */
    tx_thread_sleep(500);
#endif
#endif /*(IP_TYPE == 6) */


    /* The TFTP services used below include the NetX equivalent service which will work with
       NetX Duo TFTP. However, it is recommended for developers to port their applications
       to the newer services that take the NXD_ADDRESS type and support both IPv4 and IPv6
       communication.
    */

    /* Create a TFTP client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool, IP_TYPE);
#else
    status =  nx_tftp_client_create(&client, "TFTP Client", &client_ip, &client_pool);
#endif

    /* Check status. */
    if (status)
        return;

    /* Open a TFTP file for writing. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_WRITE, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_WRITE, 100);
#endif

    /* Check status. */
    if (status)
        return;

    /* Allocate a TFTP packet. */
#ifdef USE_DUO
    status =  nxd_tftp_client_packet_allocate(&client_pool, &my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_packet_allocate(&client_pool, &my_packet, 100);
#endif
    /* Check status. */
    if (status)
        error_counter++;

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write this packet to the file via TFTP. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_write(&client, my_packet, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_write(&client, my_packet, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Close this file. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Open the same file for reading. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_open(&client, "test.txt", &server_ip_address, NX_TFTP_OPEN_FOR_READ, 100, IP_TYPE);
#else
    status =  nx_tftp_client_file_open(&client, "test.txt", SERVER_ADDRESS, NX_TFTP_OPEN_FOR_READ, 100);
#endif

    /* Check status. */
    if (status)
        error_counter++;
    do
    {

    /* Read the file back. */
#ifdef USE_DUO
        status =  nxd_tftp_client_file_read(&client, &my_packet, 100, IP_TYPE);
#else
        status =  nx_tftp_client_file_read(&client, &my_packet, 100);
#endif
        /* Check for retranmission/dropped packet error. Benign. Try again... */
        if (status == NX_TFTP_INVALID_BLOCK_NUMBER)
        {

            continue;
        }
        else if (status == NX_TFTP_END_OF_FILE)
        {

            /* All done. */
            all_done = NX_TRUE;
        }
        else if (status != NX_SUCCESS)
        {

            /* Internal error, invalid packet or error on read. */
            break;
        }


        /* Do something with the packet data and release when done. */
        nx_packet_data_retrieve(my_packet, buffer, &data_length);
        buffer[data_length] = 0;
        printf("Receive data: %s\n", buffer);

        printf("release packet in demo.\n");

        nx_packet_release(my_packet);

    } while (all_done == NX_FALSE);

    /* Close the file again. */
#ifdef USE_DUO
    status =  nxd_tftp_client_file_close(&client, IP_TYPE);
#else
    status =  nx_tftp_client_file_close(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    /* Delete the client. */
#ifdef USE_DUO
    status =  nxd_tftp_client_delete(&client);
#else
    status =  nx_tftp_client_delete(&client);
#endif

    /* Check status. */
    if (status)
        error_counter++;

    return;
}
```

<span data-ttu-id="d58b9-146">Figura 1.1 Exemplo de utilização de TFTP com NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d58b9-146">Figure 1.1 Example of TFTP use with NetX Duo</span></span>

## <a name="configuration-options"></a><span data-ttu-id="d58b9-147">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="d58b9-147">Configuration Options</span></span>

<span data-ttu-id="d58b9-148">Existem várias opções de configuração para a construção do NetX Duo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-148">There are several configuration options for building NetX Duo TFTP.</span></span> <span data-ttu-id="d58b9-149">A lista que se segue descreve cada uma em detalhe.</span><span class="sxs-lookup"><span data-stu-id="d58b9-149">The following list describes each in detail.</span></span> <span data-ttu-id="d58b9-150">Salvo especificação em contrário, estas opções *encontram-se em nxd_tftp_client.h* e *nxd_tftp_server.h*.</span><span class="sxs-lookup"><span data-stu-id="d58b9-150">Unless otherwise specified, these options are found in *nxd_tftp_client.h* and *nxd_tftp_server.h*.</span></span>


- <span data-ttu-id="d58b9-151">**NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-151">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic TFTP error checking.</span></span> <span data-ttu-id="d58b9-152">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="d58b9-152">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="d58b9-153">**NX_TFTP_SERVER_PRIORITY** A prioridade da linha do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-153">**NX_TFTP_SERVER_PRIORITY** The priority of the TFTP server thread.</span></span> <span data-ttu-id="d58b9-154">Por predefinição, este valor é definido como 16 para especificar a prioridade 16.</span><span class="sxs-lookup"><span data-stu-id="d58b9-154">By default, this value is defined as 16 to specify priority 16.</span></span>

- <span data-ttu-id="d58b9-155">**NX_TFTP_SERVER_TIME_SLICE** A fatia de tempo para o Servidor TFTP funcionar antes de ceder a outros fios da mesma prioridade.</span><span class="sxs-lookup"><span data-stu-id="d58b9-155">**NX_TFTP_SERVER_TIME_SLICE** The time slice for the TFTP Server to run before yielding to other threads of the same priority.</span></span> <span data-ttu-id="d58b9-156">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="d58b9-156">The default value is 2.</span></span>

- <span data-ttu-id="d58b9-157">**NX_TFTP_MAX_CLIENTS** O número máximo de clientes que o servidor pode manusear de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="d58b9-157">**NX_TFTP_MAX_CLIENTS** The maximum number of clients the server can handle at one time.</span></span> <span data-ttu-id="d58b9-158">Por padrão, este valor é de 10 para suportar 10 clientes ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d58b9-158">By default, this value is 10 to support 10 clients at once.</span></span>

- <span data-ttu-id="d58b9-159">**NX_TFTP_ERROR_STRING_MAX** O número máximo de caracteres na cadeia de erro.</span><span class="sxs-lookup"><span data-stu-id="d58b9-159">**NX_TFTP_ERROR_STRING_MAX** The maximum number of characters in the error string.</span></span> <span data-ttu-id="d58b9-160">Por padrão, este valor é de 64.</span><span class="sxs-lookup"><span data-stu-id="d58b9-160">By default, this value is 64.</span></span>

- <span data-ttu-id="d58b9-161">**NX_TFTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX.</span><span class="sxs-lookup"><span data-stu-id="d58b9-161">**NX_TFTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="d58b9-162">O Cliente TFTP funcionará sem qualquer alteração se esta opção for definida.</span><span class="sxs-lookup"><span data-stu-id="d58b9-162">The TFTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="d58b9-163">O Servidor TFTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="d58b9-163">The TFTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>

- <span data-ttu-id="d58b9-164">**NX_TFTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos da TFTP UDP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-164">**NX_TFTP_TYPE_OF_SERVICE** Type of service required for the TFTP UDP requests.</span></span> <span data-ttu-id="d58b9-165">Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="d58b9-166">**NX_TFTP_FRAGMENT_OPTION** Permitem os pedidos de UDP da TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-166">**NX_TFTP_FRAGMENT_OPTION** Fragment enable for TFTP UDP requests.</span></span> <span data-ttu-id="d58b9-167">Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação da UDP TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-167">By default, this value is NX_DONT_FRAGMENT to disable TFTP UDP fragmenting.</span></span>

- <span data-ttu-id="d58b9-168">**NX_TFTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="d58b9-168">**NX_TFTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="d58b9-169">O valor predefinido é definido para 0x80.</span><span class="sxs-lookup"><span data-stu-id="d58b9-169">The default value is set to 0x80.</span></span>

- <span data-ttu-id="d58b9-170">**NX_TFTP_SOURCE_PORT** Esta opção permite que uma aplicação do Cliente TFTP especifique a porta de tomada UDP do cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d58b9-170">**NX_TFTP_SOURCE_PORT** This option allows a TFTP Client application to specify the TFTP Client UDP socket port.</span></span> <span data-ttu-id="d58b9-171">Está em incumprimento NX_ANY_PORT.</span><span class="sxs-lookup"><span data-stu-id="d58b9-171">It is defaulted to NX_ANY_PORT.</span></span>

- <span data-ttu-id="d58b9-172">***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Permite que o temporizador do servidor TFTP verifique cada sessão de clientes TFTP com atividades recentes (seja um ACK ou um pacote de dados).</span><span class="sxs-lookup"><span data-stu-id="d58b9-172">***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Enables the TFTP server’s timer to check each TFTP client session with for recent activity (either an ACK or data packet).</span></span> <span data-ttu-id="d58b9-173">Quando o tempo limite de sessão expira após o número máximo de vezes, presume-se que a ligação foi perdida.</span><span class="sxs-lookup"><span data-stu-id="d58b9-173">When the session timeout expires after the maximum number of times, it is assumed the connection was lost.</span></span> <span data-ttu-id="d58b9-174">O Servidor limpa o pedido do Cliente, fecha quaisquer ficheiros abertos e disponibiliza o pedido de ligação para o próximo Cliente.</span><span class="sxs-lookup"><span data-stu-id="d58b9-174">The Server clears the Client request, closes any open files and makes the connection request available for the next Client.</span></span> <span data-ttu-id="d58b9-175">A definição predefinida é desativada.</span><span class="sxs-lookup"><span data-stu-id="d58b9-175">The default setting is disabled.</span></span>

- <span data-ttu-id="d58b9-176">**NX_TFTP_SERVER_TIMEOUT_PERIOD** Especifica o intervalo quando a função de entrada do temporizador do servidor TFTP verifica as ligações do Cliente para receber quaisquer pacotes.</span><span class="sxs-lookup"><span data-stu-id="d58b9-176">**NX_TFTP_SERVER_TIMEOUT_PERIOD** Specifies the interval when the TFTP server timer entry function checks Client connections for receiving any packets.</span></span> <span data-ttu-id="d58b9-177">O valor predefinido é de 20 (tiques temporais).</span><span class="sxs-lookup"><span data-stu-id="d58b9-177">The default value is 20 (timer ticks).</span></span>

- <span data-ttu-id="d58b9-178">**NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** Este é o tempo limite para receber um ACK válido ou um pacote de dados do Cliente.</span><span class="sxs-lookup"><span data-stu-id="d58b9-178">**NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** This is the timeout for receiving a valid ACK or data packet from the Client.</span></span> <span data-ttu-id="d58b9-179">O valor predefinido é de 200 (carraças de temporizador)*.*</span><span class="sxs-lookup"><span data-stu-id="d58b9-179">The default value is 200 (timer ticks)*.*</span></span>

- <span data-ttu-id="d58b9-180">**NX_TFTP_SERVER_MAX_RETRIES** Especifica o número máximo de vezes que a sessão de Cliente retransmit o tempo limite é renovado.</span><span class="sxs-lookup"><span data-stu-id="d58b9-180">**NX_TFTP_SERVER_MAX_RETRIES** Specifies the maximum number of times the Client session retransmit timeout is renewed.</span></span> <span data-ttu-id="d58b9-181">Posteriormente, a sessão é encerrada pelo Servidor.</span><span class="sxs-lookup"><span data-stu-id="d58b9-181">Thereafter, the session is closed by the Server.</span></span>

- <span data-ttu-id="d58b9-182">**NX_TFTP_MAX_CLIENT_RETRANSMITS** Especifica o número máximo de vezes que o Servidor recebe um ACK duplicado ou um pacote de dados do Cliente (que cai) sem enviar uma mensagem de erro ao Cliente e fechar a sessão.</span><span class="sxs-lookup"><span data-stu-id="d58b9-182">**NX_TFTP_MAX_CLIENT_RETRANSMITS** Specifies the maximum number of times the Server receives a duplicate ACK or data packet from the Client (which it drops) without sending an error message to the Client and closing the session.</span></span> <span data-ttu-id="d58b9-183">Não tem efeito se NX_TFTP_SERVER_RETRANSMIT_ENABLE for definido.</span><span class="sxs-lookup"><span data-stu-id="d58b9-183">Has no effect if NX_TFTP_SERVER_RETRANSMIT_ENABLE is defined.</span></span>
