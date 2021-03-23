---
title: Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração
description: Existem várias opções de configuração para a construção do Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826089"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="e7d2f-103">Capítulo 3 - Azure RTOS NetX Duo DHCPv6 opções de configuração</span><span class="sxs-lookup"><span data-stu-id="e7d2f-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="e7d2f-104">Existem várias opções de configuração para a construção do Azure RTOS NetX Duo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="e7d2f-105">A seguinte lista descreve cada uma em detalhe:</span><span class="sxs-lookup"><span data-stu-id="e7d2f-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="e7d2f-106">**NX_DHCPV6_THREAD_PRIORITY** Prioridade da linha do Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="e7d2f-107">Por predefinição, este valor especifica que a linha Cliente funciona na prioridade 2.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="e7d2f-108">**NX_DHCPV6_MUTEX_WAIT** A opção Time out para obter um bloqueio exclusivo num mutex do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="e7d2f-109">O valor predefinido é TX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="e7d2f-110">**NX_DHCPV6_TICKS_PER_SECOND** Relação de tiques a segundos.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="e7d2f-111">Isto é dependente do processador.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-111">This is processor dependent.</span></span> <span data-ttu-id="e7d2f-112">O valor predefinido é 100.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-112">The default value is 100.</span></span>

- <span data-ttu-id="e7d2f-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Intervalo de tempo em segundos em que o temporizador de vida IP atualiza o tempo que o endereço IP atual foi atribuído ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="e7d2f-114">Por predefinição, este valor é 1.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-114">By default, this value is 1.</span></span>

- <span data-ttu-id="e7d2f-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Intervalo de tempo em segundos em que o temporizador da sessão atualiza o tempo que o Cliente esteve em sessão comunicando com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="e7d2f-116">Por predefinição, este valor é 1.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-116">By default, this value is 1.</span></span>

- <span data-ttu-id="e7d2f-117">**NX_DHCPV6_MAX_IA_ADDRESS** O número máximo de endereços IA que podem ser adicionados ao registo do Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="e7d2f-118">O valor predefinido é 1.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-118">The default value is 1.</span></span> 

- <span data-ttu-id="e7d2f-119">**NX_DHCPV6_NUM_DNS_SERVERS** Número de servidores DNS para armazenar no registo do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="e7d2f-120">O valor predefinido é 2.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-120">The default value is 2.</span></span>

- <span data-ttu-id="e7d2f-121">**NX_DHCPV6_NUM_TIME_SERVERS** Número de servidores de tempo para armazenar no registo do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="e7d2f-122">O valor predefinido é 1.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-122">The default value is 1.</span></span>

- <span data-ttu-id="e7d2f-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Tamanho do tampão no registo do Cliente para deter o nome de domínio de rede do cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="e7d2f-124">O valor predefinido é 30.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-124">The default value is 30.</span></span>

- <span data-ttu-id="e7d2f-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Tamanho do tampão no registo do Cliente para manter o fuso horário do Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="e7d2f-126">O valor predefinido é 10.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-126">The default value is 10.</span></span>

- <span data-ttu-id="e7d2f-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Tamanho do tampão no registo do Cliente para manter a mensagem de estado de opção numa resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="e7d2f-128">O valor predefinido é de 100 bytes.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="e7d2f-129">**NX_DHCPV6_PACKET_TIME_OUT** Tempo para fora em segundos para alocar um pacote da piscina de pacotes do Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="e7d2f-130">O valor predefinido é de 3 segundos.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="e7d2f-131">**NX_DHCPV6_TYPE_OF_SERVICE** Isto define o tipo de serviço para a transmissão de pacotes UDP a partir da tomada do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="e7d2f-132">O valor **predefinido** é NX_IP_NORMAL .</span><span class="sxs-lookup"><span data-stu-id="e7d2f-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="e7d2f-133">**NX_DHCPV6_TIME_TO_LIVE** O número de vezes que um pacote do Cliente é reencaminhado por um router de rede antes de o pacote ser descartado.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="e7d2f-134">O valor predefinido é 0x80.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-134">The default value is 0x80.</span></span>

- <span data-ttu-id="e7d2f-135">**NX_DHCPV6_QUEUE_DEPTH** Especifica o número de pacotes a manter na tomada UDP do cliente receber fila antes que o NetX Duo deite fora os pacotes.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="e7d2f-136">O valor predefinido é 5.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="e7d2f-137">Transmissão de mensagens DHCPv6</span><span class="sxs-lookup"><span data-stu-id="e7d2f-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="e7d2f-138">Existem um conjunto de opções do Cliente DHCPv6 para definir parâmetros na transmissão de mensagens DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="e7d2f-139">Esses avisos são:</span><span class="sxs-lookup"><span data-stu-id="e7d2f-139">These are:</span></span> 

  - <span data-ttu-id="e7d2f-140">tempo limite inicial</span><span class="sxs-lookup"><span data-stu-id="e7d2f-140">initial timeout</span></span>

  - <span data-ttu-id="e7d2f-141">atraso máximo na primeira transmissão</span><span class="sxs-lookup"><span data-stu-id="e7d2f-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="e7d2f-142">prazo máximo de retransmissão</span><span class="sxs-lookup"><span data-stu-id="e7d2f-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="e7d2f-143">número máximo de retransmissão</span><span class="sxs-lookup"><span data-stu-id="e7d2f-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="e7d2f-144">duração máxima para esperar pela resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="e7d2f-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="e7d2f-145">Estes parâmetros aplicam-se a cada uma das mensagens do Cliente DHCPv6:</span><span class="sxs-lookup"><span data-stu-id="e7d2f-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="e7d2f-146">SOLICIT</span><span class="sxs-lookup"><span data-stu-id="e7d2f-146">SOLICIT</span></span>

- <span data-ttu-id="e7d2f-147">PEDIDO</span><span class="sxs-lookup"><span data-stu-id="e7d2f-147">REQUEST</span></span>

- <span data-ttu-id="e7d2f-148">RENOVAR</span><span class="sxs-lookup"><span data-stu-id="e7d2f-148">RENEW</span></span>

- <span data-ttu-id="e7d2f-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="e7d2f-149">REBIND</span></span>

- <span data-ttu-id="e7d2f-150">LANÇAMENTO</span><span class="sxs-lookup"><span data-stu-id="e7d2f-150">RELEASE</span></span>

- <span data-ttu-id="e7d2f-151">DECLÍNIO</span><span class="sxs-lookup"><span data-stu-id="e7d2f-151">DECLINE</span></span>

- <span data-ttu-id="e7d2f-152">CONFIRMAR</span><span class="sxs-lookup"><span data-stu-id="e7d2f-152">CONFIRM</span></span>

- <span data-ttu-id="e7d2f-153">INFORMAR</span><span class="sxs-lookup"><span data-stu-id="e7d2f-153">INFORM</span></span>

<span data-ttu-id="e7d2f-154">Segue-se uma lista completa destas opções configuráveis e o seu padrão</span><span class="sxs-lookup"><span data-stu-id="e7d2f-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="e7d2f-155">valores:</span><span class="sxs-lookup"><span data-stu-id="e7d2f-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="e7d2f-156">Para não limitar o tempo limite de retransmissão, decrete a contagem de retransmissão da mensagem para 0.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="e7d2f-157">Para não limitar o número de vezes que uma mensagem do Cliente DHCPv6 é retransmitida (recauchutado), decreta a contagem de retransmissão da mensagem para 0.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="e7d2f-158">Independentemente do tempo limite ou do número de retrações, quando um endereço IPv6 válido expira, é removido da tabela de endereços IP e já não pode ser utilizado pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="e7d2f-159">O Cliente NetX Duo DHCPv6 começará automaticamente a enviar mensagens SOLICIT solicitando um novo endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="e7d2f-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>