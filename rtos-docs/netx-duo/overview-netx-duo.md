---
title: Compreenda Azure RTOS NetX Duo
description: Azure RTOS NetX Duo é uma pilha de rede TCP/IP de qualidade industrial avançada, projetada especificamente para aplicações em tempo real e IoT profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e3fe3bcc602f409cc76f3be47aca865bf8116697
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171340"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="3088e-103">Visão geral do Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="3088e-104">A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT.</span><span class="sxs-lookup"><span data-stu-id="3088e-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="3088e-105">A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior.</span><span class="sxs-lookup"><span data-stu-id="3088e-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="3088e-106">O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="3088e-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="3088e-107">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="3088e-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="3088e-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="3088e-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="3088e-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="3088e-109">MQTT</span></span>

* <span data-ttu-id="3088e-110">Transporte de Telemetria de Fila de Mensagens (MQTT)</span><span class="sxs-lookup"><span data-stu-id="3088e-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="3088e-111">Mínimo de 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="3088e-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="3088e-112">IP automático</span><span class="sxs-lookup"><span data-stu-id="3088e-112">Auto IP</span></span>

* <span data-ttu-id="3088e-113">Atribuição automática de endereços IPv4</span><span class="sxs-lookup"><span data-stu-id="3088e-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="3088e-114">Mínimo 1.2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="3088e-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="3088e-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="3088e-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="3088e-116">HTTP 1.0</span></span>

* <span data-ttu-id="3088e-117">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="3088e-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3088e-118">Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="3088e-119">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3088e-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="3088e-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="3088e-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="3088e-121">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="3088e-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3088e-122">Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="3088e-123">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3088e-123">Client and server support</span></span>
* <span data-ttu-id="3088e-124">Múltiplas sessões de clientes recebidas</span><span class="sxs-lookup"><span data-stu-id="3088e-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="3088e-125">Texto simples e HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="3088e-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="3088e-126">Suporte de ligação persistente</span><span class="sxs-lookup"><span data-stu-id="3088e-126">Persistent connection support</span></span>
* <span data-ttu-id="3088e-127">Upload de ficheiros multipart</span><span class="sxs-lookup"><span data-stu-id="3088e-127">Multipart file upload</span></span>
* <span data-ttu-id="3088e-128">Totalmente integrado com Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3088e-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="3088e-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="3088e-129">SMTP</span></span>

* <span data-ttu-id="3088e-130">Protocolo de transferência simples do centro comercial (SMTP)</span><span class="sxs-lookup"><span data-stu-id="3088e-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="3088e-131">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-132">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3088e-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="3088e-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="3088e-133">DHCP</span></span>

* <span data-ttu-id="3088e-134">Protocolo DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="3088e-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="3088e-135">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="3088e-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-136">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3088e-136">Client and server support</span></span>
* <span data-ttu-id="3088e-137">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="3088e-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="3088e-138">NAT</span><span class="sxs-lookup"><span data-stu-id="3088e-138">NAT</span></span>

* <span data-ttu-id="3088e-139">Tradução de Endereços de Rede (NAT)</span><span class="sxs-lookup"><span data-stu-id="3088e-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="3088e-140">Pegada mínima de 3,5K6 e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-141">Suporte de endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="3088e-141">IPv4 address support</span></span>
* <span data-ttu-id="3088e-142">NAT só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="3088e-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="3088e-143">SNMP</span></span>

* <span data-ttu-id="3088e-144">SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="3088e-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="3088e-145">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-146">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="3088e-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="3088e-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="3088e-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="3088e-148">Sistema de Nomes de Domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="3088e-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="3088e-149">Sistema de Nome de Domínio Multicast (mDNS)</span><span class="sxs-lookup"><span data-stu-id="3088e-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="3088e-150">Descoberta de serviço baseada em DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="3088e-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="3088e-151">DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada</span><span class="sxs-lookup"><span data-stu-id="3088e-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-152">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3088e-152">Client support</span></span>
* <span data-ttu-id="3088e-153">mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="3088e-154">P0P3</span><span class="sxs-lookup"><span data-stu-id="3088e-154">P0P3</span></span>

* <span data-ttu-id="3088e-155">Protocolo dos Correios Versão 3 (POP3)</span><span class="sxs-lookup"><span data-stu-id="3088e-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="3088e-156">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-157">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3088e-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="3088e-158">TELNET</span><span class="sxs-lookup"><span data-stu-id="3088e-158">TELNET</span></span>

* <span data-ttu-id="3088e-159">Pegada mínima de 0,5 KB e 0,3 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-160">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3088e-160">Client and server support</span></span>
* <span data-ttu-id="3088e-161">ApIs intuitivos telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="3088e-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="3088e-162">FTP, TFTP</span></span>

* <span data-ttu-id="3088e-163">Protocolo de Transferência de Ficheiros (FTP)</span><span class="sxs-lookup"><span data-stu-id="3088e-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="3088e-164">Protocolo TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="3088e-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="3088e-165">FTP Mínimo de 1,8 KB a 7.2 KB FLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-166">TFTP Mínimo de 1,7 KB a 2,4 KB FLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-167">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="3088e-167">Client and server support</span></span>
* <span data-ttu-id="3088e-168">APIs intuitivos de FTP e TFTP: *nx_ftp_ \** ou *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="3088e-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="3088e-169">PPP, PPPoE</span></span>

* <span data-ttu-id="3088e-170">Protocolo Polnt-to-Point (PPP)</span><span class="sxs-lookup"><span data-stu-id="3088e-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="3088e-171">Protocolo ponto a ponto sobre ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="3088e-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="3088e-172">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-173">APIs intuitivos de PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="3088e-174">PPPoE só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="3088e-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="3088e-175">SNTP</span></span>

* <span data-ttu-id="3088e-176">Protocolo simples do tempo de rede (SNTP)</span><span class="sxs-lookup"><span data-stu-id="3088e-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="3088e-177">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="3088e-178">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="3088e-178">Client support</span></span>
* <span data-ttu-id="3088e-179">APIs intuitivos: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="3088e-180">Azure RTOS NetX Duo API</span><span class="sxs-lookup"><span data-stu-id="3088e-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="3088e-181">API intuitiva e consistente</span><span class="sxs-lookup"><span data-stu-id="3088e-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="3088e-182">Convenção de nomeação de substantivos</span><span class="sxs-lookup"><span data-stu-id="3088e-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="3088e-183">Implementação rápida e zero-copy API</span><span class="sxs-lookup"><span data-stu-id="3088e-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="3088e-184">Todas as APIs têm <i>nx_\*</i> para identificar facilmente como Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="3088e-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="3088e-185">ApIs de bloqueio têm tempo limite opcional de fio</span><span class="sxs-lookup"><span data-stu-id="3088e-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="3088e-186">Consulte [o Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) para mais detalhes</span><span class="sxs-lookup"><span data-stu-id="3088e-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="3088e-187">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="3088e-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="3088e-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="3088e-188">IGMP</span></span>

* <span data-ttu-id="3088e-189">Protocolo de Gestão do Grupo de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="3088e-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="3088e-190">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="3088e-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3088e-191">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="3088e-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="3088e-192">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-193">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="3088e-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="3088e-194">Traços de nível do sistema via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="3088e-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="3088e-195">APIs intuitivos do IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="3088e-196">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="3088e-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="3088e-197">Segurança da camada de transporte de datagram (DTLS) 1.0 e 1.2</span><span class="sxs-lookup"><span data-stu-id="3088e-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="3088e-198">Flash mínimo de 11 KB</span><span class="sxs-lookup"><span data-stu-id="3088e-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="3088e-199">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="3088e-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3088e-200">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="3088e-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3088e-201">Totalmente integrado com tomadas UDP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="3088e-202">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="3088e-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="3088e-203">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="3088e-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3088e-204">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="3088e-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3088e-205">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="3088e-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="3088e-206">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3088e-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="3088e-207">Segurança da Camada de Transporte (TLS) 1.0, 1.1 e 1.2</span><span class="sxs-lookup"><span data-stu-id="3088e-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="3088e-208">Mínimo de 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="3088e-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="3088e-209">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="3088e-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3088e-210">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="3088e-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3088e-211">Totalmente integrado com tomadas Azure RTOS NetX Duo TCP</span><span class="sxs-lookup"><span data-stu-id="3088e-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="3088e-212">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="3088e-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="3088e-213">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="3088e-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3088e-214">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="3088e-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3088e-215">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="3088e-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="3088e-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="3088e-216">ICMP</span></span>

* <span data-ttu-id="3088e-217">Protocolo de mensagem de controlo da Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="3088e-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="3088e-218">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="3088e-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3088e-219">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="3088e-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="3088e-220">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-221">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="3088e-221">Ping request and ping response</span></span>
* <span data-ttu-id="3088e-222">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="3088e-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="3088e-223">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3088e-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3088e-224">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="3088e-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="3088e-225">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3088e-226">APIs intuitivos do ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="3088e-227">UDP</span><span class="sxs-lookup"><span data-stu-id="3088e-227">UDP</span></span>

* <span data-ttu-id="3088e-228">Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="3088e-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="3088e-229">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="3088e-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="3088e-230">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="3088e-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3088e-231">RX 95 Mbps em 100 Mbps Ethernet, @100MHz MCU, 14% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="3088e-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="3088e-232">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="3088e-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="3088e-233">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="3088e-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="3088e-234">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="3088e-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="3088e-235">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-236">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="3088e-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="3088e-237">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3088e-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3088e-238">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="3088e-238">Optional UDP statistics</span></span>
* <span data-ttu-id="3088e-239">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3088e-240">APIs intuitivos da UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="3088e-241">TCP</span><span class="sxs-lookup"><span data-stu-id="3088e-241">TCP</span></span>

* <span data-ttu-id="3088e-242">Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="3088e-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="3088e-243">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="3088e-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="3088e-244">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="3088e-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3088e-245">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="3088e-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="3088e-246">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="3088e-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="3088e-247">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="3088e-247">Reliable connection</span></span>
* <span data-ttu-id="3088e-248">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="3088e-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="3088e-249">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-250">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="3088e-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="3088e-251">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3088e-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3088e-252">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="3088e-252">Optional TCP statistics</span></span>
* <span data-ttu-id="3088e-253">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3088e-254">APIs intuitivos de TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="3088e-255">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="3088e-255">ARP/RARP</span></span>

* <span data-ttu-id="3088e-256">Protocolo de Resolução de Endereços (ARP)</span><span class="sxs-lookup"><span data-stu-id="3088e-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="3088e-257">Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="3088e-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="3088e-258">Mínimo de 1,7 KB FLASH, tamanho RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="3088e-259">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt</span><span class="sxs-lookup"><span data-stu-id="3088e-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="3088e-260">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-261">Cache ARP flexível e definido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="3088e-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="3088e-262">Suporte gratuito da ARP</span><span class="sxs-lookup"><span data-stu-id="3088e-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="3088e-263">Estatísticas opcionais de ARP/RARP determinadas por aplicação</span><span class="sxs-lookup"><span data-stu-id="3088e-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="3088e-264">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3088e-265">APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="3088e-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="3088e-266">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="3088e-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="3088e-267">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="3088e-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="3088e-268">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM</span><span class="sxs-lookup"><span data-stu-id="3088e-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="3088e-269">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="3088e-269">Piconet™ architecture</span></span>
* <span data-ttu-id="3088e-270">Rápido, perto do desempenho da velocidade de arame</span><span class="sxs-lookup"><span data-stu-id="3088e-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="3088e-271">Suporte de interface múltipla</span><span class="sxs-lookup"><span data-stu-id="3088e-271">Multiple interface support</span></span>
* <span data-ttu-id="3088e-272">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="3088e-272">Multihomed support</span></span>
* <span data-ttu-id="3088e-273">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="3088e-273">Static routing support</span></span>
* <span data-ttu-id="3088e-274">Suporte de fragmentação/remontagem de IP</span><span class="sxs-lookup"><span data-stu-id="3088e-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="3088e-275">Suporte de endereço IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="3088e-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="3088e-276">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="3088e-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3088e-277">Certificação de logotipo pronto da fase II IPv6</span><span class="sxs-lookup"><span data-stu-id="3088e-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="3088e-278">Estatísticas IP opcionais</span><span class="sxs-lookup"><span data-stu-id="3088e-278">Optional IP statistics</span></span>
* <span data-ttu-id="3088e-279">Interface de controlador de camada física bem definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="3088e-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="3088e-280">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3088e-281">APIs intuitivos da camada IP: *\* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="3088e-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="3088e-282">Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="3088e-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="3088e-283">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="3088e-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="3088e-284">Segurança do Protocolo de Internet (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="3088e-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="3088e-285">Camada IP</span><span class="sxs-lookup"><span data-stu-id="3088e-285">IP layer</span></span>
* <span data-ttu-id="3088e-286">Suporte cripto de hardware</span><span class="sxs-lookup"><span data-stu-id="3088e-286">Hardware crypto support</span></span>
* <span data-ttu-id="3088e-287">Suporte cripto de software, incluindo:</span><span class="sxs-lookup"><span data-stu-id="3088e-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="3088e-288">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="3088e-288">DES, 3DES</span></span>
    * <span data-ttu-id="3088e-289">AES</span><span class="sxs-lookup"><span data-stu-id="3088e-289">AES</span></span>
    * <span data-ttu-id="3088e-290">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="3088e-290">HMAC-MD5</span></span>
    * <span data-ttu-id="3088e-291">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="3088e-291">HMAC-SHA1</span></span>
* <span data-ttu-id="3088e-292">Suporte à Internet Key Exchange (IKE) Versão 2</span><span class="sxs-lookup"><span data-stu-id="3088e-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="3088e-293">IPsec Intuitivo APIs: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="3088e-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="3088e-294">IPsec só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3088e-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="3088e-295">Seguro e seguro</span><span class="sxs-lookup"><span data-stu-id="3088e-295">Safe and secure</span></span>

<span data-ttu-id="3088e-296">Azure RTOS NetX Duo está seguro.</span><span class="sxs-lookup"><span data-stu-id="3088e-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="3088e-297">Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS.</span><span class="sxs-lookup"><span data-stu-id="3088e-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="3088e-298">Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="3088e-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="3088e-299">O Microsoft Azure RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes.</span><span class="sxs-lookup"><span data-stu-id="3088e-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="3088e-300">Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.</span><span class="sxs-lookup"><span data-stu-id="3088e-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="3088e-301">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="3088e-301">Interoperability verification</span></span>

<span data-ttu-id="3088e-302">O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="3088e-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="3088e-304">O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="3088e-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="3088e-305">A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.</span><span class="sxs-lookup"><span data-stu-id="3088e-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="3088e-306">Solução IoT abrangente</span><span class="sxs-lookup"><span data-stu-id="3088e-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="3088e-307">A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="3088e-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="3088e-308">Este suporte inclui os seguintes produtos de protocolo adicional.</span><span class="sxs-lookup"><span data-stu-id="3088e-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="3088e-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="3088e-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="3088e-310">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="3088e-310">Advanced technology</span></span>

<span data-ttu-id="3088e-311">Azure RTOS NetX Duo é uma tecnologia avançada que inclui:</span><span class="sxs-lookup"><span data-stu-id="3088e-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="3088e-312">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="3088e-312">Piconet™ architecture</span></span>
* <span data-ttu-id="3088e-313">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="3088e-313">Automatic scaling</span></span>
* <span data-ttu-id="3088e-314">Tecnologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="3088e-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="3088e-315">Gestão flexível de pacotes</span><span class="sxs-lookup"><span data-stu-id="3088e-315">Flexible packet management</span></span>
* <span data-ttu-id="3088e-316">API de cópia zero e implementação</span><span class="sxs-lookup"><span data-stu-id="3088e-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="3088e-317">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="3088e-317">Multihomed support</span></span>
* <span data-ttu-id="3088e-318">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="3088e-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3088e-319">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="3088e-319">Static routing support</span></span>
* <span data-ttu-id="3088e-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="3088e-320">IPsec</span></span>
* <span data-ttu-id="3088e-321">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="3088e-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="3088e-322">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="3088e-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="3088e-323">Serviços relacionados</span><span class="sxs-lookup"><span data-stu-id="3088e-323">Related services</span></span>

<span data-ttu-id="3088e-324">O módulo de segurança Azure Security Center for IoT RTOS fornece uma solução de segurança abrangente para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="3088e-324">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="3088e-325">O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3088e-325">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="3088e-326">Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span><span class="sxs-lookup"><span data-stu-id="3088e-326">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3088e-327">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="3088e-327">Next steps</span></span>

<span data-ttu-id="3088e-328">Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="3088e-328">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
