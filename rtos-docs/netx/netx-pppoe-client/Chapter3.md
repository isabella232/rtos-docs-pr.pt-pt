---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX PPPoE
description: Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NETX PPPoE (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825591"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="9ebe3-103">Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="9ebe3-104">Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NETX PPPoE (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="9ebe3-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="9ebe3-106">**nx_pppoe_client_create** *Criar uma instância de cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="9ebe3-107">**nx_pppoe_client_delete Eliminar** *uma instância do cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="9ebe3-108">**nx_pppoe_client_host_uniq_set** *Definir o anfitrião único para cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="9ebe3-109">**nx_pppoe_client_host_uniq_set_extended** *Definir o anfitrião único para cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="9ebe3-110">**nx_pppoe_client_service_name_set** *Definir o nome de serviço para ppPoe Cliente*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="9ebe3-111">**nx_pppoe_client_service_name_set_extended** *Definir o nome de serviço para cliente PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="9ebe3-112">**nx_pppoe_client_session_connect** *Conecte a sessão de clientes PPPoE ao PPPoE Server*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="9ebe3-113">**nx_pppoe_client_session_packet_send** *Enviar pacote de sessão PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="9ebe3-114">**nx_pppoe_client_session_terminate** *encerrar a sessão do PPPoE*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="9ebe3-115">**nx_pppoe_client_session_get** *Obtenha a sessão PPPoE especificada inf*</span><span class="sxs-lookup"><span data-stu-id="9ebe3-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="9ebe3-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="9ebe3-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="9ebe3-117">Criar uma instância ppPoE cliente</span><span class="sxs-lookup"><span data-stu-id="9ebe3-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="9ebe3-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-119">Description</span></span>

<span data-ttu-id="9ebe3-120">Este serviço cria uma instância ppPoE Client com o controlador de ligação fornecido pelo utilizador para a instância IP NetX especificada.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="9ebe3-121">Se o controlador de ligação não tiver sido inicializado e ativado, o software ppPoE Client é responsável por rubricar o controlador de ligação.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="9ebe3-122">Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância ppPoe Cliente para usar para alocação interna de pacotes.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-123">Geralmente uma boa ideia para criar o fio IP NetX com uma prioridade maior do que a prioridade do fio ppPoE Client.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="9ebe3-124">Consulte o serviço *nx_ip_create* para obter mais informações sobre a especificação da prioridade do fio IP.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-125">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-125">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-126">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-127">**nome** Nome desta instância ppPoe Cliente.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="9ebe3-128">**ip_ptr** Ponteiro para bloquear por exemplo IP.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="9ebe3-129">**interface_index** Índice de interface.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="9ebe3-130">**pool_ptr** Ponteiro para a piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="9ebe3-131">**stack_ptr** Ponteiro para o início da área de pilha do ppPoE Client thread.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="9ebe3-132">**stack_size** Tamanho em bytes na pilha do fio.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="9ebe3-133">**prioridade** Prioridade das linhas internas do Cliente PPPoE (1-31).</span><span class="sxs-lookup"><span data-stu-id="9ebe3-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="9ebe3-134">**pppoe_link_driver** Controlador de ligação fornecido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="9ebe3-135">**pppoe_packet_receive** Função de receção do pacote fornecido pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-136">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-136">Return Values</span></span>

 - <span data-ttu-id="9ebe3-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="9ebe3-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Cliente PPPoE inválido, IP, piscina de pacotes ou ponteiro de pilha.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="9ebe3-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Interface inválida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="9ebe3-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Tamanho de carga útil inválido da piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="9ebe3-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Tamanho da memória inválida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="9ebe3-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Prioridade inválida da linha ppPoe Client.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-143">Allowed From</span></span>

<span data-ttu-id="9ebe3-144">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="9ebe3-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="9ebe3-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="9ebe3-147">Excluir uma instância do cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="9ebe3-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-149">Description</span></span>

<span data-ttu-id="9ebe3-150">Este serviço elimina a instância do Cliente PPPoE anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-151">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-151">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-152">**pppoe_client_ptr** Ponteiro para bloco de controlo do cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-153">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-153">Return Values</span></span>

 - <span data-ttu-id="9ebe3-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="9ebe3-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-156">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-156">Allowed From</span></span>

<span data-ttu-id="9ebe3-157">Fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="9ebe3-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="9ebe3-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="9ebe3-160">Conjunto PPPoE Cliente anfitrião único</span><span class="sxs-lookup"><span data-stu-id="9ebe3-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="9ebe3-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-162">Description</span></span>

<span data-ttu-id="9ebe3-163">Este serviço define o anfitrião ppPoE Client único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="9ebe3-164">Host-Uniq é usado por um anfitrião para associar exclusivamente um Concentrador de Acesso a um determinado pedido de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="9ebe3-165">Podem ser dados binários de qualquer valor e comprimento que o Anfitrião escolha.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-166">hospedeiro único deve ser cadeia sem fim.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-167">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-167">This service is deprecated.</span></span> <span data-ttu-id="9ebe3-168">Os desenvolvedores são encorajados a migrar para *nx_pppoe_client_host_uniq_set_extended()*.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-169">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-169">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-170">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-171">**host_uniq** Ponteiro para um hospedeiro único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="9ebe3-172">Hospedeiro único deve ser corda sem fim.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-173">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-173">Return Values</span></span>

 - <span data-ttu-id="9ebe3-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido hospeda conjunto único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="9ebe3-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-176">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-176">Allowed From</span></span>

<span data-ttu-id="9ebe3-177">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="9ebe3-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="9ebe3-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="9ebe3-180">Conjunto PPPoE Cliente anfitrião único</span><span class="sxs-lookup"><span data-stu-id="9ebe3-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="9ebe3-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-182">Description</span></span>

<span data-ttu-id="9ebe3-183">Este serviço define o anfitrião ppPoE Client único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="9ebe3-184">Host-Uniq é usado por um anfitrião para associar exclusivamente um Concentrador de Acesso a um determinado pedido de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="9ebe3-185">Podem ser dados binários de qualquer valor e comprimento que o Anfitrião escolha.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-186">hospedeiro único deve ser cadeia sem fim.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-187">Este serviço substitui *nx_pppoe_client_host_uniq_set()*.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="9ebe3-188">Esta versão fornece informações adicionais de comprimento ao serviço.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-189">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-189">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-190">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-191">**host_uniq** Ponteiro para um hospedeiro único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="9ebe3-192">Hospedeiro único deve ser corda sem fim.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="9ebe3-193">**host_uniq_length** Comprimento de host_uniq</span><span class="sxs-lookup"><span data-stu-id="9ebe3-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-194">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-194">Return Values</span></span>

 - <span data-ttu-id="9ebe3-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Cliente PPPoE bem sucedido hospeda conjunto único.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="9ebe3-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="9ebe3-197">**NX_SIZE_ERROR** (0x09) Verifique host_uniq_length falhar</span><span class="sxs-lookup"><span data-stu-id="9ebe3-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-198">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-198">Allowed From</span></span>

<span data-ttu-id="9ebe3-199">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-200">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="9ebe3-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="9ebe3-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="9ebe3-202">Definir nome de serviço do cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-203">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="9ebe3-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-204">Description</span></span>

<span data-ttu-id="9ebe3-205">Este serviço define o nome de serviço ppPoE Cliente.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="9ebe3-206">O Service-Name indicando o serviço que o Anfitrião está a solicitar.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="9ebe3-207">Se Service-Name não estiver definido, indicando que o Host aceitará qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-208">nome de serviço deve ser cadeia sem efeito</span><span class="sxs-lookup"><span data-stu-id="9ebe3-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-209">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-209">This service is deprecated.</span></span> <span data-ttu-id="9ebe3-210">Os desenvolvedores são encorajados a migrar para *nx_pppoe_client_service_name_set_extended()*.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-211">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-211">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-212">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-213">**service_name** Ponteiro para um nome de serviço.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="9ebe3-214">O nome de serviço deve ser a corda terminada sem efeito.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-215">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-215">Return Values</span></span>

 - <span data-ttu-id="9ebe3-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Conjunto de nomes de serviço pppoe bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="9ebe3-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-218">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-218">Allowed From</span></span>

<span data-ttu-id="9ebe3-219">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-220">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="9ebe3-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="9ebe3-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="9ebe3-222">Definir nome de serviço do cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="9ebe3-224">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-224">Description</span></span>

<span data-ttu-id="9ebe3-225">Este serviço define o nome de serviço ppPoE Cliente.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="9ebe3-226">O Service-Name indicando o serviço que o Anfitrião está a solicitar.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="9ebe3-227">Se Service-Name não estiver definido, indicando que o Host aceitará qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-228">o nome de serviço deve ser cadeia sem efeito.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-229">Este serviço substitui *nx_pppoe_client_service_name_set()*.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="9ebe3-230">Esta versão fornece informações adicionais sobre o comprimento do nome de serviço para a função.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-231">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-231">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-232">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-233">**service_name** Ponteiro para um nome de serviço.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="9ebe3-234">O nome de serviço deve ser a corda terminada sem efeito.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="9ebe3-235">**service_name_length** Comprimento de service_name</span><span class="sxs-lookup"><span data-stu-id="9ebe3-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-236">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-236">Return Values</span></span>

 - <span data-ttu-id="9ebe3-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Conjunto de nomes de serviço pppoe bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="9ebe3-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="9ebe3-239">**NX_SIZE_ERROR** (0x09) Verifique service_name_length falhar</span><span class="sxs-lookup"><span data-stu-id="9ebe3-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-240">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-240">Allowed From</span></span>

<span data-ttu-id="9ebe3-241">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-242">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="9ebe3-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="9ebe3-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="9ebe3-244">Conecte a sessão do cliente PPPoE</span><span class="sxs-lookup"><span data-stu-id="9ebe3-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9ebe3-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-246">Description</span></span>

<span data-ttu-id="9ebe3-247">Este serviço faz a ligação de sessão PPPoE utilizando um Cliente PPPoE previamente criado para o Servidor PPPoE especificado.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="9ebe3-248">Esta função deve ser chamada após *nx_pppoe_client_create,* *nx_pppoe_client_host_uniq_set* e *nx_pppoe_client_service_name_set*.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-249">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-249">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-250">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-251">**wait_option** Opção de espera enquanto a ligação está a ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-252">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-252">Return Values</span></span>

 - <span data-ttu-id="9ebe3-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) sessão de clientes PPPoE bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="9ebe3-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-255">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-255">Allowed From</span></span>

<span data-ttu-id="9ebe3-256">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-257">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="9ebe3-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="9ebe3-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="9ebe3-259">Envie o pacote do Cliente PPPoE para sessão especificada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-260">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="9ebe3-261">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-261">Description</span></span>

<span data-ttu-id="9ebe3-262">Este serviço envia o pacote PPPoE utilizando o ID de sessão especificado.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-263">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-263">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-264">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-265">**packet_ptr** Ponteiro para pacote PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-266">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-266">Return Values</span></span>

 - <span data-ttu-id="9ebe3-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) pacote de cliente PPPoE bem sucedido enviar.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="9ebe3-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="9ebe3-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Pacote de Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="9ebe3-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-271">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-271">Allowed From</span></span>

<span data-ttu-id="9ebe3-272">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-273">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="9ebe3-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="9ebe3-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="9ebe3-275">Sessão de clientes PPPoE encerrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="9ebe3-277">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-277">Description</span></span>

<span data-ttu-id="9ebe3-278">Este serviço termina a sessão PPPoE especificada.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-279">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-279">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-280">**pppoe_client_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-281">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-281">Return Values</span></span>

 - <span data-ttu-id="9ebe3-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Sessão de clientes PPPoE bem sucedida termina.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="9ebe3-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-284">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-284">Allowed From</span></span>

<span data-ttu-id="9ebe3-285">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-286">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="9ebe3-287">nx_pppoe_client_session_get</span><span class="sxs-lookup"><span data-stu-id="9ebe3-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="9ebe3-288">Obtenha as informações de sessão do PPPoE especificadas</span><span class="sxs-lookup"><span data-stu-id="9ebe3-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="9ebe3-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="9ebe3-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="9ebe3-290">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ebe3-290">Description</span></span>

<span data-ttu-id="9ebe3-291">Este serviço obtém as informações de sessão PPPoE especificadas, endereço físico do servidor e id de sessão.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9ebe3-292">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9ebe3-292">Input Parameters</span></span>

 - <span data-ttu-id="9ebe3-293">**pppoe_server_ptr** Ponteiro para o bloco de controlo do cliente PPPoE.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="9ebe3-294">**server_mac_msw** Endereço físico do endereço do servidor ponto MSW.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="9ebe3-295">**server_mac_lsw** Endereço físico do endereço do servidor ponto MSW.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="9ebe3-296">**session_id** Ponteiro de identificação de sessão.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="9ebe3-297">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9ebe3-297">Return Values</span></span>

 - <span data-ttu-id="9ebe3-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) sessão de clientes PPPoE bem sucedida obtém.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="9ebe3-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Ponteiro do Cliente PPPoE inválido.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="9ebe3-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) sessão ppPoE não está estabelecida.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9ebe3-301">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9ebe3-301">Allowed From</span></span>

<span data-ttu-id="9ebe3-302">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="9ebe3-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="9ebe3-303">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9ebe3-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
