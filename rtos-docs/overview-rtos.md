---
title: O que é Microsoft Azure RTOS?
description: O Azure RTOS é um sistema operativo em tempo real (RTOS) para dispositivos IoT e edge alimentados por microcontroladores (MCUs).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a6f9cfd772c81340a90b7dc217c0ccc160c7f957
ms.sourcegitcommit: 7993d2c3b0711ae2c246561a0c8bf963d8e0324a
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/24/2021
ms.locfileid: "114661203"
---
# <a name="what-is-microsoft-azure-rtos"></a>O que é Microsoft Azure RTOS?

O Azure RTOS é um sistema operativo em tempo real (RTOS) para internet das coisas (IoT) e dispositivos de borda alimentados por unidades de microcontrolador (MCUs). O Azure RTOS foi concebido para suportar os dispositivos mais constrangidos (alimentados por bateria e com menos de 64 KB de memória flash).

O Azure RTOS é pré-certificado para uma variedade de normas de segurança. Estes incluem as certificações IEC 61508 SIL 4, IEC 62304 Classe C e ISO 26262 ASIL D.

O Azure RTOS fornece um ambiente certificado de segurança EAL4+ Common Criteria, incluindo a segurança total da camada IP via IPsec e a segurança da camada de tomada via TLS e DTLS. A nossa biblioteca de criptomoedas de software obteve certificação FIPS 140-2. Também aproveitamos as capacidades criptográficas de hardware, a proteção da memória através de módulos ThreadX e o suporte para as funcionalidades de segurança ARMv8-M da ARM.

## <a name="components-of-azure-rtos"></a>Componentes do Azure RTOS

A plataforma Azure RTOS é a coleção de soluções de tempo de execução, incluindo Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo e Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

A Azure [RTOS ThreadX](threadx/overview-threadx.md) é um sistema operativo avançado Real-Time (RTOS) projetado especificamente para aplicações profundamente incorporadas. Entre os múltiplos benefícios que a Azure RTOS ThreadX oferece estão instalações avançadas de agendamento, passagem de mensagens, gestão de interrupção e serviços de mensagens. O Azure RTOS ThreadX tem muitas funcionalidades avançadas, incluindo a sua arquitetura picokernel, agendamento de limiares de pré-edição, acorrentação de eventos e um rico conjunto de serviços de sistema.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure [RTOS FileX](filex/overview-filex.md) é um sistema de ficheiros compatível com GORDURA de alto desempenho. Está totalmente integrado com a Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de ficheiros. O Azure RTOS FileX suporta a maioria dos meios físicos, incluindo disco RAM, USBX, SD CARD e memórias flash NAND/NOR via Azure RTOS LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

O Azure [RTOS GUIX](guix/overview-guix.md) é um pacote de interface gráfico de qualidade profissional, criado para atender às necessidades dos desenvolvedores de sistemas incorporados. Ao contrário das alternativas, o Azure RTOS GUIX é pequeno, rápido e facilmente apostado em praticamente qualquer configuração de hardware capaz de suportar a saída gráfica. O Azure RTOS GUIX também oferece um apelo visual excecional e uma API intuitiva e poderosa para o desenvolvimento da interface de utilizador ao nível da aplicação.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure [RTOS NetX](netx/overview-netx.md) é uma implementação de alto desempenho das normas do protocolo TCP/IP. Está totalmente integrado com a Azure RTOS ThreadX, e está disponível para todos os processadores suportados. A Azure RTOS NetX tem uma arquitetura piconet única. Combinado com uma API de cópia zero, torna-o perfeito para as aplicações profundamente incorporadas que requerem conectividade de rede.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo é uma pilha de rede TCP/IP de grau industrial avançada projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT. Azure RTOS NetX Duo é uma pilha de rede dual IPv4 e IPv6, enquanto netX é a pilha original de rede IPv4, essencialmente um subconjunto de Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure [RTOS USBX](usbx/overview-usbx.md) é um hospedeiro USB de alto desempenho, dispositivo e stack incorporado On-The-Go (OTG). Está totalmente integrado com a ThreadX e está disponível para todos os processadores suportados pela Azure RTOS ThreadX. Tal como o Azure RTOS ThreadX, o Azure RTOS USBX foi projetado para ter uma pequena pegada e alto desempenho, tornando-o ideal para aplicações profundamente incorporadas que requerem uma interface com dispositivos USB.

### <a name="windows-tools"></a>Windows ferramentas

O Azure [RTOS GUIX Studio](guix/about-guix-studio.md) oferece um ambiente completo de design de aplicações GUI, facilitando a criação e manutenção de todos os elementos gráficos no GUI da aplicação. O Azure RTOS GUIX Studio gera automaticamente código C compatível com a biblioteca Azure RTOS GUIX, pronta a ser compilada e executada no alvo.

O Azure [RTOS TraceX](tracex/overview-tracex.md) é uma ferramenta de análise baseada em hospedeiros que proporciona aos desenvolvedores uma visão gráfica dos eventos do sistema em tempo real e permite-lhes visualizar e entender melhor o comportamento dos seus sistemas em tempo real.

## <a name="the-azure-rtos-advantage"></a>A vantagem Azure RTOS
O Azure RTOS oferece as seguintes vantagens sobre outros sistemas operativos em tempo real.

### <a name="most-deployed-rtos"></a>RTOS mais implantado

A Azure RTOS tem mais de 6,2 mil milhões de implantações em todo o mundo, de acordo com a principal empresa de inteligência de mercado M2M, a VDC Research. A popularidade do Azure RTOS é um testemunho da sua fiabilidade, qualidade, tamanho, desempenho, funcionalidades avançadas, facilidade de utilização e vantagens gerais de tempo para mercado.

> *"Temos acompanhado a trajetória de crescimento da THREADX nos mercados sem fios e IoT desde a fundação da empresa, e estamos cada vez mais impressionados com a adoção generalizada da THREADX pela indústria."* – Chris Rommel, Vice-Presidente Executivo, VDC Research

### <a name="intuitive-and-consistent-api-design"></a>Design api intuitivo e consistente

* API intuitiva e consistente.
* Convenção de nomeação de substantivos.
* Todas as APIs têm prefixo líder, como *tx_* para ThreadX e *fx_* para FileX, para identificar facilmente o componente Azure RTOS a que pertencem.
* Consistência funcional em todas as APIs. Por exemplo, todas as funções da API que suspendem têm um tempo limite opcional que funciona de forma idêntica.
* Muitas APIs estão diretamente disponíveis a partir de ISRs de aplicação.
- Chamadas de notificação de utilizador opcionais para meios de comunicação e operações de ficheiros.
* Modelo de programação orientado para eventos (API).

### <a name="high-efficiency"></a>Alta eficiência

- Pequena pegada de código.
- Pegada de código escalável com base nos serviços utilizados.
- Pré-certificada pela TUV e UL ao IEC 61508 SIL 4, IEC 62304 Classe C, ISO 26262 ASIL D e EN 50128 SW-SIL4.
- Execução rápida. O Azure RTOS foi concebido para a velocidade e tem camadas mínimas de chamada de função interna para ajudar a alcançar o desempenho mais rápido possível.

### <a name="fastest-time-to-market"></a>O tempo de venda mais rápido

O Azure RTOS é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter. Como resultado, o Azure RTOS é um dos sistemas operativos em tempo real mais populares para dispositivos IoT incorporados, incluindo muitos SoCs da Broadcom, Gainspan, e assim por diante. A nossa vantagem consistente no mercado baseia-se em:

* Disponibilidade completa de código fonte.
* API fácil de usar.
* Conjunto de recursos abrangente e avançado.
* Documentação de qualidade.

### <a name="one-simple-license"></a>Uma licença simples

Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.

### <a name="full-highest-quality-source-code"></a>Código fonte completo e de alta qualidade

Ao longo dos anos, o código fonte Azure RTOS definiu a fasquia em qualidade e facilidade de compreensão. Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Pré-certificada pela TUV e UL para muitas normas de segurança

O Azure RTOS foi certificado pela SGS-TUV Saar para utilização em sistemas críticos de segurança, de acordo com o IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D e EN 50128. A certificação confirma que o Azure RTOS pode ser utilizado no desenvolvimento de software relacionado com a segurança para os mais elevados níveis de integridade de segurança do IEC-61508, IEC-62304, ISO 26262 e EN 50128 para a "Segurança Funcional dos sistemas eletrónicos, eletrónicos e programáveis relacionados com a segurança electrónica". A SGS-TUV Saar, formada através de uma joint venture da SGS-Group alemã e tuv Saarland, tornou-se a principal empresa acreditada e independente para testes, auditorias, verificação e certificação de software incorporado para sistemas relacionados com a segurança em todo o mundo. A norma de segurança industrial IEC 61508, e todas as normas que dela derivam, incluindo a IEC-62304, a ISO 26262 e a EN 50128, são utilizadas para garantir a segurança funcional de dispositivos médicos elétricos, eletrónicos e programáveis relacionados com a segurança electrónica, sistemas de controlo de processos, máquinas industriais, automóveis e sistemas de controlo ferroviário.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="Certificação SGS-TUV":::

A Azure RTOS foi reconhecida pela UL pelo cumprimento do anexo H da UL 60730-1, do anexo CSA E60730-1, do IEC 60730-1 Anexo H, ul 60335-1 Anexo R, do IEC 60335-1 anexo R e da UL 1998 para normas de segurança para os softwares em componentes programáveis. A UL é uma empresa global, independente e de ciência da segurança, com mais de um século de experiência em soluções de segurança inovadoras, que vão desde a adoção pública de eletricidade até avanços na sustentabilidade, energias renováveis e nanotecnologia.

:::image type="content" source="media/cru-logo-certification.png" alt-text="Certificação CRU UL":::

Estão à venda artefactos (Certificado, Manual de Segurança, Relatório de Teste, etc.) associados às certificações TUV e UL.

Nos casos em que a aplicação necessita de certificação adicional, está disponível um serviço de certificação através da Microsoft para fornecer certificação chave-na-curva a vários padrões utilizando a plataforma de hardware real e até mesmo cobrindo o código de aplicação. Contacte-nos para mais detalhes sobre o nosso serviço de certificação.

### <a name="eal4-common-criteria-security-certification"></a>Certificação de segurança de critérios comuns EAL4+

A Azure RTOS obteve a certificação de segurança de critérios comuns EAL4+. O Alvo de Avaliação (TOE) abrange Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS e Azure RTOS NetX MQTT. Isto representa os protocolos IoT mais típicos exigidos por sensores, dispositivos, routers de borda e gateways profundamente incorporados.

:::image type="content" source="media/eal-logo-certification.png" alt-text="Certificação EAL":::

O Mecanismo de Avaliação de Segurança de TI utilizado para a certificação de segurança RTOS SC Microsoft Azure é brightsight BV e a Autoridade de Certificação é SERTIT.

### <a name="fips-140-2-validated"></a>FIPS 140-2 Validado

As bibliotecas Azure RTOS Crypto alcançaram a Normalização Federal de Processamento de Informação 140-2 (FIPS 140-2) Certificação para software, que especifica requisitos para módulos de criptografia. O FIPS 140-2 requer que todas as agências e departamentos do governo federal que utilizem a segurança criptográfica cumpram padrões específicos relacionados com a força e capacidades de encriptação. Estas normas de segurança criptográficas são também reconhecidas no Canadá e na União Europeia.

O laboratório de avaliação de Segurança da Informação utilizado para as bibliotecas Azure RTOS Crypto foi atsec e a autoridade de certificação é [o Instituto Nacional de Normalização e Tecnologia (NIST)](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394).

### <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

Azure RTOS em microprocessadores mais populares de 32/64 bits, fora da caixa, totalmente testados e totalmente suportados, incluindo as seguintes arquiteturas avançadas.

- **Dispositivos Analógicos**: SHARC, Blackfin, CM4xx

- **Núcleo de Andes**: RISC-V

- **Ambiqmicro**: Apollo MCUs

- **BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M

- **Cadência**: Xtensa, Diamante

- **CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi

- **Cipreste**: RISC-V

- **EnSilica**: eSi-RISC

- **Infineon**: XMC1000, XMC4000, TriCore

- **Informação; Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10

- **Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

- **Microsemi**: RISC-V

- **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

- **Renesas**: SH, HS, V850, RX, RZ, Sinergia

- **Laboratórios de Silício**: EFM32

- **Sinopses**: ARC 600, 700, ARC EM, ARC HS

- **ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7

- **Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C

- **Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, Classe M

- **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Todos os valores de tempo e tamanho listados são estimativas e podem ser diferentes na sua plataforma de desenvolvimento.*

## <a name="in-the-context-of-azure-iot"></a>No contexto de Azure IoT

Além de ligar diretamente ao Azure IoT ou ligar-se indiretamente através do Azure IoT Edge, o Azure RTOS também está disponível em dispositivos Azure Sphere. A combinação de Azure RTOS e Azure Sphere reúne o processamento e a segurança em tempo real em tempo real num único dispositivo.
