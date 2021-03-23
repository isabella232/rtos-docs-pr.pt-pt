---
title: Sobre o Guia Azure RTOS ThreadX
description: Este guia fornece informações completas sobre o Azure RTOS ThreadX, o kernel em tempo real da Microsoft.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826593"
---
# <a name="about-the-azure-rtos-threadx-guide"></a>Sobre o Guia Azure RTOS ThreadX

Este guia fornece informações completas sobre o Azure RTOS ThreadX, o kernel de alto desempenho da Microsoft em tempo real. 

Destina-se ao desenvolvedor de software incorporado em tempo real. O desenvolvedor deve estar familiarizado com as funções padrão do sistema operativo em tempo real e com a linguagem de programação C.

## <a name="organization"></a>Organização

[Capítulo 1](chapter1.md) - Fornece uma visão geral básica da Azure RTOS ThreadX e da sua relação com o desenvolvimento incorporado em tempo real

[Capítulo 2](chapter2.md) - Dá os passos básicos para instalar e utilizar o Azure RTOS ThreadX na sua aplicação *mesmo fora da caixa*

[Capítulo 3](chapter3.md) - Descreve em detalhe o funcionamento do Azure RTOS ThreadX, o núcleo em tempo real de alto desempenho

[Capítulo 4](chapter4.md) - Detalha a interface da aplicação com o Azure RTOS ThreadX

[Capítulo 5](chapter5.md) - Descreve a escrita de controladores de I/O para aplicações Azure RTOS ThreadX

[Capítulo 6](chapter6.md) - Descreve a aplicação de demonstração que é fornecida com todos os pacotes de suporte ao processador Azure RTOS ThreadX

[Apêndice A](appendix-a.md) - Azure RTOS ThreadX API

[Apêndice B](appendix-b.md) - Azure RTOS ThreadX constantes

[Apêndice C](appendix-c.md) - Azure RTOS ThreadX tipos de dados

[Apêndice D](appendix-d.md) - Gráfico ASCII

## <a name="guide-conventions"></a>Convenções-Guia

*Itálico* - o tipo de letra denota títulos de livro, enfatiza palavras importantes e indica parâmetros.

**Boldface** - o tipo de letra denota palavras-chave, constantes, nomes de tipo, elementos de interface de utilizador, nomes variáveis, e enfatiza ainda palavras importantes.

***Itálico e Boldface*** - o tipo de letra denota nomes de ficheiros e nomes de funções.

> [!IMPORTANT]
> Os símbolos de informação chamam a atenção para informações importantes ou adicionais que possam afetar o desempenho ou a função.

> [!WARNING]
> Os símbolos de aviso chamam a atenção para situações em que os desenvolvedores devem ter o cuidado de evitar porque podem causar erros fatais.

## <a name="azure-rtos-threadx-data-types"></a>Tipos de dados Azure RTOS ThreadX

Além dos tipos de dados personalizados da estrutura de controlo Azure RTOS ThreadX, existem uma série de tipos especiais de dados que são utilizados nas interfaces de chamada de serviço Azure RTOS ThreadX. Estes tipos especiais de dados mapeiam diretamente para os tipos de dados do compilador C subjacente. Isto é feito para garantir a portabilidade entre diferentes compiladores C. A implementação exata pode ser encontrada no ficheiro ***tx_port.h*** incluído na fonte.

Segue-se uma lista dos tipos de dados de chamada de chamada de serviço Azure RTOS ThreadX e os seus significados associados:

| Tipo de dados  | Descrição |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **UINT** | Número inteiro básico não assinado. Este tipo deve suportar dados não assinados de 8 bits; no entanto, é mapeado para o mais conveniente tipo de dados não assinado. |
| **ULONG** | Tipo longo não assinado. Este tipo deve suportar dados não assinados de 32 bits. |
| **VAZIO** | Quase sempre equivalente ao tipo vazio do compilador. |
| **CHAR** | Na maioria das vezes, um tipo de caracteres padrão de 8 bits. |
|  |  |

Tipos de dados adicionais são utilizados dentro da fonte Azure RTOS ThreadX. Também estão localizados no ficheiro ***tx_port.h.***

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.
3. O conteúdo da cadeia *_tx_version_id* encontrado no ficheiro *tx_port.h* da sua distribuição. Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM da **_tx_build_options** variável **ULONG.** Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.
