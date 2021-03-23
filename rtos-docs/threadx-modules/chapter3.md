---
title: Capítulo 3 - Requisitos do Gestor de Módulos
description: Este artigo é uma descrição dos passos necessários para a construção do Gestor de Módulos ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826594"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="259a2-103">Capítulo 3 - Requisitos do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="259a2-104">O Gestor de Módulos ThreadX reside na parte residente da aplicação juntamente com o ThreadX RTOS.</span><span class="sxs-lookup"><span data-stu-id="259a2-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="259a2-105">É responsável por iniciar o módulo, bem como despachar e despachar todos os pedidos de módulos para serviços de API da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="259a2-106">Os ficheiros de origem **do Gestor de** Módulos ThreadX (C e montagem) devem ser adicionados ao projeto da biblioteca ThreadX "**tx**".</span><span class="sxs-lookup"><span data-stu-id="259a2-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="259a2-107">São necessários os seguintes passos para a construção do Gestor de Módulos ThreadX (cada passo é descrito em maior detalhe abaixo).</span><span class="sxs-lookup"><span data-stu-id="259a2-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="259a2-108">O **TX_THREAD** bloco de controlo deve ser alargado para incluir informações sobre o módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="259a2-109">A forma mais fácil de o conseguir é substituir a definição de **TX_THREAD_EXTENSION_2** no ficheiro **_tx_port.h_\*_ pelo _TX_THREAD_EXTENSION_2**\* encontrado em **_txm_module_port.h_**.</span><span class="sxs-lookup"><span data-stu-id="259a2-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="259a2-110">Consulte [o apêndice](appendix.md) para obter extensões específicas da porta.</span><span class="sxs-lookup"><span data-stu-id="259a2-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="259a2-111">Extensão de exemplo:</span><span class="sxs-lookup"><span data-stu-id="259a2-111">Example extension:</span></span>

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

   <span data-ttu-id="259a2-112">As seguintes extensões devem ser definidas em ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="259a2-112">The following extensions must be defined in ***tx_port.h***.</span></span>

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

2. <span data-ttu-id="259a2-113">Adicione todos os ***ficheiros de \* txm_module_manager_*** C e montagem ao projeto da biblioteca ThreadX **_tx_**.</span><span class="sxs-lookup"><span data-stu-id="259a2-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="259a2-114">Reconstruir todas as bibliotecas e projetos executáveis.</span><span class="sxs-lookup"><span data-stu-id="259a2-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="259a2-115">Se o NetX Duo for necessário, todo o código do Módulo e do Gestor do Módulo C deve ser construído com **TXM_MODULE_ENABLE_NETX_DUO** definido.</span><span class="sxs-lookup"><span data-stu-id="259a2-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="259a2-116">Fontes do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-116">Module Manager sources</span></span>

<span data-ttu-id="259a2-117">O Gestor de Módulos ThreadX tem um conjunto de ficheiros de origem que foram concebidos para serem ligados e localizados diretamente com o código ThreadX residente.</span><span class="sxs-lookup"><span data-stu-id="259a2-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="259a2-118">Estes ficheiros fornecem a capacidade de lançar um módulo e field subsequentes pedidos de API ThreadX a partir do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="259a2-119">Os ficheiros do gestor do módulo são os seguintes.</span><span class="sxs-lookup"><span data-stu-id="259a2-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="259a2-120">**Nome do arquivo**</span><span class="sxs-lookup"><span data-stu-id="259a2-120">**File Name**</span></span> |  <span data-ttu-id="259a2-121">**Conteúdos**</span><span class="sxs-lookup"><span data-stu-id="259a2-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="259a2-122">***txm_module.h***</span><span class="sxs-lookup"><span data-stu-id="259a2-122">***txm_module.h***</span></span> | <span data-ttu-id="259a2-123">Incluir o ficheiro que define as informações do módulo (também incluída no código fonte do módulo).</span><span class="sxs-lookup"><span data-stu-id="259a2-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="259a2-124">***txm_module_manager_dispatch.h***</span><span class="sxs-lookup"><span data-stu-id="259a2-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="259a2-125">Incluir ficheiro que define funções de ajudante de despacho.</span><span class="sxs-lookup"><span data-stu-id="259a2-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="259a2-126">***txm_module_manager_util.h***</span><span class="sxs-lookup"><span data-stu-id="259a2-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="259a2-127">Incluir ficheiro que define macros de ajuda interna & funções.</span><span class="sxs-lookup"><span data-stu-id="259a2-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="259a2-128">***txm_module_port.h***</span><span class="sxs-lookup"><span data-stu-id="259a2-128">***txm_module_port.h***</span></span> | <span data-ttu-id="259a2-129">Incluir ficheiro que define informações específicas do módulo por porta (também incluída no código fonte do módulo).</span><span class="sxs-lookup"><span data-stu-id="259a2-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="259a2-130">\***tx_initialize_low_level. \[ s,S,68 \]** _</span><span class="sxs-lookup"><span data-stu-id="259a2-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="259a2-131">Substitui o ficheiro da biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="259a2-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="259a2-132">Tabela de vetores atualizada e manipuladores de vetores adicionais para o gestor de módulos e exceções de memória.</span><span class="sxs-lookup"><span data-stu-id="259a2-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="259a2-133">_This ficheiro é apenas em Córtex-A7/ARM, Córtex-M7/ARM, Córtex-R4/ARM, Córtex-R4/IAR, MCF544x/GHS, RX63/IAR, RX65N/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="259a2-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="259a2-134">\***tx_thread_context_restore.s** _</span><span class="sxs-lookup"><span data-stu-id="259a2-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="259a2-135">Substitui o ficheiro da biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="259a2-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="259a2-136">Restaurar o contexto do fio após interromper o processamento.</span><span class="sxs-lookup"><span data-stu-id="259a2-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="259a2-137">_This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="259a2-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="259a2-138">***tx_thread_schedule. \[ s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="259a2-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="259a2-139">Substitui o ficheiro da biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="259a2-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="259a2-140">Código de programador alargado, que neste caso é usado para atualizar registos de gestão de memória.</span><span class="sxs-lookup"><span data-stu-id="259a2-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="259a2-141">\***tx_thread_stack_build.s_**</span><span class="sxs-lookup"><span data-stu-id="259a2-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="259a2-142">Substitui o ficheiro da biblioteca ThreadX existente.</span><span class="sxs-lookup"><span data-stu-id="259a2-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="259a2-143">Constrói a estrutura da pilha de um fio.</span><span class="sxs-lookup"><span data-stu-id="259a2-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="259a2-144">_This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="259a2-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="259a2-145">***txm_module_manager_thread_stack_build. \[ s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="259a2-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="259a2-146">Constrói todas as pilhas iniciais do módulo, inclui a configuração para acesso de dados independente à posição.</span><span class="sxs-lookup"><span data-stu-id="259a2-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="259a2-147">\***txm_module_manager_user_mode_entry. \[ s,S \]** _</span><span class="sxs-lookup"><span data-stu-id="259a2-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="259a2-148">Permite que o módulo entre no modo kernel.</span><span class="sxs-lookup"><span data-stu-id="259a2-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="259a2-149">_This ficheiro está apenas no Córtex-A7/ARM, Córtex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="259a2-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="259a2-150">***txm_module_manager_alignment_adjust.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="259a2-151">Lida com os requisitos de alinhamento específicos da porta.</span><span class="sxs-lookup"><span data-stu-id="259a2-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="259a2-152">***txm_module_manager_application_request.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="259a2-153">Trata dos pedidos específicos da aplicação ao código residente.</span><span class="sxs-lookup"><span data-stu-id="259a2-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="259a2-154">***txm_module_manager_callback_request.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="259a2-155">Envia um pedido de retorno para um módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="259a2-156">***txm_module_manager_event_flags_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="259a2-157">Processa a chamada de notificação de bandeiras de evento da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="259a2-158">***txm_module_manager_external_memory_enable.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="259a2-159">Cria uma entrada na tabela de gestão de memória para um espaço de memória partilhada a que o módulo pode aceder.</span><span class="sxs-lookup"><span data-stu-id="259a2-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="259a2-160">***txm_module_manager_file_load.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="259a2-161">Atribui e carrega um ficheiro binário de módulos na área de memória do módulo e prepara-o para a execução.</span><span class="sxs-lookup"><span data-stu-id="259a2-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="259a2-162">***txm_module_manager_in_place_load.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="259a2-163">Atribui a área de dados do módulo e prepara-se para a execução do módulo a partir do endereço de código fornecido.</span><span class="sxs-lookup"><span data-stu-id="259a2-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="259a2-164">***txm_module_manager_initialize.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="259a2-165">Inicializa o Gestor do Módulo, incluindo a especificação da área de memória do módulo disponível para módulos de carregamento e funcionamento.</span><span class="sxs-lookup"><span data-stu-id="259a2-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="259a2-166">\***txm_module_manager_initialize_mmu.c**</span><span class="sxs-lookup"><span data-stu-id="259a2-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="259a2-167">Inicialize a MMU.</span><span class="sxs-lookup"><span data-stu-id="259a2-167">Initialize MMU.</span></span> <span data-ttu-id="259a2-168">Os utilizadores podem editar este ficheiro de acordo com o seu mapa de memória.</span><span class="sxs-lookup"><span data-stu-id="259a2-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="259a2-169">_This ficheiro está apenas no Córtex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="259a2-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="259a2-170">\***txm_module_manager_mm_initialize.c**</span><span class="sxs-lookup"><span data-stu-id="259a2-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="259a2-171">Inicializar MPU/MMU.</span><span class="sxs-lookup"><span data-stu-id="259a2-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="259a2-172">Os utilizadores podem editar este ficheiro de acordo com o seu mapa de memória.</span><span class="sxs-lookup"><span data-stu-id="259a2-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="259a2-173">_This ficheiro está apenas no Córtex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="259a2-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="259a2-174">***txm_module_manager_kernel_dispatch.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="259a2-175">Lida com os pedidos da API do módulo, com base no ID do pedido.</span><span class="sxs-lookup"><span data-stu-id="259a2-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="259a2-176">***txm_module_manager_maximum_module_priority_set.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="259a2-177">Define a prioridade máxima do fio permitido num módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="259a2-178">***txm_module_manager_memory_fault_handler.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="259a2-179">Lida com falhas de memória detetadas num módulo de execução.</span><span class="sxs-lookup"><span data-stu-id="259a2-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="259a2-180">***txm_module_manager_memory_fault_notify.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="259a2-181">Regista uma chamada de notificação de aplicação sempre que ocorre uma falha de memória.</span><span class="sxs-lookup"><span data-stu-id="259a2-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="259a2-182">***txm_module_manager_memory_load.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="259a2-183">Aloca e carrega o código e os dados de um módulo e prepara o módulo para a execução.</span><span class="sxs-lookup"><span data-stu-id="259a2-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="259a2-184">***txm_module_manager_mm_register_setup.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="259a2-185">Configura registos MPU/MMU para o módulo com base no local onde o código e os dados são carregados.</span><span class="sxs-lookup"><span data-stu-id="259a2-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="259a2-186">***txm_module_manager_object_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="259a2-187">Aloca a memória para um objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="259a2-188">***txm_module_manager_object_deallocate.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="259a2-189">Dealloca memória para um objeto de módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="259a2-190">***txm_module_manager_object_pointer_get.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="259a2-191">Procura o tipo e o nome do objeto fornecidos e, se encontrado, devolve o ponteiro do objeto.</span><span class="sxs-lookup"><span data-stu-id="259a2-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="259a2-192">***txm_module_manager_object_pointer_get_extended.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="259a2-193">Procura o tipo e o nome do objeto fornecidos e, se encontrado, devolve o ponteiro do objeto.</span><span class="sxs-lookup"><span data-stu-id="259a2-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="259a2-194">Comprimento do nome especificado para segurança.</span><span class="sxs-lookup"><span data-stu-id="259a2-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="259a2-195">***txm_module_manager_object_pool_create.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="259a2-196">Cria um conjunto de objetos fora da área de dados do módulo que as aplicações do módulo podem alocar.</span><span class="sxs-lookup"><span data-stu-id="259a2-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="259a2-197">***txm_module_manager_properties_get.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="259a2-198">Obtém as propriedades do módulo especificado.</span><span class="sxs-lookup"><span data-stu-id="259a2-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="259a2-199">***txm_module_manager_queue_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="259a2-200">Processa a chamada de notificação de fila da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="259a2-201">***txm_module_manager_semaphore_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="259a2-202">Processa a chamada de notificação de semáforo da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="259a2-203">***txm_module_manager_start.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="259a2-204">Inicia a execução de um módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="259a2-205">***txm_module_manager_stop.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="259a2-206">Para a execução de um módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="259a2-207">***txm_module_manager_thread_create.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="259a2-208">Cria todos os fios do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-208">Creates all module threads.</span></span> |
| <span data-ttu-id="259a2-209">***txm_module_manager_thread_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="259a2-210">Processa a chamada de notificação de entrada/saída da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="259a2-211">***txm_module_manager_thread_reset.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="259a2-212">Reinicie um fio de módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-212">Reset a module thread.</span></span> |
| <span data-ttu-id="259a2-213">***txm_module_manager_timer_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="259a2-214">Processa expirações do temporizador da ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="259a2-215">***txm_module_manager_unload.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="259a2-216">Descarrega o módulo da área de memória do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="259a2-217">***txm_module_manager_util.c***</span><span class="sxs-lookup"><span data-stu-id="259a2-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="259a2-218">Funções de ajudante interno para gerente.</span><span class="sxs-lookup"><span data-stu-id="259a2-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="259a2-219">Inicialização do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-219">Module Manager initialization</span></span>

<span data-ttu-id="259a2-220">A parte residente da aplicação é responsável por chamar a função de inicialização do Gestor do Módulo ***txm_module_manager_initialize***.</span><span class="sxs-lookup"><span data-stu-id="259a2-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="259a2-221">Esta função configura as estruturas internas para módulos de carga e descarga, incluindo a configuração da área de memória utilizada para a atribuição da memória do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="259a2-222">Carregamento do gestor de módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-222">Module Manager loading</span></span>

<span data-ttu-id="259a2-223">O Gestor de Módulos pode carregar os módulos dinamicamente na memória do módulo a partir de ficheiros de módulos binários ou de uma secção de código do módulo que já está presente na área do código residente.</span><span class="sxs-lookup"><span data-stu-id="259a2-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="259a2-224">Além disso, o gestor do módulo pode executar código no lugar, ou seja, apenas os dados do módulo são alocados na memória do módulo e a execução do código é feita no lugar.</span><span class="sxs-lookup"><span data-stu-id="259a2-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="259a2-225">Estão disponíveis as seguintes funções de API de carga do Gestor de Módulos.</span><span class="sxs-lookup"><span data-stu-id="259a2-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="259a2-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="259a2-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="259a2-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="259a2-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="259a2-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="259a2-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="259a2-229">A versão protegida pela memória do Gestor do Módulo também garante que o módulo está carregado com o alinhamento adequado e os registos de gestão da memória são configurados corretamente para cada módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="259a2-230">Quando a proteção da memória é ativada através das opções de preâmbulo do módulo, o acesso à memória do módulo é restrito às áreas do código do módulo e dos dados.</span><span class="sxs-lookup"><span data-stu-id="259a2-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="259a2-231">Início do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-231">Module Manager starting</span></span>

<span data-ttu-id="259a2-232">O Gestor de Módulos inicia a execução de um módulo previamente carregado através da função ***API txm_module_manager_start.***</span><span class="sxs-lookup"><span data-stu-id="259a2-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="259a2-233">Para iniciar a execução do módulo, esta função cria um fio que entra no módulo no local de partida especificado no preâmbulo do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="259a2-234">A prioridade e o tamanho da pilha deste fio também estão especificados no preâmbulo do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="259a2-235">Paragem do gestor de módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-235">Module Manager stopping</span></span>

<span data-ttu-id="259a2-236">O Gestor do Módulo termina a execução de um módulo previamente carregado e executado através da função ***txm_module_manager_stop.***</span><span class="sxs-lookup"><span data-stu-id="259a2-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="259a2-237">Esta função API termina primeiro e elimina o fio inicial de partida.</span><span class="sxs-lookup"><span data-stu-id="259a2-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="259a2-238">Se o preâmbulo do módulo especificar um fio de paragem, este fio é criado e executado.</span><span class="sxs-lookup"><span data-stu-id="259a2-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="259a2-239">O Gestor do Módulo aguarda um período de tempo fixo para que o fio de paragem esteja concluído.</span><span class="sxs-lookup"><span data-stu-id="259a2-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="259a2-240">Uma vez concluído, todos os recursos do sistema criados pelo módulo são eliminados e o módulo é colocado num estado dormente, a partir do qual pode ser reiniciado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="259a2-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="259a2-241">Descarregamento do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-241">Module Manager unloading</span></span>

<span data-ttu-id="259a2-242">O Gestor do Módulo descarrega um módulo previamente carregado mas não executando através da função ***txm_module_manager_unload.***</span><span class="sxs-lookup"><span data-stu-id="259a2-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="259a2-243">Esta API liberta toda a memória associada ao módulo, libertando-a para utilização com outro módulo no futuro.</span><span class="sxs-lookup"><span data-stu-id="259a2-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="259a2-244">Pedidos do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-244">Module Manager requests</span></span>

<span data-ttu-id="259a2-245">Os pedidos feitos por módulos ao Gestor do Módulo são feitos através de macros em ***txm_module.h*** que mapeiam todas as chamadas da ThreadX para chamar a função de despacho do Gestor do Módulo através de um ponteiro de função fornecido ao módulo pelo Gestor do Módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="259a2-246">Serviços adicionais específicos de aplicações feitos através do módulo que chama ***txm_module_application_request*** são tratados pelo mesmo mecanismo macro utilizado para a API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="259a2-247">Por predefinição, esta função de manuseamento no Gestor do Módulo está vazia e concebida de modo a que a aplicação adicione o código necessário para processar os pedidos específicos da aplicação.</span><span class="sxs-lookup"><span data-stu-id="259a2-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="259a2-248">Se o pedido não for implementado pelo Gestor do Módulo, o Gestor do Módulo devolve um valor de **TX_NOT_AVAILABLE** estado de erro.</span><span class="sxs-lookup"><span data-stu-id="259a2-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="259a2-249">Este código de erro também é devolvido se o módulo solicitar uma operação que esteja fora do âmbito de acesso do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="259a2-250">Por exemplo, não é permitido criar um módulo com o bloco de controlo do temporizador ou o endereço de retorno fora da área de código do módulo.</span><span class="sxs-lookup"><span data-stu-id="259a2-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="259a2-251">Exemplo do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-251">Module Manager example</span></span>

<span data-ttu-id="259a2-252">Segue-se um exemplo do código do Gestor de Módulos que lança o módulo de exemplo previamente definido no Capítulo 2.</span><span class="sxs-lookup"><span data-stu-id="259a2-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="259a2-253">Presume-se que o módulo já está carregado, presumivelmente pelo depurador, no endereço ROM 0x00800000.</span><span class="sxs-lookup"><span data-stu-id="259a2-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

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

## <a name="module-manager-building"></a><span data-ttu-id="259a2-254">Edifício do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="259a2-254">Module Manager building</span></span>

<span data-ttu-id="259a2-255">Os ***ficheiros \* de*** origem txm_module_manager_ devem ser adicionados à biblioteca ThreadX.</span><span class="sxs-lookup"><span data-stu-id="259a2-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="259a2-256">Uma aplicação Do Gestor de Módulos ThreadX é efetivamente a mesma que uma aplicação padrão da ThreadX, que é um ou mais ficheiros de aplicação ligados juntamente com a biblioteca ThreadX ***tx.a***.</span><span class="sxs-lookup"><span data-stu-id="259a2-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="259a2-257">A construção de uma aplicação de gestor de módulos depende da utilização da cadeia de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="259a2-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="259a2-258">Consulte [o apêndice](appendix.md) para obter exemplos específicos da porta.</span><span class="sxs-lookup"><span data-stu-id="259a2-258">See [appendix](appendix.md) for port-specific examples.</span></span>
