---
title: Considerações da classe USBX DPUMP
description: USBX contém uma classe DPUMP para o lado do hospedeiro e dispositivo.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9960b391418fa2f9203e761115bcba71cc3619e8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828075"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a><span data-ttu-id="cfc1e-103">Capítulo 3: Considerações da classe USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="cfc1e-103">Chapter 3: USBX DPUMP Class Considerations</span></span>

<span data-ttu-id="cfc1e-104">USBX contém uma classe DPUMP para o lado do hospedeiro e dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-104">USBX contains a DPUMP class for the host and device side.</span></span> <span data-ttu-id="cfc1e-105">Esta classe não é uma classe padrão em si, mas sim um exemplo que ilustra como criar um dispositivo simples usando dois tubos a granel e enviando dados para trás e para a frente nestes dois tubos.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-105">This class is not a standard class in itself, but rather an example that illustrates how to create a simple device by using two bulk pipes and sending data back and forth on these two pipes.</span></span> <span data-ttu-id="cfc1e-106">A classe DPUMP pode ser usada para iniciar uma classe personalizada ou para dispositivos RS232 legados.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-106">The DPUMP class could be used to start a custom class or for legacy RS232 devices.</span></span>

<span data-ttu-id="cfc1e-107">Gráfico de fluxo USB DPUMP:</span><span class="sxs-lookup"><span data-stu-id="cfc1e-107">USB DPUMP flow chart:</span></span>

![Gráfico de fluxo USB DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a><span data-ttu-id="cfc1e-109">Classe de anfitrião USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="cfc1e-109">USBX DPUMP Host Class</span></span>

<span data-ttu-id="cfc1e-110">O lado anfitrião da Classe DPUMP tem duas funções, uma para envio de dados e outra para receber dados:</span><span class="sxs-lookup"><span data-stu-id="cfc1e-110">The host side of the DPUMP Class has two functions, one for sending data and one for receiving data:</span></span>

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

<span data-ttu-id="cfc1e-111">Ambas as funções estão a bloquear para facilitar a aplicação DPUMP.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-111">Both functions are blocking to make the DPUMP application easier.</span></span> <span data-ttu-id="cfc1e-112">Se for necessário ter ambos os tubos (IN e OUT) a funcionar ao mesmo tempo, a aplicação será necessária para criar um fio de transmissão e um fio de receção.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-112">If it is necessary to have both pipes (IN and OUT) running at the same time, the application will be required to create a transmit thread and a receive thread.</span></span>

<span data-ttu-id="cfc1e-113">O protótipo para a função de escrita é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-113">The prototype for the writing function is as follows.</span></span>

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

<span data-ttu-id="cfc1e-114">Em que:</span><span class="sxs-lookup"><span data-stu-id="cfc1e-114">Where:</span></span>

- <span data-ttu-id="cfc1e-115">dpump é o exemplo da classe</span><span class="sxs-lookup"><span data-stu-id="cfc1e-115">dpump is the instance of the class</span></span>
- <span data-ttu-id="cfc1e-116">data_pointer é o ponteiro para o tampão a ser enviado</span><span class="sxs-lookup"><span data-stu-id="cfc1e-116">data_pointer is the pointer to the buffer to be sent</span></span>
- <span data-ttu-id="cfc1e-117">requested_length é o comprimento para enviar</span><span class="sxs-lookup"><span data-stu-id="cfc1e-117">requested_length is the length to send</span></span>
- <span data-ttu-id="cfc1e-118">atual_length é o comprimento enviado após a conclusão da transferência, com sucesso ou parcialmente.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-118">actual_length is the length sent after completion of the transfer, either successfully or partially.</span></span>

<span data-ttu-id="cfc1e-119">O protótipo para a função recetora é semelhante.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-119">The prototype for the receiving function is similar.</span></span>

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

<span data-ttu-id="cfc1e-120">Aqui está um exemplo da classe DPUMP hospedeira onde uma aplicação escreve um pacote para o lado do dispositivo e recebe o mesmo pacote na receção:</span><span class="sxs-lookup"><span data-stu-id="cfc1e-120">Here is an example of the host DPUMP class where an application writes a packet to the device side and receives the same packet on the reception:</span></span>

```C
/* We start with a 'A' in buffer. */
current_char = 'A';

while(1)
{
    /* Initialize the write buffer. */
    ux_utility_memory_set(out_buffer, current_char,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE);

    /* Increment the character in buffer. */
    current_char++;

    /* Check for upper alphabet limit. */
    if (current_char > 'Z')
        current_char = 'A';

    /* Write to the Data Pump Bulk out endpoint. */
    status = ux_host_class_dpump_write (dpump, out_buffer,
        UX_HOST_CLASS_DPUMP_PACKET_SIZE,
        &actual_length);

    /* Verify that the status and the amount of data is correct. */
    if ((status == UX_SUCCESS) && actual_length == UX_HOST_CLASS_DPUMP_PACKET_SIZE)
    {
        /* Read to the Data Pump Bulk out endpoint. */
        status = ux_host_class_dpump_read (dpump, in_buffer,
            UX_HOST_CLASS_DPUMP_PACKET_SIZE, &actual_length);
    }
}
```

## <a name="usbx-dpump-device-class"></a><span data-ttu-id="cfc1e-121">Classe de dispositivo USBX DPUMP</span><span class="sxs-lookup"><span data-stu-id="cfc1e-121">USBX DPUMP Device Class</span></span>

<span data-ttu-id="cfc1e-122">A classe DPUMP do dispositivo utiliza um fio, que é iniciado na ligação ao hospedeiro USB.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-122">The device DPUMP class uses a thread, which is started upon connection to the USB host.</span></span> <span data-ttu-id="cfc1e-123">O fio aguarda um pacote vindo no ponto final do Bulk out.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-123">The thread waits for a packet coming on the Bulk Out endpoint.</span></span> <span data-ttu-id="cfc1e-124">Quando um pacote é recebido, copia o conteúdo para o tampão de ponto final em volume de descontos e regista uma transação neste ponto final, aguardando que o anfitrião emita um pedido para ler a partir deste ponto final.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-124">When a packet is received, it copies the content to the Bulk In endpoint buffer and posts a transaction on this endpoint, waiting for the host to issue a request to read from this endpoint.</span></span> <span data-ttu-id="cfc1e-125">Isto fornece um mecanismo de retorno entre o Bulk out e o Bulk Em pontos finais.</span><span class="sxs-lookup"><span data-stu-id="cfc1e-125">This provides a loopback mechanism between the Bulk Out and Bulk In endpoints.</span></span>
