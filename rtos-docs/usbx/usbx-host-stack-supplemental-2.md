---
title: Aulas de anfitrião USBX API
description: Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104828112"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="72c82-103">Capítulo 2: Aulas de anfitrião USBX API</span><span class="sxs-lookup"><span data-stu-id="72c82-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="72c82-104">Este capítulo abrange todas as APIs expostas das classes de anfitriões USBX.</span><span class="sxs-lookup"><span data-stu-id="72c82-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="72c82-105">As seguintes APIs para cada classe são descritas em detalhe.</span><span class="sxs-lookup"><span data-stu-id="72c82-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="72c82-106">Classe de impressora</span><span class="sxs-lookup"><span data-stu-id="72c82-106">Printer class</span></span>
- <span data-ttu-id="72c82-107">Classe de áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-107">Audio class</span></span>
- <span data-ttu-id="72c82-108">Classe Asix</span><span class="sxs-lookup"><span data-stu-id="72c82-108">Asix class</span></span>
- <span data-ttu-id="72c82-109">Aula de Pima/PTP</span><span class="sxs-lookup"><span data-stu-id="72c82-109">Pima/PTP class</span></span>
- <span data-ttu-id="72c82-110">Classe prolífica</span><span class="sxs-lookup"><span data-stu-id="72c82-110">Prolific class</span></span>
- <span data-ttu-id="72c82-111">Classe em série genérica</span><span class="sxs-lookup"><span data-stu-id="72c82-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="72c82-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="72c82-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="72c82-113">Leia a partir da interface da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-114">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-115">Description</span></span>

<span data-ttu-id="72c82-116">Esta função lê-se a partir da interface da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-116">This function reads from the printer interface.</span></span> <span data-ttu-id="72c82-117">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="72c82-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="72c82-118">Uma leitura só é permitida em impressoras bidis.</span><span class="sxs-lookup"><span data-stu-id="72c82-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-119">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-119">Parameters</span></span>

- <span data-ttu-id="72c82-120">**impressora**: Ponteiro para a instância da classe da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="72c82-121">**data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="72c82-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="72c82-122">**requested_length:** Comprimento a receber.</span><span class="sxs-lookup"><span data-stu-id="72c82-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="72c82-123">**atual_length:** Comprimento realmente recebido.</span><span class="sxs-lookup"><span data-stu-id="72c82-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-124">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-124">Return Value</span></span>

- <span data-ttu-id="72c82-125">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada porque a impressora não é bidisal.</span><span class="sxs-lookup"><span data-stu-id="72c82-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="72c82-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.</span><span class="sxs-lookup"><span data-stu-id="72c82-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="72c82-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="72c82-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="72c82-130">Escreva para a interface da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-132">Description</span></span>

<span data-ttu-id="72c82-133">Esta função escreve para a interface da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-133">This function writes to the printer interface.</span></span> <span data-ttu-id="72c82-134">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="72c82-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-135">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-135">Parameters</span></span>

- <span data-ttu-id="72c82-136">**impressora**: Ponteiro para a instância da classe da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="72c82-137">**data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="72c82-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="72c82-138">**requested_length:** Comprimento a enviar.</span><span class="sxs-lookup"><span data-stu-id="72c82-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="72c82-139">**atual_length:** Comprimento realmente enviado.</span><span class="sxs-lookup"><span data-stu-id="72c82-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-140">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-140">Return Value</span></span>

- <span data-ttu-id="72c82-141">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo limite, escrever incompleto.</span><span class="sxs-lookup"><span data-stu-id="72c82-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="72c82-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="72c82-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="72c82-145">Execute um reset suave à impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-146">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="72c82-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-147">Description</span></span>

<span data-ttu-id="72c82-148">Esta função executa um reset suave à impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="72c82-149">Parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="72c82-149">Input Parameter</span></span>

- <span data-ttu-id="72c82-150">**impressora**: Ponteiro para a instância da classe da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-151">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-151">Return Value</span></span>

- <span data-ttu-id="72c82-152">**UX_SUCCESS**: (0x00)O reset foi concluído.</span><span class="sxs-lookup"><span data-stu-id="72c82-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="72c82-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Tempo de transferência, reset não concluído.</span><span class="sxs-lookup"><span data-stu-id="72c82-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="72c82-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="72c82-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="72c82-156">Obtenha o estado da impressora</span><span class="sxs-lookup"><span data-stu-id="72c82-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-157">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="72c82-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-158">Description</span></span>

<span data-ttu-id="72c82-159">Esta função obtém o estado da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-159">This function obtains the printer status.</span></span> <span data-ttu-id="72c82-160">O estado da impressora é semelhante ao estado LPT (padrão 1284).</span><span class="sxs-lookup"><span data-stu-id="72c82-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-161">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-161">Parameters</span></span>

- <span data-ttu-id="72c82-162">**impressora**: Ponteiro para a instância da classe da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="72c82-163">**printer_status**: Endereço do estado a devolver.</span><span class="sxs-lookup"><span data-stu-id="72c82-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-164">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-164">Return Value</span></span>

- <span data-ttu-id="72c82-165">**UX_SUCCESS** (0x00): O reset foi concluído.</span><span class="sxs-lookup"><span data-stu-id="72c82-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="72c82-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Não há memória suficiente para efetuar a operação.</span><span class="sxs-lookup"><span data-stu-id="72c82-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="72c82-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Tempo de transferência, reset não concluído</span><span class="sxs-lookup"><span data-stu-id="72c82-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="72c82-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="72c82-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="72c82-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="72c82-170">Pegue o dispositivo da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="72c82-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-172">Description</span></span>

<span data-ttu-id="72c82-173">Esta função obtém a cadeia de ID do dispositivo ID do dispositivo IEEE 1284 (incluindo o comprimento nos dois primeiros bytes em grande formato endiano).</span><span class="sxs-lookup"><span data-stu-id="72c82-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-174">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-174">Parameters</span></span>

- <span data-ttu-id="72c82-175">**impressora**: Ponteiro para a instância da classe da impressora.</span><span class="sxs-lookup"><span data-stu-id="72c82-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="72c82-176">**descriptor_buffer**: Ponteiro para um tampão para encher a cadeia de ID do dispositivo ID do dispositivo IEEE 1284 (incluindo o comprimento nos dois primeiros bytes em formato BE)</span><span class="sxs-lookup"><span data-stu-id="72c82-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="72c82-177">**comprimento**: Comprimento do tampão em bytes.</span><span class="sxs-lookup"><span data-stu-id="72c82-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-178">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-178">Return Value</span></span>

- <span data-ttu-id="72c82-179">**UX_SUCCESS** (0x00): A operação foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="72c82-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="72c82-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Não há memória suficiente para efetuar a operação.</span><span class="sxs-lookup"><span data-stu-id="72c82-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="72c82-181">**UX_TRANSFER_TIMEOUT:**(0x5c) Tempo de transferência, pedido não concluído</span><span class="sxs-lookup"><span data-stu-id="72c82-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="72c82-182">**UX_TRANSFER_NOT_READY**: (0x25) O aparelho encontrava-se num estado inválido – deve ser anexado, endereçado ou configurado.</span><span class="sxs-lookup"><span data-stu-id="72c82-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="72c82-183">**UX_TRANSFER_STALL**: (0x21) A transferência parou.</span><span class="sxs-lookup"><span data-stu-id="72c82-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="72c82-184">**TX_WAIT_ABORTED** (0x1A) A suspensão foi abortada por outro fio, temporizador ou ISR.</span><span class="sxs-lookup"><span data-stu-id="72c82-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="72c82-185">**TX_SEMAPHORE_ERROR** (0x0C) Ponteiro semaphore de contagem inválida.</span><span class="sxs-lookup"><span data-stu-id="72c82-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="72c82-186">**TX_WAIT_ERROR** (0x04) Uma opção de espera que não TX_NO_WAIT foi especificada numa chamada de um não-fio.</span><span class="sxs-lookup"><span data-stu-id="72c82-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-187">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="72c82-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="72c82-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="72c82-189">Leia a partir da interface áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-190">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="72c82-191">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-191">Description</span></span>

<span data-ttu-id="72c82-192">Esta função lê a partir da interface de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-192">This function reads from the audio interface.</span></span> <span data-ttu-id="72c82-193">A chamada não está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="72c82-193">The call is non-blocking.</span></span> <span data-ttu-id="72c82-194">A aplicação deve garantir que a definição alternativa adequada foi selecionada para a interface de streaming de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-195">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-195">Parameters</span></span>

- <span data-ttu-id="72c82-196">**áudio**: Ponteiro para a instância da classe áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="72c82-197">**audio_transfer_request**: Ponteiro para a estrutura de transferência de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-198">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-198">Return Value</span></span>

- <span data-ttu-id="72c82-199">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="72c82-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="72c82-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Função não suportada</span><span class="sxs-lookup"><span data-stu-id="72c82-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="72c82-201">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="72c82-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="72c82-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="72c82-203">Escreva para a interface de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="72c82-205">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-205">Description</span></span>

<span data-ttu-id="72c82-206">Esta função escreve para a interface de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-206">This function writes to the audio interface.</span></span> <span data-ttu-id="72c82-207">A chamada não está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="72c82-207">The call is non-blocking.</span></span> <span data-ttu-id="72c82-208">A aplicação deve garantir que a definição alternativa adequada foi selecionada para a interface de streaming de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-209">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-209">Parameters</span></span>

- <span data-ttu-id="72c82-210">**áudio**: Ponteiro para a instância da classe áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="72c82-211">**audio_transfer_request**: Ponteiro para a estrutura de transferência de áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-212">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-212">Return Value</span></span>

- <span data-ttu-id="72c82-213">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada.</span><span class="sxs-lookup"><span data-stu-id="72c82-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="72c82-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta.</span><span class="sxs-lookup"><span data-stu-id="72c82-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="72c82-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="72c82-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="72c82-218">Obtenha um controlo específico da interface de controlo de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="72c82-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-220">Description</span></span>

<span data-ttu-id="72c82-221">Esta função lê um controlo específico da interface de controlo de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-222">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-222">Parameters</span></span>

- <span data-ttu-id="72c82-223">**áudio**: Ponteiro para a instância da classe áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="72c82-224">**audio_control**: Ponteiro para a estrutura de controlo de áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-225">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-225">Return Value</span></span>

- <span data-ttu-id="72c82-226">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="72c82-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="72c82-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada</span><span class="sxs-lookup"><span data-stu-id="72c82-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="72c82-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta</span><span class="sxs-lookup"><span data-stu-id="72c82-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="72c82-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="72c82-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="72c82-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="72c82-231">Desa ajuste um controlo específico à interface de controlo de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-232">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="72c82-233">\*\*Descrição \*\*</span><span class="sxs-lookup"><span data-stu-id="72c82-233">\*\*Description \*\*</span></span>

<span data-ttu-id="72c82-234">Esta função define um controlo específico da interface de controlo de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-235">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-235">Parameters</span></span>

- <span data-ttu-id="72c82-236">**áudio**: Ponteiro para a instância da classe áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="72c82-237">**audio_control**: Ponteiro para a estrutura de controlo de áudio</span><span class="sxs-lookup"><span data-stu-id="72c82-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-238">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-238">Return Value</span></span>

- <span data-ttu-id="72c82-239">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="72c82-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="72c82-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada</span><span class="sxs-lookup"><span data-stu-id="72c82-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="72c82-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta</span><span class="sxs-lookup"><span data-stu-id="72c82-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="72c82-242">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="72c82-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="72c82-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="72c82-244">Defina uma interface de definição alternativa da interface de streaming de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="72c82-246">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-246">Description</span></span>

<span data-ttu-id="72c82-247">Esta função define a interface de regulação alternativa adequada da interface de streaming de áudio de acordo com uma estrutura de amostragem específica.</span><span class="sxs-lookup"><span data-stu-id="72c82-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-248">Parameters</span></span>

- <span data-ttu-id="72c82-249">**áudio**: Ponteiro para a instância da classe áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="72c82-250">**audio_sampling**: Ponteiro para a estrutura de amostragem de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-251">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-251">Return Value</span></span>

- <span data-ttu-id="72c82-252">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="72c82-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="72c82-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada</span><span class="sxs-lookup"><span data-stu-id="72c82-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="72c82-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta</span><span class="sxs-lookup"><span data-stu-id="72c82-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="72c82-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) Não há definição alternativa para os valores de amostragem</span><span class="sxs-lookup"><span data-stu-id="72c82-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="72c82-256">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="72c82-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="72c82-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="72c82-258">Obtenha possíveis definições de amostragem da interface de streaming de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-259">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="72c82-260">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-260">Description</span></span>

<span data-ttu-id="72c82-261">Esta função obtém, uma a uma, todas as definições de amostragem possíveis disponíveis em cada uma das definições alternativas da interface de streaming de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="72c82-262">Na primeira vez que a função for utilizada, todos os campos do ponteiro da estrutura de chamada devem ser reiniciados.</span><span class="sxs-lookup"><span data-stu-id="72c82-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="72c82-263">A função retornará um conjunto específico de valores de streaming após a devolução, a menos que tenha sido atingido o fim das definições alternativas.</span><span class="sxs-lookup"><span data-stu-id="72c82-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="72c82-264">Quando esta função for reutilizada, os valores de amostragem anteriores serão utilizados para encontrar os valores de amostragem seguintes.</span><span class="sxs-lookup"><span data-stu-id="72c82-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-265">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-265">Parameters</span></span>

- <span data-ttu-id="72c82-266">**áudio**: Ponteiro para a instância da classe áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="72c82-267">**audio_sampling**: Ponteiro para a estrutura de amostragem de áudio.</span><span class="sxs-lookup"><span data-stu-id="72c82-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-268">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-268">Return Value</span></span>

- <span data-ttu-id="72c82-269">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída</span><span class="sxs-lookup"><span data-stu-id="72c82-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="72c82-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Função não suportada</span><span class="sxs-lookup"><span data-stu-id="72c82-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="72c82-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interface incorreta</span><span class="sxs-lookup"><span data-stu-id="72c82-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="72c82-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) Não há definição alternativa para os valores de amostragem</span><span class="sxs-lookup"><span data-stu-id="72c82-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="72c82-273">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="72c82-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="72c82-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="72c82-275">Leia a partir da interface asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-276">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-277">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-277">Description</span></span>

<span data-ttu-id="72c82-278">Esta função lê-se a partir da interface asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-278">This function reads from the asix interface.</span></span> <span data-ttu-id="72c82-279">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="72c82-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-280">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-280">Parameters</span></span>

- <span data-ttu-id="72c82-281">**asix**: Ponteiro para a instância de classe asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="72c82-282">**data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="72c82-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="72c82-283">**requested_length:** Comprimento a receber.</span><span class="sxs-lookup"><span data-stu-id="72c82-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="72c82-284">**atual_length:** Comprimento realmente recebido.</span><span class="sxs-lookup"><span data-stu-id="72c82-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-285">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-285">Return Value</span></span>

- <span data-ttu-id="72c82-286">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.</span><span class="sxs-lookup"><span data-stu-id="72c82-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-288">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="72c82-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="72c82-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="72c82-290">Escreva para a interface asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-291">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="72c82-292">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-292">Description</span></span>

<span data-ttu-id="72c82-293">Esta função escreve para a interface asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-293">This function writes to the asix interface.</span></span> <span data-ttu-id="72c82-294">A chamada não está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="72c82-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-295">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-295">Parameters</span></span>

- <span data-ttu-id="72c82-296">**asix**: Ponteiro para a instância de classe asix.</span><span class="sxs-lookup"><span data-stu-id="72c82-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="72c82-297">**pacote**: Pacote de dados Netx</span><span class="sxs-lookup"><span data-stu-id="72c82-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-298">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-298">Return Value</span></span>

- <span data-ttu-id="72c82-299">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-300">**UX_ERROR:**(0xFF) Não foi possível solicitar a transferência.</span><span class="sxs-lookup"><span data-stu-id="72c82-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-301">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="72c82-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="72c82-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="72c82-303">Abra uma sessão entre Iniciador e Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="72c82-305">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-305">Description</span></span>

<span data-ttu-id="72c82-306">Esta função abre uma sessão entre um Iniciador PIMA e um PIMA Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="72c82-307">Uma vez aberta uma sessão com sucesso, a maioria dos comandos PIMA podem ser executados.</span><span class="sxs-lookup"><span data-stu-id="72c82-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-308">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-308">Parameters</span></span>

- <span data-ttu-id="72c82-309">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-310">**pima_sessio**:< da sessão de ponte para o PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-311">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-311">Return Value</span></span>

- <span data-ttu-id="72c82-312">**UX_SUCCESS**: (0x00) Sessão aberta com sucesso</span><span class="sxs-lookup"><span data-stu-id="72c82-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="72c82-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Sessão já aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="72c82-314">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="72c82-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="72c82-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="72c82-316">Feche uma sessão entre o Iniciador e o Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="72c82-318">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-318">Description</span></span>

<span data-ttu-id="72c82-319">Esta função encerra uma sessão que foi previamente aberta entre um Iniciador PIMA e um PIMA Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="72c82-320">Uma vez que uma sessão é fechada, a maioria dos comandos PIMA não podem mais ser executados.</span><span class="sxs-lookup"><span data-stu-id="72c82-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-321">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-321">Parameters</span></span>

- <span data-ttu-id="72c82-322">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-323">**pima_session**: Pointer to PIMA session.</span><span class="sxs-lookup"><span data-stu-id="72c82-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-324">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-324">Return Value</span></span>

- <span data-ttu-id="72c82-325">**UX_SUCCESS**: (0x00) A sessão foi encerrada.</span><span class="sxs-lookup"><span data-stu-id="72c82-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="72c82-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.</span><span class="sxs-lookup"><span data-stu-id="72c82-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-327">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="72c82-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="72c82-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="72c82-329">Obtenha o conjunto de identificação de armazenamento do Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-330">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="72c82-331">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-331">Description</span></span>

<span data-ttu-id="72c82-332">Esta função obtém a matriz de identificação de armazenamento do respondente.</span><span class="sxs-lookup"><span data-stu-id="72c82-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-333">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-333">Parameters</span></span>

- <span data-ttu-id="72c82-334">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-335">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-336">**storage_ids_array**: Array onde os IDs de armazenamento serão devolvidos</span><span class="sxs-lookup"><span data-stu-id="72c82-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="72c82-337">**storage_id_length**: Comprimento da matriz de armazenamento</span><span class="sxs-lookup"><span data-stu-id="72c82-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-338">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-338">Return Value</span></span>

- <span data-ttu-id="72c82-339">**UX_SUCCESS**: (0x00) A matriz de ID de armazenamento foi povoada</span><span class="sxs-lookup"><span data-stu-id="72c82-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="72c82-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-341">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-342">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="72c82-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="72c82-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="72c82-344">Obtenha a informação de armazenamento do Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="72c82-346">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-346">Description</span></span>

<span data-ttu-id="72c82-347">Esta função obtém a informação de armazenamento de um recipiente de armazenamento de valor *storage_id*.</span><span class="sxs-lookup"><span data-stu-id="72c82-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-348">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-348">Parameters</span></span>

- <span data-ttu-id="72c82-349">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-350">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-351">**storage_id**: Identificação do recipiente de armazenamento</span><span class="sxs-lookup"><span data-stu-id="72c82-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="72c82-352">**armazenamento**: Ponteiro para o recipiente de informação de armazenamento</span><span class="sxs-lookup"><span data-stu-id="72c82-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-353">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-353">Return Value</span></span>

- <span data-ttu-id="72c82-354">**UX_SUCCESS**: (0x00) A informação de armazenamento foi recuperada</span><span class="sxs-lookup"><span data-stu-id="72c82-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="72c82-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-356">**UX_MEMORY_INSUFFICIENT** (0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-357">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="72c82-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="72c82-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="72c82-359">Obtenha o número de objetos num recipiente de armazenamento da Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="72c82-361">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-361">Description</span></span>

<span data-ttu-id="72c82-362">Esta função obtém o número de objetos armazenados num recipiente de armazenamento específico de valor storage_id que correspondem a um código de formato específico.</span><span class="sxs-lookup"><span data-stu-id="72c82-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="72c82-363">O número de objetos é devolvido no campo: ux_host_class_pima_session_nb_objects da estrutura pima_session.</span><span class="sxs-lookup"><span data-stu-id="72c82-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-364">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-364">Parameters</span></span>

- <span data-ttu-id="72c82-365">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-366">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-367">**storage_id**: Identificação do recipiente de armazenamento</span><span class="sxs-lookup"><span data-stu-id="72c82-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="72c82-368">**object_format_code**: Filtro de código de formato de objetos.</span><span class="sxs-lookup"><span data-stu-id="72c82-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="72c82-369">Os Códigos de Formato de Objeto podem ter um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="72c82-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="72c82-370">Código de formato de objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-370">Object Format Code</span></span>               | <span data-ttu-id="72c82-371">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-371">Description</span></span>   |     <span data-ttu-id="72c82-372">Código USBX</span><span class="sxs-lookup"><span data-stu-id="72c82-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="72c82-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="72c82-373">0x3000</span></span>                           | <span data-ttu-id="72c82-374">Objeto indefinido não-imagem indefinida</span><span class="sxs-lookup"><span data-stu-id="72c82-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="72c82-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="72c82-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="72c82-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="72c82-376">0x3001</span></span>                           | <span data-ttu-id="72c82-377">Associação associação (por exemplo, pasta)</span><span class="sxs-lookup"><span data-stu-id="72c82-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="72c82-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="72c82-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="72c82-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="72c82-379">0x3002</span></span>                           | <span data-ttu-id="72c82-380">Script device-modelo script específico script</span><span class="sxs-lookup"><span data-stu-id="72c82-380">Script Device-model specific script</span></span> | <span data-ttu-id="72c82-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="72c82-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="72c82-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="72c82-382">0x3003</span></span>                           | <span data-ttu-id="72c82-383">Executável dispositivo binário específico do modelo do dispositivo executável</span><span class="sxs-lookup"><span data-stu-id="72c82-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="72c82-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="72c82-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="72c82-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="72c82-385">0x3004</span></span>                           | <span data-ttu-id="72c82-386">Ficheiro de texto de texto</span><span class="sxs-lookup"><span data-stu-id="72c82-386">Text Text file</span></span>  |   <span data-ttu-id="72c82-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="72c82-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="72c82-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="72c82-388">0x3005</span></span>                           | <span data-ttu-id="72c82-389">HTML Ficheiro de Linguagem de Marcação HyperText (texto)</span><span class="sxs-lookup"><span data-stu-id="72c82-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="72c82-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="72c82-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="72c82-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="72c82-391">0x3006</span></span>                           | <span data-ttu-id="72c82-392">Ficheiro de formato de ordem de impressão digital DPOF (texto)</span><span class="sxs-lookup"><span data-stu-id="72c82-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="72c82-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="72c82-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="72c82-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="72c82-394">0x3007</span></span>                           | <span data-ttu-id="72c82-395">Clipe de áudio AIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="72c82-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="72c82-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="72c82-397">0x3008</span></span>                           | <span data-ttu-id="72c82-398">Clipe de áudio WAV</span><span class="sxs-lookup"><span data-stu-id="72c82-398">WAV Audio clip</span></span>   |  <span data-ttu-id="72c82-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="72c82-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="72c82-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="72c82-400">0x3009</span></span>                           | <span data-ttu-id="72c82-401">Clipe de áudio MP3</span><span class="sxs-lookup"><span data-stu-id="72c82-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="72c82-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="72c82-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="72c82-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="72c82-403">0x300A</span></span>                           | <span data-ttu-id="72c82-404">Clipe de vídeo DA AVI</span><span class="sxs-lookup"><span data-stu-id="72c82-404">AVI Video clip</span></span>   |  <span data-ttu-id="72c82-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="72c82-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="72c82-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="72c82-406">0x300B</span></span>                           | <span data-ttu-id="72c82-407">Clipe de vídeo MPEG</span><span class="sxs-lookup"><span data-stu-id="72c82-407">MPEG Video clip</span></span>  |  <span data-ttu-id="72c82-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="72c82-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="72c82-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="72c82-409">0x300C</span></span>                           | <span data-ttu-id="72c82-410">Formato avançado de streaming asf Microsoft (vídeo)</span><span class="sxs-lookup"><span data-stu-id="72c82-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="72c82-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="72c82-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="72c82-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="72c82-412">0x3800</span></span>                           | <span data-ttu-id="72c82-413">Objeto de imagem desconhecido indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-413">Undefined Unknown image object</span></span> | <span data-ttu-id="72c82-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="72c82-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="72c82-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="72c82-415">0x3801</span></span>                           | <span data-ttu-id="72c82-416">Formato de ficheiro permutável EXIF/JPEG, padrão JEIDA</span><span class="sxs-lookup"><span data-stu-id="72c82-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="72c82-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="72c82-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="72c82-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="72c82-418">0x3802</span></span>                           | <span data-ttu-id="72c82-419">TIFF/EP Tag Formato de ficheiro de imagem para fotografia eletrónica</span><span class="sxs-lookup"><span data-stu-id="72c82-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="72c82-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="72c82-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="72c82-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="72c82-421">0x3803</span></span>                           | <span data-ttu-id="72c82-422">Formato de imagem de armazenamento estruturado FlashPix</span><span class="sxs-lookup"><span data-stu-id="72c82-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="72c82-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="72c82-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="72c82-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="72c82-424">0x3804</span></span>                           | <span data-ttu-id="72c82-425">Ficheiro Bitmap BMP Microsoft Windows</span><span class="sxs-lookup"><span data-stu-id="72c82-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="72c82-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="72c82-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="72c82-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="72c82-427">0x3805</span></span>                           | <span data-ttu-id="72c82-428">Formato de ficheiro de imagem da câmera cânone CIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="72c82-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="72c82-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="72c82-430">0x3806</span></span>                           | <span data-ttu-id="72c82-431">Reservado indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="72c82-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="72c82-432">0x3807</span></span>                           | <span data-ttu-id="72c82-433">Formato de troca de gráficos GIF</span><span class="sxs-lookup"><span data-stu-id="72c82-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="72c82-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="72c82-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="72c82-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="72c82-435">0x3808</span></span>                           | <span data-ttu-id="72c82-436">Formato de troca de ficheiros JFIF JPEG</span><span class="sxs-lookup"><span data-stu-id="72c82-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="72c82-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="72c82-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="72c82-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="72c82-438">0x3809</span></span>                           | <span data-ttu-id="72c82-439">PCD PhotoCD Image Pac</span><span class="sxs-lookup"><span data-stu-id="72c82-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="72c82-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="72c82-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="72c82-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="72c82-441">0x380A</span></span>                           | <span data-ttu-id="72c82-442">Formato de imagem de quickdraw PICT</span><span class="sxs-lookup"><span data-stu-id="72c82-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="72c82-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="72c82-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="72c82-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="72c82-444">0x380B</span></span>                           | <span data-ttu-id="72c82-445">Gráficos de rede portáteis png</span><span class="sxs-lookup"><span data-stu-id="72c82-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="72c82-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="72c82-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="72c82-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="72c82-447">0x380C</span></span>                           | <span data-ttu-id="72c82-448">Reservado indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="72c82-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="72c82-449">0x380D</span></span>                           | <span data-ttu-id="72c82-450">Formato de ficheiro de imagem de marcação TIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="72c82-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="72c82-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="72c82-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="72c82-452">0x380E</span></span>                           | <span data-ttu-id="72c82-453">TIFF/IT Tag Formato de ficheiro de imagem para tecnologias de informação (artes gráficas)</span><span class="sxs-lookup"><span data-stu-id="72c82-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="72c82-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="72c82-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="72c82-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="72c82-455">0x380F</span></span>                           | <span data-ttu-id="72c82-456">JP2 JPEG2000 Formato de ficheiro de base</span><span class="sxs-lookup"><span data-stu-id="72c82-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="72c82-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="72c82-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="72c82-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="72c82-458">0x3810</span></span>                           | <span data-ttu-id="72c82-459">JPX JPEG2000 Formato de ficheiro estendido</span><span class="sxs-lookup"><span data-stu-id="72c82-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="72c82-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="72c82-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="72c82-461">Todos os outros códigos com MSN de 0011</span><span class="sxs-lookup"><span data-stu-id="72c82-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="72c82-462">Qualquer reservado indefinido para uso futuro</span><span class="sxs-lookup"><span data-stu-id="72c82-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="72c82-463">Todos os outros códigos com MSN de 1011</span><span class="sxs-lookup"><span data-stu-id="72c82-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="72c82-464">Qualquer tipo definido pelo fornecedor definido pelo fornecedor: Imagem</span><span class="sxs-lookup"><span data-stu-id="72c82-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="72c82-465">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-465">Return Value</span></span>

- <span data-ttu-id="72c82-466">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-468">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-469">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="72c82-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="72c82-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="72c82-471">Obtenha pegas de objeto do Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-472">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="72c82-473">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-473">Description</span></span>

<span data-ttu-id="72c82-474">Devolve uma matriz de pegas de objeto presentes no recipiente de armazenamento indicado pelo parâmetro storage_id.</span><span class="sxs-lookup"><span data-stu-id="72c82-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="72c82-475">Se for desejada uma lista agregada em todas as lojas, este valor será definido para 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="72c82-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-476">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-476">Parameters</span></span>

- <span data-ttu-id="72c82-477">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-478">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-479">**object_handes_array**: Array onde as pegas são devolvidas</span><span class="sxs-lookup"><span data-stu-id="72c82-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="72c82-480">**object_handles_length**: Comprimento da matriz</span><span class="sxs-lookup"><span data-stu-id="72c82-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="72c82-481">**storage_id**: Identificação do recipiente de armazenamento</span><span class="sxs-lookup"><span data-stu-id="72c82-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="72c82-482">**object_format_code:** Código de formato para objeto (ver tabela para função ux_host_class_pima_num_objects_get)</span><span class="sxs-lookup"><span data-stu-id="72c82-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="72c82-483">**object_handle_association**: Valor opcional da associação de objetos</span><span class="sxs-lookup"><span data-stu-id="72c82-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="72c82-484">A associação de pega de objeto pode ser um dos valores da tabela abaixo:</span><span class="sxs-lookup"><span data-stu-id="72c82-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="72c82-485">Código de Associação</span><span class="sxs-lookup"><span data-stu-id="72c82-485">AssociationCode</span></span>                        | <span data-ttu-id="72c82-486">Tipo de Associação</span><span class="sxs-lookup"><span data-stu-id="72c82-486">AssociationType</span></span>      | <span data-ttu-id="72c82-487">Interpretação</span><span class="sxs-lookup"><span data-stu-id="72c82-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="72c82-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="72c82-488">0x0000</span></span>                                 | <span data-ttu-id="72c82-489">Indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-489">Undefined</span></span>            | <span data-ttu-id="72c82-490">Indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-490">Undefined</span></span>            |
| <span data-ttu-id="72c82-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="72c82-491">0x0001</span></span>                                 | <span data-ttu-id="72c82-492">Genérico</span><span class="sxs-lookup"><span data-stu-id="72c82-492">GenericFolder</span></span>        | <span data-ttu-id="72c82-493">Não é bem-de-suso</span><span class="sxs-lookup"><span data-stu-id="72c82-493">Unused</span></span>               |
| <span data-ttu-id="72c82-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="72c82-494">0x0002</span></span>                                 | <span data-ttu-id="72c82-495">Álbum</span><span class="sxs-lookup"><span data-stu-id="72c82-495">Album</span></span>                | <span data-ttu-id="72c82-496">Reservado</span><span class="sxs-lookup"><span data-stu-id="72c82-496">Reserved</span></span>             |
| <span data-ttu-id="72c82-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="72c82-497">0x0003</span></span>                                 | <span data-ttu-id="72c82-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="72c82-498">TimeSequence</span></span>         | <span data-ttu-id="72c82-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="72c82-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="72c82-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="72c82-500">0x0004</span></span>                                 | <span data-ttu-id="72c82-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="72c82-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="72c82-502">Não é bem-de-suso</span><span class="sxs-lookup"><span data-stu-id="72c82-502">Unused</span></span>               |
| <span data-ttu-id="72c82-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="72c82-503">0x0005</span></span>                                 | <span data-ttu-id="72c82-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="72c82-504">VerticalPanoramic</span></span>    | <span data-ttu-id="72c82-505">Não é bem-de-suso</span><span class="sxs-lookup"><span data-stu-id="72c82-505">Unused</span></span>               |
| <span data-ttu-id="72c82-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="72c82-506">0x0006</span></span>                                 | <span data-ttu-id="72c82-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="72c82-507">2DPanoramic</span></span>          | <span data-ttu-id="72c82-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="72c82-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="72c82-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="72c82-509">0x0007</span></span>                                 | <span data-ttu-id="72c82-510">Data Auxiliar</span><span class="sxs-lookup"><span data-stu-id="72c82-510">AncillaryData</span></span>        | <span data-ttu-id="72c82-511">Indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-511">Undefined</span></span>            |
| <span data-ttu-id="72c82-512">Todos os outros valores com bit 15 definido para 0</span><span class="sxs-lookup"><span data-stu-id="72c82-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="72c82-513">Reservado</span><span class="sxs-lookup"><span data-stu-id="72c82-513">Reserved</span></span>             | <span data-ttu-id="72c82-514">Indefinido</span><span class="sxs-lookup"><span data-stu-id="72c82-514">Undefined</span></span>            |
| <span data-ttu-id="72c82-515">Todos os valores com bit 15 definido para 1</span><span class="sxs-lookup"><span data-stu-id="72c82-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="72c82-516">Definido pelo fornecedor</span><span class="sxs-lookup"><span data-stu-id="72c82-516">Vendor-Defined</span></span>       | <span data-ttu-id="72c82-517">Definido pelo fornecedor</span><span class="sxs-lookup"><span data-stu-id="72c82-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="72c82-518">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-518">Return Value</span></span>

- <span data-ttu-id="72c82-519">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-521">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-522">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="72c82-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="72c82-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="72c82-524">Obtenha a informação do objeto do Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-525">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="72c82-526">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-526">Description</span></span>

<span data-ttu-id="72c82-527">Esta função obtém a informação do objeto para uma pega de objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-528">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-528">Parameters</span></span>

- <span data-ttu-id="72c82-529">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-530">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-531">**object_handle**: Cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="72c82-532">**objeto**: Ponteiro para objeto de informação</span><span class="sxs-lookup"><span data-stu-id="72c82-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-533">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-533">Return Value</span></span>

- <span data-ttu-id="72c82-534">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-536">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-537">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="72c82-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="72c82-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="72c82-539">Envie a informação do objeto para o Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="72c82-541">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-541">Description</span></span>

<span data-ttu-id="72c82-542">Esta função envia as informações de armazenamento para um recipiente de armazenamento de valor storage_id.</span><span class="sxs-lookup"><span data-stu-id="72c82-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="72c82-543">O Iniciador deve utilizar este comando antes de enviar um objeto ao socorrista.</span><span class="sxs-lookup"><span data-stu-id="72c82-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-544">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-544">Parameters</span></span>

- <span data-ttu-id="72c82-545">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-546">**pima_session**: Pointer to PIMA session.</span><span class="sxs-lookup"><span data-stu-id="72c82-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="72c82-547">**storage_id**: ID de armazenamento de destino.</span><span class="sxs-lookup"><span data-stu-id="72c82-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="72c82-548">**parent_object_id**: Parent ObjectHandle on Responder onde o objeto deve ser colocado.</span><span class="sxs-lookup"><span data-stu-id="72c82-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="72c82-549">**objeto**: Ponteiro para objeto de informação.</span><span class="sxs-lookup"><span data-stu-id="72c82-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-550">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-550">Return Value</span></span>

- <span data-ttu-id="72c82-551">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-553">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-554">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="72c82-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="72c82-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="72c82-556">Abra um objeto armazenado no Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-557">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="72c82-558">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-558">Description</span></span>

<span data-ttu-id="72c82-559">Esta função abre um objeto no respondente antes de ler ou escrever.</span><span class="sxs-lookup"><span data-stu-id="72c82-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-560">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-560">Parameters</span></span>

- <span data-ttu-id="72c82-561">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-562">**pima_session**: Pointer to PIMA session.</span><span class="sxs-lookup"><span data-stu-id="72c82-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="72c82-563">**object_handle:** manuseie o objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="72c82-564">Objec : **Ponteiros** de objeção ao recipiente de informações.</span><span class="sxs-lookup"><span data-stu-id="72c82-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-565">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-565">Return Value</span></span>

- <span data-ttu-id="72c82-566">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Objeto já aberto.</span><span class="sxs-lookup"><span data-stu-id="72c82-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="72c82-569">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-570">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="72c82-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="72c82-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="72c82-572">Guarde um objeto no Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-573">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-574">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-574">Description</span></span>

<span data-ttu-id="72c82-575">Esta função recebe um objeto no respondente.</span><span class="sxs-lookup"><span data-stu-id="72c82-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-576">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-576">Parameters</span></span>

- <span data-ttu-id="72c82-577">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-578">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-579">**object_handle:** cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="72c82-580">**objeto**: Ponteiro para objeto de informação</span><span class="sxs-lookup"><span data-stu-id="72c82-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="72c82-581">**object_buffer**: Endereço de dados de objetos</span><span class="sxs-lookup"><span data-stu-id="72c82-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="72c82-582">**object_buffer_length**: Comprimento solicitado do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="72c82-583">**object_atual_length**: Comprimento do objeto devolvido</span><span class="sxs-lookup"><span data-stu-id="72c82-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-584">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-584">Return Value</span></span>

- <span data-ttu-id="72c82-585">**UX_SUCCESS:**(0x00) O objeto foi transferido</span><span class="sxs-lookup"><span data-stu-id="72c82-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="72c82-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.</span><span class="sxs-lookup"><span data-stu-id="72c82-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="72c82-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso a objeto negado</span><span class="sxs-lookup"><span data-stu-id="72c82-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="72c82-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta</span><span class="sxs-lookup"><span data-stu-id="72c82-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="72c82-590">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="72c82-591">**UX_TRANSFER_ERROR**: (0x23) Erro de transferência ao ler objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="72c82-592">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="72c82-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="72c82-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="72c82-594">Envie um objeto armazenado no Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="72c82-596">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-596">Description</span></span>

<span data-ttu-id="72c82-597">Esta função envia um objeto para o socorrista.</span><span class="sxs-lookup"><span data-stu-id="72c82-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-598">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-598">Parameters</span></span>

- <span data-ttu-id="72c82-599">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-600">**pima_sessio**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-601">**object_handle:** cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="72c82-602">**objeto**: Ponteiro para objeto de informação</span><span class="sxs-lookup"><span data-stu-id="72c82-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="72c82-603">**object_buffer**: Endereço de dados de objetos</span><span class="sxs-lookup"><span data-stu-id="72c82-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="72c82-604">**object_buffer_length**: Comprimento solicitado do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-605">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-605">Return Value</span></span>

- <span data-ttu-id="72c82-606">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta</span><span class="sxs-lookup"><span data-stu-id="72c82-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="72c82-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.</span><span class="sxs-lookup"><span data-stu-id="72c82-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="72c82-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso a objeto negado</span><span class="sxs-lookup"><span data-stu-id="72c82-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="72c82-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta</span><span class="sxs-lookup"><span data-stu-id="72c82-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="72c82-611">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="72c82-612">**UX_TRANSFER_ERROR**: (0x23) Erro de transferência ao escrever objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="72c82-613">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="72c82-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="72c82-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="72c82-615">Guarde um objeto de polegar no Responder.</span><span class="sxs-lookup"><span data-stu-id="72c82-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-616">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-617">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-617">Description</span></span>

<span data-ttu-id="72c82-618">Esta função recebe um objeto de polegar no socorrista.</span><span class="sxs-lookup"><span data-stu-id="72c82-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-619">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-619">Parameters</span></span>

- <span data-ttu-id="72c82-620">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-621">**pima_session**: Pointer to PIMA session.</span><span class="sxs-lookup"><span data-stu-id="72c82-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="72c82-622">**object_handle:** manuseie o objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="72c82-623">**objeto**: Ponteiro para objeto de informação.</span><span class="sxs-lookup"><span data-stu-id="72c82-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="72c82-624">**thumb_buffer**: Endereço dos dados dos objetos de polegar.</span><span class="sxs-lookup"><span data-stu-id="72c82-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="72c82-625">**thumb_buffer_length:** Comprimento solicitado do objeto do polegar.</span><span class="sxs-lookup"><span data-stu-id="72c82-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="72c82-626">**thumb_atual_length:** Comprimento do objeto do polegar devolvido.</span><span class="sxs-lookup"><span data-stu-id="72c82-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-627">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-627">Return Value</span></span>

- <span data-ttu-id="72c82-628">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.</span><span class="sxs-lookup"><span data-stu-id="72c82-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="72c82-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.</span><span class="sxs-lookup"><span data-stu-id="72c82-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="72c82-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Acesso ao objeto negado.</span><span class="sxs-lookup"><span data-stu-id="72c82-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="72c82-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) A transferência está incompleta.</span><span class="sxs-lookup"><span data-stu-id="72c82-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="72c82-633">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="72c82-634">**UX_TRANSFER_ERROR**: (0x23) Erro de transferência durante a leitura do objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-635">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="72c82-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="72c82-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="72c82-637">Elimine um objeto armazenado no Respondente.</span><span class="sxs-lookup"><span data-stu-id="72c82-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-638">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="72c82-639">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-639">Description</span></span>

<span data-ttu-id="72c82-640">Esta função elimina um objeto no respondente</span><span class="sxs-lookup"><span data-stu-id="72c82-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-641">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-641">Parameters</span></span>

- <span data-ttu-id="72c82-642">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-643">**pima_session**: Sessão de Ponte para PIMA</span><span class="sxs-lookup"><span data-stu-id="72c82-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="72c82-644">**object_handle:** cabo do objeto</span><span class="sxs-lookup"><span data-stu-id="72c82-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-645">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-645">Return Value</span></span>

- <span data-ttu-id="72c82-646">**UX_SUCCESS**: (0x00) O objeto foi apagado.</span><span class="sxs-lookup"><span data-stu-id="72c82-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="72c82-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.</span><span class="sxs-lookup"><span data-stu-id="72c82-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="72c82-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Não pode eliminar objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="72c82-649">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-650">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="72c82-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="72c82-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="72c82-652">Feche um objeto armazenado no Responder</span><span class="sxs-lookup"><span data-stu-id="72c82-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="72c82-654">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-654">Description</span></span>

<span data-ttu-id="72c82-655">Esta função fecha um objeto no respondente.</span><span class="sxs-lookup"><span data-stu-id="72c82-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-656">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-656">Parameters</span></span>

- <span data-ttu-id="72c82-657">**pima**: Ponteiro para a instância da classe pima.</span><span class="sxs-lookup"><span data-stu-id="72c82-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="72c82-658">**pima_session**: Pointer to PIMA session.</span><span class="sxs-lookup"><span data-stu-id="72c82-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="72c82-659">**object_handle:** Manuseie o objeto.</span><span class="sxs-lookup"><span data-stu-id="72c82-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="72c82-660">**objeto**: Ponteiro para opor.</span><span class="sxs-lookup"><span data-stu-id="72c82-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-661">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-661">Return Value</span></span>

- <span data-ttu-id="72c82-662">**UX_SUCCESS:**(0x00) O objeto foi fechado.</span><span class="sxs-lookup"><span data-stu-id="72c82-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="72c82-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Sessão não aberta.</span><span class="sxs-lookup"><span data-stu-id="72c82-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="72c82-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Objeto não aberto.</span><span class="sxs-lookup"><span data-stu-id="72c82-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="72c82-665">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente para criar o comando PIMA.</span><span class="sxs-lookup"><span data-stu-id="72c82-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-666">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="72c82-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="72c82-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="72c82-668">Leia a partir da interface de série genérica.</span><span class="sxs-lookup"><span data-stu-id="72c82-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-669">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-670">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-670">Description</span></span>

<span data-ttu-id="72c82-671">Esta função lê-se a partir da interface de série genérica.</span><span class="sxs-lookup"><span data-stu-id="72c82-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="72c82-672">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="72c82-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-673">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-673">Parameters</span></span>

- <span data-ttu-id="72c82-674">**gser**: Ponteiro para a instância da classe gser.</span><span class="sxs-lookup"><span data-stu-id="72c82-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="72c82-675">**interface_index**: Índice de interface para ler.</span><span class="sxs-lookup"><span data-stu-id="72c82-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="72c82-676">**data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="72c82-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="72c82-677">**requested_length:** Comprimento a receber.</span><span class="sxs-lookup"><span data-stu-id="72c82-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="72c82-678">**atual_length:** Comprimento realmente recebido.</span><span class="sxs-lookup"><span data-stu-id="72c82-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-679">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-679">Return Value</span></span>

- <span data-ttu-id="72c82-680">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo, leitura incompleta.</span><span class="sxs-lookup"><span data-stu-id="72c82-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-682">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="72c82-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="72c82-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="72c82-684">Escreva para a interface de série genérica.</span><span class="sxs-lookup"><span data-stu-id="72c82-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-685">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="72c82-686">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-686">Description</span></span>

<span data-ttu-id="72c82-687">Esta função escreve para a interface de série genérica.</span><span class="sxs-lookup"><span data-stu-id="72c82-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="72c82-688">A chamada está a bloquear e só regressa quando há um erro ou quando a transferência está completa.</span><span class="sxs-lookup"><span data-stu-id="72c82-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-689">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-689">Parameters</span></span>

- <span data-ttu-id="72c82-690">**gser**: Ponteiro para a instância da classe gser.</span><span class="sxs-lookup"><span data-stu-id="72c82-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="72c82-691">**interface_index**: Interface para a qual escrever.</span><span class="sxs-lookup"><span data-stu-id="72c82-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="72c82-692">**data_pointer**: Ponteiro para o endereço-tampão da carga útil dos dados.</span><span class="sxs-lookup"><span data-stu-id="72c82-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="72c82-693">**requested_length:** Comprimento a enviar.</span><span class="sxs-lookup"><span data-stu-id="72c82-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="72c82-694">**atual_length:** Comprimento realmente enviado.</span><span class="sxs-lookup"><span data-stu-id="72c82-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-695">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-695">Return Value</span></span>

- <span data-ttu-id="72c82-696">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transferir tempo limite, escrever incompleto.</span><span class="sxs-lookup"><span data-stu-id="72c82-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="72c82-698">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="72c82-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="72c82-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="72c82-700">Execute uma função IOCTL para a interface de série genérica.</span><span class="sxs-lookup"><span data-stu-id="72c82-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-701">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="72c82-702">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-702">Description</span></span>

<span data-ttu-id="72c82-703">Esta função desempenha uma função de coitl específica para a interface gser.</span><span class="sxs-lookup"><span data-stu-id="72c82-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="72c82-704">A chamada está a bloquear e só retorna quando há um erro ou quando o comando está concluído.</span><span class="sxs-lookup"><span data-stu-id="72c82-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-705">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-705">Parameters</span></span>

- <span data-ttu-id="72c82-706">**gser**: Ponteiro para a instância da classe gser.</span><span class="sxs-lookup"><span data-stu-id="72c82-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="72c82-707">**ioctl_function:** função de ioctl a desempenhar.</span><span class="sxs-lookup"><span data-stu-id="72c82-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="72c82-708">Consulte a tabela abaixo para uma das funções de coitl permitidas.</span><span class="sxs-lookup"><span data-stu-id="72c82-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="72c82-709">**parâmetro**: Pointer to a parameter specific to the ioctl</span><span class="sxs-lookup"><span data-stu-id="72c82-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-710">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-710">Return Value</span></span>

- <span data-ttu-id="72c82-711">**UX_SUCCESS**: (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-712">**UX_MEMORY_INSUFFICIENT:**(0x12) Não há memória suficiente.</span><span class="sxs-lookup"><span data-stu-id="72c82-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="72c82-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Instância de classe errada</span><span class="sxs-lookup"><span data-stu-id="72c82-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="72c82-714">**UX_FUNCTION_NOT_SUPPORTED:**(0x54) Função IOCTL desconhecida.</span><span class="sxs-lookup"><span data-stu-id="72c82-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="72c82-715">Funções ioctl</span><span class="sxs-lookup"><span data-stu-id="72c82-715">IOCTL functions</span></span>

- <span data-ttu-id="72c82-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="72c82-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="72c82-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="72c82-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="72c82-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="72c82-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="72c82-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="72c82-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="72c82-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="72c82-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="72c82-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="72c82-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="72c82-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="72c82-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="72c82-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="72c82-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="72c82-724">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="72c82-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="72c82-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="72c82-726">Inicie a receção na interface de série genérica</span><span class="sxs-lookup"><span data-stu-id="72c82-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-727">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="72c82-728">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-728">Description</span></span>

<span data-ttu-id="72c82-729">Esta função inicia a receção na interface genérica de classe em série.</span><span class="sxs-lookup"><span data-stu-id="72c82-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="72c82-730">Esta função permite a receção não bloqueada.</span><span class="sxs-lookup"><span data-stu-id="72c82-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="72c82-731">Quando um tampão é recebido, uma chamada de volta invocada para o pedido.</span><span class="sxs-lookup"><span data-stu-id="72c82-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-732">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-732">Parameters</span></span>

- <span data-ttu-id="72c82-733">**gser** Ponteiro para a instância da classe GSER.</span><span class="sxs-lookup"><span data-stu-id="72c82-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="72c82-734">**gser_reception** Estrutura que contém os parâmetros de receção</span><span class="sxs-lookup"><span data-stu-id="72c82-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-735">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-735">Return Value</span></span>

- <span data-ttu-id="72c82-736">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Instância de classe errada</span><span class="sxs-lookup"><span data-stu-id="72c82-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="72c82-738">**Erro UX_ERROR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="72c82-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="72c82-739">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="72c82-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="72c82-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="72c82-741">Parar a receção na interface de série genérica</span><span class="sxs-lookup"><span data-stu-id="72c82-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="72c82-742">Prototype</span><span class="sxs-lookup"><span data-stu-id="72c82-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="72c82-743">Descrição</span><span class="sxs-lookup"><span data-stu-id="72c82-743">Description</span></span>

<span data-ttu-id="72c82-744">Esta função impede a receção na interface genérica de classe em série.</span><span class="sxs-lookup"><span data-stu-id="72c82-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="72c82-745">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72c82-745">Parameters</span></span>

- <span data-ttu-id="72c82-746">**gser** Ponteiro para a instância da classe GSER.</span><span class="sxs-lookup"><span data-stu-id="72c82-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="72c82-747">**gser_reception** Estrutura que contém os parâmetros de receção</span><span class="sxs-lookup"><span data-stu-id="72c82-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="72c82-748">Devolver Valor</span><span class="sxs-lookup"><span data-stu-id="72c82-748">Return Value</span></span>

- <span data-ttu-id="72c82-749">**UX_SUCCESS** (0x00) A transferência de dados foi concluída.</span><span class="sxs-lookup"><span data-stu-id="72c82-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="72c82-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Instância de classe errada</span><span class="sxs-lookup"><span data-stu-id="72c82-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="72c82-751">**Erro UX_ERROR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="72c82-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="72c82-752">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72c82-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
