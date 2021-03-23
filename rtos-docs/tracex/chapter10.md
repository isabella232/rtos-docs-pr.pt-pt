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
# <a name="chapter-10---customer-user-events"></a>Capítulo 10 - Eventos de utilizador de clientes

Este capítulo contém uma descrição de como criar eventos definidos pelo utilizador e ícones personalizados e campos de informação para tais eventos. Este capítulo inclui as seguintes secções: 

## <a name="inserting-user-defined-events"></a>Inserir eventos User-Defined

A ThreadX fornece a capacidade para os desenvolvedores registarem os seus próprios eventos definidos pelo utilizador, fornecendo informações ainda mais úteis que podem ser visualizadas graficamente pela TraceX. Os números de eventos definidos pelo utilizador variam de

**TX_TRACE_USER_EVENT_START** (4096) até **TX_TRACE_USER_EVENT_END** (65535), inclusive. A colocação dos eventos no tampão de vestígios é feita através do ***tx_trace_user_event_insert,*** definido no Capítulo 5. As chamadas de exemplo a seguir inserem dois eventos definidos pelo utilizador no atual tampão de rastreio no alvo, nomeadamente o evento 4096 definido pelo utilizador e o evento 4098:

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>Exibição padrão de eventos de User-Defined

![Ícone de evento definido pelo utilizador](./media/user-guide/tx-events/image0.png)

Por predefinição, o TraceX exibe todos os eventos do utilizador com um ícone de Evento definido pelo utilizador padrão, tal como descrito no Capítulo 6. A figura 28 mostra o ícone de evento definido pelo utilizador padrão para os eventos 452 e 453, que foram colocados no tampão do evento através dos exemplos ***tx_trace_user_event_insert*** anteriores.

![Screenshot do display padrão de eventos definidos pelo utilizador. ](./media/user-guide/10.1.png)
 **FIGURA 28**

Informações detalhadas também estão disponíveis para eventos definidos pelo utilizador. A figura 28 mostra as informações detalhadas do evento 452, que tem o número do evento 4096 e mostra os quatro campos de informação especificados.

![Screenshot da exibição detalhada de eventos definidos pelo utilizador. ](./media/user-guide/10.2.png)
 **FIGURA 29**

## <a name="defining-custom-user-defined-event-icons"></a>Definindo ícones de eventos de User-Defined personalizados

O TraceX também fornece ao utilizador a capacidade de criar ícones de eventos personalizados definidos pelo utilizador e etiquetas de campo de informação personalizadas. Esta capacidade é conseguida adicionando especificações de ícones de evento ao ficheiro de configuração ***tracex_custom.trxc** _ . Este ficheiro está localizado no subdiretório _ *_CustomEvents_** do seu diretório de instalação TraceX definido pelo utilizador, que predefine c:\Azure_RTOS\TraceX. Um caminho de diretório de exemplo é mostrado na Figura 30.

![Screenshot de um caminho de diretório de exemplo. ](./media/user-guide/custom_events_folder.png)
 **FIGURA 30**

O ficheiro de configuração de evento personalizado ***tracex_custom.trxc*** é um simples ficheiro de texto ASCII que contém definições de eventos zero ou mais personalizadas. O formato do ficheiro é o seguinte:

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Cada linha entre Início e Fim é usada para definir um único evento personalizado. A TraceX fornece uma versão de modelo deste ficheiro sem eventos personalizados definidos (nada entre as etiquetas "Iniciar" e "Fim"). O formato de uma definição de evento personalizado é o seguinte:

**número, nome, abreviatura, top_color, bottom_color, label1, label2, label2, label2, label4**

em que:

- número: Define o número de evento definido pelo utilizador, entre 4096 e 65535, inclusive.</th>
- nome: Define o nome lógico para o evento definido pelo utilizador.</td>
- abreviatura: Define a abreviatura do evento definido pelo utilizador de duas letras.</td>
- top_color: Define o valor RGB para a metade superior do ícone, que é um número de três dígitos em parênteses. Algumas definições típicas de RGB são
  - PRETO = (0,0,0)       
  - BRANCO = (255.255.255)
  - VERMELHO = (255,0,0)     
  - VERDE = (0.255,0)     
  - AZUL = (0,0,255)     
  - AMARELO = (255.255,0)   
  - CYAN = (0.255.255)   
  - MAGENTA = (255.0,255)   
  A utilização da especificação RBG dá ao utilizador uma ampla gama de cores para cada ícone definido pelo utilizador. Para obter mais informações sobre a definição de cores RBG, consulte: https://en.wikipedia.org/wiki/RGB#Digital_representations
- botton_color: Define o valor RGB para a metade inferior do ícone, que é um número de três dígitos em parênteses.
- label1: Label for ***info_field_1** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .
- label2: Label for ***info_field_2** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .
- label3: Label for ***info_field_3** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .
- label4: Label for ***info_field_4** _, conforme especificado na chamada _ *_tx_trace_user_event_insert_** .

As definições de exemplo para cada um dos dois eventos definidos pelo utilizador utilizados neste capítulo são apresentadas na Figura 10.4. A primeira definição é para o evento 4096 na linha 5 do ficheiro ***tracex_custom.trxc** _ . Esta definição dá ao evento definido pelo utilizador 4096 o nome _*First_User_Event***, especifica uma abreviatura de duas letras de **FE,** torna a parte superior do ícone vermelha, a parte inferior do ícone verde, e designa os campos de informação como **First_Info1**, **First_Info2**, **First_Info3** e **First_Info4**. O evento 4098 definido pelo utilizador é definido da mesma forma na linha 6 de **_tracex_custom.trxc_**.

![Screenshot das definições de exemplo para os eventos definidos pelo utilizador. ](./media/user-guide/10.4.png)
 **FIGURA 31**

Uma vez que o ficheiro ***tracex_custom.trxc** _ é lido pela TraceX durante a inicialização, o TraceX deve ser saído e reiniciado antes que as definições de ícones personalizados possam produzir efeitos. A figura 32 mostra o ecrã TraceX dos eventos definidos pelo utilizador 452 e 453 com os ícones de eventos personalizados definidos em _*_tracex_custom.trxc_**.

![Screenshot da exibição TraceX de eventos definidos pelo utilizador com os ícones de evento personalizados. ](./media/user-guide/10.5.png)
 **FIGURA 32**

As informações adicionais na definição de evento personalizado são mostradas quando o evento que seleciona usando um duplo clique, rat-over ou clicando no botão de evento atual. A figura 33 mostra a seleção de dois cliques no evento 452. O nome do evento e os campos de informação correspondem à definição de amostra que foi adicionada a ***tracex_custom.trxc***.

![Screenshot da seleção de dois cliques em um evento. ](./media/user-guide/10.6.png)
 **FIGURA 33**
