---
title: Suporte Azure RTOS LevelX NAND
description: A memória flash NAND é comumente utilizada dentro do LevelX para grande armazenamento de dados, que é típico dos sistemas de ficheiros.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826269"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Capítulo 3 - Suporte Azure RTOS LevelX NAND

A memória flash NAND é comumente utilizada para o armazenamento de dados de grande porte, que é típico dos sistemas de ficheiros. A memória NAND consiste em *blocos.* Dentro de cada bloco NAND há uma série de *páginas.* Os blocos NAND são apagáveis, o que significa que todas as páginas dentro do bloco NAND são apagadas (definidas para todas as). Cada página de bloco NAND tem um conjunto de *bytes sobressalentes* que são utilizados pelo Azure RTOS LevelX para contabilidade, má gestão de blocos e deteção de erros. As páginas de blocos NAND estão disponíveis em vários tamanhos. Os tamanhos de página mais comuns são: 

| **Tamanho da Página** | **Bytes de reserva** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

A memória NAND difere da memória NOR na medida em que não existe acesso direto, ou seja, a memória NAND não pode ser lida diretamente do processador como a memória NOR. A memória NAND só pode ser escrita após uma apagar um número limitado de vezes. Mais uma vez, isto difere da memória NOR que pode ser escrita um número ilimitado de vezes desde que o pedido de escrita é limpar bits definidos. Finalmente, os bytes sobressalentes associados a cada página são exclusivos do flash NAND. As configurações típicas de bytes de reposição são como mostrado na tabela abaixo.

| **Bytes de reserva** | **Números byte** | **Configuração**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Bytes 0-2:     | Bytes ECC             |
|                           | Bytes 3,4,6,7: | Mapeamento do setor levelX |
|                           | Byte 5:        | Bandeira de bloco mau        |
| 16                        | Bytes 0-3,6-7: | Bytes ECC             |
|                           | Bytes 8-11:    | Mapeamento do setor levelX |
|                           | Bytes 12-15:   | Não é bem-de-suso                |
|                           | Byte 5:        | Bandeira de bloco mau        |
| 64                        | Byte 0:        | Bandeira de bloco mau        |
|                           | Bytes 2-5:     | Mapeamento do setor levelX |
|                           | Bytes 6-39:    | Não é bem-de-suso                |
|                           | Bytes 40-63:   | Bytes ECC             |

LevelX Utiliza 4 dos bytes sobressalentes de cada página NAND para acompanhar o sector lógico mapeado para a página física NAND. Estes 4 bytes são usados para implementar um número inteiro de 32 bits não assinado com um formato proprietário LevelX. A parte superior do campo de 32 bits (bit 31) é usada para indicar que o mapeamento lógico sector-a-página é válido. Se esta bit for 0, a informação nesta página já não é válida. A próxima bit - bit 30 - é usada para indicar que esta página está em processo de tornar-se obsoleta e um novo setor está sendo escrito. O bit 29 é utilizado para indicar quando a escrita de entrada de mapeamento está completa. Se o bit 29 for 0, a escrita de entrada de mapeamento está completa. Se o bit 29 estiver definido, a entrada de mapeamento estava em fase de escrita. Os bits 30 e 29 são utilizados na recuperação de uma potencial perda de energia enquanto atualizam uma nova página flash. Finalmente, os 29 bits inferiores (28-0) contêm o número do sector lógico para a página.

**Entrada de mapeamento levelX**

| Bit(s) | Significado |
| ------ | ------- |
| 31     | Bandeira válida. Quando o setor definido e lógico não é todos os que indicam que o mapeamento é válido |
| 30     | Bandeira obsoleta. Quando claro, este mapeamento ou é obsoleto ou está em vias de se tornar obsoleto. |
| 29     | Mapeamento da escrita de entrada está completo quando este bit é 0 |
| 0-28   | Sector lógico mapeado para esta página física - quando nem todos. |

O LevelX também utiliza a primeira página de cada bloco NAND para a contagem de apagamento de blocos, bem como a lista de páginas mapeadas quando o bloco está cheio. O formato da primeira página de um bloco NAND no LevelX é mostrado abaixo:

| Formato LevelX Block Page 0 |
|:--------------------------:|
| [Contagem de Apagamento de Blocos]        |
| [Mapeamento do Sector da Página 1]    |
| ...                        |
| [Página "n" Mapeamento do Sector]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> A informação de mapeamento da página só é escrita quando o bloco está cheio, ou seja, todas as páginas do bloco foram escritas. Isto permite uma pesquisa mais rápida de páginas gratuitas e mapeamento do setor lógico durante o tempo de execução.

## <a name="nand-bad-block-support"></a>Suporte de bloco mau NAND

A memória NAND também é mais provável de ter blocos maus do que a memória NOR. Isto deve-se, em grande parte, ao aumento do rendimento dos fabricantes de NAND, permitindo blocos ruins e exigindo que o software funcione em torno de tais blocos maus. LevelX lida com a gestão de blocos maus NAND simplesmente mapeando em torno de blocos maus.

O LevelX também fornece APIs para códigos de correção de erros de hamming de 256 byte (ECC) para que o controlador de Nível NºX subjacente utilize para calcular novos códigos ECC ou para executar uma correção de erro de 1 bit na leitura de página em cada secção de 256 bytes da página.

## <a name="nand-driver-requirements"></a>Requisitos do condutor nand

O LevelX requer um flash driver NAND subjacente que seja específico da parte de flash subjacente e da implementação de hardware. O controlador é especificado para LevelX durante a inicialização através do ***lx_nand_flash_open*** da API . O protótipo do condutor LevelX é o seguinte.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

O parâmetro *de instância* especifica o bloco de controlo NAND LevelX. A função de inicialização do controlador é responsável pela configuração de todos os outros serviços ao nível do condutor para a instância de Nível N/ LevelX associada. Os serviços necessários para cada instância NAND LevelX são apresentados na lista abaixo.

- Ler Página
- Escrever Página
- Apagamento de blocos
- Verificação de blocos apagadas
- Verificação de página apagada
- Estado de bloqueio obter
- Conjunto de estado de bloqueio
- Bloquear bytes extra obter
- Conjunto de bytes extra de blocos
- Manipulador de erros do sistema

## <a name="driver-initialization"></a>Inicialização do condutor

Estes serviços são configurados através da definição de ponteiros de função no **LX_NAND_FLASH** instância dentro da função de inicialização do condutor. A função de inicialização do controlador também especifica o número total de blocos, páginas por bloco, bytes por página e uma área de RAM suficientemente grande para ler uma página na memória. A função de inicialização do controlador provavelmente também executa tarefas adicionais de inicialização do dispositivo e/ou de implementação específicas antes de devolver **LX_SUCCESS**.

## <a name="driver-read-page"></a>Página de leitura do motorista

O serviço de "página de leitura" do controlador LevelX NAND é responsável pela leitura de uma página específica num bloco específico do flash NAND. Toda a lógica de verificação e correção de erros é da responsabilidade do serviço de condutor. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "ler página" do condutor nand LevelX é dado abaixo.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Onde *o bloco* e a *página* identificam qual página para ler e *destino* e *palavras* especificam onde colocar o conteúdo da página e quantas palavras de 32 bits para ler.

## <a name="driver-write-page"></a>Página de escrita do motorista

O serviço de "página de escrita" do controlador LevelX NAND é responsável por escrever uma página específica no bloco especificado do flash NAND. Toda a verificação de erros e a computação ECC é da responsabilidade do serviço de motorista. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "write page" do controlador NaND LevelX é apresentado abaixo.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Onde *o bloco* e a *página* identificam qual página para escrever e *origem* e *palavras* especificam a origem da escrita e quantas palavras de 32 bits para escrever.

> [!NOTE]
> O LevelX depende do controlador para deteção de erros de baixo nível ao escrever na página flash, que normalmente envolve ler a página de volta e comparar com o tampão de escrita para garantir que a escrita foi bem sucedida.

## <a name="driver-block-erase"></a>Apagamento do bloco de motorista

O serviço de "apagar bloco" do controlador LevelX NAND é responsável por apagar o bloco especificado do flash NAND. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço de "apagar bloco" do condutor LevelX NAND é o seguinte.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Onde *o bloco* identifica qual bloco apagar. O parâmetro *erase_count* é fornecido para fins de diagnóstico. Por exemplo, o condutor pode querer alertar outra parte do software da aplicação quando a contagem de apagamento exceder um limiar específico.

> [!NOTE]
> O LevelX depende do controlador para a deteção de erros de baixo nível quando o bloco é apagado, o que normalmente envolve garantir que todas as páginas do bloco são todas.

## <a name="driver-block-erased-verify"></a>Verificação apagada do bloco de motorista

O serviço de "verificar o bloqueio do bloco" LevelX é responsável por verificar se o bloco especificado do flash NAND é apagado. Se for apagado, o condutor NaND LevelX regressa **LX_SUCCESS**. Se o bloco não for apagado, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "blocked check" do condutor LevelX NAND é:

```c
INT nand_driver_block_erased_verify(ULONG block);
```

Onde *o bloco* especifica qual o bloco para verificar se é apagado.

> [!NOTE]
> O LevelX conta com o controlador para examinar todas as páginas e todos os bytes de cada página – incluindo bytes de reposição e dados – para garantir que são apagados (conter todas as).

## <a name="driver-page-erased-verify"></a>Página do condutor apagada Verificar

O serviço "page apagar a página" do controlador LevelX NAND é responsável por verificar se a página especificada do bloco especificado do flash NAND é apagada. Se for apagado, o condutor NaND LevelX regressa **LX_SUCCESS**. Se a página não for apagada, o controlador NAND LevelX regressa **LX_ERROR**. O protótipo do serviço "verificação de página apagada" do controlador LevelX NAND é:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
Quando *o bloco* especifica qual o bloco e a *página* especifica a página para verificar se é apagada.

> [!NOTE]
> O LevelX conta com o controlador para examinar todos os bytes da página especificada – incluindo bytes de reposição e dados – para garantir que são apagados (contêm todos os).

## <a name="driver-block-status-get"></a>Estado do bloqueio do motorista obter

O serviço "block status get" do controlador LevelX NAND é responsável pela recuperação da bandeira de bloco mau do bloco especificado do flash NAND. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "block status get" do condutor LevelX NAND é: mostrado abaixo.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

Onde *o bloco* especifica qual bloco e *bad_block_byte* especifica o destino para a bandeira de bloco ruim.

## <a name="driver-block-status-set"></a>Conjunto de estado do bloqueio do motorista

O serviço "conjunto de estado de bloqueio" do controlador LevelX NAND é responsável pela definição da bandeira de bloco mau do bloco especificado do flash NAND. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "conjunto de estado do bloco" do condutor LevelX NAND é:

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

Quando *o bloco* especificar qual o bloco e *bad_block_byte* especifica o valor da bandeira de bloco mau.

## <a name="driver-block-extra-bytes-get"></a>Driver Block Extra Bytes Get

O serviço "block extra bytes get" do controlador LevelX NAND é responsável pela recuperação de bytes extra associados a uma página específica de um bloco específico do flash NAND. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "block extra bytes get" do condutor LevelX NAND é:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

Quando *o bloco* especifica qual o bloco, a *página* especifica a página e o *destino* específicos especifica o destino para os bytes extra. O *tamanho* do parâmetro especifica quantos bytes extras obter.

## <a name="driver-block-extra-bytes-set"></a>Conjunto de bytes extra do bloco do motorista

O serviço "block extra bytes set" do controlador LevelX NAND é responsável pela definição de bytes extra numa página específica de um bloco específico do flash NAND. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "block extra bytes set" do condutor LevelX NAND é:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

Quando *o bloco* especifica qual o bloco, a *página* especifica a página específica e a *fonte* especifica a origem dos bytes extra. O *tamanho* do parâmetro especifica quantos bytes extras para definir.

## <a name="driver-system-error"></a>Erro do sistema do controlador

O serviço "manipulador de erros do sistema" LevelX NAND é responsável pela definição de erros de sistema de manuseamento detetados pelo LevelX. O processamento nesta rotina é dependente da aplicação. Se for bem sucedido, o condutor NaND LevelX regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor NaND LevelX regressa **LX_ERROR**. O protótipo do serviço "erro de sistema" do controlador NAND LevelX é:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

Quando *o bloco* especifica qual o bloco e a *página* especifica a página específica, o erro representado por *error_code* ocorreu.

## <a name="nand-simulated-driver"></a>Condutor simulado nand

O LevelX fornece um flash driver NAND simulado que simplesmente utiliza RAM para simular o funcionamento de uma peça de flash NAND. Por predefinição, o controlador simulado NAND fornece 8 blocos de flash NAND com 16 páginas por bloco e 2048 bytes por página.

A função de inicialização simulada do flash driver NAND é ***lx_nand_flash_simulator_initialize** _ e é definida em _*_lx_nand_flash_simulator.c_**. Este controlador também fornece um bom modelo para escrever controladores flash NAND específicos.

## <a name="nand-filex-integration"></a>Integração NAND FileX

Como mencionado anteriormente, o LevelX não depende do FileX para funcionamento. Todas as APIs do LevelX podem ser chamadas diretamente pelo software de aplicação para armazenar/recuperar dados brutos para os sectores lógicos fornecidos pelo LevelX. No entanto, o LevelX também suporta o FileX.

O ficheiro ***fx_nand_flash_simulated_driver.c*** contém um exemplo de controlador FileX para utilização com a simulação de flash NAND. Um aspeto interessante deste condutor é que combina setores lógicos de 512 bytes tipicamente utilizados pelo FileX em pedidos de leitura/escrita de um único sector lógico para o simulador LevelX usando páginas de 2048 byte. Isto resulta numa utilização mais eficiente da memória flash NAND. O controlador nand flash FileX para LevelX fornece um bom ponto de partida para escrever controladores FileX personalizados.  
  
> [!NOTE]
> O formato flash NAND filex deve ter um tamanho de bloco completo de sectores menos do que o flash NAND fornece. Isto ajudará a garantir um melhor desempenho durante o processamento do nível de desgaste. Técnicas adicionais para melhorar o desempenho da escrita no algoritmo de nivelamento de desgaste LevelX incluem o seguinte.

1. Certifique-se de que todas as escritas são exatamente um ou mais clusters de tamanho e começar em limites exatos do cluster.
1. Pré-alocar clusters antes de realizar grandes operações de escrita de ficheiros através da classe ***de APIs fx_file_allocate*** FileX.
1. Certifique-se de que o controlador FileX está habilitado a receber informações do sector de libertação e os pedidos feitos ao condutor para libertar os sectores são tratados no condutor, chamando ***lx_nor_flash_sector_release***.
1. O uso periódico de ***lx_nand_flash_defragment*** para libertar o maior número possível de blocos NAND e assim melhorar o desempenho da escrita.
1. Utilize a ***API lx_nand_flash_extended_cache_enable*** para fornecer uma cache RAM de vários recursos de bloco NAND para um desempenho mais rápido.
