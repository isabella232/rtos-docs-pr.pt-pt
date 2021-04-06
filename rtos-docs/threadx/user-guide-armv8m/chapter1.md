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
# <a name="chapter-1--overview"></a>Visão geral do Capítulo 1

A arquitetura ARMv8-M introduz novas funcionalidades de segurança, incluindo o TrustZone, que permite que a memória seja marcada como segura ou não segura. Seguindo as diretrizes da ARM, a ThreadX (e a aplicação do utilizador) foi concebida para ser executada em modo não seguro. O ThreadX (e a aplicação do utilizador) também pode ser executado em modo seguro. Para interagir com o software de modo seguro, são necessários alguns novos APIs Da ThreadX. Este documento descreve estes serviços ThreadX específicos da arquitetura ARMv8-M, incluindo o Córtex-M23, Cortex-M33, Cortex-M35P e Cortex-M55.
