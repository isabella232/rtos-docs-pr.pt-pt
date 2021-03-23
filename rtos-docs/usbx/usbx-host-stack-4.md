---
title: Capítulo 4 - Descrição dos serviços de anfitrião USBX
description: Saiba mais sobre os Serviços de Anfitrião USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828454"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="541d0-103">Capítulo 4 - Descrição dos serviços de anfitrião USBX</span><span class="sxs-lookup"><span data-stu-id="541d0-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="541d0-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="541d0-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="541d0-105">Inicialize o USBX para a operação do anfitrião.</span><span class="sxs-lookup"><span data-stu-id="541d0-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="541d0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-107">Description</span></span>

<span data-ttu-id="541d0-108">Esta função irá inicializar a pilha de anfitriões USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="541d0-109">A área de memória fornecida será configurada para utilização interna USBX.</span><span class="sxs-lookup"><span data-stu-id="541d0-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="541d0-110">Se UX_SUCCESS for devolvido, o USBX está pronto para o controlador de anfitrião e para o registo da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="541d0-111">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="541d0-111">Input Parameter</span></span>

- <span data-ttu-id="541d0-112">**system_change_function** Ponteiro para a rotina de retorno opcional para notificar a aplicação de alterações do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="541d0-113">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="541d0-113">Return Value</span></span>

- <span data-ttu-id="541d0-114">**UX_SUCCESS** (0x00) Inicialização bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="541d0-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="541d0-115">**UX_MEMORY_INSUFFICIENT** (0x12) Uma atribuição de memória falhou.</span><span class="sxs-lookup"><span data-stu-id="541d0-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="541d0-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="541d0-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="541d0-118">Abortar todas as transações anexas a um pedido de transferência para um ponto final.</span><span class="sxs-lookup"><span data-stu-id="541d0-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-119">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="541d0-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-120">Description</span></span>

<span data-ttu-id="541d0-121">Esta função irá cancelar todas as transações ativas ou pendentes para um pedido de transferência específico anexado a um ponto final.</span><span class="sxs-lookup"><span data-stu-id="541d0-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="541d0-122">O pedido de transferência tem uma função de retorno anexada, a função de retorno será chamada com o estado de UX_TRANSACTION_ABORTED.</span><span class="sxs-lookup"><span data-stu-id="541d0-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="541d0-123">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="541d0-123">Input Parameter</span></span>

- <span data-ttu-id="541d0-124">**ponto final** Apontador para um ponto final.</span><span class="sxs-lookup"><span data-stu-id="541d0-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-125">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-125">Return Values</span></span>

- <span data-ttu-id="541d0-126">**UX_SUCCESS** (0x00) Sem erros.</span><span class="sxs-lookup"><span data-stu-id="541d0-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="541d0-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) A pega endpoint não é válida.</span><span class="sxs-lookup"><span data-stu-id="541d0-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="541d0-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="541d0-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="541d0-130">Pegue o ponteiro para um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="541d0-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-132">Description</span></span>

<span data-ttu-id="541d0-133">Esta função devolve um ponteiro ao recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="541d0-134">Uma classe precisa de obter o seu recipiente a partir da pilha USB para procurar casos em que uma classe ou uma aplicação quer abrir um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="541d0-135">A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior UX_MAX_CLASS_NAME_LENGTH.</span><span class="sxs-lookup"><span data-stu-id="541d0-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-136">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-136">Parameters</span></span>

- <span data-ttu-id="541d0-137">**class_name** Apontador para o nome da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="541d0-138">**classe** Um ponteiro atualizado pela chamada de função que contém o recipiente de classe para o nome da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-139">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-139">Return Values</span></span>

- <span data-ttu-id="541d0-140">**UX_SUCCESS** (0x00) Sem erros, no retorno o campo de aula é arquivado com o ponteiro para o recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="541d0-141">**UX_HOST_CLASS_UNKNOWN** classe (0x59) é desconhecida pela pilha.</span><span class="sxs-lookup"><span data-stu-id="541d0-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="541d0-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="541d0-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="541d0-144">Registe uma classe USB na pilha USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-145">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="541d0-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-146">Description</span></span>

<span data-ttu-id="541d0-147">Esta função regista uma classe USB para a pilha USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="541d0-148">A classe deve especificar um ponto de entrada para a pilha USB enviar comandos como o seguinte.</span><span class="sxs-lookup"><span data-stu-id="541d0-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="541d0-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="541d0-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="541d0-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="541d0-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="541d0-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="541d0-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="541d0-152">A cadeia C de *class_name* deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="541d0-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-153">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-153">Parameters</span></span>

- <span data-ttu-id="541d0-154">**class_name** Ponteiros do nome da classe, as entradas válidas encontram-se no ficheiro ux_system_initialize.c nas classes USBX.</span><span class="sxs-lookup"><span data-stu-id="541d0-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="541d0-155">**class_entry_address** Endereço da função de entrada da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-156">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-156">Return Values</span></span>

- <span data-ttu-id="541d0-157">**UX_SUCCESS** (0x00) Classe instalada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="541d0-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="541d0-158">**UX_MEMORY_ARRAY_FULL** (0x1a) Não há mais memória para armazenar esta classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="541d0-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Classe de anfitrião já instalada.</span><span class="sxs-lookup"><span data-stu-id="541d0-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-160">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="541d0-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="541d0-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="541d0-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="541d0-162">Crie uma nova instância de classe para um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-163">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="541d0-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-164">Description</span></span>

<span data-ttu-id="541d0-165">Esta função cria uma nova instância de classe para um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="541d0-166">O caso de uma classe não está contido no código de classe para reduzir a complexidade da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="541d0-167">Em vez disso, cada instância de classe é anexada ao recipiente de classe localizado na pilha principal.</span><span class="sxs-lookup"><span data-stu-id="541d0-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-168">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-168">Parameters</span></span>

- <span data-ttu-id="541d0-169">**classe** Ponteiro para o recipiente da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="541d0-170">**class_instance** Ponteiro para a instância de classe a criar.</span><span class="sxs-lookup"><span data-stu-id="541d0-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="541d0-171">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="541d0-171">Return Value</span></span>

- <span data-ttu-id="541d0-172">**UX_SUCCESS** (0x00) A instância de classe foi anexada ao recipiente da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-173">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="541d0-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="541d0-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="541d0-175">Destrua uma instância de classe para um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-176">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="541d0-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-177">Description</span></span>

<span data-ttu-id="541d0-178">Esta função destrói uma instância de classe para um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-179">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-179">Parameters</span></span>

- <span data-ttu-id="541d0-180">**classe** Ponteiro para o recipiente da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="541d0-181">**class_instance** Apontando para o caso para destruir.</span><span class="sxs-lookup"><span data-stu-id="541d0-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-182">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-182">Return Values</span></span>

- <span data-ttu-id="541d0-183">**UX_SUCCESS** (0x00) A instância de classe foi destruída.</span><span class="sxs-lookup"><span data-stu-id="541d0-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="541d0-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A instância de classe não está ligada ao recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="541d0-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="541d0-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="541d0-187">Arranja um ponteiro de exemplo de turma para uma aula específica.</span><span class="sxs-lookup"><span data-stu-id="541d0-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="541d0-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-189">Description</span></span>

<span data-ttu-id="541d0-190">Esta função devolve um ponteiro de instância de classe para uma classe específica.</span><span class="sxs-lookup"><span data-stu-id="541d0-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="541d0-191">O caso de uma classe não está contido no código de classe para reduzir a complexidade da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="541d0-192">Pelo contrário, cada instância de classe é anexada ao recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="541d0-193">Esta função é utilizada para procurar casos de classe dentro de um recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-194">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-194">Parameters</span></span>

- <span data-ttu-id="541d0-195">**classe** Ponteiro para o recipiente da classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="541d0-196">**class_index** Um índice a utilizar pela chamada de função dentro da lista de classes anexadas ao recipiente.</span><span class="sxs-lookup"><span data-stu-id="541d0-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="541d0-197">**class_instance** Ponteiro para o caso a ser devolvido pela chamada de função.</span><span class="sxs-lookup"><span data-stu-id="541d0-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-198">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-198">Return Values</span></span>

- <span data-ttu-id="541d0-199">**UX_SUCCESS** (0x00) A instância de classe foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="541d0-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="541d0-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Não existem mais casos de classe ligados ao recipiente de classe.</span><span class="sxs-lookup"><span data-stu-id="541d0-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="541d0-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="541d0-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="541d0-203">Obtenha um ponteiro para um recipiente de configuração.</span><span class="sxs-lookup"><span data-stu-id="541d0-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="541d0-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-205">Description</span></span>

<span data-ttu-id="541d0-206">Esta função devolve um recipiente de configuração com base numa pega do dispositivo e num índice de configuração.</span><span class="sxs-lookup"><span data-stu-id="541d0-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-207">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-207">Parameters</span></span>

- <span data-ttu-id="541d0-208">**dispositivo** Ponteiro para o recipiente do dispositivo que possui a configuração solicitada.</span><span class="sxs-lookup"><span data-stu-id="541d0-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="541d0-209">**configuration_index** Índice da configuração a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="541d0-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="541d0-210">**configuração** Endereço do ponteiro para o recipiente de configuração a devolver.</span><span class="sxs-lookup"><span data-stu-id="541d0-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-211">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-211">Return Values</span></span>

- <span data-ttu-id="541d0-212">**UX_SUCCESS** (0x00) A configuração foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="541d0-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="541d0-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) O recipiente do dispositivo não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="541d0-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A pega de configuração do índice não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-215">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="541d0-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="541d0-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="541d0-217">Selecione uma configuração específica para um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-218">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="541d0-219">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-219">Description</span></span>

<span data-ttu-id="541d0-220">Esta função seleciona uma configuração específica para um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="541d0-221">Quando esta configuração é definida para o dispositivo, por padrão, cada interface do dispositivo e a sua configuração alternativa associada 0 são ativadas no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="541d0-222">Se a classe dispositivo/interface pretende alterar a configuração de uma determinada interface, tem de emitir uma chamada de serviço **ux_host_stack_interface_setting_select.**</span><span class="sxs-lookup"><span data-stu-id="541d0-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-223">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-223">Parameters</span></span>

- <span data-ttu-id="541d0-224">**configuração** Ponteiro para o recipiente de configuração que deve ser ativado para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-225">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-225">Return Values</span></span>

- <span data-ttu-id="541d0-226">**UX_SUCCESS** (0x00) A seleção de configuração foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="541d0-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="541d0-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A pega de configuração não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="541d0-228">**UX_OVER_CURRENT_CONDITION** (0x43) Existe uma condição acima da atual existente no autocarro para esta configuração.</span><span class="sxs-lookup"><span data-stu-id="541d0-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="541d0-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="541d0-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="541d0-231">Arranja um ponteiro para um contentor de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="541d0-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-232">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="541d0-233">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-233">Description</span></span>

<span data-ttu-id="541d0-234">Esta função devolve um recipiente do dispositivo com base no seu índice.</span><span class="sxs-lookup"><span data-stu-id="541d0-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="541d0-235">O índice do dispositivo começa com 0.</span><span class="sxs-lookup"><span data-stu-id="541d0-235">The device index starts with 0.</span></span> <span data-ttu-id="541d0-236">Note que o índice é um ULONG porque poderíamos ter vários controladores e um índice byte pode não ser suficiente.</span><span class="sxs-lookup"><span data-stu-id="541d0-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="541d0-237">O índice do dispositivo não deve ser confundido com o endereço do dispositivo específico para o autocarro.</span><span class="sxs-lookup"><span data-stu-id="541d0-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-238">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-238">Parameters</span></span>

- <span data-ttu-id="541d0-239">**device_index** Índice do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="541d0-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="541d0-240">**dispositivo** Endereço do ponteiro para o recipiente do dispositivo regressar.</span><span class="sxs-lookup"><span data-stu-id="541d0-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-241">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-241">Return Values</span></span>

- <span data-ttu-id="541d0-242">**UX_SUCCESS** (0x00) O recipiente do dispositivo existe e é devolvido</span><span class="sxs-lookup"><span data-stu-id="541d0-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="541d0-243">**dispositivo UX_DEVICE_HANDLE_UNKNOWN** (0x50) desconhecido</span><span class="sxs-lookup"><span data-stu-id="541d0-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="541d0-244">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="541d0-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="541d0-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="541d0-246">Arranja um contentor de ponto final.</span><span class="sxs-lookup"><span data-stu-id="541d0-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-247">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="541d0-248">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-248">Description</span></span>

<span data-ttu-id="541d0-249">Esta função devolve um recipiente de ponto final baseado no manípulo da interface e num índice de ponto final.</span><span class="sxs-lookup"><span data-stu-id="541d0-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="541d0-250">Presume-se que a definição alternativa para a interface foi selecionada ou que a definição predefinida está a ser utilizada antes do ponto final ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="541d0-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-251">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-251">Parameters</span></span>

- <span data-ttu-id="541d0-252">**interface** Ponteiro para o recipiente de interface que contém o ponto final solicitado.</span><span class="sxs-lookup"><span data-stu-id="541d0-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="541d0-253">**endpoint_index** Índice do ponto final nesta interface.</span><span class="sxs-lookup"><span data-stu-id="541d0-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="541d0-254">**ponto final** Endereço do recipiente de ponto final a devolver.</span><span class="sxs-lookup"><span data-stu-id="541d0-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-255">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-255">Return Values</span></span>

- <span data-ttu-id="541d0-256">**UX_SUCCESS** (0x00) O recipiente de ponto final existe e é devolvido.</span><span class="sxs-lookup"><span data-stu-id="541d0-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="541d0-257">**UX_INTERFACE_HANDLE_UNKNOWN** interface (0x52) especificada não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="541d0-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Índice de ponto final não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-259">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="541d0-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="541d0-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="541d0-261">Registe um controlador USB na pilha USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="541d0-263">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-263">Description</span></span>

<span data-ttu-id="541d0-264">Esta função regista um controlador USB na pilha USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="541d0-265">Aloca principalmente a memória utilizada por este controlador e passa o comando de inicialização para o controlador.</span><span class="sxs-lookup"><span data-stu-id="541d0-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-266">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-266">Parameters</span></span>

- <span data-ttu-id="541d0-267">**hcd_name** Nome do controlador anfitrião</span><span class="sxs-lookup"><span data-stu-id="541d0-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="541d0-268">**hcd_function** A função no controlador de anfitrião responsável pela inicialização.</span><span class="sxs-lookup"><span data-stu-id="541d0-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="541d0-269">**hcd_param1** O IO ou o recurso de memória utilizado pelo hcd.</span><span class="sxs-lookup"><span data-stu-id="541d0-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="541d0-270">**hcd_param2** O IRQ usado pelo controlador hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="541d0-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-271">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-271">Return Values</span></span>

- <span data-ttu-id="541d0-272">**UX_SUCCESS** (0x00) O controlador foi inicializado corretamente.</span><span class="sxs-lookup"><span data-stu-id="541d0-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="541d0-273">**UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para este controlador.</span><span class="sxs-lookup"><span data-stu-id="541d0-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="541d0-274">**UX_PORT_RESET_FAILED** (0x31) O reset do controlador falhou.</span><span class="sxs-lookup"><span data-stu-id="541d0-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="541d0-275">**UX_CONTROLLER_INIT_FAILED** (0x32) O controlador não iniciais corretamente.</span><span class="sxs-lookup"><span data-stu-id="541d0-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-276">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="541d0-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="541d0-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="541d0-278">Arranja um ponteiro de contentor de interface.</span><span class="sxs-lookup"><span data-stu-id="541d0-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-279">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="541d0-280">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-280">Description</span></span>

<span data-ttu-id="541d0-281">Esta função devolve um recipiente de interface com base num cabo de configuração, num índice de interface e num índice de definição alternativo.</span><span class="sxs-lookup"><span data-stu-id="541d0-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-282">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-282">Parameters</span></span>

- <span data-ttu-id="541d0-283">**configuração** Ponteiro para o recipiente de configuração que possui a interface.</span><span class="sxs-lookup"><span data-stu-id="541d0-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="541d0-284">**interface_index** Índice de interface a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="541d0-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="541d0-285">**alternate_setting_index** Definição alternativa dentro da interface para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="541d0-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="541d0-286">**interface** Endereço do ponteiro do recipiente de interface a ser devolvido.</span><span class="sxs-lookup"><span data-stu-id="541d0-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-287">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-287">Return Values</span></span>

- <span data-ttu-id="541d0-288">**UX_SUCCESS** (0x00) O recipiente de interface para o índice de interface e a definição alternativa foi encontrado e devolvido.</span><span class="sxs-lookup"><span data-stu-id="541d0-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="541d0-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) A configuração não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="541d0-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) A interface não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-291">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="541d0-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="541d0-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="541d0-293">Selecione uma definição alternativa para uma interface.</span><span class="sxs-lookup"><span data-stu-id="541d0-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-294">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="541d0-295">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-295">Description</span></span>

<span data-ttu-id="541d0-296">Esta função seleciona uma definição alternativa específica para uma determinada interface pertencente à configuração selecionada.</span><span class="sxs-lookup"><span data-stu-id="541d0-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="541d0-297">Esta função é utilizada para alterar da definição alternativa predefinida para uma nova definição ou para voltar à definição alternativa predefinida.</span><span class="sxs-lookup"><span data-stu-id="541d0-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="541d0-298">Quando uma nova definição alternativa é selecionada, as características do ponto final anterior são inválidas e devem ser recarregadas.</span><span class="sxs-lookup"><span data-stu-id="541d0-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="541d0-299">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="541d0-299">Input Parameter</span></span>

- <span data-ttu-id="541d0-300">**interface** Ponteiro para o recipiente de interface cuja definição alternativa deve ser selecionada.</span><span class="sxs-lookup"><span data-stu-id="541d0-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-301">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-301">Return Values</span></span>

- <span data-ttu-id="541d0-302">**UX_SUCCESS** (0x00) A definição alternativa para esta interface foi selecionada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="541d0-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="541d0-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) A interface não existe.</span><span class="sxs-lookup"><span data-stu-id="541d0-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-304">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="541d0-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="541d0-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="541d0-306">Abortar um pedido de transferência pendente.</span><span class="sxs-lookup"><span data-stu-id="541d0-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-307">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="541d0-308">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-308">Description</span></span>

<span data-ttu-id="541d0-309">Esta função aborta um pedido de transferência pendente que foi previamente apresentado.</span><span class="sxs-lookup"><span data-stu-id="541d0-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="541d0-310">Esta função apenas cancela um pedido de transferência específico.</span><span class="sxs-lookup"><span data-stu-id="541d0-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="541d0-311">A chamada de volta para a função terá o estado de UX_TRANSFER REQUEST_STATUS_ABORT.</span><span class="sxs-lookup"><span data-stu-id="541d0-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="541d0-312">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="541d0-312">Parameters</span></span>

- <span data-ttu-id="541d0-313">**pedido de transferência** Ponteiro para o pedido de transferência a ser abortado.</span><span class="sxs-lookup"><span data-stu-id="541d0-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-314">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-314">Return Values</span></span>

- <span data-ttu-id="541d0-315">**UX_SUCCESS** (0x00) A transferência USB para este pedido de transferência foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="541d0-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-316">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541d0-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="541d0-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="541d0-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="541d0-318">Solicite uma transferência USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="541d0-319">Prototype</span><span class="sxs-lookup"><span data-stu-id="541d0-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="541d0-320">Descrição</span><span class="sxs-lookup"><span data-stu-id="541d0-320">Description</span></span>

<span data-ttu-id="541d0-321">Esta função executa uma transação USB.</span><span class="sxs-lookup"><span data-stu-id="541d0-321">This function performs a USB transaction.</span></span> <span data-ttu-id="541d0-322">À entrada, o pedido de transferência dá o tubo de ponto final selecionado para esta transação e os parâmetros associados à transferência (carga útil de dados, duração da transação).</span><span class="sxs-lookup"><span data-stu-id="541d0-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="541d0-323">Para o tubo de controlo, a transação está bloqueada e só regressará quando as três fases da transferência de controlo estiverem concluídas ou se houver um erro anterior.</span><span class="sxs-lookup"><span data-stu-id="541d0-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="541d0-324">Para outros tubos, a pilha USB irá agendar a transação na USB, mas não esperará pela sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="541d0-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="541d0-325">Cada pedido de transferência de tubos não bloqueados tem de especificar um manipulador de rotina de conclusão.</span><span class="sxs-lookup"><span data-stu-id="541d0-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="541d0-326">Quando a chamada de função retornar, o estado do pedido de transferência deve ser examinado, uma vez que contém o resultado da transação.</span><span class="sxs-lookup"><span data-stu-id="541d0-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="541d0-327">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="541d0-327">Input Parameter</span></span>

- <span data-ttu-id="541d0-328">**transfer_request** Ponteiro para o pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="541d0-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="541d0-329">O pedido de transferência contém todas as informações necessárias para a transferência.</span><span class="sxs-lookup"><span data-stu-id="541d0-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="541d0-330">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="541d0-330">Return Values</span></span>

- <span data-ttu-id="541d0-331">**UX_SUCCESS** (0x00) A transferência USB para este pedido de transferência foi devidamente agendada.</span><span class="sxs-lookup"><span data-stu-id="541d0-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="541d0-332">O código de estado do pedido de transferência deve ser examinado quando o pedido de transferência estiver concluído.</span><span class="sxs-lookup"><span data-stu-id="541d0-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="541d0-333">**UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para alocar os recursos controladores necessários.</span><span class="sxs-lookup"><span data-stu-id="541d0-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="541d0-334">**UX_TRANSFER_NOT_READY** (0x25) O aparelho encontrava-se num estado inválido – deve ser anexado, endereçado ou configurado.</span><span class="sxs-lookup"><span data-stu-id="541d0-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="541d0-335">Exemplo:</span><span class="sxs-lookup"><span data-stu-id="541d0-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
