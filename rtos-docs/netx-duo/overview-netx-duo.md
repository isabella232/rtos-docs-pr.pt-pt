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
# <a name="overview-of-azure-rtos-netx-duo"></a>Visão geral do Azure RTOS NetX Duo

A pilha de rede TCP/IP incorporada da Azure RTOS NetX Duo é a pilha de rede de rede IPv4 e IPv6 TCP/IP de grau industrial avançada da Microsoft que é projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT. A NetX Duo fornece aplicações incorporadas com protocolos de rede fundamentais como IPv4, IPv6, TCP e UDP, bem como um conjunto completo de protocolos adicionais de nível superior. O Azure RTOS NetX Duo oferece segurança através de produtos adicionais de segurança adicionais, incluindo O Azure RTOS NetX Secure IPsec e Azure RTOS NetX Secure SSL/TLS/DTLS. Tudo isto combinado com uma pequena pegada, execução rápida e facilidade superior de uso fazem do Azure RTOS NetX Duo a escolha ideal para as aplicações IoT incorporadas mais exigentes.

## <a name="api-protocols"></a>Protocolos da API

### <a name="mqtt"></a>MQTT

* Transporte de Telemetria de Fila de Mensagens (MQTT)
* Mínimo de 2,7 KB FLASH
* APIs intuitivos de MQTT: *nx_mqtt_*\*

### <a name="auto-ip"></a>IP automático

* Atribuição automática de endereços IPv4
* Mínimo 1.2 KB, 300 bytes de RAM
* APIs autoIP intuitivos: *nx_autoip_ \**

### <a name="http-https"></a>HTTP, HTTPS

#### <a name="http-10"></a>HTTP 1.0

* Protocolo de Transferência de Hipertexto(HTTP)
* Mínimo de 2,8 KB a 4,8 KB FLASH / 0,4 KB a 1,0 KB RAM
* Suporte ao cliente e ao servidor
* APIs intuitivos: *nx_http_ \**

#### <a name="httphttps-11"></a>HTTP/HTTPS 1.1

* Protocolo de Transferência de Hipertexto(HTTP)
* Mínimo de 3,0 KB a 9,5 KB FLASH / 0,5 KB a 2 KB RAM
* Suporte ao cliente e ao servidor
* Múltiplas sessões de clientes recebidas
* Texto simples e HTTPS encriptado
* Suporte de ligação persistente
* Upload de ficheiros multipart
* Totalmente integrado com Azure RTOS NetX Secure TLS
* APIs intuitivos: *nx_web_http \**

### <a name="smtp"></a>SMTP

* Protocolo de transferência simples do centro comercial (SMTP)
* Pegada mínima de 4,1 KB e 0,6 KB RAM
* Apoio ao cliente
* APIs intuitivos: *nx_smtp_ \**

### <a name="dhcp"></a>DHCP

* Protocolo DHCP (Dynamic Host Configuration Protocol)
* Mínimo de 3,6 KB a 4,6 KB FLASH, pegada de RAM de 2,7 KB
* Suporte ao cliente e ao servidor
* Suporte IPv4 e IPv6
* APIs intuitivos do DHCP: *nx_dhcp_ \**

### <a name="nat"></a>NAT

* Tradução de Endereços de Rede (NAT)
* Pegada mínima de 3,5K6 e 0,6 KB RAM
* Suporte de endereço IPv4
* APIs nat intuitivos: *nx_nat_ \**
* NAT só está disponível com Azure RTOS NetX Duo

### <a name="snmp"></a>SNMP

* SNMP (Simple Network Management Protocol)
* Pegada mínima de 10,9 KB e 2,6 KB RAM
* Apoio ao agente para VI, V2 e V3
* APIs intuitivos do SNMP: *nx_snmp_ \**

### <a name="dns-mdns-dns-sd"></a>DNS, mDNS, DNS-SD

* Sistema de Nomes de Domínio (DNS)
* Sistema de Nome de Domínio Multicast (mDNS)
* Descoberta de serviço baseada em DNS (DNS-SD)
* DNS Mínimo 2.4 KB a 3 KB FLASH, 1 KB RAM pegada
* Apoio ao cliente
* APIs intuitivos: *nx_dns_ \**
* mDNS e DNS-SD só estão disponíveis com Azure RTOS NetX Duo

### <a name="p0p3"></a>P0P3

* Protocolo dos Correios Versão 3 (POP3)
* Pegada mínima de 8,1 KB e 1,4 KB RAM
* Apoio ao cliente
* APIs P0P3 intuitivo: *nx_pop3_ \**

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
* Suporte à Internet Key Exchange (IKE) Versão 2
* IPsec Intuitivo APIs: *nx_ipsec_ \**
* IPsec só está disponível com Azure RTOS NetX Duo

## <a name="small-footprint"></a>Pequena pegada

O Azure RTOS NetX Duo tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP. Para a funcionalidade TCP, são necessários mais 10 KB a 13 KB de memória da área de instrução. O uso do Azure RTOS NetX Duo RAM varia tipicamente de 2,6 KB a 3,6 KB mais a memória do pacote pool, que é definido pela aplicação. Tal como o Azure RTOS ThreadX, o tamanho do Azure RTOS NetX Duo escala automaticamente com base nos serviços utilizados pela aplicação. Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.

## <a name="fast-execution"></a>Execução rápida

O Azure RTOS NetX Duo fornece uma implementação de envio/receção de pacotes de cópia zero, altamente integrada com a Azure RTOS ThreadX, para obter o desempenho mais rápido possível. Por exemplo, o Azure RTOS NetX Duo pode normalmente obter perto de transferências de dados de velocidade bancária num processador de 80 MHz (ou menos), utilizando apenas uma pequena percentagem dos ciclos do processador.

## <a name="simple-easy-to-use"></a>Simples e fácil de usar

O Azure RTOS NetX Duo API é intuitivo, simples e altamente funcional.

Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" ou nomes altamente abreviados que são tão comuns em outros produtos de networking. Todas as APIs Azure RTOS NetX Duo têm uma *nx_* líder e seguem uma convenção de nomeação de substantivos. Além disso, existe uma consistência funcional em toda a API. Por exemplo, todas as funções da API que suspendem têm um tempo limite opcional que funciona de forma idêntica.

Para aplicações antigas, o Azure RTOS NetX Duo oferece uma camada compatível com tomada BSD adicional. Esta camada ajuda os desenvolvedores a migrar grandes aplicações de networking com facilidade.

## <a name="safe-and-secure"></a>Seguro e seguro

Azure RTOS NetX Duo está seguro. Esta segurança é fornecida através de produtos de segurança adicionais, incluindo IPsec, SSL, TLS e DTLS. Além disso, a aplicação tem controlo total sobre todo o acesso externo ao Azure RTOS NetX Duo, tornando a determinação do risco de segurança muito mais fácil.

O Microsoft Azure RTOS fornece componentes para garantir a comunicação e criar o isolamento de códigos e dados utilizando mecanismos de proteção de hardware MCU/MPU subjacentes. Em última análise, é da responsabilidade do construtor de dispositivos garantir que o dispositivo satisfaz plenamente os requisitos de segurança em evolução associados ao seu caso de utilização específico.

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Pré-certificada pela TUV e UL para muitas normas de segurança

A Azure RTOS NetX Duo foi certificada pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128. A certificação confirma que o Azure RTOS NetX Duo pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais altos níveis de integridade da segurança da IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional de sistemas de segurança electrónica, eletrônicos e programáveis". A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="Certificação SGS-TUV":::

A Azure RTOS NetX Duo foi reconhecida pela UL pelo cumprimento do anexo H da UL 60730-1, do CSA E60730-1 Anexo H, do IEC 60730-1 anexo H, ul 60335-1 anexo R, do IEC 60335-1 anexo R e das normas de segurança 1998 para as normas de segurança em componentes programáveis. A UL é uma empresa global, independente e de ciência da segurança, com mais de um século de experiência em soluções de segurança inovadoras, que vão desde a adoção pública de eletricidade até avanços na sustentabilidade, energias renováveis e nanotecnologia.

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="Certificação CRU UL":::

Estão à venda artefactos (Certificado, Manual de Segurança, Relatório de Teste, etc.) associados às certificações TUV e UL.

Nos casos em que a aplicação necessita de certificação adicional, está disponível um serviço de certificação através da Microsoft para fornecer certificação chave-na-curva a vários padrões utilizando a plataforma de hardware real e até mesmo cobrindo o código de aplicação. Contacte-nos para mais detalhes sobre o nosso serviço de certificação.

## <a name="eal4-common-criteria-security-certification"></a>Certificação de segurança de critérios comuns EAL4+

A Azure RTOS obteve a certificação de segurança de critérios comuns EAL4+. O Alvo de Evalution (TOE) abrange Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS e Azure RTOS NetX MQTT. Isto representa os protocolos IoT mais típicos exigidos por sensores, dispositivos, routers de borda e gateways profundamente incorporados.

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Certificação EAL":::

O Mecanismo de Avaliação de Segurança de TI utilizado para a certificação de segurança Microsoft Azure RTOS SC é Brightsight BV e a Autoridade de Certificação é SERTIT.

## <a name="fips-140-2-validated"></a>FIPS 140-2 Validado

As bibliotecas Azure RTOS NetX Crypto alcançaram a Normalização Federal de Processamento de Informação 140-2 (FIPS 140-2) certificação para software, que especifica requisitos para módulos de criptografia. O FIPS 140-2 requer que todas as agências e departamentos do governo federal que utilizem a segurança criptográfica cumpram padrões específicos relacionados com a força e capacidades de encriptação. Estas normas de segurança criptográficas são também reconhecidas no Canadá e na União Europeia.

O laboratório de avaliação de Segurança da Informação utilizado para as bibliotecas Azure RTOS NetX Crypto foi atsec e a autoridade de certificação é o Instituto Nacional de Normalização e Tecnologia (NIST). Reveja o site da [NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) para mais detalhes.

## <a name="interoperability-verification"></a>Verificação da interoperabilidade

O NetX Duo está em conformidade com os padrões RFC e oferece uma interoperabilidade completa com dispositivos para a maioria dos fornecedores.

![Logotipo pronto do IPv6](./media/overview-netx-duo/ipv6-ready-logo.png)

O Azure RTOS NetX Duo é uma das únicas pilhas TCP/IP incorporadas para obter a rigorosa certificação IPv6-Ready Logo, prova de que passou testes de conformidade e interoperabilidade, administrados e validados pelo IPv6 Forum. A NetX Duo também utiliza a norma da indústria IxANVL (Biblioteca de Validação de Rede Automatizada) para a implementação do protocolo TCP/IP do núcleo netX Duo.

## <a name="comprehensive-iot-solution"></a>Solução IoT abrangente

O Azure RTOS NetX Duo tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP. A NetX Duo tem uma das redes TCP/IP mais abrangentes para aplicações IoT profundamente incorporadas. Este suporte inclui os seguintes produtos de protocolo adicional:

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

## <a name="fastest-time-to-market"></a>O tempo de venda mais rápido

O Azure RTOS NetX Duo é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter. Como resultado, o NetX Duo é uma das pilhas TCP/IP mais populares para dispositivos IoT incorporados, incluindo muitos SoCs da Broadcom, Gainspan, etc. A nossa vantagem consistente no mercado baseia-se em:

* Documentação de qualidade – por favor reveja [o nosso Guia de Utilizador Azure RTOS NetX Duo](about-this-guide.md) e veja por si mesmo!
* Disponibilidade completa de código fonte
* API de fácil utilização
* Conjunto de funcionalidades abrangente e avançado

## <a name="one-simple-license"></a>Uma licença simples

Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.

## <a name="full-highest-quality-source-code"></a>Código fonte completo e de alta qualidade

Ao longo dos anos, o código fonte Azure RTOS NetX Duo estabeleceu a fasquia em qualidade e facilidade de compreensão. Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.

## <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

O Azure RTOS NetX Duo funciona com microprocessadores mais populares de 32/64 bits fora da caixa, totalmente testados e totalmente suportados, incluindo as seguintes arquiteturas avançadas:

**Dispositivos Analógicos**: SHARC, Blackfin, CM4xx

**Núcleo de Andes**: RISC-V

**Ambiqmicro**: pollo MCUs

**BRAÇO**: RM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Cadência**: Xtensa, Diamante

**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi

**Cipreste**: RISC-V

**EnSilica**: eSi-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10

**Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Sinergia

**Silício** Laboratórios: EFM32

**Sinopses**: ARC 600, 700, ARC EM, ARC HS

**ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

**Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*

## <a name="related-services"></a>Serviços relacionados

O módulo de segurança Azure Security Center for IoT RTOS fornece uma solução de segurança abrangente para dispositivos Azure RTOS. O Módulo de Segurança para O Azure RTOS oferece deteção de atividade de rede maliciosa, baseamento de comportamento de dispositivo baseado em alerta personalizado e ajuda a melhorar a higiene de segurança do dispositivo. Saiba mais sobre o [Módulo de Segurança para Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) ou inicie com o Módulo de Segurança [Configurar para O Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.

## <a name="next-steps"></a>Passos seguintes

Para saber mais sobre o NetX Duo, comece com o Guia de [Utilizador Azure RTOS NetX Duo.](about-this-guide.md)
