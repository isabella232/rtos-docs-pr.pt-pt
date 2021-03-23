---
title: Capítulo 4 - Descrição dos Serviços de Dispositivos USBX
description: Saiba mais sobre os Serviços de Dispositivo USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828136"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="69c84-103">Descrição dos Serviços de Dispositivos USBX</span><span class="sxs-lookup"><span data-stu-id="69c84-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="69c84-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="69c84-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="69c84-105">Obtenha a definição alternativa atual para um valor de interface</span><span class="sxs-lookup"><span data-stu-id="69c84-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="69c84-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-107">Description</span></span>

<span data-ttu-id="69c84-108">Esta função é utilizada pelo anfitrião USB para obter a definição alternativa atual para um valor de interface específico.</span><span class="sxs-lookup"><span data-stu-id="69c84-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="69c84-109">É chamado pelo controlador quando um **pedido de GET_INTERFACE** é recebido.</span><span class="sxs-lookup"><span data-stu-id="69c84-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-110">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-110">Input Parameter</span></span>

- <span data-ttu-id="69c84-111">**Interface_value** Valor da interface para o qual a definição alternativa atual é consultada</span><span class="sxs-lookup"><span data-stu-id="69c84-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-112">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-112">Return Values</span></span>

- <span data-ttu-id="69c84-113">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="69c84-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="69c84-114">**UX_ERROR** (0xFF) Valor errado da interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="69c84-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="69c84-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="69c84-117">Definir a definição alternativa de corrente para um valor de interface</span><span class="sxs-lookup"><span data-stu-id="69c84-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="69c84-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-119">Description</span></span>

<span data-ttu-id="69c84-120">Esta função é utilizada pelo anfitrião USB para definir a definição alternativa atual para um valor de interface específico.</span><span class="sxs-lookup"><span data-stu-id="69c84-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="69c84-121">É chamado pelo controlador quando um **pedido de SET_INTERFACE** é recebido.</span><span class="sxs-lookup"><span data-stu-id="69c84-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="69c84-122">Quando o **SET_INTERFACE** estiver concluído, os valores das definições alternativas são aplicados à classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="69c84-123">A pilha de dispositivo emitirá um **UX_SLAVE_CLASS_COMMAND_CHANGE** para a classe que detém esta interface para refletir a mudança de configuração alternativa.</span><span class="sxs-lookup"><span data-stu-id="69c84-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-124">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-124">Parameters</span></span>

- <span data-ttu-id="69c84-125">**interface_value**: Valor da interface para o qual a definição alternativa atual é definida.</span><span class="sxs-lookup"><span data-stu-id="69c84-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="69c84-126">**alternate_setting_value**: O novo valor de regulação alternativo.</span><span class="sxs-lookup"><span data-stu-id="69c84-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-127">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-127">Return Values</span></span>

- <span data-ttu-id="69c84-128">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="69c84-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="69c84-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Nenhuma interface ligada.</span><span class="sxs-lookup"><span data-stu-id="69c84-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="69c84-130">**UX_FUNCTION_NOT_SUPPORTED** dispositivo (0x54) não está configurado.</span><span class="sxs-lookup"><span data-stu-id="69c84-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="69c84-131">**UX_ERROR** (0xFF) Valor errado da interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="69c84-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="69c84-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="69c84-134">Registar uma nova classe de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="69c84-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-135">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="69c84-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-136">Description</span></span>

<span data-ttu-id="69c84-137">Esta função é utilizada pela aplicação para registar uma nova classe de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="69c84-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="69c84-138">Esta inscrição inicia um contentor de classe e não um exemplo da classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="69c84-139">Uma classe deve ter um fio ativo e ser anexada a uma interface específica.</span><span class="sxs-lookup"><span data-stu-id="69c84-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="69c84-140">Algumas classes esperam uma lista de parâmetros ou parâmetros.</span><span class="sxs-lookup"><span data-stu-id="69c84-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="69c84-141">Por exemplo, a classe de armazenamento do dispositivo esperaria a geometria do dispositivo de armazenamento que está a tentar imitar.</span><span class="sxs-lookup"><span data-stu-id="69c84-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="69c84-142">O campo de parâmetros depende, portanto, da exigência de classe e pode ser um valor ou um ponteiro para uma estrutura preenchida com os valores de classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="69c84-143">A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="69c84-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-144">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-144">Parameters</span></span>

- <span data-ttu-id="69c84-145">**class_name** Nome da classe</span><span class="sxs-lookup"><span data-stu-id="69c84-145">**class_name** Class Name</span></span>
- <span data-ttu-id="69c84-146">**class_entry_function** A função de entrada da classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="69c84-147">**configuration_number** O número de configuração a que esta classe está anexada.</span><span class="sxs-lookup"><span data-stu-id="69c84-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="69c84-148">**interface_number** O número de interface a que esta classe está anexada.</span><span class="sxs-lookup"><span data-stu-id="69c84-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="69c84-149">**parâmetro** Um ponteiro para uma lista de parâmetros específicos de classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-150">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-150">Return Values</span></span>

- <span data-ttu-id="69c84-151">**UX_SUCCESS** (0x00) A classe foi registada</span><span class="sxs-lookup"><span data-stu-id="69c84-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="69c84-152">**UX_MEMORY_INSUFFICIENT** (0x12) Não há entradas na tabela de aulas.</span><span class="sxs-lookup"><span data-stu-id="69c84-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="69c84-153">**UX_THREAD_ERROR** (0x16) Não pode criar um fio de classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="69c84-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="69c84-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="69c84-156">Não registar uma classe de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="69c84-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-157">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="69c84-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-158">Description</span></span>

<span data-ttu-id="69c84-159">Esta função é utilizada pela aplicação para não registar uma classe de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="69c84-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="69c84-160">A cadeia C de class_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="69c84-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-161">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-161">Parameters</span></span>

- <span data-ttu-id="69c84-162">**class_name**: Nome da classe</span><span class="sxs-lookup"><span data-stu-id="69c84-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="69c84-163">**class_entry_function**: A função de entrada da classe.</span><span class="sxs-lookup"><span data-stu-id="69c84-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-164">Return Values</span></span>

- <span data-ttu-id="69c84-165">**UX_SUCCESS** (0x00) A aula não estava registada.</span><span class="sxs-lookup"><span data-stu-id="69c84-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="69c84-166">**UX_NO_CLASS_MATCH** (0x57) A classe não está registada.</span><span class="sxs-lookup"><span data-stu-id="69c84-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="69c84-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="69c84-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="69c84-169">Obtenha a configuração atual</span><span class="sxs-lookup"><span data-stu-id="69c84-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-170">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="69c84-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-171">Description</span></span>

<span data-ttu-id="69c84-172">Esta função é utilizada pelo anfitrião para obter a configuração atual em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69c84-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-173">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-173">Input Parameter</span></span>

<span data-ttu-id="69c84-174">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69c84-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-175">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-175">Return Value</span></span>

- <span data-ttu-id="69c84-176">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="69c84-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-177">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="69c84-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="69c84-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="69c84-179">Definir a configuração atual</span><span class="sxs-lookup"><span data-stu-id="69c84-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-180">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="69c84-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-181">Description</span></span>

<span data-ttu-id="69c84-182">Esta função é utilizada pelo anfitrião para definir a configuração atual em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69c84-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="69c84-183">Após a receção deste comando, a pilha de dispositivo USB ativará a definição alternativa 0 de cada interface ligada a esta configuração.</span><span class="sxs-lookup"><span data-stu-id="69c84-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-184">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-184">Input Parameter</span></span>

- <span data-ttu-id="69c84-185">**configuration_value** O valor de configuração selecionado pelo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="69c84-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-186">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-186">Return Value</span></span>

- <span data-ttu-id="69c84-187">**UX_SUCCESS** (0x00) A configuração foi definida com sucesso.</span><span class="sxs-lookup"><span data-stu-id="69c84-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="69c84-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="69c84-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="69c84-190">Envie um descritor para o anfitrião</span><span class="sxs-lookup"><span data-stu-id="69c84-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-191">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="69c84-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-192">Description</span></span>

<span data-ttu-id="69c84-193">Esta função é utilizada pelo lado do dispositivo para devolver um descritor ao hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="69c84-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="69c84-194">Este descritor pode ser um descritor de dispositivos, um descritor de configuração ou um descritor de cordas.</span><span class="sxs-lookup"><span data-stu-id="69c84-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-195">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-195">Parameters</span></span>

- <span data-ttu-id="69c84-196">**descriptor_type:** O tipo de descritor.</span><span class="sxs-lookup"><span data-stu-id="69c84-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="69c84-197">Deve ser um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="69c84-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="69c84-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="69c84-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="69c84-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="69c84-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="69c84-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="69c84-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="69c84-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="69c84-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="69c84-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="69c84-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="69c84-203">**request_index:** O índice do descritor.</span><span class="sxs-lookup"><span data-stu-id="69c84-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="69c84-204">**host_length**: O comprimento exigido pelo hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="69c84-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-205">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-205">Return Values</span></span>

- <span data-ttu-id="69c84-206">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="69c84-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="69c84-207">**UX_ERROR** (0xFF) A transferência não foi concluída.</span><span class="sxs-lookup"><span data-stu-id="69c84-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-208">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="69c84-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="69c84-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="69c84-210">Desconexão da pilha de dispositivos</span><span class="sxs-lookup"><span data-stu-id="69c84-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="69c84-212">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-212">Description</span></span>

<span data-ttu-id="69c84-213">O gestor VBUS chama a esta função quando há uma desconexão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69c84-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="69c84-214">A pilha do dispositivo informará todas as classes registadas neste dispositivo e, posteriormente, libertará todos os recursos do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69c84-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-215">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-215">Input Parameter</span></span>

<span data-ttu-id="69c84-216">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69c84-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-217">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-217">Return Value</span></span>

- <span data-ttu-id="69c84-218">**UX_SUCCESS** (0x00) O aparelho foi desligado.</span><span class="sxs-lookup"><span data-stu-id="69c84-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-219">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="69c84-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="69c84-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="69c84-221">Pedido condição de paragem de ponto final</span><span class="sxs-lookup"><span data-stu-id="69c84-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-222">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="69c84-223">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-223">Description</span></span>

<span data-ttu-id="69c84-224">Esta função é chamada pela classe do dispositivo USB quando um ponto final deve devolver uma condição de Paragem ao anfitrião.</span><span class="sxs-lookup"><span data-stu-id="69c84-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-225">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-225">Input Parameter</span></span>

- <span data-ttu-id="69c84-226">**ponto final** O ponto final sobre o qual é solicitada a condição de Stall.</span><span class="sxs-lookup"><span data-stu-id="69c84-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-227">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-227">Return Value</span></span>

- <span data-ttu-id="69c84-228">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-229">**UX_ERROR** (0xFF) O aparelho encontra-se num estado inválido.</span><span class="sxs-lookup"><span data-stu-id="69c84-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="69c84-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="69c84-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="69c84-232">Acorde o anfitrião</span><span class="sxs-lookup"><span data-stu-id="69c84-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-233">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="69c84-234">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-234">Description</span></span>

<span data-ttu-id="69c84-235">Esta função é chamada quando o dispositivo quer acordar o hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="69c84-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="69c84-236">Este comando só é válido quando o dispositivo estiver em modo de suspensão.</span><span class="sxs-lookup"><span data-stu-id="69c84-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="69c84-237">Cabe à aplicação do dispositivo decidir quando pretende acordar o anfitrião USB.</span><span class="sxs-lookup"><span data-stu-id="69c84-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="69c84-238">Por exemplo, um modem USB pode acordar um hospedeiro quando deteta um sinal RING na linha telefónica.</span><span class="sxs-lookup"><span data-stu-id="69c84-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-239">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-239">Input Parameter</span></span>

<span data-ttu-id="69c84-240">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69c84-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-241">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="69c84-241">Return values</span></span>

- <span data-ttu-id="69c84-242">**UX_SUCCESS** (0x00) A chamada foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="69c84-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) A chamada falhou (o aparelho provavelmente não estava no modo suspenso).</span><span class="sxs-lookup"><span data-stu-id="69c84-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="69c84-244">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="69c84-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="69c84-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="69c84-246">Inicialize a pilha de dispositivo USB</span><span class="sxs-lookup"><span data-stu-id="69c84-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-247">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="69c84-248">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-248">Description</span></span>

<span data-ttu-id="69c84-249">Esta função é chamada pela aplicação para inicializar a pilha de dispositivo USB.</span><span class="sxs-lookup"><span data-stu-id="69c84-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="69c84-250">Não inicializa nenhuma aula ou controlador.</span><span class="sxs-lookup"><span data-stu-id="69c84-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="69c84-251">Isto deve ser feito com chamadas de função separadas.</span><span class="sxs-lookup"><span data-stu-id="69c84-251">This should be done with separate function calls.</span></span> <span data-ttu-id="69c84-252">Esta chamada fornece principalmente a pilha com a estrutura do dispositivo para a função USB.</span><span class="sxs-lookup"><span data-stu-id="69c84-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="69c84-253">Suporta velocidades altas e a toda a velocidade com a possibilidade de ter uma estrutura de dispositivo completamente separada para cada velocidade.</span><span class="sxs-lookup"><span data-stu-id="69c84-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="69c84-254">A estrutura de cordas e várias línguas são suportadas.</span><span class="sxs-lookup"><span data-stu-id="69c84-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-255">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-255">Parameters</span></span>

- <span data-ttu-id="69c84-256">**device_framework_high_speed**: Ponteiro para a estrutura de alta velocidade.</span><span class="sxs-lookup"><span data-stu-id="69c84-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="69c84-257">**device_framework_length_high_speed**: Comprimento da estrutura de alta velocidade.</span><span class="sxs-lookup"><span data-stu-id="69c84-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="69c84-258">**device_framework_full_speed**: Ponteiro para a estrutura de velocidade máxima.</span><span class="sxs-lookup"><span data-stu-id="69c84-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="69c84-259">**device_framework_length_full_speed**: Comprimento da estrutura de velocidade máxima.</span><span class="sxs-lookup"><span data-stu-id="69c84-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="69c84-260">**string_framework**: Ponteiro para a estrutura das cordas.</span><span class="sxs-lookup"><span data-stu-id="69c84-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="69c84-261">**string_framework_length**: Comprimento da estrutura das cordas.</span><span class="sxs-lookup"><span data-stu-id="69c84-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="69c84-262">**language_id_framework**: Ponteiro para a estrutura da linguagem das cordas.</span><span class="sxs-lookup"><span data-stu-id="69c84-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="69c84-263">**language_id_framework_length**: Comprimento da estrutura da linguagem de cordas.</span><span class="sxs-lookup"><span data-stu-id="69c84-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="69c84-264">**ux_system_slave_change_function**: Função a ser chamada quando o estado do dispositivo mudar.</span><span class="sxs-lookup"><span data-stu-id="69c84-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-265">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-265">Return Values</span></span>

- <span data-ttu-id="69c84-266">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-267">**UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para inicializar a pilha.</span><span class="sxs-lookup"><span data-stu-id="69c84-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="69c84-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) O descritor é inválido.</span><span class="sxs-lookup"><span data-stu-id="69c84-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-269">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="69c84-270">O pedido pode solicitar uma chamada de volta quando o controlador alterar o seu estado.</span><span class="sxs-lookup"><span data-stu-id="69c84-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="69c84-271">Os dois principais estados do controlador são:</span><span class="sxs-lookup"><span data-stu-id="69c84-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="69c84-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="69c84-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="69c84-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="69c84-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="69c84-274">Se a aplicação não necessitar de sinais de suspensão/retoma, fornecerá uma função UX_NULL.</span><span class="sxs-lookup"><span data-stu-id="69c84-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="69c84-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="69c84-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="69c84-276">Excluir uma interface de pilha</span><span class="sxs-lookup"><span data-stu-id="69c84-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-277">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="69c84-278">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-278">Description</span></span>

<span data-ttu-id="69c84-279">Esta função é chamada quando uma interface deve ser removida.</span><span class="sxs-lookup"><span data-stu-id="69c84-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="69c84-280">Uma interface é removida quando um dispositivo é extraído, ou após um reset do autocarro, ou quando há uma nova definição alternativa.</span><span class="sxs-lookup"><span data-stu-id="69c84-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-281">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-281">Input Parameter</span></span>

- <span data-ttu-id="69c84-282">**interface**: Ponteiro para a interface a remover.</span><span class="sxs-lookup"><span data-stu-id="69c84-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-283">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-283">Return Value</span></span>

- <span data-ttu-id="69c84-284">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-285">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="69c84-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="69c84-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="69c84-287">Obtenha o valor atual da interface</span><span class="sxs-lookup"><span data-stu-id="69c84-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="69c84-289">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-289">Description</span></span>

<span data-ttu-id="69c84-290">Esta função é chamada quando o anfitrião consulta a interface atual.</span><span class="sxs-lookup"><span data-stu-id="69c84-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="69c84-291">O dispositivo devolve o valor atual da interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="69c84-292">Esta função é prevadida.</span><span class="sxs-lookup"><span data-stu-id="69c84-292">This function is deprecated.</span></span> <span data-ttu-id="69c84-293">Está disponível para software antigo, mas o novo software deve utilizar a ***função ux_device_stack_alternate_setting_get.***</span><span class="sxs-lookup"><span data-stu-id="69c84-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-294">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-294">Input Parameter</span></span>

- <span data-ttu-id="69c84-295">**interface_value** Valor da interface para devolver.</span><span class="sxs-lookup"><span data-stu-id="69c84-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-296">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-296">Return Values</span></span>

- <span data-ttu-id="69c84-297">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-298">**UX_ERROR** (0xFF) Não existe interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-299">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="69c84-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="69c84-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="69c84-301">Alterar a definição alternativa da interface</span><span class="sxs-lookup"><span data-stu-id="69c84-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-302">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="69c84-303">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-303">Description</span></span>

<span data-ttu-id="69c84-304">Esta função é chamada quando o anfitrião solicita uma alteração da definição alternativa para a interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-305">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-305">Parameters</span></span>

- <span data-ttu-id="69c84-306">**device_framework**: Endereço da estrutura do dispositivo para esta interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="69c84-307">**device_framework_length**: Comprimento da estrutura do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69c84-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="69c84-308">**alternate_setting_value**: Valor de definição alternativo a utilizar por esta interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-309">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-309">Return Values</span></span>

- <span data-ttu-id="69c84-310">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-311">**UX_ERROR** (0xFF) Não existe interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-312">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="69c84-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="69c84-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="69c84-314">Comece a procurar uma classe para possuir uma instância de interface</span><span class="sxs-lookup"><span data-stu-id="69c84-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-315">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="69c84-316">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-316">Description</span></span>

<span data-ttu-id="69c84-317">Esta função é chamada quando uma interface foi selecionada pelo anfitrião e a pilha de dispositivos precisa de procurar uma classe de dispositivo para possuir esta instância de interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="69c84-318">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="69c84-318">Input Parameter</span></span>

- <span data-ttu-id="69c84-319">**interface**: Ponteiro para a interface criada.</span><span class="sxs-lookup"><span data-stu-id="69c84-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-320">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-320">Return Values</span></span>

- <span data-ttu-id="69c84-321">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-322">**UX_NO_CLASS_MATCH** (0x57) Não existe classe para esta interface.</span><span class="sxs-lookup"><span data-stu-id="69c84-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-323">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="69c84-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="69c84-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="69c84-325">Pedido de transferência de dados para o anfitrião</span><span class="sxs-lookup"><span data-stu-id="69c84-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="69c84-327">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-327">Description</span></span>

<span data-ttu-id="69c84-328">Esta função é chamada quando uma classe ou a stack quer transferir dados para o anfitrião.</span><span class="sxs-lookup"><span data-stu-id="69c84-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="69c84-329">O anfitrião sempre sonda o dispositivo, mas o dispositivo pode preparar dados com antecedência.</span><span class="sxs-lookup"><span data-stu-id="69c84-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-330">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-330">Parameters</span></span>

- <span data-ttu-id="69c84-331">**transfer_request**: Ponteiro para o pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="69c84-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="69c84-332">**slave_length**: Comprimento o aparelho quer voltar.</span><span class="sxs-lookup"><span data-stu-id="69c84-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="69c84-333">**host_length:** Comprimento solicitado pelo anfitrião.</span><span class="sxs-lookup"><span data-stu-id="69c84-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="69c84-334">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="69c84-334">Return Values</span></span>

- <span data-ttu-id="69c84-335">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="69c84-336">**UX_TRANSFER_NOT_READY** (0x25) O dispositivo encontra-se num estado inválido; deve ser **fixado,** **configurado,** ou **endereçado**.</span><span class="sxs-lookup"><span data-stu-id="69c84-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="69c84-337">**UX_ERROR** (0xFF) Erro de transporte.</span><span class="sxs-lookup"><span data-stu-id="69c84-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-338">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="69c84-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="69c84-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="69c84-340">Cancelar um pedido de transferência</span><span class="sxs-lookup"><span data-stu-id="69c84-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-341">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="69c84-342">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-342">Description</span></span>

<span data-ttu-id="69c84-343">Esta função é chamada quando uma aplicação precisa cancelar um pedido de transferência ou quando a stack precisa abortar um pedido de transferência associado a um ponto final.</span><span class="sxs-lookup"><span data-stu-id="69c84-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-344">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-344">Parameters</span></span>

- <span data-ttu-id="69c84-345">**transfer_request**: Ponteiro para o pedido de transferência.</span><span class="sxs-lookup"><span data-stu-id="69c84-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="69c84-346">**completion_code:** Código de erro a devolver à classe à espera que este pedido de transferência seja concluído.</span><span class="sxs-lookup"><span data-stu-id="69c84-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-347">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-347">Return Value</span></span>

- <span data-ttu-id="69c84-348">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="69c84-349">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69c84-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="69c84-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="69c84-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="69c84-351">Pilha de unitialização</span><span class="sxs-lookup"><span data-stu-id="69c84-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="69c84-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="69c84-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="69c84-353">Descrição</span><span class="sxs-lookup"><span data-stu-id="69c84-353">Description</span></span>

<span data-ttu-id="69c84-354">Esta função é chamada quando uma aplicação precisa de unitizar a pilha de dispositivos USBX – todos os recursos de pilha de dispositivos são libertados.</span><span class="sxs-lookup"><span data-stu-id="69c84-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="69c84-355">Isto deve ser chamado depois de todas as aulas não terem sido registadas através de ux_device_stack_class_unregister.</span><span class="sxs-lookup"><span data-stu-id="69c84-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="69c84-356">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69c84-356">Parameters</span></span>

<span data-ttu-id="69c84-357">Nenhum</span><span class="sxs-lookup"><span data-stu-id="69c84-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="69c84-358">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="69c84-358">Return Value</span></span>

<span data-ttu-id="69c84-359">**UX_SUCCESS** (0x00) Esta operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="69c84-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
