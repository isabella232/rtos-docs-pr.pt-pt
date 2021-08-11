---
title: Capítulo 3 - Requisitos do Gestor de Módulos
description: Este artigo é uma descrição dos passos necessários para a construção do Gestor de Módulos ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6c4d0993284c8e0b8264020d721ac12bdfe8117df4480fb54ee4d5b20a1f677e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799188"
---
# <a name="chapter-3---module-manager-requirements"></a>Capítulo 3 - Requisitos do Gestor de Módulos

O Gestor de Módulos ThreadX reside na parte residente da aplicação juntamente com o ThreadX RTOS. É responsável por iniciar o módulo, bem como despachar e despachar todos os pedidos de módulos para serviços de API da ThreadX.

> [!NOTE]
> Os ficheiros de origem **do Gestor de** Módulos ThreadX (C e montagem) devem ser adicionados ao projeto da biblioteca ThreadX "**tx**".

São necessários os seguintes passos para a construção do Gestor de Módulos ThreadX (cada passo é descrito em maior detalhe abaixo).

1. O **TX_THREAD** bloco de controlo deve ser alargado para incluir informações sobre o módulo. A forma mais fácil de o conseguir é substituir a definição de **TX_THREAD_EXTENSION_2** no ficheiro **_tx_port.h_*_ pelo _TX_THREAD_EXTENSION_2*** encontrado em **_txm_module_port.h_**. Consulte [o apêndice](appendix.md) para obter extensões específicas da porta.

Extensão de exemplo:

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   As seguintes extensões devem ser definidas em ***tx_port.h***.

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. Adicione todos os ***ficheiros de \* txm_module_manager_*** C e montagem ao projeto da biblioteca ThreadX **_tx_**.
3. Reconstruir todas as bibliotecas e projetos executáveis. Se o NetX Duo for necessário, todo o código do Módulo e do Gestor do Módulo C deve ser construído com **TXM_MODULE_ENABLE_NETX_DUO** definido.

## <a name="module-manager-sources"></a>Fontes do Gestor de Módulos

O Gestor de Módulos ThreadX tem um conjunto de ficheiros de origem que foram concebidos para serem ligados e localizados diretamente com o código ThreadX residente. Estes ficheiros fornecem a capacidade de lançar um módulo e field subsequentes pedidos de API ThreadX a partir do módulo. Os ficheiros do gestor do módulo são os seguintes.

| **Nome do arquivo** |  **Conteúdos** |
|-------------- | ------------- |
| ***txm_module.h*** | Incluir o ficheiro que define as informações do módulo (também incluída no código fonte do módulo). |
| ***txm_module_manager_dispatch.h*** | Incluir ficheiro que define funções de ajudante de despacho.|
| ***txm_module_manager_util.h*** | Incluir ficheiro que define macros de ajuda interna & funções. |
| ***txm_module_port.h*** | Incluir ficheiro que define informações específicas do módulo por porta (também incluída no código fonte do módulo). |
| ***tx_initialize_low_level. \[ s,S,68 \]** _ | Substitui o ficheiro da biblioteca ThreadX existente. Tabela de vetores atualizada e manipuladores de vetores adicionais para o gestor de módulos e exceções de memória. _This ficheiro é apenas em Córtex-A7/ARM, Córtex-M7/ARM, Córtex-R4/ARM, Córtex-R4/IAR, MCF544x/GHS, RX63/IAR, RX65N/IAR.*|
| ***tx_thread_context_restore.s** _ | Substitui o ficheiro da biblioteca ThreadX existente. Restaurar o contexto do fio após interromper o processamento. _This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.*|
| ***tx_thread_schedule. \[ s,S,68\]*** | Substitui o ficheiro da biblioteca ThreadX existente. Código de programador alargado, que neste caso é usado para atualizar registos de gestão de memória. |
| ***tx_thread_stack_build.s_** | Substitui o ficheiro da biblioteca ThreadX existente. Constrói a estrutura da pilha de um fio. _This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_thread_stack_build. \[ s,S,68\]*** | Constrói todas as pilhas iniciais do módulo, inclui a configuração para acesso de dados independente à posição. |
| ***txm_module_manager_user_mode_entry. \[ s,S \]** _ | Permite que o módulo entre no modo kernel. _This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_alignment_adjust.c*** | Lida com os requisitos de alinhamento específicos da porta.|
| ***txm_module_manager_application_request.c*** | Trata dos pedidos específicos da aplicação ao código residente. |
| ***txm_module_manager_callback_request.c*** | Envia um pedido de retorno para um módulo. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | Processa a chamada de notificação de bandeiras de evento da ThreadX. |
| ***txm_module_manager_external_memory_enable.c*** | Cria uma entrada na tabela de gestão de memória para um espaço de memória partilhada a que o módulo pode aceder. |
| ***txm_module_manager_file_load.c*** | Atribui e carrega um ficheiro binário de módulos na área de memória do módulo e prepara-o para a execução. |
| ***txm_module_manager_in_place_load.c*** | Atribui a área de dados do módulo e prepara-se para a execução do módulo a partir do endereço de código fornecido. |
| ***txm_module_manager_initialize.c*** | Inicializa o Gestor do Módulo, incluindo a especificação da área de memória do módulo disponível para módulos de carregamento e funcionamento. |
| ***txm_module_manager_initialize_mmu.c** | Inicialize a MMU. Os utilizadores podem editar este ficheiro de acordo com o seu mapa de memória. _This ficheiro está apenas no Córtex-A7/ARM* |
| ***txm_module_manager_mm_initialize.c** | Inicializar MPU/MMU. Os utilizadores podem editar este ficheiro de acordo com o seu mapa de memória. _This ficheiro está apenas no Córtex-A7/ARM* |
| ***txm_module_manager_kernel_dispatch.c*** | Lida com os pedidos da API do módulo, com base no ID do pedido. |
| ***txm_module_manager_maximum_module_priority_set.c*** | Define a prioridade máxima do fio permitido num módulo. |
| ***txm_module_manager_memory_fault_handler.c*** | Lida com falhas de memória detetadas num módulo de execução. |
| ***txm_module_manager_memory_fault_notify.c*** | Regista uma chamada de notificação de aplicação sempre que ocorre uma falha de memória. |
| ***txm_module_manager_memory_load.c*** | Aloca e carrega o código e os dados de um módulo e prepara o módulo para a execução. |
| ***txm_module_manager_mm_register_setup.c*** | Configura registos MPU/MMU para o módulo com base no local onde o código e os dados são carregados. |
| ***txm_module_manager_object_allocate.c*** | Aloca a memória para um objeto de módulo. |
| ***txm_module_manager_object_deallocate.c*** | Dealloca memória para um objeto de módulo. |
| ***txm_module_manager_object_pointer_get.c*** | Procura o tipo e o nome do objeto fornecidos e, se encontrado, devolve o ponteiro do objeto. |
| ***txm_module_manager_object_pointer_get_extended.c*** | Procura o tipo e o nome do objeto fornecidos e, se encontrado, devolve o ponteiro do objeto. Comprimento do nome especificado para segurança. |
| ***txm_module_manager_object_pool_create.c***  | Cria um conjunto de objetos fora da área de dados do módulo que as aplicações do módulo podem alocar. |
| ***txm_module_manager_properties_get.c*** | Obtém as propriedades do módulo especificado. |
| ***txm_module_manager_queue_notify_trampoline.c*** | Processa a chamada de notificação de fila da ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | Processa a chamada de notificação de semáforo da ThreadX.|
| ***txm_module_manager_start.c*** | Inicia a execução de um módulo. |
| ***txm_module_manager_stop.c*** | Para a execução de um módulo. |
| ***txm_module_manager_thread_create.c*** | Cria todos os fios do módulo. |
| ***txm_module_manager_thread_notify_trampoline.c*** | Processa a chamada de notificação de entrada/saída da ThreadX. |
| ***txm_module_manager_thread_reset.c*** | Reinicie um fio de módulo. |
| ***txm_module_manager_timer_notify_trampoline.c*** | Processa expirações do temporizador da ThreadX. |
| ***txm_module_manager_unload.c*** | Descarrega o módulo da área de memória do módulo. |
| ***txm_module_manager_util.c*** | Funções de ajudante interno para gerente. |

## <a name="module-manager-initialization"></a>Inicialização do Gestor de Módulos

A parte residente da aplicação é responsável por chamar a função de inicialização do Gestor do Módulo ***txm_module_manager_initialize***. Esta função configura as estruturas internas para módulos de carga e descarga, incluindo a configuração da área de memória utilizada para a atribuição da memória do módulo.

## <a name="module-manager-loading"></a>Carregamento do gestor de módulos

O Gestor de Módulos pode carregar os módulos dinamicamente na memória do módulo a partir de ficheiros de módulos binários ou de uma secção de código do módulo que já está presente na área do código residente. Além disso, o gestor do módulo pode executar código no lugar, ou seja, apenas os dados do módulo são alocados na memória do módulo e a execução do código é feita no lugar. Estão disponíveis as seguintes funções de API de carga do Gestor de Módulos.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

A versão protegida pela memória do Gestor do Módulo também garante que o módulo está carregado com o alinhamento adequado e os registos de gestão da memória são configurados corretamente para cada módulo. Quando a proteção da memória é ativada através das opções de preâmbulo do módulo, o acesso à memória do módulo é restrito às áreas do código do módulo e dos dados.

## <a name="module-manager-starting"></a>Início do Gestor de Módulos

O Gestor de Módulos inicia a execução de um módulo previamente carregado através da função ***API txm_module_manager_start.*** Para iniciar a execução do módulo, esta função cria um fio que entra no módulo no local de partida especificado no preâmbulo do módulo. A prioridade e o tamanho da pilha deste fio também estão especificados no preâmbulo do módulo.

## <a name="module-manager-stopping"></a>Paragem do gestor de módulos

O Gestor do Módulo termina a execução de um módulo previamente carregado e executado através da função ***txm_module_manager_stop.*** Esta função API termina primeiro e elimina o fio inicial de partida. Se o preâmbulo do módulo especificar um fio de paragem, este fio é criado e executado. O Gestor do Módulo aguarda um período de tempo fixo para que o fio de paragem esteja concluído. Uma vez concluído, todos os recursos do sistema criados pelo módulo são eliminados e o módulo é colocado num estado dormente, a partir do qual pode ser reiniciado ou descarregado.

## <a name="module-manager-unloading"></a>Descarregamento do Gestor de Módulos

O Gestor do Módulo descarrega um módulo previamente carregado mas não executando através da função ***txm_module_manager_unload.*** Esta API liberta toda a memória associada ao módulo, libertando-a para utilização com outro módulo no futuro.

## <a name="module-manager-requests"></a>Pedidos do Gestor de Módulos

Os pedidos feitos por módulos ao Gestor do Módulo são feitos através de macros em ***txm_module.h*** que mapeiam todas as chamadas da ThreadX para chamar a função de despacho do Gestor do Módulo através de um ponteiro de função fornecido ao módulo pelo Gestor do Módulo.

Serviços adicionais específicos de aplicações feitos através do módulo que chama ***txm_module_application_request*** são tratados pelo mesmo mecanismo macro utilizado para a API ThreadX. Por predefinição, esta função de manuseamento no Gestor do Módulo está vazia e concebida de modo a que a aplicação adicione o código necessário para processar os pedidos específicos da aplicação.

Se o pedido não for implementado pelo Gestor do Módulo, o Gestor do Módulo devolve um valor de **TX_NOT_AVAILABLE** estado de erro. Este código de erro também é devolvido se o módulo solicitar uma operação que esteja fora do âmbito de acesso do módulo. Por exemplo, não é permitido criar um módulo com o bloco de controlo do temporizador ou o endereço de retorno fora da área de código do módulo.

## <a name="module-manager-example"></a>Exemplo do Gestor de Módulos

Segue-se um exemplo do código do Gestor de Módulos que lança o módulo de exemplo previamente definido no Capítulo 2. Presume-se que o módulo já está carregado, presumivelmente pelo depurador, no endereço ROM 0x00800000.

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a>Edifício do Gestor de Módulos

Os ***ficheiros \* de*** origem txm_module_manager_ devem ser adicionados à biblioteca ThreadX.

Uma aplicação Do Gestor de Módulos ThreadX é efetivamente a mesma que uma aplicação padrão da ThreadX, que é um ou mais ficheiros de aplicação ligados juntamente com a biblioteca ThreadX ***tx.a***. A construção de uma aplicação de gestor de módulos depende da utilização da cadeia de ferramentas. Consulte [o apêndice](appendix.md) para obter exemplos específicos da porta.
