---
title: Capítulo 4 - Azure RTOS LevelX NAND APIs
description: As APIs Azure RTOS LevelX NAND disponíveis para a aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104827062"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="2fc89-103">Capítulo 4 - Azure RTOS LevelX NAND APIs</span><span class="sxs-lookup"><span data-stu-id="2fc89-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="2fc89-104">As APIs Azure RTOS LevelX NAND disponíveis para a aplicação são:</span><span class="sxs-lookup"><span data-stu-id="2fc89-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="2fc89-105">***lx_nand_flash_close** _: _Close flash instance NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="2fc89-106">***lx_nand_flash_defragment** _: _Defragment flash instance NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="2fc89-107">***lx_nand_flash_extended_cache_enable** _: _Enable/desativar cache NAND estendido*</span><span class="sxs-lookup"><span data-stu-id="2fc89-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="2fc89-108">***lx_nand_flash_initialize** _: _Initialize suporte flash NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="2fc89-109">***lx_nand_flash_open** _: _Open flash instance NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="2fc89-110">***lx_nand_flash_page_ecc_check** _: página de _Check para erros do ECC com correção*</span><span class="sxs-lookup"><span data-stu-id="2fc89-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="2fc89-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC para página*</span><span class="sxs-lookup"><span data-stu-id="2fc89-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="2fc89-112">***lx_nand_flash_partial_defragment** _: _Partial desfragmentação da flash instance NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="2fc89-113">***lx_nand_flash_sector_read** _: _Read sector flash NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="2fc89-114">***lx_nand_flash_sector_release** _: _Release sector flash NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="2fc89-115">***lx_nand_flash_sector_write** _: _Write sector flash NAND*</span><span class="sxs-lookup"><span data-stu-id="2fc89-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="2fc89-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-116">lx_nand_flash_close</span></span>

<span data-ttu-id="2fc89-117">Encerrar a flash instance NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="2fc89-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-119">Description</span></span>

<span data-ttu-id="2fc89-120">Este serviço encerra a flash instance NAND previamente aberta.</span><span class="sxs-lookup"><span data-stu-id="2fc89-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-121">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-121">Input Parameters</span></span>

- <span data-ttu-id="2fc89-122">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-123">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-123">Return Values</span></span>

- <span data-ttu-id="2fc89-124">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-125">**LX_ERROR**: (0x01) Erro de fecho de flash.</span><span class="sxs-lookup"><span data-stu-id="2fc89-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-126">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-126">Allowed From</span></span>

<span data-ttu-id="2fc89-127">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-129">See Also</span></span>

- <span data-ttu-id="2fc89-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="2fc89-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="2fc89-141">Defragment NAND flash instance</span><span class="sxs-lookup"><span data-stu-id="2fc89-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-142">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="2fc89-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-143">Description</span></span>

<span data-ttu-id="2fc89-144">Este serviço desfragmenta a flash instance NAND previamente aberta.</span><span class="sxs-lookup"><span data-stu-id="2fc89-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="2fc89-145">O processo de desfragmentamento maximiza o número de páginas e blocos gratuitos.</span><span class="sxs-lookup"><span data-stu-id="2fc89-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-146">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-146">Input Parameters</span></span>

- <span data-ttu-id="2fc89-147">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-148">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-148">Return Values</span></span>

- <span data-ttu-id="2fc89-149">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-150">**LX_ERROR**: (0x01) Erro desfragmentando flash instance.</span><span class="sxs-lookup"><span data-stu-id="2fc89-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-151">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-151">Allowed From</span></span>

<span data-ttu-id="2fc89-152">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-154">See Also</span></span>

- <span data-ttu-id="2fc89-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="2fc89-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="2fc89-166">Ativar/desativar cache NAND estendido</span><span class="sxs-lookup"><span data-stu-id="2fc89-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="2fc89-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-168">Description</span></span>

<span data-ttu-id="2fc89-169">Este serviço implementa uma camada de cache em RAM utilizando a memória fornecida pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="2fc89-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="2fc89-170">A quantidade total de memória necessária para o funcionamento total da cache pode ser calculada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2fc89-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="2fc89-171">Se a memória fornecida não for suficientemente grande para acomodar a cache NAND completa, esta rotina permitirá o máximo possível da cache flash NAND com base na memória fornecida.</span><span class="sxs-lookup"><span data-stu-id="2fc89-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="2fc89-172">A cache NAND é desativada se o endereço de memória especificado for NU.</span><span class="sxs-lookup"><span data-stu-id="2fc89-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="2fc89-173">Assim, a cache NAND pode ser usada de forma temporária.</span><span class="sxs-lookup"><span data-stu-id="2fc89-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-174">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-174">Input Parameters</span></span>

- <span data-ttu-id="2fc89-175">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="2fc89-176">**memória**: Endereço inicial para memória cache alinhado para acesso ULONG.</span><span class="sxs-lookup"><span data-stu-id="2fc89-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="2fc89-177">Um valor de LX_NULL desativa a cache.</span><span class="sxs-lookup"><span data-stu-id="2fc89-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="2fc89-178">**tamanho**: O tamanho dos bytes da memória fornecida.</span><span class="sxs-lookup"><span data-stu-id="2fc89-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-179">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-179">Return Values</span></span>

- <span data-ttu-id="2fc89-180">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-181">**LX_ERROR**: (0x01) Não há memória suficiente para um elemento da cache NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-182">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-182">Allowed From</span></span>

<span data-ttu-id="2fc89-183">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-184">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-185">See Also</span></span>

- <span data-ttu-id="2fc89-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="2fc89-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="2fc89-197">Inicialize o suporte flash NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="2fc89-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-199">Description</span></span>

<span data-ttu-id="2fc89-200">Este serviço inicializa o suporte de flash LEVELX NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="2fc89-201">Deve ser chamado antes de qualquer outra NID LEVELX.</span><span class="sxs-lookup"><span data-stu-id="2fc89-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-202">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-202">Input Parameters</span></span>

- <span data-ttu-id="2fc89-203">**Nenhuma**</span><span class="sxs-lookup"><span data-stu-id="2fc89-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-204">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-204">Return Values</span></span>

- <span data-ttu-id="2fc89-205">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-206">**LX_ERROR**: (0x01) Erro inicializando o suporte flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-207">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-207">Allowed From</span></span>

<span data-ttu-id="2fc89-208">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="2fc89-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-210">See Also</span></span>

- <span data-ttu-id="2fc89-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="2fc89-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-221">lx_nand_flash_open</span></span>

<span data-ttu-id="2fc89-222">Abra a flash instance NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="2fc89-224">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-224">Description</span></span>

<span data-ttu-id="2fc89-225">Este serviço abre uma instância de flash NAND com o bloco de controlo de flash NAND especificado e a função de inicialização do controlador.</span><span class="sxs-lookup"><span data-stu-id="2fc89-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="2fc89-226">Note que a função de inicialização do controlador é responsável pela instalação de vários ponteiros de função para leitura, escrita e apagamento de blocos/páginas do hardware NAND associado a esta instância flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-227">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-227">Input Parameters</span></span>

- <span data-ttu-id="2fc89-228">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-229">**nome**: Nome da flash instance NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="2fc89-230">**nand_driver_initialize**: Função ponteiro para a função de inicialização do controlador de flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="2fc89-231">Consulte o Capítulo 3 deste guia para obter mais detalhes sobre as responsabilidades do condutor flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-232">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-232">Return Values</span></span>

- <span data-ttu-id="2fc89-233">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-234">**LX_ERROR**: (0x01) Erro de abertura da flash instance NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="2fc89-235">**LX_NO_MEMORY**: (0x08) O condutor não forneceu o tampão para a leitura de uma página na RAM.</span><span class="sxs-lookup"><span data-stu-id="2fc89-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-236">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-236">Allowed From</span></span>

<span data-ttu-id="2fc89-237">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-239">See Also</span></span>

- <span data-ttu-id="2fc89-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="2fc89-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="2fc89-251">Ver página para erros do ECC com correção</span><span class="sxs-lookup"><span data-stu-id="2fc89-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-252">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="2fc89-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-253">Description</span></span>

<span data-ttu-id="2fc89-254">Este serviço verifica a integridade do tampão de página NAND fornecido com o ECC fornecido.</span><span class="sxs-lookup"><span data-stu-id="2fc89-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="2fc89-255">O tamanho da página (definido no ponteiro de instância flash NAND) é assumido como um múltiplo de 256 bytes e o código ECC fornecido é capaz de corrigir um erro de 1 bit em cada parte de 256 bytes da página.</span><span class="sxs-lookup"><span data-stu-id="2fc89-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-256">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-256">Input Parameters</span></span>

- <span data-ttu-id="2fc89-257">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-258">**page_buffer**: Ponteiro para o tampão da página flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="2fc89-259">**ecc_buffer**: Ponter para ECC para a página flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="2fc89-260">Note que existem 3 bytes ECC por 256 byte porção da página.</span><span class="sxs-lookup"><span data-stu-id="2fc89-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-261">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-261">Return Values</span></span>

- <span data-ttu-id="2fc89-262">**LX_SUCCESS**: (0x00) a página NAND não tem erros.</span><span class="sxs-lookup"><span data-stu-id="2fc89-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="2fc89-263">**LX_NAND_ERROR_CORRECTED**: (0x06) Erros de 1 ou mais bits foram corrigidos na página NAND — correção(s) estão no tampão de página.</span><span class="sxs-lookup"><span data-stu-id="2fc89-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="2fc89-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Demasiados erros para corrigir na página NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-265">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-265">Allowed From</span></span>

<span data-ttu-id="2fc89-266">Controlador LevelX</span><span class="sxs-lookup"><span data-stu-id="2fc89-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-267">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-268">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-268">See Also</span></span>

- <span data-ttu-id="2fc89-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="2fc89-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="2fc89-280">Compute ECC para página</span><span class="sxs-lookup"><span data-stu-id="2fc89-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-281">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="2fc89-282">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-282">Description</span></span>

<span data-ttu-id="2fc89-283">Este serviço calcula o ECC do tampão de página NAND fornecido e devolve o ECC no tampão ECC fornecido.</span><span class="sxs-lookup"><span data-stu-id="2fc89-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="2fc89-284">O tamanho da página é presumindo-se ser um múltiplo de 256 bytes (definido no ponteiro de flash nand).</span><span class="sxs-lookup"><span data-stu-id="2fc89-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="2fc89-285">O código ECC é utilizado para verificar a integridade da página quando é lido posteriormente.</span><span class="sxs-lookup"><span data-stu-id="2fc89-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-286">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-286">Input Parameters</span></span>

- <span data-ttu-id="2fc89-287">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-288">**page_buffer**: Ponteiro para o tampão da página flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="2fc89-289">**ecc_buffer**: Ponte para o destino para ECC da flash page NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="2fc89-290">Note que devem ser 3 bytes de armazenamento ECC por porção de 256 byte da página.</span><span class="sxs-lookup"><span data-stu-id="2fc89-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="2fc89-291">Por exemplo, uma página byte 2048 exigiria 24 bytes para o ECC.</span><span class="sxs-lookup"><span data-stu-id="2fc89-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-292">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-292">Return Values</span></span>

- <span data-ttu-id="2fc89-293">**LX_SUCCESS:**(0x00) ECC calculado com êxito.</span><span class="sxs-lookup"><span data-stu-id="2fc89-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="2fc89-294">**LX_ERROR:**(0x01) Erro de cálculo ECC.</span><span class="sxs-lookup"><span data-stu-id="2fc89-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-295">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-295">Allowed From</span></span>

<span data-ttu-id="2fc89-296">Controlador LevelX</span><span class="sxs-lookup"><span data-stu-id="2fc89-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-297">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-298">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-298">See Also</span></span>

- <span data-ttu-id="2fc89-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="2fc89-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="2fc89-310">Desfragmentação parcial da flash instance NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="2fc89-312">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-312">Description</span></span>

<span data-ttu-id="2fc89-313">Este serviço desfragmenta a instância flash NAND previamente aberta até ao número máximo de blocos especificados.</span><span class="sxs-lookup"><span data-stu-id="2fc89-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="2fc89-314">O processo de desfragmentamento maximiza o número de páginas e blocos gratuitos.</span><span class="sxs-lookup"><span data-stu-id="2fc89-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-315">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-315">Input Parameters</span></span>

- <span data-ttu-id="2fc89-316">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-317">**max_blocks:** Número máximo de blocos.</span><span class="sxs-lookup"><span data-stu-id="2fc89-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-318">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-318">Return Values</span></span>

- <span data-ttu-id="2fc89-319">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-320">**LX_ERROR**: (0x01) Erro desfragmentando flash instance.</span><span class="sxs-lookup"><span data-stu-id="2fc89-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-321">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-321">Allowed From</span></span>

<span data-ttu-id="2fc89-322">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-323">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-324">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-324">See Also</span></span>

- <span data-ttu-id="2fc89-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="2fc89-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="2fc89-336">Leia o setor flash NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="2fc89-338">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-338">Description</span></span>

<span data-ttu-id="2fc89-339">Este serviço lê o sector lógico a partir da flash instance NAND e se for bem-sucedido devolve o conteúdo no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="2fc89-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="2fc89-340">Note que o tamanho do sector NAND é sempre o tamanho da página do hardware NAND subjacente.</span><span class="sxs-lookup"><span data-stu-id="2fc89-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-341">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-341">Input Parameters</span></span>

- <span data-ttu-id="2fc89-342">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-343">**logical_sector**: Sector lógico para ler.</span><span class="sxs-lookup"><span data-stu-id="2fc89-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="2fc89-344">**tampão**: Ponteiro para destino para o conteúdo do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="2fc89-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="2fc89-345">Note que o tampão é assumido como do tamanho do tamanho da página flash NAND e alinhado para o acesso ulong.</span><span class="sxs-lookup"><span data-stu-id="2fc89-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-346">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-346">Return Values</span></span>

- <span data-ttu-id="2fc89-347">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span><span class="sxs-lookup"><span data-stu-id="2fc89-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-349">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-349">Allowed From</span></span>

<span data-ttu-id="2fc89-350">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-351">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-352">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-352">See Also</span></span>

- <span data-ttu-id="2fc89-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="2fc89-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="2fc89-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="2fc89-364">Libertar o sector flash NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-365">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="2fc89-366">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-366">Description</span></span>

<span data-ttu-id="2fc89-367">Este serviço liberta o mapeamento do sector lógico na instância flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="2fc89-368">Libertar um sector lógico quando não utilizado torna o nível de desgaste LevelX mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="2fc89-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-369">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-369">Input Parameters</span></span>

- <span data-ttu-id="2fc89-370">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-371">**logical_sector**: Sector lógico para a libertação.</span><span class="sxs-lookup"><span data-stu-id="2fc89-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-372">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-372">Return Values</span></span>

- <span data-ttu-id="2fc89-373">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span><span class="sxs-lookup"><span data-stu-id="2fc89-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-375">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-375">Allowed From</span></span>

<span data-ttu-id="2fc89-376">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-377">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-378">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-378">See Also</span></span>

- <span data-ttu-id="2fc89-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="2fc89-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="2fc89-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="2fc89-390">Escreva o sector flash NAND</span><span class="sxs-lookup"><span data-stu-id="2fc89-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="2fc89-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="2fc89-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="2fc89-392">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fc89-392">Description</span></span>

<span data-ttu-id="2fc89-393">Este serviço escreve o sector lógico especificado na instância flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2fc89-394">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2fc89-394">Input Parameters</span></span>

- <span data-ttu-id="2fc89-395">**nand_flash**: Ponteiro de flash nand.</span><span class="sxs-lookup"><span data-stu-id="2fc89-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="2fc89-396">**logical_sector**: Sector lógico para escrever.</span><span class="sxs-lookup"><span data-stu-id="2fc89-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="2fc89-397">**tampão**: Ponteiro para o conteúdo do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="2fc89-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="2fc89-398">Note que o tampão é assumido como do tamanho do tamanho da página flash NAND e alinhado para o acesso ulong.</span><span class="sxs-lookup"><span data-stu-id="2fc89-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="2fc89-399">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2fc89-399">Return Values</span></span>

- <span data-ttu-id="2fc89-400">**LX_SUCCESS:**(0x00) Pedido de sucesso.</span><span class="sxs-lookup"><span data-stu-id="2fc89-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="2fc89-401">**LX_NO_SECTORS**: (0x02) Não há mais sectores livres disponíveis para executar a escrita.</span><span class="sxs-lookup"><span data-stu-id="2fc89-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="2fc89-402">**LX_ERROR**: (0x01) Erro libertando o sector flash NAND.</span><span class="sxs-lookup"><span data-stu-id="2fc89-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2fc89-403">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2fc89-403">Allowed From</span></span>

<span data-ttu-id="2fc89-404">Fios</span><span class="sxs-lookup"><span data-stu-id="2fc89-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2fc89-405">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2fc89-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="2fc89-406">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fc89-406">See Also</span></span>

- <span data-ttu-id="2fc89-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="2fc89-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="2fc89-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="2fc89-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="2fc89-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="2fc89-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="2fc89-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="2fc89-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="2fc89-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="2fc89-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="2fc89-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="2fc89-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="2fc89-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="2fc89-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="2fc89-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="2fc89-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="2fc89-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="2fc89-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="2fc89-416">lx_nand_flash_sector_release</span></span>
