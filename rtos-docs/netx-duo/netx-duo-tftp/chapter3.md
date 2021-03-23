---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo TFTP
description: Este capítulo contém uma descrição de todos os serviços NetX Duo TFTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 56f0d8edb991fff6ae30b6411e375ace58c544f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825706"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a><span data-ttu-id="d32d1-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-103">Chapter 3 - Description of Azure RTOS NetX Duo TFTP services</span></span>

<span data-ttu-id="d32d1-104">Este capítulo contém uma descrição de todos os serviços NetX Duo TFTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="d32d1-104">This chapter contains a description of all NetX Duo TFTP services (listed below) in alphabetic order.</span></span> <span data-ttu-id="d32d1-105">Salvo especificação em contrário, todos os serviços suportam comunicações IPv6 e IPv4.</span><span class="sxs-lookup"><span data-stu-id="d32d1-105">Unless otherwise specified, all services support IPv6 and IPv4 communications.</span></span>

<span data-ttu-id="d32d1-106">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="d32d1-106">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="d32d1-107">**nxd_tftp_client_file_open**: *Abrir ficheiro de cliente TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-107">**nxd_tftp_client_file_open**: *Open TFTP client file*</span></span>

- <span data-ttu-id="d32d1-108">**nxd_tftp_client_create**: *Criar uma instância de cliente TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-108">**nxd_tftp_client_create**: *Create a TFTP client instance*</span></span>

- <span data-ttu-id="d32d1-109">**nxd_tftp_client_delete**: *Eliminar uma instância do cliente TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-109">**nxd_tftp_client_delete**: *Delete a TFTP client instance*</span></span>

- <span data-ttu-id="d32d1-110">**nxd_tftp_client_error_info_get**: *Obtenha informações sobre erros do cliente*</span><span class="sxs-lookup"><span data-stu-id="d32d1-110">**nxd_tftp_client_error_info_get**: *Get client error information*</span></span>

- <span data-ttu-id="d32d1-111">**nxd_tftp_client_file_close**: *Arquivo de clientes próximo*</span><span class="sxs-lookup"><span data-stu-id="d32d1-111">**nxd_tftp_client_file_close**: *Close client file*</span></span>

- <span data-ttu-id="d32d1-112">**nxd_tftp_client_file_open**: *Arquivo de cliente aberto*</span><span class="sxs-lookup"><span data-stu-id="d32d1-112">**nxd_tftp_client_file_open**: *Open client file*</span></span>

- <span data-ttu-id="d32d1-113">**nxd_tftp_client_file_read**: *Leia um bloco do ficheiro do cliente*</span><span class="sxs-lookup"><span data-stu-id="d32d1-113">**nxd_tftp_client_file_read**: *Read a block from client file*</span></span>

- <span data-ttu-id="d32d1-114">**nxd_tftp_client_file_write**: *Escreva bloco para ficheiro de cliente*</span><span class="sxs-lookup"><span data-stu-id="d32d1-114">**nxd_tftp_client_file_write**: *Write block to client file*</span></span>

- <span data-ttu-id="d32d1-115">**nxd_tftp_client_packet_allocate**: *Atribuir pacote para escrita de ficheiros de clientes*</span><span class="sxs-lookup"><span data-stu-id="d32d1-115">**nxd_tftp_client_packet_allocate**: *Allocate packet for client file write*</span></span>

- <span data-ttu-id="d32d1-116">**nxd_tftp_client_set_interface**: *Definir a interface física para pedidos de TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-116">**nxd_tftp_client_set_interface**: *Set the physical interface for TFTP requests*</span></span>

- <span data-ttu-id="d32d1-117">**nxd_tftp_server_create**: *Criar servidor TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-117">**nxd_tftp_server_create**: *Create TFTP server*</span></span>

- <span data-ttu-id="d32d1-118">**nxd_tftp_server_delete**: *Eliminar o servidor TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-118">**nxd_tftp_server_delete**: *Delete TFTP server*</span></span>

- <span data-ttu-id="d32d1-119">**nxd_tftp_server_start**: *Iniciar o servidor TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-119">**nxd_tftp_server_start**: *Start TFTP server*</span></span>

- <span data-ttu-id="d32d1-120">**nxd_tftp_server_stop**: *Parar o servidor TFTP*</span><span class="sxs-lookup"><span data-stu-id="d32d1-120">**nxd_tftp_server_stop**: *Stop TFTP server*</span></span>

> [!NOTE] 
> <span data-ttu-id="d32d1-121">Os equivalentes IPv4 de todos os serviços acima listados estão disponíveis no NetX Duo TFTP Client and Server, por *exemplo, nx_tftp_server_create* e *nx_tftp_client_file_open*.</span><span class="sxs-lookup"><span data-stu-id="d32d1-121">The IPv4 equivalents of all the services listed above are available in NetX Duo TFTP Client and Server e.g. *nx_tftp_server_create* and *nx_tftp_client_file_open*.</span></span> <span data-ttu-id="d32d1-122">Apenas as descrições da API 'Duo', por exemplo, serviços a partir *de nxd_,* são fornecidas nas páginas seguintes.</span><span class="sxs-lookup"><span data-stu-id="d32d1-122">Only the ‘Duo’ API descriptions, e.g. services beginning with *nxd_*, are provided in the following pages.</span></span> <span data-ttu-id="d32d1-123">Quando uma entrada NXD_ADDRESS \* é especificada, a API equivalente IPv4 requer a entrada ULONG.</span><span class="sxs-lookup"><span data-stu-id="d32d1-123">Where an NXD_ADDRESS \* input is specified, the IPv4 equivalent API calls for ULONG input.</span></span> <span data-ttu-id="d32d1-124">Caso contrário, não há diferença na utilização da API.</span><span class="sxs-lookup"><span data-stu-id="d32d1-124">Otherwise there is no difference in using the API.</span></span>

## <a name="nxd_tftp_client_create"></a><span data-ttu-id="d32d1-125">nxd_tftp_client_create</span><span class="sxs-lookup"><span data-stu-id="d32d1-125">nxd_tftp_client_create</span></span>

<span data-ttu-id="d32d1-126">Criar uma instância de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-126">Create a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-127">Prototype</span></span>

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-128">Description</span></span>

<span data-ttu-id="d32d1-129">Este serviço cria uma instância do Cliente TFTP para a instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-129">This service creates a TFTP Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d32d1-130">A aplicação deve certificar-se de que o IP fornecido e o pool de pacotes já estão criados.</span><span class="sxs-lookup"><span data-stu-id="d32d1-130">The application must make certain the supplied IP and packet pool are already created.</span></span> <span data-ttu-id="d32d1-131">Além disso, a UDP deve ser ativada para a instância IP antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-131">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-132">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-132">Input Parameters</span></span>

- <span data-ttu-id="d32d1-133">**tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-133">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d32d1-134">**tftp_client_name** Nome desta instância do cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-134">**tftp_client_name** Name of this TFTP Client instance</span></span>

- <span data-ttu-id="d32d1-135">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-135">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="d32d1-136">**pool_ptr** Ponteiro para pacote piscina TFTP Caso do cliente.</span><span class="sxs-lookup"><span data-stu-id="d32d1-136">**pool_ptr** Pointer to packet pool TFTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-137">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-137">Return Values</span></span>

- <span data-ttu-id="d32d1-138">**NX_SUCCESS**(0x00) TFTP bem sucedido criar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-138">**NX_SUCCESS**(0x00) Successful TFTP create.</span></span>

- <span data-ttu-id="d32d1-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Versão IP inválida ou não suportada</span><span class="sxs-lookup"><span data-stu-id="d32d1-139">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid or unsupported IP version</span></span>

- <span data-ttu-id="d32d1-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Endereço IP do Servidor Inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-140">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP address received</span></span>

- <span data-ttu-id="d32d1-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Servidor ACK não recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-141">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Server ACK not received</span></span>

- <span data-ttu-id="d32d1-142">NX_PTR_ERROR (0x16) Inválido IP, pool ou ponteiro TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-142">NX_PTR_ERROR (0x16) Invalid IP, pool, or TFTP pointer.</span></span>

- <span data-ttu-id="d32d1-143">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="d32d1-143">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="d32d1-144">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-144">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-145">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-145">Allowed From</span></span>

<span data-ttu-id="d32d1-146">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="d32d1-146">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-147">Example</span></span>

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a><span data-ttu-id="d32d1-148">nxd_tftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="d32d1-148">nxd_tftp_client_delete</span></span>

<span data-ttu-id="d32d1-149">Eliminar uma instância do cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-149">Delete a TFTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-150">Prototype</span></span>

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-151">Description</span></span>

<span data-ttu-id="d32d1-152">Este serviço elimina uma instância do Cliente TFTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-152">This service deletes a previously created TFTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-153">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-153">Input Parameters</span></span>

- <span data-ttu-id="d32d1-154">**tftp_client_ptr** Ponteiro para a instância do cliente TFTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-154">**tftp_client_ptr** Pointer to previously created TFTP client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-155">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-155">Return Values</span></span>

- <span data-ttu-id="d32d1-156">**NX_SUCCESS** (0x00) Cliente TFTP bem sucedido apagar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-156">**NX_SUCCESS** (0x00) Successful TFTP Client delete.</span></span>

- <span data-ttu-id="d32d1-157">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-157">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-158">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-158">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-159">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-159">Allowed From</span></span>

<span data-ttu-id="d32d1-160">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-160">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-161">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-161">Example</span></span>

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a><span data-ttu-id="d32d1-162">nxd_tftp_client_error_info_get</span><span class="sxs-lookup"><span data-stu-id="d32d1-162">nxd_tftp_client_error_info_get</span></span>

<span data-ttu-id="d32d1-163">Obtenha informações de erro do cliente</span><span class="sxs-lookup"><span data-stu-id="d32d1-163">Get client error information</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-164">Prototype</span></span>

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a><span data-ttu-id="d32d1-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-165">Description</span></span>

<span data-ttu-id="d32d1-166">Este serviço devolve o último código de erro recebido e define o ponteiro para a cadeia de erro interna do cliente.</span><span class="sxs-lookup"><span data-stu-id="d32d1-166">This service returns the last error code received and sets the pointer to the client’s internal error string.</span></span> <span data-ttu-id="d32d1-167">Em condições de erro, o utilizador pode visualizar o último erro enviado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="d32d1-167">In error conditions, the user can view the last error sent by the server.</span></span> <span data-ttu-id="d32d1-168">Uma cadeia de erro nulo indica que não existe qualquer erro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-168">A null error string indicates no error is present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-169">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-169">Input Parameters</span></span>

- <span data-ttu-id="d32d1-170">**tftp_client_ptr** Ponteiro para a instância do cliente TFTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-170">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="d32d1-171">**error_code** Ponteiro para a área de destino para código de erro</span><span class="sxs-lookup"><span data-stu-id="d32d1-171">**error_code** Pointer to destination area for error code</span></span>

- <span data-ttu-id="d32d1-172">**error_string** Ponteiro para destino para cadeia de erro</span><span class="sxs-lookup"><span data-stu-id="d32d1-172">**error_string** Pointer to destination for error string</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-173">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-173">Return Values</span></span>

- <span data-ttu-id="d32d1-174">**NX_SUCCESS** (0x00) Informações de erro de sucesso da TFTP obtêm.</span><span class="sxs-lookup"><span data-stu-id="d32d1-174">**NX_SUCCESS** (0x00) Successful TFTP error info get.</span></span>  

- <span data-ttu-id="d32d1-175">NX_PTR_ERROR (0x16) Ponteiro do Cliente TFTP inválido.</span><span class="sxs-lookup"><span data-stu-id="d32d1-175">NX_PTR_ERROR (0x16) Invalid TFTP Client pointer.</span></span>

- <span data-ttu-id="d32d1-176">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-176">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-177">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-177">Allowed From</span></span>

<span data-ttu-id="d32d1-178">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-178">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-179">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-179">Example</span></span>

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a><span data-ttu-id="d32d1-180">nxd_tftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="d32d1-180">nxd_tftp_client_file_close</span></span>

<span data-ttu-id="d32d1-181">Arquivar ficheiro de cliente</span><span class="sxs-lookup"><span data-stu-id="d32d1-181">Close client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-182">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-182">Prototype</span></span>

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d32d1-183">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-183">Description</span></span>

<span data-ttu-id="d32d1-184">Este serviço encerra o ficheiro previamente aberto por esta instância do Cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-184">This service closes the previously opened file by this TFTP Client instance.</span></span> <span data-ttu-id="d32d1-185">Uma instância do Cliente TFTP é permitida a ter apenas um ficheiro aberto de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d32d1-185">A TFTP Client instance is allowed to have only one file open at a time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-186">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-186">Input Parameters</span></span>

- <span data-ttu-id="d32d1-187">**tftp_client_ptr** Ponteiro para a instância do cliente TFTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-187">**tftp_client_ptr** Pointer to previously created TFTP Client instance.</span></span>

- <span data-ttu-id="d32d1-188">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-188">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-189">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-189">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-190">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-190">Return Values</span></span>

- <span data-ttu-id="d32d1-191">**NX_SUCCESS** (0x00) TFTP bem sucedido fechar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-191">**NX_SUCCESS** (0x00) Successful TFTP file close.</span></span>

- <span data-ttu-id="d32d1-192">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-192">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-193">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-193">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="d32d1-194">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponte.</span><span class="sxs-lookup"><span data-stu-id="d32d1-194">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-195">Allowed From</span></span>

<span data-ttu-id="d32d1-196">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-197">Example</span></span>

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a><span data-ttu-id="d32d1-198">nx_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="d32d1-198">nx_tftp_client_file_open</span></span>

<span data-ttu-id="d32d1-199">Abrir ficheiro de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-199">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-200">Prototype</span></span>

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d32d1-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-201">Description</span></span>

<span data-ttu-id="d32d1-202">Este serviço tenta abrir o ficheiro especificado no Servidor TFTP no endereço IP especificado.</span><span class="sxs-lookup"><span data-stu-id="d32d1-202">This service attempts to open the specified file on the TFTP Server at the specified IP address.</span></span> <span data-ttu-id="d32d1-203">O ficheiro será aberto para leitura ou escrita.</span><span class="sxs-lookup"><span data-stu-id="d32d1-203">The file will be opened for either reading or writing.</span></span> 

> [!NOTE] 
> <span data-ttu-id="d32d1-204">Isto está limitado apenas a pacotes IPv4, e destina-se a apoiar aplicações NetX TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-204">This is limited to IPv4 packets only, and is intended for supporting NetX TFTP applications.</span></span> <span data-ttu-id="d32d1-205">Os desenvolvedores são encorajados a apresentar as suas aplicações para usar o serviço equivalente "duo" *nxd_tftp_client_file_open.*</span><span class="sxs-lookup"><span data-stu-id="d32d1-205">Developers are encouraged to port their applications to using equivalent “duo” service *nxd_tftp_client_file_open.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-206">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-206">Input Parameters</span></span>

- <span data-ttu-id="d32d1-207">**tftp_client_ptr** Ponteiro para o bloco de controlo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-207">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="d32d1-208">**file_name** Nome do ficheiro ASCII, nulo e com informações de percurso adequadas.</span><span class="sxs-lookup"><span data-stu-id="d32d1-208">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="d32d1-209">**server_ip_address** Endereço TFTP do servidor.</span><span class="sxs-lookup"><span data-stu-id="d32d1-209">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="d32d1-210">**open_type** Tipo de pedido aberto, também:</span><span class="sxs-lookup"><span data-stu-id="d32d1-210">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="d32d1-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="d32d1-211">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="d32d1-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="d32d1-212">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="d32d1-213">**wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro do Cliente TFTP aberto.</span><span class="sxs-lookup"><span data-stu-id="d32d1-213">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="d32d1-214">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d32d1-214">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d32d1-215">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d32d1-215">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d32d1-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d32d1-216">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span> 
  
  <span data-ttu-id="d32d1-217">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um Servidor TFTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="d32d1-217">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span> 
  
  <span data-ttu-id="d32d1-218">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-218">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="d32d1-219">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-219">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-220">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-220">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-221">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-221">Return Values</span></span>

- <span data-ttu-id="d32d1-222">**NX_SUCCESS** (0x00) Ficheiro de cliente bem sucedido aberto</span><span class="sxs-lookup"><span data-stu-id="d32d1-222">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="d32d1-223">**cliente NX_TFTP_NOT_CLOSED** (0xC3) já tem ficheiro aberto</span><span class="sxs-lookup"><span data-stu-id="d32d1-223">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="d32d1-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-224">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d32d1-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor</span><span class="sxs-lookup"><span data-stu-id="d32d1-225">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d32d1-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-226">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="d32d1-227">**NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-227">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d32d1-228">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-228">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-229">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-229">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-230">NX_IP_ADDRESS_ERROR (0x21) Endereço IP do servidor inválido</span><span class="sxs-lookup"><span data-stu-id="d32d1-230">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="d32d1-231">NX_OPTION_ERROR (0x0A) Tipo aberto inválido</span><span class="sxs-lookup"><span data-stu-id="d32d1-231">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-232">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-232">Allowed From</span></span>

<span data-ttu-id="d32d1-233">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-234">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a><span data-ttu-id="d32d1-235">nxd_tftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="d32d1-235">nxd_tftp_client_file_open</span></span>

<span data-ttu-id="d32d1-236">Abrir ficheiro de cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-236">Open TFTP client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-237">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-237">Prototype</span></span>

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d32d1-238">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-238">Description</span></span>

<span data-ttu-id="d32d1-239">Este serviço tenta abrir o ficheiro especificado no Servidor TFTP no endereço IPv6 especificado.</span><span class="sxs-lookup"><span data-stu-id="d32d1-239">This service attempts to open the specified file on the TFTP Server at the specified IPv6 address.</span></span> <span data-ttu-id="d32d1-240">O ficheiro será aberto para leitura ou escrita.</span><span class="sxs-lookup"><span data-stu-id="d32d1-240">The file will be opened for either reading or writing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-241">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-241">Input Parameters</span></span>

- <span data-ttu-id="d32d1-242">**tftp_client_ptr** Ponteiro para o bloco de controlo TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-242">**tftp_client_ptr** Pointer to TFTP control block.</span></span>

- <span data-ttu-id="d32d1-243">**file_name** Nome do ficheiro ASCII, nulo e com informações de percurso adequadas.</span><span class="sxs-lookup"><span data-stu-id="d32d1-243">**file_name** ASCII file name, NULL-terminated and with appropriate path information.</span></span>

- <span data-ttu-id="d32d1-244">**server_ip_address** Endereço TFTP do servidor.</span><span class="sxs-lookup"><span data-stu-id="d32d1-244">**server_ip_address** Server TFTP address.</span></span>

- <span data-ttu-id="d32d1-245">**open_type** Tipo de pedido aberto, também:</span><span class="sxs-lookup"><span data-stu-id="d32d1-245">**open_type** Type of open request, either:</span></span>

  <span data-ttu-id="d32d1-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span><span class="sxs-lookup"><span data-stu-id="d32d1-246">**NX_TFTP_OPEN_FOR_READ** (0x01)</span></span>

  <span data-ttu-id="d32d1-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span><span class="sxs-lookup"><span data-stu-id="d32d1-247">**NX_TFTP_OPEN_FOR_WRITE** (0x02)</span></span>

- <span data-ttu-id="d32d1-248">**wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro do Cliente TFTP aberto.</span><span class="sxs-lookup"><span data-stu-id="d32d1-248">**wait_option** Defines how long the service will wait for the TFTP Client file open.</span></span> <span data-ttu-id="d32d1-249">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d32d1-249">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d32d1-250">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d32d1-250">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d32d1-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d32d1-251">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d32d1-252">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que um Servidor TFTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="d32d1-252">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a TFTP Server responds to the request.</span></span>

  <span data-ttu-id="d32d1-253">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-253">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server response.</span></span>

- <span data-ttu-id="d32d1-254">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-254">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-255">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-255">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-256">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-256">Return Values</span></span>

- <span data-ttu-id="d32d1-257">**NX_SUCCESS** (0x00) Ficheiro de cliente bem sucedido aberto</span><span class="sxs-lookup"><span data-stu-id="d32d1-257">**NX_SUCCESS** (0x00) Successful Client file open</span></span>

- <span data-ttu-id="d32d1-258">**cliente NX_TFTP_NOT_CLOSED** (0xC3) já tem ficheiro aberto</span><span class="sxs-lookup"><span data-stu-id="d32d1-258">**NX_TFTP_NOT_CLOSED** (0xC3) Client already has file open</span></span>

- <span data-ttu-id="d32d1-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-259">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d32d1-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor</span><span class="sxs-lookup"><span data-stu-id="d32d1-260">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d32d1-261">**versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida</span><span class="sxs-lookup"><span data-stu-id="d32d1-261">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d32d1-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-262">**NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) Invalid Server IP received</span></span>

- <span data-ttu-id="d32d1-263">**NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-263">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d32d1-264">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-264">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-265">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-265">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-266">NX_IP_ADDRESS_ERROR (0x21) Endereço IP do servidor inválido</span><span class="sxs-lookup"><span data-stu-id="d32d1-266">NX_IP_ADDRESS_ERROR (0x21) Invalid Server IP address</span></span>

- <span data-ttu-id="d32d1-267">NX_OPTION_ERROR (0x0A) Tipo aberto inválido</span><span class="sxs-lookup"><span data-stu-id="d32d1-267">NX_OPTION_ERROR (0x0A) Invalid open type</span></span>

- <span data-ttu-id="d32d1-268">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="d32d1-268">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-269">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-269">Allowed From</span></span>

<span data-ttu-id="d32d1-270">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-270">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-271">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-271">Example</span></span>

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a><span data-ttu-id="d32d1-272">nxd_tftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="d32d1-272">nxd_tftp_client_file_read</span></span>

<span data-ttu-id="d32d1-273">Leia um bloco a partir do ficheiro do cliente</span><span class="sxs-lookup"><span data-stu-id="d32d1-273">Read a block from client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-274">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-274">Prototype</span></span>

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d32d1-275">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-275">Description</span></span>

<span data-ttu-id="d32d1-276">Este serviço lê um bloco de 512 bytes do ficheiro do Cliente TFTP previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="d32d1-276">This service reads a 512-byte block from the previously opened TFTP Client file.</span></span> <span data-ttu-id="d32d1-277">Um bloco contendo menos de 512 bytes sinaliza o fim do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-277">A block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-278">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-278">Input Parameters</span></span>

- <span data-ttu-id="d32d1-279">**tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-279">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d32d1-280">**packet_ptr** Destino para pacote que contenha o bloco lido a partir do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-280">**packet_ptr** Destination for packet containing the block read from the file.</span></span>

- <span data-ttu-id="d32d1-281">**wait_option** Define quanto tempo o serviço esperará que a leitura esteja concluída.</span><span class="sxs-lookup"><span data-stu-id="d32d1-281">**wait_option** Defines how long the service will wait for the read to complete.</span></span> <span data-ttu-id="d32d1-282">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d32d1-282">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d32d1-283">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d32d1-283">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d32d1-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d32d1-284">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d32d1-285">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor TFTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="d32d1-285">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>

  <span data-ttu-id="d32d1-286">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto espera que o servidor TFTP envie um bloco do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-286">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send a block of the file.</span></span>

- <span data-ttu-id="d32d1-287">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-287">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-288">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-288">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-289">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-289">Return Values</span></span>

- <span data-ttu-id="d32d1-290">**NX_SUCCESS** (0x00) Leitura de bloco de clientes bem sucedido</span><span class="sxs-lookup"><span data-stu-id="d32d1-290">**NX_SUCCESS** (0x00) Successful Client block read</span></span>

- <span data-ttu-id="d32d1-291">**NX_TFTP_NOT_OPEN** (0xC3) Ficheiro cliente especificado não está aberto para leitura</span><span class="sxs-lookup"><span data-stu-id="d32d1-291">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for reading</span></span>

- <span data-ttu-id="d32d1-292">**NX_NO_PACKET** (0x01) Nenhum pacote recebido do Servidor.</span><span class="sxs-lookup"><span data-stu-id="d32d1-292">**NX_NO_PACKET** (0x01) No Packet received from Server.</span></span>

- <span data-ttu-id="d32d1-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-293">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d32d1-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do Servidor</span><span class="sxs-lookup"><span data-stu-id="d32d1-294">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from Server</span></span>

- <span data-ttu-id="d32d1-295">**NX_TFTP_END_OF_FILE** (0xC5) Fim do ficheiro detetado (não um erro).</span><span class="sxs-lookup"><span data-stu-id="d32d1-295">**NX_TFTP_END_OF_FILE** (0xC5) End of file detected (not an error).</span></span>

- <span data-ttu-id="d32d1-296">**versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida</span><span class="sxs-lookup"><span data-stu-id="d32d1-296">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d32d1-297">**NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-297">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d32d1-298">**NX_TFTP_FAILED** (0xC2) Código TFTP desconhecido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-298">**NX_TFTP_FAILED** (0xC2) Unknown TFTP code received</span></span>

- <span data-ttu-id="d32d1-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Número de bloco inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-299">**NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) Invalid block number received</span></span>

- <span data-ttu-id="d32d1-300">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-300">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-301">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-301">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-302">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="d32d1-302">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-303">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-303">Allowed From</span></span>

<span data-ttu-id="d32d1-304">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-304">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-305">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-305">Example</span></span>

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a><span data-ttu-id="d32d1-306">nxd_tftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="d32d1-306">nxd_tftp_client_file_write</span></span>

<span data-ttu-id="d32d1-307">Escreva um bloco para o ficheiro cliente</span><span class="sxs-lookup"><span data-stu-id="d32d1-307">Write a block to Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-308">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-308">Prototype</span></span>

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d32d1-309">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-309">Description</span></span>

<span data-ttu-id="d32d1-310">Este serviço escreve um bloco de 512 bytes para o ficheiro do Cliente TFTP previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="d32d1-310">This service writes a 512-byte block to the previously opened TFTP Client file.</span></span> <span data-ttu-id="d32d1-311">Especificar um bloco que contenha menos de 512 bytes sinaliza o fim do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-311">Specifying a block containing fewer than 512 bytes signals the end of the file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-312">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-312">Input Parameters</span></span>

- <span data-ttu-id="d32d1-313">**tftp_client_ptr** Ponteiro para o bloco de controlo do cliente TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-313">**tftp_client_ptr** Pointer to TFTP Client control block.</span></span>

- <span data-ttu-id="d32d1-314">**packet_ptr** Pacote contendo o bloco para escrever para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d32d1-314">**packet_ptr** Packet containing the block to write to the file.</span></span>

- <span data-ttu-id="d32d1-315">**wait_option** Define quanto tempo o serviço esperará que a escrita esteja concluída.</span><span class="sxs-lookup"><span data-stu-id="d32d1-315">**wait_option** Defines how long the service will wait for the write to complete.</span></span> <span data-ttu-id="d32d1-316">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d32d1-316">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d32d1-317">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d32d1-317">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d32d1-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d32d1-318">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d32d1-319">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor TFTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="d32d1-319">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the TFTP Server responds to the request.</span></span>
 
  <span data-ttu-id="d32d1-320">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto espera que o servidor TFTP envie um ACK para o pedido de escrita.</span><span class="sxs-lookup"><span data-stu-id="d32d1-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the TFTP server to send an ACK for the write request.</span></span>

- <span data-ttu-id="d32d1-321">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-321">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-322">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-322">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-323">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-323">Return Values</span></span>

- <span data-ttu-id="d32d1-324">**NX_SUCCESS** (0x00) Escrita de bloco de cliente bem sucedido</span><span class="sxs-lookup"><span data-stu-id="d32d1-324">**NX_SUCCESS** (0x00) Successful Client block write</span></span>

- <span data-ttu-id="d32d1-325">**NX_TFTP_NOT_OPEN** (0xC3) Ficheiro cliente especificado não está aberto para escrita</span><span class="sxs-lookup"><span data-stu-id="d32d1-325">**NX_TFTP_NOT_OPEN** (0xC3) Specified Client file is not open for writing</span></span>

- <span data-ttu-id="d32d1-326">**NX_TFTP_TIMEOUT** (0xC1) Tempo limite à espera do Servidor ACK</span><span class="sxs-lookup"><span data-stu-id="d32d1-326">**NX_TFTP_TIMEOUT** (0xC1) Timeout waiting for Server ACK</span></span>

- <span data-ttu-id="d32d1-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-327">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d32d1-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) Nenhum ACK recebido do servidor</span><span class="sxs-lookup"><span data-stu-id="d32d1-328">**NX_TFTP_NO_ACK_RECEIVED** (0x09) No ACK received from server</span></span>

- <span data-ttu-id="d32d1-329">**versão IP** NX_TFTP_INVALID_IP_VERSION (0x0C) Inválida</span><span class="sxs-lookup"><span data-stu-id="d32d1-329">**NX_TFTP_INVALID_IP_VERSION** (0x0C) Invalid IP version</span></span>

- <span data-ttu-id="d32d1-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Endereço de servidor inválido recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-330">**NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) Invalid server address received</span></span>

- <span data-ttu-id="d32d1-331">**NX_TFTP_CODE_ERROR** (0x05) Código de erro recebido</span><span class="sxs-lookup"><span data-stu-id="d32d1-331">**NX_TFTP_CODE_ERROR** (0x05) Received error code</span></span>

- <span data-ttu-id="d32d1-332">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-332">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-333">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-333">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-334">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="d32d1-334">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-335">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-335">Allowed From</span></span>

<span data-ttu-id="d32d1-336">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-336">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-337">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-337">Example</span></span>

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a><span data-ttu-id="d32d1-338">nxd_tftp_client_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d32d1-338">nxd_tftp_client_packet_allocate</span></span>

<span data-ttu-id="d32d1-339">Pacote de atribuição para escrita de ficheiros do Cliente</span><span class="sxs-lookup"><span data-stu-id="d32d1-339">Allocate packet for Client file write</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-340">Prototype</span></span>

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a><span data-ttu-id="d32d1-341">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-341">Description</span></span>

<span data-ttu-id="d32d1-342">Este serviço atribui um pacote UDP da piscina de pacotes especificado e abre espaço para o cabeçalho TFTP de 4 bytes antes de o pacote ser devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="d32d1-342">This service allocates a UDP packet from the specified packet pool and makes room for the 4-byte TFTP header before the packet is returned to the caller.</span></span> <span data-ttu-id="d32d1-343">O chamador pode então construir um tampão para escrever para um ficheiro de cliente.</span><span class="sxs-lookup"><span data-stu-id="d32d1-343">The caller can then build a buffer for writing to a client file.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-344">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-344">Input Parameters</span></span>

- <span data-ttu-id="d32d1-345">**pool_ptr** Ponteiro para a piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="d32d1-345">**pool_ptr** Pointer to packet pool.</span></span>

- <span data-ttu-id="d32d1-346">**packet_ptr** Destino para ponteiro para pacote atribuído.</span><span class="sxs-lookup"><span data-stu-id="d32d1-346">**packet_ptr** Destination for pointer to allocated packet.</span></span>

- <span data-ttu-id="d32d1-347">**wait_option** Define quanto tempo o serviço esperará que o pacote alocado esteja concluído.</span><span class="sxs-lookup"><span data-stu-id="d32d1-347">**wait_option** Defines how long the service will wait for the packet allocate to complete.</span></span> <span data-ttu-id="d32d1-348">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d32d1-348">The wait options are defined as follows:</span></span>

  <span data-ttu-id="d32d1-349">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d32d1-349">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>

  <span data-ttu-id="d32d1-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d32d1-350">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

  <span data-ttu-id="d32d1-351">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que a atribuição termine.</span><span class="sxs-lookup"><span data-stu-id="d32d1-351">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the allocation completes.</span></span>

  <span data-ttu-id="d32d1-352">A seleção de um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a atribuição do pacote.</span><span class="sxs-lookup"><span data-stu-id="d32d1-352">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the packet allocation.</span></span>

- <span data-ttu-id="d32d1-353">**ip_type** Indicar qual o protocolo IP a utilizar.</span><span class="sxs-lookup"><span data-stu-id="d32d1-353">**ip_type** Indicate which IP protocol to use.</span></span> <span data-ttu-id="d32d1-354">As opções válidas são IPv4 (4) ou IPv6 (6).</span><span class="sxs-lookup"><span data-stu-id="d32d1-354">Valid options are IPv4 (4) or IPv6 (6).</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-355">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-355">Return Values</span></span>

- <span data-ttu-id="d32d1-356">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="d32d1-356">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>

- <span data-ttu-id="d32d1-357">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-357">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-358">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-358">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-359">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="d32d1-359">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-360">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-360">Allowed From</span></span>

<span data-ttu-id="d32d1-361">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-361">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-362">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-362">Example</span></span>

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a><span data-ttu-id="d32d1-363">nxd_tftp_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="d32d1-363">nxd_tftp_client_set_interface</span></span>

<span data-ttu-id="d32d1-364">Definir interface física para pedidos de TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-364">Set physical interface for TFTP requests</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-365">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-365">Prototype</span></span>

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a><span data-ttu-id="d32d1-366">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-366">Description</span></span>

<span data-ttu-id="d32d1-367">Este serviço utiliza o índice de interface de entrada para definir a interface física para o Cliente TFTP enviar e receber pacotes TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-367">This service uses the input interface index to set the physical interface for the TFTP Client to send and receive TFTP packets.</span></span> <span data-ttu-id="d32d1-368">O valor predefinido é zero, para a interface primária.</span><span class="sxs-lookup"><span data-stu-id="d32d1-368">The default value is zero, for the primary interface.</span></span>

> [!NOTE]
> <span data-ttu-id="d32d1-369">A NetX Duo deve suportar a endereçamento multihome (v5.6 ou posterior) para utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-369">NetX Duo must support multihome addressing (v5.6 or later) to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-370">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-370">Input Parameters</span></span>

- <span data-ttu-id="d32d1-371">**tftp_client_ptr** Ponteiro para a instância do cliente TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-371">**tftp_client_ptr** Pointer to TFTP Client instance</span></span>

- <span data-ttu-id="d32d1-372">**if_index** Índice de interface física a utilizar</span><span class="sxs-lookup"><span data-stu-id="d32d1-372">**if_index** Index of physical interface to use</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-373">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-373">Return Values</span></span>

- <span data-ttu-id="d32d1-374">**NX_SUCCESS** (0x00) Inserir interface inválida (0x0B)</span><span class="sxs-lookup"><span data-stu-id="d32d1-374">**NX_SUCCESS** (0x00) Successfully set interface (0x0B) Invalid interface input</span></span>

- <span data-ttu-id="d32d1-375">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-375">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-376">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-376">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="d32d1-377">NX_TFTP_INVALID_INTERFACE (0x0B) Entrada de interface inválida</span><span class="sxs-lookup"><span data-stu-id="d32d1-377">NX_TFTP_INVALID_INTERFACE (0x0B) Invalid interface input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-378">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-378">Allowed From</span></span>

<span data-ttu-id="d32d1-379">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-380">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-380">Example</span></span>

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a><span data-ttu-id="d32d1-381">nxd_tftp_server_create</span><span class="sxs-lookup"><span data-stu-id="d32d1-381">nxd_tftp_server_create</span></span>

<span data-ttu-id="d32d1-382">Criar servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-382">Create TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-383">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-383">Prototype</span></span>

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-384">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-384">Description</span></span>

<span data-ttu-id="d32d1-385">Este serviço cria um Servidor TFTP que responde aos pedidos do Cliente TFTP na porta 69.</span><span class="sxs-lookup"><span data-stu-id="d32d1-385">This service creates a TFTP Server that responds to TFTP Client requests on port 69.</span></span> <span data-ttu-id="d32d1-386">O Servidor deve ser iniciado por uma chamada subsequente para *nxd_tftp_server_start*.</span><span class="sxs-lookup"><span data-stu-id="d32d1-386">The Server must be started by a subsequent call to *nxd_tftp_server_start*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d32d1-387">A aplicação deve certificar-se de que a instância IP fornecida, o pool de pacotes e a instância de mídia FileX já estão criados.</span><span class="sxs-lookup"><span data-stu-id="d32d1-387">The application must make certain the supplied IP instance, packet pool, and FileX media instance are already created.</span></span> <span data-ttu-id="d32d1-388">Além disso, a UDP deve ser ativada para a instância IP antes de ligar para este serviço.</span><span class="sxs-lookup"><span data-stu-id="d32d1-388">In addition, UDP must be enabled for the IP instance prior to calling this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-389">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-389">Input Parameters</span></span>

- <span data-ttu-id="d32d1-390">**tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-390">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

- <span data-ttu-id="d32d1-391">**tftp_server_name** Nome desta instância do Servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-391">**tftp_server_name** Name of this TFTP Server instance</span></span>

- <span data-ttu-id="d32d1-392">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="d32d1-392">**ip_ptr** Pointer to previously created IP instance.</span></span>

- <span data-ttu-id="d32d1-393">**media_ptr** Pointer para a instância de media FileX.</span><span class="sxs-lookup"><span data-stu-id="d32d1-393">**media_ptr** Pointer to FileX media instance.</span></span>

- <span data-ttu-id="d32d1-394">**stack_ptr** Ponteiro para a área da pilha do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-394">**stack_ptr** Pointer to TFTP Server stack area.</span></span>

- <span data-ttu-id="d32d1-395">**stack_size** Número de bytes na pilha do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-395">**stack_size** Number of bytes in the TFTP Server stack.</span></span>

- <span data-ttu-id="d32d1-396">**pool_ptr** Ponteiro para a piscina de pacotes TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-396">**pool_ptr** Pointer to TFTP packet pool.</span></span> 

> [!NOTE]
> <span data-ttu-id="d32d1-397">A piscina fornecida deve ter cargas de pacote de pelo menos 580 bytes de tamanho. <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d32d1-397">The supplied pool must have packet payloads at least 580 bytes in size.<sup>1</sup></span></span>

<span data-ttu-id="d32d1-398"><sup>1</sup> A porção de dados de um pacote é exatamente 512 bytes, mas o tamanho da carga útil do pacote deve ser de pelo menos 572 bytes.</span><span class="sxs-lookup"><span data-stu-id="d32d1-398"><sup>1</sup> The data portion of a packet is exactly 512 bytes, but the packet payload size must be at least 572 bytes.</span></span> <span data-ttu-id="d32d1-399">Os bytes restantes são utilizados para os cabeçalhos UDP, IPv6 e Ethernet e potenciais bytes de trailing exigidos pelo condutor para o alinhamento.</span><span class="sxs-lookup"><span data-stu-id="d32d1-399">The remaining bytes are used for the UDP, IPv6, and Ethernet headers and potential trailing bytes required by the driver for alignment.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-400">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-400">Return Values</span></span>

- <span data-ttu-id="d32d1-401">**NX_SUCCESS** (0x00) Servidor de sucesso criar</span><span class="sxs-lookup"><span data-stu-id="d32d1-401">**NX_SUCCESS** (0x00) Successful Server create</span></span>

- <span data-ttu-id="d32d1-402">**NX_TFTP_POOL_ERROR** (0xC6) Piscina de pacotes tem tamanho de pacote inferior a 560 bytes</span><span class="sxs-lookup"><span data-stu-id="d32d1-402">**NX_TFTP_POOL_ERROR** (0xC6) Packet pool has packet size of less than 560 bytes</span></span>

- <span data-ttu-id="d32d1-403">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-403">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-404">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-404">Allowed From</span></span>

<span data-ttu-id="d32d1-405">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="d32d1-405">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-406">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-406">Example</span></span>

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a><span data-ttu-id="d32d1-407">nxd_tftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="d32d1-407">nxd_tftp_server_delete</span></span>

<span data-ttu-id="d32d1-408">Excluir o Servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-408">Delete TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-409">Prototype</span></span>

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-410">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-410">Description</span></span>

<span data-ttu-id="d32d1-411">Este serviço elimina um Servidor TFTP previamente criado.</span><span class="sxs-lookup"><span data-stu-id="d32d1-411">This service deletes a previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-412">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-412">Input Parameters</span></span>

- <span data-ttu-id="d32d1-413">**tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-413">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-414">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-414">Return Values</span></span>

- <span data-ttu-id="d32d1-415">**NX_SUCCESS** (0x00) Servidor de sucesso</span><span class="sxs-lookup"><span data-stu-id="d32d1-415">**NX_SUCCESS** (0x00) Successful Server delete</span></span>

- <span data-ttu-id="d32d1-416">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-416">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-417">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-417">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-418">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-418">Allowed From</span></span>

<span data-ttu-id="d32d1-419">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-419">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-420">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-420">Example</span></span>

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a><span data-ttu-id="d32d1-421">nxd_tftp_server_start</span><span class="sxs-lookup"><span data-stu-id="d32d1-421">nxd_tftp_server_start</span></span>

<span data-ttu-id="d32d1-422">Iniciar o servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-422">Start TFTP server</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-423">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-423">Prototype</span></span>

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-424">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-424">Description</span></span>

<span data-ttu-id="d32d1-425">Este serviço inicia o Servidor TFTP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="d32d1-425">This service starts the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-426">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-426">Input Parameters</span></span>

- <span data-ttu-id="d32d1-427">**tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-427">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-428">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-428">Return Values</span></span>

- <span data-ttu-id="d32d1-429">**NX_SUCCESS** (0x00) Início do servidor de sucesso</span><span class="sxs-lookup"><span data-stu-id="d32d1-429">**NX_SUCCESS** (0x00) Successful Server start</span></span>

- <span data-ttu-id="d32d1-430">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro .</span><span class="sxs-lookup"><span data-stu-id="d32d1-430">NX_PTR_ERROR (0x16) Invalid pointer input .</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="d32d1-431">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-431">Allowed From</span></span>

<span data-ttu-id="d32d1-432">Inicialização, fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-432">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-433">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-433">Example</span></span>

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a><span data-ttu-id="d32d1-434">nxd_tftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="d32d1-434">nxd_tftp_server_stop</span></span>

<span data-ttu-id="d32d1-435">Parar o servidor TFTP</span><span class="sxs-lookup"><span data-stu-id="d32d1-435">Stop TFTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d32d1-436">Prototype</span><span class="sxs-lookup"><span data-stu-id="d32d1-436">Prototype</span></span>

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="d32d1-437">Descrição</span><span class="sxs-lookup"><span data-stu-id="d32d1-437">Description</span></span>

<span data-ttu-id="d32d1-438">Este serviço para o Servidor TFTP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="d32d1-438">This service stops the previously created TFTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="d32d1-439">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="d32d1-439">Input Parameters</span></span>

- <span data-ttu-id="d32d1-440">**tftp_server_ptr** Ponteiro para o bloco de controlo do servidor TFTP.</span><span class="sxs-lookup"><span data-stu-id="d32d1-440">**tftp_server_ptr** Pointer to TFTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="d32d1-441">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="d32d1-441">Return Values</span></span>

- <span data-ttu-id="d32d1-442">**NX_SUCCESS** (0x00) paragem do servidor de sucesso</span><span class="sxs-lookup"><span data-stu-id="d32d1-442">**NX_SUCCESS** (0x00) Successful Server stop</span></span>

- <span data-ttu-id="d32d1-443">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="d32d1-443">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

- <span data-ttu-id="d32d1-444">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="d32d1-444">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d32d1-445">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="d32d1-445">Allowed From</span></span>

<span data-ttu-id="d32d1-446">Fios</span><span class="sxs-lookup"><span data-stu-id="d32d1-446">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d32d1-447">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d32d1-447">Example</span></span>

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```