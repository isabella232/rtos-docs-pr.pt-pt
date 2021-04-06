---
title: Capítulo 3 - ApIs ThreadX para ARMv8-M
description: Neste capítulo é uma descrição dos serviços ThreadX específicos da ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377629"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="cb0c2-103">ApIs do Capítulo 3 ThreadX para ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="cb0c2-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="cb0c2-104">Este capítulo contém uma descrição dos serviços ThreadX específicos armv8-M por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="cb0c2-105">Os seus nomes são concebidos para que todos os serviços semelhantes sejam agrupados.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="cb0c2-106">Na secção "Valores de Retorno" nas seguintes descrições, os valores em **BOLD** não são afetados pela **TX_DISABLE_ERROR_CHECKING** definem utilizados para desativar a verificação de erros da API; enquanto os valores mostrados em não-arrojado são completamente desativados.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="cb0c2-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Aloque uma pilha de fios na memória segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="cb0c2-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Pilha de fio livre na memória segura</span><span class="sxs-lookup"><span data-stu-id="cb0c2-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="cb0c2-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="cb0c2-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="cb0c2-110">Aloque uma pilha de fios na memória segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="cb0c2-111">Prototype</span><span class="sxs-lookup"><span data-stu-id="cb0c2-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="cb0c2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb0c2-112">Description</span></span>

<span data-ttu-id="cb0c2-113">Este serviço aloca uma pilha de tamanho stack_size bytes em memória segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="cb0c2-114">Esta função deve ser chamada para cada fio que chama funções seguras.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cb0c2-115">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="cb0c2-115">Input Parameters</span></span>

- <span data-ttu-id="cb0c2-116">**thread_ptr** Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="cb0c2-117">**stack_size** Tamanho da pilha segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="cb0c2-118">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="cb0c2-118">Return Values</span></span>

- <span data-ttu-id="cb0c2-119">**TX_SUCCESS** (0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="cb0c2-120">**TX_SIZE_ERROR** (0x05) Stack tamanho fora do alcance.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="cb0c2-121">**TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="cb0c2-122">**TX_NO_MEMORY** (0x10) Incapaz de alocar a memória.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="cb0c2-123">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="cb0c2-124">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado para funcionar em modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cb0c2-125">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="cb0c2-125">Allowed From</span></span>

<span data-ttu-id="cb0c2-126">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="cb0c2-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="cb0c2-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb0c2-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="cb0c2-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb0c2-128">See Also</span></span>

<span data-ttu-id="cb0c2-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="cb0c2-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="cb0c2-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="cb0c2-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="cb0c2-131">Liberte uma pilha de fios em memória segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="cb0c2-132">Prototype</span><span class="sxs-lookup"><span data-stu-id="cb0c2-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="cb0c2-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb0c2-133">Description</span></span>

<span data-ttu-id="cb0c2-134">Este serviço liberta a pilha segura de um fio em memória segura.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="cb0c2-135">Esta função deve ser chamada se um fio tiver uma pilha segura e quando o fio já não precisar de chamar funções seguras ou se o fio for eliminado.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="cb0c2-136">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="cb0c2-136">Input Parameters</span></span>

- <span data-ttu-id="cb0c2-137">**thread_ptr** Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="cb0c2-138">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="cb0c2-138">Return Values</span></span>

- <span data-ttu-id="cb0c2-139">**TX_SUCCESS** (0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="cb0c2-140">**TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="cb0c2-141">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="cb0c2-142">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado para funcionar em modo de segurança.</span><span class="sxs-lookup"><span data-stu-id="cb0c2-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="cb0c2-143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="cb0c2-143">Allowed From</span></span>

<span data-ttu-id="cb0c2-144">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="cb0c2-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="cb0c2-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb0c2-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="cb0c2-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb0c2-146">See Also</span></span>

<span data-ttu-id="cb0c2-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="cb0c2-147">tx_thread_secure_stack_allocate</span></span>
