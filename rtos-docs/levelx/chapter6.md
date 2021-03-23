---
title: Capítulo 6 - Azure RTOS LevelX NOR APIs
description: As APIs Azure RTOS LevelX NOR disponíveis para a aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827050"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="df667-103">Capítulo 6 - Azure RTOS LevelX NOR APIs</span><span class="sxs-lookup"><span data-stu-id="df667-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="df667-104">As funções Azure RTOS LevelX NOR API disponíveis para a aplicação são as seguintes.</span><span class="sxs-lookup"><span data-stu-id="df667-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="df667-105">***lx_nor_flash_close** _: _Close NEM flash instance*</span><span class="sxs-lookup"><span data-stu-id="df667-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="df667-106">***lx_nor_flash_defragment** _: _Defragment NEM flash instance*</span><span class="sxs-lookup"><span data-stu-id="df667-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="df667-107">***lx_nor_flash_extended_cache_enable** _: _Enable/desativar cache NOR estendido*</span><span class="sxs-lookup"><span data-stu-id="df667-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="df667-108">***lx_nor_flash_initialize** _: _Initialize SUPORTE DE FLASH*</span><span class="sxs-lookup"><span data-stu-id="df667-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="df667-109">***lx_nor_flash_open** _: _Open NEM flash instance*</span><span class="sxs-lookup"><span data-stu-id="df667-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="df667-110">***lx_nor_flash_partial_defragment** _: _Partial desfragmentação da instância flash NOR*</span><span class="sxs-lookup"><span data-stu-id="df667-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="df667-111">***lx_nor_flash_sector_read** _: _Read sector flash*</span><span class="sxs-lookup"><span data-stu-id="df667-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="df667-112">***lx_nor_flash_sector_release** _: _Release sector flash*</span><span class="sxs-lookup"><span data-stu-id="df667-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="df667-113">***lx_nor_flash_sector_write** _: _Write sector flash*</span><span class="sxs-lookup"><span data-stu-id="df667-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="df667-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-114">lx_nor_flash_close</span></span>

<span data-ttu-id="df667-115">Encerrar a instância flash NOR</span><span class="sxs-lookup"><span data-stu-id="df667-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-116">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="df667-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-117">Description</span></span>

<span data-ttu-id="df667-118">Este serviço encerra a instância de flash NOR previamente aberta.</span><span class="sxs-lookup"><span data-stu-id="df667-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-119">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-119">Input Parameters</span></span>

- <span data-ttu-id="df667-120">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-121">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-121">Return Values</span></span>

- <span data-ttu-id="df667-122">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-123">**LX_ERROR**: (0x01) Erro de fecho de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-124">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-124">Allowed From</span></span>

<span data-ttu-id="df667-125">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-127">See Also</span></span>

- <span data-ttu-id="df667-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="df667-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="df667-137">Defragment NOR flash instance</span><span class="sxs-lookup"><span data-stu-id="df667-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-138">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="df667-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-139">Description</span></span>

<span data-ttu-id="df667-140">Este serviço desfragmenta a instância de flash NOR previamente aberta.</span><span class="sxs-lookup"><span data-stu-id="df667-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="df667-141">O processo de desfragmentamento maximiza o número de sectores e blocos livres.</span><span class="sxs-lookup"><span data-stu-id="df667-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-142">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-142">Input Parameters</span></span>

- <span data-ttu-id="df667-143">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-144">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-144">Return Values</span></span>

- <span data-ttu-id="df667-145">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-146">**LX_ERROR**: (0x01) Erro desfragmentando flash instance.</span><span class="sxs-lookup"><span data-stu-id="df667-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-147">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-147">Allowed From</span></span>

<span data-ttu-id="df667-148">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-150">See Also</span></span>

- <span data-ttu-id="df667-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="df667-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="df667-160">Ativar/desativar cache NOR estendido</span><span class="sxs-lookup"><span data-stu-id="df667-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="df667-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-162">Description</span></span>

<span data-ttu-id="df667-163">Este serviço implementa uma camada de cache do sector NOR na RAM utilizando a memória fornecida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="df667-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="df667-164">Cada 512 bytes de memória fornecidos traduz-se num sector NOR que pode ser em cache.</span><span class="sxs-lookup"><span data-stu-id="df667-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="df667-165">Os sectores em cache são aqueles que contêm a informação de controlo de blocos, por exemplo, a contagem de apagamento, o mapa do sector livre e a informação de mapeamento sectorial.</span><span class="sxs-lookup"><span data-stu-id="df667-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="df667-166">Os sectores de dados não são armazenados nesta cache.</span><span class="sxs-lookup"><span data-stu-id="df667-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-167">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-167">Input Parameters</span></span>

- <span data-ttu-id="df667-168">**nor_flash:** NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="df667-169">**memória**: Endereço inicial para memória cache, alinhado para acesso ULONG.</span><span class="sxs-lookup"><span data-stu-id="df667-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="df667-170">Um valor de LX_NULL desativa a cache.</span><span class="sxs-lookup"><span data-stu-id="df667-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="df667-171">**tamanho**: O tamanho dos bytes da memória fornecida (deve ser múltiplo de 512 bytes).</span><span class="sxs-lookup"><span data-stu-id="df667-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-172">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-172">Return Values</span></span>

- <span data-ttu-id="df667-173">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-174">**LX_ERROR**: (0x01) Não há memória suficiente para um sector NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="df667-175">**LX_DISABLED:**(0x09) NEM cache estendida desativada por opção de configuração.</span><span class="sxs-lookup"><span data-stu-id="df667-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-176">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-176">Allowed From</span></span>

<span data-ttu-id="df667-177">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-179">See Also</span></span>

- <span data-ttu-id="df667-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="df667-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="df667-189">Inicializar NOR suporte flash</span><span class="sxs-lookup"><span data-stu-id="df667-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-190">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="df667-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-191">Description</span></span>

<span data-ttu-id="df667-192">Este serviço inicializa o suporte de flash LevelX NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="df667-193">Deve ser chamado antes de qualquer outro LevelX NOR APIs.</span><span class="sxs-lookup"><span data-stu-id="df667-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-194">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-194">Input Parameters</span></span>

- <span data-ttu-id="df667-195">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="df667-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-196">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-196">Return Values</span></span>

- <span data-ttu-id="df667-197">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-198">**LX_ERROR**: (0x01) Erro inicializando NOR suporte de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-199">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-199">Allowed From</span></span>

<span data-ttu-id="df667-200">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="df667-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-202">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-202">See Also</span></span>

- <span data-ttu-id="df667-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="df667-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-211">lx_nor_flash_open</span></span>

<span data-ttu-id="df667-212">Abrir a instância flash NOR</span><span class="sxs-lookup"><span data-stu-id="df667-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-213">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="df667-214">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-214">Description</span></span>

<span data-ttu-id="df667-215">Este serviço abre uma instância de flash NOR com o bloco de controlo de flash NOR especificado e a função de inicialização do controlador.</span><span class="sxs-lookup"><span data-stu-id="df667-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="df667-216">Note que a função de inicialização do controlador é responsável pela instalação de vários ponteiros de função para a leitura, escrita e apagamento de blocos do hardware NOR associados a esta instância de flash NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-217">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-217">Input Parameters</span></span>

- <span data-ttu-id="df667-218">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="df667-219">*nome*: Nome da instância flash NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="df667-220">*nor_driver_initialize*: Função ponteiro para nor função de iniciação do controlador flash.</span><span class="sxs-lookup"><span data-stu-id="df667-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="df667-221">Consulte o capítulo 5 deste guia para obter mais detalhes sobre as responsabilidades do condutor flash NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-222">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-222">Return Values</span></span>

- <span data-ttu-id="df667-223">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-224">**LX_ERROR**: (0x01) Abertura de erro NEM flash instance.</span><span class="sxs-lookup"><span data-stu-id="df667-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="df667-225">**LX_NO_MEMORY**: (0x08) O condutor não forneceu tampão para a leitura de nenhum sector na RAM.</span><span class="sxs-lookup"><span data-stu-id="df667-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-226">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-226">Allowed From</span></span>

<span data-ttu-id="df667-227">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-228">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-229">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-229">See Also</span></span>

- <span data-ttu-id="df667-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="df667-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="df667-239">Desfragmentação parcial da instância flash NOR</span><span class="sxs-lookup"><span data-stu-id="df667-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="df667-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-241">Description</span></span>

<span data-ttu-id="df667-242">Este serviço desfragmenta a instância de flash NOR previamente aberta até ao número máximo de blocos especificados.</span><span class="sxs-lookup"><span data-stu-id="df667-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="df667-243">O processo de desfragmentamento maximiza o número de sectores e blocos livres.</span><span class="sxs-lookup"><span data-stu-id="df667-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-244">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-244">Input Parameters</span></span>

- <span data-ttu-id="df667-245">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="df667-246">*max_blocks:* Número máximo de blocos.</span><span class="sxs-lookup"><span data-stu-id="df667-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-247">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-247">Return Values</span></span>

- <span data-ttu-id="df667-248">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-249">**LX_ERROR**: (0x01) Erro desfragmentando flash instance.</span><span class="sxs-lookup"><span data-stu-id="df667-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-250">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-250">Allowed From</span></span>

<span data-ttu-id="df667-251">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-252">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="df667-253">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-253">See Also</span></span>

- <span data-ttu-id="df667-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="df667-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="df667-263">Ler NOR flash sector</span><span class="sxs-lookup"><span data-stu-id="df667-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="df667-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-265">Description</span></span>

<span data-ttu-id="df667-266">Este serviço lê o sector lógico a partir da instância de flash NOR e se for bem-sucedido devolve o conteúdo no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="df667-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="df667-267">Note que o tamanho do sector NOR é sempre de 512 bytes.</span><span class="sxs-lookup"><span data-stu-id="df667-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-268">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-268">Input Parameters</span></span>

- <span data-ttu-id="df667-269">*nor_flash* NEM ponteiro de instância flash.</span><span class="sxs-lookup"><span data-stu-id="df667-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="df667-270">*logical_sector*: Sector lógico para ler.</span><span class="sxs-lookup"><span data-stu-id="df667-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="df667-271">*tampão*: Ponteiro para destino para o conteúdo do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="df667-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="df667-272">Note que o tampão é assumido como 512 bytes e alinhado para acesso ULONG.</span><span class="sxs-lookup"><span data-stu-id="df667-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-273">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-273">Return Values</span></span>

- <span data-ttu-id="df667-274">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-275">**LX_ERROR**: (0x01) Leitura de erros NOR flash sector.</span><span class="sxs-lookup"><span data-stu-id="df667-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-276">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-276">Allowed From</span></span>

<span data-ttu-id="df667-277">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-278">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="df667-279">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-279">See Also</span></span>

- <span data-ttu-id="df667-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="df667-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="df667-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="df667-289">Release NOR flash sector</span><span class="sxs-lookup"><span data-stu-id="df667-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="df667-291">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-291">Description</span></span>

<span data-ttu-id="df667-292">Este serviço liberta o mapeamento do sector lógico na instância de flash NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="df667-293">Libertar um sector lógico quando não utilizado torna o nível de desgaste LevelX mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="df667-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-294">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-294">Input Parameters</span></span>

- <span data-ttu-id="df667-295">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="df667-296">*logical_sector*: Sector lógico para a libertação.</span><span class="sxs-lookup"><span data-stu-id="df667-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-297">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-297">Return Values</span></span>

- <span data-ttu-id="df667-298">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span><span class="sxs-lookup"><span data-stu-id="df667-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-300">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-300">Allowed From</span></span>

<span data-ttu-id="df667-301">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-302">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="df667-303">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-303">See Also</span></span>

- <span data-ttu-id="df667-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="df667-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="df667-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="df667-313">Escrever NOR flash sector</span><span class="sxs-lookup"><span data-stu-id="df667-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="df667-314">Prototype</span><span class="sxs-lookup"><span data-stu-id="df667-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="df667-315">Descrição</span><span class="sxs-lookup"><span data-stu-id="df667-315">Description</span></span>

<span data-ttu-id="df667-316">Este serviço escreve o sector lógico especificado na instância de flash NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="df667-317">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="df667-317">Input Parameters</span></span>

- <span data-ttu-id="df667-318">*nor_flash:* NEM ponteiro de exemplos de flash.</span><span class="sxs-lookup"><span data-stu-id="df667-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="df667-319">*logical_sector*: Sector lógico para escrever.</span><span class="sxs-lookup"><span data-stu-id="df667-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="df667-320">*tampão*: Ponteiro para o conteúdo do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="df667-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="df667-321">Note que o tampão é assumido como 512 bytes alinhados para o acesso ulong.</span><span class="sxs-lookup"><span data-stu-id="df667-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="df667-322">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="df667-322">Return Values</span></span>

- <span data-ttu-id="df667-323">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="df667-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="df667-324">**LX_NO_SECTORS**: (0x02) Não há mais sectores livres disponíveis para executar a escrita.</span><span class="sxs-lookup"><span data-stu-id="df667-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="df667-325">**LX_ERROR**: (0x01) Erro libertando o sector dos flashs NOR.</span><span class="sxs-lookup"><span data-stu-id="df667-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="df667-326">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="df667-326">Allowed From</span></span>

<span data-ttu-id="df667-327">Fios</span><span class="sxs-lookup"><span data-stu-id="df667-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="df667-328">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df667-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="df667-329">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df667-329">See Also</span></span>

- <span data-ttu-id="df667-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="df667-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="df667-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="df667-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="df667-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="df667-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="df667-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="df667-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="df667-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="df667-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="df667-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="df667-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="df667-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="df667-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="df667-337">lx_nor_flash_sector_release</span></span>
