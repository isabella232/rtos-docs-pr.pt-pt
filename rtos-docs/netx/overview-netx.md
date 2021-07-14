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
# <a name="overview-of-azure-rtos-netx"></a>Visão geral do Azure RTOS NetX

Azure RTOS NetX é uma pilha de rede incorporada TCP/IP IPv4 de grau industrial, projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT. Azure RTOS NetX é a pilha original de rede IPv4 da Microsoft, e é essencialmente um subconjunto de Azure RTOS. A NetX fornece aplicações incorporadas com protocolos de rede fundamentais, tais como IPv4, TCP e UDP, bem como um conjunto completo de protocolos adicionais e adicionais de alto nível. Uma pequena pegada, execução rápida e facilidade de utilização superior fazem do Azure RTOS NetX uma escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API
O Azure RTOS NetX fornece suporte para o seguinte.

### <a name="telnet"></a>TELNET

* Pegada mínima de 0,5 KB e 0,3 KB RAM.
* Suporte ao cliente e servidor.

### <a name="auto-ip"></a>IP automático

* Atribuição automática de endereços IPv4.
* Mínimo de 1,2 KB, 300 bytes de RAM.

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - Protocolo de Transferência de Hipertexto (HTTP)

* Mínimo de 2,8 KB a 4.8KBFLASH, 0,4 KB a 1,0 KB RAM.
* Suporte ao cliente e servidor.

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - Simples Protocolo de Transferência de Correio (SMTP)

* Pegada mínima de 4,1 KB e 0,6 KB RAM
* Apoio ao cliente

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - Protocolo de Configuração dinâmica do anfitrião (DHCP)

* Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB
* Suporte ao cliente e ao servidor
* Suporte IPv4

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - Pós-Office Protocolo Versão 3 (POP3)

* Pegada mínima de 8,1 KB e 1,4 KB RAM
* Apoio ao cliente

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - Protocolo de Gestão de Redes Simples (SNMP)

* Pegada mínima de 10,9 KB e 2,6 KB RAM
* Apoio ao agente para VI, V2 e V3

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - Protocolo de Transferência de Ficheiros (FTP), Protocolo de Transferência de Ficheiros Trivial (TFTP)

* FTP Mínimo de 1,8 KB a 7.2KBFLASH, 0,6 KB a 2,1 KB RAM
* TFTP Mínimo de 1,7 KB a 2.4KBFLASH, 0.3 KB a 1,8 KB RAM
* Suporte ao cliente e ao servidor

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Protocolo Polnt-to-PoInt (PPP)

* Pegada mínima de 7,1 KB e 3,8 KB RAM
* Confiável e fiável.

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - Protocolo de Tempo de Rede Simples (SNTP)

* Mínimo 4 KB e 0,5 KB RAM
* Apoio ao cliente

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* Implementação rápida e zero-copy API
* Camada opcional de BSD para porting código de tomada legado

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - Protocolo de Gestão de Grupos de Internet (IGMP)

* Flash mínimo de 2,5 KB
* Suporte ao grupo multicast IPv4
* IXIA IxANVL Validada
* Estatísticas opcionais do IGMP
* Traço de nível do sistema via Azure RTOS TraceX

### <a name="udp---user-datagram-protocol-udp"></a>UDP - Protocolo de Datagrama do Utilizador (UDP)

* Mínimo de 2,5 KB FLASH, 124 tomadas de RAM por tomada
* Processamento rápido, perto de tCP de velocidade de arame:
* RX 95 Mbps em 100 Mbps Ethernet, MCU @100MHz , 14% UTILIZAÇÃO MCU
* TX 94 Mbps em 100 Mbps Ethernet, @100MHz MCU, 10% utilização de MCU
* UDP Fast Path™ tecnologia
* Sem limites no número de UDP
* IXIA IxANVL Validada
* Suspensão opcional na tomada receber
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais da UDP
* Traço de nível do sistema via Azure RTOS TraceX

### <a name="tcp---transmission-control-protocol-tcp"></a>TCP - Protocolo de Controlo de Transmissão (TCP)

* Mínimo de 10,5K8 a 12,5 KB FLASH, 280 bytes de RAM por tomada
* Processamento rápido, perto de wlrespeed pacoteS TCP:
* RX 93 Mbps em 100 Mbps Ethernet, @100MHz MCU, 20% UTILIZAÇÃO MCU
* TX 94 Mbps em 100 Mbps Ethernet, MCU @100MHz , 27% UTILIZAÇÃO MCU
* Conexão fiável
* Não há limites para o número de tomadas TCP
* IXIA IxANVL Validada
* Suspensão opcional na tomada receber/transmitir
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais de TCP
* Traço de nível do sistema via Azure RTOS TraceX

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - Protocolo de Mensagem de Controlo de Internet (ICMP)

* Flash mínimo de 2,5 KB
* Suporte IPv4
* IXIA IxANVL Validada
* Pedido de ping e resposta de ping
* Suspensão de fio opcional em pedidos de ping
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais do ICMP
* Traço de nível do sistema via Azure RTOS TraceX

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - Protocolo de Internet (IP)

* Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB RAM.
* Piconet™ Arquitetura.
* Rápido, perto de velocidade de arame.
* Suporte de interface múltipla.
* Apoio multi-habitação.
* Suporte de encaminhamento estático.
* Suporte de fragmentação/remontagem ip.
* Suporte IPv4.
* IXIA IxANVL Validada.
* Certificação de logotipo pronto da fase II.
* Estatísticas IP opcionais.
* Interface de condutor de camada física bem definida e intuitiva.
* Rastreio de nível de sistema via Azure RTOS TraceX.

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - Protocolo de Resolução de Endereços (ARP), Protocolo de Resolução de Endereços Reversos (RARP)

* Mínimo de 1,7 KB FLASH, tamanho RAM.
* Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt.
* IXIA IxANVL Validada.
* Cache ARP flexível e definido pelo utilizador.
* Suporte gratuito da ARP.
* Estatísticas opcionais de ARP/RARP determinadas por aplicação.
* Rastreio de nível de sistema via Azure RTOS TraceX.

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, Wi-Fi, BLUETOOTH LE, 15.4, etc.

## <a name="interoperability-verification"></a>Verificação da interoperabilidade

O Azure RTOS NetX está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos da maioria dos fornecedores. O Azure RTOS NetX também utiliza a padrão da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo Azure RTOS NetX.

## <a name="advanced-technology"></a>Tecnologia avançada

Azure RTOS NetX é uma tecnologia avançada que inclui o seguinte.
* Piconet™ arquitetura.
* Escalagem automática.
* Tecnologia Fast-Path UDP™.
* Gestão flexível de pacotes.
* API de cópia zero e implementação.
* Apoio multi-habitação.
* Tempo limite opcional em toda a suspensão.
* Suporte de encaminhamento estático.
* Suporte de análise do sistema Azure RTOS TraceX.
