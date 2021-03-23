---
title: Capítulo 5 - ApIs gestor de módulos
author: philmea
description: Este artigo é um resumo das APIs do Gestor de Módulos disponíveis para a parte residente da aplicação.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825484"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="17998-103">Capítulo 5 - ApIs gestor de módulos</span><span class="sxs-lookup"><span data-stu-id="17998-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="17998-104">Resumo das APIs do Gestor de Módulos</span><span class="sxs-lookup"><span data-stu-id="17998-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="17998-105">Existem várias APIs adicionais disponíveis para a parte residente da aplicação, da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="17998-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="17998-106">***txm_module_manager_external_memory_enable** _ - _Enable o acesso do módulo a um espaço de memória partilhada*</span><span class="sxs-lookup"><span data-stu-id="17998-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="17998-107">***txm_module_manager_file_load** _ - _Load módulo do ficheiro via FileX*</span><span class="sxs-lookup"><span data-stu-id="17998-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="17998-108">***txm_module_manager_in_place_load** _ - _Load dados do módulo, execute no lugar*</span><span class="sxs-lookup"><span data-stu-id="17998-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="17998-109">***txm_module_manager_initialize** _ - _Initialize o gestor do módulo*</span><span class="sxs-lookup"><span data-stu-id="17998-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="17998-110">***txm_module_manager_mm_initialize** _ - _Initialize o hardware de gestão da memória*</span><span class="sxs-lookup"><span data-stu-id="17998-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="17998-111">***txm_module_manager_maximum_module_priority_set** _ - _set a prioridade máxima de fio permitida num módulo*</span><span class="sxs-lookup"><span data-stu-id="17998-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="17998-112">***txm_module_manager_memory_fault_notify** _ - _Register uma chamada de chamada de aplicação na falha de memória*</span><span class="sxs-lookup"><span data-stu-id="17998-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="17998-113">***txm_module_manager_memory_load** _ - _Load o módulo da memória*</span><span class="sxs-lookup"><span data-stu-id="17998-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="17998-114">***txm_module_manager_object_pool_create** _ - _Create uma piscina de objetos para módulos*</span><span class="sxs-lookup"><span data-stu-id="17998-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="17998-115">***txm_module_manager_properties_get** _ - propriedades do módulo _Get*</span><span class="sxs-lookup"><span data-stu-id="17998-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="17998-116">***txm_module_manager_start** _ - execução _Start do módulo especificado*</span><span class="sxs-lookup"><span data-stu-id="17998-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="17998-117">***txm_module_manager_stop** _ - execução _Stop do módulo especificado*</span><span class="sxs-lookup"><span data-stu-id="17998-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="17998-118">***txm_module_manager_unload** _ - _Unload o módulo*</span><span class="sxs-lookup"><span data-stu-id="17998-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="17998-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="17998-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="17998-120">Ativar o módulo para aceder a um espaço de memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="17998-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="17998-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-122">Description</span></span>

<span data-ttu-id="17998-123">Este serviço cria uma entrada na tabela de hardware de gestão de memória para uma região de memória partilhada a que o módulo pode aceder.</span><span class="sxs-lookup"><span data-stu-id="17998-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-124">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-124">Input parameters</span></span>

- <span data-ttu-id="17998-125">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="17998-126">**start_address** Endereço inicial da região de memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="17998-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="17998-127">**comprimento** Comprimento da região da memória partilhada.</span><span class="sxs-lookup"><span data-stu-id="17998-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="17998-128">**atributos** Atributos da região da memória (cache, ler, escrever, etc.).</span><span class="sxs-lookup"><span data-stu-id="17998-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="17998-129">Os atributos são específicos da porta; ver [apêndice](appendix.md) para o formato de atributos.</span><span class="sxs-lookup"><span data-stu-id="17998-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-130">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-130">Return values</span></span>

- <span data-ttu-id="17998-131">**TX_SUCCESS** (0x00) A entrada de memória criada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="17998-132">**TX_NOT_AVAILABLE** (0x1D) Gestor não inicializado ou funcionalidade não disponível.</span><span class="sxs-lookup"><span data-stu-id="17998-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="17998-133">**TX_PTR_ERROR** (0x03) Instância do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="17998-134">**TX_START_ERROR** módulo (0x10) não em estado carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="17998-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento de endereço inicial inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="17998-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="17998-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-137">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-137">Allowed from</span></span>

<span data-ttu-id="17998-138">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="17998-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="17998-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="17998-141">Módulo de carga a partir de ficheiro via FileX.</span><span class="sxs-lookup"><span data-stu-id="17998-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-142">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="17998-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-143">Description</span></span>

<span data-ttu-id="17998-144">Este serviço carrega a imagem binária do módulo contido no ficheiro especificado na área de memória do módulo e prepara-o para a execução.</span><span class="sxs-lookup"><span data-stu-id="17998-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="17998-145">Presume-se que os meios de comunicação fornecidos já estão abertos.</span><span class="sxs-lookup"><span data-stu-id="17998-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="17998-146">O sistema FileX é utilizado para carregar o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="17998-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="17998-147">Para permitir o acesso ao FileX, o módulo, biblioteca de módulos, gestor de módulos e a biblioteca ThreadX (com as fontes do Gestor do Módulo) devem ser construídos com **FX_FILEX_PRESENT** definidos nos projetos.</span><span class="sxs-lookup"><span data-stu-id="17998-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-148">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-148">Input parameters</span></span>

- <span data-ttu-id="17998-149">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="17998-150">**module_name** Nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="17998-151">**media_ptr** Ponteiro para já aberto media FileX.</span><span class="sxs-lookup"><span data-stu-id="17998-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="17998-152">**file_name** Nome do ficheiro binário do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-153">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-153">Return values</span></span>

- <span data-ttu-id="17998-154">**TX_SUCCESS** (0x00) Carga de módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="17998-155">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-156">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-157">**TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="17998-158">**TX_NOT_DONE** (0x20) Os meios de comunicação não abertos, o ficheiro não encontrado ou o ficheiro é inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="17998-159">**TX_PTR_ERROR** (0x03) Ponteiro do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="17998-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="17998-161">**módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="17998-162">**| TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="17998-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="17998-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-164">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-164">Allowed from</span></span>

<span data-ttu-id="17998-165">Fios</span><span class="sxs-lookup"><span data-stu-id="17998-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-166">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="17998-167">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-167">See also</span></span>

- <span data-ttu-id="17998-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="17998-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="17998-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="17998-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="17998-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="17998-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="17998-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="17998-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="17998-172">Carregar apenas os dados do módulo, executar o módulo na localização existente.</span><span class="sxs-lookup"><span data-stu-id="17998-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="17998-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-174">Description</span></span>

<span data-ttu-id="17998-175">Este serviço carrega a área de dados do módulo apenas na área de memória do módulo e prepara-a para a execução.</span><span class="sxs-lookup"><span data-stu-id="17998-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="17998-176">A execução do código do módulo será no lugar, ou seja, a partir do endereço compensado especificado pelo preâmbulo do módulo no local fornecido.</span><span class="sxs-lookup"><span data-stu-id="17998-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-177">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-177">Input parameters</span></span>

- <span data-ttu-id="17998-178">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="17998-179">**module_name** Nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="17998-180">**localização** Ponteiro para a área de código do módulo, preâmbulo primeiro.</span><span class="sxs-lookup"><span data-stu-id="17998-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-181">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-181">Return values</span></span>

- <span data-ttu-id="17998-182">**TX_SUCCESS** (0x00) Carga de módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="17998-183">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-184">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-185">**TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="17998-186">**TX_PTR_ERROR** (0x03) Ponteiro inválido, instância do módulo ou preâmbulo do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="17998-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="17998-188">**módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="17998-189">**TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="17998-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="17998-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-191">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-191">Allowed from</span></span>

<span data-ttu-id="17998-192">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="17998-194">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-194">See also</span></span>

- <span data-ttu-id="17998-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="17998-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="17998-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="17998-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="17998-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="17998-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="17998-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="17998-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="17998-199">Inicialize o gestor do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="17998-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-201">Description</span></span>

<span data-ttu-id="17998-202">Este serviço inicializa os recursos internos do Gestor do Módulo, incluindo a área de memória utilizada para carregar módulos.</span><span class="sxs-lookup"><span data-stu-id="17998-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-203">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-203">Input parameters</span></span>

- <span data-ttu-id="17998-204">**module_memory_start** Ponteiro para o início da memória do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="17998-205">**module_memory_size** Tamanho em bytes da memória do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-206">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-206">Return values</span></span>

- <span data-ttu-id="17998-207">**TX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="17998-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17998-208">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-209">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-209">Allowed from</span></span>

<span data-ttu-id="17998-210">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="17998-212">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-212">See also</span></span>

- <span data-ttu-id="17998-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="17998-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="17998-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="17998-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="17998-215">Inicialize o hardware de gestão da memória.</span><span class="sxs-lookup"><span data-stu-id="17998-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="17998-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-217">Description</span></span>

<span data-ttu-id="17998-218">Este serviço inicializa a MMU.</span><span class="sxs-lookup"><span data-stu-id="17998-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-219">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-219">Input parameters</span></span>

<span data-ttu-id="17998-220">nenhum</span><span class="sxs-lookup"><span data-stu-id="17998-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-221">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-221">Return values</span></span>

- <span data-ttu-id="17998-222">**TX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="17998-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17998-223">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-224">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-224">Allowed from</span></span>

<span data-ttu-id="17998-225">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="17998-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-226">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="17998-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="17998-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="17998-228">Desaprote a prioridade máxima de rosca permitida num módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-229">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="17998-230">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-230">Description</span></span>

<span data-ttu-id="17998-231">Este serviço define a prioridade máxima de linha permitida num módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-232">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-232">Input parameters</span></span>

- <span data-ttu-id="17998-233">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="17998-234">**prioridade** Prioridade máxima do fio.</span><span class="sxs-lookup"><span data-stu-id="17998-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-235">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-235">Return values</span></span>

- <span data-ttu-id="17998-236">**TX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="17998-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17998-237">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-238">**TX_PTR_ERROR** (0x03) Instância do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="17998-239">**TX_START_ERROR** módulo (0x10) não em estado carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-240">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-240">Allowed from</span></span>

<span data-ttu-id="17998-241">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-242">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="17998-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="17998-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="17998-244">Registar uma chamada de chamada de aplicação na falha de memória.</span><span class="sxs-lookup"><span data-stu-id="17998-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="17998-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-246">Description</span></span>

<span data-ttu-id="17998-247">Este serviço regista a função de chamada de chamada de notificação de falha de memória de aplicação especificada com o Gestor do Módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="17998-248">Se ocorrer uma falha de memória, esta função é chamada com um ponteiro para o fio ofensivo e a instância do módulo correspondente ao fio ofensivo.</span><span class="sxs-lookup"><span data-stu-id="17998-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="17998-249">O processamento do Gestor do Módulo termina automaticamente o fio ofensivo, mas deixa quaisquer outros fios no módulo intactos.</span><span class="sxs-lookup"><span data-stu-id="17998-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="17998-250">Cabe à aplicação decidir o que fazer com o módulo associado à falha de memória.</span><span class="sxs-lookup"><span data-stu-id="17998-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="17998-251">Consulte a **estrutura** interna _txm_module_manager_memory_fault_info para obter informações específicas sobre a própria falha de memória.</span><span class="sxs-lookup"><span data-stu-id="17998-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="17998-252">A função de chamada de notificação por falha de memória é executada diretamente a partir da exceção da falha de memória, pelo que apenas apis ThreadX permitidos a partir de rotinas de serviço de interrupção podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="17998-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="17998-253">Assim, para parar e descarregar o módulo ofensivo, a chamada de notificação de aplicação deve enviar um sinal para uma tarefa de aplicação para que o módulo possa ser parado e descarregado.</span><span class="sxs-lookup"><span data-stu-id="17998-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-254">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-254">Input parameters</span></span>

- <span data-ttu-id="17998-255">**notify_function** Função ponteiro para a chamada de notificação de falha de memória da aplicação.</span><span class="sxs-lookup"><span data-stu-id="17998-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="17998-256">O fornecimento de um valor NUDO desativa a notificação de falha de memória.</span><span class="sxs-lookup"><span data-stu-id="17998-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-257">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-257">Return values</span></span>

- <span data-ttu-id="17998-258">**TX_SUCCESS** (0x00) Registo de função de notificação com sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-259">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-259">Allowed from</span></span>

<span data-ttu-id="17998-260">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-261">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="17998-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="17998-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="17998-263">Módulo de carga da memória.</span><span class="sxs-lookup"><span data-stu-id="17998-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="17998-265">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-265">Description</span></span>

<span data-ttu-id="17998-266">Este serviço carrega o código e a área de dados do módulo na área de memória do módulo configurada por ***txm_module_manager_initialize*** e prepara-o para a execução.</span><span class="sxs-lookup"><span data-stu-id="17998-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-267">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-267">Input parameters</span></span>

- <span data-ttu-id="17998-268">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="17998-269">**module_name** Nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="17998-270">**localização** Ponteiro para a área de código do módulo, preâmbulo primeiro.</span><span class="sxs-lookup"><span data-stu-id="17998-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-271">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-271">Return values</span></span>

- <span data-ttu-id="17998-272">**TX_SUCCESS** (0x00) Carga de módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="17998-273">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-274">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-275">**TX_NO_MEMORY** (0x10) Não há memória suficiente para carregar o módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="17998-276">**TX_PTR_ERROR** (0x03) Ponteiro inválido, instância do módulo ou preâmbulo do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="17998-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Alinhamento inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="17998-278">**módulo TXM_MODULE_ALREADY_LOADED** (0xF1) já carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="17998-279">**TXM_MODULE_INVALID** (0xF2) Preâmbulo do módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="17998-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) propriedades incompatíveis.</span><span class="sxs-lookup"><span data-stu-id="17998-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-281">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-281">Allowed from</span></span>

<span data-ttu-id="17998-282">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-283">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="17998-284">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-284">See also</span></span>

- <span data-ttu-id="17998-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="17998-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="17998-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="17998-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="17998-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="17998-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="17998-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="17998-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="17998-289">Crie uma piscina de objetos para módulos.</span><span class="sxs-lookup"><span data-stu-id="17998-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="17998-291">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-291">Description</span></span>

<span data-ttu-id="17998-292">Este serviço cria um conjunto de memória de objetos do Gestor de Módulos do qual os módulos podem alocar objetos ThreadX/NetX, mantendo assim o objeto do sistema fora da área de memória do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-293">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-293">Input parameters</span></span>

- <span data-ttu-id="17998-294">**pool_memory_start** Ponteiro para o início da memória do objeto.</span><span class="sxs-lookup"><span data-stu-id="17998-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="17998-295">**pool_memory_size** Tamanho em bytes da piscina de memória do objeto.</span><span class="sxs-lookup"><span data-stu-id="17998-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-296">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-296">Return values</span></span>

- <span data-ttu-id="17998-297">**TX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="17998-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17998-298">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-299">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-299">Allowed from</span></span>

<span data-ttu-id="17998-300">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-301">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="17998-302">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-302">See also</span></span>

- <span data-ttu-id="17998-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="17998-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="17998-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="17998-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="17998-305">Obtenha propriedades de módulos.</span><span class="sxs-lookup"><span data-stu-id="17998-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="17998-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-307">Description</span></span>

<span data-ttu-id="17998-308">Este serviço devolve as propriedades (especificadas no preâmbulo) de um módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-309">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-309">Input parameters</span></span>

- <span data-ttu-id="17998-310">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="17998-311">**module_properties_ptr** Ponteiro para destino para as propriedades do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-312">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-312">Return values</span></span>

- <span data-ttu-id="17998-313">**TX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="17998-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="17998-314">**TX_PTR_ERROR** (0x03) Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="17998-315">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-316">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-316">Allowed from</span></span>

<span data-ttu-id="17998-317">Fios</span><span class="sxs-lookup"><span data-stu-id="17998-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-318">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="17998-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="17998-319">txm_module_manager_start</span></span>

<span data-ttu-id="17998-320">Inicie a execução do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="17998-322">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-322">Description</span></span>

<span data-ttu-id="17998-323">Este serviço inicia a execução do módulo especificado, já carregado.</span><span class="sxs-lookup"><span data-stu-id="17998-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-324">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-324">Input parameters</span></span>

- <span data-ttu-id="17998-325">**module_instance** Ponteiro para a instância do módulo previamente carregada.</span><span class="sxs-lookup"><span data-stu-id="17998-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-326">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-326">Return values</span></span>

- <span data-ttu-id="17998-327">**TX_SUCCESS** (0x00) Início do módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="17998-328">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-329">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-330">**TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="17998-331">**TX_START_ERROR** (0x10) Módulo já começou.</span><span class="sxs-lookup"><span data-stu-id="17998-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-332">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-332">Allowed from</span></span>

<span data-ttu-id="17998-333">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-334">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="17998-335">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-335">See also</span></span>

- <span data-ttu-id="17998-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="17998-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="17998-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="17998-337">txm_module_manager_stop</span></span>

<span data-ttu-id="17998-338">Pare a execução do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-339">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="17998-340">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-340">Description</span></span>

<span data-ttu-id="17998-341">Este serviço para um módulo que foi previamente carregado e iniciado.</span><span class="sxs-lookup"><span data-stu-id="17998-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="17998-342">A paragem de um módulo inclui a execução do fio de paragem opcional do módulo, a terminação de todos os fios e a eliminação de todos os recursos associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-343">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-343">Input parameters</span></span>

- <span data-ttu-id="17998-344">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-345">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-345">Return values</span></span>

- <span data-ttu-id="17998-346">**TX_SUCCESS** (0x00) Paragem do módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="17998-347">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-348">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-349">**TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="17998-350">**TX_START_ERROR** (0x10) Módulo não começou.</span><span class="sxs-lookup"><span data-stu-id="17998-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-351">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-351">Allowed from</span></span>

<span data-ttu-id="17998-352">Fios</span><span class="sxs-lookup"><span data-stu-id="17998-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-353">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="17998-354">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-354">See also</span></span>

- <span data-ttu-id="17998-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="17998-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="17998-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="17998-356">txm_module_manager_unload</span></span>

<span data-ttu-id="17998-357">Descarregue o módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="17998-358">Prototype</span><span class="sxs-lookup"><span data-stu-id="17998-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="17998-359">Descrição</span><span class="sxs-lookup"><span data-stu-id="17998-359">Description</span></span>

<span data-ttu-id="17998-360">Este serviço descarrega o módulo previamente carregado e parado, libertando todos os recursos de memória do módulo associado.</span><span class="sxs-lookup"><span data-stu-id="17998-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="17998-361">Parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="17998-361">Input parameters</span></span>

- <span data-ttu-id="17998-362">**module_instance** Ponteiro para a instância do módulo.</span><span class="sxs-lookup"><span data-stu-id="17998-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="17998-363">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="17998-363">Return values</span></span>

- <span data-ttu-id="17998-364">**TX_SUCCESS** 0x00) Descarregamento de módulo de sucesso.</span><span class="sxs-lookup"><span data-stu-id="17998-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="17998-365">**TX_CALLER_ERROR** (0x13) Inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="17998-366">**TX_NOT_AVAILABLE** (0x1D) Manager não inicializou.</span><span class="sxs-lookup"><span data-stu-id="17998-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="17998-367">**TX_NOT_DONE** (0x20) Módulo inválido ou módulo não parado.</span><span class="sxs-lookup"><span data-stu-id="17998-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="17998-368">**TX_PTR_ERROR** (0x03) Indicação de ponteiro ou módulo inválido.</span><span class="sxs-lookup"><span data-stu-id="17998-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="17998-369">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="17998-369">Allowed from</span></span>

<span data-ttu-id="17998-370">Inicialização e fios</span><span class="sxs-lookup"><span data-stu-id="17998-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="17998-371">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17998-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="17998-372">Veja também</span><span class="sxs-lookup"><span data-stu-id="17998-372">See also</span></span>

- <span data-ttu-id="17998-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="17998-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="17998-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="17998-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="17998-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="17998-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="17998-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="17998-376">txm_module_manager_stop</span></span>
