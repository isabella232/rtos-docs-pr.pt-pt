---
title: Capítulo 1 - Introdução ao Azure RTOS TraceX
description: Azure RTOS TraceX é uma ferramenta de análise de sistema da Microsoft que exibe informações de eventos do sistema recolhidas pela ThreadX em execução num alvo incorporado.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827685"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="f3d81-103">Capítulo 1 - Introdução ao Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="f3d81-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="f3d81-104">Azure RTOS TraceX é uma ferramenta de análise de sistema da Microsoft que exibe informações de eventos do sistema recolhidas pela ThreadX em execução num alvo incorporado.</span><span class="sxs-lookup"><span data-stu-id="f3d81-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="f3d81-105">O utilizador é responsável pela transferência do tampão de traço armazenado na RAM no alvo incorporado para um ficheiro binário no computador anfitrião.</span><span class="sxs-lookup"><span data-stu-id="f3d81-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="f3d81-106">O utilizador pode então abrir este ficheiro com traceX e analisar graficamente os eventos-alvo, diagnosticando problemas do sistema e ajustando uma aplicação de trabalho para melhorar o desempenho e a gestão de recursos.</span><span class="sxs-lookup"><span data-stu-id="f3d81-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="f3d81-107">Requisitos TraceX</span><span class="sxs-lookup"><span data-stu-id="f3d81-107">TraceX Requirements</span></span>

<span data-ttu-id="f3d81-108">TraceX requer Windows XP (ou acima).</span><span class="sxs-lookup"><span data-stu-id="f3d81-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="f3d81-109">O sistema deve ter um mínimo de 192 MB de RAM, 2 GB de espaço em disco rígido disponível e um ecrã mínimo de 1024x768 com 256 cores.</span><span class="sxs-lookup"><span data-stu-id="f3d81-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="f3d81-110">Além disso, a aplicação deve estar em execução no ThreadX V5.0 ou mais tarde.</span><span class="sxs-lookup"><span data-stu-id="f3d81-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="f3d81-111">O TraceX também requer a instalação da estrutura Microsoft .NET, o que o instalador TraceX faz automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f3d81-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="f3d81-112">Restrições TraceX</span><span class="sxs-lookup"><span data-stu-id="f3d81-112">TraceX Constraints</span></span>

<span data-ttu-id="f3d81-113">A TraceX tem os seguintes constrangimentos:</span><span class="sxs-lookup"><span data-stu-id="f3d81-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="f3d81-114">Os ficheiros TraceX estão limitados a um máximo de 32.768 eventos (cerca de 1 MB).</span><span class="sxs-lookup"><span data-stu-id="f3d81-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="f3d81-115">A fonte de carimbo de tempo deve ter uma resolução razoável.</span><span class="sxs-lookup"><span data-stu-id="f3d81-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="f3d81-116">Se a resolução for muito baixa, os acontecimentos sobrepõem-se.</span><span class="sxs-lookup"><span data-stu-id="f3d81-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="f3d81-117">Se a resolução for demasiado elevada, existe potencial para longas lacunas entre os acontecimentos.</span><span class="sxs-lookup"><span data-stu-id="f3d81-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="f3d81-118">O TraceX não pode medir com precisão intervalos entre eventos maiores do que o período de temporizador.</span><span class="sxs-lookup"><span data-stu-id="f3d81-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
