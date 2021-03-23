---
title: Capítulo 3 - Descrição dos serviços NetX HTTP
description: Este capítulo contém uma descrição de todos os serviços NetX HTTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826713"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="28f8b-103">Capítulo 3 - Descrição dos serviços NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="28f8b-104">Este capítulo contém uma descrição de todos os serviços NetX HTTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="28f8b-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="28f8b-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="28f8b-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="28f8b-106">**Serviços de clientes HTTP:**</span><span class="sxs-lookup"><span data-stu-id="28f8b-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="28f8b-107">nx_http_client_create Criar *uma instância http do cliente*</span><span class="sxs-lookup"><span data-stu-id="28f8b-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="28f8b-108">nx_http_client_delete Eliminar *uma instância do cliente HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="28f8b-109">nx_http_client_get_start Iniciar *um pedido HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="28f8b-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="28f8b-110">nx_http_client_get_start_extended Iniciar *um pedido HTTP GET*</span><span class="sxs-lookup"><span data-stu-id="28f8b-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="28f8b-111">nx_http_client_get_packet *Obtenha o próximo pacote de dados de recursos*</span><span class="sxs-lookup"><span data-stu-id="28f8b-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="28f8b-112">nx_http_client_put_start Iniciar *um pedido HTTP PUT*</span><span class="sxs-lookup"><span data-stu-id="28f8b-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="28f8b-113">nx_http_client_put_start_extended Iniciar *um pedido HTTP PUT*</span><span class="sxs-lookup"><span data-stu-id="28f8b-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="28f8b-114">nx_http_client_put_packet Enviar *o próximo pacote de dados de recursos*</span><span class="sxs-lookup"><span data-stu-id="28f8b-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="28f8b-115">*nx_http_client_set_connect_port* *Alterar a porta para ligar ao servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="28f8b-116">**Serviços de servidorES HTTP:**</span><span class="sxs-lookup"><span data-stu-id="28f8b-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="28f8b-117">nx_http_server_cache_info_callback_set Definir *chamada para recuperar a idade e última data modificada do URL especificado*</span><span class="sxs-lookup"><span data-stu-id="28f8b-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="28f8b-118">nx_http_server_callback_data_send Enviar *dados HTTP da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="28f8b-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="28f8b-119">nx_http_server_callback_generate_response_header Criar *cabeçalho de resposta em funções de retorno*</span><span class="sxs-lookup"><span data-stu-id="28f8b-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="28f8b-120">nx_http_server_callback_generate_response_header_extended Criar *cabeçalho de resposta em funções de retorno*</span><span class="sxs-lookup"><span data-stu-id="28f8b-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="28f8b-121">nx_http_server_callback_packet_send *Enviar um pacote HTTP a partir de uma chamada HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="28f8b-122">nx_http_server_callback_response_send Enviar *resposta da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="28f8b-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="28f8b-123">nx_http_server_callback_response_send_extended *Enviar resposta da função de retorno*</span><span class="sxs-lookup"><span data-stu-id="28f8b-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="28f8b-124">nx_http_server_content_get Obter *conteúdo do pedido*</span><span class="sxs-lookup"><span data-stu-id="28f8b-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="28f8b-125">nx_http_server_content_get_extended Obtenha *conteúdo do pedido; suporta pedidos vazios (duração zero de conteúdo)*</span><span class="sxs-lookup"><span data-stu-id="28f8b-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="28f8b-126">nx_http_server_content_length_get *Obtenha a duração do conteúdo no pedido*</span><span class="sxs-lookup"><span data-stu-id="28f8b-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="28f8b-127">nx_http_server_content_length_get_extended *Obtenha a duração do conteúdo no pedido; suporta pedidos vazios (duração zero de conteúdo)*</span><span class="sxs-lookup"><span data-stu-id="28f8b-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="28f8b-128">nx_http_server_create Criar *uma instância do servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="28f8b-129">nx_http_server_delete Eliminar *uma instância do servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="28f8b-130">nx_http_server_get_entity_content *Tamanho e localização do conteúdo da entidade em URL*</span><span class="sxs-lookup"><span data-stu-id="28f8b-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="28f8b-131">nx_http_server_get_entity_header *Extrair cabeçalho da entidade URL em tampão especificado*</span><span class="sxs-lookup"><span data-stu-id="28f8b-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="28f8b-132">nx_http_server_gmt_callback_set *Definir a chamada para recuperar a data e a hora do GMT*</span><span class="sxs-lookup"><span data-stu-id="28f8b-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="28f8b-133">nx_http_server_invalid_userpassword_notify_set Definir *o retorno para quando o nome de utilizador e a palavra-passe inválidos são recebidos num pedido do Cliente*</span><span class="sxs-lookup"><span data-stu-id="28f8b-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="28f8b-134">nx_http_server_mime_maps_additional_set Definir *mapas de mímica adicionais para HTML*</span><span class="sxs-lookup"><span data-stu-id="28f8b-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="28f8b-135">nx_http_server_packet_content_find *Extrair o comprimento do conteúdo no cabeçalho HTTP e definir o ponteiro para iniciar os dados de conteúdo*</span><span class="sxs-lookup"><span data-stu-id="28f8b-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="28f8b-136">nx_http_server_packet_get Receber *pacote de cliente diretamente*</span><span class="sxs-lookup"><span data-stu-id="28f8b-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="28f8b-137">nx_http_server_param_get Obtenha *o parâmetro do pedido*</span><span class="sxs-lookup"><span data-stu-id="28f8b-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="28f8b-138">nx_http_server_query_get Obter *consulta do pedido*</span><span class="sxs-lookup"><span data-stu-id="28f8b-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="28f8b-139">nx_http_server_start *Iniciar o servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="28f8b-140">nx_http_server_stop Parar *o servidor HTTP*</span><span class="sxs-lookup"><span data-stu-id="28f8b-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="28f8b-141">nx_http_server_type_get *Extrato HTTP tipo HTTP, por exemplo, texto/planície do cabeçalho*</span><span class="sxs-lookup"><span data-stu-id="28f8b-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="28f8b-142">nx_http_server_type_get_extended *Extrato HTTP tipo HTTP, por exemplo, texto/planície do cabeçalho*</span><span class="sxs-lookup"><span data-stu-id="28f8b-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="28f8b-143">nx_http_server_digest_authenticate_notify_set Definir *digerir função de retorno autenticado*</span><span class="sxs-lookup"><span data-stu-id="28f8b-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="28f8b-144">nx_http_server_authentication_check_set *Definir função de verificação de autenticação*</span><span class="sxs-lookup"><span data-stu-id="28f8b-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="28f8b-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="28f8b-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="28f8b-146">Criar uma instância de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="28f8b-147">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="28f8b-148">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-148">**Description**</span></span>

<span data-ttu-id="28f8b-149">Este serviço cria uma instância http cliente na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="28f8b-150">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-150">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-151">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-152">**client_name** Nome da instância do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="28f8b-153">**ip_ptr** Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="28f8b-154">**pool_ptr** Ponteiro para piscina de pacote padrão.</span><span class="sxs-lookup"><span data-stu-id="28f8b-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="28f8b-155">Note que os pacotes desta piscina devem ter uma carga útil suficientemente grande para manusear o cabeçalho de resposta completo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="28f8b-156">Isto é definido por NX_HTTP_CLIENT_MIN_PACKET_SIZE em *nx_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="28f8b-157">**window_size** O tamanho da tomada TCP do Cliente recebe a janela.</span><span class="sxs-lookup"><span data-stu-id="28f8b-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="28f8b-158">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-158">**Return Values**</span></span>

- <span data-ttu-id="28f8b-159">**NX_SUCCESS** (0x00) Sucesso http cliente criar</span><span class="sxs-lookup"><span data-stu-id="28f8b-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="28f8b-160">NX_PTR_ERROR (0x16) Inválido HTTP, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="28f8b-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="28f8b-161">NX_HTTP_POOL_ERROR (0xE9) Tamanho da carga útil inválida na piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="28f8b-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="28f8b-162">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-162">**Allowed From**</span></span>

<span data-ttu-id="28f8b-163">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="28f8b-163">Initialization, Threads</span></span>

<span data-ttu-id="28f8b-164">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="28f8b-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="28f8b-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="28f8b-166">Excluir uma instância de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="28f8b-167">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="28f8b-168">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-168">**Description**</span></span>

<span data-ttu-id="28f8b-169">Este serviço elimina uma instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="28f8b-170">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-170">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-171">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="28f8b-172">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-172">**Return Values**</span></span>

- <span data-ttu-id="28f8b-173">**NX_SUCCESS** (0x00) Com sucesso HTTP Cliente delete</span><span class="sxs-lookup"><span data-stu-id="28f8b-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="28f8b-174">NX_PTR_ERROR (0x16) Ponteiro HTTP inválido</span><span class="sxs-lookup"><span data-stu-id="28f8b-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="28f8b-175">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-176">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-176">**Allowed From**</span></span>

<span data-ttu-id="28f8b-177">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-177">Threads</span></span>

<span data-ttu-id="28f8b-178">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="28f8b-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="28f8b-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="28f8b-180">Inicie um pedido HTTP GET</span><span class="sxs-lookup"><span data-stu-id="28f8b-180">Start an HTTP GET request</span></span>

<span data-ttu-id="28f8b-181">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="28f8b-182">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-182">**Description**</span></span>

<span data-ttu-id="28f8b-183">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="28f8b-184">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="28f8b-185">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="28f8b-186">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-186">This service is deprecated.</span></span> <span data-ttu-id="28f8b-187">Os desenvolvedores são encorajados a migrar para *nx_http_client_get_start_extended()*</span><span class="sxs-lookup"><span data-stu-id="28f8b-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="28f8b-188">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-188">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-189">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-190">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-191">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="28f8b-192">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="28f8b-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="28f8b-193">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="28f8b-193">This is optional.</span></span> <span data-ttu-id="28f8b-194">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="28f8b-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="28f8b-195">**input_size** Número de bytes em entrada adicional opcional apontada por input_ptr.</span><span class="sxs-lookup"><span data-stu-id="28f8b-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="28f8b-196">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-197">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="28f8b-198">
-\*\*wait_option*\* Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="28f8b-199">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-200">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-202">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="28f8b-203">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-204">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-204">**Return Values**</span></span>

- <span data-ttu-id="28f8b-205">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="28f8b-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="28f8b-206">**NX_HTTP_ERROR** (0xE0) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="28f8b-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="28f8b-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="28f8b-208">**NX_HTTP_FAILED** (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="28f8b-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="28f8b-210">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-211">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="28f8b-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="28f8b-212">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-212">**Allowed From**</span></span>

<span data-ttu-id="28f8b-213">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-213">Threads</span></span>

<span data-ttu-id="28f8b-214">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="28f8b-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="28f8b-216">Inicie um pedido HTTP GET</span><span class="sxs-lookup"><span data-stu-id="28f8b-216">Start an HTTP GET request</span></span>

<span data-ttu-id="28f8b-217">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="28f8b-218">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-218">**Description**</span></span>

<span data-ttu-id="28f8b-219">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="28f8b-220">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_http_client_get_packet* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="28f8b-221">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="28f8b-222">Este serviço substitui *nx_http_client_get_start()*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="28f8b-223">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="28f8b-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="28f8b-224">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-224">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-225">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-226">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-227">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="28f8b-228">**resource_length** Comprimento da cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="28f8b-229">**input_ptr** Ponteiro para dados adicionais para o pedido GET.</span><span class="sxs-lookup"><span data-stu-id="28f8b-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="28f8b-230">Isto é opcional.</span><span class="sxs-lookup"><span data-stu-id="28f8b-230">This is optional.</span></span> <span data-ttu-id="28f8b-231">Se válido, a entrada especificada é colocada na área de conteúdo da mensagem e um POST é utilizado em vez de uma operação GET.</span><span class="sxs-lookup"><span data-stu-id="28f8b-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="28f8b-232">**input_size** Número de bytes em entrada adicional opcional apontada por input_ptr.</span><span class="sxs-lookup"><span data-stu-id="28f8b-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="28f8b-233">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-234">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-235">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="28f8b-236">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="28f8b-237">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="28f8b-238">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-239">**valor de saída de tempo** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-241">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="28f8b-242">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-243">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-243">**Return Values**</span></span>

- <span data-ttu-id="28f8b-244">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="28f8b-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="28f8b-245">**NX_HTTP_ERROR** (0xE0) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="28f8b-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="28f8b-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="28f8b-247">**NX_HTTP_FAILED** (0xE2) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="28f8b-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="28f8b-249">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-250">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="28f8b-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="28f8b-251">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-251">**Allowed From**</span></span>

<span data-ttu-id="28f8b-252">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-252">Threads</span></span>

<span data-ttu-id="28f8b-253">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="28f8b-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="28f8b-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="28f8b-255">Obtenha o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="28f8b-255">Get next resource data packet</span></span>

<span data-ttu-id="28f8b-256">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="28f8b-257">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-257">**Description**</span></span>

<span data-ttu-id="28f8b-258">Este serviço recupera o próximo pacote de conteúdo do recurso solicitado pela *chamada nx_http_client_get_start* anterior.</span><span class="sxs-lookup"><span data-stu-id="28f8b-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="28f8b-259">Devem ser feitas sucessivas chamadas para esta rotina até que seja recebida a situação de devolução do NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="28f8b-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="28f8b-260">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-260">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-261">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-262">**packet_ptr** Destino para ponteiro de pacotes que contenha conteúdo parcial de recursos.</span><span class="sxs-lookup"><span data-stu-id="28f8b-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="28f8b-263">**wait_option** Define quanto tempo o serviço irá esperar pelo pacote http Cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="28f8b-264">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-265">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-267">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="28f8b-268">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-269">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-269">**Return Values**</span></span>

- <span data-ttu-id="28f8b-270">**NX_SUCCESS** (0x00) pacote de cliente HTTP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="28f8b-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="28f8b-271">**NX_HTTP_GET_DONE** (0xEC) HTTP O pacote de obter do cliente está feito</span><span class="sxs-lookup"><span data-stu-id="28f8b-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="28f8b-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está em modo get.</span><span class="sxs-lookup"><span data-stu-id="28f8b-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="28f8b-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="28f8b-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="28f8b-274">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-275">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-276">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-276">**Allowed From**</span></span>

<span data-ttu-id="28f8b-277">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-277">Threads</span></span>

<span data-ttu-id="28f8b-278">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="28f8b-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="28f8b-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="28f8b-280">Inicie um pedido HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="28f8b-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="28f8b-281">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="28f8b-282">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-282">**Description**</span></span>

<span data-ttu-id="28f8b-283">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="28f8b-284">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="28f8b-285">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="28f8b-286">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-286">This service is deprecated.</span></span> <span data-ttu-id="28f8b-287">Os desenvolvedores são encorajados a migrar para *nx_http_client_put_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="28f8b-288">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-288">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-289">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-290">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-291">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="28f8b-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="28f8b-292">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-293">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="28f8b-294">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="28f8b-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="28f8b-295">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="28f8b-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="28f8b-296">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="28f8b-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="28f8b-297">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-298">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-300">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="28f8b-301">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-302">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-302">**Return Values**</span></span>

- <span data-ttu-id="28f8b-303">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="28f8b-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="28f8b-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="28f8b-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="28f8b-305">**(0xF1) Nome de utilizador demasiado grande para tampão**</span><span class="sxs-lookup"><span data-stu-id="28f8b-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="28f8b-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="28f8b-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="28f8b-307">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-308">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="28f8b-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="28f8b-309">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-310">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-310">**Allowed From**</span></span>

<span data-ttu-id="28f8b-311">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-311">Threads</span></span>

<span data-ttu-id="28f8b-312">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="28f8b-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="28f8b-314">Inicie um pedido HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="28f8b-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="28f8b-315">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="28f8b-316">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-316">**Description**</span></span>

<span data-ttu-id="28f8b-317">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="28f8b-318">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_http_client_put_packet* para enviar os conteúdos de recursos para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="28f8b-319">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="28f8b-320">Este serviço substitui *nx_http_client_put_start()*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="28f8b-321">Requer que o chamador especifique o comprimento do recurso, nome de utilizador e senha.</span><span class="sxs-lookup"><span data-stu-id="28f8b-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="28f8b-322">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-322">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-323">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-324">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-325">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="28f8b-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="28f8b-326">**resource_length** Comprimento da cadeia URL para o recurso enviar para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="28f8b-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="28f8b-327">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-328">**username_length** Duração do nome de utilizador opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="28f8b-329">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="28f8b-330">**password_length** Duração da senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="28f8b-331">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="28f8b-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="28f8b-332">Note que o comprimento combinado de todos os pacotes enviados através de chamadas *subsequentes* para nx_http_client_put_packet deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="28f8b-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="28f8b-333">**wait_option** Define quanto tempo o serviço vai esperar pelo início do HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="28f8b-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="28f8b-334">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-335">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-337">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="28f8b-338">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-339">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-339">**Return Values**</span></span>

- <span data-ttu-id="28f8b-340">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="28f8b-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="28f8b-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="28f8b-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="28f8b-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="28f8b-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="28f8b-343">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-344">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="28f8b-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="28f8b-345">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-346">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-346">**Allowed From**</span></span>

<span data-ttu-id="28f8b-347">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-347">Threads</span></span>

<span data-ttu-id="28f8b-348">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="28f8b-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="28f8b-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="28f8b-350">Enviar o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="28f8b-350">Send next resource data packet</span></span>

<span data-ttu-id="28f8b-351">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="28f8b-352">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-352">**Description**</span></span>

<span data-ttu-id="28f8b-353">Este serviço tenta enviar o próximo pacote de conteúdo de recursos para o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="28f8b-354">Note que esta rotina deve ser chamada repetidamente até que o comprimento combinado dos pacotes enviados seja igual ao "total_bytes" especificado na chamada *nx_http_client_put_start anterior().*</span><span class="sxs-lookup"><span data-stu-id="28f8b-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="28f8b-355">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-355">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-356">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-357">**packet_ptr** Ponteiro para o próximo conteúdo do recurso a ser enviado para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="28f8b-358">**wait_option** Define quanto tempo o serviço esperará internamente para processar o pacote HTTP Client PUT.</span><span class="sxs-lookup"><span data-stu-id="28f8b-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="28f8b-359">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="28f8b-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="28f8b-360">**valor de tempo limite** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="28f8b-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="28f8b-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="28f8b-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="28f8b-362">A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="28f8b-363">A seleção de um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="28f8b-364">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-364">**Return Values**</span></span>

- <span data-ttu-id="28f8b-365">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="28f8b-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="28f8b-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="28f8b-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Recebeu código de erro do servidor\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="28f8b-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="28f8b-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Nome inválido e/ou senha</span><span class="sxs-lookup"><span data-stu-id="28f8b-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="28f8b-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) O servidor responde antes de PUT estar completo</span><span class="sxs-lookup"><span data-stu-id="28f8b-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="28f8b-370">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-371">NX_INVALID_PACKET (0x12) Pacote demasiado pequeno para cabeçalho TCP</span><span class="sxs-lookup"><span data-stu-id="28f8b-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="28f8b-372">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-373">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-373">**Allowed From**</span></span>

<span data-ttu-id="28f8b-374">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-374">Threads</span></span>

<span data-ttu-id="28f8b-375">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="28f8b-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="28f8b-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="28f8b-377">Definir a porta de ligação para o Servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-377">Set the connection port to the Server</span></span>

<span data-ttu-id="28f8b-378">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="28f8b-379">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-379">**Description**</span></span>

<span data-ttu-id="28f8b-380">Este serviço altera a porta de ligação quando se liga ao servidor HTTP à porta especificada em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28f8b-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="28f8b-381">Caso contrário, a porta de ligação está em padrão para 80.</span><span class="sxs-lookup"><span data-stu-id="28f8b-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="28f8b-382">Isto deve ser chamado antes *nx_http_client_get_start*() e *nx_http_client_put_start*() por exemplo, quando o Cliente HTTP se conecta com o Servidor.</span><span class="sxs-lookup"><span data-stu-id="28f8b-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="28f8b-383">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-383">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-384">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="28f8b-385">**porto** Porta para ligação ao Servidor.</span><span class="sxs-lookup"><span data-stu-id="28f8b-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="28f8b-386">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-386">**Return Values**</span></span>

- <span data-ttu-id="28f8b-387">**NX_SUCCESS** (0x00) Mudou com sucesso a porta de ligação</span><span class="sxs-lookup"><span data-stu-id="28f8b-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="28f8b-388">**NX_INVALID_PORT** (0x46) Porto excede o máximo (0xFFFF) ou é zero.</span><span class="sxs-lookup"><span data-stu-id="28f8b-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="28f8b-389">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-390">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-390">**Allowed From**</span></span>

<span data-ttu-id="28f8b-391">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="28f8b-391">Threads, Initialization</span></span>

<span data-ttu-id="28f8b-392">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="28f8b-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="28f8b-394">Desa esta hora de chamada para recuperar a idade máxima e a data do URL</span><span class="sxs-lookup"><span data-stu-id="28f8b-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="28f8b-395">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="28f8b-396">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-396">**Description**</span></span>

<span data-ttu-id="28f8b-397">Este serviço define o serviço de retorno invocado para obter a idade máxima e última data modificada do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="28f8b-398">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-398">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-399">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-400">**cache_info_get** Ponteiro para a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="28f8b-401">**max_age** Ponteiro para a idade máxima de um recurso</span><span class="sxs-lookup"><span data-stu-id="28f8b-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="28f8b-402">**dados** Ponteiro para a última data modificada devolvida.</span><span class="sxs-lookup"><span data-stu-id="28f8b-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="28f8b-403">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-403">**Return Values**</span></span>

- <span data-ttu-id="28f8b-404">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="28f8b-405">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-406">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-406">**Allowed From**</span></span>

<span data-ttu-id="28f8b-407">Inicialização</span><span class="sxs-lookup"><span data-stu-id="28f8b-407">Initialization</span></span>

<span data-ttu-id="28f8b-408">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="28f8b-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="28f8b-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="28f8b-410">Enviar dados da função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-410">Send data from callback function</span></span>

<span data-ttu-id="28f8b-411">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="28f8b-412">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-412">**Description**</span></span>

<span data-ttu-id="28f8b-413">Este serviço envia os dados no pacote fornecido da rotina de chamada da aplicação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="28f8b-414">Isto é normalmente usado para enviar dados dinâmicos associados a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="28f8b-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="28f8b-415">Note que se esta função for utilizada, a rotina de retorno é responsável pelo envio de toda a resposta no formato adequado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="28f8b-416">Além disso, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="28f8b-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="28f8b-417">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-417">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-418">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-419">**data_ptr** Ponteiro para os dados a enviar.</span><span class="sxs-lookup"><span data-stu-id="28f8b-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="28f8b-420">**data_length** Número de bytes para enviar.</span><span class="sxs-lookup"><span data-stu-id="28f8b-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="28f8b-421">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-421">**Return Values**</span></span>

- <span data-ttu-id="28f8b-422">**NX_SUCCESS** (0x00) enviou com sucesso dados do Servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="28f8b-423">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-424">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-424">**Allowed From**</span></span>

<span data-ttu-id="28f8b-425">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-425">Threads</span></span>

<span data-ttu-id="28f8b-426">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="28f8b-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="28f8b-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="28f8b-428">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-428">Create a response header in a callback function</span></span>

<span data-ttu-id="28f8b-429">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="28f8b-430">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-430">**Description**</span></span>

<span data-ttu-id="28f8b-431">Este serviço chama a função interna _ *nx_http_server_generate_response_header* quando o servidor HTTP responde ao Cliente obter, colocar e apagar pedidos.</span><span class="sxs-lookup"><span data-stu-id="28f8b-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="28f8b-432">Destina-se a ser utilizado em funções de chamada do servidor HTTP quando a aplicação do servidor HTTP estiver a desenhar a sua resposta ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="28f8b-433">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-433">This service is deprecated.</span></span> <span data-ttu-id="28f8b-434">Os desenvolvedores são encorajados a migrar para *nxd_http_server_callback_generate_response_header_extended()*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="28f8b-435">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-435">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-436">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-437">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="28f8b-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="28f8b-438">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="28f8b-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="28f8b-439">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="28f8b-439">Examples:</span></span>
- <span data-ttu-id="28f8b-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="28f8b-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="28f8b-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="28f8b-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="28f8b-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="28f8b-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="28f8b-443">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="28f8b-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="28f8b-444">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="28f8b-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="28f8b-445">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="28f8b-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="28f8b-446">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-446">**Return Values**</span></span>

- <span data-ttu-id="28f8b-447">**NX_SUCCESS** (0x00) Com sucesso criado cabeçalho HTML</span><span class="sxs-lookup"><span data-stu-id="28f8b-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="28f8b-448">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-449">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-449">**Allowed From**</span></span>

<span data-ttu-id="28f8b-450">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-450">Threads</span></span>

<span data-ttu-id="28f8b-451">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="28f8b-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="28f8b-453">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-453">Create a response header in a callback function</span></span>

<span data-ttu-id="28f8b-454">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-454">**Prototype**</span></span>

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

<span data-ttu-id="28f8b-455">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-455">**Description**</span></span>

<span data-ttu-id="28f8b-456">Este serviço chama a função interna _ *nx_http_server_generate_response_header()* quando o servidor HTTP responde a solicitações de obter, colocar e apagar pedidos do Cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="28f8b-457">Destina-se a ser utilizado em funções de chamada do servidor HTTP quando a aplicação do servidor HTTP estiver a desenhar a sua resposta ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="28f8b-458">Este serviço substitui *nx_http_server_callback_generate_response_header()*.</span><span class="sxs-lookup"><span data-stu-id="28f8b-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="28f8b-459">Esta versão fornece informações adicionais de comprimento à função de retorno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="28f8b-460">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-460">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-461">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-462">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="28f8b-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="28f8b-463">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="28f8b-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="28f8b-464">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="28f8b-464">Examples:</span></span>
  - <span data-ttu-id="28f8b-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="28f8b-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="28f8b-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="28f8b-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="28f8b-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="28f8b-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="28f8b-468">**status_code** Duração do código de estado</span><span class="sxs-lookup"><span data-stu-id="28f8b-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="28f8b-469">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="28f8b-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="28f8b-470">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="28f8b-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="28f8b-471">**content_type_length** Comprimento do tipo HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="28f8b-472">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="28f8b-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="28f8b-473">**additional_header_length** Comprimento do texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="28f8b-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="28f8b-474">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-474">**Return Values**</span></span>

- <span data-ttu-id="28f8b-475">**NX_SUCCESS** (0x00) Cabeçalho criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="28f8b-476">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-477">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-477">**Allowed From**</span></span>

<span data-ttu-id="28f8b-478">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-478">Threads</span></span>

<span data-ttu-id="28f8b-479">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
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
                length, server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="28f8b-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="28f8b-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="28f8b-481">Envie um pacote HTTP da função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="28f8b-482">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="28f8b-483">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-483">**Description**</span></span>

<span data-ttu-id="28f8b-484">Este serviço envia uma resposta completa do servidor HTTP a partir de uma chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="28f8b-485">O servidor HTTP enviará o pacote com o NX_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="28f8b-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="28f8b-486">O cabeçalho HTTP e os dados devem ser anexados ao pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="28f8b-487">Se o estado de devolução indicar um erro, a aplicação HTTP deve libertar o pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="28f8b-488">A chamada deve voltar NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="28f8b-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="28f8b-489">Consulte *nx_http_server_callback_generate_response_header para* um exemplo mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="28f8b-490">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-490">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-491">**server_ptr** Ponteiro para bloco de controlo do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="28f8b-492">**packet_ptr** Ponteiro para o pacote para enviar</span><span class="sxs-lookup"><span data-stu-id="28f8b-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="28f8b-493">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-493">**Return Values**</span></span>

- <span data-ttu-id="28f8b-494">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="28f8b-495">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-496">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-496">**Allowed From**</span></span>

<span data-ttu-id="28f8b-497">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-497">Threads</span></span>

<span data-ttu-id="28f8b-498">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="28f8b-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="28f8b-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="28f8b-500">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-500">Send response from callback function</span></span>

<span data-ttu-id="28f8b-501">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="28f8b-502">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-502">**Description**</span></span>

<span data-ttu-id="28f8b-503">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="28f8b-504">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="28f8b-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="28f8b-505">Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="28f8b-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="28f8b-506">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-506">This service is deprecated.</span></span> <span data-ttu-id="28f8b-507">Os desenvolvedores são encorajados a migrar para *nx_http_server_callback_response_send_extended().*</span><span class="sxs-lookup"><span data-stu-id="28f8b-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="28f8b-508">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-508">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-509">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-510">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="28f8b-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="28f8b-511">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="28f8b-512">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="28f8b-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="28f8b-513">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-513">**Return Values**</span></span>

- <span data-ttu-id="28f8b-514">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="28f8b-515">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-515">**Allowed From**</span></span>

<span data-ttu-id="28f8b-516">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-516">Threads</span></span>

<span data-ttu-id="28f8b-517">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="28f8b-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="28f8b-519">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="28f8b-519">Send response from callback function</span></span>

<span data-ttu-id="28f8b-520">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="28f8b-521">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-521">**Description**</span></span>

<span data-ttu-id="28f8b-522">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="28f8b-523">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="28f8b-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="28f8b-524">Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="28f8b-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="28f8b-525">Este serviço substitui *nx_http_server_callback_response_send.*</span><span class="sxs-lookup"><span data-stu-id="28f8b-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="28f8b-526">Esta versão requer informação de comprimento como argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="28f8b-527">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-527">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-528">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-529">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="28f8b-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="28f8b-530">**header_length** Comprimento da corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="28f8b-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="28f8b-531">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="28f8b-532">**information_length** Comprimento da cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="28f8b-533">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="28f8b-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="28f8b-534">**additional_info_length** Comprimento da cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="28f8b-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="28f8b-535">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-535">**Return Values**</span></span>

- <span data-ttu-id="28f8b-536">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do Servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="28f8b-537">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-537">**Allowed From**</span></span>

<span data-ttu-id="28f8b-538">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-538">Threads</span></span>

<span data-ttu-id="28f8b-539">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="28f8b-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="28f8b-541">Obtenha conteúdo do pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-541">Get content from the request</span></span>

<span data-ttu-id="28f8b-542">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="28f8b-543">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-543">**Description**</span></span>

<span data-ttu-id="28f8b-544">Este serviço tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="28f8b-545">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="28f8b-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-546">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-546">This service is deprecated.</span></span> <span data-ttu-id="28f8b-547">Os desenvolvedores são encorajados a migrar para nx_http_server_content_get_extended().</span><span class="sxs-lookup"><span data-stu-id="28f8b-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="28f8b-548">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-548">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-549">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-550">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-551">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="28f8b-552">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="28f8b-553">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="28f8b-554">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="28f8b-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="28f8b-555">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="28f8b-556">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-556">**Return Values**</span></span>

- <span data-ttu-id="28f8b-557">**NX_SUCCESS** (0x00) conteúdo satisfatório do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="28f8b-558">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="28f8b-559">**NX_HTTP_DATA_END** (0xE7) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="28f8b-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Servidor tempo limite para obter o próximo pacote de conteúdo</span><span class="sxs-lookup"><span data-stu-id="28f8b-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="28f8b-561">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-562">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-563">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-563">**Allowed From**</span></span>

<span data-ttu-id="28f8b-564">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-564">Threads</span></span>

<span data-ttu-id="28f8b-565">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="28f8b-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="28f8b-567">Obtenha conteúdo a partir do pedido/suporta comprimento de conteúdo zero comprimento</span><span class="sxs-lookup"><span data-stu-id="28f8b-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="28f8b-568">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="28f8b-569">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-569">**Description**</span></span>

<span data-ttu-id="28f8b-570">Este serviço é quase idêntico ao *nx_http_server_content_get()*; tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="28f8b-571">No entanto, trata os pedidos com contentamento comprimento de valor zero ('pedido vazio') como um pedido válido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="28f8b-572">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="28f8b-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-573">Este serviço substitui *nx_http_server_content_get.*</span><span class="sxs-lookup"><span data-stu-id="28f8b-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="28f8b-574">Esta versão requer que o chamador forneça informações adicionais sobre o comprimento.</span><span class="sxs-lookup"><span data-stu-id="28f8b-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="28f8b-575">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-575">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-576">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-577">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-578">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="28f8b-579">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="28f8b-580">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="28f8b-581">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="28f8b-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="28f8b-582">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="28f8b-583">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-583">**Return Values**</span></span>

- <span data-ttu-id="28f8b-584">**NX_SUCCESS** (0x00) conteúdo HTTP bem sucedido obtém</span><span class="sxs-lookup"><span data-stu-id="28f8b-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="28f8b-585">**NX_HTTP_ERROR** (0xE0) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="28f8b-586">**NX_HTTP_DATA_END** (0xE7) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="28f8b-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Servidor tempo limite na obtenção do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="28f8b-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="28f8b-588">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-589">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-590">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-590">**Allowed From**</span></span>

<span data-ttu-id="28f8b-591">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-591">Threads</span></span>

<span data-ttu-id="28f8b-592">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="28f8b-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="28f8b-594">Obtenha a duração do conteúdo no pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-594">Get length of content in the request</span></span>

<span data-ttu-id="28f8b-595">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="28f8b-596">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-596">**Description**</span></span>

<span data-ttu-id="28f8b-597">Este serviço tenta recuperar o comprimento do conteúdo HTTP no pacote fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="28f8b-598">Se não houver conteúdo HTTP, esta rotina devolve um valor de zero.</span><span class="sxs-lookup"><span data-stu-id="28f8b-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="28f8b-599">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="28f8b-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-600">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-600">This service is deprecated.</span></span> <span data-ttu-id="28f8b-601">Os desenvolvedores são encorajados a migrar para nx_http_server_content_length_get_extended().</span><span class="sxs-lookup"><span data-stu-id="28f8b-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="28f8b-602">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-602">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-603">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-604">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="28f8b-605">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-605">**Return Values**</span></span>

- <span data-ttu-id="28f8b-606">**comprimento do conteúdo** Por engano, um valor de zero é devolvido</span><span class="sxs-lookup"><span data-stu-id="28f8b-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="28f8b-607">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-607">**Allowed From**</span></span>

<span data-ttu-id="28f8b-608">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-608">Threads</span></span>

<span data-ttu-id="28f8b-609">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="28f8b-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="28f8b-611">Obtenha o comprimento do conteúdo no pedido/suporta o comprimento do conteúdo de valor zero</span><span class="sxs-lookup"><span data-stu-id="28f8b-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="28f8b-612">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="28f8b-613">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-613">**Description**</span></span>

<span data-ttu-id="28f8b-614">Este serviço é semelhante ao *nx_http_server_content_length_get;;* tentativas de recuperar o comprimento do conteúdo HTTP no pacote fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="28f8b-615">No entanto, o valor de retorno indica o estado de conclusão bem-sucedido, e o valor real do comprimento é devolvido no ponteiro de entrada content_length.</span><span class="sxs-lookup"><span data-stu-id="28f8b-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="28f8b-616">Se não houver conteúdo/comprimento de conteúdo HTTP = 0, esta rotina ainda devolve um estado de conclusão bem-sucedido e o ponteiro de entrada content_length aponta para um comprimento válido (zero).</span><span class="sxs-lookup"><span data-stu-id="28f8b-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="28f8b-617">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="28f8b-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-618">Este serviço substitui *nx_http_server_content_length_get*().</span><span class="sxs-lookup"><span data-stu-id="28f8b-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="28f8b-619">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-619">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-620">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-621">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="28f8b-622">**content_length** Ponteiro para valor recuperado do campo Content Length</span><span class="sxs-lookup"><span data-stu-id="28f8b-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="28f8b-623">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-623">**Return Values**</span></span>

- <span data-ttu-id="28f8b-624">**NX_SUCCESS** (0x00) conteúdo satisfatório do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="28f8b-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Formato de cabeçalho HTTP impróprio</span><span class="sxs-lookup"><span data-stu-id="28f8b-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="28f8b-626">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-627">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-627">**Allowed From**</span></span>

<span data-ttu-id="28f8b-628">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-628">Threads</span></span>

<span data-ttu-id="28f8b-629">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="28f8b-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="28f8b-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="28f8b-631">Criar uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="28f8b-632">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-632">**Prototype**</span></span>

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

<span data-ttu-id="28f8b-633">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-633">**Description**</span></span>

<span data-ttu-id="28f8b-634">Este serviço cria uma instância http server, que funciona no contexto da sua própria linha ThreadX.</span><span class="sxs-lookup"><span data-stu-id="28f8b-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="28f8b-635">As rotinas de *chamada de authentication_check* e *request_notify* de aplicações opcionais dão ao software de aplicação controlo sobre as operações básicas do Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="28f8b-636">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-636">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-637">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="28f8b-638">**http_server_name** Ponteiro para o nome do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="28f8b-639">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="28f8b-640">**media_ptr** Ponteiro para a instância de media filex previamente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="28f8b-641">**stack_ptr** Ponteiro para a área da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="28f8b-642">**stack_size** Ponteiro para o tamanho da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="28f8b-643">**authentication_check** Função ponteiro para a rotina de verificação de autenticação da aplicação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="28f8b-644">Se especificado, esta rotina é chamada para cada pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="28f8b-645">Se este parâmetro for NU, não será efetuada qualquer autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="28f8b-646">**request_notify** Ponteiro de função para pedido de pedido de aplicação notificar rotina.</span><span class="sxs-lookup"><span data-stu-id="28f8b-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="28f8b-647">Se especificado, esta rotina é chamada antes do processamento do servidor HTTP do pedido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="28f8b-648">Isto permite que o nome do recurso seja redirecionado ou campos dentro de um recurso a ser atualizado antes de completar o pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="28f8b-649">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-649">**Return Values**</span></span>

- <span data-ttu-id="28f8b-650">**NX_SUCCESS** (0x00) o servidor HTTP com sucesso cria.</span><span class="sxs-lookup"><span data-stu-id="28f8b-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="28f8b-651">NX_PTR_ERROR (0x07) Inválido HTTP Servidor, IP, meios de comunicação, stack ou ponteiro de piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="28f8b-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="28f8b-652">NX_HTTP_POOL_ERROR (0xE9) A carga útil do pacote não é suficientemente grande para conter o pedido HTTP completo.</span><span class="sxs-lookup"><span data-stu-id="28f8b-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="28f8b-653">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-653">**Allowed From**</span></span>

<span data-ttu-id="28f8b-654">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="28f8b-654">Initialization, Threads</span></span>

<span data-ttu-id="28f8b-655">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="28f8b-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="28f8b-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="28f8b-657">Excluir uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="28f8b-658">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="28f8b-659">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-659">**Description**</span></span>

<span data-ttu-id="28f8b-660">Este serviço elimina uma instância do servidor HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="28f8b-661">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-661">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-662">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="28f8b-663">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-663">**Return Values**</span></span>

- <span data-ttu-id="28f8b-664">**NX_SUCCESS** (0x00) Com sucesso no servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="28f8b-665">NX_PTR_ERROR (0x07) Ponteiro do servidor HTTP Inválido</span><span class="sxs-lookup"><span data-stu-id="28f8b-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="28f8b-666">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-667">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-667">**Allowed From**</span></span>

<span data-ttu-id="28f8b-668">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-668">Threads</span></span>

<span data-ttu-id="28f8b-669">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="28f8b-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="28f8b-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="28f8b-671">Recuperar a localização e a duração dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="28f8b-672">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="28f8b-673">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-673">**Description**</span></span>

<span data-ttu-id="28f8b-674">Este serviço determina a localização do início dos dados dentro da atual entidade multipartidária nas mensagens do Cliente recebidas e o comprimento dos dados que não incluem a cadeia de limites.</span><span class="sxs-lookup"><span data-stu-id="28f8b-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="28f8b-675">Internamente, o servidor HTTP atualiza as suas próprias compensações para que esta função possa ser novamente chamada no mesmo datagrama do Cliente para mensagens com várias entidades.</span><span class="sxs-lookup"><span data-stu-id="28f8b-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="28f8b-676">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="28f8b-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="28f8b-677">Note que NX_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="28f8b-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="28f8b-678">Consulte *nx_http_server_get_entity_header* para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="28f8b-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="28f8b-679">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-679">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-680">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="28f8b-681">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="28f8b-682">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="28f8b-683">**available_offset** Ponteiro para compensar os dados da entidade a partir do ponteiro pré-final do pacote</span><span class="sxs-lookup"><span data-stu-id="28f8b-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="28f8b-684">**available_length** Ponteiro para o comprimento dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="28f8b-685">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-685">**Return Values**</span></span>

- <span data-ttu-id="28f8b-686">**NX_SUCCESS** (0x00) recuperou com sucesso o tamanho e localização do conteúdo da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="28f8b-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) O conteúdo dos marcadores multipartais internos do servidor HTTP já está encontrado</span><span class="sxs-lookup"><span data-stu-id="28f8b-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="28f8b-688">NX_HTTP_ERROR (0xE0) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="28f8b-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="28f8b-689">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-690">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-690">**Allowed From**</span></span>

<span data-ttu-id="28f8b-691">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-691">Threads</span></span>

<span data-ttu-id="28f8b-692">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="28f8b-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="28f8b-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="28f8b-694">Recuperar o conteúdo do cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="28f8b-695">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="28f8b-696">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-696">**Description**</span></span>

<span data-ttu-id="28f8b-697">Este serviço recupera o cabeçalho da entidade no tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="28f8b-698">Internamente HTTP Server atualiza os seus próprios ponteiros para localizar a próxima entidade multipartida num datagrama do Cliente com vários cabeçalhos de entidade.</span><span class="sxs-lookup"><span data-stu-id="28f8b-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="28f8b-699">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="28f8b-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="28f8b-700">Note que NX_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="28f8b-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="28f8b-701">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-701">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-702">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="28f8b-703">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="28f8b-704">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="28f8b-705">**entity_header_buffer** Ponteiro para localização para armazenar cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="28f8b-706">**buffer_size** Tamanho do tampão de entrada</span><span class="sxs-lookup"><span data-stu-id="28f8b-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="28f8b-707">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-707">**Return Values**</span></span>

- <span data-ttu-id="28f8b-708">**NX_SUCCESS** (0x00) conseguiu recuperar o chefe da entidade</span><span class="sxs-lookup"><span data-stu-id="28f8b-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="28f8b-709">**NX_HTTP_NOT_FOUND (0xE6)** Campo de cabeçalho de entidade não encontrado</span><span class="sxs-lookup"><span data-stu-id="28f8b-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="28f8b-710">**NX_HTTP_TIMEOUT (0xE1)** O tempo expirou para receber o próximo pacote para mensagem de cliente multipacket</span><span class="sxs-lookup"><span data-stu-id="28f8b-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="28f8b-711">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-712">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="28f8b-713">NX_HTTP_ERROR (0xE0) Erro HTTP Interno</span><span class="sxs-lookup"><span data-stu-id="28f8b-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="28f8b-714">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-714">**Allowed From**</span></span>

<span data-ttu-id="28f8b-715">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-715">Threads</span></span>

<span data-ttu-id="28f8b-716">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

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
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="28f8b-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="28f8b-718">Desa esta hora de chamada para obter a data e hora de GMT</span><span class="sxs-lookup"><span data-stu-id="28f8b-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="28f8b-719">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="28f8b-720">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-720">**Description**</span></span>

<span data-ttu-id="28f8b-721">Este serviço define a chamada para obter data e hora DE GMT com um servidor HTTP previamente criado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="28f8b-722">Este serviço é invocado com o servidor HTTP está a criar um cabeçalho em respostas do servidor HTTP ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="28f8b-723">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-723">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-724">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="28f8b-725">**gmt_get** Ponteiro para retorno GMT</span><span class="sxs-lookup"><span data-stu-id="28f8b-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="28f8b-726">**data** Ponteiro para a data recuperada</span><span class="sxs-lookup"><span data-stu-id="28f8b-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="28f8b-727">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-727">**Return Values**</span></span>

- <span data-ttu-id="28f8b-728">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="28f8b-729">NX_PTR_ERROR (0x07) Pacote inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="28f8b-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="28f8b-730">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-730">**Allowed From**</span></span>

<span data-ttu-id="28f8b-731">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-731">Threads</span></span>

<span data-ttu-id="28f8b-732">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="28f8b-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="28f8b-734">Desloque a chamada para lidar com o utilizador/senha inválido</span><span class="sxs-lookup"><span data-stu-id="28f8b-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="28f8b-735">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="28f8b-736">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-736">**Description**</span></span>

<span data-ttu-id="28f8b-737">Este serviço define a chamada invocada quando um nome de utilizador e palavra-passe inválidos é recebido num Pedido de Cliente obter, colocar ou apagar, seja por digestão ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="28f8b-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="28f8b-738">O servidor HTTP deve ser previamente criado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="28f8b-739">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-739">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-740">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="28f8b-741">**invalid_username_password_callback** Ponteiro para chamada inválida do utilizador/passe</span><span class="sxs-lookup"><span data-stu-id="28f8b-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="28f8b-742">**recurso** Ponteiro para o recurso especificado pelo cliente</span><span class="sxs-lookup"><span data-stu-id="28f8b-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="28f8b-743">**client_address** Endereço do cliente</span><span class="sxs-lookup"><span data-stu-id="28f8b-743">**client_address** Client address</span></span>
- <span data-ttu-id="28f8b-744">**request_type** Indica o tipo de pedido do cliente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="28f8b-745">Pode ser:</span><span class="sxs-lookup"><span data-stu-id="28f8b-745">May be:</span></span>
  - <span data-ttu-id="28f8b-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="28f8b-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="28f8b-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="28f8b-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="28f8b-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="28f8b-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="28f8b-749">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-749">**Return Values**</span></span>

- <span data-ttu-id="28f8b-750">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="28f8b-751">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-752">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-752">**Allowed From**</span></span>

<span data-ttu-id="28f8b-753">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-753">Threads</span></span>

<span data-ttu-id="28f8b-754">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="28f8b-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="28f8b-756">Definir mapas MIME adicionais para HTML</span><span class="sxs-lookup"><span data-stu-id="28f8b-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="28f8b-757">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="28f8b-758">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-758">**Description**</span></span>

<span data-ttu-id="28f8b-759">Este serviço permite ao desenvolvedor de aplicações HTTP adicionar tipos de MIME adicionais dos tipos de MIME predefinidos fornecidos pelo NetX HTTP Server (ver *nx_http_server_get_type* para lista de tipos definidos).</span><span class="sxs-lookup"><span data-stu-id="28f8b-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="28f8b-760">Quando um pedido de cliente é recebido, por exemplo, um pedido GET, o servidor HTTP analisa o tipo de ficheiro solicitado a partir do cabeçalho HTTP utilizando preferencialmente o conjunto de mapas MIME adicional e se não for encontrado, procura uma correspondência no mapa padrão do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="28f8b-761">Se não for encontrado qualquer correspondência, o tipo MIME predefine para "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="28f8b-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="28f8b-762">Se a função de notificação de pedido estiver registada no servidor HTTP, o pedido de notificação de chamada pode ligar *nx_http_server_type_get* para analisar o tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="28f8b-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="28f8b-763">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-763">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-764">**server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="28f8b-765">**mime_maps** Ponteiro para uma matriz de mapa MIME</span><span class="sxs-lookup"><span data-stu-id="28f8b-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="28f8b-766">**mime_map_num** Número de mapas MIME na matriz</span><span class="sxs-lookup"><span data-stu-id="28f8b-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="28f8b-767">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-767">**Return Values**</span></span>

- <span data-ttu-id="28f8b-768">**NX_SUCCESS** (0x00) conjunto de mapas MIME do servidor HTTP Server</span><span class="sxs-lookup"><span data-stu-id="28f8b-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="28f8b-769">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-770">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-770">**Allowed From**</span></span>

<span data-ttu-id="28f8b-771">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="28f8b-771">Initialization, Threads</span></span>

<span data-ttu-id="28f8b-772">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="28f8b-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="28f8b-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="28f8b-774">Extrair o comprimento do conteúdo e definir o ponteiro para o início dos dados</span><span class="sxs-lookup"><span data-stu-id="28f8b-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="28f8b-775">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="28f8b-776">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-776">**Description**</span></span>

<span data-ttu-id="28f8b-777">Este serviço extrai o comprimento do conteúdo do cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="28f8b-778">Também atualiza o pacote fornecido da seguinte forma: o ponteiro pré-final do pacote (início da localização do tampão do pacote para escrever) é definido para o conteúdo HTTP (dados) acabado de passar o cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="28f8b-779">Se o início do conteúdo não for encontrado no pacote atual, a função aguarda que o próximo pacote seja recebido utilizando a opção de espera NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="28f8b-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="28f8b-780">Note que isto não deve ser chamado antes de chamar *nx_http_server_get_entity_header()* porque modifica o ponteiro pré-final para além do cabeçalho da entidade.</span><span class="sxs-lookup"><span data-stu-id="28f8b-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="28f8b-781">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-781">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-782">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="28f8b-783">**packet_ptr** Ponteiro para ponter pacote para devolver o pacote com ponteiro pré-final atualizado</span><span class="sxs-lookup"><span data-stu-id="28f8b-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="28f8b-784">**content_length** Ponteiro para content_length extraído</span><span class="sxs-lookup"><span data-stu-id="28f8b-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="28f8b-785">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-785">**Return Values**</span></span>

- <span data-ttu-id="28f8b-786">**NX_SUCCESS** (0x00) comprimento de conteúdo HTTP encontrado e pacote atualizado com sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="28f8b-787">**NX_HTTP_TIMEOUT** (0xE1) O tempo expirou à espera do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="28f8b-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="28f8b-788">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-789">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-789">**Allowed From**</span></span>

<span data-ttu-id="28f8b-790">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-790">Threads</span></span>

<span data-ttu-id="28f8b-791">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="28f8b-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="28f8b-793">Receba o próximo pacote HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="28f8b-794">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="28f8b-795">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-795">**Description**</span></span>

<span data-ttu-id="28f8b-796">Este serviço devolve o próximo pacote recebido na tomada do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="28f8b-797">A opção de espera para receber um pacote é NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="28f8b-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="28f8b-798">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-798">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-799">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="28f8b-800">**packet_ptr** Ponteiro para pacote recebido</span><span class="sxs-lookup"><span data-stu-id="28f8b-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="28f8b-801">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-801">**Return Values**</span></span>

- <span data-ttu-id="28f8b-802">**NX_SUCCESS** (0x00) recebeu com sucesso o próximo pacote HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="28f8b-803">**NX_HTTP_TIMEOUT** (0xE1) O tempo expirou à espera do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="28f8b-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="28f8b-804">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-805">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-805">**Allowed From**</span></span>

<span data-ttu-id="28f8b-806">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-806">Threads</span></span>

<span data-ttu-id="28f8b-807">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="28f8b-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="28f8b-809">Obtenha o parâmetro do pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-809">Get parameter from the request</span></span>

<span data-ttu-id="28f8b-810">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="28f8b-811">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-811">**Description**</span></span>

<span data-ttu-id="28f8b-812">Este serviço tenta recuperar o parâmetro HTTP URL especificado no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="28f8b-813">Se o parâmetro HTTP solicitado não estiver presente, esta rotina devolve um estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="28f8b-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="28f8b-814">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).).*</span><span class="sxs-lookup"><span data-stu-id="28f8b-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-815">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-815">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-816">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-817">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="28f8b-818">**param_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="28f8b-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="28f8b-819">**param_ptr** Área de destino para copiar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28f8b-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="28f8b-820">**max_param_size** Tamanho máximo da área de destino do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="28f8b-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="28f8b-821">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-821">**Return Values**</span></span>

- <span data-ttu-id="28f8b-822">**NX_SUCCESS** (0x00) O parâmetro do servidor HTTP com sucesso obtém</span><span class="sxs-lookup"><span data-stu-id="28f8b-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="28f8b-823">**NX_HTTP_NOT_FOUND** (0xE6) Parâmetro especificado não encontrado</span><span class="sxs-lookup"><span data-stu-id="28f8b-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="28f8b-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Parâmetro de pedido não devidamente terminado</span><span class="sxs-lookup"><span data-stu-id="28f8b-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="28f8b-825">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-826">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-827">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-827">**Allowed From**</span></span>

<span data-ttu-id="28f8b-828">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-828">Threads</span></span>

<span data-ttu-id="28f8b-829">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="28f8b-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="28f8b-831">Obtenha consulta a partir do pedido</span><span class="sxs-lookup"><span data-stu-id="28f8b-831">Get query from the request</span></span>

<span data-ttu-id="28f8b-832">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="28f8b-833">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-833">**Description**</span></span>

<span data-ttu-id="28f8b-834">Este serviço tenta recuperar a consulta de URL HTTP especificada no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="28f8b-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="28f8b-835">Se a consulta HTTP solicitada não estiver presente, esta rotina devolve um estado de NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="28f8b-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="28f8b-836">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_http_server_create).).*</span><span class="sxs-lookup"><span data-stu-id="28f8b-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="28f8b-837">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-837">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-838">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="28f8b-839">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="28f8b-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="28f8b-840">**query_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="28f8b-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="28f8b-841">**query_ptr** Área de destino para copiar a consulta.</span><span class="sxs-lookup"><span data-stu-id="28f8b-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="28f8b-842">**max_query_size** Tamanho máximo da área de destino de consulta.</span><span class="sxs-lookup"><span data-stu-id="28f8b-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="28f8b-843">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-843">**Return Values**</span></span>

- <span data-ttu-id="28f8b-844">**NX_SUCCESS** (0x00) Consulta de servidor HTTP com sucesso obter</span><span class="sxs-lookup"><span data-stu-id="28f8b-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="28f8b-845">**NX_HTTP_FAILED** (0xE2) Tamanho da consulta muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="28f8b-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="28f8b-846">**NX_HTTP_NOT_FOUND** (0xE6) Consulta especificada não encontrada</span><span class="sxs-lookup"><span data-stu-id="28f8b-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="28f8b-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) Sem consulta no pedido do Cliente</span><span class="sxs-lookup"><span data-stu-id="28f8b-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="28f8b-848">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-849">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-850">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-850">**Allowed From**</span></span>

<span data-ttu-id="28f8b-851">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-851">Threads</span></span>

<span data-ttu-id="28f8b-852">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="28f8b-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="28f8b-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="28f8b-854">Inicie o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-854">Start the HTTP Server</span></span>

<span data-ttu-id="28f8b-855">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="28f8b-856">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-856">**Description**</span></span>

<span data-ttu-id="28f8b-857">Este serviço inicia a instância do servidor HTTP anteriormente.</span><span class="sxs-lookup"><span data-stu-id="28f8b-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="28f8b-858">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-858">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-859">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="28f8b-860">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-860">**Return Values**</span></span>

- <span data-ttu-id="28f8b-861">**NX_SUCCESS** (0x00) início do servidor HTTP com sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="28f8b-862">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-863">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-863">**Allowed From**</span></span>

<span data-ttu-id="28f8b-864">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="28f8b-864">Initialization, Threads</span></span>

<span data-ttu-id="28f8b-865">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="28f8b-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="28f8b-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="28f8b-867">Parar o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-867">Stop the HTTP Server</span></span>

<span data-ttu-id="28f8b-868">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="28f8b-869">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-869">**Description**</span></span>

<span data-ttu-id="28f8b-870">Este serviço para a instância do servidor HTTP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="28f8b-871">Esta rotina deve ser chamada antes de eliminar uma instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="28f8b-872">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-872">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-873">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="28f8b-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="28f8b-874">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-874">**Return Values**</span></span>

- <span data-ttu-id="28f8b-875">**NX_SUCCESS** (0x00) paragem de servidor HTTP com sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="28f8b-876">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-877">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="28f8b-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="28f8b-878">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-878">**Allowed From**</span></span>

<span data-ttu-id="28f8b-879">Fios</span><span class="sxs-lookup"><span data-stu-id="28f8b-879">Threads</span></span>

<span data-ttu-id="28f8b-880">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="28f8b-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="28f8b-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="28f8b-882">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="28f8b-883">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="28f8b-884">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-884">**Description**</span></span>

<span data-ttu-id="28f8b-885">Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento no valor de retorno a partir do *nome* do tampão de entrada , normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="28f8b-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="28f8b-886">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="28f8b-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="28f8b-887">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="28f8b-888">Os mapas MIME predefinidos no Servidor HTTP NetX são:</span><span class="sxs-lookup"><span data-stu-id="28f8b-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="28f8b-889">html texto/html</span><span class="sxs-lookup"><span data-stu-id="28f8b-889">html text/html</span></span>
- <span data-ttu-id="28f8b-890">texto/html</span><span class="sxs-lookup"><span data-stu-id="28f8b-890">htm text/html</span></span>
- <span data-ttu-id="28f8b-891">texto txt/planície</span><span class="sxs-lookup"><span data-stu-id="28f8b-891">txt text/plain</span></span>
- <span data-ttu-id="28f8b-892">gif imagem/gif</span><span class="sxs-lookup"><span data-stu-id="28f8b-892">gif image/gif</span></span>
- <span data-ttu-id="28f8b-893">jpg imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="28f8b-893">jpg image/jpeg</span></span>
- <span data-ttu-id="28f8b-894">ico imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="28f8b-894">ico image/x-icon</span></span>

<span data-ttu-id="28f8b-895">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="28f8b-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="28f8b-896">Consulte *nx_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="28f8b-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="28f8b-897">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="28f8b-897">This service is deprecated.</span></span> <span data-ttu-id="28f8b-898">Os desenvolvedores são encorajados a migrar para *nx_http_server_type_get_extended().*</span><span class="sxs-lookup"><span data-stu-id="28f8b-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="28f8b-899">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-899">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-900">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="28f8b-901">**nome** Ponteiro para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="28f8b-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="28f8b-902">**http_type_string** (Ponteiro para o tipo HTML extraído)</span><span class="sxs-lookup"><span data-stu-id="28f8b-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="28f8b-903">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-903">**Return Values**</span></span>

- <span data-ttu-id="28f8b-904">**Comprimento da corda em bytes** Não valor zero é sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="28f8b-905">**Zero indica erro**</span><span class="sxs-lookup"><span data-stu-id="28f8b-905">**Zero indicates error**</span></span>

<span data-ttu-id="28f8b-906">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-906">**Allowed From**</span></span>

<span data-ttu-id="28f8b-907">Aplicação</span><span class="sxs-lookup"><span data-stu-id="28f8b-907">Application</span></span>

<span data-ttu-id="28f8b-908">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="28f8b-909">Para um exemplo mais detalhado, consulte a descrição para</span><span class="sxs-lookup"><span data-stu-id="28f8b-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="28f8b-910">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="28f8b-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="28f8b-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="28f8b-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="28f8b-912">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="28f8b-913">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="28f8b-914">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-914">**Description**</span></span>

<span data-ttu-id="28f8b-915">Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento no valor de retorno a partir do *nome* do tampão de entrada , normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="28f8b-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="28f8b-916">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="28f8b-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="28f8b-917">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="28f8b-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="28f8b-918">Os mapas MIME padrão no NetX Duo HTTP Server são:</span><span class="sxs-lookup"><span data-stu-id="28f8b-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="28f8b-919">html texto/html</span><span class="sxs-lookup"><span data-stu-id="28f8b-919">html text/html</span></span>
- <span data-ttu-id="28f8b-920">texto/html</span><span class="sxs-lookup"><span data-stu-id="28f8b-920">htm text/html</span></span>
- <span data-ttu-id="28f8b-921">texto txt/planície</span><span class="sxs-lookup"><span data-stu-id="28f8b-921">txt text/plain</span></span>
- <span data-ttu-id="28f8b-922">gif imagem/gif</span><span class="sxs-lookup"><span data-stu-id="28f8b-922">gif image/gif</span></span>
- <span data-ttu-id="28f8b-923">jpg imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="28f8b-923">jpg image/jpeg</span></span>
- <span data-ttu-id="28f8b-924">ico imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="28f8b-924">ico image/x-icon</span></span>

<span data-ttu-id="28f8b-925">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="28f8b-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="28f8b-926">Consulte *nx_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="28f8b-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="28f8b-927">Este serviço substitui *nx_http_server_type_get.*</span><span class="sxs-lookup"><span data-stu-id="28f8b-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="28f8b-928">Esta versão fornece informações adicionais sobre o comprimento.</span><span class="sxs-lookup"><span data-stu-id="28f8b-928">This version supplies additional length information.</span></span>

<span data-ttu-id="28f8b-929">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-929">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-930">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="28f8b-931">**nome** Ponteiro para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="28f8b-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="28f8b-932">**name_length** Comprimento do tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="28f8b-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="28f8b-933">**http_type_string** (Ponteiro para o tipo HTML extraído)</span><span class="sxs-lookup"><span data-stu-id="28f8b-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="28f8b-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="28f8b-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="28f8b-935">Tamanho do tampão *http_type_string*</span><span class="sxs-lookup"><span data-stu-id="28f8b-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="28f8b-936">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-936">**Return Values**</span></span>

- <span data-ttu-id="28f8b-937">**Comprimento da corda em bytes** Não valor zero é sucesso</span><span class="sxs-lookup"><span data-stu-id="28f8b-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="28f8b-938">Zero indica erro</span><span class="sxs-lookup"><span data-stu-id="28f8b-938">Zero indicates error</span></span>

<span data-ttu-id="28f8b-939">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-939">**Allowed From**</span></span>

<span data-ttu-id="28f8b-940">Aplicação</span><span class="sxs-lookup"><span data-stu-id="28f8b-940">Application</span></span>

<span data-ttu-id="28f8b-941">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

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
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="28f8b-942">Para um exemplo mais detalhado, consulte a descrição para</span><span class="sxs-lookup"><span data-stu-id="28f8b-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="28f8b-943">*nx_http_server_callback_generate_response_header.*</span><span class="sxs-lookup"><span data-stu-id="28f8b-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="28f8b-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="28f8b-945">Detenda a função de retorno autenticado da digestão</span><span class="sxs-lookup"><span data-stu-id="28f8b-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="28f8b-946">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-946">**Prototype**</span></span>

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

<span data-ttu-id="28f8b-947">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-947">**Description**</span></span>

<span data-ttu-id="28f8b-948">Este serviço define a chamada invocada quando a digestão autenticada é realizada.</span><span class="sxs-lookup"><span data-stu-id="28f8b-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="28f8b-949">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-949">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-950">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="28f8b-951">**digest_authenticate_callback** Ponteiro para digerir chamada autenticada</span><span class="sxs-lookup"><span data-stu-id="28f8b-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="28f8b-952">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-952">**Return Values**</span></span>

- <span data-ttu-id="28f8b-953">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="28f8b-954">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="28f8b-955">NX_NOT_SUPPORTED (0x4B) Digerir autenticado não habilitado</span><span class="sxs-lookup"><span data-stu-id="28f8b-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="28f8b-956">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-956">**Allowed From**</span></span>

<span data-ttu-id="28f8b-957">Aplicação</span><span class="sxs-lookup"><span data-stu-id="28f8b-957">Application</span></span>

<span data-ttu-id="28f8b-958">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="28f8b-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="28f8b-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="28f8b-960">Definir função de verificação de autenticação</span><span class="sxs-lookup"><span data-stu-id="28f8b-960">Set authentication checking callback function</span></span>

<span data-ttu-id="28f8b-961">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="28f8b-961">**Prototype**</span></span>

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

<span data-ttu-id="28f8b-962">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="28f8b-962">**Description**</span></span>

<span data-ttu-id="28f8b-963">Este serviço define a função de retorno de chamada da verificação de autenticação.</span><span class="sxs-lookup"><span data-stu-id="28f8b-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="28f8b-964">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="28f8b-964">**Input Parameters**</span></span>

- <span data-ttu-id="28f8b-965">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="28f8b-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="28f8b-966">**authentication_check_extended** Ponteiro para verificação de autenticação da aplicação</span><span class="sxs-lookup"><span data-stu-id="28f8b-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="28f8b-967">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="28f8b-967">**Return Values**</span></span>

- <span data-ttu-id="28f8b-968">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="28f8b-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="28f8b-969">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="28f8b-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="28f8b-970">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="28f8b-970">**Allowed From**</span></span>

<span data-ttu-id="28f8b-971">Aplicação</span><span class="sxs-lookup"><span data-stu-id="28f8b-971">Application</span></span>

<span data-ttu-id="28f8b-972">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="28f8b-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```