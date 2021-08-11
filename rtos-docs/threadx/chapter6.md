---
title: Capítulo 6 - Sistema de Demonstração para Azure RTOS ThreadX
description: Este capítulo contém uma descrição do sistema de demonstração que é entregue com todos os pacotes de suporte ao processador Azure RTOS ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67054d67d0a6babc50a489c4ec4b738abf3efccab10060d307106e8344b00d02
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783378"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a>Capítulo 6 - Sistema de Demonstração para Azure RTOS ThreadX

Este capítulo contém uma descrição do sistema de demonstração que é entregue com todos os pacotes de suporte ao processador Azure RTOS ThreadX.

## <a name="overview"></a>Descrição Geral

Cada distribuição de produto ThreadX contém um sistema de demonstração que funciona em todos os microprocessadores suportados.

Este sistema de exemplo é definido no ficheiro de distribuição ***demo_threadx.c*** e foi concebido para ilustrar como o ThreadX é usado num ambiente multi-liscado incorporado. A demonstração consiste em inicialização, oito fios, uma piscina de byte, uma piscina de blocos, uma fila, um semáforo, um mutex e um grupo de bandeiras de evento.

> [!NOTE]
> *Com exceção do tamanho da pilha do fio, a aplicação de demonstração é idêntica em todos os processadores suportados pela ThreadX.*

A lista completa de ***demo_threadx.c,*** incluindo os números de linha referenciados ao longo do resto deste capítulo.

## <a name="application-define"></a>Definição de aplicação

A função ***tx_application_define*** executa após a inicialização básica do ThreadX estar concluída. É responsável pela criação de todos os recursos iniciais do sistema, incluindo fios, filas, semáforos, mutantes, bandeiras de eventos e piscinas de memória.

O sistema de demonstração ***tx_application_define** _ (_line números 60-164*) cria os objetos de demonstração na seguinte ordem:

- byte_pool_0
- thread_0
- thread_1
- thread_2
- thread_3
- thread_4
- thread_5
- thread_6
- thread_7
- queue_0
- semaphore_0
- event_flags_0
- mutex_0
- block_pool_0

O sistema de demonstração não cria quaisquer outros objetos ThreadX adicionais. No entanto, uma aplicação real pode criar objetos do sistema durante o tempo de execução dentro dos fios de execução.

### <a name="initial-execution"></a>Execução Inicial

Todos os fios são criados com a opção **TX_AUTO_START.** Isto os deixa inicialmente prontos para a execução. Após ***tx_application_define*** completa, o controlo é transferido para o programador de linhas e daí para cada fio individual.

A ordem pela qual os fios executam é determinada pela sua prioridade e pela ordem que foram criadas. No sistema de demonstração, ***thread_0*** executa primeiro porque tem a maior prioridade –*foi criado com uma prioridade de 1*). Após ***thread_0*** suspensão, ***thread_5*** é executado, seguido da execução de ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _* _thread_7_**, ***thread_1**_, e finalmente _*_thread_2_**.

> [!NOTE]
> *Apesar **de thread_3** e **thread_4** terem a mesma prioridade (ambas criadas com uma prioridade de 8), **thread_3** executa primeiro. Isto porque **thread_3** foi criado e pronto antes **de thread_4.** Fios de igual prioridade executam de forma FIFO.*

## <a name="thread-0"></a>Fio 0

A função ***thread_0_entry*** marca o ponto de entrada do fio *(linhas 167-190).* ***Thread_0*** é o primeiro fio no sistema de demonstração a executar. O seu processamento é simples: incrementa o seu contador, dorme por 10 tiques temporizadores, define uma bandeira de evento para acordar ***thread_5,*** e depois repete a sequência.

***Thread_0*** é o fio de prioridade mais alto do sistema. Quando o seu sono solicitado expirar, ele preempia qualquer outro fio de execução na demonstração.

## <a name="thread-1"></a>Fio 1

A função ***thread_1_entry** _ marca o ponto de entrada do fio _(linhas 193-216 *). ***Thread_1*** é o penúltimo fio do sistema de demonstração a executar. O seu processamento consiste em incrementar o seu contador, enviar uma mensagem para ***thread_2*** (através* de* ***queue_0),*** e repetir a sequência. Note que ***thread_1**_ suspende sempre _*_que queue_0_*_ fique cheio (_line 207*).

## <a name="thread-2"></a>Fio 2

A função ***thread_2_entry*** marca o ponto de entrada do fio *(linhas 219-243).* ***Thread_2*** é o último fio no sistema de demonstração a executar. O seu processamento consiste em incrementar o seu contador, receber uma mensagem de ***thread_1*** (através ***de queue_0),*** e repetir a sequência. Note que ***thread_2** _ suspende sempre _*_que queue_0_*_ fique vazia (_line 233*).

Embora ***thread_1** _ e _ *_thread_2_** partilham a menor prioridade no sistema de demonstração (prioridade* 16*), eles *Threads 3 e 4*

são também os únicos fios que estão prontos para a execução a maior parte do tempo. São também os únicos fios criados com corte de tempo *(linhas 87 e 93).* Cada fio é autorizado a executar por um máximo de 4 carraças de temporizador antes que o outro fio seja executado.

## <a name="threads-3-and-4"></a>Fios 3 e 4

A função ***thread_3_and_4_entry*** marca o ponto de entrada de ambos ***thread_3** _ e _ *_thread_4_** (linhas 246-280). Ambos os fios têm uma prioridade de 8, o que faz deles o terceiro e quarto fios no sistema de demonstração a executar. O processamento para cada fio é o mesmo: incrementando o seu contador, ficando ***semaphore_0,*** dormindo por 2 carraças temporizador, libertando ***semaphore_0***, e repetindo a sequência. Note que cada fio suspende sempre ***que semaphore_0*** não estiver disponível (linha 264).

Também ambos os fios utilizam a mesma função para o seu processamento principal.
Isto não apresenta problemas porque ambos têm a sua própria pilha única, e C é naturalmente reentrante. Cada fio determina qual é por exame do parâmetro de entrada do fio (linha 258), que é configurado quando são criados (linhas 102 e 109).

> [!NOTE]
> *Também é razoável obter o ponto de linha atual durante a execução do fio e compará-lo com o endereço do bloco de controlo para determinar a identidade do fio.*

## <a name="thread-5"></a>Fio 5

A função ***thread_5_entry*** marca o ponto de entrada do fio (linhas 283-305). ***Thread_5*** é o segundo fio condutor do sistema de demonstração a executar. O seu processamento consiste em incrementar o seu contador, obter uma bandeira de evento de ***thread_0*** (através ***de event_flags_0),*** e repetir a sequência. Note que ***thread_5*** suspende sempre que a bandeira do evento em ***event_flags_0*** não estiver disponível (linha 298).

## <a name="threads-6-and-7"></a>Fios 6 e 7

A função ***thread_6_and_7_entry*** marca o ponto de entrada de ambos ***thread_6** _ e _ *_thread_7_** (linhas 307-358). Ambos os fios têm uma prioridade de 8, o que faz deles o quinto e sexto fios do sistema de demonstração a executar. O processamento para cada fio é o mesmo: incrementando o seu contador, ficando ***mutex_0*** duas vezes, dormindo por 2 carraças temporizador, libertando ***mutex_0*** duas vezes, e repetindo a sequência. Note que cada fio suspende sempre ***que mutex_0*** não estiver disponível (linha 325).

Também ambos os fios utilizam a mesma função para o seu processamento principal. Isto não apresenta problemas porque ambos têm a sua própria pilha única, e C é naturalmente reentrante.
Cada fio determina qual é por exame do parâmetro de entrada do fio (linha 319), que é configurado quando são criados (linhas 126 e 133).

## <a name="observing-the-demonstration"></a>Observando a Demonstração

Cada um dos fios de demonstração incrementa o seu próprio contador único.
Podem ser examinados os seguintes contadores para verificar o funcionamento da demonstração:

- thread_0_counter
- thread_1_counter
- thread_2_counter
- thread_3_counter
- thread_4_counter
- thread_5_counter
- thread_6_counter
- thread_7_counter

Cada um destes balcões deve continuar a aumentar à medida que a demonstração executa, com ***thread_1_counter** _ e _ *_thread_2_counter_** aumentando ao ritmo mais rápido.

## <a name="distribution-file-demo_threadxc"></a>Ficheiro de distribuição: demo_threadx.c

Esta secção apresenta a lista completa de ***demo_threadx.c,*** incluindo os números de linha referenciados ao longo deste capítulo.

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
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

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

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
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
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
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

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
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
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
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
