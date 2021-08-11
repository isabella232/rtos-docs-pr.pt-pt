---
title: Capítulo 1 - Introdução ao Azure RTOS ThreadX para ARMv8-M.
description: Este capítulo é o ponto de partida para a leitura sobre o Azure RTOS ThreadX Addendum para ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798253"
---
# <a name="chapter-1--overview"></a>Visão geral do Capítulo 1

A arquitetura ARMv8-M introduz novas funcionalidades de segurança, incluindo o TrustZone, que permite que a memória seja marcada como segura ou não segura. Seguindo as diretrizes da ARM, a ThreadX (e a aplicação do utilizador) foi concebida para ser executada em modo não seguro. O ThreadX (e a aplicação do utilizador) também pode ser executado em modo seguro. Para interagir com o software de modo seguro, são necessários alguns novos APIs Da ThreadX. Este documento descreve estes serviços ThreadX específicos da arquitetura ARMv8-M, incluindo o Córtex-M23, Cortex-M33, Cortex-M35P e Cortex-M55.
