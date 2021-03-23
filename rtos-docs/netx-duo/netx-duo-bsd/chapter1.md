---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo BSD
description: O invólucro de API compliância de tomada BSD suporta algumas das chamadas básicas da API da Tomada de Eteção BSD, com algumas limitações e utiliza primitivos Azure RTOS NetX Duo por baixo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826161"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo BSD

O invólucro de API compliância de tomada BSD suporta algumas das chamadas básicas da API da Tomada de Eteção BSD, com algumas limitações e utiliza primitivos Azure RTOS NetX Duo por baixo.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>Fonte de invólucro de api de tomada BSD

O código fonte de invólucro foi concebido para a simplicidade e é composto por dois ficheiros, nomeadamente *nxd_bsd.h* e *nxd_bsd.c*. O ficheiro *nxd_bsd.h* define todas as constantes de invólucro api de tomada de BSD necessárias e protótipos de sub-rotina, enquanto *nxd_bsd.c* contém o código fonte de compatibilidade real da API da tomada de BSD. Estes ficheiros de origem de invólucro são comuns a todos os pacotes de suporte NetX Duo.

O pacote consiste em:

- **nxd_bsd.c**: Código fonte de invólucro
- **nxd_bsd.h**: Ficheiro principal do cabeçalho

Programas de demonstração de amostras:

- **bsd_demo_udp.c**: *Demo com dois pares da UDP (apenas IPv4)*
- **bsd_demo_tcp.c**: *Demo com um único servidor TCP e cliente*
- **bsd_demo_raw.c**: *Demo com dois pares RAW*