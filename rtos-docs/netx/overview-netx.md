---
title: Compreender Azure RTOS NetX
description: Azure RTOS NetX é uma implementação de alto desempenho dos padrões de protocolo TCP/IP, totalmente integrado com Azure RTOS ThreadX e disponível para todos os processadores suportados.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 63fd212249da6154926684f9bc844d2c2a78e84e
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754850"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="3af4a-103">Visão geral do Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="3af4a-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="3af4a-104">Azure RTOS NetX é uma pilha de rede incorporada TCP/IP IPv4 de grau industrial, projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT.</span><span class="sxs-lookup"><span data-stu-id="3af4a-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="3af4a-105">Azure RTOS NetX é a pilha original de rede IPv4 da Microsoft, e é essencialmente um subconjunto de Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="3af4a-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="3af4a-106">A NetX fornece aplicações incorporadas com protocolos de rede fundamentais, tais como IPv4, TCP e UDP, bem como um conjunto completo de protocolos adicionais e adicionais de alto nível.</span><span class="sxs-lookup"><span data-stu-id="3af4a-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="3af4a-107">Uma pequena pegada, execução rápida e facilidade de utilização superior fazem do Azure RTOS NetX uma escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="3af4a-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="3af4a-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="3af4a-108">API protocols</span></span>
<span data-ttu-id="3af4a-109">O Azure RTOS NetX fornece suporte para o seguinte.</span><span class="sxs-lookup"><span data-stu-id="3af4a-109">Azure RTOS NetX provides support for the following.</span></span>

### <a name="telnet"></a><span data-ttu-id="3af4a-110">TELNET</span><span class="sxs-lookup"><span data-stu-id="3af4a-110">TELNET</span></span>

* <span data-ttu-id="3af4a-111">Pegada mínima de 0,5 KB e 0,3 KB RAM.</span><span class="sxs-lookup"><span data-stu-id="3af4a-111">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="3af4a-112">Suporte ao cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3af4a-112">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="3af4a-113">IP automático</span><span class="sxs-lookup"><span data-stu-id="3af4a-113">Auto IP</span></span>

* <span data-ttu-id="3af4a-114">Atribuição automática de endereços IPv4.</span><span class="sxs-lookup"><span data-stu-id="3af4a-114">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="3af4a-115">Mínimo de 1,2 KB, 300 bytes de RAM.</span><span class="sxs-lookup"><span data-stu-id="3af4a-115">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="3af4a-116">HTTP - Protocolo de Transferência de Hipertexto (HTTP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-116">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="3af4a-117">Mínimo de 2,8 KB a 4.8KBFLASH, 0,4 KB a 1,0 KB RAM.</span><span class="sxs-lookup"><span data-stu-id="3af4a-117">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="3af4a-118">Suporte ao cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3af4a-118">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="3af4a-119">SMTP - Simples Protocolo de Transferência de Correio (SMTP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-119">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="3af4a-120">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-120">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-121">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3af4a-121">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="3af4a-122">DHCP - Protocolo de Configuração dinâmica do anfitrião (DHCP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-122">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="3af4a-123">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="3af4a-123">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-124">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3af4a-124">Client and server support</span></span>
* <span data-ttu-id="3af4a-125">Suporte IPv4</span><span class="sxs-lookup"><span data-stu-id="3af4a-125">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="3af4a-126">P0P3 - Pós-Office Protocolo Versão 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="3af4a-126">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="3af4a-127">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-127">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-128">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3af4a-128">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="3af4a-129">SNMP - Protocolo de Gestão de Redes Simples (SNMP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-129">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="3af4a-130">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-130">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-131">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="3af4a-131">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="3af4a-132">FTP, TFTP - Protocolo de Transferência de Ficheiros (FTP), Protocolo de Transferência de Ficheiros Trivial (TFTP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-132">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="3af4a-133">FTP Mínimo de 1,8 KB a 7.2KBFLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-133">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-134">TFTP Mínimo de 1,7 KB a 2.4KBFLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-134">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-135">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3af4a-135">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="3af4a-136">PPP - Protocolo Polnt-to-PoInt (PPP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-136">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="3af4a-137">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-137">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="3af4a-138">Confiável e fiável.</span><span class="sxs-lookup"><span data-stu-id="3af4a-138">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="3af4a-139">SNTP - Protocolo de Tempo de Rede Simples (SNTP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-139">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="3af4a-140">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3af4a-140">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="3af4a-141">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3af4a-141">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="3af4a-142">Azure RTOS NetX API</span><span class="sxs-lookup"><span data-stu-id="3af4a-142">Azure RTOS NetX API</span></span>

* <span data-ttu-id="3af4a-143">Implementação rápida e zero-copy API</span><span class="sxs-lookup"><span data-stu-id="3af4a-143">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="3af4a-144">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="3af4a-144">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="3af4a-145">IGMP - Protocolo de Gestão de Grupos de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-145">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="3af4a-146">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="3af4a-146">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3af4a-147">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="3af4a-147">IPv4 multicast group support</span></span>
* <span data-ttu-id="3af4a-148">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="3af4a-148">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="3af4a-149">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="3af4a-149">Optional IGMP statistics</span></span>
* <span data-ttu-id="3af4a-150">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3af4a-150">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="3af4a-151">UDP - Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-151">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="3af4a-152">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="3af4a-152">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="3af4a-153">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="3af4a-153">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="3af4a-154">RX 95 Mbps em 100 Mbps Ethernet, MCU @100MHz , 14% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="3af4a-154">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="3af4a-155">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="3af4a-155">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="3af4a-156">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="3af4a-156">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="3af4a-157">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="3af4a-157">No limits on the number of UDP</span></span>
* <span data-ttu-id="3af4a-158">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="3af4a-158">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="3af4a-159">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="3af4a-159">Optional suspension on socket receive</span></span>
* <span data-ttu-id="3af4a-160">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3af4a-160">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3af4a-161">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="3af4a-161">Optional UDP statistics</span></span>
* <span data-ttu-id="3af4a-162">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3af4a-162">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="3af4a-163">TCP - Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-163">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="3af4a-164">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="3af4a-164">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="3af4a-165">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="3af4a-165">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="3af4a-166">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="3af4a-166">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="3af4a-167">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% UTILIZAÇÃO MCU</span><span class="sxs-lookup"><span data-stu-id="3af4a-167">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="3af4a-168">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="3af4a-168">Reliable connection</span></span>
* <span data-ttu-id="3af4a-169">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="3af4a-169">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="3af4a-170">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="3af4a-170">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="3af4a-171">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="3af4a-171">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="3af4a-172">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3af4a-172">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3af4a-173">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="3af4a-173">Optional TCP statistics</span></span>
* <span data-ttu-id="3af4a-174">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3af4a-174">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="3af4a-175">ICMP - Protocolo de Mensagem de Controlo de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-175">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="3af4a-176">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="3af4a-176">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3af4a-177">Suporte IPv4</span><span class="sxs-lookup"><span data-stu-id="3af4a-177">IPv4 support</span></span>
* <span data-ttu-id="3af4a-178">IXIA IxANVL Validada</span><span class="sxs-lookup"><span data-stu-id="3af4a-178">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="3af4a-179">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="3af4a-179">Ping request and ping response</span></span>
* <span data-ttu-id="3af4a-180">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="3af4a-180">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="3af4a-181">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3af4a-181">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3af4a-182">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="3af4a-182">Optional ICMP statistics</span></span>
* <span data-ttu-id="3af4a-183">Traço de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3af4a-183">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="3af4a-184">IPv4 - Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-184">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="3af4a-185">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB RAM.</span><span class="sxs-lookup"><span data-stu-id="3af4a-185">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="3af4a-186">Piconet™ Arquitetura.</span><span class="sxs-lookup"><span data-stu-id="3af4a-186">Piconet™ Architecture.</span></span>
* <span data-ttu-id="3af4a-187">Rápido, perto de velocidade de arame.</span><span class="sxs-lookup"><span data-stu-id="3af4a-187">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="3af4a-188">Suporte de interface múltipla.</span><span class="sxs-lookup"><span data-stu-id="3af4a-188">Multiple interface support.</span></span>
* <span data-ttu-id="3af4a-189">Apoio multi-habitação.</span><span class="sxs-lookup"><span data-stu-id="3af4a-189">Multi-homed support.</span></span>
* <span data-ttu-id="3af4a-190">Suporte de encaminhamento estático.</span><span class="sxs-lookup"><span data-stu-id="3af4a-190">Static routing support.</span></span>
* <span data-ttu-id="3af4a-191">Suporte de fragmentação/remontagem ip.</span><span class="sxs-lookup"><span data-stu-id="3af4a-191">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="3af4a-192">Suporte IPv4.</span><span class="sxs-lookup"><span data-stu-id="3af4a-192">IPv4 Support.</span></span>
* <span data-ttu-id="3af4a-193">IXIA IxANVL Validada.</span><span class="sxs-lookup"><span data-stu-id="3af4a-193">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="3af4a-194">Certificação de logotipo pronto da fase II.</span><span class="sxs-lookup"><span data-stu-id="3af4a-194">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="3af4a-195">Estatísticas IP opcionais.</span><span class="sxs-lookup"><span data-stu-id="3af4a-195">Optional IP statistics.</span></span>
* <span data-ttu-id="3af4a-196">Interface de condutor de camada física bem definida e intuitiva.</span><span class="sxs-lookup"><span data-stu-id="3af4a-196">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="3af4a-197">Rastreio de nível de sistema via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="3af4a-197">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="3af4a-198">ARP/RARP - Protocolo de Resolução de Endereços (ARP), Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="3af4a-198">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="3af4a-199">Mínimo de 1,7 KB FLASH, tamanho RAM.</span><span class="sxs-lookup"><span data-stu-id="3af4a-199">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="3af4a-200">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt.</span><span class="sxs-lookup"><span data-stu-id="3af4a-200">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="3af4a-201">IXIA IxANVL Validada.</span><span class="sxs-lookup"><span data-stu-id="3af4a-201">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="3af4a-202">Cache ARP flexível e definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="3af4a-202">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="3af4a-203">Suporte gratuito da ARP.</span><span class="sxs-lookup"><span data-stu-id="3af4a-203">Gratuitous ARP support.</span></span>
* <span data-ttu-id="3af4a-204">Estatísticas opcionais de ARP/RARP determinadas por aplicação.</span><span class="sxs-lookup"><span data-stu-id="3af4a-204">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="3af4a-205">Rastreio de nível de sistema via Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="3af4a-205">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="3af4a-206">ETHERNET, Wi-Fi, BLUETOOTH LE, 15.4, etc.</span><span class="sxs-lookup"><span data-stu-id="3af4a-206">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="3af4a-207">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="3af4a-207">Interoperability verification</span></span>

<span data-ttu-id="3af4a-208">O Azure RTOS NetX está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos da maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="3af4a-208">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices from most vendors.</span></span> <span data-ttu-id="3af4a-209">O Azure RTOS NetX também utiliza a padrão da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo Azure RTOS NetX.</span><span class="sxs-lookup"><span data-stu-id="3af4a-209">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="3af4a-210">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="3af4a-210">Advanced technology</span></span>

<span data-ttu-id="3af4a-211">Azure RTOS NetX é uma tecnologia avançada que inclui o seguinte.</span><span class="sxs-lookup"><span data-stu-id="3af4a-211">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="3af4a-212">Piconet™ arquitetura.</span><span class="sxs-lookup"><span data-stu-id="3af4a-212">Piconet™ architecture.</span></span>
* <span data-ttu-id="3af4a-213">Escalagem automática.</span><span class="sxs-lookup"><span data-stu-id="3af4a-213">Automatic scaling.</span></span>
* <span data-ttu-id="3af4a-214">Tecnologia Fast-Path UDP™.</span><span class="sxs-lookup"><span data-stu-id="3af4a-214">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="3af4a-215">Gestão flexível de pacotes.</span><span class="sxs-lookup"><span data-stu-id="3af4a-215">Flexible packet management.</span></span>
* <span data-ttu-id="3af4a-216">API de cópia zero e implementação.</span><span class="sxs-lookup"><span data-stu-id="3af4a-216">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="3af4a-217">Apoio multi-habitação.</span><span class="sxs-lookup"><span data-stu-id="3af4a-217">Multi-homed support.</span></span>
* <span data-ttu-id="3af4a-218">Tempo limite opcional em toda a suspensão.</span><span class="sxs-lookup"><span data-stu-id="3af4a-218">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="3af4a-219">Suporte de encaminhamento estático.</span><span class="sxs-lookup"><span data-stu-id="3af4a-219">Static routing support.</span></span>
* <span data-ttu-id="3af4a-220">Suporte de análise do sistema Azure RTOS TraceX.</span><span class="sxs-lookup"><span data-stu-id="3af4a-220">Azure RTOS TraceX system analysis support.</span></span>
