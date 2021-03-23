---
title: Capítulo 3 - Descrição dos serviços FTP
description: Este capítulo contém uma descrição de todos os serviços NetX FTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825981"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="a04e7-103">Capítulo 3 - Descrição dos serviços FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="a04e7-104">Este capítulo contém uma descrição de todos os serviços NetX FTP (listados abaixo) por ordem alfabética (exceto nos casos em que os equivalentes IPv4 e IPv6 do mesmo serviço são emparelhados).</span><span class="sxs-lookup"><span data-stu-id="a04e7-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="a04e7-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="a04e7-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="a04e7-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="a04e7-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="a04e7-107">Ligue-se a um servidor FTP sobre o IPv4</span><span class="sxs-lookup"><span data-stu-id="a04e7-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-109">Description</span></span>

<span data-ttu-id="a04e7-110">Este serviço liga a instância do Cliente NetX FTP previamente criada ao Servidor FTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-111">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-111">Input Parameters</span></span>

- <span data-ttu-id="a04e7-112">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-113">**server_ip** Endereço IP do FTP Server.</span><span class="sxs-lookup"><span data-stu-id="a04e7-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="a04e7-114">**nome de utilizador** Nome de utilizador do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="a04e7-115">**senha** Senha do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="a04e7-116">**wait_option** Define quanto tempo o serviço irá esperar pela ligação ftp cliente.</span><span class="sxs-lookup"><span data-stu-id="a04e7-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="a04e7-117">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-118">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-120">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-120">Return Values</span></span>

- <span data-ttu-id="a04e7-121">**NX_SUCCESS** (0x00) Ligação FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="a04e7-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="a04e7-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Não conseguiu uma resposta de 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="a04e7-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Não conseguiu uma resposta 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="a04e7-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Não conseguiu uma resposta 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="a04e7-125">**NX_FTP_NOT_DISCONNECTED** cliente (0xD4) já está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="a04e7-126">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a04e7-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="a04e7-127">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a04e7-128">NX_IP_ADDRESS_ERROR (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-129">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-129">Allowed From</span></span>

<span data-ttu-id="a04e7-130">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="a04e7-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a04e7-132">See Also</span></span>

<span data-ttu-id="a04e7-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="a04e7-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="a04e7-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="a04e7-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="a04e7-135">Ligue-se a um servidor FTP com suporte IPv6</span><span class="sxs-lookup"><span data-stu-id="a04e7-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-137">Description</span></span>

<span data-ttu-id="a04e7-138">Este serviço liga a instância do cliente NetX Duo FTP previamente criada ao Servidor FTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="a04e7-139">As redes IPv4 e IPv6 são suportadas.</span><span class="sxs-lookup"><span data-stu-id="a04e7-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-140">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-140">Input Parameters</span></span>

- <span data-ttu-id="a04e7-141">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-142">**server_ipduo** Endereço IP do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="a04e7-143">**nome de utilizador** Nome de utilizador do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="a04e7-144">**senha** Senha do cliente para autenticação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="a04e7-145">**wait_option** Define quanto tempo o serviço irá esperar pela ligação ftp cliente.</span><span class="sxs-lookup"><span data-stu-id="a04e7-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="a04e7-146">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-147">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-149">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-149">Return Values</span></span>

- <span data-ttu-id="a04e7-150">**NX_SUCCESS** (0x00) Ligação FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="a04e7-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="a04e7-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Não conseguiu uma resposta de 22X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="a04e7-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Não conseguiu uma resposta 23X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="a04e7-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Não conseguiu uma resposta 33X (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="a04e7-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Cliente já está ligado</span><span class="sxs-lookup"><span data-stu-id="a04e7-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="a04e7-155">NX_PTR_ERROR (0x07) Inválido do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a04e7-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="a04e7-156">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="a04e7-157">NX_IP_ADDRESS_ERROR (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-158">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-158">Allowed From</span></span>

<span data-ttu-id="a04e7-159">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="a04e7-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a04e7-161">See Also</span></span>

<span data-ttu-id="a04e7-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="a04e7-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="a04e7-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="a04e7-163">nx_ftp_client_create</span></span>

<span data-ttu-id="a04e7-164">Criar uma instância de cliente FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-165">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="a04e7-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-166">Description</span></span>

<span data-ttu-id="a04e7-167">Este serviço cria uma instância de cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-168">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-168">Input Parameters</span></span>

- <span data-ttu-id="a04e7-169">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-170">**ftp_client_name** Nome do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="a04e7-171">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="a04e7-172">**window_size** Tamanho da janela anunciado para tomadas TCP deste Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="a04e7-173">**pool_ptr** Ponteiro para a piscina de pacotes predefinidos para este Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="a04e7-174">Note que a carga útil mínima do pacote deve ser suficientemente grande para manter o caminho completo e o ficheiro ou o nome do diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-175">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-175">Return Values</span></span>

- <span data-ttu-id="a04e7-176">**NX_SUCCESS** (0x00) Cliente FTP bem sucedido criar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="a04e7-177">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="a04e7-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-178">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-178">Allowed From</span></span>

<span data-ttu-id="a04e7-179">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="a04e7-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-180">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="a04e7-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="a04e7-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="a04e7-182">Excluir uma instância de cliente FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-183">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="a04e7-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-184">Description</span></span>

<span data-ttu-id="a04e7-185">Este serviço elimina uma instância do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-186">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-186">Input Parameters</span></span>

- <span data-ttu-id="a04e7-187">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-188">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-188">Return Values</span></span>

- <span data-ttu-id="a04e7-189">**NX_SUCCESS** (0x00) Cliente FTP bem sucedido apagar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="a04e7-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) cliente FTP não desligado</span><span class="sxs-lookup"><span data-stu-id="a04e7-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="a04e7-191">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-192">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-193">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-193">Allowed From</span></span>

<span data-ttu-id="a04e7-194">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-195">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="a04e7-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="a04e7-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="a04e7-197">Criar um diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-199">Description</span></span>

<span data-ttu-id="a04e7-200">Este serviço cria o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-201">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-201">Input Parameters</span></span>

- <span data-ttu-id="a04e7-202">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-203">**directory_name** Nome do diretório para criar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="a04e7-204">**wait_option** Define quanto tempo o serviço vai esperar pela criação do diretório FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="a04e7-205">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-206">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-208">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-208">Return Values</span></span>

- <span data-ttu-id="a04e7-209">**NX_SUCCESS** (0x00) Diretório FTP bem sucedido criar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="a04e7-210">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-212">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-213">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-214">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-214">Allowed From</span></span>

<span data-ttu-id="a04e7-215">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="a04e7-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="a04e7-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="a04e7-218">Definir diretório predefinido no Servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-220">Description</span></span>

<span data-ttu-id="a04e7-221">Este serviço define o diretório predefinido no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="a04e7-222">Este diretório predefinido aplica-se apenas à ligação deste cliente.</span><span class="sxs-lookup"><span data-stu-id="a04e7-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-223">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-223">Input Parameters</span></span>

- <span data-ttu-id="a04e7-224">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-225">**directory_path** Nome do caminho do diretório para definir.</span><span class="sxs-lookup"><span data-stu-id="a04e7-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="a04e7-226">**wait_option** Define quanto tempo o serviço irá esperar pelo conjunto de diretório padrão FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="a04e7-227">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-228">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-230">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-230">Return Values</span></span>

- <span data-ttu-id="a04e7-231">**NX_SUCCESS** (0x00) Conjunto padrão FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="a04e7-232">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-234">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-235">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-236">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-236">Allowed From</span></span>

<span data-ttu-id="a04e7-237">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="a04e7-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="a04e7-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="a04e7-240">Eliminar diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-242">Description</span></span>

<span data-ttu-id="a04e7-243">Este serviço elimina o diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-244">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-244">Input Parameters</span></span>

- <span data-ttu-id="a04e7-245">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-246">**directory_name** Nome do diretório para apagar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="a04e7-247">**wait_option** Define quanto tempo o serviço esperará pela eliminação do diretório FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="a04e7-248">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-249">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-251">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-251">Return Values</span></span>

- <span data-ttu-id="a04e7-252">**NX_SUCCESS** (0x00) Diretório FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="a04e7-253">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-255">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-256">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-257">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-257">Allowed From</span></span>

<span data-ttu-id="a04e7-258">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-259">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="a04e7-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="a04e7-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="a04e7-261">Obtenha listagem de diretório no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-263">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-263">Description</span></span>

<span data-ttu-id="a04e7-264">Este serviço obtém o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="a04e7-265">O ponteiro do pacote fornecido conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="a04e7-266">Cada entrada é separada por uma \<cr/lf\> combinação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="a04e7-267">O ***nx_ftp_client_directory_listing_continue*** deve ser chamado para concluir a operação do diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-268">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-268">Input Parameters</span></span>

- <span data-ttu-id="a04e7-269">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-270">**directory_name** Nome do diretório para obter conteúdo de.</span><span class="sxs-lookup"><span data-stu-id="a04e7-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="a04e7-271">**packet_ptr** Ponteiro para o ponteiro do pacote de destino.</span><span class="sxs-lookup"><span data-stu-id="a04e7-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="a04e7-272">Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="a04e7-273">**wait_option** Define quanto tempo o serviço vai esperar pela lista geminada FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="a04e7-274">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-275">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-277">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-277">Return Values</span></span>

- <span data-ttu-id="a04e7-278">**NX_SUCCESS** (0x00) Lista de diretórios FTP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="a04e7-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="a04e7-279">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-280">**serviço NX_NOT_ENABLED** (0x14) (IPv6) não habilitado</span><span class="sxs-lookup"><span data-stu-id="a04e7-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="a04e7-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Não conseguiu uma resposta de 1XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="a04e7-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-283">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-284">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-285">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-285">Allowed From</span></span>

<span data-ttu-id="a04e7-286">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-287">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="a04e7-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="a04e7-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="a04e7-289">Continue a listar de diretórios do FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-291">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-291">Description</span></span>

<span data-ttu-id="a04e7-292">Este serviço continua a obter o conteúdo do diretório especificado no Servidor FTP que está ligado ao Cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="a04e7-293">Deveria ter sido imediatamente precedido por uma chamada para ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="a04e7-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="a04e7-294">Se for bem sucedido, o ponteiro do pacote fornecido conterá uma ou mais entradas de diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="a04e7-295">Esta rotina deve ser chamada até que um estado de NX_FTP_END_OF_LISTING seja recebido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-296">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-296">Input Parameters</span></span>

- <span data-ttu-id="a04e7-297">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-298">**packet_ptr** Ponteiro para o ponteiro do pacote de destino.</span><span class="sxs-lookup"><span data-stu-id="a04e7-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="a04e7-299">Se for bem sucedido, a carga útil do pacote conterá uma ou mais entradas de diretório, separadas por um <cr/7 se>.</span><span class="sxs-lookup"><span data-stu-id="a04e7-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="a04e7-300">**wait_option** Define quanto tempo o serviço vai esperar pela lista geminada FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="a04e7-301">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-302">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-304">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-304">Return Values</span></span>

- <span data-ttu-id="a04e7-305">**NX_SUCCESS** (0x00) Lista de diretórios FTP bem sucedidos.</span><span class="sxs-lookup"><span data-stu-id="a04e7-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="a04e7-306">**NX_FTP_END_OF_LISTING** (0xD8) Não há mais inscrições neste diretório.</span><span class="sxs-lookup"><span data-stu-id="a04e7-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="a04e7-307">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-309">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-310">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-311">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-311">Allowed From</span></span>

<span data-ttu-id="a04e7-312">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-313">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="a04e7-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="a04e7-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="a04e7-315">Desligar do Servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-316">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-317">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-317">Description</span></span>

<span data-ttu-id="a04e7-318">Este serviço desliga uma ligação ftp server previamente estabelecida com o cliente FTP especificado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-319">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-319">Input Parameters</span></span>

- <span data-ttu-id="a04e7-320">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-321">**wait_option** Define quanto tempo o serviço irá esperar pela desconexão do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="a04e7-322">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-323">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-325">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-325">Return Values</span></span>

- <span data-ttu-id="a04e7-326">**NX_SUCCESS** (0x00) Desconexão FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="a04e7-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="a04e7-327">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-329">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-330">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-331">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-331">Allowed From</span></span>

<span data-ttu-id="a04e7-332">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-333">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="a04e7-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="a04e7-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="a04e7-335">Arquivar ficheiro do Cliente</span><span class="sxs-lookup"><span data-stu-id="a04e7-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-336">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-337">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-337">Description</span></span>

<span data-ttu-id="a04e7-338">Este serviço fecha um ficheiro previamente aberto no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-339">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-339">Input Parameters</span></span>

- <span data-ttu-id="a04e7-340">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-341">**wait_option** Define quanto tempo o serviço irá esperar pelo fecho do ficheiro do Cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="a04e7-342">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-343">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-345">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-345">Return Values</span></span>

- <span data-ttu-id="a04e7-346">**NX_SUCCESS** (0x00) Arquivo FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="a04e7-347">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-348">**NX_FTP_NOT_OPEN (0xD5)** Arquivo não aberto; não pode fechá-lo</span><span class="sxs-lookup"><span data-stu-id="a04e7-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="a04e7-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-350">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-351">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-352">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-352">Allowed From</span></span>

<span data-ttu-id="a04e7-353">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-354">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="a04e7-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="a04e7-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="a04e7-356">Eliminar ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-357">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-358">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-358">Description</span></span>

<span data-ttu-id="a04e7-359">Este serviço elimina o ficheiro especificado no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-360">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-360">Input Parameters</span></span>

- <span data-ttu-id="a04e7-361">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-362">**file_name** Nome do ficheiro para apagar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="a04e7-363">**wait_option** Define quanto tempo o serviço irá esperar pela eliminação do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="a04e7-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="a04e7-364">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-365">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-367">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-367">Return Values</span></span>

- <span data-ttu-id="a04e7-368">**NX_SUCCESS** (0x00) Ficheiro FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="a04e7-369">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-371">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-372">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-373">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-373">Allowed From</span></span>

<span data-ttu-id="a04e7-374">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-375">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="a04e7-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="a04e7-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="a04e7-377">Abre o ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-378">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-379">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-379">Description</span></span>

<span data-ttu-id="a04e7-380">Este serviço abre o ficheiro especificado – para leitura ou escrita – no Servidor FTP anteriormente ligado à instância de Cliente especificada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-381">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-381">Input Parameters</span></span>

- <span data-ttu-id="a04e7-382">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-383">**file_name** Nome do arquivo para abrir.</span><span class="sxs-lookup"><span data-stu-id="a04e7-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="a04e7-384">**open_type** Quer **NX_FTP_OPEN_FOR_READ** ou **NX_FTP_OPEN_FOR_WRITE.**</span><span class="sxs-lookup"><span data-stu-id="a04e7-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="a04e7-385">**wait_option** Define quanto tempo o serviço vai esperar pelo ficheiro FTP Client aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="a04e7-386">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-387">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-389">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-389">Return Values</span></span>

- <span data-ttu-id="a04e7-390">**NX_SUCCESS** (0x00) Ficheiro FTP bem sucedido aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="a04e7-391">**NX_OPTION_ERROR** (0x0A) Tipo aberto inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="a04e7-392">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-393">**NX_FTP_NOT_CLOSED** (0xD6) Cliente FTP já está aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="a04e7-394">**NX_NO_FREE_PORTS** (0x45) Não há portas TCP disponíveis para atribuir</span><span class="sxs-lookup"><span data-stu-id="a04e7-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="a04e7-395">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-396">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-397">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-397">Allowed From</span></span>

<span data-ttu-id="a04e7-398">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-399">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="a04e7-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="a04e7-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="a04e7-401">Ler a partir de arquivo</span><span class="sxs-lookup"><span data-stu-id="a04e7-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-402">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-403">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-403">Description</span></span>

<span data-ttu-id="a04e7-404">Este serviço lê um pacote de um ficheiro previamente aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="a04e7-405">Deve ser chamado repetidamente até que um estatuto de NX_FTP_END_OF_FILE seja recebido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="a04e7-406">Note que o autor da chamada não atribui um pacote para este serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="a04e7-407">Só precisa fornecer um ponteiro para um ponteiro de pacote.</span><span class="sxs-lookup"><span data-stu-id="a04e7-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="a04e7-408">Este serviço atualizará o ponteiro do pacote para apontar para um pacote recuperado da fila de receção da tomada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="a04e7-409">Se um estado de sucesso for devolvido, isso significa que havia um pacote disponível, e é da responsabilidade do ouvinte libertar o pacote quando este é feito com ele.</span><span class="sxs-lookup"><span data-stu-id="a04e7-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="a04e7-410">Se for devolvido um estado não zero (ou um estado de erro ou NX_FTP_END_OF_FILE) não libertar o pacote.</span><span class="sxs-lookup"><span data-stu-id="a04e7-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="a04e7-411">Caso contrário, gera-se um erro quando o ponteiro do pacote é NU.</span><span class="sxs-lookup"><span data-stu-id="a04e7-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-412">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-412">Input Parameters</span></span>

- <span data-ttu-id="a04e7-413">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-414">**packet_ptr** Ponteiro para o destino para o ponteiro do pacote de dados a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="a04e7-415">Se for bem sucedido, o pacote um pouco ou todos os contém do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a04e7-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="a04e7-416">**wait_option** Define quanto tempo o serviço irá esperar pela leitura do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="a04e7-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="a04e7-417">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-418">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-420">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-420">Return Values</span></span>

- <span data-ttu-id="a04e7-421">**NX_SUCCESS** (0x00) Leitura de ficheiro FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="a04e7-422">**NX_FTP_NOT_OPEN** (0xD5) Cliente FTP não está aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="a04e7-423">**NX_FTP_END_OF_FILE** (0xD7) Fim da condição do ficheiro.</span><span class="sxs-lookup"><span data-stu-id="a04e7-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="a04e7-424">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-425">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-426">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-426">Allowed From</span></span>

<span data-ttu-id="a04e7-427">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-428">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

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

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="a04e7-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="a04e7-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="a04e7-430">Rebatize o ficheiro no FTP Server</span><span class="sxs-lookup"><span data-stu-id="a04e7-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-432">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-432">Description</span></span>

<span data-ttu-id="a04e7-433">Este serviço renomea um ficheiro no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-434">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-434">Input Parameters</span></span>

- <span data-ttu-id="a04e7-435">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-436">**nome de arquivo** Nome atual do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a04e7-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="a04e7-437">**new_filename** Novo nome para arquivo.</span><span class="sxs-lookup"><span data-stu-id="a04e7-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="a04e7-438">**wait_option** Define quanto tempo o serviço irá esperar pelo nome do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="a04e7-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="a04e7-439">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-440">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-442">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-442">Return Values</span></span>

- <span data-ttu-id="a04e7-443">**NX_SUCCESS** (0x00) Com sucesso do ficheiro FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="a04e7-444">**NX_FTP_NOT_CONNECTED** (0xD3) O Cliente FTP não está ligado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="a04e7-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Não recebeu resposta 3XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="a04e7-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Não conseguiu uma resposta 2XX (ok)</span><span class="sxs-lookup"><span data-stu-id="a04e7-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="a04e7-447">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-448">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-449">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-449">Allowed From</span></span>

<span data-ttu-id="a04e7-450">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-451">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="a04e7-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="a04e7-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="a04e7-453">Escrever para arquivar</span><span class="sxs-lookup"><span data-stu-id="a04e7-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-454">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="a04e7-455">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-455">Description</span></span>

<span data-ttu-id="a04e7-456">Este serviço escreve um pacote de dados para o ficheiro previamente aberto no Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-457">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-457">Input Parameters</span></span>

- <span data-ttu-id="a04e7-458">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-459">**packet_ptr** Ponteiro do pacote contendo dados para escrever.</span><span class="sxs-lookup"><span data-stu-id="a04e7-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="a04e7-460">**wait_option** Define quanto tempo o serviço irá esperar pela escrita do ficheiro FTP Client.</span><span class="sxs-lookup"><span data-stu-id="a04e7-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="a04e7-461">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="a04e7-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="a04e7-462">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do Servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="a04e7-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que a linha de chamada suspenda indefinidamente até que um Servidor FTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-464">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-464">Return Values</span></span>

- <span data-ttu-id="a04e7-465">**NX_SUCCESS** (0x00) Escrita de ficheiro FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="a04e7-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="a04e7-466">**NX_FTP_NOT_OPEN** (0xD5) Cliente FTP não está aberto.</span><span class="sxs-lookup"><span data-stu-id="a04e7-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="a04e7-467">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-468">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-469">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-469">Allowed From</span></span>

<span data-ttu-id="a04e7-470">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-471">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="a04e7-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="a04e7-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="a04e7-473">Ativar ou desativar o modo de transferência passiva</span><span class="sxs-lookup"><span data-stu-id="a04e7-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-474">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="a04e7-475">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-475">Description</span></span>

<span data-ttu-id="a04e7-476">Este serviço permite o modo de transferência passiva se a entrada passive_mode_enabled estiver definida para NX_TRUE numa instância ftp do Cliente previamente criada, de modo a que as chamadas subsequentes para ler ou escrever ficheiros (RETR, STOR) ou descarregue uma lista de diretórios (NLST) sejam feitas em modo de transferência.</span><span class="sxs-lookup"><span data-stu-id="a04e7-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="a04e7-477">Para desativar a transferência do modo passivo e voltar ao comportamento predefinido do modo de transferência ativo, ligue para esta função com o passive_mode_enabled conjunto de entrada para NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="a04e7-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-478">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-478">Input Parameters</span></span>

- <span data-ttu-id="a04e7-479">**ftp_client_ptr** Ponteiro para o bloco de controlo do cliente FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="a04e7-480">**passive_mode_enabled** Se estiver definido para NX_TRUE, o modo passivo está ativado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="a04e7-481">Se estiver definido para NX_FALSE, o modo passivo é desativado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-482">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-482">Return Values</span></span>

- <span data-ttu-id="a04e7-483">**NX_SUCCESS** (0x00) Conjunto de modo passivo bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="a04e7-484">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-485">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="a04e7-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-486">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-486">Allowed From</span></span>

<span data-ttu-id="a04e7-487">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-488">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="a04e7-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="a04e7-489">nx_ftp_server_create</span></span>

<span data-ttu-id="a04e7-490">Criar servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-491">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="a04e7-492">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-492">Description</span></span>

<span data-ttu-id="a04e7-493">Este serviço cria uma instância FTP Server na instância IP do NetX especificada e previamente criada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="a04e7-494">Note que o Servidor FTP precisa de ser iniciado com uma chamada para ***nx_ftp_server_start*** para que comece a funcionar.</span><span class="sxs-lookup"><span data-stu-id="a04e7-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-495">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-495">Input Parameters</span></span>

- <span data-ttu-id="a04e7-496">**ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="a04e7-497">**ftp_server_name** Nome do FtP Server.</span><span class="sxs-lookup"><span data-stu-id="a04e7-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="a04e7-498">**ip_ptr** Ponteiro para a instância IP do NetX associado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="a04e7-499">Note que só pode haver um Servidor FTP para uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="a04e7-500">**media_ptr** Ponteiro para a instância de mídia filex associada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="a04e7-501">**stack_ptr** Ponteiro para a memória para a área interna da pilha do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="a04e7-502">**stack_size** Tamanho da área de pilhas especificada por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="a04e7-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="a04e7-503">**pool_ptr** Ponteiro para piscina de pacotes NetX predefinido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="a04e7-504">Note que o tamanho da carga útil dos pacotes na piscina deve ser grande o suficiente para acomodar o maior nome/caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="a04e7-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="a04e7-505">**ftp_login** Função ponteiro para a função de login da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="a04e7-506">Esta função é fornecida o nome de utilizador e a palavra-passe do Cliente solicitando uma ligação, e o endereço cliente no tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="a04e7-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="a04e7-507">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="a04e7-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="a04e7-508">**ftp_logout** Função ponteiro para a função de logout da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="a04e7-509">Esta função é fornecida com o nome de utilizador e palavra-passe do Cliente solicitando uma desconexão, e o endereço Cliente no tipo de dados ULONG.</span><span class="sxs-lookup"><span data-stu-id="a04e7-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="a04e7-510">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="a04e7-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-511">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-511">Return Values</span></span>

- <span data-ttu-id="a04e7-512">**NX_SUCCESS** (0x00) Servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="a04e7-513">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-514">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-514">Allowed From</span></span>

<span data-ttu-id="a04e7-515">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="a04e7-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-516">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="a04e7-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="a04e7-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="a04e7-518">Criar servidor FTP com suporte IPv4 e IPv6</span><span class="sxs-lookup"><span data-stu-id="a04e7-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-519">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="a04e7-520">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-520">Description</span></span>

<span data-ttu-id="a04e7-521">Este serviço cria uma instância FTP Server na instância IP do NetX especificada e previamente criada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="a04e7-522">Note que o Servidor FTP ainda precisa de ser iniciado com uma chamada para ***nx_ftp_server_start*** para que comece a funcionar após a criação do Servidor.</span><span class="sxs-lookup"><span data-stu-id="a04e7-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-523">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-523">Input Parameters</span></span>

- <span data-ttu-id="a04e7-524">**ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="a04e7-525">**ftp_server_name** Nome do FtP Server.</span><span class="sxs-lookup"><span data-stu-id="a04e7-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="a04e7-526">**ip_ptr** Ponteiro para a instância IP do NetX associado.</span><span class="sxs-lookup"><span data-stu-id="a04e7-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="a04e7-527">Note que só pode haver um Servidor FTP para uma instância IP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="a04e7-528">**media_ptr** Ponteiro para a instância de mídia filex associada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="a04e7-529">**stack_ptr** Ponteiro para a memória para a área interna da pilha do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="a04e7-530">**stack_size** Tamanho da área de pilhas especificada por *stack_ptr*.</span><span class="sxs-lookup"><span data-stu-id="a04e7-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="a04e7-531">**pool_ptr** Ponteiro para piscina de pacotes NetX predefinido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="a04e7-532">Note que o tamanho da carga útil dos pacotes na piscina deve ser grande o suficiente para acomodar o maior nome/caminho de arquivo.</span><span class="sxs-lookup"><span data-stu-id="a04e7-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="a04e7-533">**ftp_login_duo** Função ponteiro para a função de login da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="a04e7-534">Esta função é fornecida o nome de utilizador e a palavra-passe do Cliente solicitando uma ligação, e um ponteiro para o endereço Cliente no NXD_ADDRESS tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a04e7-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="a04e7-535">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="a04e7-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="a04e7-536">**ftp_logout_duo** Função ponteiro para a função de logout da aplicação.</span><span class="sxs-lookup"><span data-stu-id="a04e7-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="a04e7-537">Esta função é fornecida com o nome de utilizador e palavra-passe do Cliente solicitando uma desconexão, e um ponteiro para o endereço Cliente no tipo de dados NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="a04e7-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="a04e7-538">Se isto for válido, a função de login da aplicação deve voltar NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="a04e7-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-539">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-539">Return Values</span></span>

- <span data-ttu-id="a04e7-540">**NX_SUCCESS** (0x00) Servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="a04e7-541">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-542">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-543">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-543">Allowed From</span></span>

<span data-ttu-id="a04e7-544">Inicialização e Threads</span><span class="sxs-lookup"><span data-stu-id="a04e7-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-545">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="a04e7-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="a04e7-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="a04e7-547">Excluir servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-548">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a04e7-549">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-549">Description</span></span>

<span data-ttu-id="a04e7-550">Este serviço elimina uma instância ftp server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-551">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-551">Input Parameters</span></span>

- <span data-ttu-id="a04e7-552">**ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-553">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-553">Return Values</span></span>

- <span data-ttu-id="a04e7-554">**NX_SUCCESS** (0x00) Servidor FTP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="a04e7-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="a04e7-555">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-556">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-557">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-557">Allowed From</span></span>

<span data-ttu-id="a04e7-558">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-559">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="a04e7-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="a04e7-560">nx_ftp_server_start</span></span>

<span data-ttu-id="a04e7-561">Iniciar servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-562">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a04e7-563">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-563">Description</span></span>

<span data-ttu-id="a04e7-564">Este serviço inicia uma instância ftp server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-565">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-565">Input Parameters</span></span>

- <span data-ttu-id="a04e7-566">**ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-567">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-567">Return Values</span></span>

- <span data-ttu-id="a04e7-568">**NX_SUCCESS** (0x00) Início do servidor FTP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="a04e7-569">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-570">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-570">Allowed From</span></span>

<span data-ttu-id="a04e7-571">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-572">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="a04e7-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="a04e7-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="a04e7-574">Parar o servidor FTP</span><span class="sxs-lookup"><span data-stu-id="a04e7-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="a04e7-575">Prototype</span><span class="sxs-lookup"><span data-stu-id="a04e7-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="a04e7-576">Descrição</span><span class="sxs-lookup"><span data-stu-id="a04e7-576">Description</span></span>

<span data-ttu-id="a04e7-577">Este serviço para uma instância ftp server previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="a04e7-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a04e7-578">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="a04e7-578">Input Parameters</span></span>

- <span data-ttu-id="a04e7-579">**ftp_server_ptr** Ponteiro para o bloco de controlo do servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="a04e7-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a04e7-580">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="a04e7-580">Return Values</span></span>

- <span data-ttu-id="a04e7-581">**NX_SUCCESS** (0x00) Paragem do servidor FTP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="a04e7-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="a04e7-582">NX_PTR_ERROR (0x07) Ponteiro FTP inválido.</span><span class="sxs-lookup"><span data-stu-id="a04e7-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="a04e7-583">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="a04e7-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a04e7-584">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="a04e7-584">Allowed From</span></span>

<span data-ttu-id="a04e7-585">Fios</span><span class="sxs-lookup"><span data-stu-id="a04e7-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a04e7-586">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a04e7-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
