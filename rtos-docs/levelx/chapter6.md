---
title: Capítulo 6 - Azure RTOS LevelX NOR APIs
description: As APIs Azure RTOS LevelX NOR disponíveis para a aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790246"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Capítulo 6 - Azure RTOS LevelX NOR APIs

As funções Azure RTOS LevelX NOR API disponíveis para a aplicação são as seguintes.

- ***lx_nor_flash_close** _: _Close NEM flash instance*
- ***lx_nor_flash_defragment** _: _Defragment NEM flash instance*
- ***lx_nor_flash_extended_cache_enable** _: _Enable/desativar cache NOR estendido*
- ***lx_nor_flash_initialize** _: _Initialize SUPORTE DE FLASH*
- ***lx_nor_flash_open** _: _Open NEM flash instance*
- ***lx_nor_flash_partial_defragment** _: _Partial desfragmentação da instância flash NOR*
- ***lx_nor_flash_sector_read** _: _Read sector flash*
- ***lx_nor_flash_sector_release** _: _Release sector flash*
- ***lx_nor_flash_sector_write** _: _Write sector flash*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Encerrar a instância flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

Este serviço encerra a instância de flash NOR previamente aberta.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro de fecho de flash.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

Defragment NOR flash instance

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Description

Este serviço desfragmenta a instância de flash NOR previamente aberta. O processo de desfragmentamento maximiza o número de sectores e blocos livres.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro desfragmentando flash instance.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

Ativar/desativar cache NOR estendido

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Description

Este serviço implementa uma camada de cache do sector NOR na RAM utilizando a memória fornecida pela aplicação. Cada 512 bytes de memória fornecidos traduz-se num sector NOR que pode ser em cache. Os sectores em cache são aqueles que contêm a informação de controlo de blocos, por exemplo, a contagem de apagamento, o mapa do sector livre e a informação de mapeamento sectorial. Os sectores de dados não são armazenados nesta cache.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **nor_flash:** NEM ponteiro de exemplos de flash.  
- **memória**: Endereço inicial para memória cache, alinhado para acesso ULONG. Um valor de LX_NULL desativa a cache.  
- **tamanho**: O tamanho dos bytes da memória fornecida (deve ser múltiplo de 512 bytes).

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Não há memória suficiente para um sector NOR.
- **LX_DISABLED:**(0x09) NEM cache estendida desativada por opção de configuração.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

Inicializar NOR suporte flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Description

Este serviço inicializa o suporte de flash LevelX NOR. Deve ser chamado antes de qualquer outro LevelX NOR APIs.

### <a name="input-parameters"></a>Parâmetros de Entrada

- **Nenhuma**

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro inicializando NOR suporte de flash.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, Threads

### <a name="example"></a>Exemplo

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

Abrir a instância flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Description

Este serviço abre uma instância de flash NOR com o bloco de controlo de flash NOR especificado e a função de inicialização do controlador. Note que a função de inicialização do controlador é responsável pela instalação de vários ponteiros de função para a leitura, escrita e apagamento de blocos do hardware NOR associados a esta instância de flash NOR.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.
- *nome*: Nome da instância flash NOR.
- *nor_driver_initialize*: Função ponteiro para nor função de iniciação do controlador flash. Consulte o capítulo 5 deste guia para obter mais detalhes sobre as responsabilidades do condutor flash NOR.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Abertura de erro NEM flash instance.
- **LX_NO_MEMORY**: (0x08) O condutor não forneceu tampão para a leitura de nenhum sector na RAM.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

Desfragmentação parcial da instância flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Description

Este serviço desfragmenta a instância de flash NOR previamente aberta até ao número máximo de blocos especificados. O processo de desfragmentamento maximiza o número de sectores e blocos livres.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.
- *max_blocks:* Número máximo de blocos.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Erro desfragmentando flash instance.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

Ler NOR flash sector

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Este serviço lê o sector lógico a partir da instância de flash NOR e se for bem-sucedido devolve o conteúdo no tampão fornecido. Note que o tamanho do sector NOR é sempre de 512 bytes.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash* NEM ponteiro de instância flash.
- *logical_sector*: Sector lógico para ler.
- *tampão*: Ponteiro para destino para o conteúdo do sector lógico. Note que o tampão é assumido como 512 bytes e alinhado para acesso ULONG.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Leitura de erros NOR flash sector.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

Release NOR flash sector

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Description

Este serviço liberta o mapeamento do sector lógico na instância de flash NOR. Libertar um sector lógico quando não utilizado torna o nível de desgaste LevelX mais eficiente.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.
- *logical_sector*: Sector lógico para a libertação.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_ERROR**: (0x01) Error NOR flash sector write.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

Escrever NOR flash sector

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Description

Este serviço escreve o sector lógico especificado na instância de flash NOR.

### <a name="input-parameters"></a>Parâmetros de Entrada

- *nor_flash:* NEM ponteiro de exemplos de flash.
- *logical_sector*: Sector lógico para escrever.
- *tampão*: Ponteiro para o conteúdo do sector lógico. Note que o tampão é assumido como 512 bytes alinhados para o acesso ulong.

### <a name="return-values"></a>Valores de devolução

- **LX_SUCCESS:**(0x00) Pedido de sucesso.
- **LX_NO_SECTORS**: (0x02) Não há mais sectores livres disponíveis para executar a escrita.
- **LX_ERROR**: (0x01) Erro libertando o sector dos flashs NOR.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Consulte também

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
