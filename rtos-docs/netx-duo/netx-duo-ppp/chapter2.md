---
title: Capítulo 2 - Instalação e utilização do Protocolo Azure RTOS NetX Duo Ponto a Ponto (PPP)
description: Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do componente Azure RTOS NETX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2270a2668884dbecc8368d4ee130e419afa92491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825826"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a><span data-ttu-id="6c6a4-103">Capítulo 2 - Instalação e utilização do Protocolo Azure RTOS NetX Duo Ponto a Ponto (PPP)</span><span class="sxs-lookup"><span data-stu-id="6c6a4-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="6c6a4-104">Este capítulo contém uma descrição de várias questões relacionadas com a instalação, configuração e utilização do componente Azure RTOS NETX Duo Point-to-Point Protocol (PPP).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="6c6a4-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="6c6a4-105">Product Distribution</span></span>

<span data-ttu-id="6c6a4-106">O pacote Azure RTOS NetX Duo Point-to-Point Protocol (PPP) está disponível em <https://github.com/azure-rtos/netxduo> .</span><span class="sxs-lookup"><span data-stu-id="6c6a4-106">The Azure RTOS NetX Duo Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="6c6a4-107">O pacote inclui os seguintes ficheiros:</span><span class="sxs-lookup"><span data-stu-id="6c6a4-107">The package includes the following files:</span></span>

- <span data-ttu-id="6c6a4-108">**nx_ppp.h**: Ficheiro de cabeçalho para PPP para NetX</span><span class="sxs-lookup"><span data-stu-id="6c6a4-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="6c6a4-109">**nx_ppp.c**: Ficheiro C Fonte de PPP para NetX</span><span class="sxs-lookup"><span data-stu-id="6c6a4-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="6c6a4-110">**nx_ppp.pdf**: Descrição pdf de PPP para NetX</span><span class="sxs-lookup"><span data-stu-id="6c6a4-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="6c6a4-111">**demo_netx_ppp.c**: Demonstração de PPP NetX</span><span class="sxs-lookup"><span data-stu-id="6c6a4-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="6c6a4-112">Instalação PPP</span><span class="sxs-lookup"><span data-stu-id="6c6a4-112">PPP Installation</span></span>

<span data-ttu-id="6c6a4-113">Para utilizar pPP para netX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="6c6a4-114">Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*", então os ficheiros *nx_ppp.h* e *nx_ppp.c* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="6c6a4-115">Utilização de PPP</span><span class="sxs-lookup"><span data-stu-id="6c6a4-115">Using PPP</span></span>

<span data-ttu-id="6c6a4-116">A utilização de PPP para NetX é fácil.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="6c6a4-117">Basicamente, o código de aplicação deve incluir *nx_ppp.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="6c6a4-118">Uma vez *incluído nx_ppp.h,* o código de aplicação é então capaz de fazer as chamadas de função PPP especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="6c6a4-119">O pedido também deve incluir *nx_ppp.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="6c6a4-120">Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="6c6a4-121">Isto é tudo o que é necessário para usar pPP NetX.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="6c6a4-122">Utilização de Modems</span><span class="sxs-lookup"><span data-stu-id="6c6a4-122">Using Modems</span></span>

<span data-ttu-id="6c6a4-123">Se for necessário um modem para a ligação à internet, são necessárias algumas considerações especiais para utilizar o produto NetX PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="6c6a4-124">Basicamente, a utilização de um modem introduz lógica de inicialização adicional e lógica para a perda de comunicação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="6c6a4-125">Além disso, a maior parte da lógica adicional do modem é feita fora do contexto da PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="6c6a4-126">O fluxo básico de utilização do PPP NetX com um modem é mais ou menos assim:</span><span class="sxs-lookup"><span data-stu-id="6c6a4-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="6c6a4-127">Inicializar modem</span><span class="sxs-lookup"><span data-stu-id="6c6a4-127">Initialize Modem</span></span>

1. <span data-ttu-id="6c6a4-128">Dial Internet Service Provider (ISP)</span><span class="sxs-lookup"><span data-stu-id="6c6a4-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="6c6a4-129">Aguarde por Conexão</span><span class="sxs-lookup"><span data-stu-id="6c6a4-129">Wait for Connection</span></span>

1. <span data-ttu-id="6c6a4-130">Aguarde o pedido de userID</span><span class="sxs-lookup"><span data-stu-id="6c6a4-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="6c6a4-131">Iniciar a PPP netX [PPP em funcionamento]</span><span class="sxs-lookup"><span data-stu-id="6c6a4-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="6c6a4-132">Perda de comunicação</span><span class="sxs-lookup"><span data-stu-id="6c6a4-132">Loss of Communication</span></span>

1. <span data-ttu-id="6c6a4-133">Parar pPP netx (ou reiniciar via nx_ppp_restart)</span><span class="sxs-lookup"><span data-stu-id="6c6a4-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="6c6a4-134">Inicializar modem</span><span class="sxs-lookup"><span data-stu-id="6c6a4-134">Initialize Modem</span></span>

<span data-ttu-id="6c6a4-135">Utilizando a rotina de saída em série de baixo nível da aplicação, o modem é inicializado através de uma série de comandos de caracteres ASCII (ver documentação do modem para mais detalhes).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="6c6a4-136">Ligue o Fornecedor de Serviços de Internet</span><span class="sxs-lookup"><span data-stu-id="6c6a4-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="6c6a4-137">Utilizando a rotina de saída em série de baixo nível da aplicação, o modem é instruído para marcar o ISP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="6c6a4-138">Por exemplo, o seguinte é típico de uma cadeia ASCII usada para marcar um ISP no número 123-4567:</span><span class="sxs-lookup"><span data-stu-id="6c6a4-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="6c6a4-139">"ATDT123456\r"</span><span class="sxs-lookup"><span data-stu-id="6c6a4-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="6c6a4-140">Aguarde por Conexão</span><span class="sxs-lookup"><span data-stu-id="6c6a4-140">Wait for Connection</span></span>

<span data-ttu-id="6c6a4-141">Neste momento, a aplicação aguarda para receber indicação do modem de que foi estabelecida uma ligação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="6c6a4-142">Isto é conseguido procurando caracteres da rotina de entrada em série de baixo nível da aplicação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="6c6a4-143">Normalmente, os modems devolvem uma cadeia ASCII "CONNECT" quando uma ligação foi estabelecida.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="6c6a4-144">Aguarde a solicitação de id do utilizador</span><span class="sxs-lookup"><span data-stu-id="6c6a4-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="6c6a4-145">Uma vez estabelecida a ligação, o pedido deve agora aguardar um pedido inicial de login do ISP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="6c6a4-146">Isto normalmente assume a forma de uma cadeia ASCII como "Login?"</span><span class="sxs-lookup"><span data-stu-id="6c6a4-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="6c6a4-147">Iniciar NetX PPP</span><span class="sxs-lookup"><span data-stu-id="6c6a4-147">Start NetX PPP</span></span>

<span data-ttu-id="6c6a4-148">Neste momento, o PPP NetX pode ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="6c6a4-149">Isto é conseguido através da chamada para o serviço *nx_ppp_create* seguido pelo serviço *nx_ip_create.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="6c6a4-150">Podem também ser necessários serviços adicionais para permitir o PAP e configurar os endereços IP PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="6c6a4-151">Para mais informações, por favor leia as seguintes secções.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="6c6a4-152">Perda de comunicação</span><span class="sxs-lookup"><span data-stu-id="6c6a4-152">Loss of Communication</span></span>

<span data-ttu-id="6c6a4-153">Uma vez iniciada a PPP, qualquer informação não PPP é transmitida para a rotina de "manuseamento de pacotes inválidos" a aplicação especificada para o serviço *nx_ppp_create.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="6c6a4-154">Normalmente, os modems enviam uma cadeia ASCII como "NO CARRIER" quando a comunicação é perdida com o ISP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="6c6a4-155">Quando a aplicação receber um pacote não PPP com tais informações, deve proceder para parar a instância de PPP NetX ou reiniciar a máquina estatal de PPP através da API *nx_ppp_restart.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="6c6a4-156">Parar o PPP netx</span><span class="sxs-lookup"><span data-stu-id="6c6a4-156">Stop NetX PPP</span></span>

<span data-ttu-id="6c6a4-157">Parar a PPP NetX é bastante simples.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="6c6a4-158">Basicamente, todas as tomadas criadas devem ser desvinculados e apagadas.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="6c6a4-159">Em seguida, elimine a instância IP através do serviço *nx_ip_delete.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="6c6a4-160">Uma vez eliminada a instância IP, o serviço *nx_ppp_delete* deve ser chamado para terminar o processo de paragem das PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="6c6a4-161">Neste momento, o pedido pode agora tentar restabelecer a comunicação com o ISP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="6c6a4-162">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="6c6a4-162">Small Example System</span></span>

<span data-ttu-id="6c6a4-163">Um exemplo que ilustra como é fácil utilizar pPP NetX é descrito na Figura 1.1 que aparece abaixo.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="6c6a4-164">Neste exemplo, as PPP incluem ficheiro *nx_ppp.h* é trazido na linha 3.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="6c6a4-165">Em seguida, pPP é criado em *"tx_application_define"* na linha 56.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="6c6a4-166">O bloco de controlo de PPP "*my_ppp*" foi definido como uma variável global na linha 9 anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="6c6a4-167">As PPP devem ser criadas antes da criação da instância IP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="6c6a4-168">Após a criação bem sucedida de PPP e IP, o fio "*my_thread*" espera que a ligação PPP se viva na linha 98.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="6c6a4-169">Na linha 104, tanto as PPP como a NetX estão totalmente operacionais.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="6c6a4-170">O único item não mostrado neste exemplo é o byte em série da aplicação receber ISR.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="6c6a4-171">Terá de chamar *nx_ppp_byte_receive* com "*my_ppp*" e o byte recebido como parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a><span data-ttu-id="6c6a4-172">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="6c6a4-172">Configuration Options</span></span>

<span data-ttu-id="6c6a4-173">Existem várias opções de configuração para a construção de PPP para NetX.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="6c6a4-174">A seguinte lista descreve cada uma em detalhe:</span><span class="sxs-lookup"><span data-stu-id="6c6a4-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="6c6a4-175">**NX_DISABLE_ERROR_CHECKING**: Definida, esta opção remove a verificação básica de erros de PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="6c6a4-176">É normalmente usado após a depurada aplicação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="6c6a4-177">**NX_PPP_PPPOE_ENABLE**: Se definido, pPP pode transmitir pacote sobre Ethernet</span><span class="sxs-lookup"><span data-stu-id="6c6a4-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="6c6a4-178">**NX_PPP_BASE_TIMEOUT**: Isto define a taxa de período (em carraças tempor, que a tarefa de linha PPP é despertada para verificar se há eventos de PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="6c6a4-179">O valor predefinido é de 1\*NX_IP_PERIODIC_RATE (100 carraças).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="6c6a4-180">**NX_PPP_DISABLE_INFO**: Se definido, a recolha interna de informações sobre PPP é desativada.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="6c6a4-181">**NX_PPP_DEBUG_LOG_ENABLE**: Se definido, o registo interno de depurg de PPP está ativado.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="6c6a4-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:Se definido, a *impressão* interna de registo de PPP depurado para *stdio* está ativada.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="6c6a4-183">Isto só é válido se o registo de depurado também estiver ativado.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="6c6a4-184">**NX_PPP_DEBUG_LOG_SIZE**: Tamanho do registo de depurg (número de entradas no registo de depurg).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="6c6a4-185">Ao chegar à última entrada, a captura de depurges envolve-se à primeira entrada e substitui todos os dados previamente capturados.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="6c6a4-186">O valor predefinido é de 50.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-186">The default value is 50.</span></span>
- <span data-ttu-id="6c6a4-187">**NX_PPP_DEBUG_FRAME_SIZE**: Quantidade máxima de dados capturados a partir de uma carga útil de pacotes recebidos e guardados para depurar a saída.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="6c6a4-188">O valor predefinido é de 50.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-188">The default value is 50.</span></span>
- <span data-ttu-id="6c6a4-189">**NX_PPP_DISABLE_CHAP**: Se definido, a lógica interna de PPP CHAP é removida, incluindo a lógica de digestão MD5.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="6c6a4-190">**NX_PPP_DISABLE_PAP**: Se definido, a lógica interna do PPP PAP é removida.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="6c6a4-191">**NX_PPP_DNS_OPTION_DISABLE**: Se definido, a opção principal do servidor DNS é desativada na resposta IPCP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, the primary DNS Server Option is disabled in the IPCP response.</span></span> <span data-ttu-id="6c6a4-192">Por padrão esta opção não está definida.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-192">By default this option is not defined.</span></span>
- <span data-ttu-id="6c6a4-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: Isto especifica quantas vezes o anfitrião de PPP solicitará um endereço DNS Server do par no estado IPCP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="6c6a4-194">Isto não tem efeito se NX_PPP_DNS_OPTION_DISABLE for definido.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="6c6a4-195">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-195">The default value is 2.</span></span>
- <span data-ttu-id="6c6a4-196">**NX_PPP_HASHED_VALUE_SIZE**: Especifica o tamanho das cordas de "valor hashed" utilizadas na autenticação CHAP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="6c6a4-197">O valor predefinido é definido para 16 bytes, mas pode ser redefinido antes da inclusão de *nx_ppp.h.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="6c6a4-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP esgotarem antes de enviar outra mensagem de pedido de configuração LCP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="6c6a4-199">Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6c6a4-200">O valor predefinido é de 20.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-200">The default value is 20.</span></span>
- <span data-ttu-id="6c6a4-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se o PPP tiver esgotado antes de enviar outra mensagem de pedido de autenticação de PAP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="6c6a4-202">Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6c6a4-203">O valor predefinido é de 20.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-203">The default value is 20.</span></span>
- <span data-ttu-id="6c6a4-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP se esgotarem antes de enviarem outra mensagem de desafio CHAP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="6c6a4-205">Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6c6a4-206">O valor predefinido é de 20.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-206">The default value is 20.</span></span>
- <span data-ttu-id="6c6a4-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: Isto define o número máximo de retrações se as PPP esgotarem antes de enviar outra mensagem de pedido de configuração ipcp.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="6c6a4-208">Quando este número é atingido, o aperto de mão de PPP é abortado e o estado do link está reduzido.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="6c6a4-209">O valor predefinido é de 20.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-209">The default value is 20.</span></span>
- <span data-ttu-id="6c6a4-210">**NX_PPP_MRU**: Especifica a Unidade máxima de Receção (MRU) para PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="6c6a4-211">Por predefinição, este valor é de 1.500 bytes (o valor mínimo).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="6c6a4-212">Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6c6a4-213">**NX_PPP_MINIMUM_MRU**: Especifica o mínimo de MRU recebido numa mensagem de pedido de configuração LCP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="6c6a4-214">Por predefinição, este valor é de 1.500 bytes (o valor mínimo).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="6c6a4-215">Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6c6a4-216">**NX_PPP_NAME_SIZE**: Especifica o tamanho das cordas de "nome" utilizadas na autenticação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="6c6a4-217">O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de \*nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="6c6a4-218">**NX_PPP_PASSWORD_SIZE**: Especifica o tamanho das cordas "password" utilizadas na autenticação.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="6c6a4-219">O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de *nx_ppp.h.*</span><span class="sxs-lookup"><span data-stu-id="6c6a4-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="6c6a4-220">**NX_PPP_PROTOCOL_TIMEOUT**: Isto define a opção de espera (em segundos) para que a tarefa de PPP receba uma resposta a uma mensagem de pedido de protocolo de PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="6c6a4-221">O valor predefinido é de 4 segundos.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="6c6a4-222">**NX_PPP_RECEIVE_TIMEOUTS**: Isto define o número de vezes que o fio de PPP tempos de tarefa à espera de receber o próximo caracter num fluxo de mensagens PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="6c6a4-223">A partir daí, a PPP lança o pacote e começa a esperar para receber a próxima mensagem de PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="6c6a4-224">O valor predefinido é 4.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-224">The default value is 4.</span></span>
- <span data-ttu-id="6c6a4-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Especifica o tamanho do tampão de série de caracteres de receção.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="6c6a4-226">Por padrão, este valor é de 3.000 bytes.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="6c6a4-227">Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6c6a4-228">**NX_PPP_TIMEOUT**: Isto define a opção de espera (em carraças tempor, para alocar pacotes para transmitir dados, bem como dados de série de PPP tampão em pacotes para enviar para a camada IP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="6c6a4-229">O valor predefinido é de 4\*NX_IP_PERIODIC_RATE (400 carraças).</span><span class="sxs-lookup"><span data-stu-id="6c6a4-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="6c6a4-230">**NX_PPP_THREAD_TIME_SLICE**: Opção de corte de tempo para fios de PPP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="6c6a4-231">Por padrão, este valor é TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="6c6a4-232">Esta definição pode ser definida pela aplicação antes da inclusão do *nx_ppp.h*.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="6c6a4-233">**NX_PPP_VALUE_SIZE**: Especifica o tamanho das cordas de "valor" utilizadas na autenticação CHAP.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="6c6a4-234">O valor predefinido é definido para 32bytes, mas pode ser redefinido antes da inclusão de nx_ppp.h.</span><span class="sxs-lookup"><span data-stu-id="6c6a4-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>