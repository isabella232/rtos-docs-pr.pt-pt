---
title: Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo AutoIP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826168"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo AutoIP

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo AutoIP.

## <a name="product-distribution"></a>Distribuição de Produtos

O Azure RTOS NetX AutoIP pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . O pacote inclui três ficheiros de origem, um inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:

- **nx_auto_ip.h**: Ficheiro de cabeçalho para NetX AutoIP
- **nx_auto_ip.c**: Ficheiro C Fonte para NetX AutoIP
- **demo_netx_auto_ip.c**: Ficheiro C Fonte para demonstração de NetX AutoIP
- **nx_auto_ip.pdf**: Descrição em PDF do NetX AutoIP

## <a name="autoip-installation"></a>Instalação AutoIP

Para utilizar o NetX AutoIP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado. Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então o *nx_auto_ip.h*, *nx_auto_ip.c*, e *demo_netx_auto_ip.c* ficheiros devem ser copiados para este diretório.

## <a name="using-autoip"></a>Utilização de AutoIP

A utilização do NetX AutoIP é fácil. Basicamente, o código de aplicação deve incluir *nx_auto_ip.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX. Uma vez incluído *nx_auto_ip.h,* o código de aplicação é então capaz de fazer as chamadas de função AutoIP especificadas mais tarde neste guia. O pedido também deve incluir *nx_auto_ip.c* no processo de construção. Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação. Isto é tudo o que é necessário para usar o NetX AutoIP.

> [!NOTE]
> Uma vez que o AutoIP utiliza os serviços ARP netx, o ARP deve ser ativado com a chamada *nx_arp_enable* antes de utilizar o AutoIP.

## <a name="small-example-system"></a>Sistema de Pequenos Exemplos

Um exemplo de como é fácil utilizar o NetX AutoIP é descrito na Figura 1.1, que aparece abaixo. Neste exemplo, o AutoIP inclui ficheiro *nx_auto_ip.h* é trazido na linha 002. Em seguida, a instância NetX AutoIP é criada em "*tx_application_define*" na linha 090. Note que o bloco de controlo NetX AutoIP "auto_ip_0" foi definido anteriormente como uma variável global na linha 015. Após a criação bem sucedida, um NetX AutoIP é iniciado na linha 098. O processamento da função de retorno de alteração de endereço IP começa na linha 105, que é usada para lidar com conflitos subsequentes ou possível resolução de endereços DHCP.

> [!NOTE]
> O exemplo abaixo pressupõe que o dispositivo hospedeiro é um dispositivo de uma única casa. Para um dispositivo multihomed, a aplicação de anfitrião pode utilizar o serviço NetX AutoIP *nx_auto_ip_interface_* definido para especificar uma interface de rede secundária para sondar para um endereço IP. Consulte o Guia do [Utilizador NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) para obter mais detalhes sobre a configuração de aplicações multihomed. Note ainda que a aplicação de anfitrião deve utilizar o *nx_status_ip_interface_check* netx API para verificar se o AutoIP obteve um endereço IP.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

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
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

Figura 1.1 Exemplo de utilização automática com NetX

## <a name="configuration-options"></a>Opções de configuração

Existem várias opções de configuração para a construção do NetX AutoIP. Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:

- **NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros autoIP. É normalmente usado após a depurada aplicação.
- **NX_AUTO_IP_PROBE_WAIT**: O número de segundos a esperar antes de enviar a primeira sonda. Por predefinição, este valor é definido como 1.
- **NX_AUTO_IP_PROBE_NUM**: O número de sondas ARP a enviar. Por predefinição, este valor é definido como 3.
- **NX_AUTO_IP_PROBE_MIN**: O número mínimo de segundos para esperar entre o envio de sondas. Por predefinição, este valor é definido como 1.
- **NX_AUTO_IP_PROBE_MAX**: O número máximo de segundos para esperar entre o envio de sondas. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: O número de conflitos autoip antes de aumentar os atrasos de processamento. Por predefinição, este valor é definido como 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: O número de segundos para prolongar o período de espera quando o número total de conflitos for ultrapassado. Por predefinição, este valor é definido como 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: O número de segundos a esperar antes de enviar o anúncio. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: O número de ARP anuncia enviar. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: O número de segundos a esperar entre o envio de anúncios. Por predefinição, este valor é definido como 2.
- **NX_AUTO_IP_DEFEND_INTERVAL:** O número de segundos a esperar entre a defesa anuncia. Por predefinição, este valor é definido como 10.
