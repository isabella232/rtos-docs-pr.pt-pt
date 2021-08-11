---
title: Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 481e29cc674edfa7e437e8e14253172b89aeae6856114192f4ca5b35717c91e0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791538"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX Duo DHCPv6

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo DHCPv6.

## <a name="product-distribution"></a>Distribuição de Produtos

O Cliente NetX Duo DHCPv6 está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nxd_dhcpv6_client.h** Arquivo de cabeçalho para Cliente NetX DuoDHCPv6

- **nxd_dhcpv6_client.c** Ficheiro de código fonte para Cliente NetX Duo DHCPv6

- **demo_netxduo_dhcpv6_client.c** Programa de amostras que demonstra a configuração do Cliente DHCPv6 da NetX Duo

- **nxd_dhcpv6_client.pdf** Descrição em PDF do Cliente NetX Duo DHCPv6

## <a name="netx-duo-dhcpv6-client-installation"></a>Instalação do cliente NetX Duo DHCPv6

Para utilizar a API do Cliente NetX Duo DHCPv6, toda a distribuição acima mencionada pode ser copiada para o mesmo diretório onde o NetX Duo está instalado. Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nxd_dhcpv6_client.h* e *nxd_dhpcv6_client.c* podem ser copiados para este diretório.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Utilizando o Cliente NetX Duo DHCPv6

O código de aplicação deve incluir *nxd_dhcpv6_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar os serviços DHCPv6 Client, ThreadX e NetX Duo, respectivamente. *nxd_dhcpv6_client.c* deve ser compilado no projeto da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Identificador Exclusivo DHCP do Cliente (DUID)</span>

O Cliente DUID define exclusivamente cada Cliente numa rede. Uma aplicação deve criar um DuID do Cliente antes de solicitar um endereço IPv6 a partir de um Servidor. O DuID do Cliente é automaticamente incluído em todas as mensagens para o Servidor. Para criar um DUID, a aplicação chama o serviço *nx_dhcpv6_create_client_duid:*
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

A aplicação chama este serviço e especifica o tipo de DUID (apenas camada de ligação, ou camada de ligação mais tempo. Para a camada de ligação mais os DUIDs de tempo, este serviço fornecerá o campo de tempo se a entrada de tempo não for especificada.

Para dispositivos reiniciando e desejando utilizar uma locação de endereços IPv6 previamente atribuída, a aplicação deve criar o DuID do Cliente como o que utilizou quando lhe foi atribuído o endereço IPv6. O endereço da camada de ligação é tudo o que é necessário para criar uma camada de ligação Cliente DUID. Isto não requer armazenamento de memória não volátil anterior se o dispositivo tiver acesso ao endereço da camada de ligação. Para os DUIDs do tipo de tempo, a aplicação deve ter acesso aos mesmos dados de tempo utilizados na criação duid anterior e isso requer memória não volátil. Os clientes que não tenham qualquer armazenamento estável não devem utilizar DUIDs de tempo tipo.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Associação de Identidade de Cliente para Endereços Não Temporários (IANA)</span>

O pedido deve criar um IANA e opcionalmente um ou mais endereços IA antes de solicitar um endereço IPv6. Para tal, a aplicação chama o *serviço nx_dhcpv6_create_client_iana.* Para criar uma opção de endereço IA, a aplicação liga para o serviço *nx_dhcpv6_add_client_ia* com um endereço IPv6 solicitado e valores de vida como uma dica para o Servidor.

O IANA e os seus IAs definem cumulativamente os parâmetros de atribuição de endereços do Cliente IPv6:

Antes de iniciar o Cliente DHCPv6, a aplicação DHCPv6 Client cria um IANA utilizando o serviço *nx_dhcpv6_create_client_iana:*

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

Deve também criar um ou mais IAs utilizando o serviço *de nx_dhcpv6_create_client_ia* e solicitou endereços IPv6 antes de iniciar o DhCPv6 Client.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> O número de endereços IA que a aplicação cria não pode exceder o parâmetro NX_DHCPV6_MAX_IA_ADDRESS cujo valor padrão é 1.

O Cliente NetX Duo DHCPv6 suporta *nx_dhcpv6_create_client_ia* para aplicações de clientes DHCPv6 legados e que é idêntica a *nx_dhcpv6_add_client_ia* mas os desenvolvedores são encorajados a usar o serviço *nx_dhcpv6_add_client_ia.*

Estes serviços são demonstrados no "Small Example System" noutros capítulos.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Considerações de memória não voláteis para reutilizar IANAs e AI</span>

A aplicação deve guardar os parâmetros IANA T1, T2 e o identificador IANA para memória não volátil se pretender utilizar o mesmo endereço(es) no reinício. A aplicação também deve guardar o seu IA, que inclui o seu endereço IPv6 para memória não volátil.

A aplicação também deve armazenar o tempo decorrido que foi vinculado ao seu(s) designado(s) de endereço iPv6 para memória não volátil se desligar. Fá-lo chamando o serviço *de nx_dhcpv6_get_time_accrued* antes de parar o Cliente DHCPv6.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Assumindo que a aplicação tem um relógio independente para acompanhar o intervalo de tempo desde que parou e reiniciou o Cliente DHCPv6 após um reboot, acrescenta-se a esse tempo decorrido até ao tempo acumulado no contrato de arrendamento IPv6 antes de parar. Inicia agora a tarefa de thread do Cliente com o tempo total decorrido ligado ao arrendamento IPv6 como a entrada nv_time abaixo:

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

A partir deste ponto, a tarefa de thread do Cliente DHCPv6 assumirá a monitorização do tempo acumulado no contrato de arrendamento IPv6 para quando renovar o contrato de arrendamento.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Definição de dados de opção DHCPv6</span>

Antes de solicitar uma locação IPv6, a aplicação pode solicitar outros dados de parâmetros de rede, como servidor DNS e servidor de tempo. Alguns destes parâmetros têm serviços específicos. Alguns são mostrados abaixo:

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Início do Pedido de Endereço IPv6</span>

A aplicação inicia a linha do Cliente DHCPv6 ligando para o serviço *nx_dhcpv6_start* com uma entrada de tempo zero. Para iniciar o protocolo DHCPv6 para solicitar um endereço IPv6, a aplicação chama *nx_dhcpv6_request_solicit.*

Se a aplicação pretender utilizar uma locação IPv6 previamente atribuída, chama *nx_dhcpv6_start* com uma entrada de tempo não zero. Não deve chamar *nx_dhcpv6_request_solicit.*

A partir daí, a aplicação não precisa de fazer mais nada e o Cliente DHCPv6 monitorizará automaticamente quando for a hora de renovar ou reencambir um endereço IPv6.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o Cliente DHCPv6 da NetX Duo é descrito no pequeno exemplo abaixo usando um Cliente DHCPv6 e um controlador virtual "RAM". Esta demonstração pressupõe um dispositivo com apenas uma interface física de rede.

*tx_application_define* cria pacotes para o Cliente DHCPv6 enviar mensagens DHCPv6. Também cria um fio de aplicação e instância IP. Em seguida, permite que uDP e ICMP em IP nas linhas 130-148. Em seguida, o Cliente DHCPv6 é criado com alterações de estado *(dhcpv6_state_change_notify)* e funções de retorno do servidor *(dhcpv6_server_error_handler)* na linha151.

Na função de entrada de thread cliente, *thread_client_entry,* o Computador IP é configurado com um endereço local de ligação e habilitado para os serviços IPv6 e ICMPv6 nas linhas 202-217. Antes de iniciar o DhCPv6 Client, a aplicação cria um DuID do Cliente, uma opção IANA e uma opção de endereço IA nas linhas219-303. A opção de endereço IA é opcional se o Cliente pretender solicitar um endereço IPv6 e uma vida útil válida e preferida a partir do Servidor. O Servidor pode ou não conceder o endereço IPv6 solicitado ou os tempos de locação. A aplicação pode adicionar mais opções de IA (até NX_DHCPV6_MAX_IA_ADDRESS) para ser atribuído vários endereços globais.

Por último, a aplicação define várias opções para solicitar parâmetros de rede nas suas mensagens para o Servidor DHCPv6. A tarefa do Cliente DHCPv6 é iniciada por chamar *nx_dhcpv6_start* na linha 306, e o protocolo DHCPv6 real é iniciado no estado SOLICIT com a chamada para *nx_dhcpv6_request_solicit* na linha 317. O Cliente DHCPv6 lida automaticamente com a promoção do Estado cliente através do protocolo DHCPv6 até que esteja ligado a um endereço ou ocorra um erro. Durante este período, a aplicação aguarda a conclusão do protocolo, bem como a Duplicado Deteção de Endereços (DAD) para concluir se a instância IP estiver configurada para o PAI (que é a configuração padrão).

Após a chamada tx_thread_sleep, a aplicação verifica os parâmetros globais definidos na chamada de alteração do estado para determinar o sucesso da tarefa do Cliente DHCPv6 para obter um contrato de arrendamento IPv6 e, em caso afirmativo, que o PAI verifica a singularidade conseguiu. Isto é feito usando os contadores configurados nas funções de alteração de estado e de chamada de erro do servidor. As sondagens para não zero contagens de address_not_assigned, address_expired e server_errors para atribuição de moradas falhadas. Se a contagem de bound_addresses não for zero (pelo menos um endereço atribuído com sucesso), verifica se um address_failed_dad não zero para uma verificação de PAI falhada. Segue-se uma explicação sobre a alteração do estado e as chamadas de erro do servidor:

A chamada de alteração do estado, *dhcpv6_state_change_notify,* o estado anterior e atual do Cliente DHCPv6 para determinar se o Cliente recebeu alguma resposta válida do Servidor:

  - *dhcpv6_state_change_notify* verifica as transições diretamente do SOLICIT para o INIT e, em caso afirmativo, incrementa um contador para o Cliente DHCPv6 não receber respostas do Servidor.

A *dhcpv6_state_change_notify* verifica se o Cliente foi designado (ligado) a um ou mais endereços IPv6:

  - Se o estado novo for BOUND, incrementa um contador de endereços ligados ao Cliente.
    
O *dhcpv6_state_change_notify* também verifica um cheque de pai falhado:

  - Se o Estado transitar de DECLÍNIO para INIT, o Cliente DHCPv6 falhou na verificação do PAI num dos seus endereços atribuídos e incrementa a contagem de atribuições de endereços falhadas.
    
A última verificação por *dhcpv6_state_change_notify* neste exemplo é para um endereço bem-designado que passou o cheque do PAI para não ser renovado ou reencambido:

  - Se o estado mudar de REBIND para INIT, o Cliente não obtém qualquer resposta aos seus pedidos DE RENOVAÇÃO ou REBIND e *dhcpv6_state_change_notify* incrementa a sua contagem de endereços caducados.

O *dhcpv6_server_error_handler* se notificado pela tarefa do Cliente DHCPv6 de um estado de erro recebido do Servidor incrementa a contagem de erros do servidor.

Assumindo que tudo corre bem, a aplicação consulta o Cliente DHCPv6 para dados de endereço, incluindo tempos de locação. Obtém uma contagem de endereços válidos (atribuídos com sucesso) ligando para o serviço *nx_dhcpv6_get_valid_ip_address_count* e tempo para renovar no IANA (aplica-se a todos os endereços da IA atribuídos) ligando para *nx_dhcpv6_get_iana_lease_time* nas linhas 372-392. Em seguida, consulta o Cliente DHCPv6 por cada uma das suas opções de IA para endereço iPv6 e tempos de locação por índice de endereço.

Alguns serviços de clientes DHCPv6 *(nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address)* não requerem um índice de endereço como entrada e devolvem os parâmetros DHCPv6 para o endereço global do Cliente primário. Isto é adequado para Clientes com um único endereço IPv6 global quando chama *nx_dhcpv6_get_valid_ip_address_lease_time* na linha 384.

A configuração do Cliente DHCPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCPv6 anteriormente criado em estado vinculado entre reboots de sistema. Ligar para o *nx_dhcpv6_client_get_record* para obter o registo do Cliente DHCPv6 entre reinicializações de sistema na linha 434, chamando a *nx_dhcpv6_client_restore_record* para armazenar o registo do Cliente DHCPv6 após a ligação do sistema na linha 525.

A aplicação lança então os endereços atribuídos utilizando o serviço *nx_dhcpv6_request_release* na linha 552. Para reiniciar a aplicação para o Cliente DHCPv6 com o serviço *nx_dhcpv6_client_stop* na linha 567 e limpa todos os endereços IPv6 registados com a instância IP que foram configurados através do Cliente DHCPv6. Fá-lo chamando *nx_dhcpv6_reinitialize* na linha 578. Em seguida, reinicia a tarefa do Cliente DHCPv6 com serviços *de nx_dhcpv6_start* e *nx_dhcpv6_request_solicit* como antes.

O Cliente DHCPv6 é apagado com a chamada para *nx_dhcpv6_delete* na linha626. Note que não apaga a piscina de *pacotes e* th que criou para o Cliente DHCPv6 porque este pacote de piscina também é usado pela instância IP. Caso contrário, deverá eliminar a piscina de pacotes se não tiver mais utilidade para o mesmo utilizando o serviço NetX Duo *nx_packet_pool_delete.*

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

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

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
