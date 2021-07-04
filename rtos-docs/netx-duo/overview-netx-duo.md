---
title: Compreenda Azure RTOS NetX Duo
description: Azure RTOS NetX Duo é uma pilha de rede TCP/IP de qualidade industrial avançada, projetada especificamente para aplicações em tempo real e IoT profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549340"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="64b2c-103">Visão geral do Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="64b2c-104">A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT.</span><span class="sxs-lookup"><span data-stu-id="64b2c-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="64b2c-105">A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior.</span><span class="sxs-lookup"><span data-stu-id="64b2c-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="64b2c-106">O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="64b2c-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="64b2c-107">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="64b2c-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="64b2c-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="64b2c-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="64b2c-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="64b2c-109">MQTT</span></span>

* <span data-ttu-id="64b2c-110">Transporte de Telemetria de Fila de Mensagens (MQTT)</span><span class="sxs-lookup"><span data-stu-id="64b2c-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="64b2c-111">Mínimo de 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="64b2c-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="64b2c-112">IP automático</span><span class="sxs-lookup"><span data-stu-id="64b2c-112">Auto IP</span></span>

* <span data-ttu-id="64b2c-113">Atribuição automática de endereços IPv4</span><span class="sxs-lookup"><span data-stu-id="64b2c-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="64b2c-114">Mínimo 1.2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="64b2c-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="64b2c-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="64b2c-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="64b2c-116">HTTP 1.0</span></span>

* <span data-ttu-id="64b2c-117">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="64b2c-118">Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="64b2c-119">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="64b2c-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="64b2c-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="64b2c-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="64b2c-121">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="64b2c-122">Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="64b2c-123">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="64b2c-123">Client and server support</span></span>
* <span data-ttu-id="64b2c-124">Múltiplas sessões de clientes recebidas</span><span class="sxs-lookup"><span data-stu-id="64b2c-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="64b2c-125">Texto simples e HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="64b2c-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="64b2c-126">Suporte de ligação persistente</span><span class="sxs-lookup"><span data-stu-id="64b2c-126">Persistent connection support</span></span>
* <span data-ttu-id="64b2c-127">Upload de ficheiros multipart</span><span class="sxs-lookup"><span data-stu-id="64b2c-127">Multipart file upload</span></span>
* <span data-ttu-id="64b2c-128">Totalmente integrado com Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="64b2c-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="64b2c-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="64b2c-129">SMTP</span></span>

* <span data-ttu-id="64b2c-130">Protocolo de transferência simples do centro comercial (SMTP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="64b2c-131">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-132">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="64b2c-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="64b2c-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="64b2c-133">DHCP</span></span>

* <span data-ttu-id="64b2c-134">Protocolo DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="64b2c-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="64b2c-135">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="64b2c-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-136">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="64b2c-136">Client and server support</span></span>
* <span data-ttu-id="64b2c-137">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="64b2c-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="64b2c-138">NAT</span><span class="sxs-lookup"><span data-stu-id="64b2c-138">NAT</span></span>

* <span data-ttu-id="64b2c-139">Tradução de Endereços de Rede (NAT)</span><span class="sxs-lookup"><span data-stu-id="64b2c-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="64b2c-140">Pegada mínima de 3,5K6 e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-141">Suporte de endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="64b2c-141">IPv4 address support</span></span>
* <span data-ttu-id="64b2c-142">NAT só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="64b2c-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="64b2c-143">SNMP</span></span>

* <span data-ttu-id="64b2c-144">SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="64b2c-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="64b2c-145">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-146">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="64b2c-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="64b2c-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="64b2c-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="64b2c-148">Sistema de Nomes de Domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="64b2c-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="64b2c-149">Sistema de Nome de Domínio Multicast (mDNS)</span><span class="sxs-lookup"><span data-stu-id="64b2c-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="64b2c-150">Descoberta de serviço baseada em DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="64b2c-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="64b2c-151">DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada</span><span class="sxs-lookup"><span data-stu-id="64b2c-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-152">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="64b2c-152">Client support</span></span>
* <span data-ttu-id="64b2c-153">mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="64b2c-154">POP3</span><span class="sxs-lookup"><span data-stu-id="64b2c-154">POP3</span></span>

* <span data-ttu-id="64b2c-155">Versão 3 do Protocolo de Office (POP3)</span><span class="sxs-lookup"><span data-stu-id="64b2c-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="64b2c-156">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-157">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="64b2c-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="64b2c-158">TELNET</span><span class="sxs-lookup"><span data-stu-id="64b2c-158">TELNET</span></span>

* <span data-ttu-id="64b2c-159">Pegada mínima de 0,5 KB e 0,3 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-160">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="64b2c-160">Client and server support</span></span>
* <span data-ttu-id="64b2c-161">ApIs intuitivos telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="64b2c-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="64b2c-162">FTP, TFTP</span></span>

* <span data-ttu-id="64b2c-163">Protocolo de Transferência de Ficheiros (FTP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="64b2c-164">Protocolo TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="64b2c-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="64b2c-165">FTP Mínimo de 1,8 KB a 7.2 KB FLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-166">TFTP Mínimo de 1,7 KB a 2,4 KB FLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-167">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="64b2c-167">Client and server support</span></span>
* <span data-ttu-id="64b2c-168">APIs intuitivos de FTP e TFTP: *nx_ftp_ \** ou *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="64b2c-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="64b2c-169">PPP, PPPoE</span></span>

* <span data-ttu-id="64b2c-170">Protocolo Polnt-to-Point (PPP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="64b2c-171">Protocolo ponto a ponto sobre ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="64b2c-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="64b2c-172">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-173">APIs intuitivos de PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="64b2c-174">PPPoE só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="64b2c-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="64b2c-175">SNTP</span></span>

* <span data-ttu-id="64b2c-176">Protocolo simples do tempo de rede (SNTP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="64b2c-177">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="64b2c-178">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="64b2c-178">Client support</span></span>
* <span data-ttu-id="64b2c-179">APIs intuitivos: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="64b2c-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="64b2c-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="64b2c-181">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="64b2c-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="64b2c-182">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="64b2c-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="64b2c-183">Implementação rápida e zero-copy API</span><span class="sxs-lookup"><span data-stu-id="64b2c-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="64b2c-184">Todas as APIs têm <i>nx_\*</i> para identificar facilmente como Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="64b2c-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="64b2c-185">ApIs de bloqueio têm tempo limite opcional de fio</span><span class="sxs-lookup"><span data-stu-id="64b2c-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="64b2c-186">Consulte [o Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) para mais detalhes</span><span class="sxs-lookup"><span data-stu-id="64b2c-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="64b2c-187">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="64b2c-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="64b2c-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="64b2c-188">IGMP</span></span>

* <span data-ttu-id="64b2c-189">Protocolo de Gestão do Grupo de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="64b2c-190">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="64b2c-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="64b2c-191">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="64b2c-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="64b2c-192">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-193">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="64b2c-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="64b2c-194">Traços de nível do sistema via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="64b2c-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="64b2c-195">APIs intuitivos do IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="64b2c-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="64b2c-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="64b2c-197">Segurança da camada de transporte de datagram (DTLS) 1.0 e 1.2</span><span class="sxs-lookup"><span data-stu-id="64b2c-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="64b2c-198">Flash mínimo de 11 KB</span><span class="sxs-lookup"><span data-stu-id="64b2c-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="64b2c-199">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="64b2c-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="64b2c-200">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="64b2c-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="64b2c-201">Totalmente integrado com tomadas UDP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="64b2c-202">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="64b2c-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="64b2c-203">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="64b2c-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="64b2c-204">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="64b2c-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="64b2c-205">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="64b2c-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="64b2c-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="64b2c-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="64b2c-207">Segurança da Camada de Transporte (TLS) 1.0, 1.1 e 1.2</span><span class="sxs-lookup"><span data-stu-id="64b2c-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="64b2c-208">Mínimo de 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="64b2c-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="64b2c-209">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="64b2c-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="64b2c-210">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="64b2c-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="64b2c-211">Totalmente integrado com tomadas Azure RTOS NetX Duo TCP</span><span class="sxs-lookup"><span data-stu-id="64b2c-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="64b2c-212">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="64b2c-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="64b2c-213">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="64b2c-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="64b2c-214">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="64b2c-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="64b2c-215">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="64b2c-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="64b2c-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="64b2c-216">ICMP</span></span>

* <span data-ttu-id="64b2c-217">Protocolo de mensagem de controlo da Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="64b2c-218">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="64b2c-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="64b2c-219">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="64b2c-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="64b2c-220">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-221">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="64b2c-221">Ping request and ping response</span></span>
* <span data-ttu-id="64b2c-222">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="64b2c-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="64b2c-223">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="64b2c-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="64b2c-224">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="64b2c-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="64b2c-225">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="64b2c-226">APIs intuitivos do ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="64b2c-227">UDP</span><span class="sxs-lookup"><span data-stu-id="64b2c-227">UDP</span></span>

* <span data-ttu-id="64b2c-228">Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="64b2c-229">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="64b2c-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="64b2c-230">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="64b2c-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="64b2c-231">RX 95 Mbps em 100 Mbps Ethernet, @100MHz MCU, 14% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="64b2c-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="64b2c-232">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="64b2c-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="64b2c-233">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="64b2c-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="64b2c-234">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="64b2c-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="64b2c-235">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-236">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="64b2c-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="64b2c-237">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="64b2c-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="64b2c-238">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="64b2c-238">Optional UDP statistics</span></span>
* <span data-ttu-id="64b2c-239">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="64b2c-240">APIs intuitivos da UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="64b2c-241">TCP</span><span class="sxs-lookup"><span data-stu-id="64b2c-241">TCP</span></span>

* <span data-ttu-id="64b2c-242">Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="64b2c-243">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="64b2c-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="64b2c-244">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="64b2c-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="64b2c-245">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="64b2c-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="64b2c-246">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="64b2c-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="64b2c-247">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="64b2c-247">Reliable connection</span></span>
* <span data-ttu-id="64b2c-248">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="64b2c-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="64b2c-249">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-250">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="64b2c-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="64b2c-251">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="64b2c-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="64b2c-252">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="64b2c-252">Optional TCP statistics</span></span>
* <span data-ttu-id="64b2c-253">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="64b2c-254">APIs intuitivos de TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="64b2c-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="64b2c-255">ARP/RARP</span></span>

* <span data-ttu-id="64b2c-256">Protocolo de Resolução de Endereços (ARP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="64b2c-257">Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="64b2c-258">Mínimo de 1,7 KB FLASH, tamanho RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="64b2c-259">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt</span><span class="sxs-lookup"><span data-stu-id="64b2c-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="64b2c-260">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-261">Cache ARP flexível e definido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="64b2c-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="64b2c-262">Suporte gratuito da ARP</span><span class="sxs-lookup"><span data-stu-id="64b2c-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="64b2c-263">Estatísticas opcionais de ARP/RARP determinadas por aplicação</span><span class="sxs-lookup"><span data-stu-id="64b2c-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="64b2c-264">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="64b2c-265">APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="64b2c-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="64b2c-266">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="64b2c-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="64b2c-267">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="64b2c-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="64b2c-268">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM</span><span class="sxs-lookup"><span data-stu-id="64b2c-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="64b2c-269">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="64b2c-269">Piconet™ architecture</span></span>
* <span data-ttu-id="64b2c-270">Rápido, perto do desempenho da velocidade de arame</span><span class="sxs-lookup"><span data-stu-id="64b2c-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="64b2c-271">Suporte de interface múltipla</span><span class="sxs-lookup"><span data-stu-id="64b2c-271">Multiple interface support</span></span>
* <span data-ttu-id="64b2c-272">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="64b2c-272">Multihomed support</span></span>
* <span data-ttu-id="64b2c-273">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="64b2c-273">Static routing support</span></span>
* <span data-ttu-id="64b2c-274">Suporte de fragmentação/remontagem de IP</span><span class="sxs-lookup"><span data-stu-id="64b2c-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="64b2c-275">Suporte de endereço IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="64b2c-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="64b2c-276">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="64b2c-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="64b2c-277">Certificação de logotipo pronto da fase II IPv6</span><span class="sxs-lookup"><span data-stu-id="64b2c-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="64b2c-278">Estatísticas IP opcionais</span><span class="sxs-lookup"><span data-stu-id="64b2c-278">Optional IP statistics</span></span>
* <span data-ttu-id="64b2c-279">Interface de controlador de camada física bem definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="64b2c-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="64b2c-280">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="64b2c-281">APIs intuitivos da camada IP: *\* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="64b2c-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="64b2c-282">Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="64b2c-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="64b2c-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="64b2c-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="64b2c-284">Segurança do Protocolo de Internet (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="64b2c-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="64b2c-285">Camada IP</span><span class="sxs-lookup"><span data-stu-id="64b2c-285">IP layer</span></span>
* <span data-ttu-id="64b2c-286">Suporte cripto de hardware</span><span class="sxs-lookup"><span data-stu-id="64b2c-286">Hardware crypto support</span></span>
* <span data-ttu-id="64b2c-287">Suporte cripto de software, incluindo:</span><span class="sxs-lookup"><span data-stu-id="64b2c-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="64b2c-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="64b2c-288">DES, 3DES</span></span>
    * <span data-ttu-id="64b2c-289">AES</span><span class="sxs-lookup"><span data-stu-id="64b2c-289">AES</span></span>
    * <span data-ttu-id="64b2c-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="64b2c-290">HMAC-MD5</span></span>
    * <span data-ttu-id="64b2c-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="64b2c-291">HMAC-SHA1</span></span>
* <span data-ttu-id="64b2c-292">Suporte da Exchange da Internet (IKE) Versão 2</span><span class="sxs-lookup"><span data-stu-id="64b2c-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="64b2c-293">IPsec Intuitivo APIs: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="64b2c-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="64b2c-294">IPsec só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="64b2c-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="64b2c-295">Cofre e seguro</span><span class="sxs-lookup"><span data-stu-id="64b2c-295">Safe and secure</span></span>

<span data-ttu-id="64b2c-296">Azure RTOS NetX Duo está seguro.</span><span class="sxs-lookup"><span data-stu-id="64b2c-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="64b2c-297">Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS.</span><span class="sxs-lookup"><span data-stu-id="64b2c-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="64b2c-298">Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="64b2c-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="64b2c-299">Microsoft Azure O RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes.</span><span class="sxs-lookup"><span data-stu-id="64b2c-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="64b2c-300">Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.</span><span class="sxs-lookup"><span data-stu-id="64b2c-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="64b2c-301">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="64b2c-301">Interoperability verification</span></span>

<span data-ttu-id="64b2c-302">O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="64b2c-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="64b2c-304">O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="64b2c-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="64b2c-305">A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.</span><span class="sxs-lookup"><span data-stu-id="64b2c-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="64b2c-306">Solução IoT abrangente</span><span class="sxs-lookup"><span data-stu-id="64b2c-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="64b2c-307">A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="64b2c-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="64b2c-308">Este suporte inclui os seguintes produtos de protocolo adicional.</span><span class="sxs-lookup"><span data-stu-id="64b2c-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="64b2c-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="64b2c-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="64b2c-310">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="64b2c-310">Advanced technology</span></span>

<span data-ttu-id="64b2c-311">Azure RTOS NetX Duo é uma tecnologia avançada que inclui:</span><span class="sxs-lookup"><span data-stu-id="64b2c-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="64b2c-312">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="64b2c-312">Piconet™ architecture</span></span>
* <span data-ttu-id="64b2c-313">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="64b2c-313">Automatic scaling</span></span>
* <span data-ttu-id="64b2c-314">Tecnologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="64b2c-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="64b2c-315">Gestão flexível de pacotes</span><span class="sxs-lookup"><span data-stu-id="64b2c-315">Flexible packet management</span></span>
* <span data-ttu-id="64b2c-316">API de cópia zero e implementação</span><span class="sxs-lookup"><span data-stu-id="64b2c-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="64b2c-317">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="64b2c-317">Multihomed support</span></span>
* <span data-ttu-id="64b2c-318">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="64b2c-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="64b2c-319">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="64b2c-319">Static routing support</span></span>
* <span data-ttu-id="64b2c-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="64b2c-320">IPsec</span></span>
* <span data-ttu-id="64b2c-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="64b2c-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="64b2c-322">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="64b2c-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="64b2c-323">Serviços relacionados</span><span class="sxs-lookup"><span data-stu-id="64b2c-323">Related services</span></span>

### <a name="azure-iot"></a><span data-ttu-id="64b2c-324">Azure IoT</span><span class="sxs-lookup"><span data-stu-id="64b2c-324">Azure IoT</span></span>

<span data-ttu-id="64b2c-325">A NetX Duo inclui [o Azure IoT Middleware para Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), uma biblioteca específica da plataforma que funciona como uma camada de ligação entre o Azure RTOS e o Azure SDK para Embedded C para facilitar a conectividade aos serviços Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="64b2c-325">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="64b2c-326">Os objetivos de Azure IoT Middleware são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="64b2c-326">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="64b2c-327">Forneça as interfaces inteligentes do cliente (IoTHub_Client, DeviceProvisioning_Client) que os desenvolvedores precisam para as suas aplicações.</span><span class="sxs-lookup"><span data-stu-id="64b2c-327">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="64b2c-328">Orquestrou a interação entre o SDK Incorporado e a plataforma.</span><span class="sxs-lookup"><span data-stu-id="64b2c-328">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="64b2c-329">Fornecer inicialização da plataforma Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="64b2c-329">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="64b2c-330">IoT Plug e Suporte de Reprodução.</span><span class="sxs-lookup"><span data-stu-id="64b2c-330">IoT Plug and Play support.</span></span>
* <span data-ttu-id="64b2c-331">Capacidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="64b2c-331">Security capabilities.</span></span>
* <span data-ttu-id="64b2c-332">Limitação de recursos consciente.</span><span class="sxs-lookup"><span data-stu-id="64b2c-332">Resource limitation aware.</span></span>
* <span data-ttu-id="64b2c-333">Apoio ao protocolo.</span><span class="sxs-lookup"><span data-stu-id="64b2c-333">Protocol support.</span></span>

![Azure RTOS NetX Duo Serviços relacionados](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="64b2c-335">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="64b2c-335">Azure Defender</span></span>

<span data-ttu-id="64b2c-336">O módulo de segurança Azure Defender for IoT fornece uma solução de segurança abrangente para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="64b2c-336">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="64b2c-337">O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="64b2c-337">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="64b2c-338">Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span><span class="sxs-lookup"><span data-stu-id="64b2c-338">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="64b2c-339">Atualização do dispositivo para ioT hub</span><span class="sxs-lookup"><span data-stu-id="64b2c-339">Device Update for IoT Hub</span></span>

<span data-ttu-id="64b2c-340">A [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) é um serviço que lhe permite implementar atualizações over-the-air (OTA) para os seus dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="64b2c-340">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="64b2c-341">O módulo Device Update for IoT Hub é a implementação da Atualização do Dispositivo para OOT Hub Agent em Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="64b2c-341">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="64b2c-342">Fornece APIs simples para os construtores de dispositivos integrarem a capacidade de Atualização do Dispositivo na sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="64b2c-342">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="64b2c-343">Consulte as amostras dos principais conselhos de avaliação de semicondutores que incluem os guias de arranque para aprender a configurar, construir e implementar as atualizações over-the-air (OTA) para os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="64b2c-343">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="64b2c-344">E pode aprender mais detalhes sobre a utilização [de Device Update para IoT Hub com Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="64b2c-344">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="64b2c-345">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="64b2c-345">Next steps</span></span>

<span data-ttu-id="64b2c-346">Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="64b2c-346">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
