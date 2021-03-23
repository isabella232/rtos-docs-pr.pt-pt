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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="90eee-103">Capítulo 1 - Introdução ao Azure RTOS NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="90eee-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="90eee-104">O invólucro de API compliância de tomada BSD suporta algumas das chamadas básicas da API da Tomada de Eteção BSD, com algumas limitações e utiliza primitivos Azure RTOS NetX Duo por baixo.</span><span class="sxs-lookup"><span data-stu-id="90eee-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="90eee-105">Fonte de invólucro de api de tomada BSD</span><span class="sxs-lookup"><span data-stu-id="90eee-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="90eee-106">O código fonte de invólucro foi concebido para a simplicidade e é composto por dois ficheiros, nomeadamente *nxd_bsd.h* e *nxd_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="90eee-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="90eee-107">O ficheiro *nxd_bsd.h* define todas as constantes de invólucro api de tomada de BSD necessárias e protótipos de sub-rotina, enquanto *nxd_bsd.c* contém o código fonte de compatibilidade real da API da tomada de BSD.</span><span class="sxs-lookup"><span data-stu-id="90eee-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="90eee-108">Estes ficheiros de origem de invólucro são comuns a todos os pacotes de suporte NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="90eee-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="90eee-109">O pacote consiste em:</span><span class="sxs-lookup"><span data-stu-id="90eee-109">The package consists of:</span></span>

- <span data-ttu-id="90eee-110">**nxd_bsd.c**: Código fonte de invólucro</span><span class="sxs-lookup"><span data-stu-id="90eee-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="90eee-111">**nxd_bsd.h**: Ficheiro principal do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="90eee-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="90eee-112">Programas de demonstração de amostras:</span><span class="sxs-lookup"><span data-stu-id="90eee-112">Sample demo programs:</span></span>

- <span data-ttu-id="90eee-113">**bsd_demo_udp.c**: *Demo com dois pares da UDP (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="90eee-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="90eee-114">**bsd_demo_tcp.c**: *Demo com um único servidor TCP e cliente*</span><span class="sxs-lookup"><span data-stu-id="90eee-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="90eee-115">**bsd_demo_raw.c**: *Demo com dois pares RAW*</span><span class="sxs-lookup"><span data-stu-id="90eee-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>