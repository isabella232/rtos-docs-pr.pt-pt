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
# <a name="overview-of-azure-rtos-netx"></a>Visão geral do Azure RTOS NetX

Azure RTOS NetX é uma pilha de rede incorporada TCP/IP IPv4 de grau industrial, projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT. Azure RTOS NetX é a pilha original de rede IPv4 da Microsoft, e é essencialmente um subconjunto de Azure RTOS. A NetX fornece aplicações incorporadas com protocolos de rede fundamentais, tais como IPv4, TCP e UDP, bem como um conjunto completo de protocolos adicionais e adicionais de alto nível. Uma pequena pegada, execução rápida e facilidade de utilização superior fazem do Azure RTOS NetX uma escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API

### <a name="telnet"></a>TELNET

* Pegada mínima de 0,5 KB e 0,3 KB RAM
* Suporte ao cliente e ao servidor
* ApIs intuitivos telnet: *nx_telnet_ \**

### <a name="auto-ip"></a>IP automático

* Atribuição automática de endereços IPv4
* Mínimo 1.2 KB, 300 bytes de RAM
* APIs autoIP intuitivos: *nx_autoip_ \**

### <a name="http---hypertext-transfer-protocolhttp"></a>HTTP - Protocolo de Transferência de Hipertexto (HTTP)

* Mínimo de 2,8 KB a 4.8KBFLASH, 0,4 KB a 1,0 KB RAM
* Suporte ao cliente e ao servidor
* APIs intuitivos HTTP: *nx_http_ \**

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a>SMTP - Simples Protocolo de Transferência de Correio (SMTP)

* Pegada mínima de 4,1 KB e 0,6 KB RAM
* Apoio ao cliente
* APIs intuitivos: *nx_smtp_ \**

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a>DHCP - Protocolo de Configuração dinâmica do anfitrião (DHCP)

* Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB
* Suporte ao cliente e ao servidor
* Suporte IPv4
* APIs intuitivos do DHCP: *nx_dhcp_ \**

### <a name="p0p3---post-office-protocol-version-3-pop3"></a>P0P3 - Protocolo dos Correios Versão 3 (POP3)

* Pegada mínima de 8,1 KB e 1,4 KB RAM
* Apoio ao cliente
* APIs P0P3 intuitivo: *nx_pop3_ \**

### <a name="snmp---simple-network-management-protocol-snmp"></a>SNMP - Protocolo de Gestão de Redes Simples (SNMP)

* Pegada mínima de 10,9 KB e 2,6 KB RAM
* Apoio ao agente para VI, V2 e V3
* APIs intuitivos do SNMP: *nx_snmp_ \**

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a>FTP, TFTP - Protocolo de Transferência de Ficheiros (FTP), Protocolo de Transferência de Ficheiros Trivial (TFTP)

* FTP Mínimo de 1,8 KB a 7.2KBFLASH, 0,6 KB a 2,1 KB RAM
* TFTP Mínimo de 1,7 KB a 2.4KBFLASH, 0.3 KB a 1,8 KB RAM
* Suporte ao cliente e ao servidor
* APIs intuitivos de FTP e TFTP: <i>nx_ftp_ *</i> ou <i>nx_tftp_*</i>

### <a name="ppp---polnt-to-point-protocol-ppp"></a>PPP - Protocolo Polnt-to-PoInt (PPP)

* Pegada mínima de 7,1 KB e 3,8 KB RAM
* APIs intuitivos de PPP: *nx_ppp_ \**

### <a name="sntp---simple-network-time-protocol-sntp"></a>SNTP - Protocolo de Tempo de Rede Simples (SNTP)

* Mínimo 4 KB e 0,5 KB RAM
* Apoio ao cliente
* APIs intuitivos: *nx_sntp_ \**

### <a name="azure-rtos-netx-api"></a>Azure RTOS NetX API

* API intuitiva e consistente
* Convenção de nomeação de substantivos
* Implementação rápida e zero-copy API
* Todas as funções da API têm levado <i>nx_*</i> a identificar facilmente como Azure RTOS NetX
* As funções de API de bloqueio têm um tempo limite opcional de linha
* Camada opcional de BSD para porting código de tomada legado

### <a name="igmp---internet-group-management-protocol-igmp"></a>IGMP - Protocolo de Gestão de Grupos de Internet (IGMP)

* Flash mínimo de 2,5 KB
* Suporte ao grupo multicast IPv4
* IXIA IxANVL Validada
* Estatísticas opcionais do IGMP
* Traço de nível do sistema via Azure RTOS TraceX
* APIs intuitivos do IGMP: *nx_igmp_ \**

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
* APIs intuitivos da UDP: *nx_udp_ \**

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
* APIs intuitivos de TCP: *nx_tcp_ \**

### <a name="icmp---internet-control-message-protocol-icmp"></a>ICMP - Protocolo de Mensagem de Controlo de Internet (ICMP)

* Flash mínimo de 2,5 KB
* Suporte IPv4
* IXIA IxANVL Validada
* Pedido de ping e resposta de ping
* Suspensão de fio opcional em pedidos de ping
* Tempo limite opcional em toda a suspensão
* Estatísticas opcionais do ICMP
* Traço de nível do sistema via Azure RTOS TraceX
* APIs intuitivos do ICMP: *nx_icmp_ \**

### <a name="ipv4---internet-protocol-ip"></a>IPv4 - Protocolo de Internet (IP)

* Mínimo de 3,5 KB a 8,5 KB FLASH, 2 KB a 3 KB pegada de RAM
* Arquitetura Piconet™
* Rápido, perto do desempenho da velocidade de arame
* Suporte de interface múltipla
* Suporte multihomed
* Suporte de encaminhamento estático
* Suporte de fragmentação/remontagem de IP
* Suporte IPv4
* IXIA IxANVL Validada
* Certificação de logotipo pronto da fase II
* Estatísticas IP opcionais
* Interface de controlador de camada física bem definida e intuitiva
* Traço de nível do sistema via Azure RTOS TraceX
* APIs intuitivos da camada IP: *nx_ip_ \**, *nxd_ip_ \**
* Pré-certificada por TUV e UL a IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a>ARP/RARP - Protocolo de Resolução de Endereços (ARP), Protocolo de Resolução de Endereços Reversos (RARP)

* Mínimo de 1,7 KB FLASH, tamanho RAM
* Resolução dinâmica de endereços MAC IPv4 e 48-blt de 32 blt
* IXIA IxANVL Validada
* Cache ARP flexível e definido pelo utilizador
* Suporte gratuito da ARP
* Estatísticas opcionais de ARP/RARP determinadas por aplicação
* Traço de nível do sistema via Azure RTOS TraceX
* APIs ARP/RARP Intuitivos: *nx_arp_ \**, *\* nx_rarp_*

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a>ETHERNET, Wi-Fi, BLUETOOTH LE, 15.4, etc.

## <a name="small-footprint"></a>Pequena pegada

O Azure RTOS NetX tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP. Para a funcionalidade TCP, são necessários mais 10 KB a 13 KB de memória da área de instrução. O uso de RAM Azure RTOS NetX varia tipicamente de 2,6 KB a 3,6 KB mais a memória do pacote pool, que é definido pela aplicação. Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS NetX escala automaticamente com base nos serviços utilizados pela aplicação. Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.

## <a name="fast-execution"></a>Execução rápida

O Azure RTOS NetX fornece uma implementação de envio/receção de pacotes de cópia zero e está altamente integrado com a Azure RTOS ThreadX para alcançar o desempenho mais rápido possível. Por exemplo, o Azure RTOS NetX pode normalmente obter perto de transferências de dados de velocidade bancária num processador de 80 MHz (ou menos), utilizando apenas uma pequena percentagem dos ciclos do processador.

## <a name="simple-easy-to-use"></a>Simples e fácil de usar

O Azure RTOS NetX é simples de usar. O Azure RTOS NetX API é simultaneamente intuitivo e altamente funcional. Os nomes da API são feitos de palavras reais e não de "sopa de alfabeto" ou nomes altamente abreviados que são tão comuns em outros produtos de networking. Todas as APIs Azure RTOS NetX têm uma *nx_* líder e seguem uma convenção de nomeação de substantivos. Além disso, existe uma consistência funcional em toda a API. Por exemplo, todas as funções da API que suspendem têm um tempo limite opcional que funciona de forma idêntica. Para aplicações antigas, o Azure RTOS NetX oferece uma camada compatível com tomada BSD adicional. Esta camada ajuda os desenvolvedores a migrar grandes aplicações de networking com facilidade.

## <a name="interoperability-verification"></a>Verificação da interoperabilidade

O Azure RTOS NetX está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores. O Azure RTOS NetX também utiliza a padrão da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo Azure RTOS NetX.

## <a name="advanced-technology"></a>Tecnologia avançada

Azure RTOS NetX é uma tecnologia avançada que inclui:

* Piconet™ arquitetura
* escala automática
* Tecnologia Fast-Path UDP™
* gestão flexível de pacotes
* API de cópia zero e implementação
* suporte multihomed
* tempo limite opcional em toda a suspensão
* suporte de encaminhamento estático
* Suporte de análise do sistema Azure RTOS TraceX

## <a name="fastest-time-to-market"></a>O tempo de venda mais rápido

O Azure RTOS NetX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter. Como resultado, o Azure RTOS NetX é uma das pilhas TCP/IP mais populares para dispositivos IoT incorporados, incluindo muitos SoCs da Broadcom, Gainspan, e assim por diante. A nossa vantagem consistente no mercado baseia-se em:

* documentação de qualidade – por favor, reveja [o nosso Azure RTOS NetX User Guide](about-this-guide.md) e veja por si mesmo!
* disponibilidade completa de código fonte
* API fácil de usar
* conjunto de recursos abrangente e avançado

## <a name="one-simple-license"></a>Uma licença simples

Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.

## <a name="full-highest-quality-source-code"></a>Código fonte completo e de alta qualidade

Ao longo dos anos, o código fonte Azure RTOS NetX definiu a fasquia em qualidade e facilidade de compreensão. Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.

## <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

O Azure RTOS NetX funciona com microprocessadores mais populares de 32/64 bits, fora da caixa, totalmente testados e totalmente suportados, incluindo as seguintes arquiteturas avançadas:

**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx

**Núcleo de Andes**: RISC-V

**Ambiqmicro**: Apollo MCUs

**BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadência**: Xtensa, Diamante

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi

**Cipreste**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Informação; Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Sinergia

**Laboratórios de Silício**: EFM32

**Sinopses**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*
