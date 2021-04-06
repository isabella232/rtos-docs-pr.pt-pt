---
title: Capítulo 2 - Instalação do suporte da ThreadX para ARMv8-M
description: Este capítulo explica como instalar e utilizar o código fonte ThreadX para a arquitetura ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377623"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="8c5eb-103">Capítulo 2 Instalação do suporte da ThreadX para ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="8c5eb-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="8c5eb-104">Existem ficheiros de código fonte ThreadX adicionais para suportar a arquitetura ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="8c5eb-105">Se o ThreadX for executado em modo seguro, estes ficheiros adicionais e APIs não são necessários.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="8c5eb-106">Para executar o ThreadX em modo seguro, defina o símbolo **TX_SECURE_EXECUTION** na parte superior do **_tx_port.h_\*_ ou na linha de comando ou nas definições do projeto. Certifique-se de que a TX_SECURE_EXECUTION**\* está definida para todos os ficheiros c e de montagem.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="8c5eb-107">A ThreadX e a aplicação do utilizador serão executadas em modo seguro.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="8c5eb-108">Para executar o ThreadX e a aplicação do utilizador em modo não seguro e suportar funções seguras de segurança, por favor, faça o seguinte.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="8c5eb-109">O ficheiro ***tx_thread_secure_stack.c*** deve ser adicionado à aplicação segura.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="8c5eb-110">Os seguintes ficheiros devem ser adicionados à biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="8c5eb-111">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="8c5eb-112">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="8c5eb-113">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="8c5eb-114">***tx_thread_secure_stack_allocate.s.***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="8c5eb-115">***tx_thread_secure_stack_free.s.***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="8c5eb-116">Os dois ficheiros seguintes substituem os ficheiros genéricos na biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="8c5eb-117">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="8c5eb-118">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="8c5eb-119">Fontes adicionais da ThreadX para ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="8c5eb-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="8c5eb-120">Os ficheiros ThreadX adicionais para a arquitetura ARMv8-M TrustZone são descritos abaixo.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="8c5eb-121">**Nome do arquivo**</span><span class="sxs-lookup"><span data-stu-id="8c5eb-121">**File Name**</span></span>                            | <span data-ttu-id="8c5eb-122">**Conteúdos**</span><span class="sxs-lookup"><span data-stu-id="8c5eb-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="8c5eb-123">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="8c5eb-124">Inclua o ficheiro que define as funções de chamada não seguras threadX.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="8c5eb-125">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="8c5eb-126">Ficheiro de verificação de erros para a pilha segura alocar API.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="8c5eb-127">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="8c5eb-128">Ficheiro de verificação de erros para a API de pilha segura.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="8c5eb-129">***tx_thread_secure_stack_allocate.s.***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="8c5eb-130">Revestimento não seguro para o serviço de atribuição de pilhas seguras.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="8c5eb-131">***tx_thread_secure_stack_free.s.***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="8c5eb-132">Revestimento não seguro para o serviço gratuito de pilha segura.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="8c5eb-133">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="8c5eb-134">Manipulador para erros de pilha de fios.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="8c5eb-135">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="8c5eb-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="8c5eb-136">Registar a chamada de notificação para lidar com erros de pilha de fios.</span><span class="sxs-lookup"><span data-stu-id="8c5eb-136">Register notification callback for handling thread stack errors.</span></span> |
