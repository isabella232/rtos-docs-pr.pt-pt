---
title: Capítulo 4 - Descrição dos serviços mDNS
description: Este capítulo contém uma descrição de todos os serviços netX mDNS
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825916"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="398e4-103">Capítulo 4 - Descrição dos serviços mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="398e4-104">Este capítulo contém uma descrição de todos os serviços netX mDNS (listados abaixo).</span><span class="sxs-lookup"><span data-stu-id="398e4-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="398e4-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="398e4-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="398e4-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="398e4-106">nx_mdns_create</span></span>

<span data-ttu-id="398e4-107">Criar uma instância mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="398e4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-109">Description</span></span>

<span data-ttu-id="398e4-110">Este serviço cria uma instância mDNS sobre a instância IP específica e recursos associados.</span><span class="sxs-lookup"><span data-stu-id="398e4-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="398e4-111">Um fio também é criado para lidar com mensagens mDNS recebidas, para responder a consultas e para transmitir periodicamente mensagens de consulta.</span><span class="sxs-lookup"><span data-stu-id="398e4-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-112">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-112">Input Parameters</span></span>

- <span data-ttu-id="398e4-113">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-114">**ip_ptr** Ponteiro para a instância IP associada.</span><span class="sxs-lookup"><span data-stu-id="398e4-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="398e4-115">**packet_pool** Ponteiro para uma piscina de pacotes válido.</span><span class="sxs-lookup"><span data-stu-id="398e4-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="398e4-116">**prioridade** Prioridade da linha mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="398e4-117">**stack_ptr** Ponteiro para a área da pilha para o fio mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="398e4-118">**stack_size** Tamanho da área da pilha.</span><span class="sxs-lookup"><span data-stu-id="398e4-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="398e4-119">**host_name** Nome de anfitrião atribuído a este nó.</span><span class="sxs-lookup"><span data-stu-id="398e4-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="398e4-120">**local_service_cache** Espaço de armazenamento para serviços registados locais.</span><span class="sxs-lookup"><span data-stu-id="398e4-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="398e4-121">**local_service_cache_size** Tamanho da cache de serviço local.</span><span class="sxs-lookup"><span data-stu-id="398e4-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="398e4-122">**peer_service_cache** Espaço de armazenamento para informações de serviço recebidas</span><span class="sxs-lookup"><span data-stu-id="398e4-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="398e4-123">**peer_service_cache_size** Tamanho da cache de serviço de pares</span><span class="sxs-lookup"><span data-stu-id="398e4-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="398e4-124">**probing_notify** Função de retorno opcional invocada no final da operação de sondagem.</span><span class="sxs-lookup"><span data-stu-id="398e4-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="398e4-125">Notifica a aplicação se o nome de anfitrião (ao ativar o mDNS numa interface local), ou o nome de serviço (após registar um serviço) é único.</span><span class="sxs-lookup"><span data-stu-id="398e4-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-126">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-126">Return Values</span></span>

- <span data-ttu-id="398e4-127">**NX_SUCCESS** (0x00) criou com sucesso a instância mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-128">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-128">Allowed From</span></span>

<span data-ttu-id="398e4-129">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="398e4-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="398e4-131">nx_mdns_delete</span></span>

<span data-ttu-id="398e4-132">Eliminar uma instância mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-133">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-134">Description</span></span>

<span data-ttu-id="398e4-135">Este serviço elimina a instância mDNS e liberta os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="398e4-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-136">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-136">Input Parameters</span></span>

- <span data-ttu-id="398e4-137">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-138">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-138">Return Values</span></span>

- <span data-ttu-id="398e4-139">**NX_SUCCESS** (0x00) eliminou com sucesso a instância mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-140">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-140">Allowed From</span></span>

<span data-ttu-id="398e4-141">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="398e4-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="398e4-143">nx_mdns_enable</span></span>

<span data-ttu-id="398e4-144">Inicie o serviço mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-145">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="398e4-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-146">Description</span></span>

<span data-ttu-id="398e4-147">Esta API permite o serviço mDNS em interface física específica.</span><span class="sxs-lookup"><span data-stu-id="398e4-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="398e4-148">Uma vez que o serviço está ativado, o módulo mDNS sonda primeiro todos os seus nomes de serviço únicos na rede antes de responder às consultas recebidas na interface.</span><span class="sxs-lookup"><span data-stu-id="398e4-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-149">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-149">Input Parameters</span></span>

- <span data-ttu-id="398e4-150">**mdns_ptr** Ponteiro para o bloco de controlo de instância mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="398e4-151">**interface_index** Índice para a interface onde o serviço deve ser ativado</span><span class="sxs-lookup"><span data-stu-id="398e4-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-152">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-152">Return Values</span></span>

- <span data-ttu-id="398e4-153">**NX_SUCCESS** (0x00) ativou com sucesso o serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-154">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-154">Allowed From</span></span>

<span data-ttu-id="398e4-155">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="398e4-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="398e4-157">nx_mdns_disable</span></span>

<span data-ttu-id="398e4-158">Desativar o serviço mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="398e4-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-160">Description</span></span>

<span data-ttu-id="398e4-161">Esta API desativa o serviço mDNS na interface física específica.</span><span class="sxs-lookup"><span data-stu-id="398e4-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="398e4-162">Uma vez desativado o serviço, o mDNS envia mensagens de "adeus" para cada serviço local para a rede que está ligada à interface, para que os nós vizinhos sejam notificados.</span><span class="sxs-lookup"><span data-stu-id="398e4-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-163">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-163">Input Parameters</span></span>

- <span data-ttu-id="398e4-164">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-165">**interface_index** Índice para a interface onde o serviço deve ser desativado</span><span class="sxs-lookup"><span data-stu-id="398e4-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-166">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-166">Return Values</span></span>

- <span data-ttu-id="398e4-167">**NX_SUCCESS** (0x00) desativou com sucesso o serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-168">Allowed From</span></span>

<span data-ttu-id="398e4-169">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="398e4-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="398e4-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="398e4-172">Instala a função de notificação completa da cache mDNS</span><span class="sxs-lookup"><span data-stu-id="398e4-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="398e4-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-174">Description</span></span>

<span data-ttu-id="398e4-175">Este serviço instala uma função de retorno fornecida pelo utilizador, que é invocada quando a cache de serviço local ou a cache de serviço de pares ficam cheias.</span><span class="sxs-lookup"><span data-stu-id="398e4-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="398e4-176">Quando a cache de serviço estiver cheia, não pode ser adicionado mais mDNS Resource Record.</span><span class="sxs-lookup"><span data-stu-id="398e4-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="398e4-177">Note que a cache de serviço pode ficar cheia em resultado de fragmentação interna, quando os serviços com vários comprimentos de corda são adicionados e removidos.</span><span class="sxs-lookup"><span data-stu-id="398e4-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="398e4-178">Ao receber uma notificação completa de cache na cache de serviço de pares, a aplicação pode usar o serviço "*nx_mdns_service_cache_clear"* para apagar todas as entradas na cache de serviço de pares.</span><span class="sxs-lookup"><span data-stu-id="398e4-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-179">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-179">Input Parameters</span></span>

- <span data-ttu-id="398e4-180">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-181">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-181">Return Values</span></span>

- <span data-ttu-id="398e4-182">**NX_SUCCESS** (0x00) Instalou com sucesso a cache mDNS notificando a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="398e4-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-183">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-183">Allowed From</span></span>

<span data-ttu-id="398e4-184">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="398e4-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="398e4-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="398e4-187">Limpe a cache de serviço mDNS na função de notificação completa</span><span class="sxs-lookup"><span data-stu-id="398e4-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-189">Description</span></span>

<span data-ttu-id="398e4-190">Este serviço limpa uma cache de serviço fornecida pelo utilizador para notificar a função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="398e4-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-191">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-191">Input Parameters</span></span>

- <span data-ttu-id="398e4-192">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-193">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-193">Return Values</span></span>

- <span data-ttu-id="398e4-194">**NX_SUCCESS** (0x00) limpou com sucesso a cache de serviço mDNS notificando a função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="398e4-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-195">Allowed From</span></span>

<span data-ttu-id="398e4-196">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="398e4-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="398e4-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="398e4-199">Define o nome de domínio</span><span class="sxs-lookup"><span data-stu-id="398e4-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="398e4-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-201">Description</span></span>

<span data-ttu-id="398e4-202">Este serviço configura o nome de domínio local padrão.</span><span class="sxs-lookup"><span data-stu-id="398e4-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="398e4-203">Quando a instância mDNS é criada, o nome de domínio local predefinido é definido como ".local".</span><span class="sxs-lookup"><span data-stu-id="398e4-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="398e4-204">Esta API permite que uma aplicação substitua o nome de domínio local predefinido.</span><span class="sxs-lookup"><span data-stu-id="398e4-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-205">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-205">Input Parameters</span></span>

- <span data-ttu-id="398e4-206">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-207">**domain_name** O nome de domínio a ser usado.</span><span class="sxs-lookup"><span data-stu-id="398e4-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-208">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-208">Return Values</span></span>

- <span data-ttu-id="398e4-209">**NX_SUCCESS** (0x00) configuraram com sucesso o domínio local.</span><span class="sxs-lookup"><span data-stu-id="398e4-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-210">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-210">Allowed From</span></span>

<span data-ttu-id="398e4-211">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="398e4-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="398e4-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="398e4-214">Define os parâmetros de tempo para mensagens de anúncio de serviço</span><span class="sxs-lookup"><span data-stu-id="398e4-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-215">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="398e4-216">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-216">Description</span></span>

<span data-ttu-id="398e4-217">Este serviço reconfigura os parâmetros de tempo utilizados pelo mDNS ao enviar os anúncios de serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="398e4-218">O período de publicação começa a partir de *t* ticks e pode ser expandido telescopicamente com 2 para o poder do fator *k.*</span><span class="sxs-lookup"><span data-stu-id="398e4-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="398e4-219">O número de repetições por anúncio é *p,* o intervalo entre cada anúncio repetido é de tiques *de intervalo,* e o número de período de anúncio é max_time.</span><span class="sxs-lookup"><span data-stu-id="398e4-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="398e4-220">Por predefinição, o período inicial é definido para 1 segundo, com k = 1 (o período duplica cada vez), *p = 1* (sem repetição), retrans_interval = 0 (sem intervalo de tempo), period_interval = 0xFFFFFFFF (intervalo do período máximo) e max_time = 3 (número de publicidade).</span><span class="sxs-lookup"><span data-stu-id="398e4-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-221">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-221">Input Parameters</span></span>

- <span data-ttu-id="398e4-222">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-223">**t** Número de carraças para o período inicial.</span><span class="sxs-lookup"><span data-stu-id="398e4-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="398e4-224">O padrão é de 100 carrapatos por 1 segundo.</span><span class="sxs-lookup"><span data-stu-id="398e4-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="398e4-225">**p** Número de repetições.</span><span class="sxs-lookup"><span data-stu-id="398e4-225">**p** Number of repetitions.</span></span> <span data-ttu-id="398e4-226">O valor predefinido é 1.</span><span class="sxs-lookup"><span data-stu-id="398e4-226">Default value is 1.</span></span>
- <span data-ttu-id="398e4-227">**k** Fator telescópico.</span><span class="sxs-lookup"><span data-stu-id="398e4-227">**k** Telescopic factor.</span></span> <span data-ttu-id="398e4-228">O valor predefinido é 1.</span><span class="sxs-lookup"><span data-stu-id="398e4-228">Default value is 1.</span></span>
- <span data-ttu-id="398e4-229">**retrans_interval** Número de carraças para esperar antes de enviar mensagens de anúncio repetidas.</span><span class="sxs-lookup"><span data-stu-id="398e4-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="398e4-230">O valor predefinido é 0.</span><span class="sxs-lookup"><span data-stu-id="398e4-230">Default value is 0.</span></span>
- <span data-ttu-id="398e4-231">**period_interval** Número de tiques entre dois períodos de anúncio.</span><span class="sxs-lookup"><span data-stu-id="398e4-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="398e4-232">O valor predefinido é 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="398e4-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="398e4-233">**max_time** Número de período de anúncio a utilizar para o anúncio.</span><span class="sxs-lookup"><span data-stu-id="398e4-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="398e4-234">Após os *períodos de anúncio max_time,* não são enviadas mais mensagens de anúncio.</span><span class="sxs-lookup"><span data-stu-id="398e4-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="398e4-235">O valor predefinido é 3.</span><span class="sxs-lookup"><span data-stu-id="398e4-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-236">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-236">Return Values</span></span>

- <span data-ttu-id="398e4-237">**NX_SUCCESS** (0x00) define com sucesso os valores de tempo.</span><span class="sxs-lookup"><span data-stu-id="398e4-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-238">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-238">Allowed From</span></span>

<span data-ttu-id="398e4-239">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-240">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="398e4-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="398e4-241">nx_mdns_service_add</span></span>

<span data-ttu-id="398e4-242">Adicione um serviço local</span><span class="sxs-lookup"><span data-stu-id="398e4-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="398e4-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-244">Description</span></span>

<span data-ttu-id="398e4-245">Esta API regista um serviço oferecido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="398e4-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="398e4-246">Se a *bandeira is_unique* estiver definida, o mDNS sonda o nome de serviço para se certificar de que é único na rede local antes de começar a anunciar o serviço na rede.</span><span class="sxs-lookup"><span data-stu-id="398e4-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="398e4-247">*Exemplo* é a parte do caso do nome de serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="398e4-248">O *serviço* é a parte de serviço do nome de serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="398e4-249">Por exemplo, "_http._tcp" é um serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="398e4-250">Para descrever um serviço com subtipo, o chamador deve utilizar o parâmetro do *subtipo.*</span><span class="sxs-lookup"><span data-stu-id="398e4-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="398e4-251">Por exemplo, se o serviço pretendido for "_printer._sub._http._tcp", o campo de serviço é "_http._tcp:, e o campo de subtipo é "_printer".</span><span class="sxs-lookup"><span data-stu-id="398e4-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-252">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-252">Input Parameters</span></span>

- <span data-ttu-id="398e4-253">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-254">**exemplo** Ponteiro para o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="398e4-255">**serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo.</span><span class="sxs-lookup"><span data-stu-id="398e4-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="398e4-256">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="398e4-257">**prioridade** Prioridade de serviço</span><span class="sxs-lookup"><span data-stu-id="398e4-257">**priority** Service priority</span></span>
- <span data-ttu-id="398e4-258">**peso** Peso de serviço</span><span class="sxs-lookup"><span data-stu-id="398e4-258">**weight** Service weight</span></span>
- <span data-ttu-id="398e4-259">**porto** Número de porta TCP ou UDP que o serviço utiliza</span><span class="sxs-lookup"><span data-stu-id="398e4-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="398e4-260">**texto** Informações adicionais de texto</span><span class="sxs-lookup"><span data-stu-id="398e4-260">**text** Additional text information</span></span>
- <span data-ttu-id="398e4-261">**is_unique** Bandeira booleana indicando se o serviço é partilhado ou único.</span><span class="sxs-lookup"><span data-stu-id="398e4-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="398e4-262">Para serviços registados como únicos, o mDNS deve sondar o serviço na rede antes de começar a oferecê-lo.</span><span class="sxs-lookup"><span data-stu-id="398e4-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="398e4-263">**Interface_index** Interface física o serviço é oferecido através.</span><span class="sxs-lookup"><span data-stu-id="398e4-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="398e4-264">Para um serviço que é oferecido através de qualquer um dos serviços anexos, o valor *NX_MDNS_ALL_INTERFACES* é utilizado.</span><span class="sxs-lookup"><span data-stu-id="398e4-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-265">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-265">Return Values</span></span>

- <span data-ttu-id="398e4-266">**NX_SUCCESS** (0x00) registou com sucesso o serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-267">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-267">Allowed From</span></span>

<span data-ttu-id="398e4-268">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-269">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="398e4-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="398e4-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="398e4-271">Remover um serviço registado anterior</span><span class="sxs-lookup"><span data-stu-id="398e4-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-272">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="398e4-273">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-273">Description</span></span>

<span data-ttu-id="398e4-274">Esta API elimina um serviço registado anterior.</span><span class="sxs-lookup"><span data-stu-id="398e4-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="398e4-275">À medida que o serviço é apagado, as mensagens de "adeus" são enviadas para a rede local para que os nós vizinhos sejam notificados.</span><span class="sxs-lookup"><span data-stu-id="398e4-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-276">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-276">Input Parameters</span></span>

- <span data-ttu-id="398e4-277">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-278">**exemplo** Ponteiro para o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="398e4-279">**serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo.</span><span class="sxs-lookup"><span data-stu-id="398e4-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="398e4-280">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-281">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-281">Return Values</span></span>

- <span data-ttu-id="398e4-282">**NX_SUCCESS** (0x00) apagou com sucesso o serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-283">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-283">Allowed From</span></span>

<span data-ttu-id="398e4-284">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-285">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="398e4-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="398e4-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="398e4-287">Iniciar a descoberta de serviço de um tiro</span><span class="sxs-lookup"><span data-stu-id="398e4-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="398e4-289">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-289">Description</span></span>

<span data-ttu-id="398e4-290">Este serviço executa uma consulta mDNS de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="398e4-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="398e4-291">Se o serviço especificado for encontrado na cache de serviço por pares, a primeira instância é devolvida.</span><span class="sxs-lookup"><span data-stu-id="398e4-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="398e4-292">Se não forem encontrados serviços na cache de serviço de pares local, o módulo mDNS emite um comando de consulta e aguarda a resposta.</span><span class="sxs-lookup"><span data-stu-id="398e4-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="398e4-293">O serviço está bloqueado até que a primeira resposta seja recebida ou os tempos de consulta esgotados.</span><span class="sxs-lookup"><span data-stu-id="398e4-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-294">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-294">Input Parameters</span></span>

- <span data-ttu-id="398e4-295">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-296">**exemplo** Ponteiro para o nome da instância do serviço, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="398e4-297">**serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo.</span><span class="sxs-lookup"><span data-stu-id="398e4-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="398e4-298">o pedido deve especificar o tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-298">the application must specify the service type.</span></span>
- <span data-ttu-id="398e4-299">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="398e4-300">**service_ptr** O utilizador forneceu o ponteiro para NX_MDNS_SERVICE estrutura que armazena os resultados da consulta.</span><span class="sxs-lookup"><span data-stu-id="398e4-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="398e4-301">**wait_option** A quantidade de tempo, em carraças, para esperar por uma resposta.</span><span class="sxs-lookup"><span data-stu-id="398e4-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-302">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-302">Return Values</span></span>

- <span data-ttu-id="398e4-303">**NX_SUCCESS** (0x00) obteve com sucesso informações de serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-304">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-304">Allowed From</span></span>

<span data-ttu-id="398e4-305">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-306">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="398e4-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="398e4-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="398e4-308">Iniciar descoberta de serviço contínuo</span><span class="sxs-lookup"><span data-stu-id="398e4-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-309">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="398e4-310">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-310">Description</span></span>

<span data-ttu-id="398e4-311">Este serviço inicia uma consulta contínua.</span><span class="sxs-lookup"><span data-stu-id="398e4-311">This service starts a continuous query.</span></span> <span data-ttu-id="398e4-312">Note que o serviço regressa imediatamente.</span><span class="sxs-lookup"><span data-stu-id="398e4-312">Note that the service returns immediately.</span></span> <span data-ttu-id="398e4-313">Após a emissão de uma consulta contínua, a aplicação pode recuperar o registo de serviço utilizando o *nx_mdns_service_lookup* da API .</span><span class="sxs-lookup"><span data-stu-id="398e4-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="398e4-314">Para parar a consulta contínua, a aplicação pode utilizar a API *nx_mdns_service_query_stop*</span><span class="sxs-lookup"><span data-stu-id="398e4-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-315">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-315">Input Parameters</span></span>

- <span data-ttu-id="398e4-316">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-317">**exemplo** Ponteiro para o nome da instância do serviço, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="398e4-318">**serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="398e4-319">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-320">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-320">Return Values</span></span>

- <span data-ttu-id="398e4-321">**NX_SUCCESS** (0x00) Começou com sucesso a consulta.</span><span class="sxs-lookup"><span data-stu-id="398e4-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-322">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-322">Allowed From</span></span>

<span data-ttu-id="398e4-323">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-324">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="398e4-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="398e4-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="398e4-326">Cessar uma descoberta de serviço contínuo previamente emitida</span><span class="sxs-lookup"><span data-stu-id="398e4-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-327">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="398e4-328">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-328">Description</span></span>

<span data-ttu-id="398e4-329">Esta API encerra uma descoberta de serviço contínuo emitida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="398e4-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-330">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-330">Input Parameters</span></span>

- <span data-ttu-id="398e4-331">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-332">**exemplo** Ponteiro para o nome do serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="398e4-333">**serviço** Ponteiro para o tipo de serviço mDNS, informações de subtipo.</span><span class="sxs-lookup"><span data-stu-id="398e4-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="398e4-334">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-335">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-335">Return Values</span></span>

- <span data-ttu-id="398e4-336">**NX_SUCCESS** (0x00) parou com sucesso continua a consulta.</span><span class="sxs-lookup"><span data-stu-id="398e4-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-337">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-337">Allowed From</span></span>

<span data-ttu-id="398e4-338">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-339">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="398e4-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="398e4-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="398e4-341">Recupera o serviço a partir da cache de serviço de pares local</span><span class="sxs-lookup"><span data-stu-id="398e4-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-342">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-343">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-343">Description</span></span>

<span data-ttu-id="398e4-344">Este serviço procura serviços que correspondam ao nome da instância (se fornecido) e ao tipo de serviço na cache de serviço de pares local.</span><span class="sxs-lookup"><span data-stu-id="398e4-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="398e4-345">A aplicação iniciará a procura de serviço com *instance_index* definido para zero para o primeiro serviço na cache que corresponda à descrição.</span><span class="sxs-lookup"><span data-stu-id="398e4-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="398e4-346">A aplicação continuará a utilizar este serviço com um valor *instance_index* crescente para serviços adicionais encontrados na cache, até que o serviço *NX_NO_MORE_ENTRIES,* o que indica o fim da cache.</span><span class="sxs-lookup"><span data-stu-id="398e4-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-347">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-347">Input Parameters</span></span>

- <span data-ttu-id="398e4-348">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-349">**exemplo** Ponteiro para o nome da instância do serviço, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="398e4-350">**serviço** Ponteiro para o tipo de serviço mDNS, excluindo informações de subtipo, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="398e4-351">**subtipo** Ponteiro para a parte do subtipo do serviço mDNS, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="398e4-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="398e4-352">**Instance_index** Número de índice para o caso a ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="398e4-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="398e4-353">**service_ptr** O utilizador forneceu o ponteiro para NX_MDNS_SERVICE estrutura que armazena os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="398e4-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-354">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-354">Return Values</span></span>

- <span data-ttu-id="398e4-355">**NX_SUCCESS** (0x00) recuperou com sucesso o serviço</span><span class="sxs-lookup"><span data-stu-id="398e4-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="398e4-356">**NX_NO_MORE_ENTRIES** (0x17) Não se encontra nenhuma entrada de serviço no número de índice especificado.</span><span class="sxs-lookup"><span data-stu-id="398e4-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="398e4-357">Este código de erro indica o fim da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="398e4-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-358">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-358">Allowed From</span></span>

<span data-ttu-id="398e4-359">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-360">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="398e4-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="398e4-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="398e4-362">Configura um conjunto de ignoram o serviço</span><span class="sxs-lookup"><span data-stu-id="398e4-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="398e4-364">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-364">Description</span></span>

<span data-ttu-id="398e4-365">Esta API configura uma máscara para ignorar os serviços especificados pela *service_mask* bitmask.</span><span class="sxs-lookup"><span data-stu-id="398e4-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="398e4-366">O utilizador pode utilizar opcionalmente o service_mask para selecionar tipos de serviço que não deseja estar em cache.</span><span class="sxs-lookup"><span data-stu-id="398e4-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="398e4-367">Uma lista de serviços é definida na *tabela nx_mdns_service_types* em *nxd_mdns.c.*</span><span class="sxs-lookup"><span data-stu-id="398e4-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="398e4-368">A máscara correspondente do primeiro tipo de serviço em nx_mdns_service_types[] é 0x00000001, a máscara do segundo tipo de serviço é 0x00000002, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="398e4-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-369">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-369">Input Parameters</span></span>

- <span data-ttu-id="398e4-370">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-371">**service_mask** Tipos de serviço definidos pelo utilizador para ignorar.</span><span class="sxs-lookup"><span data-stu-id="398e4-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="398e4-372">A máscara é do tipo ULONG de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="398e4-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="398e4-373">Cada bit representa uma entrada no conjunto *de nx_mdns_service_types* definido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="398e4-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="398e4-374">Se um pouco estiver definido, o tipo de serviço correspondente especificado no *nx_mdns_service_type* matriz não será armazenado na cache de serviço de pares.</span><span class="sxs-lookup"><span data-stu-id="398e4-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-375">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-375">Return Values</span></span>

- <span data-ttu-id="398e4-376">**NX_SUCCESS** (0x00) define com sucesso a máscara de ignorar o serviço.</span><span class="sxs-lookup"><span data-stu-id="398e4-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-377">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-377">Allowed From</span></span>

<span data-ttu-id="398e4-378">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-379">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="398e4-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="398e4-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="398e4-381">Configura uma alteração de serviço notifica a função de retorno</span><span class="sxs-lookup"><span data-stu-id="398e4-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-382">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="398e4-383">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-383">Description</span></span>

<span data-ttu-id="398e4-384">Esta API configura uma alteração de serviço notificando a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="398e4-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="398e4-385">Esta função de retorno é invocada quando um serviço oferecido por outros nós na rede é adicionado, alterado ou já não está disponível.</span><span class="sxs-lookup"><span data-stu-id="398e4-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="398e4-386">O utilizador pode utilizar opcionalmente o service_mask para selecionar os tipos de serviço que pretende monitorizar.</span><span class="sxs-lookup"><span data-stu-id="398e4-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="398e4-387">Uma lista de serviços que estão a ser monitorizados está codificada na *tabela nx_mdns_service_types* em *nxd_mdns.c.*</span><span class="sxs-lookup"><span data-stu-id="398e4-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="398e4-388">A máscara correspondente do primeiro tipo de serviço em nx_mdns_service_types[] é 0x00000001, a máscara do segundo tipo de serviço é 0x00000002, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="398e4-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-389">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-389">Input Parameters</span></span>

- <span data-ttu-id="398e4-390">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-391">**service_mask** Tipos de serviço definidos pelo utilizador para monitorizar.</span><span class="sxs-lookup"><span data-stu-id="398e4-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="398e4-392">A máscara é do tipo ULONG de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="398e4-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="398e4-393">Cada bit representa uma entrada na matriz *nx_mdns_service_types.*</span><span class="sxs-lookup"><span data-stu-id="398e4-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="398e4-394">**service_change_notify** A função de retorno a invocar quando o serviço especificado for alterado.</span><span class="sxs-lookup"><span data-stu-id="398e4-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="398e4-395">A informação detalhada do serviço é devolvida na memória apontada por *service_ptr.*</span><span class="sxs-lookup"><span data-stu-id="398e4-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="398e4-396">Note que o conteúdo na memória é inválido após o regresso da função de chamada de notificação.</span><span class="sxs-lookup"><span data-stu-id="398e4-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-397">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-397">Return Values</span></span>

- <span data-ttu-id="398e4-398">**NX_SUCCESS** (0x00) instalou com sucesso a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="398e4-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-399">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-399">Allowed From</span></span>

<span data-ttu-id="398e4-400">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-401">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="398e4-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="398e4-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="398e4-403">Limpar a alteração de serviço notificar a função de retorno</span><span class="sxs-lookup"><span data-stu-id="398e4-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-405">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-405">Description</span></span>

<span data-ttu-id="398e4-406">Esta API limpa a alteração de serviço notificando a função de retorno e a .</span><span class="sxs-lookup"><span data-stu-id="398e4-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-407">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-407">Input Parameters</span></span>

- <span data-ttu-id="398e4-408">**mdns_ptr** Ponteiro para o bloco de controlo mDNS..</span><span class="sxs-lookup"><span data-stu-id="398e4-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-409">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-409">Return Values</span></span>

- <span data-ttu-id="398e4-410">**NX_SUCCESS** (0x00) limpou com sucesso a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="398e4-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-411">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-411">Allowed From</span></span>

<span data-ttu-id="398e4-412">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-413">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="398e4-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="398e4-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="398e4-415">Obtenha o endereço de anfitrião</span><span class="sxs-lookup"><span data-stu-id="398e4-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-416">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="398e4-417">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-417">Description</span></span>

<span data-ttu-id="398e4-418">Este serviço realiza uma consulta mDNS nos endereços IPv4 e IPv6 do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="398e4-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="398e4-419">Se o endereço do nome de anfitrião especificado for encontrado na cache de serviço de pares, o endereço é devolvido.</span><span class="sxs-lookup"><span data-stu-id="398e4-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="398e4-420">Se não for encontrado nenhum endereço na cache de serviço de pares, o módulo mDNS emite consultas de tipo A e AAAA e aguarda a resposta.</span><span class="sxs-lookup"><span data-stu-id="398e4-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="398e4-421">Esta API bloqueia até que uma resposta seja recebida ou os tempos de consulta saem.</span><span class="sxs-lookup"><span data-stu-id="398e4-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-422">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-422">Input Parameters</span></span>

- <span data-ttu-id="398e4-423">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="398e4-424">**host_name** Ponteiro para o nome de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="398e4-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="398e4-425">**ipv4_address** Ponteiro para um endereço alinhado de 4 byte para o espaço de armazenamento de endereços IPv4.</span><span class="sxs-lookup"><span data-stu-id="398e4-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="398e4-426">O utilizador atribuirá 4 bytes de espaço para o endereço IPv4.</span><span class="sxs-lookup"><span data-stu-id="398e4-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="398e4-427">NX_NULL endereço pode ser transmitido para esta API se a aplicação não precisar de recuperar o endereço IPv4.</span><span class="sxs-lookup"><span data-stu-id="398e4-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="398e4-428">**ipv6_address** Ponteiro para o endereço alinhado de 4 byte para o espaço de armazenamento de endereços IPv6.</span><span class="sxs-lookup"><span data-stu-id="398e4-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="398e4-429">O utilizador atribuirá 16 bytes de espaço para o endereço - IPv6.</span><span class="sxs-lookup"><span data-stu-id="398e4-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="398e4-430">NX_NULL endereço pode ser transmitido para esta API se a aplicação não precisar de recuperar o endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="398e4-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="398e4-431">**wait_option** A quantidade de tempo, em carraças, para esperar por uma resposta.</span><span class="sxs-lookup"><span data-stu-id="398e4-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-432">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-432">Return Values</span></span>

- <span data-ttu-id="398e4-433">**NX_SUCCESS** (0x00) obteve com sucesso o endereço de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="398e4-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-434">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-434">Allowed From</span></span>

<span data-ttu-id="398e4-435">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-436">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="398e4-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="398e4-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="398e4-438">Apagar todos os serviços locais</span><span class="sxs-lookup"><span data-stu-id="398e4-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-439">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-440">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-440">Description</span></span>

<span data-ttu-id="398e4-441">Este serviço limpa todas as entradas na cache de serviço local após o envio da mensagem de Adeus.</span><span class="sxs-lookup"><span data-stu-id="398e4-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-442">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-442">Input Parameters</span></span>

- <span data-ttu-id="398e4-443">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-444">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-444">Return Values</span></span>

- <span data-ttu-id="398e4-445">**NX_SUCCESS** (0x00) apagou com sucesso todas as entradas na cache.</span><span class="sxs-lookup"><span data-stu-id="398e4-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-446">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-446">Allowed From</span></span>

<span data-ttu-id="398e4-447">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-448">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="398e4-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="398e4-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="398e4-450">Apagar todos os serviços descobertos</span><span class="sxs-lookup"><span data-stu-id="398e4-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="398e4-451">Prototype</span><span class="sxs-lookup"><span data-stu-id="398e4-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="398e4-452">Descrição</span><span class="sxs-lookup"><span data-stu-id="398e4-452">Description</span></span>

<span data-ttu-id="398e4-453">Este serviço limpa todas as entradas na cache de serviço de pares.</span><span class="sxs-lookup"><span data-stu-id="398e4-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="398e4-454">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="398e4-454">Input Parameters</span></span>

- <span data-ttu-id="398e4-455">**mdns_ptr** Ponteiro para o bloco de controlo mDNS.</span><span class="sxs-lookup"><span data-stu-id="398e4-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="398e4-456">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="398e4-456">Return Values</span></span>

- <span data-ttu-id="398e4-457">**NX_SUCCESS** (0x00) apagou com sucesso todas as entradas na cache.</span><span class="sxs-lookup"><span data-stu-id="398e4-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="398e4-458">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="398e4-458">Allowed From</span></span>

<span data-ttu-id="398e4-459">Fios</span><span class="sxs-lookup"><span data-stu-id="398e4-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="398e4-460">Exemplo</span><span class="sxs-lookup"><span data-stu-id="398e4-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
