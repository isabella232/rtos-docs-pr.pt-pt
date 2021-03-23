---
title: Capítulo 4- Descrição dos serviços Azure RTOS FileX
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS FileX por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826545"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="30951-103">Capítulo 4- Descrição dos serviços Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="30951-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="30951-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS FileX por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="30951-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="30951-105">Os nomes de serviço são projetados para que todos os serviços similares sejam agrupados.</span><span class="sxs-lookup"><span data-stu-id="30951-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="30951-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="30951-107">Lê atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="30951-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="30951-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-109">Description</span></span>

<span data-ttu-id="30951-110">Este serviço lê os atributos do diretório a partir dos meios de comunicação especificados.</span><span class="sxs-lookup"><span data-stu-id="30951-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-111">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-111">Input Parameters</span></span>

- <span data-ttu-id="30951-112">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-113">**directory_name**: Ponteiro para o nome do diretório solicitado (o percurso do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="30951-114">**atributos** _ptr: Ponteiro para o destino para os atributos do diretório a serem colocados.</span><span class="sxs-lookup"><span data-stu-id="30951-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="30951-115">Os atributos do diretório são devolvidos num formato de mapa bit com as seguintes definições possíveis:</span><span class="sxs-lookup"><span data-stu-id="30951-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="30951-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="30951-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="30951-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="30951-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="30951-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="30951-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="30951-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="30951-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-122">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-122">Return Values</span></span>

- <span data-ttu-id="30951-123">**FX_SUCCESS** (0x00) Atributos de diretório de sucesso lidos</span><span class="sxs-lookup"><span data-stu-id="30951-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="30951-124">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-125">**FX _NOT FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="30951-126">**FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório</span><span class="sxs-lookup"><span data-stu-id="30951-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="30951-127">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-128">**FX_FILE_CORRUPT** 0x08) Arquivo é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-129">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-130">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-131">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-132">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-133">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="30951-134">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-135">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-135">Allowed From</span></span>

<span data-ttu-id="30951-136">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="30951-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-138">See Also</span></span>

- <span data-ttu-id="30951-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-140">fx_directory_create</span></span>
- <span data-ttu-id="30951-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-141">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-142">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-143">fx_directory_delete</span></span>
- <span data-ttu-id="30951-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-146">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-152">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-155">fx_directory_rename</span></span>
- <span data-ttu-id="30951-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="30951-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="30951-160">Define atributos de diretório</span><span class="sxs-lookup"><span data-stu-id="30951-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="30951-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-162">Description</span></span>

<span data-ttu-id="30951-163">Este serviço define os atributos do diretório aos especificados pelo autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="30951-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-164">*Esta aplicação só é permitida para modificar um subconjunto dos atributos do diretório com este serviço. Qualquer tentativa de definir atributos adicionais resultará num erro.*</span><span class="sxs-lookup"><span data-stu-id="30951-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-165">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-165">Input Parameters</span></span>

- <span data-ttu-id="30951-166">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-167">**directory_name**: Ponteiro para o nome do diretório solicitado (o percurso do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="30951-168">**atributos**: Os novos atributos a este diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="30951-169">Os atributos de diretório válidos são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="30951-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="30951-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="30951-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="30951-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="30951-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-174">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-174">Return Values</span></span>

- <span data-ttu-id="30951-175">**FX_SUCCESS** (0x00) Conjunto de atributos de sucesso</span><span class="sxs-lookup"><span data-stu-id="30951-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="30951-176">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-177">**FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="30951-178">**FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório</span><span class="sxs-lookup"><span data-stu-id="30951-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="30951-179">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-180">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito</span><span class="sxs-lookup"><span data-stu-id="30951-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="30951-181">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-182">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-183">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-184">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-185">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-186">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório</span><span class="sxs-lookup"><span data-stu-id="30951-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="30951-187">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="30951-188">**FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.</span><span class="sxs-lookup"><span data-stu-id="30951-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="30951-189">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-190">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-190">Allowed From</span></span>

<span data-ttu-id="30951-191">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="30951-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-193">See Also</span></span>

- <span data-ttu-id="30951-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-195">fx_directory_create</span></span>
- <span data-ttu-id="30951-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-196">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-197">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-198">fx_directory_delete</span></span>
- <span data-ttu-id="30951-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-201">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-207">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-210">fx_directory_rename</span></span>
- <span data-ttu-id="30951-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="30951-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-214">fx_directory_create</span></span>

<span data-ttu-id="30951-215">Cria subdireção</span><span class="sxs-lookup"><span data-stu-id="30951-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="30951-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-217">Description</span></span>

<span data-ttu-id="30951-218">Este serviço cria uma subdiretório no diretório predefinido atual ou no caminho fornecido no nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="30951-219">Ao contrário do diretório de raiz, as subdiretórios não têm um limite para o número de ficheiros que podem reter.</span><span class="sxs-lookup"><span data-stu-id="30951-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="30951-220">O diretório de raiz só pode conter o número de entradas determinadas pelo registo de arranque.</span><span class="sxs-lookup"><span data-stu-id="30951-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-221">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-221">Input Parameters</span></span>

- <span data-ttu-id="30951-222">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-223">**directory_name**: Pontear o nome do diretório para criar (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-224">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-224">Return Values</span></span>

- <span data-ttu-id="30951-225">**FX_SUCCESS** (0x00) Diretório de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="30951-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="30951-226">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-227">**FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="30951-228">**FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório</span><span class="sxs-lookup"><span data-stu-id="30951-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="30951-229">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-230">**FX_FILE _CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-231">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-232">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-233">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-234">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-235">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório</span><span class="sxs-lookup"><span data-stu-id="30951-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="30951-236">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="30951-237">**FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.</span><span class="sxs-lookup"><span data-stu-id="30951-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="30951-238">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-239">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-239">Allowed From</span></span>

<span data-ttu-id="30951-240">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-241">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="30951-242">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-242">See Also</span></span>

- <span data-ttu-id="30951-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-245">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-246">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-247">fx_directory_delete</span></span>
- <span data-ttu-id="30951-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-250">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-256">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-259">fx_directory_rename</span></span>
- <span data-ttu-id="30951-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="30951-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-263">fx_directory_default_get</span></span>

<span data-ttu-id="30951-264">Obtém o último diretório predefinido</span><span class="sxs-lookup"><span data-stu-id="30951-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-265">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="30951-266">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-266">Description</span></span>

<span data-ttu-id="30951-267">Este serviço devolve o ponteiro ao caminho definido pela ***última vez por fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="30951-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="30951-268">Se o diretório predefinido não tiver sido definido ou se o diretório predefinido atual for o diretório de raiz, é devolvido um valor de FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="30951-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-269">*O tamanho padrão da cadeia de caminho interno é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-270">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-270">Input Parameters</span></span>

- <span data-ttu-id="30951-271">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-272">**return_path_name**: Pontear o destino para a última cadeia de diretório predefinido.</span><span class="sxs-lookup"><span data-stu-id="30951-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="30951-273">Um valor de FX_NULL é devolvido se a configuração atual do diretório predefinido for a raiz.</span><span class="sxs-lookup"><span data-stu-id="30951-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="30951-274">Quando o meio de comunicação é aberto, a raiz é o padrão.</span><span class="sxs-lookup"><span data-stu-id="30951-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-275">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-275">Return Values</span></span>

- <span data-ttu-id="30951-276">**FX_SUCCESS** (0x00) Diretório padrão de sucesso obter</span><span class="sxs-lookup"><span data-stu-id="30951-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="30951-277">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-278">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="30951-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="30951-279">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-280">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-280">Allowed From</span></span>

<span data-ttu-id="30951-281">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-282">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="30951-283">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-283">See Also</span></span>

- <span data-ttu-id="30951-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-286">fx_directory_create</span></span>
- <span data-ttu-id="30951-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-287">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-288">fx_directory_delete</span></span>
- <span data-ttu-id="30951-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-291">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-297">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-300">fx_directory_rename</span></span>
- <span data-ttu-id="30951-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="30951-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-304">fx_directory_default_set</span></span>

<span data-ttu-id="30951-305">Define diretório predefinido</span><span class="sxs-lookup"><span data-stu-id="30951-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="30951-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-307">Description</span></span>

<span data-ttu-id="30951-308">Este serviço define o diretório predefinido dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="30951-309">Se for fornecido um valor de FX_NULL, o diretório predefinido é definido para o diretório de raiz dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="30951-310">Todas as operações de ficheiro subsequentes que não especificam explicitamente um caminho por defeito a este diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-311">*O tamanho padrão da cadeia de caminho interno é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-312">*Para os nomes fornecidos pela aplicação, o FileX suporta caracteres backslash \\ (/ ) e barras para a frente (/) para diretórios separados, subdiretórios e nomes de ficheiros. No entanto, o FileX utiliza apenas o carácter backslash nos caminhos devolvidos à aplicação.*</span><span class="sxs-lookup"><span data-stu-id="30951-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-313">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-313">Input Parameters</span></span>

- <span data-ttu-id="30951-314">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-315">**new_path_name**: Ponteiro para novo nome de diretório predefinido.</span><span class="sxs-lookup"><span data-stu-id="30951-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="30951-316">Se for fornecido um valor de FX_NULL, o diretório predefinido dos meios de comunicação é definido para o diretório de raiz dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-317">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-317">Return Values</span></span>

- <span data-ttu-id="30951-318">**FX_SUCCESS** (0x00) Conjunto de diretório padrão de sucesso</span><span class="sxs-lookup"><span data-stu-id="30951-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="30951-319">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-320">**FX_INVALID_PATH** (0x0D) Novo diretório não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="30951-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="30951-321">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-322">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-323">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-323">Allowed From</span></span>

<span data-ttu-id="30951-324">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-325">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="30951-326">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-326">See Also</span></span>

- <span data-ttu-id="30951-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-329">fx_directory_create</span></span>
- <span data-ttu-id="30951-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-330">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-331">fx_directory_delete</span></span>
- <span data-ttu-id="30951-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-334">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-340">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-343">fx_directory_rename</span></span>
- <span data-ttu-id="30951-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="30951-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-347">fx_directory_delete</span></span>

<span data-ttu-id="30951-348">Elimina subdireção</span><span class="sxs-lookup"><span data-stu-id="30951-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-349">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="30951-350">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-350">Description</span></span>

<span data-ttu-id="30951-351">Este serviço elimina o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-351">This service deletes the specified directory.</span></span> <span data-ttu-id="30951-352">Note que o diretório deve estar vazio para eliminá-lo.</span><span class="sxs-lookup"><span data-stu-id="30951-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-353">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-353">Input Parameters</span></span>

- <span data-ttu-id="30951-354">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-355">**directory_name**: Ponteiro para o nome do diretório para apagar (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-356">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-356">Return Values</span></span>

- <span data-ttu-id="30951-357">**FX_SUCCESS** (0x00) Diretório de sucesso</span><span class="sxs-lookup"><span data-stu-id="30951-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="30951-358">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-359">**FX_NOT_FOUND** (0x04) Não foi encontrado diretório especificado</span><span class="sxs-lookup"><span data-stu-id="30951-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="30951-360">**FX_DIR_NOT_EMPTY** (0x10) Diretório especificado não está vazio</span><span class="sxs-lookup"><span data-stu-id="30951-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="30951-361">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-362">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito</span><span class="sxs-lookup"><span data-stu-id="30951-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="30951-363">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-364">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-365">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-366">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-367">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-368">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório</span><span class="sxs-lookup"><span data-stu-id="30951-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="30951-369">**FX_NOT_DIRECTORY** (0x0E) Não uma entrada de diretório</span><span class="sxs-lookup"><span data-stu-id="30951-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="30951-370">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="30951-371">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-372">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-372">Allowed From</span></span>

<span data-ttu-id="30951-373">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-374">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="30951-375">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-375">See Also</span></span>

- <span data-ttu-id="30951-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-378">fx_directory_create</span></span>
- <span data-ttu-id="30951-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-379">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-380">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-383">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-389">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-392">fx_directory_rename</span></span>
- <span data-ttu-id="30951-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="30951-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="30951-397">Obtém a primeira entrada no diretório</span><span class="sxs-lookup"><span data-stu-id="30951-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-398">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="30951-399">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-399">Description</span></span>

<span data-ttu-id="30951-400">Este serviço recupera o primeiro nome de entrada no diretório predefinido e copia-o para o destino especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-401">*O destino especificado deve ser grande o suficiente para conter o nome FileX de tamanho máximo, tal como definido por **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="30951-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="30951-402">*Se utilizar um caminho não local, é importante evitar (com um semáforo ThreadX, mutex ou mudança de nível prioritário) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-403">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-403">Input Parameters</span></span>

- <span data-ttu-id="30951-404">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-405">**return_entry_name**: Ponteiro para o destino para o primeiro nome de entrada no diretório predefinido.</span><span class="sxs-lookup"><span data-stu-id="30951-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-406">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-406">Return Values</span></span>

- <span data-ttu-id="30951-407">**FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida</span><span class="sxs-lookup"><span data-stu-id="30951-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="30951-408">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-409">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório</span><span class="sxs-lookup"><span data-stu-id="30951-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="30951-410">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-411">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-412">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-413">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-414">**FX_PTR_ERROR** (0x18) Meios inválidos ou ponteiro de destino</span><span class="sxs-lookup"><span data-stu-id="30951-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="30951-415">**FX_CALLER_ERROR** (0x20) Caller não é um fio</span><span class="sxs-lookup"><span data-stu-id="30951-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-416">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-416">Allowed From</span></span>

<span data-ttu-id="30951-417">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-418">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="30951-419">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-419">See Also</span></span>

- <span data-ttu-id="30951-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-422">fx_directory_create</span></span>
- <span data-ttu-id="30951-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-423">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-424">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-425">fx_directory_delete</span></span>
- <span data-ttu-id="30951-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-427">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-433">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-436">fx_directory_rename</span></span>
- <span data-ttu-id="30951-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="30951-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="30951-441">Obtém a primeira entrada no diretório com informação completa</span><span class="sxs-lookup"><span data-stu-id="30951-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-442">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="30951-443">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-443">Input Parameters</span></span>

- <span data-ttu-id="30951-444">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-445">**directory_name**: Ponte para o destino para o nome de uma entrada de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="30951-446">Deve ser pelo menos tão grande quanto FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="30951-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="30951-447">**atributos**: Se não for nulo, ponteiro para o destino para os atributos da entrada a colocar.</span><span class="sxs-lookup"><span data-stu-id="30951-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="30951-448">Os atributos são devolvidos num formato de mapa bit com as seguintes definições possíveis:</span><span class="sxs-lookup"><span data-stu-id="30951-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="30951-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="30951-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="30951-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="30951-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="30951-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="30951-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="30951-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="30951-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="30951-455">**tamanho**: Se não foruso, ponteiro para o destino para o tamanho da entrada em bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="30951-456">**ano**: Se não for nulo, pontia o destino para o ano de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="30951-457">**mês**: Se não for nulo, ponteiu o destino para o mês de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="30951-458">**dia**: Se não for nulo, ponteiu o destino para o dia de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="30951-459">**hora**: Se não for nulo, ponteiu o destino para a hora de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="30951-460">**minuto**: Se não for nulo, ponteiu o destino para o minuto de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="30951-461">**segundo**: Se não for nulo, ponteiu o destino para a segunda modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-462">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-462">Return Values</span></span>

- <span data-ttu-id="30951-463">**FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida</span><span class="sxs-lookup"><span data-stu-id="30951-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="30951-464">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-465">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas neste diretório</span><span class="sxs-lookup"><span data-stu-id="30951-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="30951-466">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-467">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito</span><span class="sxs-lookup"><span data-stu-id="30951-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="30951-468">**FX_FILE _CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-469">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-470">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-471">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-472">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-473">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="30951-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="30951-474">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-475">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-475">Allowed From</span></span>

<span data-ttu-id="30951-476">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-477">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="30951-478">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-478">See Also</span></span>

- <span data-ttu-id="30951-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-481">fx_directory_create</span></span>
- <span data-ttu-id="30951-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-482">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-483">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-484">fx_directory_delete</span></span>
- <span data-ttu-id="30951-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-486">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-492">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-495">fx_directory_rename</span></span>
- <span data-ttu-id="30951-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="30951-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="30951-499">fx_directory_information_get:</span></span>

<span data-ttu-id="30951-500">Obtém informações de entrada de diretórios</span><span class="sxs-lookup"><span data-stu-id="30951-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-501">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="30951-502">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-502">Input Parameters</span></span>

- <span data-ttu-id="30951-503">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-504">**directory_name**: Ponteiro para o nome da entrada do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="30951-505">**atributos**: Ponteiro para o destino para os atributos.</span><span class="sxs-lookup"><span data-stu-id="30951-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="30951-506">**tamanho**: Ponteiro para o destino para o tamanho.</span><span class="sxs-lookup"><span data-stu-id="30951-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="30951-507">**ano**: Ponteiro para o destino do ano.</span><span class="sxs-lookup"><span data-stu-id="30951-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="30951-508">**mês**: Ponteiro para o destino do mês.</span><span class="sxs-lookup"><span data-stu-id="30951-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="30951-509">**dia**: Ponteiro para o destino do dia.</span><span class="sxs-lookup"><span data-stu-id="30951-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="30951-510">**hora**: Ponteiro para o destino durante a hora.</span><span class="sxs-lookup"><span data-stu-id="30951-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="30951-511">**minuto**: Ponteiro para o destino por um minuto.</span><span class="sxs-lookup"><span data-stu-id="30951-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="30951-512">**segundo**: Ponter para o destino para o segundo.</span><span class="sxs-lookup"><span data-stu-id="30951-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-513">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-513">Return Values</span></span>

- <span data-ttu-id="30951-514">**FX_SUCCESS** (0x00) Primeira entrada de diretório bem sucedida</span><span class="sxs-lookup"><span data-stu-id="30951-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="30951-515">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-516">**FX_NOT_FOUND** (0x04) Diretório especificado não foi encontrado nos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="30951-517">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-518">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-519">**FX_FILE _CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-520">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-521">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-522">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-523">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino.</span><span class="sxs-lookup"><span data-stu-id="30951-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="30951-524">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-525">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-525">Allowed From</span></span>

<span data-ttu-id="30951-526">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-527">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="30951-528">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-528">See Also</span></span>

- <span data-ttu-id="30951-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-531">fx_directory_create</span></span>
- <span data-ttu-id="30951-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-532">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-533">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-534">fx_directory_delete</span></span>
- <span data-ttu-id="30951-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-542">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-545">fx_directory_rename</span></span>
- <span data-ttu-id="30951-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="30951-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="30951-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="30951-550">Limpa o caminho local padrão</span><span class="sxs-lookup"><span data-stu-id="30951-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-551">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="30951-552">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-552">Description</span></span>

<span data-ttu-id="30951-553">Este serviço limpa o caminho local anterior configurado para o fio de chamada.</span><span class="sxs-lookup"><span data-stu-id="30951-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-554">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-554">Input Parameters</span></span>

- <span data-ttu-id="30951-555">**media_ptr**: Ponter para um meio de comunicação previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-556">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-556">Return Values</span></span>

- <span data-ttu-id="30951-557">**FX_SUCCESS** (0x00) Caminho local bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="30951-558">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos atualmente</span><span class="sxs-lookup"><span data-stu-id="30951-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="30951-559">**FX_NO_LCOAL_PATH FX_NOT_IMPLEMENTED** (0x22) é definido</span><span class="sxs-lookup"><span data-stu-id="30951-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="30951-560">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-561">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-561">Allowed From</span></span>

<span data-ttu-id="30951-562">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-563">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="30951-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-564">See Also</span></span>

- <span data-ttu-id="30951-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-567">fx_directory_create</span></span>
- <span data-ttu-id="30951-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-568">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-569">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-570">fx_directory_delete</span></span>
- <span data-ttu-id="30951-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-573">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-578">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-581">fx_directory_rename</span></span>
- <span data-ttu-id="30951-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="30951-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="30951-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="30951-586">Obtém a cadeia de caminho local atual</span><span class="sxs-lookup"><span data-stu-id="30951-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-587">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="30951-588">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-588">Description</span></span>

<span data-ttu-id="30951-589">Este serviço devolve o ponteiro de percurso local dos meios de comunicação especificados.</span><span class="sxs-lookup"><span data-stu-id="30951-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="30951-590">Se não houver um caminho local definido, um NU É devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="30951-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-591">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-591">Input Parameters</span></span>

- <span data-ttu-id="30951-592">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-593">**return_path_name**: Ponter para o ponteiro de corda de destino para que a cadeia de caminho local seja armazenada.</span><span class="sxs-lookup"><span data-stu-id="30951-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-594">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-594">Return Values</span></span>

- <span data-ttu-id="30951-595">**FX_SUCCESS** (0x00) Caminho local bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="30951-596">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos atualmente</span><span class="sxs-lookup"><span data-stu-id="30951-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="30951-597">**NX_NO_LCOAL_PATH FX_NOT_IMPLEMENTED** (0x22)</span><span class="sxs-lookup"><span data-stu-id="30951-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="30951-598">**FX_PTR_ERROR** (0x18) Ponteiro de meios inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="30951-599">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-599">Allowed From</span></span>

<span data-ttu-id="30951-600">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-601">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="30951-602">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-602">See Also</span></span>

- <span data-ttu-id="30951-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-605">fx_directory_create</span></span>
- <span data-ttu-id="30951-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-606">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-607">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-608">fx_directory_delete</span></span>
- <span data-ttu-id="30951-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-611">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-616">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-619">fx_directory_rename</span></span>
- <span data-ttu-id="30951-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="30951-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="30951-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="30951-624">Restaura o caminho local anterior</span><span class="sxs-lookup"><span data-stu-id="30951-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-625">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="30951-626">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-626">Description</span></span>

<span data-ttu-id="30951-627">Este serviço restaura um caminho local previamente definido.</span><span class="sxs-lookup"><span data-stu-id="30951-627">This service restores a previously set local path.</span></span> <span data-ttu-id="30951-628">A posição de pesquisa de diretórios feita neste caminho local também é restaurada, o que torna esta rotina útil em diretórios recursivos pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="30951-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-629">*Cada caminho local contém uma cadeia de caminhos local de **FX_MAXIMUM_PATH** em tamanho, que por padrão é de 256 caracteres. Esta cadeia de caminhos interno não é utilizada pelo FileX e é fornecida apenas para a utilização da aplicação. Se **FX_LOCAL_PATH** vai ser declarado como uma variável local, os utilizadores devem ter cuidado com a pilha que cresce pelo tamanho desta estrutura. Os utilizadores são bem-vindos a reduzir o tamanho de **FX_MAXIMUM_PATH** e a reconstruir a fonte da biblioteca FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-630">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-630">Input Parameters</span></span>

- <span data-ttu-id="30951-631">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-632">**local_path_ptr**: Ponte rumo ao caminho local previamente definido.</span><span class="sxs-lookup"><span data-stu-id="30951-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="30951-633">É muito importante garantir que este ponteiro realmente aponta para um caminho local usado e ainda intacto.</span><span class="sxs-lookup"><span data-stu-id="30951-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-634">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-634">Return Values</span></span>

- <span data-ttu-id="30951-635">**FX_SUCCESS** (0x00) Restaurar o caminho local bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="30951-636">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão atualmente abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="30951-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH é definido.</span><span class="sxs-lookup"><span data-stu-id="30951-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="30951-638">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de percurso local.</span><span class="sxs-lookup"><span data-stu-id="30951-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-639">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-639">Allowed From</span></span>

<span data-ttu-id="30951-640">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-641">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="30951-642">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-642">See Also</span></span>

- <span data-ttu-id="30951-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-645">fx_directory_create</span></span>
- <span data-ttu-id="30951-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-646">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-647">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-648">fx_directory_delete</span></span>
- <span data-ttu-id="30951-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-651">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-656">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-659">fx_directory_rename</span></span>
- <span data-ttu-id="30951-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="30951-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="30951-664">Cria um caminho local específico de linha</span><span class="sxs-lookup"><span data-stu-id="30951-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-665">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="30951-666">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-666">Description</span></span>

<span data-ttu-id="30951-667">Este serviço estabelece um caminho específico de fio, conforme especificado pela \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="30951-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="30951-668">Após a conclusão com sucesso desta rotina, as informações locais armazenadas em _ *_local_path_ptr_*\* terão precedência sobre o caminho global dos meios de comunicação para todas as operações de arquivo e diretório feitas por este fio.</span><span class="sxs-lookup"><span data-stu-id="30951-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="30951-669">Isto não terá qualquer impacto em qualquer outro fio no sistema</span><span class="sxs-lookup"><span data-stu-id="30951-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="30951-670">*O tamanho padrão da cadeia de caminho local é de 256 caracteres; pode ser alterado modificando **FX_MAXIMUM_PATH** em **fx_api.h** e reconstruindo toda a biblioteca Do FicheiroX. O caminho da corda do personagem é mantido para a aplicação e não é usado internamente pelo FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-671">*Para os nomes fornecidos pela aplicação, o FileX suporta caracteres backslash \\ (/ ) e barras para a frente (/) para diretórios separados, subdiretórios e nomes de ficheiros. No entanto, o FileX utiliza apenas o carácter backslash nos caminhos devolvidos à aplicação.*</span><span class="sxs-lookup"><span data-stu-id="30951-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-672">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-672">Input Parameters</span></span>

- <span data-ttu-id="30951-673">**media_ptr**: Ponte para o meio de comunicação anteriormente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="30951-674">**local_path_ptr**: Destino para a detenção das informações do percurso local específicas do fio.</span><span class="sxs-lookup"><span data-stu-id="30951-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="30951-675">O endereço desta estrutura pode ser fornecido para a função de restauro do caminho local no futuro.</span><span class="sxs-lookup"><span data-stu-id="30951-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="30951-676">**new_path_name**: Especifica o caminho local para a configuração.</span><span class="sxs-lookup"><span data-stu-id="30951-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-677">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-677">Return Values</span></span>

- <span data-ttu-id="30951-678">**FX_SUCCESS** (0x00) Conjunto de diretório padrão bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="30951-679">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="30951-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="30951-681">**FX_INVALID_PATH** (0x0D) Não foi possível encontrar novos diretórios.</span><span class="sxs-lookup"><span data-stu-id="30951-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="30951-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH é definido.</span><span class="sxs-lookup"><span data-stu-id="30951-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="30951-683">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de percurso local.</span><span class="sxs-lookup"><span data-stu-id="30951-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-684">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-684">Allowed From</span></span>

<span data-ttu-id="30951-685">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-686">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="30951-687">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-687">See Also</span></span>

- <span data-ttu-id="30951-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-690">fx_directory_create</span></span>
- <span data-ttu-id="30951-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-691">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-692">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-693">fx_directory_delete</span></span>
- <span data-ttu-id="30951-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-696">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-701">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-704">fx_directory_rename</span></span>
- <span data-ttu-id="30951-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="30951-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="30951-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="30951-709">Obtém um nome longo de nome curto</span><span class="sxs-lookup"><span data-stu-id="30951-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-710">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="30951-711">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-711">Description</span></span>

<span data-ttu-id="30951-712">Este serviço recupera o nome longo (se houver) associado ao nome fornecido curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="30951-713">O nome curto pode ser um nome de ficheiro ou um nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-714">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-714">Input Parameters</span></span>

- <span data-ttu-id="30951-715">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-716">**short_name**: Ponteiro para o nome curto de origem (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="30951-717">**long_name**: Ponte para destino para o nome longo.</span><span class="sxs-lookup"><span data-stu-id="30951-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="30951-718">Se não houver um nome comprido, o nome curto é devolvido.</span><span class="sxs-lookup"><span data-stu-id="30951-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="30951-719">Note que o destino para o nome longo deve ser grande o suficiente para manter FX_MAX_LONG_NAME_LEN caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-720">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-720">Return Values</span></span>

- <span data-ttu-id="30951-721">**FX_SUCCESS** (0x00) Nome longo bem sucedido obter</span><span class="sxs-lookup"><span data-stu-id="30951-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="30951-722">**FX_NOT_FOUND** (0x04) Nome curto não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="30951-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="30951-723">**erro de** FX_IO_ERROR (0x90) do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="30951-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="30951-724">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos</span><span class="sxs-lookup"><span data-stu-id="30951-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="30951-725">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-726">**FX_SECTOR_INVALID** (0x89) Sector inválido</span><span class="sxs-lookup"><span data-stu-id="30951-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="30951-727">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada da FAT</span><span class="sxs-lookup"><span data-stu-id="30951-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="30951-728">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-729">**FX_PTR_ERROR** (0x18) Meios inválidos ou ponteiros de nome</span><span class="sxs-lookup"><span data-stu-id="30951-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="30951-730">**FX_CALLER_ERROR** (0x20) Caller não é um fio</span><span class="sxs-lookup"><span data-stu-id="30951-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-731">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-731">Allowed From</span></span>

<span data-ttu-id="30951-732">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-733">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="30951-734">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-734">See Also</span></span>

- <span data-ttu-id="30951-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-737">fx_directory_create</span></span>
- <span data-ttu-id="30951-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-738">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-739">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-740">fx_directory_delete</span></span>
- <span data-ttu-id="30951-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-743">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-748">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-751">fx_directory_rename</span></span>
- <span data-ttu-id="30951-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="30951-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="30951-756">Obtém um nome longo de nome curto</span><span class="sxs-lookup"><span data-stu-id="30951-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-757">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="30951-758">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-758">Description</span></span>

<span data-ttu-id="30951-759">Este serviço recupera o nome longo (se houver) associado ao nome fornecido curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="30951-760">O nome curto pode ser um nome de ficheiro ou um nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-761">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-761">Input Parameters</span></span>

- <span data-ttu-id="30951-762">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-763">**short_name**: Ponteiro para o nome curto de origem (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="30951-764">**long_name**: Ponte para destino para o nome longo.</span><span class="sxs-lookup"><span data-stu-id="30951-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="30951-765">Se não houver um nome comprido, o nome curto é devolvido.</span><span class="sxs-lookup"><span data-stu-id="30951-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="30951-766">Nota: O destino para o nome longo deve ser grande o suficiente para manter **FX_MAX_LONG_NAME_LEN** caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="30951-767">**long_file_name_buffer_length**: Comprimento do tampão de nome comprido.</span><span class="sxs-lookup"><span data-stu-id="30951-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-768">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-768">Return Values</span></span>

- <span data-ttu-id="30951-769">**FX_SUCCESS** (0x00) Nome longo bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="30951-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="30951-770">**FX_NOT_FOUND** (0x04) Nome curto não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="30951-771">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-772">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-773">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-774">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-775">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-776">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-777">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="30951-778">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-779">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-779">Allowed From</span></span>

<span data-ttu-id="30951-780">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-781">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="30951-782">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-782">See Also</span></span>

- <span data-ttu-id="30951-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-785">fx_directory_create</span></span>
- <span data-ttu-id="30951-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-786">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-787">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-788">fx_directory_delete</span></span>
- <span data-ttu-id="30951-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-791">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-799">fx_directory_rename</span></span>
- <span data-ttu-id="30951-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="30951-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-803">fx_directory_name_test</span></span>

<span data-ttu-id="30951-804">Ensaios para diretório</span><span class="sxs-lookup"><span data-stu-id="30951-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-805">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="30951-806">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-806">Description</span></span>

<span data-ttu-id="30951-807">Este serviço testa se o nome fornecido é ou não um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="30951-808">Em caso afirmativo, um FX_SUCCESS é devolvido.</span><span class="sxs-lookup"><span data-stu-id="30951-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-809">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-809">Input Parameters</span></span>

- <span data-ttu-id="30951-810">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-811">**directory_name**: Ponteiro para o nome da entrada do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-812">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-812">Return Values</span></span>

- <span data-ttu-id="30951-813">**FX_SUCCESS** (0x00) O nome fornecido é um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="30951-814">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos</span><span class="sxs-lookup"><span data-stu-id="30951-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="30951-815">**FX_NOT_FOUND** (0x04) não foi encontrado o diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="30951-816">**FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório</span><span class="sxs-lookup"><span data-stu-id="30951-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="30951-817">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-818">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-819">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-820">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-821">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-822">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-823">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="30951-824">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-825">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-825">Allowed From</span></span>

<span data-ttu-id="30951-826">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-827">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="30951-828">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-828">See Also</span></span>

- <span data-ttu-id="30951-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-831">fx_directory_create</span></span>
- <span data-ttu-id="30951-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-832">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-833">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-834">fx_directory_delete</span></span>
- <span data-ttu-id="30951-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-837">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-845">fx_directory_rename</span></span>
- <span data-ttu-id="30951-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="30951-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="30951-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="30951-849">Apanha a próxima entrada de diretório</span><span class="sxs-lookup"><span data-stu-id="30951-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="30951-851">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-851">Description</span></span>

<span data-ttu-id="30951-852">Este serviço devolve o próximo nome de entrada no diretório padrão atual.</span><span class="sxs-lookup"><span data-stu-id="30951-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-853">*Se utilizar um caminho não local, também é importante evitar (com um semáforo ThreadX ou nível prioritário de thread) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-854">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-854">Input Parameters</span></span>

- <span data-ttu-id="30951-855">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-856">**return_entry_name**: Ponteiro para o destino para o próximo nome de entrada no diretório predefinido.</span><span class="sxs-lookup"><span data-stu-id="30951-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="30951-857">O tampão a que este ponteiro aponta deve ser suficientemente grande para manter o tamanho máximo do nome FileX, definido por **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="30951-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-858">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-858">Return Values</span></span>

- <span data-ttu-id="30951-859">**FX_SUCCESS** (0x00) Sucesso próxima entrada encontrar</span><span class="sxs-lookup"><span data-stu-id="30951-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="30951-860">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-861">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="30951-862">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-863">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-864">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-865">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-866">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-867">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-868">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-869">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-869">Allowed From</span></span>

<span data-ttu-id="30951-870">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-871">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-872">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-872">See Also</span></span>

- <span data-ttu-id="30951-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-875">fx_directory_create</span></span>
- <span data-ttu-id="30951-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-876">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-877">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-878">fx_directory_delete</span></span>
- <span data-ttu-id="30951-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-881">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-887">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-889">fx_directory_rename</span></span>
- <span data-ttu-id="30951-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="30951-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="30951-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="30951-894">Obtém a próxima entrada de diretório com informação completa</span><span class="sxs-lookup"><span data-stu-id="30951-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="30951-896">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-896">Description</span></span>

<span data-ttu-id="30951-897">Este serviço recupera o próximo nome de entrada no diretório predefinido e copia-o para o destino especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="30951-898">Também devolve informações completas sobre a entrada, conforme especificado pelos parâmetros de entrada adicionais.</span><span class="sxs-lookup"><span data-stu-id="30951-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-899">\*O destino especificado deve ser grande o suficiente para manter o nome FileX de tamanho máximo, tal como definido por \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="30951-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="30951-900">*Se utilizar um caminho não local, é importante evitar (com um semáforo ThreadX, mutex ou mudança de nível prioritário) que outros fios de aplicação mudem este diretório enquanto está a decorrer um diretório. Caso contrário, podem ser obtidos resultados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-901">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-901">Input Parameters</span></span>

- <span data-ttu-id="30951-902">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-903">**directory_name**: Ponte para o destino para o nome de uma entrada de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="30951-904">Deve ter pelo menos o tamanho **FX_MAX_LONG_NAME_LEN.**</span><span class="sxs-lookup"><span data-stu-id="30951-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="30951-905">**atributos**: Se não for nulo, ponteiro para o destino para os atributos da entrada a colocar. Os atributos são devolvidos num formato de mapa bit com as seguintes definições possíveis:</span><span class="sxs-lookup"><span data-stu-id="30951-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="30951-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="30951-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="30951-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="30951-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="30951-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="30951-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="30951-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="30951-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="30951-912">**tamanho**: Se não foruso, ponteiro para o destino para o tamanho da entrada em bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="30951-913">**mês**: Se não for nulo, ponteiu o destino para o mês de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="30951-914">**ano**: Se não for nulo, pontia o destino para o ano de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="30951-915">**dia**: Se não for nulo, ponteiu o destino para o dia de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="30951-916">**hora**: Se não for nulo, ponteiu o destino para a hora de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="30951-917">**minuto**: Se não for nulo, ponteiu o destino para o minuto de modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="30951-918">**segundo**: Se não for nulo, ponteiu o destino para a segunda modificação da entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-919">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-919">Return Values</span></span>

- <span data-ttu-id="30951-920">**FX_SUCCESS** (0x00) O diretório de sucesso da próxima entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="30951-921">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-922">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="30951-923">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-924">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-925">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-926">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-927">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-928">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-929">**FX_PTR_ERROR** (0x18) O ponteiro de mídia inválido ou todos os parâmetros de entrada são NULOS.</span><span class="sxs-lookup"><span data-stu-id="30951-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="30951-930">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-931">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-931">Allowed From</span></span>

<span data-ttu-id="30951-932">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-933">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="30951-934">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-934">See Also</span></span>

- <span data-ttu-id="30951-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-937">fx_directory_create</span></span>
- <span data-ttu-id="30951-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-938">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-939">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-940">fx_directory_delete</span></span>
- <span data-ttu-id="30951-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-943">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-949">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-951">fx_directory_rename</span></span>
- <span data-ttu-id="30951-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="30951-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-955">fx_directory_rename</span></span>

<span data-ttu-id="30951-956">Renomeia diretório</span><span class="sxs-lookup"><span data-stu-id="30951-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-957">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="30951-958">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-958">Description</span></span>

<span data-ttu-id="30951-959">Este serviço altera o nome do diretório para o novo nome especificado do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="30951-960">O renomeamento também é feito em relação ao caminho especificado ou ao caminho padrão.</span><span class="sxs-lookup"><span data-stu-id="30951-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="30951-961">Se um caminho for especificado no novo nome do diretório, o diretório renomeado é efetivamente movido para o caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="30951-962">Se não for especificado nenhum caminho, o diretório renomeado é colocado na trajetória predefinida atual.</span><span class="sxs-lookup"><span data-stu-id="30951-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-963">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-963">Input Parameters</span></span>

- <span data-ttu-id="30951-964">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-965">**old_directory_name**: Ponteiro para o nome atual do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="30951-966">**new_directory_name**: Ponteiro para o novo nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-967">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-967">Return Values</span></span>

- <span data-ttu-id="30951-968">**FX_SUCCESS** (0x00) Nomeador de diretório de sucesso.</span><span class="sxs-lookup"><span data-stu-id="30951-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="30951-969">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-970">**FX_NOT_FOUND** (0x04) não foi encontrado o diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="30951-971">**FX_NOT_DIRECTORY** (0x0E) A entrada não é um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="30951-972">**FX_INVALID_NAME** (0x0C) O novo nome do diretório é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="30951-973">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-974">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-975">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-976">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-977">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-978">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-979">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-980">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais inscrições neste diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="30951-981">**FX_INVALID_PATH** (0x0D) Caminho inválido fornecido com nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="30951-982">**FX_ALREADY_CREATED** (0x0B) Já foi criado o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="30951-983">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-984">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-985">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-985">Allowed From</span></span>

<span data-ttu-id="30951-986">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-987">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="30951-988">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-988">See Also</span></span>

- <span data-ttu-id="30951-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-991">fx_directory_create</span></span>
- <span data-ttu-id="30951-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-992">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-993">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-994">fx_directory_delete</span></span>
- <span data-ttu-id="30951-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-997">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="30951-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="30951-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="30951-1010">Obtém um nome curto de um nome comprido</span><span class="sxs-lookup"><span data-stu-id="30951-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1011">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="30951-1012">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1012">Description</span></span>

<span data-ttu-id="30951-1013">Este serviço recupera o nome curto (formato 8.3) associado ao nome longo fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="30951-1014">O nome longo pode ser um nome de arquivo ou um nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1015">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1015">Input Parameters</span></span>

- <span data-ttu-id="30951-1016">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-1017">**long_name**: Ponteiro para fonte de nome longo.</span><span class="sxs-lookup"><span data-stu-id="30951-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="30951-1018">**short_name**: Ponteiro para o nome curto de destino (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="30951-1019">Note que o destino para o nome curto deve ser grande o suficiente para conter 14 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1020">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1020">Return Values</span></span>

- <span data-ttu-id="30951-1021">**FX_SUCCESS** (0x00) Nome curto bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="30951-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="30951-1022">**FX_NOT_FOUND** (0x04) Nome longo não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="30951-1023">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1024">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1025">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1026">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1027">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1028">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1029">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-1030">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="30951-1031">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1032">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1032">Allowed From</span></span>

<span data-ttu-id="30951-1033">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1034">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1035">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1035">See Also</span></span>

- <span data-ttu-id="30951-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-1038">fx_directory_create</span></span>
- <span data-ttu-id="30951-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1041">fx_directory_delete</span></span>
- <span data-ttu-id="30951-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1053">fx_directory_rename</span></span>
- <span data-ttu-id="30951-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="30951-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="30951-1057">Obtém um nome curto de um nome comprido</span><span class="sxs-lookup"><span data-stu-id="30951-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="30951-1059">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1059">Description</span></span>

<span data-ttu-id="30951-1060">Este serviço recupera o nome curto (formato 8.3) associado ao nome longo fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="30951-1061">O nome longo pode ser um nome de arquivo ou um nome de diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1062">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1062">Input Parameters</span></span>

- <span data-ttu-id="30951-1063">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-1064">**long_name**: Ponteiro para fonte de nome longo.</span><span class="sxs-lookup"><span data-stu-id="30951-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="30951-1065">**short_name**: Ponteiro para o nome curto de destino (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="30951-1066">Nota: O destino do nome curto deve ser grande o suficiente para conter 14 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="30951-1067">**short_file_name_length**: Comprimento do tampão de nome curto.</span><span class="sxs-lookup"><span data-stu-id="30951-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1068">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1068">Return Values</span></span>

- <span data-ttu-id="30951-1069">**FX_SUCCESS** (0x00) Nome curto bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="30951-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="30951-1070">**FX_NOT_FOUND** (0x04) Nome longo não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="30951-1071">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1072">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1073">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1074">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1075">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1076">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1077">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-1078">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="30951-1079">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1080">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1080">Allowed From</span></span>

<span data-ttu-id="30951-1081">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1082">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1083">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1083">See Also</span></span>

- <span data-ttu-id="30951-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-1086">fx_directory_create</span></span>
- <span data-ttu-id="30951-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1089">fx_directory_delete</span></span>
- <span data-ttu-id="30951-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1101">fx_directory_rename</span></span>
- <span data-ttu-id="30951-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="30951-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="30951-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="30951-1105">Permite o serviço tolerante a falhas</span><span class="sxs-lookup"><span data-stu-id="30951-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1106">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="30951-1107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1107">Description</span></span>

<span data-ttu-id="30951-1108">Este serviço permite o módulo tolerante a falhas.</span><span class="sxs-lookup"><span data-stu-id="30951-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="30951-1109">Ao iniciar, o módulo tolerante a falhas deteta se o sistema de ficheiros está ou não sob proteção tolerante a falhas do FileX.</span><span class="sxs-lookup"><span data-stu-id="30951-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="30951-1110">Caso contrário, o serviço encontra setores disponíveis no sistema de ficheiros para armazenar registos em transações do sistema de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="30951-1111">Se o sistema de ficheiros estiver sob proteção tolerante a falhas do FileX, aplica os registos no sistema de ficheiros para manter a sua integridade.</span><span class="sxs-lookup"><span data-stu-id="30951-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1112">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1112">Input Parameters</span></span>

- <span data-ttu-id="30951-1113">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1114">**memory_ptr**: Ponteie para um bloco de memória utilizado pelo módulo tolerante de avaria como memória de risco.</span><span class="sxs-lookup"><span data-stu-id="30951-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="30951-1115">**memory_size:** O tamanho da memória do arranhão.</span><span class="sxs-lookup"><span data-stu-id="30951-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="30951-1116">Para que as falhas tolerantes funcionem corretamente, o tamanho da memória de risco deve ser de, pelo menos, 3072 bytes, e deve ser múltiplo do tamanho do sector.</span><span class="sxs-lookup"><span data-stu-id="30951-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1117">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1117">Return Values</span></span>

- <span data-ttu-id="30951-1118">**FX_SUCCESS** (0x00) com sucesso permitiu tolerante a falhas.</span><span class="sxs-lookup"><span data-stu-id="30951-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="30951-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) tamanho da memória demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="30951-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="30951-1120">**FX_BOOT_ERROR** (0x01) Erro do sector do arranque.</span><span class="sxs-lookup"><span data-stu-id="30951-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="30951-1121">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1122">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais cluster gratuito disponível.</span><span class="sxs-lookup"><span data-stu-id="30951-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="30951-1123">**FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.</span><span class="sxs-lookup"><span data-stu-id="30951-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="30951-1124">Sector **FX_SECTOR_INVALID** (0x89) é inválido</span><span class="sxs-lookup"><span data-stu-id="30951-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="30951-1125">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1126">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-1127">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1128">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1128">Allowed From</span></span>

<span data-ttu-id="30951-1129">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="30951-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="30951-1131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1131">See Also</span></span>

- <span data-ttu-id="30951-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-1132">fx_system_initialize</span></span>
- <span data-ttu-id="30951-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-1133">fx_media_abort</span></span>
- <span data-ttu-id="30951-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-1135">fx_media_check</span></span>
- <span data-ttu-id="30951-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-1136">fx_media_close</span></span>
- <span data-ttu-id="30951-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-1140">fx_media_flush</span></span>
- <span data-ttu-id="30951-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-1141">fx_media_format</span></span>
- <span data-ttu-id="30951-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-1142">fx_media_open</span></span>
- <span data-ttu-id="30951-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-1144">fx_media_read</span></span>
- <span data-ttu-id="30951-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-1145">fx_media_space_available</span></span>
- <span data-ttu-id="30951-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="30951-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1149">fx_file_allocate</span></span>

<span data-ttu-id="30951-1150">Aloca espaço para um ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="30951-1152">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1152">Description</span></span>

<span data-ttu-id="30951-1153">Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="30951-1154">O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="30951-1155">O resultado é então arredondado para todo o cluster seguinte.</span><span class="sxs-lookup"><span data-stu-id="30951-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="30951-1156">Para alocar espaço para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="30951-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1157">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1157">Input Parameters</span></span>

- <span data-ttu-id="30951-1158">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1159">**tamanho**: Número de bytes a atribuir para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1160">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1160">Return Values</span></span>

- <span data-ttu-id="30951-1161">**FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="30951-1162">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1163">**FX_FAT_READ_ERROR** (0x03) Não leu a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="30951-1164">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1165">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1166">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais cluster gratuito disponível.</span><span class="sxs-lookup"><span data-stu-id="30951-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="30951-1167">**FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.</span><span class="sxs-lookup"><span data-stu-id="30951-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="30951-1168">Sector **FX_SECTOR_INVALID** (0x89) é inválido</span><span class="sxs-lookup"><span data-stu-id="30951-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="30951-1169">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1170">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1171">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1172">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1173">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1173">Allowed From</span></span>

<span data-ttu-id="30951-1174">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1176">See Also</span></span>

- <span data-ttu-id="30951-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1180">fx_file_close fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="30951-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1182">fx_file_delete</span></span>
- <span data-ttu-id="30951-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1189">fx_file_open fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="30951-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1191">fx_file_rename fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="30951-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1192">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1194">fx_file_write</span></span>
- <span data-ttu-id="30951-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="30951-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="30951-1201">Lê atributos de ficheiros</span><span class="sxs-lookup"><span data-stu-id="30951-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1202">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-1203">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1203">Description</span></span>

<span data-ttu-id="30951-1204">Este serviço lê os atributos do ficheiro a partir dos meios de comunicação especificados.</span><span class="sxs-lookup"><span data-stu-id="30951-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1205">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1205">Input Parameters</span></span>

- <span data-ttu-id="30951-1206">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1207">**file_name**: Pontear o nome do ficheiro solicitado (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="30951-1208">**attributes_ptr**: Ponter para o destino para que os atributos do ficheiro sejam colocados.</span><span class="sxs-lookup"><span data-stu-id="30951-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="30951-1209">Os atributos do ficheiro são devolvidos num formato de mapa bit com as seguintes definições possíveis:</span><span class="sxs-lookup"><span data-stu-id="30951-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="30951-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="30951-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="30951-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="30951-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="30951-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="30951-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="30951-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="30951-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1216">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1216">Return Values</span></span>

- <span data-ttu-id="30951-1217">**FX_SUCCESS** (0x00) Leitura de atributos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="30951-1218">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1219">**FX_NOT_FOUND** ficheiro especificado (0x04) não foi encontrado nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="30951-1220">**FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="30951-1221">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1222">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1223">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1224">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1225">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1226">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou atributos.</span><span class="sxs-lookup"><span data-stu-id="30951-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="30951-1227">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1228">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1228">Allowed From</span></span>

<span data-ttu-id="30951-1229">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="30951-1231">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1231">See Also</span></span>

- <span data-ttu-id="30951-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1232">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1235">fx_file_close fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="30951-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1237">fx_file_delete</span></span>
- <span data-ttu-id="30951-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1244">fx_file_open</span></span>
- <span data-ttu-id="30951-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1245">fx_file_read</span></span>
- <span data-ttu-id="30951-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1247">fx_file_rename</span></span>
- <span data-ttu-id="30951-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1248">fx_file_seek</span></span>
- <span data-ttu-id="30951-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1249">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1251">fx_file_write</span></span>
- <span data-ttu-id="30951-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="30951-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="30951-1258">Define atributos de ficheiros</span><span class="sxs-lookup"><span data-stu-id="30951-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1259">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="30951-1260">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1260">Description</span></span>

<span data-ttu-id="30951-1261">Este serviço define os atributos do ficheiro aos especificados pelo autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="30951-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-1262">*A aplicação só é permitida para modificar um subconjunto dos atributos do ficheiro com este serviço. Qualquer tentativa de definir atributos adicionais resultará num erro.*</span><span class="sxs-lookup"><span data-stu-id="30951-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1263">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1263">Input Parameters</span></span>

- <span data-ttu-id="30951-1264">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1265">**file_name**: Ponteiro para o nome do ficheiro solicitado\*\* (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="30951-1266">**atributos**: Os novos atributos para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="30951-1267">Os atributos de ficheiro válidos são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="30951-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="30951-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="30951-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="30951-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="30951-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="30951-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1272">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1272">Return Values</span></span>

- <span data-ttu-id="30951-1273">**FX_SUCCESS** (0x00) Conjunto de atributos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="30951-1274">**FX_ACCESS_ERROR** ficheiro (0x06) está aberto e não pode ter os seus atributos definidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="30951-1275">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1276">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1277">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1278">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas na tabela FAT ou no mapa do cluster exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="30951-1279">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-1280">**FX_NOT_FOUND** ficheiro especificado (0x04) não foi encontrado nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="30951-1281">**FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="30951-1282">Sector **FX_SECTOR_INVALID** (0x89) é inválido</span><span class="sxs-lookup"><span data-stu-id="30951-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="30951-1283">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1284">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1285">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-1286">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-1287">**FX_INVALID_ATTR** (0x19) Atributos inválidos selecionados.</span><span class="sxs-lookup"><span data-stu-id="30951-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="30951-1288">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1289">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1289">Allowed From</span></span>

<span data-ttu-id="30951-1290">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1291">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="30951-1292">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1292">See Also</span></span>

- <span data-ttu-id="30951-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1293">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1296">fx_file_close</span></span>
- <span data-ttu-id="30951-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1297">fx_file_create</span></span>
- <span data-ttu-id="30951-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1299">fx_file_delete</span></span>
- <span data-ttu-id="30951-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1306">fx_file_open</span></span>
- <span data-ttu-id="30951-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1307">fx_file_read</span></span>
- <span data-ttu-id="30951-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1309">fx_file_rename</span></span>
- <span data-ttu-id="30951-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1310">fx_file_seek</span></span>
- <span data-ttu-id="30951-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1311">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1313">fx_file_write</span></span>
- <span data-ttu-id="30951-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="30951-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="30951-1320">Melhor esforço para alocar espaço para um arquivo</span><span class="sxs-lookup"><span data-stu-id="30951-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1321">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="30951-1322">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1322">Description</span></span>

<span data-ttu-id="30951-1323">Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="30951-1324">O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="30951-1325">O resultado é então arredondado para todo o cluster seguinte.</span><span class="sxs-lookup"><span data-stu-id="30951-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="30951-1326">Se não houver aglomerados consecutivos suficientes disponíveis nos meios de comunicação, este serviço liga o maior bloco disponível de clusters consecutivos ao ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="30951-1327">A quantidade de espaço efetivamente alocada ao ficheiro é devolvida ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="30951-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="30951-1328">Para alocar espaço para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="30951-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1329">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1329">Input Parameters</span></span>

- <span data-ttu-id="30951-1330">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1331">**tamanho**: Número de bytes a atribuir para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1332">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1332">Return Values</span></span>

- <span data-ttu-id="30951-1333">**FX_SUCCESS** (0x00) Alocação de ficheiros de melhor esforço bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="30951-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="30951-1334">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1335">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1336">**FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.</span><span class="sxs-lookup"><span data-stu-id="30951-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="30951-1337">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1338">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1339">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1340">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1341">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1342">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1343">**FX_PTR_ERROR** (0x18) Ponteiro ou destino de ficheiros inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="30951-1344">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1345">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1345">Allowed From</span></span>

<span data-ttu-id="30951-1346">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1347">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="30951-1348">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1348">See Also</span></span>

- <span data-ttu-id="30951-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1349">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1352">fx_file_close</span></span>
- <span data-ttu-id="30951-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1353">fx_file_create</span></span>
- <span data-ttu-id="30951-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1355">fx_file_delete</span></span>
- <span data-ttu-id="30951-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1362">fx_file_open</span></span>
- <span data-ttu-id="30951-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1363">fx_file_read</span></span>
- <span data-ttu-id="30951-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1365">fx_file_rename</span></span>
- <span data-ttu-id="30951-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1366">fx_file_seek</span></span>
- <span data-ttu-id="30951-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1367">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1369">fx_file_write</span></span>
- <span data-ttu-id="30951-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="30951-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1375">fx_file_close</span></span>

<span data-ttu-id="30951-1376">Arquivo de fechos</span><span class="sxs-lookup"><span data-stu-id="30951-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1377">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-1378">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1378">Description</span></span>

<span data-ttu-id="30951-1379">Este serviço fecha o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1379">This service closes the specified file.</span></span> <span data-ttu-id="30951-1380">Se o ficheiro estiver aberto para escrita e se foi modificado, este serviço completa o processo de modificação do ficheiro atualizando a sua entrada no diretório com o novo tamanho e a hora e data do sistema atuais.</span><span class="sxs-lookup"><span data-stu-id="30951-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1381">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1381">Input Parameters</span></span>

- <span data-ttu-id="30951-1382">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1383">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1383">Return Values</span></span>

- <span data-ttu-id="30951-1384">**FX_SUCCESS** (0x00) Arquivo bem sucedido perto.</span><span class="sxs-lookup"><span data-stu-id="30951-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="30951-1385">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-1386">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1387">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1388">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1389">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou atributos.</span><span class="sxs-lookup"><span data-stu-id="30951-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="30951-1390">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1391">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1391">Allowed From</span></span>

<span data-ttu-id="30951-1392">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1393">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1394">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1394">See Also</span></span>

- <span data-ttu-id="30951-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1395">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1399">fx_file_create</span></span>
- <span data-ttu-id="30951-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1401">fx_file_delete</span></span>
- <span data-ttu-id="30951-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1408">fx_file_open</span></span>
- <span data-ttu-id="30951-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1409">fx_file_read</span></span>
- <span data-ttu-id="30951-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1411">fx_file_rename</span></span>
- <span data-ttu-id="30951-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1412">fx_file_seek</span></span>
- <span data-ttu-id="30951-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1413">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1415">fx_file_write</span></span>
- <span data-ttu-id="30951-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="30951-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1421">fx_file_create</span></span>

<span data-ttu-id="30951-1422">Cria ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1423">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="30951-1424">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1424">Description</span></span>

<span data-ttu-id="30951-1425">Este serviço cria o ficheiro especificado no diretório predefinido ou no caminho do diretório fornecido com o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-1426">*Este serviço cria um ficheiro de comprimento zero, ou seja, sem aglomerados atribuídos. A atribuição será feita automaticamente em posteriores escritas de ficheiros ou pode ser feita com antecedência com o serviço fx_file_allocate ou fx_file_extended_allocate para o espaço além de 4GB).*</span><span class="sxs-lookup"><span data-stu-id="30951-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1427">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1427">Input Parameters</span></span>

- <span data-ttu-id="30951-1428">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1429">**file_name**: Pontear o nome do ficheiro para criar (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1430">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1430">Return Values</span></span>

- <span data-ttu-id="30951-1431">**FX_SUCCESS** (0x00) Criação de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="30951-1432">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1433">**FX_ALREADY_CREATED** (0x0B) Já foi criado o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="30951-1434">**FX_NO_MORE_SPACE** (0x0A) Ou não há mais entradas no diretório de raiz ou não há mais clusters disponíveis.</span><span class="sxs-lookup"><span data-stu-id="30951-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="30951-1435">**FX_INVALID_PATH** (0x0D) Caminho inválido fornecido com nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="30951-1436">**FX_INVALID_NAME** (0x0C) O nome do ficheiro é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="30951-1437">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1438">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1439">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1440">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1441">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1442">**FX_MEDIA_INVALID** (0x02)Meios inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="30951-1443">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1444">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="30951-1445">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de nome de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="30951-1446">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1447">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1447">Allowed From</span></span>

<span data-ttu-id="30951-1448">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1449">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="30951-1450">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1450">See Also</span></span>
- <span data-ttu-id="30951-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1451">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1455">fx_file_close</span></span>
- <span data-ttu-id="30951-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1457">fx_file_delete</span></span>
- <span data-ttu-id="30951-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1464">fx_file_open</span></span>
- <span data-ttu-id="30951-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1465">fx_file_read</span></span>
- <span data-ttu-id="30951-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1467">fx_file_rename</span></span>
- <span data-ttu-id="30951-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1468">fx_file_seek</span></span>
- <span data-ttu-id="30951-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1469">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1471">fx_file_write</span></span>
- <span data-ttu-id="30951-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="30951-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="30951-1478">Define data e hora do arquivo</span><span class="sxs-lookup"><span data-stu-id="30951-1478">Sets file date and time</span></span>

<span data-ttu-id="30951-1479">Definição data e hora do arquivo</span><span class="sxs-lookup"><span data-stu-id="30951-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1480">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="30951-1481">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1481">Description</span></span>

<span data-ttu-id="30951-1482">Este serviço define a data e a hora do ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="30951-1483">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1483">Input Parameters</span></span>

- <span data-ttu-id="30951-1484">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-1485">**file_name**: Ponteiro para o nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="30951-1486">**ano**: Valor do ano (1980-2107 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="30951-1487">**mês**: Valor do mês (1-12 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="30951-1488">**dia**: Valor do dia (1-31 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="30951-1489">**hora**: Valor da hora (0-23 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="30951-1490">**minuto**: Valor do minuto (0-59 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="30951-1491">**segundo**: Valor do segundo (0-59 inclusive).</span><span class="sxs-lookup"><span data-stu-id="30951-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1492">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1492">Return Values</span></span>

- <span data-ttu-id="30951-1493">**FX_SUCCESS** (0x00) Data/hora de sucesso.</span><span class="sxs-lookup"><span data-stu-id="30951-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="30951-1494">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1495">**FX_NOT_FOUND** ficheiro (0x04) não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="30951-1496">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="30951-1497">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1498">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1499">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1500">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-1501">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1502">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1503">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="30951-1504">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="30951-1505">**FX_INVALID_YEAR** (0x12) Ano é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="30951-1506">**FX_INVALID_MONTH** (0x13) Mês é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="30951-1507">**FX_INVALID_DAY** (0x14) Dia é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="30951-1508">**FX_INVALID_HOUR** (0x15) Hora é inválida.</span><span class="sxs-lookup"><span data-stu-id="30951-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="30951-1509">**FX_INVALID_MINUTE** (0x16) O minuto é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="30951-1510">**FX_INVALID_SECOND** (0x17) O segundo é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1511">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1511">Allowed From</span></span>

<span data-ttu-id="30951-1512">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1513">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="30951-1514">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1514">See Also</span></span>

- <span data-ttu-id="30951-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1515">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1519">fx_file_close</span></span>
- <span data-ttu-id="30951-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1520">fx_file_create</span></span>
- <span data-ttu-id="30951-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1521">fx_file_delete</span></span>
- <span data-ttu-id="30951-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1528">fx_file_open</span></span>
- <span data-ttu-id="30951-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1529">fx_file_read</span></span>
- <span data-ttu-id="30951-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1531">fx_file_rename</span></span>
- <span data-ttu-id="30951-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1532">fx_file_seek</span></span>
- <span data-ttu-id="30951-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1533">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1535">fx_file_write</span></span>
- <span data-ttu-id="30951-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="30951-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="30951-1542">Elimina ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-1542">Deletes file</span></span>

<span data-ttu-id="30951-1543">Eliminação de Ficheiros</span><span class="sxs-lookup"><span data-stu-id="30951-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1544">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="30951-1545">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1545">Description</span></span>

<span data-ttu-id="30951-1546">Este serviço elimina o ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="30951-1547">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1547">Input Parameters</span></span>

- <span data-ttu-id="30951-1548">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1549">**file_name**: Pontear o nome do ficheiro para apagar (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1550">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1550">Return Values</span></span>

- <span data-ttu-id="30951-1551">**FX_SUCCESS** (0x00) Ficheiros bem sucedidos apagam..</span><span class="sxs-lookup"><span data-stu-id="30951-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="30951-1552">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1553">**FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="30951-1554">**FX_NOT_A_FILE** (0x05) Nome de ficheiro especificado era um diretório ou volume.</span><span class="sxs-lookup"><span data-stu-id="30951-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="30951-1555">**FX_ACCESS_ERROR** ficheiro especificado (0x06) está atualmente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="30951-1556">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1557">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1558">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1559">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1560">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1561">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1562">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1563">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-1564">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-1565">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1566">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1566">Allowed From</span></span>

<span data-ttu-id="30951-1567">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1568">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1569">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1569">See Also</span></span>

- <span data-ttu-id="30951-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1570">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1574">fx_file_close</span></span>
- <span data-ttu-id="30951-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1575">fx_file_create</span></span>
- <span data-ttu-id="30951-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1583">fx_file_open</span></span>
- <span data-ttu-id="30951-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1584">fx_file_read</span></span>
- <span data-ttu-id="30951-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1586">fx_file_rename</span></span>
- <span data-ttu-id="30951-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1587">fx_file_seek</span></span>
- <span data-ttu-id="30951-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1588">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1590">fx_file_write</span></span>
- <span data-ttu-id="30951-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="30951-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="30951-1597">Aloca espaço para um ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1598">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="30951-1599">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1599">Description</span></span>

<span data-ttu-id="30951-1600">Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="30951-1601">O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="30951-1602">O resultado é então arredondado para todo o cluster seguinte.</span><span class="sxs-lookup"><span data-stu-id="30951-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="30951-1603">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1604">O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite ao chamador pré-alocar o espaço para além da gama de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1605">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1605">Input Parameters</span></span>

- <span data-ttu-id="30951-1606">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1607">**tamanho**: Número de bytes a atribuir para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1608">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1608">Return Values</span></span>

- <span data-ttu-id="30951-1609">**FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="30951-1610">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1611">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1612">**FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.</span><span class="sxs-lookup"><span data-stu-id="30951-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="30951-1613">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1614">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1615">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1616">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1617">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1618">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1619">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1620">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1621">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1621">Allowed From</span></span>

<span data-ttu-id="30951-1622">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1623">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1624">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1624">See Also</span></span>

- <span data-ttu-id="30951-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1625">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1629">fx_file_close</span></span>
- <span data-ttu-id="30951-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1630">fx_file_create</span></span>
- <span data-ttu-id="30951-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1632">fx_file_delete</span></span>
- <span data-ttu-id="30951-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1638">fx_file_open</span></span>
- <span data-ttu-id="30951-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1639">fx_file_read</span></span>
- <span data-ttu-id="30951-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1641">fx_file_rename</span></span>
- <span data-ttu-id="30951-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1642">fx_file_seek</span></span>
- <span data-ttu-id="30951-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1643">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1645">fx_file_write</span></span>
- <span data-ttu-id="30951-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="30951-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="30951-1652">Melhor esforço para alocar espaço para um arquivo</span><span class="sxs-lookup"><span data-stu-id="30951-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1653">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="30951-1654">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1654">Description</span></span>

<span data-ttu-id="30951-1655">Este serviço atribui e liga um ou mais aglomerados contíguos ao fim do ficheiro especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="30951-1656">O FileX determina o número de clusters necessários dividindo o tamanho solicitado pelo número de bytes por cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="30951-1657">O resultado é então arredondado para todo o cluster seguinte.</span><span class="sxs-lookup"><span data-stu-id="30951-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="30951-1658">Se não houver aglomerados consecutivos suficientes disponíveis nos meios de comunicação, este serviço liga o maior bloco disponível de clusters consecutivos ao ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="30951-1659">A quantidade de espaço efetivamente alocada ao ficheiro é devolvida ao autor da chamada.</span><span class="sxs-lookup"><span data-stu-id="30951-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="30951-1660">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1661">O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite ao chamador pré-alocar o espaço para além da gama de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1662">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1662">Input Parameters</span></span>

- <span data-ttu-id="30951-1663">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1664">**tamanho**: Número de bytes a atribuir para o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1665">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1665">Return Values</span></span>

- <span data-ttu-id="30951-1666">**FX_SUCCESS** (0x00) Atribuição de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="30951-1667">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1668">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1669">**FX_NO_MORE_SPACE** (0x0A) Os meios de comunicação associados a este ficheiro não dispõem de clusters suficientes.</span><span class="sxs-lookup"><span data-stu-id="30951-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="30951-1670">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1671">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1672">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1673">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1674">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1675">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1676">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1677">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1678">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1678">Allowed From</span></span>

<span data-ttu-id="30951-1679">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1680">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1681">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1681">See Also</span></span>

- <span data-ttu-id="30951-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1682">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1686">fx_file_close</span></span>
- <span data-ttu-id="30951-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1687">fx_file_create</span></span>
- <span data-ttu-id="30951-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1689">fx_file_delete</span></span>
- <span data-ttu-id="30951-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1695">fx_file_open</span></span>
- <span data-ttu-id="30951-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1696">fx_file_read</span></span>
- <span data-ttu-id="30951-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1698">fx_file_rename</span></span>
- <span data-ttu-id="30951-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1699">fx_file_seek</span></span>
- <span data-ttu-id="30951-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1700">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1702">fx_file_write</span></span>
- <span data-ttu-id="30951-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="30951-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="30951-1709">Posições para um byte relativo offset</span><span class="sxs-lookup"><span data-stu-id="30951-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1710">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="30951-1711">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1711">Description</span></span>

<span data-ttu-id="30951-1712">Este serviço posiciona o ponteiro interno de leitura/escrita para o byte relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="30951-1713">Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="30951-1714">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1715">O parâmetro *byte_offset* tem um valor inteiro de 64bit, o que permite ao ouvinte reposicionar o ponteiro de leitura/escrita para além da gama de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-1716">*Se a operação de procura tentar passar o fim do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado até ao fim do ficheiro. Inversamente, se a operação de procura tentar posicionar-se após o início do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado para o início do ficheiro.*</span><span class="sxs-lookup"><span data-stu-id="30951-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1717">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1717">Input Parameters</span></span>

- <span data-ttu-id="30951-1718">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1719">**byte_offset**: Byte relativo desejado compensado em ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="30951-1720">**seek_from**: A direção e o local de onde realizar o parente procuram.</span><span class="sxs-lookup"><span data-stu-id="30951-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="30951-1721">As opções de procura válidas são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="30951-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="30951-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="30951-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="30951-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="30951-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="30951-1725">FX_SEEK_BACK (0x03) Se FX_SEEK_BEGIN for especificada, a operação seek é realizada desde o início do processo.</span><span class="sxs-lookup"><span data-stu-id="30951-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="30951-1726">Se FX_SEEK_END for especificado, a operação seek é efetuada para trás a partir da extremidade do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="30951-1727">Se FX_SEEK_FORWARD for especificado, a operação seek é executada para a frente a partir da posição atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="30951-1728">Se FX_SEEK_BACK for especificado, a operação seek é efetuada para trás a partir da posição atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1729">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1729">Return Values</span></span>

- <span data-ttu-id="30951-1730">**FX_SUCCESS** (0x00) Procura de arquivos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="30951-1731">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1732">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1733">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1734">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1735">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1736">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1737">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1738">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1738">Allowed From</span></span>

<span data-ttu-id="30951-1739">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1740">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1741">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1741">See Also</span></span>

- <span data-ttu-id="30951-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1742">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1746">fx_file_close</span></span>
- <span data-ttu-id="30951-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1747">fx_file_create</span></span>
- <span data-ttu-id="30951-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1749">fx_file_delete</span></span>
- <span data-ttu-id="30951-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1755">fx_file_open</span></span>
- <span data-ttu-id="30951-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1756">fx_file_read</span></span>
- <span data-ttu-id="30951-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1758">fx_file_rename</span></span>
- <span data-ttu-id="30951-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1759">fx_file_seek</span></span>
- <span data-ttu-id="30951-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1760">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1762">fx_file_write</span></span>
- <span data-ttu-id="30951-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="30951-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="30951-1769">Posições para byte offset</span><span class="sxs-lookup"><span data-stu-id="30951-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1770">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="30951-1771">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1771">Description</span></span>

<span data-ttu-id="30951-1772">Este serviço posiciona o ponteiro interno de leitura/escrita para o byte especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="30951-1773">Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="30951-1774">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1775">O parâmetro *byte_offset* tem um valor inteiro de 64bit, o que permite ao ouvinte reposicionar o ponteiro de leitura/escrita para além da gama de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1776">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1776">Input Parameters</span></span>

- <span data-ttu-id="30951-1777">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-1778">**byte_offset**: Byte byte offset em ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="30951-1779">Um valor de zero posicionará o ponteiro de leitura/escrita no início do ficheiro, enquanto um valor superior ao tamanho do ficheiro posicionará o ponteiro de leitura/escrita no final do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1780">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1780">Return Values</span></span>

- <span data-ttu-id="30951-1781">**FX_SUCCESS** (0x00) Procura de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="30951-1782">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-1783">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1784">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1785">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1786">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1787">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1788">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1789">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1789">Allowed From</span></span>

<span data-ttu-id="30951-1790">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1791">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1792">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1792">See Also</span></span>

- <span data-ttu-id="30951-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1793">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1797">fx_file_close</span></span>
- <span data-ttu-id="30951-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1798">fx_file_create</span></span>
- <span data-ttu-id="30951-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1800">fx_file_delete</span></span>
- <span data-ttu-id="30951-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1806">fx_file_open fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="30951-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1808">fx_file_rename</span></span>
- <span data-ttu-id="30951-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1809">fx_file_seek</span></span>
- <span data-ttu-id="30951-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1810">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1812">fx_file_write</span></span>
- <span data-ttu-id="30951-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="30951-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="30951-1819">Arquivo truncates</span><span class="sxs-lookup"><span data-stu-id="30951-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1820">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="30951-1821">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1821">Description</span></span>

<span data-ttu-id="30951-1822">Este serviço trunca o tamanho do ficheiro para o tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="30951-1823">Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="30951-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="30951-1824">Nenhum dos clusters de meios associados ao ficheiro é libertado.</span><span class="sxs-lookup"><span data-stu-id="30951-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-1825">*Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="30951-1826">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1827">O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite que o chamador opere além da faixa de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1828">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1828">Input Parameters</span></span>

- <span data-ttu-id="30951-1829">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-1830">**tamanho**: Novo tamanho do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1830">**size**: New file size.</span></span> <span data-ttu-id="30951-1831">Bytes passado este novo tamanho de arquivo são descartados.</span><span class="sxs-lookup"><span data-stu-id="30951-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1832">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1832">Return Values</span></span>

- <span data-ttu-id="30951-1833">**FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="30951-1834">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-1835">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1836">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1837">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1838">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1839">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1840">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1841">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="30951-1842">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1843">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1844">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1844">Allowed From</span></span>

<span data-ttu-id="30951-1845">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1846">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1847">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1847">See Also</span></span>

- <span data-ttu-id="30951-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1848">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1852">fx_file_close</span></span>
- <span data-ttu-id="30951-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1853">fx_file_create</span></span>
- <span data-ttu-id="30951-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1855">fx_file_delete</span></span>
- <span data-ttu-id="30951-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1861">fx_file_open</span></span>
- <span data-ttu-id="30951-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1862">fx_file_read</span></span>
- <span data-ttu-id="30951-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1864">fx_file_rename</span></span>
- <span data-ttu-id="30951-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1865">fx_file_seek</span></span>
- <span data-ttu-id="30951-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1866">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1868">fx_file_write</span></span>
- <span data-ttu-id="30951-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="30951-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="30951-1875">Truncates arquivo e liberta cluster(s)</span><span class="sxs-lookup"><span data-stu-id="30951-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1876">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="30951-1877">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1877">Description</span></span>

<span data-ttu-id="30951-1878">Este serviço trunca o tamanho do ficheiro para o tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="30951-1879">Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="30951-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="30951-1880">Ao contrário do ***serviço fx_file_extended_truncate,*** este serviço liberta quaisquer clusters não-reutilizados.</span><span class="sxs-lookup"><span data-stu-id="30951-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-1881">*Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="30951-1882">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-1883">O parâmetro *de tamanho* tem um valor inteiro de 64 bits, o que permite que o chamador opere além da faixa de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1884">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1884">Input Parameters</span></span>

- <span data-ttu-id="30951-1885">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-1886">**tamanho**: Novo tamanho do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1886">**size**: New file size.</span></span> <span data-ttu-id="30951-1887">Bytes passado este novo tamanho de arquivo são descartados.</span><span class="sxs-lookup"><span data-stu-id="30951-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1888">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1888">Return Values</span></span>

- <span data-ttu-id="30951-1889">**FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="30951-1890">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-1891">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-1892">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1893">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-1894">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1895">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-1896">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1897">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1898">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-1899">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-1900">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1901">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1901">Allowed From</span></span>

<span data-ttu-id="30951-1902">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1903">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1904">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1904">See Also</span></span>

- <span data-ttu-id="30951-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1905">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-1909">fx_file_close</span></span>
- <span data-ttu-id="30951-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1910">fx_file_create</span></span>
- <span data-ttu-id="30951-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1912">fx_file_delete</span></span>
- <span data-ttu-id="30951-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1918">fx_file_open</span></span>
- <span data-ttu-id="30951-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1919">fx_file_read</span></span>
- <span data-ttu-id="30951-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1921">fx_file_rename</span></span>
- <span data-ttu-id="30951-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1922">fx_file_seek</span></span>
- <span data-ttu-id="30951-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1923">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1925">fx_file_write</span></span>
- <span data-ttu-id="30951-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="30951-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-1931">fx_file_open</span></span>

<span data-ttu-id="30951-1932">Abre o ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1933">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="30951-1934">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1934">Description</span></span>

<span data-ttu-id="30951-1935">Este serviço abre o ficheiro especificado para leitura ou escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="30951-1936">Um ficheiro pode ser aberto para leitura várias vezes, enquanto um ficheiro só pode ser aberto para escrita uma vez até que o escritor feche o ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-1937">*Deve ter-se cuidado se um ficheiro estiver simultaneamente aberto para leitura e escrita. A escrita de ficheiros executada quando um ficheiro é aberto simultaneamente para leitura pode não ser visto pelo leitor, a menos que o leitor feche e reabra o ficheiro para leitura. Da mesma forma, o autor do ficheiro deve ter cuidado ao utilizar os serviços de truncato de ficheiros. Se um ficheiro for truncado pelo escritor, os leitores do mesmo ficheiro podem devolver dados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-1938">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-1938">Input Parameters</span></span>

- <span data-ttu-id="30951-1939">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-1940">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-1941">**file_name**: Pontear o nome do ficheiro a abrir (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="30951-1942">**open_type:** Tipo de ficheiro aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="30951-1943">As opções de tipo aberto válido são:</span><span class="sxs-lookup"><span data-stu-id="30951-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="30951-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="30951-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="30951-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="30951-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="30951-1947">Abrir ficheiros com FX_OPEN_FOR_READ e FX_OPEN_FOR_READ_FAST é semelhante:</span><span class="sxs-lookup"><span data-stu-id="30951-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="30951-1948">FX_OPEN_FOR_READ inclui a verificação de que a lista ligada de clusters que compõem o ficheiro está intacta, e FX_OPEN_FOR_READ_FAST não efetua esta verificação, o que o torna mais rápido.</span><span class="sxs-lookup"><span data-stu-id="30951-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-1949">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-1949">Return Values</span></span>

- <span data-ttu-id="30951-1950">**FX_SUCCESS** (0x00) Arquivo bem sucedido aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="30951-1951">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-1952">**FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="30951-1953">**FX_NOT_A_FILE** (0x05) Nome de ficheiro especificado era um diretório ou volume.</span><span class="sxs-lookup"><span data-stu-id="30951-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="30951-1954">**FX_FILE_CORRUPT** (0x08) Ficheiro especificado é corrupto e o ficheiro aberto falhou.</span><span class="sxs-lookup"><span data-stu-id="30951-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="30951-1955">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado já está aberto ou o tipo aberto é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="30951-1956">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-1957">**FX_MEDIA_INVALID** (0x02) Meios de comunicação inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="30951-1958">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-1959">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-1960">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-1961">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.</span><span class="sxs-lookup"><span data-stu-id="30951-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="30951-1962">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="30951-1963">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-1964">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-1964">Allowed From</span></span>

<span data-ttu-id="30951-1965">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-1966">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="30951-1967">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-1967">See Also</span></span>

- <span data-ttu-id="30951-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1968">fx_file_allocate</span></span>
- <span data-ttu-id="30951-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1972">fx_file_close fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="30951-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-1974">fx_file_delete</span></span>
- <span data-ttu-id="30951-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1981">fx_file_read</span></span>
- <span data-ttu-id="30951-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1983">fx_file_rename</span></span>
- <span data-ttu-id="30951-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-1984">fx_file_seek</span></span>
- <span data-ttu-id="30951-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-1985">fx_file_truncate</span></span>
- <span data-ttu-id="30951-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-1987">fx_file_write</span></span>
- <span data-ttu-id="30951-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="30951-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-1993">fx_file_read</span></span>

<span data-ttu-id="30951-1994">Lê bytes a partir de arquivo</span><span class="sxs-lookup"><span data-stu-id="30951-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-1995">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="30951-1996">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-1996">Description</span></span>

<span data-ttu-id="30951-1997">Este serviço lê bytes do ficheiro e armazena-os no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="30951-1998">Depois de concluída a leitura, o ponteiro de leitura interno do ficheiro é ajustado para apontar para o byte seguinte no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="30951-1999">Se houver menos bytes restantes no pedido, apenas os bytes restantes são armazenados no tampão.</span><span class="sxs-lookup"><span data-stu-id="30951-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="30951-2000">Em todo o caso, o número total de bytes colocados no tampão é devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="30951-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2001">*O pedido deve assegurar que o tampão fornecido seja capaz de armazenar o número especificado de bytes solicitados.*</span><span class="sxs-lookup"><span data-stu-id="30951-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2002">*O desempenho mais rápido é alcançado se o tampão de destino estiver num limite de palavras longas e o tamanho solicitado for uniformemente divisível por tamanhos de **(ULONG).***</span><span class="sxs-lookup"><span data-stu-id="30951-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2003">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2003">Input Parameters</span></span>

- <span data-ttu-id="30951-2004">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-2005">**buffer_ptr**: Ponter para o tampão de destino para a leitura.</span><span class="sxs-lookup"><span data-stu-id="30951-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="30951-2006">**request_size**: Número máximo de bytes para ler.</span><span class="sxs-lookup"><span data-stu-id="30951-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="30951-2007">**atual_size**: Pontear para a variável para manter o número real de bytes lidos no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2008">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2008">Return Values</span></span>

- <span data-ttu-id="30951-2009">**FX_SUCCESS** (0x00) Leitura de ficheiro bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="30951-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="30951-2010">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-2011">**FX_FILE_CORRUPT** ficheiro especificado (0x08) é corrupto e a leitura falhou.</span><span class="sxs-lookup"><span data-stu-id="30951-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="30951-2012">**FX_END_OF_FILE** (0x09) O fim do ficheiro foi alcançado.</span><span class="sxs-lookup"><span data-stu-id="30951-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="30951-2013">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2014">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-2015">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2016">**FX_PTR_ERROR** (0x18) Ficheiro inválido ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="30951-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="30951-2017">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2018">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2018">Allowed From</span></span>

<span data-ttu-id="30951-2019">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2020">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="30951-2021">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2021">See Also</span></span>

- <span data-ttu-id="30951-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="30951-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="30951-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="30951-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="30951-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="30951-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="30951-2026">fx_file_close,</span></span>
- <span data-ttu-id="30951-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="30951-2027">fx_file_create,</span></span>
- <span data-ttu-id="30951-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="30951-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="30951-2029">fx_file_delete,</span></span>
- <span data-ttu-id="30951-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="30951-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="30951-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="30951-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="30951-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="30951-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="30951-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="30951-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="30951-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="30951-2036">fx_file_open,</span></span>
- <span data-ttu-id="30951-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="30951-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="30951-2038">fx_file_rename,</span></span>
- <span data-ttu-id="30951-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2039">fx_file_seek,</span></span>
- <span data-ttu-id="30951-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="30951-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="30951-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="30951-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="30951-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="30951-2042">fx_file_write,</span></span>
- <span data-ttu-id="30951-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="30951-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="30951-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="30951-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="30951-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="30951-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="30951-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="30951-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="30951-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="30951-2049">Posições para um byte relativo offset</span><span class="sxs-lookup"><span data-stu-id="30951-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2050">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="30951-2051">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2051">Description</span></span>

<span data-ttu-id="30951-2052">Este serviço posiciona o ponteiro interno de leitura/escrita para o byte relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="30951-2053">Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-2054">*Se a operação de procura tentar passar o fim do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado até ao fim do ficheiro. Inversamente, se a operação de procura tentar posicionar-se após o início do ficheiro, o ponteiro de leitura/escrita do ficheiro é posicionado para o início do ficheiro.*</span><span class="sxs-lookup"><span data-stu-id="30951-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="30951-2055">Para procurar com um valor compensado para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="30951-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2056">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2056">Input Parameters</span></span>

- <span data-ttu-id="30951-2057">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-2058">**byte_offset**: Byte relativo desejado compensado em ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="30951-2059">**seek_from**: A direção e o local de onde realizar o parente procuram.</span><span class="sxs-lookup"><span data-stu-id="30951-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="30951-2060">As opções de procura válidas são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="30951-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="30951-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="30951-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="30951-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="30951-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="30951-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="30951-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="30951-2065">Se FX_SEEK_BEGIN for especificada, a operação seek é realizada desde o início do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="30951-2066">Se FX_SEEK_END for especificado, a operação seek é efetuada para trás a partir da extremidade do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="30951-2067">Se FX_SEEK_FORWARD for especificado, a operação seek é executada para a frente a partir da posição atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="30951-2068">Se FX_SEEK_BACK for especificado, a operação seek é efetuada para trás a partir da posição atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2069">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2069">Return Values</span></span>

- <span data-ttu-id="30951-2070">**FX_SUCCESS** (0x00) Procura de arquivos bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="30951-2071">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-2072">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2073">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2074">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2075">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-2076">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-2077">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2078">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2078">Allowed From</span></span>

<span data-ttu-id="30951-2079">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2080">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="30951-2081">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2081">See Also</span></span>

- <span data-ttu-id="30951-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2082">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2086">fx_file_close</span></span>
- <span data-ttu-id="30951-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2087">fx_file_create</span></span>
- <span data-ttu-id="30951-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2089">fx_file_delete</span></span>
- <span data-ttu-id="30951-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2096">fx_file_open</span></span>
- <span data-ttu-id="30951-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2097">fx_file_read</span></span>
- <span data-ttu-id="30951-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2098">fx_file_rename</span></span>
- <span data-ttu-id="30951-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2099">fx_file_seek</span></span>
- <span data-ttu-id="30951-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2100">fx_file_truncate</span></span>
- <span data-ttu-id="30951-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2102">fx_file_write</span></span>
- <span data-ttu-id="30951-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="30951-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2108">fx_file_rename</span></span>

<span data-ttu-id="30951-2109">Arquivo de renomes</span><span class="sxs-lookup"><span data-stu-id="30951-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2110">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="30951-2111">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2111">Description</span></span>

<span data-ttu-id="30951-2112">Este serviço altera o nome do ficheiro especificado por *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="30951-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="30951-2113">O renomeamento também é feito em relação ao caminho especificado ou ao caminho padrão.</span><span class="sxs-lookup"><span data-stu-id="30951-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="30951-2114">Se um caminho for especificado no nome do novo ficheiro, o ficheiro renomeado é efetivamente movido para o caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="30951-2115">Se não for especificado nenhum caminho, o ficheiro renomeado é colocado na trajetória predefinida atual.</span><span class="sxs-lookup"><span data-stu-id="30951-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2116">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2116">Input Parameters</span></span>

- <span data-ttu-id="30951-2117">**media_ptr**: Ponteiro para um bloco de controlo de meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="30951-2118">**old_file_name**: Ponter o nome do ficheiro para renomear (o caminho do diretório é opcional).</span><span class="sxs-lookup"><span data-stu-id="30951-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="30951-2119">**new_file_name**: Ponter para o novo nome do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="30951-2120">O caminho do diretório não é permitido.</span><span class="sxs-lookup"><span data-stu-id="30951-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2121">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2121">Return Values</span></span>

- <span data-ttu-id="30951-2122">**FX_SUCCESS** (0x00) Rebatizador de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="30951-2123">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2124">**FX_NOT_FOUND** (0x04) Ficheiro especificado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="30951-2125">**FX_NOT_A_FILE** (0x05) Ficheiro especificado é um diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="30951-2126">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado já está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="30951-2127">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2128">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="30951-2129">**FX_INVALID_NAME** (0x0C) O nome de novo ficheiro especificado não é um nome de ficheiro válido.</span><span class="sxs-lookup"><span data-stu-id="30951-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="30951-2130">**FX_INVALID_PATH** caminho (0x0D) é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="30951-2131">**FX_ALREADY_CREATED** (0x0B) O novo nome do ficheiro é utilizado.</span><span class="sxs-lookup"><span data-stu-id="30951-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="30951-2132">**FX_MEDIA_INVALID** (0x02) Os meios de comunicação são inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="30951-2133">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2134">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2135">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-2136">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-2137">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="30951-2138">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-2139">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2140">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2140">Allowed From</span></span>

<span data-ttu-id="30951-2141">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="30951-2143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2143">See Also</span></span>

- <span data-ttu-id="30951-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2144">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2148">fx_file_close</span></span>
- <span data-ttu-id="30951-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2149">fx_file_create</span></span>
- <span data-ttu-id="30951-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2151">fx_file_delete</span></span>
- <span data-ttu-id="30951-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2158">fx_file_open</span></span>
- <span data-ttu-id="30951-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2159">fx_file_read</span></span>
- <span data-ttu-id="30951-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2161">fx_file_seek</span></span>
- <span data-ttu-id="30951-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2162">fx_file_truncate</span></span>
- <span data-ttu-id="30951-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2164">fx_file_write</span></span>
- <span data-ttu-id="30951-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="30951-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2170">fx_file_seek</span></span>

<span data-ttu-id="30951-2171">Posições para byte offset</span><span class="sxs-lookup"><span data-stu-id="30951-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2172">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="30951-2173">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2173">Description</span></span>

<span data-ttu-id="30951-2174">Este serviço posiciona o ponteiro interno de leitura/escrita para o byte especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="30951-2175">Qualquer pedido de leitura ou escrita subsequente começará neste local no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="30951-2176">Para procurar com um valor compensado para além de 4GB, a aplicação utilizará o serviço *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="30951-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2177">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2177">Input Parameters</span></span>

- <span data-ttu-id="30951-2178">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-2179">**byte_offset**: Byte byte offset em ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="30951-2180">Um valor de zero posicionará o ponteiro de leitura/escrita no início do ficheiro, enquanto um valor superior ao tamanho do ficheiro posicionará o ponteiro de leitura/escrita no final do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2181">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2181">Return Values</span></span>

- <span data-ttu-id="30951-2182">**FX_SUCCESS** (0x00) Procura de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="30951-2183">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-2184">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2185">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2186">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2187">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-2188">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-2189">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2190">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2190">Allowed From</span></span>

<span data-ttu-id="30951-2191">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="30951-2193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2193">See Also</span></span>

- <span data-ttu-id="30951-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2194">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2198">fx_file_close</span></span>
- <span data-ttu-id="30951-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2199">fx_file_create</span></span>
- <span data-ttu-id="30951-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2201">fx_file_delete</span></span>
- <span data-ttu-id="30951-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2208">fx_file_open</span></span>
- <span data-ttu-id="30951-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2209">fx_file_read</span></span>
- <span data-ttu-id="30951-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2210">fx_file_rename</span></span>
- <span data-ttu-id="30951-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2211">fx_file_seek</span></span>
- <span data-ttu-id="30951-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2212">fx_file_truncate</span></span>
- <span data-ttu-id="30951-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2214">fx_file_write</span></span>
- <span data-ttu-id="30951-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="30951-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2220">fx_file_truncate</span></span>

<span data-ttu-id="30951-2221">Arquivo truncates</span><span class="sxs-lookup"><span data-stu-id="30951-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2222">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="30951-2223">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2223">Description</span></span>

<span data-ttu-id="30951-2224">Este serviço trunca o tamanho do ficheiro para o tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="30951-2225">Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="30951-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="30951-2226">Nenhum dos clusters de meios associados ao ficheiro é libertado.</span><span class="sxs-lookup"><span data-stu-id="30951-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2227">*Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="30951-2228">Para operar além de 4GB, a aplicação deve utilizar o serviço *fx_file_extended_truncate*.</span><span class="sxs-lookup"><span data-stu-id="30951-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2229">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2229">Input Parameters</span></span>

- <span data-ttu-id="30951-2230">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-2231">**tamanho**: Novo tamanho do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2231">**size**: New file size.</span></span> <span data-ttu-id="30951-2232">Bytes passado este novo tamanho de arquivo são descartados.</span><span class="sxs-lookup"><span data-stu-id="30951-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2233">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2233">Return Values</span></span>

- <span data-ttu-id="30951-2234">**FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="30951-2235">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-2236">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-2237">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2238">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-2239">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2240">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2241">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-2242">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação</span><span class="sxs-lookup"><span data-stu-id="30951-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="30951-2243">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-2244">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2245">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2245">Allowed From</span></span>

<span data-ttu-id="30951-2246">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2247">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="30951-2248">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2248">See Also</span></span>

- <span data-ttu-id="30951-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2249">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2253">fx_file_close</span></span>
- <span data-ttu-id="30951-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2254">fx_file_create</span></span>
- <span data-ttu-id="30951-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2256">fx_file_delete</span></span>
- <span data-ttu-id="30951-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2263">fx_file_open</span></span>
- <span data-ttu-id="30951-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2264">fx_file_read</span></span>
- <span data-ttu-id="30951-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2266">fx_file_rename</span></span>
- <span data-ttu-id="30951-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2267">fx_file_seek</span></span>
- <span data-ttu-id="30951-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2269">fx_file_write</span></span>
- <span data-ttu-id="30951-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="30951-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="30951-2276">Truncates arquivo e liberta cluster(s)</span><span class="sxs-lookup"><span data-stu-id="30951-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2277">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="30951-2278">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2278">Description</span></span>

<span data-ttu-id="30951-2279">Este serviço trunca o tamanho do ficheiro para o tamanho especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="30951-2280">Se o tamanho fornecido for maior do que o tamanho real do ficheiro, este serviço não faz nada.</span><span class="sxs-lookup"><span data-stu-id="30951-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="30951-2281">Ao contrário do ***serviço fx_file_truncate,*** este serviço liberta quaisquer clusters não-reutilizados.</span><span class="sxs-lookup"><span data-stu-id="30951-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2282">*Tenha cuidado com os ficheiros truncados que também podem estar abertos simultaneamente para leitura. Truncar um ficheiro também aberto para leitura pode resultar na leitura de dados inválidos.*</span><span class="sxs-lookup"><span data-stu-id="30951-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="30951-2283">Para operar além de 4GB, a aplicação deve utilizar o serviço *fx_file_extended_truncate_release*.</span><span class="sxs-lookup"><span data-stu-id="30951-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2284">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2284">Input Parameters</span></span>

- <span data-ttu-id="30951-2285">**file_ptr**: Ponter para um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="30951-2286">**tamanho**: Novo tamanho do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2286">**size**: New file size.</span></span> <span data-ttu-id="30951-2287">Bytes passado este novo tamanho de arquivo são descartados.</span><span class="sxs-lookup"><span data-stu-id="30951-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2288">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2288">Return Values</span></span>

- <span data-ttu-id="30951-2289">**FX_SUCCESS** (0x00) Truncado de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="30951-2290">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-2291">**FX_NOT_OPEN** ficheiro especificado (0x07) não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="30951-2292">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="30951-2293">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação subjacentes estão protegidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="30951-2294">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="30951-2295">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2296">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-2297">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-2298">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço para completar a operação.</span><span class="sxs-lookup"><span data-stu-id="30951-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="30951-2299">**FX_PTR_ERROR** (0x18) Ponteiro de ficheiros inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="30951-2300">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2301">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2301">Allowed From</span></span>

<span data-ttu-id="30951-2302">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2303">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="30951-2304">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2304">See Also</span></span>

- <span data-ttu-id="30951-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2305">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2309">fx_file_close</span></span>
- <span data-ttu-id="30951-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2310">fx_file_create</span></span>
- <span data-ttu-id="30951-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2312">fx_file_delete</span></span>
- <span data-ttu-id="30951-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2319">fx_file_open</span></span>
- <span data-ttu-id="30951-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2320">fx_file_read</span></span>
- <span data-ttu-id="30951-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2322">fx_file_rename</span></span>
- <span data-ttu-id="30951-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2323">fx_file_seek</span></span>
- <span data-ttu-id="30951-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2324">fx_file_truncate</span></span>
- <span data-ttu-id="30951-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2325">fx_file_write</span></span>
- <span data-ttu-id="30951-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="30951-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2331">fx_file_write</span></span>

<span data-ttu-id="30951-2332">Escreve bytes para arquivar</span><span class="sxs-lookup"><span data-stu-id="30951-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2333">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="30951-2334">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2334">Description</span></span>

<span data-ttu-id="30951-2335">Este serviço escreve bytes a partir do tampão especificado a partir da posição atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="30951-2336">Após a gravação estar concluída, o ponteiro de leitura interna do ficheiro é ajustado para apontar para o byte seguinte no ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2337">*O desempenho mais rápido é alcançado se o tampão de origem estiver num limite de palavras longas e o tamanho solicitado for uniformemente divisível por tamanhos de **(ULONG).***</span><span class="sxs-lookup"><span data-stu-id="30951-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2338">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2338">Input Parameters</span></span>

- <span data-ttu-id="30951-2339">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-2340">**buffer_ptr**: Ponter para o tampão de origem para a escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="30951-2341">**tamanho**: Número de bytes para escrever.</span><span class="sxs-lookup"><span data-stu-id="30951-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2342">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2342">Return Values</span></span>

- <span data-ttu-id="30951-2343">**FX_SUCCESS** (0x00) Escrita de ficheiro bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="30951-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="30951-2344">**FX_NOT_OPEN** (0x07) Ficheiro especificado não está aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="30951-2345">**FX_ACCESS_ERROR** (0x06) O ficheiro especificado não está aberto para escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="30951-2346">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço disponível nos meios de comunicação para realizar esta escrita.</span><span class="sxs-lookup"><span data-stu-id="30951-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="30951-2347">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2348">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-2349">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2350">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2351">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a entrada de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="30951-2352">**FX_NO_MORE_ENTRIES** (0x0F) Não há mais entradas de FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="30951-2353">**FX_PTR_ERROR** (0x18) Ficheiro inválido ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="30951-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="30951-2354">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2355">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2355">Allowed From</span></span>

<span data-ttu-id="30951-2356">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2357">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="30951-2358">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2358">See Also</span></span>

- <span data-ttu-id="30951-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="30951-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="30951-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="30951-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="30951-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="30951-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="30951-2363">fx_file_close,</span></span>
- <span data-ttu-id="30951-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="30951-2364">fx_file_create,</span></span>
- <span data-ttu-id="30951-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="30951-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="30951-2366">fx_file_delete,</span></span>
- <span data-ttu-id="30951-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="30951-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="30951-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="30951-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="30951-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="30951-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="30951-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="30951-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="30951-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="30951-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="30951-2373">fx_file_open,</span></span>
- <span data-ttu-id="30951-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="30951-2374">fx_file_read,</span></span>
- <span data-ttu-id="30951-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="30951-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="30951-2376">fx_file_rename,</span></span>
- <span data-ttu-id="30951-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="30951-2377">fx_file_seek,</span></span>
- <span data-ttu-id="30951-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="30951-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="30951-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="30951-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="30951-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="30951-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="30951-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="30951-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="30951-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="30951-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="30951-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="30951-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="30951-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="30951-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="30951-2386">Define a função de notificação de escrita de ficheiro</span><span class="sxs-lookup"><span data-stu-id="30951-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2387">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="30951-2388">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2388">Description</span></span>

<span data-ttu-id="30951-2389">Este serviço instala a função de retorno que é invocada após uma operação de escrita de ficheiros bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="30951-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2390">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2390">Input Parameters</span></span>

- <span data-ttu-id="30951-2391">**file_ptr**: Ponter para o bloco de controlo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="30951-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="30951-2392">**file_write_notify**: Função de reversão de gravação de ficheiro a instalar.</span><span class="sxs-lookup"><span data-stu-id="30951-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="30951-2393">Desativar a função de retorno para NUS desativa a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="30951-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2394">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2394">Return Values</span></span>

- <span data-ttu-id="30951-2395">**FX_SUCCESS** (0x00) instalou com sucesso a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="30951-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="30951-2396">**file_ptr FX_PTR_ERROR** (0x18) é NU.</span><span class="sxs-lookup"><span data-stu-id="30951-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="30951-2397">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2398">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2398">Allowed From</span></span>

<span data-ttu-id="30951-2399">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2400">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="30951-2401">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2401">See Also</span></span>

- <span data-ttu-id="30951-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2402">fx_file_allocate</span></span>
- <span data-ttu-id="30951-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-2406">fx_file_close</span></span>
- <span data-ttu-id="30951-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2407">fx_file_create</span></span>
- <span data-ttu-id="30951-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-2409">fx_file_delete</span></span>
- <span data-ttu-id="30951-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-2416">fx_file_open</span></span>
- <span data-ttu-id="30951-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-2417">fx_file_read</span></span>
- <span data-ttu-id="30951-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2419">fx_file_rename</span></span>
- <span data-ttu-id="30951-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-2420">fx_file_seek</span></span>
- <span data-ttu-id="30951-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-2421">fx_file_truncate</span></span>
- <span data-ttu-id="30951-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-2423">fx_file_write</span></span>
- <span data-ttu-id="30951-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="30951-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2428">fx_media_abort</span></span>

<span data-ttu-id="30951-2429">Aborta atividades mediáticas</span><span class="sxs-lookup"><span data-stu-id="30951-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2430">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2431">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2431">Description</span></span>

<span data-ttu-id="30951-2432">Este serviço aborta todas as atividades atuais associadas aos meios de comunicação, incluindo o encerramento de todos os ficheiros abertos, o envio de um pedido de abortar ao motorista associado e a colocação dos meios de comunicação em estado abortado.</span><span class="sxs-lookup"><span data-stu-id="30951-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="30951-2433">Este serviço é normalmente chamado quando são detetados erros de E/S.</span><span class="sxs-lookup"><span data-stu-id="30951-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2434">*Os meios de comunicação devem ser reabertos para o utilizar novamente após a operação de aborto.*</span><span class="sxs-lookup"><span data-stu-id="30951-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2435">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2435">Input Parameters</span></span>

- <span data-ttu-id="30951-2436">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2437">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2437">Return Values</span></span>

- <span data-ttu-id="30951-2438">**FX_SUCCESS** (0x00) Os meios de comunicação de sucesso abortam.</span><span class="sxs-lookup"><span data-stu-id="30951-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="30951-2439">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2440">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-2441">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2442">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2442">Allowed From</span></span>

<span data-ttu-id="30951-2443">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2444">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2445">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2445">See Also</span></span>

- <span data-ttu-id="30951-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2448">fx_media_check</span></span>
- <span data-ttu-id="30951-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2449">fx_media_close</span></span>
- <span data-ttu-id="30951-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2453">fx_media_flush</span></span>
- <span data-ttu-id="30951-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2454">fx_media_format</span></span>
- <span data-ttu-id="30951-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2455">fx_media_open</span></span>
- <span data-ttu-id="30951-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2457">fx_media_read</span></span>
- <span data-ttu-id="30951-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2458">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2461">fx_media_write</span></span>
- <span data-ttu-id="30951-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="30951-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="30951-2464">Invalida cache do sector lógico</span><span class="sxs-lookup"><span data-stu-id="30951-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2465">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="30951-2466">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2466">Description</span></span>

<span data-ttu-id="30951-2467">Este serviço elimina todos os sectores sujos da cache e, em seguida, invalida toda a cache do sector lógico.</span><span class="sxs-lookup"><span data-stu-id="30951-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2468">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2468">Input Parameters</span></span>

- <span data-ttu-id="30951-2469">**media_ptr**: Ponteiro para o bloco de controlo dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2470">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2470">Return Values</span></span>

- <span data-ttu-id="30951-2471">**FX_SUCCESS** (0x00) Cache de mídia bem sucedida invalida.</span><span class="sxs-lookup"><span data-stu-id="30951-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="30951-2472">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2473">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2474">**FX_PTR_ERROR** (0x18) Media inválidos ou ponteiro de risco.</span><span class="sxs-lookup"><span data-stu-id="30951-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="30951-2475">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2476">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2476">Allowed From</span></span>

<span data-ttu-id="30951-2477">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2478">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2479">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2479">See Also</span></span>

- <span data-ttu-id="30951-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2481">fx_media_abort</span></span>
- <span data-ttu-id="30951-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2482">fx_media_check</span></span>
- <span data-ttu-id="30951-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2483">fx_media_close</span></span>
- <span data-ttu-id="30951-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2487">fx_media_flush</span></span>
- <span data-ttu-id="30951-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2488">fx_media_format</span></span>
- <span data-ttu-id="30951-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2489">fx_media_open</span></span>
- <span data-ttu-id="30951-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2491">fx_media_read</span></span>
- <span data-ttu-id="30951-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2492">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2495">fx_media_write</span></span>
- <span data-ttu-id="30951-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="30951-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2497">fx_media_check</span></span>

<span data-ttu-id="30951-2498">Verifica os erros dos meios de comunicação social</span><span class="sxs-lookup"><span data-stu-id="30951-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2499">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2500">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2500">Description</span></span>

<span data-ttu-id="30951-2501">Este serviço verifica os meios de comunicação especificados para erros estruturais básicos, incluindo ligação cruzada de ficheiros/diretórios, cadeias de GORDURA inválidas e aglomerados perdidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="30951-2502">Este serviço também fornece a capacidade de corrigir erros detetados.</span><span class="sxs-lookup"><span data-stu-id="30951-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="30951-2503">O serviço fx_media_check requer memória de risco para a sua primeira análise de resumos e ficheiros nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="30951-2504">Especificamente, a memória de risco fornecida ao serviço de verificação de meios de comunicação deve ser suficientemente grande para conter várias entradas de diretório, uma estrutura de dados para "empilhar" a posição de entrada do diretório atual antes de entrar em subdiretas e, finalmente, o mapa lógico fat bit.</span><span class="sxs-lookup"><span data-stu-id="30951-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="30951-2505">A memória de risco deve ser pelo menos 512-1024 bytes mais memória para o mapa lógico fat bit, que requer tantos bits quanto há aglomerados nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="30951-2506">Por exemplo, um dispositivo com 8000 clusters exigiria 1000 bytes para representar e, assim, exigiria uma área de risco total na ordem dos bytes de 2048.</span><span class="sxs-lookup"><span data-stu-id="30951-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2507">*Este serviço só deve ser chamado imediatamente após fx_media_open e sem qualquer outra atividade do sistema de ficheiros.*</span><span class="sxs-lookup"><span data-stu-id="30951-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2508">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2508">Input Parameters</span></span>

- <span data-ttu-id="30951-2509">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-2510">**scratch_memory_ptr**: Ponteiro para o início da memória de risco.</span><span class="sxs-lookup"><span data-stu-id="30951-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="30951-2511">**scratch_memory_size:** Tamanho da memória de risco em bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="30951-2512">**error_correction_option**: As bits de opção de correção de erro, quando a broca está definida, é efetuada uma correção de erros.</span><span class="sxs-lookup"><span data-stu-id="30951-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="30951-2513">As bits de correção de erros são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="30951-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="30951-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="30951-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="30951-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="30951-2516">FX_LOST_CLUSTER_ERROR (0x04) Simplesmente OU em conjunto as opções de correção de erros necessárias.</span><span class="sxs-lookup"><span data-stu-id="30951-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="30951-2517">Se não for necessária uma correção de erros, deve ser fornecido um valor de 0.</span><span class="sxs-lookup"><span data-stu-id="30951-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="30951-2518">**errors_detected_ptr**: Destino para bits de deteção de erros, conforme definido abaixo:</span><span class="sxs-lookup"><span data-stu-id="30951-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="30951-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="30951-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="30951-2520">FX_LOST_CLUSTER_ERROR FX_DIRECTORY_ERROR (0x02) (0x04)</span><span class="sxs-lookup"><span data-stu-id="30951-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="30951-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="30951-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2522">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2522">Return Values</span></span>

- <span data-ttu-id="30951-2523">**FX_SUCCESS** (0x00) Verificação bem sucedida dos meios de comunicação social, veja os erros detetados no destino para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="30951-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="30951-2524">**FX_ACCESS_ERROR** (0x06) Não é possível efetuar a verificação com ficheiros abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="30951-2525">**FX_FILE_CORRUPT** ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2526">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2527">**FX_NO_MORE_SPACE** (0x0A) Não há mais espaço nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="30951-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) A memória de risco fornecida não é suficientemente grande.</span><span class="sxs-lookup"><span data-stu-id="30951-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="30951-2529">**FX_ERROR_NOT_FIXED** (0x93) Corrupção de diretório de raiz FAT32 que não foi possível fixar.</span><span class="sxs-lookup"><span data-stu-id="30951-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="30951-2530">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2531">**FX_SECTOR_INVALID** sector (0x89) é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="30951-2532">**FX_PTR_ERROR** (0x18) Media inválidos ou ponteiro de risco.</span><span class="sxs-lookup"><span data-stu-id="30951-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="30951-2533">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="30951-2534">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2534">Allowed From</span></span>

<span data-ttu-id="30951-2535">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2536">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2537">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2537">See Also</span></span>

- <span data-ttu-id="30951-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2539">fx_media_abort</span></span>
- <span data-ttu-id="30951-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2541">fx_media_close</span></span>
- <span data-ttu-id="30951-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2545">fx_media_flush</span></span>
- <span data-ttu-id="30951-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2546">fx_media_format</span></span>
- <span data-ttu-id="30951-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2547">fx_media_open</span></span>
- <span data-ttu-id="30951-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2549">fx_media_read</span></span>
- <span data-ttu-id="30951-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2550">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2553">fx_media_write</span></span>
- <span data-ttu-id="30951-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="30951-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2555">fx_media_close</span></span>

<span data-ttu-id="30951-2556">Fecha os meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2557">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2558">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2558">Description</span></span>

<span data-ttu-id="30951-2559">Este serviço fecha os meios de comunicação especificados.</span><span class="sxs-lookup"><span data-stu-id="30951-2559">This service closes the specified media.</span></span> <span data-ttu-id="30951-2560">No processo de fecho dos meios de comunicação, todos os ficheiros abertos estão fechados e os restantes tampão são lavados para os meios físicos.</span><span class="sxs-lookup"><span data-stu-id="30951-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2561">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2561">Input Parameters</span></span>

- <span data-ttu-id="30951-2562">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2563">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2563">Return Values</span></span>

- <span data-ttu-id="30951-2564">**FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="30951-2565">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2566">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2567">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-2568">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2569">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2569">Allowed From</span></span>

<span data-ttu-id="30951-2570">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2571">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2572">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2572">See Also</span></span>

- <span data-ttu-id="30951-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2574">fx_media_abort</span></span>
- <span data-ttu-id="30951-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2576">fx_media_check</span></span>
- <span data-ttu-id="30951-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2580">fx_media_flush</span></span>
- <span data-ttu-id="30951-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2581">fx_media_format</span></span>
- <span data-ttu-id="30951-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2582">fx_media_open</span></span>
- <span data-ttu-id="30951-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2584">fx_media_read</span></span>
- <span data-ttu-id="30951-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2585">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2588">fx_media_write</span></span>
- <span data-ttu-id="30951-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="30951-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="30951-2591">Define a função de notificação de mídia próxima</span><span class="sxs-lookup"><span data-stu-id="30951-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2592">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="30951-2593">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2593">Description</span></span>

<span data-ttu-id="30951-2594">Este serviço define uma função de chamada de notificação que será invocada após o encerramento de um meio de comunicação com sucesso.</span><span class="sxs-lookup"><span data-stu-id="30951-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2595">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2595">Input Parameters</span></span>

- <span data-ttu-id="30951-2596">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-2597">**media_close_notify**: Os meios de comunicação estão perto notificam a função de chamada a instalar.</span><span class="sxs-lookup"><span data-stu-id="30951-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="30951-2598">Passar NUDIS como a função de retorno desativa a chamada de fecho dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2599">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2599">Return Values</span></span>

- <span data-ttu-id="30951-2600">**FX_SUCCESS** (0x00) instalou com sucesso a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="30951-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="30951-2601">**FX_PTR_ERROR** (0x18) media_ptr é NU.</span><span class="sxs-lookup"><span data-stu-id="30951-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="30951-2602">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2603">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2603">Allowed From</span></span>

<span data-ttu-id="30951-2604">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2605">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="30951-2606">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2606">See Also</span></span>

- <span data-ttu-id="30951-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2608">fx_media_abort</span></span>
- <span data-ttu-id="30951-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2610">fx_media_check</span></span>
- <span data-ttu-id="30951-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2611">fx_media_close</span></span>
- <span data-ttu-id="30951-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2614">fx_media_flush</span></span>
- <span data-ttu-id="30951-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2615">fx_media_format</span></span>
- <span data-ttu-id="30951-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2616">fx_media_open</span></span>
- <span data-ttu-id="30951-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2618">fx_media_read</span></span>
- <span data-ttu-id="30951-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2619">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2622">fx_media_write</span></span>
- <span data-ttu-id="30951-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="30951-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="30951-2625">Meios de forma formatos</span><span class="sxs-lookup"><span data-stu-id="30951-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2626">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="30951-2627">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2627">Description</span></span>

<span data-ttu-id="30951-2628">Este serviço forma os meios fornecidos de forma exFAT compatível com base nos parâmetros fornecidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="30951-2629">Este serviço deve ser chamado antes da abertura dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2630">*A formatação de um meio de comunicação já formatado apaga efetivamente todos os ficheiros e diretórios nos meios de comunicação.*</span><span class="sxs-lookup"><span data-stu-id="30951-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2631">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2631">Input Parameters</span></span>

- <span data-ttu-id="30951-2632">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2632">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="30951-2633">Isto é utilizado apenas para fornecer algumas informações básicas necessárias para o condutor operar.</span><span class="sxs-lookup"><span data-stu-id="30951-2633">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="30951-2634">**condutor**: Pontear o controlador de I/S para este meio de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2634">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="30951-2635">Este será normalmente o mesmo condutor fornecido à chamada fx_media_open subsequente.</span><span class="sxs-lookup"><span data-stu-id="30951-2635">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="30951-2636">**driver_info_ptr**: Pontear para informações opcionais que o condutor de E/S pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="30951-2636">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="30951-2637">**memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2637">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="30951-2638">memory_size Especifica o tamanho da memória dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2638">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="30951-2639">O tamanho deve ser pelo menos tão grande quanto o tamanho do sector dos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2639">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="30951-2640">**volume_name**: Pontear para a cadeia de nomes de volume, que é um máximo de 11 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-2640">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="30951-2641">**number_of_fats**: Número de FATs nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2641">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="30951-2642">A implementação atual suporta uma FAT nos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2642">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="30951-2643">**hidden_sectors**: Número de sectores escondidos antes do sector de arranque destes meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2643">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="30951-2644">Isto é típico quando várias divisórias estão presentes.</span><span class="sxs-lookup"><span data-stu-id="30951-2644">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="30951-2645">**total_sectors**: Número total de sectores nos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2645">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="30951-2646">**bytes_per_sector**: Número de bytes por sector, que é tipicamente 512.</span><span class="sxs-lookup"><span data-stu-id="30951-2646">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="30951-2647">FileX requer que este seja um múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="30951-2647">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="30951-2648">**sectors_per_cluster**: Número de sectores em cada cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-2648">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="30951-2649">O cluster é a unidade de atribuição mínima num sistema de ficheiros FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2649">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="30951-2650">**volumne_serial_number:** Número de série a utilizar para este volume.</span><span class="sxs-lookup"><span data-stu-id="30951-2650">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="30951-2651">**boundary_unit**: Dimensão do alinhamento da área dos dados físicos, em número de sectores.</span><span class="sxs-lookup"><span data-stu-id="30951-2651">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2652">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2652">Return Values</span></span>

- <span data-ttu-id="30951-2653">**FX_SUCCESS** (0x00) Formato de mídia bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-2653">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="30951-2654">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2654">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2655">**FX_PTR_ERROR** (0x18) Meios de comunicação, controlador ou ponteiro de memória inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2655">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="30951-2656">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2656">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2657">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2657">Allowed From</span></span>

<span data-ttu-id="30951-2658">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2658">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2659">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2659">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2660">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2660">See Also</span></span>

- <span data-ttu-id="30951-2661">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2661">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2662">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2662">fx_media_abort</span></span>
- <span data-ttu-id="30951-2663">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2663">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2664">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2664">fx_media_check</span></span>
- <span data-ttu-id="30951-2665">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2665">fx_media_close</span></span>
- <span data-ttu-id="30951-2666">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2666">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2667">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2667">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2668">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2668">fx_media_flush</span></span>
- <span data-ttu-id="30951-2669">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2669">fx_media_format</span></span>
- <span data-ttu-id="30951-2670">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2670">fx_media_open</span></span>
- <span data-ttu-id="30951-2671">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2671">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2672">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2672">fx_media_read</span></span>
- <span data-ttu-id="30951-2673">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2673">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2674">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2674">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2675">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2675">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2676">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2676">fx_media_write</span></span>
- <span data-ttu-id="30951-2677">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2677">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="30951-2678">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2678">fx_media_extended_space_available</span></span>

<span data-ttu-id="30951-2679">Devolve espaço de mídia disponível</span><span class="sxs-lookup"><span data-stu-id="30951-2679">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2680">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2680">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2681">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2681">Description</span></span>

<span data-ttu-id="30951-2682">Este serviço devolve o número de bytes disponíveis nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2682">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="30951-2683">Este serviço foi concebido para exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2683">This service is designed for exFAT.</span></span> <span data-ttu-id="30951-2684">O ponteiro para *available_bytes* parâmetro tem um valor inteiro de 64 bits, o que permite ao ouvinte trabalhar com meios para além da gama de 4GB.</span><span class="sxs-lookup"><span data-stu-id="30951-2684">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2685">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2685">Input Parameters</span></span>

- <span data-ttu-id="30951-2686">**media_ptr**: Ponter para um meio de comunicação previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2686">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="30951-2687">**available_bytes_ptr**: Bytes disponíveis deixados nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2687">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2688">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2688">Return Values</span></span>

- <span data-ttu-id="30951-2689">**FX_SUCCESS** (0x00) recuperou com sucesso o espaço disponível nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2689">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="30951-2690">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2690">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2691">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido ou ponteiro bytes disponível é NU.</span><span class="sxs-lookup"><span data-stu-id="30951-2691">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="30951-2692">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2692">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2693">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2693">Allowed From</span></span>

<span data-ttu-id="30951-2694">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2694">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2695">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2695">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="30951-2696">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2696">See Also</span></span>

- <span data-ttu-id="30951-2697">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2697">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2698">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2698">fx_media_abort</span></span>
- <span data-ttu-id="30951-2699">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2699">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2700">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2700">fx_media_check</span></span>
- <span data-ttu-id="30951-2701">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2701">fx_media_close</span></span>
- <span data-ttu-id="30951-2702">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2702">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2703">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2703">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2704">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2704">fx_media_flush</span></span>
- <span data-ttu-id="30951-2705">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2705">fx_media_format</span></span>
- <span data-ttu-id="30951-2706">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2706">fx_media_open</span></span>
- <span data-ttu-id="30951-2707">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2707">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2708">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2708">fx_media_read</span></span>
- <span data-ttu-id="30951-2709">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2709">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2710">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2710">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2711">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2711">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2712">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2712">fx_media_write</span></span>
- <span data-ttu-id="30951-2713">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2713">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="30951-2714">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2714">fx_media_flush</span></span>

<span data-ttu-id="30951-2715">Flushes dados para meios físicos</span><span class="sxs-lookup"><span data-stu-id="30951-2715">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2716">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2716">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2717">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2717">Description</span></span>

<span data-ttu-id="30951-2718">Este serviço elimina todos os sectores em cache e entradas de diretórios de quaisquer ficheiros modificados para os meios físicos.</span><span class="sxs-lookup"><span data-stu-id="30951-2718">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2719">*Esta rotina pode ser chamada periodicamente pelo pedido para reduzir o risco de corrupção de ficheiros e/ou perda de dados em caso de perda súbita de poder no alvo.*</span><span class="sxs-lookup"><span data-stu-id="30951-2719">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2720">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2720">Input Parameters</span></span>

- <span data-ttu-id="30951-2721">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2721">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2722">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2722">Return Values</span></span>

- <span data-ttu-id="30951-2723">**FX_SUCCESS** (0x00) Flush de mídia bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="30951-2723">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="30951-2724">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2724">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2725">**FX_FILE_CORRUPT**    ficheiro (0x08) é corrompido.</span><span class="sxs-lookup"><span data-stu-id="30951-2725">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="30951-2726">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2726">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2727">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2727">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2728">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-2728">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-2729">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2729">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-2730">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2730">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2731">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2731">Allowed From</span></span>

<span data-ttu-id="30951-2732">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2733">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2733">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2734">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2734">See Also</span></span>

- <span data-ttu-id="30951-2735">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2735">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2736">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2736">fx_media_abort</span></span>
- <span data-ttu-id="30951-2737">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2737">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2738">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2738">fx_media_check</span></span>
- <span data-ttu-id="30951-2739">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2739">fx_media_close</span></span>
- <span data-ttu-id="30951-2740">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2740">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2741">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2741">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2742">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2742">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2743">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2743">fx_media_format</span></span>
- <span data-ttu-id="30951-2744">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2744">fx_media_open</span></span>
- <span data-ttu-id="30951-2745">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2745">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2746">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2746">fx_media_read</span></span>
- <span data-ttu-id="30951-2747">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2747">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2748">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2748">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2749">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2749">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2750">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2750">fx_media_write</span></span>
- <span data-ttu-id="30951-2751">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2751">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="30951-2752">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2752">fx_media_format</span></span>

<span data-ttu-id="30951-2753">Meios de forma formatos</span><span class="sxs-lookup"><span data-stu-id="30951-2753">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2754">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2754">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="30951-2755">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2755">Description</span></span>

<span data-ttu-id="30951-2756">Este serviço forma o meio fornecido de forma compatível COM FAT 12/16/32 com base nos parâmetros fornecidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2756">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="30951-2757">Este serviço deve ser chamado antes da abertura dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2757">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2758">*A formatação de um meio de comunicação já formatado apaga efetivamente todos os ficheiros e diretórios nos meios de comunicação.*</span><span class="sxs-lookup"><span data-stu-id="30951-2758">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2759">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2759">Input Parameters</span></span>

- <span data-ttu-id="30951-2760">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2760">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="30951-2761">Isto é utilizado apenas para fornecer algumas informações básicas necessárias para o condutor operar.</span><span class="sxs-lookup"><span data-stu-id="30951-2761">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="30951-2762">**condutor**: Pontear o controlador de I/S para este meio de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2762">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="30951-2763">Este será normalmente o mesmo condutor fornecido à chamada fx_media_open subsequente.</span><span class="sxs-lookup"><span data-stu-id="30951-2763">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="30951-2764">**driver_info_ptr**: Pontear para informações opcionais que o condutor de E/S pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="30951-2764">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="30951-2765">**memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2765">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="30951-2766">**memory_size**: Especifica o tamanho da memória dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2766">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="30951-2767">O tamanho deve ser pelo menos tão grande quanto o tamanho do sector dos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2767">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="30951-2768">**volume_name**: Pontear para a cadeia de nomes de volume, que é um máximo de 11 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-2768">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="30951-2769">**number_of_fats**: Número de FATs nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2769">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="30951-2770">O valor mínimo é 1 para a FAT primária.</span><span class="sxs-lookup"><span data-stu-id="30951-2770">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="30951-2771">Valores superiores a 1 resultam na manutenção de cópias FAT adicionais no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="30951-2771">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="30951-2772">**directory_entries**: Número de entradas de diretório no diretório de raiz.</span><span class="sxs-lookup"><span data-stu-id="30951-2772">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="30951-2773">**hidden_sectors**: Número de sectores escondidos antes do sector de arranque destes meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2773">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="30951-2774">Isto é típico quando várias divisórias estão presentes.</span><span class="sxs-lookup"><span data-stu-id="30951-2774">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="30951-2775">**total_sectors**: Número total de sectores nos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2775">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="30951-2776">**bytes_per_sector**: Número de bytes por sector, que é tipicamente 512.</span><span class="sxs-lookup"><span data-stu-id="30951-2776">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="30951-2777">FileX requer que este seja um múltiplo de 32.</span><span class="sxs-lookup"><span data-stu-id="30951-2777">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="30951-2778">**sectors_per_cluster**: Número de sectores em cada cluster.</span><span class="sxs-lookup"><span data-stu-id="30951-2778">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="30951-2779">O cluster é a unidade de atribuição mínima num sistema de ficheiros FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2779">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="30951-2780">**cabeças**: Número de cabeças físicas.</span><span class="sxs-lookup"><span data-stu-id="30951-2780">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="30951-2781">**sectors_per_track**: Número de sectores por via.</span><span class="sxs-lookup"><span data-stu-id="30951-2781">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2782">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2782">Return Values</span></span>

- <span data-ttu-id="30951-2783">**FX_SUCCESS** (0x00) Formato de mídia bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-2783">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="30951-2784">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2784">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2785">**FX_PTR_ERROR** (0x18) Meios de comunicação, controlador ou ponteiro de memória inválidos.</span><span class="sxs-lookup"><span data-stu-id="30951-2785">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="30951-2786">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2786">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2787">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2787">Allowed From</span></span>

<span data-ttu-id="30951-2788">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2789">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2789">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="30951-2790">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2790">See Also</span></span>

- <span data-ttu-id="30951-2791">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2791">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2792">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2792">fx_media_abort</span></span>
- <span data-ttu-id="30951-2793">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2793">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2794">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2794">fx_media_check</span></span>
- <span data-ttu-id="30951-2795">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2795">fx_media_close</span></span>
- <span data-ttu-id="30951-2796">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2796">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2797">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2797">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2798">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2798">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2799">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2799">fx_media_flush</span></span>
- <span data-ttu-id="30951-2800">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2800">fx_media_open</span></span>
- <span data-ttu-id="30951-2801">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2801">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2802">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2802">fx_media_read</span></span>
- <span data-ttu-id="30951-2803">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2803">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2804">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2804">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2805">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2805">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2806">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2806">fx_media_write</span></span>
- <span data-ttu-id="30951-2807">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2807">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="30951-2808">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2808">fx_media_open</span></span>

<span data-ttu-id="30951-2809">Abre os meios de comunicação para acesso a ficheiros</span><span class="sxs-lookup"><span data-stu-id="30951-2809">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2810">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2810">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="30951-2811">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2811">Description</span></span>

<span data-ttu-id="30951-2812">Este serviço abre um meio de acesso a ficheiros utilizando o controlador de E/S fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-2812">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-2813">*A memória fornecida a este serviço é utilizada para implementar uma cache do sector lógico interno, daí que mais memória fornecida, mais física é reduzida a I/O. O FileX requer uma cache de pelo menos um sector lógico (bytes por sector dos meios de comunicação).*</span><span class="sxs-lookup"><span data-stu-id="30951-2813">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2814">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2814">Input Parameters</span></span>

- <span data-ttu-id="30951-2815">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2815">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-2816">**media_name**: Ponteiro para o nome dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2816">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="30951-2817">**media_driver**: Ponteiro para o controlador de I/O para este meio de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2817">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="30951-2818">O controlador de E/S deve estar em conformidade com os requisitos do controlador FileX definidos no capítulo 5.</span><span class="sxs-lookup"><span data-stu-id="30951-2818">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="30951-2819">**driver_info_ptr**: Pontear para informações opcionais que o controlador de E/S fornecido pode utilizar.</span><span class="sxs-lookup"><span data-stu-id="30951-2819">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="30951-2820">**memory_ptr**: Ponte para a memória de trabalho para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2820">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="30951-2821">**memory_size**: Especifica o tamanho da memória dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2821">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="30951-2822">O tamanho deve ser tão grande quanto o tamanho do sector dos meios de comunicação (normalmente 512 bytes).</span><span class="sxs-lookup"><span data-stu-id="30951-2822">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2823">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2823">Return Values</span></span>

- <span data-ttu-id="30951-2824">**FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2824">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="30951-2825">**FX_BOOT_ERROR** (0x01) Erro de leitura do sector de arranque dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2825">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="30951-2826">**FX_MEDIA_INVALID** (0x02) O sector de arranque especificado dos meios de comunicação é corrupto ou inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2826">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="30951-2827">Além disso, este código de devolução é utilizado para indicar que o tamanho da cache do sector lógico ou o tamanho da entrada FAT não é uma potência de 2.</span><span class="sxs-lookup"><span data-stu-id="30951-2827">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="30951-2828">**FX_FAT_READ_ERROR** (0x03) Erro de leitura do meio de comunicação FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-2828">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="30951-2829">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2829">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2830">**FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.</span><span class="sxs-lookup"><span data-stu-id="30951-2830">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="30951-2831">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2831">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2832">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2832">Allowed From</span></span>

<span data-ttu-id="30951-2833">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2834">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2834">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="30951-2835">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2835">See Also</span></span>

- <span data-ttu-id="30951-2836">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2836">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2837">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2837">fx_media_abort</span></span>
- <span data-ttu-id="30951-2838">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2838">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2839">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2839">fx_media_check</span></span>
- <span data-ttu-id="30951-2840">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2840">fx_media_close</span></span>
- <span data-ttu-id="30951-2841">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2841">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2842">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2842">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2843">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2843">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2844">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2844">fx_media_flush</span></span>
- <span data-ttu-id="30951-2845">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2845">fx_media_format</span></span>
- <span data-ttu-id="30951-2846">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2846">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2847">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2847">fx_media_read</span></span>
- <span data-ttu-id="30951-2848">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2848">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2849">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2849">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2850">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2850">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2851">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2851">fx_media_write</span></span>
- <span data-ttu-id="30951-2852">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2852">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="30951-2853">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2853">fx_media_open_notify_set</span></span>

<span data-ttu-id="30951-2854">Define a função de notificação aberta dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-2854">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2855">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2855">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="30951-2856">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2856">Description</span></span>

<span data-ttu-id="30951-2857">Este serviço define uma função de chamada de notificação que será invocada após a abertura de um meio de comunicação com sucesso.</span><span class="sxs-lookup"><span data-stu-id="30951-2857">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2858">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2858">Input Parameters</span></span>

- <span data-ttu-id="30951-2859">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2859">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-2860">**media_open_notify**: Os meios de comunicação estão abertos a notificar a função de retorno a instalar.</span><span class="sxs-lookup"><span data-stu-id="30951-2860">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="30951-2861">Passar NUDIS como a função de retorno desativa o retorno aberto dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2861">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2862">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2862">Return Values</span></span>


- <span data-ttu-id="30951-2863">**FX_SUCCESS** (0x00) A função de retorno com sucesso instalou a função de retorno.</span><span class="sxs-lookup"><span data-stu-id="30951-2863">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="30951-2864">**FX_PTR_ERROR** (0x18) media_ptr é NU.</span><span class="sxs-lookup"><span data-stu-id="30951-2864">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="30951-2865">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2865">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2866">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2866">Allowed From</span></span>

<span data-ttu-id="30951-2867">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2868">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2868">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="30951-2869">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2869">See Also</span></span>

- <span data-ttu-id="30951-2870">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2870">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2871">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2871">fx_media_abort</span></span>
- <span data-ttu-id="30951-2872">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2872">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2873">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2873">fx_media_check</span></span>
- <span data-ttu-id="30951-2874">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2874">fx_media_close</span></span>
- <span data-ttu-id="30951-2875">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2875">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2876">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2876">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2877">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2877">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2878">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2878">fx_media_flush</span></span>
- <span data-ttu-id="30951-2879">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2879">fx_media_format</span></span>
- <span data-ttu-id="30951-2880">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2880">fx_media_open</span></span>
- <span data-ttu-id="30951-2881">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2881">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2882">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2882">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2883">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2883">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2884">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2884">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2885">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2885">fx_media_write</span></span>
- <span data-ttu-id="30951-2886">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2886">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="30951-2887">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2887">fx_media_read</span></span>

<span data-ttu-id="30951-2888">Lê o setor lógico dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-2888">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2889">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2889">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-2890">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2890">Description</span></span>

<span data-ttu-id="30951-2891">Este serviço lê um sector lógico dos meios de comunicação social e coloca-o no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-2891">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2892">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2892">Input Parameters</span></span>

- <span data-ttu-id="30951-2893">**media_ptr**: Ponter para um meio de comunicação previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2893">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="30951-2894">**logical_sector**: Sector lógico para ler.</span><span class="sxs-lookup"><span data-stu-id="30951-2894">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="30951-2895">**buffer_ptr**: Ponte para o destino para o sector lógico ler.</span><span class="sxs-lookup"><span data-stu-id="30951-2895">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2896">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2896">Return Values</span></span>

- <span data-ttu-id="30951-2897">**FX_SUCCESS** (0x00) Leitura bem sucedida dos meios de comunicação social.</span><span class="sxs-lookup"><span data-stu-id="30951-2897">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="30951-2898">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2898">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2899">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2899">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2900">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-2900">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-2901">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro tampão.</span><span class="sxs-lookup"><span data-stu-id="30951-2901">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="30951-2902">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2902">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2903">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2903">Allowed From</span></span>

<span data-ttu-id="30951-2904">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2904">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2905">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2905">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="30951-2906">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2906">See Also</span></span>

- <span data-ttu-id="30951-2907">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2907">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2908">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2908">fx_media_abort</span></span>
- <span data-ttu-id="30951-2909">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2909">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2910">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2910">fx_media_check</span></span>
- <span data-ttu-id="30951-2911">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2911">fx_media_close</span></span>
- <span data-ttu-id="30951-2912">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2912">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2913">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2913">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2914">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2914">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2915">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2915">fx_media_flush</span></span>
- <span data-ttu-id="30951-2916">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2916">fx_media_format</span></span>
- <span data-ttu-id="30951-2917">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2917">fx_media_open</span></span>
- <span data-ttu-id="30951-2918">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2918">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2919">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2919">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2920">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2920">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2921">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2921">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2922">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2922">fx_media_write</span></span>
- <span data-ttu-id="30951-2923">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2923">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="30951-2924">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2924">fx_media_space_available</span></span>

<span data-ttu-id="30951-2925">Devolve espaço de mídia disponível</span><span class="sxs-lookup"><span data-stu-id="30951-2925">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2926">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2926">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="30951-2927">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2927">Description</span></span>

<span data-ttu-id="30951-2928">Este serviço devolve o número de bytes disponíveis nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2928">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="30951-2929">Para trabalhar com os meios de comunicação superiores a 4GB, a aplicação deve utilizar o serviço *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="30951-2929">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2930">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2930">Input Parameters</span></span>

- <span data-ttu-id="30951-2931">**media_ptr**: Ponter para um meio de comunicação previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2931">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="30951-2932">**available_bytes_ptr**: Bytes disponíveis deixados nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2932">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2933">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2933">Return Values</span></span>

- <span data-ttu-id="30951-2934">**FX_SUCCESS** (0x00) devolveu com sucesso o espaço disponível nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2934">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="30951-2935">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2935">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2936">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido ou ponteiro bytes disponível é NU.</span><span class="sxs-lookup"><span data-stu-id="30951-2936">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="30951-2937">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2937">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2938">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2938">Allowed From</span></span>

<span data-ttu-id="30951-2939">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2939">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2940">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2940">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="30951-2941">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2941">See Also</span></span>

- <span data-ttu-id="30951-2942">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2942">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2943">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2943">fx_media_abort</span></span>
- <span data-ttu-id="30951-2944">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2944">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2945">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2945">fx_media_check</span></span>
- <span data-ttu-id="30951-2946">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2946">fx_media_close</span></span>
- <span data-ttu-id="30951-2947">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2947">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2948">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2948">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2949">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2949">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2950">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2950">fx_media_flush</span></span>
- <span data-ttu-id="30951-2951">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2951">fx_media_format</span></span>
- <span data-ttu-id="30951-2952">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2952">fx_media_open</span></span>
- <span data-ttu-id="30951-2953">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2953">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2954">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2954">fx_media_read</span></span>
- <span data-ttu-id="30951-2955">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2955">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-2956">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2956">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2957">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2957">fx_media_write</span></span>
- <span data-ttu-id="30951-2958">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2958">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="30951-2959">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-2959">fx_media_volume_get</span></span>

<span data-ttu-id="30951-2960">Obtém o nome do volume dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-2960">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-2961">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-2961">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="30951-2962">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-2962">Description</span></span>

<span data-ttu-id="30951-2963">Este serviço recupera o nome de volume do meio de comunicação anteriormente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-2963">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-2964">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-2964">Input Parameters</span></span>

- <span data-ttu-id="30951-2965">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-2965">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-2966">**volume_name**: Ponter para o destino para o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="30951-2966">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="30951-2967">Note que o destino deve ser pelo menos grande o suficiente para ter 12 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-2967">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="30951-2968">**volume_source**: Designa onde recuperar o nome, quer do sector do arranque, quer do diretório de raiz.</span><span class="sxs-lookup"><span data-stu-id="30951-2968">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="30951-2969">Os valores válidos para este parâmetro são:</span><span class="sxs-lookup"><span data-stu-id="30951-2969">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="30951-2970">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="30951-2970">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="30951-2971">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="30951-2971">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-2972">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-2972">Return Values</span></span>

- <span data-ttu-id="30951-2973">**FX_SUCCESS** (0x00) Volume de mídia bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="30951-2973">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="30951-2974">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-2974">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-2975">**volume FX_NOT_FOUND** (0x04) não encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-2975">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="30951-2976">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-2976">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-2977">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino de volume.</span><span class="sxs-lookup"><span data-stu-id="30951-2977">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="30951-2978">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-2978">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-2979">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-2979">Allowed From</span></span>

<span data-ttu-id="30951-2980">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-2980">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-2981">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-2981">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="30951-2982">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-2982">See Also</span></span>

- <span data-ttu-id="30951-2983">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-2983">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-2984">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-2984">fx_media_abort</span></span>
- <span data-ttu-id="30951-2985">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-2985">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-2986">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-2986">fx_media_check</span></span>
- <span data-ttu-id="30951-2987">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-2987">fx_media_close</span></span>
- <span data-ttu-id="30951-2988">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2988">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-2989">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-2989">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-2990">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2990">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-2991">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-2991">fx_media_flush</span></span>
- <span data-ttu-id="30951-2992">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-2992">fx_media_format</span></span>
- <span data-ttu-id="30951-2993">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-2993">fx_media_open</span></span>
- <span data-ttu-id="30951-2994">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-2994">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-2995">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-2995">fx_media_read</span></span>
- <span data-ttu-id="30951-2996">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-2996">fx_media_space_available</span></span>
- <span data-ttu-id="30951-2997">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-2997">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-2998">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-2998">fx_media_write</span></span>
- <span data-ttu-id="30951-2999">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-2999">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="30951-3000">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-3000">fx_media_volume_get_extended</span></span>

<span data-ttu-id="30951-3001">Obtém o nome do volume de mídia de meios de comunicação anteriormente abertos</span><span class="sxs-lookup"><span data-stu-id="30951-3001">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3002">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3002">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="30951-3003">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3003">Description</span></span>

<span data-ttu-id="30951-3004">Este serviço recupera o nome de volume do meio de comunicação anteriormente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-3004">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3005">Este serviço é idêntico a ***fx_media_volume_get()** _ exceto que o chamador passa no tamanho do tampão _ *volume_name** .</span><span class="sxs-lookup"><span data-stu-id="30951-3005">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3006">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3006">Input Parameters</span></span>


- <span data-ttu-id="30951-3007">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3007">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3008">**volume_name**: Ponter para o destino para o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="30951-3008">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="30951-3009">Note que o destino deve ser pelo menos grande o suficiente para ter 12 caracteres.</span><span class="sxs-lookup"><span data-stu-id="30951-3009">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="30951-3010">**volume_name_buffer_length**: Tamanho do tampão de volume_name.</span><span class="sxs-lookup"><span data-stu-id="30951-3010">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="30951-3011">**volume_source**: Designa onde recuperar o nome, quer do sector do arranque, quer do diretório de raiz.</span><span class="sxs-lookup"><span data-stu-id="30951-3011">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="30951-3012">Os valores válidos para este parâmetro são:</span><span class="sxs-lookup"><span data-stu-id="30951-3012">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="30951-3013">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="30951-3013">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="30951-3014">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="30951-3014">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3015">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3015">Return Values</span></span>

- <span data-ttu-id="30951-3016">**FX_SUCCESS** (0x00) Volume de mídia bem sucedido obtém.</span><span class="sxs-lookup"><span data-stu-id="30951-3016">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="30951-3017">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3017">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3018">**volume FX_NOT_FOUND** (0x04) não encontrado.</span><span class="sxs-lookup"><span data-stu-id="30951-3018">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="30951-3019">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3019">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3020">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiro de destino de volume.</span><span class="sxs-lookup"><span data-stu-id="30951-3020">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="30951-3021">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3021">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3022">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3022">Allowed From</span></span>

<span data-ttu-id="30951-3023">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3023">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3024">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3024">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3025">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3025">See Also</span></span>

- <span data-ttu-id="30951-3026">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-3026">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-3027">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-3027">fx_media_abort</span></span>
- <span data-ttu-id="30951-3028">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-3028">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-3029">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-3029">fx_media_check</span></span>
- <span data-ttu-id="30951-3030">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-3030">fx_media_close</span></span>
- <span data-ttu-id="30951-3031">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3031">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-3032">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-3032">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-3033">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3033">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-3034">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-3034">fx_media_flush</span></span>
- <span data-ttu-id="30951-3035">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-3035">fx_media_format</span></span>
- <span data-ttu-id="30951-3036">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-3036">fx_media_open</span></span>
- <span data-ttu-id="30951-3037">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3037">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-3038">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-3038">fx_media_read</span></span>
- <span data-ttu-id="30951-3039">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3039">fx_media_space_available</span></span>
- <span data-ttu-id="30951-3040">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-3040">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-3041">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-3041">fx_media_write</span></span>
- <span data-ttu-id="30951-3042">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3042">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="30951-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-3043">fx_media_volume_set</span></span>

<span data-ttu-id="30951-3044">Define o nome do volume dos meios de comunicação</span><span class="sxs-lookup"><span data-stu-id="30951-3044">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3045">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3045">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="30951-3046">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3046">Description</span></span>

<span data-ttu-id="30951-3047">Este serviço define o nome de volume do meio de comunicação anteriormente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-3047">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3048">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3048">Input Parameters</span></span>

- <span data-ttu-id="30951-3049">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3049">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3050">**volume_name**: Ponteiro para o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="30951-3050">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3051">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3051">Return Values</span></span>

- <span data-ttu-id="30951-3052">**FX_SUCCESS** (0x00) Conjunto de volume de mídia bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="30951-3052">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="30951-3053">**FX_INVALID_NAME** (0x0C) Volume_name é inválida.</span><span class="sxs-lookup"><span data-stu-id="30951-3053">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="30951-3054">**FX_MEDIA_INVALID** (0x02) Incapaz de definir o nome do volume.</span><span class="sxs-lookup"><span data-stu-id="30951-3054">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="30951-3055">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3055">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3056">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3056">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3057">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3057">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-3058">**FX_PTR_ERROR** (0x18) Media inválido ou ponteiro de nome de volume.</span><span class="sxs-lookup"><span data-stu-id="30951-3058">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="30951-3059">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3059">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3060">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3060">Allowed From</span></span>

<span data-ttu-id="30951-3061">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3061">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3062">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3062">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3063">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3063">See Also</span></span>

- <span data-ttu-id="30951-3064">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-3064">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-3065">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-3065">fx_media_abort</span></span>
- <span data-ttu-id="30951-3066">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-3066">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-3067">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-3067">fx_media_check</span></span>
- <span data-ttu-id="30951-3068">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-3068">fx_media_close</span></span>
- <span data-ttu-id="30951-3069">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3069">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-3070">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-3070">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-3071">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3071">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-3072">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-3072">fx_media_flush</span></span>
- <span data-ttu-id="30951-3073">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-3073">fx_media_format</span></span>
- <span data-ttu-id="30951-3074">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-3074">fx_media_open</span></span>
- <span data-ttu-id="30951-3075">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3075">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-3076">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-3076">fx_media_read</span></span>
- <span data-ttu-id="30951-3077">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3077">fx_media_space_available</span></span>
- <span data-ttu-id="30951-3078">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-3078">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-3079">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-3079">fx_media_write</span></span>
- <span data-ttu-id="30951-3080">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3080">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="30951-3081">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="30951-3081">fx_media_write</span></span>

<span data-ttu-id="30951-3082">Escreve o setor lógico</span><span class="sxs-lookup"><span data-stu-id="30951-3082">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3083">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3083">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="30951-3084">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3084">Description</span></span>

<span data-ttu-id="30951-3085">Este serviço escreve o tampão fornecido para o sector lógico especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-3085">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3086">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3086">Input Parameters</span></span>

- <span data-ttu-id="30951-3087">**media_ptr**: Ponter para um meio de comunicação previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="30951-3087">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="30951-3088">**logical_sector**: Sector lógico para escrever.</span><span class="sxs-lookup"><span data-stu-id="30951-3088">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="30951-3089">**buffer_ptr**: Ponteiro para a fonte para o setor lógico escrever.</span><span class="sxs-lookup"><span data-stu-id="30951-3089">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3090">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3090">Return Values</span></span>

- <span data-ttu-id="30951-3091">**FX_SUCCESS** (0x00) Os meios de comunicação de sucesso escrevem.</span><span class="sxs-lookup"><span data-stu-id="30951-3091">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="30951-3092">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3092">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3093">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3093">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-3094">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3094">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3095">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3095">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-3096">**FX_PTR_ERROR** (0x18) Ponteiro de mídia inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3096">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="30951-3097">**FX_CALLER_ERROR**    (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3097">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3098">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3098">Allowed From</span></span>

<span data-ttu-id="30951-3099">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3099">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3100">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3100">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="30951-3101">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3101">See Also</span></span>

- <span data-ttu-id="30951-3102">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="30951-3102">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="30951-3103">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="30951-3103">fx_media_abort</span></span>
- <span data-ttu-id="30951-3104">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="30951-3104">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="30951-3105">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="30951-3105">fx_media_check</span></span>
- <span data-ttu-id="30951-3106">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="30951-3106">fx_media_close</span></span>
- <span data-ttu-id="30951-3107">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3107">fx_media_close_notify_set</span></span>
- <span data-ttu-id="30951-3108">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="30951-3108">fx_media_exFAT_format</span></span>
- <span data-ttu-id="30951-3109">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3109">fx_media_extended_space_available</span></span>
- <span data-ttu-id="30951-3110">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="30951-3110">fx_media_flush</span></span>
- <span data-ttu-id="30951-3111">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="30951-3111">fx_media_format</span></span>
- <span data-ttu-id="30951-3112">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="30951-3112">fx_media_open</span></span>
- <span data-ttu-id="30951-3113">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3113">fx_media_open_notify_set</span></span>
- <span data-ttu-id="30951-3114">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="30951-3114">fx_media_read</span></span>
- <span data-ttu-id="30951-3115">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="30951-3115">fx_media_space_available</span></span>
- <span data-ttu-id="30951-3116">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="30951-3116">fx_media_volume_get</span></span>
- <span data-ttu-id="30951-3117">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="30951-3117">fx_media_volume_set</span></span>
- <span data-ttu-id="30951-3118">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3118">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="30951-3119">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="30951-3119">fx_system_date_get</span></span>

<span data-ttu-id="30951-3120">Obtém a data do sistema de ficheiros</span><span class="sxs-lookup"><span data-stu-id="30951-3120">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3121">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3121">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="30951-3122">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3122">Description</span></span>

<span data-ttu-id="30951-3123">Este serviço devolve a data atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="30951-3123">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3124">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3124">Input Parameters</span></span>

- <span data-ttu-id="30951-3125">**ano**: Ponteiro para destino para o ano.</span><span class="sxs-lookup"><span data-stu-id="30951-3125">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="30951-3126">**mês**: Ponteiro para destino para o mês.</span><span class="sxs-lookup"><span data-stu-id="30951-3126">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="30951-3127">**dia**: Ponteiro para destino para o dia.</span><span class="sxs-lookup"><span data-stu-id="30951-3127">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3128">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3128">Return Values</span></span>

- <span data-ttu-id="30951-3129">**FX_SUCCESS** (0x00) Recuperação de datas bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="30951-3129">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="30951-3130">**FX_PTR_ERROR** (0x18) Um ou mais dos parâmetros de entrada são NUOS.</span><span class="sxs-lookup"><span data-stu-id="30951-3130">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3131">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3131">Allowed From</span></span>

<span data-ttu-id="30951-3132">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3133">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3134">See Also</span></span>

- <span data-ttu-id="30951-3135">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="30951-3135">fx_system_date_set</span></span>
- <span data-ttu-id="30951-3136">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3136">fx_system_initialize</span></span>
- <span data-ttu-id="30951-3137">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="30951-3137">fx_system_time_get</span></span>
- <span data-ttu-id="30951-3138">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3138">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="30951-3139">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="30951-3139">fx_system_date_set</span></span>

<span data-ttu-id="30951-3140">Define a data do sistema</span><span class="sxs-lookup"><span data-stu-id="30951-3140">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3141">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3141">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="30951-3142">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3142">Description</span></span>

<span data-ttu-id="30951-3143">Este serviço define a data do sistema conforme especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-3143">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-3144">*Este serviço deve ser chamado pouco depois **fx_system_initialize** para definir a data inicial do sistema. Por predefinição, a data do sistema é a da última versão genérica do FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-3144">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3145">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3145">Input Parameters</span></span>

- <span data-ttu-id="30951-3146">**ano**: Ano Novo.</span><span class="sxs-lookup"><span data-stu-id="30951-3146">**year**: New year.</span></span> <span data-ttu-id="30951-3147">A gama válida é de 1980 até ao ano 2107.</span><span class="sxs-lookup"><span data-stu-id="30951-3147">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="30951-3148">**mês**: Mês Novo.</span><span class="sxs-lookup"><span data-stu-id="30951-3148">**month**: New month.</span></span> <span data-ttu-id="30951-3149">O intervalo válido é de 1 a 12.</span><span class="sxs-lookup"><span data-stu-id="30951-3149">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="30951-3150">**dia**: Novo dia.</span><span class="sxs-lookup"><span data-stu-id="30951-3150">**day**: New day.</span></span> <span data-ttu-id="30951-3151">O intervalo válido é de 1 a 31, dependendo das condições do mês e do ano bissexto.</span><span class="sxs-lookup"><span data-stu-id="30951-3151">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3152">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3152">Return Values</span></span>

- <span data-ttu-id="30951-3153">**FX_SUCCESS** (0x00) Definição de data de sucesso.</span><span class="sxs-lookup"><span data-stu-id="30951-3153">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="30951-3154">**FX_INVALID_YEAR** (0x12) Ano inválido especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-3154">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="30951-3155">**FX_INVALID_MONTH** (0x13) mês inválido especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-3155">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="30951-3156">**FX_INVALID_DAY** (0x14) Dia inválido especificado.</span><span class="sxs-lookup"><span data-stu-id="30951-3156">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3157">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3157">Allowed From</span></span>

<span data-ttu-id="30951-3158">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="30951-3158">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3159">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3160">See Also</span></span>

- <span data-ttu-id="30951-3161">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="30951-3161">fx_system_date_get</span></span>
- <span data-ttu-id="30951-3162">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3162">fx_system_initialize</span></span>
- <span data-ttu-id="30951-3163">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="30951-3163">fx_system_time_get</span></span>
- <span data-ttu-id="30951-3164">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3164">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="30951-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3165">fx_system_initialize</span></span>

<span data-ttu-id="30951-3166">Inicializa todo o sistema</span><span class="sxs-lookup"><span data-stu-id="30951-3166">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3167">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3167">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="30951-3168">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3168">Description</span></span>

<span data-ttu-id="30951-3169">Este serviço inicializa todas as principais estruturas de dados do FileX.</span><span class="sxs-lookup"><span data-stu-id="30951-3169">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="30951-3170">Deve ser chamado em ***tx_application_define*** ou possivelmente a partir de um fio de inicialização e deve ser chamado antes de usar qualquer outro serviço FileX.</span><span class="sxs-lookup"><span data-stu-id="30951-3170">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-3171">*Uma vez inicializado por esta chamada, a aplicação deve chamar ***fx_system_date_set** _ e _ *fx_system_time_set** para começar com uma data e hora precisas do sistema.*</span><span class="sxs-lookup"><span data-stu-id="30951-3171">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3172">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3172">Input Parameters</span></span>

<span data-ttu-id="30951-3173">Nenhum</span><span class="sxs-lookup"><span data-stu-id="30951-3173">None</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3174">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3174">Return Values</span></span>

<span data-ttu-id="30951-3175">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="30951-3175">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3176">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3176">Allowed From</span></span>

<span data-ttu-id="30951-3177">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="30951-3177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3178">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="30951-3179">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3179">See Also</span></span>

- <span data-ttu-id="30951-3180">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="30951-3180">fx_system_date_get</span></span>
- <span data-ttu-id="30951-3181">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="30951-3181">fx_system_date_set</span></span>
- <span data-ttu-id="30951-3182">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="30951-3182">fx_system_time_get</span></span>
- <span data-ttu-id="30951-3183">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3183">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="30951-3184">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="30951-3184">fx_system_time_get</span></span>

<span data-ttu-id="30951-3185">Obtém tempo atual do sistema</span><span class="sxs-lookup"><span data-stu-id="30951-3185">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3186">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3186">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="30951-3187">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3187">Description</span></span>

<span data-ttu-id="30951-3188">Este serviço recupera o tempo atual do sistema.</span><span class="sxs-lookup"><span data-stu-id="30951-3188">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3189">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3189">Input Parameters</span></span>

- <span data-ttu-id="30951-3190">**hora**: Ponteiro para destino por hora.</span><span class="sxs-lookup"><span data-stu-id="30951-3190">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="30951-3191">**minuto**: Ponteiro para destino por um minuto.</span><span class="sxs-lookup"><span data-stu-id="30951-3191">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="30951-3192">**segundo**: Ponteiro para destino para o segundo.</span><span class="sxs-lookup"><span data-stu-id="30951-3192">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3193">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3193">Return Values</span></span>

- <span data-ttu-id="30951-3194">**FX_SUCCESS** (0x00) Recuperação de tempo bem sucedida do sistema.</span><span class="sxs-lookup"><span data-stu-id="30951-3194">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="30951-3195">**FX_PTR_ERROR** (0x18) Um ou mais dos parâmetros de entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3195">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3196">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3196">Allowed From</span></span>

<span data-ttu-id="30951-3197">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3197">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3198">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3199">See Also</span></span>

- <span data-ttu-id="30951-3200">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="30951-3200">fx_system_date_get</span></span>
- <span data-ttu-id="30951-3201">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="30951-3201">fx_system_date_set</span></span>
- <span data-ttu-id="30951-3202">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3202">fx_system_initialize</span></span>
- <span data-ttu-id="30951-3203">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3203">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="30951-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3204">fx_system_time_set</span></span>

<span data-ttu-id="30951-3205">Define o tempo atual do sistema</span><span class="sxs-lookup"><span data-stu-id="30951-3205">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3206">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3206">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="30951-3207">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3207">Description</span></span>

<span data-ttu-id="30951-3208">Este serviço define o tempo atual do sistema para o especificado pelos parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="30951-3208">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-3209">*Este serviço deve ser chamado pouco depois **fx_system_initialize** para definir o tempo inicial do sistema. Por padrão, o tempo do sistema é 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="30951-3209">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3210">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3210">Input Parameters</span></span>

- <span data-ttu-id="30951-3211">**hora:** Hora nova (0-23).</span><span class="sxs-lookup"><span data-stu-id="30951-3211">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="30951-3212">**minuto**: Novo minuto (0-59).</span><span class="sxs-lookup"><span data-stu-id="30951-3212">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="30951-3213">**segundo**: Novo segundo (0-59).</span><span class="sxs-lookup"><span data-stu-id="30951-3213">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3214">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3214">Return Values</span></span>

- <span data-ttu-id="30951-3215">**FX_SUCCESS** (0x00) Recuperação de tempo bem sucedida do sistema.</span><span class="sxs-lookup"><span data-stu-id="30951-3215">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="30951-3216">**FX_INVALID_HOUR**    (0x15) A hora nova é inválida.</span><span class="sxs-lookup"><span data-stu-id="30951-3216">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="30951-3217">**FX_INVALID_MINUTE** (0x16) Novo minuto é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3217">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="30951-3218">**FX_INVALID_SECOND** (0x17) O segundo novo é inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3218">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3219">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3219">Allowed From</span></span>

<span data-ttu-id="30951-3220">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3221">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3221">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3222">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3222">See Also</span></span>

- <span data-ttu-id="30951-3223">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="30951-3223">fx_system_date_get</span></span>
- <span data-ttu-id="30951-3224">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="30951-3224">fx_system_date_set</span></span>
- <span data-ttu-id="30951-3225">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="30951-3225">fx_system_initialize</span></span>
- <span data-ttu-id="30951-3226">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="30951-3226">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="30951-3227">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-3227">fx_unicode_directory_create</span></span>

<span data-ttu-id="30951-3228">Cria um diretório Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3228">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3229">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3229">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="30951-3230">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3230">Description</span></span>

<span data-ttu-id="30951-3231">Este serviço cria um subdiretório nomeado Unicode no diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro de nome de origem Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3231">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="30951-3232">Se for bem sucedido, o nome curto (formato 8.3) da recém-criada subdirectory Unicode é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3232">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-3233">*Todas as operações no subdiretório Unicode (tornando-o o caminho padrão, eliminação, etc.) devem ser efetuadas fornecendo o nome curto devolvido (formato 8.3) aos serviços de diretório padrão do FileX.*</span><span class="sxs-lookup"><span data-stu-id="30951-3233">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3234">*Este serviço não é suportado em meios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="30951-3234">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3235">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3235">Input Parameters</span></span>

- <span data-ttu-id="30951-3236">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3236">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3237">**source_unicode_name**: Pontear o nome Unicode para o novo subdiretório.</span><span class="sxs-lookup"><span data-stu-id="30951-3237">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="30951-3238">**source_unicode_length**: Comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3238">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="30951-3239">**short_name**: Ponter para o destino para nome curto (formato 8.3) para o novo subdiretório Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3239">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3240">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3240">Return Values</span></span>

- <span data-ttu-id="30951-3241">**FX_SUCCESS** (0x00) Diretório de sucesso Unicode criar.</span><span class="sxs-lookup"><span data-stu-id="30951-3241">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="30951-3242">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3242">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3243">**FX_ALREADY_CREATED** (0x0B) Diretório especificado já existe.</span><span class="sxs-lookup"><span data-stu-id="30951-3243">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="30951-3244">**FX_NO_MORE_SPACE** (0x0A) Não há mais clusters disponíveis nos meios de comunicação para a entrada do novo diretório.</span><span class="sxs-lookup"><span data-stu-id="30951-3244">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="30951-3245">**FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3245">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="30951-3246">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3246">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-3247">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3247">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3248">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3248">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="30951-3249">**FX_IO_ERROR (0x90)** Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3249">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3250">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3250">Allowed From</span></span>

<span data-ttu-id="30951-3251">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3252">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3252">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3253">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3253">See Also</span></span>

- <span data-ttu-id="30951-3254">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3254">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-3255">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3255">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-3256">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-3256">fx_directory_create</span></span>
- <span data-ttu-id="30951-3257">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-3257">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-3258">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-3258">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-3259">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3259">fx_directory_delete</span></span>
- <span data-ttu-id="30951-3260">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3260">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-3261">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3261">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-3262">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-3262">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-3263">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-3263">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-3264">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-3264">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-3265">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-3265">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-3266">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-3266">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-3267">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3267">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-3268">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-3268">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-3269">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3269">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-3270">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3270">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-3271">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3271">fx_directory_rename</span></span>
- <span data-ttu-id="30951-3272">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3272">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-3273">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3273">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="30951-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3274">fx_unicode_directory_rename</span></span>

<span data-ttu-id="30951-3275">Rebatiza diretório usando a cadeia Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3275">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3276">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3276">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="30951-3277">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3277">Description</span></span>

<span data-ttu-id="30951-3278">Este serviço altera uma subdiretório nomeada pelo Unicode para o novo nome Unicode especificado no diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="30951-3278">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="30951-3279">Os parâmetros do nome Unicode não devem ter informações sobre o caminho.</span><span class="sxs-lookup"><span data-stu-id="30951-3279">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3280">*Este serviço não é suportado em meios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="30951-3280">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3281">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3281">Input Parameters</span></span>

- <span data-ttu-id="30951-3282">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3282">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3283">**old_unicode_name**: Pontear o nome Unicode para o ficheiro atual.</span><span class="sxs-lookup"><span data-stu-id="30951-3283">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="30951-3284">**old_unicode_name_length**: Comprimento do nome atual do Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3284">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="30951-3285">**new_unicode_name**: Pontear o novo nome do ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3285">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="30951-3286">**old_unicode_name_length**: Comprimento do novo nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3286">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="30951-3287">**new_short_name**: Ponteiro para destino para nome curto (formato 8.3) para o rebatizado ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3287">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="30951-3288">Diretório de renomeação com Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3288">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3289">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3289">Return Values</span></span>

- <span data-ttu-id="30951-3290">**FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3290">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="30951-3291">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3291">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3292">**FX_ALREADY_CREATED** (0x0B) Nome de diretório especificado já existe.</span><span class="sxs-lookup"><span data-stu-id="30951-3292">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="30951-3293">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3293">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3294">**FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.</span><span class="sxs-lookup"><span data-stu-id="30951-3294">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="30951-3295">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3295">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="30951-3296">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados estão protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3296">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3297">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3297">Allowed From</span></span>

<span data-ttu-id="30951-3298">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3298">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3299">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3299">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3300">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3300">See Also</span></span>

- <span data-ttu-id="30951-3301">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3301">fx_directory_attributes_read</span></span>
- <span data-ttu-id="30951-3302">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3302">fx_directory_attributes_set</span></span>
- <span data-ttu-id="30951-3303">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-3303">fx_directory_create</span></span>
- <span data-ttu-id="30951-3304">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="30951-3304">fx_directory_default_get</span></span>
- <span data-ttu-id="30951-3305">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="30951-3305">fx_directory_default_set</span></span>
- <span data-ttu-id="30951-3306">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3306">fx_directory_delete</span></span>
- <span data-ttu-id="30951-3307">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3307">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="30951-3308">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3308">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="30951-3309">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="30951-3309">fx_directory_information_get</span></span>
- <span data-ttu-id="30951-3310">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="30951-3310">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="30951-3311">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="30951-3311">fx_directory_local_path_get</span></span>
- <span data-ttu-id="30951-3312">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="30951-3312">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="30951-3313">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="30951-3313">fx_directory_local_path_set</span></span>
- <span data-ttu-id="30951-3314">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3314">fx_directory_long_name_get</span></span>
- <span data-ttu-id="30951-3315">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="30951-3315">fx_directory_name_test</span></span>
- <span data-ttu-id="30951-3316">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3316">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="30951-3317">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="30951-3317">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="30951-3318">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3318">fx_directory_rename</span></span>
- <span data-ttu-id="30951-3319">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3319">fx_directory_short_name_get</span></span>
- <span data-ttu-id="30951-3320">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="30951-3320">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="30951-3321">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3321">fx_unicode_file_create</span></span>

<span data-ttu-id="30951-3322">Cria um ficheiro Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3322">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3323">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3323">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="30951-3324">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3324">Description</span></span>

<span data-ttu-id="30951-3325">Este serviço cria um ficheiro nomeado pelo Unicode no diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro de nome de origem Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3325">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="30951-3326">Se for bem sucedido, o nome curto (formato 8.3) do ficheiro Unicode recém-criado é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3326">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="30951-3327">*Todas as operações no ficheiro Unicode (abertura, escrita, leitura, fecho, etc.) devem ser efetuadas fornecendo o nome curto devolvido (formato 8.3) aos serviços de ficheiros FileX padrão.*</span><span class="sxs-lookup"><span data-stu-id="30951-3327">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3328">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3328">Input Parameters</span></span>


- <span data-ttu-id="30951-3329">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3329">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3330">**source_unicode_name**: Ponter o nome Unicode para o novo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-3330">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="30951-3331">**source_unicode_length**: Comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3331">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="30951-3332">**short_name**: Ponteiro para destino para nome curto (formato 8.3) para o novo ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3332">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3333">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3333">Return Values</span></span>

- <span data-ttu-id="30951-3334">**FX_SUCCESS** (0x00) Criação de ficheiros bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-3334">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="30951-3335">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3335">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3336">**FX_ALREADY_CREATED** (0x0B) Ficheiro especificado já existe.</span><span class="sxs-lookup"><span data-stu-id="30951-3336">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="30951-3337">**FX_NO_MORE_SPACE** (0x0A) Não há mais clusters disponíveis nos meios de comunicação para a entrada do novo ficheiro.</span><span class="sxs-lookup"><span data-stu-id="30951-3337">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="30951-3338">**FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3338">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="30951-3339">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3339">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3340">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados são protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3340">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="30951-3341">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3341">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3342">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3342">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3343">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3343">Allowed From</span></span>

<span data-ttu-id="30951-3344">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3344">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3345">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3345">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3346">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3346">See Also</span></span>

- <span data-ttu-id="30951-3347">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3347">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3348">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3348">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3349">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3349">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3350">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3350">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3351">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3351">fx_file_close</span></span>
- <span data-ttu-id="30951-3352">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3352">fx_file_create</span></span>
- <span data-ttu-id="30951-3353">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3353">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3354">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3354">fx_file_delete</span></span>
- <span data-ttu-id="30951-3355">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3355">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3356">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3356">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3357">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3357">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3358">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3358">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3359">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3359">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3360">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3360">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3361">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3361">fx_file_open</span></span>
- <span data-ttu-id="30951-3362">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3362">fx_file_read</span></span>
- <span data-ttu-id="30951-3363">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3363">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3364">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3364">fx_file_rename</span></span>
- <span data-ttu-id="30951-3365">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3365">fx_file_seek</span></span>
- <span data-ttu-id="30951-3366">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3366">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3367">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3367">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3368">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3368">fx_file_write</span></span>
- <span data-ttu-id="30951-3369">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3369">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3370">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3370">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3371">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3371">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-3372">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3372">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="30951-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3373">fx_unicode_file_rename</span></span>

<span data-ttu-id="30951-3374">Renomea um ficheiro usando uma cadeia unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3374">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3375">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3375">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="30951-3376">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3376">Description</span></span>

<span data-ttu-id="30951-3377">Este serviço altera um nome de ficheiro nomeado Unicode para o novo nome Unicode especificado no diretório predefinido atual.</span><span class="sxs-lookup"><span data-stu-id="30951-3377">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="30951-3378">Os parâmetros do nome Unicode não devem ter informações sobre o caminho.</span><span class="sxs-lookup"><span data-stu-id="30951-3378">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3379">*Este serviço não é suportado em meios exFAT.*</span><span class="sxs-lookup"><span data-stu-id="30951-3379">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3380">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3380">Input Parameters</span></span>

- <span data-ttu-id="30951-3381">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3381">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3382">**old_unicode_name**: Pontear o nome Unicode para o ficheiro atual.</span><span class="sxs-lookup"><span data-stu-id="30951-3382">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="30951-3383">**old_unicode_name_length**: Comprimento do nome atual do Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3383">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="30951-3384">**new_unicode_name**: Pontear o novo nome do ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3384">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="30951-3385">**new_unicode_name_length**: Comprimento do novo nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3385">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="30951-3386">**new_short_name**: Ponteiro para destino para nome curto (formato 8.3) para o rebatizado ficheiro Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3386">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3387">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3387">Return Values</span></span>


- <span data-ttu-id="30951-3388">**FX_SUCCESS** (0x00) Meios de comunicação bem sucedidos abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3388">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="30951-3389">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3389">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3390">**FX_ALREADY_CREATED** (0x0B) Nome de ficheiro especificado já existe.</span><span class="sxs-lookup"><span data-stu-id="30951-3390">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="30951-3391">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3391">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3392">**FX_PTR_ERROR** (0x18) Um ou mais ponteiros são NUOS.</span><span class="sxs-lookup"><span data-stu-id="30951-3392">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="30951-3393">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3393">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="30951-3394">**FX_WRITE_PROTECT** (0x23) Os meios de comunicação especificados estão protegidos por escrito.</span><span class="sxs-lookup"><span data-stu-id="30951-3394">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3395">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3395">Allowed From</span></span>

<span data-ttu-id="30951-3396">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3396">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3397">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3397">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="30951-3398">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3398">See Also</span></span>

- <span data-ttu-id="30951-3399">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3399">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3400">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3400">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3401">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3401">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3402">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3402">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3403">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3403">fx_file_close</span></span>
- <span data-ttu-id="30951-3404">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3404">fx_file_create</span></span>
- <span data-ttu-id="30951-3405">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3405">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3406">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3406">fx_file_delete</span></span>
- <span data-ttu-id="30951-3407">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3407">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3408">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3408">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3409">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3409">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3410">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3410">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3411">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3411">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3412">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3412">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3413">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3413">fx_file_open</span></span>
- <span data-ttu-id="30951-3414">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3414">fx_file_read</span></span>
- <span data-ttu-id="30951-3415">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3415">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3416">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3416">fx_file_rename</span></span>
- <span data-ttu-id="30951-3417">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3417">fx_file_seek</span></span>
- <span data-ttu-id="30951-3418">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3418">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3419">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3419">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3420">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3420">fx_file_write</span></span>
- <span data-ttu-id="30951-3421">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3421">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3422">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3422">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3423">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3423">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-3424">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3424">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="30951-3425">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="30951-3425">fx_unicode_length_get</span></span>

<span data-ttu-id="30951-3426">Obtém comprimento do nome Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3426">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3427">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3427">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="30951-3428">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3428">Description</span></span>

<span data-ttu-id="30951-3429">Este serviço determina o comprimento do nome Unicode fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-3429">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="30951-3430">Um caracteres Unicode é representado por dois bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-3430">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="30951-3431">Um nome Unicode é uma série de dois caracteres Unicode byte terminados por dois bytes NULL (dois bytes de 0 valor).</span><span class="sxs-lookup"><span data-stu-id="30951-3431">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3432">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3432">Input Parameters</span></span>

<span data-ttu-id="30951-3433">**unicode_name**: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3433">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3434">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3434">Return Values</span></span>

<span data-ttu-id="30951-3435">**comprimento**: Comprimento do nome Unicode (número de caracteres Unicode no nome).</span><span class="sxs-lookup"><span data-stu-id="30951-3435">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3436">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3436">Allowed From</span></span>

<span data-ttu-id="30951-3437">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3438">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3438">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3439">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3439">See Also</span></span>

- <span data-ttu-id="30951-3440">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3440">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3441">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3441">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3442">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3442">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3443">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3443">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3444">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3444">fx_file_close</span></span>
- <span data-ttu-id="30951-3445">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3445">fx_file_create</span></span>
- <span data-ttu-id="30951-3446">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3446">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3447">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3447">fx_file_delete</span></span>
- <span data-ttu-id="30951-3448">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3448">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3449">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3449">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3450">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3450">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3451">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3451">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3452">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3452">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3453">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3453">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3454">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3454">fx_file_open</span></span>
- <span data-ttu-id="30951-3455">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3455">fx_file_read</span></span>
- <span data-ttu-id="30951-3456">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3456">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3457">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3457">fx_file_rename</span></span>
- <span data-ttu-id="30951-3458">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3458">fx_file_seek</span></span>
- <span data-ttu-id="30951-3459">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3459">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3460">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3460">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3461">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3461">fx_file_write</span></span>
- <span data-ttu-id="30951-3462">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3462">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3463">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3463">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3464">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3464">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3465">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3465">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-3466">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3466">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="30951-3467">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-3467">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="30951-3468">Obtém comprimento do nome Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3468">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3469">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3469">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="30951-3470">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3470">Description</span></span>

<span data-ttu-id="30951-3471">Este serviço obtém o comprimento do nome Unicode fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-3471">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="30951-3472">Um caracteres Unicode é representado por dois bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-3472">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="30951-3473">Um nome Unicode é uma série de caracteres Unicode de doisbytes terminados por dois bytes NULL (dois bytes de 0 valor).</span><span class="sxs-lookup"><span data-stu-id="30951-3473">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3474">*Este serviço é idêntico ao **fx_unicode_length_get()** exceto que o chamador passa no tamanho do tampão **unicode_name,** incluindo os dois caracteres NU.*</span><span class="sxs-lookup"><span data-stu-id="30951-3474">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3475">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3475">Input Parameters</span></span>

- <span data-ttu-id="30951-3476">**unicode_name**: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3476">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="30951-3477">**buffer_length**: Tamanho do tampão de nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3477">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3478">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3478">Return Values</span></span>

<span data-ttu-id="30951-3479">**comprimento**: Comprimento do nome Unicode (número de caracteres Unicode no nome).</span><span class="sxs-lookup"><span data-stu-id="30951-3479">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3480">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3480">Allowed From</span></span>

<span data-ttu-id="30951-3481">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3481">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3482">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3482">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3483">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3483">See Also</span></span>

- <span data-ttu-id="30951-3484">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3484">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3485">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3485">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3486">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3486">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3487">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3487">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3488">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3488">fx_file_close</span></span>
- <span data-ttu-id="30951-3489">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3489">fx_file_create</span></span>
- <span data-ttu-id="30951-3490">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3490">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3491">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3491">fx_file_delete</span></span>
- <span data-ttu-id="30951-3492">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3492">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3493">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3493">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3494">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3494">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3495">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3495">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3496">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3496">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3497">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3497">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3498">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3498">fx_file_open</span></span>
- <span data-ttu-id="30951-3499">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3499">fx_file_read</span></span>
- <span data-ttu-id="30951-3500">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3500">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3501">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3501">fx_file_rename</span></span>
- <span data-ttu-id="30951-3502">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3502">fx_file_seek</span></span>
- <span data-ttu-id="30951-3503">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3503">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3504">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3504">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3505">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3505">fx_file_write</span></span>
- <span data-ttu-id="30951-3506">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3506">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3507">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3507">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3508">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3508">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3509">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3509">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-3510">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3510">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="30951-3511">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3511">fx_unicode_name_get</span></span>

<span data-ttu-id="30951-3512">Obtém o nome Unicode de nome curto</span><span class="sxs-lookup"><span data-stu-id="30951-3512">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3513">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3513">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="30951-3514">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3514">Description</span></span>

<span data-ttu-id="30951-3515">Este serviço recupera o nome Unicode associado ao nome curto fornecido (formato 8.3) dentro do diretório predefinido atual — nenhuma informação sobre o caminho é permitida no parâmetro de nome curto.</span><span class="sxs-lookup"><span data-stu-id="30951-3515">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="30951-3516">Se for bem sucedido, o nome Unicode associado ao nome curto é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3516">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3517">*Este serviço pode ser utilizado para obter nomes unicode para ambos os ficheiros e subdireções.*</span><span class="sxs-lookup"><span data-stu-id="30951-3517">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3518">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3518">Input Parameters</span></span>

- <span data-ttu-id="30951-3519">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3519">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3520">**short_name** Ponteiro para nome curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-3520">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="30951-3521">**destination_unicode_name**: Ponter para o destino do nome Unicode associado ao nome curto fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-3521">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="30951-3522">**destination_unicode_length**: Ponteiro para devolver o comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3522">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3523">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3523">Return Values</span></span>

- <span data-ttu-id="30951-3524">**FX_SUCCESS** (0x00) Recuperação de nomes unicode bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-3524">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="30951-3525">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3525">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="30951-3526">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-3526">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-3527">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3527">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3528">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3528">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3529">**FX_NOT_FOUND** (0x04) Não foi encontrado nome curto ou o tamanho do destino Unicode é demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="30951-3529">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="30951-3530">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3530">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-3531">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3531">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3532">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3532">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3533">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3533">Allowed From</span></span>

<span data-ttu-id="30951-3534">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3535">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3535">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3536">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3536">See Also</span></span>

- <span data-ttu-id="30951-3537">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3537">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3538">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3538">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3539">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3539">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3540">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3540">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3541">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3541">fx_file_close</span></span>
- <span data-ttu-id="30951-3542">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3542">fx_file_create</span></span>
- <span data-ttu-id="30951-3543">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3543">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3544">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3544">fx_file_delete</span></span>
- <span data-ttu-id="30951-3545">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3545">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3546">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3546">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3547">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3547">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3548">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3548">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3549">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3549">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3550">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3550">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3551">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3551">fx_file_open</span></span>
- <span data-ttu-id="30951-3552">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3552">fx_file_read</span></span>
- <span data-ttu-id="30951-3553">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3553">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3554">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3554">fx_file_rename</span></span>
- <span data-ttu-id="30951-3555">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3555">fx_file_seek</span></span>
- <span data-ttu-id="30951-3556">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3556">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3557">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3557">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3558">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3558">fx_file_write</span></span>
- <span data-ttu-id="30951-3559">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3559">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3560">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3560">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3561">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3561">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3562">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3562">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="30951-3563">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-3563">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="30951-3564">Obtém o nome Unicode de nome curto</span><span class="sxs-lookup"><span data-stu-id="30951-3564">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3565">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3565">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="30951-3566">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3566">Description</span></span>

<span data-ttu-id="30951-3567">Este serviço recupera o nome Unicode associado ao nome curto fornecido (formato 8.3) dentro do diretório predefinido atual — nenhuma informação sobre o caminho é permitida no parâmetro de nome curto.</span><span class="sxs-lookup"><span data-stu-id="30951-3567">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="30951-3568">Se for bem sucedido, o nome Unicode associado ao nome curto é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3568">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3569">\*Este serviço é idêntico a \***fx_unicode_name_get,**_exceto que o chamador fornece o tamanho do tampão Unicode de destino como argumento de entrada. Isto permite que o serviço garanta que não substituirá o destino Unicode buffer_</span><span class="sxs-lookup"><span data-stu-id="30951-3569">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3570">*Este serviço pode ser utilizado para obter nomes unicode para ambos os ficheiros e subdireções.*</span><span class="sxs-lookup"><span data-stu-id="30951-3570">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3571">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3571">Input Parameters</span></span>

- <span data-ttu-id="30951-3572">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3572">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3573">**short_name**: Ponteiro para nome curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-3573">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="30951-3574">**destination_unicode_name**: Ponter para o destino do nome Unicode associado ao nome curto fornecido.</span><span class="sxs-lookup"><span data-stu-id="30951-3574">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="30951-3575">**destination_unicode_length**: Ponteiro para devolver o comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3575">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="30951-3576">**unicode_name_buffer_length**: Tamanho do tampão de nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3576">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="30951-3577">Nota: É necessário um exterminador NULO, o que faz um byte extra.</span><span class="sxs-lookup"><span data-stu-id="30951-3577">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3578">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3578">Return Values</span></span>

- <span data-ttu-id="30951-3579">**FX_SUCCESS** (0x00) Recuperação de nomes unicode bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-3579">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="30951-3580">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3580">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="30951-3581">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-3581">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-3582">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3582">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3583">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3583">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3584">**FX_NOT_FOUND** (0x04) Não foi encontrado nome curto ou o tamanho do destino Unicode é demasiado pequeno.</span><span class="sxs-lookup"><span data-stu-id="30951-3584">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="30951-3585">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3585">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-3586">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3586">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3587">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3587">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3588">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3588">Allowed From</span></span>

<span data-ttu-id="30951-3589">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3590">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3590">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3591">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3591">See Also</span></span>

- <span data-ttu-id="30951-3592">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3592">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3593">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3593">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3594">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3594">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3595">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3595">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3596">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3596">fx_file_close</span></span>
- <span data-ttu-id="30951-3597">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3597">fx_file_create</span></span>
- <span data-ttu-id="30951-3598">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3598">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3599">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3599">fx_file_delete</span></span>
- <span data-ttu-id="30951-3600">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3600">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3601">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3601">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3602">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3602">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3603">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3603">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3604">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3604">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3605">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3605">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3606">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3606">fx_file_open</span></span>
- <span data-ttu-id="30951-3607">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3607">fx_file_read</span></span>
- <span data-ttu-id="30951-3608">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3608">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3609">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3609">fx_file_rename</span></span>
- <span data-ttu-id="30951-3610">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3610">fx_file_seek</span></span>
- <span data-ttu-id="30951-3611">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3611">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3612">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3612">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3613">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3613">fx_file_write</span></span>
- <span data-ttu-id="30951-3614">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3614">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3615">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3615">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3616">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3616">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3617">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3617">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="30951-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3618">fx_unicode_short_name_get</span></span>

<span data-ttu-id="30951-3619">Obtém nome curto do nome Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3619">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3620">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3620">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="30951-3621">Este serviço recupera o nome curto (formato 8.3) associado ao nome Unicode dentro do diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3621">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="30951-3622">Se for bem sucedido, o nome curto associado ao nome Unicode é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3622">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3623">*Este serviço pode ser utilizado para obter nomes curtos para ficheiros e subdireções.*</span><span class="sxs-lookup"><span data-stu-id="30951-3623">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3624">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3624">Input Parameters</span></span>

- <span data-ttu-id="30951-3625">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3625">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3626">**source_unicode_name**: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3626">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="30951-3627">**source_unicode_length**: Comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3627">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="30951-3628">**destination_short_name**: Ponter para o destino para o nome curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-3628">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="30951-3629">Isto deve ter pelo menos 13 bytes de tamanho.</span><span class="sxs-lookup"><span data-stu-id="30951-3629">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3630">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3630">Return Values</span></span>

- <span data-ttu-id="30951-3631">**FX_SUCCESS** (0x00) Recuperação de nomes curtos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-3631">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="30951-3632">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3632">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="30951-3633">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-3633">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="30951-3634">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3634">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3635">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3635">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3636">**FX_NOT_FOUND** (0x04) Não foi encontrado o nome unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3636">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="30951-3637">**FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3637">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="30951-3638">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3638">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-3639">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3639">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3640">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3640">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3641">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3641">Allowed From</span></span>

<span data-ttu-id="30951-3642">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3642">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3643">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3643">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3644">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3644">See Also</span></span>

- <span data-ttu-id="30951-3645">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3645">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3646">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3646">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3647">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3648">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3648">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3649">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3649">fx_file_close</span></span>
- <span data-ttu-id="30951-3650">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3650">fx_file_create</span></span>
- <span data-ttu-id="30951-3651">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3651">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3652">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3652">fx_file_delete</span></span>
- <span data-ttu-id="30951-3653">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3653">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3654">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3654">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3655">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3655">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3656">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3656">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3657">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3657">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3658">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3658">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3659">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3659">fx_file_open</span></span>
- <span data-ttu-id="30951-3660">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3660">fx_file_read</span></span>
- <span data-ttu-id="30951-3661">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3661">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3662">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3662">fx_file_rename</span></span>
- <span data-ttu-id="30951-3663">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3663">fx_file_seek</span></span>
- <span data-ttu-id="30951-3664">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3664">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3665">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3665">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3666">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3666">fx_file_write</span></span>
- <span data-ttu-id="30951-3667">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3667">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3668">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3668">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3669">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3669">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3670">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3670">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="30951-3671">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="30951-3671">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="30951-3672">Obtém nome curto do nome Unicode</span><span class="sxs-lookup"><span data-stu-id="30951-3672">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="30951-3673">Prototype</span><span class="sxs-lookup"><span data-stu-id="30951-3673">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="30951-3674">Descrição</span><span class="sxs-lookup"><span data-stu-id="30951-3674">Description</span></span>

<span data-ttu-id="30951-3675">Este serviço recupera o nome curto (formato 8.3) associado ao nome Unicode dentro do diretório predefinido atual — nenhuma informação de caminho é permitida no parâmetro nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3675">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="30951-3676">Se for bem sucedido, o nome curto associado ao nome Unicode é devolvido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="30951-3676">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30951-3677">*Este serviço é idêntico ao **fx_unicode_short_name_get()**, exceto que o chamador fornece o tamanho do tampão de destino como argumento de entrada. Isto permite que o serviço garanta que o nome curto não exceda o tampão de destino.*</span><span class="sxs-lookup"><span data-stu-id="30951-3677">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="30951-3678">*Este serviço pode ser usado para obter nomes curtos para ambos os ficheiros e subdireções*</span><span class="sxs-lookup"><span data-stu-id="30951-3678">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30951-3679">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="30951-3679">Input Parameters</span></span>

- <span data-ttu-id="30951-3680">**media_ptr**: Ponter para o bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="30951-3680">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="30951-3681">**source_unicode_name**: Ponteiro para o nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3681">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="30951-3682">**source_unicode_length**: Comprimento do nome Unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3682">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="30951-3683">**destination_short_name**: Ponter para o destino para o nome curto (formato 8.3).</span><span class="sxs-lookup"><span data-stu-id="30951-3683">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="30951-3684">Isto deve ter pelo menos 13 bytes de tamanho.</span><span class="sxs-lookup"><span data-stu-id="30951-3684">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="30951-3685">**short_name_buffer_length**: Tamanho do tampão de destino.</span><span class="sxs-lookup"><span data-stu-id="30951-3685">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="30951-3686">O tamanho do tampão deve ser de, pelo menos, 14 bytes.</span><span class="sxs-lookup"><span data-stu-id="30951-3686">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="30951-3687">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="30951-3687">Return Values</span></span>

- <span data-ttu-id="30951-3688">**FX_SUCCESS** (0x00) Recuperação de nomes curtos bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="30951-3688">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="30951-3689">**FX_FAT_READ_ERROR** (0x03) Incapaz de ler a tabela FAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3689">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="30951-3690">**FX_FILE_CORRUPT** (0x08) File é corrompido</span><span class="sxs-lookup"><span data-stu-id="30951-3690">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="30951-3691">**FX_IO_ERROR** (0x90) Erro de I/O do condutor.</span><span class="sxs-lookup"><span data-stu-id="30951-3691">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="30951-3692">**FX_MEDIA_NOT_OPEN** (0x11) Os meios de comunicação especificados não estão abertos.</span><span class="sxs-lookup"><span data-stu-id="30951-3692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="30951-3693">**FX_NOT_FOUND** (0x04) Não foi encontrado o nome unicode.</span><span class="sxs-lookup"><span data-stu-id="30951-3693">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="30951-3694">**FX_NOT_IMPLEMENTED** (0x22) Serviço não implementado para o sistema de ficheiros exFAT.</span><span class="sxs-lookup"><span data-stu-id="30951-3694">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="30951-3695">**FX_SECTOR_INVALID** (0x89) Sector inválido.</span><span class="sxs-lookup"><span data-stu-id="30951-3695">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="30951-3696">**FX_PTR_ERROR** (0x18) Meios de comunicação inválidos ou ponteiros de nome.</span><span class="sxs-lookup"><span data-stu-id="30951-3696">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="30951-3697">**FX_CALLER_ERROR** (0x20) Caller não é um fio.</span><span class="sxs-lookup"><span data-stu-id="30951-3697">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30951-3698">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="30951-3698">Allowed From</span></span>

<span data-ttu-id="30951-3699">Fios</span><span class="sxs-lookup"><span data-stu-id="30951-3699">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30951-3700">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30951-3700">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="30951-3701">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30951-3701">See Also</span></span>

- <span data-ttu-id="30951-3702">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3702">fx_file_allocate</span></span>
- <span data-ttu-id="30951-3703">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="30951-3703">fx_file_attributes_read</span></span>
- <span data-ttu-id="30951-3704">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="30951-3704">fx_file_attributes_set</span></span>
- <span data-ttu-id="30951-3705">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3705">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3706">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="30951-3706">fx_file_close</span></span>
- <span data-ttu-id="30951-3707">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3707">fx_file_create</span></span>
- <span data-ttu-id="30951-3708">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="30951-3708">fx_file_date_time_set</span></span>
- <span data-ttu-id="30951-3709">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="30951-3709">fx_file_delete</span></span>
- <span data-ttu-id="30951-3710">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3710">fx_file_extended_allocate</span></span>
- <span data-ttu-id="30951-3711">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="30951-3711">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="30951-3712">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3712">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="30951-3713">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3713">fx_file_extended_seek</span></span>
- <span data-ttu-id="30951-3714">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3714">fx_file_extended_truncate</span></span>
- <span data-ttu-id="30951-3715">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3715">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="30951-3716">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="30951-3716">fx_file_open</span></span>
- <span data-ttu-id="30951-3717">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="30951-3717">fx_file_read</span></span>
- <span data-ttu-id="30951-3718">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3718">fx_file_relative_seek</span></span>
- <span data-ttu-id="30951-3719">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3719">fx_file_rename</span></span>
- <span data-ttu-id="30951-3720">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="30951-3720">fx_file_seek</span></span>
- <span data-ttu-id="30951-3721">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="30951-3721">fx_file_truncate</span></span>
- <span data-ttu-id="30951-3722">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="30951-3722">fx_file_truncate_release</span></span>
- <span data-ttu-id="30951-3723">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="30951-3723">fx_file_write</span></span>
- <span data-ttu-id="30951-3724">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="30951-3724">fx_file_write_notify_set</span></span>
- <span data-ttu-id="30951-3725">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="30951-3725">fx_unicode_file_create</span></span>
- <span data-ttu-id="30951-3726">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="30951-3726">fx_unicode_file_rename</span></span>
- <span data-ttu-id="30951-3727">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3727">fx_unicode_name_get</span></span>
- <span data-ttu-id="30951-3728">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="30951-3728">fx_unicode_short_name_get</span></span>
