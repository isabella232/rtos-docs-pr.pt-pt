---
title: Capítulo 1 - Introdução ao Cliente PTP Azure RTOS NetX Duo
description: Este capítulo contém uma introdução ao Cliente PTP Azure RTOS NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf7210529121c8e49ff3cabbb7c673288b803f24760096396f32f33d4a9fb7e6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798049"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a>Capítulo 1 - Introdução ao Cliente PTP Azure RTOS NetX Duo

O Azure RTOS NetX Duo PTP implementa a parte cliente do Protocolo de Tempo de Precisão (PTP) versão 2, IEEE 1588-2008. É utilizado para sincronizar relógios entre MCUs na rede local comunicando-se uns aos outros através de pacotes multicast IPv4 ou IPv6.

## <a name="netx-duo-ptp-client-setup"></a>Configuração do cliente NetX Duo PTP

Para funcionar corretamente, o pacote de clientes PTP requer que já tenha sido criada uma instância IP NetX Duo.

Por padrão, o cliente PTP junta-se ao grupo multicast IPv4. Para executar o cliente PTP numa rede IPv6, `NX_ENABLE_IPV6_MULTICAST` deve ser definido na construção da biblioteca NetX Duo.

Ao criar o cliente PTP, a aplicação deve fornecer uma função de retorno para lidar com os timetamps de pacotes de entrada e saída. Para obter alta resolução, recomendamos aplicações para gerar timetamps usando um temporizador de alta resolução. Para executar o PTP no simulador, é fornecida uma implementação baseada em `nx_ptp_client_soft_clock_callback` software.

O cliente PTP requer uma piscina de pacotes para transmitir mensagens PTP. O tamanho da carga útil do pacote de pacotes não deve ser `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` inferior, que é 108 bytes para IPv4, e 128 bytes se o IPv6 estiver ativado.

Depois de criar o Cliente PTP, a aplicação pode iniciar o cliente PTP. A sincronização é feita no fio do ajudante PTP. Uma função de retorno do evento pode ser especificada. Será invocado quando qualquer um dos seguintes eventos acontecer.
* Um mestre é selecionado; 
* O tempo está calibrado.
* Um mestre de tempos fora.

## <a name="netx-duo-ptp-client-messages"></a>Mensagens de clientes NetX Duo PTP

O cliente NetX Duo PTP implementa apenas o mecanismo de resposta ao pedido de atraso. O cliente PTP abre duas portas UDP. *319* para mensagem **de evento** e *320* para mensagem **geral.** Há cinco tipos de mensagem para este mecanismo.

* **Anuncie.** Esta é uma mensagem de evento. É usado para a seleção do relógio principal.
* **Sincronizar.** Esta é uma mensagem de evento. É usado para enviar o tempo de origem e calcular o atraso do caminho de mestre para cliente.
* **Follow_Up.** Esta é uma mensagem geral. É opcional e usado para corrigir o tempo de origem na mensagem Sync relacionada. É enviado apenas quando a bit de dois passos na bandeira de Sync é definida.
* **Delay_Req.** Esta é uma mensagem de evento. É enviado do cliente PTP para calcular o atraso do caminho de cliente para mestre, ao receber Delay_Resp.
* **Delay_Resp.** Esta é uma mensagem de evento. É enviado de mestre para cliente para calcular o atraso do caminho de cliente para mestre.

*Note que o algoritmo do "melhor relógio principal" não é implementado. Apenas o primeiro relógio principal é aceite quando o cliente PTP está em estado de escuta.*

## <a name="netx-duo-ptp-client-clock-callback"></a>Chamada do relógio do cliente NetX Duo PTP
Para sincronizar o relógio do mestre, o cliente PTP precisa de um relógio local. Uma função de retorno do relógio é passada para cliente PTP durante a criação. O formato da rotina de chamada do relógio é definido abaixo.
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
Os parâmetros de entrada são definidos da seguinte forma:
* *client_ptr* aponta para o cliente PTP.
* *a operação* especifica a operação de retorno, os valores válidos são definidos como indicado na lista abaixo.
  * **NX_PTP_CLIENT_CLOCK_INIT** Inicialize o relógio.
  * **NX_PTP_CLIENT_CLOCK_SET** Definir a temperatura de corrente especificada por `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Devolva a hora atual para `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extraição de hora de `packet_ptr` . `time_ptr`
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Ajuste a corrente da hora de seqdós menos de *1* segundo.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque o `packet_ptr` que requer notificar o cliente PTP da marca de tempo quando é transmitido.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Atualize o temporizador suave. Pode ser ignorado pelo relógio de hardware.
* *time_ptr* aponta para a hora.
* *packet_ptr* aponta para o pacote.
* *callback_data* aponta para dados de retorno opacos.

O NX_PTP_TIME tipo de dados é definido da seguinte forma.
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a>Chamada de evento do cliente netx duo PTP
A função de retorno do evento pode ser configurada para notificar a aplicação do estado do cliente PTP. O formato da rotina de chamada do evento é definido como mostrado abaixo.
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
Os parâmetros de entrada são.
* *client_ptr* aponta para o cliente PTP.
* *o evento* especifica o evento de retorno, os valores válidos são definidos como:
  * **NX_PTP_CLIENT_EVENT_MASTER** Um relógio principal é selecionado.
  * **NX_PTP_CLIENT_EVENT_SYNC** O cliente PTP está calibrado.
  * **NX_PTP_CLIENT_EVENT_TIMEOUT** O relógio principal está no intervalo.
* *event_data* especifica os dados relacionados com o evento. Quando o evento é **NX_PTP_CLIENT_EVENT_MASTER,** event_data aponta para `NX_PTP_CLIENT_MASTER` o exemplo. Quando o evento é **NX_PTP_CLIENT_EVENT_SYNC,** os dados do evento apontam para `NX_PTP_CLIENT_SYNC` o exemplo.

## <a name="netx-duo-ptp-client-communication"></a>Comunicação do Cliente NetX Duo PTP
Como mencionado anteriormente, o cliente NetX Duo PTP apenas suporta o mecanismo de resposta ao pedido de atraso. Este mecanismo mede o atraso médio entre o cliente e o relógio principal como abaixo:
1. Cliente recebe *mensagem de anúncio* do mestre e seleciona-a como melhor mestre.
1. O cliente recebe mensagem *Sync* do mestre. O tempotamp *t1* é o tempo de origem nesta mensagem. O relógio *t2* é lido a partir do relógio local quando esta mensagem é recebida.
1. O cliente recebe *Follow_Up* mensagem do mestre. Esta mensagem é opcional e válida apenas quando dois passos na bandeira *de Sync* são definidos. Em seguida, o tempotamp *t1* é atualizado para o tempo de origem da estada nesta mensagem.
1. O cliente envia *Delay_Req* mensagem ao mestre. O relógio *t3* é lido a partir do relógio local quando a mensagem é transmitida.
1. O cliente recebe *Delay_Resp* mensagem do mestre. O tempotamp *t4* é o tempo de receção nesta mensagem.

O atraso médio do caminho é calculado como mostrado abaixo.
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
A compensação do mestre é calculada como mostrado abaixo.
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> *The ***correctionField** _ é ignorado durante o calculation._