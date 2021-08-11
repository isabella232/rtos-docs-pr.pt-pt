---
title: Capítulo 2 - Requisitos do Módulo
description: Este artigo é uma descrição dos requisitos para a construção de um Módulo ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b814e7c2b510093b809b70b02d9a11ed39996d114f2306e0993893799453cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791963"
---
# <a name="chapter-2---module-requirements"></a>Capítulo 2 - Requisitos do módulo

Um Módulo ThreadX contém um preâmbulo, que define as características básicas do módulo. O preâmbulo é seguido pela área de instrução do módulo. Os módulos podem ser executados no lugar ou podem ser carregados na área de memória do módulo pelo Gestor do Módulo antes da execução. O único requisito é que o preâmbulo esteja sempre localizado no primeiro endereço do módulo. A figura 2 ilustra um layout básico do módulo.

| Layout do módulo |
|:---:|
| \[preâmbulo do módulo\]         |
| \[área de instrução do módulo\] |
| \[área de RAM de módulo\]         |

**Figura 2** - Layout do Módulo

> [!NOTE]
> Os módulos devem ser construídos com a posição adequada código independente e opções de compilador/linker de dados. Isto permite a execução do módulo em qualquer área de memória.

Quando um fio de módulo é criado, um espaço de segunda pilha é atribuído para utilização quando o fio está no núcleo protegido pela memória. O tamanho do espaço de pilha de núcleo do fio é configurável pelo utilizador utilizando **TXM_MODULE_KERNEL_STACK_SIZE** em **_txm_module_port.h_*_. Isto permite que um tamanho de pilha menor seja utilizado ao criar um fio módulo, uma vez que a pilha especificada pelo utilizador ao ligar _*_tx_thread_create_** é usada apenas no módulo.

> [!NOTE]
> A parte superior de uma pilha de fio de módulo contém a estrutura de informação de entrada de fio **(TXM_MODULE_THREAD_ENTRY_INFO),** pelo que o tamanho da pilha disponível é diminuído pelo tamanho desta estrutura. Ao criar um fio num módulo, aumente o tamanho da pilha pelo menos este tamanho desta estrutura.

São necessários os seguintes passos para a criação e construção de um Módulo ThreadX (cada passo é descrito com maior detalhe abaixo).

1. Todos os ficheiros C de um módulo devem #define **TXM_MODULE** antes de incluir **_txm_module.h_**. Isto pode ser realizado no ficheiro de origem que está a ser compilado ou como parte das definições do projeto. Ao fazê-lo, a API threadx chama para a versão específica do módulo da API que invoca a função de despacho no Gestor de Módulos residente para executar a chamada para a função API real.
2. Cada módulo deve ter um preâmbulo no seu primeiro endereço de área de instrução que defina as características e as necessidades de recursos do módulo.
3. Cada módulo deve ligar o preâmbulo no início da área de instrução do módulo.
4. Cada módulo deve ligar-se a uma biblioteca de módulos ***(txm.a),*** que contém funções específicas do módulo utilizadas para interagir com o ThreadX.

## <a name="module-sources"></a>Fontes de módulos

Os Módulos ThreadX têm o seu próprio conjunto de ficheiros de origem que são concebidos para serem ligados e localizados diretamente com o código fonte do módulo. Estes ficheiros fornecem a ponte entre o módulo separado e o gestor de módulos residente. Os ficheiros módulos são os seguintes.

| Nome de Ficheiro | Conteúdos |
|---|---|
| **txm_module.h** | Incluir ficheiro que define informações do módulo. |
| **txm_module_port.h** | Incluir ficheiro que define informações específicas do módulo por porta. |
| **txm_module_user.h** | Define e valoriza o utilizador pode personalizar. |
| **txm_module_initialize.s[1][3]** | Chama funções intrínsecas ao módulo de arranque. |
| **txm_module_preamble. \{ s/S/68\}** | Ficheiro de montagem do preâmbulo do módulo. Este ficheiro define vários atributos específicos do módulo e está ligado ao código de aplicação do módulo. |
| **txm_module_application_request.c [1]** | A função de pedido de pedido de módulo envia um pedido específico de aplicação para o código residente. |
| **txm_module_callback_request_thread_entry.c &nbsp; [1]** | Thread de chamada de módulo que é responsável pelo processamento de chamadas solicitadas pelo módulo, incluindo temporizadores e chamadas de notificação. |
| **txm_*.c [1][2]** | Os serviços padrão da API ThreadX, estes chamam o despachante kernel.
| **txm_module_object_allocate.c [1]** | Função do módulo para alocar memória para objetos de módulos localizados no conjunto de memória do gestor. |
| **txm_module_object_deallocate.c [1]** | Função do módulo para translocar memória para objetos de módulo localizados no conjunto de memória do gestor. |
| **txm_module_object_pointer_get.c [1]** | Função do módulo para recuperar um ponteiro para um objeto do sistema. |
| **txm_module_object_pointer_get_extended.c [1]** | Função do módulo para recuperar um ponteiro para um objeto do sistema, segurança do comprimento do nome. |
| **txm_module_thread_shell_entry.c [1]** | Função de entrada de fio do módulo. |
| **txm_module_thread_system_suspend.c [1]** | Função do módulo para suspender um fio. |

**[1]** Localizado na biblioteca **_txm.a_**.

**[2]** Estes ficheiros têm o mesmo nome que os ficheiros API da ThreadX, com **prefixo txm_** em vez de **tx_** prefixo.

**[3]** O **ficheiro txm_module_initialize.s destina-se** apenas a portas com ferramentas ARM.

## <a name="module-preamble"></a>Preâmbulo do módulo

O Módulo Preâmbulo define características e recursos do módulo. Informações como a função de entrada inicial do fio e a área de memória inicial associada ao fio são definidas no preâmbulo. Exemplos de preâmbulo específicos do porto estão no [apêndice](appendix.md). A figura 3 mostra um preâmbulo do módulo ThreadX para um alvo genérico (as linhas que começam com * são valores tipicamente modificados pela aplicação):

```c
    AREA Init, CODE, READONLY

    /* Define public symbols. */
    EXPORT __txm_module_preamble

    /* Define application-specific start/stop entry points for the module. */
    IMPORT demo_module_start

    /* Define common external refrences. */
    IMPORT _txm_module_thread_shell_entry
    IMPORT _txm_module_callback_request_thread_entry
    IMPORT |Image$$ER_RO$$Length|
    IMPORT |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                  ; Module ID
    DCD     0x6                                         ; Module Major Version
    DCD     0x1                                         ; Module Minor Version
    DCD     32                                          ; Module Preamble Size in 32-bit words
*   DCD     0x12345678                                  ; Module ID (application defined)
*   DCD     0x01000001                                  ; Module Properties where:
                                                        ; Bits 31-24: Compiler ID
                                                        ;   0 -> IAR
                                                        ;   1 -> ARM
                                                        ;   2 -> GNU
                                                        ;   Bits 23-1: Reserved
                                                        ;   Bit 0: 0 -> Privileged mode execution (no MMU protection)
                                                        ;          1 -> User mode execution (MMU protection)
    DCD     _txm_module_thread_shell_entry - . + .      ; Module Shell Entry Point
*   DCD     demo_module_start - . + .                   ; Module Start Thread Entry Point
    DCD     0                                           ; Module Stop Thread Entry Point
*   DCD     1                                           ; Module Start/Stop Thread Priority
*   DCD     2048                                        ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD     1                                            ; Module Callback Thread Priority
    DCD     2048                                         ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length|                       ; Module Code Size
    DCD     |Image$$ER_RW$$Length|                       ; Module Data Size
    DCD     0                                            ; Reserved 0
    DCD     0                                            ; Reserved 1
    DCD     0                                            ; Reserved 2
    DCD     0                                            ; Reserved 3
    DCD     0                                            ; Reserved 4
    DCD     0                                            ; Reserved 5
    DCD     0                                            ; Reserved 6
    DCD     0                                            ; Reserved 7
    DCD     0                                            ; Reserved 8
    DCD     0                                            ; Reserved 9
    DCD     0                                            ; Reserved 10
    DCD     0                                            ; Reserved 11
    DCD     0                                            ; Reserved 12
    DCD     0                                            ; Reserved 13
    DCD     0                                            ; Reserved 14
    DCD     0                                            ; Reserved 15
    END
```

**Figura 3**

Na maioria dos casos, o desenvolvedor apenas precisa de definir o fio inicial do módulo (offset 0x1C), o ID do módulo (offset 0x10), a prioridade do fio de partida/paragem (offset 0x24) e o tamanho da pilha de linha de arranque/paragem (offset 0x28). A demonstração acima é configurada de modo a que o fio de partida do módulo seja ***demo_module_start** _, o módulo ID é _*_0x12345678_*_, e o fio de partida tem uma prioridade de _*_1_*_, e um tamanho de pilha de _ *_2048_** bytes.

Algumas aplicações podem definir opcionalmente um fio de paragem, que é executado à medida que o Gestor do Módulo para o módulo. Além disso, algumas aplicações podem utilizar o campo Propriedades do Módulo, definido da seguinte forma.

## <a name="module-properties-bit-map"></a>Mapa de bits de propriedades de módulos

A tabela abaixo mostra um exemplo do mapa de bits de propriedades. Os bitmaps de propriedades específicas do porto estão no [apêndice.](appendix.md)

| Bit | Valor | Significado |
|---|---|---|
| 0 | 0<br />1 | Execução de modo privilegiado<br />Execução do modo de utilizador |
| 1 | 0<br />1 | Sem proteção MPU<br />Proteção MPU (deve ter o modo de utilizador selecionado) |
| 2 | 0<br />1 | Desativar o acesso à memória partilhada/externa<br />Ativar o acesso à memória partilhada/externa |
| [23-3] | 0 | Reservado
| [31-24] | <br />0x01<br />0x02<br />0x03 | **ID do compilador**<br />IAR<br />ARM<br />GNU |


## <a name="module-linker-control-file"></a>Ficheiro de controlo do linker do módulo

Ao construir um módulo, o preâmbulo do módulo deve ser colocado antes de qualquer outra secção de código. Um módulo deve ser construído com secções de código e dados independentes de posição. Os ficheiros de linker de exemplo específicos da porta estão no [apêndice](appendix.md).

## <a name="module-threadx-library"></a>Biblioteca Do Módulo ThreadX

Cada módulo deve ligar-se a uma biblioteca ThreadX especial, centrada em módulos. Esta biblioteca fornece acesso aos serviços ThreadX no código residente. A maior parte do acesso é realizado através dos ***ficheiros .c \* txm_.*** Segue-se um exemplo da chamada de acesso ao módulo para a função API ThreadX **_tx_thread_relinquish_* _ (em _*_ \_ txm_thread_relinquish.c \* ***).

```c
(_txm_module_kernel_call_dispatcher)(TXM_THREAD_RELINQUISH_CALL, 0, 0, 0);
```

Neste exemplo, o ponteiro de função fornecido pelo Gestor do Módulo é utilizado para chamar a função de despacho do Gestor do Módulo com o ID associado ao serviço ***tx_thread_relinquish.*** Este serviço não tem parâmetros.

## <a name="module-example"></a>Exemplo do módulo

Segue-se um exemplo da demonstração padrão da ThreadX sob a forma de um módulo. As principais diferenças entre a demonstração padrão da ThreadX e a demonstração do módulo são.

1. Substituição de ***tx_api.h** _ com _ *_txm_module.h_**
2. Adição de **#define TXM_MODULE** antes **_de txm_module.h_**
3. Substituição de ***main** _ e _ *tx_application_define** com **_demo_module_start_**
4. Declarando ponteiros para *objetos* ThreadX em vez dos próprios objetos.

```c
/* Specify that this is a module! */
#define TXM_MODULE

/* Include the ThreadX module header. */
#include "txm_module.h"

/* Define constants. */
#define DEMO_STACK_SIZE         1024
#define DEMO_BYTE_POOL_SIZE     9120
#define DEMO_BLOCK_POOL_SIZE    100
#define DEMO_QUEUE_SIZE         100

/* Define the pool space in the bss section of the module. ULONG is used to
   get word alignment. */
   
ULONG                   demo_module_pool_space[DEMO_BYTE_POOL_SIZE / 4];

/* Define the ThreadX object control block pointers. */

TX_THREAD               *thread_0;
TX_THREAD               *thread_1;
TX_THREAD               *thread_2;
TX_THREAD               *thread_3;
TX_THREAD               *thread_4;
TX_THREAD               *thread_5;
TX_THREAD               *thread_6;
TX_THREAD               *thread_7;
TX_QUEUE                *queue_0;
TX_SEMAPHORE            *semaphore_0;
TX_MUTEX                *mutex_0;
TX_EVENT_FLAGS_GROUP    *event_flags_0;
TX_BYTE_POOL            *byte_pool_0;
TX_BLOCK_POOL           *block_pool_0;


/* Define the counters used in the demo application. */
ULONG       thread_0_counter;
ULONG       thread_1_counter;
ULONG       thread_1_messages_sent;
ULONG       thread_2_counter;
ULONG       thread_2_messages_received;
ULONG       thread_3_counter;
ULONG       thread_4_counter;
ULONG       thread_5_counter;
ULONG       thread_6_counter;
ULONG       thread_7_counter;
ULONG       semaphore_0_puts;
ULONG       event_0_sets;
ULONG       queue_0_sends;

/* Define thread prototypes. */

void    thread_0_entry(ULONG thread_input);
void    thread_1_entry(ULONG thread_input);
void    thread_2_entry(ULONG thread_input);
void    thread_3_and_4_entry(ULONG thread_input);
void    thread_5_entry(ULONG thread_input);
void    thread_6_and_7_entry(ULONG thread_input);

/* Define notify functions. */

void semaphore_0_notify(TX_SEMAPHORE *semaphore_ptr)
{
    if (semaphore_ptr == semaphore_0)
        semaphore_0_puts++;
}


void event_0_notify(TX_EVENT_FLAGS_GROUP *event_flag_group_ptr)
{
    if (event_flag_group_ptr == event_flags_0)
        event_0_sets++;
}


void queue_0_notify(TX_QUEUE *queue_ptr)
{
    if (queue_ptr == queue_0)
        queue_0_sends++;
}

/* Define the module start function. */
void demo_module_start(ULONG id)
{
    CHAR *pointer;

    /* Allocate all the objects. In memory protection mode,
        modules cannot allocate control blocks within their
        own memory area so they cannot corrupt the resident
        portion of ThreadX by corrupting the control block(s). */
    txm_module_object_allocate(&thread_0, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_1, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_2, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_3, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_4, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_5, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_6, sizeof(TX_THREAD));
    txm_module_object_allocate(&thread_7, sizeof(TX_THREAD));
    txm_module_object_allocate(&queue_0, sizeof(TX_QUEUE));
    txm_module_object_allocate(&semaphore_0, sizeof(TX_SEMAPHORE));
    txm_module_object_allocate(&mutex_0, sizeof(TX_MUTEX));
    txm_module_object_allocate(&event_flags_0, sizeof(TX_EVENT_FLAGS_GROUP));
    txm_module_object_allocate(&byte_pool_0, sizeof(TX_BYTE_POOL));
    txm_module_object_allocate(&block_pool_0, sizeof(TX_BLOCK_POOL));

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(byte_pool_0, "module byte pool 0",
        demo_module_pool_space, DEMO_BYTE_POOL_SIZE);

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 0. */
    tx_thread_create(thread_0, "module thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through
        a ThreadX message queue. It is also interesting to note that
        these threads have a time slice. */
    tx_thread_create(thread_1, "module thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack and create thread 2. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_2, "module thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX
        counting semaphore. An interesting thing here is that both threads
        share the same instruction area. */
    tx_thread_create(thread_3, "module thread 3",
        thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 4. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_4, "module thread 4",
        thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag which
        will be set by thread 0. */
    tx_thread_create(thread_5, "module thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(thread_6, "module thread 6",
        thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack and create thread 7. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_STACK_SIZE, TX_NO_WAIT);
    tx_thread_create(thread_7, "module thread 7",
        thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(queue_0, "module queue 0", TX_1_ULONG, pointer,
        DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Register queue send callback. */
    tx_queue_send_notify(queue_0, queue_0_notify);

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(semaphore_0, "module semaphore 0", 1);

    /* Register semaphore put callback. */
    tx_semaphore_put_notify(semaphore_0, semaphore_0_notify);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(event_flags_0, "module event flags 0");

    /* Register event flag set callback. */
    tx_event_flags_set_notify(event_flags_0, event_0_notify);

    /* Create the mutex used by thread 6 and 7 without priority
        inheritance. */
    tx_mutex_create(mutex_0, "module mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(byte_pool_0, (VOID **) &pointer,
        DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool. */
    tx_block_pool_create(block_pool_0, "module block pool 0",
        sizeof(ULONG), pointer, DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block. */
    tx_block_allocate(block_pool_0, (VOID **) &pointer,
        TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);

}

/* Define all the threads. */

void thread_0_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wake up thread 5. */
        status = tx_event_flags_set(event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_1_entry(ULONG thread_input)
{
    UINT status;

    /* This thread simply sends messages to a queue shared by
       thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(queue_0, &thread_1_messages_sent,
            TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}

void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what
           we expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}

void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 3 and thread 4. As the loop
       below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}

void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;

    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(event_flags_0, 0x1, TX_OR_CLEAR,
                                        &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
       below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows that an
           owning thread may retrieve the mutex it owns multiple times. */
        status = tx_mutex_get(mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually release ownership
           since it was obtained twice. */
        status = tx_mutex_put(mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```

## <a name="building-modules"></a>Módulos de Construção

A construção de um módulo depende da utilização da cadeia de ferramentas. Consulte [o apêndice](appendix.md) para obter exemplos específicos da porta. As atividades comuns a todos os portos incluem o seguinte.

- Construção de uma biblioteca de módulos
- Construção da aplicação do módulo

Cada módulo é necessário para ter uma **txm_module_preamble** (configuração especificamente para o módulo) e a biblioteca do módulo (por exemplo, **_txm.a)._**
