---
title: Capítulo 4 - Azure RTOS LevelX NAND APIs
description: As APIs Azure RTOS LevelX NAND disponíveis para a aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d92b6c10921b4d04345610e139101e93c7a439ff695a89a79245894ad9ef1fec
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790288"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Capítulo 4 - Azure RTOS LevelX NAND APIs

As APIs Azure RTOS LevelX NAND disponíveis para a aplicação são:

- ***lx_nand_flash_close** _: _Close flash instance NAND*
- ***lx_nand_flash_defragment** _: _Defragment flash instance NAND*
- ***lx_nand_flash_extended_cache_enable** _: _Enable/desativar cache NAND estendido*
- ***lx_nand_flash_initialize** _: _Initialize suporte flash NAND*
- ***lx_nand_flash_open** _: _Open flash instance NAND*
- ***lx_nand_flash_page_ecc_check** _: página de _Check para erros do ECC com correção*
- ***lx_nand_flash_page_ecc_compute** _: _Computes ECC para página*
- ***lx_nand_flash_partial_defragment** _: _Partial desfragmentação da flash instance NAND*
- ***lx_nand_flash_sector_read** _: _Read sector flash NAND*
- ***lx_nand_flash_sector_release** _: _Release sector flash NAND*
- ***lx_nand_flash_sector_write** _: _Write sector flash NAND*

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Encerrar a flash instance NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

Este serviço encerra a flash instance NAND previamente aberta.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro de fecho de flash.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

Defragment NAND flash instance

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Description

Este serviço desfragmenta a flash instance NAND previamente aberta. O processo de desfragmentamento maximiza o número de páginas e blocos gratuitos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro desfragmentando flash instance.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

Ativar/desativar cache NAND estendido

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

Este serviço implementa uma camada de cache em RAM utilizando a memória fornecida pela aplicação. A quantidade total de memória necessária para o funcionamento total da cache pode ser calculada da seguinte forma:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Se a memória fornecida não for suficientemente grande para acomodar a cache NAND completa, esta rotina permitirá o máximo possível da cache flash NAND com base na memória fornecida.

A cache NAND é desativada se o endereço de memória especificado for NU. Assim, a cache NAND pode ser usada de forma temporária.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.  
- **memória**: Endereço inicial para memória cache alinhado para acesso ULONG. Um valor de LX_NULL desativa a cache.  
- **tamanho**: O tamanho dos bytes da memória fornecida.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Não há memória suficiente para um elemento da cache NAND.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

Inicialize o suporte flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Description

Este serviço inicializa o suporte de flash LEVELX NAND. Deve ser chamado antes de qualquer outra NID LEVELX.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro inicializando o suporte flash NAND.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

Abra a flash instance NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Description

Este serviço abre uma instância de flash NAND com o bloco de controlo de flash NAND especificado e a função de inicialização do controlador. Note que a função de inicialização do controlador é responsável pela instalação de vários ponteiros de função para leitura, escrita e apagamento de blocos/páginas do hardware NAND associado a esta instância flash NAND.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **nome**: Nome da flash instance NAND.
- **nand_driver_initialize**: Função ponteiro para a função de inicialização do controlador de flash NAND. Consulte o Capítulo 3 deste guia para obter mais detalhes sobre as responsabilidades do condutor flash NAND.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro de abertura da flash instance NAND.
- **LX_NO_MEMORY**: (0x08) O condutor não forneceu o tampão para a leitura de uma página na RAM.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

Ver página para erros do ECC com correção

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

Este serviço verifica a integridade do tampão de página NAND fornecido com o ECC fornecido. O tamanho da página (definido no ponteiro de instância flash NAND) é assumido como um múltiplo de 256 bytes e o código ECC fornecido é capaz de corrigir um erro de 1 bit em cada parte de 256 bytes da página.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **page_buffer**: Ponteiro para o tampão da página flash NAND.
- **ecc_buffer**: Ponter para ECC para a página flash NAND. Note que existem 3 bytes ECC por 256 byte porção da página.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS**: (0x00) a página NAND não tem erros.
- **LX_NAND_ERROR_CORRECTED**: (0x06) Erros de 1 ou mais bits foram corrigidos na página NAND — correção(s) estão no tampão de página.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Demasiados erros para corrigir na página NAND.

### <a name="allowed-from"></a>Permitido a partir de

Controlador LevelX

### <a name="example"></a>Exemplo

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

Compute ECC para página

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Description

Este serviço calcula o ECC do tampão de página NAND fornecido e devolve o ECC no tampão ECC fornecido. O tamanho da página é presumindo-se ser um múltiplo de 256 bytes (definido no ponteiro de flash nand). O código ECC é utilizado para verificar a integridade da página quando é lido posteriormente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **page_buffer**: Ponteiro para o tampão da página flash NAND.
- **ecc_buffer**: Ponte para o destino para ECC da flash page NAND. Note que devem ser 3 bytes de armazenamento ECC por porção de 256 byte da página. Por exemplo, uma página byte 2048 exigiria 24 bytes para o ECC.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) ECC calculado com êxito.
- **LX_ERROR:**(0x01) Erro de cálculo ECC.

### <a name="allowed-from"></a>Permitido a partir de

Controlador LevelX

### <a name="example"></a>Exemplo

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

Desfragmentação parcial da flash instance NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Description

Este serviço desfragmenta a instância flash NAND previamente aberta até ao número máximo de blocos especificados. O processo de desfragmentamento maximiza o número de páginas e blocos gratuitos.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **max_blocks:** Número máximo de blocos.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro desfragmentando flash instance.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

Leia o setor flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Este serviço lê o sector lógico a partir da flash instance NAND e se for bem-sucedido devolve o conteúdo no tampão fornecido. Note que o tamanho do sector NAND é sempre o tamanho da página do hardware NAND subjacente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **logical_sector**: Sector lógico para ler.
- **tampão**: Ponteiro para destino para o conteúdo do sector lógico. Note que o tampão é assumido como do tamanho do tamanho da página flash NAND e alinhado para o acesso ulong.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Error reading NAND flash sector.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

Libertar o sector flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

Este serviço liberta o mapeamento do sector lógico na instância flash NAND. Libertar um sector lógico quando não utilizado torna o nível de desgaste LevelX mais eficiente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **logical_sector**: Sector lógico para a libertação.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Error NAND flash sector write.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

Escreva o sector flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Este serviço escreve o sector lógico especificado na instância flash NAND.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nand_flash**: Ponteiro de flash nand.
- **logical_sector**: Sector lógico para escrever.
- **tampão**: Ponteiro para o conteúdo do sector lógico. Note que o tampão é assumido como do tamanho do tamanho da página flash NAND e alinhado para o acesso ulong.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_NO_SECTORS**: (0x02) Não há mais sectores livres disponíveis para executar a escrita.
- **LX_ERROR**: (0x01) Erro libertando o sector flash NAND.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Consulte também

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
