---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX PPPoE Server
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NETX PPPoE Server.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825586"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX PPPoE Server

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NETX PPPoE Server.

## <a name="product-distribution"></a>Distribuição de Produtos

O PPPoE Server para NetX está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_pppoe_server.h:** Ficheiro de cabeçalho para PPPoE Server para NetX
- **nx_pppoe_server.c**: Ficheiro C Fonte para PPPoE Server para NetX
- **nx_pppoe_server.pdf**: Descrição em PDF do PPPoE Server para o NetX
- **demo_netx_pppoe_server.c**: Demonstração do Servidor PPPoE NetX

## <a name="pppoe-server-installation"></a>Instalação do servidor PPPoe

Para utilizar o PPPoE Server para o NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*", então os ficheiros *nx_pppoe_server.h* e *nx_pppoe_server.c* devem ser copiados para este diretório.

## <a name="using-pppoe-server"></a>Usando o servidor PPPoE

A utilização do PPPoE Server para o NetX é fácil. Basicamente, o código de aplicação deve incluir *nx_pppoe_server.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente. Uma vez *incluído nx_pppoe_server.h,* o código de aplicação é então capaz de fazer as chamadas de função PPPoE Server especificadas mais tarde neste guia. O pedido também deve incluir *nx_pppoe_server.c* no processo de construção. Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX PPPoE Server.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Segue-se um exemplo que ilustra como utilizar o NetX PPPoE Server na Figura 1.1. Neste exemplo, o PPPoE Server inclui ficheiro *nx_pppoe_server.h* é trazido na linha 50. Em seguida, o PPPoE Server é criado em *"thread_0_entry"* na linha 248. Note que o PPPoE Server deve ser criado após a criação da instância IP. A instância IP é criada e inicializada linha165. O bloco de controlo ppPoE Server "*pppoe_server*" foi definido como uma variável global na linha 79 anteriormente. As funções de notificação são definidas na linha 257. Note que pppoe_session_data_receive função de notificação devem ser definidas. Após a criação bem sucedida do IP e ppPoE Server, o processo ppPoE Server de estabelecer uma sessão PPPoE na chamada para nx_pppoe_server_enable na linha 272.

Em geral, o módulo PPPoE deve ser utilizado com módulo PPP. Neste exemplo, o Servidor PPP inclui ficheiro *nx_ppp.h* é trazido na linha 49. Em seguida, o PPP Server é criado na linha 174. A linha 182 configura a função para enviar o pacote de PPP. Linha 188-200 configura os endereços IP e define o protocolo pap. A linha 115-139 configura o nome de utilizador e a palavra-passe para o protocolo pap.

Após a sessão do PPPoE. A aplicação pode ligar para nx_pppoe_server_session_get para obter a informação da sessão (endereço MAC cliente e id de sessão) na linha 281.

Quando a aplicação deixar de processar o tráfego de PPP, a aplicação PppCloseInd ou nx_pppoe_server_session_terminate para encerrar a sessão ppPoE.

> [!NOTE]
> Neste exemplo, o PPPoE Server trabalha com uma pilha IP normal ao mesmo tempo e partilha um controlador Ethernet. Passe o mesmo controlador Ethernet para a instância IP normal na linha 165 e na placa ppPoE Server na linha 248.

> [!NOTE]
> As funções são fornecidas pela implementação do PPPoE para chamadas pelo software em NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE definidas.

Se definido, ativa a funcionalidade que controla a sessão PPPoE.

O servidor PPPoE não responde automaticamente ao pedido até que a aplicação chame API específica, se não definida, PPPoE Server responde automaticamente ao pedido. Permite por padrão em nx_pppoe_server.h.

Nota: redefina **NX_PHYSICAL_HEADER** a 24 para garantir espaço suficiente para o enchimento do cabeçalho físico. Cabeçalho físico:14 (Cabeçalho Ethernet) + 6 (cabeçalho PPPoE) + 2 (cabeçalho PPP) + 2 (aligamento de quatro byte).

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

Figura 1.1 Exemplo da utilização do Servidor PPPoE com o NetX

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do PPPoE Server para o NetX. A seguinte lista descreve cada uma em detalhe:

- **NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros do PPPoE Server. É normalmente usado após a depurada aplicação.

- **NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: Se definido, permite a funcionalidade que controla a sessão PPPoE. O servidor PPPoE não responde automaticamente ao pedido até que a aplicação ligue para a API específica.

- **NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: Se definido, permite que a função inicialize o controlador Ethernet no módulo PPPoE. Desativa por defeito.

- **NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Opção de corte de tempo para o fio ppPoE Server. Por padrão, este valor é TX_NO_TIME_SLICE.

- **NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: Isto define o número máximo de sessões de clientes simultâneas. Por padrão, este valor é 10.

- **NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: Isto define o tamanho máximo do Host-Uniq. Por padrão, este valor é de 32.

- **NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: Isto define o tamanho máximo de Relay-Session-Id. Por padrão, este valor é 12.

- **NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Especifica o tamanho mínimo de carga útil do pacote para o PPPoE Server. Se o tamanho da carga útil do pacote for maior do que este valor, pode evitar o pacote acorrentado. Por predefinição, este valor é de 1520 (Tamanho máximo de carga útil do Ethernet 1500, Cabeçalho Ethernet 14, CRC 2 e alinhamento de quatro bytes 4).

- **NX_PPPOE_SERVER_PACKET_TIMEOUT**: Isto define a poção de espera (em carraças tempor, para alocar pacotes ou anexar dados em pacotes. Por predefinição, este valor é **NX_IP_PERIODIC_RATE** (100 carraças).

- **NX_PPPOE_SERVER_START_SESSION_ID**: Isto define o ID de sessão de início para atribuir à Sessão PPPoE. Por padrão, este valor é 0X4944 (valor ASCII para ID).