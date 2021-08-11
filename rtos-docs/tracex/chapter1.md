---
title: Capítulo 1 - Introdução ao Azure RTOS TraceX
description: Azure RTOS TraceX é uma ferramenta de análise de sistema da Microsoft que exibe informações de eventos do sistema recolhidas pela ThreadX em execução num alvo incorporado.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 70eb06341e5d57f59c74888046bda3bbf95dc88cac56332be640d9576551796f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785061"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a>Capítulo 1 - Introdução ao Azure RTOS TraceX

Azure RTOS TraceX é uma ferramenta de análise de sistema da Microsoft que exibe informações de eventos do sistema recolhidas pela ThreadX em execução num alvo incorporado. O utilizador é responsável pela transferência do tampão de traço armazenado na RAM no alvo incorporado para um ficheiro binário no computador anfitrião. O utilizador pode então abrir este ficheiro com traceX e analisar graficamente os eventos-alvo, diagnosticando problemas do sistema e ajustando uma aplicação de trabalho para melhorar o desempenho e a gestão de recursos.

## <a name="tracex-requirements"></a>Requisitos TraceX

TraceX requer Windows XP (ou acima). O sistema deve ter um mínimo de 192 MB de RAM, 2 GB de espaço em disco rígido disponível e um ecrã mínimo de 1024x768 com 256 cores. Além disso, a aplicação deve estar em execução no ThreadX V5.0 ou mais tarde.

O TraceX também requer a instalação da estrutura Microsoft .NET, o que o instalador TraceX faz automaticamente.

## <a name="tracex-constraints"></a>Restrições TraceX

A TraceX tem os seguintes constrangimentos:

- Os ficheiros TraceX estão limitados a um máximo de 32.768 eventos (cerca de 1 MB).
- A fonte de carimbo de tempo deve ter uma resolução razoável. Se a resolução for muito baixa, os acontecimentos sobrepõem-se. Se a resolução for demasiado elevada, existe potencial para longas lacunas entre os acontecimentos.
- O TraceX não pode medir com precisão intervalos entre eventos maiores do que o período de temporizador.
