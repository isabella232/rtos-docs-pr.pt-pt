---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX AutoIP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX AutoIP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826846"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="73f64-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="73f64-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX AutoIP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="73f64-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="73f64-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="73f64-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="73f64-106">**nx_auto_ip_create**: *Criar instância autoIP*</span><span class="sxs-lookup"><span data-stu-id="73f64-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="73f64-107">**nx_auto_ip_delete**: *Eliminar instância autoIP*</span><span class="sxs-lookup"><span data-stu-id="73f64-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="73f64-108">**nx_auto_ip_get_address**: *Obtenha o endereço autoIP atual*</span><span class="sxs-lookup"><span data-stu-id="73f64-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="73f64-109">**nx_auto_ip_set_interface**: *Definir interface IP que necessite de um endereço AutoIP*</span><span class="sxs-lookup"><span data-stu-id="73f64-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="73f64-110">**nx_auto_ip_start**: *Iniciar o processamento do AutoIP*</span><span class="sxs-lookup"><span data-stu-id="73f64-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="73f64-111">**nx_auto_ip_stop**: *Parar o processamento de AutoIP*</span><span class="sxs-lookup"><span data-stu-id="73f64-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="73f64-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="73f64-112">nx_auto_ip_create</span></span>

<span data-ttu-id="73f64-113">Criar exemplo de AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="73f64-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-115">Description</span></span>

<span data-ttu-id="73f64-116">Este serviço cria uma instância AutoIP na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="73f64-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="73f64-117">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="73f64-118">**nome**: Nome da instância AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="73f64-119">**ip_ptr**: Indicação para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="73f64-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="73f64-120">**stack_ptr**: Ponteiro para a área da pilha de fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="73f64-121">**stack_size**: Tamanho da área da pilha de fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="73f64-122">**prioridade**: Prioridade da linha AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="73f64-123">Se o DHCP for utilizado, o fio DHCP deve ter uma prioridade maior do que o fio de instância IP e o fio AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-124">Return Values</span></span>

- <span data-ttu-id="73f64-125">**NX_SUCCESS**: (0x00) Criação autoIP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="73f64-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="73f64-126">**NX_AUTO_IP_ERROR**: (0xA00) O AutoIP cria erro.</span><span class="sxs-lookup"><span data-stu-id="73f64-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="73f64-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr ou ponteiro de pilha.</span><span class="sxs-lookup"><span data-stu-id="73f64-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="73f64-128">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-129">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-129">Allowed From</span></span>

<span data-ttu-id="73f64-130">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="73f64-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="73f64-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="73f64-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-132">See Also</span></span>

<span data-ttu-id="73f64-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="73f64-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="73f64-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="73f64-135">Apagar a instância AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="73f64-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-137">Description</span></span>

<span data-ttu-id="73f64-138">Este serviço elimina uma instância AutoIP previamente criada na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="73f64-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73f64-139">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="73f64-139">Input Parameters</span></span>

- <span data-ttu-id="73f64-140">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-141">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-141">Return Values</span></span>

- <span data-ttu-id="73f64-142">**NX_SUCCESS**: (0x00) Eliminar autoIP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="73f64-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="73f64-143">**NX_AUTO_IP_ERROR**: (0xA00) Erro de eliminação automática.</span><span class="sxs-lookup"><span data-stu-id="73f64-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="73f64-144">NX_PTR_ERROR (0x16): Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="73f64-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="73f64-145">NX_CALLER_ERROR (0x11): Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-146">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-146">Allowed From</span></span>

<span data-ttu-id="73f64-147">Fios</span><span class="sxs-lookup"><span data-stu-id="73f64-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="73f64-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="73f64-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-149">See Also</span></span>

<span data-ttu-id="73f64-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="73f64-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="73f64-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="73f64-152">Obtenha o endereço AutoIP atual</span><span class="sxs-lookup"><span data-stu-id="73f64-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-153">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="73f64-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-154">Description</span></span>

<span data-ttu-id="73f64-155">Este serviço recupera o endereço AutoIP atualmente configurado.</span><span class="sxs-lookup"><span data-stu-id="73f64-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="73f64-156">Se não houver um, é devolvido um endereço IP de 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="73f64-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73f64-157">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="73f64-157">Input Parameters</span></span>

- <span data-ttu-id="73f64-158">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="73f64-159">**local_ip_address**: Destino para endereço IP de devolução.</span><span class="sxs-lookup"><span data-stu-id="73f64-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-160">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-160">Return Values</span></span>

- <span data-ttu-id="73f64-161">**NX_SUCCESS**: (0x00) O endereço AutoIP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="73f64-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="73f64-162">**NX_AUTO_IP_NO_LOCAL:**(0xA01) Sem endereço AutoIP válido.</span><span class="sxs-lookup"><span data-stu-id="73f64-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="73f64-163">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="73f64-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="73f64-164">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-165">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-165">Allowed From</span></span>

<span data-ttu-id="73f64-166">Inicialização, Temporizadores, Fios, ISRs</span><span class="sxs-lookup"><span data-stu-id="73f64-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="73f64-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="73f64-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-168">See Also</span></span>

<span data-ttu-id="73f64-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="73f64-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="73f64-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="73f64-171">Definir interface de rede para AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-172">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="73f64-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-173">Description</span></span>

<span data-ttu-id="73f64-174">Este serviço define o índice para a interface de rede AutoIP irá sondar para um endereço IP de rede.</span><span class="sxs-lookup"><span data-stu-id="73f64-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="73f64-175">O padrão é zero (a interface de rede primária).</span><span class="sxs-lookup"><span data-stu-id="73f64-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="73f64-176">Apenas aplicável a dispositivos multihomed.</span><span class="sxs-lookup"><span data-stu-id="73f64-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73f64-177">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="73f64-177">Input Parameters</span></span>

- <span data-ttu-id="73f64-178">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="73f64-179">**interface_index**: Interface para sondar o endereço IP</span><span class="sxs-lookup"><span data-stu-id="73f64-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-180">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-180">Return Values</span></span>

- <span data-ttu-id="73f64-181">**NX_SUCCESS**: (0x00) conjunto de interface autoIP bem sucedido</span><span class="sxs-lookup"><span data-stu-id="73f64-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="73f64-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX:**(0xA02) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="73f64-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="73f64-183">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="73f64-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="73f64-184">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-185">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-185">Allowed From</span></span>

<span data-ttu-id="73f64-186">Inicialização, Temporizadores, Fios, ISRs</span><span class="sxs-lookup"><span data-stu-id="73f64-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="73f64-187">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="73f64-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-188">See Also</span></span>

<span data-ttu-id="73f64-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start nx_auto_ip_stop nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="73f64-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="73f64-190">nx_auto_ip_start</span></span>

<span data-ttu-id="73f64-191">Iniciar o processamento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="73f64-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-193">Description</span></span>

<span data-ttu-id="73f64-194">Este serviço inicia o protocolo AutoIP numa instância AutoIP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="73f64-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73f64-195">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="73f64-195">Input Parameters</span></span>

- <span data-ttu-id="73f64-196">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="73f64-197">**starting_local_address**: Endereço de partida autoIP opcional.</span><span class="sxs-lookup"><span data-stu-id="73f64-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="73f64-198">Um valor de IP_ADDRESS (0,0,0,0) especifica que deve ser derivado um endereço AutoIP aleatório.</span><span class="sxs-lookup"><span data-stu-id="73f64-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="73f64-199">Caso contrário, se for especificado um endereço AutoIP válido, o NetX AutoIP tenta atribuir esse endereço.</span><span class="sxs-lookup"><span data-stu-id="73f64-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-200">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-200">Return Values</span></span>

- <span data-ttu-id="73f64-201">**NX_SUCCESS**: (0x00) Arranque autoIP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="73f64-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="73f64-202">**NX_AUTO_IP_ERROR**: (0xA00) Erro de arranque autoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="73f64-203">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="73f64-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="73f64-204">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-205">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-205">Allowed From</span></span>

<span data-ttu-id="73f64-206">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="73f64-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="73f64-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="73f64-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-208">See Also</span></span>

<span data-ttu-id="73f64-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="73f64-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="73f64-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="73f64-211">Parar o processamento de AutoIP</span><span class="sxs-lookup"><span data-stu-id="73f64-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="73f64-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="73f64-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="73f64-213">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f64-213">Description</span></span>

<span data-ttu-id="73f64-214">Este serviço para o protocolo AutoIP numa instância autoIP previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="73f64-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="73f64-215">Este serviço é normalmente utilizado quando o endereço IP é alterado via DHCP ou manualmente para um endereço não AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="73f64-216">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="73f64-216">Input Parameters</span></span>

- <span data-ttu-id="73f64-217">**auto_ip_ptr**: Ponteiro para o bloco de controlo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="73f64-218">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="73f64-218">Return Values</span></span>

- <span data-ttu-id="73f64-219">**NX_SUCCESS:**(0x00) Paragem autoIP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="73f64-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="73f64-220">**NX_AUTO_IP_ERROR**: (0xA00) Erro de paragem autoIP.</span><span class="sxs-lookup"><span data-stu-id="73f64-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="73f64-221">NX_PTR_ERROR: (0x16) Ponteiro AutoIP inválido.</span><span class="sxs-lookup"><span data-stu-id="73f64-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="73f64-222">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="73f64-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="73f64-223">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="73f64-223">Allowed From</span></span>

<span data-ttu-id="73f64-224">Fios</span><span class="sxs-lookup"><span data-stu-id="73f64-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="73f64-225">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f64-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="73f64-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f64-226">See Also</span></span>

<span data-ttu-id="73f64-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="73f64-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>