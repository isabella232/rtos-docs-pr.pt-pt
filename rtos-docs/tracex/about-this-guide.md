---
title: Guia de utilizador Azure RTOS TraceX
description: Este guia contém informações completas sobre o Azure RTOS TraceX, a ferramenta de análise de sistema baseada em Windows da Microsoft.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 89a39112d6fc6d231408179ebb3867c21f927326930a1610529b142aa71a1027
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784075"
---
# <a name="about-this-guide"></a>Acerca deste guia

Este guia contém informações completas sobre o Azure RTOS TraceX, a ferramenta de análise do sistema baseada em Windows da Microsoft para Microsoft Azure RTOS.

Destina-se ao desenvolvedor de software incorporado em tempo real utilizando O Azure RTOS ThreadX Real-Time Sistema Operativo (RTOS) e componentes adicionais. O desenvolvedor deve estar familiarizado com os conceitos padrão Azure RTOS ThreadX Azure RTOS FileX e Azure RTOS NetX.

## <a name="organization"></a>Organização

- [Capítulo 1](chapter1.md) - contém uma visão geral básica do Azure RTOS TraceX e descreve a sua relação com o desenvolvimento em tempo real.
- [Capítulo 2](chapter2.md) - dá os passos básicos para instalar e utilizar o Azure RTOS TraceX para analisar a sua aplicação fora da caixa.
- [Capítulo 3](chapter3.md) - descreve as principais características do Azure RTOS TraceX.
- [Capítulo 4](chapter4.md) - detalhes das características de análise de desempenho do Azure RTOS TraceX.
- [Capítulo 5](chapter5.md) - descreve como configurar Azure RTOS ThreadX, Azure RTOS FileX e Azure RTOS NetX para gerar um tampão de traço que seja visível por Azure RTOS TraceX.
- [Capítulo 6](chapter6.md) - descreve em detalhe os eventos Azure RTOS TraceX.
- [Capítulo 7](chapter7.md) - descreve em detalhe os eventos Azure RTOS FileX.
- [Capítulo 8](chapter8.md) - descreve em detalhe os eventos Azure RTOS NetX.
- [Capítulo 9](chapter9.md) - descreve em detalhe os eventos Azure RTOS USBX.
- [Capítulo 10](chapter10.md) - descreve a criação de eventos personalizados do utilizador em detalhe.
- [Capítulo 11](chapter11.md) - descreve o tampão de vestígios interno em detalhe.
- [Apêndice A](appendix-a.md) - Arquivo específico da porta Azure RTOS ThreadX com a sua fonte de carimbo de tempo para recolha de eventos de rastreio.
- [Apêndice B](appendix-b.md) - Ficheiro Azure RTOS ThreadX *tx_trace.h* que mostra detalhes de implementação relativos ao tampão de rastreio do evento.
- [Apêndice C](appendix-c.md) - Resumo dos utilitários da linha de comando para converter vários formatos de ficheiros em ficheiros binários Azure RTOS TraceX.
- [Apêndice D](appendix-d.md) - Exemplos de despejo de ficheiros de vestígios de várias ferramentas de desenvolvimento.

## <a name="guide-conventions"></a>Convenções-Guia

*Itálico* - O tipo de letra denota títulos de livro, enfatiza palavras importantes e indica variáveis.

**Boldface** - Typeface denota nomes de ficheiros, palavras-chave, e enfatiza ainda palavras e variáveis importantes.

> [!NOTE]
> Indica informação de nota.

## <a name="customer-support-center"></a>Centro de Apoio ao Cliente

Por favor envie um bilhete de apoio através do Portal Azure para perguntas ou ajuda a usar os passos aqui. Por favor, forneça-nos as seguintes informações numa mensagem de correio eletrónico para que possamos resolver de forma mais eficiente o seu pedido de apoio:

1. Uma descrição pormenorizada do problema, incluindo a frequência da ocorrência e se pode ser reproduzida de forma fiável.
2. Uma descrição detalhada de quaisquer alterações à aplicação e/ou Azure RTOS ThreadX que precederam o problema.
3. O conteúdo da cadeia *_tx_version_id* encontrado no ficheiro *tx_port.h* da sua distribuição. Esta corda fornecer-nos-á informações valiosas sobre o seu ambiente de tempo de execução.
4. O conteúdo em RAM da *_tx_build_options* variável ULONG. Esta variável vai dar-nos informações sobre como a sua biblioteca Azure RTOS ThreadX foi construída.
