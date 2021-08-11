---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo TFTP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo TFTP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ae4e82a0f878af06bd178035cb9429cfe2a14d0bc4bbf848db7d321463586a20
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801262"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-tftp"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo TFTP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo TFTP.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX Duo pode ser obtido a partir do nosso repositório de código fonte pública em https://github.com/azure-rtos/netxduo/ . O pacote inclui os seguintes ficheiros:


- **nxd_tftp_client.h** Arquivo de cabeçalho para Cliente TFTP Da Dupla NetX

- **nxd_tftp_client.c** Arquivo C Fonte para Cliente TFTP NetX Duo

- **nxd_tftp_server.h** Arquivo de cabeçalho para NetX Duo TFTP Server

- **nxd_tftp_server.c** C Arquivo de origem para NetX Duo TFTP Server

- **filex_stub.h** Ficheiro de stub se o FileX não estiver presente

- **nxd_tftp.pdf** Descrição em PDF do NetX Duo TFTP

- **demo_netxduo_tftp.c** Demonstração de TFTP da NetX Duo

## <a name="tftp-installation"></a>Instalação TFTP

Para utilizar o NetX Duo TFTP, toda a distribuição mencionada anteriormente pode ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então o *nxd_tftp_client.h*, *nxd_tftp_client.c*, *nxd_tftp_server.h* e *nxd_tftp_server.c* ficheiros podem ser copiados para este diretório.

## <a name="using-tftp"></a>Utilização de TFTP

Para executar uma aplicação TFTP, o código de aplicação deve incluir *nxd_tftp_client.h* e/ou nxd_tftp_server.h depois de incluir *tx_api.h, fx_api.h* e *nx_api.h,* para utilizar ThreadX, FileX e NetX Duo, respectivamente. O projeto de candidatura deve também incluir *nxd_tftp_client.c* e/ou *nxd_tftp_server.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX Duo TFTP. Uma vez incluído *o(s) ficheiro de cabeçalho,* o código de aplicação pode então utilizar os serviços TFTP.

> [!NOTE]
> Uma vez que a TFTP utiliza os serviços netx Duo UDP, a UDP deve ser ativada com a *chamada nx_udp_enable* antes de utilizar o TFTP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o NetX Duo TFTP é descrito na Figura 1.1 que aparece abaixo. Neste exemplo, o TFTP inclui *ficheiros nxd_tftp_client.h* e *nxd_tftp_server.h* são trazidos nas linhas 19 e 20. Em seguida, o SftP Server é criado em "*tx_application_define*" na linha 179. 

> [!NOTE]
> O bloco de controlo do servidor TFTP "*foi* definido como uma variável global na linha 45 anteriormente. Esta demonstração opta por utilizar o IPv4 para a sua comunicação TFTP na linha 14. Após a criação bem sucedida, o Servidor TFTP é iniciado na linha 304. Na linha 411 é criado o Cliente TFTP. E finalmente, o Cliente escreve o ficheiro na linha 450 e lê o ficheiro na linha 485.

A tarefa de linha do servidor TFTP é interrompida e o Servidor TFTP é eliminado na linha 324. A aplicação deve chamar fx_media_close (linha 331) para fechar todos os ficheiros e atualizar ficheiros e dados de diretório para os meios USB.

> [!NOTE]
> Este exemplo utiliza o FileX para o tratamento do Servidor TFTP de receber e descarregar pedidos de ficheiros do Cliente TFTP. No entanto, se NX_TFTP_NO_FILEX estiver definido, a aplicação pode incluir file_stub.h em vez de fx_api.h.
>
> Note também que as aplicações existentes do cliente e servidor NetX TFTP funcionarão com o NetX Duo TFTP. No entanto, o desenvolvedor de aplicações é encorajado a apresentar as suas aplicações NetX TFTP para o NetX Duo. Os serviços TFTP netx equivalentes são:

- *nxd_tftp_server_start*

- *nxd_tftp_server_stop*

- *nxd_tftp_client_file_read*

- *nxd_tftp_client_file_write*

- *nxd_tftp_client_file_open*

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

Figura 1.1 Exemplo de utilização de TFTP com NetX Duo

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX Duo TFTP. A lista que se segue descreve cada uma em detalhe. Salvo especificação em contrário, estas opções *encontram-se em nxd_tftp_client.h* e *nxd_tftp_server.h*.


- **NX_DISABLE_ERROR_CHECKING** Definida, esta opção remove a verificação básica de erros TFTP. É normalmente usado após a depurada aplicação.

- **NX_TFTP_SERVER_PRIORITY** A prioridade da linha do servidor TFTP. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.

- **NX_TFTP_SERVER_TIME_SLICE** A fatia de tempo para o Servidor TFTP funcionar antes de ceder a outros fios da mesma prioridade. O valor predefinido é 2.

- **NX_TFTP_MAX_CLIENTS** O número máximo de clientes que o servidor pode manusear de uma só vez. Por padrão, este valor é de 10 para suportar 10 clientes ao mesmo tempo.

- **NX_TFTP_ERROR_STRING_MAX** O número máximo de caracteres na cadeia de erro. Por padrão, este valor é de 64.

- **NX_TFTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX. O Cliente TFTP funcionará sem qualquer alteração se esta opção for definida. O Servidor TFTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.

- **NX_TFTP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos da TFTP UDP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.

- **NX_TFTP_FRAGMENT_OPTION** Permitem os pedidos de UDP da TFTP. Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação da UDP TFTP.

- **NX_TFTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.

- **NX_TFTP_SOURCE_PORT** Esta opção permite que uma aplicação do Cliente TFTP especifique a porta de tomada UDP do cliente TFTP. Está em incumprimento NX_ANY_PORT.

- ***NX_TFTP_SERVER_RETRANSMIT_ENABLE*** Permite que o temporizador do servidor TFTP verifique cada sessão de clientes TFTP com atividades recentes (seja um ACK ou um pacote de dados). Quando o tempo limite de sessão expira após o número máximo de vezes, presume-se que a ligação foi perdida. O Servidor limpa o pedido do Cliente, fecha quaisquer ficheiros abertos e disponibiliza o pedido de ligação para o próximo Cliente. A definição predefinida é desativada.

- **NX_TFTP_SERVER_TIMEOUT_PERIOD** Especifica o intervalo quando a função de entrada do temporizador do servidor TFTP verifica as ligações do Cliente para receber quaisquer pacotes. O valor predefinido é de 20 (tiques temporais).

- **NX_TFTP_SERVER_RETRANSMIT_TIMEOUT** Este é o tempo limite para receber um ACK válido ou um pacote de dados do Cliente. O valor predefinido é de 200 (carraças de temporizador)*.*

- **NX_TFTP_SERVER_MAX_RETRIES** Especifica o número máximo de vezes que a sessão de Cliente retransmit o tempo limite é renovado. Posteriormente, a sessão é encerrada pelo Servidor.

- **NX_TFTP_MAX_CLIENT_RETRANSMITS** Especifica o número máximo de vezes que o Servidor recebe um ACK duplicado ou um pacote de dados do Cliente (que cai) sem enviar uma mensagem de erro ao Cliente e fechar a sessão. Não tem efeito se NX_TFTP_SERVER_RETRANSMIT_ENABLE for definido.
