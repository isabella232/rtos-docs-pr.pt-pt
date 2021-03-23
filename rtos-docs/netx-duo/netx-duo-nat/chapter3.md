---
title: Capítulo 3 - Opções de configuração NAT
description: A lista a seguir inclui todas as opções e a sua função descrita em detalhe
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9c10d6f0d2f36d2794ab1229081799f0032cada8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825861"
---
# <a name="chapter-3---nat-configuration-options"></a>Capítulo 3 - Opções de configuração NAT

As opções configuráveis para o NetX Duo NAT API podem ser encontradas em *nx_nat.h,* com exceção da primeira, **NX_DISABLE_ERROR_CHECKING** que se encontra em *nx_nat.c*. A lista a seguir inclui todas as opções e a sua função descrita em detalhe:

- **NX_NAT_DISABLE_ERROR_CHECKING** Esta opção, se definida, remove a verificação básica de erros NAT. É normalmente usado após a depurada aplicação. O estado padrão netx duo NAT é definido (ativado).
- **NX_NAT_ENABLE_REPLACEMENT** Esta opção, se definida, permite a substituição automática quando a cache NAT está cheia.
  > [!NOTE]
  > Substitua apenas a sessão não TCP mais antiga.
- **NX_NAT_MIN_ENTRY_COUNT** Esta opção define a contagem mínima para a entrada na tradução. A contagem predefinida é 3.
- **NX_NAT_TCP_SESSION_TIMEOUT** Esta opção define o tempo limite para a entrada de tradução para as Sessões TCP. O tempo limite padrão é de 24 horas.
- **NX_NAT_NON_TCP_SESSION_TIMEOUT** Esta opção define o tempo limite para a entrada de tradução para sessões não TCP. O tempo limite de tempo padrão é de 240 segundos.
- **NX_NAT_START_TCP_PORT** Esta opção define o valor inicial para encontrar uma porta TCP nãousada para atribuir um pacote TCP de saída. O valor padrão é 20000.
- **NX_NAT_END_TCP_PORT** Esta opção define o limite superior da porta TCP para atribuir um pacote TCP de saída. O valor predefinido é 30000.
- **NX_NAT_START_UDP_PORT** Esta opção define o valor inicial para encontrar uma porta UDP não uusada para atribuir um pacote UDP de saída. O valor padrão é 20000.
- **NX_NAT_END_UDP_PORT** Esta opção define o limite superior da porta UDP para atribuir um pacote UDP de saída. O valor predefinido é 30000.
- **NX_NAT_START_ICMP_QUERY_ID** Esta opção define o valor inicial para encontrar um ID de consulta nãoused para atribuir um pacote de consulta ICMP de saída. O valor padrão é 20000.
- **NX_NAT_END_ICMP_QUERY_ID** Esta opção define o limite superior dos IDs de consulta para atribuir um pacote de consulta ICMP de saída. O valor predefinido é 30000.
