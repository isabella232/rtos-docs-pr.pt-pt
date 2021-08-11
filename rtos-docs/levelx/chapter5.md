---
title: Capítulo 5 - Suporte Azure RTOS LevelX NOR
description: Nor flash memory é composto por blocos que são tipicamente divisíveis por 512 bytes. O Azure RTOS LevelX divide cada bloco de flash NOR em sectores lógicos de 512 byte.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5d06fa66f0cae29eeb2a89560704b2ef510597e44a565499bf672a75555f208
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790569"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Capítulo 5 - Suporte Azure RTOS LevelX NOR

Nor flash memory é composto por *blocos* que são tipicamente divisíveis por 512 bytes. Não existem conceito de uma *página* flash na memória flash NOR. Além disso, não existem bytes *sobressalentes* na memória flash NOR, pelo que o Azure RTOS LevelX deve utilizar a própria memória flash NOR para todas as informações de gestão. O acesso direto à leitura é possível na memória flash NOR. O acesso de escrita requer normalmente uma sequência especial de operações. Nem a memória flash pode ser escrita várias vezes, desde que os bits estejam a ser limpos. Os bits na memória flash NOR só podem ser definidos uma vez, através da operação do bloco de apagamento.

O LevelX divide cada bloco de flash NOR em *sectores lógicos* de 512 byte. Além disso, o LevelX utiliza os primeiros sectores "n" de cada bloco de flash NOR para armazenar informações de gestão. O formato da informação de gestão de memória flash LevelX NOR é:

**Formato de bloco LevelX NOR**

| Byte Offset  | Conteúdos                     |
| ------------ | ---------------------------- |
| 0            | [Contagem de Apagamento de Blocos]          |
| 4            | [Setor mínimo mapeado]      |
| 8            | [Sector Mapeado Máximo]      |
| 12           | [Mapa do Bit do Sector Livre]        |
| m            | [Seção de Mapeamento sector 0]     |
|              | …                            |
| m+4*(n-1)    | [Entrada de Mapeamento sectorial n]   |
|              | …                            |
| t            | [Sector 0 Conteúdos]          |
|              | …                            |
| s+512*(n-1) | [Sector "n" Conteúdos]         |

O Conde de *32 bits* de Eliminação de Blocos contém o número de vezes que o bloco foi apagado. O principal objetivo do LevelX é manter a contagem de apagamento de todos os blocos relativamente perto para ajudar a evitar que qualquer bloco se desgaste prematuramente. Os campos mínimos de 32 bits *do sector mapeado* e *do sector máximo mapeados* só são escritos quando todos os sectores lógicos do bloco foram mapeados e escritos. Estes campos são úteis para otimizar a operação de leitura do sector. A entrada *do Mapa do Bit do Sector Livre* é um mapa de um pouco onde cada bit corresponde a um setor não mapeado no bloco. Para este campo é mais eficaz a pesquisa no sector livre. Este é um campo de comprimento variável que requer uma palavra para cada 32 sectores do bloco. A matriz *de entrada de mapeamento sectorial* contém informações de mapeamento para cada sector do bloco. Cada entrada tem o seguinte formato:

**Entrada de Mapeamento do Setor**

| Bit(s) | Significado  |
| ------ | -------- |
| 31     | Bandeira válida. Quando o setor definido e lógico nem todos indicam que o mapeamento é válido |
| 30     | Bandeira obsoleta. Quando claro, este mapeamento ou é obsoleto ou está em vias de se tornar obsoleto. |
| 29     | Mapeamento da escrita de entrada está completo quando este bit é 0 |
| 0-28   | Sector lógico mapeado para este setor físico - quando nem todos. |

A parte superior do campo de 32 bits (bit 31) é usada para indicar que o mapeamento do sector lógico é válido. Se este bit for 0, a informação nesta entrada (e os correspondentes conteúdos sectoriais) deixaram de ser válidas. A próxima parte - bit 30 - é utilizada para indicar que este sector está em vias de se tornar obsoleto e está a ser escrito um novo sector. O bit 29 é utilizado para indicar quando a escrita de entrada de mapeamento está completa. Se o bit 29 for 0, a escrita de entrada de mapeamento está completa. Se o bit 29 estiver definido, a entrada de mapeamento estava em fase de escrita. Os bits 30 e 29 são usados na recuperação de uma potencial perda de energia enquanto atualizam um novo mapeamento do setor. Finalmente, os 29 bits mais baixos (28-0) contêm o número do sector lógico para o sector. Se um sector não tiver sido mapeado, todas as bits serão definidas, ou seja, terá um valor de 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>NOR Requisitos do condutor

O LevelX requer um controlador de flash NOR subjacente que seja específico da parte de flash subjacente e da implementação de hardware. O controlador é especificado para LevelX durante a inicialização através do ***lx_nor_flash_open*** da API . O protótipo do condutor LevelX é:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

O parâmetro "*exemplo*" especifica o bloco de controlo LevelX NOR. A função de inicialização do controlador é responsável pela configuração de todos os outros serviços ao nível do condutor para a instância de Nível N/ LevelX associada. Os serviços necessários para cada instância LevelX NOR são:

- Setor de Leitura
- Setor de Escrita
- Apagamento de blocos
- Verificação de blocos apagadas
- Manipulador de erros do sistema

## <a name="driver-initialization"></a>Inicialização do condutor

Estes serviços são configurados através da definição de ponteiros de função no **LX_NOR_FLASH** instância dentro da função de inicialização do controlador. A função de inicialização do controlador também é responsável por:

1. Especificando o endereço base do flash.
1. Especificando o número total de blocos e o número de palavras por bloco.
1. Um tampão RAM para ler um sector de flash (512 bytes) e alinhado para acesso ULONG.

A função de inicialização do controlador provavelmente também executa tarefas adicionais de inicialização do dispositivo e/ou de implementação específicas antes de devolver **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Setor de Leitura de Motorista

O serviço "reading sector" do condutor LevelX NOR é responsável pela leitura de um sector específico num bloco específico do flash NOR. Toda a lógica de verificação e correção de erros é da responsabilidade do serviço de condutor. Se for bem sucedido, o controlador LevelX NOR regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor LevelX NOR regressa *LX_ERROR*. O protótipo do serviço "ler sector de leitura" do condutor LevelX NOR é:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Onde "*flash_address*" especifica o endereço de um sector lógico dentro de um bloco de memória NOR e "*destino*" e "*palavras*" especificam onde colocar o conteúdo do sector e quantas palavras de 32 bits para ler.

## <a name="driver-write-sector"></a>Setor de Escrita de Motorista

O serviço "sector de escrita" LevelX NOR é responsável por escrever um sector específico num bloco do flash NOR. Toda a verificação de erros é da responsabilidade do serviço de motorista. Se for bem sucedido, o controlador LevelX NOR regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor LevelX NOR regressa **LX_ERROR**. O protótipo do serviço "sector de escrita" do condutor LevelX NOR é:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Onde "*flash_address*" especifica o endereço de um sector lógico dentro de um bloco de memória NOR flash e "*fonte*" e "*palavras*" especificam a fonte da escrita e quantas palavras de 32 bits para escrever.

> [!NOTE]
> O LevelX conta com o condutor para verificar se o sector da escrita foi bem sucedido. Isto é normalmente feito lendo o valor programado para garantir que corresponde ao valor solicitado a ser escrito.

## <a name="driver-block-erase"></a>Apagamento do bloco de motorista

O serviço de "apagar blocos" levelX NOR é responsável por apagar o bloco especificado do flash NOR. Se for bem sucedido, o controlador LevelX NOR regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor LevelX NOR regressa **LX_ERROR**. O protótipo do serviço de "eliminação de blocos" levelX NOR é:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Onde "*bloco*" identifica que BLOCO PARA apagar. O parâmetro "*erase_count*" é fornecido para fins de diagnóstico. Por exemplo, o condutor pode querer alertar outra parte do software da aplicação quando a contagem de apagamento exceder um limiar específico.

> [!NOTE]
> O LevelX conta com o controlador para examinar todos os bytes do bloco para garantir que são apagados (conter todos os).

## <a name="driver-block-erased-verify"></a>Verificação apagada do bloco de motorista

O serviço de "verificar o bloqueio do bloco" LevelX NOR é responsável por verificar se o bloco especificado do flash NOR é apagado. Se for apagado, o condutor LevelX NOR regressa **LX_SUCCESS**. Se o bloco não for apagado, o condutor LevelX NOR regressa **LX_ERROR**. O protótipo do serviço "blocked check" do controlador LevelX NOR é:

```c
INT nor_driver_block_erased_verify(ULONG block);
```

Onde "*bloco*" especifica qual bloco para verificar se é apagado.

> [!NOTE]
> O LevelX conta com o controlador para examinar todos os bytes do especificado para garantir que são apagados (conter todos os).

## <a name="driver-system-error"></a>Erro do sistema do controlador

O serviço "manipulador de erros do sistema" LevelX NOR é responsável pela definição de erros do sistema de manuseamento detetados pelo LevelX. O processamento nesta rotina é dependente da aplicação. Se for bem sucedido, o condutor LevelX NOR regressa **LX_SUCCESS**. Se não for bem sucedido, o condutor LevelX NOR regressa **LX_ERROR**. O protótipo do serviço "erro do sistema" do controlador LevelX NOR é:

```c
INT nor_driver_system_error(UINT error_code);
```

Onde "*error_code*" representa o erro que ocorreu.

## <a name="nor-simulated-driver"></a>NOR Simulado Condutor

O LevelX fornece um controlador de flash NOR simulado que simplesmente utiliza RAM para simular o funcionamento de uma peça de flash NOR. Por predefinição, o controlador simulado NOR fornece 8 blocos de flash NOR com 16 sectores de 512 bytes por bloco.

A função de inicialização simulada do condutor de flash NOR é ***lx_nor_flash_simulator_initialize** _ e é definida em _*_lx_nor_flash_simulator.c_**. Este controlador também fornece um bom modelo para escrever controladores flash NOR específicos.

## <a name="nor-filex-integration"></a>INTEGRAÇÃO NOR FileX

Como mencionado anteriormente, o LevelX não depende do FileX para funcionamento. Todas as APIs do LevelX podem ser chamadas diretamente pelo software de aplicação para armazenar/recuperar dados brutos para os sectores lógicos fornecidos pelo LevelX. No entanto, o LevelX também suporta o FileX.

O ficheiro ***fx_nor_flash_simulated_driver.c*** contém um exemplo de controlador FileX para utilização com a simulação de flash NOR. O controlador NOR flash FileX para o LevelX fornece um bom ponto de partida para a escrita de controladores FileX personalizados.

> [!NOTE]
> O formato flash FileX NOR deve ser um tamanho de bloco completo de sectores menos do que o flash NOR fornece. Isto ajudará a garantir um melhor desempenho durante o processamento do nível de desgaste. Técnicas adicionais para melhorar o desempenho da escrita no algoritmo de nivelamento de desgaste LevelX incluem:
> 1. Certifique-se de que todas as escritas são exatamente um ou mais clusters de tamanho e começar em limites exatos do cluster.
> 2. Pré-alocar clusters antes de realizar grandes operações de escrita de ficheiros através da classe ***de APIs fx_file_allocate*** FileX.
> 3.  O uso periódico de ***lx_nor_flash_defragment*** para libertar o maior número possível de blocos NOR e assim melhorar o desempenho da escrita.
> 4. Certifique-se de que o controlador FileX está habilitado a receber informações do sector de libertação e os pedidos feitos ao condutor para libertar os sectores são tratados no condutor, chamando ***lx_nor_flash_sector_release***.
