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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="0a1f1-103">Capítulo 2 - Instalação e utilização do Azure RTOS NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="0a1f1-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX Duo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="0a1f1-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="0a1f1-105">Product Distribution</span></span>

<span data-ttu-id="0a1f1-106">O Azure RTOS NetX AutoIP pode ser obtido a partir do nosso repositório de código fonte pública em [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="0a1f1-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="0a1f1-107">O pacote inclui três ficheiros de origem, um inclui ficheiros e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0a1f1-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="0a1f1-108">**nx_auto_ip.h**: Ficheiro de cabeçalho para NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="0a1f1-109">**nx_auto_ip.c**: Ficheiro C Fonte para NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="0a1f1-110">**demo_netx_auto_ip.c**: Ficheiro C Fonte para demonstração de NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="0a1f1-111">**nx_auto_ip.pdf**: Descrição em PDF do NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="0a1f1-112">Instalação AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-112">AutoIP Installation</span></span>

<span data-ttu-id="0a1f1-113">Para utilizar o NetX AutoIP, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="0a1f1-114">Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então o *nx_auto_ip.h*, *nx_auto_ip.c*, e *demo_netx_auto_ip.c* ficheiros devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="0a1f1-115">Utilização de AutoIP</span><span class="sxs-lookup"><span data-stu-id="0a1f1-115">Using AutoIP</span></span>

<span data-ttu-id="0a1f1-116">A utilização do NetX AutoIP é fácil.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="0a1f1-117">Basicamente, o código de aplicação deve incluir *nx_auto_ip.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="0a1f1-118">Uma vez incluído *nx_auto_ip.h,* o código de aplicação é então capaz de fazer as chamadas de função AutoIP especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="0a1f1-119">O pedido também deve incluir *nx_auto_ip.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="0a1f1-120">Estes ficheiros devem ser compilados da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="0a1f1-121">Isto é tudo o que é necessário para usar o NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1f1-122">Uma vez que o AutoIP utiliza os serviços ARP netx, o ARP deve ser ativado com a chamada *nx_arp_enable* antes de utilizar o AutoIP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="0a1f1-123">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="0a1f1-123">Small Example System</span></span>

<span data-ttu-id="0a1f1-124">Um exemplo de como é fácil utilizar o NetX AutoIP é descrito na Figura 1.1, que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="0a1f1-125">Neste exemplo, o AutoIP inclui ficheiro *nx_auto_ip.h* é trazido na linha 002.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="0a1f1-126">Em seguida, a instância NetX AutoIP é criada em "*tx_application_define*" na linha 090.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="0a1f1-127">Note que o bloco de controlo NetX AutoIP "auto_ip_0" foi definido anteriormente como uma variável global na linha 015.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="0a1f1-128">Após a criação bem sucedida, um NetX AutoIP é iniciado na linha 098.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="0a1f1-129">O processamento da função de retorno de alteração de endereço IP começa na linha 105, que é usada para lidar com conflitos subsequentes ou possível resolução de endereços DHCP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1f1-130">O exemplo abaixo pressupõe que o dispositivo hospedeiro é um dispositivo de uma única casa.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="0a1f1-131">Para um dispositivo multihomed, a aplicação de anfitrião pode utilizar o serviço NetX AutoIP *nx_auto_ip_interface_* definido para especificar uma interface de rede secundária para sondar para um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="0a1f1-132">Consulte o Guia do [Utilizador NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) para obter mais detalhes sobre a configuração de aplicações multihomed.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="0a1f1-133">Note ainda que a aplicação de anfitrião deve utilizar o *nx_status_ip_interface_check* netx API para verificar se o AutoIP obteve um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

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

<span data-ttu-id="0a1f1-134">Figura 1.1 Exemplo de utilização automática com NetX</span><span class="sxs-lookup"><span data-stu-id="0a1f1-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="0a1f1-135">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="0a1f1-135">Configuration Options</span></span>

<span data-ttu-id="0a1f1-136">Existem várias opções de configuração para a construção do NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="0a1f1-137">Segue-se uma lista de todas as opções, onde cada uma é descrita em detalhe:</span><span class="sxs-lookup"><span data-stu-id="0a1f1-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="0a1f1-138">**NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros autoIP.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="0a1f1-139">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="0a1f1-140">**NX_AUTO_IP_PROBE_WAIT**: O número de segundos a esperar antes de enviar a primeira sonda.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="0a1f1-141">Por predefinição, este valor é definido como 1.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="0a1f1-142">**NX_AUTO_IP_PROBE_NUM**: O número de sondas ARP a enviar.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="0a1f1-143">Por predefinição, este valor é definido como 3.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="0a1f1-144">**NX_AUTO_IP_PROBE_MIN**: O número mínimo de segundos para esperar entre o envio de sondas.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="0a1f1-145">Por predefinição, este valor é definido como 1.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="0a1f1-146">**NX_AUTO_IP_PROBE_MAX**: O número máximo de segundos para esperar entre o envio de sondas.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="0a1f1-147">Por predefinição, este valor é definido como 2.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="0a1f1-148">**NX_AUTO_IP_MAX_CONFLICTS**: O número de conflitos autoip antes de aumentar os atrasos de processamento.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="0a1f1-149">Por predefinição, este valor é definido como 10.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="0a1f1-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: O número de segundos para prolongar o período de espera quando o número total de conflitos for ultrapassado.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="0a1f1-151">Por predefinição, este valor é definido como 60.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="0a1f1-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: O número de segundos a esperar antes de enviar o anúncio.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="0a1f1-153">Por predefinição, este valor é definido como 2.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="0a1f1-154">**NX_AUTO_IP_ANNOUNCE_NUM**: O número de ARP anuncia enviar.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="0a1f1-155">Por predefinição, este valor é definido como 2.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="0a1f1-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: O número de segundos a esperar entre o envio de anúncios.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="0a1f1-157">Por predefinição, este valor é definido como 2.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="0a1f1-158">**NX_AUTO_IP_DEFEND_INTERVAL:** O número de segundos a esperar entre a defesa anuncia.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="0a1f1-159">Por predefinição, este valor é definido como 10.</span><span class="sxs-lookup"><span data-stu-id="0a1f1-159">By default, this value is defined as 10.</span></span>
