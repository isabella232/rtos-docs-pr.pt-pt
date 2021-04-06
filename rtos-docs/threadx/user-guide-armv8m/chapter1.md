---
title: Capítulo 1 - Introdução ao Azure RTOS ThreadX para ARMv8-M.
description: Este capítulo é o ponto de partida para a leitura sobre o Azure RTOS ThreadX Addendum para ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377628"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="93ce7-103">Visão geral do Capítulo 1</span><span class="sxs-lookup"><span data-stu-id="93ce7-103">Chapter 1  Overview</span></span>

<span data-ttu-id="93ce7-104">A arquitetura ARMv8-M introduz novas funcionalidades de segurança, incluindo o TrustZone, que permite que a memória seja marcada como segura ou não segura.</span><span class="sxs-lookup"><span data-stu-id="93ce7-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="93ce7-105">Seguindo as diretrizes da ARM, a ThreadX (e a aplicação do utilizador) foi concebida para ser executada em modo não seguro.</span><span class="sxs-lookup"><span data-stu-id="93ce7-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="93ce7-106">O ThreadX (e a aplicação do utilizador) também pode ser executado em modo seguro.</span><span class="sxs-lookup"><span data-stu-id="93ce7-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="93ce7-107">Para interagir com o software de modo seguro, são necessários alguns novos APIs Da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="93ce7-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="93ce7-108">Este documento descreve estes serviços ThreadX específicos da arquitetura ARMv8-M, incluindo o Córtex-M23, Cortex-M33, Cortex-M35P e Cortex-M55.</span><span class="sxs-lookup"><span data-stu-id="93ce7-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
