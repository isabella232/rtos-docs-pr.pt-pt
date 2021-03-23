---
title: Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX POP3
description: O Cliente NetX POP3 inclui um ficheiro de origem, um ficheiro de cabeçalho e um ficheiro de demonstração. Existem dois ficheiros adicionais para os serviços de digestão MD5.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826665"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX POP3

O Cliente NetX POP3 inclui um ficheiro de origem, um ficheiro de cabeçalho e um ficheiro de demonstração. Existem dois ficheiros adicionais para os serviços de digestão MD5. Existe também um ficheiro PDF do Guia do Utilizador (este documento).

- **nx_pop3_client.c**: Ficheiro C Fonte para a API do Cliente NetX POP3
- **nx_pop3_client.h**: Ficheiro de cabeçalho C para a API do cliente NetX POP3
- **demo_netxduo_pop3_client.c**: Ficheiro de demonstração para criação e iniciação de sessão de clientes POP3
- **nx_md5.c**: Ficheiro C Fonte que define os serviços de digestão MD5
- **nx_md5.h**: Ficheiro de cabeçalho C que define os serviços de digestão MD5
- **nx_pop3_client.pdf**: Guia de Utilizador do Cliente NetX POP3

Para utilizar o Cliente NetX POP3, toda a distribuição mencionada anteriormente pode ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\mcf5272\green*" então o *nx_md5.h,* *nx_md5.c,* *nx_pop3_client.h e nx_pop3_client.c* ficheiros devem ser copiados para este diretório.

## <a name="using-netx-pop3-client"></a>Usando o cliente NetX POP3

Para utilizar o serviço De Cliente NetX POP3, a aplicação deve adicionar *nx_pop3_client.c* ao seu projeto de construção. O código de aplicação deve incluir *nx_md5.h, nx_pop3.h e nx_pop3_client.h* após *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX.

Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e o código do objeto deve ser ligado juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o Cliente NetX POP3.

## <a name="small-example-of-the-netx-pop3-client"></a>Pequeno exemplo do Cliente NetX POP3

Um exemplo de como utilizar os serviços de clientes NetX POP3 é descrito na Figura 1 que aparece abaixo. Esta demonstração configura as duas chamadas para notificação de transferência de correio e conclusão da sessão nas linhas 37 e 38. A piscina de pacotes do Cliente POP3 é criada na linha 76. A tarefa de linha IP é criada na linha 88. Note que esta piscina de pacotes também é usada para a piscina de pacotes do Cliente POP3. O TCP está ativado na tarefa IP na linha 107.

O Cliente POP3 é criado na linha 133 dentro da função de entrada de fio de aplicação, *demo_thread_entry*. Isto porque o serviço *nx_pop3_client_create* também tenta fazer uma ligação TCP com o servidor POP3. Se for bem sucedido, a aplicação consulta o servidor POP3 pelo número de itens na sua caixa de correio na linha 149 utilizando o serviço *nx_pop3_client_mail_items_get.*

Se houver um ou mais itens, a aplicação itera através do ciclo de cada e-mail para descarregar a mensagem de correio. O pedido DO REA é feito na linha 149 na *chamada nx_pop3_client_mail_item_get.* Se for bem sucedido, a aplicação descarrega pacotes usando o serviço *nx_pop3_client_mail_item_message_get* na linha 177 até que detete o último pacote da mensagem foi recebido na linha 196. Por último, a aplicação elimina o item de correio, assumindo que ocorreu um download bem sucedido na linha 199 na *nx_pop3_client_mail_item_delete* chamada. O RFC 1939 recomenda que os Clientes POP3 instruam o Servidor a apagar itens de correio descarregados para evitar que o correio se acumule na gota de correio do Cliente. O Servidor pode fazê-lo automaticamente de qualquer forma.

Uma vez descarregados todos os itens de correio, ou se uma chamada de serviço do Cliente POP3 falhar, a aplicação sai do loop e elimina o Cliente POP3 na linha 217 utilizando o serviço *nx_pop3_client_delete.*

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);

    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                            CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                            _nx_ram_network_driver, free_memory_pointer,
                            2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}

/* Define the application thread entry function. */

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
                        NX_TRUE,
                        &client_ip, &client_packet_pool, SERVER_ADDRESS,
                        SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
        {
            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {
                break;
            }

            if (bytes_retrieved != 0)
            {

            printf("Received %d bytes of data for item %d: %s\n",
                    packet_ptr -> nx_packet_length,
                    mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);
    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

Figura 1: Exemplo de uma aplicação do Cliente NetX POP3

## <a name="pop3-client-configuration-options"></a>Opções de configuração do cliente POP3

Existem várias opções de configuração com o Cliente NetX POP3. Segue-se uma lista de todas as opções descritas em detalhe:

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: Isto define a opção de espera em segundos para que o Cliente POP3 aloque um pacote. O valor predefinido é 1 segundo.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: Isto define a opção de espera em segundos para que o Cliente POP3 se conecte com o Servidor POP3. O valor predefinido é de 30 segundos.

- **NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: Isto define a opção de espera em segundos para que o Cliente POP3 se desligue do Servidor POP3. O valor predefinido é de 2 segundos.

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: Esta opção define a opção de espera em segundos em chamadas de serviço *nx_tcp_socket_send.* O valor predefinido é de 2 segundos.

- **NX_POP3_SERVER_REPLY_TIMEOUT**: Esta opção define a opção de espera no *nx_tcp_socket_receive* serviço pede a resposta do Servidor a um pedido do Cliente. O valor predefinido é de 10 segundos.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: Esta opção define o tamanho da janela de receção do Cliente TCP. Isto deve ser definido para o tamanho de MTU de instância IP menos o cabeçalho IP e TCP. O valor predefinido é 1460.

- **NX_POP3_MAX_USERNAME**: Esta opção define o tamanho do tampão do nome de utilizador do Cliente POP3. O valor predefinido é de 40 bytes.

- **NX_POP3_MAX_PASSWORD**: Esta opção define o tamanho do tampão da palavra-passe do Cliente POP3. O valor predefinido é de 20 bytes.