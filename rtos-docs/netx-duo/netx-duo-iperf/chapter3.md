---
title: Capítulo 3 - Execução do Teste de Transmissão UDP
description: Este capítulo fornece instruções para o funcionamento da amostra do Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a68ba3ddb71adc424002c815fd023f50b552997
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609962"
---
# <a name="chapter-3-running-the-demonstration"></a>Capítulo 3 Executando a Demonstração

Assumindo que o navegador anfitrião está a exibir a página web netX Duo Iperf Demonstration como mostrado anteriormente e o Jperf está a ser executado no anfitrião, este capítulo descreve como executar cada teste Iperf.

## <a name="running-the-udp-transmit-test"></a>Executando o Teste de Transmissão UDP

O Teste de Transmissão UDP determina o desempenho da transmissão UDP da NetX Duo ao anfitrião. Neste teste, o alvo netX Duo é o cliente e o anfitrião Jperf é o servidor. Em primeiro lugar, selecione **Server** e **UDP** no Jperf IDE. Em seguida, selecione **Run IPerf!** para iniciar o servidor Iperf, como mostrado abaixo.

![A fazer o teste de transmissão da UDP.](media/picture3.jpg)

Agora, a partir da página web netX Duo Iperf Demonstration, selecione o botão Iniciar o **Teste de Transmissão UDP** para iniciar o teste. Deverá agora observar as estatísticas de desempenho no JPERf IDE e na página web netx Duo atualizadas, como mostrado abaixo.

![Estatísticas de teste de transmissão da UDP.](media/picture4.jpg)

Para completar o teste, selecione **aqui** link na página web netX Duo Iperf Demonstration. Deve agora observar os resultados do teste. Neste exemplo, o desempenho da transmissão da UDP no alvo da NetX Duo para o anfitrião Iperf foi de 94Mbps no alvo netx duo, como mostrado abaixo.

![Resultados dos testes de transmissão da UDP.](media/picture5.jpg)

## <a name="running-the-udp-receive-test"></a>Executar o Teste de Receção da UDP

O Teste de Receção UDP determina o desempenho da receção UDP da NetX Duo no alvo NetX Duo. Neste teste, o alvo netX Duo é o servidor e o anfitrião Jperf é o cliente. Em primeiro lugar, selecione **Cliente** e **UDP** no JPERF IDE. Em seguida, selecione **Start UDP Receive Test** na página web NetX Duo Iperf Demonstration, como mostrado na ilustração seguinte.

![Executar o teste de receção da UDP.](media/picture6.jpg)

Agora selecione **Run IPerf!** do IDE jperf e observar estatísticas no IDE jperf, como mostrado abaixo.

![UDP recebe estatísticas de teste.](media/picture7.jpg)

Para completar o teste, selecione o link **aqui** na página web netX Duo Iperf Demonstration. Deve agora observar os resultados do teste. Neste exemplo, o desempenho da receção da UDP no alvo netx duo foi de 95Mbps, como mostrado abaixo.

![UDP recebe resultados dos testes](media/picture8.jpg)

## <a name="running-the-tcp-transmit-test"></a>Executando o Teste de Transmissão TCP

O Teste de Transmissão TCP determina o desempenho da transmissão NetX Duo TCP ao anfitrião. Neste teste, o alvo netX Duo é o cliente e o anfitrião Jperf é o servidor. Em primeiro lugar, selecione **Server** e **TCP** no JPERF IDE. Em seguida, selecione **Run IPerf!** para iniciar o servidor Iperf, como mostrado abaixo.

![A executar o teste de transmissão de TCP.](media/picture9.jpg)

Agora, a partir da página web netX Duo Iperf Demonstration, selecione o botão iniciar o **teste de transmissão TCP** para iniciar o teste. Deverá agora observar as estatísticas de desempenho no JPERf IDE e na página web netx Duo Iperf Demonstration atualizada, como mostrado abaixo.

![Estatísticas de transmissão de TCP.](media/picture10.jpg)

Para completar o teste, selecione o link ***aqui*** na página web netX Duo Iperf Demonstration. Deve agora observar os resultados do teste. Neste exemplo, o desempenho da transmissão TCP no alvo netx duo foi de 91Mbps, como mostrado abaixo.

![TCP transmite os resultados dos testes.](media/picture11.jpg)

## <a name="running-the-tcp-receive-test"></a>Executar o Teste de Receção TCP

O Teste de Receção TCP determina o desempenho da receção NetX Duo TCP no alvo NetX Duo. Neste teste, o alvo netX Duo é o servidor e o anfitrião Jperf é o cliente. Em primeiro lugar, selecione **Cliente** e **TCP** no JPERF IDE. Em seguida, selecione **Start TCP Receive Test** na página web NetX Duo, como mostrado.

![Executar o teste de receção de TCP](media/picture12.jpg)

Agora selecione **Run IPerf!** do IDE jperf e observar estatísticas no IDE jperf, como mostrado abaixo.

![A TCP recebe estatísticas de teste.](media/picture13.jpg)

Para completar o teste, selecione o link ***aqui*** na página web netX Duo Iperf Demonstration. Deve agora observar os resultados do teste. Neste exemplo, o desempenho da receção da TCP no alvo netx duo foi de 71Mbps, como mostrado abaixo.

![A TCP recebe os resultados dos testes.](media/picture14.jpg)
