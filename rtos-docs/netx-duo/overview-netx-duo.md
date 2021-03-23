---
title: Compreenda Azure RTOS NetX Duo
description: Azure RTOS NetX Duo é uma pilha de rede TCP/IP de qualidade industrial avançada, projetada especificamente para aplicações em tempo real e IoT profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826924"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="bbed7-103">Visão geral do Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="bbed7-104">A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT.</span><span class="sxs-lookup"><span data-stu-id="bbed7-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="bbed7-105">A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior.</span><span class="sxs-lookup"><span data-stu-id="bbed7-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="bbed7-106">O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="bbed7-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="bbed7-107">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="bbed7-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="bbed7-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="bbed7-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="bbed7-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="bbed7-109">MQTT</span></span>

* <span data-ttu-id="bbed7-110">Transporte de Telemetria de Fila de Mensagens (MQTT)</span><span class="sxs-lookup"><span data-stu-id="bbed7-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="bbed7-111">Mínimo de 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="bbed7-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="bbed7-112">APIs intuitivos de MQTT: *nx_mqtt_*\*</span><span class="sxs-lookup"><span data-stu-id="bbed7-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="bbed7-113">IP automático</span><span class="sxs-lookup"><span data-stu-id="bbed7-113">Auto IP</span></span>

* <span data-ttu-id="bbed7-114">Atribuição automática de endereços IPv4</span><span class="sxs-lookup"><span data-stu-id="bbed7-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="bbed7-115">Mínimo 1.2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="bbed7-116">APIs autoIP intuitivos: *nx_autoip_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="bbed7-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="bbed7-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="bbed7-118">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="bbed7-118">HTTP 1.0</span></span>

* <span data-ttu-id="bbed7-119">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="bbed7-120">Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="bbed7-121">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="bbed7-121">Client and server support</span></span>
* <span data-ttu-id="bbed7-122">APIs intuitivos: *nx_http_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="bbed7-123">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="bbed7-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="bbed7-124">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="bbed7-125">Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="bbed7-126">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="bbed7-126">Client and server support</span></span>
* <span data-ttu-id="bbed7-127">Múltiplas sessões de clientes recebidas</span><span class="sxs-lookup"><span data-stu-id="bbed7-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="bbed7-128">Texto simples e HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="bbed7-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="bbed7-129">Suporte de ligação persistente</span><span class="sxs-lookup"><span data-stu-id="bbed7-129">Persistent connection support</span></span>
* <span data-ttu-id="bbed7-130">Upload de ficheiros multipart</span><span class="sxs-lookup"><span data-stu-id="bbed7-130">Multipart file upload</span></span>
* <span data-ttu-id="bbed7-131">Totalmente integrado com Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="bbed7-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="bbed7-132">APIs intuitivos: *nx_web_http \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="bbed7-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="bbed7-133">SMTP</span></span>

* <span data-ttu-id="bbed7-134">Protocolo de transferência simples do centro comercial (SMTP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="bbed7-135">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-136">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="bbed7-136">Client support</span></span>
* <span data-ttu-id="bbed7-137">APIs intuitivos: *nx_smtp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="bbed7-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="bbed7-138">DHCP</span></span>

* <span data-ttu-id="bbed7-139">Protocolo DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="bbed7-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="bbed7-140">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="bbed7-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-141">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="bbed7-141">Client and server support</span></span>
* <span data-ttu-id="bbed7-142">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="bbed7-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="bbed7-143">APIs intuitivos do DHCP: *nx_dhcp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="bbed7-144">NAT</span><span class="sxs-lookup"><span data-stu-id="bbed7-144">NAT</span></span>

* <span data-ttu-id="bbed7-145">Tradução de Endereços de Rede (NAT)</span><span class="sxs-lookup"><span data-stu-id="bbed7-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="bbed7-146">Pegada mínima de 3,5K6 e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-147">Suporte de endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="bbed7-147">IPv4 address support</span></span>
* <span data-ttu-id="bbed7-148">APIs nat intuitivos: *nx_nat_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="bbed7-149">NAT só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="bbed7-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="bbed7-150">SNMP</span></span>

* <span data-ttu-id="bbed7-151">SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="bbed7-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="bbed7-152">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-153">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="bbed7-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="bbed7-154">APIs intuitivos do SNMP: *nx_snmp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="bbed7-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="bbed7-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="bbed7-156">Sistema de Nomes de Domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="bbed7-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="bbed7-157">Sistema de Nome de Domínio Multicast (mDNS)</span><span class="sxs-lookup"><span data-stu-id="bbed7-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="bbed7-158">Descoberta de serviço baseada em DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="bbed7-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="bbed7-159">DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada</span><span class="sxs-lookup"><span data-stu-id="bbed7-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-160">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="bbed7-160">Client support</span></span>
* <span data-ttu-id="bbed7-161">APIs intuitivos: *nx_dns_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="bbed7-162">mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="bbed7-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="bbed7-163">P0P3</span></span>

* <span data-ttu-id="bbed7-164">Protocolo dos Correios Versão 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="bbed7-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="bbed7-165">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-166">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="bbed7-166">Client support</span></span>
* <span data-ttu-id="bbed7-167">APIs P0P3 intuitivo: *nx_pop3_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="bbed7-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="bbed7-168">TELNET</span></span>

* <span data-ttu-id="bbed7-169">Pegada mínima de 0,5 KB e 0,3 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-170">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="bbed7-170">Client and server support</span></span>
* <span data-ttu-id="bbed7-171">ApIs intuitivos telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="bbed7-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="bbed7-172">FTP, TFTP</span></span>

* <span data-ttu-id="bbed7-173">Protocolo de Transferência de Ficheiros (FTP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="bbed7-174">Protocolo TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="bbed7-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="bbed7-175">FTP Mínimo de 1,8 KB a 7.2 KB FLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-176">TFTP Mínimo de 1,7 KB a 2,4 KB FLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-177">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="bbed7-177">Client and server support</span></span>
* <span data-ttu-id="bbed7-178">APIs intuitivos de FTP e TFTP: *nx_ftp_ \** ou *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="bbed7-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="bbed7-179">PPP, PPPoE</span></span>

* <span data-ttu-id="bbed7-180">Protocolo Polnt-to-Point (PPP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="bbed7-181">Protocolo ponto a ponto sobre ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="bbed7-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="bbed7-182">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-183">APIs intuitivos de PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="bbed7-184">PPPoE só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="bbed7-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="bbed7-185">SNTP</span></span>

* <span data-ttu-id="bbed7-186">Protocolo simples do tempo de rede (SNTP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="bbed7-187">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="bbed7-188">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="bbed7-188">Client support</span></span>
* <span data-ttu-id="bbed7-189">APIs intuitivos: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="bbed7-190">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="bbed7-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="bbed7-191">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="bbed7-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="bbed7-192">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="bbed7-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="bbed7-193">Implementação rápida e zero-copy API</span><span class="sxs-lookup"><span data-stu-id="bbed7-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="bbed7-194">Todas as APIs têm <i>nx_\*</i> para identificar facilmente como Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="bbed7-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="bbed7-195">ApIs de bloqueio têm tempo limite opcional de fio</span><span class="sxs-lookup"><span data-stu-id="bbed7-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="bbed7-196">Consulte [o Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) para mais detalhes</span><span class="sxs-lookup"><span data-stu-id="bbed7-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="bbed7-197">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="bbed7-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="bbed7-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="bbed7-198">IGMP</span></span>

* <span data-ttu-id="bbed7-199">Protocolo de Gestão do Grupo de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="bbed7-200">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="bbed7-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="bbed7-201">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="bbed7-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="bbed7-202">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-203">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="bbed7-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="bbed7-204">Traços de nível do sistema via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="bbed7-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="bbed7-205">APIs intuitivos do IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="bbed7-206">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="bbed7-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="bbed7-207">Segurança da camada de transporte de datagram (DTLS) 1.0 e 1.2</span><span class="sxs-lookup"><span data-stu-id="bbed7-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="bbed7-208">Flash mínimo de 11 KB</span><span class="sxs-lookup"><span data-stu-id="bbed7-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="bbed7-209">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="bbed7-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="bbed7-210">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="bbed7-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="bbed7-211">Totalmente integrado com tomadas UDP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="bbed7-212">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="bbed7-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="bbed7-213">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="bbed7-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="bbed7-214">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="bbed7-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="bbed7-215">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="bbed7-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="bbed7-216">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="bbed7-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="bbed7-217">Segurança da Camada de Transporte (TLS) 1.0, 1.1 e 1.2</span><span class="sxs-lookup"><span data-stu-id="bbed7-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="bbed7-218">Mínimo de 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="bbed7-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="bbed7-219">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="bbed7-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="bbed7-220">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="bbed7-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="bbed7-221">Totalmente integrado com tomadas Azure RTOS NetX Duo TCP</span><span class="sxs-lookup"><span data-stu-id="bbed7-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="bbed7-222">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="bbed7-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="bbed7-223">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="bbed7-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="bbed7-224">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="bbed7-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="bbed7-225">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="bbed7-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="bbed7-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="bbed7-226">ICMP</span></span>

* <span data-ttu-id="bbed7-227">Protocolo de mensagem de controlo da Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="bbed7-228">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="bbed7-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="bbed7-229">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="bbed7-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="bbed7-230">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-231">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="bbed7-231">Ping request and ping response</span></span>
* <span data-ttu-id="bbed7-232">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="bbed7-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="bbed7-233">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="bbed7-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bbed7-234">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="bbed7-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="bbed7-235">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bbed7-236">APIs intuitivos do ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="bbed7-237">UDP</span><span class="sxs-lookup"><span data-stu-id="bbed7-237">UDP</span></span>

* <span data-ttu-id="bbed7-238">Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="bbed7-239">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="bbed7-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="bbed7-240">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="bbed7-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="bbed7-241">RX 95 Mbps em 100 Mbps Ethernet, @100MHz MCU, 14% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="bbed7-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="bbed7-242">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="bbed7-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="bbed7-243">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="bbed7-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="bbed7-244">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="bbed7-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="bbed7-245">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-246">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="bbed7-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="bbed7-247">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="bbed7-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bbed7-248">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="bbed7-248">Optional UDP statistics</span></span>
* <span data-ttu-id="bbed7-249">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bbed7-250">APIs intuitivos da UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="bbed7-251">TCP</span><span class="sxs-lookup"><span data-stu-id="bbed7-251">TCP</span></span>

* <span data-ttu-id="bbed7-252">Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="bbed7-253">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="bbed7-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="bbed7-254">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="bbed7-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="bbed7-255">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="bbed7-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="bbed7-256">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="bbed7-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="bbed7-257">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="bbed7-257">Reliable connection</span></span>
* <span data-ttu-id="bbed7-258">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="bbed7-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="bbed7-259">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-260">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="bbed7-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="bbed7-261">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="bbed7-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bbed7-262">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="bbed7-262">Optional TCP statistics</span></span>
* <span data-ttu-id="bbed7-263">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bbed7-264">APIs intuitivos de TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="bbed7-265">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="bbed7-265">ARP/RARP</span></span>

* <span data-ttu-id="bbed7-266">Protocolo de Resolução de Endereços (ARP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="bbed7-267">Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="bbed7-268">Mínimo de 1,7 KB FLASH, tamanho RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="bbed7-269">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt</span><span class="sxs-lookup"><span data-stu-id="bbed7-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="bbed7-270">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-271">Cache ARP flexível e definido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="bbed7-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="bbed7-272">Suporte gratuito da ARP</span><span class="sxs-lookup"><span data-stu-id="bbed7-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="bbed7-273">Estatísticas opcionais de ARP/RARP determinadas por aplicação</span><span class="sxs-lookup"><span data-stu-id="bbed7-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="bbed7-274">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bbed7-275">APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="bbed7-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="bbed7-276">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="bbed7-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="bbed7-277">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="bbed7-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="bbed7-278">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM</span><span class="sxs-lookup"><span data-stu-id="bbed7-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="bbed7-279">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="bbed7-279">Piconet™ architecture</span></span>
* <span data-ttu-id="bbed7-280">Rápido, perto do desempenho da velocidade de arame</span><span class="sxs-lookup"><span data-stu-id="bbed7-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="bbed7-281">Suporte de interface múltipla</span><span class="sxs-lookup"><span data-stu-id="bbed7-281">Multiple interface support</span></span>
* <span data-ttu-id="bbed7-282">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="bbed7-282">Multihomed support</span></span>
* <span data-ttu-id="bbed7-283">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="bbed7-283">Static routing support</span></span>
* <span data-ttu-id="bbed7-284">Suporte de fragmentação/remontagem de IP</span><span class="sxs-lookup"><span data-stu-id="bbed7-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="bbed7-285">Suporte de endereço IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="bbed7-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="bbed7-286">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="bbed7-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="bbed7-287">Certificação de logotipo pronto da fase II IPv6</span><span class="sxs-lookup"><span data-stu-id="bbed7-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="bbed7-288">Estatísticas IP opcionais</span><span class="sxs-lookup"><span data-stu-id="bbed7-288">Optional IP statistics</span></span>
* <span data-ttu-id="bbed7-289">Interface de controlador de camada física bem definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="bbed7-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="bbed7-290">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="bbed7-291">APIs intuitivos da camada IP: *\* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="bbed7-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="bbed7-292">Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="bbed7-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="bbed7-293">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="bbed7-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="bbed7-294">Segurança do Protocolo de Internet (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="bbed7-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="bbed7-295">Camada IP</span><span class="sxs-lookup"><span data-stu-id="bbed7-295">IP layer</span></span>
* <span data-ttu-id="bbed7-296">Suporte cripto de hardware</span><span class="sxs-lookup"><span data-stu-id="bbed7-296">Hardware crypto support</span></span>
* <span data-ttu-id="bbed7-297">Suporte cripto de software, incluindo:</span><span class="sxs-lookup"><span data-stu-id="bbed7-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="bbed7-298">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="bbed7-298">DES, 3DES</span></span>
    * <span data-ttu-id="bbed7-299">AES</span><span class="sxs-lookup"><span data-stu-id="bbed7-299">AES</span></span>
    * <span data-ttu-id="bbed7-300">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="bbed7-300">HMAC-MD5</span></span>
    * <span data-ttu-id="bbed7-301">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="bbed7-301">HMAC-SHA1</span></span>
* <span data-ttu-id="bbed7-302">Suporte à Internet Key Exchange (IKE) Versão 2</span><span class="sxs-lookup"><span data-stu-id="bbed7-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="bbed7-303">IPsec Intuitivo APIs: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="bbed7-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="bbed7-304">IPsec só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="bbed7-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="bbed7-305">Pequena pegada</span><span class="sxs-lookup"><span data-stu-id="bbed7-305">Small-footprint</span></span>

<span data-ttu-id="bbed7-306">O Azure RTOS NetX Duo tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP.</span><span class="sxs-lookup"><span data-stu-id="bbed7-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="bbed7-307">Para a funcionalidade TCP, são necessários mais 10 KB a 13 KB de memória da área de instrução.</span><span class="sxs-lookup"><span data-stu-id="bbed7-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="bbed7-308">O uso do Azure RTOS NetX Duo RAM varia tipicamente de 2,6 KB a 3,6 KB mais a memória do pacote pool, que é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="bbed7-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="bbed7-309">Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS NetX Duo escala automaticamente com base nos serviços utilizados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="bbed7-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="bbed7-310">Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="bbed7-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="bbed7-311">Execução rápida</span><span class="sxs-lookup"><span data-stu-id="bbed7-311">Fast execution</span></span>

<span data-ttu-id="bbed7-312">O Azure RTOS NetX Duo fornece uma implementação de envio/receção de pacotes de cópia zero, altamente integrada com a Azure RTOS ThreadX, para obter o desempenho mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="bbed7-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="bbed7-313">Por exemplo, o Azure RTOS NetX Duo pode normalmente obter perto de transferências de dados de velocidade bancária num processador de 80 MHz (ou menos), utilizando apenas uma pequena percentagem dos ciclos do processador.</span><span class="sxs-lookup"><span data-stu-id="bbed7-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="bbed7-314">Simples e fácil de usar</span><span class="sxs-lookup"><span data-stu-id="bbed7-314">Simple, easy-to-use</span></span>

<span data-ttu-id="bbed7-315">O Azure RTOS NetX Duo API é intuitivo, simples e altamente funcional.</span><span class="sxs-lookup"><span data-stu-id="bbed7-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="bbed7-316">Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" ou nomes altamente abreviados que são tão comuns em outros produtos de networking.</span><span class="sxs-lookup"><span data-stu-id="bbed7-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="bbed7-317">Todas as APIs Azure RTOS NetX Duo têm uma *nx_* líder e seguem uma convenção de nomeação de substantivos.</span><span class="sxs-lookup"><span data-stu-id="bbed7-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="bbed7-318">Além disso, existe uma consistência funcional em toda a API.</span><span class="sxs-lookup"><span data-stu-id="bbed7-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="bbed7-319">Por exemplo, todas as funções da API que suspendem têm um tempo limite opcional que funciona de forma idêntica.</span><span class="sxs-lookup"><span data-stu-id="bbed7-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="bbed7-320">Para aplicações antigas, o Azure RTOS NetX Duo oferece uma camada compatível com tomada BSD adicional.</span><span class="sxs-lookup"><span data-stu-id="bbed7-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="bbed7-321">Esta camada ajuda os desenvolvedores a migrar grandes aplicações de networking com facilidade.</span><span class="sxs-lookup"><span data-stu-id="bbed7-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="bbed7-322">Seguro e seguro</span><span class="sxs-lookup"><span data-stu-id="bbed7-322">Safe and secure</span></span>

<span data-ttu-id="bbed7-323">Azure RTOS NetX Duo está seguro.</span><span class="sxs-lookup"><span data-stu-id="bbed7-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="bbed7-324">Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS.</span><span class="sxs-lookup"><span data-stu-id="bbed7-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="bbed7-325">Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="bbed7-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="bbed7-326">O Microsoft Azure RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes.</span><span class="sxs-lookup"><span data-stu-id="bbed7-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="bbed7-327">Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.</span><span class="sxs-lookup"><span data-stu-id="bbed7-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="bbed7-328">Pré-certificada pela TUV e UL para muitas normas de segurança</span><span class="sxs-lookup"><span data-stu-id="bbed7-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="bbed7-329">A Azure RTOS NetX Duo foi certificada pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128.</span><span class="sxs-lookup"><span data-stu-id="bbed7-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="bbed7-330">A certificação confirma que o Azure RTOS NetX Duo pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais altos níveis de integridade da segurança da IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional de sistemas de segurança electrónica, eletrônicos e programáveis".</span><span class="sxs-lookup"><span data-stu-id="bbed7-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="bbed7-331">A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo.</span><span class="sxs-lookup"><span data-stu-id="bbed7-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="bbed7-332">A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.</span><span class="sxs-lookup"><span data-stu-id="bbed7-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="Certificação SGS-TUV":::

<span data-ttu-id="bbed7-334">A Azure RTOS NetX Duo foi reconhecida pela UL pelo cumprimento do anexo H da UL 60730-1, do CSA E60730-1 Anexo H, do IEC 60730-1 anexo H, ul 60335-1 anexo R, do IEC 60335-1 anexo R e das normas de segurança 1998 para as normas de segurança em componentes programáveis.</span><span class="sxs-lookup"><span data-stu-id="bbed7-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="bbed7-335">A UL é uma empresa global, independente e de ciência da segurança, com mais de um século de experiência em soluções de segurança inovadoras, que vão desde a adoção pública de eletricidade até avanços na sustentabilidade, energias renováveis e nanotecnologia.</span><span class="sxs-lookup"><span data-stu-id="bbed7-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="Certificação CRU UL":::

<span data-ttu-id="bbed7-337">Estão à venda artefactos (Certificado, Manual de Segurança, Relatório de Teste, etc.) associados às certificações TUV e UL.</span><span class="sxs-lookup"><span data-stu-id="bbed7-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="bbed7-338">Nos casos em que a aplicação necessita de certificação adicional, está disponível um serviço de certificação através da Microsoft para fornecer certificação chave-na-curva a vários padrões utilizando a plataforma de hardware real e até mesmo cobrindo o código de aplicação.</span><span class="sxs-lookup"><span data-stu-id="bbed7-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="bbed7-339">Contacte-nos para mais detalhes sobre o nosso serviço de certificação.</span><span class="sxs-lookup"><span data-stu-id="bbed7-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="bbed7-340">Certificação de segurança de critérios comuns EAL4+</span><span class="sxs-lookup"><span data-stu-id="bbed7-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="bbed7-341">A Azure RTOS obteve a certificação de segurança de critérios comuns EAL4+.</span><span class="sxs-lookup"><span data-stu-id="bbed7-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="bbed7-342">O Alvo de Evalution (TOE) abrange Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS e Azure RTOS NetX MQTT.</span><span class="sxs-lookup"><span data-stu-id="bbed7-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="bbed7-343">Isto representa os protocolos IoT mais típicos exigidos por sensores, dispositivos, routers de borda e gateways profundamente incorporados.</span><span class="sxs-lookup"><span data-stu-id="bbed7-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certificação EAL":::

<span data-ttu-id="bbed7-345">O Mecanismo de Avaliação de Segurança de TI utilizado para a certificação de segurança Microsoft Azure RTOS SC é Brightsight BV e a Autoridade de Certificação é SERTIT.</span><span class="sxs-lookup"><span data-stu-id="bbed7-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="bbed7-346">FIPS 140-2 Validado</span><span class="sxs-lookup"><span data-stu-id="bbed7-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="bbed7-347">As bibliotecas Azure RTOS NetX Crypto alcançaram a Normalização Federal de Processamento de Informação 140-2 (FIPS 140-2) certificação para software, que especifica requisitos para módulos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="bbed7-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="bbed7-348">O FIPS 140-2 requer que todas as agências e departamentos do governo federal que utilizem a segurança criptográfica cumpram padrões específicos relacionados com a força e capacidades de encriptação.</span><span class="sxs-lookup"><span data-stu-id="bbed7-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="bbed7-349">Estas normas de segurança criptográficas são também reconhecidas no Canadá e na União Europeia.</span><span class="sxs-lookup"><span data-stu-id="bbed7-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="bbed7-350">O laboratório de avaliação de Segurança da Informação utilizado para as bibliotecas Azure RTOS NetX Crypto foi atsec e a autoridade de certificação é o Instituto Nacional de Normalização e Tecnologia (NIST).</span><span class="sxs-lookup"><span data-stu-id="bbed7-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="bbed7-351">Reveja o site da [NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="bbed7-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="bbed7-352">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="bbed7-352">Interoperability verification</span></span>

<span data-ttu-id="bbed7-353">O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="bbed7-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="bbed7-355">O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="bbed7-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="bbed7-356">A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.</span><span class="sxs-lookup"><span data-stu-id="bbed7-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="bbed7-357">Solução IoT abrangente</span><span class="sxs-lookup"><span data-stu-id="bbed7-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="bbed7-358">O Azure RTOS NetX Duo tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP.</span><span class="sxs-lookup"><span data-stu-id="bbed7-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="bbed7-359">A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="bbed7-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="bbed7-360">Este suporte inclui os seguintes produtos de protocolo adicional:</span><span class="sxs-lookup"><span data-stu-id="bbed7-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="bbed7-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="bbed7-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="bbed7-362">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="bbed7-362">Advanced technology</span></span>

<span data-ttu-id="bbed7-363">Azure RTOS NetX Duo é uma tecnologia avançada que inclui:</span><span class="sxs-lookup"><span data-stu-id="bbed7-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="bbed7-364">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="bbed7-364">Piconet™ architecture</span></span>
* <span data-ttu-id="bbed7-365">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="bbed7-365">Automatic scaling</span></span>
* <span data-ttu-id="bbed7-366">Tecnologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="bbed7-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="bbed7-367">Gestão flexível de pacotes</span><span class="sxs-lookup"><span data-stu-id="bbed7-367">Flexible packet management</span></span>
* <span data-ttu-id="bbed7-368">API de cópia zero e implementação</span><span class="sxs-lookup"><span data-stu-id="bbed7-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="bbed7-369">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="bbed7-369">Multihomed support</span></span>
* <span data-ttu-id="bbed7-370">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="bbed7-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="bbed7-371">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="bbed7-371">Static routing support</span></span>
* <span data-ttu-id="bbed7-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="bbed7-372">IPsec</span></span>
* <span data-ttu-id="bbed7-373">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="bbed7-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="bbed7-374">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="bbed7-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="bbed7-375">O tempo de venda mais rápido</span><span class="sxs-lookup"><span data-stu-id="bbed7-375">Fastest time-to-market</span></span>

<span data-ttu-id="bbed7-376">O Azure RTOS NetX Duo é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter.</span><span class="sxs-lookup"><span data-stu-id="bbed7-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="bbed7-377">Como resultado, o NetX Duo é uma das pilhas TCP/IP mais populares para dispositivos IoT incorporados, incluindo muitos SoCs da Broadcom, Gainspan, etc. A nossa vantagem consistente no mercado baseia-se em:</span><span class="sxs-lookup"><span data-stu-id="bbed7-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="bbed7-378">Documentação de qualidade – por favor reveja [o nosso Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) e veja por si mesmo!</span><span class="sxs-lookup"><span data-stu-id="bbed7-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="bbed7-379">Disponibilidade completa de código fonte</span><span class="sxs-lookup"><span data-stu-id="bbed7-379">Complete source code availability</span></span>
* <span data-ttu-id="bbed7-380">API de fácil utilização</span><span class="sxs-lookup"><span data-stu-id="bbed7-380">Easy-to-use API</span></span>
* <span data-ttu-id="bbed7-381">Conjunto de funcionalidades abrangente e avançado</span><span class="sxs-lookup"><span data-stu-id="bbed7-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="bbed7-382">Uma licença simples</span><span class="sxs-lookup"><span data-stu-id="bbed7-382">One Simple License</span></span>

<span data-ttu-id="bbed7-383">Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.</span><span class="sxs-lookup"><span data-stu-id="bbed7-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="bbed7-384">Código fonte completo e de alta qualidade</span><span class="sxs-lookup"><span data-stu-id="bbed7-384">Full, highest-quality source code</span></span>

<span data-ttu-id="bbed7-385">Ao longo dos anos, o código fonte Azure RTOS NetX Duo estabeleceu a fasquia em qualidade e facilidade de compreensão.</span><span class="sxs-lookup"><span data-stu-id="bbed7-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="bbed7-386">Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.</span><span class="sxs-lookup"><span data-stu-id="bbed7-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="bbed7-387">Apoia as arquiteturas mais populares</span><span class="sxs-lookup"><span data-stu-id="bbed7-387">Supports most popular architectures</span></span>

<span data-ttu-id="bbed7-388">O Azure RTOS NetX Duo funciona com microprocessadores mais populares de 32/64 bits fora da caixa, totalmente testados e totalmente suportados, incluindo as seguintes arquiteturas avançadas:</span><span class="sxs-lookup"><span data-stu-id="bbed7-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="bbed7-389">**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="bbed7-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="bbed7-390">**Núcleo de Andes**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bbed7-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="bbed7-391">**Ambiqmicro**: pollo MCUs</span><span class="sxs-lookup"><span data-stu-id="bbed7-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="bbed7-392">**BRAÇO**: RM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="bbed7-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="bbed7-393">**Cadência**: Xtensa, Diamante</span><span class="sxs-lookup"><span data-stu-id="bbed7-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="bbed7-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi</span><span class="sxs-lookup"><span data-stu-id="bbed7-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="bbed7-395">**Cipreste**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bbed7-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="bbed7-396">**EnSilica**: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="bbed7-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="bbed7-397">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="bbed7-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="bbed7-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="bbed7-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="bbed7-399">**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="bbed7-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="bbed7-400">**Microsemi**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="bbed7-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="bbed7-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="bbed7-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="bbed7-402">**Renesas**: SH, HS, V850, RX, RZ, Sinergia</span><span class="sxs-lookup"><span data-stu-id="bbed7-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="bbed7-403">**Silício** Laboratórios: EFM32</span><span class="sxs-lookup"><span data-stu-id="bbed7-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="bbed7-404">**Sinopses**: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="bbed7-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="bbed7-405">**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="bbed7-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="bbed7-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="bbed7-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="bbed7-407">**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M</span><span class="sxs-lookup"><span data-stu-id="bbed7-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="bbed7-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="bbed7-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="bbed7-409">*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*</span><span class="sxs-lookup"><span data-stu-id="bbed7-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="bbed7-410">Serviços relacionados</span><span class="sxs-lookup"><span data-stu-id="bbed7-410">Related services</span></span>

<span data-ttu-id="bbed7-411">O módulo de segurança Azure Security Center for IoT RTOS fornece uma solução de segurança abrangente para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="bbed7-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="bbed7-412">O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bbed7-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="bbed7-413">Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span><span class="sxs-lookup"><span data-stu-id="bbed7-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bbed7-414">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="bbed7-414">Next steps</span></span>

<span data-ttu-id="bbed7-415">Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="bbed7-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
