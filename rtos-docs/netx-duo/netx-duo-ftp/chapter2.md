---
title: Capítulo 2 - Instalação e utilização de FTP
description: Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização dos serviços FTP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bef7dcce9354e6653dd92c5a47a29d120268faeb4a30b4d146c9e10d2d69084e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790229"
---
# <a name="chapter-2---installation-and-use-of-ftp"></a>Capítulo 2 - Instalação e utilização de FTP

Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização dos serviços FTP NetX Duo.

## <a name="product-distribution"></a>Distribuição de Produtos

NetX Duo FTP está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nxd_ftp_client.h** Arquivo de cabeçalho para Cliente FTP da NetX Duo
- **nxd_ftp_client.c** Arquivo C Fonte para Cliente FTP Da Dupla NetX
- **nxd_ftp_server.h** Arquivo de cabeçalho para NetX Duo FTP Server
- **nxd_ftp_server.c** C Arquivo de origem para NetX Duo FTP Server
- **filex_stub.h** Ficheiro de stub se o FileX não estiver presente
- **nxd_ftp.pdf** Descrição em PDF de FTP para NetX Duo
- **demo_netxduo_ftp.c** Sistema de demonstração FTP

## <a name="netx-duo-ftp-installation"></a>Instalação FTP netx duo

Para utilizar a API FTP Da Dupla NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*", então o *nxd_ftp_client.h* e *nxd_ftp_client.c* devem ser copiados para este diretório para aplicações ftp cliente, e *nxd_ftp_server.h* e *nxd_ftp_server.c* ficheiros devem ser copiados para este diretório para aplicações FTP Server.

## <a name="using-netx-duo-ftp"></a>Usando o NetX Duo FTP

A utilização da API FTP da NetX Duo é fácil. Basicamente, o código de aplicação deve incluir *nxd_ftp_client.h* para aplicações ftp cliente ou *nxd_ftp_server* para aplicações FTP Server, depois de incluir *tx_api.h, fx_api.h* e *nx_api.h,* para utilizar ThreadX, FileX e NetX Duo, respectivamente. O projeto de construção deve incluir o código fonte FTP e o ficheiro de aplicação do anfitrião, e, claro, os ficheiros da biblioteca ThreadX e NetX. Isto é tudo o que é necessário para usar o NetX Duo FTP.

Note que, uma vez que a FTP utiliza os serviços NetX Duo TCP, a TCP deve ser ativada com a *chamada nx_tcp_enable* antes da utilização do FTP.

Note que a biblioteca NetX Duo pode ser ativada para iPv6 e ainda suportar redes IPv4. No entanto, a NetX Duo não pode suportar o IPv6 a menos que esteja ativado. Para desativar o processamento do IPv6 no NetX Duo, o **NX_DISABLE_IPV6** deve ser definido no ficheiro *nx_user.h,* e esse ficheiro deve ser incluído na construção da biblioteca NetX Duo definindo **NX_INCLUDE_USER_DEFINE_FILE** no ficheiro *nx_port.h.* Por predefinição, **NX_DISABLE_IPV6** não está definido (o IPv6 está ativado). Isto é diferente do serviço *nxd_ipv6_enable* que estabelece os protocolos e serviços IPv6 na tarefa IP, e exige **que NX_DISABLE_IPV6** não sejam definidos.

## <a name="small-example-system-of-netx-duo-ftp"></a>Sistema de exemplo pequeno do NetX Duo FTP

Um exemplo de como é fácil utilizar o NetX Duo FTP é descrito na Figura 1.1 que aparece abaixo. Neste exemplo, são criados tanto um Servidor FTP como um Cliente FTP. Portanto, ambos os ftp incluem ficheiros *nxd_ftp_client.h e nxd_ftp_server.h são trazidos* nas linhas 10 e 11. Em seguida, o FTP Server é criado em "*tx_application_define*" na linha 99. Note que os blocos de controlo FTP Server e Cliente são definidos como variáveis globais na linha 26 anteriormente.

Esta demonstração mostra como usar as funções duo disponíveis no NetX Duo FTP, bem como os serviços FTP limitados IPv4. Para utilizar as funções IPv6, a demonstração define USE_IPV6 na linha 16

Na linha 162 o FTP Server é criado com ***nxd_ftp_server_create** _ se a aplicação do anfitrião definir USE_IPV6 que suporta o IPv4 e o IPv6. Caso contrário, o FTP Server é criado com _ *_nx_ftp_server_create_** na linha 166 com o serviço IPv4 limitado. Note que a função 'duo' utiliza diferentes argumentos de função de login e logout do que o serviço IPv4, ambos definidos na parte inferior do ficheiro nas linhas 534-568.

O servidor FTP deve então estabelecer o seu endereço IPv6 (global e link local) com o NetX Duo, a partir da linha 466 na função de entrada de fio do servidor FTP. O servidor FTP é então iniciado na linha 518 e está pronto para pedidos de clientes FTP.

O Cliente FTP é criado na linha 316 e passa pelo mesmo processo que o FTP Server para obter a tarefa IP do cliente FTP ativado, e os seus endereços IPv6 validados a partir das linhas 263-313.

Em seguida, o Cliente liga-se ao Servidor FTP utilizando ***nxd_ftp_client_connect** _ na linha 334 se tiver definido USE_IPV6, ou linha 340 se estiver a utilizar o serviço limitado IPv4 _*_nx_ftp_client_connect_**. Ao longo da função de thread ftp Client, escreve um ficheiro para o servidor FTP e lê-o antes de desligar.

```C
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack.  This demo
   relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
   and then back to the server.  */



#include    "tx_api.h"
#include    "fx_api.h"
#include    "nx_api.h"
#include    "nxd_ftp_client.h"
#include    "nxd_ftp_server.h"

#define     DEMO_STACK_SIZE         4096

#ifdef FEATURE_NX_IPV6
#define USE_IPV6
#endif /* FEATURE_NX_IPV6 */


/* Define the ThreadX, NetX, and FileX object control blocks...  */

TX_THREAD               server_thread;
TX_THREAD               client_thread;
NX_PACKET_POOL          server_pool;
NX_IP                   server_ip;
NX_PACKET_POOL          client_pool;
NX_IP                   client_ip;
FX_MEDIA                ram_disk;


/* Define the NetX FTP object control blocks.  */

NX_FTP_CLIENT           ftp_client;
NX_FTP_SERVER           ftp_server;


/* Define the counters used in the demo application...  */

ULONG                   error_counter = 0;


/* Define the memory area for the FileX RAM disk.  */

UCHAR                   ram_disk_memory[32000];
UCHAR                   ram_disk_sector_cache[512];


#define FTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)

extern UINT  _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                        VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                        CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                        UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                        UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions.  */
VOID    _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);


void    client_thread_entry(ULONG thread_input);
void    thread_server_entry(ULONG thread_input);


#ifdef USE_IPV6
/* Define NetX Duo IP address for the NetX Duo FTP Server and Client. */
NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;
endif


/* Define server login/logout functions.  These are stubs for functions that would
   validate a client login request.   */

#ifdef USE_IPV6
UINT    server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info);
#else
UINT    server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
UINT    server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
    ULONG client_ip_address, UINT client_port,
    CHAR *name, CHAR *password, CHAR *extra_info);
#endif


/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return(0);
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

    UINT    status;
    UCHAR   *pointer;


    /* Setup the working pointer.  */
    pointer =  (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry, 0,
                     pointer, DEMO_STACK_SIZE,
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize NetX.  */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server.  */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool", 256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server.  */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance", FTP_SERVER_ADDRESS, 0xFFFFFF00UL,
                                        &server_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance.  */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP.  */
    nx_tcp_enable(&server_ip);

#ifdef USE_IPV6

    /* Next set the NetX Duo FTP Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Create the FTP server.  */
    status =  nxd_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login6, server_logout6);
#else
    /* Create the FTP server.  */
    status =  nx_ftp_server_create(&ftp_server, "FTP Server Instance", &server_ip,
                                    &ram_disk, pointer, DEMO_STACK_SIZE, &server_pool,
                                    server_login, server_logout);
#endif
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread.  */
    status = tx_thread_create(&client_thread, "FTP Client thread ", client_thread_entry, 0,
            pointer, DEMO_STACK_SIZE,
            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE ;

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client.  */
    status =  nx_packet_pool_create(&client_pool, "NetX Client Packet Pool", 256, pointer, 8192);
    pointer =  pointer + 8192;

    /* Create an IP instance for the FTP client.  */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS, 0xFFFFFF00UL,
                                                &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP.  */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance.  */
    nx_tcp_enable(&client_ip);

    return;

}

/* Define the FTP client thread.  */

void    client_thread_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;

#ifdef USE_IPV6
UINT        iface_index, address_index;
#endif


    /* Format the RAM disk - the memory for the RAM disk was defined above.  */
    status = _fx_media_format(&ram_disk,
                            _fx_ram_driver,                  /* Driver entry                */
                            ram_disk_memory,                 /* RAM disk memory pointer     */
                            ram_disk_sector_cache,           /* Media buffer pointer        */
                            sizeof(ram_disk_sector_cache),   /* Media buffer size           */
                            "MY_RAM_DISK",                   /* Volume Name                 */
                            1,                               /* Number of FATs              */
                            32,                              /* Directory Entries           */
                            0,                               /* Hidden sectors              */
                            256,                             /* Total sectors               */
                            128,                             /* Sector size                 */
                            1,                               /* Sectors per cluster         */
                            1,                               /* Heads                       */
                            1);                              /* Sectors per track           */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk.  */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
        ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Let the IP threads and driver initialize the system.    */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    status = nxd_icmp_enable(&client_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Set the Client link local and global addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Let NetX Duo validate the addresses. */
    tx_thread_sleep(400);

#endif  /* USE_IPV6 */

    /* Create an FTP client.  */
    status =  nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Created the FTP Client\n");

#ifdef USE_IPV6

    do
    {

        /* Now connect with the NetX Duo FTP (IPv6) server. */
        status =  nxd_ftp_client_connect(&ftp_client, &server_ip_address, "name", "password", 100);
    } while (status != NX_SUCCESS);

#else

    /* Now connect with the NetX FTP (IPv4) server. */
    status =  nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS, "name", "password", 100);

#endif  /* USE_IPV6 */

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet.  */
    status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    /* Write ABCs into the packet payload!  */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ  ", 28);

    /* Adjust the write pointer.  */
    my_packet -> nx_packet_length =  28;
    my_packet -> nx_packet_append_ptr =  my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt.  */
    status =  nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");


    /* Close the file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");


    /* Now open the same file for reading.  */
    status =  nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file.  */
    status =  nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
            printf("Reread the FTP client test.txt file\n");
            nx_packet_release(my_packet);
    }

    /* Close this file.  */
    status =  nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server.  */
    status =  nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;


    /* Delete the FTP client.  */
    status =  nx_ftp_client_delete(&ftp_client);

    /* Check status.  */
    if (status != NX_SUCCESS)
        error_counter++;
}


/* Define the helper FTP server thread.  */
void    thread_server_entry(ULONG thread_input)
{

    UINT            status;
#ifdef  USE_IPV6
    UINT            iface_index, address_index;
#endif

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

#ifdef USE_IPV6

    /* Here's where we make the FTP server IPv6 enabled. */
    status = nxd_ipv6_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

    status = nxd_icmp_enable(&server_ip);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
     }

     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&server_ip, iface_index, &server_ip_address, 64, &address_index);

    /* Check for global address set error.  */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);

#endif /* USE_IPV6 */

    /* OK to start the FTP Server.   */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute.    */
    tx_thread_relinquish();

    return;
}


#ifdef USE_IPV6
UINT  server_login6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    NXD_ADDRESS *client_ipduo_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged in6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout6(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, NXD_ADDRESS *client_ipduo_address,
                     UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out6!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#else
UINT  server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success.  */
    return(NX_SUCCESS);
}

UINT  server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr, ULONG client_ip_address,
                    UINT client_port, CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success.  */
    return(NX_SUCCESS);
}
#endif  /* USE_IPV6 */
```

**Figura 1.1 Exemplo do Duo FTP da NetX**

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção de NetX FTP e NetX Duo FTP. Os valores predefinidos são listados, mas cada definição pode ser definido pelo

aplicação antes da inclusão do ficheiro de cabeçalho NetX Duo FTP especificado. Se não for especificado nenhum ficheiro de cabeçalho, a opção está disponível tanto em *nxd_ftp_client.h como nxd_ftp_server.h*. A seguinte lista descreve cada uma em detalhe:

- **NX_FTP_SERVER_PRIORITY** A prioridade da linha FTP Server. Por predefinição, este valor é definido como 16 para especificar a prioridade 16.
- **NX_FTP_MAX_CLIENTS** O número máximo de Clientes que o Servidor pode manusear de uma só vez. Por padrão, este valor é 4 para suportar 4 Clientes ao mesmo tempo.
- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD** O tamanho mínimo da carga útil do pacote do Servidor em bytes, incluindo porta-cabeçalhos de TCP, IP e moldura de rede mais dados HTTP. O valor predefinido é de 256 (comprimento máximo de nome de ficheiro no FileX) + 12 bytes para informações de ficheiros e NX_PHYSICAL_TRAILER.
- **NX_FTP_SERVER_TIMEOUT** Especifica o número de carraças ThreadX que os serviços internos vão suspender. O valor predefinido é definido para 1 segundo (1 * NX_IP_PERIODIC_RATE).
- **NX_FTP_ACTIVITY_TIMEOUT** Especifica o número de segundos que uma ligação do Cliente é mantida se não houver atividade. O valor predefinido é definido para 240.
- **NX_FTP_TIMEOUT_PERIOD** Especifica os intervalos em segundos quando o Servidor verifica a atividade do Cliente. O valor predefinido é definido para 60.
- **NX_FTP_SERVER_RETRY_SECONDS** Especifica o intervalo inicial em segundos antes de retransmitir a resposta do servidor. O valor predefinido é 2.
- **NX_FTP_SERVER_TRANSMIT_QUEUE_DEPTH** Especifica a profundidade máxima dos pacotes de transmissão em fila na tomada do Servidor. O valor predefinido é de 20.
- **NX_FTP_SERVER_RETRY_MAX** Especifica as retrícas máximas por pacote. O valor predefinido é 10.
- **NX_FTP_SERVER_RETRY_SHIFT** Especifica o número de bits para deslocar na definição do tempo limite de re-padrão. O valor predefinido é de 2, por exemplo, cada intervalo de retígio é o dobro do tempo de reação anterior.
- **NX_FTP_NO_FILEX** Definida, esta opção fornece um canhoto para dependências de FileX. O Cliente FTP funcionará sem qualquer alteração se esta opção for definida. O Servidor FTP terá de ser modificado ou o utilizador terá de criar um punhado de serviços FileX para funcionar corretamente.
- **NX_FTP_CONTROL_TOS** Tipo de serviço necessário para os pedidos de controlo FTP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
- **NX_FTP_DATA_TOS** Tipo de serviço necessário para os pedidos de dados FTP. Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.
- **NX_FTP_FRAGMENT_OPTION** Ativar fragmentos para pedidos FTP. Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação ftp TCP.
- **NX_FTP_CONTROL_WINDOW_SIZE** Tamanho da janela da tomada de controlo TCP. Por padrão, este valor é de 400 bytes.
- **NX_FTP_DATA_WINDOW_SIZE** Tamanho da janela da tomada de dados TCP. Por padrão, este valor é 2048 bytes.
- **NX_FTP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado. O valor predefinido é definido para 0x80.
- **NX_FTP_USERNAME_SIZE** Especifica o número de bytes permitidos num nome de utilizador fornecido *pelo* Cliente. O valor predefinido é definido para 20 *.*
- **NX_FTP_PASSWORD_SIZE** Especifica o número de bytes permitidos numa *senha* fornecida pelo cliente. O valor predefinido é definido para 20.
