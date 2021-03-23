---
title: Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826798"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="87287-103">Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="87287-103">Chapter 2 - Installation and use of Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="87287-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente Azure RTOS NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="87287-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="87287-105">Product Distribution</span></span>

<span data-ttu-id="87287-106">DHCP para NetX está disponível em [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="87287-106">DHCP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="87287-107">O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="87287-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="87287-108">**nx_dhcp.h** Arquivo de cabeçalho para DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="87287-108">**nx_dhcp.h** Header file for DHCP for NetX</span></span>

- <span data-ttu-id="87287-109">**nx_dhcp.c** C Arquivo de origem para DHCP para NetX</span><span class="sxs-lookup"><span data-stu-id="87287-109">**nx_dhcp.c** C Source file for DHCP for NetX</span></span>

- <span data-ttu-id="87287-110">**nx_dhcp.pdf** Descrição em PDF do DHCP para o NetX</span><span class="sxs-lookup"><span data-stu-id="87287-110">**nx_dhcp.pdf** PDF description of DHCP for NetX</span></span>

- <span data-ttu-id="87287-111">**demo_netx_dhcp.c** Demonstração do NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="87287-111">**demo_netx_dhcp.c** NetX DHCP demonstration</span></span>

- <span data-ttu-id="87287-112">**demo_netx_multihome_dhcp_client.c** Demonstração do cliente NetX DHCP de DHCP em várias interfaces</span><span class="sxs-lookup"><span data-stu-id="87287-112">**demo_netx_multihome_dhcp_client.c** NetX DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="87287-113">Instalação DHCP</span><span class="sxs-lookup"><span data-stu-id="87287-113">DHCP Installation</span></span>

<span data-ttu-id="87287-114">Para utilizar o DHCP para o NetX, toda a distribuição mencionada anteriormente deve ser copiada para o mesmo diretório onde o NetX está instalado.</span><span class="sxs-lookup"><span data-stu-id="87287-114">To use DHCP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="87287-115">Por exemplo, se o NetX for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nx_dhcp.h* e *nx_dhcp.c* devem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="87287-115">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dhcp.h* and *nx_dhcp.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="87287-116">Utilização do DHCP</span><span class="sxs-lookup"><span data-stu-id="87287-116">Using DHCP</span></span>

<span data-ttu-id="87287-117">A utilização do DHCP para o NetX é fácil.</span><span class="sxs-lookup"><span data-stu-id="87287-117">Using DHCP for NetX is easy.</span></span> <span data-ttu-id="87287-118">Basicamente, o código de aplicação deve incluir *nx_dhcp.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar o ThreadX e o NetX, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="87287-118">Basically, the application code must include *nx_dhcp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="87287-119">Uma vez *incluído nx_dhcp.h,* o código de aplicação é então capaz de fazer as chamadas de função DHCP especificadas mais tarde neste guia.</span><span class="sxs-lookup"><span data-stu-id="87287-119">Once *nx_dhcp.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="87287-120">O pedido também deve incluir *nx_dhcp.c* no processo de construção.</span><span class="sxs-lookup"><span data-stu-id="87287-120">The application must also include *nx_dhcp.c* in the build process.</span></span> <span data-ttu-id="87287-121">Este ficheiro deve ser compilado da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="87287-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="87287-122">Isto é tudo o que é necessário para usar o NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="87287-123">Note que uma vez que o DHCP utiliza os serviços de UDP NetX, o UDP deve ser ativado com a *chamada nx_udp_enable* antes de utilizar o DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-123">Note that since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="87287-124">Para obter um endereço IP previamente atribuído, o Cliente DHCP pode iniciar o processo DHCP com a mensagem Request e o Option 50 "Endereço IP Solicitado" para o Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="87287-125">O Servidor DHCP responderá com uma mensagem ACK se conceder o endereço IP ao Cliente ou a um NACK se recusar.</span><span class="sxs-lookup"><span data-stu-id="87287-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="87287-126">Neste último caso, o Cliente DHCP reinicia o processo DHCP no estado do Init com uma mensagem Discover e sem endereço IP solicitado.</span><span class="sxs-lookup"><span data-stu-id="87287-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="87287-127">A aplicação de anfitrião cria primeiro o Cliente DHCP, depois liga para o serviço API *nx_dhcp_request_client_ip* para definir o endereço IP solicitado antes de iniciar o processo DHCP com *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="87287-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="87287-128">Um exemplo de pedido dhCP é fornecido em outros lugares neste documento para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="87287-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="87287-129">No Estado Vinculado</span><span class="sxs-lookup"><span data-stu-id="87287-129">In the Bound State</span></span>

<span data-ttu-id="87287-130">Enquanto o Cliente DHCP se encontra no estado vinculado, o fio do Cliente DHCP processa o Estado cliente uma vez por intervalo (conforme especificado por NX_DHCP_TIME_INTERVAL) e decrementa o tempo restante no contrato de arrendamento IP atribuído ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="87287-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="87287-131">Quando o tempo de renovação tiver decorrido, o estado do Cliente DHCP é atualizado para o estado DE RENOVAÇÃO onde o Cliente solicitará uma renovação do Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>


## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="87287-132">Envio de mensagens DHCP para o servidor</span><span class="sxs-lookup"><span data-stu-id="87287-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="87287-133">O Cliente DHCP dispõe de serviços API que permitem ao anfitrião enviar uma mensagem para o Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="87287-134">Note que estes serviços NÃO se destinam à aplicação de anfitrião para executar manualmente o protocolo do Cliente DHCP, uma vez que enviam a mensagem principalmente sem atualizar necessariamente o estado interno do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol as they primarily send the message without necessarily updating the DHCP Client internal state.</span></span>

  - <span data-ttu-id="87287-135">*nx_dhcp_release:* isto envia uma mensagem RELEASE para o Servidor quando a aplicação do anfitrião está a sair da rede ou precisa de abdicar do seu endereço IP.</span><span class="sxs-lookup"><span data-stu-id="87287-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>

  - <span data-ttu-id="87287-136">*nx_dhcp_decline:* isto envia uma mensagem DECLINAR para o Servidor se a aplicação do anfitrião determinar independentemente do Cliente DHCP que o seu endereço IP já está a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="87287-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>

  - <span data-ttu-id="87287-137">*nx_dhcp_forcerenew:* isto envia uma mensagem FORCERENEW para o Servidor</span><span class="sxs-lookup"><span data-stu-id="87287-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>

  - <span data-ttu-id="87287-138">*nx_dhcp_send_request*: Isto requer como argumento um tipo de mensagem DHCP, conforme especificado em *nx_dhcp.h*, e envia a mensagem para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="87287-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nx_dhcp.h*, and sends the message to the Server.</span></span> <span data-ttu-id="87287-139">Esta posição destina-se principalmente ao envio da mensagem DHCP INFORM.</span><span class="sxs-lookup"><span data-stu-id="87287-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="87287-140">Consulte "*Descrição dos Serviços DHCP*" para obter mais informações sobre estes serviços em outros lugares deste documento.</span><span class="sxs-lookup"><span data-stu-id="87287-140">See “*Description of DHCP Services*” for more information about these services elsewhere in this document.</span></span>

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="87287-141">Iniciar e Parar o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="87287-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="87287-142">Para parar o Cliente DHCP, independentemente de ter alcançado um estado vinculado, a aplicação de anfitrião chama *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="87287-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="87287-143">Para reiniciar um cliente DHCP, a aplicação de anfitrião deve primeiro parar o Cliente DHCP usando o serviço *nx_dhcp_stop* acima descrito.</span><span class="sxs-lookup"><span data-stu-id="87287-143">To restart a DHCP client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="87287-144">Em seguida, o anfitrião pode *chamá nx_dhcp_start* para retomar o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="87287-145">Se a aplicação anfitriã pretender limpar um perfil de Cliente DHCP anterior, por exemplo, um obtido a partir de um servidor DHCP anterior em outra rede, a aplicação do anfitrião deve ligar *para nx_dhcp_reinitialize* para executar esta tarefa internamente antes de ligar nx_dhcp_start.</span><span class="sxs-lookup"><span data-stu-id="87287-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling nx_dhcp_start.</span></span>

<span data-ttu-id="87287-146">Uma sequência típica pode ser:</span><span class="sxs-lookup"><span data-stu-id="87287-146">A typical sequence might be:</span></span>

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="87287-147">Para aplicações DHCP em execução apenas numa única interface DHCP, parar o Cliente DHCP também inativa o temporizador DHCP CLIENT.</span><span class="sxs-lookup"><span data-stu-id="87287-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="87287-148">Assim, já não está a acompanhar o tempo que resta no arrendamento IP.</span><span class="sxs-lookup"><span data-stu-id="87287-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="87287-149">Parar o Cliente DHCP numa determinada interface não irá inativar o temporizador do Cliente DHCP, mas irá parar as atualizações do temporizador para o tempo restante no aluguer IP nessa interface.</span><span class="sxs-lookup"><span data-stu-id="87287-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface.</span></span>

<span data-ttu-id="87287-150">Portanto, parar o Cliente DHCP não é aconselhável a menos que a aplicação de anfitrião exija reiniciar ou mudar de rede.</span><span class="sxs-lookup"><span data-stu-id="87287-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="87287-151">Utilização do Cliente DHCP com IP automático</span><span class="sxs-lookup"><span data-stu-id="87287-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="87287-152">O Cliente NetX DHCP trabalha em simultâneo com o protocolo AUTO IP em aplicações onde DHCP e Auto IP garantem um endereço onde um Servidor DHCP não está garantido para estar disponível ou responder.</span><span class="sxs-lookup"><span data-stu-id="87287-152">The NetX DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="87287-153">No entanto, se o anfitrião não conseguir detetar um Servidor ou obter um endereço IP atribuído, pode mudar para o protocolo IP automático para um endereço IP local.</span><span class="sxs-lookup"><span data-stu-id="87287-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="87287-154">No entanto, antes de o fazer, é aconselhável parar temporariamente o Cliente DHCP enquanto o AUTO IP passa pelas fases de "sonda" e "defesa".</span><span class="sxs-lookup"><span data-stu-id="87287-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="87287-155">Uma vez atribuído um endereço IP automático ao anfitrião, o Cliente DHCP pode ser reiniciado e se um Servidor DHCP ficar disponível, o endereço IP do anfitrião pode aceitar o endereço IP oferecido pelo Servidor DHCP enquanto a aplicação estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="87287-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="87287-156">O NetX Auto IP tem uma notificação de alteração de endereço para o anfitrião monitorizar as suas atividades em caso de alteração de endereço IP.</span><span class="sxs-lookup"><span data-stu-id="87287-156">The NetX Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="87287-157">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="87287-157">Small Example System</span></span>

<span data-ttu-id="87287-158">Um exemplo de como a utilização do NetX é descrita na Figura 1.1 abaixo.</span><span class="sxs-lookup"><span data-stu-id="87287-158">An example of how use NetX is described in Figure 1.1 below.</span></span> <span data-ttu-id="87287-159">O Cliente DHCP é criado "*my_thread_entry*" na linha 101.</span><span class="sxs-lookup"><span data-stu-id="87287-159">The DHCP Client is created “*my_thread_entry*” at line 101.</span></span> <span data-ttu-id="87287-160">Após a criação bem sucedida, o processo DHCP é iniciado na chamada para *nx_dhcp_start* na linha 108.</span><span class="sxs-lookup"><span data-stu-id="87287-160">After successful creation, the DHCP process is initiated at the call to *nx_dhcp_start* at line 108.</span></span> <span data-ttu-id="87287-161">Neste momento, inicia-se a tentativa do Cliente DHCP de contactar o servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-161">At this point the DHCP Client attempts are initiated to contact the DHCP server.</span></span> <span data-ttu-id="87287-162">Durante este processo, o código de aplicação aguarda que um endereço IP válido seja registado na instância IP utilizando o serviço *nx_ip_status_check* (ou *nx_ip_interface_status_check* para uma interface secundária) a partir da linha 95.</span><span class="sxs-lookup"><span data-stu-id="87287-162">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) starting at line 95.</span></span> <span data-ttu-id="87287-163">Isto é mais comumente feito em loop com uma opção de espera mais curta.</span><span class="sxs-lookup"><span data-stu-id="87287-163">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="87287-164">Após a linha 127, o DHCP recebeu um endereço IP válido e a aplicação pode então prosseguir, utilizando os serviços NetX TCP/IP conforme pretendido.</span><span class="sxs-lookup"><span data-stu-id="87287-164">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX TCP/IP services as desired.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="87287-165">Figura 1.1 Exemplo da utilização do DHCP com o NetX</span><span class="sxs-lookup"><span data-stu-id="87287-165">Figure 1.1 Example of DHCP use with NetX</span></span>

## <a name="multi-server-environments"></a><span data-ttu-id="87287-166">Ambientes multi-servidores</span><span class="sxs-lookup"><span data-stu-id="87287-166">Multi-Server Environments</span></span>

<span data-ttu-id="87287-167">Nas redes onde existe mais de um Servidor DHCP, o Cliente DHCP aceita a primeira mensagem de Oferta de Servidor DHCP recebida, avança para o estado de Pedido e ignora quaisquer outras ofertas recebidas.</span><span class="sxs-lookup"><span data-stu-id="87287-167">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="87287-168">Sondas ARP</span><span class="sxs-lookup"><span data-stu-id="87287-168">ARP Probes</span></span>

<span data-ttu-id="87287-169">O Cliente DHCP pode ser configurado para enviar uma ou mais sondas ARP após a atribuição de endereços IP do Servidor DHCP para verificar se o endereço IP ainda não está a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="87287-169">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="87287-170">O passo da sonda ARP é recomendado pelo RFC 2131 e é particularmente importante em ambientes com mais de um Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-170">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="87287-171">Se a aplicação de anfitrião permitir a opção NX_DHCP_CLIENT_SEND_ARP_PROBE (ver **Opções de Configuração** no Capítulo Dois para opções adicionais de sonda ARP), o Cliente DHCP enviará uma sonda ARP 'auto-endereçada' e aguardará o tempo especificado para uma resposta.</span><span class="sxs-lookup"><span data-stu-id="87287-171">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="87287-172">Se nenhum for recebido, o Cliente DHCP avança para o estado de Bound.</span><span class="sxs-lookup"><span data-stu-id="87287-172">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="87287-173">Se uma resposta for recebida, o Cliente DHCP assume que o endereço já está em uso.</span><span class="sxs-lookup"><span data-stu-id="87287-173">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="87287-174">Envia automaticamente uma mensagem DECLINar para o Servidor e reinicia o Cliente para reiniciar as sondas DHCP novamente a partir do estado INIT.</span><span class="sxs-lookup"><span data-stu-id="87287-174">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="87287-175">Isto reinicia a máquina estatal DHCP e o Cliente envia outra mensagem DISCOVER para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="87287-175">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="87287-176">Protocolo BOOTP</span><span class="sxs-lookup"><span data-stu-id="87287-176">BOOTP Protocol</span></span>

<span data-ttu-id="87287-177">O Cliente DHCP também suporta o protocolo BOOTP, bem como o protocolo DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-177">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="87287-178">Para ativar esta opção e utilizar o BOOTP em vez de DHCP, a aplicação do anfitrião deve definir a opção de configuração NX_DHCP_BOOTP_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="87287-178">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="87287-179">A aplicação de anfitrião ainda pode solicitar endereços IP específicos no protocolo BOOTP.</span><span class="sxs-lookup"><span data-stu-id="87287-179">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="87287-180">No entanto, o Cliente DHCP não suporta o carregamento do sistema operativo anfitrião, uma vez que o BOOTP é por vezes utilizado para o fazer.</span><span class="sxs-lookup"><span data-stu-id="87287-180">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="87287-181">DHCP em uma interface secundária</span><span class="sxs-lookup"><span data-stu-id="87287-181">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="87287-182">O Cliente DHCP NetX pode funcionar em interfaces secundárias em vez da interface primária predefinido.</span><span class="sxs-lookup"><span data-stu-id="87287-182">The NetX DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="87287-183">Para executar o Cliente NetX DHCP numa interface de rede secundária, a aplicação de anfitrião deve definir o índice de interface do Cliente DHCP para a interface secundária utilizando o serviço API *nx_dhcp_set_interface_index.*</span><span class="sxs-lookup"><span data-stu-id="87287-183">To run NetX DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="87287-184">A interface já deve estar ligada à interface de rede primária utilizando o serviço *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="87287-184">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="87287-185">Consulte o Guia do Utilizador NetX para obter mais detalhes sobre a fixação de interfaces secundárias.</span><span class="sxs-lookup"><span data-stu-id="87287-185">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="87287-186">Abaixo na Figura 1.2 encontra-se um sistema de exemplo no qual a aplicação do anfitrião se conecta ao servidor DHCP na sua interface secundária.</span><span class="sxs-lookup"><span data-stu-id="87287-186">Below in Figure 1.2 is an example system on which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="87287-187">Na linha 65, a interface secundária é anexada à tarefa IP com um endereço IP nulo.</span><span class="sxs-lookup"><span data-stu-id="87287-187">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="87287-188">Na linha 104, após a criação da instância do Cliente DHCP, o índice de interface do cliente DHCP é definido para 1 (por exemplo, a compensação da interface primária que por si só é índice 0) chamando *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="87287-188">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="87287-189">Então o Cliente DHCP está pronto para ser iniciado na linha 108.</span><span class="sxs-lookup"><span data-stu-id="87287-189">Then the DHCP Client is ready to be started in line 108.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="87287-190">Figura 1.2 Exemplo de DHCP para NetX com suporte multihome</span><span class="sxs-lookup"><span data-stu-id="87287-190">Figure 1.2 Example of DHCP for NetX with multihome support</span></span>

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="87287-191">Cliente DHCP em múltiplas interfaces simultaneamente</span><span class="sxs-lookup"><span data-stu-id="87287-191">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="87287-192">Para executar o Cliente DHCP em várias interfaces, NX_MAX_PHYSICAL_INTERFACES em *nx_api.h* devem ser definidos para o número de interfaces físicas ligadas ao dispositivo.</span><span class="sxs-lookup"><span data-stu-id="87287-192">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="87287-193">Por predefinição, este valor é 1 (por exemplo, a interface primária).</span><span class="sxs-lookup"><span data-stu-id="87287-193">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="87287-194">Para registar uma interface adicional para a instância IP, utilize o serviço *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="87287-194">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="87287-195">Consulte o Guia do Utilizador NetX para obter mais detalhes sobre a fixação de interfaces secundárias.</span><span class="sxs-lookup"><span data-stu-id="87287-195">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="87287-196">O próximo passo é definir o NX_DHCP_CLIENT_MAX_RECORDS em *nx_dhcp.h* para o número máximo de interfaces que se espera que sejam executadas em simultâneo.</span><span class="sxs-lookup"><span data-stu-id="87287-196">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nx_dhcp.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="87287-197">Note que NX_DHCP_CLIENT_MAX_RECORDS não tem que ser igual a NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="87287-197">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="87287-198">Por exemplo, NX_MAX_PHYSICAL_INTERFACES pode ser 3 e NX_DHCP_CLIENT_MAX_RECORDS igual a 2.</span><span class="sxs-lookup"><span data-stu-id="87287-198">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="87287-199">Nesta configuração, apenas duas interfaces (e podem ser qualquer uma das três interfaces físicas a qualquer momento) das três interfaces físicas podem executar DHCP a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="87287-199">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="87287-200">A DHCP Client Records não tem um mapeamento de um a um para interfaces de rede, por exemplo, o Registo do Cliente 1 não se correlaciona automaticamente com o índice de interface física 1.</span><span class="sxs-lookup"><span data-stu-id="87287-200">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="87287-201">NX_DHCP_CLIENT_MAX_RECORDS também podem ser definidos para maiores do que NX_MAX_PHYSICAL_INTERFACES mas isso criaria registos de clientes não utilizados e seria um uso ineficiente da memória.</span><span class="sxs-lookup"><span data-stu-id="87287-201">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="87287-202">Antes de iniciar o DHCP em qualquer interface, a aplicação deve permitir essas interfaces chamando *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="87287-202">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="87287-203">Note que a exceção é a interface primária que é automaticamente ativada na chamada *nx_dhcp_create* (e que pode ser desativada usando o serviço *nx_dhcp_interface_disable* discutido abaixo).</span><span class="sxs-lookup"><span data-stu-id="87287-203">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="87287-204">A qualquer momento, uma interface pode ser desativada para DHCP ou DHCP pode ser interrompida nessa interface independentemente de outras interfaces que executam o DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-204">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="87287-205">Como mencionado acima, para permitir uma interface específica para DHCP, use o serviço *nx_dhcp_interface_enable* e especifique o índice de interface física no argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="87287-205">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="87287-206">Até NX_DHCP_CLIENT_MAX_RECORDS interfaces podem ser ativadas com a única limitação de que o argumento de entrada do índice de interface seja inferior a NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="87287-206">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="87287-207">Para iniciar o DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_start.*</span><span class="sxs-lookup"><span data-stu-id="87287-207">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="87287-208">Para iniciar o DHCP em todas as interfaces ativadas, utilize o serviço *nx_dhcp_start.*</span><span class="sxs-lookup"><span data-stu-id="87287-208">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="87287-209">(As interfaces que já iniciaram o DHCP não serão afetadas pela *nx_dhcp_start*.)</span><span class="sxs-lookup"><span data-stu-id="87287-209">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="87287-210">Para parar o DHCP numa interface, utilize o serviço *nx_dhcp_interface_stop.*</span><span class="sxs-lookup"><span data-stu-id="87287-210">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="87287-211">O DHCP já deve ter começado nessa interface ou é devolvido um estado de erro.</span><span class="sxs-lookup"><span data-stu-id="87287-211">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="87287-212">Para parar o DHCP em todas as interfaces ativadas, utilize o serviço *nx_dhcp_stop.*</span><span class="sxs-lookup"><span data-stu-id="87287-212">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="87287-213">O DHCP pode ser parado independentemente de outras interfaces a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="87287-213">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="87287-214">A maioria dos serviços existentes do DhCP Client têm um equivalente de interface, por *exemplo, nx_dhcp_interface_release* é o equivalente específico da interface de *nx_dhcp_release.*</span><span class="sxs-lookup"><span data-stu-id="87287-214">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="87287-215">Se o Cliente DHCP estiver configurado para uma única interface, realizam a mesma ação.</span><span class="sxs-lookup"><span data-stu-id="87287-215">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="87287-216">Note que os serviços específicos do DHCP normalmente se aplicam a todas as interfaces, mas não a todas.</span><span class="sxs-lookup"><span data-stu-id="87287-216">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="87287-217">Neste último caso, o serviço específico de não interface aplica-se à primeira interface ativada pelo DHCP encontrada na pesquisa da lista de registos de interface do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-217">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="87287-218">Consulte **a Descrição dos Serviços** no Capítulo Três para saber como um serviço específico não-interface funciona quando várias interfaces estão ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-218">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="87287-219">Na sequência de exemplo abaixo, a instância IP tem duas interfaces de rede e executa primeiro o DHCP na interface secundária.</span><span class="sxs-lookup"><span data-stu-id="87287-219">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="87287-220">Em algum momento depois, começa o DHCP na interface primária.</span><span class="sxs-lookup"><span data-stu-id="87287-220">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="87287-221">Em seguida, lança o endereço IP na interface primária e reinicia o DHCP na interface primária:</span><span class="sxs-lookup"><span data-stu-id="87287-221">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

<span data-ttu-id="87287-222">Para obter uma lista completa de serviços específicos da interface consulte **descrição dos serviços** no capítulo três.</span><span class="sxs-lookup"><span data-stu-id="87287-222">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="87287-223">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="87287-223">Configuration Options</span></span>

<span data-ttu-id="87287-224">As opções DHCP configuráveis do utilizador em *nx_dhcp.h* permitem que a aplicação do anfitrião afina o Cliente DHCP para os seus requisitos específicos.</span><span class="sxs-lookup"><span data-stu-id="87287-224">User configurable DHCP options in *nx_dhcp.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="87287-225">Segue-se uma lista destes parâmetros:</span><span class="sxs-lookup"><span data-stu-id="87287-225">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="87287-226">**NX_DHCP_ENABLE_BOOTP** Definida, esta opção permite o protocolo BOOTP em vez de DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-226">**NX_DHCP_ENABLE_BOOTP** Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="87287-227">Por predefinição, esta opção é desativada.</span><span class="sxs-lookup"><span data-stu-id="87287-227">By default this option is disabled.</span></span>

- <span data-ttu-id="87287-228">**NX_DHCP_CLIENT_RESTORE_STATE** Se definido, isto permite ao Cliente DHCP guardar a sua licença de cliente DHCP atual 'estado' incluindo o tempo restante no arrendamento, e restaurar este estado entre reinicializações de aplicação do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-228">**NX_DHCP_CLIENT_RESTORE_STATE** If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="87287-229">O valor predefinido é desativado.</span><span class="sxs-lookup"><span data-stu-id="87287-229">The default value is disabled.</span></span>

- <span data-ttu-id="87287-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** Se estiver definido, o Cliente DHCP não criará a sua própria piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="87287-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="87287-231">A aplicação de anfitrião deve utilizar o serviço nx_dhcp_packet_pool_set para definir o conjunto de pacotes do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-231">The host application must use the nx_dhcp_packet_pool_set service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="87287-232">O valor predefinido é desativado.</span><span class="sxs-lookup"><span data-stu-id="87287-232">The default value is disabled.</span></span>

- <span data-ttu-id="87287-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Definido, isto permite ao Cliente DHCP enviar uma sonda ARP após a atribuição de endereço IP para verificar se o endereço DHCP atribuído não é propriedade de outro anfitrião.</span><span class="sxs-lookup"><span data-stu-id="87287-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="87287-234">Por predefinição, esta opção é desativada.</span><span class="sxs-lookup"><span data-stu-id="87287-234">By default, this option is disabled.</span></span>

- <span data-ttu-id="87287-235">**NX_DHCP_ARP_PROBE_WAIT** Define o tempo que o Cliente DHCP espera por uma resposta após o envio de uma sonda ARP.</span><span class="sxs-lookup"><span data-stu-id="87287-235">**NX_DHCP_ARP_PROBE_WAIT** Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="87287-236">O valor predefinido é de um segundo (1 \* NX_IP_PERIODIC_RATE)</span><span class="sxs-lookup"><span data-stu-id="87287-236">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>

- <span data-ttu-id="87287-237">**NX_DHCP_ARP_PROBE_MIN** Define a variação mínima no intervalo entre o envio de sondas ARP.</span><span class="sxs-lookup"><span data-stu-id="87287-237">**NX_DHCP_ARP_PROBE_MIN** Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="87287-238">O valor é de incumprimento para 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="87287-238">The value is defaulted to 1 second.</span></span>

- <span data-ttu-id="87287-239">**NX_DHCP_ARP_PROBE_MAX** Define a variação máxima no intervalo entre o envio de sondas ARP.</span><span class="sxs-lookup"><span data-stu-id="87287-239">**NX_DHCP_ARP_PROBE_MAX** Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="87287-240">O valor está em incumprimento de 2 segundos.</span><span class="sxs-lookup"><span data-stu-id="87287-240">The value is defaulted to 2 seconds.</span></span>

- <span data-ttu-id="87287-241">**NX_DHCP_ARP_PROBE_NUM** Define o número de sondas ARP enviadas para determinar se o endereço IP atribuído pelo servidor DHCP já está em uso.</span><span class="sxs-lookup"><span data-stu-id="87287-241">**NX_DHCP_ARP_PROBE_NUM** Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="87287-242">O valor é desafinado em 3 sondas.</span><span class="sxs-lookup"><span data-stu-id="87287-242">The value is defaulted to 3 probes.</span></span>

- <span data-ttu-id="87287-243">**NX_DHCP_RESTART_WAIT** Define o tempo que o Cliente DHCP espera para reiniciar o DHCP se o endereço IP atribuído ao Cliente DHCP já estiver em uso.</span><span class="sxs-lookup"><span data-stu-id="87287-243">**NX_DHCP_RESTART_WAIT** Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="87287-244">O valor está em incumprimento de 10 segundos.</span><span class="sxs-lookup"><span data-stu-id="87287-244">The value is defaulted to 10 seconds.</span></span>

- <span data-ttu-id="87287-245">**NX_DHCP_CLIENT_MAX_RECORDS** Especifica o número máximo de registos de interface para guardar para a instância do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-245">**NX_DHCP_CLIENT_MAX_RECORDS** Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="87287-246">Um registo de interface do Cliente DHCP é um registo do Cliente DHCP em execução numa interface específica.</span><span class="sxs-lookup"><span data-stu-id="87287-246">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="87287-247">O valor predefinido é definido à medida que as interfaces físicas contam(NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="87287-247">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>

- <span data-ttu-id="87287-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Definido, isto permite ao Cliente DHCP enviar a opção máxima de tamanho de mensagem DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="87287-249">Por predefinição, esta opção é desativada.</span><span class="sxs-lookup"><span data-stu-id="87287-249">By default, this option is disabled.</span></span>

- <span data-ttu-id="87287-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Definido, isto permite ao Cliente DHCP verificar o nome do anfitrião de entrada no nx_dhcp_create chamada para caracteres ou comprimento inválidos.</span><span class="sxs-lookup"><span data-stu-id="87287-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="87287-251">Por predefinição, esta opção é desativada.</span><span class="sxs-lookup"><span data-stu-id="87287-251">By default, this option is disabled.</span></span>

- <span data-ttu-id="87287-252">**NX_DHCP_THREAD_PRIORITY** Prioridade do fio DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-252">**NX_DHCP_THREAD_PRIORITY** Priority of the DHCP thread.</span></span> <span data-ttu-id="87287-253">Por predefinição, este valor especifica que o fio DHCP funciona na prioridade 3.</span><span class="sxs-lookup"><span data-stu-id="87287-253">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>

- <span data-ttu-id="87287-254">**NX_DHCP_THREAD_STACK_SIZE** Tamanho da pilha de fios DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-254">**NX_DHCP_THREAD_STACK_SIZE** Size of the DHCP thread stack.</span></span> <span data-ttu-id="87287-255">Por padrão, o tamanho é 2048 bytes.</span><span class="sxs-lookup"><span data-stu-id="87287-255">By default, the size is 2048 bytes.</span></span>

- <span data-ttu-id="87287-256">**NX_DHCP_TIME_INTERVAL** Intervalo em segundos quando a função de expiração do temporizador do cliente DHCP executa.</span><span class="sxs-lookup"><span data-stu-id="87287-256">**NX_DHCP_TIME_INTERVAL** Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="87287-257">Esta função atualiza todos os intervalos de tempo no processo DHCP, por exemplo, se as mensagens devem ser retransmitidas ou o estado do Cliente DHCP alterado.</span><span class="sxs-lookup"><span data-stu-id="87287-257">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="87287-258">Por padrão, este valor é de 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="87287-258">By default, this value is 1 second.</span></span>

- <span data-ttu-id="87287-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Tamanho do tampão de opções DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Size of DHCP options buffer.</span></span> <span data-ttu-id="87287-260">Por padrão, este valor é 312.</span><span class="sxs-lookup"><span data-stu-id="87287-260">By default, this value is 312.</span></span>

- <span data-ttu-id="87287-261">**NX_DHCP_PACKET_PAYLOAD** Especifica o tamanho dos bytes da carga útil do pacote do cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-261">**NX_DHCP_PACKET_PAYLOAD** Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="87287-262">O valor predefinido é NX_DHCP_MINIMUM_IP_DATAGRAM + tamanho do cabeçalho físico.</span><span class="sxs-lookup"><span data-stu-id="87287-262">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="87287-263">O tamanho do cabeçalho físico numa rede de fios é geralmente o tamanho da moldura Ethernet.</span><span class="sxs-lookup"><span data-stu-id="87287-263">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>

- <span data-ttu-id="87287-264">**NX_DHCP_PACKET_POOL_SIZE** Especifica o tamanho da piscina de pacotes do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-264">**NX_DHCP_PACKET_POOL_SIZE** Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="87287-265">O valor predefinido é (5\*NX_DHCP_PACKET_PAYLOAD) que fornecerá quatro pacotes mais espaço para a cobertura interna do pacote.</span><span class="sxs-lookup"><span data-stu-id="87287-265">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>

- <span data-ttu-id="87287-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Especifica a opção de espera mínima para receber uma resposta do Servidor DHCP à mensagem do cliente antes de retransmissão da mensagem.</span><span class="sxs-lookup"><span data-stu-id="87287-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="87287-267">O valor predefinido é o RFC 2131 recomendado 4 segundos.</span><span class="sxs-lookup"><span data-stu-id="87287-267">The default value is the RFC 2131 recommended 4 seconds.</span></span>

- <span data-ttu-id="87287-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Especifica a opção de espera máxima para receber uma resposta do Servidor DHCP à mensagem do cliente antes de retransmissão da mensagem.</span><span class="sxs-lookup"><span data-stu-id="87287-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="87287-269">O valor predefinido é o RFC 2131 recomendado 64 segundos.</span><span class="sxs-lookup"><span data-stu-id="87287-269">The default value is the RFC 2131 recommended 64 seconds.</span></span>

- <span data-ttu-id="87287-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Especifica a opção mínima de espera para receber uma mensagem do Servidor DHCP e enviar um pedido de renovação após o Cliente DHCP estar ligado a um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="87287-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="87287-271">O valor predefinido é de 60 segundos.</span><span class="sxs-lookup"><span data-stu-id="87287-271">The default value is 60 seconds.</span></span> <span data-ttu-id="87287-272">No entanto, o Cliente DHCP utiliza os tempos de validade de Renovação e Rebind a partir da mensagem do servidor DHCP antes de incumprimento ao tempo limite mínimo de renovação.</span><span class="sxs-lookup"><span data-stu-id="87287-272">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>

- <span data-ttu-id="87287-273">**NX_DHCP_TYPE_OF_SERVICE** Tipo de serviço necessário para os pedidos da DHCP UDP.</span><span class="sxs-lookup"><span data-stu-id="87287-273">**NX_DHCP_TYPE_OF_SERVICE** Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="87287-274">Por predefinição, este valor é definido como NX_IP_NORMAL para indicar o serviço normal de pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="87287-274">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="87287-275">**NX_DHCP_FRAGMENT_OPTION** Ativar fragmentos para pedidos de UDP DHCP.</span><span class="sxs-lookup"><span data-stu-id="87287-275">**NX_DHCP_FRAGMENT_OPTION** Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="87287-276">Por padrão, este valor é NX_DONT_FRAGMENT para desativar a fragmentação da DHCP UDP.</span><span class="sxs-lookup"><span data-stu-id="87287-276">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>

- <span data-ttu-id="87287-277">**NX_DHCP_TIME_TO_LIVE** Especifica o número de routers que este pacote pode passar antes de ser descartado.</span><span class="sxs-lookup"><span data-stu-id="87287-277">**NX_DHCP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="87287-278">O valor predefinido é definido para 0x80.</span><span class="sxs-lookup"><span data-stu-id="87287-278">The default value is set to 0x80.</span></span>

- <span data-ttu-id="87287-279">**NX_DHCP_QUEUE_DEPTH** Especifica o número de profundidade máxima da fila de receção.</span><span class="sxs-lookup"><span data-stu-id="87287-279">**NX_DHCP_QUEUE_DEPTH** Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="87287-280">O valor predefinido é definido para 4.</span><span class="sxs-lookup"><span data-stu-id="87287-280">The default value is set to 4.</span></span>
