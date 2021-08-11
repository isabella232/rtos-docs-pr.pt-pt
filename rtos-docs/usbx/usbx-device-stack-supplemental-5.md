---
title: Capítulo 5 - USBX OTG
description: Saiba como o USBX suporta as funcionalidades OTG do USB quando um controlador USB compatível com OTG estiver disponível no design de hardware.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0abe355f05492edb74635db2aa6607abbcf9de6b2693290b06b740d2b9286d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791062"
---
# <a name="chapter-5---usbx-otg"></a>Capítulo 5 - USBX OTG

O USBX suporta as funcionalidades OTG de USB quando um controlador USB compatível com OTG está disponível no design de hardware.

USBX suporta OTG na pilha USB do núcleo. Mas para que o OTG funcione, requer um controlador USB específico. As funções do controlador USBX OTG podem ser encontradas no diretório usbx_otg. A versão USBX atual suporta apenas o NXP LPC3131 com todas as capacidades OTG.

As funções regulares do controlador do controlador (anfitrião ou dispositivo) ainda podem ser encontradas na usbx_device_controllers USBX padrão e usbx_host_controllers mas o diretório usbx_otg contém as funções OTG específicas associadas ao controlador USB.

Existem quatro categorias de funções para um controlador OTG, além das funções habituais de hospedeiro/dispositivo.

- Funções específicas do VBUS
- Início e paragem do controlador
- Gestor de funções USB
- Interromper manipuladores

## <a name="vbus-functions"></a>Funções VBUS

Cada controlador precisa de ter um gestor VBUS para alterar o estado da VBUS com base nos requisitos de gestão de energia. Normalmente, esta função só funciona ligando ou desligando O VBUS.

## <a name="start-and-stop-the-controller"></a>Iniciar e parar o controlador

Ao contrário de uma implementação USB regular, o OTG requer que o hospedeiro e/ou a pilha do dispositivo sejam ativados e desativados quando a função muda.

## <a name="usb-role-manager"></a>Gestor de funções USB

O gestor de funções USB recebe comandos para alterar o estado do USB. Há vários Estados que precisam de transições de e para:

| Estado                    | Valor | Descrição                                           |
| ------------------------ | ----- | ----------------------------------------------------- |
| UX_OTG_IDLE            | 0     | O dispositivo está inativo. Não está ligado a nada. |
| UX_OTG_IDLE_TO_HOST  | 1     | O dispositivo está ligado ao conector do tipo A             |
| UX_OTG_IDLE_TO_SLAVE | 2     | O dispositivo está ligado ao conector do tipo B             |
| UX_OTG_HOST_TO_IDLE  | 3     | Dispositivo de anfitrião foi desligado                          |
| UX_OTG_HOST_TO_SLAVE | 4     | Troca de papéis de Hospedeiro para Escravo                          |
| UX_OTG_SLAVE_TO_IDLE | 5     | O dispositivo escravo está desligado                          |
| UX_OTG_SLAVE_TO_HOST | 6     | Troca de papéis de Slave para Host                          |

## <a name="interrupt-handlers"></a>Interromper manipuladores

Tanto os controladores de hospedeiro como os controladores de dispositivos para o OTG precisam de diferentes manipuladores de interrupção para monitorizar os sinais para além das tradicionais interrupções USB, em particular os sinais devido ao SRP e vbus.

Como inicializar um controlador USB OTG. Utilizamos o NXP LPC3131 como exemplo aqui.

```C
/* Initialize the LPC3131 OTG controller. */
status = ux_otg_lpc3131_initialize(0x19000000, lpc3131_vbus_function,
    tx_demo_change_mode_callback);
```

Neste exemplo, inicializamos o LPC3131 no modo OTG, passando uma função VBUS e uma chamada de mudança de modo (de hospedeiro a escravo ou vice-versa).

A função de retorno deve simplesmente gravar o novo modo e acordar um fio pendente para agir o estado novo.

```C
void tx_demo_change_mode_callback(ULONG mode) {
    /* Simply save the otg mode. */
    otg_mode = mode;

    /* Wake up the thread that is waiting. */
    ux_utility_semaphore_put(&mode_change_semaphore);
}
```

O valor do modo que é passado pode ter os seguintes valores.

- **UX_OTG_MODE_IDLE**
- **UX_OTG_MODE_SLAVE**
- **UX_OTG_MODE_HOST**

A aplicação pode sempre verificar o que é o dispositivo olhando para a variável:

```C
_ux_system_otg -> ux_system_otg_device_type
```

Os seus valores podem ser qualquer um dos seguintes.

- **UX_OTG_DEVICE_A**
- **UX_OTG_DEVICE_B**
- **UX_OTG_DEVICE_IDLE**

Um dispositivo de anfitrião USB OTG pode sempre pedir uma troca de funções emitindo o seguinte comando.

```C
/* Ask the stack to perform a HNP swap with the device. We relinquish the host role to A device. */
ux_host_stack_role_swap(storage -> ux_host_class_storage_device);
```

Para um dispositivo escravo, não há nenhuma ordem a emitir, mas o dispositivo escravo pode definir um estado para mudar o papel, que será recolhido pelo hospedeiro quando emitir um **GET_STATUS** e a troca será iniciada.

```C
/* We are a B device, ask for role swap.
   The next GET_STATUS from the host will get the status change and do the HNP. */
_ux_system_otg -> ux_system_otg_slave_role_swap_flag =
    UX_OTG_HOST_REQUEST_FLAG;
```
