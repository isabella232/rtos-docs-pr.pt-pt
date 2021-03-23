---
title: Capítulo 1 - Introdução ao Azure RTOS NetX Duo mDNS/DNS-SD
description: Azure RTOS NetX Duo mDNS/DNS-SD aumenta o serviço tradicional de DNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825927"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="cdf0d-103">Capítulo 1 - Introdução ao Azure RTOS NetX Duo mDNS/DNS-SD</span><span class="sxs-lookup"><span data-stu-id="cdf0d-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="cdf0d-104">O mDNS e o DNS-SD são protocolos concebidos para aumentar o serviço tradicional de DNS.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="cdf0d-105">O mDNS fornece o nome do anfitrião e o serviço de procura aos nós da rede local.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="cdf0d-106">Cada nó usa o canal multicast IPv4 ou IPv6 para anunciar serviços que oferece aos seus vizinhos, responde a perguntas dos seus vizinhos, e envia consultas sobre o comportamento das suas aplicações.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="cdf0d-107">Por design, o mDNS opera num ambiente distribuído, eliminando assim um serviço centralizado.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="cdf0d-108">O DNS-SD é construído em cima do mDNS.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="cdf0d-109">O DNS-SD permite que os nós anunciem os serviços que prestam à rede local ou descubram serviços oferecidos por outros nós na rede local.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="cdf0d-110">Ao longo do documento, o termo *mDNS* refere-se aos serviços que abrangem tanto a especificação do mDNS como a especificação DNS-SD.</span><span class="sxs-lookup"><span data-stu-id="cdf0d-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="cdf0d-111">norma mDNS</span><span class="sxs-lookup"><span data-stu-id="cdf0d-111">mDNS Standard</span></span>

<span data-ttu-id="cdf0d-112">A implementação do NetX Duo mDNS/DNS-SD está em conformidade com os seguintes RFCs:</span><span class="sxs-lookup"><span data-stu-id="cdf0d-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="cdf0d-113">RFC 6762: especificação mDNS</span><span class="sxs-lookup"><span data-stu-id="cdf0d-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="cdf0d-114">RFC 6763: Especificação DNS-SD</span><span class="sxs-lookup"><span data-stu-id="cdf0d-114">RFC 6763: DNS-SD Specification</span></span>