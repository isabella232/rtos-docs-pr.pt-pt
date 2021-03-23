---
title: Capítulo 1 - Introdução ao Cliente PTP Azure RTOS NetX Duo
description: Este capítulo contém uma introdução ao Cliente PTP Azure RTOS NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825807"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="b97d2-103">Capítulo 1 - Introdução ao Cliente PTP Azure RTOS NetX Duo</span><span class="sxs-lookup"><span data-stu-id="b97d2-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="b97d2-104">O Azure RTOS NetX Duo PTP implementa a parte cliente do Protocolo de Tempo de Precisão (PTP) versão 2, IEEE 1588-2008.</span><span class="sxs-lookup"><span data-stu-id="b97d2-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="b97d2-105">É utilizado para sincronizar relógios entre MCUs na rede local comunicando-se uns aos outros através de pacotes multicast IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="b97d2-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="b97d2-106">Configuração do cliente NetX Duo PTP</span><span class="sxs-lookup"><span data-stu-id="b97d2-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="b97d2-107">Para funcionar corretamente, o pacote de clientes PTP requer que já tenha sido criada uma instância IP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="b97d2-108">Por padrão, o cliente PTP junta-se ao grupo multicast IPv4.</span><span class="sxs-lookup"><span data-stu-id="b97d2-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="b97d2-109">Para executar o cliente PTP numa rede IPv6, `NX_ENABLE_IPV6_MULTICAST` deve ser definido na construção da biblioteca NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="b97d2-110">Ao criar o cliente PTP, a aplicação deve fornecer uma função de retorno para lidar com os timetamps de pacotes de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="b97d2-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="b97d2-111">Para obter alta resolução, recomendamos aplicações para gerar timetamps usando um temporizador de alta resolução.</span><span class="sxs-lookup"><span data-stu-id="b97d2-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="b97d2-112">Para executar o PTP no simulador, é fornecida uma implementação baseada em `nx_ptp_client_soft_clock_callback` software.</span><span class="sxs-lookup"><span data-stu-id="b97d2-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="b97d2-113">O cliente PTP requer uma piscina de pacotes para transmitir mensagens PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="b97d2-114">O tamanho da carga útil do pacote de pacotes não deve ser `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE` inferior, que é 108 bytes para IPv4, e 128 bytes se o IPv6 estiver ativado.</span><span class="sxs-lookup"><span data-stu-id="b97d2-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="b97d2-115">Depois de criar o Cliente PTP, a aplicação pode iniciar o cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="b97d2-116">A sincronização é feita no fio do ajudante PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="b97d2-117">Uma função de retorno do evento pode ser especificada.</span><span class="sxs-lookup"><span data-stu-id="b97d2-117">An event callback function can be specified.</span></span> <span data-ttu-id="b97d2-118">Será invocado quando qualquer um dos seguintes eventos acontecer.</span><span class="sxs-lookup"><span data-stu-id="b97d2-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="b97d2-119">Um mestre é selecionado;</span><span class="sxs-lookup"><span data-stu-id="b97d2-119">A master is selected;</span></span> 
* <span data-ttu-id="b97d2-120">O tempo está calibrado.</span><span class="sxs-lookup"><span data-stu-id="b97d2-120">The time is calibrated.</span></span>
* <span data-ttu-id="b97d2-121">Um mestre de tempos fora.</span><span class="sxs-lookup"><span data-stu-id="b97d2-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="b97d2-122">Mensagens de clientes NetX Duo PTP</span><span class="sxs-lookup"><span data-stu-id="b97d2-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="b97d2-123">O cliente NetX Duo PTP implementa apenas o mecanismo de resposta ao pedido de atraso.</span><span class="sxs-lookup"><span data-stu-id="b97d2-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="b97d2-124">O cliente PTP abre duas portas UDP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="b97d2-125">*319* para mensagem **de evento** e *320* para mensagem **geral.**</span><span class="sxs-lookup"><span data-stu-id="b97d2-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="b97d2-126">Há cinco tipos de mensagem para este mecanismo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="b97d2-127">**Anuncie.**</span><span class="sxs-lookup"><span data-stu-id="b97d2-127">**Announce**.</span></span> <span data-ttu-id="b97d2-128">Esta é uma mensagem de evento.</span><span class="sxs-lookup"><span data-stu-id="b97d2-128">This is an event message.</span></span> <span data-ttu-id="b97d2-129">É usado para a seleção do relógio principal.</span><span class="sxs-lookup"><span data-stu-id="b97d2-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="b97d2-130">**Sincronizar.** Esta é uma mensagem de evento.</span><span class="sxs-lookup"><span data-stu-id="b97d2-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="b97d2-131">É usado para enviar o tempo de origem e calcular o atraso do caminho de mestre para cliente.</span><span class="sxs-lookup"><span data-stu-id="b97d2-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="b97d2-132">**Follow_Up.**</span><span class="sxs-lookup"><span data-stu-id="b97d2-132">**Follow_Up**.</span></span> <span data-ttu-id="b97d2-133">Esta é uma mensagem geral.</span><span class="sxs-lookup"><span data-stu-id="b97d2-133">This is a general message.</span></span> <span data-ttu-id="b97d2-134">É opcional e usado para corrigir o tempo de origem na mensagem Sync relacionada.</span><span class="sxs-lookup"><span data-stu-id="b97d2-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="b97d2-135">É enviado apenas quando a bit de dois passos na bandeira de Sync é definida.</span><span class="sxs-lookup"><span data-stu-id="b97d2-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="b97d2-136">**Delay_Req.**</span><span class="sxs-lookup"><span data-stu-id="b97d2-136">**Delay_Req**.</span></span> <span data-ttu-id="b97d2-137">Esta é uma mensagem de evento.</span><span class="sxs-lookup"><span data-stu-id="b97d2-137">This is an event message.</span></span> <span data-ttu-id="b97d2-138">É enviado do cliente PTP para calcular o atraso do caminho de cliente para mestre, ao receber Delay_Resp.</span><span class="sxs-lookup"><span data-stu-id="b97d2-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="b97d2-139">**Delay_Resp.**</span><span class="sxs-lookup"><span data-stu-id="b97d2-139">**Delay_Resp**.</span></span> <span data-ttu-id="b97d2-140">Esta é uma mensagem de evento.</span><span class="sxs-lookup"><span data-stu-id="b97d2-140">This is an event message.</span></span> <span data-ttu-id="b97d2-141">É enviado de mestre para cliente para calcular o atraso do caminho de cliente para mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="b97d2-142">*Note que o algoritmo do "melhor relógio principal" não é implementado. Apenas o primeiro relógio principal é aceite quando o cliente PTP está em estado de escuta.*</span><span class="sxs-lookup"><span data-stu-id="b97d2-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="b97d2-143">Chamada do relógio do cliente NetX Duo PTP</span><span class="sxs-lookup"><span data-stu-id="b97d2-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="b97d2-144">Para sincronizar o relógio do mestre, o cliente PTP precisa de um relógio local.</span><span class="sxs-lookup"><span data-stu-id="b97d2-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="b97d2-145">Uma função de retorno do relógio é passada para cliente PTP durante a criação.</span><span class="sxs-lookup"><span data-stu-id="b97d2-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="b97d2-146">O formato da rotina de chamada do relógio é definido abaixo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="b97d2-147">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="b97d2-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="b97d2-148">*client_ptr* aponta para o cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="b97d2-149">*a operação* especifica a operação de retorno, os valores válidos são definidos como indicado na lista abaixo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="b97d2-150">**NX_PTP_CLIENT_CLOCK_INIT** Inicialize o relógio.</span><span class="sxs-lookup"><span data-stu-id="b97d2-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="b97d2-151">**NX_PTP_CLIENT_CLOCK_SET** Definir a temperatura de corrente especificada por `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="b97d2-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="b97d2-152">**NX_PTP_CLIENT_CLOCK_GET** Devolva a hora atual para `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="b97d2-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="b97d2-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extraição de hora de `packet_ptr` . `time_ptr`</span><span class="sxs-lookup"><span data-stu-id="b97d2-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="b97d2-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Ajuste a corrente da hora de seqdós menos de *1* segundo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="b97d2-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque o `packet_ptr` que requer notificar o cliente PTP da marca de tempo quando é transmitido.</span><span class="sxs-lookup"><span data-stu-id="b97d2-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="b97d2-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Atualize o temporizador suave.</span><span class="sxs-lookup"><span data-stu-id="b97d2-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="b97d2-157">Pode ser ignorado pelo relógio de hardware.</span><span class="sxs-lookup"><span data-stu-id="b97d2-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="b97d2-158">*time_ptr* aponta para a hora.</span><span class="sxs-lookup"><span data-stu-id="b97d2-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="b97d2-159">*packet_ptr* aponta para o pacote.</span><span class="sxs-lookup"><span data-stu-id="b97d2-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="b97d2-160">*callback_data* aponta para dados de retorno opacos.</span><span class="sxs-lookup"><span data-stu-id="b97d2-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="b97d2-161">O NX_PTP_TIME tipo de dados é definido da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="b97d2-161">The NX_PTP_TIME data type is defined as follows.</span></span>
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

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="b97d2-162">Chamada de evento do cliente netx duo PTP</span><span class="sxs-lookup"><span data-stu-id="b97d2-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="b97d2-163">A função de retorno do evento pode ser configurada para notificar a aplicação do estado do cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="b97d2-164">O formato da rotina de chamada do evento é definido como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="b97d2-165">Os parâmetros de entrada são.</span><span class="sxs-lookup"><span data-stu-id="b97d2-165">The input parameters are.</span></span>
* <span data-ttu-id="b97d2-166">*client_ptr* aponta para o cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="b97d2-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="b97d2-167">*o evento* especifica o evento de retorno, os valores válidos são definidos como:</span><span class="sxs-lookup"><span data-stu-id="b97d2-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="b97d2-168">**NX_PTP_CLIENT_EVENT_MASTER** Um relógio principal é selecionado.</span><span class="sxs-lookup"><span data-stu-id="b97d2-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="b97d2-169">**NX_PTP_CLIENT_EVENT_SYNC** O cliente PTP está calibrado.</span><span class="sxs-lookup"><span data-stu-id="b97d2-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="b97d2-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** O relógio principal está no intervalo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="b97d2-171">*event_data* especifica os dados relacionados com o evento.</span><span class="sxs-lookup"><span data-stu-id="b97d2-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="b97d2-172">Quando o evento é **NX_PTP_CLIENT_EVENT_MASTER,** event_data aponta para `NX_PTP_CLIENT_MASTER` o exemplo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="b97d2-173">Quando o evento é **NX_PTP_CLIENT_EVENT_SYNC,** os dados do evento apontam para `NX_PTP_CLIENT_SYNC` o exemplo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="b97d2-174">Comunicação do Cliente NetX Duo PTP</span><span class="sxs-lookup"><span data-stu-id="b97d2-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="b97d2-175">Como mencionado anteriormente, o cliente NetX Duo PTP apenas suporta o mecanismo de resposta ao pedido de atraso.</span><span class="sxs-lookup"><span data-stu-id="b97d2-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="b97d2-176">Este mecanismo mede o atraso médio entre o cliente e o relógio principal como abaixo:</span><span class="sxs-lookup"><span data-stu-id="b97d2-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="b97d2-177">Cliente recebe *mensagem de anúncio* do mestre e seleciona-a como melhor mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="b97d2-178">O cliente recebe mensagem *Sync* do mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="b97d2-179">O tempotamp *t1* é o tempo de origem nesta mensagem.</span><span class="sxs-lookup"><span data-stu-id="b97d2-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="b97d2-180">O relógio *t2* é lido a partir do relógio local quando esta mensagem é recebida.</span><span class="sxs-lookup"><span data-stu-id="b97d2-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="b97d2-181">O cliente recebe *Follow_Up* mensagem do mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="b97d2-182">Esta mensagem é opcional e válida apenas quando dois passos na bandeira *de Sync* são definidos.</span><span class="sxs-lookup"><span data-stu-id="b97d2-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="b97d2-183">Em seguida, o tempotamp *t1* é atualizado para o tempo de origem da estada nesta mensagem.</span><span class="sxs-lookup"><span data-stu-id="b97d2-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="b97d2-184">O cliente envia *Delay_Req* mensagem ao mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="b97d2-185">O relógio *t3* é lido a partir do relógio local quando a mensagem é transmitida.</span><span class="sxs-lookup"><span data-stu-id="b97d2-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="b97d2-186">O cliente recebe *Delay_Resp* mensagem do mestre.</span><span class="sxs-lookup"><span data-stu-id="b97d2-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="b97d2-187">O tempotamp *t4* é o tempo de receção nesta mensagem.</span><span class="sxs-lookup"><span data-stu-id="b97d2-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="b97d2-188">O atraso médio do caminho é calculado como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="b97d2-189">A compensação do mestre é calculada como mostrado abaixo.</span><span class="sxs-lookup"><span data-stu-id="b97d2-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="b97d2-190">\*The \***correctionField** _ é ignorado durante o calculation._</span><span class="sxs-lookup"><span data-stu-id="b97d2-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>