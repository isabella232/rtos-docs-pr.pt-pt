---
title: Compreenda Azure RTOS NetX Duo
description: Azure RTOS NetX Duo é uma pilha de rede TCP/IP de qualidade industrial avançada, projetada especificamente para aplicações em tempo real e IoT profundamente incorporadas.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b40a57bf385ddcf623ff7cbe0d2e798c547227d7
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754901"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="fb082-103">Visão geral do Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="fb082-104">A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT.</span><span class="sxs-lookup"><span data-stu-id="fb082-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="fb082-105">A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior.</span><span class="sxs-lookup"><span data-stu-id="fb082-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="fb082-106">O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS.</span><span class="sxs-lookup"><span data-stu-id="fb082-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="fb082-107">Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.</span><span class="sxs-lookup"><span data-stu-id="fb082-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="fb082-108">Protocolos da API</span><span class="sxs-lookup"><span data-stu-id="fb082-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="fb082-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="fb082-109">MQTT</span></span>

* <span data-ttu-id="fb082-110">Transporte de Telemetria de Fila de Mensagens (MQTT)</span><span class="sxs-lookup"><span data-stu-id="fb082-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="fb082-111">Mínimo de 2,7 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fb082-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="fb082-112">IP automático</span><span class="sxs-lookup"><span data-stu-id="fb082-112">Auto IP</span></span>

* <span data-ttu-id="fb082-113">Atribuição automática de endereços IPv4</span><span class="sxs-lookup"><span data-stu-id="fb082-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="fb082-114">Mínimo 1.2 KB, 300 bytes de RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="fb082-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="fb082-115">HTTP, HTTPS</span></span>
<span data-ttu-id="fb082-116">A NetX Duo suporta os seguintes protocolos HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fb082-116">NetX Duo supports the following HTTP/HTTPS protocols.</span></span>

#### <a name="http-10"></a><span data-ttu-id="fb082-117">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="fb082-117">HTTP 1.0</span></span>

* <span data-ttu-id="fb082-118">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="fb082-118">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fb082-119">Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-119">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="fb082-120">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="fb082-120">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="fb082-121">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="fb082-121">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="fb082-122">Protocolo de Transferência de Hipertexto(HTTP)</span><span class="sxs-lookup"><span data-stu-id="fb082-122">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fb082-123">Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-123">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="fb082-124">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="fb082-124">Client and server support</span></span>
* <span data-ttu-id="fb082-125">Múltiplas sessões de clientes recebidas</span><span class="sxs-lookup"><span data-stu-id="fb082-125">Multiple incoming client sessions</span></span>
* <span data-ttu-id="fb082-126">Texto simples e HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="fb082-126">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="fb082-127">Suporte de ligação persistente</span><span class="sxs-lookup"><span data-stu-id="fb082-127">Persistent connection support</span></span>
* <span data-ttu-id="fb082-128">Upload de ficheiros multipart</span><span class="sxs-lookup"><span data-stu-id="fb082-128">Multipart file upload</span></span>
* <span data-ttu-id="fb082-129">Totalmente integrado com Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="fb082-129">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="fb082-130">SMTP</span><span class="sxs-lookup"><span data-stu-id="fb082-130">SMTP</span></span>

* <span data-ttu-id="fb082-131">Protocolo de transferência simples do centro comercial (SMTP)</span><span class="sxs-lookup"><span data-stu-id="fb082-131">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="fb082-132">Pegada mínima de 4,1 KB e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-132">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-133">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="fb082-133">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="fb082-134">DHCP</span><span class="sxs-lookup"><span data-stu-id="fb082-134">DHCP</span></span>

* <span data-ttu-id="fb082-135">Protocolo DHCP (Dynamic Host Configuration Protocol)</span><span class="sxs-lookup"><span data-stu-id="fb082-135">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="fb082-136">Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB</span><span class="sxs-lookup"><span data-stu-id="fb082-136">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-137">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="fb082-137">Client and server support</span></span>
* <span data-ttu-id="fb082-138">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="fb082-138">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="fb082-139">NAT</span><span class="sxs-lookup"><span data-stu-id="fb082-139">NAT</span></span>

* <span data-ttu-id="fb082-140">Tradução de Endereços de Rede (NAT)</span><span class="sxs-lookup"><span data-stu-id="fb082-140">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="fb082-141">Pegada mínima de 3,5K6 e 0,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-141">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-142">Suporte de endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="fb082-142">IPv4 address support</span></span>
* <span data-ttu-id="fb082-143">NAT só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-143">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="fb082-144">SNMP</span><span class="sxs-lookup"><span data-stu-id="fb082-144">SNMP</span></span>

* <span data-ttu-id="fb082-145">SNMP (Simple Network Management Protocol)</span><span class="sxs-lookup"><span data-stu-id="fb082-145">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="fb082-146">Pegada mínima de 10,9 KB e 2,6 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-146">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-147">Apoio ao agente para VI, V2 e V3</span><span class="sxs-lookup"><span data-stu-id="fb082-147">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="fb082-148">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="fb082-148">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="fb082-149">Sistema de Nomes de Domínio (DNS)</span><span class="sxs-lookup"><span data-stu-id="fb082-149">Domain Name System (DNS)</span></span>
* <span data-ttu-id="fb082-150">Sistema de Nome de Domínio Multicast (mDNS)</span><span class="sxs-lookup"><span data-stu-id="fb082-150">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="fb082-151">Descoberta de serviço baseada em DNS (DNS-SD)</span><span class="sxs-lookup"><span data-stu-id="fb082-151">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="fb082-152">DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada</span><span class="sxs-lookup"><span data-stu-id="fb082-152">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-153">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="fb082-153">Client support</span></span>
* <span data-ttu-id="fb082-154">mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-154">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="fb082-155">POP3</span><span class="sxs-lookup"><span data-stu-id="fb082-155">POP3</span></span>

* <span data-ttu-id="fb082-156">Versão 3 do Protocolo de Office (POP3)</span><span class="sxs-lookup"><span data-stu-id="fb082-156">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="fb082-157">Pegada mínima de 8,1 KB e 1,4 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-157">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-158">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="fb082-158">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="fb082-159">TELNET</span><span class="sxs-lookup"><span data-stu-id="fb082-159">TELNET</span></span>

* <span data-ttu-id="fb082-160">Pegada mínima de 0,5 KB e 0,3 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-160">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-161">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="fb082-161">Client and server support</span></span>
* <span data-ttu-id="fb082-162">ApIs intuitivos telnet: *nx_telnet_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-162">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="fb082-163">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="fb082-163">FTP, TFTP</span></span>

* <span data-ttu-id="fb082-164">Protocolo de Transferência de Ficheiros (FTP)</span><span class="sxs-lookup"><span data-stu-id="fb082-164">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="fb082-165">Protocolo TFTP (Trivial File Transfer Protocol)</span><span class="sxs-lookup"><span data-stu-id="fb082-165">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="fb082-166">FTP Mínimo de 1,8 KB a 7.2 KB FLASH, 0,6 KB a 2,1 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-166">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-167">TFTP Mínimo de 1,7 KB a 2,4 KB FLASH, 0.3 KB a 1,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-167">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-168">Suporte ao cliente e ao servidor</span><span class="sxs-lookup"><span data-stu-id="fb082-168">Client and server support</span></span>
* <span data-ttu-id="fb082-169">APIs intuitivos de FTP e TFTP: *nx_ftp_ \** ou *nx_tftp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-169">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="fb082-170">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="fb082-170">PPP, PPPoE</span></span>

* <span data-ttu-id="fb082-171">Protocolo Polnt-to-Point (PPP)</span><span class="sxs-lookup"><span data-stu-id="fb082-171">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="fb082-172">Protocolo ponto a ponto sobre ethernet (PPPoE)</span><span class="sxs-lookup"><span data-stu-id="fb082-172">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="fb082-173">Pegada mínima de 7,1 KB e 3,8 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-173">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-174">APIs intuitivos de PPP: *nx_ppp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-174">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="fb082-175">PPPoE só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-175">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="fb082-176">SNTP</span><span class="sxs-lookup"><span data-stu-id="fb082-176">SNTP</span></span>

* <span data-ttu-id="fb082-177">Protocolo simples do tempo de rede (SNTP)</span><span class="sxs-lookup"><span data-stu-id="fb082-177">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="fb082-178">Mínimo 4 KB e 0,5 KB RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-178">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="fb082-179">Apoio ao cliente</span><span class="sxs-lookup"><span data-stu-id="fb082-179">Client support</span></span>
* <span data-ttu-id="fb082-180">APIs intuitivos: *nx_sntp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-180">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="legacy-code-support"></a><span data-ttu-id="fb082-181">Suporte de código legado</span><span class="sxs-lookup"><span data-stu-id="fb082-181">Legacy code support</span></span>

* <span data-ttu-id="fb082-182">Camada opcional de BSD para porting código de tomada legado</span><span class="sxs-lookup"><span data-stu-id="fb082-182">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="fb082-183">IGMP</span><span class="sxs-lookup"><span data-stu-id="fb082-183">IGMP</span></span>

* <span data-ttu-id="fb082-184">Protocolo de Gestão do Grupo de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="fb082-184">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="fb082-185">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="fb082-185">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fb082-186">Suporte ao grupo multicast IPv4</span><span class="sxs-lookup"><span data-stu-id="fb082-186">IPv4 multicast group support</span></span>
* <span data-ttu-id="fb082-187">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-187">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-188">Estatísticas opcionais do IGMP</span><span class="sxs-lookup"><span data-stu-id="fb082-188">Optional IGMP statistics</span></span>
* <span data-ttu-id="fb082-189">Traços de nível do sistema via Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="fb082-189">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="fb082-190">APIs intuitivos do IGMP: *nx_igmp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-190">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="fb082-191">Azure RTOS NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="fb082-191">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="fb082-192">Segurança da camada de transporte de datagram (DTLS) 1.0 e 1.2</span><span class="sxs-lookup"><span data-stu-id="fb082-192">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="fb082-193">Flash mínimo de 11 KB</span><span class="sxs-lookup"><span data-stu-id="fb082-193">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="fb082-194">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="fb082-194">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fb082-195">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="fb082-195">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fb082-196">Totalmente integrado com tomadas UDP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-196">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="fb082-197">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="fb082-197">Hardware Crypto Support</span></span>
* <span data-ttu-id="fb082-198">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="fb082-198">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fb082-199">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="fb082-199">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fb082-200">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="fb082-200">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="fb082-201">Azure RTOS NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="fb082-201">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="fb082-202">Segurança da Camada de Transporte (TLS) 1.0, 1.1 e 1.2</span><span class="sxs-lookup"><span data-stu-id="fb082-202">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="fb082-203">Mínimo de 8,8 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="fb082-203">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="fb082-204">Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz</span><span class="sxs-lookup"><span data-stu-id="fb082-204">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fb082-205">Implementação simplificada do X.509</span><span class="sxs-lookup"><span data-stu-id="fb082-205">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fb082-206">Totalmente integrado com tomadas Azure RTOS NetX Duo TCP</span><span class="sxs-lookup"><span data-stu-id="fb082-206">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="fb082-207">Suporte crypto de hardware</span><span class="sxs-lookup"><span data-stu-id="fb082-207">Hardware Crypto Support</span></span>
* <span data-ttu-id="fb082-208">Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span><span class="sxs-lookup"><span data-stu-id="fb082-208">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fb082-209">Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521</span><span class="sxs-lookup"><span data-stu-id="fb082-209">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fb082-210">Suporte de chave encriptado (dependente de hardware)</span><span class="sxs-lookup"><span data-stu-id="fb082-210">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="fb082-211">ICMP</span><span class="sxs-lookup"><span data-stu-id="fb082-211">ICMP</span></span>

* <span data-ttu-id="fb082-212">Protocolo de mensagem de controlo da Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="fb082-212">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="fb082-213">Flash mínimo de 2,5 KB</span><span class="sxs-lookup"><span data-stu-id="fb082-213">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fb082-214">Suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="fb082-214">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="fb082-215">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-215">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-216">Pedido de ping e resposta de ping</span><span class="sxs-lookup"><span data-stu-id="fb082-216">Ping request and ping response</span></span>
* <span data-ttu-id="fb082-217">Suspensão de fio opcional em pedidos de ping</span><span class="sxs-lookup"><span data-stu-id="fb082-217">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="fb082-218">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="fb082-218">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb082-219">Estatísticas opcionais do ICMP</span><span class="sxs-lookup"><span data-stu-id="fb082-219">Optional ICMP statistics</span></span>
* <span data-ttu-id="fb082-220">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-220">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb082-221">APIs intuitivos do ICMP: *nx_icmp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-221">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="fb082-222">UDP</span><span class="sxs-lookup"><span data-stu-id="fb082-222">UDP</span></span>

* <span data-ttu-id="fb082-223">Protocolo de Datagrama do Utilizador (UDP)</span><span class="sxs-lookup"><span data-stu-id="fb082-223">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="fb082-224">Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="fb082-224">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="fb082-225">Processamento rápido, perto de tCP de velocidade de arame:</span><span class="sxs-lookup"><span data-stu-id="fb082-225">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fb082-226">RX 95 Mbps em 100 Mbps Ethernet, @100MHz MCU, 14% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="fb082-226">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="fb082-227">TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="fb082-227">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="fb082-228">UDP Fast Path™ tecnologia</span><span class="sxs-lookup"><span data-stu-id="fb082-228">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="fb082-229">Sem limites no número de UDP</span><span class="sxs-lookup"><span data-stu-id="fb082-229">No limits on the number of UDP</span></span>
* <span data-ttu-id="fb082-230">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-231">Suspensão opcional na tomada receber</span><span class="sxs-lookup"><span data-stu-id="fb082-231">Optional suspension on socket receive</span></span>
* <span data-ttu-id="fb082-232">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="fb082-232">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb082-233">Estatísticas opcionais da UDP</span><span class="sxs-lookup"><span data-stu-id="fb082-233">Optional UDP statistics</span></span>
* <span data-ttu-id="fb082-234">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-234">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb082-235">APIs intuitivos da UDP: *nx_udp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-235">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="fb082-236">TCP</span><span class="sxs-lookup"><span data-stu-id="fb082-236">TCP</span></span>

* <span data-ttu-id="fb082-237">Protocolo de Controlo de Transmissão (TCP)</span><span class="sxs-lookup"><span data-stu-id="fb082-237">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="fb082-238">Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada</span><span class="sxs-lookup"><span data-stu-id="fb082-238">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="fb082-239">Processamento rápido, perto de wlrespeed pacoteS TCP:</span><span class="sxs-lookup"><span data-stu-id="fb082-239">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fb082-240">RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="fb082-240">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="fb082-241">TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% utilização de MCU</span><span class="sxs-lookup"><span data-stu-id="fb082-241">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="fb082-242">Conexão fiável</span><span class="sxs-lookup"><span data-stu-id="fb082-242">Reliable connection</span></span>
* <span data-ttu-id="fb082-243">Não há limites para o número de tomadas TCP</span><span class="sxs-lookup"><span data-stu-id="fb082-243">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="fb082-244">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-244">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-245">Suspensão opcional na tomada receber/transmitir</span><span class="sxs-lookup"><span data-stu-id="fb082-245">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="fb082-246">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="fb082-246">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb082-247">Estatísticas opcionais de TCP</span><span class="sxs-lookup"><span data-stu-id="fb082-247">Optional TCP statistics</span></span>
* <span data-ttu-id="fb082-248">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-248">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb082-249">APIs intuitivos de TCP: *nx_tcp_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-249">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="fb082-250">ARP/RARP</span><span class="sxs-lookup"><span data-stu-id="fb082-250">ARP/RARP</span></span>

* <span data-ttu-id="fb082-251">Protocolo de Resolução de Endereços (ARP)</span><span class="sxs-lookup"><span data-stu-id="fb082-251">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="fb082-252">Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="fb082-252">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="fb082-253">Mínimo de 1,7 KB FLASH, tamanho RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-253">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="fb082-254">Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt</span><span class="sxs-lookup"><span data-stu-id="fb082-254">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="fb082-255">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-255">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-256">Cache ARP flexível e definido pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="fb082-256">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="fb082-257">Suporte gratuito da ARP</span><span class="sxs-lookup"><span data-stu-id="fb082-257">Gratuitous ARP support</span></span>
* <span data-ttu-id="fb082-258">Estatísticas opcionais de ARP/RARP determinadas por aplicação</span><span class="sxs-lookup"><span data-stu-id="fb082-258">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="fb082-259">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-259">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb082-260">APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*</span><span class="sxs-lookup"><span data-stu-id="fb082-260">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="fb082-261">IPv4 &amp; IPv6</span><span class="sxs-lookup"><span data-stu-id="fb082-261">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="fb082-262">Protocolo de Internet (IP)</span><span class="sxs-lookup"><span data-stu-id="fb082-262">Internet Protocol (IP)</span></span>
* <span data-ttu-id="fb082-263">Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM</span><span class="sxs-lookup"><span data-stu-id="fb082-263">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="fb082-264">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="fb082-264">Piconet™ architecture</span></span>
* <span data-ttu-id="fb082-265">Rápido, perto do desempenho da velocidade de arame</span><span class="sxs-lookup"><span data-stu-id="fb082-265">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="fb082-266">Suporte de interface múltipla</span><span class="sxs-lookup"><span data-stu-id="fb082-266">Multiple interface support</span></span>
* <span data-ttu-id="fb082-267">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="fb082-267">Multihomed support</span></span>
* <span data-ttu-id="fb082-268">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="fb082-268">Static routing support</span></span>
* <span data-ttu-id="fb082-269">Suporte de fragmentação/remontagem de IP</span><span class="sxs-lookup"><span data-stu-id="fb082-269">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="fb082-270">Suporte de endereço IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="fb082-270">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="fb082-271">IXIA IxANVL validada</span><span class="sxs-lookup"><span data-stu-id="fb082-271">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fb082-272">Certificação de logotipo pronto da fase II IPv6</span><span class="sxs-lookup"><span data-stu-id="fb082-272">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="fb082-273">Estatísticas IP opcionais</span><span class="sxs-lookup"><span data-stu-id="fb082-273">Optional IP statistics</span></span>
* <span data-ttu-id="fb082-274">Interface de controlador de camada física bem definida e intuitiva</span><span class="sxs-lookup"><span data-stu-id="fb082-274">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="fb082-275">Traços de nível do sistema via Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-275">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb082-276">APIs intuitivos da camada IP: *\* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_</span><span class="sxs-lookup"><span data-stu-id="fb082-276">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="fb082-277">Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4</span><span class="sxs-lookup"><span data-stu-id="fb082-277">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="fb082-278">Azure RTOS NetX Secure IPSEC</span><span class="sxs-lookup"><span data-stu-id="fb082-278">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="fb082-279">Segurança do Protocolo de Internet (IPSEC)</span><span class="sxs-lookup"><span data-stu-id="fb082-279">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="fb082-280">Camada IP</span><span class="sxs-lookup"><span data-stu-id="fb082-280">IP layer</span></span>
* <span data-ttu-id="fb082-281">Suporte cripto de hardware</span><span class="sxs-lookup"><span data-stu-id="fb082-281">Hardware crypto support</span></span>
* <span data-ttu-id="fb082-282">Suporte cripto de software, incluindo:</span><span class="sxs-lookup"><span data-stu-id="fb082-282">Software crypto support, including:</span></span>
    * <span data-ttu-id="fb082-283">DES, 3DES</span><span class="sxs-lookup"><span data-stu-id="fb082-283">DES, 3DES</span></span>
    * <span data-ttu-id="fb082-284">AES</span><span class="sxs-lookup"><span data-stu-id="fb082-284">AES</span></span>
    * <span data-ttu-id="fb082-285">HMAC-MD5</span><span class="sxs-lookup"><span data-stu-id="fb082-285">HMAC-MD5</span></span>
    * <span data-ttu-id="fb082-286">HMAC-SHA1</span><span class="sxs-lookup"><span data-stu-id="fb082-286">HMAC-SHA1</span></span>
* <span data-ttu-id="fb082-287">Suporte da Exchange da Internet (IKE) Versão 2</span><span class="sxs-lookup"><span data-stu-id="fb082-287">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="fb082-288">IPsec Intuitivo APIs: *nx_ipsec_ \**</span><span class="sxs-lookup"><span data-stu-id="fb082-288">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="fb082-289">IPsec só está disponível com Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="fb082-289">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="fb082-290">Cofre e seguro</span><span class="sxs-lookup"><span data-stu-id="fb082-290">Safe and secure</span></span>

<span data-ttu-id="fb082-291">Azure RTOS NetX Duo está seguro.</span><span class="sxs-lookup"><span data-stu-id="fb082-291">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="fb082-292">Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS.</span><span class="sxs-lookup"><span data-stu-id="fb082-292">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="fb082-293">Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.</span><span class="sxs-lookup"><span data-stu-id="fb082-293">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="fb082-294">Microsoft Azure O RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes.</span><span class="sxs-lookup"><span data-stu-id="fb082-294">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="fb082-295">Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.</span><span class="sxs-lookup"><span data-stu-id="fb082-295">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="fb082-296">Verificação da interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="fb082-296">Interoperability verification</span></span>

<span data-ttu-id="fb082-297">O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.</span><span class="sxs-lookup"><span data-stu-id="fb082-297">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="fb082-299">O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="fb082-299">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="fb082-300">A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.</span><span class="sxs-lookup"><span data-stu-id="fb082-300">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="fb082-301">Solução IoT abrangente</span><span class="sxs-lookup"><span data-stu-id="fb082-301">Comprehensive IoT solution</span></span>

<span data-ttu-id="fb082-302">A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas.</span><span class="sxs-lookup"><span data-stu-id="fb082-302">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="fb082-303">Este suporte inclui os seguintes produtos de protocolo adicional.</span><span class="sxs-lookup"><span data-stu-id="fb082-303">This support includes the following add-on protocol products.</span></span>

* <span data-ttu-id="fb082-304">MQTT</span><span class="sxs-lookup"><span data-stu-id="fb082-304">MQTT</span></span>
* <span data-ttu-id="fb082-305">CoAP</span><span class="sxs-lookup"><span data-stu-id="fb082-305">CoAP</span></span>
* <span data-ttu-id="fb082-306">LWM2M</span><span class="sxs-lookup"><span data-stu-id="fb082-306">LWM2M</span></span>
* <span data-ttu-id="fb082-307">6LoWPAN</span><span class="sxs-lookup"><span data-stu-id="fb082-307">6LoWPAN</span></span>
* <span data-ttu-id="fb082-308">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="fb082-308">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="fb082-309">IPsec</span><span class="sxs-lookup"><span data-stu-id="fb082-309">IPsec</span></span>
* <span data-ttu-id="fb082-310">AutoIP</span><span class="sxs-lookup"><span data-stu-id="fb082-310">AutoIP</span></span>
* <span data-ttu-id="fb082-311">DHCP</span><span class="sxs-lookup"><span data-stu-id="fb082-311">DHCP</span></span>
* <span data-ttu-id="fb082-312">DNS</span><span class="sxs-lookup"><span data-stu-id="fb082-312">DNS</span></span>
* <span data-ttu-id="fb082-313">mDNS</span><span class="sxs-lookup"><span data-stu-id="fb082-313">mDNS</span></span>
* <span data-ttu-id="fb082-314">DNS-SD</span><span class="sxs-lookup"><span data-stu-id="fb082-314">DNS-SD</span></span>
* <span data-ttu-id="fb082-315">FTP</span><span class="sxs-lookup"><span data-stu-id="fb082-315">FTP</span></span>
* <span data-ttu-id="fb082-316">HTTP</span><span class="sxs-lookup"><span data-stu-id="fb082-316">HTTP</span></span>
* <span data-ttu-id="fb082-317">IPsec</span><span class="sxs-lookup"><span data-stu-id="fb082-317">IPsec</span></span>
* <span data-ttu-id="fb082-318">NAT</span><span class="sxs-lookup"><span data-stu-id="fb082-318">NAT</span></span>
* <span data-ttu-id="fb082-319">POP3</span><span class="sxs-lookup"><span data-stu-id="fb082-319">POP3</span></span>
* <span data-ttu-id="fb082-320">PPP</span><span class="sxs-lookup"><span data-stu-id="fb082-320">PPP</span></span>
* <span data-ttu-id="fb082-321">PPPoE</span><span class="sxs-lookup"><span data-stu-id="fb082-321">PPPoE</span></span>
* <span data-ttu-id="fb082-322">SMTP</span><span class="sxs-lookup"><span data-stu-id="fb082-322">SMTP</span></span>
* <span data-ttu-id="fb082-323">SNMP v1/2/3</span><span class="sxs-lookup"><span data-stu-id="fb082-323">SNMP v1/2/3</span></span>
* <span data-ttu-id="fb082-324">Telnet</span><span class="sxs-lookup"><span data-stu-id="fb082-324">Telnet</span></span>
* <span data-ttu-id="fb082-325">TFTP</span><span class="sxs-lookup"><span data-stu-id="fb082-325">TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="fb082-326">Tecnologia avançada</span><span class="sxs-lookup"><span data-stu-id="fb082-326">Advanced technology</span></span>

<span data-ttu-id="fb082-327">Azure RTOS NetX Duo é uma tecnologia avançada que inclui o seguinte.</span><span class="sxs-lookup"><span data-stu-id="fb082-327">Azure RTOS NetX Duo is advanced technology that includes the following.</span></span>

* <span data-ttu-id="fb082-328">Piconet™ arquitetura</span><span class="sxs-lookup"><span data-stu-id="fb082-328">Piconet™ architecture</span></span>
* <span data-ttu-id="fb082-329">Dimensionamento automático</span><span class="sxs-lookup"><span data-stu-id="fb082-329">Automatic scaling</span></span>
* <span data-ttu-id="fb082-330">Tecnologia Fast-Path UDP™</span><span class="sxs-lookup"><span data-stu-id="fb082-330">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="fb082-331">Gestão flexível de pacotes</span><span class="sxs-lookup"><span data-stu-id="fb082-331">Flexible packet management</span></span>
* <span data-ttu-id="fb082-332">API de cópia zero e implementação</span><span class="sxs-lookup"><span data-stu-id="fb082-332">Zero-copy API and implementation</span></span>
* <span data-ttu-id="fb082-333">Suporte multihomed</span><span class="sxs-lookup"><span data-stu-id="fb082-333">Multihomed support</span></span>
* <span data-ttu-id="fb082-334">Tempo limite opcional em toda a suspensão</span><span class="sxs-lookup"><span data-stu-id="fb082-334">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb082-335">Suporte de encaminhamento estático</span><span class="sxs-lookup"><span data-stu-id="fb082-335">Static routing support</span></span>
* <span data-ttu-id="fb082-336">IPsec</span><span class="sxs-lookup"><span data-stu-id="fb082-336">IPsec</span></span>
* <span data-ttu-id="fb082-337">SSL/TLS/DTLS</span><span class="sxs-lookup"><span data-stu-id="fb082-337">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="fb082-338">Suporte de análise do sistema Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="fb082-338">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="fb082-339">Serviços relacionados</span><span class="sxs-lookup"><span data-stu-id="fb082-339">Related services</span></span>

<span data-ttu-id="fb082-340">A NetX Duo fornece os seguintes serviços adicionais.</span><span class="sxs-lookup"><span data-stu-id="fb082-340">NetX Duo provides the following additional services.</span></span>

* <span data-ttu-id="fb082-341">Azure IoT Middleware</span><span class="sxs-lookup"><span data-stu-id="fb082-341">Azure IoT Middleware</span></span>
* <span data-ttu-id="fb082-342">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="fb082-342">Azure Defender</span></span>
* <span data-ttu-id="fb082-343">Atualização do dispositivo para IoT Hub.</span><span class="sxs-lookup"><span data-stu-id="fb082-343">Device update for IoT Hub.</span></span>

### <a name="azure-iot-middleware"></a><span data-ttu-id="fb082-344">Azure IoT Middleware</span><span class="sxs-lookup"><span data-stu-id="fb082-344">Azure IoT Middleware</span></span>

<span data-ttu-id="fb082-345">A NetX Duo inclui [o Azure IoT Middleware para Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), uma biblioteca específica da plataforma que funciona como uma camada de ligação entre o Azure RTOS e o Azure SDK para Embedded C para facilitar a conectividade aos serviços Azure IoT.</span><span class="sxs-lookup"><span data-stu-id="fb082-345">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="fb082-346">Os objetivos de Azure IoT Middleware são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="fb082-346">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="fb082-347">Forneça as interfaces inteligentes do cliente (IoTHub_Client, DeviceProvisioning_Client) que os desenvolvedores precisam para as suas aplicações.</span><span class="sxs-lookup"><span data-stu-id="fb082-347">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="fb082-348">Orquestrou a interação entre o SDK Incorporado e a plataforma.</span><span class="sxs-lookup"><span data-stu-id="fb082-348">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="fb082-349">Fornecer inicialização da plataforma Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="fb082-349">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="fb082-350">IoT Plug e Suporte de Reprodução.</span><span class="sxs-lookup"><span data-stu-id="fb082-350">IoT Plug and Play support.</span></span>
* <span data-ttu-id="fb082-351">Capacidades de segurança.</span><span class="sxs-lookup"><span data-stu-id="fb082-351">Security capabilities.</span></span>
* <span data-ttu-id="fb082-352">Limitação de recursos consciente.</span><span class="sxs-lookup"><span data-stu-id="fb082-352">Resource limitation aware.</span></span>
* <span data-ttu-id="fb082-353">Apoio ao protocolo.</span><span class="sxs-lookup"><span data-stu-id="fb082-353">Protocol support.</span></span>

![Azure RTOS NetX Duo Serviços relacionados](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="fb082-355">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="fb082-355">Azure Defender</span></span>

<span data-ttu-id="fb082-356">O módulo de segurança Azure Defender for IoT fornece uma solução de segurança abrangente para dispositivos Azure RTOS.</span><span class="sxs-lookup"><span data-stu-id="fb082-356">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="fb082-357">O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fb082-357">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="fb082-358">Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span><span class="sxs-lookup"><span data-stu-id="fb082-358">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="fb082-359">Atualização do dispositivo para ioT hub</span><span class="sxs-lookup"><span data-stu-id="fb082-359">Device Update for IoT Hub</span></span>

<span data-ttu-id="fb082-360">A [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) é um serviço que lhe permite implementar atualizações over-the-air (OTA) para os seus dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="fb082-360">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="fb082-361">O módulo Device Update for IoT Hub é a implementação da Atualização do Dispositivo para OOT Hub Agent em Azure RTOS NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fb082-361">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="fb082-362">Fornece APIs simples para os construtores de dispositivos integrarem a capacidade de Atualização do Dispositivo na sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="fb082-362">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="fb082-363">Consulte as amostras dos principais conselhos de avaliação de semicondutores que incluem os guias de arranque para aprender a configurar, construir e implementar as atualizações over-the-air (OTA) para os dispositivos.</span><span class="sxs-lookup"><span data-stu-id="fb082-363">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="fb082-364">E pode aprender mais detalhes sobre a utilização [de Device Update para IoT Hub com Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="fb082-364">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fb082-365">Passos seguintes</span><span class="sxs-lookup"><span data-stu-id="fb082-365">Next steps</span></span>

<span data-ttu-id="fb082-366">Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)</span><span class="sxs-lookup"><span data-stu-id="fb082-366">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
