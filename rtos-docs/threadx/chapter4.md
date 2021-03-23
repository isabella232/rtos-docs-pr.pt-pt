---
title: Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825459"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="8036f-103">Capítulo 4 - Descrição dos Serviços Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="8036f-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="8036f-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS ThreadX por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="8036f-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="8036f-105">Os seus nomes são concebidos para que todos os serviços semelhantes sejam agrupados.</span><span class="sxs-lookup"><span data-stu-id="8036f-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="8036f-106">Na secção "Valores de Retorno" nas seguintes descrições, os valores em **BOLD** não são afetados pela **TX_DISABLE_ERROR_CHECKING** definem utilizados para desativar a verificação de erros da API; enquanto os valores mostrados em nãobold são completamente desativados.</span><span class="sxs-lookup"><span data-stu-id="8036f-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="8036f-107">Além disso, um "**Sim**" listado sob a rubrica "**Preemption Possible**" indica que ligar para o serviço pode retomar um fio de maior prioridade, antecipando assim o fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="8036f-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="8036f-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-108">tx_block_allocate</span></span>

<span data-ttu-id="8036f-109">Alocar bloco de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="8036f-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-110">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-111">Description</span></span>

<span data-ttu-id="8036f-112">Este serviço aloca um bloco de memória de tamanho fixo a partir do conjunto de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="8036f-113">O tamanho real do bloco de memória é determinado durante a criação do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-114">*É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído. Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes fatais!*</span><span class="sxs-lookup"><span data-stu-id="8036f-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-115">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-115">Parameters</span></span>

- <span data-ttu-id="8036f-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-116">**pool_ptr**</span></span> <br><span data-ttu-id="8036f-117">Ponteiro para um conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="8036f-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-118">**block_ptr**</span></span> <br><span data-ttu-id="8036f-119">Ponteiro para um ponteiro de bloco de destino.</span><span class="sxs-lookup"><span data-stu-id="8036f-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="8036f-120">Na atribuição bem sucedida, o endereço do bloco de memória atribuído é colocado onde este parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="8036f-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="8036f-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-121">**wait_option**</span></span> <br><span data-ttu-id="8036f-122">Define como o serviço se comporta se não houver blocos de memória disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8036f-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="8036f-123">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-124">**TX_NO_WAIT** (0x00000000) - A seleção **TX_NO_WAIT** resulta num retorno imediato deste serviço, independentemente de ter sido bem sucedida ou não.</span><span class="sxs-lookup"><span data-stu-id="8036f-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="8036f-125">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="8036f-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="8036f-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que um bloco de memória esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="8036f-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="8036f-127">*Valor de tempo limite* (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por um bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-128">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-128">Return Values</span></span>

- <span data-ttu-id="8036f-129">**TX_SUCCESS**    (0x00) Alocação de blocos de memória bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="8036f-130">**TX_DELETED**    (0x01) O conjunto de blocos de memória foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-131">**TX_NO_MEMORY**  (0x10) O Serviço não foi capaz de alocar um bloco de memória dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="8036f-132">**TX_WAIT_ABORTED**   (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="8036f-133">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="8036f-134">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="8036f-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8036f-135">**TX_PTR_ERROR**  (0x03) Ponteiro inválido para ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="8036f-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-136">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-136">Allowed From</span></span>

<span data-ttu-id="8036f-137">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-138">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-138">Preemption Possible</span></span>

<span data-ttu-id="8036f-139">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-140">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-141">See Also</span></span>

- <span data-ttu-id="8036f-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-142">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8036f-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8036f-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="8036f-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-149">tx_block_pool_create</span></span>

<span data-ttu-id="8036f-150">Criar piscina de blocos de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="8036f-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="8036f-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-152">Description</span></span>

<span data-ttu-id="8036f-153">Este serviço cria uma piscina de blocos de memória de tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="8036f-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="8036f-154">A área de memória especificada é dividida em tantos blocos de memória de tamanho fixo quanto possível utilizando a fórmula:</span><span class="sxs-lookup"><span data-stu-id="8036f-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="8036f-155">**blocos totais** =**(bytes totais)**/**(tamanho do bloco** + tamanho (vazio \*))</span><span class="sxs-lookup"><span data-stu-id="8036f-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="8036f-156">\*Cada bloco de memória contém um ponteiro de sobrecarga que é invisível para o utilizador e é representado pelo "tamanho(vazio) *na fórmula anterior.*</span><span class="sxs-lookup"><span data-stu-id="8036f-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-157">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-157">Parameters</span></span>

- <span data-ttu-id="8036f-158">**pool_ptr**  Ponteiro para um bloco de controlo de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="8036f-159">**name_ptr**  Ponteiro para o nome do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="8036f-160">**block_size**    Número de bytes em cada bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="8036f-161">**pool_start**    Endereço inicial do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="8036f-162">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="8036f-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="8036f-163">**pool_size** Número total de bytes disponíveis para o conjunto de blocos de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-164">Return Values</span></span>

- <span data-ttu-id="8036f-165">**TX_SUCCESS**    (0x00) Criação de piscina de blocos de memória bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="8036f-166">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="8036f-167">Ou o ponteiro é NULO ou a piscina já está criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="8036f-168">**TX_PTR_ERROR**  (0x03) Endereço inicial inválido da piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="8036f-169">**TX_CALLER_ERROR**   (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="8036f-170">**TX_SIZE_ERROR** (0x05) O tamanho da piscina é inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-171">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-171">Allowed From</span></span>

<span data-ttu-id="8036f-172">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-173">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-173">Preemption Possible</span></span>

<span data-ttu-id="8036f-174">No</span><span class="sxs-lookup"><span data-stu-id="8036f-174">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-175">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-176">See Also</span></span>

- <span data-ttu-id="8036f-177">tx_block_allocate, tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-180">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="8036f-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-181">tx_block_pool_delete</span></span>

<span data-ttu-id="8036f-182">Apagar o conjunto de blocos de memória</span><span class="sxs-lookup"><span data-stu-id="8036f-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-183">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-184">Description</span></span>

<span data-ttu-id="8036f-185">Este serviço elimina o conjunto de memória de bloco especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="8036f-186">Todos os fios suspensos à espera de um bloco de memória desta piscina são retomados e dado um **estado de retorno TX_DELETED.**</span><span class="sxs-lookup"><span data-stu-id="8036f-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-187">*É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de uma piscina eliminada ou dos seus antigos blocos de memória.*</span><span class="sxs-lookup"><span data-stu-id="8036f-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-188">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-188">Parameters</span></span>

- <span data-ttu-id="8036f-189">**pool_ptr** Ponteiro para um conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-190">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-190">Return Values</span></span>

- <span data-ttu-id="8036f-191">**TX_SUCCESS** (0x00) Eliminação bem sucedida do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="8036f-192">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="8036f-193">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-194">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-194">Allowed From</span></span>

<span data-ttu-id="8036f-195">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-196">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-196">Preemption Possible</span></span>

<span data-ttu-id="8036f-197">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="8036f-199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-199">See Also</span></span>

- <span data-ttu-id="8036f-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-200">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-201">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-204">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="8036f-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="8036f-206">Recuperar informações sobre a piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="8036f-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-207">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-207">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-208">Description</span></span>

<span data-ttu-id="8036f-209">Este serviço obtém informações sobre o conjunto de memórias de bloco especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-210">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-210">Parameters</span></span>

- <span data-ttu-id="8036f-211">**pool_ptr**  Ponteiro para o bloco de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="8036f-212">**nome**  Ponteiro para o destino para o ponteiro para o nome da piscina do bloco.</span><span class="sxs-lookup"><span data-stu-id="8036f-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="8036f-213">**disponível** Ponteiro para o destino para o número de blocos disponíveis na piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="8036f-214">**total_blocks**  Ponteiro para o destino para o número total de blocos na piscina de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="8036f-215">**first_suspended**   Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste bloco pool.</span><span class="sxs-lookup"><span data-stu-id="8036f-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="8036f-216">**suspended_count**   Ponteiro para o destino para o número de fios atualmente suspensos neste bloco pool.</span><span class="sxs-lookup"><span data-stu-id="8036f-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="8036f-217">**next_pool** Ponteiro para o destino para o ponteiro do próximo conjunto de blocos criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-218">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-219">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-219">Return Values</span></span>

- <span data-ttu-id="8036f-220">**TX_SUCCESS** (0x00) Recuperar informações de piscina de blocos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="8036f-221">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-222">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-222">Allowed From</span></span>

<span data-ttu-id="8036f-223">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-224">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-224">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-225">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-225">See Also</span></span>

- <span data-ttu-id="8036f-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-226">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-227">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-231">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="8036f-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="8036f-233">Obtenha informações de desempenho da piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="8036f-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-234">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="8036f-235">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-235">Description</span></span>

<span data-ttu-id="8036f-236">Este serviço obtém informações de desempenho sobre o conjunto de blocos de memória especificados.</span><span class="sxs-lookup"><span data-stu-id="8036f-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-237">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-238">Parameters</span></span>

- <span data-ttu-id="8036f-239">**pool_ptr**  Ponteiro para o bloco de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="8036f-240">**atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-241">**liberta**  Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-242">**suspensões**   Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="8036f-243">**intervalos**  Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="8036f-244">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-245">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-245">Return Values</span></span>

- <span data-ttu-id="8036f-246">**TX_SUCCESS**    (0x00) Desempenho bem sucedido da piscina de blocos obter.</span><span class="sxs-lookup"><span data-stu-id="8036f-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="8036f-247">**TX_PTR_ERROR**  (0x03) Ponteiro de piscina de bloco inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="8036f-248">**TX_FEATURE_NOT_ENABLED**    (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-249">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-249">Allowed From</span></span>

<span data-ttu-id="8036f-250">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-251">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-251">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-252">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-252">See Also</span></span>

- <span data-ttu-id="8036f-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-253">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-254">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8036f-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="8036f-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="8036f-261">Obtenha informações de desempenho do sistema de piscina de blocos</span><span class="sxs-lookup"><span data-stu-id="8036f-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-263">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-263">Description</span></span>

<span data-ttu-id="8036f-264">Este serviço obtém informações de desempenho sobre todos os conjuntos de blocos de memória na aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-265">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-266">Parameters</span></span>

- <span data-ttu-id="8036f-267">**atribui** Ponteiro para destino para o número total de pedidos de atribuição realizados em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="8036f-268">**liberta**  Ponteiro para destino para o número total de pedidos de libertação realizados em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="8036f-269">**suspensões**   Ponteiro para o destino para o número total de suspensões de atribuição de fios em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="8036f-270">**intervalos**  Ponteiro para o destino para o número total de intervalos de suspensão atribuídos em todas as piscinas de blocos.</span><span class="sxs-lookup"><span data-stu-id="8036f-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-271">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-272">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-272">Return Values</span></span>

- <span data-ttu-id="8036f-273">**TX_SUCCESS** (0x00) Desempenho do sistema de piscina de blocos bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="8036f-274">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-275">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-275">Allowed From</span></span>

<span data-ttu-id="8036f-276">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-277">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-277">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-278">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-278">See Also</span></span>

- <span data-ttu-id="8036f-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-279">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-280">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8036f-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8036f-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="8036f-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="8036f-287">Priorizar lista de suspensão de piscina de bloco</span><span class="sxs-lookup"><span data-stu-id="8036f-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-289">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-289">Description</span></span>

<span data-ttu-id="8036f-290">Este serviço coloca o fio de prioridade mais elevado suspenso por um bloco de memória nesta piscina na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="8036f-291">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-292">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-292">Parameters</span></span>

- <span data-ttu-id="8036f-293">**pool_ptr** Ponteiro para um bloco de controlo de piscina de bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-294">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-294">Return Values</span></span>

- <span data-ttu-id="8036f-295">**TX_SUCCESS** (0x00) Prioridades de piscina de blocos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="8036f-296">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de bloco de memória inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-297">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-297">Allowed From</span></span>

<span data-ttu-id="8036f-298">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-299">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-299">Preemption Possible</span></span>

<span data-ttu-id="8036f-300">No</span><span class="sxs-lookup"><span data-stu-id="8036f-300">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-301">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-301">Example</span></span>
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

### <a name="see-also"></a><span data-ttu-id="8036f-302">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-302">See Also</span></span>

- <span data-ttu-id="8036f-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-303">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-304">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8036f-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="8036f-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8036f-310">tx_block_release</span></span>

<span data-ttu-id="8036f-311">Liberte o bloco de memória de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="8036f-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-312">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="8036f-313">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-313">Description</span></span>

<span data-ttu-id="8036f-314">Este serviço liberta um bloco previamente atribuído de volta ao seu pool de memória associado.</span><span class="sxs-lookup"><span data-stu-id="8036f-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="8036f-315">Se houver um ou mais fios suspensos à espera de blocos de memória desta piscina, o primeiro fio suspenso é dado a este bloco de memória e retomado.</span><span class="sxs-lookup"><span data-stu-id="8036f-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="8036f-316">*A aplicação deve evitar a utilização de uma área de bloco de memória depois de ter sido libertada de volta à piscina.*</span><span class="sxs-lookup"><span data-stu-id="8036f-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-317">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-317">Parameters</span></span>

- <span data-ttu-id="8036f-318">**block_ptr** Ponteiro para o bloco de memória previamente atribuído.</span><span class="sxs-lookup"><span data-stu-id="8036f-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-319">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-319">Return Values</span></span>

- <span data-ttu-id="8036f-320">**TX_SUCCESS** (0x00) Desbloqueio do bloco de memória bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="8036f-321">**TX_PTR_ERROR** (0x03) Ponteiro inválido para o bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-322">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-322">Allowed From</span></span>

<span data-ttu-id="8036f-323">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-324">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-324">Preemption Possible</span></span>

<span data-ttu-id="8036f-325">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-326">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-326">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-327">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-327">See Also</span></span>

- <span data-ttu-id="8036f-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-328">tx_block_allocate</span></span>
- <span data-ttu-id="8036f-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-329">tx_block_pool_create</span></span>
- <span data-ttu-id="8036f-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="8036f-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8036f-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="8036f-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-335">tx_byte_allocate</span></span>

<span data-ttu-id="8036f-336">Alocar bytes de memória</span><span class="sxs-lookup"><span data-stu-id="8036f-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-338">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-338">Description</span></span>

<span data-ttu-id="8036f-339">Este serviço atribui o número especificado de bytes da piscina de bytes de memória especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-340">*É importante garantir que o código de aplicação não escreve fora do bloco de memória atribuído. Se isso acontecer, a corrupção ocorre num bloco de memória adjacente (geralmente subsequente). Os resultados são imprevisíveis e muitas vezes fatais!*</span><span class="sxs-lookup"><span data-stu-id="8036f-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-341">*O desempenho deste serviço é uma função do tamanho do bloco e da quantidade de fragmentação na piscina. Por conseguinte, este serviço não deve ser utilizado durante os fios críticos de execução.*</span><span class="sxs-lookup"><span data-stu-id="8036f-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-342">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-342">Parameters</span></span>

- <span data-ttu-id="8036f-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-343">**pool_ptr**</span></span> <br><span data-ttu-id="8036f-344">Ponteiro para um conjunto de blocos de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="8036f-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-345">**memory_ptr**</span></span> <br><span data-ttu-id="8036f-346">Ponteiro para um ponteiro de memória de destino.</span><span class="sxs-lookup"><span data-stu-id="8036f-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="8036f-347">Na atribuição bem sucedida, o endereço da área de memória atribuída é colocado onde este parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="8036f-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="8036f-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="8036f-348">**memory_size**</span></span> <br><span data-ttu-id="8036f-349">Número de bytes solicitados.</span><span class="sxs-lookup"><span data-stu-id="8036f-349">Number of bytes requested.</span></span>
- <span data-ttu-id="8036f-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-350">**wait_option**</span></span> <br><span data-ttu-id="8036f-351">Define como o serviço se comporta se não houver memória suficiente disponível.</span><span class="sxs-lookup"><span data-stu-id="8036f-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="8036f-352">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-353">**TX_NO_WAIT** (0x00000000) - A seleção **TX_NO_WAIT** resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-354">*Esta é a única opção válida se o serviço for chamado de inicialização.*</span><span class="sxs-lookup"><span data-stu-id="8036f-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="8036f-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que esteja disponível memória suficiente.</span><span class="sxs-lookup"><span data-stu-id="8036f-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="8036f-356">*Valor de tempo limite* (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pela memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-357">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-357">Return Values</span></span>

- <span data-ttu-id="8036f-358">**TX_SUCCESS** (0x00) Alocação de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="8036f-359">**TX_DELETED** (0x01) O pool de memória foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-360">**TX_NO_MEMORY** serviço (0x10) não foi capaz de alocar a memória dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="8036f-361">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-362">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="8036f-363">**TX_PTR_ERROR** (0x03) Ponteiro inválido para ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="8036f-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="8036f-364">**TX_SIZE_ERROR** (0X05) O tamanho solicitado é zero ou maior do que a piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="8036f-365">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="8036f-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8036f-366">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-367">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-367">Allowed From</span></span>

<span data-ttu-id="8036f-368">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-369">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-369">Preemption Possible</span></span>

<span data-ttu-id="8036f-370">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-371">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-371">Example</span></span>
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

### <a name="see-also"></a><span data-ttu-id="8036f-372">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-372">See Also</span></span>

- <span data-ttu-id="8036f-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="8036f-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-380">tx_byte_pool_create</span></span>

<span data-ttu-id="8036f-381">Criar piscina de memória de bytes</span><span class="sxs-lookup"><span data-stu-id="8036f-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-382">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="8036f-383">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-383">Description</span></span>

<span data-ttu-id="8036f-384">Este serviço cria uma piscina de byte de memória na área especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="8036f-385">Inicialmente, a piscina é composta por basicamente um bloco livre muito grande.</span><span class="sxs-lookup"><span data-stu-id="8036f-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="8036f-386">No entanto, a piscina é dividida em blocos menores à medida que as dotações são feitas.</span><span class="sxs-lookup"><span data-stu-id="8036f-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-387">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-387">Parameters</span></span>

- <span data-ttu-id="8036f-388">**pool_ptr** Ponteiro para um bloco de controlo de piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="8036f-389">**name_ptr** Ponteiro para o nome do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="8036f-390">**pool_start** Endereço inicial do pool de memórias.</span><span class="sxs-lookup"><span data-stu-id="8036f-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="8036f-391">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="8036f-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="8036f-392">**pool_size** Número total de bytes disponíveis para o pool de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-393">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-393">Return Values</span></span>

- <span data-ttu-id="8036f-394">**TX_SUCCESS** (0x00) Criação de piscina de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="8036f-395">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="8036f-396">Ou o ponteiro é NULO ou a piscina já está criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="8036f-397">**TX_PTR_ERROR** (0x03) Endereço inicial inválido da piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="8036f-398">**TX_SIZE_ERROR** (0x05) O tamanho da piscina é inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="8036f-399">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-400">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-400">Allowed From</span></span>

<span data-ttu-id="8036f-401">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-402">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-402">Preemption Possible</span></span>

<span data-ttu-id="8036f-403">No</span><span class="sxs-lookup"><span data-stu-id="8036f-403">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-404">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-404">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-405">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-405">See Also</span></span>

- <span data-ttu-id="8036f-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-406">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="8036f-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="8036f-414">Apagar piscina de byte de memória</span><span class="sxs-lookup"><span data-stu-id="8036f-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-415">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-416">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-416">Description</span></span>

<span data-ttu-id="8036f-417">Este serviço elimina o conjunto de bytes de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="8036f-418">Todos os fios suspensos à espera de memória desta piscina são retomados e dado um **estado de retorno TX_DELETED.**</span><span class="sxs-lookup"><span data-stu-id="8036f-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-419">*É da responsabilidade da aplicação gerir a área de memória associada à piscina, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de um pool ou memória eliminados previamente atribuídos a partir do mesmo.*</span><span class="sxs-lookup"><span data-stu-id="8036f-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-420">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-420">Parameters</span></span>

- <span data-ttu-id="8036f-421">**pool_ptr** Ponteiro para um pool de memória previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-422">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-422">Return Values</span></span>

- <span data-ttu-id="8036f-423">**TX_SUCCESS** (0x00) Eliminação bem sucedida do pool de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="8036f-424">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="8036f-425">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-426">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-426">Allowed From</span></span>

<span data-ttu-id="8036f-427">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-428">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-428">Preemption Possible</span></span>

<span data-ttu-id="8036f-429">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-430">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-431">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-431">See Also</span></span>

- <span data-ttu-id="8036f-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-432">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="8036f-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="8036f-440">Recuperar informações sobre a piscina byte</span><span class="sxs-lookup"><span data-stu-id="8036f-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-441">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-442">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-442">Description</span></span>

<span data-ttu-id="8036f-443">Este serviço obtém informações sobre o byte de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-444">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-444">Parameters</span></span>

- <span data-ttu-id="8036f-445">**pool_ptr** Ponteiro para piscina de memória previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="8036f-446">**nome** Ponteiro para o destino para o ponteiro para o nome da piscina byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="8036f-447">**disponível** Ponteiro para o destino para o número de bytes disponíveis na piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="8036f-448">**fragmentos** Ponteiro para o destino para o número total de fragmentos de memória na piscina byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="8036f-449">**first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão desta piscina byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="8036f-450">**suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos nesta piscina byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="8036f-451">**next_pool** Ponteiro para o destino para o ponteiro do próximo byte criado pool.</span><span class="sxs-lookup"><span data-stu-id="8036f-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-452">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-453">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-453">Return Values</span></span>

- <span data-ttu-id="8036f-454">**TX_SUCCESS** (0x00) Recuperar informações de piscina bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="8036f-455">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-456">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-456">Allowed From</span></span>

<span data-ttu-id="8036f-457">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-458">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-458">Preemption Possible</span></span>

<span data-ttu-id="8036f-459">No</span><span class="sxs-lookup"><span data-stu-id="8036f-459">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-460">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-460">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-461">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-461">See Also</span></span>

- <span data-ttu-id="8036f-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-462">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="8036f-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="8036f-470">Obter informações sobre desempenho da piscina byte</span><span class="sxs-lookup"><span data-stu-id="8036f-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-471">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-471">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-472">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-472">Description</span></span>

<span data-ttu-id="8036f-473">Este serviço obtém informações de desempenho sobre a piscina de byte de memória especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-474">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-475">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-475">Parameters</span></span>

- <span data-ttu-id="8036f-476">**pool_ptr** Ponteiro para a piscina byte de memória previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="8036f-477">**atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-478">**liberta** Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-479">**fragments_searched** Ponteiro para o destino para o número de fragmentos de memória interna pesquisados durante os pedidos de atribuição nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="8036f-480">**funde** Ponteiro para destino para o número de blocos de memória internos fundidos durante os pedidos de atribuição nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="8036f-481">**divisões** Ponteiro para o destino para o número de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="8036f-482">**suspensões** Ponteiro para o destino para o número de suspensões de atribuição de fios nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="8036f-483">**intervalos** Ponteiro para o destino para o número de intervalos de suspensão atribuídos nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-484">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-485">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-485">Return Values</span></span>

- <span data-ttu-id="8036f-486">**TX_SUCCESS** (0x00) Desempenho de byte de piscina bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="8036f-487">**TX_PTR_ERROR** (0x03) Ponteiro de piscina inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="8036f-488">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-489">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-489">Allowed From</span></span>

<span data-ttu-id="8036f-490">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-491">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-491">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8036f-492">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-492">See Also</span></span>

- <span data-ttu-id="8036f-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-493">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="8036f-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="8036f-501">Obtenha informações sobre o desempenho do sistema de piscinas byte</span><span class="sxs-lookup"><span data-stu-id="8036f-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-502">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-502">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="8036f-503">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-503">Description</span></span>

<span data-ttu-id="8036f-504">Este serviço obtém informações de desempenho sobre todas as piscinas de byte de memória no sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-505">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-506">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-506">Parameters</span></span>

- <span data-ttu-id="8036f-507">**atribui** Ponteiro para destino para o número de pedidos de atribuição realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-508">**liberta** Ponteiro para destino para o número de pedidos de lançamento realizados nesta piscina.</span><span class="sxs-lookup"><span data-stu-id="8036f-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8036f-509">**fragments_searched** Ponteiro para o destino para o número total de fragmentos de memória interna pesquisados durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8036f-510">**funde** Ponteiro para destino para o número total de blocos de memória internos fundidos durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8036f-511">**divisões** Ponteiro para destino para o número total de blocos de memória internos divididos (fragmentos) criados durante os pedidos de atribuição em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8036f-512">**suspensões** Ponteiro para destino para o número total de suspensões de atribuição de fios em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="8036f-513">**intervalos** Ponteiro para o destino para o número total de intervalos de suspensão alocados em todas as piscinas byte.</span><span class="sxs-lookup"><span data-stu-id="8036f-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-514">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-515">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-515">Return Values</span></span>

- <span data-ttu-id="8036f-516">**TX_SUCCESS** (0x00) Desempenho de byte de piscina bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="8036f-517">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-518">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-518">Allowed From</span></span>

 <span data-ttu-id="8036f-519">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-520">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-520">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-521">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-521">See Also</span></span>

- <span data-ttu-id="8036f-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-522">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8036f-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="8036f-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="8036f-530">Lista de suspensão de piscina de byte priorize</span><span class="sxs-lookup"><span data-stu-id="8036f-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-531">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8036f-532">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-532">Description</span></span>

<span data-ttu-id="8036f-533">Este serviço coloca o fio de prioridade mais elevado suspenso para memória nesta piscina na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="8036f-534">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-535">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-535">Parameters</span></span>

- <span data-ttu-id="8036f-536">**pool_ptr** Ponteiro para um bloco de controlo de piscina de memória.</span><span class="sxs-lookup"><span data-stu-id="8036f-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-537">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-537">Return Values</span></span>

- <span data-ttu-id="8036f-538">**TX_SUCCESS** (0x00) Prioridades de memória bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="8036f-539">**TX_POOL_ERROR** (0x02) Ponteiro de piscina de memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-540">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-540">Allowed From</span></span>

<span data-ttu-id="8036f-541">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-542">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-542">Preemption Possible</span></span>

<span data-ttu-id="8036f-543">No</span><span class="sxs-lookup"><span data-stu-id="8036f-543">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-544">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-544">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-545">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-545">See Also</span></span>

- <span data-ttu-id="8036f-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-546">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="8036f-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8036f-553">tx_byte_release</span></span>

<span data-ttu-id="8036f-554">Liberte bytes de volta à piscina de memória</span><span class="sxs-lookup"><span data-stu-id="8036f-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-555">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-556">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-556">Description</span></span>

<span data-ttu-id="8036f-557">Este serviço liberta uma área de memória previamente atribuída à sua piscina associada.</span><span class="sxs-lookup"><span data-stu-id="8036f-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="8036f-558">Se houver um ou mais fios suspensos à espera da memória desta piscina, cada fio suspenso é dado memória e retomado até que a memória esteja esgotada ou até que não haja mais fios suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="8036f-559">Este processo de atribuição de memória a fios suspensos começa sempre com o primeiro fio suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-560">*A aplicação deve evitar a utilização da área de memória após a sua libertação.*</span><span class="sxs-lookup"><span data-stu-id="8036f-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-561">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-561">Parameters</span></span>

- <span data-ttu-id="8036f-562">**memory_ptr** Ponteiro para a área de memória previamente atribuída.</span><span class="sxs-lookup"><span data-stu-id="8036f-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-563">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-563">Return Values</span></span>

- <span data-ttu-id="8036f-564">**TX_SUCCESS** (0x00) Libertação de memória bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="8036f-565">**TX_PTR_ERROR** (0x03) Ponteiro da área da memória inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="8036f-566">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-567">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-567">Allowed From</span></span>

<span data-ttu-id="8036f-568">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-569">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-569">Preemption Possible</span></span>

<span data-ttu-id="8036f-570">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-571">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-572">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-572">See Also</span></span>

- <span data-ttu-id="8036f-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8036f-573">tx_byte_allocate</span></span>
- <span data-ttu-id="8036f-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8036f-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="8036f-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8036f-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8036f-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8036f-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="8036f-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-580">tx_event_flags_create</span></span>

<span data-ttu-id="8036f-581">Criar grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="8036f-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-583">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-583">Description</span></span>

<span data-ttu-id="8036f-584">Este serviço cria um grupo de 32 bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="8036f-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="8036f-585">Todas as 32 bandeiras do grupo estão inicializadas a zero.</span><span class="sxs-lookup"><span data-stu-id="8036f-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="8036f-586">Cada bandeira do evento é representada por um único pedaço.</span><span class="sxs-lookup"><span data-stu-id="8036f-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-587">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-587">Parameters</span></span>

- <span data-ttu-id="8036f-588">**group_ptr** Ponteiro para um bloco de controlo de grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="8036f-589">**name_ptr** Apontando para o nome do grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-590">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-590">Return Values</span></span>

- <span data-ttu-id="8036f-591">**TX_SUCCESS** (0x00) Criação de grupo de eventos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="8036f-592">**TX_GROUP_ERROR** (0x06) Ponteiro do grupo de eventos inválidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="8036f-593">Ou o ponteiro é **NU** OU o grupo de eventos já está criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="8036f-594">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-595">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-595">Allowed From</span></span>

<span data-ttu-id="8036f-596">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-597">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-597">Preemption Possible</span></span>

<span data-ttu-id="8036f-598">No</span><span class="sxs-lookup"><span data-stu-id="8036f-598">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-599">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-600">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-600">See Also</span></span>

- <span data-ttu-id="8036f-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-602">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-606">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="8036f-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-608">tx_event_flags_delete</span></span>

<span data-ttu-id="8036f-609">Apagar grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="8036f-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-610">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-611">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-611">Description</span></span>

<span data-ttu-id="8036f-612">Este serviço elimina o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="8036f-613">Todos os fios suspensos à espera de eventos deste grupo são retomados e dado um TX_DELETED estatuto de devolução.</span><span class="sxs-lookup"><span data-stu-id="8036f-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="8036f-614">*O pedido deve garantir que um conjunto de chamadas notificantes para este grupo de bandeiras de evento seja concluído (ou desativado) antes de eliminar o grupo de bandeiras do evento. Além disso, a aplicação deve impedir a utilização futura de um grupo de bandeiras de eventos eliminado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-615">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-615">Parameters</span></span>

- <span data-ttu-id="8036f-616">**group_ptr** Ponteiro para um grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-617">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-617">Return Values</span></span>

- <span data-ttu-id="8036f-618">**TX_SUCCESS** (0x00) A eliminação de bandeiras de eventos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="8036f-619">**TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8036f-620">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-621">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-621">Allowed From</span></span>

<span data-ttu-id="8036f-622">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-623">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-623">Preemption Possible</span></span>

<span data-ttu-id="8036f-624">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-625">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-625">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-626">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-626">See Also</span></span>

- <span data-ttu-id="8036f-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-627">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-628">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-632">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="8036f-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-634">tx_event_flags_get</span></span>

<span data-ttu-id="8036f-635">Receba bandeiras de evento do grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="8036f-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-636">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-637">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-637">Description</span></span>

<span data-ttu-id="8036f-638">Este serviço recupera bandeiras de eventos do grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="8036f-639">Cada grupo de bandeiras de evento contém 32 bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="8036f-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="8036f-640">Cada bandeira é representada por um único pedaço.</span><span class="sxs-lookup"><span data-stu-id="8036f-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="8036f-641">Este serviço pode recuperar uma variedade de combinações de bandeira de evento, como selecionado pelos parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="8036f-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-642">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-642">Parameters</span></span>

- <span data-ttu-id="8036f-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-643">**group_ptr**</span></span> <br><span data-ttu-id="8036f-644">Ponteiro para um grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="8036f-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="8036f-645">**requested_flags**</span></span> <br><span data-ttu-id="8036f-646">Variável não assinada de 32 bits que representa as bandeiras de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="8036f-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-647">**get_option**</span></span> <br><span data-ttu-id="8036f-648">Especifica se são necessárias todas ou quaisquer das bandeiras de eventos solicitadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="8036f-649">Seguem-se as seguintes seleções válidas:</span><span class="sxs-lookup"><span data-stu-id="8036f-649">The following are valid selections:</span></span>

  - <span data-ttu-id="8036f-650">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="8036f-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="8036f-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="8036f-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="8036f-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8036f-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="8036f-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="8036f-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="8036f-654">A seleção de TX_AND ou TX_AND_CLEAR especifica que todas as bandeiras do evento devem estar presentes no grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="8036f-655">Selecionar TX_OR ou TX_OR_CLEAR especifica que qualquer bandeira de evento é satisfatória.</span><span class="sxs-lookup"><span data-stu-id="8036f-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="8036f-656">As bandeiras do evento que satisfaçam o pedido são apuradas (definidas para zero) se forem especificadas TX_AND_CLEAR ou TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="8036f-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="8036f-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="8036f-658">Ponteiro para o destino de onde são colocadas as bandeiras do evento recuperado.</span><span class="sxs-lookup"><span data-stu-id="8036f-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="8036f-659">Note-se que as bandeiras obtidas podem conter bandeiras que não foram solicitadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="8036f-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-660">**wait_option**</span></span>  <br><span data-ttu-id="8036f-661">Define como o serviço se comporta se as bandeiras de eventos selecionadas não estiverem definidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="8036f-662">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-663">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-664">Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="8036f-665">**TX_WAIT_FOREVER** valor de tempo limite (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que as bandeiras do evento estejam disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8036f-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="8036f-666">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera pelas bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-667">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-667">Return Values</span></span>

- <span data-ttu-id="8036f-668">**TX_SUCCESS** (0x00) Bandeiras de eventos bem-sucedidas recebem.</span><span class="sxs-lookup"><span data-stu-id="8036f-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="8036f-669">**TX_DELETED** (0x01) Grupo de bandeiras de evento foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-670">**TX_NO_EVENTS** (0x07) O Serviço não conseguiu obter os eventos especificados dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="8036f-671">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-672">**TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8036f-673">**TX_PTR_ERROR** (0x03) Ponteiro inválido para bandeiras reais do evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="8036f-674">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="8036f-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8036f-675">**TX_OPTION_ERROR** (0x08) Foi especificada a opção de opção de opção inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-676">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-676">Allowed From</span></span>

<span data-ttu-id="8036f-677">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-678">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-678">Preemption Possible</span></span>

<span data-ttu-id="8036f-679">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-680">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-680">Example</span></span>

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

<span data-ttu-id="8036f-681">**Ver Também**</span><span class="sxs-lookup"><span data-stu-id="8036f-681">**See Also**</span></span>

- <span data-ttu-id="8036f-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-682">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-687">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="8036f-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="8036f-690">Recuperar informações sobre o grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="8036f-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="8036f-691">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="8036f-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="8036f-692">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="8036f-692">**Description**</span></span>

<span data-ttu-id="8036f-693">Este serviço obtém informações sobre o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="8036f-694">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="8036f-694">**Parameters**</span></span>

- <span data-ttu-id="8036f-695">**group_ptr** Ponteiro para um bloco de controlo de grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="8036f-696">**nome** Ponteiro para o destino para o ponteiro para o nome do grupo bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="8036f-697">**current_flags** Ponteiro para destino para as bandeiras do conjunto atual no grupo de bandeiras do evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="8036f-698">**first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="8036f-699">**suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste grupo de bandeiras de evento.</span><span class="sxs-lookup"><span data-stu-id="8036f-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="8036f-700">**next_group** Ponteiro para o destino para o ponteiro do próximo grupo de bandeiras de eventos criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-701">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-702">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-702">Return Values</span></span>

- <span data-ttu-id="8036f-703">**TX_SUCCESS** (0x00) Recuperação de informação de grupo de eventos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="8036f-704">**TX_GROUP_ERROR** (0x06) Ponteiro do grupo de eventos inválidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-705">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-705">Allowed From</span></span>

<span data-ttu-id="8036f-706">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-707">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-707">Preemption Possible</span></span>

<span data-ttu-id="8036f-708">No</span><span class="sxs-lookup"><span data-stu-id="8036f-708">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-709">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-709">Example</span></span>

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
<span data-ttu-id="8036f-710">**Ver Também**</span><span class="sxs-lookup"><span data-stu-id="8036f-710">**See Also**</span></span>

- <span data-ttu-id="8036f-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-711">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-713">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-716">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="8036f-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="8036f-719">Obtenha informações de desempenho do grupo de bandeiras de eventos</span><span class="sxs-lookup"><span data-stu-id="8036f-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-720">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-721">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-721">Description</span></span>

<span data-ttu-id="8036f-722">Este serviço obtém informações de desempenho sobre o grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-723">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-724">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-724">Parameters</span></span>

- <span data-ttu-id="8036f-725">**group_ptr** Ponteiro para grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="8036f-726">**conjuntos** Ponteiro para destino para o número de bandeiras de eventos definir pedidos realizados neste grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="8036f-727">**recebe** O ponteiro para o destino para o número de bandeiras de eventos recebe pedidos realizados neste grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="8036f-728">**suspensões** O ponteiro para o destino para o número de bandeiras de eventos de thread obter suspensões neste grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="8036f-729">**intervalos** O ponteiro para o destino para o número de bandeiras do evento obtém intervalos de suspensão neste grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-730">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-731">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-731">Return Values</span></span>

- <span data-ttu-id="8036f-732">**TX_SUCCESS** (0x00) O desempenho do grupo de bandeiras de eventos bem-sucedidos obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="8036f-733">**TX_PTR_ERROR** (0x03) Inválido sinaliza o ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8036f-734">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-735">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-735">Allowed From</span></span>

<span data-ttu-id="8036f-736">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-737">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-737">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-738">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-738">See Also</span></span>

- <span data-ttu-id="8036f-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-739">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-741">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-744">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="8036f-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="8036f-747">Recuperar informações do sistema de desempenho</span><span class="sxs-lookup"><span data-stu-id="8036f-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-748">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-749">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-749">Description</span></span>

<span data-ttu-id="8036f-750">Este serviço obtém informações de desempenho sobre todos os grupos de bandeiras de eventos no sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-751">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-752">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-752">Parameters</span></span>

- <span data-ttu-id="8036f-753">**conjuntos** Ponteiro para destino para o número total de bandeiras de eventos definir pedidos realizados em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="8036f-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="8036f-754">**recebe** O ponteiro para o destino para o número total de bandeiras de eventos recebe pedidos realizados em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="8036f-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="8036f-755">**suspensões** O ponteiro para o destino para o número total de bandeiras de eventos de thread obtém suspensões em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="8036f-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="8036f-756">**intervalos** O ponteiro para o destino para o número total de bandeiras de eventos obtém intervalos de suspensão em todos os grupos.</span><span class="sxs-lookup"><span data-stu-id="8036f-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-757">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-758">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-758">Return Values</span></span>

- <span data-ttu-id="8036f-759">**TX_SUCCESS** (0x00) Desempenho do sistema de bandeiras de eventos bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="8036f-760">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="8036f-761">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-761">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-762">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-762">See Also</span></span>

- <span data-ttu-id="8036f-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-763">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-765">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-768">tx_event_flags_set</span></span>
- <span data-ttu-id="8036f-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="8036f-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-770">tx_event_flags_set</span></span>

<span data-ttu-id="8036f-771">Definir bandeiras de evento em um grupo de bandeiras de evento</span><span class="sxs-lookup"><span data-stu-id="8036f-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-772">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="8036f-773">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-773">Description</span></span>

<span data-ttu-id="8036f-774">Este serviço define ou limpa bandeiras de eventos num grupo de bandeiras de eventos, dependendo da opção definida especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="8036f-775">Todos os fios suspensos cujo pedido de bandeiras de evento é agora preenchido são retomados.</span><span class="sxs-lookup"><span data-stu-id="8036f-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-776">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-776">Parameters</span></span>

- <span data-ttu-id="8036f-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-777">**group_ptr**</span></span> <br><span data-ttu-id="8036f-778">Ponteiro para o bloco de controlo de grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="8036f-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="8036f-779">**flags_to_set**</span></span> <br><span data-ttu-id="8036f-780">Especifica as bandeiras do evento para definir ou limpar com base na opção definida selecionada.</span><span class="sxs-lookup"><span data-stu-id="8036f-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="8036f-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-781">**set_option**</span></span> <br><span data-ttu-id="8036f-782">Especifica se as bandeiras do evento especificadas são ANDed ou ORed nas atuais bandeiras do grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="8036f-783">Seguem-se as seguintes seleções válidas:</span><span class="sxs-lookup"><span data-stu-id="8036f-783">The following are valid selections:</span></span>
  - <span data-ttu-id="8036f-784">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="8036f-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="8036f-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8036f-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="8036f-786">A seleção TX_AND especifica que as bandeiras de eventos especificadas são **especadas** nas bandeiras do evento atual no grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="8036f-787">Esta opção é frequentemente usada para limpar bandeiras de eventos em um grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="8036f-788">Caso contrário, se TX_OR for especificado, as bandeiras de eventos especificadas são **ORed** com o evento atual no grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-789">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-789">Return Values</span></span>
- <span data-ttu-id="8036f-790">**TX_SUCCESS** (0x00) Conjunto de bandeiras de eventos bem-sucedidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="8036f-791">**TX_GROUP_ERROR** (0x06) Ponteiro inválido para grupo de bandeiras de eventos.</span><span class="sxs-lookup"><span data-stu-id="8036f-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="8036f-792">**TX_OPTION_ERROR** (0x08) A opção de conjunto inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-793">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-793">Preemption Possible</span></span>

<span data-ttu-id="8036f-794">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-795">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-795">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-796">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-796">See Also</span></span>

- <span data-ttu-id="8036f-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-797">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-799">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="8036f-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="8036f-805">Notifique a aplicação quando as bandeiras do evento forem definidas</span><span class="sxs-lookup"><span data-stu-id="8036f-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-806">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="8036f-807">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-807">Description</span></span>

<span data-ttu-id="8036f-808">Este serviço regista uma função de chamada de chamada de notificação que é chamada sempre que uma ou mais bandeiras de eventos são definidas no grupo de bandeiras de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="8036f-809">O processamento da chamada de notificação é definido pela</span><span class="sxs-lookup"><span data-stu-id="8036f-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-810">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-810">Parameters</span></span>
- <span data-ttu-id="8036f-811">**group_ptr** Ponteiro para grupo de bandeiras de eventos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="8036f-812">**events_set_notify** Ponteiro para as bandeiras de evento da aplicação definir função de notificação.</span><span class="sxs-lookup"><span data-stu-id="8036f-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="8036f-813">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="8036f-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-814">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-814">Return Values</span></span>

- <span data-ttu-id="8036f-815">**TX_SUCCESS** (0x00) Registo bem sucedido de bandeiras de eventos definir notificação.</span><span class="sxs-lookup"><span data-stu-id="8036f-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="8036f-816">**TX_GROUP_ERROR** (0x06) Inválido sinaliza o ponteiro do grupo.</span><span class="sxs-lookup"><span data-stu-id="8036f-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8036f-817">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="8036f-818">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-818">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-819">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-819">See Also</span></span>

- <span data-ttu-id="8036f-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8036f-820">tx_event_flags_create</span></span>
- <span data-ttu-id="8036f-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="8036f-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8036f-822">tx_event_flags_get</span></span>
- <span data-ttu-id="8036f-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8036f-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8036f-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8036f-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="8036f-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="8036f-827">tx_interrupt_control</span></span>

<span data-ttu-id="8036f-828">Ativar e desativar interrupções</span><span class="sxs-lookup"><span data-stu-id="8036f-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-829">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="8036f-830">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-830">Description</span></span>

<span data-ttu-id="8036f-831">Este serviço permite ou desativa as interrupções conforme especificado pelo parâmetro de entrada *new_posture*.</span><span class="sxs-lookup"><span data-stu-id="8036f-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-832">*Se este serviço for chamado de um fio de aplicação, a postura de interrupção permanece parte do contexto desse fio. Por exemplo, se o fio chamar esta rotina para desativar as interrupções e, em seguida, suspender, quando é retomado, as interrupções são novamente desativadas.*</span><span class="sxs-lookup"><span data-stu-id="8036f-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="8036f-833">*Este serviço não deve ser utilizado para permitir interrupções durante a inicialização! Fazê-lo pode causar resultados imprevisíveis.*</span><span class="sxs-lookup"><span data-stu-id="8036f-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-834">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-834">Parameters</span></span>

- <span data-ttu-id="8036f-835">**new_posture** Este parâmetro especifica se as interrupções são desativadas ou ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="8036f-836">Os valores legais incluem **TX_INT_DISABLE** e **TX_INT_ENABLE.**</span><span class="sxs-lookup"><span data-stu-id="8036f-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="8036f-837">Os valores reais para estes parâmetros são específicos do porto.</span><span class="sxs-lookup"><span data-stu-id="8036f-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="8036f-838">Além disso, algumas arquiteturas de processamento podem suportar posturas adicionais de interrupção de desativação.</span><span class="sxs-lookup"><span data-stu-id="8036f-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-839">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-839">Return Values</span></span>
- <span data-ttu-id="8036f-840">**postura anterior** Este serviço devolve a postura de interrupção anterior ao chamador.</span><span class="sxs-lookup"><span data-stu-id="8036f-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="8036f-841">Isto permite que os utilizadores do serviço restaurem a postura anterior após as interrupções serem desativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-842">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-842">Allowed From</span></span>

<span data-ttu-id="8036f-843">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-844">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-844">Preemption Possible</span></span>

<span data-ttu-id="8036f-845">No</span><span class="sxs-lookup"><span data-stu-id="8036f-845">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-846">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="8036f-847">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-847">See Also</span></span>

<span data-ttu-id="8036f-848">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="8036f-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-849">tx_mutex_create</span></span>

<span data-ttu-id="8036f-850">Criar mutex de exclusão mútua</span><span class="sxs-lookup"><span data-stu-id="8036f-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-851">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="8036f-852">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-852">Description</span></span>

<span data-ttu-id="8036f-853">Este serviço cria um mutex para exclusão mútua inter-roscada para proteção de recursos.</span><span class="sxs-lookup"><span data-stu-id="8036f-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-854">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-854">Parameters</span></span>

- <span data-ttu-id="8036f-855">**mutex_ptr** Ponteiro para um bloco de controlo de mutantes.</span><span class="sxs-lookup"><span data-stu-id="8036f-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="8036f-856">**name_ptr** Apontando para o nome do mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="8036f-857">**priority_inherit** Especifica se este mutex suporta ou não a herança prioritária.</span><span class="sxs-lookup"><span data-stu-id="8036f-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="8036f-858">Se este valor for TX_INHERIT, então a herança prioritária é apoiada.</span><span class="sxs-lookup"><span data-stu-id="8036f-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="8036f-859">No entanto, se TX_NO_INHERIT for especificada, a herança prioritária não é apoiada por este mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-860">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-860">Return Values</span></span>

- <span data-ttu-id="8036f-861">**TX_SUCCESS** (0x00) Criação mutex bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="8036f-862">**TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="8036f-863">Ou o ponteiro é NULO ou o mutex já está criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="8036f-864">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="8036f-865">**TX_INHERIT_ERROR** (0x1F) Parâmetro de herdade de prioridade inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-866">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-866">Allowed From</span></span>

<span data-ttu-id="8036f-867">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-868">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-868">Preemption Possible</span></span>

<span data-ttu-id="8036f-869">No</span><span class="sxs-lookup"><span data-stu-id="8036f-869">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-870">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-870">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-871">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-871">See Also</span></span>

- <span data-ttu-id="8036f-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-872">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-873">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="8036f-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-879">tx_mutex_delete</span></span>

<span data-ttu-id="8036f-880">Eliminar o mutex de exclusão mútua</span><span class="sxs-lookup"><span data-stu-id="8036f-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-881">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-882">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-882">Description</span></span>

<span data-ttu-id="8036f-883">Este serviço elimina o mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="8036f-884">Todos os fios suspensos à espera do mutex são retomados e dado um **TX_DELETED** estado de retorno.</span><span class="sxs-lookup"><span data-stu-id="8036f-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-885">*É da responsabilidade da aplicação impedir a utilização de um mutex apagado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-886">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-886">Parameters</span></span>

- <span data-ttu-id="8036f-887">**mutex_ptr** Ponteiro para um mutex criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-888">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-888">Return Values</span></span>

- <span data-ttu-id="8036f-889">**TX_SUCCESS** (0x00) Eliminação mutex bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="8036f-890">**TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8036f-891">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-892">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-892">Allowed From</span></span>

<span data-ttu-id="8036f-893">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-894">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-894">Preemption Possible</span></span>

<span data-ttu-id="8036f-895">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-896">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-897">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-897">See Also</span></span>

- <span data-ttu-id="8036f-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-898">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-899">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="8036f-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-905">tx_mutex_get</span></span>

<span data-ttu-id="8036f-906">Obter a propriedade do mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-907">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-908">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-908">Description</span></span>

<span data-ttu-id="8036f-909">Este serviço tenta obter a propriedade exclusiva do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="8036f-910">Se o fio de chamamento já possuir o mutex, um contador interno é incrementado e um estado de sucesso é devolvido.</span><span class="sxs-lookup"><span data-stu-id="8036f-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="8036f-911">Se o mutex for propriedade de outro fio e este fio for de maior prioridade e a herança prioritária foi especificada na criação de mutex, a prioridade do fio de menor prioridade será temporariamente elevada à do fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="8036f-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-912">*A prioridade do fio de menor prioridade que possui um mutex com prioridade nunca deve ser modificada por um fio externo durante a propriedade do mutex.*</span><span class="sxs-lookup"><span data-stu-id="8036f-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-913">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-913">Parameters</span></span>

- <span data-ttu-id="8036f-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="8036f-915">Ponteiro para um mutex criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="8036f-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-916">**wait_option**</span></span> <br><span data-ttu-id="8036f-917">Define como o serviço se comporta se o mutex já é propriedade de outro fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="8036f-918">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-919">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-920">*Esta é a única opção válida se o serviço for chamado da Initialization.*</span><span class="sxs-lookup"><span data-stu-id="8036f-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="8036f-921">**TX_WAIT_FOREVER** valor de tempo limite (0xFFFFFFFF) - A seleção **TX_WAIT_FOREVER** faz com que o fio de chamada suspenda indefinidamente até que o mutex esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="8036f-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="8036f-922">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera pelo mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-923">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-923">Return Values</span></span>

- <span data-ttu-id="8036f-924">**TX_SUCCESS** (0x00) Mutex bem sucedido obter operação.</span><span class="sxs-lookup"><span data-stu-id="8036f-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="8036f-925">**TX_DELETED** (0x01) Mutex foi eliminado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-926">**TX_NOT_AVAILABLE** (0x1D) O serviço não conseguiu obter a propriedade do mutex dentro do tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="8036f-927">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-928">**TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8036f-929">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="8036f-930">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-931">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-931">Allowed From</span></span>

<span data-ttu-id="8036f-932">Inicialização e fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-933">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-933">Preemption Possible</span></span>

<span data-ttu-id="8036f-934">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-935">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="8036f-936">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-936">See Also</span></span>

- <span data-ttu-id="8036f-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-937">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-938">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="8036f-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-944">tx_mutex_info_get</span></span>

<span data-ttu-id="8036f-945">Recuperar informações sobre o mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-946">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-946">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-947">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-947">Description</span></span>

<span data-ttu-id="8036f-948">Este serviço obtém informações do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-949">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-949">Parameters</span></span>

- <span data-ttu-id="8036f-950">**mutex_ptr** Ponteiro para bloco de controlo de mutantes.</span><span class="sxs-lookup"><span data-stu-id="8036f-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="8036f-951">**nome** Ponteiro para o destino para o ponteiro para o nome do mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="8036f-952">**contar** Ponteiro para o destino para a contagem de propriedade do mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="8036f-953">**proprietário** Ponteiro para destino para o ponteiro do fio próprio.</span><span class="sxs-lookup"><span data-stu-id="8036f-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="8036f-954">**first_suspended** Ponteiro para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="8036f-955">**suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="8036f-956">**next_mutex** Ponteiro para o destino para o ponteiro do próximo mutex criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-957">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-958">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-958">Return Values</span></span>

- <span data-ttu-id="8036f-959">**TX_SUCCESS** (0x00) Recuperação de informação mutex bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="8036f-960">**TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-961">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-961">Allowed From</span></span>

<span data-ttu-id="8036f-962">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-963">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-963">Preemption Possible</span></span>

<span data-ttu-id="8036f-964">No</span><span class="sxs-lookup"><span data-stu-id="8036f-964">No</span></span>

<span data-ttu-id="8036f-965">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="8036f-965">**Example**</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-966">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-966">See Also</span></span>

- <span data-ttu-id="8036f-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-967">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-968">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-969">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="8036f-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="8036f-975">Obtenha informações sobre desempenho de mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-976">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-977">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-977">Description</span></span>

<span data-ttu-id="8036f-978">Este serviço recupera informações de desempenho sobre o mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-979">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-980">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-980">Parameters</span></span>

- <span data-ttu-id="8036f-981">**mutex_ptr** Ponteiro para o mutex criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="8036f-982">**coloca** Ponteiro para o destino para o número de pedidos de colocação realizados neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="8036f-983">**recebe** Ponteiro para o destino para o número de pedidos de obter realizados neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="8036f-984">**suspensões** Ponteiro para o destino para o número de mutex thread obter suspensões neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="8036f-985">**intervalos** Ponteiro para o destino para o número de mutaxos obter intervalos de suspensão neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="8036f-986">**inversões** Ponteiro para o destino para o número de inversões prioritárias de linha neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="8036f-987">**heranças** Ponteiro para o destino para o número de operações de herança prioritária de linha neste mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-988">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-989">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-989">Return Values</span></span>

- <span data-ttu-id="8036f-990">**TX_SUCCESS** (0x00) Desempenho mutex bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="8036f-991">**TX_PTR_ERROR** (0x03) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8036f-992">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-993">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-993">Allowed From</span></span>

<span data-ttu-id="8036f-994">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-995">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-995">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-996">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-996">See Also</span></span>

- <span data-ttu-id="8036f-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-997">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-998">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-999">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="8036f-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="8036f-1005">Obtenha informações sobre desempenho do sistema mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1006">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="8036f-1007">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1007">Description</span></span>

<span data-ttu-id="8036f-1008">Este serviço obtém informações de desempenho sobre todos os mutaxos do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1009">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1010">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1010">Parameters</span></span>

- <span data-ttu-id="8036f-1011">**coloca** Ponteiro para destino para o número total de pedidos de colocação realizados em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="8036f-1012">**recebe** Ponteiro para destino para o número total de pedidos de obter realizados em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="8036f-1013">**suspensões** Ponteiro para o destino para o número total de fios mutex obter suspensões em todos os mutais.</span><span class="sxs-lookup"><span data-stu-id="8036f-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="8036f-1014">**intervalos** Ponteiro para o destino para o número total de mutantes obter intervalos de suspensão em todos os mutais.</span><span class="sxs-lookup"><span data-stu-id="8036f-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="8036f-1015">**inversões** Ponteiro para o destino para o número total de inversões prioritárias de linha em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="8036f-1016">**heranças** Ponteiro para destino para o número total de operações de herança prioritária de fio em todos os mutaxos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1017">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1018">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1018">Return Values</span></span>

- <span data-ttu-id="8036f-1019">**TX_SUCCESS** (0x00) Desempenho do sistema mutex bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="8036f-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1021">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1021">Allowed From</span></span>

<span data-ttu-id="8036f-1022">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1023">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1023">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1024">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1024">See Also</span></span>

- <span data-ttu-id="8036f-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1025">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1027">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8036f-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="8036f-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="8036f-1033">Priorizar lista de suspensão de mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1034">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1035">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1035">Description</span></span>

<span data-ttu-id="8036f-1036">Este serviço coloca o fio de prioridade mais elevado suspenso para a propriedade do mutex na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="8036f-1037">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1038">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1038">Parameters</span></span>

- <span data-ttu-id="8036f-1039">**mutex_ptr** Ponteiro para o mutex anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1040">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1040">Return Values</span></span>

- <span data-ttu-id="8036f-1041">**TX_SUCCESS** (0x00) Prioridades de mutex bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="8036f-1042">**TX_MUTEX_ERROR** (0x1C) Ponteiro mutex inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1043">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1043">Allowed From</span></span>

<span data-ttu-id="8036f-1044">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1045">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1045">Preemption Possible</span></span>

<span data-ttu-id="8036f-1046">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1047">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1047">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1048">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1048">See Also</span></span>

- <span data-ttu-id="8036f-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1049">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1051">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="8036f-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1056">tx_mutex_put</span></span>

<span data-ttu-id="8036f-1057">Libertar a propriedade do mutex</span><span class="sxs-lookup"><span data-stu-id="8036f-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1059">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1059">Description</span></span>

<span data-ttu-id="8036f-1060">Este serviço desvaloriza a contagem de propriedade do mutex especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="8036f-1061">Se a contagem de propriedade for zero, o mutex é disponibilizado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1062">*Se a herança prioritária foi selecionada durante a criação de mutaxos, a prioridade do fio de libertação será restaurada à prioridade que tinha quando obteve inicialmente a propriedade do mutex. Quaisquer outras alterações prioritárias efetuadas no fio de libertação durante a propriedade do mutex podem ser desfeitas.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1063">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1063">Parameters</span></span>
- <span data-ttu-id="8036f-1064">mutex_ptr Pointer para o mutex anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1065">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1065">Return Values</span></span>
- <span data-ttu-id="8036f-1066">**TX_SUCCESS** (0x00) Libertação de mutex bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="8036f-1067">**TX_NOT_OWNED** (0x1E) A Mutex não é propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="8036f-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="8036f-1068">**TX_MUTEX_ERROR** (0x1C) Ponteiro inválido para mutex.</span><span class="sxs-lookup"><span data-stu-id="8036f-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="8036f-1069">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1070">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1070">Allowed From</span></span>

<span data-ttu-id="8036f-1071">Inicialização e fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1072">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1072">Preemption Possible</span></span>

<span data-ttu-id="8036f-1073">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1074">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-1075">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1075">See Also</span></span>

- <span data-ttu-id="8036f-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1076">tx_mutex_create</span></span>
- <span data-ttu-id="8036f-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="8036f-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1078">tx_mutex_get</span></span>
- <span data-ttu-id="8036f-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="8036f-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8036f-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="8036f-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1083">tx_queue_create</span></span>

<span data-ttu-id="8036f-1084">Criar fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="8036f-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1085">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="8036f-1086">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1086">Description</span></span>

<span data-ttu-id="8036f-1087">Este serviço cria uma fila de mensagens que é normalmente usada para comunicação interligada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="8036f-1088">O número total de mensagens é calculado a partir do tamanho da mensagem especificada e do número total de bytes na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1089">*Se o número total de bytes especificados na área de memória da fila não for igualmente divisível pelo tamanho da mensagem especificada, os bytes restantes na área da memória não são utilizados.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1090">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1090">Parameters</span></span>

- <span data-ttu-id="8036f-1091">**queue_ptr** Ponteiro para um bloco de controlo de fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8036f-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="8036f-1092">**name_ptr** Ponteiro para o nome da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="8036f-1093">**message_size** Especifica o tamanho de cada mensagem na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="8036f-1094">Os tamanhos da mensagem variam de 1 32 bits de palavras a 16 palavras de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="8036f-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="8036f-1095">As opções de tamanho de mensagem válidas são valores numéricos de 1 a 16, inclusive.</span><span class="sxs-lookup"><span data-stu-id="8036f-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="8036f-1096">**queue_start** Endereço inicial da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="8036f-1097">O endereço inicial deve ser alinhado com o tamanho do tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="8036f-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="8036f-1098">**queue_size** Número total de bytes disponíveis para a fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1099">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1099">Return Values</span></span>

- <span data-ttu-id="8036f-1100">**TX_SUCCESS** (0x00) Criação de fila de mensagens bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="8036f-1101">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="8036f-1102">Ou o ponteiro é NU OU a fila já está criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="8036f-1103">**TX_PTR_ERROR** (0x03) Endereço inicial inválido da fila da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="8036f-1104">**TX_SIZE_ERROR** (0x05) O tamanho da fila da mensagem é inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="8036f-1105">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1106">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1106">Allowed From</span></span>

<span data-ttu-id="8036f-1107">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1108">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1108">Preemption Possible</span></span>

<span data-ttu-id="8036f-1109">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1110">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1111">See Also</span></span>

- <span data-ttu-id="8036f-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1112">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1113">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1119">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1120">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="8036f-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1122">tx_queue_delete</span></span>

<span data-ttu-id="8036f-1123">Apagar fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="8036f-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1124">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1125">Description</span></span>

<span data-ttu-id="8036f-1126">Este serviço elimina a fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="8036f-1127">Todos os fios suspensos à espera de uma mensagem desta fila são retomados e dado um estado de devolução TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="8036f-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="8036f-1128">*O pedido deve certificar-se de que qualquer pedido de notificação para esta fila está concluído (ou desativado) antes de apagar a fila. Além disso, a aplicação deve impedir qualquer utilização futura de uma fila eliminada.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="8036f-1129">*É também da responsabilidade da aplicação gerir a área de memória associada à fila, que está disponível após a conclusão deste serviço.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1130">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1130">Parameters</span></span>

- <span data-ttu-id="8036f-1131">**queue_ptr** Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1132">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1132">Return Values</span></span>

- <span data-ttu-id="8036f-1133">**TX_SUCCESS** (0x00) Eliminação da fila de mensagens bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="8036f-1134">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8036f-1135">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1136">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1136">Allowed From</span></span>

<span data-ttu-id="8036f-1137">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1138">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1138">Preemption Possible</span></span>

<span data-ttu-id="8036f-1139">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1140">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1141">See Also</span></span>

- <span data-ttu-id="8036f-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1142">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1143">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1149">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1150">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="8036f-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1152">tx_queue_flush</span></span>

<span data-ttu-id="8036f-1153">Mensagens vazias na fila da mensagem</span><span class="sxs-lookup"><span data-stu-id="8036f-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1154">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1155">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1155">Description</span></span>

<span data-ttu-id="8036f-1156">Este serviço elimina todas as mensagens armazenadas na fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="8036f-1157">Se a fila estiver cheia, as mensagens de todos os fios suspensos são descartadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="8036f-1158">Cada fio suspenso é então retomado com um estado de retorno que indica que o envio da mensagem foi bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="8036f-1159">Se a fila estiver vazia, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1160">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1160">Parameters</span></span>

- <span data-ttu-id="8036f-1161">**queue_ptr** Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1162">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1162">Return Values</span></span>

- <span data-ttu-id="8036f-1163">**TX_SUCCESS** (0x00) Mensagem de sucesso na fila da fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="8036f-1164">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1165">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1165">Allowed From</span></span>

<span data-ttu-id="8036f-1166">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1167">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1167">Preemption Possible</span></span>

<span data-ttu-id="8036f-1168">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1169">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1170">See Also</span></span>

- <span data-ttu-id="8036f-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1171">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1172">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1178">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1179">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="8036f-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1181">tx_queue_front_send</span></span>

<span data-ttu-id="8036f-1182">Enviar mensagem para a frente da fila</span><span class="sxs-lookup"><span data-stu-id="8036f-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1183">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-1184">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1184">Description</span></span>

<span data-ttu-id="8036f-1185">Este serviço envia uma mensagem para a localização frontal da fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="8036f-1186">A mensagem é **copiada** para a frente da fila a partir da área de memória especificada pelo ponteiro de origem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1187">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1187">Parameters</span></span>

- <span data-ttu-id="8036f-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1188">**queue_ptr**</span></span> <br><span data-ttu-id="8036f-1189">Ponteiro para um bloco de controlo de fila de mensagens.</span><span class="sxs-lookup"><span data-stu-id="8036f-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="8036f-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1190">**source_ptr**</span></span> <br><span data-ttu-id="8036f-1191">Ponteiro para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1191">Pointer to the message.</span></span>
- <span data-ttu-id="8036f-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-1192">**wait_option**</span></span>  <br><span data-ttu-id="8036f-1193">Define como o serviço se comporta se a fila da mensagem estiver cheia.</span><span class="sxs-lookup"><span data-stu-id="8036f-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="8036f-1194">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-1195">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-1196">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="8036f-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="8036f-1198">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1199">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1199">Return Values</span></span>

- <span data-ttu-id="8036f-1200">**TX_SUCCESS** (0x00) Envio bem sucedido de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="8036f-1201">**TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-1202">**TX_QUEUE_FULL** (0x0B) O Serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8036f-1203">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-1204">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8036f-1205">**TX_PTR_ERROR** (0x03) Ponteiro de origem inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="8036f-1206">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1207">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1207">Allowed From</span></span>

<span data-ttu-id="8036f-1208">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1209">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1209">Preemption Possible</span></span>

<span data-ttu-id="8036f-1210">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1211">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1212">See Also</span></span>

- <span data-ttu-id="8036f-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1213">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1214">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1215">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1220">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1221">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="8036f-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1223">tx_queue_info_get</span></span>

<span data-ttu-id="8036f-1224">Recuperar informações sobre a fila</span><span class="sxs-lookup"><span data-stu-id="8036f-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1225">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1225">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-1226">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1226">Description</span></span>

<span data-ttu-id="8036f-1227">Este serviço obtém informações sobre a fila de mensagens especificadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1228">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1228">Parameters</span></span>

- <span data-ttu-id="8036f-1229">**queue_ptr** Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8036f-1230">**nome** Ponteiro para o destino para o ponteiro para o nome da fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="8036f-1231">**enqueso** Ponteiro para o destino para o número de mensagens atualmente na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="8036f-1232">**available_storage** Ponteiro para destino para o número de mensagens para as recados atualmente tem espaço para.</span><span class="sxs-lookup"><span data-stu-id="8036f-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="8036f-1233">**first_suspended** Ponteiro para destino para o ponteiro para o fio que é o primeiro na lista de suspensão desta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="8036f-1234">**suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="8036f-1235">**next_queue** Ponteiro para o destino para o ponteiro da próxima fila criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1236">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1237">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1237">Return Values</span></span>

- <span data-ttu-id="8036f-1238">**TX_SUCCESS** (0x00) Informações de fila bem sucedidas obtêm.</span><span class="sxs-lookup"><span data-stu-id="8036f-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="8036f-1239">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1240">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1240">Allowed From</span></span>

<span data-ttu-id="8036f-1241">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1242">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1242">Preemption Possible</span></span>

<span data-ttu-id="8036f-1243">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1244">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1244">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1245">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1245">See Also</span></span>

- <span data-ttu-id="8036f-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1246">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1247">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1248">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1253">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1254">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="8036f-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="8036f-1257">Obtenha informações sobre desempenho da fila</span><span class="sxs-lookup"><span data-stu-id="8036f-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1258">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1258">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-1259">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1259">Description</span></span>

<span data-ttu-id="8036f-1260">Este serviço recupera informações de desempenho sobre a fila especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1261">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1262">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1262">Parameters</span></span>

- <span data-ttu-id="8036f-1263">**queue_ptr** Ponteiro para a fila previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="8036f-1264">**messages_sent** Ponteiro para destino para o número de pedidos de envio realizados nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="8036f-1265">**messages_received** Ponteiro para destino para o número de pedidos de receção realizados nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="8036f-1266">**empty_suspensions** Ponteiro para o destino para o número de suspensões vazias de fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="8036f-1267">**full_suspensions** Ponteiro para o destino para o número de suspensões completas da fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="8036f-1268">**full_errors** Ponteiro para o destino para o número de erros completos da fila nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="8036f-1269">**intervalos** Ponteiro para o destino para o número de intervalos de suspensão de fio nesta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1270">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1271">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1271">Return Values</span></span>

- <span data-ttu-id="8036f-1272">**TX_SUCCESS** (0x00) Desempenho de fila bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="8036f-1273">**TX_PTR_ERROR** (0x03) Ponteiro de fila inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="8036f-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1275">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1275">Allowed From</span></span>

<span data-ttu-id="8036f-1276">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1277">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1277">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1278">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1278">See Also</span></span>

- <span data-ttu-id="8036f-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1279">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1280">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1281">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1286">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1287">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="8036f-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="8036f-1290">Obtenha informações sobre desempenho do sistema de fila</span><span class="sxs-lookup"><span data-stu-id="8036f-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1291">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-1292">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1292">Description</span></span>

<span data-ttu-id="8036f-1293">Este serviço obtém informações de desempenho sobre todas as filas do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1294">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1295">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1295">Parameters</span></span>

- <span data-ttu-id="8036f-1296">**messages_sent** Ponteiro para destino para o número total de pedidos de envio realizados em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="8036f-1297">**messages_received** Ponteiro para destino para o número total de pedidos de receção realizados em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="8036f-1298">**empty_suspensions** Ponteiro para o destino para o número total de suspensões vazias de fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="8036f-1299">**full_suspensions** Ponteiro para o destino para o número total de suspensões completas da fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="8036f-1300">**full_errors** Ponteiro para o destino para o número total de erros completos da fila em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="8036f-1301">**intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio em todas as filas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1302">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="8036f-1303">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="8036f-1303">**Return Values**</span></span>

- <span data-ttu-id="8036f-1304">**TX_SUCCESS** (0x00) Desempenho do sistema de fila bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="8036f-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1306">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1306">Allowed From</span></span>

<span data-ttu-id="8036f-1307">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1308">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1308">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1309">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1309">See Also</span></span>

- <span data-ttu-id="8036f-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1310">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1311">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1312">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1317">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1318">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="8036f-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="8036f-1321">Priorizar lista de suspensão de filas</span><span class="sxs-lookup"><span data-stu-id="8036f-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1322">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1323">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1323">Description</span></span>

<span data-ttu-id="8036f-1324">Este serviço coloca o fio de prioridade mais elevado suspenso para uma mensagem (ou para colocar uma mensagem) nesta fila na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="8036f-1325">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1326">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1326">Parameters</span></span>

- <span data-ttu-id="8036f-1327">**queue_ptr** Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1328">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1328">Return Values</span></span>

- <span data-ttu-id="8036f-1329">**TX_SUCCESS** (0x00) Prioridades de fila bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="8036f-1330">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1331">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1331">Allowed From</span></span>

<span data-ttu-id="8036f-1332">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1333">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1333">Preemption Possible</span></span>

<span data-ttu-id="8036f-1334">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1335">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1335">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1336">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1336">See Also</span></span>

- <span data-ttu-id="8036f-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1337">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1338">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1339">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1344">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1345">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="8036f-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1347">tx_queue_receive</span></span>

<span data-ttu-id="8036f-1348">Receba mensagem da fila da mensagem</span><span class="sxs-lookup"><span data-stu-id="8036f-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1349">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-1350">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1350">Description</span></span>

<span data-ttu-id="8036f-1351">Este serviço recupera uma mensagem da fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="8036f-1352">A mensagem recuperada é **copiada** da fila para a área de memória especificada pelo ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="8036f-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="8036f-1353">Essa mensagem é então removida da fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1354">*A área de memória de destino especificada deve ser suficientemente grande para conter a mensagem; ou seja, o destino da mensagem apontado por*  \* **destination_ptr** _ _must ser pelo menos tão grande quanto o tamanho da mensagem para esta fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="8036f-1355">Caso contrário, se o destino não for suficientemente grande, a corrupção da memória ocorre na seguinte área de memória.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1356">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1356">Parameters</span></span>

- <span data-ttu-id="8036f-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1357">**queue_ptr**</span></span> <br><span data-ttu-id="8036f-1358">Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8036f-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1359">**destination_ptr**</span></span> <br><span data-ttu-id="8036f-1360">Localização de onde copiar a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="8036f-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-1361">**wait_option**</span></span> <br><span data-ttu-id="8036f-1362">Define como o serviço se comporta se a fila da mensagem estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="8036f-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="8036f-1363">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-1364">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-1365">Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="8036f-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção de TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que uma mensagem esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="8036f-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="8036f-1367">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1368">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1368">Return Values</span></span>

- <span data-ttu-id="8036f-1369">**TX_SUCCESS** (0x00) Recuperação bem sucedida da mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="8036f-1370">**TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-1371">**TX_QUEUE_EMPTY** (0x0A) O Serviço não conseguiu recuperar uma mensagem porque a fila estava vazia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8036f-1372">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-1373">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8036f-1374">**TX_PTR_ERROR** (0x03) Ponteiro de destino inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="8036f-1375">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="8036f-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1376">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1376">Allowed From</span></span>

<span data-ttu-id="8036f-1377">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1378">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1378">Preemption Possible</span></span>

<span data-ttu-id="8036f-1379">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1380">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1380">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1381">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1381">See Also</span></span>

- <span data-ttu-id="8036f-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1382">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1383">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1384">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1390">tx_queue_send</span></span>
- <span data-ttu-id="8036f-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="8036f-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1392">tx_queue_send</span></span>

<span data-ttu-id="8036f-1393">Enviar mensagem para a fila de mensagens</span><span class="sxs-lookup"><span data-stu-id="8036f-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1394">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-1395">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1395">Description</span></span>

<span data-ttu-id="8036f-1396">Este serviço envia uma mensagem para a fila de mensagens especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="8036f-1397">A mensagem enviada é **copiada** para a fila a partir da área de memória especificada pelo ponteiro de origem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1398">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1398">Parameters</span></span>
- <span data-ttu-id="8036f-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1399">**queue_ptr**</span></span> <br><span data-ttu-id="8036f-1400">Ponteiro para uma fila de mensagens previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8036f-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1401">**source_ptr**</span></span> <br><span data-ttu-id="8036f-1402">Ponteiro para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1402">Pointer to the message.</span></span>
- <span data-ttu-id="8036f-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-1403">**wait_option**</span></span> <br><span data-ttu-id="8036f-1404">Define como o serviço se comporta se a fila da mensagem estiver cheia.</span><span class="sxs-lookup"><span data-stu-id="8036f-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="8036f-1405">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-1406">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-1407">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, Inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="8036f-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que haja espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="8036f-1409">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto espera por espaço na fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1410">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1410">Return Values</span></span>

- <span data-ttu-id="8036f-1411">**TX_SUCCESS** (0x00) Envio bem sucedido de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="8036f-1412">**TX_DELETED** (0x01) A fila da mensagem foi apagada enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-1413">**TX_QUEUE_FULL** (0x0B) O Serviço não pôde enviar mensagem porque a fila estava cheia durante o tempo especificado para esperar.</span><span class="sxs-lookup"><span data-stu-id="8036f-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8036f-1414">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-1415">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila de mensagens inválidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8036f-1416">**TX_PTR_ERROR** (0x03) Ponteiro de origem inválido para mensagem.</span><span class="sxs-lookup"><span data-stu-id="8036f-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="8036f-1417">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de uma não-leitura.</span><span class="sxs-lookup"><span data-stu-id="8036f-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1418">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1418">Allowed From</span></span>

<span data-ttu-id="8036f-1419">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1420">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1420">Preemption Possible</span></span>

<span data-ttu-id="8036f-1421">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1422">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1422">Example</span></span>

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

<span data-ttu-id="8036f-1423">**Ver Também**</span><span class="sxs-lookup"><span data-stu-id="8036f-1423">**See Also**</span></span>

- <span data-ttu-id="8036f-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1424">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1425">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1426">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1432">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="8036f-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="8036f-1435">Notifique o pedido quando a mensagem é enviada para a fila</span><span class="sxs-lookup"><span data-stu-id="8036f-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1436">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="8036f-1437">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1437">Description</span></span>

<span data-ttu-id="8036f-1438">Este serviço regista uma função de chamada de notificação que é chamada sempre que uma mensagem é enviada para a fila especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="8036f-1439">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="8036f-1440">*A chamada de notificação de envio de fila da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1441">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1441">Parameters</span></span>

- <span data-ttu-id="8036f-1442">**queue_ptr** Ponteiro para a fila previamente criada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="8036f-1443">**queue_send_notify** Ponteiro para a função de notificação de envio de fila da aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="8036f-1444">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1445">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1445">Return Values</span></span>

- <span data-ttu-id="8036f-1446">**TX_SUCCESS** (0x00) Registo bem sucedido da notificação de envio de fila.</span><span class="sxs-lookup"><span data-stu-id="8036f-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="8036f-1447">**TX_QUEUE_ERROR** (0x09) Ponteiro de fila inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="8036f-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1449">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1449">Allowed From</span></span>

<span data-ttu-id="8036f-1450">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1451">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1451">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1452">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1452">See Also</span></span>

- <span data-ttu-id="8036f-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1453">tx_queue_create</span></span>
- <span data-ttu-id="8036f-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1454">tx_queue_delete</span></span>
- <span data-ttu-id="8036f-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8036f-1455">tx_queue_flush</span></span>
- <span data-ttu-id="8036f-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="8036f-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="8036f-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8036f-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="8036f-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8036f-1461">tx_queue_receive</span></span>
- <span data-ttu-id="8036f-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8036f-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="8036f-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="8036f-1464">Coloque um caso na contagem de semáforos com teto</span><span class="sxs-lookup"><span data-stu-id="8036f-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1465">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="8036f-1466">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1466">Description</span></span>

<span data-ttu-id="8036f-1467">Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um.</span><span class="sxs-lookup"><span data-stu-id="8036f-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="8036f-1468">Se o valor atual do semáforo de contagem for superior ou igual ao teto especificado, o caso não será colocado e será devolvido um erro de TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="8036f-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1469">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1469">Parameters</span></span>

- <span data-ttu-id="8036f-1470">**semaphore_ptr** Ponteiro para semáforo criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="8036f-1471">**teto** Limite máximo permitido para o semáforo (valores válidos variam de 1 a 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="8036f-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1472">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1472">Return Values</span></span>

- <span data-ttu-id="8036f-1473">**TX_SUCCESS (0x00)** Teto de semáforo bem sucedido colocado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="8036f-1474">**TX_CEILING_EXCEEDED** (0x21) O pedido de colocação excede o limite máximo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="8036f-1475">**TX_INVALID_CEILING** (0x22) Foi fornecido um valor inválido de zero para o teto.</span><span class="sxs-lookup"><span data-stu-id="8036f-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="8036f-1476">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1477">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1477">Allowed From</span></span>

<span data-ttu-id="8036f-1478">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1479">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-1480">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1480">See Also</span></span>

- <span data-ttu-id="8036f-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="8036f-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1490">tx_semaphore_create</span></span>

<span data-ttu-id="8036f-1491">Criar semáforo de contagem</span><span class="sxs-lookup"><span data-stu-id="8036f-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1492">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="8036f-1493">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1493">Description</span></span>

<span data-ttu-id="8036f-1494">Este serviço cria um semáforo de contagem para sincronização inter-thread.</span><span class="sxs-lookup"><span data-stu-id="8036f-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="8036f-1495">A contagem inicial de semáforos é especificada como um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1496">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1496">Parameters</span></span>

- <span data-ttu-id="8036f-1497">**semaphore_ptr** Ponteiro para um bloco de controlo de semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="8036f-1498">**name_ptr** Apontando para o nome do semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="8036f-1499">**initial_count** Especifica a contagem inicial para este semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="8036f-1500">Os valores legais vão de 0x00000000 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1501">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1501">Return Values</span></span>

- <span data-ttu-id="8036f-1502">**TX_SUCCESS** (0x00) Criação de semáforos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="8036f-1503">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="8036f-1504">Ou o ponteiro é NU OU o semáforo já está criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="8036f-1505">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1506">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1506">Allowed From</span></span>

<span data-ttu-id="8036f-1507">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1508">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1508">Preemption Possible</span></span>

<span data-ttu-id="8036f-1509">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1510">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1510">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1511">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1511">See Also</span></span>

- <span data-ttu-id="8036f-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="8036f-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="8036f-1522">Eliminar semáforo de contagem</span><span class="sxs-lookup"><span data-stu-id="8036f-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1523">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1524">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1524">Description</span></span>

<span data-ttu-id="8036f-1525">Este serviço elimina o semáforo de contagem especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="8036f-1526">Todos os fios suspensos à espera de uma instância de semáforo são retomados e dado um estado de retorno TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="8036f-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1527">*O pedido deve assegurar-se de que uma chamada de notificação colocada para este semáforo seja concluída (ou desativada) antes de eliminar o semáforo. Além disso, o pedido deve impedir qualquer utilização futura de um semáforo eliminado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1528">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1528">Parameters</span></span>

- <span data-ttu-id="8036f-1529">**semaphore_ptr** Ponteiro para um semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1530">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1530">Return Values</span></span>

- <span data-ttu-id="8036f-1531">**TX_SUCCESS** (0x00) Eliminação de semaphores de contagem bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="8036f-1532">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="8036f-1533">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1534">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1534">Allowed From</span></span>

<span data-ttu-id="8036f-1535">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1536">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1536">Preemption Possible</span></span>

<span data-ttu-id="8036f-1537">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1538">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="8036f-1539">**Ver Também**</span><span class="sxs-lookup"><span data-stu-id="8036f-1539">**See Also**</span></span>

- <span data-ttu-id="8036f-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="8036f-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1549">tx_semaphore_get</span></span>

<span data-ttu-id="8036f-1550">Obtenha o exemplo da contagem de semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1551">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="8036f-1552">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1552">Description</span></span>

<span data-ttu-id="8036f-1553">Este serviço recupera uma instância (uma contagem única) do semáforo de contagem especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="8036f-1554">Como resultado, a contagem de semáforos especificados é diminuída por um.</span><span class="sxs-lookup"><span data-stu-id="8036f-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1555">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1555">Parameters</span></span>

- <span data-ttu-id="8036f-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="8036f-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="8036f-1557">Ponteiro para um semáforo de contagem previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="8036f-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="8036f-1558">**wait_option**</span></span> <br><span data-ttu-id="8036f-1559">Define como o serviço se comporta se não houver casos do semáforo disponível; ou seja, a contagem de semáforos é zero.</span><span class="sxs-lookup"><span data-stu-id="8036f-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="8036f-1560">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8036f-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="8036f-1561">**TX_NO_WAIT** (0x00000000) - A seleção TX_NO_WAIT resulta num retorno imediato deste serviço, independentemente de ter sido ou não bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8036f-1562">*Esta é a única opção válida se o serviço for chamado de uma não linha; por exemplo, inicialização, temporizador ou ISR.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="8036f-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - A seleção de TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que esteja disponível um caso de semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="8036f-1564">Valor de tempo limite (0x00000001 através de 0xFFFFFFFE) - Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda por uma instância de semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1565">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1565">Return Values</span></span>

- <span data-ttu-id="8036f-1566">**TX_SUCCESS** (0x00) Recuperação bem sucedida de um caso de semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="8036f-1567">**TX_DELETED** (0x01) O semáforo de contagem foi apagado enquanto o fio foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8036f-1568">**TX_NO_INSTANCE** (0x0D) O serviço não conseguiu recuperar um caso do semáforo de contagem (a contagem de semáforos é zero dentro do tempo especificado para esperar).</span><span class="sxs-lookup"><span data-stu-id="8036f-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="8036f-1569">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-1570">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="8036f-1571">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1572">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1572">Allowed From</span></span>

<span data-ttu-id="8036f-1573">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1574">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1574">Preemption Possible</span></span>

<span data-ttu-id="8036f-1575">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1576">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1576">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1577">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1577">See Also</span></span>

- <span data-ttu-id="8036f-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="8036f-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="8036f-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="8036f-1587">Recuperar informações sobre semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1588">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="8036f-1589">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1589">Description</span></span>

<span data-ttu-id="8036f-1590">Este serviço obtém informações sobre o semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1591">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1591">Parameters</span></span>

- <span data-ttu-id="8036f-1592">**semaphore_ptr** Ponteiro para o bloco de controlo de semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="8036f-1593">**nome** Ponteiro para o destino para o ponteiro para o nome do semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="8036f-1594">**current_value** Ponteiro para o destino para a contagem atual do semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="8036f-1595">**first_suspended** Ponteiro para o destino para o ponteiro para o fio que é o primeiro na lista de suspensão deste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="8036f-1596">**suspended_count** Ponteiro para o destino para o número de fios atualmente suspensos neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="8036f-1597">**next_semaphore** Ponteiro para o destino para o ponteiro do próximo semáforo criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1598">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1599">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1599">Return Values</span></span>

- <span data-ttu-id="8036f-1600">**TX_SUCCESS** (0x00) recuperação de informações.</span><span class="sxs-lookup"><span data-stu-id="8036f-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="8036f-1601">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1602">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1602">Allowed From</span></span>

<span data-ttu-id="8036f-1603">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1604">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1604">Preemption Possible</span></span>

<span data-ttu-id="8036f-1605">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1606">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1606">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1607">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1607">See Also</span></span>

- <span data-ttu-id="8036f-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="8036f-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="8036f-1618">Obtenha informações de desempenho de semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1619">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-1620">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1620">Description</span></span>

<span data-ttu-id="8036f-1621">Este serviço recupera informações de desempenho sobre o semáforo especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1622">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="8036f-1623">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="8036f-1623">**Parameters**</span></span>

-  <span data-ttu-id="8036f-1624">**semaphore_ptr** Ponteiro para semáforo criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="8036f-1625">**coloca** Ponteiro para destino para o número de pedidos de colocação realizados neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="8036f-1626">**recebe** Ponteiro para destino para o número de pedidos de obter realizados neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="8036f-1627">**suspensões** Ponteiro para o destino para o número de suspensões de fio neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="8036f-1628">**intervalos** Ponteiro para o destino para o número de intervalos de suspensão de fio neste semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1629">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1630">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1630">Return Values</span></span>

- <span data-ttu-id="8036f-1631">**TX_SUCCESS** (0x00) Desempenho do semáforo bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="8036f-1632">**TX_PTR_ERROR** (0x03) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="8036f-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1634">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1634">Allowed From</span></span>

<span data-ttu-id="8036f-1635">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1636">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1636">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1637">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1637">See Also</span></span>

- <span data-ttu-id="8036f-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="8036f-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="8036f-1648">Obtenha informações sobre desempenho do sistema de semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1649">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="8036f-1650">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1650">Description</span></span>

<span data-ttu-id="8036f-1651">Este serviço obtém informações de desempenho sobre todos os semáforos do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1652">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações sobre o desempenho\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1653">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1653">Parameters</span></span>

- <span data-ttu-id="8036f-1654">**coloca** Ponteiro para destino para o número total de pedidos de colocação realizados em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="8036f-1655">**recebe** Ponteiro para destino para o número total de pedidos de obter realizados em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="8036f-1656">**suspensões** Ponteiro para o destino para o número total de suspensões de fio em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="8036f-1657">**intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio em todos os semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1658">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1659">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1659">Return Values</span></span>

- <span data-ttu-id="8036f-1660">**TX_SUCCESS** (0x00) desempenho do sistema obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="8036f-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1662">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1662">Allowed From</span></span>

<span data-ttu-id="8036f-1663">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1664">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1664">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1665">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1665">See Also</span></span>

- <span data-ttu-id="8036f-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="8036f-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="8036f-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="8036f-1676">Priorizar lista de suspensão de semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1677">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1678">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1678">Description</span></span>

<span data-ttu-id="8036f-1679">Este serviço coloca o fio de prioridade mais elevado suspenso por uma instância do semáforo na parte da frente da lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="8036f-1680">Todos os outros fios permanecem na mesma ordem FIFO em que foram suspensos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1681">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1681">Parameters</span></span>

- <span data-ttu-id="8036f-1682">**semaphore_ptr** Ponteiro para um semáforo previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1683">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1683">Return Values</span></span>

- <span data-ttu-id="8036f-1684">**TX_SUCCESS** (0x00) Prioridades de semáforos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="8036f-1685">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1686">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1686">Allowed From</span></span>

<span data-ttu-id="8036f-1687">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1688">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1688">Preemption Possible</span></span>

<span data-ttu-id="8036f-1689">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1690">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1690">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1691">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1691">See Also</span></span>

- <span data-ttu-id="8036f-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="8036f-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1697">tx_semaphore_put</span></span>

<span data-ttu-id="8036f-1698">Coloque um caso na contagem de semáforos</span><span class="sxs-lookup"><span data-stu-id="8036f-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1699">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1700">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1700">Description</span></span>

<span data-ttu-id="8036f-1701">Este serviço coloca uma instância no semáforo de contagem especificado, que na realidade incrementa o semáforo de contagem por um.</span><span class="sxs-lookup"><span data-stu-id="8036f-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1702">*Se este serviço for chamado quando o semáforo for todos (OxFFFFFFFF), a nova operação de colocação fará com que o semáforo seja reposto a zero.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1703">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1703">Parameters</span></span>

- <span data-ttu-id="8036f-1704">**semaphore_ptr** Ponteiro para o bloco de controlo de semáforos previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1705">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1705">Return Values</span></span>

- <span data-ttu-id="8036f-1706">**TX_SUCCESS** (0x00) Semaphore bem sucedido colocado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="8036f-1707">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro inválido para contar semáforo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1708">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1708">Allowed From</span></span>

<span data-ttu-id="8036f-1709">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1710">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1710">Preemption Possible</span></span>

<span data-ttu-id="8036f-1711">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1712">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-1713">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1713">See Also</span></span>

- <span data-ttu-id="8036f-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="8036f-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="8036f-1724">Notificar o pedido quando o semáforo for colocado</span><span class="sxs-lookup"><span data-stu-id="8036f-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1725">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="8036f-1726">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1726">Description</span></span>

<span data-ttu-id="8036f-1727">Este serviço regista uma função de chamada de notificação que é chamada sempre que o semáforo especificado é colocado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="8036f-1728">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1729">*A chamada de notificação de semáforo da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1730">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1730">Parameters</span></span>

- <span data-ttu-id="8036f-1731">**semaphore_ptr** Ponteiro para semáforo criado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8036f-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="8036f-1732">**semaphore_put_notify** Ponteiro para o semáforo da aplicação colocar função de notificação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="8036f-1733">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1734">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1734">Return Values</span></span>

- <span data-ttu-id="8036f-1735">**TX_SUCCESS** (0x00) Registo bem sucedido da notificação de semáforos.</span><span class="sxs-lookup"><span data-stu-id="8036f-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="8036f-1736">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semáforo inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="8036f-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1738">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1738">Allowed From</span></span>

<span data-ttu-id="8036f-1739">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1740">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1740">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1741">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1741">See Also</span></span>

- <span data-ttu-id="8036f-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8036f-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="8036f-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="8036f-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="8036f-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8036f-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8036f-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8036f-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8036f-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8036f-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="8036f-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1751">tx_thread_create</span></span>

<span data-ttu-id="8036f-1752">Criar linha de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1753">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1753">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-1754">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1754">Description</span></span>

<span data-ttu-id="8036f-1755">Este serviço cria um fio de aplicação que inicia a execução na função de entrada de tarefa especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="8036f-1756">A pilha, prioridade, limiar de pré-escamação e corte de tempo estão entre os atributos especificados pelos parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="8036f-1757">Além disso, o estado de execução inicial do fio também é especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="8036f-1758">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="8036f-1758">**Parameters**</span></span>

- <span data-ttu-id="8036f-1759">**thread_ptr** Ponteiro para um bloco de controlo de rosca.</span><span class="sxs-lookup"><span data-stu-id="8036f-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="8036f-1760">**name_ptr** Ponteiro para o nome do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="8036f-1761">**entry_function** Especifica a função C inicial para a execução do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="8036f-1762">Quando um fio regressa desta função de entrada, é colocado num estado *completo* e suspenso indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="8036f-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="8036f-1763">**entry_input** Um valor de 32 bits que é passado para a função de entrada do fio quando executa pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="8036f-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="8036f-1764">A utilização para esta entrada é determinada exclusivamente pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="8036f-1765">**stack_start** Endereço inicial da área de memória da pilha.</span><span class="sxs-lookup"><span data-stu-id="8036f-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="8036f-1766">**stack_size** Bytes de números na área de memória da pilha.</span><span class="sxs-lookup"><span data-stu-id="8036f-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="8036f-1767">A área da pilha do fio deve ser grande o suficiente para lidar com a sua pior função de nidificação de chamadas e uso variável local.</span><span class="sxs-lookup"><span data-stu-id="8036f-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="8036f-1768">**prioridade** Prioridade numérica do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="8036f-1769">Os valores legais variam entre 0 e TX_MAX_PRIORITES-1, onde o valor de 0 representa a maior prioridade.</span><span class="sxs-lookup"><span data-stu-id="8036f-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="8036f-1770">**preempt_threshold** Nível de prioridade mais elevado (0 a TX_MAX_PRIORITIES-1)) de pré-incapacidade.</span><span class="sxs-lookup"><span data-stu-id="8036f-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="8036f-1771">Apenas prioridades superiores a este nível são permitidas para antecipar este fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="8036f-1772">Este valor deve ser inferior ou igual à prioridade especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="8036f-1773">Um valor igual à prioridade do fio desativa o limiar de pré-substituição.</span><span class="sxs-lookup"><span data-stu-id="8036f-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="8036f-1774">**time_slice** O número de carraças-temporizador deste fio é permitido funcionar antes que outros fios prontos da mesma prioridade sejam autorizados a correr.</span><span class="sxs-lookup"><span data-stu-id="8036f-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="8036f-1775">Note que a utilização do limiar de pré-substituição desativa o corte de tempo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="8036f-1776">Os valores legais de corte de tempo variam de 1 a 0xFFFFFFFF (inclusive).</span><span class="sxs-lookup"><span data-stu-id="8036f-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="8036f-1777">Um valor de **TX_NO_TIME_SLICE** (um valor de 0) desativa o corte de tempo deste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8036f-1778">*A utilização de corte de tempo resulta numa ligeira quantidade de sobrecarga do sistema.   Uma vez que o corte de tempo só é útil nos casos em que múltiplos fios partilham a mesma prioridade, os fios que têm uma prioridade única não devem ser atribuídos a uma fatia de tempo.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="8036f-1779">**auto_start** Especifica se o fio começa imediatamente ou se é colocado num estado suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="8036f-1780">As opções legais são **TX_AUTO_START** (0x01) e **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8036f-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="8036f-1781">Se TX_DONT_START for especificado, o pedido deve ligar mais tarde tx_thread_resume para que o fio seja executado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1782">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1782">Return Values</span></span>

- <span data-ttu-id="8036f-1783">**TX_SUCCESS** (0x00) Criação de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="8036f-1784">**TX_THREAD_ERROR** (0x0E) Ponteiro de controlo de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="8036f-1785">Ou o ponteiro é NULO ou o fio já está criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="8036f-1786">**TX_PTR_ERROR** (0x03) Endereço inicial inválido do ponto de entrada ou da área da pilha é inválido, normalmente NULO.</span><span class="sxs-lookup"><span data-stu-id="8036f-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="8036f-1787">**TX_SIZE_ERROR** (0x05) O tamanho da área da pilha é inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="8036f-1788">Os fios devem ter pelo menos **TX_MINIMUM_STACK** bytes para executar.</span><span class="sxs-lookup"><span data-stu-id="8036f-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="8036f-1789">**TX_PRIORITY_ERROR** (0x0F) Prioridade do fio inválido, que é um valor fora do intervalo de (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8036f-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8036f-1790">**TX_THRESH_ERROR** (0x18) Retenção de preempção inválida especificada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="8036f-1791">Este valor deve ser uma prioridade válida inferior ou igual à prioridade inicial do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="8036f-1792">**TX_START_ERROR** (0x10) Seleção de arranque automático inválida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="8036f-1793">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1794">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1794">Allowed From</span></span>

<span data-ttu-id="8036f-1795">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1796">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1796">Preemption Possible</span></span>

<span data-ttu-id="8036f-1797">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1798">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1798">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1799">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1799">See Also</span></span>

- <span data-ttu-id="8036f-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1800">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-1802">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-1809">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-1810">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="8036f-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1817">tx_thread_delete</span></span>

<span data-ttu-id="8036f-1818">Eliminar o fio da aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1819">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-1820">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1820">Description</span></span>

<span data-ttu-id="8036f-1821">Este serviço elimina o fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="8036f-1822">Uma vez que o fio especificado deve estar num estado encerrado ou concluído, este serviço não pode ser chamado de um fio que tenta apagar-se.</span><span class="sxs-lookup"><span data-stu-id="8036f-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1823">*É da responsabilidade da aplicação gerir a área de memória associada à pilha do fio, que está disponível após a conclusão deste serviço. Além disso, a aplicação deve impedir a utilização de um fio eliminado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1824">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1824">Parameters</span></span>

- <span data-ttu-id="8036f-1825">**thread_ptr** Ponteiro para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1826">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1826">Return Values</span></span>

- <span data-ttu-id="8036f-1827">**TX_SUCCESS** (0x00) Eliminação de rosca bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="8036f-1828">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-1829">**TX_DELETE_ERROR** (0x11) O fio especificado não se encontra num estado encerrado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="8036f-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="8036f-1830">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1831">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1831">Allowed From</span></span>

<span data-ttu-id="8036f-1832">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1833">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1833">Preemption Possible</span></span>

<span data-ttu-id="8036f-1834">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1835">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1835">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1836">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1836">See Also</span></span>

- <span data-ttu-id="8036f-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1837">tx_thread_create</span></span>
- <span data-ttu-id="8036f-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-1839">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-1846">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-1847">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="8036f-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="8036f-1855">Notificar o pedido após a entrada e saída do fio</span><span class="sxs-lookup"><span data-stu-id="8036f-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1856">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="8036f-1857">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1857">Description</span></span>

<span data-ttu-id="8036f-1858">Este serviço regista uma função de chamada de notificação que é chamada sempre que o fio especificado é introduzido ou sai.</span><span class="sxs-lookup"><span data-stu-id="8036f-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="8036f-1859">O processamento da chamada de notificação é definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1860">A chamada de notificação de entrada/saída da aplicação não está autorizada a ligar para qualquer API ThreadX com uma opção de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1861">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1861">Parameters</span></span>

- <span data-ttu-id="8036f-1862">**thread_ptr** Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="8036f-1863">**entry_exit_notify** Ponteiro para a função de notificação de entrada/saída da aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="8036f-1864">O segundo parâmetro da função de notificação de entrada/saída designa se estiver presente uma entrada ou saída.</span><span class="sxs-lookup"><span data-stu-id="8036f-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="8036f-1865">O valor **TX_THREAD_ENTRY** (0x00) indica que o fio foi introduzido, enquanto o valor **TX_THREAD_EXIT** (0x01) indica que o fio foi saído.</span><span class="sxs-lookup"><span data-stu-id="8036f-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="8036f-1866">Se este valor for **TX_NULL,** a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="8036f-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1867">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1867">Return Values</span></span>

- <span data-ttu-id="8036f-1868">**TX_SUCCESS** (0x00) Registo bem sucedido da função de notificação de entrada/saída do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="8036f-1869">**TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="8036f-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema foi compilado com capacidades de notificação desativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1871">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1871">Allowed From</span></span>

<span data-ttu-id="8036f-1872">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1873">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1873">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1874">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1874">See Also</span></span>

- <span data-ttu-id="8036f-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1875">tx_thread_create</span></span>
- <span data-ttu-id="8036f-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1876">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-1878">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-1885">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-1886">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="8036f-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-1893">tx_thread_identify</span></span>

<span data-ttu-id="8036f-1894">Recupera o ponteiro para a atual execução do fio</span><span class="sxs-lookup"><span data-stu-id="8036f-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1895">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="8036f-1896">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1896">Description</span></span>

<span data-ttu-id="8036f-1897">Este serviço devolve um ponteiro ao fio atualmente executado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="8036f-1898">Se não houver fio, este serviço devolve um ponteiro nulo.</span><span class="sxs-lookup"><span data-stu-id="8036f-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1899">*Se este serviço for chamado de um ISR, o valor de retorno representa o fio em execução antes do manipulador de interrupção de execução.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1900">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1900">Parameters</span></span>

<span data-ttu-id="8036f-1901">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="8036f-1902">Valores retuen</span><span class="sxs-lookup"><span data-stu-id="8036f-1902">Retuen Values</span></span>

- <span data-ttu-id="8036f-1903">**ponteiro de fio** Ponteiro para o fio de execução atual.</span><span class="sxs-lookup"><span data-stu-id="8036f-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="8036f-1904">Se não houver fio, o valor de retorno é **TX_NULL**.</span><span class="sxs-lookup"><span data-stu-id="8036f-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1905">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1905">Allowed From</span></span>

<span data-ttu-id="8036f-1906">Fios e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1907">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1907">Preemption Possible</span></span>

<span data-ttu-id="8036f-1908">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1909">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1909">Example</span></span>

<span data-ttu-id="8036f-1910">TX_THREAD \*my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="8036f-1910">TX_THREAD \*my_thread_ptr;</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1911">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1911">See Also</span></span>

- <span data-ttu-id="8036f-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1912">tx_thread_create</span></span>
- <span data-ttu-id="8036f-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1913">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-1921">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-1922">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="8036f-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1929">tx_thread_info_get</span></span>

<span data-ttu-id="8036f-1930">Recuperar informações sobre o fio</span><span class="sxs-lookup"><span data-stu-id="8036f-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1931">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1931">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-1932">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1932">Description</span></span>

<span data-ttu-id="8036f-1933">Este serviço recupera informações sobre o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1934">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1934">Parameters</span></span>
- <span data-ttu-id="8036f-1935">**thread_ptr** Ponteiro para o bloco de controlo de roscar.</span><span class="sxs-lookup"><span data-stu-id="8036f-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="8036f-1936">**nome** Ponteiro para o destino para o ponteiro para o nome do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="8036f-1937">**estado** Ponteiro para o destino para o estado de execução atual do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="8036f-1938">Os valores possíveis são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="8036f-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="8036f-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="8036f-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="8036f-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="8036f-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="8036f-1941">**TX_TERMINATED** (0x02)</span><span class="sxs-lookup"><span data-stu-id="8036f-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="8036f-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="8036f-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="8036f-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="8036f-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="8036f-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="8036f-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="8036f-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="8036f-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="8036f-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="8036f-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="8036f-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="8036f-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="8036f-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="8036f-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="8036f-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="8036f-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="8036f-1950">**run_count** Ponteiro para destino para a contagem de corridas do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="8036f-1951">**prioridade** Ponteiro para o destino para a prioridade do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="8036f-1952">**preemption_threshold** Ponteiro para destino para o limiar de pré-deempação do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="8036f-1953">**time_slice** Ponteiro para o destino para a fatia de tempo do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="8036f-1954">**next_thread** Ponteiro para destino para o próximo ponteiro de linha criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="8036f-1955">**suspended_thread** Ponteiro para destino para ponteiro para o próximo fio na lista de suspensão.</span><span class="sxs-lookup"><span data-stu-id="8036f-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-1956">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-1957">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-1957">Return Values</span></span>

- <span data-ttu-id="8036f-1958">**TX_SUCCESS** (0x00) Recuperação de informações de fio bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="8036f-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="8036f-1959">**TX_THREAD_ERROR** (0x0E) Ponteiro de controlo de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-1960">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-1960">Allowed From</span></span>

<span data-ttu-id="8036f-1961">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-1962">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-1962">Preemption Possible</span></span>

<span data-ttu-id="8036f-1963">No</span><span class="sxs-lookup"><span data-stu-id="8036f-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-1964">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-1964">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-1965">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-1965">See Also</span></span>

- <span data-ttu-id="8036f-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-1966">tx_thread_create</span></span>
- <span data-ttu-id="8036f-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-1967">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-1969">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-1975">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-1976">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="8036f-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="8036f-1984">Obtenha informações sobre desempenho de thread</span><span class="sxs-lookup"><span data-stu-id="8036f-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-1985">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-1985">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-1986">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-1986">Description</span></span>

<span data-ttu-id="8036f-1987">Este serviço recupera informações de desempenho sobre o fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-1988">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined para que este serviço devolva informações sobre o desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-1989">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-1989">Parameters</span></span>
- <span data-ttu-id="8036f-1990">**thread_ptr** Ponteiro para fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="8036f-1991">**retomas** Ponteiro para o destino para o número de recomeços deste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="8036f-1992">**suspensões** Ponteiro para o destino para o número de suspensões deste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="8036f-1993">**solicited_preemptions** Ponteiro para o destino para o número de preventivas como resultado de uma chamada de serviço API threadX feita por este fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="8036f-1994">**interrupt_preemptions** Ponteiro para o destino para o número de preemposições deste fio como resultado do processamento de interrupção.</span><span class="sxs-lookup"><span data-stu-id="8036f-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="8036f-1995">**priority_inversions** Ponteiro para o destino para o número de inversões prioritárias deste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="8036f-1996">**time_slices** Ponteiro para o destino para o número de fatias de tempo deste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="8036f-1997">**renuncia** Ponteiro para destino para o número de renúncias de fio realizadas por este fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="8036f-1998">**intervalos** Ponteiro para o destino para o número de intervalos de suspensão neste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="8036f-1999">**wait_aborts** Ponteiro para destino para o número de abortos de espera realizados neste fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="8036f-2000">**last_preempted_by** Ponteiro para o destino para o ponteiro de linha que por último preemptou este fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2001">*O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2002">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2002">Return Values</span></span>

- <span data-ttu-id="8036f-2003">**TX_SUCCESS** (0x00) Desempenho do fio bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="8036f-2004">**TX_PTR_ERROR** (0x03) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="8036f-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2006">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2006">Allowed From</span></span>

<span data-ttu-id="8036f-2007">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2008">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2008">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2009">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2009">See Also</span></span>

- <span data-ttu-id="8036f-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2010">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2011">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2013">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2019">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2020">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="8036f-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="8036f-2028">Obtenha informações sobre desempenho do sistema de fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2029">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2029">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-2030">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2030">Description</span></span>

<span data-ttu-id="8036f-2031">Este serviço obtém informações de desempenho sobre todos os fios do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="8036f-2032">*A biblioteca e aplicação ThreadX devem ser construídas com*</span><span class="sxs-lookup"><span data-stu-id="8036f-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="8036f-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined para que este serviço devolva informações sobre o desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2034">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2034">Parameters</span></span>

- <span data-ttu-id="8036f-2035">**retomas** Ponteiro para o destino para o número total de resmuções de roscas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="8036f-2036">**suspensões** Ponteiro para destino para o número total de suspensões de fios.</span><span class="sxs-lookup"><span data-stu-id="8036f-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="8036f-2037">**solicited_preemptions** Ponteiro para destino para o número total de preempções de linha como resultado de um fio chamando um serviço API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8036f-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="8036f-2038">**interrupt_preemptions** Ponteiro para o destino para o número total de preemposições de rosca como resultado do processamento de interrupção.</span><span class="sxs-lookup"><span data-stu-id="8036f-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="8036f-2039">**priority_inversions** Ponteiro para o destino para o número total de inversões prioritárias de linha.</span><span class="sxs-lookup"><span data-stu-id="8036f-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="8036f-2040">**time_slices** Ponteiro para o destino para o número total de fatias de tempo de fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="8036f-2041">**renuncia** Ponteiro para destino para o número total de renúncias de fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="8036f-2042">**intervalos** Ponteiro para o destino para o número total de intervalos de suspensão de fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="8036f-2043">**wait_aborts** Ponteiro para destino para o número total de thread wait aborta.</span><span class="sxs-lookup"><span data-stu-id="8036f-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="8036f-2044">**non_idle_returns** Ponteiro para o destino para o número de vezes que um fio retorna ao sistema quando outro fio está pronto para ser executado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="8036f-2045">**idle_returns** Ponteiro para destino para o número de vezes que um fio retorna ao sistema quando nenhum outro fio está pronto para ser executado (sistema inativo).</span><span class="sxs-lookup"><span data-stu-id="8036f-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2046">*O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2047">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2047">Return Values</span></span>

- <span data-ttu-id="8036f-2048">**TX_SUCCESS** (0x00) Desempenho do sistema de fio bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="8036f-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2050">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2050">Allowed From</span></span>

<span data-ttu-id="8036f-2051">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2052">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2052">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2053">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2053">See Also</span></span>

- <span data-ttu-id="8036f-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2054">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2055">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2057">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2063">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2064">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="8036f-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="8036f-2072">Alterar limiar de preempção do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2073">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="8036f-2074">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2074">Description</span></span>

<span data-ttu-id="8036f-2075">Este serviço altera o limiar de pré-substituição do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="8036f-2076">O limiar de prevenção previne a preempção do fio especificado por roscas iguais ou inferiores ao valor do limiar de prevenção.</span><span class="sxs-lookup"><span data-stu-id="8036f-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="8036f-2077">*A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2078">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2078">Parameters</span></span>
- <span data-ttu-id="8036f-2079">**thread_ptr** Ponteiro para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="8036f-2080">**new_threshold** Novo nível de prioridade do limiar de pré-edição (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8036f-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8036f-2081">**old_threshold** Ponteiro para um local para devolver o limiar de pré-substituição anterior.</span><span class="sxs-lookup"><span data-stu-id="8036f-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2082">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2082">Return Values</span></span>

- <span data-ttu-id="8036f-2083">**TX_SUCCESS** (0x00) Alteração do limiar de pré-edição bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="8036f-2084">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2085">**TX_THRESH_ERROR** (0x18) O novo limiar de pré-substituição especificado não é uma prioridade de linha válida (um valor diferente (0 a **TX_MAX_PRIORITIES**-1)) ou é maior do que (prioridade inferior) do que a prioridade atual do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="8036f-2086">**TX_PTR_ERROR** (0x03) Ponteiro inválido para o local de armazenamento de retenção preventiva anterior.</span><span class="sxs-lookup"><span data-stu-id="8036f-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="8036f-2087">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2088">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2088">Allowed From</span></span>

<span data-ttu-id="8036f-2089">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2090">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2090">Preemption Possible</span></span>

<span data-ttu-id="8036f-2091">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2092">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2092">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2093">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2093">See Also</span></span>

- <span data-ttu-id="8036f-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2094">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2095">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2097">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2103">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2104">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="8036f-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="8036f-2112">Alterar prioridade do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2113">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="8036f-2114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2114">Description</span></span>

<span data-ttu-id="8036f-2115">Este serviço altera a prioridade do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="8036f-2116">As prioridades válidas variam entre 0 e TX_MAX_PRIORITES-1, onde 0 representa o nível de maior prioridade.</span><span class="sxs-lookup"><span data-stu-id="8036f-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2117">\*O limiar de pré-substituição do fio especificado é automaticamente definido para a nova prioridade.</span><span class="sxs-lookup"><span data-stu-id="8036f-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="8036f-2118">Se for desejado um novo limiar, o serviço \***tx_thread_preemption_change** _ deve ser utilizado após este call._</span><span class="sxs-lookup"><span data-stu-id="8036f-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2119">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2119">Parameters</span></span>

- <span data-ttu-id="8036f-2120">**thread_ptr** Ponteiro para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="8036f-2121">**new_priority** Novo nível de prioridade do fio (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8036f-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8036f-2122">**old_priority** Ponteiro para um local para devolver a prioridade anterior da linha.</span><span class="sxs-lookup"><span data-stu-id="8036f-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2123">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2123">Return Values</span></span>

- <span data-ttu-id="8036f-2124">**TX_SUCCESS** (0x00) Mudança de prioridade bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="8036f-2125">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2126">**TX_PRIORITY_ERROR** (0x0F) A nova prioridade especificada não é válida (um valor diferente (0 a TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8036f-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8036f-2127">**TX_PTR_ERROR** (0x03) Ponteiro inválido para localização de armazenamento prioritário anterior.</span><span class="sxs-lookup"><span data-stu-id="8036f-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="8036f-2128">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2129">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2129">Allowed From</span></span>

<span data-ttu-id="8036f-2130">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2131">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2131">Preemption Possible</span></span>

<span data-ttu-id="8036f-2132">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2133">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8036f-2134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2134">See Also</span></span>

- <span data-ttu-id="8036f-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2135">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2136">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2138">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2144">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2145">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="8036f-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="8036f-2153">Renunciar ao controlo a outros fios de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2154">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="8036f-2155">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2155">Description</span></span>

<span data-ttu-id="8036f-2156">Este serviço renuncia ao controlo do processador a outras linhas prontas a executar na mesma prioridade ou maior.</span><span class="sxs-lookup"><span data-stu-id="8036f-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2157">*Além de renunciar ao controlo a fios da mesma prioridade, este serviço também renuncia ao controlo ao fio de maior prioridade impedido de ser executado devido à definição do limiar de prevenção da linha atual.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2158">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2158">Parameters</span></span>

<span data-ttu-id="8036f-2159">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2160">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2160">Return Values</span></span>

<span data-ttu-id="8036f-2161">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2162">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2162">Allowed From</span></span>

<span data-ttu-id="8036f-2163">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2164">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2164">Preemption Possible</span></span>

<span data-ttu-id="8036f-2165">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="8036f-2166">Exemplos</span><span class="sxs-lookup"><span data-stu-id="8036f-2166">Examples</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2167">See Also</span></span>

- <span data-ttu-id="8036f-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2168">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2169">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2171">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2177">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2178">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="8036f-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2185">tx_thread_reset</span></span>

<span data-ttu-id="8036f-2186">Linha de reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2187">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2188">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2188">Description</span></span>

<span data-ttu-id="8036f-2189">Este serviço reinicia o fio especificado para executar no ponto de entrada definido na criação do fio.</span><span class="sxs-lookup"><span data-stu-id="8036f-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="8036f-2190">O fio deve estar em um **estado TX_COMPLETED** ou **TX_TERMINATED** para que seja reposto</span><span class="sxs-lookup"><span data-stu-id="8036f-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2191">*O fio deve ser retomado para que volte a ser executado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2192">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2192">Parameters</span></span>

- <span data-ttu-id="8036f-2193">**thread_ptr** Ponteiro para um fio previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2194">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2194">Return Values</span></span>

- <span data-ttu-id="8036f-2195">**TX_SUCCESS** (0x00) Reposição de fio bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="8036f-2196">**TX_NOT_DONE** (0x20) O fio especificado não está num estado **TX_COMPLETED** ou **TX_TERMINATED.**</span><span class="sxs-lookup"><span data-stu-id="8036f-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="8036f-2197">**TX_THREAD_ERROR** (0x0E) Ponteiro de rosca inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="8036f-2198">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2199">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2199">Allowed From</span></span>

<span data-ttu-id="8036f-2200">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2201">Example</span></span>

<span data-ttu-id="8036f-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="8036f-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2203">See Also</span></span>

- <span data-ttu-id="8036f-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2204">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2205">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2207">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="8036f-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2214">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="8036f-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2221">tx_thread_resume</span></span>

<span data-ttu-id="8036f-2222">Retomar linha de aplicação suspensa</span><span class="sxs-lookup"><span data-stu-id="8036f-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2223">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2224">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2224">Description</span></span>

<span data-ttu-id="8036f-2225">Este serviço retoma ou prepara para a execução um fio que foi previamente suspenso por uma ***chamada tx_thread_suspend.***</span><span class="sxs-lookup"><span data-stu-id="8036f-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="8036f-2226">Além disso, este serviço retoma os fios que foram criados sem um arranque automático.</span><span class="sxs-lookup"><span data-stu-id="8036f-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2227">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2227">Parameters</span></span>

- <span data-ttu-id="8036f-2228">**thread_ptr** Ponteiro para um fio de aplicação suspenso.</span><span class="sxs-lookup"><span data-stu-id="8036f-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2229">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2229">Return Values</span></span>

- <span data-ttu-id="8036f-2230">**TX_SUCCESS** (0x00) Currículo de fio bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="8036f-2231">**TX_SUSPEND_LIFTED** (0x19) A suspensão adiada previamente definida foi levantada.</span><span class="sxs-lookup"><span data-stu-id="8036f-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="8036f-2232">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2233">**TX_RESUME_ERROR** (0x12) O fio especificado não está suspenso ou foi previamente suspenso por um serviço que não **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="8036f-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2234">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2234">Allowed From</span></span>

<span data-ttu-id="8036f-2235">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2236">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2236">Preemption Possible</span></span>

<span data-ttu-id="8036f-2237">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2237">Yes</span></span>

<span data-ttu-id="8036f-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="8036f-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2239">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2240">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2240">See Also</span></span>

- <span data-ttu-id="8036f-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2241">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2242">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2244">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2251">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="8036f-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2258">tx_thread_sleep</span></span>

<span data-ttu-id="8036f-2259">Suspender o fio de corrente por tempo especificado</span><span class="sxs-lookup"><span data-stu-id="8036f-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2260">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="8036f-2261">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2261">Description</span></span>

<span data-ttu-id="8036f-2262">Este serviço faz com que o fio de chamada suspenda o número especificado de carraças temporais.</span><span class="sxs-lookup"><span data-stu-id="8036f-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="8036f-2263">A quantidade de tempo físico associado a um tique-taque do temporizador é específica da aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="8036f-2264">Este serviço só pode ser chamado a partir de um fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2265">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2265">Parameters</span></span>

- <span data-ttu-id="8036f-2266">**timer_ticks** O número de carraças temporizador para suspender o fio da aplicação de chamada, que varia de 0 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="8036f-2267">Se 0 for especificado, o serviço retorna imediatamente.</span><span class="sxs-lookup"><span data-stu-id="8036f-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2268">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2268">Return Values</span></span>

- <span data-ttu-id="8036f-2269">**TX_SUCCESS** (0x00) Sono de linha bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="8036f-2270">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="8036f-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8036f-2271">**TX_CALLER_ERROR** serviço (0x13) chamado de um não-thread.</span><span class="sxs-lookup"><span data-stu-id="8036f-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2272">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2272">Allowed From</span></span>

<span data-ttu-id="8036f-2273">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2274">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2274">Preemption Possible</span></span>

<span data-ttu-id="8036f-2275">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2276">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2277">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2277">See Also</span></span>

- <span data-ttu-id="8036f-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2280">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2287">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2288">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="8036f-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="8036f-2295">Registar chamada de notificação de erro de pilha de fio</span><span class="sxs-lookup"><span data-stu-id="8036f-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2296">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="8036f-2297">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2297">Description</span></span>

<span data-ttu-id="8036f-2298">Este serviço regista uma função de chamada de notificação para lidar com erros de pilha de fios.</span><span class="sxs-lookup"><span data-stu-id="8036f-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="8036f-2299">Quando a ThreadX detetar um erro de pilha de fio durante a execução, chamará esta função de notificação para processar o erro.</span><span class="sxs-lookup"><span data-stu-id="8036f-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="8036f-2300">O processamento do erro é completamente definido pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="8036f-2301">Qualquer coisa desde suspender o fio de violação até reiniciar todo o sistema pode ser feito.</span><span class="sxs-lookup"><span data-stu-id="8036f-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2302">*A biblioteca ThreadX deve ser construída com* **TX_ENABLE_STACK_CHECKING** *definidas para que este serviço devolva informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2303">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2303">Parameters</span></span>
- <span data-ttu-id="8036f-2304">**error_handler** Ponteiro para a função de manuseamento de erros de pilha da aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="8036f-2305">Se este valor for TX_NULL, a notificação é desativada.</span><span class="sxs-lookup"><span data-stu-id="8036f-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2306">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2306">Return Values</span></span>

- <span data-ttu-id="8036f-2307">**TX_SUCCESS** (0x00) Reposição de fio bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="8036f-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2309">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2309">Allowed From</span></span>

<span data-ttu-id="8036f-2310">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2311">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="8036f-2312">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2312">See Also</span></span>

- <span data-ttu-id="8036f-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2313">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2314">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2316">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="8036f-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2323">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2324">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="8036f-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2330">tx_thread_suspend</span></span>

<span data-ttu-id="8036f-2331">Suspender o fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2333">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2333">Description</span></span>

<span data-ttu-id="8036f-2334">Este serviço suspende o fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="8036f-2335">Um fio pode chamar este serviço para se suspender.</span><span class="sxs-lookup"><span data-stu-id="8036f-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2336">*Se o fio especificado já estiver suspenso por outro motivo, esta suspensão é mantida internamente até que a suspensão prévia seja levantada. Quando isso acontece, esta suspensão incondicional do fio especificado é executada. Outros pedidos de suspensão incondicional não têm efeito.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="8036f-2337">Depois de suspensa, o fio deve ser retomado por ***tx_thread_resume*** para ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="8036f-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2338">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2338">Parameters</span></span>

- <span data-ttu-id="8036f-2339">**thread_ptr** Ponteiro para um fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2340">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2340">Return Values</span></span>

- <span data-ttu-id="8036f-2341">**TX_SUCCESS** (0x00) Suspender o fio de sucesso.</span><span class="sxs-lookup"><span data-stu-id="8036f-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="8036f-2342">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2343">**TX_SUSPEND_ERROR** (0x14) O fio especificado encontra-se num estado encerrado ou concluído.</span><span class="sxs-lookup"><span data-stu-id="8036f-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="8036f-2344">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2345">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2345">Allowed From</span></span>

<span data-ttu-id="8036f-2346">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2347">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2347">Preemption Possible</span></span>

<span data-ttu-id="8036f-2348">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2349">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2350">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2350">See Also</span></span>

- <span data-ttu-id="8036f-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2351">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2352">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2354">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2361">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2362">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="8036f-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2368">tx_thread_terminate</span></span>

<span data-ttu-id="8036f-2369">Termina linha de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2370">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8036f-2371">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2371">Description</span></span>

<span data-ttu-id="8036f-2372">Este serviço termina o fio de aplicação especificado, independentemente de o fio estar suspenso ou não.</span><span class="sxs-lookup"><span data-stu-id="8036f-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="8036f-2373">Um fio pode chamar este serviço para terminar sozinho.</span><span class="sxs-lookup"><span data-stu-id="8036f-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2374">*É da responsabilidade da aplicação assegurar que o fio está num estado adequado para a rescisão. Por exemplo, um fio não deve ser terminado durante o processamento crítico da aplicação ou no interior de outros componentes do middleware onde possa deixar esse processamento num estado desconhecido.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2375">*Depois de ter sido encerrado, o fio deve ser reiniciado para que volte a ser executado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2376">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2376">Parameters</span></span>

- <span data-ttu-id="8036f-2377">**thread_ptr** Ponteiro para o fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2378">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2378">Return Values</span></span>
- <span data-ttu-id="8036f-2379">**TX_SUCCESS** (0x00) Fim de linha bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="8036f-2380">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2381">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2382">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2382">Allowed From</span></span>

<span data-ttu-id="8036f-2383">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2384">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2384">Preemption Possible</span></span>

<span data-ttu-id="8036f-2385">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2386">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2387">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2387">See Also</span></span>

- <span data-ttu-id="8036f-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2390">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2397">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2398">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8036f-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="8036f-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="8036f-2405">Altera a fatia de tempo do fio de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2406">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="8036f-2407">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2407">Description</span></span>

<span data-ttu-id="8036f-2408">Este serviço altera a fatia de tempo do fio de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="8036f-2409">Selecionar uma fatia de tempo para um fio assegura que não executará mais do que o número especificado de carraças de temporizador antes que outros fios das mesmas prioridades ou mais altas tenham a oportunidade de executar.</span><span class="sxs-lookup"><span data-stu-id="8036f-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2410">*A utilização do limiar de pré-substituição desativa o corte de tempo para o fio especificado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2411">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2411">Parameters</span></span>

- <span data-ttu-id="8036f-2412">**thread_ptr** Ponteiro para o fio de aplicação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="8036f-2413">**new_time_slice** Novo valor de fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="8036f-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="8036f-2414">Os valores legais incluem valores TX_NO_TIME_SLICE e numéricos de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8036f-2415">**old_time_slice** Ponteiro para o local para armazenar o valor dos ísamentos anteriores do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2416">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2416">Return Values</span></span>

- <span data-ttu-id="8036f-2417">**TX_SUCCESS** (0x00) Oportunidade de corte de tempo bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="8036f-2418">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2419">**TX_PTR_ERROR** (0x03) Ponteiro inválido para o local de armazenamento anterior da fatia de tempo.</span><span class="sxs-lookup"><span data-stu-id="8036f-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="8036f-2420">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2421">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2421">Allowed From</span></span>

<span data-ttu-id="8036f-2422">Fios e temporizadores</span><span class="sxs-lookup"><span data-stu-id="8036f-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2423">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2423">Preemption Possible</span></span>

<span data-ttu-id="8036f-2424">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2425">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2425">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2426">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2426">See Also</span></span>

- <span data-ttu-id="8036f-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2427">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2428">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2430">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2437">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2438">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="8036f-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8036f-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="8036f-2445">Abortar suspensão do fio especificado</span><span class="sxs-lookup"><span data-stu-id="8036f-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2446">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2447">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2447">Description</span></span>

<span data-ttu-id="8036f-2448">Este serviço aborta o sono ou qualquer outro objeto suspenso do fio especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="8036f-2449">Se a espera for abortada, um **valor TX_WAIT_ABORTED** é devolvido do serviço que o fio estava à espera.</span><span class="sxs-lookup"><span data-stu-id="8036f-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2450">*Este serviço não liberta suspensão explícita que é feita pelo serviço tx_thread_suspend.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2451">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2451">Parameters</span></span>

- <span data-ttu-id="8036f-2452">**thread_ptr** Ponteiro para um fio de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2453">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2453">Return Values</span></span>

- <span data-ttu-id="8036f-2454">**TX_SUCCESS** (0x00) Abortar a espera de fio bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="8036f-2455">**TX_THREAD_ERROR** (0x0E) Ponteiro de linha de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8036f-2456">**TX_WAIT_ABORT_ERROR** (0x1B) O fio especificado não está em estado de espera.</span><span class="sxs-lookup"><span data-stu-id="8036f-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2457">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2457">Allowed From</span></span>

<span data-ttu-id="8036f-2458">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2459">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2459">Preemption Possible</span></span>
<span data-ttu-id="8036f-2460">Sim</span><span class="sxs-lookup"><span data-stu-id="8036f-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2461">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2462">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2462">See Also</span></span>

- <span data-ttu-id="8036f-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2463">tx_thread_create</span></span>
- <span data-ttu-id="8036f-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2464">tx_thread_delete</span></span>
- <span data-ttu-id="8036f-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8036f-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8036f-2466">tx_thread_identify</span></span>
- <span data-ttu-id="8036f-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="8036f-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8036f-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8036f-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8036f-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="8036f-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8036f-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="8036f-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8036f-2473">tx_thread_reset</span></span>
- <span data-ttu-id="8036f-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8036f-2474">tx_thread_resume</span></span>
- <span data-ttu-id="8036f-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8036f-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="8036f-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8036f-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8036f-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8036f-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="8036f-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8036f-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="8036f-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="8036f-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2480">tx_time_get</span></span>

<span data-ttu-id="8036f-2481">Recupera o tempo atual</span><span class="sxs-lookup"><span data-stu-id="8036f-2481">Retrieves the current time</span></span>

<span data-ttu-id="8036f-2482">Temporizadores de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2483">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="8036f-2484">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2484">Description</span></span>

<span data-ttu-id="8036f-2485">Este serviço devolve o conteúdo do relógio interno do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="8036f-2486">Cada timertick aumenta o relógio do sistema interno por um.</span><span class="sxs-lookup"><span data-stu-id="8036f-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="8036f-2487">O relógio do sistema está definido para zero durante a inicialização e pode ser alterado para um valor específico pelo ***serviço tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="8036f-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2488">*O tempo real que cada temporizador representa é específico da aplicação.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="8036f-2489">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="8036f-2489">**Parameters**</span></span>

<span data-ttu-id="8036f-2490">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2491">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2491">Return Values</span></span>

- <span data-ttu-id="8036f-2492">**relógio do sistema tiques** Valor do relógio interno, livre, do sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2493">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2493">Allowed From</span></span>

<span data-ttu-id="8036f-2494">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2495">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2495">Preemption Possible</span></span>
<span data-ttu-id="8036f-2496">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2497">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2498">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2498">See Also</span></span>

- <span data-ttu-id="8036f-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="8036f-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="8036f-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="8036f-2500">tx_time_set</span></span>

<span data-ttu-id="8036f-2501">Define a hora atual</span><span class="sxs-lookup"><span data-stu-id="8036f-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2502">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="8036f-2503">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2503">Description</span></span>

<span data-ttu-id="8036f-2504">Este serviço define o relógio do sistema interno ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="8036f-2505">Cada temporizador aumenta o relógio do sistema interno por um.</span><span class="sxs-lookup"><span data-stu-id="8036f-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2506">*O tempo real que cada temporizador representa é específico da aplicação.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2507">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2507">Parameters</span></span>

- <span data-ttu-id="8036f-2508">**new_time** Novo tempo para colocar no relógio do sistema, os valores legais variam de 0 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2509">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2509">Return Values</span></span>

<span data-ttu-id="8036f-2510">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8036f-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2511">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2511">Allowed From</span></span>

<span data-ttu-id="8036f-2512">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2513">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2513">Preemption Possible</span></span>

<span data-ttu-id="8036f-2514">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2515">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2516">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2516">See Also</span></span>

- <span data-ttu-id="8036f-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="8036f-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2518">tx_timer_activate</span></span>

<span data-ttu-id="8036f-2519">Ativar o temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="8036f-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2520">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2521">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2521">Description</span></span>

<span data-ttu-id="8036f-2522">Este serviço ativa o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="8036f-2523">As rotinas de expiração dos temporizadores que expiram ao mesmo tempo são executadas na ordem em que foram ativados.</span><span class="sxs-lookup"><span data-stu-id="8036f-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2524">*Um temporizador de um tiro expirado deve ser reposto através*  \* **tx_timer_change** _ _before pode ser ativado novamente.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2525">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2525">Parameters</span></span>

- <span data-ttu-id="8036f-2526">**timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="8036f-2527">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="8036f-2527">**Return Values**</span></span>

- <span data-ttu-id="8036f-2528">**TX_SUCCESS** (0x00) Ativação do temporizador de aplicação bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="8036f-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="8036f-2529">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8036f-2530">**TX_ACTIVATE_ERROR** (0x17) Timer já estava ativo ou é um temporizador de um tiro que já expirou.</span><span class="sxs-lookup"><span data-stu-id="8036f-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2531">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2531">Allowed From</span></span>

<span data-ttu-id="8036f-2532">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2533">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2533">Preemption Possible</span></span>

<span data-ttu-id="8036f-2534">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2535">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2536">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2536">See Also</span></span>

- <span data-ttu-id="8036f-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2537">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2538">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2540">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="8036f-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2544">tx_timer_change</span></span>

<span data-ttu-id="8036f-2545">Alterar temporizador de aplicação</span><span class="sxs-lookup"><span data-stu-id="8036f-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2546">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="8036f-2547">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2547">Description</span></span>

<span data-ttu-id="8036f-2548">Este serviço altera as características de expiração do temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="8036f-2549">O temporizador deve ser desativado antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2550">*Uma chamada para o*  \* **tx_timer_activate** _ _service é necessária após este serviço para recomeçar o temporizador.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2551">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2551">Parameters</span></span>

- <span data-ttu-id="8036f-2552">**timer_ptr** Ponteiro para um bloco de controlo do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="8036f-2553">**initial_ticks** Especifica o número inicial de carraças para a expiração do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="8036f-2554">Os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8036f-2555">**reschedule_ticks** Especifica o número de tiques para todos os expiradores do temporizador após o primeiro.</span><span class="sxs-lookup"><span data-stu-id="8036f-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="8036f-2556">Um zero para este parâmetro faz do temporizador um *temporizador de um tiro.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="8036f-2557">Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2558">*Um temporizador de um tiro expirado deve ser reposto através* 
\* **tx_timer_change** _ _before pode ser ativado novamente.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2559">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2559">Return Values</span></span>

- <span data-ttu-id="8036f-2560">**TX_SUCCESS** (0x00) Alteração do temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="8036f-2561">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8036f-2562">**TX_TICK_ERROR** (0x16) Valor inválido (um zero) fornecido para os tiques iniciais.</span><span class="sxs-lookup"><span data-stu-id="8036f-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="8036f-2563">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2564">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2564">Allowed From</span></span>

<span data-ttu-id="8036f-2565">Fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2566">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2566">Preemption Possible</span></span>

<span data-ttu-id="8036f-2567">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2568">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2568">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2569">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2569">See Also</span></span>

- <span data-ttu-id="8036f-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2570">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2571">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2573">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="8036f-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2577">tx_timer_create</span></span>

<span data-ttu-id="8036f-2578">Criar temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="8036f-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2579">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2579">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="8036f-2580">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2580">Description</span></span>

<span data-ttu-id="8036f-2581">Este serviço cria um temporizador de aplicação com a função de expiração especificada e periódico.</span><span class="sxs-lookup"><span data-stu-id="8036f-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2582">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2582">Parameters</span></span>

- <span data-ttu-id="8036f-2583">**timer_ptr** Ponteiro para um bloco de controlo do temporizador</span><span class="sxs-lookup"><span data-stu-id="8036f-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="8036f-2584">**name_ptr** Ponteiro para o nome do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="8036f-2585">**expiration_function** Função de aplicação para ligar quando o temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="8036f-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="8036f-2586">**expiration_input** Entrada para passar para a função de expiração quando o temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="8036f-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="8036f-2587">**initial_ticks** Especifica o número inicial de carraças para a expiração do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="8036f-2588">Os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8036f-2589">**reschedule_ticks** Especifica o número de tiques para todos os expiradores do temporizador após o primeiro.</span><span class="sxs-lookup"><span data-stu-id="8036f-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="8036f-2590">Um zero para este parâmetro faz do temporizador um *temporizador de um tiro.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="8036f-2591">Caso contrário, para os temporizadores periódicos, os valores legais variam de 1 a 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8036f-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8036f-2592">*Depois de expirar um temporizador de uma única vez, deve ser reiniciado através de tx_timer_change antes de poder ser ativado novamente.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="8036f-2593">**auto_activate** Determina se o temporizador é ativado automaticamente durante a criação.</span><span class="sxs-lookup"><span data-stu-id="8036f-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="8036f-2594">Se este valor for **TX_AUTO_ACTIVATE** (0x01), o temporizador torna-se ativo.</span><span class="sxs-lookup"><span data-stu-id="8036f-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="8036f-2595">Caso contrário, se o valor **TX_NO_ACTIVATE** (0x00) for selecionado, o temporizador é criado num estado não ativo.</span><span class="sxs-lookup"><span data-stu-id="8036f-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="8036f-2596">Neste caso, é necessária uma chamada de serviço **_tx_timer_activate_** subsequente para iniciar o temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2597">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2597">Return Values</span></span>

- <span data-ttu-id="8036f-2598">**TX_SUCCESS** (0x00) Criação de temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="8036f-2599">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="8036f-2600">Ou o ponteiro é NULO ou o temporizador já está criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="8036f-2601">**TX_TICK_ERROR** (0x16) Valor inválido (um zero) fornecido para os tiques iniciais.</span><span class="sxs-lookup"><span data-stu-id="8036f-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="8036f-2602">**TX_ACTIVATE_ERROR** (0x17) Ativação inválida selecionada.</span><span class="sxs-lookup"><span data-stu-id="8036f-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="8036f-2603">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2604">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2604">Allowed From</span></span>

<span data-ttu-id="8036f-2605">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2606">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2606">Preemption Possible</span></span>

<span data-ttu-id="8036f-2607">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2608">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2608">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2609">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2609">See Also</span></span>

- <span data-ttu-id="8036f-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2610">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2611">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2613">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="8036f-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="8036f-2618">Temporizador de aplicação desativado</span><span class="sxs-lookup"><span data-stu-id="8036f-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2619">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2620">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2620">Description</span></span>

<span data-ttu-id="8036f-2621">Este serviço desativa o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="8036f-2622">Se o temporizador já estiver desativado, este serviço não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="8036f-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2623">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2623">Parameters</span></span>

- <span data-ttu-id="8036f-2624">**timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2625">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2625">Return Values</span></span>

- <span data-ttu-id="8036f-2626">**TX_SUCCESS** (0x00) Desativação do temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="8036f-2627">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2628">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2628">Allowed From</span></span>

<span data-ttu-id="8036f-2629">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2630">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2630">Preemption Possible</span></span>

<span data-ttu-id="8036f-2631">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2632">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2633">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2633">See Also</span></span>

- <span data-ttu-id="8036f-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2634">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2635">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2636">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2637">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="8036f-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2641">tx_timer_delete</span></span>

<span data-ttu-id="8036f-2642">Eliminar temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="8036f-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2643">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="8036f-2644">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2644">Description</span></span>

<span data-ttu-id="8036f-2645">Este serviço elimina o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2646">*É da responsabilidade da aplicação impedir a utilização de um temporizador eliminado.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2647">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2647">Parameters</span></span>

- <span data-ttu-id="8036f-2648">**timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2649">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2649">Return Values</span></span>

- <span data-ttu-id="8036f-2650">**TX_SUCCESS** (0x00) Eliminação do temporizador de aplicação bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="8036f-2651">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8036f-2652">**TX_CALLER_ERROR** (0x13) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="8036f-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2653">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2653">Allowed From</span></span>

<span data-ttu-id="8036f-2654">Fios</span><span class="sxs-lookup"><span data-stu-id="8036f-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2655">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2655">Preemption Possible</span></span>

<span data-ttu-id="8036f-2656">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2657">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="8036f-2658">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2658">See Also</span></span>

- <span data-ttu-id="8036f-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2659">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2660">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2661">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="8036f-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2666">tx_timer_info_get</span></span>

<span data-ttu-id="8036f-2667">Recuperar informações sobre um temporizador de aplicações</span><span class="sxs-lookup"><span data-stu-id="8036f-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2668">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="8036f-2669">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2669">Description</span></span>

<span data-ttu-id="8036f-2670">Este serviço obtém informações sobre o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2671">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2671">Parameters</span></span>

- <span data-ttu-id="8036f-2672">**timer_ptr** Ponteiro para um temporizador de aplicação previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="8036f-2673">**nome** Ponteiro para o destino para o ponteiro para o nome do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="8036f-2674">**ativo** Ponteiro para o destino para a indicação ativa do temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="8036f-2675">Se o temporizador estiver inativo ou este serviço for chamado do temporizador em si, é devolvido um **valor TX_FALSE.**</span><span class="sxs-lookup"><span data-stu-id="8036f-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="8036f-2676">Caso contrário, se o temporizador estiver ativo, é devolvido um valor **TX_TRUE.**</span><span class="sxs-lookup"><span data-stu-id="8036f-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="8036f-2677">**remaining_ticks** Ponteiro para o destino para o número de carraças de temporizador que sobrou antes do temporizador expirar.</span><span class="sxs-lookup"><span data-stu-id="8036f-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="8036f-2678">**reschedule_ticks** Ponteiro para o destino para o número de carraças tempor que serão usadas para reagendar automaticamente este temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="8036f-2679">Se o valor for zero, então o temporizador é um tiro e não será reagendado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="8036f-2680">**next_timer** Ponteiro para o destino para o ponteiro do próximo temporizador de aplicação criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2681">*O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2682">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2682">Return Values</span></span>

- <span data-ttu-id="8036f-2683">**TX_SUCCESS** (0x00) Recuperação de informações cronometrador de sucesso.</span><span class="sxs-lookup"><span data-stu-id="8036f-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="8036f-2684">**TX_TIMER_ERROR** (0x15) Ponteiro do temporizador de aplicação inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2685">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2685">Allowed From</span></span>

<span data-ttu-id="8036f-2686">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8036f-2687">Preempção Possível</span><span class="sxs-lookup"><span data-stu-id="8036f-2687">Preemption Possible</span></span>

<span data-ttu-id="8036f-2688">No</span><span class="sxs-lookup"><span data-stu-id="8036f-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2689">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2689">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2690">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2690">See Also</span></span>

- <span data-ttu-id="8036f-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2691">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2692">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2693">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2695">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8036f-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="8036f-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="8036f-2700">Obtenha informações de desempenho do temporizador</span><span class="sxs-lookup"><span data-stu-id="8036f-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2701">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="8036f-2702">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2702">Description</span></span>

<span data-ttu-id="8036f-2703">Este serviço recupera informações de desempenho sobre o temporizador de aplicação especificado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2704">*A biblioteca e aplicação ThreadX devem ser construídas com*  \* **TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined para este serviço devolver informações de desempenho.\*</span><span class="sxs-lookup"><span data-stu-id="8036f-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8036f-2705">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8036f-2705">Parameters</span></span>
- <span data-ttu-id="8036f-2706">**timer_ptr** Ponteiro para temporizador previamente criado.</span><span class="sxs-lookup"><span data-stu-id="8036f-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="8036f-2707">**ativa** Ponteiro para destino para o número de pedidos de ativação realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="8036f-2708">**reativa** Ponteiro para o destino para o número de reativações automáticas realizadas neste temporizador periódico.</span><span class="sxs-lookup"><span data-stu-id="8036f-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="8036f-2709">**desativa** Ponteiro para destino para o número de pedidos de desativação realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="8036f-2710">**expirações** Ponteiro para o destino para o número de expirações deste temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="8036f-2711">**expiration_adjusts** Ponteiro para destino para o número de ajustes internos de validade realizados neste temporizador.</span><span class="sxs-lookup"><span data-stu-id="8036f-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="8036f-2712">Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).</span><span class="sxs-lookup"><span data-stu-id="8036f-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="8036f-2713">[NOTA] *O fornecimento de um TX_NULL para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2714">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2714">Return Values</span></span>

- <span data-ttu-id="8036f-2715">**TX_SUCCESS** (0x00) Desempenho do temporizador de sucesso obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="8036f-2716">**TX_PTR_ERROR** (0x03) Ponteiro temporizador inválido.</span><span class="sxs-lookup"><span data-stu-id="8036f-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="8036f-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2718">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2718">Allowed From</span></span>

<span data-ttu-id="8036f-2719">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2720">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2720">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2721">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2721">See Also</span></span>

- <span data-ttu-id="8036f-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2722">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2723">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2724">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2726">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="8036f-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="8036f-2730">Obtenha informações sobre o desempenho do sistema do temporizador</span><span class="sxs-lookup"><span data-stu-id="8036f-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8036f-2731">Prototype</span><span class="sxs-lookup"><span data-stu-id="8036f-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="8036f-2732">Descrição</span><span class="sxs-lookup"><span data-stu-id="8036f-2732">Description</span></span>

<span data-ttu-id="8036f-2733">Este serviço obtém informações de desempenho sobre todos os temporizadores de aplicação no sistema.</span><span class="sxs-lookup"><span data-stu-id="8036f-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8036f-2734">*A biblioteca e aplicação ThreadX devem ser construídas com* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *definidas para este serviço devolver informações de desempenho.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="8036f-2735">**Parâmetros**</span><span class="sxs-lookup"><span data-stu-id="8036f-2735">**Parameters**</span></span>

- <span data-ttu-id="8036f-2736">**ativa** Ponteiro para destino para o número total de pedidos de ativação realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="8036f-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="8036f-2737">**reativa** Ponteiro para destino para o número total de reativação automática realizada em todos os temporizadores periódicos.</span><span class="sxs-lookup"><span data-stu-id="8036f-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="8036f-2738">**desativa** Ponteiro para destino para o número total de pedidos de desativação realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="8036f-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="8036f-2739">**expirações** Ponteiro para destino para o número total de expirações em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="8036f-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="8036f-2740">**expiration_adjusts** Ponteiro para destino para o número total de ajustes internos de validade realizados em todos os temporizadores.</span><span class="sxs-lookup"><span data-stu-id="8036f-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="8036f-2741">Estes ajustes são efetuados no temporizador interrompem o processamento para temporizadores que são maiores do que o tamanho da lista de temporizadores predefinidos (por temporizadores predefinidos com prazos superiores a 32 carraças).</span><span class="sxs-lookup"><span data-stu-id="8036f-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="8036f-2742">*O fornecimento de um **TX_NULL** para qualquer parâmetro indica que o parâmetro não é necessário.*</span><span class="sxs-lookup"><span data-stu-id="8036f-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="8036f-2743">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="8036f-2743">Return Values</span></span>

- <span data-ttu-id="8036f-2744">**TX_SUCCESS** (0x00) Desempenho do sistema temporizador de sucesso obtém.</span><span class="sxs-lookup"><span data-stu-id="8036f-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="8036f-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) O sistema não foi compilado com informações de desempenho ativadas.</span><span class="sxs-lookup"><span data-stu-id="8036f-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8036f-2746">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="8036f-2746">Allowed From</span></span>

<span data-ttu-id="8036f-2747">Inicialização, fios, temporizadores e ISRs</span><span class="sxs-lookup"><span data-stu-id="8036f-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8036f-2748">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8036f-2748">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8036f-2749">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8036f-2749">See Also</span></span>

- <span data-ttu-id="8036f-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8036f-2750">tx_timer_activate</span></span>
- <span data-ttu-id="8036f-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8036f-2751">tx_timer_change</span></span>
- <span data-ttu-id="8036f-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8036f-2752">tx_timer_create</span></span>
- <span data-ttu-id="8036f-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8036f-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="8036f-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8036f-2754">tx_timer_delete</span></span>
- <span data-ttu-id="8036f-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="8036f-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8036f-2756">tx_timer_performance_info_get</span></span>
