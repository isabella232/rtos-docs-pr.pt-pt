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
# <a name="overview-of-azure-rtos-netx-duo"></a>Visão geral do Azure RTOS NetX Duo

A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT. A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior. O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS. Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API

### <a name="mqtt"></a>MQTT

* Transporte de Telemetria de Fila de Mensagens (MQTT)
* Mínimo de 2,7 KB FLASH

### <a name="auto-ip"></a>IP automático

* Atribuição automática de endereços IPv4
* Mínimo 1.2 KB, 300 bytes de RAM

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Protocolo de Transferência de Hipertexto(HTTP)
* Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM
* Suporte ao cliente e ao servidor

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Protocolo de Transferência de Hipertexto(HTTP)
* Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM
* Suporte ao cliente e ao servidor
* Múltiplas sessões de clientes recebidas
* Texto simples e HTTPS encriptado
* Suporte de ligação persistente
* Upload de ficheiros multipart
* Totalmente integrado com Azure RTOS NetX Secure TLS

### <a name="smtp"></a>SMTP

* Protocolo de transferência simples do centro comercial (SMTP)
* Pegada mínima de 4,1 KB e 0,6 KB RAM
* Apoio ao cliente

### <a name="dhcp"></a>DHCP

* Protocolo DHCP (Dynamic Host Configuration Protocol)
* Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB
* Suporte ao cliente e ao servidor
* Suporte IPv4 e IPv6

### <a name="nat"></a>NAT

* Tradução de Endereços de Rede (NAT)
* Pegada mínima de 3,5K6 e 0,6 KB RAM
* Suporte de endereço IPv4
* NAT só está disponível com Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* SNMP (Simple Network Management Protocol)
* Pegada mínima de 10,9 KB e 2,6 KB RAM
* Apoio ao agente para VI, V2 e V3

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* Sistema de Nomes de Domínio (DNS)
* Sistema de Nome de Domínio Multicast (mDNS)
* Descoberta de serviço baseada em DNS (DNS-SD)
* DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada
* Apoio ao cliente
* mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo

### <a name="pop3"></a>POP3

* Versão 3 do Protocolo de Office (POP3)
* Pegada mínima de 8,1 KB e 1,4 KB RAM
* Apoio ao cliente

### <a name="telnet"></a>TELNET

* Pegada mínima de 0,5 KB e 0,3 KB RAM
* Suporte ao cliente e ao servidor
* ApIs intuitivos telnet: *nx_telnet_ \**

### <a name="ftp-tftp"></a>FTP, TFTP

* Protocolo de Transferência de Ficheiros (FTP)
* Protocolo TFTP (Trivial File Transfer Protocol)
* FTP Mínimo de 1,8 KB a 7.2 KB FLASH, 0,6 KB a 2,1 KB RAM
* TFTP Mínimo de 1,7 KB a 2,4 KB FLASH, 0.3 KB a 1,8 KB RAM
* Suporte ao cliente e ao servidor
* APIs intuitivos de FTP e TFTP: *nx_ftp_ \** ou *nx_tftp_ \**

### <a name="ppp-pppoe"></a>PPP, PPPoE

* Protocolo Polnt-to-Point (PPP)
* Protocolo ponto a ponto sobre ethernet (PPPoE)
* Pegada mínima de 7,1 KB e 3,8 KB RAM
* APIs intuitivos de PPP: *nx_ppp_ \**

* PPPoE só está disponível com Azure RTOS NetX Duo

### <a name="sntp"></a>SNTP

* Protocolo simples do tempo de rede (SNTP)
* Mínimo 4 KB e 0,5 KB RAM
* Apoio ao cliente
* APIs intuitivos: *nx_sntp_ \**

### <a name="azure-rtos-netx-duo-api"></a>Azure RTOS NetX Duo API

* API intuitiva e consistente
* Convenção de nomeação de substantivos
* Implementação rápida e zero-copy API
* Todas as APIs têm <i>nx_*</i> para identificar facilmente como Azure RTOS NetX
* ApIs de bloqueio têm tempo limite opcional de fio
* Consulte [o Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) para mais detalhes
* Camada opcional de BSD para porting código de tomada legado

### <a name="igmp"></a>IGMP

* Protocolo de Gestão do Grupo de Internet (IGMP)
* Flash mínimo de 2,5 KB
* Suporte ao grupo multicast IPv4
* IXIA IxANVL validada
* Estatísticas opcionais do IGMP
* Traços de nível do sistema via Azure RTOS ThreadX
* APIs intuitivos do IGMP: *nx_igmp_ \**

### <a name="azure-rtos-netx-secure-dtls"></a>Azure RTOS NetX Secure DTLS

* Segurança da camada de transporte de datagram (DTLS) 1.0 e 1.2
* Flash mínimo de 11 KB
* Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz
* Implementação simplificada do X.509
* Totalmente integrado com tomadas UDP Azure RTOS NetX Duo
* Suporte crypto de hardware
* Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521
* Suporte de chave encriptado (dependente de hardware)

### <a name="azure-rtos-netx-secure-tls"></a>Azure RTOS NetX Secure TLS

* Segurança da Camada de Transporte (TLS) 1.0, 1.1 e 1.2
* Mínimo de 8,8 KB FLASH
* Rápido, software RSA 2048-bit tamanho chave ~1 segundo @120MHz
* Implementação simplificada do X.509
* Totalmente integrado com tomadas Azure RTOS NetX Duo TCP
* Suporte crypto de hardware
* Suporte Crypto software: RSA (todos os tamanhos das chaves), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)
* Criptografia da Curva Elíptica (ECC) com ECDSA (assinatura) e ECDH (encriptação), incluindo curvas P 192/224/256/384/521
* Suporte de chave encriptado (dependente de hardware)

### <a name="icmp"></a>ICMP

* Protocolo de mensagem de controlo da Internet (ICMP)
* Flash mínimo de 2,5 KB
* Suporte IPv4 e IPv6
* IXIA IxANVL validada
* Pedido de ping e resposta de ping
* Suspensão de fio opcional em pedidos de ping
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais do ICMP
* Traços de nível do sistema via Azure RTOS TraceX
* APIs intuitivos do ICMP: *nx_icmp_ \**

### <a name="udp"></a>UDP

* Protocolo de Datagrama do Utilizador (UDP)
* Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada
* Processamento rápido, perto de tCP de velocidade de arame:
    * RX 95 Mbps em 100 Mbps Ethernet, @100MHz MCU, 14% utilização de MCU
    * TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU
* UDP Fast Path™ tecnologia
* Sem limites no número de UDP
* IXIA IxANVL validada
* Suspensão opcional na tomada receber
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais da UDP
* Traços de nível do sistema via Azure RTOS TraceX
* APIs intuitivos da UDP: *nx_udp_ \**

### <a name="tcp"></a>TCP

* Protocolo de Controlo de Transmissão (TCP)
* Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada
* Processamento rápido, perto de wlrespeed pacoteS TCP:
    * RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% utilização de MCU
    * TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% utilização de MCU
* Conexão fiável
* Não há limites para o número de tomadas TCP
* IXIA IxANVL validada
* Suspensão opcional na tomada receber/transmitir
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais de TCP
* Traços de nível do sistema via Azure RTOS TraceX
* APIs intuitivos de TCP: *nx_tcp_ \**

### <a name="arprarp"></a>ARP/RARP

* Protocolo de Resolução de Endereços (ARP)
* Protocolo de Resolução de Endereços Reversos (RARP)
* Mínimo de 1,7 KB FLASH, tamanho RAM
* Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt
* IXIA IxANVL validada
* Cache ARP flexível e definido pelo utilizador
* Suporte gratuito da ARP
* Estatísticas opcionais de ARP/RARP determinadas por aplicação
* Traços de nível do sistema via Azure RTOS TraceX
* APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*

### <a name="ipv4-amp-ipv6"></a>IPv4 &amp; IPv6

* Protocolo de Internet (IP)
* Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM
* Piconet™ arquitetura
* Rápido, perto do desempenho da velocidade de arame
* Suporte de interface múltipla
* Suporte multihomed
* Suporte de encaminhamento estático
* Suporte de fragmentação/remontagem de IP
* Suporte de endereço IPv4 e IPv6
* IXIA IxANVL validada
* Certificação de logotipo pronto da fase II IPv6
* Estatísticas IP opcionais
* Interface de controlador de camada física bem definida e intuitiva
* Traços de nível do sistema via Azure RTOS TraceX
* APIs intuitivos da camada IP: *\* nx_ip_*, *nxd_ip_ \** *\** , nxd_ipv6_
* Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4

### <a name="azure-rtos-netx-secure-ipsec"></a>Azure RTOS NetX Secure IPSEC

* Segurança do Protocolo de Internet (IPSEC)
* Camada IP
* Suporte cripto de hardware
* Suporte cripto de software, incluindo:
    * DES, 3DES
    * AES
    * HMAC-MD5
    * HMAC-SHA1
* Suporte da Exchange da Internet (IKE) Versão 2
* IPsec Intuitivo APIs: *nx_ipsec_ \**
* IPsec só está disponível com Azure RTOS NetX Duo

## <a name="safe-and-secure"></a>Cofre e seguro

Azure RTOS NetX Duo está seguro. Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS. Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.

Microsoft Azure O RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes. Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.


## <a name="interoperability-verification"></a>Verificação da interoperabilidade

O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum. A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.

## <a name="comprehensive-iot-solution"></a>Solução IoT abrangente

A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas. Este suporte inclui os seguintes produtos de protocolo adicional.

MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP

## <a name="advanced-technology"></a>Tecnologia avançada

Azure RTOS NetX Duo é uma tecnologia avançada que inclui:

* Piconet™ arquitetura
* Dimensionamento automático
* Tecnologia Fast-Path UDP™
* Gestão flexível de pacotes
* API de cópia zero e implementação
* Suporte multihomed
* Tempo limite opcional em toda a suspensão
* Suporte de encaminhamento estático
* IPsec
* SSL/TLS/DTLS
* Suporte de análise do sistema Azure RTOS TraceX

## <a name="related-services"></a>Serviços relacionados

### <a name="azure-iot"></a>Azure IoT

A NetX Duo inclui [o Azure IoT Middleware para Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), uma biblioteca específica da plataforma que funciona como uma camada de ligação entre o Azure RTOS e o Azure SDK para Embedded C para facilitar a conectividade aos serviços Azure IoT. Os objetivos de Azure IoT Middleware são os seguintes.
* Forneça as interfaces inteligentes do cliente (IoTHub_Client, DeviceProvisioning_Client) que os desenvolvedores precisam para as suas aplicações.
* Orquestrou a interação entre o SDK Incorporado e a plataforma.
* Fornecer inicialização da plataforma Azure RTOS.
* IoT Plug e Suporte de Reprodução.
* Capacidades de segurança.
* Limitação de recursos consciente.
* Apoio ao protocolo.

![Azure RTOS NetX Duo Serviços relacionados](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a>Azure Defender

O módulo de segurança Azure Defender for IoT fornece uma solução de segurança abrangente para dispositivos Azure RTOS. O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo. Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.

### <a name="device-update-for-iot-hub"></a>Atualização do dispositivo para ioT hub

A [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) é um serviço que lhe permite implementar atualizações over-the-air (OTA) para os seus dispositivos IoT. O módulo Device Update for IoT Hub é a implementação da Atualização do Dispositivo para OOT Hub Agent em Azure RTOS NetX Duo. Fornece APIs simples para os construtores de dispositivos integrarem a capacidade de Atualização do Dispositivo na sua aplicação.

Consulte as amostras dos principais conselhos de avaliação de semicondutores que incluem os guias de arranque para aprender a configurar, construir e implementar as atualizações over-the-air (OTA) para os dispositivos.

E pode aprender mais detalhes sobre a utilização [de Device Update para IoT Hub com Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).

## <a name="next-steps"></a>Passos seguintes

Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)
