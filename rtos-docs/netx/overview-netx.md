---
title: Compreender Azure RTOS NetX
description: Azure RTOS NetX é uma implementação de alto desempenho dos padrões de protocolo TCP/IP, totalmente integrado com Azure RTOS ThreadX e disponível para todos os processadores suportados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825585"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="45d72-103">Visão geral do Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="45d72-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="45d72-104">Azure RTOS NetX é uma pilha de rede incorporada TCP/IP IPv4 de grau industrial, projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="45d72-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="45d72-105">Azure RTOS NetX é a pilha original de rede IPv4 da Microsoft, e é essencialmente um subconjunto de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="45d72-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="45d72-106">A NetX fornece aplicações incorporadas com protocolos de rede fundamentais, tais como IPv4, TCP e UDP, bem como um conjunto completo de protocolos adicionais e adicionais de alto nível.</span><span class="sxs-lookup"><span data-stu-id="45d72-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="45d72-107">Uma pequena pegada, execução rápida e facilidade de utilização superior fazem do Azure RTOS NetX uma escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="45d72-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="45d72-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="45d72-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="45d72-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="45d72-109">TELNET</span></span>

* <span data-ttu-id="45d72-110">Pegada mínima de 0,5 KB e 0,3 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-111">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="45d72-111">Client and server support</span></span>
* <span data-ttu-id="45d72-112">ApIs intuitivos telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="45d72-113">IP automático</span><span class="sxs-lookup"><span data-stu-id="45d72-113">Auto IP</span></span>

* <span data-ttu-id="45d72-114">Atribuição automática de endereços IPv4</span><span class="sxs-lookup"><span data-stu-id="45d72-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="45d72-115">Mínimo 1.2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="45d72-116">APIs autoIP intuitivos: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="45d72-117">HTTP - Protocolo de Transferência de Hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="45d72-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="45d72-118">Mínimo de 2,8 KB a 4.8KBFLASH, 0,4 KB a 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-119">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="45d72-119">Client and server support</span></span>
* <span data-ttu-id="45d72-120">APIs intuitivos HTTP: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="45d72-121">SMTP - Simples Protocolo de Transferência de Correio (SMTP)</span><span class="sxs-lookup"><span data-stu-id="45d72-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="45d72-122">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-123">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="45d72-123">Client support</span></span>
* <span data-ttu-id="45d72-124">APIs intuitivos: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="45d72-125">DHCP - Protocolo de Configuração dinâmica do anfitrião (DHCP)</span><span class="sxs-lookup"><span data-stu-id="45d72-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="45d72-126">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="45d72-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-127">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="45d72-127">Client and server support</span></span>
* <span data-ttu-id="45d72-128">Suporte IPv4</span><span class="sxs-lookup"><span data-stu-id="45d72-128">IPv4 support</span></span>
* <span data-ttu-id="45d72-129">APIs intuitivos do DHCP: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="45d72-130">P0P3 - Protocolo dos Correios Versão 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="45d72-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="45d72-131">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-132">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="45d72-132">Client support</span></span>
* <span data-ttu-id="45d72-133">APIs P0P3 intuitivo: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="45d72-134">SNMP - Protocolo de Gestão de Redes Simples (SNMP)</span><span class="sxs-lookup"><span data-stu-id="45d72-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="45d72-135">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-136">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="45d72-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="45d72-137">APIs intuitivos do SNMP: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="45d72-138">FTP, TFTP - Protocolo de Transferência de Ficheiros (FTP), Protocolo de Transferência de Ficheiros Trivial (TFTP)</span><span class="sxs-lookup"><span data-stu-id="45d72-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="45d72-139">FTP Mínimo de 1,8 KB a 7.2KBFLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-140">TFTP Mínimo de 1,7 KB a 2.4KBFLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-141">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="45d72-141">Client and server support</span></span>
* <span data-ttu-id="45d72-142">APIs intuitivos de FTP e TFTP: <i>nx_ftp_ *</i> ou <i>nx_tftp_*</i></span><span class="sxs-lookup"><span data-stu-id="45d72-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="45d72-143">PPP - Protocolo Polnt-to-PoInt (PPP)</span><span class="sxs-lookup"><span data-stu-id="45d72-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="45d72-144">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-145">APIs intuitivos de PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="45d72-146">SNTP - Protocolo de Tempo de Rede Simples (SNTP)</span><span class="sxs-lookup"><span data-stu-id="45d72-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="45d72-147">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="45d72-148">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="45d72-148">Client support</span></span>
* <span data-ttu-id="45d72-149">APIs intuitivos: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="45d72-150">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="45d72-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="45d72-151">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="45d72-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="45d72-152">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="45d72-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="45d72-153">Implementação rápida e zero-copy API</span><span class="sxs-lookup"><span data-stu-id="45d72-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="45d72-154">Todas as funções da API têm levado <i>nx_\*</i> a identificar facilmente como Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="45d72-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="45d72-155">As funções de API de bloqueio têm um tempo limite opcional de linha</span><span class="sxs-lookup"><span data-stu-id="45d72-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="45d72-156">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="45d72-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="45d72-157">IGMP - Protocolo de Gestão de Grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="45d72-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="45d72-158">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="45d72-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="45d72-159">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="45d72-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="45d72-160">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-161">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="45d72-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="45d72-162">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-163">APIs intuitivos do IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="45d72-164">UDP - Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="45d72-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="45d72-165">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="45d72-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="45d72-166">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="45d72-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="45d72-167">RX 95 Mbps em 100 Mbps Ethernet, MCU @100MHz , 14% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="45d72-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="45d72-168">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="45d72-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="45d72-169">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="45d72-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="45d72-170">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="45d72-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="45d72-171">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-172">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="45d72-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="45d72-173">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="45d72-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="45d72-174">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="45d72-174">Optional UDP statistics</span></span>
* <span data-ttu-id="45d72-175">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-176">APIs intuitivos da UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="45d72-177">TCP - Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="45d72-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="45d72-178">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="45d72-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="45d72-179">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="45d72-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="45d72-180">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="45d72-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="45d72-181">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="45d72-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="45d72-182">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="45d72-182">Reliable connection</span></span>
* <span data-ttu-id="45d72-183">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="45d72-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="45d72-184">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-185">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="45d72-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="45d72-186">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="45d72-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="45d72-187">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="45d72-187">Optional TCP statistics</span></span>
* <span data-ttu-id="45d72-188">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-189">APIs intuitivos de TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="45d72-190">ICMP - Protocolo de Mensagem de Controlo de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="45d72-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="45d72-191">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="45d72-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="45d72-192">Suporte IPv4</span><span class="sxs-lookup"><span data-stu-id="45d72-192">IPv4 support</span></span>
* <span data-ttu-id="45d72-193">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-194">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="45d72-194">Ping request and ping response</span></span>
* <span data-ttu-id="45d72-195">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="45d72-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="45d72-196">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="45d72-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="45d72-197">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="45d72-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="45d72-198">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-199">APIs intuitivos do ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="45d72-200">IPv4 - Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="45d72-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="45d72-201">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="45d72-202">Arquitetura Piconet™</span><span class="sxs-lookup"><span data-stu-id="45d72-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="45d72-203">Rápido, perto do desempenho da velocidade de arame</span><span class="sxs-lookup"><span data-stu-id="45d72-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="45d72-204">Suporte de interface múltipla</span><span class="sxs-lookup"><span data-stu-id="45d72-204">Multiple interface support</span></span>
* <span data-ttu-id="45d72-205">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="45d72-205">Multihomed support</span></span>
* <span data-ttu-id="45d72-206">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="45d72-206">Static routing support</span></span>
* <span data-ttu-id="45d72-207">Suporte de fragmentação/remontagem de IP</span><span class="sxs-lookup"><span data-stu-id="45d72-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="45d72-208">Suporte IPv4</span><span class="sxs-lookup"><span data-stu-id="45d72-208">IPv4 Support</span></span>
* <span data-ttu-id="45d72-209">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-210">Certificação de logotipo pronto da fase II</span><span class="sxs-lookup"><span data-stu-id="45d72-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="45d72-211">Estatísticas IP opcionais</span><span class="sxs-lookup"><span data-stu-id="45d72-211">Optional IP statistics</span></span>
* <span data-ttu-id="45d72-212">Interface de controlador de camada física bem definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="45d72-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="45d72-213">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-214">APIs intuitivos da camada IP: *nx_ip_ \**, *nxd_ip_ \**</span><span class="sxs-lookup"><span data-stu-id="45d72-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="45d72-215">Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="45d72-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="45d72-216">ARP/RARP - Protocolo de Resolução de Endereços (ARP), Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="45d72-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="45d72-217">Mínimo de 1,7 KB FLASH, tamanho RAM</span><span class="sxs-lookup"><span data-stu-id="45d72-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="45d72-218">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt</span><span class="sxs-lookup"><span data-stu-id="45d72-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="45d72-219">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="45d72-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="45d72-220">Cache ARP flexível e definido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="45d72-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="45d72-221">Suporte gratuito da ARP</span><span class="sxs-lookup"><span data-stu-id="45d72-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="45d72-222">Estatísticas opcionais de ARP/RARP determinadas por aplicação</span><span class="sxs-lookup"><span data-stu-id="45d72-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="45d72-223">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="45d72-224">APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="45d72-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="45d72-225">ETHERNET, Wi-Fi, BLUETOOTH LE, 15.4, etc.</span><span class="sxs-lookup"><span data-stu-id="45d72-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="45d72-226">Pequena pegada</span><span class="sxs-lookup"><span data-stu-id="45d72-226">Small-footprint</span></span>

<span data-ttu-id="45d72-227">O Azure RTOS NetX tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP.</span><span class="sxs-lookup"><span data-stu-id="45d72-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="45d72-228">Para a funcionalidade TCP, são necessários mais 10 KB a 13 KB de memória da área de instrução.</span><span class="sxs-lookup"><span data-stu-id="45d72-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="45d72-229">O uso de RAM Azure RTOS NetX varia tipicamente de 2,6 KB a 3,6 KB mais a memória do pacote pool, que é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="45d72-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="45d72-230">Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS NetX escala automaticamente com base nos serviços utilizados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="45d72-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="45d72-231">Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="45d72-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="45d72-232">Execução rápida</span><span class="sxs-lookup"><span data-stu-id="45d72-232">Fast execution</span></span>

<span data-ttu-id="45d72-233">O Azure RTOS NetX fornece uma implementação de envio/receção de pacotes de cópia zero e está altamente integrado com a Azure RTOS ThreadX para alcançar o desempenho mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="45d72-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="45d72-234">Por exemplo, o Azure RTOS NetX pode normalmente obter perto de transferências de dados de velocidade bancária num processador de 80 MHz (ou menos), utilizando apenas uma pequena percentagem dos ciclos do processador.</span><span class="sxs-lookup"><span data-stu-id="45d72-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="45d72-235">Simples e fácil de usar</span><span class="sxs-lookup"><span data-stu-id="45d72-235">Simple, easy-to-use</span></span>

<span data-ttu-id="45d72-236">O Azure RTOS NetX é simples de usar.</span><span class="sxs-lookup"><span data-stu-id="45d72-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="45d72-237">O Azure RTOS NetX API é simultaneamente intuitivo e altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="45d72-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="45d72-238">Os nomes da API são feitos de palavras reais e não de "sopa de alfabeto" ou nomes altamente abreviados que são tão comuns em outros produtos de networking.</span><span class="sxs-lookup"><span data-stu-id="45d72-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="45d72-239">Todas as APIs Azure RTOS NetX têm uma *nx_* líder e seguem uma convenção de nomeação de substantivos.</span><span class="sxs-lookup"><span data-stu-id="45d72-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="45d72-240">Além disso, existe uma consistência funcional em toda a API.</span><span class="sxs-lookup"><span data-stu-id="45d72-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="45d72-241">Por exemplo, todas as funções da API que suspendem têm um tempo limite opcional que funciona de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="45d72-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="45d72-242">Para aplicações antigas, o Azure RTOS NetX oferece uma camada compatível com tomada BSD adicional.</span><span class="sxs-lookup"><span data-stu-id="45d72-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="45d72-243">Esta camada ajuda os desenvolvedores a migrar grandes aplicações de networking com facilidade.</span><span class="sxs-lookup"><span data-stu-id="45d72-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="45d72-244">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="45d72-244">Interoperability verification</span></span>

<span data-ttu-id="45d72-245">O Azure RTOS NetX está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="45d72-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="45d72-246">O Azure RTOS NetX também utiliza a padrão da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="45d72-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="45d72-247">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="45d72-247">Advanced technology</span></span>

<span data-ttu-id="45d72-248">Azure RTOS NetX é uma tecnologia avançada que inclui:</span><span class="sxs-lookup"><span data-stu-id="45d72-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="45d72-249">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="45d72-249">Piconet™ architecture</span></span>
* <span data-ttu-id="45d72-250">escala automática</span><span class="sxs-lookup"><span data-stu-id="45d72-250">automatic scaling</span></span>
* <span data-ttu-id="45d72-251">Tecnologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="45d72-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="45d72-252">gestão flexível de pacotes</span><span class="sxs-lookup"><span data-stu-id="45d72-252">flexible packet management</span></span>
* <span data-ttu-id="45d72-253">API de cópia zero e implementação</span><span class="sxs-lookup"><span data-stu-id="45d72-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="45d72-254">suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="45d72-254">multihomed support</span></span>
* <span data-ttu-id="45d72-255">tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="45d72-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="45d72-256">suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="45d72-256">static routing support</span></span>
* <span data-ttu-id="45d72-257">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="45d72-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="45d72-258">O tempo de venda mais rápido</span><span class="sxs-lookup"><span data-stu-id="45d72-258">Fastest time-to-market</span></span>

<span data-ttu-id="45d72-259">O Azure RTOS NetX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter.</span><span class="sxs-lookup"><span data-stu-id="45d72-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="45d72-260">Como resultado, o Azure RTOS NetX é uma das pilhas TCP/IP mais populares para dispositivos IoT incorporados, incluindo muitos SoCs da Broadcom, Gainspan, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="45d72-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="45d72-261">A nossa vantagem consistente no mercado baseia-se em:</span><span class="sxs-lookup"><span data-stu-id="45d72-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="45d72-262">documentação de qualidade – por favor, reveja [o nosso Azure RTOS NetX User Guide](about-this-guide.md) e veja por si mesmo!</span><span class="sxs-lookup"><span data-stu-id="45d72-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="45d72-263">disponibilidade completa de código fonte</span><span class="sxs-lookup"><span data-stu-id="45d72-263">complete source code availability</span></span>
* <span data-ttu-id="45d72-264">API fácil de usar</span><span class="sxs-lookup"><span data-stu-id="45d72-264">easy-to-use API</span></span>
* <span data-ttu-id="45d72-265">conjunto de recursos abrangente e avançado</span><span class="sxs-lookup"><span data-stu-id="45d72-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="45d72-266">Uma licença simples</span><span class="sxs-lookup"><span data-stu-id="45d72-266">One Simple License</span></span>

<span data-ttu-id="45d72-267">Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.</span><span class="sxs-lookup"><span data-stu-id="45d72-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="45d72-268">Código fonte completo e de alta qualidade</span><span class="sxs-lookup"><span data-stu-id="45d72-268">Full, highest-quality source code</span></span>

<span data-ttu-id="45d72-269">Ao longo dos anos, o código fonte Azure RTOS NetX definiu a fasquia em qualidade e facilidade de compreensão.</span><span class="sxs-lookup"><span data-stu-id="45d72-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="45d72-270">Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.</span><span class="sxs-lookup"><span data-stu-id="45d72-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="45d72-271">Apoia as arquiteturas mais populares</span><span class="sxs-lookup"><span data-stu-id="45d72-271">Supports most popular architectures</span></span>

<span data-ttu-id="45d72-272">O Azure RTOS NetX funciona com microprocessadores mais populares de 32/64 bits, fora da caixa, totalmente testados e totalmente suportados, incluindo as seguintes arquiteturas avançadas:</span><span class="sxs-lookup"><span data-stu-id="45d72-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="45d72-273">**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="45d72-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="45d72-274">**Núcleo de Andes**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="45d72-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="45d72-275">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="45d72-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="45d72-276">**BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="45d72-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="45d72-277">**Cadência**: Xtensa, Diamante</span><span class="sxs-lookup"><span data-stu-id="45d72-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="45d72-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi</span><span class="sxs-lookup"><span data-stu-id="45d72-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="45d72-279">**Cipreste**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="45d72-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="45d72-280">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="45d72-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="45d72-281">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="45d72-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="45d72-282">**Informação; Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="45d72-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="45d72-283">**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="45d72-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="45d72-284">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="45d72-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="45d72-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="45d72-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="45d72-286">**Renesas**: SH, HS, V850, RX, RZ, Sinergia</span><span class="sxs-lookup"><span data-stu-id="45d72-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="45d72-287">**Laboratórios de Silício**: EFM32</span><span class="sxs-lookup"><span data-stu-id="45d72-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="45d72-288">**Sinopses**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="45d72-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="45d72-289">**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="45d72-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="45d72-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="45d72-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="45d72-291">**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M</span><span class="sxs-lookup"><span data-stu-id="45d72-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="45d72-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="45d72-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="45d72-293">*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*</span><span class="sxs-lookup"><span data-stu-id="45d72-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
