---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo HTTP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo HTTP (listados abaixo) por ordem alfabética, com exceção do equivalente 'NetX' (apenas IPv4) do mesmo serviço são emparelhados em conjunto).
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825969"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="bab4f-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="bab4f-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX Duo HTTP (listados abaixo) por ordem alfabética, com exceção do equivalente 'NetX' (apenas IPv4) do mesmo serviço são emparelhados em conjunto).</span><span class="sxs-lookup"><span data-stu-id="bab4f-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="bab4f-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em BOLD não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="bab4f-106">**Serviços de clientes HTTP:**</span><span class="sxs-lookup"><span data-stu-id="bab4f-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="bab4f-107">**nx_http_client_create** *Criar uma instância http do cliente*</span><span class="sxs-lookup"><span data-stu-id="bab4f-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="bab4f-108">**nx_http_client_delete** *Eliminar uma instância do cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="bab4f-109">**nx_http_client_get_start** *Iniciar um pedido HTTP GET (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="bab4f-110">**nx_http_client_get_start_extended** *Iniciar um pedido HTTP GET (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="bab4f-111">**nxd_http_client_get_start** *Iniciar um pedido HTTP GET (IPv4 ou IPv6)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="bab4f-112">**nxd_http_client_get_start_extended** *Iniciar um pedido HTTP GET (IPv4 ou IPv6)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="bab4f-113">**nx_http_client_get_packet** *Obtenha o próximo pacote de dados de recursos*</span><span class="sxs-lookup"><span data-stu-id="bab4f-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="bab4f-114">**nx_http_client_put_start** *Iniciar um pedido HTTP PUT (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="bab4f-115">**nx_http_client_put_start_extended** *Iniciar um pedido HTTP PUT (apenas IPv4)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="bab4f-116">**nxd_http_client_put_start** *Iniciar um pedido HTTP PUT (IPv4 ou IPv6)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="bab4f-117">**nxd_http_client_put_start_extended** *Iniciar um pedido HTTP PUT (IPv4 ou IPv6)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="bab4f-118">**nx_http_client_put_packet** *Enviar o próximo pacote de dados de recursos*</span><span class="sxs-lookup"><span data-stu-id="bab4f-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="bab4f-119">**nx_http_client_set_connect_port** *Alterar a porta para ligar ao servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="bab4f-120">**Serviços de servidorES HTTP:**</span><span class="sxs-lookup"><span data-stu-id="bab4f-120">**HTTP server services:**</span></span>

- <span data-ttu-id="bab4f-121">**nx_http_server_cache_info_callback_set** *Definir chamada para recuperar a idade e última data modificada do URL especificado*</span><span class="sxs-lookup"><span data-stu-id="bab4f-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="bab4f-122">**nx_http_server_callback_data_send** *Enviar dados HTTP da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="bab4f-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="bab4f-123">**nx_http_server_callback_generate_response_header Criar** *cabeçalho de resposta em funções de retorno*</span><span class="sxs-lookup"><span data-stu-id="bab4f-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="bab4f-124">**nx_http_server_callback_generate_response_header_extended Criar** *cabeçalho de resposta em funções de retorno*</span><span class="sxs-lookup"><span data-stu-id="bab4f-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="bab4f-125">**nx_http_server_callback_packet_send** *Enviar um pacote HTTP a partir de uma chamada HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="bab4f-126">**nx_http_server_callback_response_send** *Enviar resposta da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="bab4f-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="bab4f-127">**nx_http_server_callback_response_send_extended** *Enviar resposta da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="bab4f-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="bab4f-128">**nx_http_server_content_get** *Obter conteúdo do pedido*</span><span class="sxs-lookup"><span data-stu-id="bab4f-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="bab4f-129">**nx_http_server_content_get_extended** *Obtenha conteúdo do pedido; suporta pedidos vazios (duração zero de conteúdo)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="bab4f-130">**nx_http_server_content_length_get** *Obtenha a duração do conteúdo no pedido*</span><span class="sxs-lookup"><span data-stu-id="bab4f-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="bab4f-131">**nx_http_server_content_length_get_extended** *Obtenha a duração do conteúdo no pedido; suporta pedidos vazios (duração zero de conteúdo)*</span><span class="sxs-lookup"><span data-stu-id="bab4f-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="bab4f-132">**nx_http_server_create** *Criar uma instância do servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="bab4f-133">**nx_http_server_delete** \* Eliminar uma instância do servidor HTTP\*</span><span class="sxs-lookup"><span data-stu-id="bab4f-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="bab4f-134">**nx_http_server_get_entity_content** *Tamanho e localização do conteúdo da entidade em URL*</span><span class="sxs-lookup"><span data-stu-id="bab4f-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="bab4f-135">**nx_http_server_get_entity_header** *Extrair cabeçalho da entidade URL em tampão especificado*</span><span class="sxs-lookup"><span data-stu-id="bab4f-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="bab4f-136">**nx_http_server_gmt_callback_set** *Definir chamada para recuperar data e hora gMT*</span><span class="sxs-lookup"><span data-stu-id="bab4f-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="bab4f-137">**nx_http_server_invalid_userpassword_notify_set** *Definir o retorno para quando o nome de utilizador e a palavra-passe inválidos são recebidos num pedido do Cliente*</span><span class="sxs-lookup"><span data-stu-id="bab4f-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="bab4f-138">**nx_http_server_mime_maps_additional_set** *Definir mapas de mímica adicionais para HTML*</span><span class="sxs-lookup"><span data-stu-id="bab4f-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="bab4f-139">**nx_http_server_packet_content_find** *Extrair o comprimento do conteúdo no cabeçalho HTTP e definir o ponteiro para iniciar os dados de conteúdo*</span><span class="sxs-lookup"><span data-stu-id="bab4f-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="bab4f-140">**nx_http_server_packet_get** *Receber pacote de cliente diretamente*</span><span class="sxs-lookup"><span data-stu-id="bab4f-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="bab4f-141">**nx_http_server_param_get** *Obter o parâmetro do pedido*</span><span class="sxs-lookup"><span data-stu-id="bab4f-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="bab4f-142">**nx_http_server_query_get** *Obter consulta do pedido*</span><span class="sxs-lookup"><span data-stu-id="bab4f-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="bab4f-143">**nx_http_server_start** *Iniciar o servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="bab4f-144">**nx_http_server_stop** *Parar o servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="bab4f-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="bab4f-145">**nx_http_server_type_get (prevadado)** *Extrato HTTP tipo, por exemplo, texto/planície do cabeçalho*</span><span class="sxs-lookup"><span data-stu-id="bab4f-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="bab4f-146">**nx_http_server_type_get_extended** *Extrato HTTP tipo HTTP, por exemplo, texto/planície do cabeçalho*</span><span class="sxs-lookup"><span data-stu-id="bab4f-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="bab4f-147">**nx_http_server_digest_authenticate_notify_set** *Definir digerir função de retorno autenticado*</span><span class="sxs-lookup"><span data-stu-id="bab4f-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="bab4f-148">**nx_http_server_authentication_check_set** *Definir função de verificação de chamada de autenticação*</span><span class="sxs-lookup"><span data-stu-id="bab4f-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="bab4f-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="bab4f-149">nx_http_client_create</span></span>

<span data-ttu-id="bab4f-150">Criar uma instância ppPoE cliente</span><span class="sxs-lookup"><span data-stu-id="bab4f-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-152">Description</span></span>

<span data-ttu-id="bab4f-153">Este serviço cria uma instância http cliente na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-154">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-154">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-155">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-156">**client_name** Nome da instância do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="bab4f-157">**ip_ptr** Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="bab4f-158">**pool_ptr** Ponteiro para piscina de pacote padrão.</span><span class="sxs-lookup"><span data-stu-id="bab4f-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="bab4f-159">Note que os pacotes desta piscina devem ter uma carga útil suficientemente grande para manusear o cabeçalho de resposta completo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="bab4f-160">Isto é definido por NX_HTTP_CLIENT_MIN_PACKET_SIZE em *nx_http.h*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="bab4f-161">**window_size** O tamanho da tomada TCP do Cliente recebe a janela.</span><span class="sxs-lookup"><span data-stu-id="bab4f-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-162">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-162">Return Values</span></span>

 - <span data-ttu-id="bab4f-163">**NX_SUCCESS** (0x00) Sucesso http cliente criar</span><span class="sxs-lookup"><span data-stu-id="bab4f-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="bab4f-164">NX_PTR_ERROR (0x07) Inválido HTTP, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="bab4f-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="bab4f-165">NX_HTTP_POOL_ERROR (0xE9) Tamanho da carga útil inválida na piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="bab4f-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-166">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-166">Allowed From</span></span>

<span data-ttu-id="bab4f-167">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="bab4f-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="bab4f-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="bab4f-169">nx_http_client_delete</span></span>

<span data-ttu-id="bab4f-170">Excluir uma instância de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-172">Description</span></span>

<span data-ttu-id="bab4f-173">Este serviço elimina uma instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-174">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-174">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-175">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-176">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-176">Return Values</span></span>

 - <span data-ttu-id="bab4f-177">**NX_SUCCESS** (0x00) Com sucesso HTTP Cliente delete</span><span class="sxs-lookup"><span data-stu-id="bab4f-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="bab4f-178">NX_PTR_ERROR (0x07) Ponteiro HTTP inválido</span><span class="sxs-lookup"><span data-stu-id="bab4f-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="bab4f-179">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-180">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-180">Allowed From</span></span>

<span data-ttu-id="bab4f-181">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-182">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="bab4f-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="bab4f-183">nx_http_client_get_start</span></span>

<span data-ttu-id="bab4f-184">Inicie um pedido HTTP GET sobre o IPv4</span><span class="sxs-lookup"><span data-stu-id="bab4f-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-185">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-186">Description</span></span>

<span data-ttu-id="bab4f-187">Este serviço tenta criar e enviar um pedido GET com o recurso especificado por "recurso" no caso http cliente anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="bab4f-188">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-189">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o Servidor HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="bab4f-190">Este serviço funciona apenas através da rede IPv4.</span><span class="sxs-lookup"><span data-stu-id="bab4f-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="bab4f-191">Para aplicações que precisam de se ligar à rede IPv6, *nxd_http_client_get_start_extended()* devem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="bab4f-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="bab4f-192">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-192">This service is deprecated.</span></span> <span data-ttu-id="bab4f-193">Os desenvolvedores são encorajados a migrar para *nx_http_client_get_start_extended()* ou *nxd_http_client_get_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-194">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-194">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-195">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-196">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-197">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-198">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="bab4f-199">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="bab4f-199">This is optional.</span></span> <span data-ttu-id="bab4f-200">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="bab4f-201">**input_size** Número de bytes na entrada adicional opcional apontada por ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="bab4f-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="bab4f-202">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-203">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-204">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="bab4f-205">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="bab4f-206">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-208">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-209">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-210">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-210">Return Values</span></span>

 - <span data-ttu-id="bab4f-211">**NX_SUCCESS** (0x00) enviou com sucesso o cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="bab4f-212">Get mensagem de início.</span><span class="sxs-lookup"><span data-stu-id="bab4f-212">GET start message.</span></span>
 - <span data-ttu-id="bab4f-213">**NX_HTTP_ERROR** (0xE0) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="bab4f-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-215">**NX_HTTP_FAILED** (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="bab4f-217">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-218">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="bab4f-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-219">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-219">Allowed From</span></span>

<span data-ttu-id="bab4f-220">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-221">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-221">Example</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="bab4f-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="bab4f-223">Inicie um pedido HTTP GET sobre o IPv4</span><span class="sxs-lookup"><span data-stu-id="bab4f-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-224">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-225">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-225">Description</span></span>

<span data-ttu-id="bab4f-226">Este serviço tenta criar e enviar um pedido GET com o recurso especificado por "recurso" no caso http cliente anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="bab4f-227">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-228">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o Servidor HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="bab4f-229">Este serviço funciona apenas através da rede IPv4.</span><span class="sxs-lookup"><span data-stu-id="bab4f-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="bab4f-230">Para aplicações que precisam de se ligar à rede IPv6, *nxd_http_client_get_start_extended()* devem ser utilizadas.</span><span class="sxs-lookup"><span data-stu-id="bab4f-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="bab4f-231">Este serviço substitui *nx_http_client_get_start()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="bab4f-232">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-233">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-233">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-234">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-235">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-236">**Recurso Pointer** para url string para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-237">**resource_length** Comprimento da cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-238">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="bab4f-239">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="bab4f-239">This is optional.</span></span> <span data-ttu-id="bab4f-240">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="bab4f-241">**input_size** Número de bytes na entrada adicional opcional apontada por ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="bab4f-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="bab4f-242">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-243">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-244">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-245">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-246">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="bab4f-247">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-248">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-250">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-251">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-252">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-252">Return Values</span></span>

 - <span data-ttu-id="bab4f-253">**NX_SUCCESS** (0x00) enviou com sucesso o cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="bab4f-254">Mensagem de início GET</span><span class="sxs-lookup"><span data-stu-id="bab4f-254">GET start message</span></span>
 - <span data-ttu-id="bab4f-255">**NX_HTTP_ERROR** (0xE0) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="bab4f-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-257">**NX_HTTP_FAILED** (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="bab4f-259">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-260">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="bab4f-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-261">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-261">Allowed From</span></span>

<span data-ttu-id="bab4f-262">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-263">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-263">Example</span></span>

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="bab4f-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="bab4f-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="bab4f-265">Envie um pedido HTTP GET (IPv4 ou IPv6)</span><span class="sxs-lookup"><span data-stu-id="bab4f-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-266">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-267">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-267">Description</span></span>

<span data-ttu-id="bab4f-268">Este serviço tenta criar e enviar um pedido GET com o recurso especificado por "recurso" no caso http cliente anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="bab4f-269">Pode ser utilizado para ligar à rede IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="bab4f-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="bab4f-270">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="bab4f-271">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o Servidor HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="bab4f-272">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-272">This service is deprecated.</span></span> <span data-ttu-id="bab4f-273">Os desenvolvedores são encorajados a migrar para *nxd_http_client_get_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-274">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-274">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-275">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-276">**Server_ip** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-277">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-278">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="bab4f-279">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="bab4f-279">This is optional.</span></span> <span data-ttu-id="bab4f-280">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="bab4f-281">**input_size** Número de bytes na entrada adicional opcional apontada por ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="bab4f-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="bab4f-282">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-283">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-284">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-285">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-286">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="bab4f-287">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-288">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-290">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-291">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-292">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-292">Return Values</span></span>

 - <span data-ttu-id="bab4f-293">**NX_SUCCESS** (0x00) enviou com sucesso pedido GET</span><span class="sxs-lookup"><span data-stu-id="bab4f-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="bab4f-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Palavra-passe excede o tamanho do tampão</span><span class="sxs-lookup"><span data-stu-id="bab4f-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="bab4f-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-296">**NX_HTTP_FAILED** (0xE2) Parâmetros de pacote inválidos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="bab4f-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome ou senha inválida</span><span class="sxs-lookup"><span data-stu-id="bab4f-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="bab4f-298">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-299">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-300">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-300">Allowed From</span></span>

<span data-ttu-id="bab4f-301">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-302">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-302">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="bab4f-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="bab4f-304">Envie um pedido HTTP GET (IPv4 ou IPv6)</span><span class="sxs-lookup"><span data-stu-id="bab4f-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-306">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-306">Description</span></span>

<span data-ttu-id="bab4f-307">Este serviço tenta criar e enviar um pedido GET com o recurso especificado por "recurso" no caso http cliente anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="bab4f-308">Pode ser utilizado para ligar à rede IPv4 ou IPv6.</span><span class="sxs-lookup"><span data-stu-id="bab4f-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="bab4f-309">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-310">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o Servidor HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="bab4f-311">Este serviço substitui *nxd_http_client_get_start()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="bab4f-312">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-313">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-313">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-314">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-315">**Server_ip** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-316">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-317">**resource_length** Comprimento da cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-318">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="bab4f-319">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="bab4f-319">This is optional.</span></span> <span data-ttu-id="bab4f-320">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="bab4f-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="bab4f-321">**input_size** Número de bytes na entrada adicional opcional apontada por ```input_ptr``` .</span><span class="sxs-lookup"><span data-stu-id="bab4f-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="bab4f-322">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-323">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-324">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-325">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-326">**wait_option** Define quanto tempo o serviço esperará internamente para processar o cliente HTTP começar.</span><span class="sxs-lookup"><span data-stu-id="bab4f-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="bab4f-327">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-328">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-330">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-331">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-332">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-332">Return Values</span></span>

 - <span data-ttu-id="bab4f-333">**NX_SUCCESS** (0x00) enviou com sucesso pedido GET</span><span class="sxs-lookup"><span data-stu-id="bab4f-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="bab4f-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Palavra-passe excede o tamanho do tampão</span><span class="sxs-lookup"><span data-stu-id="bab4f-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="bab4f-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-336">**NX_HTTP_FAILED** (0xE2) Parâmetros de pacote inválidos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="bab4f-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome ou senha inválida</span><span class="sxs-lookup"><span data-stu-id="bab4f-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="bab4f-338">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-339">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-340">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-340">Allowed From</span></span>

<span data-ttu-id="bab4f-341">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-342">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-342">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="bab4f-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="bab4f-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="bab4f-344">Obtenha o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-346">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-346">Description</span></span>

<span data-ttu-id="bab4f-347">Este serviço recupera o próximo pacote de conteúdo do recurso solicitado pela *chamada nx_http_client_get_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="bab4f-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="bab4f-348">Devem ser feitas sucessivas chamadas para esta rotina até que seja recebida a situação de devolução do NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="bab4f-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-349">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-349">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-350">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-351">**packet_ptr** Destino para ponteiro de pacotes que contenha conteúdo parcial de recursos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="bab4f-352">**wait_option** Define quanto tempo o serviço irá esperar pelo pacote http Cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="bab4f-353">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-354">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-356">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-357">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-358">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-358">Return Values</span></span>

 - <span data-ttu-id="bab4f-359">**NX_SUCCESS** (0x00) pacote de cliente HTTP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="bab4f-360">**NX_HTTP_GET_DONE** (0xEC) HTTP O pacote de obter do cliente está feito</span><span class="sxs-lookup"><span data-stu-id="bab4f-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="bab4f-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está em modo get.</span><span class="sxs-lookup"><span data-stu-id="bab4f-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="bab4f-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="bab4f-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="bab4f-363">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-364">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-365">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-365">Allowed From</span></span>

<span data-ttu-id="bab4f-366">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-367">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="bab4f-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="bab4f-368">nx_http_client_put_start</span></span>

<span data-ttu-id="bab4f-369">Inicie um pedido HTTP PUT sobre o IPv4</span><span class="sxs-lookup"><span data-stu-id="bab4f-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-370">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-371">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-371">Description</span></span>

<span data-ttu-id="bab4f-372">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="bab4f-373">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet()* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-374">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o servidor HTTP indicar que suporta pedidos DE REenso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="bab4f-375">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-375">This service is deprecated.</span></span> <span data-ttu-id="bab4f-376">Os desenvolvedores são encorajados a migrar para *nxd_http_client_put_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-377">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-377">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-378">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-379">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-380">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-381">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-382">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-383">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="bab4f-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="bab4f-384">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="bab4f-385">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="bab4f-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="bab4f-386">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-387">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-389">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-390">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-391">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-391">Return Values</span></span>

 - <span data-ttu-id="bab4f-392">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="bab4f-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="bab4f-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="bab4f-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="bab4f-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-395">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-396">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="bab4f-397">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-398">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-398">Allowed From</span></span>

<span data-ttu-id="bab4f-399">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-400">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="bab4f-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="bab4f-402">Inicie um pedido HTTP PUT sobre o IPv4</span><span class="sxs-lookup"><span data-stu-id="bab4f-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-403">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-404">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-404">Description</span></span>

<span data-ttu-id="bab4f-405">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="bab4f-406">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet()* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-407">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o servidor HTTP indicar que suporta pedidos DE REenso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="bab4f-408">Este serviço substitui *nx_http_client_put_start()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="bab4f-409">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-410">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-410">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-411">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-412">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-413">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-414">**resource_length** Comprimento da cadeia URL para o recurso enviar para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="bab4f-415">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-416">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-417">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-418">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-419">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="bab4f-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="bab4f-420">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="bab4f-421">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="bab4f-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="bab4f-422">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-423">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-425">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-426">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-427">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-427">Return Values</span></span>

 - <span data-ttu-id="bab4f-428">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="bab4f-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="bab4f-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="bab4f-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="bab4f-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-431">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-432">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="bab4f-433">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-434">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-434">Allowed From</span></span>

<span data-ttu-id="bab4f-435">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-436">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="bab4f-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="bab4f-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="bab4f-438">Inicie um pedido HTTP PUT (IPv4 ou IPv6)</span><span class="sxs-lookup"><span data-stu-id="bab4f-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-439">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-440">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-440">Description</span></span>

<span data-ttu-id="bab4f-441">Este serviço tenta colocar (enviar) o recurso especificado no servidor HTTP no endereço IP fornecido sobre o IPv6.</span><span class="sxs-lookup"><span data-stu-id="bab4f-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="bab4f-442">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet()* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-443">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o servidor HTTP indicar que suporta pedidos DE REenso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="bab4f-444">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-444">This service is deprecated.</span></span> <span data-ttu-id="bab4f-445">Os desenvolvedores são encorajados a migrar para *nxd_http_client_put_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-446">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-446">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-447">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-448">**server_ip** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-449">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="bab4f-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="bab4f-450">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-451">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-452">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="bab4f-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="bab4f-453">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="bab4f-454">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="bab4f-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="bab4f-455">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-456">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-458">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-459">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-460">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-460">Return Values</span></span>

 - <span data-ttu-id="bab4f-461">**NX_SUCCESS** (0x00) enviaram com sucesso o pedido HTTP Client PUT</span><span class="sxs-lookup"><span data-stu-id="bab4f-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="bab4f-462">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do cliente</span><span class="sxs-lookup"><span data-stu-id="bab4f-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="bab4f-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-464">**NX_HTTP_FAILED** (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="bab4f-465">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-466">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="bab4f-467">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-468">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-468">Allowed From</span></span>

<span data-ttu-id="bab4f-469">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-470">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-470">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="bab4f-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="bab4f-472">Inicie um pedido HTTP PUT (IPv4 ou IPv6)</span><span class="sxs-lookup"><span data-stu-id="bab4f-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-473">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-474">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-474">Description</span></span>

<span data-ttu-id="bab4f-475">Este serviço tenta colocar (enviar) o recurso especificado no servidor HTTP no endereço IP fornecido sobre o IPv6.</span><span class="sxs-lookup"><span data-stu-id="bab4f-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="bab4f-476">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet()* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-477">A cadeia de recursos pode referir-se a um ficheiro local, por ``` “/index.htm” ``` exemplo, ou pode referir-se a outro URL, por exemplo, ```http://abc.website.com/index.htm``` se o servidor HTTP indicar que suporta pedidos DE REenso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="bab4f-478">Este serviço substitui *nxd_http_client_put_start()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="bab4f-479">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="bab4f-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-480">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-480">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-481">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-482">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-483">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="bab4f-484">**resource_length** Comprimento da cadeia URL para o recurso enviar para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="bab4f-485">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-486">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="bab4f-487">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-488">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="bab4f-489">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="bab4f-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="bab4f-490">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="bab4f-491">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="bab4f-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="bab4f-492">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-493">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-495">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-496">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-497">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-497">Return Values</span></span>

 - <span data-ttu-id="bab4f-498">**NX_SUCCESS** (0x00) enviaram com sucesso o pedido HTTP Client PUT</span><span class="sxs-lookup"><span data-stu-id="bab4f-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="bab4f-499">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do cliente</span><span class="sxs-lookup"><span data-stu-id="bab4f-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="bab4f-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-501">NX_HTTP_FAILED (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="bab4f-502">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-503">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="bab4f-504">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-505">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-505">Allowed From</span></span>

<span data-ttu-id="bab4f-506">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-507">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-507">Example</span></span>

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="bab4f-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="bab4f-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="bab4f-509">Enviar o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="bab4f-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-510">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="bab4f-511">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-511">Description</span></span>

<span data-ttu-id="bab4f-512">Este serviço tenta enviar o próximo pacote de conteúdo de recursos para o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-513">Esta rotina deve ser chamada repetidamente até que o comprimento combinado dos pacotes enviados seja igual ao "total_bytes" especificado na chamada *nx_http_client_put_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="bab4f-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-514">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-514">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-515">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-516">**packet_ptr** Ponteiro para o próximo conteúdo do recurso a ser enviado para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="bab4f-517">**wait_option** Define quanto tempo o serviço esperará internamente para processar o pacote HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="bab4f-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="bab4f-518">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bab4f-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="bab4f-519">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="bab4f-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="bab4f-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="bab4f-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="bab4f-521">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="bab4f-522">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-523">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-523">Return Values</span></span>

 - <span data-ttu-id="bab4f-524">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="bab4f-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="bab4f-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="bab4f-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Código de erro do Servidor Recebido</span><span class="sxs-lookup"><span data-stu-id="bab4f-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="bab4f-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="bab4f-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="bab4f-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha</span><span class="sxs-lookup"><span data-stu-id="bab4f-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="bab4f-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) O servidor responde antes de PUT estar completo</span><span class="sxs-lookup"><span data-stu-id="bab4f-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="bab4f-530">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-531">NX_INVALID_PACKET (0x12) Pacote demasiado pequeno para cabeçalho TCP</span><span class="sxs-lookup"><span data-stu-id="bab4f-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="bab4f-532">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-533">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-533">Allowed From</span></span>

<span data-ttu-id="bab4f-534">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-535">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="bab4f-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="bab4f-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="bab4f-537">Definir a porta de ligação para o Servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-538">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="bab4f-539">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-539">Description</span></span>

<span data-ttu-id="bab4f-540">Este serviço altera a porta de ligação quando se liga ao servidor HTTP à porta especificada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bab4f-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="bab4f-541">Caso contrário, a porta de ligação está em padrão para 80.</span><span class="sxs-lookup"><span data-stu-id="bab4f-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="bab4f-542">Isto deve ser chamado antes *nx_http_client_get_start()* e *nx_http_client_put_start()* por exemplo, quando o Cliente HTTP se conecta com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-543">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-543">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-544">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="bab4f-545">**porto** Porta para ligação ao Servidor.</span><span class="sxs-lookup"><span data-stu-id="bab4f-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-546">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-546">Return Values</span></span>

 - <span data-ttu-id="bab4f-547">**NX_SUCCESS** (0x00) mude com sucesso a porta</span><span class="sxs-lookup"><span data-stu-id="bab4f-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="bab4f-548">NX_INVALID_PORT (0x46) Porto excede o máximo (0xFFFF) ou é zero</span><span class="sxs-lookup"><span data-stu-id="bab4f-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="bab4f-549">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-550">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-550">Allowed From</span></span>

<span data-ttu-id="bab4f-551">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="bab4f-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-552">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="bab4f-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="bab4f-554">Desa esta hora de chamada para recuperar a idade máxima e a data do URL</span><span class="sxs-lookup"><span data-stu-id="bab4f-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-555">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="bab4f-556">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-556">Description</span></span>

<span data-ttu-id="bab4f-557">Este serviço define o serviço de retorno invocado para obter a idade máxima e última data modificada do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-558">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-558">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-559">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-560">**cache_info_get** Ponteiro para a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="bab4f-561">**max_age** Ponteiro para a idade máxima de um recurso</span><span class="sxs-lookup"><span data-stu-id="bab4f-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="bab4f-562">**dados** Ponteiro para a última data modificada devolvida.</span><span class="sxs-lookup"><span data-stu-id="bab4f-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-563">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-563">Return Values</span></span>

 - <span data-ttu-id="bab4f-564">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="bab4f-565">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-566">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-566">Allowed From</span></span>

<span data-ttu-id="bab4f-567">Inicialização</span><span class="sxs-lookup"><span data-stu-id="bab4f-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-568">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="bab4f-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="bab4f-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="bab4f-570">Enviar dados da função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-572">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-572">Description</span></span>

<span data-ttu-id="bab4f-573">Este serviço envia os dados no pacote fornecido da rotina de chamada da aplicação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="bab4f-574">Isto é normalmente usado para enviar dados dinâmicos associados a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="bab4f-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-575">Se esta função for utilizada, a rotina de retorno é responsável pelo envio de toda a resposta no formato adequado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="bab4f-576">Além disso, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="bab4f-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-577">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-577">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-578">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-579">**data_ptr** Ponteiro para os dados a enviar.</span><span class="sxs-lookup"><span data-stu-id="bab4f-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="bab4f-580">**data_length**  Número de bytes para enviar.</span><span class="sxs-lookup"><span data-stu-id="bab4f-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-581">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-581">Return Values</span></span>

 - <span data-ttu-id="bab4f-582">**NX_SUCCESS** (0x00) enviou com sucesso dados do Servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="bab4f-583">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-584">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-584">Allowed From</span></span>

<span data-ttu-id="bab4f-585">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-586">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-586">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="bab4f-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="bab4f-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="bab4f-588">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-589">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="bab4f-590">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-590">Description</span></span>

<span data-ttu-id="bab4f-591">Este serviço liga para a função interna *_nx_http_server_generate_response_header* quando o servidor HTTP responde ao Cliente obter, colocar e apagar pedidos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="bab4f-592">Destina-se a ser utilizado em funções de chamada do servidor HTTP quando a aplicação do servidor HTTP estiver a desenhar a sua resposta ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="bab4f-593">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-593">This service is deprecated.</span></span> <span data-ttu-id="bab4f-594">Os desenvolvedores são encorajados a migrar para *nxd_http_server_callback_generate_response_header_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-595">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-595">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-596">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-597">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="bab4f-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="bab4f-598">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="bab4f-599">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="bab4f-599">Examples:</span></span>
    - <span data-ttu-id="bab4f-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="bab4f-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="bab4f-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="bab4f-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="bab4f-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="bab4f-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="bab4f-603">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="bab4f-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="bab4f-604">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="bab4f-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="bab4f-605">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="bab4f-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-606">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-606">Return Values</span></span>

 - <span data-ttu-id="bab4f-607">**NX_SUCCESS** (0x00) Cabeçalho criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="bab4f-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="bab4f-608">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-609">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-609">Allowed From</span></span>

<span data-ttu-id="bab4f-610">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-611">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-611">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="bab4f-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="bab4f-613">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-614">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-615">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-615">Description</span></span>

<span data-ttu-id="bab4f-616">Este serviço chama a função interna *_nx_http_server_generate_response_header()* quando o servidor HTTP responde a solicitações de obter, colocar e apagar pedidos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="bab4f-617">Destina-se a ser utilizado em funções de chamada do servidor HTTP quando a aplicação do servidor HTTP estiver a desenhar a sua resposta ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="bab4f-618">Este serviço substitui *nx_http_server_callback_generate_response_header()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="bab4f-619">Esta versão fornece informações adicionais de comprimento à função de retorno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-620">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-620">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-621">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-622">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="bab4f-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="bab4f-623">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="bab4f-624">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="bab4f-624">Examples:</span></span>
    - <span data-ttu-id="bab4f-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="bab4f-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="bab4f-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="bab4f-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="bab4f-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="bab4f-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="bab4f-628">**status_code** Duração do código de estado</span><span class="sxs-lookup"><span data-stu-id="bab4f-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="bab4f-629">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="bab4f-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="bab4f-630">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="bab4f-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="bab4f-631">**content_type_length** Comprimento do tipo HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="bab4f-632">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="bab4f-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="bab4f-633">**additional_header_length** Comprimento do texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="bab4f-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-634">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-634">Return Values</span></span>

 - <span data-ttu-id="bab4f-635">**NX_SUCCESS** (0x00) Cabeçalho criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="bab4f-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="bab4f-636">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-637">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-637">Allowed From</span></span>

<span data-ttu-id="bab4f-638">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-639">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-639">Example</span></span>

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="bab4f-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="bab4f-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="bab4f-641">Envie um pacote HTTP da função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-643">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-643">Description</span></span>

<span data-ttu-id="bab4f-644">Este serviço envia uma resposta completa do servidor HTTP a partir de uma chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="bab4f-645">O servidor HTTP enviará o pacote com o NX_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="bab4f-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="bab4f-646">O cabeçalho HTTP e os dados devem ser anexados ao pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="bab4f-647">Se o estado de devolução indicar um erro, a aplicação HTTP deve libertar o pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="bab4f-648">A chamada deve voltar NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="bab4f-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="bab4f-649">Consulte *nx_http_server_callback_generate_response_header para* um exemplo mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-650">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-650">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-651">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-652">**packet_ptr** Ponteiro para o pacote para enviar</span><span class="sxs-lookup"><span data-stu-id="bab4f-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-653">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-653">Return Values</span></span>

 - <span data-ttu-id="bab4f-654">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do Servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="bab4f-655">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-656">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-656">Allowed From</span></span>

<span data-ttu-id="bab4f-657">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-658">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-658">Example</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="bab4f-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="bab4f-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="bab4f-660">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-661">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="bab4f-662">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-662">Description</span></span>

<span data-ttu-id="bab4f-663">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="bab4f-664">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="bab4f-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-665">Se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="bab4f-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="bab4f-666">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-666">This service is deprecated.</span></span> <span data-ttu-id="bab4f-667">Os desenvolvedores são encorajados a migrar para *nxd_http_server_callback_response_send_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-668">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-668">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-669">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-670">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="bab4f-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="bab4f-671">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="bab4f-672">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="bab4f-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-673">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-673">Return Values</span></span>

 - <span data-ttu-id="bab4f-674">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do Servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-675">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-675">Allowed From</span></span>

<span data-ttu-id="bab4f-676">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-677">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-677">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="bab4f-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="bab4f-679">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="bab4f-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-680">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-680">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-681">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-681">Description</span></span>

<span data-ttu-id="bab4f-682">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="bab4f-683">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="bab4f-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-684">Se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="bab4f-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="bab4f-685">Este serviço substitui *nx_http_server_callback_response_send()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="bab4f-686">Esta versão requer informações adicionais de comprimento como argumentos.</span><span class="sxs-lookup"><span data-stu-id="bab4f-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-687">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-687">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-688">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-689">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="bab4f-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="bab4f-690">**header_length** Comprimento da corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="bab4f-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="bab4f-691">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="bab4f-692">**information_length** Comprimento da cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="bab4f-693">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="bab4f-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="bab4f-694">**additional_info_length** Comprimento da cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="bab4f-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-695">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-695">Return Values</span></span>

 - <span data-ttu-id="bab4f-696">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do Servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-697">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-697">Allowed From</span></span>

<span data-ttu-id="bab4f-698">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-699">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-699">Example</span></span>

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="bab4f-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-700">nx_http_server_content_get</span></span>

<span data-ttu-id="bab4f-701">Obtenha conteúdo do pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-702">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-703">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-703">Description</span></span>

<span data-ttu-id="bab4f-704">Este serviço tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="bab4f-705">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).*</span><span class="sxs-lookup"><span data-stu-id="bab4f-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="bab4f-706">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-706">This service is deprecated.</span></span> <span data-ttu-id="bab4f-707">Os desenvolvedores são encorajados a migrar para *nx_http_server_content_get_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-708">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-708">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-709">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-710">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-711">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="bab4f-712">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="bab4f-713">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="bab4f-714">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="bab4f-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="bab4f-715">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-716">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-716">Return Values</span></span>

 - <span data-ttu-id="bab4f-717">**NX_SUCCESS** (0x00) conteúdo satisfatório do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="bab4f-718">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="bab4f-719">**NX_HTTP_DATA_END** (0xE7) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="bab4f-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Servidor tempo limite para obter o próximo pacote de conteúdo</span><span class="sxs-lookup"><span data-stu-id="bab4f-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="bab4f-721">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-722">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-723">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-723">Allowed From</span></span>

<span data-ttu-id="bab4f-724">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-725">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="bab4f-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="bab4f-727">Obtenha conteúdo a partir do pedido/suporta comprimento de conteúdo zero comprimento</span><span class="sxs-lookup"><span data-stu-id="bab4f-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-728">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-729">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-729">Description</span></span>

<span data-ttu-id="bab4f-730">Este serviço é quase idêntico ao *nx_http_server_content_get;);* tenta recuperar a quantidade especificada de conteúdo do pedido do POST ou DO CLIENTE PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="bab4f-731">No entanto, trata os pedidos com contentamento comprimento de valor zero ('pedido vazio') como um pedido válido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="bab4f-732">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="bab4f-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="bab4f-733">Este serviço substitui *nx_http_server_content_get()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="bab4f-734">Esta versão requer que o chamador forneça informações adicionais sobre o comprimento.</span><span class="sxs-lookup"><span data-stu-id="bab4f-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-735">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-735">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-736">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-737">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-738">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="bab4f-739">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="bab4f-740">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="bab4f-741">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="bab4f-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="bab4f-742">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-743">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-743">Return Values</span></span>

 - <span data-ttu-id="bab4f-744">**NX_SUCCESS** (0x00) conteúdo HTTP bem sucedido obtém</span><span class="sxs-lookup"><span data-stu-id="bab4f-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="bab4f-745">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="bab4f-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="bab4f-746">**NX_HTTP_DATA_END** (0xE7) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="bab4f-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Servidor tempo limite na obtenção do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="bab4f-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="bab4f-748">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="bab4f-749">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-750">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-750">Allowed From</span></span>

<span data-ttu-id="bab4f-751">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-752">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="bab4f-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="bab4f-754">Obtenha a duração do conteúdo no pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-755">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-756">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-756">Description</span></span>

<span data-ttu-id="bab4f-757">Este serviço tenta recuperar o comprimento do conteúdo HTTP no pacote fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="bab4f-758">Se não houver conteúdo HTTP, esta rotina devolve um valor de zero.</span><span class="sxs-lookup"><span data-stu-id="bab4f-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="bab4f-759">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="bab4f-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="bab4f-760">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-760">This service is deprecated.</span></span> <span data-ttu-id="bab4f-761">Os desenvolvedores são encorajados a migrar para *nx_http_server_content_length_get_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-762">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-762">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-763">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-764">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-765">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-765">Return Values</span></span>

 - <span data-ttu-id="bab4f-766">**comprimento do conteúdo** Por engano, um valor de zero é devolvido</span><span class="sxs-lookup"><span data-stu-id="bab4f-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="bab4f-767">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-767">Allowed From</span></span>

<span data-ttu-id="bab4f-768">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-769">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="bab4f-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="bab4f-771">Obtenha o comprimento do conteúdo no pedido/suporta o comprimento do conteúdo de valor zero</span><span class="sxs-lookup"><span data-stu-id="bab4f-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-772">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-773">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-773">Description</span></span>

<span data-ttu-id="bab4f-774">Este serviço é semelhante ao *nx_http_server_content_length_get;* tenta recuperar o comprimento do conteúdo HTTP no pacote fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="bab4f-775">No entanto, o valor de retorno indica o estado de conclusão bem-sucedido, e o valor real do comprimento é devolvido no ponteiro de entrada ```content_length``` .</span><span class="sxs-lookup"><span data-stu-id="bab4f-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="bab4f-776">Se não houver conteúdo/comprimento de conteúdo HTTP = 0, esta rotina ainda devolve um estado de conclusão bem-sucedido e o ponteiro de entrada content_length aponta para um comprimento válido (zero).</span><span class="sxs-lookup"><span data-stu-id="bab4f-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="bab4f-777">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).*</span><span class="sxs-lookup"><span data-stu-id="bab4f-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="bab4f-778">Este serviço substitui *nx_http_server_content_length_get()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-779">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-779">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-780">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-781">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="bab4f-782">**content_length** Ponteiro para valor recuperado do campo Content Length</span><span class="sxs-lookup"><span data-stu-id="bab4f-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-783">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-783">Return Values</span></span>

 - <span data-ttu-id="bab4f-784">**NX_SUCCESS** (0x00) Conteúdo satisfatório do servidor obtém</span><span class="sxs-lookup"><span data-stu-id="bab4f-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="bab4f-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Formato de cabeçalho HTTP impróprio</span><span class="sxs-lookup"><span data-stu-id="bab4f-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="bab4f-786">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-787">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-787">Allowed From</span></span>

<span data-ttu-id="bab4f-788">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-789">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="bab4f-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="bab4f-790">nx_http_server_create</span></span>

<span data-ttu-id="bab4f-791">Criar uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-792">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-792">Prototype</span></span>

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="bab4f-793">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-793">Description</span></span>

<span data-ttu-id="bab4f-794">Este serviço cria uma instância http server, que funciona no contexto da sua própria linha ThreadX.</span><span class="sxs-lookup"><span data-stu-id="bab4f-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="bab4f-795">As rotinas de *chamada de authentication_check* e request_notify de aplicações opcionais dão ao software de aplicação controlo sobre as operações básicas do Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-796">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-796">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-797">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="bab4f-798">**http_server_name** Ponteiro para o nome do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="bab4f-799">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="bab4f-800">**media_ptr** Ponteiro para a instância de media filex previamente criada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="bab4f-801">**stack_ptr** Ponteiro para a área da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="bab4f-802">**stack_size** Ponteiro para o tamanho da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="bab4f-803">**authentication_check** Função ponteiro para a rotina de verificação de autenticação da aplicação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="bab4f-804">Se especificado, esta rotina é chamada para cada pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="bab4f-805">Se este parâmetro for NU, não será efetuada qualquer autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="bab4f-806">**request_notify** Ponteiro de função para pedido de pedido de aplicação notificar rotina.</span><span class="sxs-lookup"><span data-stu-id="bab4f-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="bab4f-807">Se especificado, esta rotina é chamada antes do processamento do servidor HTTP do pedido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="bab4f-808">Isto permite que o nome do recurso seja redirecionado ou campos dentro de um recurso a ser atualizado antes de completar o pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-809">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-809">Return Values</span></span>

 - <span data-ttu-id="bab4f-810">**NX_SUCCESS** (0x00) o servidor HTTP com sucesso cria.</span><span class="sxs-lookup"><span data-stu-id="bab4f-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="bab4f-811">NX_PTR_ERROR (0x07) Inválido HTTP Servidor, IP, meios de comunicação, stack ou ponteiro de piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="bab4f-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="bab4f-812">NX_HTTP_POOL_ERROR (0xE9) A carga útil do pacote não é suficientemente grande para conter o pedido HTTP completo.</span><span class="sxs-lookup"><span data-stu-id="bab4f-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-813">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-813">Allowed From</span></span>

<span data-ttu-id="bab4f-814">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="bab4f-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-815">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="bab4f-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="bab4f-816">nx_http_server_delete</span></span>

<span data-ttu-id="bab4f-817">Excluir uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-819">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-819">Description</span></span>

<span data-ttu-id="bab4f-820">Este serviço elimina uma instância do servidor HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-821">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-821">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-822">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-823">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-823">Return Values</span></span>

 - <span data-ttu-id="bab4f-824">**NX_SUCCESS** (0x00) Com sucesso no servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="bab4f-825">NX_PTR_ERROR (0x07) Ponteiro do servidor HTTP Inválido</span><span class="sxs-lookup"><span data-stu-id="bab4f-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="bab4f-826">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-827">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-827">Allowed From</span></span>

<span data-ttu-id="bab4f-828">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-829">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="bab4f-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="bab4f-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="bab4f-831">Recuperar a localização e a duração dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-832">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-833">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-833">Description</span></span>

<span data-ttu-id="bab4f-834">Este serviço determina a localização do início dos dados dentro da atual entidade multipartidária nas mensagens do Cliente recebidas e o comprimento dos dados que não incluem a cadeia de limites.</span><span class="sxs-lookup"><span data-stu-id="bab4f-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="bab4f-835">Internamente, o servidor HTTP atualiza as suas próprias compensações para que esta função possa ser novamente chamada no mesmo datagrama do Cliente para mensagens com várias entidades.</span><span class="sxs-lookup"><span data-stu-id="bab4f-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="bab4f-836">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="bab4f-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-837">NX_HTTP_MULTIPART_ENABLE deve ser habilitado a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="bab4f-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="bab4f-838">Consulte [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="bab4f-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-839">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-839">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-840">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="bab4f-841">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="bab4f-842">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="bab4f-843">**available_offset** Ponteiro para compensar os dados da entidade a partir do ponteiro pré-final do pacote</span><span class="sxs-lookup"><span data-stu-id="bab4f-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="bab4f-844">**available_length** Ponteiro para o comprimento dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-845">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-845">Return Values</span></span>

 - <span data-ttu-id="bab4f-846">**NX_SUCCESS** (0x00) recuperou com sucesso o tamanho e localização do conteúdo da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="bab4f-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) O conteúdo dos marcadores multipartais internos do servidor HTTP já está encontrado</span><span class="sxs-lookup"><span data-stu-id="bab4f-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="bab4f-848">NX_HTTP_ERROR (0xE0) Erro HTTP Interno</span><span class="sxs-lookup"><span data-stu-id="bab4f-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="bab4f-849">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-850">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-850">Allowed From</span></span>

<span data-ttu-id="bab4f-851">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-852">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-852">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="bab4f-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="bab4f-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="bab4f-854">Recuperar o conteúdo do cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-855">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-856">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-856">Description</span></span>

<span data-ttu-id="bab4f-857">Este serviço recupera o cabeçalho da entidade no tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="bab4f-858">Internamente HTTP Server atualiza os seus próprios ponteiros para localizar a próxima entidade multipartida num datagrama do Cliente com vários cabeçalhos de entidade.</span><span class="sxs-lookup"><span data-stu-id="bab4f-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="bab4f-859">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="bab4f-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-860">NX_HTTP_MULTIPART_ENABLE deve ser habilitado a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="bab4f-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-861">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-861">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-862">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="bab4f-863">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="bab4f-864">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="bab4f-865">**entity_header_buffer** Ponteiro para localização para armazenar cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="bab4f-866">**buffer_size** Tamanho do tampão de entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-867">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-867">Return Values</span></span>

 - <span data-ttu-id="bab4f-868">**NX_SUCCESS** (0x00) conseguiu recuperar o chefe da entidade</span><span class="sxs-lookup"><span data-stu-id="bab4f-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="bab4f-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Campo de cabeçalho de entidade não encontrado</span><span class="sxs-lookup"><span data-stu-id="bab4f-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="bab4f-870">**NX_HTTP_TIMEOUT** **(0xE1)** O tempo expirou para receber o próximo pacote para mensagem de cliente multipacket</span><span class="sxs-lookup"><span data-stu-id="bab4f-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="bab4f-871">NX_HTTP_ERROR (0xE0) Erro HTTP Interno</span><span class="sxs-lookup"><span data-stu-id="bab4f-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="bab4f-872">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-873">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-874">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-874">Allowed From</span></span>

<span data-ttu-id="bab4f-875">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-876">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-876">Example</span></span>

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
  NX_SUCCESS)
 {
                nx_packet_release(response_pkt);
     }
    }


}
else
{
    /* Indicate we have not processed the response to client yet.*/
    return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="bab4f-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="bab4f-878">Desa esta hora de chamada para obter a data e hora de GMT</span><span class="sxs-lookup"><span data-stu-id="bab4f-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-879">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="bab4f-880">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-880">Description</span></span>

<span data-ttu-id="bab4f-881">Este serviço define a chamada para obter data e hora DE GMT com um servidor HTTP previamente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="bab4f-882">Este serviço é invocado com o servidor HTTP está a criar um cabeçalho em respostas do servidor HTTP ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-883">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-883">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-884">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="bab4f-885">**gmt_getv** Ponteiro para retorno GMT</span><span class="sxs-lookup"><span data-stu-id="bab4f-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="bab4f-886">**datev** Ponteiro para a data recuperada</span><span class="sxs-lookup"><span data-stu-id="bab4f-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-887">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-887">Return Values</span></span>

 - <span data-ttu-id="bab4f-888">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="bab4f-889">NX_PTR_ERROR (0x07) Pacote inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bab4f-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-890">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-890">Allowed From</span></span>

<span data-ttu-id="bab4f-891">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-892">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-892">Example</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="bab4f-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="bab4f-894">Desloque a chamada para lidar com o utilizador/senha inválido</span><span class="sxs-lookup"><span data-stu-id="bab4f-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="bab4f-896">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-896">Description</span></span>

<span data-ttu-id="bab4f-897">Este serviço define a chamada invocada quando um nome de utilizador e palavra-passe inválidos é recebido num Pedido de Cliente obter, colocar ou apagar, seja por digestão ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="bab4f-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="bab4f-898">O servidor HTTP deve ser previamente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-899">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-899">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-900">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="bab4f-901">**invalid_username_password_callback** Ponteiro para chamada inválida do utilizador/passe</span><span class="sxs-lookup"><span data-stu-id="bab4f-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="bab4f-902">**recurso** Ponteiro para o recurso especificado pelo cliente</span><span class="sxs-lookup"><span data-stu-id="bab4f-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="bab4f-903">**client_address** Ponteiro para endereço do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="bab4f-904">Pode ser IPv4 ou IPv6</span><span class="sxs-lookup"><span data-stu-id="bab4f-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="bab4f-905">**request_type** Indica o tipo de pedido do cliente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="bab4f-906">Pode ser:</span><span class="sxs-lookup"><span data-stu-id="bab4f-906">May be:</span></span>
    - <span data-ttu-id="bab4f-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="bab4f-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="bab4f-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="bab4f-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="bab4f-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="bab4f-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="bab4f-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="bab4f-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="bab4f-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="bab4f-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-912">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-912">Return Values</span></span>

 - <span data-ttu-id="bab4f-913">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="bab4f-914">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-915">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-915">Allowed From</span></span>

<span data-ttu-id="bab4f-916">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-917">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-917">Example</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="bab4f-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="bab4f-919">Definir mapas MIME adicionais para HTML</span><span class="sxs-lookup"><span data-stu-id="bab4f-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-920">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="bab4f-921">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-921">Description</span></span>

<span data-ttu-id="bab4f-922">Este serviço permite ao desenvolvedor de aplicações HTTP adicionar tipos de MIME adicionais dos tipos de MIME predefinidos fornecidos pelo NetX Duo HTTP Server (ver *nx_http_server_get_type* para lista de tipos definidos).</span><span class="sxs-lookup"><span data-stu-id="bab4f-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="bab4f-923">Quando um pedido de cliente é recebido, por exemplo, um pedido GET, o servidor HTTP analisa o tipo de ficheiro solicitado a partir do cabeçalho HTTP utilizando preferencialmente o conjunto de mapas MIME adicional e se não for encontrado, procura uma correspondência no mapa padrão do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="bab4f-924">Se não for encontrado qualquer correspondência, o tipo MIME predefine para "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="bab4f-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="bab4f-925">Se a função de notificação de pedido estiver registada no servidor HTTP, o pedido de notificação de chamada pode ligar *nx_http_server_type_retrieve()* para analisar o tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="bab4f-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-926">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-926">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-927">**server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="bab4f-928">**mime_maps** Ponteiro para uma matriz de mapa MIME</span><span class="sxs-lookup"><span data-stu-id="bab4f-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="bab4f-929">**mime_map_num** Número de mapas MIME na matriz</span><span class="sxs-lookup"><span data-stu-id="bab4f-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-930">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-930">Return Values</span></span>

 - <span data-ttu-id="bab4f-931">**NX_SUCCESS** (0x00) conjunto de mapas MIME do servidor HTTP Server</span><span class="sxs-lookup"><span data-stu-id="bab4f-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="bab4f-932">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-933">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-933">Allowed From</span></span>

<span data-ttu-id="bab4f-934">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="bab4f-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-935">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-935">Example</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="bab4f-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="bab4f-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="bab4f-937">Extrair o comprimento do conteúdo e definir o ponteiro para o início dos dados</span><span class="sxs-lookup"><span data-stu-id="bab4f-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-938">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="bab4f-939">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-939">Description</span></span>

<span data-ttu-id="bab4f-940">Este serviço extrai o comprimento do conteúdo do cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="bab4f-941">Também atualiza o pacote fornecido da seguinte forma: o ponteiro pré-final do pacote (início da localização do tampão do pacote para escrever) é definido para o conteúdo HTTP (dados) acabado de passar o cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="bab4f-942">Se o início do conteúdo não for encontrado no pacote atual, a função aguarda que o próximo pacote seja recebido utilizando a opção de espera NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="bab4f-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-943">Isto não deve ser chamado antes de chamar *nx_http_server_get_entity_header* porque modifica o ponteiro pré-final para além do cabeçalho da entidade.</span><span class="sxs-lookup"><span data-stu-id="bab4f-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-944">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-944">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-945">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="bab4f-946">**packet_ptr** Ponteiro para ponter pacote para devolver o pacote com ponteiro pré-final atualizado</span><span class="sxs-lookup"><span data-stu-id="bab4f-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="bab4f-947">**content_length** Ponteiro para extrair ```content_length```</span><span class="sxs-lookup"><span data-stu-id="bab4f-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-948">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-948">Return Values</span></span>

 - <span data-ttu-id="bab4f-949">**NX_SUCCESS** (0x00) comprimento de conteúdo HTTP encontrado e pacote atualizado com sucesso</span><span class="sxs-lookup"><span data-stu-id="bab4f-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="bab4f-950">**NX_HTTP_TIMEOUT** (0xE1) O tempo expirou à espera do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="bab4f-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="bab4f-951">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-952">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-952">Allowed From</span></span>

<span data-ttu-id="bab4f-953">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-954">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-954">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="bab4f-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="bab4f-956">Receba o próximo pacote HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-957">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-958">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-958">Description</span></span>

<span data-ttu-id="bab4f-959">Este serviço devolve o próximo pacote recebido na tomada do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="bab4f-960">A opção de espera para receber um pacote é NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="bab4f-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-961">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-961">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-962">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="bab4f-963">**packet_ptr** Ponteiro para pacote recebido</span><span class="sxs-lookup"><span data-stu-id="bab4f-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-964">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-964">Return Values</span></span>

 - <span data-ttu-id="bab4f-965">**NX_SUCCESS** (0x00) recebeu com sucesso o próximo pacote</span><span class="sxs-lookup"><span data-stu-id="bab4f-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="bab4f-966">**NX_HTTP_TIMEOUT** (0xE1) O tempo expirou à espera do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="bab4f-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="bab4f-967">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-968">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-968">Allowed From</span></span>

<span data-ttu-id="bab4f-969">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-970">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="bab4f-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-971">nx_http_server_param_get</span></span>

<span data-ttu-id="bab4f-972">Obtenha o parâmetro do pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-973">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-974">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-974">Description</span></span>

<span data-ttu-id="bab4f-975">Este serviço tenta recuperar o parâmetro HTTP URL especificado no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="bab4f-976">Se o parâmetro HTTP solicitado não estiver presente, esta rotina devolve um estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="bab4f-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="bab4f-977">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).*</span><span class="sxs-lookup"><span data-stu-id="bab4f-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-978">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-978">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-979">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-980">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="bab4f-981">**param_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="bab4f-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="bab4f-982">**param_ptr** Área de destino para copiar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab4f-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="bab4f-983">**max_param_size** Tamanho máximo da área de destino do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bab4f-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-984">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-984">Return Values</span></span>

 - <span data-ttu-id="bab4f-985">**NX_SUCCESS** (0x00) O parâmetro do servidor HTTP com sucesso obtém</span><span class="sxs-lookup"><span data-stu-id="bab4f-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="bab4f-986">**NX_HTTP_NOT_FOUND** (0xE6) Parâmetro especificado não encontrado</span><span class="sxs-lookup"><span data-stu-id="bab4f-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="bab4f-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parâmetro de pedido não devidamente terminado</span><span class="sxs-lookup"><span data-stu-id="bab4f-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="bab4f-988">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-989">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-990">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-990">Allowed From</span></span>

<span data-ttu-id="bab4f-991">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-992">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="bab4f-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-993">nx_http_server_query_get</span></span>

<span data-ttu-id="bab4f-994">Obtenha consulta a partir do pedido</span><span class="sxs-lookup"><span data-stu-id="bab4f-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-995">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-996">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-996">Description</span></span>

<span data-ttu-id="bab4f-997">Este serviço tenta recuperar a consulta de URL HTTP especificada no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="bab4f-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="bab4f-998">Se a consulta HTTP solicitada não estiver presente, esta rotina devolve um estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="bab4f-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="bab4f-999">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).*</span><span class="sxs-lookup"><span data-stu-id="bab4f-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1000">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1000">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1001">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="bab4f-1002">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="bab4f-1003">**query_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="bab4f-1004">**query_ptr** Área de destino para copiar a consulta.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="bab4f-1005">**max_query_size** Tamanho máximo da área de destino de consulta.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1006">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1006">Return Values</span></span>

 - <span data-ttu-id="bab4f-1007">**NX_SUCCESS** (0x00) Consulta de servidor HTTP com sucesso obter</span><span class="sxs-lookup"><span data-stu-id="bab4f-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="bab4f-1008">**NX_HTTP_FAILED** (0xE2) Tamanho da consulta muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="bab4f-1009">**NX_HTTP_NOT_FOUND** (0xE6) Consulta especificada não encontrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="bab4f-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) Sem consulta no pedido do Cliente</span><span class="sxs-lookup"><span data-stu-id="bab4f-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="bab4f-1011">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-1012">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1013">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1013">Allowed From</span></span>

<span data-ttu-id="bab4f-1014">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1015">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="bab4f-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="bab4f-1016">nx_http_server_start</span></span>

<span data-ttu-id="bab4f-1017">Inicie o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1018">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-1019">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1019">Description</span></span>

<span data-ttu-id="bab4f-1020">Este serviço inicia a instância do servidor HTTP anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1021">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1021">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1022">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1023">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1023">Return Values</span></span>

 - <span data-ttu-id="bab4f-1024">**NX_SUCCESS** (0x00) Início do servidor de sucesso</span><span class="sxs-lookup"><span data-stu-id="bab4f-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="bab4f-1025">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1026">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1026">Allowed From</span></span>

<span data-ttu-id="bab4f-1027">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="bab4f-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1028">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="bab4f-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="bab4f-1029">nx_http_server_stop</span></span>

<span data-ttu-id="bab4f-1030">Parar o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1031">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="bab4f-1032">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1032">Description</span></span>

<span data-ttu-id="bab4f-1033">Este serviço para a instância do servidor HTTP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="bab4f-1034">Esta rotina deve ser chamada antes de eliminar uma instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1035">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1035">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1036">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1037">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1037">Return Values</span></span>

 - <span data-ttu-id="bab4f-1038">**NX_SUCCESS** (0x00) paragem do servidor de sucesso</span><span class="sxs-lookup"><span data-stu-id="bab4f-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="bab4f-1039">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-1040">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="bab4f-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1041">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1041">Allowed From</span></span>

<span data-ttu-id="bab4f-1042">Fios</span><span class="sxs-lookup"><span data-stu-id="bab4f-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1043">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="bab4f-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="bab4f-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="bab4f-1045">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1046">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="bab4f-1047">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="bab4f-1048">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1048">This service is deprecated.</span></span> <span data-ttu-id="bab4f-1049">Os utilizadores são encorajados a utilizar o serviço *nx_http_server_type_retrieve()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="bab4f-1050">Este serviço extrai o tipo de pedido HTTP no http_type_string tampão e o seu comprimento no valor de retorno do nome do tampão de entrada, normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="bab4f-1051">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="bab4f-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="bab4f-1052">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="bab4f-1053">Os mapas MIME padrão no NetX Duo HTTP Server são:</span><span class="sxs-lookup"><span data-stu-id="bab4f-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="bab4f-1054">**html** texto/html</span><span class="sxs-lookup"><span data-stu-id="bab4f-1054">**html** text/html</span></span>
 - <span data-ttu-id="bab4f-1055">**texto/html**</span><span class="sxs-lookup"><span data-stu-id="bab4f-1055">**htm** text/html</span></span>
 - <span data-ttu-id="bab4f-1056">**texto txt/planície**</span><span class="sxs-lookup"><span data-stu-id="bab4f-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="bab4f-1057">**gif** imagem/gif</span><span class="sxs-lookup"><span data-stu-id="bab4f-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="bab4f-1058">**jpg** imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="bab4f-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="bab4f-1059">**ico** imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="bab4f-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="bab4f-1060">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="bab4f-1061">Consulte *nx_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="bab4f-1062">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1062">This service is deprecated.</span></span> <span data-ttu-id="bab4f-1063">Os desenvolvedores são encorajados a migrar para *nx_http_server_type_get_extended()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1064">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1064">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1065">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="bab4f-1066">**nome Ponteiro** para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="bab4f-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="bab4f-1067">**http_type_string** (Ponteiro para o tipo HTML extraído)</span><span class="sxs-lookup"><span data-stu-id="bab4f-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1068">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1068">Return Values</span></span>

 - <span data-ttu-id="bab4f-1069">**Comprimento da corda em bytes** Não tem valor zero é sucesso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="bab4f-1070">Zero indica erro.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1071">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1071">Allowed From</span></span>

<span data-ttu-id="bab4f-1072">Aplicação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1073">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1073">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="bab4f-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="bab4f-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="bab4f-1075">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1076">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="bab4f-1077">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1077">Description</span></span>

<span data-ttu-id="bab4f-1078">Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento no valor de retorno a partir do *nome* do tampão de entrada , normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="bab4f-1079">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="bab4f-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="bab4f-1080">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="bab4f-1081">Os mapas MIME padrão no NetX Duo HTTP Server são:</span><span class="sxs-lookup"><span data-stu-id="bab4f-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="bab4f-1082">**html** texto/html</span><span class="sxs-lookup"><span data-stu-id="bab4f-1082">**html** text/html</span></span>
 - <span data-ttu-id="bab4f-1083">**texto/html**</span><span class="sxs-lookup"><span data-stu-id="bab4f-1083">**htm** text/html</span></span>
 - <span data-ttu-id="bab4f-1084">**texto txt/planície**</span><span class="sxs-lookup"><span data-stu-id="bab4f-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="bab4f-1085">**gif** imagem/gif</span><span class="sxs-lookup"><span data-stu-id="bab4f-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="bab4f-1086">**jpg** imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="bab4f-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="bab4f-1087">**ico** imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="bab4f-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="bab4f-1088">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="bab4f-1089">Consulte *nx_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="bab4f-1090">Este serviço substitui *nx_http_server_type_get()*.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="bab4f-1091">Esta versão fornece informações adicionais sobre o comprimento.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1092">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1092">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1093">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="bab4f-1094">**nome** Ponteiro para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="bab4f-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="bab4f-1095">**name_length** Comprimento do tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="bab4f-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="bab4f-1096">**http_type_string** (Ponteiro para o tipo HTML extraído)</span><span class="sxs-lookup"><span data-stu-id="bab4f-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="bab4f-1097">**http_type_string_max_size** Tamanho do tampão http_type_string</span><span class="sxs-lookup"><span data-stu-id="bab4f-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1098">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1098">Return Values</span></span>

 - <span data-ttu-id="bab4f-1099">**Comprimento da corda em bytes** Não tem valor zero é sucesso.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="bab4f-1100">Zero indica erro.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1101">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1101">Allowed From</span></span>

<span data-ttu-id="bab4f-1102">Aplicação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1103">Example</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="bab4f-1104">Para um exemplo mais detalhado, consulte a descrição [*para nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span><span class="sxs-lookup"><span data-stu-id="bab4f-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="bab4f-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="bab4f-1106">Detenda a função de retorno autenticado da digestão</span><span class="sxs-lookup"><span data-stu-id="bab4f-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1107">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1107">Prototype</span></span>

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a><span data-ttu-id="bab4f-1108">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1108">Description</span></span>

<span data-ttu-id="bab4f-1109">Este serviço define a chamada invocada quando a digestão autenticada é realizada.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1110">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1110">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1111">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="bab4f-1112">**digest_authenticate_callback** Ponteiro para digerir chamada autenticada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1113">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1113">Return Values</span></span>

 - <span data-ttu-id="bab4f-1114">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="bab4f-1115">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="bab4f-1116">NX_NOT_SUPPORTED (0x4B) Digerir autenticado não habilitado</span><span class="sxs-lookup"><span data-stu-id="bab4f-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1117">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1117">Allowed From</span></span>

<span data-ttu-id="bab4f-1118">Aplicação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1119">Example</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="bab4f-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="bab4f-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="bab4f-1121">Definir função de verificação de autenticação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="bab4f-1122">Prototype</span><span class="sxs-lookup"><span data-stu-id="bab4f-1122">Prototype</span></span>

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a><span data-ttu-id="bab4f-1123">Descrição</span><span class="sxs-lookup"><span data-stu-id="bab4f-1123">Description</span></span>

<span data-ttu-id="bab4f-1124">Este serviço define a função de retorno de chamada da verificação de autenticação.</span><span class="sxs-lookup"><span data-stu-id="bab4f-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="bab4f-1125">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1125">Input Parameters</span></span>

 - <span data-ttu-id="bab4f-1126">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="bab4f-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="bab4f-1127">**authentication_check_extended** Ponteiro para verificação de autenticação da aplicação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="bab4f-1128">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="bab4f-1128">Return Values</span></span>

 - <span data-ttu-id="bab4f-1129">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="bab4f-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="bab4f-1130">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="bab4f-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="bab4f-1131">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="bab4f-1131">Allowed From</span></span>

<span data-ttu-id="bab4f-1132">Aplicação</span><span class="sxs-lookup"><span data-stu-id="bab4f-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="bab4f-1133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bab4f-1133">Example</span></span>

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
