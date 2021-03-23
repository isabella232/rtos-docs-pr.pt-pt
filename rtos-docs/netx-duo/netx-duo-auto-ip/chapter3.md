---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo AutoIP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo AutoIP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826167"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="54cc9-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="54cc9-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo AutoIP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="54cc9-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="54cc9-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="54cc9-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="54cc9-106">**nx_auto_ip_create**: *Criar instância autoIP*</span><span class="sxs-lookup"><span data-stu-id="54cc9-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="54cc9-107">**nx_auto_ip_delete**: *Eliminar instância autoIP*</span><span class="sxs-lookup"><span data-stu-id="54cc9-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="54cc9-108">**nx_auto_ip_get_address**: *Obtenha o endereço autoIP atual*</span><span class="sxs-lookup"><span data-stu-id="54cc9-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="54cc9-109">**nx_auto_ip_set_interface**: *Definir interface IP que necessite de um endereço AutoIP*</span><span class="sxs-lookup"><span data-stu-id="54cc9-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="54cc9-110">**nx_auto_ip_start**: *Iniciar o processamento do AutoIP*</span><span class="sxs-lookup"><span data-stu-id="54cc9-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="54cc9-111">**nx_auto_ip_stop**: *Parar o processamento de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="54cc9-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="54cc9-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="54cc9-112">nx_auto_ip_create</span></span>

<span data-ttu-id="54cc9-113">Criar exemplo de AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="54cc9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-115">Description</span></span>

<span data-ttu-id="54cc9-116">Este serviço cria uma instância AutoIP na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="54cc9-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-117">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-117">Input Parameters</span></span>

- <span data-ttu-id="54cc9-118">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="54cc9-119">**nome**: Nome da instância AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="54cc9-120">**ip_ptr**: Indicação para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="54cc9-121">**stack_ptr**: Ponteiro para a área da pilha de fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="54cc9-122">**stack_size**: Tamanho da área da pilha de fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="54cc9-123">**prioridade**: Prioridade da linha AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="54cc9-124">Se o DHCP for utilizado, o fio DHCP deve ter uma prioridade maior do que o fio de instância IP e o fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-125">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-125">Return Values</span></span>

- <span data-ttu-id="54cc9-126">**NX_SUCCESS**: (0x00) Criação autoIP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="54cc9-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="54cc9-127">**NX_AUTO_IP_ERROR**: (0xA00) O AutoIP cria erro.</span><span class="sxs-lookup"><span data-stu-id="54cc9-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="54cc9-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr ou ponteiro de pilha.</span><span class="sxs-lookup"><span data-stu-id="54cc9-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="54cc9-129">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-130">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-130">Allowed From</span></span>

<span data-ttu-id="54cc9-131">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="54cc9-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-133">See Also</span></span>

<span data-ttu-id="54cc9-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="54cc9-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="54cc9-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="54cc9-136">Apagar a instância AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="54cc9-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-138">Description</span></span>

<span data-ttu-id="54cc9-139">Este serviço elimina uma instância AutoIP previamente criada na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="54cc9-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-140">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-140">Input Parameters</span></span>

- <span data-ttu-id="54cc9-141">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-142">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-142">Return Values</span></span>

- <span data-ttu-id="54cc9-143">**NX_SUCCESS**: (0x00) Eliminar autoIP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="54cc9-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="54cc9-144">**NX_AUTO_IP_ERROR**: (0xA00) Erro de eliminação automática.</span><span class="sxs-lookup"><span data-stu-id="54cc9-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="54cc9-145">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="54cc9-146">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-147">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-147">Allowed From</span></span>

<span data-ttu-id="54cc9-148">Fios</span><span class="sxs-lookup"><span data-stu-id="54cc9-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-150">See Also</span></span>

<span data-ttu-id="54cc9-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="54cc9-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="54cc9-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="54cc9-153">Obtenha o endereço AutoIP atual</span><span class="sxs-lookup"><span data-stu-id="54cc9-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="54cc9-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-155">Description</span></span>

<span data-ttu-id="54cc9-156">Este serviço recupera o endereço AutoIP atualmente configurado.</span><span class="sxs-lookup"><span data-stu-id="54cc9-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="54cc9-157">Se não houver um, é devolvido um endereço IP de 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="54cc9-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-158">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-158">Input Parameters</span></span>

- <span data-ttu-id="54cc9-159">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="54cc9-160">**local_ip_address**: Destino para endereço IP de devolução.</span><span class="sxs-lookup"><span data-stu-id="54cc9-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-161">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-161">Return Values</span></span>

- <span data-ttu-id="54cc9-162">**NX_SUCCESS**: (0x00) O endereço AutoIP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="54cc9-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="54cc9-163">**NX_AUTO_IP_NO_LOCAL:**(0xA01) Sem endereço AutoIP válido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="54cc9-164">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="54cc9-165">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-166">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-166">Allowed From</span></span>

<span data-ttu-id="54cc9-167">Inicialização, Temporizadores, Fios, ISRs</span><span class="sxs-lookup"><span data-stu-id="54cc9-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-169">See Also</span></span>

<span data-ttu-id="54cc9-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="54cc9-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="54cc9-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="54cc9-172">Definir interface de rede para AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="54cc9-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-174">Description</span></span>

<span data-ttu-id="54cc9-175">Este serviço define o índice para a interface de rede AutoIP irá sondar para um endereço IP de rede.</span><span class="sxs-lookup"><span data-stu-id="54cc9-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="54cc9-176">O padrão é zero (a interface de rede primária).</span><span class="sxs-lookup"><span data-stu-id="54cc9-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="54cc9-177">Apenas aplicável a dispositivos multihomed.</span><span class="sxs-lookup"><span data-stu-id="54cc9-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-178">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-178">Input Parameters</span></span>

- <span data-ttu-id="54cc9-179">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="54cc9-180">**interface_index**: Interface para sondar o endereço IP</span><span class="sxs-lookup"><span data-stu-id="54cc9-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-181">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-181">Return Values</span></span>

- <span data-ttu-id="54cc9-182">**NX_SUCCESS**: (0x00) conjunto de interface autoIP bem sucedido</span><span class="sxs-lookup"><span data-stu-id="54cc9-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="54cc9-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX:**(0xA02) Interface de rede inválida NX_PTR_ERROR (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="54cc9-184">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-185">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-185">Allowed From</span></span>

<span data-ttu-id="54cc9-186">Inicialização, Temporizadores, Fios, ISRs</span><span class="sxs-lookup"><span data-stu-id="54cc9-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-187">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-188">See Also</span></span>

<span data-ttu-id="54cc9-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="54cc9-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="54cc9-190">nx_auto_ip_start</span></span>

<span data-ttu-id="54cc9-191">Iniciar o processamento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="54cc9-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-193">Description</span></span>

<span data-ttu-id="54cc9-194">Este serviço inicia o protocolo AutoIP numa instância AutoIP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="54cc9-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-195">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-195">Input Parameters</span></span>

- <span data-ttu-id="54cc9-196">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="54cc9-197">**starting_local_address**: Endereço de partida autoIP opcional.</span><span class="sxs-lookup"><span data-stu-id="54cc9-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="54cc9-198">Um valor de IP_ADDRESS (0,0,0,0) especifica que deve ser derivado um endereço AutoIP aleatório.</span><span class="sxs-lookup"><span data-stu-id="54cc9-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="54cc9-199">Caso contrário, se for especificado um endereço AutoIP válido, o NetX AutoIP tenta atribuir esse endereço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-200">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-200">Return Values</span></span>

- <span data-ttu-id="54cc9-201">**NX_SUCCESS**: (0x00) Arranque autoIP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="54cc9-202">**NX_AUTO_IP_ERROR**: (0xA00) Erro de arranque autoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="54cc9-203">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="54cc9-204">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-205">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-205">Allowed From</span></span>

<span data-ttu-id="54cc9-206">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="54cc9-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-208">See Also</span></span>

<span data-ttu-id="54cc9-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="54cc9-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="54cc9-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="54cc9-211">Parar o processamento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="54cc9-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="54cc9-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="54cc9-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="54cc9-213">Descrição</span><span class="sxs-lookup"><span data-stu-id="54cc9-213">Description</span></span>

<span data-ttu-id="54cc9-214">Este serviço para o protocolo AutoIP numa instância autoIP previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="54cc9-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="54cc9-215">Este serviço é normalmente utilizado quando o endereço IP é alterado via DHCP ou manualmente para um endereço não AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="54cc9-216">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="54cc9-216">Input Parameters</span></span>

- <span data-ttu-id="54cc9-217">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="54cc9-218">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="54cc9-218">Return Values</span></span>

- <span data-ttu-id="54cc9-219">**NX_SUCCESS:**(0x00) Paragem autoIP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="54cc9-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="54cc9-220">**NX_AUTO_IP_ERROR**: (0xA00) Erro de paragem autoIP.</span><span class="sxs-lookup"><span data-stu-id="54cc9-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="54cc9-221">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="54cc9-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="54cc9-222">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="54cc9-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="54cc9-223">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="54cc9-223">Allowed From</span></span>

<span data-ttu-id="54cc9-224">Fios</span><span class="sxs-lookup"><span data-stu-id="54cc9-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="54cc9-225">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54cc9-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="54cc9-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54cc9-226">See Also</span></span>

<span data-ttu-id="54cc9-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="54cc9-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>