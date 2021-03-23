---
title: Capítulo 1 - Introdução ao Azure RTOS NetX BSD
description: O Azure RTOS NetX BSD Sockets API Compliancy Wrapr suporta algumas das chamadas básicas da API de tomadas BSD com algumas limitações e utiliza primitivos NetX por baixo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825609"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="b49cb-103">Capítulo 1 - Introdução ao Azure RTOS NetX BSD</span><span class="sxs-lookup"><span data-stu-id="b49cb-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="b49cb-104">O Invólucro de Combinação de Tomadas BSD NetX suporta algumas das chamadas básicas da API de tomadas BSD com algumas limitações e utiliza primitivos NetX por baixo.</span><span class="sxs-lookup"><span data-stu-id="b49cb-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="b49cb-105">Esta camada de compatibilidade com a API de tomadas BSD deve funcionar tão rápida ou ligeiramente mais rápida do que as implementações típicas de BSD, uma vez que este Invólucro utiliza primitivos Internos netX e contorna a verificação básica de erros netX.</span><span class="sxs-lookup"><span data-stu-id="b49cb-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="b49cb-106">Fonte de invólucro de combinação de tomadas BSD API</span><span class="sxs-lookup"><span data-stu-id="b49cb-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="b49cb-107">O código fonte de invólucro BSD foi concebido para a simplicidade e é composto por apenas dois ficheiros, *nx_bsd.h* e *nx_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="b49cb-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="b49cb-108">O ficheiro *nx_bsd.h* define todas as constantes de invólucro api de tomadas BSD necessárias e protótipos de sub-rotina, enquanto *nx_bsd.c* contém o código fonte de compatibilidade API das tomadas BSD reais.</span><span class="sxs-lookup"><span data-stu-id="b49cb-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="b49cb-109">Estes ficheiros de origem BSD Wrapper são comuns a todos os pacotes de suporte NetX.</span><span class="sxs-lookup"><span data-stu-id="b49cb-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="b49cb-110">O pacote consiste em:</span><span class="sxs-lookup"><span data-stu-id="b49cb-110">The package consists of:</span></span>

- <span data-ttu-id="b49cb-111">**nx_bsd.c**: Código fonte de invólucro</span><span class="sxs-lookup"><span data-stu-id="b49cb-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="b49cb-112">**nx_bsd.h**: Ficheiro principal do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="b49cb-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="b49cb-113">Programas de demonstração de amostras:</span><span class="sxs-lookup"><span data-stu-id="b49cb-113">Sample demo programs:</span></span>

- <span data-ttu-id="b49cb-114">**bsd_demo_tcp.c**: *Demo com um único servidor TCP e cliente*</span><span class="sxs-lookup"><span data-stu-id="b49cb-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="b49cb-115">**bsd_demo_udp.c**: *Demo com dois clientes UDP e um servidor UDP*</span><span class="sxs-lookup"><span data-stu-id="b49cb-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
