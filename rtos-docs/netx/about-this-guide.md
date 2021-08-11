---
title: Sobre o Guia de Utilizador Azure RTOS NetX
description: Este guia contém informações completas sobre o Azure RTOS NetX, a pilha de rede de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7d77997e8c5bac598f382e1169a56727af09ab108f57c90cc6265df0691b5926
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796417"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a>Sobre o Guia de Utilizador Azure RTOS NetX

Este guia contém informações completas sobre o Azure RTOS NetX, a pilha de rede de alto desempenho da Microsoft.

Destina-se a desenvolvedores de software em tempo real familiarizados com conceitos básicos de rede, Azure RTOS ThreadX e a linguagem de programação C.

## <a name="organization"></a>Organização

[Capítulo 1](chapter1.md) - Introduz Azure RTOS NetX

[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS NetX com a sua aplicação ThreadX.

[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS NetX e informações básicas sobre as normas de rede TCP/IP.

[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS NetX.

[Capítulo 5](chapter5.md) - Descreve os controladores de rede para o Azure RTOS NetX.

[Apêndice A](appendix-a.md) - Azure RTOS NetX Services

[Apêndice B](appendix-b.md) - Azure RTOS NetX Constants

[Apêndice C](appendix-c.md) - Azure RTOS NetX Data Types

[Apêndice D](appendix-d.md) - API de tomada BSD-Compatible

[Apêndice E](appendix-e.md) - Gráfico ASCII

## <a name="azure-rtos-netx-data-types"></a>Tipos de dados Azure RTOS NetX

Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS NetX, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS NetX. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.

Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS NetX e os seus significados associados:

| Tipos de Dados | Description  |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **UINT**  | Número inteiro básico não assinado. Este tipo deve suportar dados não assinados de 32 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado. |
| **ULONG** | Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits.                                                                      |
| **VAZIO**  | Quase sempre equivalente ao tipo vazio do compilador.                                                                                 |
| **CHAR**  | Na maioria das vezes, um tipo de caracteres padrão de 8 bits.                                                                                           |

Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS NetX. Estão localizados nos ficheiros ***tx_port.h_** ou _ *_nx_port.h*_*

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.

2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS NetX que precederam o problema.

3. O conteúdo das cordas **_tx_version_id** e **_nx_version_id** encontrados nos ficheiros **_tx_port.h_*_ e _*_nx_port.h_** da sua distribuição. Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.

4. O conteúdo em RAM das seguintes variáveis **ULONG:**

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS NetX foram construídas.

5. Um tampão de vestígio capturado imediatamente após o problema ter sido detetado. Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS NetX com **TX_ENABLE_EVENT_TRACE** e chamando **tx_trace_enable** com a informação do tampão de traços. Consulte o Guia do Utilizador Azure RTOS TraceX para obter mais detalhes.
