---
title: Capítulo 3 - Descrição dos Serviços de Servidores Azure RTOS NetX PPPoE
description: Este capítulo contém uma descrição de todos os serviços do Azure RTOS NETX PPPoE Server (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826600"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="05fd3-103">Capítulo 3 - Descrição dos Serviços de Servidores Azure RTOS NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="05fd3-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="05fd3-104">Este capítulo contém uma descrição de todos os serviços do Azure RTOS NETX PPPoE Server (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="05fd3-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="05fd3-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="05fd3-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="05fd3-106">**nx_pppoe_server_create**: *Criar uma instância ppPoE Server*</span><span class="sxs-lookup"><span data-stu-id="05fd3-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="05fd3-107">**nx_pppoe_server_ac_name_set**: *Definir nome do concentrador de acesso*</span><span class="sxs-lookup"><span data-stu-id="05fd3-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="05fd3-108">**nx_pppoe_server_delete**: *Eliminar uma instância do servidor PPPoE*</span><span class="sxs-lookup"><span data-stu-id="05fd3-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="05fd3-109">**nx_pppoe_server_enable**: *Ativar os serviços do PPPoE Server*</span><span class="sxs-lookup"><span data-stu-id="05fd3-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="05fd3-110">**nx_pppoe_server_disable**: *Desativar os serviços do PPPoE Server*</span><span class="sxs-lookup"><span data-stu-id="05fd3-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="05fd3-111">**nx_pppoe_server_callback_notify_set**: *Definir as funções de chamada ppPoE Server notificam funções*</span><span class="sxs-lookup"><span data-stu-id="05fd3-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="05fd3-112">**nx_pppoe_server_service_name_set**: *Definir o nome do serviço ppPoE Server*</span><span class="sxs-lookup"><span data-stu-id="05fd3-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="05fd3-113">**nx_pppoe_server_session_send**: *Enviar dados do PPPoE Server para sessão especificada*</span><span class="sxs-lookup"><span data-stu-id="05fd3-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="05fd3-114">**nx_pppoe_server_session_packet_send**: *Enviar pacote ppPoE Server para sessão especificada*</span><span class="sxs-lookup"><span data-stu-id="05fd3-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="05fd3-115">**nx_pppoe_server_session_terminate**: *Terminar a sessão PPPoE especificada*</span><span class="sxs-lookup"><span data-stu-id="05fd3-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="05fd3-116">**nx_pppoe_server_session_get**: *Obtenha as informações de sessão especificadas*</span><span class="sxs-lookup"><span data-stu-id="05fd3-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="05fd3-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="05fd3-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="05fd3-118">Criar uma instância ppPoE Server</span><span class="sxs-lookup"><span data-stu-id="05fd3-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-119">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="05fd3-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-120">Description</span></span>

<span data-ttu-id="05fd3-121">Este serviço cria uma instância ppPoE Server com o controlador de ligação fornecido pelo utilizador para a instância IP netX especificada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="05fd3-122">Se o controlador de ligação não tiver sido inicializado e ativado, o software de corte PPPoE é responsável por rubricar o controlador de ligação.</span><span class="sxs-lookup"><span data-stu-id="05fd3-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="05fd3-123">Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância ppPoE Server para usar para alocação interna de pacotes.</span><span class="sxs-lookup"><span data-stu-id="05fd3-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="05fd3-124">Note que geralmente é uma boa ideia criar o fio IP NetX com uma prioridade maior do que a prioridade do fio PPPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="05fd3-125">Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.</span><span class="sxs-lookup"><span data-stu-id="05fd3-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-126">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-126">Input Parameters</span></span>

- <span data-ttu-id="05fd3-127">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-128">**nome**: Nome desta instância ppPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="05fd3-129">**ip_ptr**: Ponteiro para o bloco de controlo por exemplo IP.</span><span class="sxs-lookup"><span data-stu-id="05fd3-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="05fd3-130">**interface_index:** Índice de interface.</span><span class="sxs-lookup"><span data-stu-id="05fd3-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="05fd3-131">**pppoe_link_driver**: Controlador de ligação fornecido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="05fd3-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="05fd3-132">**pool_ptr**: Ponteiro para a piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="05fd3-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="05fd3-133">**stack_ptr**: Ponteiro para o início da área de pilha do ppPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="05fd3-134">**stack_size:** Tamanho dos bytes na pilha do fio.</span><span class="sxs-lookup"><span data-stu-id="05fd3-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="05fd3-135">**prioridade**: Prioridade das linhas internas do Servidor PPPoE (1-31).</span><span class="sxs-lookup"><span data-stu-id="05fd3-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-136">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-136">Return Values</span></span>

- <span data-ttu-id="05fd3-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="05fd3-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Inválido PPPoE Server, IP, pool de pacotes ou ponteiro de pilha.</span><span class="sxs-lookup"><span data-stu-id="05fd3-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="05fd3-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Interface inválida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="05fd3-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Tamanho de carga inválida do pacote.</span><span class="sxs-lookup"><span data-stu-id="05fd3-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="05fd3-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Tamanho da memória inválida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="05fd3-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Prioridade inválida da linha PPPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-143">Allowed From</span></span>

<span data-ttu-id="05fd3-144">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="05fd3-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="05fd3-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="05fd3-147">Excluir uma instância do Servidor PPPoE</span><span class="sxs-lookup"><span data-stu-id="05fd3-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="05fd3-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-149">Description</span></span>

<span data-ttu-id="05fd3-150">Este serviço elimina a instância do Servidor PPPoE anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-151">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-151">Input Parameters</span></span>

- <span data-ttu-id="05fd3-152">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-153">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-153">Return Values</span></span>

- <span data-ttu-id="05fd3-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-156">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-156">Allowed From</span></span>

<span data-ttu-id="05fd3-157">Fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="05fd3-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="05fd3-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="05fd3-160">Ativar o serviço PPPoE Server</span><span class="sxs-lookup"><span data-stu-id="05fd3-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="05fd3-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-162">Description</span></span>

<span data-ttu-id="05fd3-163">Este serviço permite os serviços ppPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="05fd3-164">Esta função deve ser chamada após *nx_pppoe_server_create* e *nx_pppoe_server_callback_notify_set*.</span><span class="sxs-lookup"><span data-stu-id="05fd3-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-165">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-165">Input Parameters</span></span>

- <span data-ttu-id="05fd3-166">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-167">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-167">Return Values</span></span>

- <span data-ttu-id="05fd3-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-170">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-170">Allowed From</span></span>

<span data-ttu-id="05fd3-171">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="05fd3-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="05fd3-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="05fd3-174">Desativar o serviço PPPoE Server</span><span class="sxs-lookup"><span data-stu-id="05fd3-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="05fd3-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-176">Description</span></span>

<span data-ttu-id="05fd3-177">Este serviço desativa os serviços ppPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-178">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-178">Input Parameters</span></span>

- <span data-ttu-id="05fd3-179">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-180">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-180">Return Values</span></span>

- <span data-ttu-id="05fd3-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-183">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-183">Allowed From</span></span>

<span data-ttu-id="05fd3-184">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="05fd3-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="05fd3-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="05fd3-187">Definir chamadas ppPoE Server notificam funções</span><span class="sxs-lookup"><span data-stu-id="05fd3-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="05fd3-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="05fd3-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-189">Description</span></span>

<span data-ttu-id="05fd3-190">Este serviço define as funções de chamada PPPoE Server notificam as funções.</span><span class="sxs-lookup"><span data-stu-id="05fd3-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="05fd3-191">Esta função deve ser chamada antes *nx_pppoe_server_enabl, e* o ponteiro de função pppoe_data_receive_notify deve ser definido, se não, *nx_pppoe_server_enable* será falha.</span><span class="sxs-lookup"><span data-stu-id="05fd3-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-192">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-192">Input Parameters</span></span>

- <span data-ttu-id="05fd3-193">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-194">**pppoe_discover_initiation_notify**: Função de aplicação que é chamada sempre que PPPoE descobre a mensagem de iniciação é recebida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="05fd3-195">Se este valor for NU, descubra que a função de retorno de iniciação está desativada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="05fd3-196">**pppoe_discover_request_notify**: Função de aplicação que é chamada sempre que PPPoE descobrir mensagem de pedido é recebida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="05fd3-197">Se este valor for NU, descubra que a função de retorno do pedido é desativada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="05fd3-198">**pppoe_discover_terminate_notify**: Função de aplicação que é chamada sempre que PPPoE descobre que a mensagem de terminação é recebida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="05fd3-199">Se este valor for NU, descubra que a função de retorno de terminação está desativada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="05fd3-200">**pppoe_discover_terminate_confirm**: Função de aplicação que é chamada sempre que PPPoE descobre que a mensagem de terminação é enviada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="05fd3-201">Se este valor for NU, descubra que a função de retorno de terminação está desativada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="05fd3-202">**pppoe_data_receive_notify**: Função de aplicação que é chamada sempre que a mensagem de dados PPPoE é recebida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="05fd3-203">Este valor não deve ser zero.</span><span class="sxs-lookup"><span data-stu-id="05fd3-203">This value must not be zero.</span></span>
- <span data-ttu-id="05fd3-204">**pppoe_data_send_notify**: Função de aplicação que é chamada sempre que a mensagem de dados PPPoE é enviada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="05fd3-205">Se este valor for NU, a função de retorno de envio de dados é desativada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-206">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-206">Return Values</span></span>

- <span data-ttu-id="05fd3-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro ou ponteiro de função do PpPoE Inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-209">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-209">Allowed From</span></span>

<span data-ttu-id="05fd3-210">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="05fd3-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="05fd3-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="05fd3-213">Definir nome do concentrador de acesso</span><span class="sxs-lookup"><span data-stu-id="05fd3-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-214">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="05fd3-215">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-215">Description</span></span>

<span data-ttu-id="05fd3-216">Esta função definiu a chamada de função do nome do concentrador de acesso.</span><span class="sxs-lookup"><span data-stu-id="05fd3-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="05fd3-217">A cadeia de ac_name deve ser terminada sem nulo e a duração de ac_name corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="05fd3-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-218">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-218">Input Parameters</span></span>

- <span data-ttu-id="05fd3-219">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-220">**ac_name**: Aceda ao nome do Concentrador.</span><span class="sxs-lookup"><span data-stu-id="05fd3-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="05fd3-221">**ac_name_length:** Comprimento de ac_ame.</span><span class="sxs-lookup"><span data-stu-id="05fd3-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-222">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-222">Return Values</span></span>

- <span data-ttu-id="05fd3-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Conjunto de servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="05fd3-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Inválido PPPoE Server, IP, pool de pacotes ou ponteiro de pilha.</span><span class="sxs-lookup"><span data-stu-id="05fd3-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="05fd3-225">**NX_SIZE_ERROR**: (0x09) Verifique name_length falha.</span><span class="sxs-lookup"><span data-stu-id="05fd3-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-226">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-226">Allowed From</span></span>

<span data-ttu-id="05fd3-227">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-228">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="05fd3-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="05fd3-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="05fd3-230">Definir nome de serviço do servidor PPPoE</span><span class="sxs-lookup"><span data-stu-id="05fd3-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="05fd3-232">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-232">Description</span></span>

<span data-ttu-id="05fd3-233">Este serviço define o nome de serviço ppPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-234">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-234">Input Parameters</span></span>

- <span data-ttu-id="05fd3-235">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-236">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-236">Return Values</span></span>

- <span data-ttu-id="05fd3-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-239">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-239">Allowed From</span></span>

<span data-ttu-id="05fd3-240">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-241">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="05fd3-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="05fd3-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="05fd3-243">Enviar dados do PPPoE Server para sessão especificada</span><span class="sxs-lookup"><span data-stu-id="05fd3-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-244">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="05fd3-245">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-245">Description</span></span>

<span data-ttu-id="05fd3-246">Este serviço envia quadro PPPoE usando o ID de sessão especificado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-247">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-247">Input Parameters</span></span>

- <span data-ttu-id="05fd3-248">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-249">**session_index**: O índice da sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="05fd3-250">**data_ptr**: Ponteiro para o início do quadro de dados do PPPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="05fd3-251">**data_length**: Duração do quadro de dados do PPPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-252">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-252">Return Values</span></span>

- <span data-ttu-id="05fd3-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="05fd3-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="05fd3-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="05fd3-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-258">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-258">Allowed From</span></span>

<span data-ttu-id="05fd3-259">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-260">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="05fd3-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="05fd3-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="05fd3-262">Envie o pacote do PPPoE Server para sessão especificada</span><span class="sxs-lookup"><span data-stu-id="05fd3-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-263">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="05fd3-264">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-264">Description</span></span>

<span data-ttu-id="05fd3-265">Este serviço envia o pacote PPPoE utilizando o ID de sessão especificado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-266">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-266">Input Parameters</span></span>

- <span data-ttu-id="05fd3-267">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-268">**session_index**: O índice da sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="05fd3-269">**packet_ptr**: Ponteiro para pacote PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-270">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-270">Return Values</span></span>

- <span data-ttu-id="05fd3-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="05fd3-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Pacote inválido do PPPoE Server.</span><span class="sxs-lookup"><span data-stu-id="05fd3-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="05fd3-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="05fd3-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="05fd3-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-277">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-277">Allowed From</span></span>

<span data-ttu-id="05fd3-278">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-279">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="05fd3-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="05fd3-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="05fd3-281">Termine a sessão PPPoE especificada</span><span class="sxs-lookup"><span data-stu-id="05fd3-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-282">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="05fd3-283">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-283">Description</span></span>

<span data-ttu-id="05fd3-284">Este serviço termina a sessão PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-285">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-285">Input Parameters</span></span>

- <span data-ttu-id="05fd3-286">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-287">**session_index**: O índice da sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-288">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-288">Return Values</span></span>

- <span data-ttu-id="05fd3-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="05fd3-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) o serviço PPPoE Server não está ativado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="05fd3-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="05fd3-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-294">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-294">Allowed From</span></span>

<span data-ttu-id="05fd3-295">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-296">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="05fd3-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="05fd3-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="05fd3-298">Obtenha as informações de sessão do PPPoE especificadas</span><span class="sxs-lookup"><span data-stu-id="05fd3-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-299">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="05fd3-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-300">Description</span></span>

<span data-ttu-id="05fd3-301">Este serviço obtém as informações de sessão PPPoE especificadas, endereço físico do cliente e id de sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-302">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-302">Input Parameters</span></span>

- <span data-ttu-id="05fd3-303">**pppoe_server_ptr**: Ponteiro para o bloco de controlo do servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="05fd3-304">**session_index**: O índice da sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="05fd3-305">**client_mac_msw**: Ponteiro MSW de endereço físico do cliente.</span><span class="sxs-lookup"><span data-stu-id="05fd3-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="05fd3-306">**client_mac_lsw**: Ponteiro MSW de endereço físico do cliente.</span><span class="sxs-lookup"><span data-stu-id="05fd3-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="05fd3-307">**session_id:** Ponteiro de identificação de sessão.</span><span class="sxs-lookup"><span data-stu-id="05fd3-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-308">Return Values</span></span>

- <span data-ttu-id="05fd3-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Servidor PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="05fd3-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Ponteiro do Servidor PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="05fd3-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Índice de sessão PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="05fd3-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="05fd3-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-313">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-313">Allowed From</span></span>

<span data-ttu-id="05fd3-314">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-315">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="05fd3-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="05fd3-316">PppInitInd</span></span>

<span data-ttu-id="05fd3-317">Configure o nome de serviço predefinido</span><span class="sxs-lookup"><span data-stu-id="05fd3-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="05fd3-319">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-319">Description</span></span>

<span data-ttu-id="05fd3-320">O software PPPoE exporá esta função para permitir que o software da TTP configuure o 'Nome de Serviço predefinido' que o PPPoE deve utilizar para filtrar os pedidos PADI de entrada.</span><span class="sxs-lookup"><span data-stu-id="05fd3-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="05fd3-321">O software PPPoE deve lembrar-se desta informação, e se um pacote PADI for recebido contendo um nome de serviço que corresponda, então deve chamar PppDiscoverReq.</span><span class="sxs-lookup"><span data-stu-id="05fd3-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-322">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-322">Input Parameters</span></span>

- <span data-ttu-id="05fd3-323">**comprimento**: Duração do nome de serviço predefinido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="05fd3-324">**aData**: Nome de serviço predefinido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-325">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-325">Return Values</span></span>

<span data-ttu-id="05fd3-326">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-327">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-327">Allowed From</span></span>

<span data-ttu-id="05fd3-328">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-329">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="05fd3-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="05fd3-330">PppDiscoverCnf</span></span>

<span data-ttu-id="05fd3-331">Defina o campo nome de serviço do pacote PADO</span><span class="sxs-lookup"><span data-stu-id="05fd3-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="05fd3-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-333">Description</span></span>

<span data-ttu-id="05fd3-334">O software PPPoE exporá esta função para permitir que o software da TTP defina o campo nome de serviço do pacote PADO.</span><span class="sxs-lookup"><span data-stu-id="05fd3-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="05fd3-335">O software PPPoE não deve enviar o PADO até que o PppDiscoverCnf seja chamado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="05fd3-336">O pacote PADO deve conter um nome de concentrador de acesso (utilizando o id de identificação de identificação 0x0102 de identificação de identificação definido no RFC2516), definido na inicialização do software PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="05fd3-337">Vários nomes de serviço podem ser passados numData, com cada nome a ser anulado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="05fd3-338">O carácter nulo é utilizado como separador para proporcionar a máxima flexibilidade no caso de outros comandos precisarem de ser transmitidos como parte do nome de serviço.</span><span class="sxs-lookup"><span data-stu-id="05fd3-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-339">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-339">Input Parameters</span></span>

- <span data-ttu-id="05fd3-340">**comprimento**: Duração do nome de serviço predefinido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="05fd3-341">**aData**: Nome de serviço predefinido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="05fd3-342">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-343">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-343">Return Values</span></span>

<span data-ttu-id="05fd3-344">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-345">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-345">Allowed From</span></span>

<span data-ttu-id="05fd3-346">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-347">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="05fd3-348">PppOpencnf</span><span class="sxs-lookup"><span data-stu-id="05fd3-348">PppOpenCnf</span></span>

<span data-ttu-id="05fd3-349">Aceitar ou rejeitar a sessão do PPPoE</span><span class="sxs-lookup"><span data-stu-id="05fd3-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-350">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="05fd3-351">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-351">Description</span></span>

<span data-ttu-id="05fd3-352">O software PPPoE exporá esta função para permitir que o software da TTP aceite ou rejeite a sessão PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="05fd3-353">Em resposta a isto, a stack PPPoE deve aceitar a ligação e atribuir um número único de PPPoE Session_ID número associado à interfaceHandle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-354">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-354">Input Parameters</span></span>

- <span data-ttu-id="05fd3-355">**aceitar:** NX_TRUE se a ligação for aceite.</span><span class="sxs-lookup"><span data-stu-id="05fd3-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="05fd3-356">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-357">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-357">Return Values</span></span>

<span data-ttu-id="05fd3-358">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-359">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-359">Allowed From</span></span>

<span data-ttu-id="05fd3-360">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-361">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="05fd3-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="05fd3-362">PppCloseInd</span></span>

<span data-ttu-id="05fd3-363">Fechar uma sessão ppPoE</span><span class="sxs-lookup"><span data-stu-id="05fd3-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="05fd3-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-365">Description</span></span>

<span data-ttu-id="05fd3-366">O software PPPoE exporá esta função para permitir que o software da TTP encerre uma sessão ppPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="05fd3-367">O software PPPoE indicará a cadeia de código causa na etiqueta Generic-Error (0x0203) na mensagem PADT</span><span class="sxs-lookup"><span data-stu-id="05fd3-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-368">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-368">Input Parameters</span></span>

- <span data-ttu-id="05fd3-369">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="05fd3-370">**causeCode**: Cadeia terminada nula para envio de informações sobre o motivo para fechar a ligação a partir do Servidor PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-371">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-371">Return Values</span></span>

<span data-ttu-id="05fd3-372">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-373">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-373">Allowed From</span></span>

<span data-ttu-id="05fd3-374">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-375">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="05fd3-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="05fd3-376">PppCloseCnf</span></span>

<span data-ttu-id="05fd3-377">Confirme que o cabo foi libertado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-378">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="05fd3-379">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-379">Description</span></span>

<span data-ttu-id="05fd3-380">O software PPPoE exporá esta função para permitir que o software da TTP confirme que o cabo foi libertado.</span><span class="sxs-lookup"><span data-stu-id="05fd3-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-381">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-381">Input Parameters</span></span>

- <span data-ttu-id="05fd3-382">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-383">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-383">Return Values</span></span>

<span data-ttu-id="05fd3-384">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-385">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-385">Allowed From</span></span>

<span data-ttu-id="05fd3-386">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-387">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="05fd3-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="05fd3-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="05fd3-389">Permitir que os dados de PPP anteriores sejam reconhecidos</span><span class="sxs-lookup"><span data-stu-id="05fd3-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-390">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="05fd3-391">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-391">Description</span></span>

<span data-ttu-id="05fd3-392">O software PPPoE exporá esta função para permitir que um PppTransmitDataReq anterior seja reconhecido.</span><span class="sxs-lookup"><span data-stu-id="05fd3-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="05fd3-393">Implica que o software da TTP está pronto para uma nova moldura de PPP do PPPoE.</span><span class="sxs-lookup"><span data-stu-id="05fd3-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-394">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-394">Input Parameters</span></span>

- <span data-ttu-id="05fd3-395">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="05fd3-396">**aData**: Ponter o tampão de dados de PPP que foi aceite.</span><span class="sxs-lookup"><span data-stu-id="05fd3-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="05fd3-397">**Packet_id:** Identificador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="05fd3-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-398">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-398">Return Values</span></span>

<span data-ttu-id="05fd3-399">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-400">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-400">Allowed From</span></span>

<span data-ttu-id="05fd3-401">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-402">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="05fd3-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="05fd3-403">PppReceiveDataInd</span></span>

<span data-ttu-id="05fd3-404">Receber dados da transmissão através do Ethernet</span><span class="sxs-lookup"><span data-stu-id="05fd3-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="05fd3-405">Prototype</span><span class="sxs-lookup"><span data-stu-id="05fd3-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="05fd3-406">Descrição</span><span class="sxs-lookup"><span data-stu-id="05fd3-406">Description</span></span>

<span data-ttu-id="05fd3-407">O software PPPoE irá expor esta função para receber dados para transmissão através do Ethernet</span><span class="sxs-lookup"><span data-stu-id="05fd3-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05fd3-408">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="05fd3-408">Input Parameters</span></span>

- <span data-ttu-id="05fd3-409">**interfaceHandle**: Interface handle.</span><span class="sxs-lookup"><span data-stu-id="05fd3-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="05fd3-410">**comprimento**: O número de bytes numData.</span><span class="sxs-lookup"><span data-stu-id="05fd3-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="05fd3-411">**aData**: Tampão de dados contendo o quadro de dados de PPP.</span><span class="sxs-lookup"><span data-stu-id="05fd3-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="05fd3-412">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="05fd3-412">Return Values</span></span>

<span data-ttu-id="05fd3-413">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="05fd3-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05fd3-414">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="05fd3-414">Allowed From</span></span>

<span data-ttu-id="05fd3-415">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="05fd3-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="05fd3-416">Exemplo</span><span class="sxs-lookup"><span data-stu-id="05fd3-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```