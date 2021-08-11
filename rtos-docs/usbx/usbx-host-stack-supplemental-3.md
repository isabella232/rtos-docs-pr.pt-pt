---
title: Considerações da classe USBX DPUMP
description: USBX contém uma classe DPUMP para o lado do hospedeiro e dispositivo.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 72aa9c1e2200049bf81d64543b690edd001c4ecf9c2cdeb4c3bea5f1b03aa5b8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802583"
---
# <a name="chapter-3-usbx-dpump-class-considerations"></a>Capítulo 3: Considerações da classe USBX DPUMP

USBX contém uma classe DPUMP para o lado do hospedeiro e dispositivo. Esta classe não é uma classe padrão em si, mas sim um exemplo que ilustra como criar um dispositivo simples usando dois tubos a granel e enviando dados para trás e para a frente nestes dois tubos. A classe DPUMP pode ser usada para iniciar uma classe personalizada ou para dispositivos RS232 legados.

Gráfico de fluxo USB DPUMP:

![Gráfico de fluxo USB DPUMP](./media/usbx-host-stack-supplemental/usb-dpump-flow-chart.png)

## <a name="usbx-dpump-host-class"></a>Classe de anfitrião USBX DPUMP

O lado anfitrião da Classe DPUMP tem duas funções, uma para envio de dados e outra para receber dados:

- `ux_host_class_dpump_write`
- `ux_host_class_dpump_read`

Ambas as funções estão a bloquear para facilitar a aplicação DPUMP. Se for necessário ter ambos os tubos (IN e OUT) a funcionar ao mesmo tempo, a aplicação será necessária para criar um fio de transmissão e um fio de receção.

O protótipo para a função de escrita é o seguinte.

```C
UINT ux_host_class_dpump_write(UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,  
    ULONG *actual_length)
```

Em que:

- dpump é o exemplo da classe
- data_pointer é o ponteiro para o tampão a ser enviado
- requested_length é o comprimento para enviar
- atual_length é o comprimento enviado após a conclusão da transferência, com sucesso ou parcialmente.

O protótipo para a função recetora é semelhante.

```C
UINT ux_host_class_dpump_read(
    UX_HOST_CLASS_DPUMP *dpump,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

Aqui está um exemplo da classe DPUMP hospedeira onde uma aplicação escreve um pacote para o lado do dispositivo e recebe o mesmo pacote na receção:

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

## <a name="usbx-dpump-device-class"></a>Classe de dispositivo USBX DPUMP

A classe DPUMP do dispositivo utiliza um fio, que é iniciado na ligação ao hospedeiro USB. O fio aguarda um pacote vindo no ponto final do Bulk out. Quando um pacote é recebido, copia o conteúdo para o tampão de ponto final em volume de descontos e regista uma transação neste ponto final, aguardando que o anfitrião emita um pedido para ler a partir deste ponto final. Isto fornece um mecanismo de retorno entre o Bulk out e o Bulk Em pontos finais.
