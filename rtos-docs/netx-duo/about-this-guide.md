---
title: Sobre o Azure RTOS NetX Duo User Guide
description: Este guia contém informações completas sobre o Azure RTOS NetX Duo, a pilha de rede dupla IPv4/IPv6 de alto desempenho da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826239"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a>Sobre o Azure RTOS NetX Duo User Guide

Este guia contém informações completas sobre o Azure RTOS NetX Duo, a pilha de rede dupla IPv4/IPv6 de alto desempenho da Microsoft. 

Destina-se a desenvolvedores de software em tempo real familiarizados com conceitos básicos de rede, Azure RTOS ThreadX e a linguagem de programação C.

## <a name="organization"></a>Organização

[Capítulo 1](chapter1.md) - Introduz Azure RTOS NetX Duo

[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS NetX Duo com a sua aplicação ThreadX

[Capítulo 3](chapter3.md) - Fornece uma visão geral funcional do sistema Azure RTOS NetX Duo e informações básicas sobre as normas de rede TCP/IP

[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS NetX Duo

[Capítulo 5](chapter5.md) - Descreve os controladores de rede para Azure RTOS NetX Duo

[Apêndice A](appendix-a.md) - Azure RTOS NetX Duo Services

[Apêndice B](appendix-b.md) - Azure RTOS NetX Duo Constants

[Apêndice C](appendix-c.md) - Azure RTOS NetX Duo Data Types

[Apêndice D](appendix-d.md) - API de tomada BSD-Compatible

[Apêndice E](appendix-e.md) - Gráfico ASCII

## <a name="guide-conventions"></a>Convenções-Guia

Itálico - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.

**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.

> [!IMPORTANT]
> Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.
 
> [!WARNING]
> Os símbolos de aviso chamam a atenção para situações que os desenvolvedores devem evitar porque podem causar erros fatais.

## <a name="azure-rtos-netx-duo-data-types"></a>Azure RTOS NetX Duo Data Types

Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS NetX Duo, existem vários tipos de dados especiais que são utilizados nas interfaces de chamada de serviço Azure RTOS NetX Duo. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata é herdada da ThreadX e pode ser encontrada no ficheiro ***tx_port.h*** incluído na distribuição ThreadX.

Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS NetX Duo e os seus significados associados:

**UINT**: Número inteiro básico não assinado. Este tipo deve suportar dados não assinados de 32 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado.  
**ULONG**: Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits.
**VOID**: Quase sempre equivalente ao tipo de vazio do compilador.  
**CHAR**: Na maioria das vezes um tipo de caracteres padrão de 8 bits.  

Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS NetX Duo. Estão localizados nos ficheiros ***tx_port.h_** ou _ *_nx_port.h*_*

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS NetX Duo que precederam o problema.
3. O conteúdo das cordas _tx_version_id e _nx_version_id encontrado nos ficheiros tx_port.h e nx_port.h da sua distribuição. Estas cordas fornecer-nos-ão informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM das seguintes variáveis ULONG:

    **_tx_build_options**

    **_nx_system_build_options1**

    **_nx_system_build_options2**

    **_nx_system_build_options3**

    **_nx_system_build_options4**

    **_nx_system_build_options5**

    Estas variáveis dar-nos-ão informações sobre como as suas bibliotecas Azure RTOS ThreadX e Azure RTOS NetX Duo foram construídas.

5. Um tampão de vestígio capturado imediatamente após o problema ter sido detetado. Isto é conseguido construindo as bibliotecas Azure RTOS ThreadX e Azure RTOS NetX Duo com TX_ENABLE_EVENT_TRACE e chamando tx_trace_enable com a informação do tampão de traços.
