---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS NetX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825640"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="0ef0c-103">Capítulo 4 - Descrição dos Serviços Azure RTOS NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="0ef0c-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="0ef0c-105">Os nomes de serviço são projetados para que todos os serviços similares sejam agrupados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="0ef0c-106">Por exemplo, todos os serviços ARP são encontrados no início deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef0c-107">*Note que uma API de tomada de BSD-Compatible está disponível para código de aplicação legado que não pode tirar o máximo partido da API NetX de alto desempenho. Consulte o Apêndice D para obter mais informações sobre a API da tomada de BSD-Compatible.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="0ef0c-108">Na secção "Valores de Retorno" de cada descrição, os valores em **BOLD** não são afetados pela opção NX_DISABLE_ERROR_CHECKING utilizada para desativar a verificação de erros da API, enquanto os valores em não-negrito são completamente desativados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="0ef0c-109">As secções "Allowed From" indicam a partir da qual cada serviço NetX pode ser chamado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="0ef0c-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="0ef0c-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="0ef0c-111">Invalidar todas as entradas dinâmicas na cache ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-112">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-113">Description</span></span>

<span data-ttu-id="0ef0c-114">Este serviço invalida todas as entradas dinâmicas de ARP atualmente na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-115">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-115">Parameters</span></span>

- <span data-ttu-id="0ef0c-116">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-117">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-117">Return Values</span></span>

- <span data-ttu-id="0ef0c-118">**NX_SUCCESS** (0x00) Cache ARP bem sucedido invalida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="0ef0c-119">**NX_NOT_ENABLED** (0x14) ARP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-120">**NX_PTR_ERROR** (0x07) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-121">**NX_CALLER_ERROR** (0x11) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-122">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-122">Allowed From</span></span>

<span data-ttu-id="0ef0c-123">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-124">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-124">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-125">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-125">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-127">See Also</span></span>

- <span data-ttu-id="0ef0c-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-129">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="0ef0c-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="0ef0c-133">Definir entrada dinâmica ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-135">Description</span></span>

<span data-ttu-id="0ef0c-136">Este serviço atribui uma entrada dinâmica a partir da cache ARP e configura o IP especificado para o mapeamento de endereço físico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="0ef0c-137">Se for especificado um endereço físico zero, é enviado um pedido real de ARP para a rede, a fim de ter o endereço físico resolvido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="0ef0c-138">Note também que esta entrada será removida se o envelhecimento ARP estiver ativo ou se a cache ARP estiver esgotada e esta é a entrada ARP menos usada recentemente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-139">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-139">Parameters</span></span>

- <span data-ttu-id="0ef0c-140">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-141">**ip_address** Endereço IP para mapa.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="0ef0c-142">**physical_msw** Top 16 bits (47-32) do endereço físico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="0ef0c-143">**physical_lsw** Inferior 32 bits (31-0) do endereço físico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-144">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-144">Return Values</span></span>

- <span data-ttu-id="0ef0c-145">**NX_SUCCESS** (0x00) Conjunto de entrada dinâmica ARP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="0ef0c-146">**NX_NO_MORE_ENTRIES** (0x17) Não há mais entradas ARP disponíveis na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="0ef0c-147">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-148">**NX_PTR_ERROR** (0x07) Ponteiro de instância IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="0ef0c-149">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-150">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-151">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-151">Allowed From</span></span>

<span data-ttu-id="0ef0c-152">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-153">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-153">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-154">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-154">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-156">See Also</span></span>

- <span data-ttu-id="0ef0c-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="0ef0c-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="0ef0c-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="0ef0c-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-161">nx_arp_enable</span></span>

<span data-ttu-id="0ef0c-162">Ativa o Protocolo de Resolução de Endereços (ARP).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-163">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="0ef0c-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-164">Description</span></span>

<span data-ttu-id="0ef0c-165">Este serviço inicializa o componente ARP do NetX para a instância IP específica.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="0ef0c-166">A inicialização do ARP inclui a configuração da cache ARP e várias rotinas de processamento ARP necessárias para o envio e receção de mensagens ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-167">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-167">Parameters</span></span>

- <span data-ttu-id="0ef0c-168">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-169">**arp_cache_memory** Ponteiro para a área de memória para colocar cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="0ef0c-170">**arp_cache_size** Cada entrada ARP é de 52 bytes, o número total de entradas ARP é, portanto, o tamanho dividido por 52.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-171">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-171">Return Values</span></span>

- <span data-ttu-id="0ef0c-172">**NX_SUCCESS** (0x00) Ativar ARP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="0ef0c-173">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória cache.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="0ef0c-174">**NX_SIZE_ERROR** (0x09) A memória de cache ARP fornecida pelo utilizador é demasiado pequena.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="0ef0c-175">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-176">**NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-177">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-177">Allowed From</span></span>

<span data-ttu-id="0ef0c-178">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-179">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-179">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-180">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-180">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-181">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-182">See Also</span></span>

- <span data-ttu-id="0ef0c-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="0ef0c-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="0ef0c-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="0ef0c-188">Envie um pedido gratuito de ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-189">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-190">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-190">Description</span></span>

<span data-ttu-id="0ef0c-191">Este serviço passa por todas as interfaces físicas para transmitir pedidos ARP gratuitos, desde que o endereço IP da interface seja válido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="0ef0c-192">Se uma resposta ARP for posteriormente recebida, o manipulador de resposta fornecido é chamado para processar a resposta ao ARP gratuito.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-193">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-193">Parameters</span></span>

- <span data-ttu-id="0ef0c-194">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-195">**response_handler** Ponteiro para função de manuseamento de resposta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="0ef0c-196">Se NX_NULL for fornecida, as respostas são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-197">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-197">Return Values</span></span>

- <span data-ttu-id="0ef0c-198">**NX_SUCCESS** (0x00) Enviado gratuito gratuito.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="0ef0c-199">**NX_NO_PACKET** (0x01) Nenhum pacote disponível.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="0ef0c-200">**NX_NOT_ENABLED** (0x14) ARP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-201">**NX_IP_ADDRESS_ERROR** (0x21) O endereço IP atual é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="0ef0c-202">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-203">**NX_CALLER_ERROR** (0x11) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-204">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-204">Allowed From</span></span>

<span data-ttu-id="0ef0c-205">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-206">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-206">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-207">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-207">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-209">See Also</span></span>

- <span data-ttu-id="0ef0c-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="0ef0c-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="0ef0c-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="0ef0c-215">Localizar endereço de hardware físico dado um endereço IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-217">Description</span></span>

<span data-ttu-id="0ef0c-218">Este serviço tenta encontrar um endereço de hardware físico na cache ARP que esteja associado ao endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-219">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-219">Parameters</span></span>

- <span data-ttu-id="0ef0c-220">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-221">**ip_address** Endereço IP para procurar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="0ef0c-222">**physical_msw** Ponteiro para a variável para devolver os 16 bits superiores (47-32) do endereço físico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="0ef0c-223">**physical_lsw** Ponteiro para a variável para devolver os 32 bits inferiores (31-0) do endereço físico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-224">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-224">Return Values</span></span>

- <span data-ttu-id="0ef0c-225">**NX_SUCCESS** (0x00) Bem sucedido no endereço de hardware ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="0ef0c-226">**NX_ENTRY_NOT_FOUND** (0x16) O mapeamento não foi encontrado na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="0ef0c-227">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-228">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="0ef0c-229">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-230">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-231">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-231">Allowed From</span></span>

<span data-ttu-id="0ef0c-232">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-233">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-233">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-234">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-234">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-235">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-236">See Also</span></span>

- <span data-ttu-id="0ef0c-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="0ef0c-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-241">nx_arp_info_get</span></span>

<span data-ttu-id="0ef0c-242">Recuperar informações sobre atividades de ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-243">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="0ef0c-244">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-244">Description</span></span>

<span data-ttu-id="0ef0c-245">Este serviço obtém informações sobre as atividades ARP para a instância IP associada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="0ef0c-246">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-247">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-247">Parameters</span></span>

- <span data-ttu-id="0ef0c-248">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-249">**arp_requests_sent** Ponteiro para destino para o total de pedidos de ARP enviados a partir desta instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="0ef0c-250">**arp_requests_received** Ponteiro para destino para o total de pedidos de ARP recebidos da rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="0ef0c-251">**arp_responses_sent** Ponteiro para destino para o total de respostas ARP enviadas a partir desta instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="0ef0c-252">**arp_responses_received** Ponteiro para o destino para o total de respostas ARP recebidas da rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="0ef0c-253">**arp_dynamic_entries** Ponteiro para o destino para o número atual de entradas dinâmicas de ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="0ef0c-254">**arp_static_entries** Ponteiro para o destino para o número atual de entradas estáticas de ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="0ef0c-255">**arp_aged_entries** Ponteiro para o destino do número total de entradas ARP que envelheceram e se tornaram inválidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="0ef0c-256">**arp_invalid_messages** Ponteiro para o destino das mensagens ARP inválidas totais recebidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-257">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-257">Return Values</span></span>

- <span data-ttu-id="0ef0c-258">**NX_SUCCESS** (0x00) Recuperação de informações ARP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-259">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-260">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-261">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-262">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-262">Allowed From</span></span>

<span data-ttu-id="0ef0c-263">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-264">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-264">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-265">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-265">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-266">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-267">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-267">See Also</span></span>

- <span data-ttu-id="0ef0c-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-269">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="0ef0c-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="0ef0c-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="0ef0c-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="0ef0c-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="0ef0c-274">Localizar endereço IP dado um endereço físico</span><span class="sxs-lookup"><span data-stu-id="0ef0c-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-276">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-276">Description</span></span>

<span data-ttu-id="0ef0c-277">Este serviço tenta encontrar um endereço IP na cache ARP que esteja associado ao endereço físico fornecido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-278">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-278">Parameters</span></span>

- <span data-ttu-id="0ef0c-279">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-280">**ip_address** Ponteiro para devolver o endereço IP, se for encontrado um que tenha sido mapeado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="0ef0c-281">**physical_msw** Top 16 bits (47-32) do endereço físico para procurar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="0ef0c-282">**physical_lsw** Menos 32 bits (31-0) do endereço físico para procurar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-283">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-283">Return Values</span></span>

- <span data-ttu-id="0ef0c-284">**NX_SUCCESS** (0x00) Sucesso do endereço IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="0ef0c-285">**NX_ENTRY_NOT_FOUND** (0x16) O mapeamento não foi encontrado na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="0ef0c-286">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de memória.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="0ef0c-287">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-288">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-290">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-290">Allowed From</span></span>

<span data-ttu-id="0ef0c-291">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-292">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-292">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-293">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-293">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-294">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-295">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-295">See Also</span></span>

- <span data-ttu-id="0ef0c-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-297">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-298">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-299">nx_arp_static_entries_delete,nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="0ef0c-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="0ef0c-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="0ef0c-302">Eliminar todas as entradas estáticas de ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-303">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-304">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-304">Description</span></span>

<span data-ttu-id="0ef0c-305">Este serviço elimina todas as entradas estáticas na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-306">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-306">Parameters</span></span>

- <span data-ttu-id="0ef0c-307">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-308">Return Values</span></span>

- <span data-ttu-id="0ef0c-309">**NX_SUCCESS** (0x00) As entradas estáticas são eliminadas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="0ef0c-310">**NX_PTR_ERROR** (0x07) Ponteiro ip_ptr Inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="0ef0c-311">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-312">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-313">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-313">Allowed From</span></span>

<span data-ttu-id="0ef0c-314">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-315">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-315">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-316">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-316">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-317">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-318">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-318">See Also</span></span>

- <span data-ttu-id="0ef0c-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-320">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-321">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="0ef0c-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="0ef0c-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="0ef0c-325">Criar IP estático para mapeamento de hardware em cache ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-327">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-327">Description</span></span>

<span data-ttu-id="0ef0c-328">Este serviço cria um mapeamento de endereço ip-físico estático na cache ARP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="0ef0c-329">As entradas ARP estáticas não estão sujeitas a atualizações periódicas ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-330">Parameters</span></span>

- <span data-ttu-id="0ef0c-331">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-332">**ip_address** Endereço IP para mapa.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="0ef0c-333">**physical_msw** Top 16 bits (47-32) do endereço físico para mapear.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="0ef0c-334">**physical_lsw** Inferior 32 bits (31-0) do endereço físico para mapear.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-335">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-335">Return Values</span></span>

- <span data-ttu-id="0ef0c-336">**NX_SUCCESS** (0x00) Entrada estática bem sucedida da ARP cria.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="0ef0c-337">**NX_NO_MORE_ENTRIES** (0x17) Não há mais entradas ARP disponíveis na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="0ef0c-338">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-339">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-340">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-341">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-343">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-343">Allowed From</span></span>

<span data-ttu-id="0ef0c-344">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-345">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-345">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-346">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-346">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-347">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-348">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-348">See Also</span></span>

- <span data-ttu-id="0ef0c-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-350">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-351">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="0ef0c-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="0ef0c-355">Elimine IP estático para mapeamento de hardware em cache ARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-356">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-357">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-357">Description</span></span>

<span data-ttu-id="0ef0c-358">Este serviço encontra e elimina um mapeamento de endereço ip-físico previamente criado na cache ARP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-359">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-359">Parameters</span></span>

- <span data-ttu-id="0ef0c-360">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-361">**ip_address** Endereço IP que foi mapeado estáticamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="0ef0c-362">**physical_msw** Top 16 bits (47 - 32) do endereço físico que foi mapeado estáticamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="0ef0c-363">**physical_lsw** Inferior 32 bits (31 - 0) do endereço físico que foi mapeado estáticamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-364">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-364">Return Values</span></span>

- <span data-ttu-id="0ef0c-365">**NX_SUCCESS** (0x00) Entrada estática bem sucedida da ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="0ef0c-366">**NX_ENTRY_NOT_FOUND** (0x16) A entrada estática ARP não foi encontrada na cache ARP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="0ef0c-367">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-368">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-369">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-370">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw e physical_lsw são 0.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-372">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-372">Allowed From</span></span>

<span data-ttu-id="0ef0c-373">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-374">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-374">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-375">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-375">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-376">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-377">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-377">See Also</span></span>

- <span data-ttu-id="0ef0c-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="0ef0c-379">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="0ef0c-380">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="0ef0c-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="0ef0c-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="0ef0c-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-383">nx_icmp_enable</span></span>

<span data-ttu-id="0ef0c-384">Ativar o Protocolo de Mensagens de Controlo de Internet (ICMP)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-386">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-386">Description</span></span>

<span data-ttu-id="0ef0c-387">Este serviço permite o componente ICMP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="0ef0c-388">O componente ICMP é responsável pelo tratamento de mensagens de erro da Internet e pedidos e respostas de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-389">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-389">Parameters</span></span>

- <span data-ttu-id="0ef0c-390">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-391">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-391">Return Values</span></span>

- <span data-ttu-id="0ef0c-392">**NX_SUCCESS** (0x00) ICMP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="0ef0c-393">**NX_ALREADY_ENABLED** (0x15) ICMP já está habilitado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="0ef0c-394">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-395">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-396">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-396">Allowed From</span></span>

<span data-ttu-id="0ef0c-397">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-398">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-398">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-399">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-399">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-400">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-401">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-401">See Also</span></span>

- <span data-ttu-id="0ef0c-402">nx_icmp_info_get, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="0ef0c-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="0ef0c-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-403">nx_icmp_info_get</span></span>

<span data-ttu-id="0ef0c-404">Recuperar informações sobre atividades do ICMP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-405">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="0ef0c-406">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-406">Description</span></span>

<span data-ttu-id="0ef0c-407">Este serviço obtém informações sobre as atividades do ICMP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-408">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-409">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-409">Parameters</span></span>

- <span data-ttu-id="0ef0c-410">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-411">**pings_sent** Ponteiro para o destino para o número total de pings enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="0ef0c-412">**ping_timeouts** Ponteiro para o destino para o número total de intervalos de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="0ef0c-413">**ping_threads_suspended** Ponteiro para o destino do número total de fios suspensos em pedidos de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="0ef0c-414">**ping_responses_received** Ponteiro para a estinação do número total de respostas de ping recebidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="0ef0c-415">**icmp_checksum_errors** Ponteiro para o destino do número total de erros de verificação ICMP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="0ef0c-416">**icmp_unhandled_messages** Ponteiro para a estinação do número total de mensagens ICMP não manuseadas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-417">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-417">Return Values</span></span>

- <span data-ttu-id="0ef0c-418">**NX_SUCCESS** (0x00) Recuperação de informação bem sucedida do ICMP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-419">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-420">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-421">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-422">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-422">Allowed From</span></span>

<span data-ttu-id="0ef0c-423">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-424">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-424">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-425">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-425">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-426">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-427">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-427">See Also</span></span>

- <span data-ttu-id="0ef0c-428">nx_icmp_enable, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="0ef0c-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="0ef0c-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="0ef0c-429">nx_icmp_ping</span></span>

<span data-ttu-id="0ef0c-430">Enviar pedido de ping para endereço IP especificado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-432">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-432">Description</span></span>

<span data-ttu-id="0ef0c-433">Este serviço envia um pedido de ping para o endereço IP especificado e aguarda o tempo especificado para uma mensagem de resposta a ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="0ef0c-434">Se não for recebida qualquer resposta, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="0ef0c-435">Caso contrário, toda a mensagem de resposta é devolvida na variável apontada por response_ptr.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="0ef0c-436">*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido depois de já não ser necessário.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-437">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-437">Parameters</span></span>

- <span data-ttu-id="0ef0c-438">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-439">**ip_address** Endereço IP, em ordem de anfitrião byte, para ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="0ef0c-440">Ponteiro de dados para a área de dados para mensagem de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="0ef0c-441">**data_size** Número de bytes nos dados do ping</span><span class="sxs-lookup"><span data-stu-id="0ef0c-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="0ef0c-442">**response_ptr** Ponteiro para o ponteiro do pacote para devolver a mensagem de resposta do ping dentro</span><span class="sxs-lookup"><span data-stu-id="0ef0c-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="0ef0c-443">**wait_option** Define quanto tempo esperar por uma resposta de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="0ef0c-444">as opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="0ef0c-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="0ef0c-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="0ef0c-447">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-448">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-448">Return Values</span></span>

- <span data-ttu-id="0ef0c-449">**NX_SUCCESS** (0x00) Ping de sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="0ef0c-450">O ponteiro da mensagem de resposta foi colocado na variável apontada por response_ptr.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="0ef0c-451">**NX_NO_PACKET** (0x01) Incapaz de atribuir um pacote de pedido de ping.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="0ef0c-452">**NX_OVERFLOW** (0x03) Área de dados especificada excede o tamanho do pacote padrão para esta instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="0ef0c-453">**NX_NO_RESPONSE** (0x29) A IP solicitada não respondeu.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="0ef0c-454">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-455">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-456">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de resposta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="0ef0c-457">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-458">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-459">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-459">Allowed From</span></span>

<span data-ttu-id="0ef0c-460">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-461">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-461">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-462">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-462">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-463">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-464">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-464">See Also</span></span>

- <span data-ttu-id="0ef0c-465">nx_icmp_enable, nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="0ef0c-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-466">nx_igmp_enable</span></span>

<span data-ttu-id="0ef0c-467">Ativar o Protocolo de Gestão do Grupo de Internet (IGMP)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-468">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-469">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-469">Description</span></span>

<span data-ttu-id="0ef0c-470">Este serviço permite o componente IGMP na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="0ef0c-471">A componente IGMP é responsável por fornecer suporte para operações de gestão de grupos multicast IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-472">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-472">Parameters</span></span>

- <span data-ttu-id="0ef0c-473">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-474">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-474">Return Values</span></span>

- <span data-ttu-id="0ef0c-475">**NX_SUCCESS** (0x00) IGMP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="0ef0c-476">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-477">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-478">**NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-479">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-479">Allowed From</span></span>

<span data-ttu-id="0ef0c-480">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-481">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-481">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-482">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-482">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-483">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-484">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-484">See Also</span></span>

- <span data-ttu-id="0ef0c-485">nx_igmp_info_get,nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="0ef0c-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="0ef0c-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-488">nx_igmp_info_get</span></span>

<span data-ttu-id="0ef0c-489">Recuperar informações sobre atividades do IGMP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-490">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="0ef0c-491">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-491">Description</span></span>

<span data-ttu-id="0ef0c-492">Este serviço obtém informações sobre as atividades do IGMP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-493">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-494">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-494">Parameters</span></span>

- <span data-ttu-id="0ef0c-495">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-496">**igmp_reports_sent** Ponteiro para o destino para o número total de relatórios do ICMP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="0ef0c-497">**igmp_queries_received** Ponteiro para destino para o número total de consultas recebidas pelo router multicast.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="0ef0c-498">**igmp_checksum_errors** Ponteiro para o destino do número total de erros de verificação IGMP em pacotes de receção.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="0ef0c-499">**current_groups_joined** Ponteiro para o destino do número atual de grupos unidos através desta instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-500">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-500">Return Values</span></span>

- <span data-ttu-id="0ef0c-501">**NX_SUCCESS** (0x00) Recuperação de informações bem sucedidas do IGMP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-502">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-503">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-504">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-505">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-505">Allowed From</span></span>

<span data-ttu-id="0ef0c-506">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-507">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-507">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-508">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-508">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-509">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-510">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-510">See Also</span></span>

- <span data-ttu-id="0ef0c-511">nx_igmp_enable, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="0ef0c-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="0ef0c-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="0ef0c-515">Desativar o loopback IGMP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-516">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-517">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-517">Description</span></span>

<span data-ttu-id="0ef0c-518">Este serviço desativa o loopback IGMP para todos os grupos multicasts subsequentes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-519">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-519">Parameters</span></span>

- <span data-ttu-id="0ef0c-520">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-521">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-521">Return Values</span></span>
- <span data-ttu-id="0ef0c-522">**NX_SUCCESS** (0x00) Desativação de loopback IGMP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="0ef0c-523">**NX_NOT_ENABLED** (0x14) IGMP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-524">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-525">**NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-526">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-526">Allowed From</span></span>

<span data-ttu-id="0ef0c-527">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-528">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-528">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-529">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-529">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-530">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-531">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-531">See Also</span></span>

- <span data-ttu-id="0ef0c-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="0ef0c-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="0ef0c-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="0ef0c-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="0ef0c-536">Ativar o loopback IGMP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-537">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-538">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-538">Description</span></span>

<span data-ttu-id="0ef0c-539">Este serviço permite o loopback IGMP para todos os grupos multicasts subsequentes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-540">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-540">Parameters</span></span>

- <span data-ttu-id="0ef0c-541">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-542">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-542">Return Values</span></span>
- <span data-ttu-id="0ef0c-543">**NX_SUCCESS** (0x00) Desativação de loopback IGMP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="0ef0c-544">**NX_NOT_ENABLED** (0x14) IGMP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-545">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-546">**NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-547">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-547">Allowed From</span></span>

<span data-ttu-id="0ef0c-548">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-549">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-549">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-550">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-550">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-551">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-552">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-552">See Also</span></span>

- <span data-ttu-id="0ef0c-553">nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="0ef0c-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="0ef0c-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="0ef0c-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="0ef0c-557">Junte a instância IP a grupo multicast especificado através de uma interface</span><span class="sxs-lookup"><span data-stu-id="0ef0c-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="0ef0c-559">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-559">Description</span></span>

<span data-ttu-id="0ef0c-560">Este serviço junta-se a uma instância IP ao grupo multicast especificado através de uma interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="0ef0c-561">Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="0ef0c-562">Depois de se juntar ao grupo multicast, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo através da interface de rede especificada e também reportará aos routers que este IP é membro deste grupo multicast.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="0ef0c-563">A adesão ao IGMP junta-se, reporta e deixa as mensagens também são enviadas através da interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-564">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-564">Parameters</span></span>

- <span data-ttu-id="0ef0c-565">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-566">**group_address** Endereço de grupo multicast classe D IP para se juntar na ordem byte de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="0ef0c-567">**interface_index** Índice da Interface ligado à instância NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-568">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-568">Return Values</span></span>

- <span data-ttu-id="0ef0c-569">**NX_SUCCESS** (0x00) Grupo multicast bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="0ef0c-570">**NX_NO_MORE_ENTRIES** (0x17) Não podem ser acompanhados mais grupos multicast, o máximo excedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="0ef0c-571">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-572">**NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="0ef0c-573">**NX_IP_ADDRESS_ERROR** endereço de grupo multicast fornecido (0x21) não é um endereço de classe D válido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="0ef0c-574">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-575">**NX_NOT_ENABLED** suporte multicast IP (0x14) não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-576">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-576">Allowed From</span></span>

<span data-ttu-id="0ef0c-577">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-578">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-578">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-579">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-579">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-580">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-581">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-581">See Also</span></span>

- <span data-ttu-id="0ef0c-582">nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="0ef0c-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="0ef0c-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="0ef0c-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="0ef0c-586">Junte-se à instância IP para grupo multicast especificado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-587">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="0ef0c-588">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-588">Description</span></span>

<span data-ttu-id="0ef0c-589">Este serviço junta-se a uma instância IP ao grupo multicast especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="0ef0c-590">Mantém-se um contador interno para acompanhar o número de vezes que o mesmo grupo foi acompanhado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="0ef0c-591">O condutor é ordenado a enviar um relatório IGMP se este for o primeiro pedido de junção na rede indicando a intenção do anfitrião de se juntar ao grupo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="0ef0c-592">Após a adesão, o componente IGMP permitirá a receção de pacotes IP com este endereço de grupo e informará aos routers que este IP é membro deste grupo multicast.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef0c-593">*Para se juntar a um grupo multicast num dispositivo não primário, utilize o **serviço nx_igmp_multicast_interface_join.***</span><span class="sxs-lookup"><span data-stu-id="0ef0c-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="0ef0c-594">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="0ef0c-594">**Parameters**</span></span>

- <span data-ttu-id="0ef0c-595">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-596">**group_address** Endereço de grupo multicast classe D IP para aderir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-597">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-597">Return Values</span></span>

- <span data-ttu-id="0ef0c-598">**NX_SUCCESS** (0x00) Grupo multicast bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="0ef0c-599">**NX_NO_MORE_ENTRIES** (0x17) Não podem ser acompanhados mais grupos multicast, o máximo excedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="0ef0c-600">**NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="0ef0c-601">**NX_IP_ADDRESS_ERROR** (0x21) Endereço de grupo IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="0ef0c-602">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-603">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-604">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-605">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-605">Allowed From</span></span>

<span data-ttu-id="0ef0c-606">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-607">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-607">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-608">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-608">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-609">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-610">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-610">See Also</span></span>

- <span data-ttu-id="0ef0c-611">nx_igmp_enable, nx_igmp_info_get nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="0ef0c-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="0ef0c-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="0ef0c-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="0ef0c-615">Fazer com que a instância IP deixe o grupo multicast especificado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-616">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="0ef0c-617">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-617">Description</span></span>

<span data-ttu-id="0ef0c-618">Este serviço faz com que uma instância IP saia do grupo multicast especificado, se o número de pedidos de licença corresponder ao número de pedidos de associação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="0ef0c-619">Caso contrário, a contagem interna de juntas é simplesmente decrementeda.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-620">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-620">Parameters</span></span>

- <span data-ttu-id="0ef0c-621">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-622">**group_address** Grupo multicast para sair.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-623">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-623">Return Values</span></span>

- <span data-ttu-id="0ef0c-624">**NX_SUCCESS** (0x00) Grupo multicast bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="0ef0c-625">**NX_ENTRY_NOT_FOUND** (0x16) Não foi encontrado o pedido de aderião anterior.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="0ef0c-626">**NX_INVALID_INTERFACE** (0x4C) Índice de dispositivo aponta para uma interface de rede inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="0ef0c-627">**NX_IP_ADDRESS_ERROR** (0x21) Endereço de grupo IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="0ef0c-628">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-629">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-630">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-631">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-631">Allowed From</span></span>

<span data-ttu-id="0ef0c-632">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-633">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-633">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-634">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-634">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-635">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="0ef0c-636">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-636">See Also</span></span>

- <span data-ttu-id="0ef0c-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="0ef0c-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="0ef0c-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="0ef0c-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="0ef0c-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="0ef0c-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="0ef0c-641">Notifique a aplicação se o endereço IP mudar</span><span class="sxs-lookup"><span data-stu-id="0ef0c-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="0ef0c-643">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-643">Description</span></span>

<span data-ttu-id="0ef0c-644">Este serviço regista uma função de notificação de aplicação que é chamada sempre que o endereço IP é alterado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-645">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-645">Parameters</span></span>

- <span data-ttu-id="0ef0c-646">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-647">**change_notify** Ponteiro para função de notificação de alteração IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="0ef0c-648">Se este parâmetro for NX_NULL, a notificação de alteração de endereço IP é desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="0ef0c-649">**additional_info** Ponteiro para informações adicionais opcionais que também são fornecidas à função de notificação quando o endereço IP é alterado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-650">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-650">Return Values</span></span>

- <span data-ttu-id="0ef0c-651">**NX_SUCCESS** (0x00) Notificação de alteração de endereço IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="0ef0c-652">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-653">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-654">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-654">Allowed From</span></span>

<span data-ttu-id="0ef0c-655">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-656">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-656">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-657">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-657">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-658">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-659">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-659">See Also</span></span>

- <span data-ttu-id="0ef0c-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="0ef0c-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="0ef0c-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="0ef0c-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-664">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="0ef0c-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-665">nx_ip_address_get</span></span>

<span data-ttu-id="0ef0c-666">Recuperar endereço IP e máscara de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-667">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="0ef0c-668">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-668">Description</span></span>

<span data-ttu-id="0ef0c-669">Este serviço recupera o endereço IP e a sua máscara de sub-rede da interface de rede primária.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="0ef0c-670">\*Para obter informações sobre o dispositivo secundário, utilize o serviço</span><span class="sxs-lookup"><span data-stu-id="0ef0c-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="0ef0c-671">**nx_ip_interface_address_get**.\*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-672">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-672">Parameters</span></span>

- <span data-ttu-id="0ef0c-673">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-674">**ip_address** Ponteiro para destino para endereço IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="0ef0c-675">**network_mask** Ponteiro para destino para máscara de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-676">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-676">Return Values</span></span>

- <span data-ttu-id="0ef0c-677">**NX_SUCCESS** (0x00) endereço IP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="0ef0c-678">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro variável de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="0ef0c-679">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-680">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-680">Allowed From</span></span>

<span data-ttu-id="0ef0c-681">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-682">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-682">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-683">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-683">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-684">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-685">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-685">See Also</span></span>

- <span data-ttu-id="0ef0c-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="0ef0c-687">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="0ef0c-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="0ef0c-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-692">nx_ip_address_set</span></span>

<span data-ttu-id="0ef0c-693">Definir endereço IP e máscara de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-694">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="0ef0c-695">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-695">Description</span></span>

<span data-ttu-id="0ef0c-696">Este serviço define endereço IP e máscara de rede para a interface de rede primária.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="0ef0c-697">*Para definir o endereço IP e a máscara de rede para o dispositivo secundário, utilize o **nx_ip_interface_address_set** de serviço .*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-698">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-698">Parameters</span></span>

- <span data-ttu-id="0ef0c-699">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-700">**ip_address** Novo endereço IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="0ef0c-701">**network_mask** Nova máscara de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-702">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-702">Return Values</span></span>

- <span data-ttu-id="0ef0c-703">**NX_SUCCESS** (0x00) conjunto de endereços IP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="0ef0c-704">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-705">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-706">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-707">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-707">Allowed From</span></span>

<span data-ttu-id="0ef0c-708">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-709">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-709">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-710">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-710">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-711">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-712">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-712">See Also</span></span>

- <span data-ttu-id="0ef0c-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="0ef0c-714">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="0ef0c-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="0ef0c-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-719">nx_ip_create</span></span>

<span data-ttu-id="0ef0c-720">Criar uma instância IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-721">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="0ef0c-722">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-722">Description</span></span>

<span data-ttu-id="0ef0c-723">Este serviço cria uma instância IP com o endereço IP fornecido pelo utilizador e o controlador de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="0ef0c-724">Além disso, a aplicação deve fornecer um conjunto de pacotes previamente criado para a instância IP para usar para a atribuição interna de pacotes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="0ef0c-725">Note que o controlador de rede de aplicações fornecido não é chamado até que o fio deste IP seja executado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-726">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-726">Parameters</span></span>

- <span data-ttu-id="0ef0c-727">**ip_ptr** Ponteiro para bloquear para criar uma nova instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="0ef0c-728">**nome** Nome deste novo exemplo de IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="0ef0c-729">**ip_address** Endereço IP para este novo exemplo de IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="0ef0c-730">**network_mask** Máscara para delinear a parte da rede do endereço IP para utilizações de sub-redes e super-redes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="0ef0c-731">**default_pool** Ponteiro para o bloco de controlo da piscina de pacotes NetX previamente criado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="0ef0c-732">**ip_network_driver** Controlador de rede fornecido pelo utilizador utilizado para enviar e receber pacotes IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="0ef0c-733">**memory_ptr** Ponteiro para a área de memória para a área de pilha do ajudante IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="0ef0c-734">**memory_size** Número de bytes na área de memória para a pilha do fio do ajudante IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="0ef0c-735">**prioridade** Prioridade do fio do ajudante ip.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-736">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-736">Return Values</span></span>
- <span data-ttu-id="0ef0c-737">**NX_SUCCESS** (0x00) criação de instância IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="0ef0c-738">**NX_NOT_IMPLEMENTED** (0x4A) a biblioteca NetX está configurada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="0ef0c-739">**NX_PTR_ERROR** (0x07) IP inválido, ponteiro de função do controlador de rede, piscina de pacotes ou ponteiro de memória.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="0ef0c-740">**NX_SIZE_ERROR** (0x09) O tamanho da pilha fornecida é demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="0ef0c-741">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-742">**NX_IP_ADDRESS_ERROR** (0x21) O endereço IP fornecido é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="0ef0c-743">**NX_OPTION_ERROR** (0x21) A prioridade fornecida do fio IP é inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-744">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-744">Allowed From</span></span>

<span data-ttu-id="0ef0c-745">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-746">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-746">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-747">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-747">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-748">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-749">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-749">See Also</span></span>

- <span data-ttu-id="0ef0c-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-751">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="0ef0c-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="0ef0c-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-756">nx_ip_delete</span></span>

<span data-ttu-id="0ef0c-757">Eliminar instância IP previamente criada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-758">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-759">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-759">Description</span></span>

<span data-ttu-id="0ef0c-760">Este serviço elimina uma instância IP previamente criada e liberta todos os recursos do sistema detidos pela instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-761">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-761">Parameters</span></span>
- <span data-ttu-id="0ef0c-762">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-763">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-763">Return Values</span></span>

- <span data-ttu-id="0ef0c-764">**NX_SUCCESS** (0x00) Eliminação IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="0ef0c-765">**NX_SOCKETS_BOUND** (0x28) Este caso IP ainda tem tomadas UDP ou TCP ligadas a ele.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="0ef0c-766">Todas as tomadas devem ser desvinculados e eliminadas antes de eliminar a instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="0ef0c-767">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-768">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-769">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-769">Allowed From</span></span>

<span data-ttu-id="0ef0c-770">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-771">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-771">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-772">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-773">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-774">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-774">See Also</span></span>

- <span data-ttu-id="0ef0c-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-776">nx_ip_create, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="0ef0c-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="0ef0c-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="0ef0c-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="0ef0c-782">Emitir comando ao controlador de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-783">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-784">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-784">Description</span></span>

<span data-ttu-id="0ef0c-785">Este serviço fornece uma interface direta ao controlador de interface de rede primária da aplicação especificado durante a ***chamada nx_ip_create.***</span><span class="sxs-lookup"><span data-stu-id="0ef0c-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="0ef0c-786">Os comandos específicos da aplicação podem ser utilizados desde que o seu valor numérico seja superior ou igual a NX_LINK_USER_COMMAND.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="0ef0c-787">*Para emitir comando para o dispositivo secundário, utilize o serviço **nx_ip_driver_interface_direct_command.***</span><span class="sxs-lookup"><span data-stu-id="0ef0c-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-788">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-788">Parameters</span></span>

- <span data-ttu-id="0ef0c-789">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-790">**comando** Código de comando numérico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-790">**command** Numeric command code.</span></span> <span data-ttu-id="0ef0c-791">Os comandos padrão são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="0ef0c-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="0ef0c-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="0ef0c-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="0ef0c-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="0ef0c-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="0ef0c-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="0ef0c-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="0ef0c-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="0ef0c-800">**return_value_ptr** Ponteiro para devolver variável no chamador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-801">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-801">Return Values</span></span>

- <span data-ttu-id="0ef0c-802">**NX_SUCCESS** (0x00) Comando direto do controlador de rede bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="0ef0c-803">**NX_UNHANDLED_COMMAND** (0x44) Comando do controlador de rede não manuseado ou não simplificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="0ef0c-804">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="0ef0c-805">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-806">**NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-807">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-807">Allowed From</span></span>

<span data-ttu-id="0ef0c-808">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-808">Threads</span></span>

- <span data-ttu-id="0ef0c-809">**Preempção Possível**</span><span class="sxs-lookup"><span data-stu-id="0ef0c-809">**Preemption Possible**</span></span>

<span data-ttu-id="0ef0c-810">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-810">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-811">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-812">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-812">See Also</span></span>

- <span data-ttu-id="0ef0c-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="0ef0c-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="0ef0c-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-817">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="0ef0c-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="0ef0c-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="0ef0c-819">Emitir comando ao controlador de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-820">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-821">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-821">Description</span></span>

<span data-ttu-id="0ef0c-822">Este serviço fornece um comando direto ao controlador de dispositivo de rede da aplicação na instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="0ef0c-823">Os comandos específicos da aplicação podem ser utilizados desde que o seu valor numérico seja superior ou igual a *NX_LINK_USER_COMMAND*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-824">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-824">Parameters</span></span>

- <span data-ttu-id="0ef0c-825">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-826">**comando** Código de comando numérico.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-826">**command** Numeric command code.</span></span> <span data-ttu-id="0ef0c-827">Os comandos padrão são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="0ef0c-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="0ef0c-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="0ef0c-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="0ef0c-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="0ef0c-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="0ef0c-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="0ef0c-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="0ef0c-836">**interface_index** Índice da interface de rede para o que o comando deve ser enviado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="0ef0c-837">**return_value_ptr** Ponteiro para devolver variável no chamador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-838">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-838">Return Values</span></span>
- <span data-ttu-id="0ef0c-839">**NX_SUCCESS** (0x00) Comando direto do controlador de rede bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="0ef0c-840">**NX_UNHANDLED_COMMAND** (0x44) Comando do controlador de rede não manuseado ou não simplificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="0ef0c-841">**NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="0ef0c-842">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="0ef0c-843">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-844">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-844">Allowed From</span></span>

<span data-ttu-id="0ef0c-845">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-846">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-846">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-847">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-847">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-848">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-849">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-849">See Also</span></span>

- <span data-ttu-id="0ef0c-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="0ef0c-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-854">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="0ef0c-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="0ef0c-856">Desativar o encaminhamento do pacote IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-857">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-858">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-858">Description</span></span>

<span data-ttu-id="0ef0c-859">Este serviço desativa o encaminhamento de pacotes IP dentro do componente IP NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="0ef0c-860">Na criação da tarefa IP, este serviço é automaticamente desativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-861">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-861">Parameters</span></span>

- <span data-ttu-id="0ef0c-862">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-863">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-863">Return Values</span></span>

- <span data-ttu-id="0ef0c-864">**NX_SUCCESS** (0x00) Desativação de IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="0ef0c-865">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-866">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-867">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-867">Allowed From</span></span>

<span data-ttu-id="0ef0c-868">Inicialização, fios, temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-869">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-869">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-870">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-870">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-871">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-872">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-872">See Also</span></span>

- <span data-ttu-id="0ef0c-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="0ef0c-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-877">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="0ef0c-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="0ef0c-879">Ativar o encaminhamento de pacotes IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-880">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-881">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-881">Description</span></span>

<span data-ttu-id="0ef0c-882">Este serviço permite reencaminhar pacotes IP dentro do componente NetX IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="0ef0c-883">Na criação da tarefa IP, este serviço é automaticamente desativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-884">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-884">Parameters</span></span>

- <span data-ttu-id="0ef0c-885">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-886">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-886">Return Values</span></span>
- <span data-ttu-id="0ef0c-887">**NX_SUCCESS** (0x00) Ativação de encaminhamento IP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="0ef0c-888">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-889">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-890">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-890">Allowed From</span></span>

<span data-ttu-id="0ef0c-891">Inicialização, fios, temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-892">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-892">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-893">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-893">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-894">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-895">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-895">See Also</span></span>

- <span data-ttu-id="0ef0c-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-900">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="0ef0c-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="0ef0c-902">Desativar a fragmentação do pacote IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-903">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-904">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-904">Description</span></span>

<span data-ttu-id="0ef0c-905">Este serviço desativa a fragmentação e a montagem do pacote IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="0ef0c-906">Para pacotes à espera de serem remontados, este serviço liberta estes pacotes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="0ef0c-907">Na criação da tarefa IP, este serviço é automaticamente desativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-908">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-908">Parameters</span></span>

- <span data-ttu-id="0ef0c-909">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-910">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-910">Return Values</span></span>
- <span data-ttu-id="0ef0c-911">**NX_SUCCESS** (0x00) Desativação de fragmentos IP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="0ef0c-912">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-913">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-914">**NX_NOT_ENABLED** (0x14) A fragmentação ip não está ativada na instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-915">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-915">Allowed From</span></span>

<span data-ttu-id="0ef0c-916">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-917">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-917">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-918">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-918">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-919">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-920">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-920">See Also</span></span>

- <span data-ttu-id="0ef0c-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-925">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="0ef0c-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="0ef0c-927">Ativar a fragmentação do pacote IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-928">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-929">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-929">Description</span></span>

<span data-ttu-id="0ef0c-930">Este serviço permite a fragmentação e remontagem da funcionalidade do pacote IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="0ef0c-931">Na criação da tarefa IP, este serviço é automaticamente desativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-932">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-932">Parameters</span></span>

- <span data-ttu-id="0ef0c-933">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-934">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-934">Return Values</span></span>

- <span data-ttu-id="0ef0c-935">**NX_SUCCESS** (0x00) Ativar o fragmento IP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="0ef0c-936">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-937">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-938">**NX_NOT_ENABLED** (0x14) As características de fragmentação IP não são compiladas no NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-939">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-939">Allowed From</span></span>

<span data-ttu-id="0ef0c-940">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-941">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-941">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-942">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-942">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-943">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-944">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-944">See Also</span></span>

- <span data-ttu-id="0ef0c-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="0ef0c-949">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="0ef0c-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="0ef0c-951">Definir endereço IP gateway</span><span class="sxs-lookup"><span data-stu-id="0ef0c-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-952">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="0ef0c-953">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-953">Description</span></span>

<span data-ttu-id="0ef0c-954">Este serviço define o endereço IP gateway IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="0ef0c-955">Todo o tráfego fora da rede é encaminhado para este portal de transmissão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="0ef0c-956">O gateway deve estar diretamente acessível através de uma das interfaces de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-957">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-957">Parameters</span></span>

- <span data-ttu-id="0ef0c-958">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-959">**ip_address** Endereço IP do portal.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-960">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-960">Return Values</span></span>

- <span data-ttu-id="0ef0c-961">**NX_SUCCESS** (0x00) conjunto de endereço IP de Gateway bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="0ef0c-962">**NX_PTR_ERROR** (0x07) Ponteiro de instância IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="0ef0c-963">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-964">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-965">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-965">Allowed From</span></span>

<span data-ttu-id="0ef0c-966">Inicialização, fio</span><span class="sxs-lookup"><span data-stu-id="0ef0c-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-967">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-967">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-968">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-968">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-969">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="0ef0c-970">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-970">See Also</span></span>

- <span data-ttu-id="0ef0c-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="0ef0c-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-972">nx_ip_info_get</span></span>

<span data-ttu-id="0ef0c-973">Recuperar informações sobre atividades ip</span><span class="sxs-lookup"><span data-stu-id="0ef0c-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-974">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="0ef0c-975">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-975">Description</span></span>

<span data-ttu-id="0ef0c-976">Este serviço obtém informações sobre as atividades IP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-977">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-978">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-978">Parameters</span></span>

- <span data-ttu-id="0ef0c-979">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-980">**ip_total_packets_sent** Ponteiro para destino para o número total de pacotes IP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="0ef0c-981">**ip_total_bytes_sent** Ponteiro para destino para o número total de bytes enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="0ef0c-982">**ip_total_packets_received** Ponteiro para o destino do número total de pacotes de IP recebem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="0ef0c-983">**ip_total_bytes_received** Ponteiro para o destino do número total de bytes IP recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="0ef0c-984">**ip_invalid_packets** Ponteiro para o destino do número total de pacotes IP inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="0ef0c-985">**ip_receive_packets_dropped** Ponteiro para o destino do número total de pacotes de receção reduzido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="0ef0c-986">**ip_receive_checksum_errors** Ponteiro para o destino do número total de erros de checkum nos pacotes de receção.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="0ef0c-987">**ip_send_packets_dropped** Ponteiro para o destino do número total de pacotes de envio reduzidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="0ef0c-988">**ip_total_fragments_sent** Ponteiro para o destino do número total de fragmentos enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="0ef0c-989">**ip_total_fragments_received** Ponteiro para o destino do número total de fragmentos recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-990">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-990">Return Values</span></span>

- <span data-ttu-id="0ef0c-991">**NX_SUCCESS** (0x00) Recuperação de informações IP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-992">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-993">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-994">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-994">Allowed From</span></span>

<span data-ttu-id="0ef0c-995">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-996">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-996">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-997">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-997">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-998">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-999">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-999">See Also</span></span>

- <span data-ttu-id="0ef0c-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="0ef0c-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="0ef0c-1006">Recuperar endereço IP de interface</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1007">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1008">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1008">Description</span></span>

<span data-ttu-id="0ef0c-1009">Este serviço recupera o endereço IP de uma interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="0ef0c-1010">*O dispositivo especificado, se não o dispositivo primário, deve ser previamente ligado à instância IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1011">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1011">Parameters</span></span>

- <span data-ttu-id="0ef0c-1012">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1013">**interface_index** Índice de interface, o mesmo valor que o índice da interface de rede anexada à instância IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="0ef0c-1014">**ip_address** Ponteiro para destino para o endereço IP interface do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="0ef0c-1015">**network_mask** Ponteiro para destino para a máscara de rede de interface do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1016">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1016">Return Values</span></span>

- <span data-ttu-id="0ef0c-1017">**NX_SUCCESS** (0x00) endereço IP bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="0ef0c-1018">**NX_INVALID_INTERFACE** (0x4C) A interface de rede especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="0ef0c-1019">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1020">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1021">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1021">Allowed From</span></span>

<span data-ttu-id="0ef0c-1022">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1023">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1023">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1024">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1025">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1026">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1026">See Also</span></span>

- <span data-ttu-id="0ef0c-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="0ef0c-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="0ef0c-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="0ef0c-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="0ef0c-1031">Definir interface endereço IP e máscara de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1032">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1033">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1033">Description</span></span>

<span data-ttu-id="0ef0c-1034">Este serviço define o endereço IP e a máscara de rede para a interface IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="0ef0c-1035">*A interface especificada deve ser previamente anexada à instância IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1036">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1036">Parameters</span></span>

- <span data-ttu-id="0ef0c-1037">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1038">**interface_index** Índice da interface anexa à instância NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="0ef0c-1039">**ip_address** Novo endereço IP de interface de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="0ef0c-1040">**network_mask** Nova máscara de rede de interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1041">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1041">Return Values</span></span>

- <span data-ttu-id="0ef0c-1042">**NX_SUCCESS** (0x00) conjunto de endereços IP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="0ef0c-1043">**NX_INVALID_INTERFACE** (0x4C) A interface de rede especificada é inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="0ef0c-1044">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1045">**NX_PTR_ERROR** (0x07) Ponteiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="0ef0c-1046">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1047">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1047">Allowed From</span></span>

<span data-ttu-id="0ef0c-1048">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1049">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1049">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1050">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1051">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1052">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1052">See Also</span></span>

- <span data-ttu-id="0ef0c-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="0ef0c-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="0ef0c-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="0ef0c-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="0ef0c-1057">Anexar interface de rede à instância IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="0ef0c-1059">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1059">Description</span></span>

<span data-ttu-id="0ef0c-1060">Este serviço adiciona uma interface de rede física à interface IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="0ef0c-1061">Note que a instância IP é criada com a interface primária para que cada interface adicional seja secundária à interface primária.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="0ef0c-1062">O número total de interfaces de rede anexas à instância IP (incluindo a interface primária) não pode exceder **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="0ef0c-1063">Se o fio IP ainda não estiver em funcionamento, as interfaces secundárias serão inicializadas como parte do processo de arranque do fio IP que inicializa todas as interfaces físicas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="0ef0c-1064">Se a linha IP ainda não estiver em funcionamento, a interface secundária é inicializada como parte do serviço ***nx_ip_interface_attach.***</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="0ef0c-1065">*ip_ptr deve apontar para uma estrutura DE IP NetX válida.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="0ef0c-1066">***NX_MAX_PHYSICAL_INTERFACES** devem ser configurados para o número de interfaces de rede para a instância IP. O valor predefinido é um.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1067">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1067">Parameters</span></span>

- <span data-ttu-id="0ef0c-1068">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1069">**interface_name** Ponteiro para interface linha nome.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="0ef0c-1070">**ip_address** Endereço IP do dispositivo na ordem byte anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="0ef0c-1071">**network_mask** Máscara de rede do dispositivo na ordem byte hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="0ef0c-1072">**ip_link_driver** Controlador Ethernet para a interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1073">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1073">Return Values</span></span>

- <span data-ttu-id="0ef0c-1074">**NX_SUCCESS** (0x00) A entrada é adicionada à mesa de encaminhamento estática.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="0ef0c-1075">**NX_NO_MORE_ENTRIES** (0x17) Número máximo de interfaces.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="0ef0c-1076">**NX_MAX_PHYSICAL_INTERFACES** é excedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="0ef0c-1077">**NX_DUPLICATED_ENTRY** (0x52) O endereço IP fornecido já é utilizado neste caso IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="0ef0c-1078">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1079">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="0ef0c-1080">**NX_IP_ADDRESS_ERROR** (0x21) Entrada de endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1081">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1081">Allowed From</span></span>

<span data-ttu-id="0ef0c-1082">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1083">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1083">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1084">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1085">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1086">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1086">See Also</span></span>

- <span data-ttu-id="0ef0c-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="0ef0c-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="0ef0c-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="0ef0c-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="0ef0c-1091">Recuperar parâmetros de interface de rede</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-1092">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1093">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1093">Description</span></span>

<span data-ttu-id="0ef0c-1094">Este serviço obtém informações sobre os parâmetros de rede para a interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="0ef0c-1095">Todos os dados são recuperados por encomenda de byte de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="0ef0c-1096">*ip_ptr deve apontar para uma estrutura DE IP NetX válida. A interface especificada, se não a interface primária, deve ser previamente anexada à instância IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1097">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1097">Parameters</span></span>

- <span data-ttu-id="0ef0c-1098">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1099">**interface_index** Índice especificando interface de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="0ef0c-1100">**interface_name** Ponteiro para o tampão que detém o nome da interface de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="0ef0c-1101">**ip_address** Ponteiro para o destino para o endereço IP da interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="0ef0c-1102">**network_mask** Ponteiro para destino para máscara de rede.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="0ef0c-1103">**mtu_size** Ponteiro para destino para unidade de transferência máxima para esta interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="0ef0c-1104">**physical_address_msw** Ponteiro para o destino para os 16 melhores bits do endereço MAC do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="0ef0c-1105">**physical_address_lsw** Ponteiro para destino para menos 32 bits do endereço MAC do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-1106">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1106">Return Values</span></span>
- <span data-ttu-id="0ef0c-1107">**NX_SUCCESS** informações de interface (0x00) foram obtidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="0ef0c-1108">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="0ef0c-1109">**NX_INVALID_INTERFACE** (0x4C) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1110">**NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1111">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1111">Allowed From</span></span>

<span data-ttu-id="0ef0c-1112">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1113">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1113">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1114">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1116">See Also</span></span>

- <span data-ttu-id="0ef0c-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="0ef0c-1118">nx_ip_interface_attach, nx_ip_interface_status_check.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="0ef0c-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="0ef0c-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="0ef0c-1121">Verificar o estado de verificação de uma instância IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-1122">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1123">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1123">Description</span></span>

<span data-ttu-id="0ef0c-1124">Este serviço verifica e aguarda opcionalmente o estado especificado da interface de rede de uma instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1125">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1125">Parameters</span></span>

- <span data-ttu-id="0ef0c-1126">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1127">**interface_index** Número do índice de interface</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="0ef0c-1128">**needed_status** Estado ip solicitado, definido no formulário bit-mape da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="0ef0c-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="0ef0c-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="0ef0c-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="0ef0c-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="0ef0c-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="0ef0c-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="0ef0c-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="0ef0c-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="0ef0c-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="0ef0c-1138">**atual_status** Ponteiro para o destino de bits reais definido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="0ef0c-1139">**wait_option** Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="0ef0c-1140">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="0ef0c-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="0ef0c-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="0ef0c-1143">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1144">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1144">Return Values</span></span>

- <span data-ttu-id="0ef0c-1145">**NX_SUCCESS** (0x00) Verificação de estado IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="0ef0c-1146">**NX_NOT_SUCCESSFUL** pedido de estado (0x43) não foi satisfeito dentro do prazo especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="0ef0c-1147">**NX_PTR_ERROR** ponteiro IP (0x07) é ou tornou-se inválido, ou o ponteiro de estado real é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="0ef0c-1148">**NX_OPTION_ERROR** (0x0a) A opção de estado necessária inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="0ef0c-1149">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1150">**Interface_index NX_INVALID_INTERFACE** (0x4C) está fora de alcance.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="0ef0c-1151">ou a interface não é válida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1152">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1152">Allowed From</span></span>

<span data-ttu-id="0ef0c-1153">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1154">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1154">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1155">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1157">See Also</span></span>

- <span data-ttu-id="0ef0c-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="0ef0c-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="0ef0c-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="0ef0c-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="0ef0c-1162">Desa um conjunto de alterações de estado de ligação notifique a função de retorno de chamadas</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1163">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="0ef0c-1164">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1164">Description</span></span>

<span data-ttu-id="0ef0c-1165">Este serviço configura a alteração do estado de ligação notifica a função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="0ef0c-1166">A rotina *de link_status_change_notify* fornecida pelo utilizador é invocada quando o estado da interface primária ou secundária é alterado (por exemplo, o endereço IP é alterado.) Se *link_status_change_notify* é NU, a alteração do estado de ligação notifica a função de chamada de chamada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1167">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1167">Parameters</span></span>

- <span data-ttu-id="0ef0c-1168">**ip_ptr** Ponteiro do bloco de controlo IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="0ef0c-1169">**link_status_change_notify** Função de retorno fornecida pelo utilizador a ser chamada a uma alteração da interface física.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-1170">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1170">Return Values</span></span>

- <span data-ttu-id="0ef0c-1171">**NX_SUCCESS** (0x00) Conjunto de sucesso</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="0ef0c-1172">**NX_PTR_ERROR** (0x07) Ponteiro do bloco de controlo IP inválido ou novo ponteiro de endereço físico</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="0ef0c-1173">**NX_CALLER_ERROR** (0x11) O serviço não é chamado a partir da inicialização do sistema ou do contexto do fio.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1174">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1174">Allowed From</span></span>

<span data-ttu-id="0ef0c-1175">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1176">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1176">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1177">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1179">See Also</span></span>

- <span data-ttu-id="0ef0c-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="0ef0c-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="0ef0c-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="0ef0c-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="0ef0c-1184">Desativar o envio/receção de pacotes brutos</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-1185">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1186">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1186">Description</span></span>

<span data-ttu-id="0ef0c-1187">Este serviço desativa a transmissão e receção de pacotes IP crus para este caso IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="0ef0c-1188">Se o serviço de pacotes brutos foi previamente ativado, e existem pacotes crus na fila de receção, este serviço libertará quaisquer pacotes crus recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1189">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1189">Parameters</span></span>

- <span data-ttu-id="0ef0c-1190">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1191">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1191">Return Values</span></span>

- <span data-ttu-id="0ef0c-1192">**NX_SUCCESS** (0x00) Pacotes IP crus bem sucedidos desativar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="0ef0c-1193">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1194">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1195">Allowed From</span></span>

<span data-ttu-id="0ef0c-1196">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1197">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1197">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1198">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1200">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1200">See Also</span></span>

- <span data-ttu-id="0ef0c-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="0ef0c-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="0ef0c-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="0ef0c-1204">Permitir o processamento de pacotes crus</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-1205">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1206">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1206">Description</span></span>

<span data-ttu-id="0ef0c-1207">Este serviço permite a transmissão e receção de pacotes IP crus para este caso IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="0ef0c-1208">Os pacotes de TCP, UDP, ICMP e IGMP ainda são processados pela NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="0ef0c-1209">Pacotes com tipos de protocolo de camada superior desconhecida são processados pela rotina de receção de pacotes crus.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1210">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1210">Parameters</span></span>

- <span data-ttu-id="0ef0c-1211">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1212">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1212">Return Values</span></span>

- <span data-ttu-id="0ef0c-1213">**NX_SUCCESS** (0x00) Pacotes ip crus bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="0ef0c-1214">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1215">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1216">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1216">Allowed From</span></span>

<span data-ttu-id="0ef0c-1217">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1218">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1218">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1219">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1220">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1221">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1221">See Also</span></span>

- <span data-ttu-id="0ef0c-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="0ef0c-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="0ef0c-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="0ef0c-1225">Enviar pacote IP cru através de interface de rede especificada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1226">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1227">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1227">Description</span></span>

<span data-ttu-id="0ef0c-1228">Este serviço envia um pacote IP bruto para o endereço IP de destino usando o endereço IP local especificado como endereço de origem, e através da interface de rede associada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="0ef0c-1229">Note que esta rotina retorna imediatamente, e não é, portanto, conhecido se o pacote IP foi realmente enviado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="0ef0c-1230">O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="0ef0c-1231">Este serviço difere de outros serviços na medida em que não há forma de saber se o pacote foi realmente enviado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="0ef0c-1232">Pode perder-se na Internet.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="0ef0c-1233">*Note que o processamento de IP bruto deve ser ativado.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="0ef0c-1234">*Este serviço é semelhante ao **nx_ip_raw_packet_send,** exceto que este serviço permite que uma aplicação envie pacote IP cru a partir de interfaces físicas especificadas.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1235">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1235">Parameters</span></span>

- <span data-ttu-id="0ef0c-1236">**ip_ptr** Ponteiro para tarefa IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="0ef0c-1237">**packet_ptr** Ponteiro para pacote para transmitir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="0ef0c-1238">**destination_ip** Endereço IP para enviar pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="0ef0c-1239">**address_index** Índice do endereço da interface para enviar o pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="0ef0c-1240">**type_of_service** Tipo de serviço para pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1241">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1241">Return Values</span></span>

- <span data-ttu-id="0ef0c-1242">**NX_SUCCESS** (0x00) Pacote transmitido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="0ef0c-1243">**NX_IP_ADDRESS_ERROR** (0x21) Não existe uma interface de saída adequada disponível.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="0ef0c-1244">**NX_NOT_ENABLED** (0x14) processamento de pacotes IP crus não ativados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="0ef0c-1245">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1246">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="0ef0c-1247">**NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="0ef0c-1248">**NX_OVERFLOW** (0x03) Ponteiro de pré-final de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="0ef0c-1249">**NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="0ef0c-1250">**NX_INVALID_INTERFACE** (0x4C) Índice de interface inválido especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1251">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1251">Allowed From</span></span>

<span data-ttu-id="0ef0c-1252">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1253">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1253">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1254">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1255">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1256">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1256">See Also</span></span>

- <span data-ttu-id="0ef0c-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="0ef0c-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="0ef0c-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="0ef0c-1260">Receba pacote IP cru</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1261">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1262">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1262">Description</span></span>

<span data-ttu-id="0ef0c-1263">Este serviço recebe um pacote IP cru a partir da instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="0ef0c-1264">Se houver pacotes IP na fila de receção de pacotes brutos, o primeiro pacote (mais antigo) é devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="0ef0c-1265">Caso contrário, se não houver pacotes disponíveis, o chamador pode suspender conforme especificado pela opção de espera.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="0ef0c-1266">*Se NX_SUCCESS, for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1267">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1267">Parameters</span></span>

- <span data-ttu-id="0ef0c-1268">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1269">**packet_ptr** Ponteiro para o ponteiro para colocar o pacote IP bruto recebido dentro</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="0ef0c-1270">**wait_option** Define como o serviço se comporta se não houver pacotes IP crus disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="0ef0c-1271">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1274">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1275">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1275">Return Values</span></span>

- <span data-ttu-id="0ef0c-1276">**NX_SUCCESS** (0x00) Pacote IP cru bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="0ef0c-1277">**NX_NO_PACKET** (0x01) Não estava disponível nenhum pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="0ef0c-1278">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-1279">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-1280">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro do pacote de devolução.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1281">**NX_CALLER_ERROR** (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1282">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1282">Allowed From</span></span>

<span data-ttu-id="0ef0c-1283">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1284">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1284">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1285">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1286">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1287">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1287">See Also</span></span>

- <span data-ttu-id="0ef0c-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="0ef0c-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="0ef0c-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="0ef0c-1291">Enviar pacote IP cru</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1292">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1293">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1293">Description</span></span>

<span data-ttu-id="0ef0c-1294">Este serviço envia um pacote IP cru para o endereço IP destino.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="0ef0c-1295">Note que esta rotina retorna imediatamente, pelo que não se sabe se o pacote IP foi efetivamente enviado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="0ef0c-1296">O controlador de rede será responsável pela libertação do pacote quando a transmissão estiver completa.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="0ef0c-1297">Para um sistema multihome, o NetX utiliza o endereço IP de destino para encontrar uma interface de rede apropriada e utiliza o endereço IP da interface como endereço de origem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="0ef0c-1298">Se o endereço IP de destino for transmitido ou multicast, a primeira interface válida é utilizada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="0ef0c-1299">As aplicações utilizam o ***nx_ip_raw_packet_interface_send*** neste caso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="0ef0c-1300">*A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede libertará o pacote após a transmissão.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1301">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1301">Parameters</span></span>

- <span data-ttu-id="0ef0c-1302">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1303">**packet_ptr** Ponteiro para o pacote IP cru para enviar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="0ef0c-1304">**destination_ip** Endereço IP de destino, que pode ser um endereço IP de anfitrião específico, uma transmissão de rede, um loop-back interno ou um endereço multicast.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="0ef0c-1305">**type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="0ef0c-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="0ef0c-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="0ef0c-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="0ef0c-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-1311">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1311">Return Values</span></span>

- <span data-ttu-id="0ef0c-1312">**NX_SUCCESS** (0x00) Pacotes crus IP bem sucedidos enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="0ef0c-1313">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-1314">**NX_NOT_ENABLED** (0x14) A função IP raw não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="0ef0c-1315">**NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="0ef0c-1316">**NX_UNDERFLOW** (0x02) Não há espaço suficiente para preparar um cabeçalho IP no pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="0ef0c-1317">**NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="0ef0c-1318">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1319">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1320">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1320">Allowed From</span></span>

<span data-ttu-id="0ef0c-1321">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1322">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1322">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1323">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1324">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1325">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1325">See Also</span></span>

- <span data-ttu-id="0ef0c-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="0ef0c-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="0ef0c-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="0ef0c-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="0ef0c-1330">Adicione rota estática à mesa de encaminhamento</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1331">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1332">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1332">Description</span></span>

<span data-ttu-id="0ef0c-1333">Este serviço adiciona uma entrada na tabela de encaminhamento estático.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="0ef0c-1334">Note que o endereço *next_hop* deve estar diretamente acessível a partir de um dos dispositivos de rede locais.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="0ef0c-1335">*Note que ip_ptr deve apontar para uma estrutura CÓP NetX válida e a biblioteca NetX deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para utilizar este serviço. Por padrão, o NetX é construído sem NX_ENABLE_IP_STATIC_ROUTING definido.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1336">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1336">Parameters</span></span>

- <span data-ttu-id="0ef0c-1337">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1338">**network_address** Endereço de rede alvo, em ordem byte de anfitrião</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="0ef0c-1339">**net_mask** Máscara de rede de alvo, em ordem byte hospedeiro</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="0ef0c-1340">**next_hop** Próximo endereço de lúpulo para a rede alvo, em ordem byte anfitrião</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1341">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1341">Return Values</span></span>

- <span data-ttu-id="0ef0c-1342">**NX_SUCCESS** (0x00) A entrada é adicionada à mesa de encaminhamento estática.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="0ef0c-1343">**NX_OVERFLOW** (0x03) A mesa de encaminhamento está cheia.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="0ef0c-1344">**NX_NOT_SUPPORTED** (0x4B) Esta função não está compilada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="0ef0c-1345">**NX_IP_ADDRESS_ERROR** (0x21) O próximo lúpulo não é diretamente acessível através de interfaces locais.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="0ef0c-1346">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1347">**NX_PTR_ERROR** (0x07) Ponteiro ip_ptr Inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1348">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1348">Allowed From</span></span>

<span data-ttu-id="0ef0c-1349">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1350">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1350">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1351">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1352">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1353">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1353">See Also</span></span>

- <span data-ttu-id="0ef0c-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="0ef0c-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="0ef0c-1356">Eliminar rota estática da mesa de encaminhamento</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1357">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1358">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1358">Description</span></span>

<span data-ttu-id="0ef0c-1359">Este serviço elimina uma entrada da tabela de encaminhamento estático.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="0ef0c-1360">*Note que ip_ptr deve apontar para uma estrutura CÓP NetX válida e a biblioteca NetX deve ser construída com NX_ENABLE_IP_STATIC_ROUTING definida para utilizar este serviço. Por padrão, o NetX é construído sem NX_ENABLE_IP_STATIC_ROUTING definido.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1361">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1361">Parameters</span></span>

- <span data-ttu-id="0ef0c-1362">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1363">**network_address** Endereço de rede de destino, em ordem byte anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="0ef0c-1364">**net_mask** Máscara de rede de alvo, em ordem byte de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1365">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1365">Allowed From</span></span>

<span data-ttu-id="0ef0c-1366">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1367">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1367">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1368">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1369">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1370">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1370">See Also</span></span>

- <span data-ttu-id="0ef0c-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="0ef0c-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1372">nx_ip_status_check</span></span>

<span data-ttu-id="0ef0c-1373">Verificar o estado de verificação de uma instância IP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1374">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1375">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1375">Description</span></span>

<span data-ttu-id="0ef0c-1376">Este serviço verifica e aguarda opcionalmente o estado especificado da interface de rede primária de uma instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="0ef0c-1377">Para obter o estatuto nas interfaces secundárias, as aplicações utilizarão o ***serviço nx_ip_interface_status_check.***</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1378">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1378">Parameters</span></span>

- <span data-ttu-id="0ef0c-1379">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1380">**needed_status** Estado ip solicitado, definido no formulário bit-mape da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="0ef0c-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="0ef0c-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="0ef0c-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="0ef0c-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="0ef0c-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="0ef0c-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="0ef0c-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="0ef0c-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="0ef0c-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="0ef0c-1390">**atual_status** Ponteiro para o destino de bits reais definido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="0ef0c-1391">**wait_option** Define como o serviço se comporta se as bits de estado solicitados não estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="0ef0c-1392">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1395">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1396">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1396">Return Values</span></span>

- <span data-ttu-id="0ef0c-1397">**NX_SUCCESS** (0x00) Verificação de estado IP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="0ef0c-1398">**NX_NOT_SUCCESSFUL** pedido de estado (0x43) não foi satisfeito dentro do prazo especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="0ef0c-1399">**NX_PTR_ERROR** ponteiro IP (0x07) é ou tornou-se inválido, ou o ponteiro de estado real é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="0ef0c-1400">**NX_OPTION_ERROR** (0x0a) A opção de estado necessária inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="0ef0c-1401">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1402">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1402">Allowed From</span></span>

<span data-ttu-id="0ef0c-1403">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1404">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1404">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1405">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1406">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1407">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1407">See Also</span></span>

- <span data-ttu-id="0ef0c-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="0ef0c-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1413">nx_packet_allocate</span></span>

<span data-ttu-id="0ef0c-1414">Alocar pacote a partir de piscina especificada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1415">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1416">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1416">Description</span></span>

<span data-ttu-id="0ef0c-1417">Este serviço atribui um pacote da piscina especificada e ajusta o ponteiro pré-final no pacote de acordo com o tipo de pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="0ef0c-1418">Se não houver pacote disponível, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1419">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1419">Parameters</span></span>

- <span data-ttu-id="0ef0c-1420">**pool_ptr** Ponteiro para piscina de pacotes previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="0ef0c-1421">**packet_ptr** Ponteiro para o ponteiro do ponteiro do pacote atribuído.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1422">**packet_type** Define o tipo de pacote solicitado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="0ef0c-1423">Consulte "Packet Pools" na página 49 do Capítulo 3 para obter uma lista de tipos de pacotes suportados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="0ef0c-1424">**wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="0ef0c-1425">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1428">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1429">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1429">Return Values</span></span>

- <span data-ttu-id="0ef0c-1430">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="0ef0c-1431">**NX_NO_PACKET** (0x01) Nenhum pacote disponível.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="0ef0c-1432">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-1433">**NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="0ef0c-1434">**NX_OPTION_ERROR** (0x0A) Tipo de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="0ef0c-1435">**NX_PTR_ERROR** (0x07) Ponteiro de retorno de piscina ou pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="0ef0c-1436">**NX_CALLER_ERROR** (0x11) Opção de espera inválida de não-leitura.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1437">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1437">Allowed From</span></span>

<span data-ttu-id="0ef0c-1438">Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="0ef0c-1439">A opção de espera deve ser NX_NO_WAIT quando utilizada no contexto ISR ou no temporizador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1440">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1440">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1441">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1442">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1443">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1443">See Also</span></span>

- <span data-ttu-id="0ef0c-1444">nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1447">nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="0ef0c-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1449">nx_packet_copy</span></span>

<span data-ttu-id="0ef0c-1450">Pacote de cópia</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1451">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1452">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1452">Description</span></span>

<span data-ttu-id="0ef0c-1453">Este serviço copia as informações no pacote fornecido a um ou mais novos pacotes que são atribuídos a partir da piscina de pacotes fornecidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="0ef0c-1454">Se for bem sucedido, o ponteiro para o novo pacote é devolvido no destino apontado por **new_packet_ptr**.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1455">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1455">Parameters</span></span>

- <span data-ttu-id="0ef0c-1456">**packet_ptr** Ponteiro para o pacote de origem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="0ef0c-1457">**new_packet_ptr** Ponteiro para o destino de onde devolver o ponteiro à nova cópia do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="0ef0c-1458">**pool_ptr** Ponteiro para o pacote de pacotes anteriormente criado que é usado para alocar um ou mais pacotes para a cópia.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="0ef0c-1459">**wait_option** Define como o serviço espera se não houver pacotes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="0ef0c-1460">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1463">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1464">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1464">Return Values</span></span>
- <span data-ttu-id="0ef0c-1465">**NX_SUCCESS** (0x00) Cópia de pacote bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="0ef0c-1466">**NX_NO_PACKET** (0x01) Pacote não disponível para cópia.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="0ef0c-1467">**NX_INVALID_PACKET** (0x12) O pacote de origem ou cópia vazio falhou.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="0ef0c-1468">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-1469">**NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="0ef0c-1470">**NX_PTR_ERROR** (0x07) Piscina inválida, pacote ou ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="0ef0c-1471">**NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="0ef0c-1472">**NX_OVERFLOW** (0x03) Ponteiro de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="0ef0c-1473">**NX_CALLER_ERROR** (0x11) Foi especificada uma opção de espera na inicialização ou numa ISR.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1474">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1474">Allowed From</span></span>

<span data-ttu-id="0ef0c-1475">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1476">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1476">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1477">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1478">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1479">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1479">See Also</span></span>

- <span data-ttu-id="0ef0c-1480">nx_packet_allocate, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1483">nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="0ef0c-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1485">nx_packet_data_append</span></span>

<span data-ttu-id="0ef0c-1486">Dados do apêndice ao fim do pacote</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1487">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1488">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1488">Description</span></span>

<span data-ttu-id="0ef0c-1489">Este serviço anexa dados ao final do pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="0ef0c-1490">A área de dados fornecida é copiada para o pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="0ef0c-1491">Se não houver memória suficiente disponível e a função de pacote acorrentado estiver ativada, um ou mais pacotes serão atribuídos para satisfazer o pedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="0ef0c-1492">Se a função de pacote acorrentado não estiver ativada, *NX_SIZE_ERROR* é devolvida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1493">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1493">Parameters</span></span>

- <span data-ttu-id="0ef0c-1494">**packet_ptr** Ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1495">**data_start** Ponteiro para o início da área de dados do utilizador para anexar ao pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="0ef0c-1496">**data_size** Tamanho da área de dados do utilizador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="0ef0c-1497">**pool_ptr** Ponteiro para pacote de piscina a partir do qual atribuir outro pacote se não houver espaço suficiente no pacote atual.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="0ef0c-1498">**wait_option** Define como o serviço se comporta se não houver pacotes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="0ef0c-1499">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1502">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1503">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1503">Return Values</span></span>

- <span data-ttu-id="0ef0c-1504">**NX_SUCCESS** (0x00) Pacote de sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="0ef0c-1505">**NX_NO_PACKET** (0x01) Nenhum pacote disponível.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="0ef0c-1506">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="0ef0c-1507">**NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="0ef0c-1508">**NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="0ef0c-1509">**NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="0ef0c-1510">**NX_PTR_ERROR** (0x07) Piscina inválida, pacote ou dados Pointer.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="0ef0c-1511">**NX_SIZE_ERROR** (0x09) Tamanho de dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="0ef0c-1512">**NX_CALLER_ERROR** (0x11) Opção de espera inválida de não-leitura.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1513">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1513">Allowed From</span></span>

<span data-ttu-id="0ef0c-1514">Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1515">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1515">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1516">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1517">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="0ef0c-1518">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1518">See Also</span></span>

- <span data-ttu-id="0ef0c-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="0ef0c-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="0ef0c-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="0ef0c-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="0ef0c-1524">Extrair dados do pacote através de uma compensação</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1525">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1526">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1526">Description</span></span>

<span data-ttu-id="0ef0c-1527">Este serviço copia dados de um pacote NetX (ou cadeia de pacotes) a partir da compensação especificada do ponteiro pré-conjunto do pacote do tamanho especificado em bytes no tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="0ef0c-1528">O número de bytes copiados é devolvido em *bytes_copied.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="0ef0c-1529">Este serviço não remove dados do pacote, nem ajusta o ponteiro pré-conjunto ou outras informações internas do estado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1530">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1530">Parameters</span></span>

- <span data-ttu-id="0ef0c-1531">**packet_ptr** Ponteiro para pacote para extrair</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="0ef0c-1532">**compensar** Compensado do ponteiro pré-final atual.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="0ef0c-1533">**buffer_start** Ponteiro para o início do tampão de poupança</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="0ef0c-1534">**buffer_length** Número de bytes para copiar</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="0ef0c-1535">**bytes_copied** Número de bytes realmente copiados</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1536">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1536">Return Values</span></span>

- <span data-ttu-id="0ef0c-1537">**NX_SUCCESS** (0x00) Cópia de pacote de sucesso</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="0ef0c-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Foi fornecido valor de compensação inválido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="0ef0c-1539">**NX_PTR_ERROR** (0x07) Ponteiro de pacote inválido ou ponteiro tampão</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1540">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1540">Allowed From</span></span>

<span data-ttu-id="0ef0c-1541">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1542">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1542">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1543">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1544">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1545">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1545">See Also</span></span>

- <span data-ttu-id="0ef0c-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="0ef0c-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="0ef0c-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="0ef0c-1551">Recuperar dados do pacote</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1552">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1553">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1553">Description</span></span>

<span data-ttu-id="0ef0c-1554">Este serviço copia os dados do pacote fornecido no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="0ef0c-1555">O número real de bytes copiados é devolvido no destino apontado por **bytes_copied**.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="0ef0c-1556">Note que este serviço não altera o estado interno do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="0ef0c-1557">Os dados que estão a ser recuperados ainda estão disponíveis no pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="0ef0c-1558">*O tampão de destino deve ser grande o suficiente para manter o conteúdo do pacote. Caso contrário, a memória será corrompida causando resultados imprevisíveis.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1559">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1559">Parameters</span></span>

- <span data-ttu-id="0ef0c-1560">**packet_ptr** Ponteiro para o pacote de origem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="0ef0c-1561">**buffer_start** Ponteiro para o início da área tampão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="0ef0c-1562">**bytes_copied** Ponteiro para o destino para o número de bytes copiados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1563">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1563">Return Values</span></span>

- <span data-ttu-id="0ef0c-1564">**NX_SUCCESS** (0x00) Recuperação de dados de pacotes bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="0ef0c-1565">**pacote** inválido NX_INVALID_PACKET (0x12).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="0ef0c-1566">**NX_PTR_ERROR** (0x07) Pacote inválido, arranque do tampão ou bytes ponteiros copiados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1567">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1567">Allowed From</span></span>

<span data-ttu-id="0ef0c-1568">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1569">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1569">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1570">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1571">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1572">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1572">See Also</span></span>

- <span data-ttu-id="0ef0c-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="0ef0c-1575">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1576">nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="0ef0c-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1578">nx_packet_length_get</span></span>

<span data-ttu-id="0ef0c-1579">Obtenha o comprimento dos dados do pacote</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1580">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1581">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1581">Description</span></span>

<span data-ttu-id="0ef0c-1582">Este serviço obtém o comprimento dos dados no pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1583">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1583">Parameters</span></span>

- <span data-ttu-id="0ef0c-1584">**packet_ptr** Ponteiro para o pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="0ef0c-1585">**comprimento** Destino para o comprimento do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1586">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1586">Allowed From</span></span>

<span data-ttu-id="0ef0c-1587">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1588">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1588">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1589">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1590">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1591">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1591">See Also</span></span>

- <span data-ttu-id="0ef0c-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1594">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1595">nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="0ef0c-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="0ef0c-1598">Criar piscina de pacotes na área de memória especificada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1599">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1600">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1600">Description</span></span>

<span data-ttu-id="0ef0c-1601">Este serviço cria um conjunto de pacotes do tamanho especificado do pacote na área de memória fornecida pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1602">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1602">Parameters</span></span>

- <span data-ttu-id="0ef0c-1603">**pool_ptr** Ponteiro para bloco de controlo de piscina de pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="0ef0c-1604">**nome** Ponteiro para o nome da aplicação para a piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="0ef0c-1605">**payload_size** Número de bytes em cada pacote na piscina.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="0ef0c-1606">Este valor deve ser de, pelo menos, 40 bytes e deve ser igualmente divisível por 4.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="0ef0c-1607">**memory_ptr** Ponteiro para a área de memória para colocar a piscina de pacotes dentro</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="0ef0c-1608">O ponteiro deve ser alinhado num limite ULONG.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="0ef0c-1609">**memory_size** Tamanho da área de memória da piscina.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1610">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1610">Return Values</span></span>

- <span data-ttu-id="0ef0c-1611">**NX_SUCCESS** (0x00) Conjunto de pacotes bem sucedidos criar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="0ef0c-1612">**NX_PTR_ERROR** (0x07) Piscina inválida ou ponteiro de memória.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="0ef0c-1613">**NX_SIZE_ERROR** (0x09) Bloco inválido ou tamanho da memória.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="0ef0c-1614">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1615">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1615">Allowed From</span></span>

<span data-ttu-id="0ef0c-1616">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1617">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1617">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1618">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1619">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1620">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1620">See Also</span></span>

- <span data-ttu-id="0ef0c-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="0ef0c-1624">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="0ef0c-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="0ef0c-1626">Eliminar piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1627">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1628">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1628">Description</span></span>

<span data-ttu-id="0ef0c-1629">Este serviço elimina uma piscina de pacotes previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="0ef0c-1630">NetX verifica quaisquer fios atualmente suspensos em pacotes na piscina de pacotes e limpa a suspensão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1631">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1631">Parameters</span></span>

- <span data-ttu-id="0ef0c-1632">**pool_ptr** Ponteiro do bloco de controlo da piscina de pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1633">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1633">Return Values</span></span>

- <span data-ttu-id="0ef0c-1634">**NX_SUCCESS** (0x00) Pacotes de sucesso eliminar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="0ef0c-1635">**NX_PTR_ERROR** (0x07) Ponteiro de piscina inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="0ef0c-1636">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1637">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1637">Allowed From</span></span>

<span data-ttu-id="0ef0c-1638">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1639">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1639">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1640">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1641">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1642">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1642">See Also</span></span>

- <span data-ttu-id="0ef0c-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1645">nx_packet_length_get, nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="0ef0c-1646">nx_packet_pool_info_get, nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="0ef0c-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="0ef0c-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="0ef0c-1649">Recuperar informações sobre uma piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1650">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1651">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1651">Description</span></span>

<span data-ttu-id="0ef0c-1652">Este serviço obtém informações sobre a piscina de pacotes especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="0ef0c-1653">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1654">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1654">Parameters</span></span>

- <span data-ttu-id="0ef0c-1655">**pool_ptr** Ponteiro para piscina de pacotes previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="0ef0c-1656">**total_packets** Ponteiro para destino para o número total de pacotes na piscina.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="0ef0c-1657">**free_packets** Ponteiro para o destino para o número total de pacotes atualmente gratuitos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="0ef0c-1658">**empty_pool_requests** Ponteiro para o destino do número total de pedidos de atribuição quando a piscina estava vazia.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="0ef0c-1659">**empty_pool_suspensions** Ponteiro para o destino do número total de suspensões de piscina vazias.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="0ef0c-1660">**invalid_packet_releases** Ponteiro para o destino do número total de lançamentos de pacotes inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1661">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1661">Return Values</span></span>

- <span data-ttu-id="0ef0c-1662">**NX_SUCCESS** (0x00) Recuperação de informações de piscina de pacotes bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="0ef0c-1663">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1664">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1665">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1665">Allowed From</span></span>

<span data-ttu-id="0ef0c-1666">Inicialização, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1667">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1667">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1668">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1669">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1670">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1670">See Also</span></span>

- <span data-ttu-id="0ef0c-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="0ef0c-1674">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="0ef0c-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1675">nx_packet_release</span></span>

<span data-ttu-id="0ef0c-1676">Liberação pacote previamente atribuído</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1677">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1678">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1678">Description</span></span>

<span data-ttu-id="0ef0c-1679">Este serviço liberta um pacote, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="0ef0c-1680">Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="0ef0c-1681">*O pedido deve impedir a libertação de um pacote mais de uma vez, porque fazê-lo irá causar resultados imprevisíveis.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1682">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1682">Parameters</span></span>

- <span data-ttu-id="0ef0c-1683">**packet_ptr** Ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-1684">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1684">Return Values</span></span>
- <span data-ttu-id="0ef0c-1685">**NX_SUCCESS** (0x00) Lançamento de pacote bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="0ef0c-1686">**NX_PTR_ERROR** (0x07) Ponteiro do pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1687">**NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="0ef0c-1688">**NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1689">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1689">Allowed From</span></span>

<span data-ttu-id="0ef0c-1690">Inicialização, fios, temporizadores e ISRs (controladores de rede de aplicações)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1691">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1691">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1692">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1693">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1694">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1694">See Also</span></span>

- <span data-ttu-id="0ef0c-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="0ef0c-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="0ef0c-1700">Liberte um pacote transmitido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1701">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1702">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1702">Description</span></span>

<span data-ttu-id="0ef0c-1703">Para pacotes não TCP, este serviço liberta um pacote transmitido, incluindo quaisquer pacotes adicionais acorrentados ao pacote especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="0ef0c-1704">Se outro fio for bloqueado na atribuição do pacote, é dado o pacote e retomado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="0ef0c-1705">Para um pacote TCP transmitido, o pacote é marcado como sendo transmitido, mas não libertado até que o pacote seja reconhecido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="0ef0c-1706">Este serviço é normalmente chamado do controlador de rede da aplicação após a transmissão de um pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="0ef0c-1707">*O controlador de rede deve remover o cabeçalho dos meios de comunicação físicos e ajustar o comprimento do pacote antes de ligar para este serviço.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1708">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1708">Parameters</span></span>

- <span data-ttu-id="0ef0c-1709">**packet_ptr** Ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1710">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1710">Return Values</span></span>

- <span data-ttu-id="0ef0c-1711">**NX_SUCCESS** (0x00) Libertação bem sucedida do pacote de transmissão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="0ef0c-1712">**NX_PTR_ERROR** (0x07) Ponteiro do pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="0ef0c-1713">**NX_UNDERFLOW** (0x02) O ponteiro prepend é inferior ao arranque da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="0ef0c-1714">**NX_OVERFLOW** (0x03) O ponteiro do apêndice é maior do que a extremidade da carga útil.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1715">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1715">Allowed From</span></span>

<span data-ttu-id="0ef0c-1716">Inicialização, fios, temporizadores, controladores de rede de aplicações (incluindo ISRs)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1717">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1717">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1718">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1719">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1720">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1720">See Also</span></span>

- <span data-ttu-id="0ef0c-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="0ef0c-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="0ef0c-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="0ef0c-1724">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="0ef0c-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1725">nx_rarp_disable</span></span>

<span data-ttu-id="0ef0c-1726">Desativar o Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1727">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1728">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1728">Description</span></span>

<span data-ttu-id="0ef0c-1729">Este serviço desativa o componente RARP do NetX para a instância IP específica.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="0ef0c-1730">Para um sistema multihome, este serviço desativa o RARP em todas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1731">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1731">Parameters</span></span>

- <span data-ttu-id="0ef0c-1732">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1733">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1733">Return Values</span></span>

- <span data-ttu-id="0ef0c-1734">**NX_SUCCESS** (0x00) RaRP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="0ef0c-1735">**NX_NOT_ENABLED** (0x14) RARP não estava ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="0ef0c-1736">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1737">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1738">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1738">Allowed From</span></span>

<span data-ttu-id="0ef0c-1739">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1740">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1740">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1741">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1742">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1743">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1743">See Also</span></span>

- <span data-ttu-id="0ef0c-1744">nx_rarp_enable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="0ef0c-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1745">nx_rarp_enable</span></span>

<span data-ttu-id="0ef0c-1746">Ativar o Protocolo de Resolução de Endereços Reversos (RARP)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1747">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1748">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1748">Description</span></span>

<span data-ttu-id="0ef0c-1749">Este serviço permite o componente RARP do NetX para a instância IP específica.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="0ef0c-1750">Os componentes RARP procuram através de todas as interfaces de rede anexas para um endereço IP zero.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="0ef0c-1751">Um endereço IP zero indica que a interface ainda não tem a atribuição de endereço IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="0ef0c-1752">A RARP tenta resolver o endereço IP, permitindo o processo RARP nessa interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1753">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1753">Parameters</span></span>

- <span data-ttu-id="0ef0c-1754">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1755">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1755">Return Values</span></span>

- <span data-ttu-id="0ef0c-1756">**NX_SUCCESS** (0x00) RARP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="0ef0c-1757">**NX_IP_ADDRESS_ERROR** endereço IP (0x21) já é válido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="0ef0c-1758">**NX_ALREADY_ENABLED** (0x15) RARP já estava ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="0ef0c-1759">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1760">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1761">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1761">Allowed From</span></span>

<span data-ttu-id="0ef0c-1762">Inicialização, fios, temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1763">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1763">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1764">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1765">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1766">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1766">See Also</span></span>

- <span data-ttu-id="0ef0c-1767">nx_rarp_disable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="0ef0c-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="0ef0c-1769">Recuperar informações sobre as atividades da RARP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1770">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1771">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1771">Description</span></span>

<span data-ttu-id="0ef0c-1772">Este serviço obtém informações sobre as atividades da RARP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-1773">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1774">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1774">Parameters</span></span>

- <span data-ttu-id="0ef0c-1775">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1776">**rarp_requests_sent** Ponteiro para destino para o número total de pedidos de RARP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="0ef0c-1777">**rarp_responses_received** Ponteiro para destino para o número total de respostas RARP recebidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="0ef0c-1778">**rarp_invalid_messages** Ponteiro para o destino do número total de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-1779">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1779">Return Values</span></span>
- <span data-ttu-id="0ef0c-1780">**NX_SUCCESS** (0x00) Recuperação de informações rarp bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-1781">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1782">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-1783">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1784">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1784">Allowed From</span></span>

<span data-ttu-id="0ef0c-1785">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1786">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1786">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1787">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1788">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1789">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1789">See Also</span></span>

- <span data-ttu-id="0ef0c-1790">nx_rarp_disable, nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="0ef0c-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1791">nx_system_initialize</span></span>

<span data-ttu-id="0ef0c-1792">Inicializar o Sistema NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1793">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1794">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1794">Description</span></span>

<span data-ttu-id="0ef0c-1795">Este serviço inicializa os recursos básicos do sistema NetX em preparação para utilização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="0ef0c-1796">Deve ser chamado pela aplicação durante a inicialização e antes de qualquer outra chamada NetX ser feita.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1797">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1797">Parameters</span></span>

<span data-ttu-id="0ef0c-1798">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1799">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1799">Return Values</span></span>

<span data-ttu-id="0ef0c-1800">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1801">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1801">Allowed From</span></span>

<span data-ttu-id="0ef0c-1802">Inicialização, fios, temporizadores, ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1803">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1803">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1804">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1805">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1806">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1806">See Also</span></span>

- <span data-ttu-id="0ef0c-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="0ef0c-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="0ef0c-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="0ef0c-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="0ef0c-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="0ef0c-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="0ef0c-1813">Ligação da tomada TCP do cliente à porta TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1814">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1815">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1815">Description</span></span>

<span data-ttu-id="0ef0c-1816">Este serviço liga a tomada do cliente TCP previamente criada à porta TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="0ef0c-1817">As tomadas TCP válidas variam de 0 a 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="0ef0c-1818">Se a porta TCP especificada não estiver disponível, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1819">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1819">Parameters</span></span>

- <span data-ttu-id="0ef0c-1820">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-1821">**porto** Número da porta para ligar (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="0ef0c-1822">Se o número da porta for NX_ANY_PORT (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="0ef0c-1823">**wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="0ef0c-1824">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1827">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1828">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1828">Return Values</span></span>

- <span data-ttu-id="0ef0c-1829">**NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="0ef0c-1830">**NX_ALREADY_BOUND** (0x22) Esta tomada já está ligada a outra porta TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="0ef0c-1831">**NX_PORT_UNAVAILABLE** (0x23) O porto já está ligado a uma tomada diferente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="0ef0c-1832">**NX_NO_FREE_PORTS** (0x45) Não há porta livre.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="0ef0c-1833">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="0ef0c-1834">**porta NX_INVALID_PORT** (0x46) Inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="0ef0c-1835">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-1836">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1837">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1838">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1838">Allowed From</span></span>

<span data-ttu-id="0ef0c-1839">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1840">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1840">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1841">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1842">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1843">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1843">See Also</span></span>

- <span data-ttu-id="0ef0c-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="0ef0c-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="0ef0c-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="0ef0c-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="0ef0c-1855">Ligue a tomada TCP do cliente</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1856">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1857">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1857">Description</span></span>

<span data-ttu-id="0ef0c-1858">Este serviço liga a tomada do cliente TCP previamente criada e ligada à porta do servidor especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="0ef0c-1859">As portas de servidores TCP válidas variam de 0 a 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="0ef0c-1860">Se a ligação não estiver concluída imediatamente, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1861">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1861">Parameters</span></span>

- <span data-ttu-id="0ef0c-1862">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-1863">**server_ip** O endereço IP do servidor.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="0ef0c-1864">**server_port** Número da porta do servidor para ligar (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="0ef0c-1865">**wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="0ef0c-1866">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-1869">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1870">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1870">Return Values</span></span>

- <span data-ttu-id="0ef0c-1871">**NX_SUCCESS** (0x00) Ligação de tomadas bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="0ef0c-1872">**NX_NOT_BOUND** (0x24) A tomada não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="0ef0c-1873">**NX_NOT_CLOSED** (0x35) A tomada não se encontra fechada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="0ef0c-1874">**NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, a tentativa de ligação está em curso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="0ef0c-1875">**NX_INVALID_INTERFACE** (0x4C) Interface inválida fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="0ef0c-1876">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-1877">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP do servidor inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="0ef0c-1878">**porta NX_INVALID_PORT** (0x46) Inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="0ef0c-1879">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-1880">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1881">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1882">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1882">Allowed From</span></span>

<span data-ttu-id="0ef0c-1883">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1884">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1884">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1885">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1886">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1887">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1887">See Also</span></span>

- <span data-ttu-id="0ef0c-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="0ef0c-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="0ef0c-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="0ef0c-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="0ef0c-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="0ef0c-1899">Obtenha o número da porta vinculado à tomada TCP do cliente</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1900">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1901">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1901">Description</span></span>

<span data-ttu-id="0ef0c-1902">Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1903">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1903">Parameters</span></span>

- <span data-ttu-id="0ef0c-1904">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-1905">**port_ptr** Ponteiro para o destino para o número da porta de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="0ef0c-1906">Os números de porta válidos são (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1907">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1907">Return Values</span></span>

- <span data-ttu-id="0ef0c-1908">**NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="0ef0c-1909">**NX_NOT_BOUND** (0x24) Esta tomada não está ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="0ef0c-1910">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida ou ponteiro de retorno da porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="0ef0c-1911">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1912">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1913">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1913">Allowed From</span></span>

<span data-ttu-id="0ef0c-1914">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1915">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1915">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1916">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1917">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1918">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1918">See Also</span></span>

- <span data-ttu-id="0ef0c-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="0ef0c-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="0ef0c-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="0ef0c-1930">Tomada de cliente unbind TCP da porta TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1931">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1932">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1932">Description</span></span>

<span data-ttu-id="0ef0c-1933">Este serviço liberta a encadernação entre a tomada do cliente TCP e uma porta TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="0ef0c-1934">Se houver outros fios à espera de ligar outra tomada ao mesmo número de porta, o primeiro fio suspenso fica ligado a esta porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1935">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1935">Parameters</span></span>

- <span data-ttu-id="0ef0c-1936">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1937">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1937">Return Values</span></span>

- <span data-ttu-id="0ef0c-1938">**NX_SUCCESS** (0x00) Tomada desaderada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="0ef0c-1939">**NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="0ef0c-1940">**NX_NOT_CLOSED** (0x35) A tomada não foi desligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="0ef0c-1941">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-1942">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-1943">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1944">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1944">Allowed From</span></span>

<span data-ttu-id="0ef0c-1945">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1946">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1946">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1947">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1948">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1949">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1949">See Also</span></span>

- <span data-ttu-id="0ef0c-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="0ef0c-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="0ef0c-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1960">nx_tcp_enable</span></span>

<span data-ttu-id="0ef0c-1961">Ativar o componente TCP do NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1962">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1963">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1963">Description</span></span>

<span data-ttu-id="0ef0c-1964">Este serviço permite o componente do Protocolo de Controlo de Transmissão (TCP) do NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="0ef0c-1965">Após ativação, as ligações TCP podem ser estabelecidas pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1966">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1966">Parameters</span></span>

- <span data-ttu-id="0ef0c-1967">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-1968">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1968">Return Values</span></span>

- <span data-ttu-id="0ef0c-1969">**NX_SUCCESS** (0x00) TCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="0ef0c-1970">**NX_ALREADY_ENABLED** (0x15) TCP já está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="0ef0c-1971">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-1972">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-1973">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1973">Allowed From</span></span>

<span data-ttu-id="0ef0c-1974">Inicialização, fios, temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-1975">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1975">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-1976">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-1977">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-1978">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1978">See Also</span></span>

- <span data-ttu-id="0ef0c-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="0ef0c-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="0ef0c-1990">Encontre a próxima porta TCP disponível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-1991">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-1992">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1992">Description</span></span>

<span data-ttu-id="0ef0c-1993">Este serviço tenta localizar uma porta TCP gratuita (desvinculada) a partir da porta fornecida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="0ef0c-1994">A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="0ef0c-1995">Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="0ef0c-1996">*Este serviço pode ser chamado de outro fio e ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada do cliente em si liga-se sob a proteção de um mutex.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-1997">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1997">Parameters</span></span>

- <span data-ttu-id="0ef0c-1998">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-1999">**porto** Número da porta para iniciar a pesquisa em (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="0ef0c-2000">**free_port_ptr** Ponteiro para o destino valor de retorno de porto livre.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2001">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2001">Return Values</span></span>

- <span data-ttu-id="0ef0c-2002">**NX_SUCCESS** (0x00) Achado de porta livre com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="0ef0c-2003">**NX_NO_FREE_PORTS** (0x45) Não foram encontradas portas livres.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="0ef0c-2004">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2005">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2006">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-2007">**NX_INVALID_PORT** (0x46) O número de porta especificado é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2008">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2008">Allowed From</span></span>

<span data-ttu-id="0ef0c-2009">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2010">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2010">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2011">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2012">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2013">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2013">See Also</span></span>

- <span data-ttu-id="0ef0c-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="0ef0c-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="0ef0c-2025">Recuperar informações sobre atividades da TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2026">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2027">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2027">Description</span></span>

<span data-ttu-id="0ef0c-2028">Este serviço obtém informações sobre as atividades da TCP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-2029">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2030">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2030">Parameters</span></span>

- <span data-ttu-id="0ef0c-2031">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2032">**tcp_packets_sent** Ponteiro para o destino para o número total de pacotes TCP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="0ef0c-2033">**tcp_bytes_sent** Ponteiro para o destino para o número total de bytes TCP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="0ef0c-2034">**tcp_packets_received** Ponteiro para o destino do número total de pacotes TCP recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="0ef0c-2035">**tcp_bytes_received** Ponteiro para o destino do número total de bytes TCP recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="0ef0c-2036">**tcp_invalid_packets** Ponteiro para o destino do número total de pacotes TCP inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="0ef0c-2037">**tcp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção TCP caiu.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="0ef0c-2038">**tcp_checksum_errors** Ponteiro para o destino do número total de pacotes TCP com erros de checkum.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="0ef0c-2039">**tcp_connections** Ponteiro para o destino do número total de ligações TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="0ef0c-2040">**tcp_disconnections** Ponteiro para o destino do número total de desconexões TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="0ef0c-2041">**tcp_connections_dropped** O ponteiro para o destino do número total de ligações TCP diminuiu.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="0ef0c-2042">**tcp_retransmit_packets** Ponteiro para o destino do número total de pacotes TCP retransmiitados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2043">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2043">Return Values</span></span>

- <span data-ttu-id="0ef0c-2044">**NX_SUCCESS** (0x00) Recuperação de informação bem sucedida da TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-2045">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2046">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2047">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2048">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2048">Allowed From</span></span>

<span data-ttu-id="0ef0c-2049">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2050">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2050">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2051">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2052">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2053">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2053">See Also</span></span>

- <span data-ttu-id="0ef0c-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="0ef0c-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="0ef0c-2065">Aceitar ligação TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2066">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2067">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2067">Description</span></span>

<span data-ttu-id="0ef0c-2068">Este serviço aceita (ou prepara-se para aceitar) um pedido de ligação ao cliente TCP para uma porta previamente configurada para escuta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="0ef0c-2069">Este serviço pode ser chamado imediatamente após a aplicação chamar o serviço de escuta ou de re-escuta, ou depois de a rotina de chamada de escuta ser chamada quando a ligação do cliente estiver realmente presente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="0ef0c-2070">Se uma ligação não puder ser estabelecida imediatamente, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="0ef0c-2071">*A aplicação deve ligar **nx_tcp_server_socket_unaccept** depois de a ligação já não ser necessária para remover a ligação da tomada do servidor à porta do servidor.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="0ef0c-2072">*As rotinas de chamada de aplicação são chamadas de dentro do fio de ajuda do IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2073">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2073">Parameters</span></span>

- <span data-ttu-id="0ef0c-2074">**socket_ptr** Ponteiro para o bloco de controlo da tomada do servidor TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="0ef0c-2075">**wait_option** Define como o serviço se comporta enquanto a ligação está sendo estabelecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="0ef0c-2076">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2079">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-2080">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2080">Return Values</span></span>
- <span data-ttu-id="0ef0c-2081">**NX_SUCCESS** (0x00) A tomada do servidor TCP bem sucedida aceita (ligação passiva).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="0ef0c-2082">**NX_NOT_LISTEN_STATE** (0x36) A tomada do servidor fornecida não está num estado de escuta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="0ef0c-2083">**NX_IN_PROGRESS** (0x37) Não foi especificada qualquer espera, a tentativa de ligação está em curso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="0ef0c-2084">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="0ef0c-2085">**NX_PTR_ERROR** (0x07) Erro do ponteiro da tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="0ef0c-2086">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2087">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2088">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2088">Allowed From</span></span>

<span data-ttu-id="0ef0c-2089">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2090">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2090">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2091">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2092">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2093">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2093">See Also</span></span>

- <span data-ttu-id="0ef0c-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="0ef0c-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="0ef0c-2105">Ativar a escuta da ligação do cliente na porta TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2106">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2107">Description</span></span>

<span data-ttu-id="0ef0c-2108">Este serviço permite ouvir um pedido de ligação ao cliente na porta TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="0ef0c-2109">Quando um pedido de ligação ao cliente é recebido, a tomada do servidor fornecida fica ligada à porta especificada e a função de chamada de chamada de chamada de ouvido fornecida é chamada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="0ef0c-2110">O processamento da rotina de chamada de escuta está completamente à altura da aplicação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="0ef0c-2111">Pode conter lógica para acordar um fio de aplicação que posteriormente executa uma operação de aceitação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="0ef0c-2112">Se a aplicação já tiver um fio suspenso no processamento de aceitação para esta tomada, a rotina de chamada de escuta pode não ser necessária.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="0ef0c-2113">Se a aplicação pretender manusear ligações adicionais ao cliente na mesma porta, o ***nx_tcp_server_socket_relisten*** deve ser chamado com uma tomada disponível (uma tomada no estado FECHADO) para a próxima ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="0ef0c-2114">Até que o serviço de re-ouvir seja chamado, as ligações adicionais do cliente são em fila.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="0ef0c-2115">Quando a profundidade máxima da fila é excedida, o pedido de ligação mais antigo é retirado a favor da fila do novo pedido de ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="0ef0c-2116">A profundidade máxima da fila é especificada por este serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="0ef0c-2117">*As rotinas de chamada de aplicação são chamadas a partir do fio interno do ajudante IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2118">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2118">Parameters</span></span>

- <span data-ttu-id="0ef0c-2119">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2120">**porto** Número da porta para ouvir (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="0ef0c-2121">**socket_ptr** Ponteiro para tomada a utilizar para a ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="0ef0c-2122">**listen_queue_size** Número de pedidos de ligação ao cliente que podem ser na fila.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="0ef0c-2123">**listen_callback** Função de aplicação para ligar quando a ligação é recebida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="0ef0c-2124">Se for especificado um NU, a função de chamada de escuta é desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2125">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2125">Return Values</span></span>

- <span data-ttu-id="0ef0c-2126">**NX_SUCCESS** (0x00) Porta TCP bem sucedida ouvir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="0ef0c-2127">**NX_MAX_LISTEN** (0x33) Não há mais estruturas de pedido de escuta disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="0ef0c-2128">A NX_MAX_LISTEN_REQUESTS constante em nx_api.h define quantos pedidos de escuta ativa são possíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="0ef0c-2129">**NX_NOT_CLOSED** (0x35) A tomada do servidor fornecida não está fechada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="0ef0c-2130">**NX_ALREADY_BOUND** (0x22) A tomada do servidor fornecida já está ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="0ef0c-2131">**NX_DUPLICATE_LISTEN** (0x34) Já existe um pedido de escuta ativo para este porto.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="0ef0c-2132">**NX_INVALID_PORT** (0x46) Porta inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="0ef0c-2133">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2134">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2135">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2136">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2136">Allowed From</span></span>

<span data-ttu-id="0ef0c-2137">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2138">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2138">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2139">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2141">See Also</span></span>

- <span data-ttu-id="0ef0c-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="0ef0c-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="0ef0c-2153">Re-ouvir a ligação do cliente na porta TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2154">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2155">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2155">Description</span></span>

<span data-ttu-id="0ef0c-2156">Este serviço é chamado depois de ter sido recebida uma ligação numa porta que foi configurada anteriormente para escuta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="0ef0c-2157">O principal objetivo deste serviço é fornecer uma nova tomada de servidor para a próxima ligação ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="0ef0c-2158">Se um pedido de ligação for feito em fila, a ligação será processada imediatamente durante esta chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="0ef0c-2159">*A mesma rotina de chamada especificada pelo pedido de escuta original também é chamada quando existe uma ligação para esta nova tomada do servidor.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2160">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2160">Parameters</span></span>

- <span data-ttu-id="0ef0c-2161">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2162">**porto** Número da porta para voltar a ouvir (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="0ef0c-2163">**socket_ptr** Tomada para utilizar para a próxima ligação ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2164">Return Values</span></span>
- <span data-ttu-id="0ef0c-2165">**NX_SUCCESS** (0x00) Porta TCP bem sucedida a ouvir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="0ef0c-2166">**NX_NOT_CLOSED** (0x35) A tomada do servidor fornecida não está fechada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="0ef0c-2167">**NX_ALREADY_BOUND** (0x22) A tomada do servidor fornecida já está ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="0ef0c-2168">**NX_INVALID_RELISTEN** (0x47) Já existe um ponteiro de tomada válido para esta porta ou a porta especificada não tem um pedido de escuta ativo.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="0ef0c-2169">**NX_CONNECTION_PENDING** (0x48) O mesmo que NX_SUCCESS, exceto que houve um pedido de ligação em fila e foi processado durante esta chamada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="0ef0c-2170">**NX_INVALID_PORT** (0x46) Porta inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="0ef0c-2171">**NX_PTR_ERROR** (0x07) IP inválido ou ouvir o ponteiro de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="0ef0c-2172">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2173">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2174">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2174">Allowed From</span></span>

<span data-ttu-id="0ef0c-2175">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2176">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2176">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2177">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2179">See Also</span></span>

- <span data-ttu-id="0ef0c-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="0ef0c-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="0ef0c-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="0ef0c-2191">Remova a associação da tomada com a porta de escuta</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2192">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2193">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2193">Description</span></span>

<span data-ttu-id="0ef0c-2194">Este serviço remove a associação entre esta tomada do servidor e a porta do servidor especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="0ef0c-2195">O pedido deve ligar para este serviço após uma desconexão ou após uma chamada de aceitação infrutífera.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2196">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2196">Parameters</span></span>

- <span data-ttu-id="0ef0c-2197">**socket_ptr** Ponteiro para a instância de tomada do servidor previamente configurada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2198">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2198">Return Values</span></span>

- <span data-ttu-id="0ef0c-2199">**NX_SUCCESS** (0x00) Tomada de servidor bem sucedida não acepte.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="0ef0c-2200">**NX_NOT_LISTEN_STATE** (0x36) A tomada do servidor encontra-se num estado impróprio e provavelmente não está desligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="0ef0c-2201">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2202">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2203">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2204">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2204">Allowed From</span></span>

<span data-ttu-id="0ef0c-2205">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2206">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2206">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2207">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2209">See Also</span></span>

- <span data-ttu-id="0ef0c-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="0ef0c-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="0ef0c-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="0ef0c-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="0ef0c-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="0ef0c-2220">Desativar a escuta da ligação ao cliente na porta TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2221">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2222">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2222">Description</span></span>

<span data-ttu-id="0ef0c-2223">Este serviço desativa a audição de um pedido de ligação ao cliente na porta TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2224">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2224">Parameters</span></span>

- <span data-ttu-id="0ef0c-2225">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2226">**porto** Número de portas para desativar a audição (0 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2227">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2227">Return Values</span></span>

- <span data-ttu-id="0ef0c-2228">**NX_SUCCESS** (0x00) TCP bem sucedido ouvir desativar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="0ef0c-2229">**NX_ENTRY_NOT_FOUND** (0x16) A audição não estava ativada para a porta especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="0ef0c-2230">**NX_INVALID_PORT** (0x46) Porta inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="0ef0c-2231">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2232">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2233">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2234">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2234">Allowed From</span></span>

<span data-ttu-id="0ef0c-2235">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2236">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2236">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2237">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2239">See Also</span></span>

- <span data-ttu-id="0ef0c-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="0ef0c-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="0ef0c-2251">Recupera o número de bytes disponíveis para recuperação</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2252">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2253">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2253">Description</span></span>

<span data-ttu-id="0ef0c-2254">Este serviço obtém o número de bytes disponíveis para recuperação na tomada TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="0ef0c-2255">Note que a tomada TCP já deve estar ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2256">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2256">Parameters</span></span>

- <span data-ttu-id="0ef0c-2257">**socket_ptr** Ponteiro para tomada TCP previamente criada e conectada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2258">**bytes_available** Ponteiro para destino para bytes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2259">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2259">Return Values</span></span>

- <span data-ttu-id="0ef0c-2260">**NX_SUCCESS** (0x00) O Serviço executa com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="0ef0c-2261">O número de bytes disponíveis para leitura é devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="0ef0c-2262">**NX_NOT_CONNECTED** (0x38) A tomada não se encontra ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="0ef0c-2263">**NX_PTR_ERROR** (0x07) Ponteiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="0ef0c-2264">**NX_NOT_ENABLED** (0x14) TCP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-2265">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2266">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2266">Allowed From</span></span>

<span data-ttu-id="0ef0c-2267">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2268">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2268">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2269">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2270">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2271">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2271">See Also</span></span>

- <span data-ttu-id="0ef0c-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="0ef0c-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="0ef0c-2283">Criar tomada de cliente TCP ou servidor</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2284">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2285">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2285">Description</span></span>

<span data-ttu-id="0ef0c-2286">Este serviço cria um cliente TCP ou tomada de servidor para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-2287">*As rotinas de chamada de aplicação são chamadas a partir do fio associado a esta instância IP.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2288">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2288">Parameters</span></span>

- <span data-ttu-id="0ef0c-2289">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2290">**socket_ptr** Ponteiro para o novo bloco de controlo da tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="0ef0c-2291">**nome** Nome da aplicação para esta tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2292">**type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="0ef0c-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="0ef0c-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="0ef0c-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="0ef0c-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="0ef0c-2298">**fragmento**  Especifica se é permitida a fragmentação ip.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="0ef0c-2299">Se NX_FRAGMENT_OKAY (0x0) for especificado, é permitida a fragmentação ip.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="0ef0c-2300">Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="0ef0c-2301">**time_to_live** Especifica o valor de 8 bits que define quantos routers este pacote pode passar antes de ser jogado fora.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="0ef0c-2302">O valor predefinido é especificado por NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="0ef0c-2303">**window_size** Define o número máximo de bytes permitidos na fila de receção para esta tomada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="0ef0c-2304">**urgent_data_callback** Função de aplicação que é chamada sempre que os dados urgentes são detetados no fluxo de receção.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="0ef0c-2305">Se este valor for NX_NULL, os dados urgentes são ignorados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="0ef0c-2306">**disconnect_callback** Função de aplicação que é chamada sempre que uma desconexão é emitida pela tomada na outra extremidade da ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="0ef0c-2307">Se este valor for NX_NULL, a função de desconexão é desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2308">Return Values</span></span>
- <span data-ttu-id="0ef0c-2309">**NX_SUCCESS** (0x00) Tomada de cliente bem sucedida da TCP criar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="0ef0c-2310">**NX_OPTION_ERROR** (0x0A) Tipo de serviço inválido, fragmento, tamanho da janela inválido ou opção de tempo-tolive.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="0ef0c-2311">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2312">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2313">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2314">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2314">Allowed From</span></span>

<span data-ttu-id="0ef0c-2315">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2316">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2316">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2317">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2318">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2319">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2319">See Also</span></span>

- <span data-ttu-id="0ef0c-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="0ef0c-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="0ef0c-2331">Eliminar tomada TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2333">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2333">Description</span></span>

<span data-ttu-id="0ef0c-2334">Este serviço elimina uma tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="0ef0c-2335">Se a tomada ainda estiver ligada ou ligada, o serviço devolve um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2336">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2336">Parameters</span></span>

- <span data-ttu-id="0ef0c-2337">**socket_ptr** Tomada TCP previamente criada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2338">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2338">Return Values</span></span>

- <span data-ttu-id="0ef0c-2339">**NX_SUCCESS** (0x00) Apagar a tomada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="0ef0c-2340">**NX_NOT_CREATED** (0x27) Tomada não foi criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="0ef0c-2341">**NX_STILL_BOUND** (0x42) A tomada ainda está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="0ef0c-2342">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2343">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2344">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2345">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2345">Allowed From</span></span>

<span data-ttu-id="0ef0c-2346">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2347">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2347">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2348">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2349">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2350">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2350">See Also</span></span>

- <span data-ttu-id="0ef0c-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="0ef0c-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="0ef0c-2362">Desligue as ligações de tomada de cliente e servidor</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2363">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2364">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2364">Description</span></span>

<span data-ttu-id="0ef0c-2365">Este serviço desliga uma ligação estabelecida de tomada de cliente ou servidor.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="0ef0c-2366">Uma desconexão de uma tomada do servidor deve ser seguida por um pedido não aceite, enquanto uma tomada de cliente desligada é deixada num estado pronto para outro pedido de ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="0ef0c-2367">Se o processo de desconexão não puder terminar imediatamente, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2368">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2368">Parameters</span></span>

- <span data-ttu-id="0ef0c-2369">**socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="0ef0c-2370">**wait_option** Define como o serviço se comporta enquanto a desconexão está em curso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="0ef0c-2371">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2374">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2375">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2375">Return Values</span></span>

- <span data-ttu-id="0ef0c-2376">**NX_SUCCESS** (0x00) Desconexão de tomadas com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="0ef0c-2377">**NX_NOT_CONNECTED** (0x38) A tomada especificada não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="0ef0c-2378">**NX_IN_PROGRESS** (0x37) A desconexão está em curso, não foi especificada qualquer espera.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="0ef0c-2379">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-2380">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2381">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2382">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2383">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2383">Allowed From</span></span>

<span data-ttu-id="0ef0c-2384">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2385">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2385">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2386">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2387">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2388">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2388">See Also</span></span>

- <span data-ttu-id="0ef0c-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="0ef0c-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="0ef0c-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="0ef0c-2399">Instalar a desconexão TCP completa notificar a função de retorno</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2400">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2401">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2401">Description</span></span>

<span data-ttu-id="0ef0c-2402">Este serviço regista uma função de retorno que é invocada após a conclusão de uma operação de desconexão da tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="0ef0c-2403">A função de chamada completa da tomada TCP está disponível se o NetX for construído com a opção</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="0ef0c-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2405">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2405">Parameters</span></span>

- <span data-ttu-id="0ef0c-2406">**socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="0ef0c-2407">**tcp_disconnect_complete_notify** A função de retorno a instalar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2408">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2408">Return Values</span></span>
- <span data-ttu-id="0ef0c-2409">**NX_SUCCESS** (0x00) registou com sucesso a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="0ef0c-2410">**NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação alargada não está incorporada na biblioteca NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="0ef0c-2411">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2412">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2413">**NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2414">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2414">Allowed From</span></span>

<span data-ttu-id="0ef0c-2415">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2416">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2416">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2417">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2418">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2419">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2419">See Also</span></span>

- <span data-ttu-id="0ef0c-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="0ef0c-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="0ef0c-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="0ef0c-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2424">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="0ef0c-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="0ef0c-2427">Definir TCP estabelecer notificação função de retorno</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2428">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2429">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2429">Description</span></span>

<span data-ttu-id="0ef0c-2430">Este serviço regista uma função de retorno, que é chamada depois de uma tomada TCP fazer uma ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="0ef0c-2431">A tomada TCP estabelece a função de retorno de chamada se o NetX for construído com a opção ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** definida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2432">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2432">Parameters</span></span>

- <span data-ttu-id="0ef0c-2433">**socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="0ef0c-2434">**tcp_establish_notify** Função de retorno invocada após a criação de uma ligação TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2435">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2435">Return Values</span></span>

- <span data-ttu-id="0ef0c-2436">**NX_SUCCESS** (0x00) define com sucesso a função de notificação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="0ef0c-2437">**NX_NOT_SUPPORTED** (0x4B) A funcionalidade de notificação alargada não está incorporada na biblioteca NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="0ef0c-2438">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2439">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2440">**NX_NOT_ENABLED** (0x14) TCP não foi habilitado pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2441">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2441">Allowed From</span></span>

<span data-ttu-id="0ef0c-2442">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2443">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2443">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2444">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2445">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2446">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2446">See Also</span></span>

- <span data-ttu-id="0ef0c-2447">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="0ef0c-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="0ef0c-2454">Recuperar informações sobre as atividades da tomada de TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2455">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2456">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2456">Description</span></span>

<span data-ttu-id="0ef0c-2457">Este serviço obtém informações sobre as atividades da tomada TCP para a instância de tomada TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="0ef0c-2458">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2459">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2459">Parameters</span></span>

- <span data-ttu-id="0ef0c-2460">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-2461">**tcp_packets_sent** Ponteiro para o destino para o número total de pacotes TCP enviados na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="0ef0c-2462">**tcp_bytes_sent** Ponteiro para destino para o número total de bytes TCP enviados na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="0ef0c-2463">**tcp_packets_received** Ponteiro para o destino do número total de pacotes TCP recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="0ef0c-2464">**tcp_bytes_received** Ponteiro para o destino do número total de bytes TCP recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="0ef0c-2465">**tcp_retransmit_packets** Ponteiro para o destino do número total de retransmissão de pacotes TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="0ef0c-2466">**tcp_packets_queued** Ponteiro para o destino do número total de pacotes TCP em fila na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="0ef0c-2467">**tcp_checksum_errors** Ponteiro para o destino do número total de pacotes TCP com erros de verificação na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="0ef0c-2468">**tcp_socket_state** Ponteiro para o destino do estado atual da tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="0ef0c-2469">**tcp_transmit_queue_depth** Ponteiro para o destino do número total de pacotes de transmissão ainda em fila à espera de ACK.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="0ef0c-2470">**tcp_transmit_window** Ponteiro para o destino do tamanho atual da janela de transmissão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="0ef0c-2471">**tcp_receive_window** Ponteiro para o destino da corrente receber o tamanho da janela.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2472">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2472">Return Values</span></span>

- <span data-ttu-id="0ef0c-2473">**NX_SUCCESS** (0x00) Recuperação de informações de tomadas TCP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="0ef0c-2474">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2475">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2476">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2477">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2478">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2478">Allowed From</span></span>

<span data-ttu-id="0ef0c-2479">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2480">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2480">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2481">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2482">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2483">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2483">See Also</span></span>

- <span data-ttu-id="0ef0c-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="0ef0c-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="0ef0c-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="0ef0c-2494">Obtenha MSS de tomada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2495">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2496">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2496">Description</span></span>

<span data-ttu-id="0ef0c-2497">Este serviço recupera o tamanho máximo de segmento local (MSS) da tomada especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2498">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2498">Parameters</span></span>

- <span data-ttu-id="0ef0c-2499">**socket_ptr** Ponteiro para tomada previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="0ef0c-2500">**mss** Destino para o regresso da MSS.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2501">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2501">Return Values</span></span>

- <span data-ttu-id="0ef0c-2502">**NX_SUCCESS** (0x00) MSS bem sucedidos obtêm.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="0ef0c-2503">**NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro de destino MSS.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="0ef0c-2504">**NX_NOT_ENABLED** (0x14) TCP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-2505">**NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2506">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2506">Allowed From</span></span>

<span data-ttu-id="0ef0c-2507">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2508">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2508">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2509">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2510">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2511">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2511">See Also</span></span>

- <span data-ttu-id="0ef0c-2512">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2513">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="0ef0c-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="0ef0c-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2517">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="0ef0c-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="0ef0c-2520">Obtenha MSS da tomada TCP par</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2521">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2522">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2522">Description</span></span>

<span data-ttu-id="0ef0c-2523">Este serviço recupera o Tamanho Máximo do Segmento (MSS) anunciado pela tomada de pares.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2524">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2524">Parameters</span></span>

- <span data-ttu-id="0ef0c-2525">**socket_ptr** Ponteiro para tomada previamente criada e conectada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="0ef0c-2526">**mss** Destino para devolver o MSS.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-2527">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2527">Return Values</span></span>

- <span data-ttu-id="0ef0c-2528">**NX_SUCCESS** (0x00) MSS de sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="0ef0c-2529">**NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro de destino MSS.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="0ef0c-2530">**NX_NOT_ENABLED** (0x14) TCP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-2531">**NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2532">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2532">Allowed From</span></span>

<span data-ttu-id="0ef0c-2533">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2534">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2534">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2535">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2536">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2537">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2537">See Also</span></span>

- <span data-ttu-id="0ef0c-2538">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2539">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="0ef0c-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2543">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="0ef0c-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="0ef0c-2546">Definir MSS de tomada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2547">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2548">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2548">Description</span></span>

<span data-ttu-id="0ef0c-2549">Este serviço define o tamanho máximo do segmento da tomada especificada (MSS).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="0ef0c-2550">Note que o valor MSS deve estar dentro da interface de rede IP MTU, permitindo espaço para cabeçalhos IP e TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="0ef0c-2551">Este serviço deve ser utilizado antes de uma tomada TCP iniciar o processo de ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="0ef0c-2552">Se o serviço for utilizado após a criação de uma ligação TCP, o novo valor não tem qualquer efeito na ligação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2553">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2553">Parameters</span></span>

- <span data-ttu-id="0ef0c-2554">**socket_ptr** Ponteiro para tomada previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="0ef0c-2555">**mss** Valor da MSS para definir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2556">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2556">Return Values</span></span>

- <span data-ttu-id="0ef0c-2557">**NX_SUCCESS** (0x00) Conjunto MSS bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="0ef0c-2558">**NX_SIZE_ERROR** (0x09) O valor especificado de MSS é demasiado elevado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="0ef0c-2559">**NX_NOT_CONNECTED** (0x38) A ligação TCP não foi estabelecida</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="0ef0c-2560">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2561">**NX_NOT_ENABLED** (0x14) TCP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-2562">**NX_CALLER_ERROR** (0x11) Caller não é um fio ou inicialização.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2563">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2563">Allowed From</span></span>

<span data-ttu-id="0ef0c-2564">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2565">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2565">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2566">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2567">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2568">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2568">See Also</span></span>

- <span data-ttu-id="0ef0c-2569">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2570">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="0ef0c-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2574">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="0ef0c-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="0ef0c-2577">Recuperar informações sobre a tomada de TCP do par</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2578">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2579">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2579">Description</span></span>

<span data-ttu-id="0ef0c-2580">Este serviço recupera o endereço IP e informações de porta para a tomada TCP conectada sobre a rede IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2581">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2581">Parameters</span></span>

- <span data-ttu-id="0ef0c-2582">**socket_ptr** Ponteiro para tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2583">**peer_ip_address** Ponteiro para destino para endereço IP peer, em ordem byte anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="0ef0c-2584">**peer_port** Ponteiro para destino para número de porta de pares, em ordem byte de anfitrião.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2585">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2585">Return Values</span></span>

- <span data-ttu-id="0ef0c-2586">**NX_SUCCESS** (0x00) O Serviço executa com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="0ef0c-2587">O endereço IP peer e o número da porta são devolvidos ao chamador.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="0ef0c-2588">**NX_NOT_CONNECTED** (0x38) A tomada não se encontra ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="0ef0c-2589">**NX_PTR_ERROR** (0x07) Ponteiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="0ef0c-2590">**NX_NOT_ENABLED** (0x14) TCP não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="0ef0c-2591">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2592">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2592">Allowed From</span></span>

<span data-ttu-id="0ef0c-2593">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2594">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2594">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2595">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2596">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2597">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2597">See Also</span></span>

- <span data-ttu-id="0ef0c-2598">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2599">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2603">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="0ef0c-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="0ef0c-2606">Receber dados da tomada TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2607">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2608">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2608">Description</span></span>

<span data-ttu-id="0ef0c-2609">Este serviço recebe dados de TCP da tomada especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="0ef0c-2610">Se não forem dados na tomada especificada, o chamador suspende com base na opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="0ef0c-2611">*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2612">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2612">Parameters</span></span>

- <span data-ttu-id="0ef0c-2613">**socket_ptr** Ponteiro para a instância de tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-2614">**packet_ptr** Ponteiro para ponteiro de pacoteS TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="0ef0c-2615">**wait_option** Define como o serviço se comporta se não houver dados atualmente em fila nesta tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="0ef0c-2616">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2619">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2620">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2620">Return Values</span></span>
- <span data-ttu-id="0ef0c-2621">**NX_SUCCESS** (0x00) Os dados de tomadas bem sucedidos recebem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="0ef0c-2622">**NX_NOT_BOUND** (0x24) A tomada ainda não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="0ef0c-2623">**NX_NO_PACKET** (0x01) Nenhum dado recebido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="0ef0c-2624">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-2625">**NX_NOT_CONNECTED** (0x38) A tomada já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="0ef0c-2626">**NX_PTR_ERROR** (0x07) Tomada inválida ou ponteiro do pacote de devolução.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="0ef0c-2627">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2628">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2629">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2629">Allowed From</span></span>

<span data-ttu-id="0ef0c-2630">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2631">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2631">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2632">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2633">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2633">Example</span></span>

<span data-ttu-id="0ef0c-2634">/\* Receba um pacote da tomada do cliente TCP previamente criada e conectada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="0ef0c-2635">Se não houver pacote disponível, aguarde 200 carraças de temporizador antes de desistir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="0ef0c-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="0ef0c-2637">/\* Se o estado for NX_SUCCESS, o pacote recebido é apontado por "packet_ptr".</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="0ef0c-2638">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2638">See Also</span></span>

- <span data-ttu-id="0ef0c-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="0ef0c-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="0ef0c-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="0ef0c-2649">Notificar a aplicação dos pacotes recebidos</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="0ef0c-2650">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2651">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2651">Description</span></span>

<span data-ttu-id="0ef0c-2652">Este serviço configura o ponteiro de função de notificação de receção com a função de retorno especificado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="0ef0c-2653">Esta função de retorno é então chamada sempre que um ou mais pacotes são recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="0ef0c-2654">Se for fornecido um ponteiro NX_NULL, a função de notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2655">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2655">Parameters</span></span>

- <span data-ttu-id="0ef0c-2656">**socket_ptr** Ponteiro para a tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2657">**tcp_receive_notify** O ponteiro da função de retorno da aplicação que é chamado quando um ou mais pacotes são recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2658">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2658">Return Values</span></span>

- <span data-ttu-id="0ef0c-2659">**NX_SUCCESS** (0x00) A tomada de sucesso recebe a notificação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="0ef0c-2660">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2661">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2662">**NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2663">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2663">Allowed From</span></span>

<span data-ttu-id="0ef0c-2664">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2665">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2665">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2666">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2667">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2668">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2668">See Also</span></span>

- <span data-ttu-id="0ef0c-2669">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2670">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2674">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="0ef0c-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="0ef0c-2677">Enviar dados através de uma tomada TCP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2678">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2679">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2679">Description</span></span>

<span data-ttu-id="0ef0c-2680">Este serviço envia dados de TCP através de uma tomada TCP previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="0ef0c-2681">Se o último tamanho da janela anunciado pelo recetor for inferior a este pedido, o serviço suspende opcionalmente com base na opção de espera especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="0ef0c-2682">Este serviço garante que nenhum dado de pacote maior do que o MSS é enviado para a camada IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="0ef0c-2683">*A menos que um erro seja devolvido, o pedido não deve libertar o pacote após esta chamada. Ao fazê-lo, o controlador da rede também tentará libertar o pacote após a transmissão.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2684">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2684">Parameters</span></span>

- <span data-ttu-id="0ef0c-2685">**socket_ptr** Ponteiro para a instância de tomada TCP previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-2686">**packet_ptr** Ponteiro do pacote de dados da TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="0ef0c-2687">**wait_option** Define como o serviço se comporta se o pedido for maior do que o tamanho da janela do recetor.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="0ef0c-2688">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2691">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2692">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2692">Return Values</span></span>

- <span data-ttu-id="0ef0c-2693">**NX_SUCCESS** (0x00) Envio de tomadas bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="0ef0c-2694">**NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="0ef0c-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) Não foi encontrada nenhuma interface de saída adequada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="0ef0c-2696">**NX_NOT_CONNECTED** (0x38) A tomada já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="0ef0c-2697">**NX_WINDOW_OVERFLOW** (0x39) O pedido é maior do que o tamanho da janela anunciado pelo recetor em bytes.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="0ef0c-2698">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-2699">**NX_INVALID_PACKET** (0x12) Pacote não é atribuído.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="0ef0c-2700">**NX_TX_QUEUE_DEPTH** (0x49) Foi atingida a profundidade máxima da fila de transmissão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="0ef0c-2701">**NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="0ef0c-2702">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2703">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2704">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-2705">**NX_UNDERFLOW** (0x02) O ponteiro de preparação do pacote é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2706">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2706">Allowed From</span></span>

<span data-ttu-id="0ef0c-2707">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2708">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2708">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2709">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2710">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2711">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2711">See Also</span></span>

- <span data-ttu-id="0ef0c-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="0ef0c-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="0ef0c-2722">Aguarde que a tomada TCP entre em estado específico</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2723">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="0ef0c-2724">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2724">Description</span></span>

<span data-ttu-id="0ef0c-2725">Este serviço aguarda que a tomada entre no estado pretendido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="0ef0c-2726">Se a tomada não estiver no estado pretendido, o serviço suspende de acordo com a opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2727">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2727">Parameters</span></span>

- <span data-ttu-id="0ef0c-2728">**socket_ptr** Ponteiro para a instância de tomada TCP previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="0ef0c-2729">**desired_state** Estado de TCP desejado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="0ef0c-2730">Os estados de tomada TCP válidos são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="0ef0c-2732">NX_TCP_LISTEN_STATE (0x02)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="0ef0c-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="0ef0c-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="0ef0c-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="0ef0c-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="0ef0c-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="0ef0c-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="0ef0c-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="0ef0c-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="0ef0c-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="0ef0c-2742">**wait_option** Define como o serviço se comporta se o estado solicitado não estiver presente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="0ef0c-2743">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2746">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2747">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2747">Return Values</span></span>
- <span data-ttu-id="0ef0c-2748">**NX_SUCCESS** (0x00) Espera de estado bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="0ef0c-2749">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2750">**NX_NOT_SUCCESSFUL** Estado (0x43) não está presente dentro do tempo de espera especificado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="0ef0c-2751">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-2752">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2753">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-2754">**NX_OPTION_ERROR** (0x0A) O estado de tomada pretendido é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2755">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2755">Allowed From</span></span>

<span data-ttu-id="0ef0c-2756">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2757">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2757">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2758">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2759">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2760">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2760">See Also</span></span>

- <span data-ttu-id="0ef0c-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="0ef0c-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="0ef0c-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="0ef0c-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="0ef0c-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="0ef0c-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="0ef0c-2771">Instale o callback para o estado de espera cronometrado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2772">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2773">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2773">Description</span></span>

<span data-ttu-id="0ef0c-2774">Este serviço regista uma função de retorno que é invocada quando a tomada TCP está em estado de espera cronometrado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="0ef0c-2775">Para utilizar este serviço, a biblioteca NetX deve ser construída com a opção ***NX_ENABLE_EXTENDED_NOTIFY*** definida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2776">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2776">Parameters</span></span>

- <span data-ttu-id="0ef0c-2777">**socket_ptr** Ponteiro para a instância de tomada de cliente ou servidor previamente ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="0ef0c-2778">**tcp_timed_wait_callback** A função de retorno de espera cronometrado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2779">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2779">Return Values</span></span>

- <span data-ttu-id="0ef0c-2780">**NX_SUCCESS** (0x00) regista com sucesso a tomada de função de retorno</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="0ef0c-2781">**NX_NOT_SUPPORTED** (0x4B) a biblioteca NetX é construída sem a funcionalidade de notificação estendida ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="0ef0c-2782">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2783">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2784">**NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2785">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2785">Allowed From</span></span>

<span data-ttu-id="0ef0c-2786">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2787">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2787">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2788">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2789">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2790">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2790">See Also</span></span>

- <span data-ttu-id="0ef0c-2791">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2792">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-2796">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="0ef0c-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="0ef0c-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="0ef0c-2799">Configurar os parâmetros de transmissão da tomada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2800">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2801">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2801">Description</span></span>

<span data-ttu-id="0ef0c-2802">Este serviço configura vários parâmetros de transmissão da tomada TCP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2803">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2803">Parameters</span></span>

- <span data-ttu-id="0ef0c-2804">**socket_ptr** Ponteiro para a tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2805">**max_queue_depth** Número máximo de pacotes autorizados a ser em fila para transmissão.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="0ef0c-2806">**tempo limite** O número de marcadores ThreadX marca um ACK é esperado antes do pacote ser enviado novamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="0ef0c-2807">**max_retries** Número máximo de retró assim que é permitido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="0ef0c-2808">**timeout_shift** Valor para deslocar o tempo limite para cada relemque subsequente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="0ef0c-2809">Um valor de 0, resulta no mesmo intervalo entre as sucessivas retrações.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="0ef0c-2810">Um valor de 1, duplica o tempo limite entre as retrações.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2811">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2811">Return Values</span></span>
- <span data-ttu-id="0ef0c-2812">**NX_SUCCESS** (0x00) Configuração de tomada de transmissão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="0ef0c-2813">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-2814">**NX_OPTION_ERROR** (0x0a) Opção de profundidade de fila inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="0ef0c-2815">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2816">**NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2817">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2817">Allowed From</span></span>

<span data-ttu-id="0ef0c-2818">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2819">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2819">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2820">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2821">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2822">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2822">See Also</span></span>

- <span data-ttu-id="0ef0c-2823">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2824">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-2828">nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="0ef0c-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="0ef0c-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="0ef0c-2831">Notifique a aplicação de atualizações do tamanho da janela</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2832">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-2833">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2833">Description</span></span>

<span data-ttu-id="0ef0c-2834">Este serviço instala uma rotina de chamada de atualização da janela da tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="0ef0c-2835">Esta rotina é chamada automaticamente sempre que a tomada especificada recebe um pacote indicando um aumento no tamanho da janela do hospedeiro remoto.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2836">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2836">Parameters</span></span>

- <span data-ttu-id="0ef0c-2837">**socket_ptr** Ponteiro para tomada TCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="0ef0c-2838">**tcp_window_update_notify** Rotina de chamada a ser chamada quando o tamanho da janela muda.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="0ef0c-2839">Um valor de NULO desativa a atualização da alteração da janela.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2840">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2840">Return Values</span></span>
- <span data-ttu-id="0ef0c-2841">**NX_SUCCESS** (0x00) A rotina de chamada é instalada na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="0ef0c-2842">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2843">**NX_PTR_ERROR** (0x07) Ponteiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="0ef0c-2844">**NX_NOT_ENABLED** (0x14) funcionalidade TCP não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2845">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2845">Allowed From</span></span>

<span data-ttu-id="0ef0c-2846">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2847">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2847">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2848">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2849">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2850">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2850">See Also</span></span>

- <span data-ttu-id="0ef0c-2851">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-2852">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="0ef0c-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="0ef0c-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="0ef0c-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="0ef0c-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2857">nx_udp_enable</span></span>

<span data-ttu-id="0ef0c-2858">Ativar o componente UDP do NetX</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2859">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2860">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2860">Description</span></span>

<span data-ttu-id="0ef0c-2861">Este serviço permite o componente do Protocolo de Datagram do Utilizador (UDP) do NetX.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="0ef0c-2862">Após ativação, os datagramas da UDP podem ser enviados e recebidos pelo pedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2863">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2863">Parameters</span></span>

- <span data-ttu-id="0ef0c-2864">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2865">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2865">Return Values</span></span>

- <span data-ttu-id="0ef0c-2866">**NX_SUCCESS** (0x00) UDP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="0ef0c-2867">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2868">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2869">**NX_ALREADY_ENABLED** (0x15) Este componente já foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2870">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2870">Allowed From</span></span>

<span data-ttu-id="0ef0c-2871">Inicialização, fios, temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2872">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2872">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2873">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2874">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2875">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2875">See Also</span></span>

- <span data-ttu-id="0ef0c-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="0ef0c-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="0ef0c-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="0ef0c-2885">Encontre a próxima porta UDP disponível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2886">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2887">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2887">Description</span></span>

<span data-ttu-id="0ef0c-2888">Este serviço procura uma porta UDP gratuita (não ligada) a partir do número de porta fornecido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="0ef0c-2889">A lógica de pesquisa irá envolver-se se a pesquisa atingir o valor máximo da porta de 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="0ef0c-2890">Se a pesquisa for bem sucedida, a porta livre é devolvida na variável apontada por *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="0ef0c-2891">*Este serviço pode ser chamado de outro fio e pode ter a mesma porta devolvida. Para evitar esta condição de regata, a aplicação pode pretender colocar este serviço e a tomada efetiva se ligam sob a proteção de um mutex.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2892">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2892">Parameters</span></span>

- <span data-ttu-id="0ef0c-2893">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2894">**porto** Número da porta para iniciar a pesquisa (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="0ef0c-2895">**free_port_ptr** Ponteiro para a variável de retorno de porto livre de destino.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="0ef0c-2896">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2896">Return Values</span></span>

- <span data-ttu-id="0ef0c-2897">**NX_SUCCESS** (0x00) Achado de porta livre com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="0ef0c-2898">**NX_NO_FREE_PORTS** (0x45) Não foram encontradas portas livres.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="0ef0c-2899">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2900">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2901">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="0ef0c-2902">**NX_INVALID_PORT** (0x46) O número de porta especificado é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2903">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2903">Allowed From</span></span>

<span data-ttu-id="0ef0c-2904">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2905">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2905">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2906">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2907">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2908">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2908">See Also</span></span>

- <span data-ttu-id="0ef0c-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="0ef0c-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="0ef0c-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2917">nx_udp_info_get</span></span>

<span data-ttu-id="0ef0c-2918">Recuperar informações sobre atividades da UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2919">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2920">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2920">Description</span></span>

<span data-ttu-id="0ef0c-2921">Este serviço obtém informações sobre as atividades da UDP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="0ef0c-2922">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2923">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2923">Parameters</span></span>

- <span data-ttu-id="0ef0c-2924">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-2925">**udp_packets_sent** Ponteiro para o destino para o número total de pacotes UDP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="0ef0c-2926">**udp_bytes_sent** Ponteiro para destino para o número total de bytes UDP enviados.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="0ef0c-2927">**udp_packets_received** Ponteiro para o destino do número total de pacotes UDP recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="0ef0c-2928">**udp_bytes_received** Ponteiro para o destino do número total de bytes UDP recebidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="0ef0c-2929">**udp_invalid_packets** Ponteiro para o destino do número total de pacotes UDP inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="0ef0c-2930">**udp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção UDP caiu.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="0ef0c-2931">**udp_checksum_errors** Ponteiro para o destino do número total de pacotes UDP com erros de checkum.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2932">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2932">Return Values</span></span>

- <span data-ttu-id="0ef0c-2933">**NX_SUCCESS** (0x00) Recuperação de informações bem sucedidas da UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="0ef0c-2934">**NX_PTR_ERROR** (0x07) Ponteiro IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="0ef0c-2935">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-2936">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2937">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2937">Allowed From</span></span>

<span data-ttu-id="0ef0c-2938">Inicialização, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2939">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2939">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2940">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2941">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2942">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2942">See Also</span></span>

- <span data-ttu-id="0ef0c-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="0ef0c-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="0ef0c-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="0ef0c-2952">Extrair parâmetros de rede do pacote UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2953">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2954">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2954">Description</span></span>

<span data-ttu-id="0ef0c-2955">Este serviço extrai parâmetros de rede, tais como endereço IP, número de porta de pares, tipo de protocolo (este serviço devolve sempre o tipo UDP) de um pacote recebido numa interface de entrada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2956">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2956">Parameters</span></span>

- <span data-ttu-id="0ef0c-2957">**packet_ptr** Ponteiro para pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="0ef0c-2958">**ip_address** Ponteiro para o endereço IP remetente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="0ef0c-2959">**protocolo** Ponteiro para o protocolo (UDP).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="0ef0c-2960">**porto** Ponteiro para o número da porta do remetente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="0ef0c-2961">**interface_index** Ponteiro para receber índice de interface.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2962">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2962">Return Values</span></span>

- <span data-ttu-id="0ef0c-2963">**NX_SUCCESS** (0x00) dados de interface de pacote extraídos com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="0ef0c-2964">**NX_INVALID_PACKET** (0x12) O pacote não contém quadro IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="0ef0c-2965">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="0ef0c-2966">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-2967">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2967">Allowed From</span></span>

<span data-ttu-id="0ef0c-2968">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-2969">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2969">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-2970">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-2971">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-2972">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2972">See Also</span></span>

- <span data-ttu-id="0ef0c-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="0ef0c-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="0ef0c-2982">Ligue a tomada UDP à porta UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-2983">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-2984">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2984">Description</span></span>

<span data-ttu-id="0ef0c-2985">Este serviço liga a tomada UDP previamente criada à porta UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="0ef0c-2986">As tomadas UDP válidas variam de 0 a 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="0ef0c-2987">Se o número de porta solicitado estiver ligado a outra tomada, este serviço aguarda por um período de tempo especificado para que a tomada se desvincula do número da porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-2988">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2988">Parameters</span></span>

- <span data-ttu-id="0ef0c-2989">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="0ef0c-2990">**porto** Número da porta para ligar (1 a 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="0ef0c-2991">Se o número da porta for NX_ANY_PORT (0x0000), a instância IP procurará a próxima porta livre e usará-a para a encadernação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="0ef0c-2992">**wait_option** Define como o serviço se comporta se a porta já está ligada a outra tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="0ef0c-2993">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-2996">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-2997">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2997">Return Values</span></span>

- <span data-ttu-id="0ef0c-2998">**NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="0ef0c-2999">**NX_ALREADY_BOUND** (0x22) Esta tomada já está ligada a outra porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="0ef0c-3000">**NX_PORT_UNAVAILABLE** (0x23) O porto já está ligado a uma tomada diferente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="0ef0c-3001">**NX_NO_FREE_PORTS** (0x45) Não há porta livre.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="0ef0c-3002">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="0ef0c-3003">**NX_INVALID_PORT** (0x46) Porta inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="0ef0c-3004">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3005">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3006">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3007">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3007">Allowed From</span></span>

<span data-ttu-id="0ef0c-3008">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3009">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3009">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3010">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3011">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3012">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3012">See Also</span></span>

- <span data-ttu-id="0ef0c-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="0ef0c-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="0ef0c-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="0ef0c-3022">Recupera o número de bytes disponíveis para recuperação</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3023">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3024">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3024">Description</span></span>

<span data-ttu-id="0ef0c-3025">Este serviço recupera o número de bytes disponíveis para receção na tomada UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3026">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3026">Parameters</span></span>

- <span data-ttu-id="0ef0c-3027">**socket_ptr** Ponteiro para tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="0ef0c-3028">**bytes_available** Ponteiro para destino para bytes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3029">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3029">Return Values</span></span>

- <span data-ttu-id="0ef0c-3030">**NX_SUCCESS** (0x00) Bytes de sucesso disponível.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="0ef0c-3031">**NX_NOT_SUCCESSFUL** (0x43) Tomada não ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="0ef0c-3032">**NX_PTR_ERROR** (0x07) Ponteiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="0ef0c-3033">**NX_NOT_ENABLED** funcionalidade UDP (0x14) não está ativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="0ef0c-3034">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3035">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3035">Allowed From</span></span>

<span data-ttu-id="0ef0c-3036">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3037">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3037">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3038">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3039">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3040">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3040">See Also</span></span>

- <span data-ttu-id="0ef0c-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3042">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="0ef0c-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="0ef0c-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="0ef0c-3050">Desativar a parte de verificação da tomada UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3051">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3052">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3052">Description</span></span>

<span data-ttu-id="0ef0c-3053">Este serviço desativa a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="0ef0c-3054">Quando a lógica de checkum é desativada, um valor de zero é carregado no campo de verificação do cabeçalho UDP para todos os pacotes enviados através desta tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="0ef0c-3055">Um valor de dados de valor zero no cabeçalho UDP indica ao recetor que a parte de verificação não é calculada para este pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="0ef0c-3056">Note também que isto não tem efeito se ***NX_DISABLE_UDP_RX_CHECKSUM** _ e _ *_NX_DISABLE_UDP_TX_CHECKSUM_** são definidos ao receber e enviar pacotes UDP respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3057">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3057">Parameters</span></span>

- <span data-ttu-id="0ef0c-3058">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3059">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3059">Return Values</span></span>

- <span data-ttu-id="0ef0c-3060">**NX_SUCCESS** (0x00) Desativação de verificação de tomadas bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="0ef0c-3061">**NX_NOT_BOUND** (0x24) A tomada não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="0ef0c-3062">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3063">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3064">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3065">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3065">Allowed From</span></span>

<span data-ttu-id="0ef0c-3066">Inicialização, fios, temporizador</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3067">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3067">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3068">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3069">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3070">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3070">See Also</span></span>

- <span data-ttu-id="0ef0c-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3072">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="0ef0c-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="0ef0c-3080">Ativar a parte de verificação da tomada UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3081">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3082">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3082">Description</span></span>

<span data-ttu-id="0ef0c-3083">Este serviço permite a lógica de checkum para o envio e receção de pacotes na tomada UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="0ef0c-3084">A função de verificação abrange toda a área de dados da UDP, bem como um cabeçalho pseudo-IP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="0ef0c-3085">Note também que isso não tem qualquer efeito se **NX_DISABLE_UDP_RX_CHECKSUM** e **NX_DISABLE_UDP_TX_CHECKSUM** forem definidos ao receber e enviar pacotes UDP respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3086">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3086">Parameters</span></span>

- <span data-ttu-id="0ef0c-3087">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3088">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3088">Return Values</span></span>

- <span data-ttu-id="0ef0c-3089">**NX_SUCCESS** (0x00) Ativar a tomada de verificação com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="0ef0c-3090">**NX_NOT_BOUND** (0x24) A tomada não está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="0ef0c-3091">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3092">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3093">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3094">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3094">Allowed From</span></span>

<span data-ttu-id="0ef0c-3095">Inicialização, fios, temporizador</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3096">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3096">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3097">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3098">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3099">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3099">See Also</span></span>

- <span data-ttu-id="0ef0c-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3101">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="0ef0c-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="0ef0c-3109">Criar tomada UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3110">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3111">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3111">Description</span></span>

<span data-ttu-id="0ef0c-3112">Este serviço cria uma tomada UDP para a instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3113">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3113">Parameters</span></span>

- <span data-ttu-id="0ef0c-3114">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="0ef0c-3115">**socket_ptr** Ponteiro para o novo bloco de controlo de tomadas UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="0ef0c-3116">**nome** Nome da aplicação para esta tomada UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="0ef0c-3117">**type_of_service** Define o tipo de serviço para a transmissão, os valores legais são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="0ef0c-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="0ef0c-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="0ef0c-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="0ef0c-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="0ef0c-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="0ef0c-3123">**fragmento** Especifica se é permitida a fragmentação ip.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="0ef0c-3124">Se NX_FRAGMENT_OKAY (0x0) for especificado, é permitida a fragmentação ip.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="0ef0c-3125">Se NX_DONT_FRAGMENT (0x4000) for especificado, a fragmentação ip está desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="0ef0c-3126">**time_to_live** Especifica o valor de 8 bits que define quantos routers este pacote pode passar antes de ser jogado fora.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="0ef0c-3127">O valor predefinido é especificado por NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="0ef0c-3128">**queue_maximum** Define o número máximo de datagramas da UDP que podem ser pré-visualizados para esta tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="0ef0c-3129">Após o limite de fila ser atingido, para cada novo pacote recebido o pacote UDP mais antigo é lançado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3130">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3130">Return Values</span></span>

- <span data-ttu-id="0ef0c-3131">**NX_SUCCESS** (0x00) Tomada UDP bem sucedida criar.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="0ef0c-3132">**NX_OPTION_ERROR** (0x0A) Opção de serviço, fragmento ou tempo-a-vida inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="0ef0c-3133">**NX_PTR_ERROR** (0x07) IP inválido ou ponteiro de tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3134">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3135">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3136">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3136">Allowed From</span></span>

<span data-ttu-id="0ef0c-3137">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3138">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3138">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3139">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3141">See Also</span></span>

- <span data-ttu-id="0ef0c-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3143">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="0ef0c-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="0ef0c-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3149">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="0ef0c-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="0ef0c-3151">Eliminar tomada UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3152">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3153">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3153">Description</span></span>

<span data-ttu-id="0ef0c-3154">Este serviço elimina uma tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="0ef0c-3155">Se a tomada estava ligada a uma porta, a tomada deve ser desaderada primeiro.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3156">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3156">Parameters</span></span>

- <span data-ttu-id="0ef0c-3157">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3158">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3158">Return Values</span></span>

- <span data-ttu-id="0ef0c-3159">**NX_SUCCESS** (0x00) Apagar a tomada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="0ef0c-3160">**NX_STILL_BOUND** (0x42) A tomada ainda está ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="0ef0c-3161">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3162">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3163">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3164">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3164">Allowed From</span></span>

<span data-ttu-id="0ef0c-3165">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3166">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3166">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3167">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3169">See Also</span></span>

- <span data-ttu-id="0ef0c-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3171">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="0ef0c-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3177">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="0ef0c-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="0ef0c-3179">Recuperar informações sobre as atividades da tomada da UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3180">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3181">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3181">Description</span></span>

<span data-ttu-id="0ef0c-3182">Este serviço obtém informações sobre as atividades da tomada UDP para a instância de tomada UDP especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="0ef0c-3183">*Se um ponteiro de destino for NX_NULL, essa informação específica não é devolvida ao autor da chamada.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3184">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3184">Parameters</span></span>

- <span data-ttu-id="0ef0c-3185">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="0ef0c-3186">**udp_packets_sent** Ponteiro para o destino para o número total de pacotes UDP enviados na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="0ef0c-3187">**udp_bytes_sent** Ponteiro para destino para o número total de bytes UDP enviados na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="0ef0c-3188">**udp_packets_received** Ponteiro para o destino do número total de pacotes UDP recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="0ef0c-3189">**udp_bytes_received** Ponteiro para o destino do número total de bytes UDP recebidos na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="0ef0c-3190">**udp_packets_queued** Ponteiro para o destino do número total de pacotes de UDP em fila na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="0ef0c-3191">**udp_receive_packets_dropped** O ponteiro para o destino do número total de pacotes de receção UDP caiu para tomada devido ao tamanho da fila ser excedido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="0ef0c-3192">**udp_checksum_errors** Ponteiro para o destino do número total de pacotes UDP com erros de verificação na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3193">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3193">Return Values</span></span>

- <span data-ttu-id="0ef0c-3194">**NX_SUCCESS** (0x00) Recuperação de informações de tomadas UDP bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="0ef0c-3195">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3196">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3197">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3198">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3198">Allowed From</span></span>

<span data-ttu-id="0ef0c-3199">Inicialização, fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3200">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3200">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3201">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3202">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3203">See Also</span></span>

- <span data-ttu-id="0ef0c-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3205">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="0ef0c-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3211">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="0ef0c-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="0ef0c-3213">Recolha o número da porta vinculado à tomada UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3214">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3215">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3215">Description</span></span>

<span data-ttu-id="0ef0c-3216">Este serviço recupera o número de porta associado à tomada, o que é útil para encontrar a porta atribuída pela NetX em situações em que o NX_ANY_PORT foi especificado no momento em que a tomada foi ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3217">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3217">Parameters</span></span>

- <span data-ttu-id="0ef0c-3218">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="0ef0c-3219">**port_ptr** Ponteiro para o destino para o número da porta de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="0ef0c-3220">Os números de porta válidos são (1- 0xFFFF).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3221">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3221">Return Values</span></span>

- <span data-ttu-id="0ef0c-3222">**NX_SUCCESS** (0x00) Ligação de tomada bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="0ef0c-3223">**NX_NOT_BOUND** (0x24) Esta tomada não está ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="0ef0c-3224">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida ou ponteiro de retorno da porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="0ef0c-3225">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3226">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3227">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3227">Allowed From</span></span>

<span data-ttu-id="0ef0c-3228">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3229">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3229">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3230">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3231">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3232">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3232">See Also</span></span>

- <span data-ttu-id="0ef0c-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3234">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3240">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="0ef0c-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="0ef0c-3242">Receber datagrama da tomada UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3243">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3244">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3244">Description</span></span>

<span data-ttu-id="0ef0c-3245">Este serviço recebe um datagrama de UDP a partir da tomada especificada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="0ef0c-3246">Se não houver um datagrama na tomada especificada, o chamador suspende com base na opção de espera fornecida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="0ef0c-3247">*Se NX_SUCCESS for devolvido, o pedido é responsável pela libertação do pacote recebido quando já não for necessário.*</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3248">Parameters</span></span>

- <span data-ttu-id="0ef0c-3249">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="0ef0c-3250">**packet_ptr** Ponteiro para o ponteiro do pacote de dados da UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="0ef0c-3251">**wait_option** Define como o serviço se comporta se um datagram não estiver atualmente em fila nesta tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="0ef0c-3252">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="0ef0c-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="0ef0c-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="0ef0c-3255">valor de tempo limite em carrapatos (0x00000001 a 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3256">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3256">Allowed From</span></span>

<span data-ttu-id="0ef0c-3257">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3258">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3258">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3259">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3260">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3261">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3261">See Also</span></span>

- <span data-ttu-id="0ef0c-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3263">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="0ef0c-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3269">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="0ef0c-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="0ef0c-3271">Notifique a aplicação de cada pacote recebido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3272">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="0ef0c-3273">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3273">Description</span></span>

<span data-ttu-id="0ef0c-3274">Este serviço define o ponteiro de função de notificação de receção à função de retorno especificado pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="0ef0c-3275">Esta função de retorno é então chamada sempre que um pacote é recebido na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="0ef0c-3276">Se for fornecido um ponteiro NX_NULL, a função de notificação de receção é desativada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3277">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3277">Parameters</span></span>

- <span data-ttu-id="0ef0c-3278">**socket_ptr** Ponteiro para a tomada UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="0ef0c-3279">**udp_receive_notify** Ponteiro da função de retorno da aplicação que é chamado quando um pacote é recebido na tomada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3280">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3280">Allowed From</span></span>

<span data-ttu-id="0ef0c-3281">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3282">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3282">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3283">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3284">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3285">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3285">See Also</span></span>

- <span data-ttu-id="0ef0c-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3287">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="0ef0c-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="0ef0c-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="0ef0c-3295">Enviar um UDP Datagram</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3296">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3297">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3297">Description</span></span>

<span data-ttu-id="0ef0c-3298">Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="0ef0c-3299">O NetX encontra um endereço IP local adequado como endereço de origem baseado no endereço IP de destino.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="0ef0c-3300">Para especificar uma interface específica e endereço IP de origem, a aplicação deve utilizar o serviço **nx_udp_socket_interface_send.**</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="0ef0c-3301">Note que este serviço retorna imediatamente independentemente de o datagrama da UDP ter sido enviado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="0ef0c-3302">A tomada deve estar ligada a um porto local.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3303">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3303">Parameters</span></span>

- <span data-ttu-id="0ef0c-3304">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="0ef0c-3305">**packet_ptr** Ponteiro do pacote de datagrama da UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="0ef0c-3306">**ip_address** Endereço IP de destino</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="0ef0c-3307">**porto** Número de porta de destino válido entre 1 e 0xFFFF), em encomenda byte de anfitrião</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3308">Return Values</span></span>

- <span data-ttu-id="0ef0c-3309">**NX_SUCCESS** (0x00) Envio de tomada uDP bem sucedida</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="0ef0c-3310">**NX_NOT_BOUND** (0x24) Tomada não ligada a nenhuma porta</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="0ef0c-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) Não é possível encontrar uma interface de saída adequada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="0ef0c-3312">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP do servidor inválido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="0ef0c-3313">**NX_UNDERFLOW** (0x02) Não há espaço suficiente para cabeçalho UDP no pacote</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="0ef0c-3314">**NX_OVERFLOW** (0x03) O ponteiro do apêndice do pacote é inválido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="0ef0c-3315">**ponteiro de tomada** inválida NX_PTR_ERROR (0x07)</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="0ef0c-3316">**NX_CALLER_ERROR** (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="0ef0c-3317">**NX_NOT_ENABLED** (0x14) UDP não foi habilitado</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="0ef0c-3318">**NX_INVALID_PORT** (0x46) Número de porta não está dentro de um alcance válido</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3319">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3319">Allowed From</span></span>

<span data-ttu-id="0ef0c-3320">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3321">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3321">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3322">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3323">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3324">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3324">See Also</span></span>

- <span data-ttu-id="0ef0c-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3326">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="0ef0c-3332">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="0ef0c-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="0ef0c-3334">Envie datagrama através da tomada UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3335">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3336">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3336">Description</span></span>

<span data-ttu-id="0ef0c-3337">Este serviço envia um datagrama de UDP através de uma tomada UDP previamente criada e ligada através da interface de rede com o endereço IP especificado como endereço de origem.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="0ef0c-3338">Note que o serviço regressa imediatamente, independentemente de o datagrama da UDP ter sido enviado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3339">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3339">Parameters</span></span>

- <span data-ttu-id="0ef0c-3340">**socket_ptr** Tomada para transmitir o pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="0ef0c-3341">**packet_ptr** Ponteiro para pacote para transmitir.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="0ef0c-3342">**ip_address** Endereço IP destino para enviar pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="0ef0c-3343">**porto** Porto de destino.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3343">**port** Destination port.</span></span>
- <span data-ttu-id="0ef0c-3344">**address_index** Índice do endereço associado à interface para enviar o pacote.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3345">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3345">Return Values</span></span>

- <span data-ttu-id="0ef0c-3346">**NX_SUCCESS** (0x00) Packet enviado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="0ef0c-3347">**NX_NOT_BOUND** (0x24) Tomada não ligada a uma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="0ef0c-3348">**NX_IP_ADDRESS_ERROR** (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="0ef0c-3349">**NX_NOT_ENABLED** processamento de UDP (0x14) não está ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="0ef0c-3350">**NX_PTR_ERROR** (0x07) Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="0ef0c-3351">**NX_OVERFLOW** (0x03) Ponteiro de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="0ef0c-3352">**NX_UNDERFLOW** (0x02) Ponteiro de pré-final de pacote inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="0ef0c-3353">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3354">**NX_INVALID_INTERFACE** (0x4C) Índice de endereços inválidos.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="0ef0c-3355">**NX_INVALID_PORT** (0x46) O número do porto excede o número máximo de porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3356">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3356">Allowed From</span></span>

<span data-ttu-id="0ef0c-3357">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3358">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3358">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3359">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3360">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3361">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3361">See Also</span></span>

- <span data-ttu-id="0ef0c-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3363">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="0ef0c-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="0ef0c-3371">Tomada UDP desaderada da porta UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3372">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3373">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3373">Description</span></span>

<span data-ttu-id="0ef0c-3374">Este serviço liberta a encadernação entre a tomada UDP e uma porta UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="0ef0c-3375">Quaisquer pacotes recebidos armazenados na fila de receção são libertados como parte da operação un encaderna.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="0ef0c-3376">Se houver outros fios à espera de ligar outra tomada à porta desvinculada, o primeiro fio suspenso fica então ligado à porta recém-desvinculada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3377">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3377">Parameters</span></span>

- <span data-ttu-id="0ef0c-3378">**socket_ptr** Ponteiro para a instância de tomada UDP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3379">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3379">Return Values</span></span>

- <span data-ttu-id="0ef0c-3380">**NX_SUCCESS** (0x00) Tomada desaderada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="0ef0c-3381">**NX_NOT_BOUND** (0x24) Tomada não estava ligada a nenhuma porta.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="0ef0c-3382">**NX_PTR_ERROR** (0x07) Ponteiro de tomada inválida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="0ef0c-3383">**NX_CALLER_ERROR** (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="0ef0c-3384">**NX_NOT_ENABLED** (0x14) Este componente não foi ativado.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3385">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3385">Allowed From</span></span>

<span data-ttu-id="0ef0c-3386">Fios</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3387">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3387">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3388">Sim</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3389">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3390">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3390">See Also</span></span>

- <span data-ttu-id="0ef0c-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3392">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="0ef0c-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="0ef0c-3400">Extrair IP e enviar porta a partir do datagrama da UDP</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef0c-3401">Prototype</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="0ef0c-3402">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3402">Description</span></span>

<span data-ttu-id="0ef0c-3403">Este serviço extrai o número de IP e porta do remetente dos cabeçalhos IP e UDP do programa de dados da UDP fornecido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="0ef0c-3404">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3404">Parameters</span></span>

- <span data-ttu-id="0ef0c-3405">**packet_ptr** Ponteiro do pacote de datagrama da UDP.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="0ef0c-3406">**ip_address** Ponteiro válido para a variável de endereço IP de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="0ef0c-3407">**porto** Ponteiro válido para a variável porta de retorno.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef0c-3408">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3408">Return Values</span></span>

- <span data-ttu-id="0ef0c-3409">**NX_SUCCESS** (0x00) Extração IP/porta de origem bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="0ef0c-3410">**NX_INVALID_PACKET** (0x12) O pacote fornecido é inválido.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="0ef0c-3411">**NX_PTR_ERROR** (0x07) Pacote inválido ou IP ou destino portuário.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef0c-3412">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3412">Allowed From</span></span>

<span data-ttu-id="0ef0c-3413">Inicialização, fios, temporizadores, ISR</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="0ef0c-3414">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3414">Preemption Possible</span></span>

<span data-ttu-id="0ef0c-3415">No</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="0ef0c-3416">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="0ef0c-3417">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3417">See Also</span></span>

- <span data-ttu-id="0ef0c-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="0ef0c-3419">nx_udp_packet_info_extract, nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="0ef0c-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="0ef0c-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="0ef0c-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="0ef0c-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="0ef0c-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="0ef0c-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="0ef0c-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>