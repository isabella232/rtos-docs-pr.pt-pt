---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX FTP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX FTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826720"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a><span data-ttu-id="c9fb7-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-103">Chapter 3 - Description of Azure RTOS NetX FTP services</span></span>

<span data-ttu-id="c9fb7-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX FTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-104">This chapter contains a description of all Azure RTOS NetX FTP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="c9fb7-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="c9fb7-106">**nx_ftp_client_connect**: *Ligue-se ao servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-106">**nx_ftp_client_connect**: *Connect to FTP Server*</span></span>
- <span data-ttu-id="c9fb7-107">**nx_ftp_client_create**: *Criar uma instância de cliente FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-107">**nx_ftp_client_create**: *Create an FTP Client instance*</span></span>
- <span data-ttu-id="c9fb7-108">**nx_ftp_client_delete**: *Eliminar uma instância de cliente FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-108">**nx_ftp_client_delete**: *Delete an FTP Client instance*</span></span>
- <span data-ttu-id="c9fb7-109">**nx_ftp_client_directory_create**: *Criar um diretório no Servidor*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-109">**nx_ftp_client_directory_create**: *Create a directory on Server*</span></span>
- <span data-ttu-id="c9fb7-110">**nx_ftp_client_directory_default_set**: *Definir diretório predefinido no Servidor*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-110">**nx_ftp_client_directory_default_set**: *Set default directory on Server*</span></span>
- <span data-ttu-id="c9fb7-111">**nx_ftp_client_directory_delete**: *Eliminar um diretório no Servidor*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-111">**nx_ftp_client_directory_delete**: *Delete a directory on Server*</span></span>
- <span data-ttu-id="c9fb7-112">**nx_ftp_client_directory_listing_get**: *Obtenha listagem de diretórios do Server*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-112">**nx_ftp_client_directory_listing_get**: *Get directory listing from Server*</span></span>
- <span data-ttu-id="c9fb7-113">**nx_ftp_client_directory_listing_continue**: *Continue a listar de diretórios do Server*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-113">**nx_ftp_client_directory_listing_continue**: *Continue directory listing from Server*</span></span>
- <span data-ttu-id="c9fb7-114">**nx_ftp_client_disconnect**: *Desligar do servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-114">**nx_ftp_client_disconnect**: *Disconnect from FTP Server*</span></span>
- <span data-ttu-id="c9fb7-115">**nx_ftp_client_file_close**: *Arquivo de clientes próximos*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-115">**nx_ftp_client_file_close**: *Close Client file*</span></span>
- <span data-ttu-id="c9fb7-116">**nx_ftp_client_file_delete**: *Eliminar ficheiro no Servidor*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-116">**nx_ftp_client_file_delete**: *Delete file on Server*</span></span>
- <span data-ttu-id="c9fb7-117">**nx_ftp_client_file_open**: *Ficheiro Open Client*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-117">**nx_ftp_client_file_open**: *Open Client file*</span></span>
- <span data-ttu-id="c9fb7-118">**nx_ftp_client_file_read**: *Ler a partir de arquivo*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-118">**nx_ftp_client_file_read**: *Read from file*</span></span>
- <span data-ttu-id="c9fb7-119">**nx_ftp_client_file_rename**: *Rebatize o ficheiro no Servidor*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-119">**nx_ftp_client_file_rename**: *Rename file on Server*</span></span>
- <span data-ttu-id="c9fb7-120">**nx_ftp_client_file_write**: *Escreva para arquivar*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-120">**nx_ftp_client_file_write**: *Write to file*</span></span>
- <span data-ttu-id="c9fb7-121">**nx_ftp_server_create**: *Criar servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-121">**nx_ftp_server_create**: *Create FTP Server*</span></span>
- <span data-ttu-id="c9fb7-122">**nx_ftp_server_delete**: *Eliminar servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-122">**nx_ftp_server_delete**: *Delete FTP Server*</span></span>
- <span data-ttu-id="c9fb7-123">**nx_ftp_server_start**: *Iniciar o servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-123">**nx_ftp_server_start**: *Start FTP Server*</span></span>
- <span data-ttu-id="c9fb7-124">**nx_ftp_server_stop**: *Parar o servidor FTP*</span><span class="sxs-lookup"><span data-stu-id="c9fb7-124">**nx_ftp_server_stop**: *Stop FTP Server*</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="c9fb7-125">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="c9fb7-125">nx_ftp_client_connect</span></span>

<span data-ttu-id="c9fb7-126">Ligue-se a um servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-126">Connect to an FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-127">Prototype</span></span>

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-128">Description</span></span>

<span data-ttu-id="c9fb7-129">Este serviço liga a instância do Cliente FTP previamente criada ao Servidor FTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-129">This service connects the previously created FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-130">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-130">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-131">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-131">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-132">**server_ip**: Endereço IP do FtP Server.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-132">**server_ip**: IP address of FTP Server.</span></span>
- <span data-ttu-id="c9fb7-133">**nome de utilizador**: Nome de utilizador do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-133">**username**: Client username for authentication.</span></span>
- <span data-ttu-id="c9fb7-134">**palavra-passe**: Senha do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-134">**password**: Client password for authentication.</span></span>
- <span data-ttu-id="c9fb7-135">**wait_option**: Define quanto tempo o serviço aguarda pela ligação do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-135">**wait_option**: Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="c9fb7-136">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-136">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-137">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-137">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-138">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-139">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-139">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-140">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-140">Return Values</span></span>

- <span data-ttu-id="c9fb7-141">**NX_SUCCESS:**(0x00) Ligação FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-141">**NX_SUCCESS**: (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="c9fb7-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Não conseguiu uma resposta de 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-142">**NX_TFTP_EXPECTED_22X_CODE**: (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="c9fb7-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Não conseguiu uma resposta 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-143">**NX_FTP_EXPECTED_23X_CODE**: (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="c9fb7-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Não conseguiu uma resposta 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-144">**NX_FTP_EXPECTED_33X_CODE**: (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="c9fb7-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) O cliente já está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-145">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="c9fb7-146">NX_PTR_ERROR: (0x07) Inválido inout do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-146">NX_PTR_ERROR: (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="c9fb7-147">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-147">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="c9fb7-148">NX_IP_ADDRESS_ERROR: (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-148">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-149">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-149">Allowed From</span></span>

<span data-ttu-id="c9fb7-150">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-150">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-151">Example</span></span>

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a><span data-ttu-id="c9fb7-152">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="c9fb7-152">nx_ftp_client_create</span></span>

<span data-ttu-id="c9fb7-153">Criar uma instância de cliente FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-153">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-154">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-154">Prototype</span></span>

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="c9fb7-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-155">Description</span></span>

<span data-ttu-id="c9fb7-156">Este serviço cria uma instância de cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-156">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-157">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-157">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-158">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-158">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-159">**ftp_client_name**: Nome do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-159">**ftp_client_name**: Name of FTP Client.</span></span>
- <span data-ttu-id="c9fb7-160">**ip_ptr**: Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-160">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="c9fb7-161">**window_size**: Tamanho da janela anunciado para tomada TCP deste Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-161">**window_size**: Advertised window size for TCP socket of this FTP Client.</span></span>
- <span data-ttu-id="c9fb7-162">**pool_ptr**: Ponter para o pacote predefinido para este Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-162">**pool_ptr**: Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="c9fb7-163">Note que a carga útil mínima do pacote deve ser suficientemente grande para manter o caminho completo e o ficheiro ou o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-163">Note that the minimum packet payload must be large enough to hold complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-164">Return Values</span></span>

- <span data-ttu-id="c9fb7-165">**NX_SUCCESS:**(0x00) Cliente FTP bem sucedido criar.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-165">**NX_SUCCESS**: (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="c9fb7-166">NX_PTR_ERROR: (0x16) FTP inválido, ponteiro IP ou ponteiro de piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-166">NX_PTR_ERROR: (0x16) Invalid FTP, IP pointer, or packet pool pointer.</span></span> <span data-ttu-id="c9fb7-167">ponteiro de senha.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-167">password pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-168">Allowed From</span></span>

<span data-ttu-id="c9fb7-169">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="c9fb7-169">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-170">Example</span></span>

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="c9fb7-171">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c9fb7-171">nx_ftp_client_delete</span></span>

<span data-ttu-id="c9fb7-172">Excluir uma instância de cliente FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-172">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-173">Prototype</span></span>

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="c9fb7-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-174">Description</span></span>

<span data-ttu-id="c9fb7-175">Este serviço elimina uma instância do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-175">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-176">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-176">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-177">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-177">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-178">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-178">Return Values</span></span>

- <span data-ttu-id="c9fb7-179">**NX_SUCCESS:**(0x00) O cliente FTP bem sucedido apaga.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-179">**NX_SUCCESS**: (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="c9fb7-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) Erro de exclusão do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-180">**NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP Client delete error.</span></span>
- <span data-ttu-id="c9fb7-181">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-181">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-182">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-182">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-183">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-183">Allowed From</span></span>

<span data-ttu-id="c9fb7-184">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-185">Example</span></span>

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="c9fb7-186">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="c9fb7-186">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="c9fb7-187">Criar um diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-187">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-188">Prototype</span></span>

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-189">Description</span></span>

<span data-ttu-id="c9fb7-190">Este serviço cria o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-190">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-191">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-191">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-192">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-192">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-193">**directory_name**: Nome do diretório para criar.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-193">**directory_name**: Name of directory to create.</span></span>
- <span data-ttu-id="c9fb7-194">**wait_option**: Define quanto tempo o serviço vai esperar pela criação do diretório FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-194">**wait_option**: Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="c9fb7-195">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-195">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-196">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-196">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-197">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-198">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-198">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-199">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-199">Return Values</span></span>

- <span data-ttu-id="c9fb7-200">**NX_SUCCESS**: (0x00) Diretório FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-200">**NX_SUCCESS**: (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="c9fb7-201">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-201">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-202">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="c9fb7-203">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-203">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="c9fb7-204">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-205">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-205">Allowed From</span></span>

<span data-ttu-id="c9fb7-206">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-206">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-207">Example</span></span>

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="c9fb7-208">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="c9fb7-208">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="c9fb7-209">Definir diretório predefinido no Servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-209">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-210">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-210">Prototype</span></span>

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-211">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-211">Description</span></span>

<span data-ttu-id="c9fb7-212">Este serviço define o diretório predefinido no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-212">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c9fb7-213">Este diretório predefinido aplica-se apenas à ligação deste cliente.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-213">This default directory applies only to this client's connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-214">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-214">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-215">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-215">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-216">**directory_path**: Nome do caminho do diretório a definir.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-216">**directory_path**: Name of directory path to set.</span></span>
- <span data-ttu-id="c9fb7-217">**wait_option**: Define quanto tempo o serviço irá esperar pelo conjunto de diretórios padrão FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-217">**wait_option**: Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="c9fb7-218">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-218">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-219">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-219">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-220">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-221">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-221">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-222">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-222">Return Values</span></span>

- <span data-ttu-id="c9fb7-223">**NX_SUCCESS**: (0x00) Conjunto padrão FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-223">**NX_SUCCESS**: (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="c9fb7-224">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-224">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-225">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="c9fb7-226">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-226">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="c9fb7-227">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-227">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-228">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-228">Allowed From</span></span>

<span data-ttu-id="c9fb7-229">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-230">Example</span></span>

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="c9fb7-231">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="c9fb7-231">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="c9fb7-232">Eliminar diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-232">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-233">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-233">Prototype</span></span>

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-234">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-234">Description</span></span>

<span data-ttu-id="c9fb7-235">Este serviço elimina o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-235">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-236">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-236">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-237">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-237">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-238">**directory_name**: Nome do diretório para apagar.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-238">**directory_name**: Name of directory to delete.</span></span>
- <span data-ttu-id="c9fb7-239">**wait_option**: Define quanto tempo o serviço esperará pela eliminação do diretório FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-239">**wait_option**: Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="c9fb7-240">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-240">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-241">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-241">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-242">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-243">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-243">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-244">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-244">Return Values</span></span>

- <span data-ttu-id="c9fb7-245">**NX_SUCCESS**: (0x00) Um diretório FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-245">**NX_SUCCESS**: (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="c9fb7-246">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-246">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-247">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span> 
- <span data-ttu-id="c9fb7-248">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-248">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span> 
- <span data-ttu-id="c9fb7-249">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-249">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-250">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-250">Allowed From</span></span>

<span data-ttu-id="c9fb7-251">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-252">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-252">Example</span></span>

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="c9fb7-253">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="c9fb7-253">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="c9fb7-254">Obtenha listagem de diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-254">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-255">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-255">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-256">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-256">Description</span></span>

<span data-ttu-id="c9fb7-257">Este serviço obtém o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-257">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c9fb7-258">O ponteiro do pacote fornecido conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-258">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="c9fb7-259">Cada entrada é separada por uma &lt; combinação cr/lf\</span><span class="sxs-lookup"><span data-stu-id="c9fb7-259">Each entry is separated by a &lt;cr/lf\combination.</span></span> <span data-ttu-id="c9fb7-260">O ***nx_ftp_client_directory_listing_continue***: deve ser chamado para concluir a operação do diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-260">The ***nx_ftp_client_directory_listing_continue***: should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-261">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-261">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-262">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-262">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-263">**directory_name**: Nome do diretório para obter conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-263">**directory_name**: Name of directory to get contents of.</span></span>
- <span data-ttu-id="c9fb7-264">**packet_ptr**: Ponteiro para o ponteiro do pacote de destino.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-264">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="c9fb7-265">Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-265">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="c9fb7-266">**wait_option**: Define quanto tempo o serviço aguarda pela lista geminada FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-266">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="c9fb7-267">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-267">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-268">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-268">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-269">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-270">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-270">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-271">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-271">Return Values</span></span>

- <span data-ttu-id="c9fb7-272">**NX_SUCCESS**: (0x00) Lista de diretórios FTP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-272">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="c9fb7-273">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-273">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-274">**NX_NOT_ENABLED:**(0x14) Serviço (IPv6) não ativado</span><span class="sxs-lookup"><span data-stu-id="c9fb7-274">**NX_NOT_ENABLED**: (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="c9fb7-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Não conseguiu uma resposta de 1XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-275">**NX_FTP_EXPECTED_1XX_CODE**: (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-276">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-277">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-277">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-278">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-278">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-279">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-279">Allowed From</span></span>

<span data-ttu-id="c9fb7-280">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-281">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-281">Example</span></span>

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="c9fb7-282">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="c9fb7-282">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="c9fb7-283">Continue a listar de diretórios do FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-283">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-284">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-284">Prototype</span></span>

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-285">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-285">Description</span></span>

<span data-ttu-id="c9fb7-286">Este serviço continua a obter o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-286">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="c9fb7-287">Deveria ter sido imediatamente precedido por uma chamada para ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-287">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="c9fb7-288">Se for bem sucedido, o ponteiro do pacote fornecido conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-288">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="c9fb7-289">Esta rotina deve ser chamada até que um estado de NX_FTP_END_OF_LISTING seja recebido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-289">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-290">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-290">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-291">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-291">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-292">**packet_ptr**: Ponteiro para o ponteiro do pacote de destino.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-292">**packet_ptr**: Pointer to destination packet pointer.</span></span> <span data-ttu-id="c9fb7-293">Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório, separadas por um &lt; cr/lf &gt; .</span><span class="sxs-lookup"><span data-stu-id="c9fb7-293">If successful, the packet payload will contain one or more directory entries, separated by a &lt;cr/lf&gt;.</span></span>
- <span data-ttu-id="c9fb7-294">**wait_option**: Define quanto tempo o serviço aguarda pela lista geminada FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-294">**wait_option**: Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="c9fb7-295">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-295">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-296">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-296">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-297">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-298">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-298">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-299">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-299">Return Values</span></span>

- <span data-ttu-id="c9fb7-300">**NX_SUCCESS**: (0x00) Lista de diretórios FTP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-300">**NX_SUCCESS**: (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="c9fb7-301">**NX_FTP_END_OF_LISTING**: (0xD8) Não há mais inscrições neste diretório.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-301">**NX_FTP_END_OF_LISTING**: (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="c9fb7-302">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-302">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-303">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-304">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-304">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-305">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-305">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-306">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-306">Allowed From</span></span>

<span data-ttu-id="c9fb7-307">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-308">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-308">Example</span></span>

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="c9fb7-309">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="c9fb7-309">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="c9fb7-310">Desligar do Servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-310">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-311">Prototype</span></span>

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-312">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-312">Description</span></span>

<span data-ttu-id="c9fb7-313">Este serviço desliga uma ligação ftp server previamente estabelecida com o cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-313">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-314">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-314">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-315">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-315">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-316">**wait_option**: Define quanto tempo o serviço esperará pela desconexão do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-316">**wait_option**: Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="c9fb7-317">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-317">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-318">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-318">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-319">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-320">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-320">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-321">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-321">Return Values</span></span>

- <span data-ttu-id="c9fb7-322">**NX_SUCCESS**: (0x00) Desconexão FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-322">**NX_SUCCESS**: (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="c9fb7-323">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-323">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-324">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-325">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-325">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-326">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-327">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-327">Allowed From</span></span>

<span data-ttu-id="c9fb7-328">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-329">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-329">Example</span></span>

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="c9fb7-330">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="c9fb7-330">nx_ftp_client_file_close</span></span>

<span data-ttu-id="c9fb7-331">Arquivar ficheiro do Cliente</span><span class="sxs-lookup"><span data-stu-id="c9fb7-331">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-332">Prototype</span></span>

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-333">Description</span></span>

<span data-ttu-id="c9fb7-334">Este serviço fecha um ficheiro previamente aberto no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-334">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-335">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-335">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-336">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-336">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-337">**wait_option**: Define quanto tempo o serviço irá esperar pelo fecho do ficheiro do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-337">**wait_option**: Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="c9fb7-338">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-338">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-339">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-339">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-340">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-341">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-341">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-342">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-342">Return Values</span></span>

- <span data-ttu-id="c9fb7-343">**NX_SUCCESS**: (0x00) Arquivo FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-343">**NX_SUCCESS**: (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="c9fb7-344">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-344">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-345">**NX_FTP_NOT_OPEN (0xD5)**: Arquivo não aberto; não pode fechá-lo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-345">**NX_FTP_NOT_OPEN (0xD5)**: File not open; cannot close it</span></span>
- <span data-ttu-id="c9fb7-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-346">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-347">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-347">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-348">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-348">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-349">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-349">Allowed From</span></span>

<span data-ttu-id="c9fb7-350">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-351">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-351">Example</span></span>

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="c9fb7-352">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="c9fb7-352">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="c9fb7-353">Eliminar ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-353">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-354">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-354">Prototype</span></span>

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-355">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-355">Description</span></span>

<span data-ttu-id="c9fb7-356">Este serviço elimina o ficheiro especificado no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-356">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-357">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-357">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-358">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-358">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-359">**file_name**: Nome do ficheiro para eliminar.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-359">**file_name**: Name of file to delete.</span></span>
- <span data-ttu-id="c9fb7-360">**wait_option**: Define quanto tempo o serviço esperará pela eliminação do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-360">**wait_option**: Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="c9fb7-361">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-361">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-362">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-362">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-363">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-364">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-364">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-365">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-365">Return Values</span></span>

- <span data-ttu-id="c9fb7-366">**NX_SUCCESS:**(0x00) Eliminar ficheiros FTP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-366">**NX_SUCCESS**: (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="c9fb7-367">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-367">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-368">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-369">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-369">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-370">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-371">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-371">Allowed From</span></span>

<span data-ttu-id="c9fb7-372">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-373">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-373">Example</span></span>

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="c9fb7-374">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="c9fb7-374">nx_ftp_client_file_open</span></span>

<span data-ttu-id="c9fb7-375">Abre o ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-375">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-376">Prototype</span></span>

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-377">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-377">Description</span></span>

<span data-ttu-id="c9fb7-378">Este serviço abre o ficheiro especificado – para leitura ou escrita – no Servidor FTP anteriormente ligado à instância de Cliente especificada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-378">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-379">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-379">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-380">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-380">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-381">**file_name**: Nome do ficheiro a abrir.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-381">**file_name**: Name of file to open.</span></span>
- <span data-ttu-id="c9fb7-382">**open_type:** **NX_FTP_OPEN_FOR_READ** ou **NX_FTP_OPEN_FOR_WRITE**.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-382">**open_type**: Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="c9fb7-383">**wait_option**: Define quanto tempo o serviço irá esperar pelo ficheiro FTP Client aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-383">**wait_option**: Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="c9fb7-384">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-384">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-385">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-385">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-386">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-387">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-387">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-388">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-388">Return Values</span></span>

- <span data-ttu-id="c9fb7-389">**NX_SUCCESS**: (0x00) Arquivo FTP bem sucedido aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-389">**NX_SUCCESS**: (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="c9fb7-390">**NX_OPTION_ERROR:**(0x0A) Tipo aberto inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-390">**NX_OPTION_ERROR**: (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="c9fb7-391">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-391">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-392">**NX_FTP_NOT_CLOSED**: (0xD6) O Cliente FTP já está aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-392">**NX_FTP_NOT_CLOSED**: (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="c9fb7-393">**NX_NO_FREE_PORTS**: (0x45) Não há portas TCP disponíveis para atribuir</span><span class="sxs-lookup"><span data-stu-id="c9fb7-393">**NX_NO_FREE_PORTS**: (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="c9fb7-394">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-394">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-395">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-395">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-396">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-396">Allowed From</span></span>

<span data-ttu-id="c9fb7-397">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-398">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-398">Example</span></span>

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="c9fb7-399">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="c9fb7-399">nx_ftp_client_file_read</span></span>

<span data-ttu-id="c9fb7-400">Ler a partir de arquivo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-400">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-401">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-401">Prototype</span></span>

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-402">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-402">Description</span></span>

<span data-ttu-id="c9fb7-403">Este serviço lê um pacote de um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-403">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="c9fb7-404">Deve ser chamado repetidamente até que um estatuto de NX_FTP_END_OF_FILE seja recebido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-404">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="c9fb7-405">Note que o autor da chamada não atribui um pacote para este serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-405">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="c9fb7-406">Só precisa fornecer um ponteiro para um ponteiro de pacote.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-406">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="c9fb7-407">Este serviço atualizará o ponteiro do pacote para apontar para um pacote recuperado da fila de receção da tomada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-407">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="c9fb7-408">Se um estado de sucesso for devolvido, isso significa que havia um pacote disponível, e é da responsabilidade do ouvinte libertar o pacote quando este é feito com ele.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-408">If a successful status is returned, that means there was a packet available, and it is the caller's responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="c9fb7-409">Se for devolvido um estado não zero (ou um estado de erro ou NX_FTP_END_OF_FILE) não libertar o pacote.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-409">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="c9fb7-410">Caso contrário, gera-se um erro quando o ponteiro do pacote é NU.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-410">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-411">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-411">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-412">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-412">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-413">**packet_ptr**: Ponter para o destino para o ponteiro do pacote de dados recuperado da fila.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-413">**packet_ptr**: Pointer to destination for the data packet pointer retrieved from the queue.</span></span> <span data-ttu-id="c9fb7-414">Se for bem sucedido, os dados do pacote contêm alguns ou todos os ficheiros.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-414">If successful, the packet data contains some or all of the file.</span></span>
- <span data-ttu-id="c9fb7-415">**wait_option**: Define quanto tempo o serviço irá esperar pela leitura do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-415">**wait_option**: Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="c9fb7-416">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-416">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-417">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-417">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-418">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-419">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-419">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-420">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-420">Return Values</span></span>

- <span data-ttu-id="c9fb7-421">**NX_SUCCESS**: (0x00) Leitura de ficheiro FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-421">**NX_SUCCESS**: (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="c9fb7-422">**NX_FTP_NOT_OPEN**: (0xD5) O Cliente FTP não está aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-422">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="c9fb7-423">**NX_FTP_END_OF_FILE**: (0xD7) Fim da condição do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-423">**NX_FTP_END_OF_FILE**: (0xD7) End of file condition.</span></span>
- <span data-ttu-id="c9fb7-424">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-424">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-425">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-425">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-426">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-426">Allowed From</span></span>

<span data-ttu-id="c9fb7-427">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-428">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-428">Example</span></span>

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="c9fb7-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="c9fb7-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="c9fb7-430">Rebatize o ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="c9fb7-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-431">Prototype</span></span>

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-432">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-432">Description</span></span>

<span data-ttu-id="c9fb7-433">Este serviço renomea um ficheiro no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-434">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-434">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-435">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-435">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-436">**nome de arquivo**: Nome atual do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-436">**filename**: Current name of file.</span></span>
- <span data-ttu-id="c9fb7-437">**new_filename**: Novo nome para arquivo.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-437">**new_filename**: New name for file.</span></span>
- <span data-ttu-id="c9fb7-438">**wait_option**: Define quanto tempo o serviço irá esperar pelo nome do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-438">**wait_option**: Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="c9fb7-439">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-440">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-440">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-441">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-442">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-442">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-443">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-443">Return Values</span></span>

- <span data-ttu-id="c9fb7-444">**NX_SUCCESS**: (0x00) Renomeado ficheiro FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-444">**NX_SUCCESS**: (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="c9fb7-445">**NX_FTP_NOT_CONNECTED**: (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-445">**NX_FTP_NOT_CONNECTED**: (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="c9fb7-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Não recebeu resposta 3XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-446">**NX_FTP_EXPECTED_3XX_CODE**: (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-447">**NX_FTP_EXPECTED_2XX_CODE**: (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="c9fb7-448">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-448">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-449">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-449">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-450">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-450">Allowed From</span></span>

<span data-ttu-id="c9fb7-451">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-452">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-452">Example</span></span>

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="c9fb7-453">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="c9fb7-453">nx_ftp_client_file_write</span></span>

<span data-ttu-id="c9fb7-454">Escrever para arquivar</span><span class="sxs-lookup"><span data-stu-id="c9fb7-454">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-455">Prototype</span></span>

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="c9fb7-456">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-456">Description</span></span>

<span data-ttu-id="c9fb7-457">Este serviço escreve um pacote de dados para o ficheiro previamente aberto no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-457">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-458">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-458">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-459">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-459">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-460">**packet_ptr**: Ponteiro de pacote contendo dados para escrever.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-460">**packet_ptr**: Packet pointer containing data to write.</span></span>
- <span data-ttu-id="c9fb7-461">**wait_option**: Define quanto tempo o serviço esperará pela escrita do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-461">**wait_option**: Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="c9fb7-462">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c9fb7-462">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c9fb7-463">**valor de tempo limite:**(0x00000001 até 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c9fb7-463">**timeout value**: (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c9fb7-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-464">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span> <span data-ttu-id="c9fb7-465">Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaque para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-465">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-466">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-466">Return Values</span></span>

- <span data-ttu-id="c9fb7-467">**NX_SUCCESS**: (0x00) Escrita de ficheiro FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-467">**NX_SUCCESS**: (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="c9fb7-468">**NX_FTP_NOT_OPEN**: (0xD5) O Cliente FTP não está aberto.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-468">**NX_FTP_NOT_OPEN**: (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="c9fb7-469">NX_PTR_ERROR: (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-469">NX_PTR_ERROR: (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-470">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-470">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-471">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-471">Allowed From</span></span>

<span data-ttu-id="c9fb7-472">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-473">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-473">Example</span></span>

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="c9fb7-474">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="c9fb7-474">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="c9fb7-475">Ativar ou desativar o modo de transferência passiva</span><span class="sxs-lookup"><span data-stu-id="c9fb7-475">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-476">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-476">Prototype</span></span>

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="c9fb7-477">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-477">Description</span></span>

<span data-ttu-id="c9fb7-478">Este serviço permite o modo de transferência passiva se a entrada passive_mode_enabled estiver definida para NX_TRUE numa instância ftp do Cliente previamente criada, de modo a que as chamadas subsequentes para ler ou escrever ficheiros (RETR, STOR) ou descarregue uma lista de diretórios (NLST) sejam feitas em modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-478">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="c9fb7-479">Para desativar a transferência do modo passivo e voltar ao comportamento predefinido do modo de transferência ativo, ligue para esta função com o passive_mode_enabled conjunto de entrada para NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-479">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-480">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-480">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-481">**ftp_client_ptr**: Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-481">**ftp_client_ptr**: Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="c9fb7-482">**passive_mode_enabled:**</span><span class="sxs-lookup"><span data-stu-id="c9fb7-482">**passive_mode_enabled**:</span></span>
  - <span data-ttu-id="c9fb7-483">Se estiver definido para NX_TRUE, o modo passivo está ativado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-483">If set to NX_TRUE, passive mode is enabled.</span></span>
  - <span data-ttu-id="c9fb7-484">Se estiver definido para NX_FALSE, o modo passivo é desativado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-484">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-485">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-485">Return Values</span></span>

- <span data-ttu-id="c9fb7-486">**NX_SUCCESS**: (0x00) Conjunto de modo passivo bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-486">**NX_SUCCESS**: (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="c9fb7-487">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-487">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-488">NX_INVALID_PARAMETERS: (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c9fb7-488">NX_INVALID_PARAMETERS: (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-489">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-489">Allowed From</span></span>

<span data-ttu-id="c9fb7-490">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-491">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-491">Example</span></span>

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="c9fb7-492">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="c9fb7-492">nx_ftp_server_create</span></span>

<span data-ttu-id="c9fb7-493">Criar servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-493">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-494">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-494">Prototype</span></span>

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="c9fb7-495">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-495">Description</span></span>

<span data-ttu-id="c9fb7-496">Este serviço cria uma instância FTP Server na instância IP do NetX especificada e previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-496">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="c9fb7-497">Note que o Servidor FTP precisa de ser iniciado com uma chamada para ***nx_ftp_server_start*** para que comece a funcionar.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-497">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-498">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-498">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-499">**ftp_server_ptr**: Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-499">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="c9fb7-500">**ftp_server_name**: Nome do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-500">**ftp_server_name**: Name of FTP Server.</span></span>
- <span data-ttu-id="c9fb7-501">**ip_ptr**: Ponteiro para a instância IP do NetX associado.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-501">**ip_ptr**: Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="c9fb7-502">Note que só pode haver um Servidor FTP para uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-502">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="c9fb7-503">**media_ptr**: Ponteiro para a instância de media filex associada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-503">**media_ptr**: Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="c9fb7-504">**stack_ptr**: Pontear para a memória para a área interna da pilha do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-504">**stack_ptr**: Pointer to memory for the internal FTP Server thread's stack area.</span></span>
- <span data-ttu-id="c9fb7-505">**stack_size**: Tamanho da área de pilhas especificada por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-505">**stack_size**: Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="c9fb7-506">**pool_ptr**: Ponteiro para o pacote netx predefinido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-506">**pool_ptr**: Pointer to default NetX packet pool.</span></span> <span data-ttu-id="c9fb7-507">Note que o tamanho da carga útil dos pacotes na piscina deve ser grande o suficiente para acomodar o maior nome/caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-507">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="c9fb7-508">**ftp_login**: Função ponteiro para a função de login da aplicação.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-508">**ftp_login**: Function pointer to application's login function.</span></span> <span data-ttu-id="c9fb7-509">Esta função é fornecida o nome de utilizador e a palavra-passe do Cliente solicitando uma ligação.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-509">This function is supplied the username and password from the Client requesting a connection.</span></span> <span data-ttu-id="c9fb7-510">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-510">If this is valid, the application's login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="c9fb7-511">**ftp_logout**: Função ponteiro para a função de logout da aplicação.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-511">**ftp_logout**: Function pointer to application's logout function.</span></span> <span data-ttu-id="c9fb7-512">Esta função é fornecida com o nome de utilizador e palavra-passe do Cliente solicitando uma desconexão.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-512">This function is supplied the username and password from the Client requesting a disconnection.</span></span> <span data-ttu-id="c9fb7-513">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-513">If this is valid, the application's login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-514">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-514">Return Values</span></span>

- <span data-ttu-id="c9fb7-515">**NX_SUCCESS:**(0x00) Servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-515">**NX_SUCCESS**: (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="c9fb7-516">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-516">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-517">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-517">Allowed From</span></span>

<span data-ttu-id="c9fb7-518">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="c9fb7-518">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-519">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-519">Example</span></span>

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="c9fb7-520">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="c9fb7-520">nx_ftp_server_delete</span></span>

<span data-ttu-id="c9fb7-521">Excluir servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-521">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-522">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-522">Prototype</span></span>

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c9fb7-523">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-523">Description</span></span>

<span data-ttu-id="c9fb7-524">Este serviço elimina uma instância ftp server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-524">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-525">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-525">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-526">**ftp_server_ptr**: Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-526">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-527">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-527">Return Values</span></span>

- <span data-ttu-id="c9fb7-528">**NX_SUCCESS**: (0x00) Servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-528">**NX_SUCCESS**: (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="c9fb7-529">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-529">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-530">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-530">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-531">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-531">Allowed From</span></span>

<span data-ttu-id="c9fb7-532">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-533">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-533">Example</span></span>

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="c9fb7-534">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="c9fb7-534">nx_ftp_server_start</span></span>

<span data-ttu-id="c9fb7-535">Iniciar servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-535">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-536">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-536">Prototype</span></span>

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c9fb7-537">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-537">Description</span></span>

<span data-ttu-id="c9fb7-538">Este serviço inicia uma instância ftp server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-538">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-539">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-539">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-540">**ftp_server_ptr**: Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-540">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-541">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-541">Return Values</span></span>

- <span data-ttu-id="c9fb7-542">**NX_SUCCESS**: (0x00) Arranque do servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-542">**NX_SUCCESS**: (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="c9fb7-543">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-543">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-544">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-544">Allowed From</span></span>

<span data-ttu-id="c9fb7-545">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="c9fb7-545">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-546">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-546">Example</span></span>

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="c9fb7-547">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="c9fb7-547">nx_ftp_server_stop</span></span>

<span data-ttu-id="c9fb7-548">Parar o servidor FTP</span><span class="sxs-lookup"><span data-stu-id="c9fb7-548">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="c9fb7-549">Prototype</span><span class="sxs-lookup"><span data-stu-id="c9fb7-549">Prototype</span></span>

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="c9fb7-550">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9fb7-550">Description</span></span>

<span data-ttu-id="c9fb7-551">Este serviço para uma instância ftp server previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-551">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c9fb7-552">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c9fb7-552">Input Parameters</span></span>

- <span data-ttu-id="c9fb7-553">**ftp_server_ptr**: Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-553">**ftp_server_ptr**: Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="c9fb7-554">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c9fb7-554">Return Values</span></span>

- <span data-ttu-id="c9fb7-555">**NX_SUCCESS**: (0x00) Paragem do servidor FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-555">**NX_SUCCESS**: (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="c9fb7-556">NX_PTR_ERROR: (0x16) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-556">NX_PTR_ERROR: (0x16) Invalid FTP pointer.</span></span>
- <span data-ttu-id="c9fb7-557">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="c9fb7-557">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c9fb7-558">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c9fb7-558">Allowed From</span></span>

<span data-ttu-id="c9fb7-559">Fios</span><span class="sxs-lookup"><span data-stu-id="c9fb7-559">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c9fb7-560">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9fb7-560">Example</span></span>

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
