---
title: O que é Microsoft Azure RTOS?
description: O Azure RTOS é um sistema operativo em tempo real (RTOS) para dispositivos IoT e edge alimentados por microcontroladores (MCUs).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 3b1c63135f6069652d7f66fc976b9d770a4dfeb2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826599"
---
# <a name="what-is-microsoft-azure-rtos"></a>O que é Microsoft Azure RTOS

O Azure RTOS é um sistema operativo em tempo real (RTOS) para dispositivos IoT e edge alimentados por microcontroladores (MCUs). O Azure RTOS foi concebido para suportar os dispositivos mais constrangidos (alimentados por bateria e com menos de 64 KB de memória flash).
 
O Azure RTOS é pré-certificado para uma variedade de normas de segurança. Estes incluem as certificações IEC 61508 SIL 4, IEC 62304 Classe C e ISO 26262 ASIL D. Azure RTOS ThreadX também é certificada do DO-178.

O Azure RTOS fornece um ambiente certificado de segurança EAL4+ Common Criteria, incluindo a segurança total da camada IP via IPsec e a segurança da camada de tomada via TLS e DTLS. A nossa biblioteca de criptomoedas de software obteve certificação FIPS 140-2. Também aproveitamos as capacidades criptográficas de hardware, a proteção da memória através de módulos ThreadX e o suporte para as funcionalidades de segurança ARMv8-M da ARM.

## <a name="components-of-azure-rtos"></a>Componentes do Azure RTOS

A plataforma Azure RTOS é a coleção de soluções de tempo de execução, incluindo Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo e Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

O Azure RTOS ThreadX é um Sistema Operativo em Tempo Real (RTOS) avançado criado especificamente para aplicações profundamente incorporadas. Entre os múltiplos benefícios que a Azure RTOS ThreadX oferece estão instalações avançadas de agendamento, passagem de mensagens, gestão de interrupção e serviços de mensagens. O Azure RTOS ThreadX tem muitas funcionalidades avançadas, incluindo a sua arquitetura picokernel, agendamento de limiares de pré-edição, acorrentação de eventos e um rico conjunto de serviços de sistema.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure RTOS FileX é um sistema de ficheiros compatível com GORDURA de alto desempenho. Está totalmente integrado com a Azure RTOS ThreadX e está disponível para todos os processadores suportados. Tal como o Azure RTOS ThreadX, o Azure RTOS FileX foi concebido para ter uma pequena pegada e alto desempenho, tornando-o ideal para as aplicações profundamente incorporadas que requerem operações de ficheiros. O Azure RTOS FileX suporta a maioria dos meios físicos, incluindo disco RAM, USBX, SD CARD e memórias flash NAND/NOR via Azure RTOS LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

O Azure RTOS GUIX é um pacote de interface gráfico de qualidade profissional, criado para atender às necessidades dos desenvolvedores de sistemas incorporados. Ao contrário das alternativas, o Azure RTOS GUIX é pequeno, rápido e facilmente apostado em praticamente qualquer configuração de hardware capaz de suportar a saída gráfica. O Azure RTOS GUIX também oferece um apelo visual excecional e uma API intuitiva e poderosa para o desenvolvimento da interface de utilizador ao nível da aplicação.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure RTOS NetX é uma implementação de alto desempenho das normas do protocolo TCP/IP. Está totalmente integrado com a Azure RTOS ThreadX, e está disponível para todos os processadores suportados. A Azure RTOS NetX tem uma arquitetura piconet única. Combinado com uma API de cópia zero, torna-o perfeito para as aplicações profundamente incorporadas que requerem conectividade de rede.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure RTOS NetX Duo é uma pilha de rede TCP/IP de grau industrial avançada projetada especificamente para aplicações profundamente incorporadas, em tempo real e IoT. Azure RTOS NetX Duo é uma pilha de rede dual IPv4 e IPv6, enquanto netX é a pilha original de rede IPv4, essencialmente um subconjunto de Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure RTOS USBX é um hospedeiro USB de alto desempenho, dispositivo e stack incorporado On-The-Go (OTG). Está totalmente integrado com a ThreadX e está disponível para todos os processadores suportados pela Azure RTOS ThreadX. Tal como o Azure RTOS ThreadX, o Azure RTOS USBX foi projetado para ter uma pequena pegada e alto desempenho, tornando-o ideal para aplicações profundamente incorporadas que requerem uma interface com dispositivos USB.

### <a name="windows-tools"></a>Ferramentas windows

O Azure RTOS GUIX Studio oferece um ambiente completo de design de aplicações GUI, facilitando a criação e manutenção de todos os elementos gráficos no GUI da aplicação. O Azure RTOS GUIX Studio gera automaticamente código C compatível com a biblioteca Azure RTOS GUIX, pronta a ser compilada e executada no alvo.

O Azure RTOS TraceX é uma ferramenta de análise baseada em hospedeiros que proporciona aos desenvolvedores uma visão gráfica dos eventos do sistema em tempo real e permite-lhes visualizar e entender melhor o comportamento dos seus sistemas em tempo real.

## <a name="in-the-context-of-azure-iot"></a>No contexto de Azure IoT

Além de ligar diretamente ao Azure IoT ou ligar-se indiretamente através do Azure IoT Edge, o Azure RTOS também está disponível em dispositivos Azure Sphere. A combinação de Azure RTOS e Azure Sphere reúne o processamento e a segurança em tempo real em tempo real num único dispositivo.
