---
title: Capítulo 1 - Introdução à Pilha de Anfitriões USBX Azure RTOS
description: Este capítulo introduz a pilha de anfitriões USBX, descrevendo as suas aplicações e benefícios.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe9b3e4f36a50af9c1267b2e6285b77feecd946660bf23691e70cb66f8bc042
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791005"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a>Capítulo 1 - Introdução à Pilha de Anfitriões USBX Azure RTOS

USBX é uma pilha USB completa para aplicações profundamente incorporadas. Este capítulo introduz USBX, descrevendo as suas aplicações e benefícios.

## <a name="usbx-features"></a>Recursos USBX

USBX suporta as três especificações USB existentes: 1.1, 2.0 e OTG. Foi projetado para ser escalável e irá acomodar as simples topologias USB com apenas um dispositivo conectado, bem como topologias complexas com múltiplos dispositivos e centros em cascata. O USBX suporta todos os tipos de transferência de dados dos protocolos USB: controlo, granel, interrupção e isocronous.

O USBX suporta tanto o lado do anfitrião como o lado do dispositivo. Cada lado é composto por três camadas.

- Camada do controlador
- Camada de pilha
- Camada de classe

A relação entre as camadas USB é a seguinte.

![Camadas USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a>Destaques do produto

- Suporte completo do processador ThreadX
- Sem royalties
- Complete o código fonte ANSI C
- Desempenho em tempo real
- Suporte técnico responsivo
- Suporte de controlador de vários anfitriões
- Suporte de classe múltipla
- Múltiplas instâncias de classe
- Integração de classes com ThreadX, FileX e NetX
- Suporte para dispositivos USB com múltiplas configurações
- Suporte para dispositivos compostos USB
- Apoio aos centros em cascata
- Suporte para gestão de energia USB
- Suporte para OTG USB
- Eventos de rastreio de exportação para TraceX

## <a name="powerful-services-of-usbx"></a>Serviços Poderosos da USBX

### <a name="multiple-host-controller-support"></a>Suporte ao controlador de vários anfitriões

USBX pode suportar vários controladores de anfitriões USB em execução em simultâneo. Esta funcionalidade permite que o USBX suporte a norma USB 2.0 utilizando o esquema de retrocompatibilidade associado à maioria dos controladores anfitriões USB 2.0 no mercado.

### <a name="usb-software-scheduler"></a>Programador de software USB

USBX contém um programador de software USB necessário para suportar controladores USB que não têm processamento de lista de hardware. O programador de software USBX organizará transferências USB com a frequência correta de serviço e prioridade, e instruirá o controlador USB a executar cada transferência.

### <a name="complete-usb-device-framework-support"></a>Suporte completo do dispositivo USB

O USBX pode suportar os dispositivos USB mais exigentes, incluindo múltiplas configurações, múltiplas interfaces e múltiplas configurações alternativas.

### <a name="easy-to-use-apis"></a>APIs fáceis de usar

A USBX fornece a melhor pilha USB profundamente incorporada de uma forma que é fácil de entender e usar. A API USBX torna os serviços intuitivos e consistentes. Ao utilizar as APIs de classe USBX fornecidas, a aplicação do utilizador não precisa de compreender a complexidade dos protocolos USB.
