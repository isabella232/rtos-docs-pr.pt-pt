---
title: Capítulo 10 - Eventos de utilizador de clientes
description: Este capítulo contém uma descrição de como criar eventos definidos pelo utilizador e ícones personalizados e campos de informação para tais eventos.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827607"
---
# <a name="chapter-10---customer-user-events"></a><span data-ttu-id="b6b01-103">Capítulo 10 - Eventos de utilizador de clientes</span><span class="sxs-lookup"><span data-stu-id="b6b01-103">Chapter 10 - Customer user events</span></span>

<span data-ttu-id="b6b01-104">Este capítulo contém uma descrição de como criar eventos definidos pelo utilizador e ícones personalizados e campos de informação para tais eventos.</span><span class="sxs-lookup"><span data-stu-id="b6b01-104">This chapter contains a description of how to create user-defined events and custom icons and information fields for such events.</span></span> <span data-ttu-id="b6b01-105">Este capítulo inclui as seguintes secções:</span><span class="sxs-lookup"><span data-stu-id="b6b01-105">This chapter includes the following sections:</span></span> 

## <a name="inserting-user-defined-events"></a><span data-ttu-id="b6b01-106">Inserir eventos User-Defined</span><span class="sxs-lookup"><span data-stu-id="b6b01-106">Inserting User-Defined Events</span></span>

<span data-ttu-id="b6b01-107">A ThreadX fornece a capacidade para os desenvolvedores registarem os seus próprios eventos definidos pelo utilizador, fornecendo informações ainda mais úteis que podem ser visualizadas graficamente pela TraceX.</span><span class="sxs-lookup"><span data-stu-id="b6b01-107">ThreadX provides the ability for developers to log their own user-defined events, providing even more useful information that can be viewed graphically by TraceX.</span></span> <span data-ttu-id="b6b01-108">Os números de eventos definidos pelo utilizador variam de</span><span class="sxs-lookup"><span data-stu-id="b6b01-108">User-defined event numbers range from</span></span>

<span data-ttu-id="b6b01-109">**TX_TRACE_USER_EVENT_START** (4096) até **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span><span class="sxs-lookup"><span data-stu-id="b6b01-109">**TX_TRACE_USER_EVENT_START** (4096) through **TX_TRACE_USER_EVENT_END** (65535), inclusive.</span></span> <span data-ttu-id="b6b01-110">A colocação dos eventos no tampão de vestígios é feita através do ***tx_trace_user_event_insert,*** definido no Capítulo 5.</span><span class="sxs-lookup"><span data-stu-id="b6b01-110">The placement of the events in the trace buffer is done via the ***tx_trace_user_event_insert***, defined in Chapter 5.</span></span> <span data-ttu-id="b6b01-111">As chamadas de exemplo a seguir inserem dois eventos definidos pelo utilizador no atual tampão de rastreio no alvo, nomeadamente o evento 4096 definido pelo utilizador e o evento 4098:</span><span class="sxs-lookup"><span data-stu-id="b6b01-111">The following example calls insert two user-defined events into the current trace buffer on the target, namely user-defined event 4096 and event 4098:</span></span>

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a><span data-ttu-id="b6b01-112">Exibição padrão de eventos de User-Defined</span><span class="sxs-lookup"><span data-stu-id="b6b01-112">Default Display of User-Defined Events</span></span>

![Ícone de evento definido pelo utilizador](./media/user-guide/tx-events/image0.png)

<span data-ttu-id="b6b01-114">Por predefinição, o TraceX exibe todos os eventos do utilizador com um ícone de Evento definido pelo utilizador padrão, tal como descrito no Capítulo 6.</span><span class="sxs-lookup"><span data-stu-id="b6b01-114">By default, TraceX displays all user events with a default user-defined Event icon as described in Chapter 6.</span></span> <span data-ttu-id="b6b01-115">A figura 28 mostra o ícone de evento definido pelo utilizador padrão para os eventos 452 e 453, que foram colocados no tampão do evento através dos exemplos ***tx_trace_user_event_insert*** anteriores.</span><span class="sxs-lookup"><span data-stu-id="b6b01-115">Figure 28 shows the default user-defined event icon for events 452 and 453, which were placed in the event buffer via the previous ***tx_trace_user_event_insert*** examples.</span></span>

<span data-ttu-id="b6b01-116">![Screenshot do display padrão de eventos definidos pelo utilizador. ](./media/user-guide/10.1.png)
 **FIGURA 28**</span><span class="sxs-lookup"><span data-stu-id="b6b01-116">![Screenshot of the default display of user-defined events.](./media/user-guide/10.1.png)
**FIGURE 28**</span></span>

<span data-ttu-id="b6b01-117">Informações detalhadas também estão disponíveis para eventos definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="b6b01-117">Detailed information is also available for user-defined Events.</span></span> <span data-ttu-id="b6b01-118">A figura 28 mostra as informações detalhadas do evento 452, que tem o número do evento 4096 e mostra os quatro campos de informação especificados.</span><span class="sxs-lookup"><span data-stu-id="b6b01-118">Figure 28 shows the detailed event information for event 452, which has event number 4096 and shows the specified four information fields.</span></span>

<span data-ttu-id="b6b01-119">![Screenshot da exibição detalhada de eventos definidos pelo utilizador. ](./media/user-guide/10.2.png)
 **FIGURA 29**</span><span class="sxs-lookup"><span data-stu-id="b6b01-119">![Screenshot of the detailed display of user-defined events.](./media/user-guide/10.2.png)
**FIGURE 29**</span></span>

## <a name="defining-custom-user-defined-event-icons"></a><span data-ttu-id="b6b01-120">Definindo ícones de eventos de User-Defined personalizados</span><span class="sxs-lookup"><span data-stu-id="b6b01-120">Defining Custom User-Defined Event Icons</span></span>

<span data-ttu-id="b6b01-121">O TraceX também fornece ao utilizador a capacidade de criar ícones de eventos personalizados definidos pelo utilizador e etiquetas de campo de informação personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b6b01-121">TraceX also provides the user the ability to create custom user-defined event icons and custom information field labels.</span></span> <span data-ttu-id="b6b01-122">Esta capacidade é conseguida adicionando especificações de ícones de evento ao ficheiro de configuração \***tracex_custom.trxc** _ .</span><span class="sxs-lookup"><span data-stu-id="b6b01-122">This capability is achieved by adding event icon specifications to the \***tracex_custom.trxc** _ configuration file.</span></span> <span data-ttu-id="b6b01-123">Este ficheiro está localizado no subdiretório _ *_CustomEvents_*\* do seu diretório de instalação TraceX definido pelo utilizador, que predefine c:\Azure_RTOS\TraceX.</span><span class="sxs-lookup"><span data-stu-id="b6b01-123">This file is located in the _ *_CustomEvents_*\* subdirectory of your user-defined TraceX installation directory, which defaults to c:\Azure_RTOS\TraceX.</span></span> <span data-ttu-id="b6b01-124">Um caminho de diretório de exemplo é mostrado na Figura 30.</span><span class="sxs-lookup"><span data-stu-id="b6b01-124">An example directory path is shown in Figure 30.</span></span>

<span data-ttu-id="b6b01-125">![Screenshot de um caminho de diretório de exemplo. ](./media/user-guide/custom_events_folder.png)
 **FIGURA 30**</span><span class="sxs-lookup"><span data-stu-id="b6b01-125">![Screenshot of an example directory path.](./media/user-guide/custom_events_folder.png)
**FIGURE 30**</span></span>

<span data-ttu-id="b6b01-126">O ficheiro de configuração de evento personalizado ***tracex_custom.trxc*** é um simples ficheiro de texto ASCII que contém definições de eventos zero ou mais personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b6b01-126">The ***tracex_custom.trxc*** custom event configuration file is a simple ASCII text file containing zero or more custom event definitions.</span></span> <span data-ttu-id="b6b01-127">O formato do ficheiro é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6b01-127">The format of the file is as follows:</span></span>

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

<span data-ttu-id="b6b01-128">Cada linha entre Início e Fim é usada para definir um único evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="b6b01-128">Each line between Start and End is used to define a single custom event.</span></span> <span data-ttu-id="b6b01-129">A TraceX fornece uma versão de modelo deste ficheiro sem eventos personalizados definidos (nada entre as etiquetas "Iniciar" e "Fim").</span><span class="sxs-lookup"><span data-stu-id="b6b01-129">TraceX provides a template version of this file with no custom events defined (nothing between the "Start" and "End" labels).</span></span> <span data-ttu-id="b6b01-130">O formato de uma definição de evento personalizado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b6b01-130">The format of a custom event definition is as follows:</span></span>

<span data-ttu-id="b6b01-131">**número, nome, abreviatura, top_color, bottom_color, label1, label2, label2, label2, label4**</span><span class="sxs-lookup"><span data-stu-id="b6b01-131">**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**</span></span>

<span data-ttu-id="b6b01-132">em que:</span><span class="sxs-lookup"><span data-stu-id="b6b01-132">where:</span></span>

- <span data-ttu-id="b6b01-133">número: Define o número de evento definido pelo utilizador, entre 4096 e 65535, inclusive.</span><span class="sxs-lookup"><span data-stu-id="b6b01-133">number: Defines the user-defined event number, between 4096 and 65535, inclusive.</span></span></th>
- <span data-ttu-id="b6b01-134">nome: Define o nome lógico para o evento definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="b6b01-134">name: Defines the logical name for the user-defined event.</span></span></td>
- <span data-ttu-id="b6b01-135">abreviatura: Define a abreviatura do evento definido pelo utilizador de duas letras.</span><span class="sxs-lookup"><span data-stu-id="b6b01-135">abbreviation: Defines the two-letter user-defined event abbreviation.</span></span></td>
- <span data-ttu-id="b6b01-136">top_color: Define o valor RGB para a metade superior do ícone, que é um número de três dígitos em parênteses.</span><span class="sxs-lookup"><span data-stu-id="b6b01-136">top_color: Defines the RGB value for the top-half of the icon, which is a three-digit number in parenthesis.</span></span> <span data-ttu-id="b6b01-137">Algumas definições típicas de RGB são</span><span class="sxs-lookup"><span data-stu-id="b6b01-137">Some typical RGB definitions are</span></span>
  - <span data-ttu-id="b6b01-138">PRETO = (0,0,0)</span><span class="sxs-lookup"><span data-stu-id="b6b01-138">BLACK = (0,0,0)</span></span>       
  - <span data-ttu-id="b6b01-139">BRANCO = (255.255.255)</span><span class="sxs-lookup"><span data-stu-id="b6b01-139">WHITE = (255,255,255)</span></span>
  - <span data-ttu-id="b6b01-140">VERMELHO = (255,0,0)</span><span class="sxs-lookup"><span data-stu-id="b6b01-140">RED = (255,0,0)</span></span>     
  - <span data-ttu-id="b6b01-141">VERDE = (0.255,0)</span><span class="sxs-lookup"><span data-stu-id="b6b01-141">GREEN = (0,255,0)</span></span>     
  - <span data-ttu-id="b6b01-142">AZUL = (0,0,255)</span><span class="sxs-lookup"><span data-stu-id="b6b01-142">BLUE = (0,0,255)</span></span>     
  - <span data-ttu-id="b6b01-143">AMARELO = (255.255,0)</span><span class="sxs-lookup"><span data-stu-id="b6b01-143">YELLOW = (255,255,0)</span></span>   
  - <span data-ttu-id="b6b01-144">CYAN = (0.255.255)</span><span class="sxs-lookup"><span data-stu-id="b6b01-144">CYAN = (0,255,255)</span></span>   
  - <span data-ttu-id="b6b01-145">MAGENTA = (255.0,255)</span><span class="sxs-lookup"><span data-stu-id="b6b01-145">MAGENTA = (255,0,255)</span></span>   
  <span data-ttu-id="b6b01-146">A utilização da especificação RBG dá ao utilizador uma ampla gama de cores para cada ícone definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="b6b01-146">Using the RBG specification gives the user a broad range of colors for each user-defined icon.</span></span> <span data-ttu-id="b6b01-147">Para obter mais informações sobre a definição de cores RBG, consulte: https://en.wikipedia.org/wiki/RGB#Digital_representations</span><span class="sxs-lookup"><span data-stu-id="b6b01-147">For more information on RBG color definition, see: https://en.wikipedia.org/wiki/RGB#Digital_representations</span></span>
- <span data-ttu-id="b6b01-148">botton_color: Define o valor RGB para a metade inferior do ícone, que é um número de três dígitos em parênteses.</span><span class="sxs-lookup"><span data-stu-id="b6b01-148">botton_color: Defines the RGB value for the bottom half of the icon, which is a three-digit number in parenthesis.</span></span>
- <span data-ttu-id="b6b01-149">label1: Label for ***info_field_1** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .</span><span class="sxs-lookup"><span data-stu-id="b6b01-149">label1: Label for ***info_field_1** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b6b01-150">label2: Label for ***info_field_2** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .</span><span class="sxs-lookup"><span data-stu-id="b6b01-150">label2: Label for ***info_field_2** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b6b01-151">label3: Label for ***info_field_3** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .</span><span class="sxs-lookup"><span data-stu-id="b6b01-151">label3: Label for ***info_field_3** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>
- <span data-ttu-id="b6b01-152">label4: Label for ***info_field_4** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .</span><span class="sxs-lookup"><span data-stu-id="b6b01-152">label4: Label for ***info_field_4** _, as specified in the _ *_tx_trace_user_event_insert_** call.</span></span>

<span data-ttu-id="b6b01-153">As definições de exemplo para cada um dos dois eventos definidos pelo utilizador utilizados neste capítulo são apresentadas na Figura 10.4.</span><span class="sxs-lookup"><span data-stu-id="b6b01-153">Example definitions for each of the two user-defined events used in this chapter are shown in Figure 10.4.</span></span> <span data-ttu-id="b6b01-154">A primeira definição é para o evento 4096 na linha 5 do ficheiro \***tracex_custom.trxc** _ .</span><span class="sxs-lookup"><span data-stu-id="b6b01-154">The first definition is for event 4096 at line 5 of the \***tracex_custom.trxc** _ file.</span></span> <span data-ttu-id="b6b01-155">Esta definição dá ao evento definido pelo utilizador 4096 o nome _\*First_User_Event\*\*\*, especifica uma abreviatura de duas letras de **FE,** torna a parte superior do ícone vermelha, a parte inferior do ícone verde, e designa os campos de informação como **First_Info1**, **First_Info2**, **First_Info3** e **First_Info4**.</span><span class="sxs-lookup"><span data-stu-id="b6b01-155">This definition gives user-defined event 4096 the name _\*First_User_Event\*\*, specifies a two-letter abbreviation of **FE**, makes the top portion of the icon red, the bottom portion of the icon green, and names the information fields as **First_Info1**, **First_Info2**, **First_Info3**, and **First_Info4**.</span></span> <span data-ttu-id="b6b01-156">O evento 4098 definido pelo utilizador é definido da mesma forma na linha 6 de **_tracex_custom.trxc_**.</span><span class="sxs-lookup"><span data-stu-id="b6b01-156">User-defined event 4098 is defined similarly at line 6 of **_tracex_custom.trxc_**.</span></span>

<span data-ttu-id="b6b01-157">![Screenshot das definições de exemplo para os eventos definidos pelo utilizador. ](./media/user-guide/10.4.png)
 **FIGURA 31**</span><span class="sxs-lookup"><span data-stu-id="b6b01-157">![Screenshot of the example definitions for the user-defined events.](./media/user-guide/10.4.png)
**FIGURE 31**</span></span>

<span data-ttu-id="b6b01-158">Uma vez que o ficheiro \***tracex_custom.trxc** _ é lido pela TraceX durante a inicialização, o TraceX deve ser saído e reiniciado antes que as definições de ícones personalizados possam produzir efeitos.</span><span class="sxs-lookup"><span data-stu-id="b6b01-158">Since the \***tracex_custom.trxc** _ file is read by TraceX during initialization, TraceX must be exited and restarted before the custom icon definitions can take effect.</span></span> <span data-ttu-id="b6b01-159">A figura 32 mostra o ecrã TraceX dos eventos definidos pelo utilizador 452 e 453 com os ícones de eventos personalizados definidos em _\*_tracex_custom.trxc_\*\*.</span><span class="sxs-lookup"><span data-stu-id="b6b01-159">Figure 32 shows the TraceX display of user-defined events 452 and 453 with the custom event icons defined in _\*_tracex_custom.trxc_\*\*.</span></span>

<span data-ttu-id="b6b01-160">![Screenshot da exibição TraceX de eventos definidos pelo utilizador com os ícones de evento personalizados. ](./media/user-guide/10.5.png)
 **FIGURA 32**</span><span class="sxs-lookup"><span data-stu-id="b6b01-160">![Screenshot of the TraceX display of user defined events with the custom event icons.](./media/user-guide/10.5.png)
**FIGURE 32**</span></span>

<span data-ttu-id="b6b01-161">As informações adicionais na definição de evento personalizado são mostradas quando o evento que seleciona usando um duplo clique, rat-over ou clicando no botão de evento atual.</span><span class="sxs-lookup"><span data-stu-id="b6b01-161">The additional information in the custom event definition is shown when the event you select using a double-click, mouse-over, or clicking the current event button.</span></span> <span data-ttu-id="b6b01-162">A figura 33 mostra a seleção de dois cliques no evento 452.</span><span class="sxs-lookup"><span data-stu-id="b6b01-162">Figure 33 shows the double-click selection on event 452.</span></span> <span data-ttu-id="b6b01-163">O nome do evento e os campos de informação correspondem à definição de amostra que foi adicionada a ***tracex_custom.trxc***.</span><span class="sxs-lookup"><span data-stu-id="b6b01-163">The event name and information fields all match the sample definition that was added to ***tracex_custom.trxc***.</span></span>

<span data-ttu-id="b6b01-164">![Screenshot da seleção de dois cliques em um evento. ](./media/user-guide/10.6.png)
 **FIGURA 33**</span><span class="sxs-lookup"><span data-stu-id="b6b01-164">![Screenshot of the double-click selection on an event.](./media/user-guide/10.6.png)
**FIGURE 33**</span></span>
