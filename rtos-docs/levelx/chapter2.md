---
title: Capítulo 2 - Instalação e utilização do Azure RTOS LevelX
description: A instalação e utilização do LevelX é simples e descrita nas seguintes secções deste capítulo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cfd2d616896e1797114e55abcaf1a7559685282f29c2d0dee8274d2a26ea8f0e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790314"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a>Capítulo 2 - Instalação e utilização do Azure RTOS LevelX

A instalação e utilização do Azure RTOS LevelX é simples e descrita nas seguintes secções deste capítulo.

## <a name="distribution"></a>Distribuição

O LevelX é distribuído em ANSI C, onde cada função está contida no seu próprio ficheiro C separado. Os ficheiros na distribuição levelX são os seguintes.
- lx_api.h
- lx_nand_flash_256byte_ecc_check.c
- lx_nand_flash_256byte_ecc_compute.c
- lx_nand_flash_block_full_update.c
- lx_nand_flash_block_reclaim.c
- lx_nand_flash_close.c
- lx_nand_flash_defragment.c  
- lx_nand_flash_extended_cache_enable.c
- lx_nand_flash_initialize.c
- lx_nand_flash_logical_sector_find.c
- lx_nand_flash_next_block_to_erase_find.c
- lx_nand_flash_open.c
- lx_nand_flash_page_ecc_check.c
- lx_nand_flash_page_ecc_compute.c  
- lx_nand_flash_partial_defragment.c
- lx_nand_flash_physical_page_allocate.c
- lx_nand_flash_sector_mapping_cache_invalidate.c
- lx_nand_flash_sector_read.c
- lx_nand_flash_sector_release.c
- lx_nand_flash_sector_write.c
- lx_nand_flash_system_error.c
- lx_nor_flash_block_reclaim.c
- lx_nor_flash_close.c
- lx_nor_flash_defragment.c  
- lx_nor_flash_extended_cache_enable.c
- lx_nor_flash_initialize.c
- lx_nor_flash_logical_sector_find.c
- lx_nor_flash_next_block_to_erase_find.c
- lx_nor_flash_open.c
- lx_nor_flash_partial_defragment.c
- lx_nor_flash_physical_sector_allocate.c
- lx_nor_flash_sector_mapping_cache_invalidate.c
- lx_nor_flash_sector_read.c
- lx_nor_flash_sector_release.c
- lx_nor_flash_sector_write.c
- lx_nor_flash_system_error.c

Há também amostras de simulador e controlador FileX para ambos os casos LevelX NAND e NOR, da seguinte forma.

- demo_filex_nand_flash.c  
- fx_nand_flash_simulated_driver.c
- lx_nand_flash_simulator.c
- demo_filex_nor_flash.c  
- fx_nor_flash_simulated_driver.c
- lx_nor_flash_simulator.c

É claro que, se apenas for necessário um flash NAND, apenas são necessários os ficheiros flash NAND LevelX ***(lx_nand_ \* .c).*** Da mesma forma, se apenas não forem necessários flash, apenas são necessários os ficheiros DE FLASH NOR (**_lx_nor_ \_ .c***)

## <a name="configuration-options"></a>Opções de configuração

O LevelX pode ser configurado no momento da compilação através das definições condicionais descritas abaixo. Basta adicionar a definição desejada à compilação de cada fonte LevelX para utilizar a opção.

- **LX_DIRECT_READ**: Definida, esta opção contorna a rotina de leitura do flash NOR a favor ou a leitura direta da memória NOR, resultando num aumento significativo de desempenho.
- **LX_FREE_SECTOR_DATA_VERIFY**: Definido, isto faz com que a lógica de abertura de instância LevelX NOR para verificar os sectores NOR livres são todos uns.
- **LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: Por padrão, este valor é de 16 e define o tamanho da cache de mapeamento do sector lógico. Os grandes valores melhoram o desempenho, mas a memória de custos. O tamanho mínimo é de 8 e todos os valores devem ser uma potência de 2.
- **LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Definido, isto cria uma cache de mapeamento direto, de modo que não há falhas de cache. Também requer que LX_NAND_SECTOR_MAPPING_CACHE_SIZE represente o número exato de páginas totais no seu dispositivo flash.
- **LX_NOR_DISABLE_EXTENDED_CACHE**: Definido, isto desativou a cache NOR estendida.
- **LX_NOR_EXTENDED_CACHE_SIZE**: Por defeito, este valor é de 8, o que representa um máximo de 8 sectores que podem ser cached em um caso NOR.
- **LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: Por padrão, este valor é de 16 e define o tamanho da cache de mapeamento do sector lógico. Os grandes valores melhoram o desempenho, mas a memória de custos. O tamanho mínimo é de 8 e todos os valores devem ser uma potência de 2.
- **LX_THREAD_SAFE_ENABLE**: Definido, isto torna o LevelX seguro com um objeto mutex ThreadX em toda a API.
- **LX_STANDALONE_ENABLE**: Definido, permite que o LevelX seja utilizado em modo autónomo (sem Azure RTOS). Por padrão, este símbolo não está definido.

> [!IMPORTANT]
> Ao utilizar o LevelX no modo Autónomo **(LX_STANDALONE_ENABLE** deve ser definido), não são necessários ficheiros/bibliotecas ThreadX. A função de segurança de linha LevelX é desativada neste modo.

## <a name="using-levelx"></a>Usando o LevelX

Para utilizar o LevelX, por si só ou com o FileX, inclua o ficheiro ***lx_api.h** _ no código que faz referência à API LevelX. Certifique-se também de que o código do objeto LevelX está disponível no momento do link. Por favor, examine os ficheiros _*_demo_filex_nand_flash.c_*_ e _ *_demo_filex_nor_flash.c_** para exemplos de como usar o LevelX.
