---
title: Capítulo 1 - Introdução ao Cliente Azure RTOS NetX DHCP
description: No NetX, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço nx_ip_create.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 44eb764c84a15a1bc96cf94bcbc8f81be7b41eef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826804"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="c649a-103">Capítulo 1 - Introdução ao Cliente Azure RTOS NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-103">Chapter 1 - Introduction to Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="c649a-104">No NetX, o endereço IP da aplicação é um dos parâmetros fornecidos para a chamada de serviço *nx_ip_create.*</span><span class="sxs-lookup"><span data-stu-id="c649a-104">In NetX, the application’s IP address is one of the supplied parameters to the *nx_ip_create* service call.</span></span> <span data-ttu-id="c649a-105">O fornecimento do endereço IP não levanta qualquer problema se o endereço IP for conhecido da aplicação, quer estática quer através da configuração do utilizador.</span><span class="sxs-lookup"><span data-stu-id="c649a-105">Supplying the IP address poses no problem if the IP address is known to the application, either statically or through user configuration.</span></span> <span data-ttu-id="c649a-106">No entanto, existem alguns casos em que a aplicação não sabe ou se importa com o seu endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c649a-106">However, there are some instances where the application doesn’t know or care what its IP address is.</span></span> <span data-ttu-id="c649a-107">Nestas situações, deve ser fornecido um endereço IP zero à função *nx_ip_create* e o protocolo do Cliente Azure RTOS DHCP deve ser utilizado para obter dinamicamente um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c649a-107">In such situations, a zero IP address should be supplied to the *nx_ip_create* function and the Azure RTOS DHCP Client protocol should be used to dynamically obtain an IP address.</span></span>

## <a name="dynamic-ip-address-assignment"></a><span data-ttu-id="c649a-108">Atribuição dinâmica de endereços IP</span><span class="sxs-lookup"><span data-stu-id="c649a-108">Dynamic IP Address Assignment</span></span>

<span data-ttu-id="c649a-109">O serviço básico utilizado para obter um endereço IP dinâmico da rede é o Protocolo de Resolução de Endereços Reversos (RARP).</span><span class="sxs-lookup"><span data-stu-id="c649a-109">The basic service used to obtain a dynamic IP address from the network is the Reverse Address Resolution Protocol (RARP).</span></span> <span data-ttu-id="c649a-110">Este protocolo é semelhante ao ARP, exceto que foi concebido para obter um endereço IP para si mesmo em vez de encontrar o endereço MAC para outro nó de rede.</span><span class="sxs-lookup"><span data-stu-id="c649a-110">This protocol is similar to ARP, except it is designed to obtain an IP address for itself instead of finding the MAC address for another network node.</span></span> <span data-ttu-id="c649a-111">A mensagem RARP de baixo nível é transmitida na rede local e é da responsabilidade de um servidor na rede responder com uma resposta RARP, que contém um endereço IP atribuído dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="c649a-111">The low-level RARP message is broadcast on the local network and it is the responsibility of a server on the network to respond with an RARP response, which contains a dynamically allocated IP address.</span></span>

<span data-ttu-id="c649a-112">Embora a RARP ofereça um serviço de alocação dinâmica de endereços IP, tem várias deficiências.</span><span class="sxs-lookup"><span data-stu-id="c649a-112">Although RARP provides a service for dynamic allocation of IP addresses, it has several shortcomings.</span></span> <span data-ttu-id="c649a-113">A deficiência mais gritante é que o RARP apenas fornece uma atribuição dinâmica do endereço IP.</span><span class="sxs-lookup"><span data-stu-id="c649a-113">The most glaring deficiency is that RARP only provides dynamic allocation of the IP address.</span></span> <span data-ttu-id="c649a-114">Na maioria das situações, é necessária mais informação para que um dispositivo participe adequadamente numa rede.</span><span class="sxs-lookup"><span data-stu-id="c649a-114">In most situations, more information is necessary in order for a device to properly participate on a network.</span></span> <span data-ttu-id="c649a-115">Além de um endereço IP, a maioria dos dispositivos precisa da máscara de rede e do endereço IP gateway.</span><span class="sxs-lookup"><span data-stu-id="c649a-115">In addition to an IP address, most devices need the network mask and the gateway IP address.</span></span> <span data-ttu-id="c649a-116">O endereço IP de um servidor DNS e outras informações de rede também podem ser necessários.</span><span class="sxs-lookup"><span data-stu-id="c649a-116">The IP address of a DNS server and other network information may also be needed.</span></span> <span data-ttu-id="c649a-117">A RARP não tem a capacidade de fornecer esta informação.</span><span class="sxs-lookup"><span data-stu-id="c649a-117">RARP does not have the ability to provide this information.</span></span>

## <a name="rarp-alternatives"></a><span data-ttu-id="c649a-118">Alternativas RARP</span><span class="sxs-lookup"><span data-stu-id="c649a-118">RARP Alternatives</span></span>

<span data-ttu-id="c649a-119">Para superar as deficiências da RARP, os investigadores desenvolveram um mecanismo de atribuição de endereços IP mais abrangente chamado Protocolo de Bootstrap (BOOTP).</span><span class="sxs-lookup"><span data-stu-id="c649a-119">In order to overcome the deficiencies of RARP, researchers developed a more comprehensive IP address allocation mechanism called the Bootstrap Protocol (BOOTP).</span></span> <span data-ttu-id="c649a-120">Este protocolo tem a capacidade de alocar dinamicamente um endereço IP e também fornecer informações adicionais importantes de rede.</span><span class="sxs-lookup"><span data-stu-id="c649a-120">This protocol has the ability to dynamically allocate an IP address and also provide additional important network information.</span></span> <span data-ttu-id="c649a-121">No entanto, o BOOTP tem a desvantagem de ser projetado para configurações de rede estática.</span><span class="sxs-lookup"><span data-stu-id="c649a-121">However, BOOTP has the drawback of being designed for static network configurations.</span></span> <span data-ttu-id="c649a-122">Não permite uma atribuição rápida ou automatizada de endereços.</span><span class="sxs-lookup"><span data-stu-id="c649a-122">It does not allow for quick or automated address assignment.</span></span>

<span data-ttu-id="c649a-123">É aqui que o Protocolo de Configuração do Anfitrião Dinâmico (DHCP) é extremamente útil.</span><span class="sxs-lookup"><span data-stu-id="c649a-123">This is where the Dynamic Host Configuration Protocol (DHCP) is extremely useful.</span></span> <span data-ttu-id="c649a-124">O DHCP foi concebido para alargar a funcionalidade básica do BOOTP para incluir a atribuição de servidores IP completamente automatizados e alocação de endereços IP completamente dinâmicos através da "locação" de um endereço IP a um cliente por um período de tempo especificado.</span><span class="sxs-lookup"><span data-stu-id="c649a-124">DHCP is designed to extend the basic functionality of BOOTP to include completely automated IP server allocation and completely dynamic IP address allocation through “leasing” an IP address to a client for a specified period of time.</span></span> <span data-ttu-id="c649a-125">O DHCP também pode ser configurado para alocar endereços IP de forma estática como o BOOTP.</span><span class="sxs-lookup"><span data-stu-id="c649a-125">DHCP can also be configured to allocate IP addresses in a static manner like BOOTP.</span></span>

## <a name="dhcp-messages"></a><span data-ttu-id="c649a-126">Mensagens DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-126">DHCP Messages</span></span>

<span data-ttu-id="c649a-127">Embora o DHCP melhore consideravelmente a funcionalidade do BOOTP, o DHCP utiliza o mesmo formato de mensagem que o BOOTP e suporta as mesmas opções de fornecedor que o BOOTP.</span><span class="sxs-lookup"><span data-stu-id="c649a-127">Although DHCP greatly enhances the functionality of BOOTP, DHCP uses the same message format as BOOTP and supports the same vendor options as BOOTP.</span></span> <span data-ttu-id="c649a-128">Para desempenhar a sua função, a DHCP introduz sete novas opções específicas do DHCP, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c649a-128">In order to perform its function, DHCP introduces seven new DHCP-specific options, as follows:</span></span>

- <span data-ttu-id="c649a-129">DESCUBRA (1) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-129">DISCOVER (1) (sent by DHCP Client)</span></span>

- <span data-ttu-id="c649a-130">OFERTA (2) (enviado pelo Servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-130">OFFER (2) (sent by DHCP Server)</span></span>

- <span data-ttu-id="c649a-131">PEDIDO (3) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-131">REQUEST (3) (sent by DHCP Client)</span></span>

- <span data-ttu-id="c649a-132">DECLÍNIO (4) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-132">DECLINE (4) (sent by DHCP Client)</span></span>

- <span data-ttu-id="c649a-133">ACK (5) (enviado pelo Servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-133">ACK (5) (sent by DHCP Server)</span></span>

- <span data-ttu-id="c649a-134">NACK (6) (enviado pelo Servidor DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-134">NACK (6) (sent by DHCP Server)</span></span>

- <span data-ttu-id="c649a-135">LANÇAMENTO (7) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-135">RELEASE (7) (sent by DHCP Client)</span></span>

- <span data-ttu-id="c649a-136">INFORM (8) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-136">INFORM (8) (sent by DHCP Client)</span></span>

- <span data-ttu-id="c649a-137">FORCERENEW (9) (enviado pelo Cliente DHCP)</span><span class="sxs-lookup"><span data-stu-id="c649a-137">FORCERENEW (9) (sent by DHCP Client)</span></span>

## <a name="dhcp-communication"></a><span data-ttu-id="c649a-138">Comunicação DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-138">DHCP Communication</span></span>

<span data-ttu-id="c649a-139">O DHCP utiliza o protocolo UDP para enviar pedidos e respostas de campo.</span><span class="sxs-lookup"><span data-stu-id="c649a-139">DHCP utilizes the UDP protocol to send requests and field responses.</span></span> <span data-ttu-id="c649a-140">Antes de ter um endereço IP, as mensagens UDP que transportam as informações do DHCP são enviadas e recebidas utilizando o endereço de transmissão IP de 255.255.255.255.255.</span><span class="sxs-lookup"><span data-stu-id="c649a-140">Prior to having an IP address, UDP messages carrying the DHCP information are sent and received by utilizing the IP broadcast address of 255.255.255.255.</span></span>

## <a name="dhcp-client-state-machine"></a><span data-ttu-id="c649a-141">Máquina do Estado do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-141">DHCP Client State Machine</span></span>

<span data-ttu-id="c649a-142">O Cliente DHCP é implementado como uma máquina estatal.</span><span class="sxs-lookup"><span data-stu-id="c649a-142">The DHCP Client is implemented as a state machine.</span></span> <span data-ttu-id="c649a-143">A máquina estatal é processada por um fio DHCP interno que é criado durante *nx_dhcp_create* processamento.</span><span class="sxs-lookup"><span data-stu-id="c649a-143">The state machine is processed by an internal DHCP thread that is created during *nx_dhcp_create* processing.</span></span> <span data-ttu-id="c649a-144">Os principais estados do Cliente DHCP são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="c649a-144">The main states of DHCP Client are as follows:</span></span>


- <span data-ttu-id="c649a-145">**NX_DHCP_STATE_BOOT** Começando com um endereço IP anterior</span><span class="sxs-lookup"><span data-stu-id="c649a-145">**NX_DHCP_STATE_BOOT** Starting with a previous IP address</span></span>

- <span data-ttu-id="c649a-146">**NX_DHCP_STATE_INIT** Começando sem o valor do endereço IP anterior</span><span class="sxs-lookup"><span data-stu-id="c649a-146">**NX_DHCP_STATE_INIT** Starting with no previous   IP address value</span></span>

- <span data-ttu-id="c649a-147">**NX_DHCP_STATE_SELECTING** À espera de uma resposta de qualquer servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-147">**NX_DHCP_STATE_SELECTING** Waiting for a response from any DHCP server</span></span>

- <span data-ttu-id="c649a-148">**NX_DHCP_STATE_REQUESTING** Servidor DHCP identificado, pedido de endereço IP enviado</span><span class="sxs-lookup"><span data-stu-id="c649a-148">**NX_DHCP_STATE_REQUESTING** DHCP Server identified, IP address request sent</span></span>

- <span data-ttu-id="c649a-149">**NX_DHCP_STATE_BOUND** DhCP IP Endereço de arrendamento estabelecido</span><span class="sxs-lookup"><span data-stu-id="c649a-149">**NX_DHCP_STATE_BOUND** DHCP IP Address lease established</span></span>

- <span data-ttu-id="c649a-150">**NX_DHCP_STATE_RENEWING** DHCP IP Endereço prazo de renovação de contrato decorrido, renovação solicitada</span><span class="sxs-lookup"><span data-stu-id="c649a-150">**NX_DHCP_STATE_RENEWING** DHCP IP Address lease renewal time elapsed, renewal requested</span></span>

- <span data-ttu-id="c649a-151">**NX_DHCP_STATE_REBINDING** DHCP IP Endereço de locação reencambido tempo decorrido, renovação solicitada</span><span class="sxs-lookup"><span data-stu-id="c649a-151">**NX_DHCP_STATE_REBINDING** DHCP IP Address lease rebind time elapsed, renewal requested</span></span>

- <span data-ttu-id="c649a-152">**NX_DHCP_STATE_FORCERENEW** DhCP IP Endereço de aluguer estabelecido, renovação de força por servidor (atualmente não suportado) ou pela chamada de nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="c649a-152">**NX_DHCP_STATE_FORCERENEW** DHCP IP Address lease established, force renewal by server (currently not supported) or by the application calling nx_dhcp_force_renew</span></span>

- <span data-ttu-id="c649a-153">**NX_DHCP_STATE_ADDRESS_PROBING** Sondagem do Endereço IP do DHCP, envie a sonda ARP para detetar o conflito de endereços IP.</span><span class="sxs-lookup"><span data-stu-id="c649a-153">**NX_DHCP_STATE_ADDRESS_PROBING** DHCP IP Address probing, send the ARP probe to detect IP address conflict.</span></span>

## <a name="dhcp-client-multiple-interface-support"></a><span data-ttu-id="c649a-154">Suporte de interface múltipla do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-154">DHCP Client Multiple Interface Support</span></span>

<span data-ttu-id="c649a-155">O Cliente DHCP foi previamente implementado para funcionar apenas numa única interface de rede.</span><span class="sxs-lookup"><span data-stu-id="c649a-155">The DHCP Client was previously implemented to run on only a single network interface.</span></span> <span data-ttu-id="c649a-156">O comportamento padrão foi (e ainda é) para o Cliente DHCP funcionar na interface principal.</span><span class="sxs-lookup"><span data-stu-id="c649a-156">The default behavior was (and still is) for the DHCP Client to run on the primary interface.</span></span> <span data-ttu-id="c649a-157">Ao chamar *nx_dhcp_set_interface_index,* a aplicação poderia (e ainda pode) executar DHCP numa interface de rede secundária em vez da interface primária.</span><span class="sxs-lookup"><span data-stu-id="c649a-157">By calling *nx_dhcp_set_interface_index*, the application could (and still can) run DHCP on a secondary network interface instead of the primary interface.</span></span>

<span data-ttu-id="c649a-158">Suporta agora o DHCP em várias interfaces em paralelo.</span><span class="sxs-lookup"><span data-stu-id="c649a-158">It now supports DHCP running on multiple interfaces in parallel.</span></span> <span data-ttu-id="c649a-159">Consulte **o Cliente DHCP em Múltiplas Interfaces Simultaneamente** no Capítulo Dois para obter detalhes específicos sobre como executar o Cliente DHCP em mais de uma interface física simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="c649a-159">See **DHCP Client on Multiple Interfaces Simultaneously** in Chapter Two for specific details how to run DHCP Client on more than one physical interface simultaneously.</span></span>

## <a name="dhcp-user-request"></a><span data-ttu-id="c649a-160">Pedido de utilizador DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-160">DHCP User Request</span></span>

<span data-ttu-id="c649a-161">Uma vez que o servidor DHCP concede um endereço IP, o processamento do cliente DHCP pode solicitar parâmetros adicionais - um de cada vez - utilizando o serviço *nx_dhcp_user_option_request.*</span><span class="sxs-lookup"><span data-stu-id="c649a-161">Once the DHCP server grants an IP address, the DHCP client processing can request additional parameters — one at a time — by using the *nx_dhcp_user_option_request* service.</span></span>

## <a name="dhcp-client-socket-queue"></a><span data-ttu-id="c649a-162">Fila de tomada de cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="c649a-162">DHCP Client Socket Queue</span></span> 

<span data-ttu-id="c649a-163">O Cliente DHCP limpa automaticamente os pacotes de transmissão dos Servidores DHCP destinados a outros Clientes DHCP da sua tomada recebem fila enquanto espera que o Servidor responda a si próprio.</span><span class="sxs-lookup"><span data-stu-id="c649a-163">The DHCP Client automatically clears broadcast packets from DHCP Servers intended for other DHCP Clients from its socket receive queue while waiting for Server to respond to itself.</span></span> <span data-ttu-id="c649a-164">Numa rede movimentada, não fazê-lo poderia fazer com que os pacotes destinados ao Cliente fossem abandonados.</span><span class="sxs-lookup"><span data-stu-id="c649a-164">In a busy network, not doing so could cause packets intended for the Client to be dropped.</span></span>

## <a name="dhcp-rfcs"></a><span data-ttu-id="c649a-165">DHCP RFCs</span><span class="sxs-lookup"><span data-stu-id="c649a-165">DHCP RFCs</span></span>

<span data-ttu-id="c649a-166">NetX DHCP está em conformidade com RFC2132, RFC2131 e RFCs relacionados.</span><span class="sxs-lookup"><span data-stu-id="c649a-166">NetX DHCP is compliant with RFC2132, RFC2131, and related RFCs.</span></span>

