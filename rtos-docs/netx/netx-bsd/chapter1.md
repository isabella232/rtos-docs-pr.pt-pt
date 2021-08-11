---
title: Capítulo 1 - Introdução ao Azure RTOS NetX BSD
description: O Azure RTOS NetX BSD Sockets API Compliancy Wrapr suporta algumas das chamadas básicas da API de tomadas BSD com algumas limitações e utiliza primitivos NetX por baixo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b58283a38a25ffdd438d7853999f3b6e390f280a947aa45101d8df86447bf3dd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796725"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a>Capítulo 1 - Introdução ao Azure RTOS NetX BSD

O Invólucro de Combinação de Tomadas BSD NetX suporta algumas das chamadas básicas da API de tomadas BSD com algumas limitações e utiliza primitivos NetX por baixo. Esta camada de compatibilidade com a API de tomadas BSD deve funcionar tão rápida ou ligeiramente mais rápida do que as implementações típicas de BSD, uma vez que este Invólucro utiliza primitivos Internos netX e contorna a verificação básica de erros netX.

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a>Fonte de invólucro de combinação de tomadas BSD API

O código fonte de invólucro BSD foi concebido para a simplicidade e é composto por apenas dois ficheiros, *nx_bsd.h* e *nx_bsd.c*. O ficheiro *nx_bsd.h* define todas as constantes de invólucro api de tomadas BSD necessárias e protótipos de sub-rotina, enquanto *nx_bsd.c* contém o código fonte de compatibilidade API das tomadas BSD reais. Estes ficheiros de origem BSD Wrapper são comuns a todos os pacotes de suporte NetX.

O pacote consiste em:

- **nx_bsd.c**: Código fonte de invólucro
- **nx_bsd.h**: Ficheiro principal do cabeçalho

Programas de demonstração de amostras:

- **bsd_demo_tcp.c**: *Demo com um único servidor TCP e cliente*
- **bsd_demo_udp.c**: *Demo com dois clientes UDP e um servidor UDP*
