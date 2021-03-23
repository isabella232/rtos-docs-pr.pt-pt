---
title: Capítulo 3 - Considerações da Classe USBX DPUMP
description: USBX contém uma classe DPUMP para o lado do hospedeiro e dispositivo. Esta classe não é uma classe padrão em si, mas sim um exemplo que ilustra como criar um dispositivo simples usando dois tubos a granel e enviando dados para trás e para a frente nestes dois tubos
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c7870f1984fe3104d30e3b9efd82010218acbe27
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828615"
---
# <a name="chapter-3---usbx-dpump-class-considerations"></a>Capítulo 3 - Considerações da Classe USBX DPUMP

USBX contém uma classe **DPUMP** para o lado do hospedeiro e dispositivo. Esta classe não é uma classe padrão em si, mas sim um exemplo que ilustra como criar um dispositivo simples usando dois tubos a granel e enviando dados para trás e para a frente nestes dois tubos. A classe **DPUMP** pode ser usada para iniciar uma classe personalizada ou para dispositivos RS232 legados.

Gráfico de fluxo USB DPUMP:

![Gráfico de fluxo USB DPUMP](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a>Classe de dispositivo USBX DPUMP

A classe **DPUMP** do dispositivo utiliza um fio, que é iniciado na ligação ao hospedeiro USB. O fio aguarda um pacote vindo no ponto final do Bulk out. Quando um pacote é recebido, copia o conteúdo para o tampão de ponto final em volume de descontos e regista uma transação neste ponto final, aguardando que o anfitrião emita um pedido para ler a partir deste ponto final. Isto fornece um mecanismo de retorno entre o Bulk out e o Bulk Em pontos finais.
