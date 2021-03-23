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
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a><span data-ttu-id="9ea89-103">Apêndice A - Azure RTOS NetX Duo SNTP Códigos de erro fatal</span><span class="sxs-lookup"><span data-stu-id="9ea89-103">Appendix A - Azure RTOS NetX Duo SNTP Fatal Error Codes</span></span>

<span data-ttu-id="9ea89-104">Os seguintes códigos de erro resultarão no Azure RTOS NETX Duo SNTP Client abortando atualizações de tempo com o servidor atual.</span><span class="sxs-lookup"><span data-stu-id="9ea89-104">The following error codes will result in the Azure RTOS NetX Duo SNTP Client aborting time updates with the current server.</span></span> <span data-ttu-id="9ea89-105">Cabe à aplicação decidir se o servidor deve ser removido da lista de clientes disponíveis da SNTP ou simplesmente mudar para o próximo servidor disponível na lista.</span><span class="sxs-lookup"><span data-stu-id="9ea89-105">It is up to the application to decide if the server should be removed from the SNTP Client list of available servers, or simply switch to the next available server on the list.</span></span> <span data-ttu-id="9ea89-106">A definição de cada estado de erro é definida em \*nxd_sntp_client.h.</span><span class="sxs-lookup"><span data-stu-id="9ea89-106">The definition of each error status is defined in \*nxd_sntp_client.h.</span></span> *

<span data-ttu-id="9ea89-107">Quando o Cliente SNTP retorna um erro da lista abaixo para a aplicação, o Servidor deve provavelmente ser substituído por outro Servidor.</span><span class="sxs-lookup"><span data-stu-id="9ea89-107">When the SNTP Client returns an error from the list below to the application, the Server should probably be replaced with another Server.</span></span> <span data-ttu-id="9ea89-108">Note que o estado de erro NX_SNTP_KOD_REMOVE_SERVER é deixado ao beijo do cliente SNTP do manipulador de morte (função de retorno de chamada) para definir:</span><span class="sxs-lookup"><span data-stu-id="9ea89-108">Note that the NX_SNTP_KOD_REMOVE_SERVER error status is left to the SNTP Client kiss of death handler (callback function) to set:</span></span>

- <span data-ttu-id="9ea89-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span><span class="sxs-lookup"><span data-stu-id="9ea89-109">NX_SNTP_KOD_REMOVE_SERVER 0xD0C</span></span>  
- <span data-ttu-id="9ea89-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span><span class="sxs-lookup"><span data-stu-id="9ea89-110">NX_SNTP_SERVER_AUTH_FAIL 0xD0D</span></span>  
- <span data-ttu-id="9ea89-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span><span class="sxs-lookup"><span data-stu-id="9ea89-111">NX_SNTP_INVALID_NTP_VERSION 0xD11</span></span>  
- <span data-ttu-id="9ea89-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span><span class="sxs-lookup"><span data-stu-id="9ea89-112">NX_SNTP_INVALID_SERVER_MODE 0xD12</span></span>  
- <span data-ttu-id="9ea89-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span><span class="sxs-lookup"><span data-stu-id="9ea89-113">NX_SNTP_INVALID_SERVER_STRATUM 0xD15</span></span>  

<span data-ttu-id="9ea89-114">Quando o Cliente SNTP retorna um erro da lista abaixo para a aplicação, o Servidor só pode ser temporariamente incapaz de fornecer atualizações de tempo válidas e não precisa de ser removido:</span><span class="sxs-lookup"><span data-stu-id="9ea89-114">When the SNTP Client returns an error from the list below to the application, the Server may only temporarily be unable to provide valid time updates and need not be removed:</span></span>

- <span data-ttu-id="9ea89-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span><span class="sxs-lookup"><span data-stu-id="9ea89-115">HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09</span></span>  
- <span data-ttu-id="9ea89-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span><span class="sxs-lookup"><span data-stu-id="9ea89-116">NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A</span></span>  
- <span data-ttu-id="9ea89-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span><span class="sxs-lookup"><span data-stu-id="9ea89-117">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B</span></span>  
- <span data-ttu-id="9ea89-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span><span class="sxs-lookup"><span data-stu-id="9ea89-118">NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17</span></span>  
- <span data-ttu-id="9ea89-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span><span class="sxs-lookup"><span data-stu-id="9ea89-119">NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16</span></span>  
- <span data-ttu-id="9ea89-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span><span class="sxs-lookup"><span data-stu-id="9ea89-120">NX_SNTP_INVALID_RTT_TIME 0xD21</span></span>  
- <span data-ttu-id="9ea89-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span><span class="sxs-lookup"><span data-stu-id="9ea89-121">NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24</span></span>