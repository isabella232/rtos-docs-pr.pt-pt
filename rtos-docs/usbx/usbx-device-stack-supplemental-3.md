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
# <a name="chapter-3---usbx-dpump-class-considerations"></a><span data-ttu-id="8959a-104">Capítulo 3 - Considerações da Classe USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="8959a-104">Chapter 3 - USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="8959a-105">USBX contém uma classe **DPUMP** para o lado do hospedeiro e dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8959a-105">USBX contains a **DPUMP** class for the host and device side.</span></span> <span data-ttu-id="8959a-106">Esta classe não é uma classe padrão em si, mas sim um exemplo que ilustra como criar um dispositivo simples usando dois tubos a granel e enviando dados para trás e para a frente nestes dois tubos.</span><span class="sxs-lookup"><span data-stu-id="8959a-106">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="8959a-107">A classe **DPUMP** pode ser usada para iniciar uma classe personalizada ou para dispositivos RS232 legados.</span><span class="sxs-lookup"><span data-stu-id="8959a-107">The **DPUMP** class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="8959a-108">Gráfico de fluxo USB DPUMP:</span><span class="sxs-lookup"><span data-stu-id="8959a-108">USB DPUMP flow chart:</span></span>

![Gráfico de fluxo USB DPUMP](./media/usbx-device-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="8959a-110">Classe de dispositivo USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="8959a-110">USBX DPUMP Device Class</span></span>

<span data-ttu-id="8959a-111">A classe **DPUMP** do dispositivo utiliza um fio, que é iniciado na ligação ao hospedeiro USB.</span><span class="sxs-lookup"><span data-stu-id="8959a-111">The device **DPUMP** class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="8959a-112">O fio aguarda um pacote vindo no ponto final do Bulk out.</span><span class="sxs-lookup"><span data-stu-id="8959a-112">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="8959a-113">Quando um pacote é recebido, copia o conteúdo para o tampão de ponto final em volume de descontos e regista uma transação neste ponto final, aguardando que o anfitrião emita um pedido para ler a partir deste ponto final.</span><span class="sxs-lookup"><span data-stu-id="8959a-113">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="8959a-114">Isto fornece um mecanismo de retorno entre o Bulk out e o Bulk Em pontos finais.</span><span class="sxs-lookup"><span data-stu-id="8959a-114">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
