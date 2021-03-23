---
title: Compreenda Azure RTOS USBX
description: Azure RTOS USBX é um hospedeiro USB de alto desempenho, dispositivo e stack incorporado em movimento (OTG), O Azure RTOS USBX está totalmente integrado com Azure RTOS ThreadX e está disponível para todos os processadores suportados por Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 87eb6ee9f8733db3201280d377aa832b87131871
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828471"
---
# <a name="overview-of-azure-rtos-usbx"></a>Visão geral do Azure RTOS USBX

Azure RTOS USBX é um hospedeiro USB de alto desempenho, dispositivo e stack incorporado on-the-go (OTG). O Azure RTOS USBX está totalmente integrado com o Azure RTOS ThreadX e está disponível para todos os processadores suportados pela ThreadX. Tal como o ThreadX, o Azure RTOS USBX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para aplicações profundamente incorporadas que requerem uma interface com dispositivos USB.

## <a name="host-device-otg--extensive-class-support"></a>Hospedeiro, dispositivo, OTG & suporte de classe extensiva

A pilha de protocolo USB,de Azure RTOS USBX é uma solução USB incorporada em grau industrial projetada especificamente para aplicações de IoT profundamente incorporadas, em tempo real e ioT. O Azure RTOS USBX fornece suporte ao hospedeiro, dispositivo e OTG, bem como um extenso suporte de classe. O Azure RTOS USBX está totalmente integrado com o Sistema Operativo ThreadX Real-Time, o Azure RTOS FileX incorporado no sistema de ficheiros compatível com a GORDURA, o Azure RTOS NetX e o Azure RTOS NetX Duo incorporados TCP/IP. Tudo isto, combinado com uma pegada extremamente pequena, execução rápida e facilidade superior de utilização, fazem do Azure RTOS USBX a escolha ideal para as aplicações IoT incorporadas mais exigentes que requerem conectividade USB.

### <a name="small-footprint"></a>Pequena pegada

O Azure RTOS USBX tem uma pegada mínima notável de 10,5 KB de FLASH e 5.1 KB RAM para suporte a um dispositivo USBX Azure RTOS CDC/ACM. O anfitrião Azure RTOS USBX requer um mínimo de 18 KB de FLASH e 25 KB de RAM para suporte CDC/ACM.

Para a funcionalidade TCP, são necessários mais 10 KB a 13 KB de memória da área de instrução. O uso do RAM Azure RTOS USBX varia tipicamente de 2,6 KB a 3,6 KB mais a memória do pacote pool, que é definido pela aplicação.

Tal como o ThreadX, o tamanho do Azure RTOS USBX escala automaticamente com base nos serviços realmente utilizados pela aplicação. Isto praticamente elimina a necessidade de configuração complicada e constrói parâmetros, tornando as coisas mais fáceis para o desenvolvedor.

### <a name="fast-execution"></a>Execução rápida

O Azure RTOS USBX foi concebido para velocidade e tem camadas mínimas de chamada interna e suporte para cache e utilização de DMA. Tudo isto e uma filosofia geral de design orientada para o desempenho ajuda o Azure RTOS USBX a alcançar o desempenho mais rápido possível.

### <a name="simple-easy-to-use"></a>Simples e fácil de usar

Azure RTOS USBX é simples de usar. O Azure RTOS USBX API é simultaneamente intuitivo e altamente funcional. Os nomes da API são feitos de palavras reais e não da "sopa do alfabeto" ou nomes altamente abreviados que são tão comuns em outros produtos do sistema de ficheiros. Todas as APIs Azure RTOS USBX têm um "ux_" líder e seguem uma convenção de nomeação de substantivos. Além disso, existe uma consistência funcional em toda a API. Por exemplo, todas as APIs que suspendem têm um tempo limite opcional que funciona de forma idêntica para as APIs.

### <a name="usb-interoperability-verification"></a>Verificação da interoperabilidade USB

A azure RTOS USBX Device Stack foi rigorosamente testada com a ferramenta de teste padrão USB IF USBCV para garantir o pleno cumprimento das especificações USB e interoperabilidade com diferentes sistemas de anfitrião.
Além disso, a pilha Azure RTOS USBX OTG foi verificada e certificada pelo laboratório independente allion em Taiwan.

### <a name="usb-host-controller-support"></a>Suporte do controlador do anfitrião USB

O Azure RTOS USBX suporta grandes padrões USB como OHCI e EHCI. Além disso, o Azure RTOS USBX suporta controladores de anfitriões USB discretos proprietários da Atmel, Microchip, Philips, Renesas, ST, TI e outros fornecedores. O Azure RTOS USBX também suporta vários controladores hospedeiros na mesma aplicação.
Suporte ao controlador de dispositivos USB Azure RTOS USBX suporta controladores de dispositivos USB populares de Dispositivos Analógicos, Atmel, Microchip, NXP, Philips, Renesas, ST, TI e outros fornecedores.

### <a name="extensive-host-class-support"></a>Apoio extensivo da classe de anfitrião

O Azure RTOS USBX Host fornece suporte para as classes mais populares, incluindo ASIX, AUDIO, CDC/ACM, CDC/ECM, GSER, HID (teclado, rato e controlo remoto), HUB, PIMA (PTP/MTP), IMPRESSORA, PROLIFIC e ARMAZENAMENTO.

### <a name="extensive-usb-device-class-support"></a>Suporte extensivo da classe de dispositivo USB

O Dispositivo Azure RTOS USBX fornece suporte para as classes mais populares, incluindo CDC/ACM, CDC/ECM, DFU, HID, PIMA (PTP/MTP) (c/MTP), RNDIS e ARMAZENAMENTO. O suporte para aulas personalizadas também está disponível.

### <a name="pictbridge-support"></a>Suporte pictbridge

O Azure RTOS USBX suporta toda a implementação de Pictbridge tanto no hospedeiro como no dispositivo. Pictbridge fica em cima da classe Azure RTOS USBX PIMA (PTP/MTP) em ambos os lados. A norma PictBridge permite a ligação de uma câmara digital parada ou um telefone inteligente diretamente a uma impressora sem PC, permitindo a impressão direta a certas impressoras conscientes de Pictbridge. Quando uma câmara ou telefone está ligado a uma impressora, a impressora é o anfitrião USB e a câmara é o dispositivo USB. No entanto, com Pictbridge, a câmara aparecerá como sendo o anfitrião e os comandos são expulsos da câmara. A câmara é o servidor de armazenamento, a impressora o cliente de armazenamento. A câmara é o cliente de impressão e a impressora é, naturalmente, o servidor de impressão. Pictbridge usa USB como camada de transporte, mas depende de PTP (Protocolo de Transferência de Imagem) para o protocolo de comunicação.

### <a name="custom-class-support"></a>Suporte de classe personalizado

Azure RTOS USBX Host and Device suportam aulas personalizadas. Uma classe personalizada de exemplo é fornecida na distribuição Azure RTOS USBX. Esta classe simples de bomba de dados chama-se DPUMP e pode ser usada como um modelo para classes de aplicações personalizadas.
Tecnologia avançada Azure RTOS USBX Host e Device suportam classes personalizadas. Uma classe personalizada de exemplo é fornecida na distribuição Azure RTOS USBX. Azure RTOS USBX é uma tecnologia avançada que inclui:

* Suporte ao anfitrião, dispositivo e OTG
* Suporte USB baixo, completo e de alta velocidade
* Dimensionamento automático
* Totalmente integrado com ThreadX, Azure RTOS FileX e Azure RTOS NetX
* Métricas de desempenho opcionais
* Suporte de análise do sistema Azure RTOS TraceX

### <a name="fastest-time-to-market"></a>O tempo de venda mais rápido

O Azure RTOS USBX tem uma pegada notavelmente pequena de 9 KB a 15 KB para suporte básico de IP e UDP. O Azure RTOS USBX é fácil de instalar, aprender, usar, depurar, verificar, certificar e manter. Como resultado, o Azure RTOS USBX é uma das soluções USB mais populares para dispositivos IoT incorporados. A nossa vantagem consistente no mercado baseia-se em:

* Documentação de qualidade – por favor, reveja os nossos Guias de Anfitriões e Utilizadores de Dispositivos Azure RTOS e veja por si mesmo!
* Disponibilidade completa de código fonte
* API de fácil utilização
* Conjunto de funcionalidades abrangente e avançado

## <a name="one-simple-license"></a>Uma licença simples

Não há qualquer custo para usar e testar o código fonte e nenhum custo para licenças de produção quando implementados em dispositivos pré-licenciados, todos os outros dispositivos precisam de uma licença anual simples.

## <a name="full-highest-quality-source-code"></a>Código fonte completo e de alta qualidade

Ao longo dos anos, o código fonte Azure RTOS NetX definiu a fasquia em qualidade e facilidade de compreensão. Além disso, a convenção de ter uma função por ficheiro prevê uma fácil navegação de origem.

### <a name="supports-most-popular-architectures"></a>Apoia as arquiteturas mais populares

O Azure RTOS USBX funciona nos microprocessadores mais populares de 32/64 bits, fora da caixa, totalmente testados e totalmente suportados, incluindo os seguintes:

* **Dispositivos Analógicos**: SHARC, Blackfin, CM4xx
* **Núcleo de Andes**: RISC-V
* **Ambiqmicro**: Apollo MCUs
* **BRAÇO**: ARM7, ARM9, ARM11, Córtex-M0/M3/M4/M7/A15/A5/A7/A8/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M
* **Cadência**: Xtensa, Diamante
* **CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WiCED WiFi
* **Cipreste**: RISC-V
* **EnSilica**: eSi-RISC
* **Infineon**: XMC1000, XMC4000, TriCore
* **Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Ciclone, Arria 10
* **Microchip**: AVR32, ARM7, ARM9, Córtex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32
* **Microsemi**: RISC-V
* **NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4
* **Renesas**: SH, HS, V850, RX, RZ, Synergy Silicon Labs: EFM32
* **Sinopses**: ARC 600, 700, ARC EM, ARC HS
* **ST**: STM32, ARM7, ARM9, Córtex-M3/M4/M7
* **Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C
* **Computação de ondas**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

## <a name="azure-rtos-usbx-apis"></a>Azure RTOS USBX APIs

### <a name="azure-rtos-usbx-host-api"></a>Azure RTOS USBX Host API

O Azure RTOS USBX Host API é uma API intuitiva e consistente, seguindo uma convenção de nomeação de substantivos verbos. Todas as APIs têm ux_host_* para identificar facilmente como USBX. Quaisquer APIs de bloqueio têm tempo de tempo de linha opcional.

* ASIX
    - Mínimo de 0,3 KB FLASH, 4 KB RAM
    - Escala automática Vestígios de nível de sistema através do Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_asix_**
* ÁUDIO
    - Mínimo de 1,2 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_audio_**
* CDC/ACM
    - Mínimo de 1,4 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_cdc_acm_**
* HID
    - Mínimo de 0,3 KB FLASH, 4 KB RAM
    - Teclado, rato e suporte remoto
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_hid_** 
* HUB
    - Mínimo de 1,7 KB FLASH, 2 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_hub_**
* PIMA (PTP/MTP)
    - Mínimo de 0,9 KB FLASH, 8 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_pima_**
* IMPRESSORA
    - Mínimo de 0,8 KB FLASH, 8 KB RAM
    - Dimensionamento automático
    -  Traços de nível do sistema via Azure RTOS TraceX
    -  Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_printer_**
* PROLÍFICO
    - Mínimo de 1,5 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_prolific_**
* RIO STORAG
    - Mínimo de 5,6 KB FLASH, 4 KB RAM
    - Dimensionamento automático<br> Integrado com Azure RTOS FileX
    - Traços de nível do sistema via Azure RTOS TraceX
    - Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_class_storage_**
* PILHA DE anfitrião USB
    - Suporta muitos controladores hospedeiros
    - Mínimo de 18 KB FLASH, 25 KB RAM
    - Dimensionamento automático
    - Suporte para vários controladores de anfitriões na mesma plataforma
    -  Suporte USB baixo, completo e de alta velocidade
    -  Traços de nível do sistema via Azure RTOS TraceX
    -  Azure Azure RTOS USBX hospeda APIs neste formulário: *ux_host_stack_* * 
* OHCI, EHCI, CONTROLADORES DE HOSPEDEIROS PROPRIETÁRIOS 

### <a name="azure-rtos-usbx-device-api"></a>Azure RTOS USBX Device API

O Azure RTOS USBX Device API é uma API intuitiva e consistente na sequência de uma convenção de nomeação de substantivos verbos. Todas as APIs têm levado ux_device_* a identificar-se facilmente como USBX. As APIs de bloqueio têm um tempo limite opcional de linha. Consulte o [Guia do Utilizador do Anfitrião Azure RTOS USBX](usbx-host-stack-about.md) para obter mais detalhes.

* CDC/ACM
    - Mínimo de 0,8 KB FLASH, 2 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs dispositivo INTUItivo Azure RTOS USBX nesta forma: *ux_device_class_cdc_acm_**.
* CDC/ECM
    - Mínimo de 1,5 KB FLASH, 4 KB a 8 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX<br> ApIs dispositivo INTUItivo Azure RTOS USBX nesta forma: *ux_device_class_cdc_ecm_**.
* DFU
    - Mínimo de 1,1 KB FLASH, 2 KB RAM
    -  Dimensionamento automático
    -  Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_dfu_** 
* RIO GSER
    - Mínimo de 0,6 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_gser_**
* HID
    - Mínimo de 0,9 KB FLASH, 2 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - Dispositivo intuitivo Azure RTOS USBX apIs neste formulário: *ux_device_class_hid_** PIMA (PTP/MTP)
    - Mínimo de 5,2 KB FLASH, 8 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_pima_** 
* ARMAZENAMENTO
    - Mínimo de 2,3 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_storage_**
* Rio RNDIS
    - Mínimo de 2,3 KB FLASH, 4 KB a 8 KB RAM
    - Dimensionamento automático
    - Integrado com Azure RTOS NetX e Azure RTOS NetX DUO
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_rndls_**
* Stack de dispositivo USBX Azure RTOS
    - Mínimo de 2,3 KB FLASH, 4 KB RAM
    - Dimensionamento automático
    - Traços de nível do sistema via Azure RTOS TraceX
    - ApIs do dispositivo INTUItivo Azure RTOS USBX neste formulário: *ux_device_class_storage_**
* CONTROLADORES DE HOSPEDEIROS PROPRIETÁRIOS

## <a name="next-steps"></a>Passos seguintes

Comece a trabalhar com o anfitrião e a pilha de dispositivos Azure RTOS USBX seguindo o nosso [Guia de Utilizador da Pilha de Anfitriões](usbx-host-stack-about.md) ou o Guia do Utilizador da Pilha de [Dispositivos](usbx-device-stack-about.md).