---
title: Capítulo 2 - Instalar e utilizar o Azure RTOS NetX Duo Iperf
description: Este capítulo fornece instruções para instalar e utilizar a amostra Iperf.
author: v-condav
ms.author: v-condav
ms.date: 08/16/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7e80d89a334ceec3467b23574ab5c231a15f68a1
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/20/2021
ms.locfileid: "122609956"
---
# <a name="chapter-2-installation-and-use"></a>Capítulo 2 Instalação e Utilização

Este capítulo contém uma descrição de vários problemas relacionados com a instalação, configuração e utilização da Demonstração de Iperf NetX Duo.

## <a name="installing-the-demonstration"></a>Instalação da Demonstração

Siga as instruções de instalação específicas da plataforma fornecidas na distribuição.

## <a name="installing-iperf"></a>Instalação do Iperf

Há uma variedade de programas Iperf que pode usar. No entanto, os exemplos deste documento baseiam-se no ***Jperf 2.0.2*** baseado em Java, que está disponível a partir de várias fontes na Internet.

> [Nota] *Jperf requer que Java seja instalado na máquina de anfitrião.*

## <a name="setting-the-ip-address"></a>Definição do Endereço IP

Por predefinição, o endereço IP da Demonstração do Iperf NetX Duo está definido para **192.2.2.149**. Esta é a configuração no ficheiro **_demo_netx_duo_iperf.c_*_ como um parâmetro para a chamada para _*_nx_ip_create_**.

## <a name="network-assumptions"></a>Pressupostos de rede

Esta demonstração pressupõe que a máquina hospedeira do Iperf e o quadro-alvo que executa a Demonstração do Iperf NetX Duo estão ligados a um interruptor Ethernet full-duplex de 100Mbps. Para obter o melhor desempenho, não deve haver outro tráfego na rede de teste.

Também é possível ligar o anfitrião Iperf e a placa-alvo NetX Duo de costas com um cabo Ethernet transversal.

## <a name="running-the-demonstration"></a>Executando a Demonstração

Fazer a demonstração é fácil; simplesmente carregar, construir e executar o projeto de demonstração netx duo Iperf - tipicamente nomeado ***demo_netx_duo_iperf***.

## <a name="browse-to-the-demonstration"></a>Navegue pela Demonstração

Navegue para o quadro alvo através de um browser na plataforma de anfitriões Iperf. Assumindo o endereço IP do quadro-alvo de **192.2.2.149,** o seguinte é um exemplo da página inicial da Demonstração de Iperf NetX Duo.

![Um exemplo da página inicial do Iperf](media/Picture1.jpg)

## <a name="running-jperf"></a>Jperf correndo

Executar o Jperf é fácil, basta clicar duas vezes no ficheiro de lote Windows ***jperf.bat** _. Isto lança o JPERf IDE, como mostrado abaixo. Uma vez apresentado o JPERf IDE, o campo _ *Endereço do servidor** deve ser definido para o endereço IP do quadro-alvo de demonstração NetX Duo Iperf. Neste exemplo, o endereço IP do quadro-alvo netx duo é **de 192.2.2.149**. Destaque ainda para os campos **UDP Bandwidth** e **UDP Packet Size.** Estes precisam de ser configurados para um desempenho ótimo da UDP, como mostrado abaixo.

![Otimizar o desempenho da UDP.](media/Picture2.jpg)
