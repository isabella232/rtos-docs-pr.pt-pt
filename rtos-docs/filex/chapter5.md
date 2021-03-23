---
title: Capítulo 5 - Condutores de E/S para Azure RTOS FileX
description: Este capítulo contém uma descrição dos controladores de I/S para O Azure RTOS FileX e foi concebido para ajudar os desenvolvedores a escrever condutores específicos da aplicação.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826539"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="2e704-103">Capítulo 5 - Condutores de E/S para Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="2e704-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="2e704-104">Este capítulo contém uma descrição dos controladores de I/S para O Azure RTOS FileX e foi concebido para ajudar os desenvolvedores a escrever condutores específicos da aplicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="2e704-105">Introdução do condutor de I/O</span><span class="sxs-lookup"><span data-stu-id="2e704-105">I/O Driver Introduction</span></span>

<span data-ttu-id="2e704-106">O FileX suporta vários dispositivos de mídia.</span><span class="sxs-lookup"><span data-stu-id="2e704-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="2e704-107">A estrutura FX_MEDIA define tudo o que é necessário para gerir um dispositivo de mídia.</span><span class="sxs-lookup"><span data-stu-id="2e704-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="2e704-108">Esta estrutura contém todas as informações dos meios de comunicação, incluindo o controlador de I/O específico dos meios de comunicação e parâmetros associados para a passagem de informações e estado entre o controlador e o FileX.</span><span class="sxs-lookup"><span data-stu-id="2e704-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="2e704-109">Na maioria dos sistemas, existe um controlador de E/S único para cada instância de media FileX.</span><span class="sxs-lookup"><span data-stu-id="2e704-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="2e704-110">Entrada do condutor I/O</span><span class="sxs-lookup"><span data-stu-id="2e704-110">I/O Driver Entry</span></span>

<span data-ttu-id="2e704-111">Cada controlador FileX I/O tem uma única função de entrada definida pela chamada de serviço ***fx_media_open.***</span><span class="sxs-lookup"><span data-stu-id="2e704-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="2e704-112">A função de entrada do controlador tem o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="2e704-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="2e704-113">O FileX chama a função de entrada do controlador de I/S para solicitar todo o acesso aos meios físicos, incluindo a inicialização e a leitura do setor de arranque.</span><span class="sxs-lookup"><span data-stu-id="2e704-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="2e704-114">Os pedidos feitos ao condutor são feitos sequencialmente; ou seja, o FileX aguarda que o pedido atual seja concluído antes de ser enviado outro pedido.</span><span class="sxs-lookup"><span data-stu-id="2e704-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="2e704-115">Pedidos de motorista de I/O</span><span class="sxs-lookup"><span data-stu-id="2e704-115">I/O Driver Requests</span></span>

<span data-ttu-id="2e704-116">Como cada controlador de E/S tem uma única função de entrada, o FileX faz pedidos específicos através do bloco de controlo de mídia.</span><span class="sxs-lookup"><span data-stu-id="2e704-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="2e704-117">Especificamente, o  **fx_media_driver_request** membro da **FX_MEDIA** é usado para especificar o pedido exato do condutor.</span><span class="sxs-lookup"><span data-stu-id="2e704-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="2e704-118">O condutor de I/S comunica o sucesso ou insucesso do pedido através do **fx_media_driver_status** membro da **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="2e704-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="2e704-119">Se o pedido do condutor tiver sido bem sucedido, **FX_SUCCESS** é colocado neste campo antes do retorno do condutor.</span><span class="sxs-lookup"><span data-stu-id="2e704-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="2e704-120">Caso contrário, se for detetado um erro, FX_IO_ERROR é colocado neste campo.</span><span class="sxs-lookup"><span data-stu-id="2e704-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="2e704-121">Inicialização do condutor</span><span class="sxs-lookup"><span data-stu-id="2e704-121">Driver Initialization</span></span>

<span data-ttu-id="2e704-122">Embora o processamento de inicialização do condutor real seja específico da aplicação, geralmente consiste na inicialização da estrutura de dados e possivelmente em alguma inicialização preliminar de hardware.</span><span class="sxs-lookup"><span data-stu-id="2e704-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="2e704-123">Este pedido é o primeiro feito pelo FileX e é feito a partir do serviço fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="2e704-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="2e704-124">Se for detetada proteção contra a escrita dos meios de comunicação, o condutor fx_media_driver_write_protect membro da FX_MEDIA deve ser definido para FX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="2e704-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="2e704-125">São utilizados os seguintes membros FX_MEDIA para o pedido de inicialização do condutor de E/S:</span><span class="sxs-lookup"><span data-stu-id="2e704-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="2e704-126">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-126">FX_MEDIA member</span></span>|<span data-ttu-id="2e704-127">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-128">fx_media_driver_request</span></span>|<span data-ttu-id="2e704-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="2e704-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="2e704-130">O FileX fornece um mecanismo para informar o controlador de aplicações quando os sectores já não estão a ser utilizados.</span><span class="sxs-lookup"><span data-stu-id="2e704-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="2e704-131">Isto é especialmente útil para os gestores de memória FLASH que devem gerir todos os sectores lógicos em uso mapeados para o FLASH.</span><span class="sxs-lookup"><span data-stu-id="2e704-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="2e704-132">Se tal notificação dos sectores livres for necessária, o condutor da aplicação limita-se a definir o campo *fx_media_driver_free_sector_update* na estrutura **FX_MEDIA** associada para **FX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="2e704-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="2e704-133">Depois de definido, o FileX faz uma **_chamada de_** controlador de I/S FX_DRIVER_RELEASE_SECTORS indicando quando um ou mais sectores consecutivos ficam livres.</span><span class="sxs-lookup"><span data-stu-id="2e704-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="2e704-134">Leitura do Setor de Arranque</span><span class="sxs-lookup"><span data-stu-id="2e704-134">Boot Sector Read</span></span>

<span data-ttu-id="2e704-135">Em vez de utilizar um pedido de leitura padrão, o FileX faz um pedido específico para ler o setor de arranque dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="2e704-136">São utilizados os seguintes **membros FX_MEDIA** para o pedido de arranque do condutor:</span><span class="sxs-lookup"><span data-stu-id="2e704-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="2e704-137">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-137">FX_MEDIA member</span></span>|<span data-ttu-id="2e704-138">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-139">fx_media_driver_request</span></span>| <span data-ttu-id="2e704-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="2e704-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="2e704-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="2e704-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="2e704-142">Endereço de destino para o setor de arranque.</span><span class="sxs-lookup"><span data-stu-id="2e704-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="2e704-143">Escrita do Setor de Arranque</span><span class="sxs-lookup"><span data-stu-id="2e704-143">Boot Sector Write</span></span>

<span data-ttu-id="2e704-144">Em vez de utilizar um pedido de escrita padrão, o FileX faz um pedido específico para escrever o setor de arranque dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="2e704-145">São utilizados os seguintes **membros FX_MEDIA** para o pedido de escrita do sector do arranque do condutor:</span><span class="sxs-lookup"><span data-stu-id="2e704-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="2e704-146">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-146">FX_MEDIA member</span></span>|<span data-ttu-id="2e704-147">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-148">fx_media_driver_request</span></span>| <span data-ttu-id="2e704-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="2e704-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="2e704-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="2e704-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="2e704-151">Endereço de fonte para o sector de arranque.</span><span class="sxs-lookup"><span data-stu-id="2e704-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="2e704-152">Leitura do Sector</span><span class="sxs-lookup"><span data-stu-id="2e704-152">Sector Read</span></span>

<span data-ttu-id="2e704-153">O FileX lê um ou mais sectores na memória ao emitir um pedido de leitura ao controlador de E/S.</span><span class="sxs-lookup"><span data-stu-id="2e704-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="2e704-154">São utilizados os seguintes **membros FX_MEDIA** para o pedido de leitura do controlador de E/S:</span><span class="sxs-lookup"><span data-stu-id="2e704-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="2e704-155">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-155">FX_MEDIA member</span></span>|<span data-ttu-id="2e704-156">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-157">fx_media_driver_request</span></span>| <span data-ttu-id="2e704-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="2e704-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="2e704-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="2e704-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="2e704-160">Setor lógico para ler</span><span class="sxs-lookup"><span data-stu-id="2e704-160">Logical sector to read</span></span>|
|<span data-ttu-id="2e704-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="2e704-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="2e704-162">Número de sectores a ler</span><span class="sxs-lookup"><span data-stu-id="2e704-162">Number of sectors to read</span></span>|
|<span data-ttu-id="2e704-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="2e704-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="2e704-164">Tampão de destino para o(s) sectorial(s) lido</span><span class="sxs-lookup"><span data-stu-id="2e704-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="2e704-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="2e704-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="2e704-166">Definido para FX_TRUE se um sector de dados de ficheiros for solicitado.</span><span class="sxs-lookup"><span data-stu-id="2e704-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="2e704-167">Caso contrário, FX_FALSE se for solicitado um sector de sistema (FAT ou sector de diretório).</span><span class="sxs-lookup"><span data-stu-id="2e704-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="2e704-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="2e704-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="2e704-169">Define o tipo explícito de sector solicitado, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2e704-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="2e704-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="2e704-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="2e704-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="2e704-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="2e704-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="2e704-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="2e704-173">Escrita sectorial</span><span class="sxs-lookup"><span data-stu-id="2e704-173">Sector Write</span></span>

<span data-ttu-id="2e704-174">FileX escreve um ou mais sectores para os meios físicos, emitindo um pedido de escrita ao controlador de I/S.</span><span class="sxs-lookup"><span data-stu-id="2e704-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="2e704-175">São utilizados os seguintes membros FX_MEDIA para o pedido de escrita do condutor de E/S:</span><span class="sxs-lookup"><span data-stu-id="2e704-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="2e704-176">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-176">FX_MEDIA member</span></span>| <span data-ttu-id="2e704-177">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-178">fx_media_driver_request</span></span>|<span data-ttu-id="2e704-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="2e704-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="2e704-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="2e704-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="2e704-181">Setor lógico para escrever</span><span class="sxs-lookup"><span data-stu-id="2e704-181">Logical sector to write</span></span>|
|<span data-ttu-id="2e704-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="2e704-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="2e704-183">Número de sectores a escrever</span><span class="sxs-lookup"><span data-stu-id="2e704-183">Number of sectors to write</span></span>|
|<span data-ttu-id="2e704-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="2e704-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="2e704-185">Tampão de origem para o sector(s) para escrever</span><span class="sxs-lookup"><span data-stu-id="2e704-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="2e704-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="2e704-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="2e704-187">Definido para FX_TRUE se for solicitado um sector do sistema (FAT ou sector do diretório).</span><span class="sxs-lookup"><span data-stu-id="2e704-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="2e704-188">Caso contrário, FX_FALSE se for solicitado um sector de dados de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="2e704-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="2e704-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="2e704-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="2e704-190">Define o tipo explícito de sector solicitado, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="2e704-190">Defines the explicit type of sector requested, as follows:</span></span>
<span data-ttu-id="2e704-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span><span class="sxs-lookup"><span data-stu-id="2e704-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span></span>

### <a name="driver-flush"></a><span data-ttu-id="2e704-192">Auto-descarga do condutor</span><span class="sxs-lookup"><span data-stu-id="2e704-192">Driver Flush</span></span>

<span data-ttu-id="2e704-193">O FileX descarrega todos os sectores atualmente na cache do sector do condutor para os meios físicos, emitindo um pedido de descarga ao condutor de I/O.</span><span class="sxs-lookup"><span data-stu-id="2e704-193">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="2e704-194">Naturalmente, se o condutor não estiver a fazer caching sectores, este pedido não requer processamento de condutor.</span><span class="sxs-lookup"><span data-stu-id="2e704-194">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="2e704-195">São utilizados os seguintes membros FX_MEDIA para o pedido de autoclismo do condutor:</span><span class="sxs-lookup"><span data-stu-id="2e704-195">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="2e704-196">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-196">FX_MEDIA member</span></span>| <span data-ttu-id="2e704-197">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-197">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-198">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-198">fx_media_driver_request</span></span>|<span data-ttu-id="2e704-199">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="2e704-199">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="2e704-200">Aborto do motorista</span><span class="sxs-lookup"><span data-stu-id="2e704-200">Driver Abort</span></span>

<span data-ttu-id="2e704-201">A FileX informa o condutor a abortar toda a atividade física de E/S com os meios físicos, emitindo um pedido de abortar ao controlador de I/O.</span><span class="sxs-lookup"><span data-stu-id="2e704-201">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="2e704-202">O condutor não deve voltar a efetuar qualquer E/S até ser re-inicializado.</span><span class="sxs-lookup"><span data-stu-id="2e704-202">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="2e704-203">São utilizados os seguintes membros FX_MEDIA para o pedido de aborto do condutor de E/S:</span><span class="sxs-lookup"><span data-stu-id="2e704-203">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="2e704-204">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-204">FX_MEDIA member</span></span>| <span data-ttu-id="2e704-205">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-205">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-206">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-206">fx_media_driver_request</span></span>| <span data-ttu-id="2e704-207">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="2e704-207">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="2e704-208">Sectores de Libertação</span><span class="sxs-lookup"><span data-stu-id="2e704-208">Release Sectors</span></span>

<span data-ttu-id="2e704-209">Se previamente selecionado pelo controlador durante a inicialização, o FileX informa o controlador sempre que um ou mais sectores consecutivos ficam livres.</span><span class="sxs-lookup"><span data-stu-id="2e704-209">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="2e704-210">Se o controlador for realmente um gestor FLASH, esta informação pode ser usada para dizer ao gestor flash que estes sectores já não são necessários.</span><span class="sxs-lookup"><span data-stu-id="2e704-210">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="2e704-211">São utilizados os seguintes **membros FX_MEDIA** para o pedido dos sectores de libertação de E/O:</span><span class="sxs-lookup"><span data-stu-id="2e704-211">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="2e704-212">FX_MEDIA membro</span><span class="sxs-lookup"><span data-stu-id="2e704-212">FX_MEDIA member</span></span>| <span data-ttu-id="2e704-213">Significado</span><span class="sxs-lookup"><span data-stu-id="2e704-213">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="2e704-214">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="2e704-214">fx_media_driver_request</span></span>|<span data-ttu-id="2e704-215">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="2e704-215">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="2e704-216">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="2e704-216">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="2e704-217">Início do setor livre</span><span class="sxs-lookup"><span data-stu-id="2e704-217">Start of free sector</span></span>|
|<span data-ttu-id="2e704-218">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="2e704-218">fx_media_driver_sectors</span></span>|<span data-ttu-id="2e704-219">Número de sectores livres</span><span class="sxs-lookup"><span data-stu-id="2e704-219">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="2e704-220">Suspensão do condutor</span><span class="sxs-lookup"><span data-stu-id="2e704-220">Driver Suspension</span></span>

<span data-ttu-id="2e704-221">Porque i/S com meios físicos pode levar algum tempo, suspender o fio de vocação é muitas vezes desejável.</span><span class="sxs-lookup"><span data-stu-id="2e704-221">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="2e704-222">É claro que isto pressupõe que a conclusão da operação de E/S subjacente é interrompida.</span><span class="sxs-lookup"><span data-stu-id="2e704-222">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="2e704-223">Em caso afirmativo, a suspensão do fio é facilmente implementada com um semáforo ThreadX.</span><span class="sxs-lookup"><span data-stu-id="2e704-223">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="2e704-224">Após iniciar a operação de entrada ou saída, o controlador de I/S suspende o seu próprio semáforo de I/O interno (criado com uma contagem inicial de zero durante a inicialização do condutor).</span><span class="sxs-lookup"><span data-stu-id="2e704-224">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="2e704-225">Como parte do processo de interrupção de conclusão do condutor, o mesmo semáforo de I/O está definido, o que por sua vez acorda o fio suspenso.</span><span class="sxs-lookup"><span data-stu-id="2e704-225">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="2e704-226">Tradução do Sector</span><span class="sxs-lookup"><span data-stu-id="2e704-226">Sector Translation</span></span>

<span data-ttu-id="2e704-227">Como o FileX vê os meios como sectores lógicos lineares, os pedidos de E/S feitos ao condutor de I/O são feitos com sectores lógicos.</span><span class="sxs-lookup"><span data-stu-id="2e704-227">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="2e704-228">É da responsabilidade do condutor traduzir entre sectores lógicos e a geometria física dos meios de comunicação social, que podem incluir cabeças, pistas e sectores físicos.</span><span class="sxs-lookup"><span data-stu-id="2e704-228">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="2e704-229">Para os meios de comunicação flash e RAM, os sectores lógicos normalmente mapeiam o diretório para sectores físicos.</span><span class="sxs-lookup"><span data-stu-id="2e704-229">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="2e704-230">Em todo o caso, aqui estão as fórmulas típicas para executar o mapeamento lógico para o setor físico no condutor de E/S:</span><span class="sxs-lookup"><span data-stu-id="2e704-230">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="2e704-231">Note-se que os sectores físicos começam em um, enquanto os sectores lógicos começam a zero.</span><span class="sxs-lookup"><span data-stu-id="2e704-231">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="2e704-232">Sectores Ocultos</span><span class="sxs-lookup"><span data-stu-id="2e704-232">Hidden Sectors</span></span>

<span data-ttu-id="2e704-233">Os sectores ocultos residiam antes do recorde de arranque nos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-233">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="2e704-234">Por estarem realmente fora do âmbito do esquema do sistema de ficheiros FAT, devem ser contabilizados em cada operação do sector lógico que o condutor faz.</span><span class="sxs-lookup"><span data-stu-id="2e704-234">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="2e704-235">Media Write Protect</span><span class="sxs-lookup"><span data-stu-id="2e704-235">Media Write Protect</span></span>

<span data-ttu-id="2e704-236">O controlador FileX pode ligar a escrever proteger definindo o campo fx_media_driver_write_protect no bloco de controlo dos meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-236">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="2e704-237">Isto causará a devolvição de um erro se alguma chamada do FileX for feita numa tentativa de escrever para os meios de comunicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-237">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="2e704-238">Condutor de RAM de amostra</span><span class="sxs-lookup"><span data-stu-id="2e704-238">Sample RAM Driver</span></span>

<span data-ttu-id="2e704-239">O sistema de demonstração FileX é entregue com um pequeno controlador de disco RAM, que é definido no ficheiro fx_ram_driver.c.</span><span class="sxs-lookup"><span data-stu-id="2e704-239">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="2e704-240">O condutor assume um espaço de memória de 32K e cria um recorde de arranque para 256 sectores de 128 bytes.</span><span class="sxs-lookup"><span data-stu-id="2e704-240">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="2e704-241">Este ficheiro fornece um bom exemplo de como implementar controladores específicos do FileX I/O da aplicação.</span><span class="sxs-lookup"><span data-stu-id="2e704-241">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
