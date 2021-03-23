---
title: Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a154dbeb91b46a2c8bd5f4585e168a6b62d042ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826095"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a><span data-ttu-id="534a0-103">Capítulo 2 - Instalação e utilização do Cliente Azure RTOS NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="534a0-104">Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização do componente cliente Azure RTOS NetX Duo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DHCPv6 Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="534a0-105">Distribuição de Produtos</span><span class="sxs-lookup"><span data-stu-id="534a0-105">Product Distribution</span></span>

<span data-ttu-id="534a0-106">O Cliente NetX Duo DHCPv6 está disponível em [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) .</span><span class="sxs-lookup"><span data-stu-id="534a0-106">NetX Duo DHCPv6 Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="534a0-107">O pacote inclui dois ficheiros de origem e um ficheiro PDF que contém este documento, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="534a0-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="534a0-108">**nxd_dhcpv6_client.h** Arquivo de cabeçalho para Cliente NetX DuoDHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-108">**nxd_dhcpv6_client.h** Header file for NetX DuoDHCPv6 Client</span></span>

- <span data-ttu-id="534a0-109">**nxd_dhcpv6_client.c** Ficheiro de código fonte para Cliente NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-109">**nxd_dhcpv6_client.c** Source code file for NetX Duo DHCPv6 Client</span></span>

- <span data-ttu-id="534a0-110">**demo_netxduo_dhcpv6_client.c** Programa de amostras que demonstra a configuração do Cliente DHCPv6 da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="534a0-110">**demo_netxduo_dhcpv6_client.c** Sample program demonstrating the setup of the NetX Duo DHCPv6 Client</span></span>

- <span data-ttu-id="534a0-111">**nxd_dhcpv6_client.pdf** Descrição em PDF do Cliente NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-111">**nxd_dhcpv6_client.pdf** PDF description of NetX Duo DHCPv6 Client</span></span>

## <a name="netx-duo-dhcpv6-client-installation"></a><span data-ttu-id="534a0-112">Instalação do cliente NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-112">NetX Duo DHCPv6 Client Installation</span></span>

<span data-ttu-id="534a0-113">Para utilizar a API do Cliente NetX Duo DHCPv6, toda a distribuição acima mencionada pode ser copiada para o mesmo diretório onde o NetX Duo está instalado.</span><span class="sxs-lookup"><span data-stu-id="534a0-113">To use NetX Duo DHCPv6 Client API, the entire distribution mentioned above can be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="534a0-114">Por exemplo, se o NetX Duo for instalado no diretório "*\threadx\arm7\green*" então os ficheiros *nxd_dhcpv6_client.h* e *nxd_dhpcv6_client.c* podem ser copiados para este diretório.</span><span class="sxs-lookup"><span data-stu-id="534a0-114">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcpv6_client.h* and *nxd_dhpcv6_client.c* files can be copied into this directory.</span></span>

## <a name="using-the-netx-duo-dhcpv6-client"></a><span data-ttu-id="534a0-115">Utilizando o Cliente NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="534a0-115">Using the NetX Duo DHCPv6 Client</span></span>

<span data-ttu-id="534a0-116">O código de aplicação deve incluir *nxd_dhcpv6_client.h* depois de incluir *tx_api.h* e *nx_api.h,* para utilizar os serviços DHCPv6 Client, ThreadX e NetX Duo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="534a0-116">The application code must include *nxd_dhcpv6_client.h* after it includes *tx_api.h* and *nx_api.h*, to use DHCPv6 Client, ThreadX and NetX Duo services, respectively.</span></span> <span data-ttu-id="534a0-117">*nxd_dhcpv6_client.c* deve ser compilado no projeto da mesma forma que outros ficheiros de aplicações e a sua forma de objeto deve ser ligada juntamente com os ficheiros da aplicação.</span><span class="sxs-lookup"><span data-stu-id="534a0-117">*nxd_dhcpv6_client.c* must be compiled in the project in the same manner as other application files and its object form must be linked along with the files of the application.</span></span>

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span data-ttu-id="534a0-118"><span class="underline">Identificador Exclusivo DHCP do Cliente (DUID)</span></span><span class="sxs-lookup"><span data-stu-id="534a0-118"><span class="underline">Client DHCP Unique Identifier (DUID)</span></span></span>

<span data-ttu-id="534a0-119">O Cliente DUID define exclusivamente cada Cliente numa rede.</span><span class="sxs-lookup"><span data-stu-id="534a0-119">The Client DUID uniquely defines each Client on a network.</span></span> <span data-ttu-id="534a0-120">Uma aplicação deve criar um DuID do Cliente antes de solicitar um endereço IPv6 a partir de um Servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-120">An application must create a Client DUID prior to requesting an IPv6 address from a Server.</span></span> <span data-ttu-id="534a0-121">O DuID do Cliente é automaticamente incluído em todas as mensagens para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-121">The Client DUID is automatically included in all messages to the Server.</span></span> <span data-ttu-id="534a0-122">Para criar um DUID, a aplicação chama o serviço *nx_dhcpv6_create_client_duid:*</span><span class="sxs-lookup"><span data-stu-id="534a0-122">To create a DUID, the application calls the service *nx_dhcpv6_create_client_duid:*</span></span>
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

<span data-ttu-id="534a0-123">A aplicação chama este serviço e especifica o tipo de DUID (apenas camada de ligação, ou camada de ligação mais tempo.</span><span class="sxs-lookup"><span data-stu-id="534a0-123">The application calls this service and specifies the type of DUID (link layer only, or link layer plus time.</span></span> <span data-ttu-id="534a0-124">Para a camada de ligação mais os DUIDs de tempo, este serviço fornecerá o campo de tempo se a entrada de tempo não for especificada.</span><span class="sxs-lookup"><span data-stu-id="534a0-124">For link layer plus time DUIDs, this service will provide the time field if the time input is not specified.</span></span>

<span data-ttu-id="534a0-125">Para dispositivos reiniciando e desejando utilizar uma locação de endereços IPv6 previamente atribuída, a aplicação deve criar o DuID do Cliente como o que utilizou quando lhe foi atribuído o endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-125">For devices rebooting and wishing to use a previously assigned IPv6 address lease, the application must create the Client DUID as the one it used when assigned the IPv6 address.</span></span> <span data-ttu-id="534a0-126">O endereço da camada de ligação é tudo o que é necessário para criar uma camada de ligação Cliente DUID.</span><span class="sxs-lookup"><span data-stu-id="534a0-126">The link layer address is all that is needed to create a link layer Client DUID.</span></span> <span data-ttu-id="534a0-127">Isto não requer armazenamento de memória não volátil anterior se o dispositivo tiver acesso ao endereço da camada de ligação.</span><span class="sxs-lookup"><span data-stu-id="534a0-127">This does not require previous non volatile memory storage if the device has access to the link layer address.</span></span> <span data-ttu-id="534a0-128">Para os DUIDs do tipo de tempo, a aplicação deve ter acesso aos mesmos dados de tempo utilizados na criação duid anterior e isso requer memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="534a0-128">For DUIDs of type time, the application must have access to the same time data used in the previous DUID creation and this does require non volatile memory.</span></span> <span data-ttu-id="534a0-129">Os clientes que não tenham qualquer armazenamento estável não devem utilizar DUIDs de tempo tipo.</span><span class="sxs-lookup"><span data-stu-id="534a0-129">Clients that do not have any stable storage must not use DUIDs of type time.</span></span>

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span data-ttu-id="534a0-130"><span class="underline">Associação de Identidade de Cliente para Endereços Não Temporários (IANA)</span></span><span class="sxs-lookup"><span data-stu-id="534a0-130"><span class="underline">Client Identity Association for Non Temporary Addresses (IANA)</span></span></span>

<span data-ttu-id="534a0-131">O pedido deve criar um IANA e opcionalmente um ou mais endereços IA antes de solicitar um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-131">The application must create an IANA and optionally one or more IA addresses before requesting an IPv6 address.</span></span> <span data-ttu-id="534a0-132">Para tal, a aplicação chama o *serviço nx_dhcpv6_create_client_iana.*</span><span class="sxs-lookup"><span data-stu-id="534a0-132">To do so, the application calls the *nx_dhcpv6_create_client_iana* service.</span></span> <span data-ttu-id="534a0-133">Para criar uma opção de endereço IA, a aplicação liga para o serviço *nx_dhcpv6_add_client_ia* com um endereço IPv6 solicitado e valores de vida como uma dica para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-133">To create an IA address option, the application calls the *nx_dhcpv6_add_client_ia* service with a requested IPv6 address and lifetime values as a hint to the Server.</span></span>

<span data-ttu-id="534a0-134">O IANA e os seus IAs definem cumulativamente os parâmetros de atribuição de endereços do Cliente IPv6:</span><span class="sxs-lookup"><span data-stu-id="534a0-134">The IANA and its IAs cumulatively define the Client IPv6 address assignment parameters:</span></span>

<span data-ttu-id="534a0-135">Antes de iniciar o Cliente DHCPv6, a aplicação DHCPv6 Client cria um IANA utilizando o serviço *nx_dhcpv6_create_client_iana:*</span><span class="sxs-lookup"><span data-stu-id="534a0-135">Before starting the DHCPv6 Client, the DHCPv6 Client application creates an IANA using the *nx_dhcpv6_create_client_iana* service:</span></span>

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

<span data-ttu-id="534a0-136">Deve também criar um ou mais IAs utilizando o serviço *de nx_dhcpv6_create_client_ia* e solicitou endereços IPv6 antes de iniciar o DhCPv6 Client.</span><span class="sxs-lookup"><span data-stu-id="534a0-136">It must also create one or more IAs using the *nx_dhcpv6_create_client_ia* service and requested IPv6 addresses before starting the DHCPv6 Client.</span></span>

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> <span data-ttu-id="534a0-137">O número de endereços IA que a aplicação cria não pode exceder o parâmetro NX_DHCPV6_MAX_IA_ADDRESS cujo valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="534a0-137">The number of IA addresses the application creates cannot exceed the NX_DHCPV6_MAX_IA_ADDRESS parameter whose default value is 1.</span></span>

<span data-ttu-id="534a0-138">O Cliente NetX Duo DHCPv6 suporta *nx_dhcpv6_create_client_ia* para aplicações de clientes DHCPv6 legados e que é idêntica a *nx_dhcpv6_add_client_ia* mas os desenvolvedores são encorajados a usar o serviço *nx_dhcpv6_add_client_ia.*</span><span class="sxs-lookup"><span data-stu-id="534a0-138">The NetX Duo DHCPv6 Client supports *nx_dhcpv6_create_client_ia* for legacy DHCPv6 Client applications and which is identical to *nx_dhcpv6_add_client_ia* but developers are encouraged to use the *nx_dhcpv6_add_client_ia* service.</span></span>

<span data-ttu-id="534a0-139">Estes serviços são demonstrados no "Small Example System" noutros capítulos.</span><span class="sxs-lookup"><span data-stu-id="534a0-139">These services are demonstrated in the “Small Example System” elsewhere in this chapter.</span></span>

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span data-ttu-id="534a0-140"><span class="underline">Considerações de memória não voláteis para reutilizar IANAs e AI</span></span><span class="sxs-lookup"><span data-stu-id="534a0-140"><span class="underline">Non Volatile Memory Considerations To Reuse IANAs and IAs</span></span></span>

<span data-ttu-id="534a0-141">A aplicação deve guardar os parâmetros IANA T1, T2 e o identificador IANA para memória não volátil se pretender utilizar o mesmo endereço(es) no reinício.</span><span class="sxs-lookup"><span data-stu-id="534a0-141">The application must save IANA parameters T1, T2, and the IANA identifier to non volatile memory if it wishes to use the same address(es) on rebooting.</span></span> <span data-ttu-id="534a0-142">A aplicação também deve guardar o seu IA, que inclui o seu endereço IPv6 para memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="534a0-142">The application must also save its IA which includes its IPv6 address to non volatile memory.</span></span>

<span data-ttu-id="534a0-143">A aplicação também deve armazenar o tempo decorrido que foi vinculado ao seu(s) designado(s) de endereço iPv6 para memória não volátil se desligar.</span><span class="sxs-lookup"><span data-stu-id="534a0-143">The application must also store the time elapsed that it has been bound to its assigned IPv6 address lease(s) to non volatile memory if shutting down.</span></span> <span data-ttu-id="534a0-144">Fá-lo chamando o serviço *de nx_dhcpv6_get_time_accrued* antes de parar o Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-144">It does this by calling the *nx_dhcpv6_get_time_accrued* service before it stops the DHCPv6 Client.</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

<span data-ttu-id="534a0-145">Assumindo que a aplicação tem um relógio independente para acompanhar o intervalo de tempo desde que parou e reiniciou o Cliente DHCPv6 após um reboot, acrescenta-se a esse tempo decorrido até ao tempo acumulado no contrato de arrendamento IPv6 antes de parar.</span><span class="sxs-lookup"><span data-stu-id="534a0-145">Assuming the application has an independent clock to track the time interval from when it stopped and restarted the DHCPv6 Client after a reboot, it adds to that elapsed time to the time accrued on the IPv6 lease before stopping.</span></span> <span data-ttu-id="534a0-146">Inicia agora a tarefa de thread do Cliente com o tempo total decorrido ligado ao arrendamento IPv6 como a entrada nv_time abaixo:</span><span class="sxs-lookup"><span data-stu-id="534a0-146">It now starts the Client thread task with the total elapsed time bound to the IPv6 lease as the nv_time input below:</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

<span data-ttu-id="534a0-147">A partir deste ponto, a tarefa de thread do Cliente DHCPv6 assumirá a monitorização do tempo acumulado no contrato de arrendamento IPv6 para quando renovar o contrato de arrendamento.</span><span class="sxs-lookup"><span data-stu-id="534a0-147">From this point, the DHCPv6 Client thread task will take over monitoring the time accrued on the IPv6 lease for when to renew the lease.</span></span>

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span data-ttu-id="534a0-148"><span class="underline">Definição de dados de opção DHCPv6</span></span><span class="sxs-lookup"><span data-stu-id="534a0-148"><span class="underline">Setting DHCPv6 Option Data</span></span></span>

<span data-ttu-id="534a0-149">Antes de solicitar uma locação IPv6, a aplicação pode solicitar outros dados de parâmetros de rede, como servidor DNS e servidor de tempo.</span><span class="sxs-lookup"><span data-stu-id="534a0-149">Before requesting an IPv6 lease, the application can request other network parameter data such as DNS server and time server.</span></span> <span data-ttu-id="534a0-150">Alguns destes parâmetros têm serviços específicos.</span><span class="sxs-lookup"><span data-stu-id="534a0-150">Some of these parameters have specific services.</span></span> <span data-ttu-id="534a0-151">Alguns são mostrados abaixo:</span><span class="sxs-lookup"><span data-stu-id="534a0-151">A few are shown below:</span></span>

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span data-ttu-id="534a0-152"><span class="underline">Início do Pedido de Endereço IPv6</span></span><span class="sxs-lookup"><span data-stu-id="534a0-152"><span class="underline">Initiating the IPv6 address Request</span></span></span>

<span data-ttu-id="534a0-153">A aplicação inicia a linha do Cliente DHCPv6 ligando para o serviço *nx_dhcpv6_start* com uma entrada de tempo zero.</span><span class="sxs-lookup"><span data-stu-id="534a0-153">The application starts the DHCPv6 Client thread by calling the *nx_dhcpv6_start* service with a zero time input.</span></span> <span data-ttu-id="534a0-154">Para iniciar o protocolo DHCPv6 para solicitar um endereço IPv6, a aplicação chama *nx_dhcpv6_request_solicit.*</span><span class="sxs-lookup"><span data-stu-id="534a0-154">To initiate the DHCPv6 protocol to request an IPv6 address, the application calls *nx_dhcpv6_request_solicit.*</span></span>

<span data-ttu-id="534a0-155">Se a aplicação pretender utilizar uma locação IPv6 previamente atribuída, chama *nx_dhcpv6_start* com uma entrada de tempo não zero.</span><span class="sxs-lookup"><span data-stu-id="534a0-155">If the application wishes to use a previously assigned IPv6 lease assigned, it calls *nx_dhcpv6_start* with a non zero time input.</span></span> <span data-ttu-id="534a0-156">Não deve chamar *nx_dhcpv6_request_solicit.*</span><span class="sxs-lookup"><span data-stu-id="534a0-156">It should not call *nx_dhcpv6_request_solicit*.</span></span>

<span data-ttu-id="534a0-157">A partir daí, a aplicação não precisa de fazer mais nada e o Cliente DHCPv6 monitorizará automaticamente quando for a hora de renovar ou reencambir um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-157">Thereafter the application need do nothing more and the DHCPv6 Client will automatically monitor when it is time to renew or rebind an IPv6 address.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="534a0-158">Sistema de Pequenos Exemplos</span><span class="sxs-lookup"><span data-stu-id="534a0-158">Small Example System</span></span>

<span data-ttu-id="534a0-159">Um exemplo de como é fácil utilizar o Cliente DHCPv6 da NetX Duo é descrito no pequeno exemplo abaixo usando um Cliente DHCPv6 e um controlador virtual "RAM".</span><span class="sxs-lookup"><span data-stu-id="534a0-159">An example of how easy it is to use the NetX Duo DHCPv6 Client is described in the small example below using a DHCPv6 Client and a virtual “RAM” driver.</span></span> <span data-ttu-id="534a0-160">Esta demonstração pressupõe um dispositivo com apenas uma interface física de rede.</span><span class="sxs-lookup"><span data-stu-id="534a0-160">This demo assumes a device with only a single physical network interface.</span></span>

<span data-ttu-id="534a0-161">*tx_application_define* cria pacotes para o Cliente DHCPv6 enviar mensagens DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-161">*tx_application_define* creates packet pool for the DHCPv6 Client to send DHCPv6 messages.</span></span> <span data-ttu-id="534a0-162">Também cria um fio de aplicação e instância IP.</span><span class="sxs-lookup"><span data-stu-id="534a0-162">It also creates an application thread and IP instance.</span></span> <span data-ttu-id="534a0-163">Em seguida, permite que uDP e ICMP em IP nas linhas 130-148.</span><span class="sxs-lookup"><span data-stu-id="534a0-163">It then enables UDP and ICMP on IP in lines 130-148.</span></span> <span data-ttu-id="534a0-164">Em seguida, o Cliente DHCPv6 é criado com alterações de estado *(dhcpv6_state_change_notify)* e funções de retorno do servidor *(dhcpv6_server_error_handler)* na linha151.</span><span class="sxs-lookup"><span data-stu-id="534a0-164">Then the DHCPv6 Client is created with state change (*dhcpv6_state_change_notify* ) and server error (*dhcpv6_server_error_handler*) callback functions in line151.</span></span>

<span data-ttu-id="534a0-165">Na função de entrada de thread cliente, *thread_client_entry,* o Computador IP é configurado com um endereço local de ligação e habilitado para os serviços IPv6 e ICMPv6 nas linhas 202-217.</span><span class="sxs-lookup"><span data-stu-id="534a0-165">In the Client thread entry function, *thread_client_entry*, the Client IP is set up with a link local address and enabled for IPv6 and ICMPv6 services on lines 202-217.</span></span> <span data-ttu-id="534a0-166">Antes de iniciar o DhCPv6 Client, a aplicação cria um DuID do Cliente, uma opção IANA e uma opção de endereço IA nas linhas219-303.</span><span class="sxs-lookup"><span data-stu-id="534a0-166">Before starting the DHCPv6 Client, the application creates a Client DUID, an IANA option and an IA address option on lines219-303.</span></span> <span data-ttu-id="534a0-167">A opção de endereço IA é opcional se o Cliente pretender solicitar um endereço IPv6 e uma vida útil válida e preferida a partir do Servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-167">The IA address option is optional if the Client wishes to request an IPv6 address and valid and preferred lifetimes from the Server.</span></span> <span data-ttu-id="534a0-168">O Servidor pode ou não conceder o endereço IPv6 solicitado ou os tempos de locação.</span><span class="sxs-lookup"><span data-stu-id="534a0-168">The Server may or may not grant the requested IPv6 address or lease times.</span></span> <span data-ttu-id="534a0-169">A aplicação pode adicionar mais opções de IA (até NX_DHCPV6_MAX_IA_ADDRESS) para ser atribuído vários endereços globais.</span><span class="sxs-lookup"><span data-stu-id="534a0-169">The application may add more IA options (up to NX_DHCPV6_MAX_IA_ADDRESS) to be assigned multiple global addresses.</span></span>

<span data-ttu-id="534a0-170">Por último, a aplicação define várias opções para solicitar parâmetros de rede nas suas mensagens para o Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-170">Lastly, the application sets various options to request network parameters in its messages to the DHCPv6 Server.</span></span> <span data-ttu-id="534a0-171">A tarefa do Cliente DHCPv6 é iniciada por chamar *nx_dhcpv6_start* na linha 306, e o protocolo DHCPv6 real é iniciado no estado SOLICIT com a chamada para *nx_dhcpv6_request_solicit* na linha 317.</span><span class="sxs-lookup"><span data-stu-id="534a0-171">The DHCPv6 Client task is started by calling *nx_dhcpv6_start* in line306, and the actual DHCPv6 protocol is started in the SOLICIT state with the call to *nx_dhcpv6_request_solicit* in line 317.</span></span> <span data-ttu-id="534a0-172">O Cliente DHCPv6 lida automaticamente com a promoção do Estado cliente através do protocolo DHCPv6 até que esteja ligado a um endereço ou ocorra um erro.</span><span class="sxs-lookup"><span data-stu-id="534a0-172">The DHCPv6 Client then automatically handles the promotion of the Client state through the DHCPv6 protocol until it is bound to an address or an error occurs.</span></span> <span data-ttu-id="534a0-173">Durante este período, a aplicação aguarda a conclusão do protocolo, bem como a Duplicado Deteção de Endereços (DAD) para concluir se a instância IP estiver configurada para o PAI (que é a configuração padrão).</span><span class="sxs-lookup"><span data-stu-id="534a0-173">During this time, the application waits for the protocol to complete, as well as the Duplicate Address Detection (DAD) to complete if the IP instance is configured for DAD (which is the default configuration).</span></span>

<span data-ttu-id="534a0-174">Após a chamada tx_thread_sleep, a aplicação verifica os parâmetros globais definidos na chamada de alteração do estado para determinar o sucesso da tarefa do Cliente DHCPv6 para obter um contrato de arrendamento IPv6 e, em caso afirmativo, que o PAI verifica a singularidade conseguiu.</span><span class="sxs-lookup"><span data-stu-id="534a0-174">After the tx_thread_sleep call, the application checks on the global parameters set in the state change callback to determine the success of both the DHCPv6 Client task to get assigned an IPv6 lease and if so, that the DAD check for uniqueness succeeded.</span></span> <span data-ttu-id="534a0-175">Isto é feito usando os contadores configurados nas funções de alteração de estado e de chamada de erro do servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-175">This is done using the counters set up in the state change and server error callback functions.</span></span> <span data-ttu-id="534a0-176">As sondagens para não zero contagens de address_not_assigned, address_expired e server_errors para atribuição de moradas falhadas.</span><span class="sxs-lookup"><span data-stu-id="534a0-176">The application polls for non zero counts of address_not_assigned, address_expired and server_errors for failed address assignment.</span></span> <span data-ttu-id="534a0-177">Se a contagem de bound_addresses não for zero (pelo menos um endereço atribuído com sucesso), verifica se um address_failed_dad não zero para uma verificação de PAI falhada.</span><span class="sxs-lookup"><span data-stu-id="534a0-177">If the count of bound_addresses is non zero (at least one address successfully assigned), it checks for a non zero address_failed_dad for a failed DAD check.</span></span> <span data-ttu-id="534a0-178">Segue-se uma explicação sobre a alteração do estado e as chamadas de erro do servidor:</span><span class="sxs-lookup"><span data-stu-id="534a0-178">An explanation of the state change and server error callbacks follows:</span></span>

<span data-ttu-id="534a0-179">A chamada de alteração do estado, *dhcpv6_state_change_notify,* o estado anterior e atual do Cliente DHCPv6 para determinar se o Cliente recebeu alguma resposta válida do Servidor:</span><span class="sxs-lookup"><span data-stu-id="534a0-179">The state change callback, *dhcpv6_state_change_notify*, the previous and current DHCPv6 Client state to determine if the Client received any valid Server responses:</span></span>

  - <span data-ttu-id="534a0-180">*dhcpv6_state_change_notify* verifica as transições diretamente do SOLICIT para o INIT e, em caso afirmativo, incrementa um contador para o Cliente DHCPv6 não receber respostas do Servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-180">*dhcpv6_state_change_notify* checks for transitions directly from SOLICIT to INIT and if so it increments a counter for the DHCPv6 Client receiving no responses from the Server.</span></span>

<span data-ttu-id="534a0-181">A *dhcpv6_state_change_notify* verifica se o Cliente foi designado (ligado) a um ou mais endereços IPv6:</span><span class="sxs-lookup"><span data-stu-id="534a0-181">Next *dhcpv6_state_change_notify* checks if the Client was assigned (bound) to one or more IPv6 addresses:</span></span>

  - <span data-ttu-id="534a0-182">Se o estado novo for BOUND, incrementa um contador de endereços ligados ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="534a0-182">If the new state is BOUND, it increments a counter of addresses bound to the Client.</span></span>
    
<span data-ttu-id="534a0-183">O *dhcpv6_state_change_notify* também verifica um cheque de pai falhado:</span><span class="sxs-lookup"><span data-stu-id="534a0-183">The *dhcpv6_state_change_notify* also checks for a failed DAD check:</span></span>

  - <span data-ttu-id="534a0-184">Se o Estado transitar de DECLÍNIO para INIT, o Cliente DHCPv6 falhou na verificação do PAI num dos seus endereços atribuídos e incrementa a contagem de atribuições de endereços falhadas.</span><span class="sxs-lookup"><span data-stu-id="534a0-184">If the state transitions from DECLINE to INIT, the DHCPv6 Client has failed DAD check on one of its assigned addresses and increments the count of failed address assignments.</span></span>
    
<span data-ttu-id="534a0-185">A última verificação por *dhcpv6_state_change_notify* neste exemplo é para um endereço bem-designado que passou o cheque do PAI para não ser renovado ou reencambido:</span><span class="sxs-lookup"><span data-stu-id="534a0-185">The last check by *dhcpv6_state_change_notify* in this example is for a successfully assigned address that passed the DAD check to fail to be renewed or rebind:</span></span>

  - <span data-ttu-id="534a0-186">Se o estado mudar de REBIND para INIT, o Cliente não obtém qualquer resposta aos seus pedidos DE RENOVAÇÃO ou REBIND e *dhcpv6_state_change_notify* incrementa a sua contagem de endereços caducados.</span><span class="sxs-lookup"><span data-stu-id="534a0-186">If the state changes from REBIND to INIT, the Client did not get any responses to either its RENEW or REBIND requests and *dhcpv6_state_change_notify* increments its count of expired addresses.</span></span>

<span data-ttu-id="534a0-187">O *dhcpv6_server_error_handler* se notificado pela tarefa do Cliente DHCPv6 de um estado de erro recebido do Servidor incrementa a contagem de erros do servidor.</span><span class="sxs-lookup"><span data-stu-id="534a0-187">The *dhcpv6_server_error_handler* if notified by the DHCPv6 Client task of an error status received from the Server increments the count of server errors.</span></span>

<span data-ttu-id="534a0-188">Assumindo que tudo corre bem, a aplicação consulta o Cliente DHCPv6 para dados de endereço, incluindo tempos de locação.</span><span class="sxs-lookup"><span data-stu-id="534a0-188">Assuming all goes well, the application queries the DHCPv6 Client for address data including lease times.</span></span> <span data-ttu-id="534a0-189">Obtém uma contagem de endereços válidos (atribuídos com sucesso) ligando para o serviço *nx_dhcpv6_get_valid_ip_address_count* e tempo para renovar no IANA (aplica-se a todos os endereços da IA atribuídos) ligando para *nx_dhcpv6_get_iana_lease_time* nas linhas 372-392.</span><span class="sxs-lookup"><span data-stu-id="534a0-189">It gets a count of valid (successfully assigned) addresses by calling the *nx_dhcpv6_get_valid_ip_address_count* service and time to renew in the IANA (applies to all IA addresses assigned) by calling *nx_dhcpv6_get_iana_lease_time* on lines 372-392.</span></span> <span data-ttu-id="534a0-190">Em seguida, consulta o Cliente DHCPv6 por cada uma das suas opções de IA para endereço iPv6 e tempos de locação por índice de endereço.</span><span class="sxs-lookup"><span data-stu-id="534a0-190">It then queries the DHCPv6 Client for each of its IA options for IPv6 address and lease times by address index.</span></span>

<span data-ttu-id="534a0-191">Alguns serviços de clientes DHCPv6 *(nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address)* não requerem um índice de endereço como entrada e devolvem os parâmetros DHCPv6 para o endereço global do Cliente primário.</span><span class="sxs-lookup"><span data-stu-id="534a0-191">Some DHCPv6 Client services (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) do not require an address index as an input, and return DHCPv6 parameters for the primary Client global address.</span></span> <span data-ttu-id="534a0-192">Isto é adequado para Clientes com um único endereço IPv6 global quando chama *nx_dhcpv6_get_valid_ip_address_lease_time* na linha 384.</span><span class="sxs-lookup"><span data-stu-id="534a0-192">This is suitable for Clients with a single global IPv6 address when it calls *nx_dhcpv6_get_valid_ip_address_lease_time* in line 384.</span></span>

<span data-ttu-id="534a0-193">A configuração do Cliente DHCPv6, NX_DHCPV6_CLIENT_RESTORE_STATE, permite que um sistema restabeleça um Cliente DHCPv6 anteriormente criado em estado vinculado entre reboots de sistema.</span><span class="sxs-lookup"><span data-stu-id="534a0-193">The DHCPv6 Client configuration, NX_DHCPV6_CLIENT_RESTORE_STATE, t allows a system to restore a previously created DHCPv6 Client in Bound state between system reboots.</span></span> <span data-ttu-id="534a0-194">Ligar para o *nx_dhcpv6_client_get_record* para obter o registo do Cliente DHCPv6 entre reinicializações de sistema na linha 434, chamando a *nx_dhcpv6_client_restore_record* para armazenar o registo do Cliente DHCPv6 após a ligação do sistema na linha 525.</span><span class="sxs-lookup"><span data-stu-id="534a0-194">Calling the *nx_dhcpv6_client_get_record* to get the DHCPv6 Client record between system reboots on line 434, calling the *nx_dhcpv6_client_restore_record* to store the DHCPv6 Client record after system power up on line 525.</span></span>

<span data-ttu-id="534a0-195">A aplicação lança então os endereços atribuídos utilizando o serviço *nx_dhcpv6_request_release* na linha 552.</span><span class="sxs-lookup"><span data-stu-id="534a0-195">The application then releases the assigned addresses using the *nx_dhcpv6_request_release* service in line 552.</span></span> <span data-ttu-id="534a0-196">Para reiniciar a aplicação para o Cliente DHCPv6 com o serviço *nx_dhcpv6_client_stop* na linha 567 e limpa todos os endereços IPv6 registados com a instância IP que foram configurados através do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="534a0-196">To restart the application stops the DHCPv6 Client with the *nx_dhcpv6_client_stop* service in line 567 and clears all IPv6 addresses registered with the IP instance that were configured throughthe DHCPv6 Client.</span></span> <span data-ttu-id="534a0-197">Fá-lo chamando *nx_dhcpv6_reinitialize* na linha 578.</span><span class="sxs-lookup"><span data-stu-id="534a0-197">It does this by calling *nx_dhcpv6_reinitialize* in line 578.</span></span> <span data-ttu-id="534a0-198">Em seguida, reinicia a tarefa do Cliente DHCPv6 com serviços *de nx_dhcpv6_start* e *nx_dhcpv6_request_solicit* como antes.</span><span class="sxs-lookup"><span data-stu-id="534a0-198">Then it restarts the DHCPv6 Client task with *nx_dhcpv6_start* and *nx_dhcpv6_request_solicit* services as before.</span></span>

<span data-ttu-id="534a0-199">O Cliente DHCPv6 é apagado com a chamada para *nx_dhcpv6_delete* na linha626.</span><span class="sxs-lookup"><span data-stu-id="534a0-199">The DHCPv6 Client is deleted with the call to *nx_dhcpv6_delete* in line626.</span></span> <span data-ttu-id="534a0-200">Note que não apaga a piscina de *pacotes e* th que criou para o Cliente DHCPv6 porque este pacote de piscina também é usado pela instância IP.</span><span class="sxs-lookup"><span data-stu-id="534a0-200">Note that it does not delete th *e* packet pool it created for the DHCPv6 Client because this packet pool is also used by the IP instance.</span></span> <span data-ttu-id="534a0-201">Caso contrário, deverá eliminar a piscina de pacotes se não tiver mais utilidade para o mesmo utilizando o serviço NetX Duo *nx_packet_pool_delete.*</span><span class="sxs-lookup"><span data-stu-id="534a0-201">Otherwise it should delete the packet pool if it has no further use for it using the NetX Duo *nx_packet_pool_delete* service.</span></span>

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
