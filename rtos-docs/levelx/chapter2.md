---
title: Capítulo 2 - Instalação e utilização do Azure RTOS LevelX
description: A instalação e utilização do LevelX é simples e descrita nas seguintes secções deste capítulo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223320"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="dc713-103">Capítulo 2 - Instalação e utilização do Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="dc713-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="dc713-104">A instalação e utilização do Azure RTOS LevelX é simples e descrita nas seguintes secções deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="dc713-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="dc713-105">Distribuição</span><span class="sxs-lookup"><span data-stu-id="dc713-105">Distribution</span></span>

<span data-ttu-id="dc713-106">O LevelX é distribuído em ANSI C, onde cada função está contida no seu próprio ficheiro C separado.</span><span class="sxs-lookup"><span data-stu-id="dc713-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="dc713-107">Os ficheiros na distribuição levelX são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="dc713-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="dc713-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="dc713-108">lx_api.h</span></span>
- <span data-ttu-id="dc713-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="dc713-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="dc713-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="dc713-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="dc713-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="dc713-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="dc713-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="dc713-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="dc713-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="dc713-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="dc713-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="dc713-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="dc713-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="dc713-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="dc713-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="dc713-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="dc713-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="dc713-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="dc713-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="dc713-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="dc713-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="dc713-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="dc713-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="dc713-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="dc713-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="dc713-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="dc713-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="dc713-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="dc713-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="dc713-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="dc713-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="dc713-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="dc713-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="dc713-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="dc713-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="dc713-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="dc713-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="dc713-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="dc713-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="dc713-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="dc713-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="dc713-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="dc713-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="dc713-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="dc713-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="dc713-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="dc713-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="dc713-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="dc713-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="dc713-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="dc713-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="dc713-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="dc713-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="dc713-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="dc713-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="dc713-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="dc713-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="dc713-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="dc713-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="dc713-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="dc713-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="dc713-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="dc713-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="dc713-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="dc713-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="dc713-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="dc713-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="dc713-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="dc713-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="dc713-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="dc713-144">Há também amostras de simulador e controlador FileX para ambos os casos LevelX NAND e NOR, da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="dc713-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="dc713-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="dc713-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="dc713-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="dc713-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="dc713-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="dc713-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="dc713-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="dc713-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="dc713-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="dc713-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="dc713-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="dc713-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="dc713-151">É claro que, se apenas for necessário um flash NAND, apenas são necessários os ficheiros flash NAND LevelX ***(lx_nand_ \* .c).***</span><span class="sxs-lookup"><span data-stu-id="dc713-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="dc713-152">Da mesma forma, se apenas não forem necessários flash, apenas são necessários os ficheiros DE FLASH NOR (\*\*_lx_nor_ \_ .c\*\*\*)</span><span class="sxs-lookup"><span data-stu-id="dc713-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="dc713-153">Opções de configuração</span><span class="sxs-lookup"><span data-stu-id="dc713-153">Configuration Options</span></span>

<span data-ttu-id="dc713-154">O LevelX pode ser configurado no momento da compilação através das definições condicionais descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="dc713-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="dc713-155">Basta adicionar a definição desejada à compilação de cada fonte LevelX para utilizar a opção.</span><span class="sxs-lookup"><span data-stu-id="dc713-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="dc713-156">**LX_DIRECT_READ**: Definida, esta opção contorna a rotina de leitura do flash NOR a favor ou a leitura direta da memória NOR, resultando num aumento significativo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="dc713-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="dc713-157">**LX_FREE_SECTOR_DATA_VERIFY**: Definido, isto faz com que a lógica de abertura de instância LevelX NOR para verificar os sectores NOR livres são todos uns.</span><span class="sxs-lookup"><span data-stu-id="dc713-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="dc713-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: Por padrão, este valor é de 16 e define o tamanho da cache de mapeamento do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="dc713-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="dc713-159">Os grandes valores melhoram o desempenho, mas a memória de custos.</span><span class="sxs-lookup"><span data-stu-id="dc713-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="dc713-160">O tamanho mínimo é de 8 e todos os valores devem ser uma potência de 2.</span><span class="sxs-lookup"><span data-stu-id="dc713-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="dc713-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Definido, isto cria uma cache de mapeamento direto, de modo que não há falhas de cache.</span><span class="sxs-lookup"><span data-stu-id="dc713-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="dc713-162">Também requer que LX_NAND_SECTOR_MAPPING_CACHE_SIZE represente o número exato de páginas totais no seu dispositivo flash.</span><span class="sxs-lookup"><span data-stu-id="dc713-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="dc713-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Definido, isto desativou a cache NOR estendida.</span><span class="sxs-lookup"><span data-stu-id="dc713-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="dc713-164">**LX_NOR_EXTENDED_CACHE_SIZE**: Por defeito, este valor é de 8, o que representa um máximo de 8 sectores que podem ser cached em um caso NOR.</span><span class="sxs-lookup"><span data-stu-id="dc713-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="dc713-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: Por padrão, este valor é de 16 e define o tamanho da cache de mapeamento do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="dc713-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="dc713-166">Os grandes valores melhoram o desempenho, mas a memória de custos.</span><span class="sxs-lookup"><span data-stu-id="dc713-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="dc713-167">O tamanho mínimo é de 8 e todos os valores devem ser uma potência de 2.</span><span class="sxs-lookup"><span data-stu-id="dc713-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="dc713-168">**LX_THREAD_SAFE_ENABLE**: Definido, isto torna o LevelX seguro com um objeto mutex ThreadX em toda a API.</span><span class="sxs-lookup"><span data-stu-id="dc713-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="dc713-169">**LX_STANDALONE_ENABLE**: Definido, permite que o LevelX seja utilizado em modo autónomo (sem Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="dc713-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="dc713-170">Por padrão, este símbolo não está definido.</span><span class="sxs-lookup"><span data-stu-id="dc713-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc713-171">Ao utilizar o LevelX no modo Autónomo **(LX_STANDALONE_ENABLE** deve ser definido), não são necessários ficheiros/bibliotecas ThreadX.</span><span class="sxs-lookup"><span data-stu-id="dc713-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="dc713-172">A função de segurança de linha LevelX é desativada neste modo.</span><span class="sxs-lookup"><span data-stu-id="dc713-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="dc713-173">Usando o LevelX</span><span class="sxs-lookup"><span data-stu-id="dc713-173">Using LevelX</span></span>

<span data-ttu-id="dc713-174">Para utilizar o LevelX, por si só ou com o FileX, inclua o ficheiro \***lx_api.h** _ no código que faz referência à API LevelX.</span><span class="sxs-lookup"><span data-stu-id="dc713-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="dc713-175">Certifique-se também de que o código do objeto LevelX está disponível no momento do link.</span><span class="sxs-lookup"><span data-stu-id="dc713-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="dc713-176">Por favor, examine os ficheiros _*_demo_filex_nand_flash.c_*_ e _ *_demo_filex_nor_flash.c_*\* para exemplos de como usar o LevelX.</span><span class="sxs-lookup"><span data-stu-id="dc713-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
