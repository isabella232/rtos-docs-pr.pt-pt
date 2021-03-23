---
title: Apêndice A - Azure RTOS NetX Duo SNTP Códigos de erro fatal
description: Os seguintes códigos de erro resultarão no Azure RTOS NETX Duo SNTP Client abortando atualizações de tempo com o servidor atual.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825760"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>Apêndice A - Azure RTOS NetX Duo SNTP Códigos de erro fatal

Os seguintes códigos de erro resultarão no Azure RTOS NETX Duo SNTP Client abortando atualizações de tempo com o servidor atual. Cabe à aplicação decidir se o servidor deve ser removido da lista de clientes disponíveis da SNTP ou simplesmente mudar para o próximo servidor disponível na lista. A definição de cada estado de erro é definida em *nxd_sntp_client.h. *

Quando o Cliente SNTP retorna um erro da lista abaixo para a aplicação, o Servidor deve provavelmente ser substituído por outro Servidor. Note que o estado de erro NX_SNTP_KOD_REMOVE_SERVER é deixado ao beijo do cliente SNTP do manipulador de morte (função de retorno de chamada) para definir:

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

Quando o Cliente SNTP retorna um erro da lista abaixo para a aplicação, o Servidor só pode ser temporariamente incapaz de fornecer atualizações de tempo válidas e não precisa de ser removido:

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24