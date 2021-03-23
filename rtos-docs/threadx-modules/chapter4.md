---
title: Capítulo 4 - APIs do módulo
author: philmea
ms.author: philmea
description: Este artigo é um resumo das APIs adicionais disponíveis para um módulo.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825489"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="0c477-103">Capítulo 4 - APIs do módulo</span><span class="sxs-lookup"><span data-stu-id="0c477-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="0c477-104">Resumo das APIs do Módulo</span><span class="sxs-lookup"><span data-stu-id="0c477-104">Summary of Module APIs</span></span>

<span data-ttu-id="0c477-105">Existem várias funções API adicionais disponíveis para um módulo, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0c477-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="0c477-106">***txm_module_application_request** _ - pedido específico de _Application ao código residente*</span><span class="sxs-lookup"><span data-stu-id="0c477-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="0c477-107">***txm_module_object_allocate** _ - _Allocate memória fora do módulo para objeto*</span><span class="sxs-lookup"><span data-stu-id="0c477-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="0c477-108">***txm_module_object_deallocate** _ - _Deallocate memória de objeto previamente atribuída*</span><span class="sxs-lookup"><span data-stu-id="0c477-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="0c477-109">***txm_module_object_pointer_get** _ - _Find objeto do sistema e recuperar o ponteiro do objeto*</span><span class="sxs-lookup"><span data-stu-id="0c477-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="0c477-110">***txm_module_object_pointer_get_extended** _ - _Find objeto do sistema e recuperar o ponteiro do objeto, a segurança do comprimento do nome*</span><span class="sxs-lookup"><span data-stu-id="0c477-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="0c477-111">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-111">Return values</span></span>

<span data-ttu-id="0c477-112">Códigos de erro adicionais são devolvidos para algumas APOs RTOS Azure.</span><span class="sxs-lookup"><span data-stu-id="0c477-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="0c477-113">Estes códigos de erro adicionais são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0c477-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="0c477-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indica que o módulo não tem as propriedades corretas para fazer uma chamada API.</span><span class="sxs-lookup"><span data-stu-id="0c477-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="0c477-115">Por exemplo, chamar apis de rastreio no modo de utilizador.</span><span class="sxs-lookup"><span data-stu-id="0c477-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="0c477-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indica que a memória fornecida pelo módulo é inválida ou está num local inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="0c477-117">Por exemplo, nos módulos protegidos pela memória, os blocos de controlo de objetos não podem ser localizados na memória que o módulo possa aceder.</span><span class="sxs-lookup"><span data-stu-id="0c477-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="0c477-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): A chamada especificada na API está fora do alcance do código do módulo e, portanto, é inválida.</span><span class="sxs-lookup"><span data-stu-id="0c477-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="0c477-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="0c477-119">txm_module_application_request</span></span>

<span data-ttu-id="0c477-120">Pedido específico de inscrição para código residente.</span><span class="sxs-lookup"><span data-stu-id="0c477-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="0c477-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="0c477-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="0c477-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c477-122">Description</span></span>

<span data-ttu-id="0c477-123">Este serviço faz o pedido especificado à parte residente do pedido.</span><span class="sxs-lookup"><span data-stu-id="0c477-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="0c477-124">Presume-se que a estrutura do pedido é preparada antes da chamada.</span><span class="sxs-lookup"><span data-stu-id="0c477-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="0c477-125">O processamento efetivo do pedido ocorre no código residente na função ***_txm_module_manager_application_request***.</span><span class="sxs-lookup"><span data-stu-id="0c477-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="0c477-126">Por predefinição, esta função é deixada vazia e foi concebida para que o desenvolvedor de aplicações residentes se modifique.</span><span class="sxs-lookup"><span data-stu-id="0c477-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c477-127">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c477-127">Input parameters</span></span>

- <span data-ttu-id="0c477-128">**pedido** ID do pedido (candidatura definida)</span><span class="sxs-lookup"><span data-stu-id="0c477-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="0c477-129">**param_1** Primeiro parâmetro</span><span class="sxs-lookup"><span data-stu-id="0c477-129">**param_1** First parameter</span></span>
- <span data-ttu-id="0c477-130">**param_2** Segundo parâmetro</span><span class="sxs-lookup"><span data-stu-id="0c477-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="0c477-131">**param_3** Terceiro parâmetro</span><span class="sxs-lookup"><span data-stu-id="0c477-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="0c477-132">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-132">Return values</span></span>

- <span data-ttu-id="0c477-133">**TX_SUCCESS** (0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="0c477-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="0c477-134">**TX_NOT_AVAILABLE** (0x1D) Pedido não suportado pelo código residente.</span><span class="sxs-lookup"><span data-stu-id="0c477-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c477-135">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-135">Allowed from</span></span>

<span data-ttu-id="0c477-136">Fios de módulos</span><span class="sxs-lookup"><span data-stu-id="0c477-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="0c477-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c477-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="0c477-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="0c477-138">txm_module_object_allocate</span></span>

<span data-ttu-id="0c477-139">Aloque a memória na piscina de objetos (criada pela aplicação residente) para um bloco de controlo de objetos de módulo.</span><span class="sxs-lookup"><span data-stu-id="0c477-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="0c477-140">Prototype</span><span class="sxs-lookup"><span data-stu-id="0c477-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="0c477-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c477-141">Description</span></span>

<span data-ttu-id="0c477-142">Este serviço atribui a memória a um objeto de módulo da memória fora do módulo, o que ajuda a prevenir a corrupção do bloco de controlo de objetos pelo código do módulo.</span><span class="sxs-lookup"><span data-stu-id="0c477-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="0c477-143">Nos sistemas protegidos pela memória, todos os blocos de controlo de objetos devem ser atribuídos com esta API antes de poderem ser criados.</span><span class="sxs-lookup"><span data-stu-id="0c477-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c477-144">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c477-144">Input parameters</span></span>

- <span data-ttu-id="0c477-145">**object_ptr** Destino do ponteiro de objetos na atribuição bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0c477-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="0c477-146">**object_size** Tamanho em bytes do objeto a atribuir.</span><span class="sxs-lookup"><span data-stu-id="0c477-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c477-147">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-147">Return values</span></span>

- <span data-ttu-id="0c477-148">**TX_SUCCESS** (0x00) Alocado objeto bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0c477-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="0c477-149">**TX_NO_MEMORY** (0x10) Não há memória suficiente.</span><span class="sxs-lookup"><span data-stu-id="0c477-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="0c477-150">**TX_NOT_AVAILABLE** (0x1D) Gestor de módulos não criou um pool de objetos para alocar a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c477-151">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-151">Allowed from</span></span>

<span data-ttu-id="0c477-152">Fios de módulos</span><span class="sxs-lookup"><span data-stu-id="0c477-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="0c477-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c477-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="0c477-154">Veja também</span><span class="sxs-lookup"><span data-stu-id="0c477-154">See also</span></span>

- <span data-ttu-id="0c477-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="0c477-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="0c477-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="0c477-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="0c477-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="0c477-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="0c477-158">Deallocate memória de objeto previamente atribuída</span><span class="sxs-lookup"><span data-stu-id="0c477-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="0c477-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="0c477-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="0c477-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c477-160">Description</span></span>

<span data-ttu-id="0c477-161">***Este serviço foi depreciado porque já não é necessário.***</span><span class="sxs-lookup"><span data-stu-id="0c477-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="0c477-162">A memória que foi previamente atribuída através \***de txm_module_object_allocate**_ é transatada no\* serviço _ _tx_ \_ _delete\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="0c477-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c477-163">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c477-163">Input parameters</span></span>

- <span data-ttu-id="0c477-164">**object_ptr** Ponteiro de objeto para negociar.</span><span class="sxs-lookup"><span data-stu-id="0c477-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c477-165">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-165">Return values</span></span>

- <span data-ttu-id="0c477-166">**TX_SUCCESS** (0x00) Alocado objeto bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0c477-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c477-167">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-167">Allowed from</span></span>

<span data-ttu-id="0c477-168">Fios de módulos</span><span class="sxs-lookup"><span data-stu-id="0c477-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="0c477-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c477-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="0c477-170">Veja também</span><span class="sxs-lookup"><span data-stu-id="0c477-170">See also</span></span>

- <span data-ttu-id="0c477-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="0c477-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="0c477-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="0c477-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="0c477-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="0c477-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="0c477-174">Encontre objeto do sistema e recupere o ponteiro do objeto</span><span class="sxs-lookup"><span data-stu-id="0c477-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="0c477-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="0c477-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="0c477-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c477-176">Description</span></span>

<span data-ttu-id="0c477-177">Este serviço recupera o ponteiro de objetos de um tipo específico com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="0c477-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="0c477-178">Se o objeto não for encontrado, é devolvido um erro.</span><span class="sxs-lookup"><span data-stu-id="0c477-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="0c477-179">Caso contrário, se o objeto for encontrado, o endereço desse objeto é colocado em "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="0c477-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="0c477-180">Este ponteiro pode então ser utilizado para fazer chamadas de serviço do sistema, para interagir com o código residente e/ou outros módulos carregados no sistema.</span><span class="sxs-lookup"><span data-stu-id="0c477-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c477-181">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c477-181">Input parameters</span></span>

- <span data-ttu-id="0c477-182">**object_type** Tipo de objeto ThreadX solicitado.</span><span class="sxs-lookup"><span data-stu-id="0c477-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="0c477-183">Os tipos válidos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0c477-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="0c477-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="0c477-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="0c477-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="0c477-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="0c477-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="0c477-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="0c477-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="0c477-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="0c477-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="0c477-196">**nome** Nome do objeto específico da aplicação, tal como definido quando o objeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="0c477-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="0c477-197">**object_ptr** Destino para ponteiro de objetos.</span><span class="sxs-lookup"><span data-stu-id="0c477-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c477-198">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-198">Return values</span></span>

- <span data-ttu-id="0c477-199">**TX_SUCCESS** (0x00) Objeto bem sucedido obter.</span><span class="sxs-lookup"><span data-stu-id="0c477-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="0c477-200">**TX_OPTION_ERROR** (0x08) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="0c477-201">**TX_PTR_ERROR** (0x03) Destino inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="0c477-202">**TX_SIZE_ERROR** (0x05) Tamanho inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="0c477-203">**TX_NO_INSTANCE** (0x0D) Objeto não encontrado.</span><span class="sxs-lookup"><span data-stu-id="0c477-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c477-204">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-204">Allowed from</span></span>

<span data-ttu-id="0c477-205">Fios de módulos</span><span class="sxs-lookup"><span data-stu-id="0c477-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="0c477-206">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c477-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="0c477-207">Veja também</span><span class="sxs-lookup"><span data-stu-id="0c477-207">See also</span></span>

- <span data-ttu-id="0c477-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="0c477-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="0c477-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="0c477-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="0c477-210">Encontre objeto do sistema e recupere o ponteiro do objeto</span><span class="sxs-lookup"><span data-stu-id="0c477-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="0c477-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="0c477-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="0c477-212">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c477-212">Description</span></span>

<span data-ttu-id="0c477-213">Este serviço recupera o ponteiro de objetos de um tipo específico com um nome específico.</span><span class="sxs-lookup"><span data-stu-id="0c477-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="0c477-214">Se o objeto não for encontrado, é devolvido um erro.</span><span class="sxs-lookup"><span data-stu-id="0c477-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="0c477-215">Caso contrário, se o objeto for encontrado, o endereço desse objeto é colocado em "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="0c477-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="0c477-216">Este ponteiro pode então ser utilizado para fazer chamadas de serviço do sistema, para interagir com o código residente e/ou outros módulos carregados no sistema.</span><span class="sxs-lookup"><span data-stu-id="0c477-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0c477-217">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="0c477-217">Input parameters</span></span>

- <span data-ttu-id="0c477-218">**object_type** Tipo de objeto ThreadX solicitado.</span><span class="sxs-lookup"><span data-stu-id="0c477-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="0c477-219">Os tipos válidos são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0c477-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="0c477-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="0c477-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="0c477-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="0c477-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="0c477-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="0c477-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="0c477-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="0c477-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="0c477-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="0c477-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="0c477-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="0c477-232">**nome** Nome do objeto específico da aplicação, tal como definido quando o objeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="0c477-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="0c477-233">**name_length** Comprimento do nome.</span><span class="sxs-lookup"><span data-stu-id="0c477-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="0c477-234">**object_ptr** Destino para ponteiro de objetos.</span><span class="sxs-lookup"><span data-stu-id="0c477-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="0c477-235">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="0c477-235">Return values</span></span>

- <span data-ttu-id="0c477-236">**TX_SUCCESS** (0x00) Objeto bem sucedido obter.</span><span class="sxs-lookup"><span data-stu-id="0c477-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="0c477-237">**TX_OPTION_ERROR** (0x08) Tipo de objeto inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="0c477-238">**TX_PTR_ERROR** (0x03) Destino inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="0c477-239">**TX_SIZE_ERROR** (0x05) Tamanho inválido.</span><span class="sxs-lookup"><span data-stu-id="0c477-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="0c477-240">**TX_NO_INSTANCE** (0x0D) Objeto não encontrado.</span><span class="sxs-lookup"><span data-stu-id="0c477-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0c477-241">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0c477-241">Allowed from</span></span>

<span data-ttu-id="0c477-242">Fios de módulos</span><span class="sxs-lookup"><span data-stu-id="0c477-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="0c477-243">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c477-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="0c477-244">Veja também</span><span class="sxs-lookup"><span data-stu-id="0c477-244">See also</span></span>

- <span data-ttu-id="0c477-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="0c477-245">txm_module_manager_object_pointer_get</span></span>
