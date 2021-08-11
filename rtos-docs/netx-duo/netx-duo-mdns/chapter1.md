---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo mDNS/DNS-SD
description: Azure RTOS NetX Duo mDNS/DNS-SD aumenta o serviço tradicional de DNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7cde8e81809dcc74ee5d0b09d8e7a8d2ae96850cd84250a5bf003fdd5763925a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796451"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Capítulo 1 - Introdução ao Azure RTOS NetX Duo mDNS/DNS-SD

O mDNS e o DNS-SD são protocolos concebidos para aumentar o serviço tradicional de DNS. O mDNS fornece o nome do anfitrião e o serviço de procura aos nós da rede local. Cada nó usa o canal multicast IPv4 ou IPv6 para anunciar serviços que oferece aos seus vizinhos, responde a perguntas dos seus vizinhos, e envia consultas sobre o comportamento das suas aplicações. Por design, o mDNS opera num ambiente distribuído, eliminando assim um serviço centralizado.

O DNS-SD é construído em cima do mDNS. O DNS-SD permite que os nós anunciem os serviços que prestam à rede local ou descubram serviços oferecidos por outros nós na rede local. Ao longo do documento, o termo *mDNS* refere-se aos serviços que abrangem tanto a especificação do mDNS como a especificação DNS-SD.

## <a name="mdns-standard"></a>norma mDNS

A implementação do NetX Duo mDNS/DNS-SD está em conformidade com os seguintes RFCs:

- RFC 6762: especificação mDNS
- RFC 6763: Especificação DNS-SD