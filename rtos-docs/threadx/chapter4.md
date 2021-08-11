---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783412"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX

Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX por ordem alfabética. Os seus nomes são concebidos para que todos os serviços semelhantes sejam agrupados. Na secção "Valores de Retorno" nas seguintes descrições, os valores em **BOLD** não são afetados pela **TX_DISABLE_ERROR_CHECKING** definem utilizados para desativar a verificação de erros da API; enquanto os valores mostrados em nãobold são completamente desativados. Além disso, um "**Sim**" listado sob a rubrica "**Preemption Possible**" indica que ligar para o serviço pode retomar um fio de maior prioridade, antecipando assim o fio de chamada.

## <a name="tx_block_allocate"></a>tx_block_allocate

Alocar bloco de memória de tamanho fixo

### <a name="prototype"></a>Prototype

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço aloca um bloco de memória de tamanho fixo a partir do conjunto de memória especificado. O tamanho real do bloco de memória é determinado durante a criação do pool de memória.

> [!IMPORTANT]
> *É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído. Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes fatais!*

### <a name="parameters"></a>Parâmetros

- **pool_ptr** <br>Ponteiro para um conjunto de blocos de memória previamente criado.
- **block_ptr** <br>Ponteiro para um ponteiro de bloco de destino. Na atribuição bem sucedida, o endereço do bloco de memória atribuído é colocado onde este parâmetro aponta.
- **wait_option** <br>Define como o serviço se comporta se não houver blocos de memória disponíveis. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção **TX_NO_WAIT** resulta num retorno imediato deste serviço, independentemente de ter sido bem sucedida ou não. *Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que um bloco de memória esteja disponível.
  - *Valor de tempo limite* (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por um bloco de memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS**    (0x00) Alocação de blocos de memória bem sucedidos.
- **TX_DELETED**    (0x01) O conjunto de blocos de memória foi apagado enquanto o fio foi suspenso.
- **TX_NO_MEMORY**  (0x10) O Serviço não foi capaz de alocar um bloco de memória dentro do tempo especificado para esperar.
- **TX_WAIT_ABORTED**   (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.
- **TX_PTR_ERROR**  (0x03) Ponteiro inválido para ponteiro de destino.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a>Consulte também

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

Criar piscina de blocos de memória de tamanho fixo

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>Description

Este serviço cria uma piscina de blocos de memória de tamanho fixo. A área de memória especificada é dividida em tantos blocos de memória de tamanho fixo quanto possível utilizando a fórmula:

**blocos totais** =**(bytes totais)**/**(tamanho do bloco** + tamanho (vazio *))

> [!NOTE]
>*Cada bloco de memória contém um ponteiro de sobrecarga que é invisível para o utilizador e é representado pelo "tamanho(vazio) *na fórmula anterior.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr**  Ponteiro para um bloco de controlo de piscina de bloco de memória.
- **name_ptr**  Ponteiro para o nome do bloco de memória.
- **block_size**    Número de bytes em cada bloco de memória.
- **pool_start**    Endereço inicial do bloco de memória. O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.
- **pool_size** Número total de bytes disponíveis para o conjunto de blocos de memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS**    (0x00) Criação de piscina de blocos de memória bem-sucedido.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido. Ou o ponteiro é NULO ou a piscina já está criada.
- **TX_PTR_ERROR**  (0x03) Endereço inicial inválido da piscina.
- **TX_CALLER_ERROR**   (0x13) Inválido deste serviço.
- **TX_SIZE_ERROR** (0x05) O tamanho da piscina é inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate, tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Apagar o conjunto de blocos de memória

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o conjunto de memória de bloco especificado. Todos os fios suspensos à espera de um bloco de memória desta piscina são retomados e dado um **estado de retorno TX_DELETED.**

> [!NOTE]
> *É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de uma piscina eliminada ou dos seus antigos blocos de memória.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para um conjunto de blocos de memória previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação bem sucedida do bloco de memória.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Recuperar informações sobre a piscina de blocos

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a>Description

Este serviço obtém informações sobre o conjunto de memórias de bloco especificado.

### <a name="parameters"></a>Parâmetros

- **pool_ptr**  Ponteiro para o bloco de memória previamente criado.
- **nome**  Ponteiro para o destino para o ponteiro para o nome da piscina do bloco.
- **disponível** Ponteiro para o destino para o número de blocos disponíveis na piscina de blocos.
- **total_blocks**  Ponteiro para o destino para o número total de blocos na piscina de blocos.
- **first_suspended**   Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste bloco pool.
- **suspended_count**   Ponteiro para o destino para o número de fios atualmente suspensos neste bloco pool.
- **next_pool** Ponteiro para o destino para o ponteiro do próximo conjunto de blocos criado.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperar informações de piscina de blocos bem sucedidos.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Obtenha informações de desempenho da piscina de blocos

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre o conjunto de blocos de memória especificados.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr**  Ponteiro para o bloco de memória previamente criado.
- **atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.
- **liberta**  Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.
- **suspensões**   Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.
- **intervalos**  Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.

>[!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS**    (0x00) Desempenho bem sucedido da piscina de blocos obter.
- **TX_PTR_ERROR**  (0x03) Ponteiro de piscina de bloco inválido.
- **TX_FEATURE_NOT_ENABLED**    (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

Obtenha informações de desempenho do sistema de piscina de blocos

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os conjuntos de blocos de memória na aplicação.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **atribui** Ponteiro para destino para o número total de pedidos de atribuição realizados em todas as piscinas de blocos.
- **liberta**  Ponteiro para destino para o número total de pedidos de libertação realizados em todas as piscinas de blocos.
- **suspensões**   Ponteiro para o destino para o número total de suspensões de atribuição de fios em todas as piscinas de blocos.
- **intervalos**  Ponteiro para o destino para o número total de intervalos de suspensão atribuídos em todas as piscinas de blocos.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do sistema de piscina de blocos bem sucedido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

Priorizar lista de suspensão de piscina de bloco

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Description

Este serviço coloca o fio de prioridade mais elevado suspenso por um bloco de memória nesta piscina na parte da frente da lista de suspensão. Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para um bloco de controlo de piscina de bloco de memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Prioridades de piscina de blocos bem sucedidos.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

Liberte o bloco de memória de tamanho fixo

### <a name="prototype"></a>Prototype

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>Description

Este serviço liberta um bloco previamente atribuído de volta ao seu pool de memória associado. Se houver um ou mais fios suspensos à espera de blocos de memória desta piscina, o primeiro fio suspenso é dado a este bloco de memória e retomado.

>[!IMPORTANT]
>*A aplicação deve evitar a utilização de uma área de bloco de memória depois de ter sido libertada de volta à piscina.*

### <a name="parameters"></a>Parâmetros

- **block_ptr** Ponteiro para o bloco de memória previamente atribuído.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desbloqueio do bloco de memória bem sucedido.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para o bloco de memória.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>Consulte também

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

Alocar bytes de memória

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço atribui o número especificado de bytes da piscina de bytes de memória especificada.

> [!IMPORTANT]
> *É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído. Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes fatais!*

> [!NOTE]
> *O desempenho deste serviço é uma função do tamanho do bloco e da quantidade de fragmentação na piscina. Por conseguinte, este serviço não deve ser utilizado durante os fios críticos de execução.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr** <br>Ponteiro para um conjunto de blocos de memória previamente criado.
- **memory_ptr** <br>Ponteiro para um ponteiro de memória de destino. Na atribuição bem sucedida, o endereço da área de memória atribuída é colocado onde este parâmetro aponta.
- **memory_size** <br>Número de bytes solicitados.
- **wait_option** <br>Define como o serviço se comporta se não houver memória suficiente disponível. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção **TX_NO_WAIT** resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedida. *Esta é a única opção válida se o serviço for chamado de inicialização.*
  - **TX_WAIT_FOREVER** 0xFFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que esteja disponível memória suficiente.
  - *Valor de tempo limite* (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pela memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Alocação de memória bem sucedida.
- **TX_DELETED** (0x01) O pool de memória foi apagado enquanto o fio foi suspenso.
- **TX_NO_MEMORY** serviço (0x10) não foi capaz de alocar a memória dentro do tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para ponteiro de destino.
- **TX_SIZE_ERROR** (0X05) O tamanho solicitado é zero ou maior do que a piscina.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

Criar piscina de memória de bytes

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>Description

Este serviço cria uma piscina de byte de memória na área especificada. Inicialmente, a piscina é composta por basicamente um bloco livre muito grande. No entanto, a piscina é dividida em blocos menores à medida que as dotações são feitas.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para um bloco de controlo de piscina de memória.
- **name_ptr** Ponteiro para o nome do pool de memória.
- **pool_start** Endereço inicial do pool de memórias. O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.
- **pool_size** Número total de bytes disponíveis para o pool de memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de piscina de memória bem sucedida.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida. Ou o ponteiro é NULO ou a piscina já está criada.
- **TX_PTR_ERROR** (0x03) Endereço inicial inválido da piscina.
- **TX_SIZE_ERROR** (0x05) O tamanho da piscina é inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

Apagar piscina de byte de memória

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o conjunto de bytes de memória especificado. Todos os fios suspensos à espera de memória desta piscina são retomados e dado um **estado de retorno TX_DELETED.**

> [!IMPORTANT]
> *É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de um pool ou memória eliminados previamente atribuídos a partir do mesmo.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para um pool de memória previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação bem sucedida do pool de memória.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

Recuperar informações sobre a piscina byte

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a>Description

Este serviço obtém informações sobre o byte de memória especificado.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para piscina de memória previamente criada.
- **nome** Ponteiro para o destino para o ponteiro para o nome da piscina byte.
- **disponível** Ponteiro para o destino para o número de bytes disponíveis na piscina.
- **fragmentos** Ponteiro para o destino para o número total de fragmentos de memória na piscina byte.
- **first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão desta piscina byte.
- **suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos nesta piscina byte.
- **next_pool** Ponteiro para o destino para o ponteiro do próximo byte criado pool.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperar informações de piscina bem sucedidas.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

Obter informações sobre desempenho da piscina byte

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre a piscina de byte de memória especificada.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para a piscina byte de memória previamente criada.
- **atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.
- **liberta** Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.
- **fragments_searched** Ponteiro para o destino para o número de fragmentos de memória interna pesquisados durante os pedidos de atribuição nesta piscina.
- **funde** Ponteiro para destino para o número de blocos de memória internos fundidos durante os pedidos de atribuição nesta piscina.
- **divisões** Ponteiro para o destino para o número de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição nesta piscina.
- **suspensões** Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.
- **intervalos** Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho de byte de piscina bem sucedido.
- **TX_PTR_ERROR** (0x03) Ponteiro de piscina inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

Obtenha informações sobre o desempenho do sistema de piscinas byte

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todas as piscinas de byte de memória no sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.
- **liberta** Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.
- **fragments_searched** Ponteiro para o destino para o número total de fragmentos de memória interna pesquisados durante os pedidos de atribuição em todas as piscinas byte.
- **funde** Ponteiro para destino para o número total de blocos de memória internos fundidos durante os pedidos de atribuição em todas as piscinas byte.
- **divisões** Ponteiro para destino para o número total de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição em todas as piscinas byte.
- **suspensões** Ponteiro para destino para o número total de suspensões de atribuição de fios em todas as piscinas byte.
- **intervalos** Ponteiro para o destino para o número total de intervalos de suspensão alocados em todas as piscinas byte.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho de byte de piscina bem sucedido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

 Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

Lista de suspensão de piscina de byte priorize

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Description

Este serviço coloca o fio de prioridade mais elevado suspenso para memória nesta piscina na parte da frente da lista de suspensão. Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.

### <a name="parameters"></a>Parâmetros

- **pool_ptr** Ponteiro para um bloco de controlo de piscina de memória.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Prioridades de memória bem sucedidas.
- **TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

Liberte bytes de volta à piscina de memória

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>Description

Este serviço liberta uma área de memória previamente atribuída à sua piscina associada. Se houver um ou mais fios suspensos à espera da memória desta piscina, cada fio suspenso é dado memória e retomado até que a memória esteja esgotada ou até que não haja mais fios suspensos. Este processo de atribuição de memória a fios suspensos começa sempre com o primeiro fio suspenso.

> [!IMPORTANT]
> *A aplicação deve evitar a utilização da área de memória após a sua libertação.*

### <a name="parameters"></a>Parâmetros

- **memory_ptr** Ponteiro para a área de memória previamente atribuída.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Libertação de memória bem sucedida.
- **TX_PTR_ERROR** (0x03) Ponteiro da área da memória inválida.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>Consulte também

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

Criar grupo de bandeiras de eventos

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>Description

Este serviço cria um grupo de 32 bandeiras de eventos. Todas as 32 bandeiras do grupo estão inicializadas a zero. Cada bandeira do evento é representada por um único pedaço.

### <a name="parameters"></a>Parâmetros

- **group_ptr** Ponteiro para um bloco de controlo de grupo de bandeiras de evento.
- **name_ptr** Apontando para o nome do grupo de bandeiras do evento.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de grupo de eventos bem sucedidos.
- **TX_GROUP_ERROR** (0x06) Ponteiro do grupo de eventos inválidos. Ou o ponteiro é **NU** OU o grupo de eventos já está criado.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

Apagar grupo de bandeiras de eventos

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o grupo de bandeiras de eventos especificado. Todos os fios suspensos à espera de eventos deste grupo são retomados e dado um TX_DELETED estatuto de devolução.

>[!IMPORTANT]
> *O pedido deve garantir que um conjunto de chamadas notificantes para este grupo de bandeiras de evento seja concluído (ou desativado) antes de eliminar o grupo de bandeiras do evento. Além disso, a aplicação deve impedir a utilização futura de um grupo de bandeiras de eventos eliminado.*

### <a name="parameters"></a>Parâmetros

- **group_ptr** Ponteiro para um grupo de bandeiras de eventos previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) A eliminação de bandeiras de eventos bem-sucedidos.
- **TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

Receba bandeiras de evento do grupo de bandeiras de eventos

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço recupera bandeiras de eventos do grupo de bandeiras de eventos especificado. Cada grupo de bandeiras de evento contém 32 bandeiras de eventos. Cada bandeira é representada por um único pedaço. Este serviço pode recuperar uma variedade de combinações de bandeira de evento, como selecionado pelos parâmetros de entrada.

### <a name="parameters"></a>Parâmetros

- **group_ptr** <br>Ponteiro para um grupo de bandeiras de eventos previamente criado.
- **requested_flags** <br>Variável não assinada de 32 bits que representa as bandeiras de eventos solicitadas.
- **get_option** <br>Especifica se são necessárias todas ou quaisquer das bandeiras de eventos solicitadas. Seguem-se as seguintes seleções válidas:

  - **TX_AND** (0x02)
  - **TX_AND_CLEAR** (0x03)
  - **TX_OR** (0x00)
  - **TX_OR_CLEAR** (0x01)

    A seleção de TX_AND ou TX_AND_CLEAR especifica que todas as bandeiras do evento devem estar presentes no grupo. Selecionar TX_OR ou TX_OR_CLEAR especifica que qualquer bandeira de evento é satisfatória. As bandeiras do evento que satisfaçam o pedido são apuradas (definidas para zero) se forem especificadas TX_AND_CLEAR ou TX_OR_CLEAR.

- **actual_flags_ptr** <br>Ponteiro para o destino de onde são colocadas as bandeiras do evento recuperado. Note-se que as bandeiras obtidas podem conter bandeiras que não foram solicitadas.
- **wait_option**  <br>Define como o serviço se comporta se as bandeiras de eventos selecionadas não estiverem definidas. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.
  - **TX_WAIT_FOREVER** valor de tempo limite (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que as bandeiras do evento estejam disponíveis.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera pelas bandeiras do evento.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Bandeiras de eventos bem-sucedidas recebem.
- **TX_DELETED** (0x01) Grupo de bandeiras de evento foi apagado enquanto o fio foi suspenso.
- **TX_NO_EVENTS** (0x07) O Serviço não conseguiu obter os eventos especificados dentro do tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para bandeiras reais do evento.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.
- **TX_OPTION_ERROR** (0x08) Foi especificada a opção de opção de opção inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

**Ver Também**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Recuperar informações sobre o grupo de bandeiras de eventos

**Protótipo**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**Descrição**

Este serviço obtém informações sobre o grupo de bandeiras de eventos especificado.

**Parâmetros**

- **group_ptr** Ponteiro para um bloco de controlo de grupo de bandeiras de evento.
- **nome** Ponteiro para o destino para o ponteiro para o nome do grupo bandeiras do evento.
- **current_flags** Ponteiro para destino para as bandeiras do conjunto atual no grupo de bandeiras do evento.
- **first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste grupo de bandeiras de evento.
- **suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste grupo de bandeiras de evento.
- **next_group** Ponteiro para o destino para o ponteiro do próximo grupo de bandeiras de eventos criado.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação de informação de grupo de eventos bem-sucedidos.
- **TX_GROUP_ERROR** (0x06) Ponteiro do grupo de eventos inválidos.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
**Ver Também**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

Obtenha informações de desempenho do grupo de bandeiras de eventos

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre o grupo de bandeiras de eventos especificado.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **group_ptr** Ponteiro para grupo de bandeiras de eventos previamente criado.
- **conjuntos** Ponteiro para destino para o número de bandeiras de eventos definir pedidos realizados neste grupo.
- **recebe** O ponteiro para o destino para o número de bandeiras de eventos recebe pedidos realizados neste grupo.
- **suspensões** O ponteiro para o destino para o número de bandeiras de eventos de thread obter suspensões neste grupo.
- **intervalos** O ponteiro para o destino para o número de bandeiras do evento obtém intervalos de suspensão neste grupo.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) O desempenho do grupo de bandeiras de eventos bem-sucedidos obtém.
- **TX_PTR_ERROR** (0x03) Inválido sinaliza o ponteiro do grupo.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

Recuperar informações do sistema de desempenho

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os grupos de bandeiras de eventos no sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **conjuntos** Ponteiro para destino para o número total de bandeiras de eventos definir pedidos realizados em todos os grupos.
- **recebe** O ponteiro para o destino para o número total de bandeiras de eventos recebe pedidos realizados em todos os grupos.
- **suspensões** O ponteiro para o destino para o número total de bandeiras de eventos de thread obtém suspensões em todos os grupos.
- **intervalos** O ponteiro para o destino para o número total de bandeiras de eventos obtém intervalos de suspensão em todos os grupos.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do sistema de bandeiras de eventos bem sucedido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="example"></a>Exemplo

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

Definir bandeiras de evento em um grupo de bandeiras de evento

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>Description

Este serviço define ou limpa bandeiras de eventos num grupo de bandeiras de eventos, dependendo da opção definida especificada. Todos os fios suspensos cujo pedido de bandeiras de evento é agora preenchido são retomados.

### <a name="parameters"></a>Parâmetros

- **group_ptr** <br>Ponteiro para o bloco de controlo de grupo de bandeiras de eventos previamente criado.
- **flags_to_set** <br>Especifica as bandeiras do evento para definir ou limpar com base na opção definida selecionada.
- **set_option** <br>Especifica se as bandeiras do evento especificadas são ANDed ou ORed nas atuais bandeiras do grupo. Seguem-se as seguintes seleções válidas:
  - **TX_AND** (0x02)
  - **TX_OR** (0x00)

  A seleção TX_AND especifica que as bandeiras de eventos especificadas são **especadas** nas bandeiras do evento atual no grupo. Esta opção é frequentemente usada para limpar bandeiras de eventos em um grupo. Caso contrário, se TX_OR for especificado, as bandeiras de eventos especificadas são **ORed** com o evento atual no grupo.

### <a name="return-values"></a>Valores de devolução
- **TX_SUCCESS** (0x00) Conjunto de bandeiras de eventos bem-sucedidas.
- **TX_GROUP_ERROR** (0x06) Ponteiro inválido para grupo de bandeiras de eventos.
- **TX_OPTION_ERROR** (0x08) A opção de conjunto inválida especificada.

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

Notifique a aplicação quando as bandeiras do evento forem definidas

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>Description

Este serviço regista uma função de chamada de chamada de notificação que é chamada sempre que uma ou mais bandeiras de eventos são definidas no grupo de bandeiras de eventos especificado. O processamento da chamada de notificação é definido pela

### <a name="parameters"></a>Parâmetros
- **group_ptr** Ponteiro para grupo de bandeiras de eventos previamente criado.
- **events_set_notify** Ponteiro para as bandeiras de evento da aplicação definir função de notificação. Se este valor for TX_NULL, a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Registo bem sucedido de bandeiras de eventos definir notificação.
- **TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.

### <a name="example"></a>Exemplo

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a>Consulte também

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

Ativar e desativar interrupções

### <a name="prototype"></a>Prototype

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>Description

Este serviço permite ou desativa as interrupções conforme especificado pelo parâmetro de entrada *new_posture*.

> [!NOTE]
> *Se este serviço for chamado de um fio de aplicação, a postura de interrupção permanece parte do contexto desse fio. Por exemplo, se o fio chamar esta rotina para desativar as interrupções e, em seguida, suspender, quando é retomado, as interrupções são novamente desativadas.*

> [!WARNING]
> *Este serviço não deve ser utilizado para permitir interrupções durante a inicialização! Fazê-lo pode causar resultados imprevisíveis.*

### <a name="parameters"></a>Parâmetros

- **new_posture** Este parâmetro especifica se as interrupções são desativadas ou ativadas. Os valores legais incluem **TX_INT_DISABLE** e **TX_INT_ENABLE.** Os valores reais para estes parâmetros são específicos do porto. Além disso, algumas arquiteturas de processamento podem suportar posturas adicionais de interrupção de desativação.

### <a name="return-values"></a>Valores de devolução
- **postura anterior** Este serviço devolve a postura de interrupção anterior ao chamador. Isto permite que os utilizadores do serviço restaurem a postura anterior após as interrupções serem desativadas.

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>Consulte também

Nenhuma

## <a name="tx_mutex_create"></a>tx_mutex_create

Criar mutex de exclusão mútua

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>Description

Este serviço cria um mutex para exclusão mútua inter-roscada para proteção de recursos.

### <a name="parameters"></a>Parâmetros

- **mutex_ptr** Ponteiro para um bloco de controlo de mutantes.
- **name_ptr** Apontando para o nome do mutex.
- **priority_inherit** Especifica se este mutex suporta ou não a herança prioritária. Se este valor for TX_INHERIT, então a herança prioritária é apoiada. No entanto, se TX_NO_INHERIT for especificada, a herança prioritária não é apoiada por este mutex.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação mutex bem sucedida.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido. Ou o ponteiro é NULO ou o mutex já está criado.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.
- **TX_INHERIT_ERROR** (0x1F) Parâmetro de herdade de prioridade inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

Eliminar o mutex de exclusão mútua

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o mutex especificado. Todos os fios suspensos à espera do mutex são retomados e dado um **TX_DELETED** estado de retorno.

> [!NOTE]
> *É da responsabilidade da aplicação impedir a utilização de um mutex apagado.*

### <a name="parameters"></a>Parâmetros

- **mutex_ptr** Ponteiro para um mutex criado anteriormente.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação mutex bem sucedida.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

Obter a propriedade do mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço tenta obter a propriedade exclusiva do mutex especificado. Se o fio de chamamento já possuir o mutex, um contador interno é incrementado e um estado de sucesso é devolvido.

Se o mutex for propriedade de outro fio e este fio for de maior prioridade e a herança prioritária foi especificada na criação de mutex, a prioridade do fio de menor prioridade será temporariamente elevada à do fio de chamada.

> [!NOTE]
> *A prioridade do fio de menor prioridade que possui um mutex com prioridade nunca deve ser modificada por um fio externo durante a propriedade do mutex.*

### <a name="parameters"></a>Parâmetros

- **mutex_ptr**   <br>Ponteiro para um mutex criado anteriormente.
- **wait_option** <br>Define como o serviço se comporta se o mutex já é propriedade de outro fio. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. *Esta é a única opção válida se o serviço for chamado da Initialization.*
  - **TX_WAIT_FOREVER** valor de tempo limite (0xFFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que o mutex esteja disponível.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pelo mutex.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Mutex bem sucedido obter operação.
- **TX_DELETED** (0x01) Mutex foi eliminado enquanto o fio foi suspenso.
- **TX_NOT_AVAILABLE** (0x1D) O serviço não conseguiu obter a propriedade do mutex dentro do tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

Recuperar informações sobre o mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a>Description

Este serviço obtém informações do mutex especificado.

### <a name="parameters"></a>Parâmetros

- **mutex_ptr** Ponteiro para bloco de controlo de mutantes.
- **nome** Ponteiro para o destino para o ponteiro para o nome do mutex.
- **contar** Ponteiro para o destino para a contagem de propriedade do mutex.
- **proprietário** Ponteiro para destino para o ponteiro do fio próprio.
- **first_suspended** Ponteiro para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste mutex.
- **suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste mutex.
- **next_mutex** Ponteiro para o destino para o ponteiro do próximo mutex criado.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação de informação mutex bem sucedida.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

**Exemplo**

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

Obtenha informações sobre desempenho de mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

Este serviço recupera informações de desempenho sobre o mutex especificado.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **mutex_ptr** Ponteiro para o mutex criado anteriormente.
- **coloca** Ponteiro para o destino para o número de pedidos de colocação realizados neste mutex.
- **recebe** Ponteiro para o destino para o número de pedidos de obter realizados neste mutex.
- **suspensões** Ponteiro para o destino para o número de mutex thread obter suspensões neste mutex.
- **intervalos** Ponteiro para o destino para o número de mutaxos obter intervalos de suspensão neste mutex.
- **inversões** Ponteiro para o destino para o número de inversões prioritárias de linha neste mutex.
- **heranças** Ponteiro para o destino para o número de operações de herança prioritária de linha neste mutex.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho mutex bem sucedido obtém.
- **TX_PTR_ERROR** (0x03) Ponteiro mutex inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

Obtenha informações sobre desempenho do sistema mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os mutaxos do sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **coloca** Ponteiro para destino para o número total de pedidos de colocação realizados em todos os mutaxos.
- **recebe** Ponteiro para destino para o número total de pedidos de obter realizados em todos os mutaxos.
- **suspensões** Ponteiro para o destino para o número total de fios mutex obter suspensões em todos os mutais.
- **intervalos** Ponteiro para o destino para o número total de mutantes obter intervalos de suspensão em todos os mutais.
- **inversões** Ponteiro para o destino para o número total de inversões prioritárias de linha em todos os mutaxos.
- **heranças** Ponteiro para destino para o número total de operações de herança prioritária de fio em todos os mutaxos.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do sistema mutex bem sucedido obtém.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

Priorizar lista de suspensão de mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Este serviço coloca o fio de prioridade mais elevado suspenso para a propriedade do mutex na parte da frente da lista de suspensão. Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.

### <a name="parameters"></a>Parâmetros

- **mutex_ptr** Ponteiro para o mutex anteriormente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Prioridades de mutex bem sucedidos.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

Libertar a propriedade do mutex

### <a name="prototype"></a>Prototype

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Description

Este serviço desvaloriza a contagem de propriedade do mutex especificado. Se a contagem de propriedade for zero, o mutex é disponibilizado.

> [!NOTE]
> *Se a herança prioritária foi selecionada durante a criação de mutaxos, a prioridade do fio de libertação será restaurada à prioridade que tinha quando obteve inicialmente a propriedade do mutex. Quaisquer outras alterações prioritárias efetuadas no fio de libertação durante a propriedade do mutex podem ser desfeitas.*

### <a name="parameters"></a>Parâmetros
- mutex_ptr Pointer para o mutex anteriormente criado.

### <a name="return-values"></a>Valores de devolução
- **TX_SUCCESS** (0x00) Libertação de mutex bem sucedido.
- **TX_NOT_OWNED** (0x1E) A Mutex não é propriedade do chamador.
- **TX_MUTEX_ERROR** (0x1C) Ponteiro inválido para mutex.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>Consulte também

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

Criar fila de mensagens

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>Description

Este serviço cria uma fila de mensagens que é normalmente usada para comunicação interligada. O número total de mensagens é calculado a partir do tamanho da mensagem especificada e do número total de bytes na fila.

> [!NOTE]
> *Se o número total de bytes especificados na área de memória da fila não for igualmente divisível pelo tamanho da mensagem especificada, os bytes restantes na área da memória não são utilizados.*

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para um bloco de controlo de fila de mensagens.
- **name_ptr** Ponteiro para o nome da fila da mensagem.
- **message_size** Especifica o tamanho de cada mensagem na fila. Os tamanhos da mensagem variam de 1 32 bits de palavras a 16 palavras de 32 bits. As opções de tamanho de mensagem válidas são valores numéricos de 1 a 16, inclusive.
- **queue_start** Endereço inicial da fila da mensagem. O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.
- **queue_size** Número total de bytes disponíveis para a fila da mensagem.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de fila de mensagens bem sucedida.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas. Ou o ponteiro é NU OU a fila já está criada.
- **TX_PTR_ERROR** (0x03) Endereço inicial inválido da fila da mensagem.
- **TX_SIZE_ERROR** (0x05) O tamanho da fila da mensagem é inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a>Consulte também

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

Apagar fila de mensagens

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Este serviço elimina a fila de mensagens especificada. Todos os fios suspensos à espera de uma mensagem desta fila são retomados e dado um estado de devolução TX_DELETED.

>[!IMPORTANT]
> *O pedido deve certificar-se de que qualquer pedido de notificação para esta fila está concluído (ou desativado) antes de apagar a fila. Além disso, a aplicação deve impedir qualquer utilização futura de uma fila eliminada.* <br><br>*É também da responsabilidade da aplicação gerir a área de memória associada à fila, que está disponível após a conclusão deste serviço.*

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para uma fila de mensagens previamente criada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação da fila de mensagens bem sucedida.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

Mensagens vazias na fila da mensagem

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Este serviço elimina todas as mensagens armazenadas na fila de mensagens especificada.

Se a fila estiver cheia, as mensagens de todos os fios suspensos são descartadas. Cada fio suspenso é então retomado com um estado de retorno que indica que o envio da mensagem foi bem sucedido. Se a fila estiver vazia, este serviço não faz nada.

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para uma fila de mensagens previamente criada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Mensagem de sucesso na fila da fila.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

Enviar mensagem para a frente da fila

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia uma mensagem para a localização frontal da fila de mensagens especificada. A mensagem é **copiada** para a frente da fila a partir da área de memória especificada pelo ponteiro de origem.

### <a name="parameters"></a>Parâmetros

- **queue_ptr** <br>Ponteiro para um bloco de controlo de fila de mensagens.
- **source_ptr** <br>Ponteiro para a mensagem.
- **wait_option**  <br>Define como o serviço se comporta se a fila da mensagem estiver cheia. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. *Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por espaço na fila.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Envio bem sucedido de mensagem.
- **TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.
- **TX_QUEUE_FULL** (0x0B) O Serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.
- **TX_PTR_ERROR** (0x03) Ponteiro de origem inválido para mensagem.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

Recuperar informações sobre a fila

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a>Description

Este serviço obtém informações sobre a fila de mensagens especificadas.

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para uma fila de mensagens previamente criada.
- **nome** Ponteiro para o destino para o ponteiro para o nome da fila.
- **enqueso** Ponteiro para o destino para o número de mensagens atualmente na fila.
- **available_storage** Ponteiro para destino para o número de mensagens para as recados atualmente tem espaço para.
- **first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão desta fila.
- **suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos nesta fila.
- **next_queue** Ponteiro para o destino para o ponteiro da próxima fila criada.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Informações de fila bem sucedidas obtêm.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

Obtenha informações sobre desempenho da fila

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço recupera informações de desempenho sobre a fila especificada.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para a fila previamente criada.
- **messages_sent** Ponteiro para destino para o número de pedidos de envio realizados nesta fila.
- **messages_received** Ponteiro para destino para o número de pedidos de receção realizados nesta fila.
- **empty_suspensions** Ponteiro para o destino para o número de suspensões vazias de fila nesta fila.
- **full_suspensions** Ponteiro para o destino para o número de suspensões completas da fila nesta fila.
- **full_errors** Ponteiro para o destino para o número de erros completos da fila nesta fila.
- **intervalos** Ponteiro para o destino para o número de intervalos de suspensão de fio nesta fila.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho de fila bem sucedido obtém.
- **TX_PTR_ERROR** (0x03) Ponteiro de fila inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

Obtenha informações sobre desempenho do sistema de fila

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todas as filas do sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros

- **messages_sent** Ponteiro para destino para o número total de pedidos de envio realizados em todas as filas.
- **messages_received** Ponteiro para destino para o número total de pedidos de receção realizados em todas as filas.
- **empty_suspensions** Ponteiro para o destino para o número total de suspensões vazias de fila em todas as filas.
- **full_suspensions** Ponteiro para o destino para o número total de suspensões completas da fila em todas as filas.
- **full_errors** Ponteiro para o destino para o número total de erros completos da fila em todas as filas.
- **intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio em todas as filas.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

**Valores de devolução**

- **TX_SUCCESS** (0x00) Desempenho do sistema de fila bem sucedido obtém.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

Priorizar lista de suspensão de filas

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Description

Este serviço coloca o fio de prioridade mais elevado suspenso para uma mensagem (ou para colocar uma mensagem) nesta fila na parte da frente da lista de suspensão.

Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para uma fila de mensagens previamente criada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Prioridades de fila bem sucedida.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

Receba mensagem da fila da mensagem

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço recupera uma mensagem da fila de mensagens especificada. A mensagem recuperada é **copiada** da fila para a área de memória especificada pelo ponteiro de destino. Essa mensagem é então removida da fila.

> [!IMPORTANT]
> *A área de memória de destino especificada deve ser suficientemente grande para conter a mensagem; ou seja, o destino da mensagem apontado por*  * **destination_ptr** _ _must ser pelo menos tão grande quanto o tamanho da mensagem para esta fila. Caso contrário, se o destino não for suficientemente grande, a corrupção da memória ocorre na seguinte área de memória.*

### <a name="parameters"></a>Parâmetros

- **queue_ptr** <br>Ponteiro para uma fila de mensagens previamente criada.
- **destination_ptr** <br>Localização de onde copiar a mensagem.
- **wait_option** <br>Define como o serviço se comporta se a fila da mensagem estiver vazia. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção de TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que uma mensagem esteja disponível.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por uma mensagem.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação bem sucedida da mensagem.
- **TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.
- **TX_QUEUE_EMPTY** (0x0A) O Serviço não conseguiu recuperar uma mensagem porque a fila estava vazia durante o tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.
- **TX_PTR_ERROR** (0x03) Ponteiro de destino inválido para mensagem.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

Enviar mensagem para a fila de mensagens

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço envia uma mensagem para a fila de mensagens especificada. A mensagem enviada é **copiada** para a fila a partir da área de memória especificada pelo ponteiro de origem.

### <a name="parameters"></a>Parâmetros
- **queue_ptr** <br>Ponteiro para uma fila de mensagens previamente criada.
- **source_ptr** <br>Ponteiro para a mensagem.
- **wait_option** <br>Define como o serviço se comporta se a fila da mensagem estiver cheia. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. *Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por espaço na fila.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Envio bem sucedido de mensagem.
- **TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.
- **TX_QUEUE_FULL** (0x0B) O Serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.
- **TX_PTR_ERROR** (0x03) Ponteiro de origem inválido para mensagem.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

**Ver Também**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

Notifique o pedido quando a mensagem é enviada para a fila

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>Description

Este serviço regista uma função de chamada de notificação que é chamada sempre que uma mensagem é enviada para a fila especificada. O processamento da chamada de notificação é definido pela aplicação.

>[!NOTE]
> *A chamada de notificação de envio de fila da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.*

### <a name="parameters"></a>Parâmetros

- **queue_ptr** Ponteiro para a fila previamente criada.
- **queue_send_notify** Ponteiro para a função de notificação de envio de fila da aplicação. Se este valor for TX_NULL, a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Registo bem sucedido da notificação de envio de fila.
- **TX_QUEUE_ERROR** (0x09) Ponteiro de fila inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a>Consulte também

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

Coloque um caso na contagem de semáforos com teto

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>Description

Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um. Se o valor atual do semáforo de contagem for superior ou igual ao teto especificado, o caso não será colocado e será devolvido um erro de TX_CEILING_EXCEEDED.

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para semáforo criado anteriormente.
- **teto** Limite máximo permitido para o semáforo (valores válidos variam de 1 a 0xFFFFFFFF).

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS (0x00)** Teto de semáforo bem sucedido colocado.
- **TX_CEILING_EXCEEDED** (0x21) O pedido de colocação excede o limite máximo.
- **TX_INVALID_CEILING** (0x22) Foi fornecido um valor inválido de zero para o teto.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

Criar semáforo de contagem

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>Description

Este serviço cria um semáforo de contagem para sincronização inter-thread. A contagem inicial de semáforos é especificada como um parâmetro de entrada.

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para um bloco de controlo de semáforos.
- **name_ptr** Apontando para o nome do semáforo.
- **initial_count** Especifica a contagem inicial para este semáforo. Os valores legais vão de 0x00000000 a 0xFFFFFFFF.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de semáforos bem sucedidos.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido. Ou o ponteiro é NU OU o semáforo já está criado.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

Eliminar semáforo de contagem

### <a name="prototype"></a>Prototype
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o semáforo de contagem especificado. Todos os fios suspensos à espera de uma instância de semáforo são retomados e dado um estado de retorno TX_DELETED.

> [!IMPORTANT]
> *O pedido deve assegurar-se de que uma chamada de notificação colocada para este semáforo seja concluída (ou desativada) antes de eliminar o semáforo. Além disso, o pedido deve impedir qualquer utilização futura de um semáforo eliminado.*

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para um semáforo previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação de semaphores de contagem bem sucedida.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**Ver Também**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

Obtenha o exemplo da contagem de semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Description

Este serviço recupera uma instância (uma contagem única) do semáforo de contagem especificado. Como resultado, a contagem de semáforos especificados é diminuída por um.

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** <br>Ponteiro para um semáforo de contagem previamente criado.
- **wait_option** <br>Define como o serviço se comporta se não houver casos do semáforo disponível; ou seja, a contagem de semáforos é zero. As opções de espera são definidas da seguinte forma:
  - **TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido. *Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, inicialização, temporizador ou ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção de TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que esteja disponível um caso de semáforo.
  - Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda por uma instância de semáforo.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação bem sucedida de um caso de semáforo.
- **TX_DELETED** (0x01) O semáforo de contagem foi apagado enquanto o fio foi suspenso.
- **TX_NO_INSTANCE** (0x0D) O serviço não conseguiu recuperar um caso do semáforo de contagem (a contagem de semáforos é zero dentro do tempo especificado para esperar).
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.
- **TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

Recuperar informações sobre semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>Description

Este serviço obtém informações sobre o semáforo especificado.

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para o bloco de controlo de semáforos.
- **nome** Ponteiro para o destino para o ponteiro para o nome do semáforo.
- **current_value** Ponteiro para o destino para a contagem atual do semáforo.
- **first_suspended** Ponteiro para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste semáforo.
- **suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste semáforo.
- **next_semaphore** Ponteiro para o destino para o ponteiro do próximo semáforo criado.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) recuperação de informações.

- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

Obtenha informações de desempenho de semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço recupera informações de desempenho sobre o semáforo especificado.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.*

**Parâmetros**

-  **semaphore_ptr** Ponteiro para semáforo criado anteriormente.
-  **coloca** Ponteiro para destino para o número de pedidos de colocação realizados neste semáforo.
-  **recebe** Ponteiro para destino para o número de pedidos de obter realizados neste semáforo.
-  **suspensões** Ponteiro para o destino para o número de suspensões de fio neste semáforo.
-  **intervalos** Ponteiro para o destino para o número de intervalos de suspensão de fio neste semáforo.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do semáforo bem sucedido obtém.
- **TX_PTR_ERROR** (0x03) Ponteiro semáforo inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

Obtenha informações sobre desempenho do sistema de semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os semáforos do sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações sobre o desempenho*

### <a name="parameters"></a>Parâmetros

- **coloca** Ponteiro para destino para o número total de pedidos de colocação realizados em todos os semáforos.
- **recebe** Ponteiro para destino para o número total de pedidos de obter realizados em todos os semáforos.
- **suspensões** Ponteiro para o destino para o número total de suspensões de fio em todos os semáforos.
- **intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio em todos os semáforos.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) desempenho do sistema obtém.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

Priorizar lista de suspensão de semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Este serviço coloca o fio de prioridade mais elevado suspenso por uma instância do semáforo na parte da frente da lista de suspensão. Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para um semáforo previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Prioridades de semáforos bem sucedidos.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

Coloque um caso na contagem de semáforos

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Description

Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um.

> [!NOTE]
> *Se este serviço for chamado quando o semáforo for todos (OxFFFFFFFF), a nova operação de colocação fará com que o semáforo seja reposto a zero.*

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para o bloco de controlo de semáforos previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Semaphore bem sucedido colocado.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro inválido para contar semáforo.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

Notificar o pedido quando o semáforo for colocado

### <a name="prototype"></a>Prototype

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>Description

Este serviço regista uma função de chamada de notificação que é chamada sempre que o semáforo especificado é colocado. O processamento da chamada de notificação é definido pela aplicação.

> [!NOTE]
> *A chamada de notificação de semáforo da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.*

### <a name="parameters"></a>Parâmetros

- **semaphore_ptr** Ponteiro para semáforo criado anteriormente.
- **semaphore_put_notify** Ponteiro para o semáforo da aplicação colocar função de notificação. Se este valor for TX_NULL, a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Registo bem sucedido da notificação de semáforos.
- **TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a>Consulte também

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

Criar linha de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a>Description

Este serviço cria um fio de aplicação que inicia a execução na função de entrada de tarefa especificada. A pilha, prioridade, limiar de pré-escamação e corte de tempo estão entre os atributos especificados pelos parâmetros de entrada. Além disso, o estado de execução inicial do fio também é especificado.

**Parâmetros**

- **thread_ptr** Ponteiro para um bloco de controlo de rosca.
- **name_ptr** Ponteiro para o nome do fio.
- **entry_function** Especifica a função C inicial para a execução do fio. Quando um fio regressa desta função de entrada, é colocado num estado *completo* e suspenso indefinidamente.
- **entry_input** Um valor de 32 bits que é passado para a função de entrada do fio quando executa pela primeira vez. A utilização para esta entrada é determinada exclusivamente pela aplicação.
- **stack_start** Endereço inicial da área de memória da pilha.
- **stack_size** Bytes de números na área de memória da pilha. A área da pilha do fio deve ser grande o suficiente para lidar com a sua pior função de nidificação de chamadas e uso variável local.
- **prioridade** Prioridade numérica do fio. Os valores legais variam entre 0 e TX_MAX_PRIORITES-1, onde o valor de 0 representa a maior prioridade.
- **preempt_threshold** Nível de prioridade mais elevado (0 a TX_MAX_PRIORITIES-1)) de pré-incapacidade. Apenas prioridades superiores a este nível são permitidas para antecipar este fio. Este valor deve ser inferior ou igual à prioridade especificada. Um valor igual à prioridade do fio desativa o limiar de pré-substituição.
- **time_slice** O número de carraças-temporizador deste fio é permitido funcionar antes que outros fios prontos da mesma prioridade sejam autorizados a correr. Note que a utilização do limiar de pré-substituição desativa o corte de tempo. Os valores legais de corte de tempo variam de 1 a 0xFFFFFFFF (inclusive). Um valor de **TX_NO_TIME_SLICE** (um valor de 0) desativa o corte de tempo deste fio.

  > [!NOTE]
  > *A utilização de corte de tempo resulta numa ligeira quantidade de sobrecarga do sistema.   Uma vez que o corte de tempo só é útil nos casos em que múltiplos fios partilham a mesma prioridade, os fios que têm uma prioridade única não devem ser atribuídos a uma fatia de tempo.*

- **auto_start** Especifica se o fio começa imediatamente ou se é colocado num estado suspenso. As opções legais são **TX_AUTO_START** (0x01) e **TX_DONT_START** (0x00). Se TX_DONT_START for especificado, o pedido deve ligar mais tarde tx_thread_resume para que o fio seja executado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de fio bem sucedido.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de controlo de rosca inválido. Ou o ponteiro é NULO ou o fio já está criado.
- **TX_PTR_ERROR** (0x03) Endereço inicial inválido do ponto de entrada ou da área da pilha é inválido, normalmente NULO.
- **TX_SIZE_ERROR** (0x05) O tamanho da área da pilha é inválido. Os fios devem ter pelo menos **TX_MINIMUM_STACK** bytes para executar.
- **TX_PRIORITY_ERROR** (0x0F) Prioridade do fio inválido, que é um valor fora do intervalo de (0 a TX_MAX_PRIORITIES-1)).
- **TX_THRESH_ERROR** (0x18) Retenção de preempção inválida especificada. Este valor deve ser uma prioridade válida inferior ou igual à prioridade inicial do fio.
- **TX_START_ERROR** (0x10) Seleção de arranque automático inválida.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a>Consulte também

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

Eliminar o fio da aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o fio de aplicação especificado. Uma vez que o fio especificado deve estar num estado encerrado ou concluído, este serviço não pode ser chamado de um fio que tenta apagar-se.

> [!NOTE]
> *É da responsabilidade da aplicação gerir a área de memória associada à pilha do fio, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de um fio eliminado.*

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio de aplicação previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação de rosca bem sucedida.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_DELETE_ERROR** (0x11) O fio especificado não se encontra num estado encerrado ou concluído.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

Notificar o pedido após a entrada e saída do fio

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>Description

Este serviço regista uma função de chamada de notificação que é chamada sempre que o fio especificado é introduzido ou sai. O processamento da chamada de notificação é definido pela aplicação.

> [!NOTE]
> A chamada de notificação de entrada/saída da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para fio previamente criado.
- **entry_exit_notify** Ponteiro para a função de notificação de entrada/saída da aplicação. O segundo parâmetro da função de notificação de entrada/saída designa se estiver presente uma entrada ou saída. O valor **TX_THREAD_ENTRY** (0x00) indica que o fio foi introduzido, enquanto o valor **TX_THREAD_EXIT** (0x01) indica que o fio foi saído. Se este valor for **TX_NULL,** a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Registo bem sucedido da função de notificação de entrada/saída do fio.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

Recupera o ponteiro para a atual execução do fio

### <a name="prototype"></a>Prototype

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Description

Este serviço devolve um ponteiro ao fio atualmente executado. Se não houver fio, este serviço devolve um ponteiro nulo.

> [!NOTE]
> *Se este serviço for chamado de um ISR, o valor de retorno representa o fio em execução antes do manipulador de interrupção de execução.*

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="retuen-values"></a>Valores retuen

- **ponteiro de fio** Ponteiro para o fio de execução atual. Se não houver fio, o valor de retorno é **TX_NULL**.

### <a name="allowed-from"></a>Permitido a partir de

Fios e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

TX_THREAD *my_thread_ptr;

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

Recuperar informações sobre o fio

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a>Description

Este serviço recupera informações sobre o fio especificado.

### <a name="parameters"></a>Parâmetros
- **thread_ptr** Ponteiro para o bloco de controlo de roscar.
- **nome** Ponteiro para o destino para o ponteiro para o nome do fio.
- **estado** Ponteiro para o destino para o estado de execução atual do fio. Os valores possíveis são os seguintes.
    - **TX_READY** (0x00)
    - **TX_COMPLETED** (0x01)
    - **TX_TERMINATED** (0x02)
    - **TX_SUSPENDED** (0x03)
    - **TX_SLEEP** (0x04)
    - **TX_QUEUE_SUSP** (0x05)
    - **TX_SEMAPHORE_SUSP** (0x06)
    - **TX_EVENT_FLAG** (0x07)
    - **TX_BLOCK_MEMORY** (0x08)
    - **TX_BYTE_MEMORY** (0x09)
    - **TX_MUTEX_SUSP** (0x0D)  

- **run_count** Ponteiro para destino para a contagem de corridas do fio.
- **prioridade** Ponteiro para o destino para a prioridade do fio.
- **preemption_threshold** Ponteiro para destino para o limiar de pré-deempação do fio.
**time_slice** Ponteiro para o destino para a fatia de tempo do fio.
**next_thread** Ponteiro para destino para o próximo ponteiro de linha criado.

**suspended_thread** Ponteiro para destino para ponteiro para o próximo fio na lista de suspensão.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação de informações de fio bem sucedidas.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de controlo de rosca inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

Obtenha informações sobre desempenho de thread

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a>Description

Este serviço recupera informações de desempenho sobre o fio especificado.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined para que este serviço devolva informações sobre o desempenho.*

### <a name="parameters"></a>Parâmetros
- **thread_ptr** Ponteiro para fio previamente criado.
- **retomas** Ponteiro para o destino para o número de recomeços deste fio.
- **suspensões** Ponteiro para o destino para o número de suspensões deste fio.
- **solicited_preemptions** Ponteiro para o destino para o número de preventivas como resultado de uma chamada de serviço API threadX feita por este fio.
- **interrupt_preemptions** Ponteiro para o destino para o número de preemposições deste fio como resultado do processamento de interrupção.
- **priority_inversions** Ponteiro para o destino para o número de inversões prioritárias deste fio.
- **time_slices** Ponteiro para o destino para o número de fatias de tempo deste fio.
- **renuncia** Ponteiro para destino para o número de renúncias de fio realizadas por este fio.
- **intervalos** Ponteiro para o destino para o número de intervalos de suspensão neste fio.
- **wait_aborts** Ponteiro para destino para o número de abortos de espera realizados neste fio.
- **last_preempted_by** Ponteiro para o destino para o ponteiro de linha que por último preemptou este fio.

> [!NOTE]
> *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do fio bem sucedido obtém.
- **TX_PTR_ERROR** (0x03) Ponteiro de rosca inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

Obtenha informações sobre desempenho do sistema de fios

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os fios do sistema.

*A biblioteca e aplicação ThreadX devem ser construídas com*

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined para que este serviço devolva informações sobre o desempenho.*

### <a name="parameters"></a>Parâmetros

- **retomas** Ponteiro para o destino para o número total de resmuções de roscas.
- **suspensões** Ponteiro para destino para o número total de suspensões de fios.
- **solicited_preemptions** Ponteiro para destino para o número total de preempções de linha como resultado de um fio chamando um serviço API ThreadX.
- **interrupt_preemptions** Ponteiro para o destino para o número total de preemposições de rosca como resultado do processamento de interrupção.
- **priority_inversions** Ponteiro para o destino para o número total de inversões prioritárias de linha.
- **time_slices** Ponteiro para o destino para o número total de fatias de tempo de fio.
- **renuncia** Ponteiro para destino para o número total de renúncias de fio.
- **intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio.
- **wait_aborts** Ponteiro para destino para o número total de thread wait aborta.
- **non_idle_returns** Ponteiro para o destino para o número de vezes que um fio retorna ao sistema quando outro fio está pronto para ser executado.
- **idle_returns** Ponteiro para destino para o número de vezes que um fio retorna ao sistema quando nenhum outro fio está pronto para ser executado (sistema inativo).

> [!NOTE]
> *O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do sistema de fio bem sucedido obtém.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

Alterar limiar de preempção do fio de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>Description

Este serviço altera o limiar de pré-substituição do fio especificado. O limiar de prevenção previne a preempção do fio especificado por roscas iguais ou inferiores ao valor do limiar de prevenção.

>[!NOTE]
> *A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.*

### <a name="parameters"></a>Parâmetros
- **thread_ptr** Ponteiro para um fio de aplicação previamente criado.
- **new_threshold** Novo nível de prioridade do limiar de pré-edição (0 a TX_MAX_PRIORITIES-1)).
- **old_threshold** Ponteiro para um local para devolver o limiar de pré-substituição anterior.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Alteração do limiar de pré-edição bem-sucedido.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_THRESH_ERROR** (0x18) O novo limiar de pré-substituição especificado não é uma prioridade de linha válida (um valor diferente (0 a **TX_MAX_PRIORITIES**-1)) ou é maior do que (prioridade inferior) do que a prioridade atual do fio.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para o local de armazenamento de retenção preventiva anterior.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

Alterar prioridade do fio de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>Description

Este serviço altera a prioridade do fio especificado. As prioridades válidas variam entre 0 e TX_MAX_PRIORITES-1, onde 0 representa o nível de maior prioridade.

> [!IMPORTANT]
> *O limiar de pré-substituição do fio especificado é automaticamente definido para a nova prioridade. Se for desejado um novo limiar, o serviço ***tx_thread_preemption_change** _ deve ser utilizado após este call._

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio de aplicação previamente criado.
- **new_priority** Novo nível de prioridade do fio (0 a TX_MAX_PRIORITIES-1)).
- **old_priority** Ponteiro para um local para devolver a prioridade anterior da linha.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Mudança de prioridade bem sucedida.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_PRIORITY_ERROR** (0x0F) A nova prioridade especificada não é válida (um valor diferente (0 a TX_MAX_PRIORITIES-1)).
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para localização de armazenamento prioritário anterior.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

Renunciar ao controlo a outros fios de aplicação

### <a name="prototype"></a>Prototype

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>Description

Este serviço renuncia ao controlo do processador a outras linhas prontas a executar na mesma prioridade ou maior.

> [!NOTE]
> *Além de renunciar ao controlo a fios da mesma prioridade, este serviço também renuncia ao controlo ao fio de maior prioridade impedido de ser executado devido à definição do limiar de prevenção da linha atual.*

### <a name="parameters"></a>Parâmetros

Nenhum

### <a name="return-values"></a>Valores de devolução

Nenhuma

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="examples"></a>Exemplos

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

Linha de reset

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço reinicia o fio especificado para executar no ponto de entrada definido na criação do fio. O fio deve estar em um **estado TX_COMPLETED** ou **TX_TERMINATED** para que seja reposto

> [!IMPORTANT]
> *O fio deve ser retomado para que volte a ser executado.*

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reposição de fio bem sucedida.
- **TX_NOT_DONE** (0x20) O fio especificado não está num estado **TX_COMPLETED** ou **TX_TERMINATED.**
- **TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="example"></a>Exemplo

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

Retomar linha de aplicação suspensa

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço retoma ou prepara para a execução um fio que foi previamente suspenso por uma ***chamada tx_thread_suspend.*** Além disso, este serviço retoma os fios que foram criados sem um arranque automático.

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio de aplicação suspenso.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Currículo de fio bem sucedido.
- **TX_SUSPEND_LIFTED** (0x19) A suspensão adiada previamente definida foi levantada.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_RESUME_ERROR** (0x12) O fio especificado não está suspenso ou foi previamente suspenso por um serviço que não **_tx_thread_suspend_**.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

TX_THREAD my_thread;

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

Suspender o fio de corrente por tempo especificado

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>Description

Este serviço faz com que o fio de chamada suspenda o número especificado de carraças temporais. A quantidade de tempo físico associado a um tique-taque do temporizador é específica da aplicação. Este serviço só pode ser chamado a partir de um fio de aplicação.

### <a name="parameters"></a>Parâmetros

- **timer_ticks** O número de carraças temporizador para suspender o fio da aplicação de chamada, que varia de 0 a 0xFFFFFFFF. Se 0 for especificado, o serviço retorna imediatamente.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Sono de linha bem sucedido.
- **TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.
- **TX_CALLER_ERROR** serviço (0x13) chamado de um não-thread.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Registar chamada de notificação de erro de pilha de fio

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>Description

Este serviço regista uma função de chamada de notificação para lidar com erros de pilha de fios. Quando a ThreadX detetar um erro de pilha de fio durante a execução, chamará esta função de notificação para processar o erro. O processamento do erro é completamente definido pela aplicação. Qualquer coisa desde suspender o fio de violação até reiniciar todo o sistema pode ser feito.

> [!IMPORTANT]
> *A biblioteca ThreadX deve ser construída com* **TX_ENABLE_STACK_CHECKING** *definidas para que este serviço devolva informações de desempenho.*

### <a name="parameters"></a>Parâmetros
- **error_handler** Ponteiro para a função de manuseamento de erros de pilha da aplicação. Se este valor for TX_NULL, a notificação é desativada.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Reposição de fio bem sucedida.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Suspender o fio de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço suspende o fio de aplicação especificado. Um fio pode chamar este serviço para se suspender.

> [!NOTE]
> *Se o fio especificado já estiver suspenso por outro motivo, esta suspensão é mantida internamente até que a suspensão prévia seja levantada. Quando isso acontece, esta suspensão incondicional do fio especificado é executada. Outros pedidos de suspensão incondicional não têm efeito.*

Depois de suspensa, o fio deve ser retomado por ***tx_thread_resume*** para ser executado novamente.

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio de aplicação.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Suspender o fio de sucesso.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_SUSPEND_ERROR** (0x14) O fio especificado encontra-se num estado encerrado ou concluído.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

Termina linha de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Description

Este serviço termina o fio de aplicação especificado, independentemente de o fio estar suspenso ou não. Um fio pode chamar este serviço para terminar sozinho.

> [!NOTE]
> *É da responsabilidade da aplicação assegurar que o fio está num estado adequado para a rescisão. Por exemplo, um fio não deve ser terminado durante o processamento crítico da aplicação ou no interior de outros componentes do middleware onde possa deixar esse processamento num estado desconhecido.*

> [!IMPORTANT]
> *Depois de ter sido encerrado, o fio deve ser reiniciado para que volte a ser executado.*

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para o fio de aplicação.

### <a name="return-values"></a>Valores de devolução
- **TX_SUCCESS** (0x00) Fim de linha bem sucedida.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Altera a fatia de tempo do fio de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>Description

Este serviço altera a fatia de tempo do fio de aplicação especificado. Selecionar uma fatia de tempo para um fio assegura que não executará mais do que o número especificado de carraças de temporizador antes que outros fios das mesmas prioridades ou mais altas tenham a oportunidade de executar.

> [!NOTE]
> *A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.*

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para o fio de aplicação.
- **new_time_slice** Novo valor de fatia de tempo. Os valores legais incluem valores TX_NO_TIME_SLICE e numéricos de 1 a 0xFFFFFFFF.
- **old_time_slice** Ponteiro para o local para armazenar o valor dos ísamentos anteriores do fio especificado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Oportunidade de corte de tempo bem sucedida.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_PTR_ERROR** (0x03) Ponteiro inválido para o local de armazenamento anterior da fatia de tempo.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios e temporizadores

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

Abortar suspensão do fio especificado

### <a name="prototype"></a>Prototype

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Description

Este serviço aborta o sono ou qualquer outro objeto suspenso do fio especificado. Se a espera for abortada, um **valor TX_WAIT_ABORTED** é devolvido do serviço que o fio estava à espera.

> [!NOTE]
> *Este serviço não liberta suspensão explícita que é feita pelo serviço tx_thread_suspend.*

### <a name="parameters"></a>Parâmetros

- **thread_ptr** Ponteiro para um fio de aplicação previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Abortar a espera de fio bem sucedida.
- **TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.
- **TX_WAIT_ABORT_ERROR** (0x1B) O fio especificado não está em estado de espera.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível
Yes

### <a name="example"></a>Exemplo

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>Consulte também

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

Recupera o tempo atual

Temporizadores de aplicação

### <a name="prototype"></a>Prototype

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>Description

Este serviço devolve o conteúdo do relógio interno do sistema. Cada timertick aumenta o relógio do sistema interno por um. O relógio do sistema está definido para zero durante a inicialização e pode ser alterado para um valor específico pelo ***serviço tx_time_set***.

> [!NOTE]
> *O tempo real que cada temporizador representa é específico da aplicação.*

**Parâmetros**

Nenhuma

### <a name="return-values"></a>Valores de devolução

- **relógio do sistema tiques** Valor do relógio interno, livre, do sistema.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível
No

### <a name="example"></a>Exemplo

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>Consulte também

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Define a hora atual

### <a name="prototype"></a>Prototype

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>Description

Este serviço define o relógio do sistema interno ao valor especificado. Cada temporizador aumenta o relógio do sistema interno por um.

> [!NOTE]
> *O tempo real que cada temporizador representa é específico da aplicação.*

### <a name="parameters"></a>Parâmetros

- **new_time** Novo tempo para colocar no relógio do sistema, os valores legais variam de 0 a 0xFFFFFFFF.

### <a name="return-values"></a>Valores de devolução

Nenhuma

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>Consulte também

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

Ativar o temporizador de aplicações

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Este serviço ativa o temporizador de aplicação especificado. As rotinas de expiração dos temporizadores que expiram ao mesmo tempo são executadas na ordem em que foram ativados.

> [!NOTE]
> *Um temporizador de um tiro expirado deve ser reposto através*  * **tx_timer_change** _ _before pode ser ativado novamente.*

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.

**Valores de devolução**

- **TX_SUCCESS** (0x00) Ativação do temporizador de aplicação bem sucedida.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.
- **TX_ACTIVATE_ERROR** (0x17) Timer já estava ativo ou é um temporizador de um tiro que já expirou.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

Alterar temporizador de aplicação

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>Description

Este serviço altera as características de expiração do temporizador de aplicação especificado. O temporizador deve ser desativado antes de ligar para este serviço.

> [!NOTE]
> *Uma chamada para o*  * **tx_timer_activate** _ _service é necessária após este serviço para recomeçar o temporizador.*

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um bloco de controlo do temporizador.
- **initial_ticks** Especifica o número inicial de carraças para a expiração do temporizador. Os valores legais variam de 1 a 0xFFFFFFFF.
- **reschedule_ticks** Especifica o número de tiques para todos os expiradores do temporizador após o primeiro. Um zero para este parâmetro faz do temporizador um *temporizador de um tiro.* Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.

> [!NOTE]
> *Um temporizador de um tiro expirado deve ser reposto através* 
* **tx_timer_change** _ _before pode ser ativado novamente.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Alteração do temporizador de aplicação bem sucedido.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.
- **TX_TICK_ERROR** (0x16) Valor inválido (um zero) fornecido para os tiques iniciais.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

Criar temporizador de aplicações

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a>Description

Este serviço cria um temporizador de aplicação com a função de expiração especificada e periódico.

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um bloco de controlo do temporizador
- **name_ptr** Ponteiro para o nome do temporizador.
- **expiration_function** Função de aplicação para ligar quando o temporizador expirar.
- **expiration_input** Entrada para passar para a função de expiração quando o temporizador expirar.
- **initial_ticks** Especifica o número inicial de carraças para a expiração do temporizador. Os valores legais variam de 1 a 0xFFFFFFFF.
- **reschedule_ticks** Especifica o número de tiques para todos os expiradores do temporizador após o primeiro. Um zero para este parâmetro faz do temporizador um *temporizador de um tiro.* Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.

  > [!NOTE]
  > *Depois de expirar um temporizador de uma única vez, deve ser reiniciado através de tx_timer_change antes de poder ser ativado novamente.*

- **auto_activate** Determina se o temporizador é ativado automaticamente durante a criação. Se este valor for **TX_AUTO_ACTIVATE** (0x01), o temporizador torna-se ativo. Caso contrário, se o valor **TX_NO_ACTIVATE** (0x00) for selecionado, o temporizador é criado num estado não ativo. Neste caso, é necessária uma chamada de serviço **_tx_timer_activate_** subsequente para iniciar o temporizador.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Criação de temporizador de aplicação bem sucedido.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido. Ou o ponteiro é NULO ou o temporizador já está criado.
- **TX_TICK_ERROR** (0x16) Valor inválido (um zero) fornecido para os tiques iniciais.
- **TX_ACTIVATE_ERROR** (0x17) Ativação inválida selecionada.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização e fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

Temporizador de aplicação desativado

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Este serviço desativa o temporizador de aplicação especificado. Se o temporizador já estiver desativado, este serviço não tem efeito.

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desativação do temporizador de aplicação bem sucedido.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

Eliminar temporizador de aplicações

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Description

Este serviço elimina o temporizador de aplicação especificado.

> [!NOTE]
> *É da responsabilidade da aplicação impedir a utilização de um temporizador eliminado.*

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Eliminação do temporizador de aplicação bem sucedido.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.
- **TX_CALLER_ERROR** (0x13) Inválido deste serviço.

### <a name="allowed-from"></a>Permitido a partir de

Fios

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

Recuperar informações sobre um temporizador de aplicações

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>Description

Este serviço obtém informações sobre o temporizador de aplicação especificado.

### <a name="parameters"></a>Parâmetros

- **timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.
- **nome** Ponteiro para o destino para o ponteiro para o nome do temporizador.
- **ativo** Ponteiro para o destino para a indicação ativa do temporizador. Se o temporizador estiver inativo ou este serviço for chamado do temporizador em si, é devolvido um **valor TX_FALSE.** Caso contrário, se o temporizador estiver ativo, é devolvido um valor **TX_TRUE.**
- **remaining_ticks** Ponteiro para o destino para o número de carraças de temporizador que sobrou antes do temporizador expirar.
- **reschedule_ticks** Ponteiro para o destino para o número de carraças tempor que serão usadas para reagendar automaticamente este temporizador. Se o valor for zero, então o temporizador é um tiro e não será reagendado.
- **next_timer** Ponteiro para o destino para o ponteiro do próximo temporizador de aplicação criado.

> [!NOTE]
> *O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Recuperação de informações cronometrador de sucesso.
- **TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="preemption-possible"></a>Preempção Possível

No

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

Obtenha informações de desempenho do temporizador

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

Este serviço recupera informações de desempenho sobre o temporizador de aplicação especificado.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com*  * **TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.*

### <a name="parameters"></a>Parâmetros
- **timer_ptr** Ponteiro para temporizador previamente criado.
- **ativa** Ponteiro para destino para o número de pedidos de ativação realizados neste temporizador.
- **reativa** Ponteiro para o destino para o número de reativações automáticas realizadas neste temporizador periódico.
- **desativa** Ponteiro para destino para o número de pedidos de desativação realizados neste temporizador.
- **expirações** Ponteiro para o destino para o número de expirações deste temporizador.
- **expiration_adjusts** Ponteiro para destino para o número de ajustes internos de validade realizados neste temporizador. Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).

> [NOTA] *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do temporizador de sucesso obtém.
- **TX_PTR_ERROR** (0x03) Ponteiro temporizador inválido.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

Obtenha informações sobre o desempenho do sistema do temporizador

### <a name="prototype"></a>Prototype

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Description

Este serviço obtém informações de desempenho sobre todos os temporizadores de aplicação no sistema.

> [!IMPORTANT]
> *A biblioteca e aplicação ThreadX devem ser construídas com* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*

**Parâmetros**

- **ativa** Ponteiro para destino para o número total de pedidos de ativação realizados em todos os temporizadores.
- **reativa** Ponteiro para destino para o número total de reativação automática realizada em todos os temporizadores periódicos.
- **desativa** Ponteiro para destino para o número total de pedidos de desativação realizados em todos os temporizadores.
- **expirações** Ponteiro para destino para o número total de expirações em todos os temporizadores.
- **expiration_adjusts** Ponteiro para destino para o número total de ajustes internos de validade realizados em todos os temporizadores. Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).

> [!NOTE]
> *O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*

### <a name="return-values"></a>Valores de devolução

- **TX_SUCCESS** (0x00) Desempenho do sistema temporizador de sucesso obtém.
- **TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.

### <a name="allowed-from"></a>Permitido a partir de

Inicialização, fios, temporizadores e ISRs

### <a name="example"></a>Exemplo

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>Consulte também

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
