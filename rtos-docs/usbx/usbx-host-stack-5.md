---
title: Capítulo 5 - Aulas de Anfitrião USBX API
description: Saiba mais sobre a API das Classes de Anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828621"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="f878e-103">Capítulo 5 - Aulas de Anfitrião USBX API</span><span class="sxs-lookup"><span data-stu-id="f878e-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="f878e-104">Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="f878e-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="f878e-105">As seguintes APIs para cada classe são descritas em detalhe.</span><span class="sxs-lookup"><span data-stu-id="f878e-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="f878e-106">Classe HID</span><span class="sxs-lookup"><span data-stu-id="f878e-106">HID class</span></span>
- <span data-ttu-id="f878e-107">Classe CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="f878e-107">CDC-ACM class</span></span>
- <span data-ttu-id="f878e-108">Classe CDC-ECM</span><span class="sxs-lookup"><span data-stu-id="f878e-108">CDC-ECM class</span></span>
- <span data-ttu-id="f878e-109">Classe de armazenamento</span><span class="sxs-lookup"><span data-stu-id="f878e-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="f878e-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="f878e-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="f878e-111">Registe um cliente HID na classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-112">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="f878e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-113">Description</span></span>

<span data-ttu-id="f878e-114">Esta função é utilizada para registar um cliente HID na classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="f878e-115">A classe HID precisa de encontrar uma correspondência entre um dispositivo HID e um cliente HID antes de solicitar dados deste dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f878e-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="f878e-116">A cadeia C de hid_client_name deve ser anulada e o comprimento do mesmo (sem o próprio exterminador nulo) não deve ser superior **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="f878e-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-117">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-117">Parameters</span></span>

- <span data-ttu-id="f878e-118">**hid_client_name** Ponteiro para o nome do cliente HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="f878e-119">**hid_client_handler** Ponteiro para o manipulador de clientes HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-120">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-120">Return Values</span></span>

- <span data-ttu-id="f878e-121">**UX_SUCCESS** (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="f878e-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f878e-122">**UX_MEMORY_INSUFFICIENT** (0x12) A atribuição de memória para cliente falhou.</span><span class="sxs-lookup"><span data-stu-id="f878e-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="f878e-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Clientes Max já registados.</span><span class="sxs-lookup"><span data-stu-id="f878e-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="f878e-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Esta classe já existe</span><span class="sxs-lookup"><span data-stu-id="f878e-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="f878e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="f878e-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="f878e-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="f878e-127">Registe uma chamada da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-128">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="f878e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-129">Description</span></span>

<span data-ttu-id="f878e-130">Esta função é utilizada para registar uma chamada da classe HID para o cliente HID quando um relatório é recebido.</span><span class="sxs-lookup"><span data-stu-id="f878e-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-131">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-131">Parameters</span></span>

- <span data-ttu-id="f878e-132">**escondeu** Ponteiro para a instância da classe HID</span><span class="sxs-lookup"><span data-stu-id="f878e-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="f878e-133">**call_back** Ponteiro para a estrutura call_back</span><span class="sxs-lookup"><span data-stu-id="f878e-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-134">Valores de retorno</span><span class="sxs-lookup"><span data-stu-id="f878e-134">Return values</span></span>

- <span data-ttu-id="f878e-135">**UX_SUCCESS** (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="f878e-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="f878e-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Caso HID inválido.</span><span class="sxs-lookup"><span data-stu-id="f878e-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="f878e-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Erro no registo de chamada do relatório.</span><span class="sxs-lookup"><span data-stu-id="f878e-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="f878e-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="f878e-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="f878e-140">Inicie o ponto final periódico para uma instância de classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="f878e-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-142">Description</span></span>

<span data-ttu-id="f878e-143">Esta função é utilizada para iniciar o ponto final periódico (interromper) para o exemplo da classe HID que está ligada a este cliente HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="f878e-144">A classe HID não pode iniciar o ponto final periódico até que o cliente HID seja ativado e, portanto, cabe ao cliente HID iniciar este ponto final para receber relatórios.</span><span class="sxs-lookup"><span data-stu-id="f878e-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="f878e-145">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="f878e-145">Input Parameter</span></span>

- <span data-ttu-id="f878e-146">**escondeu** Ponteiro para a instância da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-147">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-147">Return Values</span></span>

- <span data-ttu-id="f878e-148">**UX_SUCCESS** (0x00) Relatórios periódicos com sucesso começaram.</span><span class="sxs-lookup"><span data-stu-id="f878e-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="f878e-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Erro no relatório periódico.</span><span class="sxs-lookup"><span data-stu-id="f878e-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="f878e-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="f878e-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="f878e-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="f878e-153">Pare o ponto final periódico para uma instância de classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="f878e-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-155">Description</span></span>

<span data-ttu-id="f878e-156">Esta função é utilizada para parar o ponto final periódico (interromper) para o exemplo da classe HID que está ligada a este cliente HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="f878e-157">A classe HID não pode parar o ponto final periódico até que o cliente HID seja desativado, todos os seus recursos libertados e, portanto, cabe ao cliente HID parar este ponto final.</span><span class="sxs-lookup"><span data-stu-id="f878e-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="f878e-158">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="f878e-158">Input Parameter</span></span>

- <span data-ttu-id="f878e-159">**escondeu** Ponteiro para a instância da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-160">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-160">Return Values</span></span>

- <span data-ttu-id="f878e-161">**UX_SUCCESS** (0x00) Relatórios periódicos parados com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="f878e-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Erro no relatório periódico.</span><span class="sxs-lookup"><span data-stu-id="f878e-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="f878e-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe</span><span class="sxs-lookup"><span data-stu-id="f878e-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="f878e-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="f878e-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="f878e-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="f878e-166">Obtenha um relatório de uma instância da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="f878e-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-168">Description</span></span>

<span data-ttu-id="f878e-169">Esta função é utilizada para receber um relatório diretamente do dispositivo sem depender do ponto final periódico.</span><span class="sxs-lookup"><span data-stu-id="f878e-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="f878e-170">Este relatório provém do ponto final de controlo, mas o seu tratamento é o mesmo que se tratasse do ponto final periódico.</span><span class="sxs-lookup"><span data-stu-id="f878e-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-171">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-171">Parameters</span></span>

- <span data-ttu-id="f878e-172">**escondeu** Ponteiro para a instância da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="f878e-173">**client_report** Ponteiro para o relatório do cliente hid.</span><span class="sxs-lookup"><span data-stu-id="f878e-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-174">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-174">Return Values</span></span>

- <span data-ttu-id="f878e-175">**UX_SUCCESS** (0x00) O relatório foi recebido com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="f878e-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) O relatório do cliente foi inválido ou erro durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="f878e-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="f878e-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="f878e-178">**UX_BUFFER_OVERFLOW** (0x5d) O tampão fornecido não é suficientemente grande para acomodar o relatório não comprimido.</span><span class="sxs-lookup"><span data-stu-id="f878e-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-179">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="f878e-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="f878e-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="f878e-181">Enviar um relatório</span><span class="sxs-lookup"><span data-stu-id="f878e-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-182">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="f878e-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-183">Description</span></span>

<span data-ttu-id="f878e-184">Esta função é utilizada para enviar um relatório diretamente para o dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f878e-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-185">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-185">Parameters</span></span>

- <span data-ttu-id="f878e-186">**escondeu** Ponteiro para a instância da classe HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="f878e-187">**client_report** Ponteiro para o relatório do cliente hid.</span><span class="sxs-lookup"><span data-stu-id="f878e-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-188">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-188">Return Values</span></span>

- <span data-ttu-id="f878e-189">**UX_SUCCESS** (0x00) O relatório foi enviado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="f878e-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) O relatório do cliente foi inválido ou erro durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="f878e-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="f878e-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="f878e-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) O tampão fornecido não é suficientemente grande para acomodar o relatório não comprimido.</span><span class="sxs-lookup"><span data-stu-id="f878e-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-193">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="f878e-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="f878e-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="f878e-195">Pegue botões de rato.</span><span class="sxs-lookup"><span data-stu-id="f878e-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-196">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="f878e-197">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-197">Description</span></span>

<span data-ttu-id="f878e-198">Esta função é usada para obter os botões do rato</span><span class="sxs-lookup"><span data-stu-id="f878e-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-199">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-199">Parameters</span></span>

- <span data-ttu-id="f878e-200">**mouse_instance** Ponteiro para a instância do rato HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="f878e-201">**mouse_buttons** Ponteiro para os botões de retorno.</span><span class="sxs-lookup"><span data-stu-id="f878e-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-202">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-202">Return Values</span></span>

- <span data-ttu-id="f878e-203">**UX_SUCCESS** botão do rato (0x00) recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="f878e-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-205">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="f878e-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="f878e-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="f878e-207">Obter a posição do rato.</span><span class="sxs-lookup"><span data-stu-id="f878e-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-208">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="f878e-209">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-209">Description</span></span>

<span data-ttu-id="f878e-210">Esta função é usada para obter a posição do rato em coordenadas x & y.</span><span class="sxs-lookup"><span data-stu-id="f878e-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-211">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-211">Parameters</span></span>

- <span data-ttu-id="f878e-212">**mouse_instance** Ponteiro para a instância do rato HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="f878e-213">**mouse_x_position** Ponteiro para a coordenada x.</span><span class="sxs-lookup"><span data-stu-id="f878e-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="f878e-214">**mouse_y_position** Ponteiro para a coordenada y.</span><span class="sxs-lookup"><span data-stu-id="f878e-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-215">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-215">Return Values</span></span>

- <span data-ttu-id="f878e-216">**UX_SUCCESS** (0x00) X &amp; Y coordenadas com sucesso recuperadas.</span><span class="sxs-lookup"><span data-stu-id="f878e-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="f878e-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-218">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="f878e-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="f878e-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="f878e-220">Pegue a chave e o estado do teclado.</span><span class="sxs-lookup"><span data-stu-id="f878e-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="f878e-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-222">Description</span></span>

<span data-ttu-id="f878e-223">Esta função é utilizada para obter a chave e o estado do teclado.</span><span class="sxs-lookup"><span data-stu-id="f878e-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-224">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-224">Parameters</span></span>

- <span data-ttu-id="f878e-225">**keyboard_instance** Ponteiro para a instância do teclado HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="f878e-226">**keyboard_key** Ponteiro para o recipiente da chave do teclado.</span><span class="sxs-lookup"><span data-stu-id="f878e-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="f878e-227">**keyboard_state** Ponteiro para o recipiente do estado do teclado.</span><span class="sxs-lookup"><span data-stu-id="f878e-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-228">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-228">Return Values</span></span>

- <span data-ttu-id="f878e-229">**UX_SUCCESS** (0x00) Chave e estado recuperado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="f878e-230">**UX_ERROR** (0xff) Nada a relatar.</span><span class="sxs-lookup"><span data-stu-id="f878e-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="f878e-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="f878e-232">O estado do teclado pode ter os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="f878e-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="f878e-233">**0x10000** UX_HID_KEYBOARD_STATE_KEY_UP</span><span class="sxs-lookup"><span data-stu-id="f878e-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="f878e-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="f878e-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="f878e-235">**0x0002 UX_HID_KEYBOARD_STATE_CAPS_LOCK**</span><span class="sxs-lookup"><span data-stu-id="f878e-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="f878e-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="f878e-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="f878e-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="f878e-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="f878e-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="f878e-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="f878e-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="f878e-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="f878e-240">**0x0300 UX_HID_KEYBOARD_STATE_SHIFT**</span><span class="sxs-lookup"><span data-stu-id="f878e-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="f878e-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="f878e-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="f878e-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="f878e-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="f878e-243">**0x0a00 UX_HID_KEYBOARD_STATE_ALT**</span><span class="sxs-lookup"><span data-stu-id="f878e-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="f878e-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="f878e-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="f878e-245">**0x2000 UX_HID_KEYBOARD_STATE_RIGHT_CTRL**</span><span class="sxs-lookup"><span data-stu-id="f878e-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="f878e-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="f878e-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="f878e-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="f878e-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="f878e-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="f878e-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="f878e-249">**0xa000 UX_HID_KEYBOARD_STATE_GUI**</span><span class="sxs-lookup"><span data-stu-id="f878e-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="f878e-250">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="f878e-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="f878e-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="f878e-252">Execute uma função IOCTL no teclado HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-253">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="f878e-254">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-254">Description</span></span>

<span data-ttu-id="f878e-255">Esta função executa uma função de coitl específica para o teclado HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="f878e-256">A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.</span><span class="sxs-lookup"><span data-stu-id="f878e-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-257">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-257">Parameters</span></span>

- <span data-ttu-id="f878e-258">**keyboard_instance** Ponteiro para a instância do teclado HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="f878e-259">**ioctl_function** função de localização.</span><span class="sxs-lookup"><span data-stu-id="f878e-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="f878e-260">Consulte a tabela abaixo para uma das funções de coitl permitidas.</span><span class="sxs-lookup"><span data-stu-id="f878e-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="f878e-261">**parâmetro** Ponteiro para um parâmetro específico do ioctl.</span><span class="sxs-lookup"><span data-stu-id="f878e-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-262">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-262">Return Values</span></span>

- <span data-ttu-id="f878e-263">**UX_SUCCESS** (0x00) A função ioctl concluída com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="f878e-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Função IOCTL desconhecida</span><span class="sxs-lookup"><span data-stu-id="f878e-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="f878e-265">Funções ioctl</span><span class="sxs-lookup"><span data-stu-id="f878e-265">IOCTL functions</span></span>

- <span data-ttu-id="f878e-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="f878e-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="f878e-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="f878e-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="f878e-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="f878e-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="f878e-269">Exemplo – alterar o layout do teclado</span><span class="sxs-lookup"><span data-stu-id="f878e-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="f878e-270">Exemplo – desativar a chave do teclado descodificar</span><span class="sxs-lookup"><span data-stu-id="f878e-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="f878e-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="f878e-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="f878e-272">Obtenha o uso do controlo remoto</span><span class="sxs-lookup"><span data-stu-id="f878e-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-273">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="f878e-274">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-274">Description</span></span>

<span data-ttu-id="f878e-275">Esta função é utilizada para obter os controlos remotos.</span><span class="sxs-lookup"><span data-stu-id="f878e-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-276">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-276">Parameters</span></span>

- <span data-ttu-id="f878e-277">**remote_control_instance** Ponteiro para a instância de controlo remoto HID.</span><span class="sxs-lookup"><span data-stu-id="f878e-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="f878e-278">**uso** Ponteiro para o uso.</span><span class="sxs-lookup"><span data-stu-id="f878e-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="f878e-279">**valor** Ponteiro para o valor para a utilização.</span><span class="sxs-lookup"><span data-stu-id="f878e-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-280">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-280">Return Values</span></span>

- <span data-ttu-id="f878e-281">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f878e-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f878e-282">**UX_ERROR** (0xff) Nada a relatar.</span><span class="sxs-lookup"><span data-stu-id="f878e-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="f878e-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso de classe HID não existe.</span><span class="sxs-lookup"><span data-stu-id="f878e-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="f878e-284">A lista de todas as utilizações possíveis é demasiado longa para caber neste manual do utilizador.</span><span class="sxs-lookup"><span data-stu-id="f878e-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="f878e-285">Para uma descrição completa, o ux_host_class_hid.h tem todo o conjunto de valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="f878e-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-286">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="f878e-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="f878e-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="f878e-288">Leia a partir da interface cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="f878e-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="f878e-290">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-290">Description</span></span>

<span data-ttu-id="f878e-291">Esta função lê-se a partir da interface cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="f878e-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="f878e-292">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="f878e-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-293">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-293">Parameters</span></span>

- <span data-ttu-id="f878e-294">**cdc_acm** Apontando para a cdc_acm exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="f878e-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="f878e-295">**data_pointer** Ponteiro para o endereço tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="f878e-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f878e-296">**requested_length** Comprimento a ser recebido.</span><span class="sxs-lookup"><span data-stu-id="f878e-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="f878e-297">**atual_length** Comprimento realmente recebido.</span><span class="sxs-lookup"><span data-stu-id="f878e-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-298">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-298">Return Values</span></span>

- <span data-ttu-id="f878e-299">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f878e-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f878e-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A cdc_acm instância é inválida.</span><span class="sxs-lookup"><span data-stu-id="f878e-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="f878e-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transferir tempo, leitura incompleta.</span><span class="sxs-lookup"><span data-stu-id="f878e-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-302">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="f878e-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="f878e-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="f878e-304">Escreva para a interface cdc_acm</span><span class="sxs-lookup"><span data-stu-id="f878e-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="f878e-306">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-306">Description</span></span>

<span data-ttu-id="f878e-307">Esta função escreve para a interface cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="f878e-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="f878e-308">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="f878e-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-309">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-309">Parameters</span></span>

- <span data-ttu-id="f878e-310">**cdc_acm** Apontando para a cdc_acm exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="f878e-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="f878e-311">**data_pointer** Ponteiro para o endereço tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="f878e-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="f878e-312">**requested_length** Comprimento a ser enviado.</span><span class="sxs-lookup"><span data-stu-id="f878e-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="f878e-313">**atual_length** Comprimento realmente enviado.</span><span class="sxs-lookup"><span data-stu-id="f878e-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="f878e-314">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="f878e-314">Return Values</span></span>

- <span data-ttu-id="f878e-315">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f878e-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f878e-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) A cdc_acm instância é inválida.</span><span class="sxs-lookup"><span data-stu-id="f878e-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="f878e-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transferir tempo, escrevendo incompleto.</span><span class="sxs-lookup"><span data-stu-id="f878e-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="f878e-318">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f878e-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="f878e-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="f878e-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="f878e-320">Execute uma função DE IOCTL para a interface cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="f878e-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-321">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="f878e-322">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-322">Description</span></span>

<span data-ttu-id="f878e-323">Esta função desempenha uma função de coitl específica para a interface cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="f878e-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="f878e-324">A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.</span><span class="sxs-lookup"><span data-stu-id="f878e-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-325">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-325">Parameters</span></span>

- <span data-ttu-id="f878e-326">**cdc_acm** Apontando para a cdc_acm exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="f878e-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="f878e-327">**ioctl_function** função de localização.</span><span class="sxs-lookup"><span data-stu-id="f878e-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="f878e-328">Consulte a tabela abaixo para uma das funções de coitl permitidas.</span><span class="sxs-lookup"><span data-stu-id="f878e-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="f878e-329">**parâmetro** Ponteiro para um parâmetro específico do ioctl</span><span class="sxs-lookup"><span data-stu-id="f878e-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="f878e-330">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="f878e-330">Return Value</span></span>

- <span data-ttu-id="f878e-331">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="f878e-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="f878e-332">**UX_MEMORY_INSUFFICIENT** (0x12) Não tem memória suficiente.</span><span class="sxs-lookup"><span data-stu-id="f878e-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="f878e-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) caso CDC-ACM está num estado inválido.</span><span class="sxs-lookup"><span data-stu-id="f878e-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="f878e-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Função IOCTL desconhecida.</span><span class="sxs-lookup"><span data-stu-id="f878e-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="f878e-335">Funções ioctl:</span><span class="sxs-lookup"><span data-stu-id="f878e-335">IOCTL functions:</span></span>

- <span data-ttu-id="f878e-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="f878e-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="f878e-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="f878e-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="f878e-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="f878e-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="f878e-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="f878e-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="f878e-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="f878e-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="f878e-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="f878e-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="f878e-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="f878e-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="f878e-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="f878e-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="f878e-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="f878e-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="f878e-345">Inicia a receção de dados de fundo do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f878e-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-346">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="f878e-347">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-347">Description</span></span>

<span data-ttu-id="f878e-348">Esta função faz com que o USBX leia continuamente os dados do dispositivo em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="f878e-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="f878e-349">Após a conclusão de cada transação, é invocada a chamada especificada em **cdc_acm_reception** para que a aplicação possa efetuar o tratamento posterior dos dados da transação.</span><span class="sxs-lookup"><span data-stu-id="f878e-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="f878e-350">**ux_host_class_cdc_acm_read** não devem ser utilizados enquanto estiver a ser utilizada a receção de fundo.</span><span class="sxs-lookup"><span data-stu-id="f878e-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-351">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-351">Parameters</span></span>

- <span data-ttu-id="f878e-352">**cdc_acm** Apontando para a cdc_acm exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="f878e-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="f878e-353">**cdc_acm_reception** Ponteiro para parâmetro que contém valores que definem o comportamento da receção de fundo.</span><span class="sxs-lookup"><span data-stu-id="f878e-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="f878e-354">O layout deste parâmetro segue:</span><span class="sxs-lookup"><span data-stu-id="f878e-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="f878e-355">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="f878e-355">Return Value</span></span>

- <span data-ttu-id="f878e-356">**UX_SUCCESS** (0x00) A receção de fundo começou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="f878e-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Instância de classe errada.</span><span class="sxs-lookup"><span data-stu-id="f878e-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="f878e-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="f878e-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="f878e-359">Para a receção de fundo dos pacotes.</span><span class="sxs-lookup"><span data-stu-id="f878e-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="f878e-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="f878e-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="f878e-361">Descrição</span><span class="sxs-lookup"><span data-stu-id="f878e-361">Description</span></span>

<span data-ttu-id="f878e-362">Esta função faz com que o USBX pare a receção de fundo previamente iniciada por **ux_host_class_cdc_acm_reception_start**.</span><span class="sxs-lookup"><span data-stu-id="f878e-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="f878e-363">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f878e-363">Parameters</span></span>

- <span data-ttu-id="f878e-364">**cdc_acm** Apontando para a cdc_acm exemplo de classe.</span><span class="sxs-lookup"><span data-stu-id="f878e-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="f878e-365">**cdc_acm_reception** Ponteiro para o mesmo parâmetro que foi usado para iniciar a receção de fundo.</span><span class="sxs-lookup"><span data-stu-id="f878e-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="f878e-366">O layout deste parâmetro segue:</span><span class="sxs-lookup"><span data-stu-id="f878e-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="f878e-367">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="f878e-367">Return Value</span></span>

- <span data-ttu-id="f878e-368">**UX_SUCCESS** (0x00) A receção de fundo parou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="f878e-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="f878e-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Instância de classe errada.</span><span class="sxs-lookup"><span data-stu-id="f878e-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
