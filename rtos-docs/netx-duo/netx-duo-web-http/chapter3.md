---
title: Capítulo 3 - Descrição dos serviços HTTP
description: Este capítulo contém uma descrição de todos os serviços NetX Web HTTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875277"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="5a5c6-103">Capítulo 3 - Descrição dos serviços HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="5a5c6-104">Este capítulo contém uma descrição de todos os serviços NetX Web HTTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="5a5c6-106">API do cliente HTTP E HTTPS</span><span class="sxs-lookup"><span data-stu-id="5a5c6-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="5a5c6-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="5a5c6-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="5a5c6-108">Abra uma tomada de texto simples para um servidor HTTP para pedidos personalizados</span><span class="sxs-lookup"><span data-stu-id="5a5c6-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-109">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-110">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-110">Description</span></span>

<span data-ttu-id="5a5c6-111">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-112">Este serviço abre uma tomada TCP de texto simples para um servidor HTTP, mas não envia nenhum pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="5a5c6-113">Os pedidos são criados com *n x_web_http_client_request_initialize()* e enviados *através nx_web_http_client_request_send()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="5a5c6-114">Os cabeçalhos HTTP personalizados podem ser adicionados ao pedido utilizando *nx_web_http_client_request_header_add()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="5a5c6-115">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="5a5c6-116">**Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-117">Os métodos nx_web_http_client_\*_start são fornecidos por conveniência (por *exemplo, nx_web_http_client_get_start*()) e manuseam a geração de pedidos e a ligação da tomada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="5a5c6-118">Pode utilizar esses serviços em vez de *nx_web_http_client_connect()* e as rotinas relacionadas se não precisar de cabeçalhos HTTP personalizados nos seus pedidos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-119">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-119">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-120">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-121">**server_ip** Endereço IP do servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="5a5c6-122">**server_port** Porta no servidor HTTP remoto (por exemplo, 80 para HTTP).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="5a5c6-123">**wait_option** Define quanto tempo o serviço vai esperar pelas operações subjacentes à rede.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="5a5c6-124">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-125">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-127">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-127">Return Values</span></span>

- <span data-ttu-id="5a5c6-128">**NX_SUCCESS** (0x00) Ligação bem sucedida da tomada TCP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="5a5c6-129">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-130">NX_WEB_HTTP_NOT_READY (0x3000A) Outro pedido já está em curso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-131">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-131">Allowed From</span></span>

<span data-ttu-id="5a5c6-132">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-133">Example</span></span>

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="5a5c6-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="5a5c6-134">nx_web_http_client_create</span></span>

<span data-ttu-id="5a5c6-135">Criar uma instância de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-137">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-137">Description</span></span>

<span data-ttu-id="5a5c6-138">Este serviço cria uma instância http cliente na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="5a5c6-139">A instância do Cliente pode ser usada para HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="5a5c6-140">Consulte os serviços *nx_web_http_client_connect()* e *nx_web_http_client_secure_connect()* para obter mais informações sobre o início de um caso HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="5a5c6-141">Consulte também a API para *nx_web_http_client_get_\*\*, *nx_web_http_client_put_**\* *nx_web_http_client_post_*\* para simples invocações de métodos GET, PUT e POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-142">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-142">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-143">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-144">**client_name** Nome da instância do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="5a5c6-145">**ip_ptr** Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="5a5c6-146">**pool_ptr** Ponteiro para piscina de pacote padrão.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="5a5c6-147">Note que os pacotes desta piscina devem ter uma carga útil suficientemente grande para manusear o cabeçalho de resposta completo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="5a5c6-148">Isto é definido por *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* em *nx_web_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="5a5c6-149">**window_size** O tamanho da tomada TCP do Cliente recebe a janela.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-150">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-150">Return Values</span></span>

- <span data-ttu-id="5a5c6-151">**NX_SUCCESS** (0x00) Sucesso http cliente criar</span><span class="sxs-lookup"><span data-stu-id="5a5c6-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="5a5c6-152">NX_PTR_ERROR (0x16) Inválido HTTP, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="5a5c6-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5a5c6-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Tamanho da carga útil inválida na piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="5a5c6-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-154">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-154">Allowed From</span></span>

<span data-ttu-id="5a5c6-155">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="5a5c6-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="5a5c6-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="5a5c6-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="5a5c6-158">Excluir uma instância de cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-160">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-160">Description</span></span>

<span data-ttu-id="5a5c6-161">Este serviço elimina uma instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-162">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-162">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-163">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-164">Return Values</span></span>

- <span data-ttu-id="5a5c6-165">**NX_SUCCESS** (0x00) Com sucesso HTTP Cliente delete</span><span class="sxs-lookup"><span data-stu-id="5a5c6-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="5a5c6-166">NX_PTR_ERROR (0x16) Ponteiro HTTP inválido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="5a5c6-167">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-168">Allowed From</span></span>

<span data-ttu-id="5a5c6-169">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="5a5c6-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="5a5c6-172">Inicie um pedido de exclusão httptext simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-174">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-174">Description</span></span>

<span data-ttu-id="5a5c6-175">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-176">Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-177">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="5a5c6-178">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-179">Esta API está prevadida.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-179">This API is deprecated.</span></span> <span data-ttu-id="5a5c6-180">Os desenvolvedores são encorajados a usar *nx_web_http_client_delete_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-181">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-181">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-182">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-183">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-184">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-185">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-186">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-187">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-188">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-189">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-190">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-191">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-192">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-193">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-195">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-195">Return Values</span></span>

- <span data-ttu-id="5a5c6-196">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE</span><span class="sxs-lookup"><span data-stu-id="5a5c6-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="5a5c6-197">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-201">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-202">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-203">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-203">Allowed From</span></span>

<span data-ttu-id="5a5c6-204">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-205">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-205">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="5a5c6-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="5a5c6-207">Inicie um pedido de exclusão httptext simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-208">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-209">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-209">Description</span></span>

<span data-ttu-id="5a5c6-210">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-211">Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-212">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="5a5c6-213">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-214">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-215">Este serviço substitui *nx_web_http_client_delete_start* ().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="5a5c6-216">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-217">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-217">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-218">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-219">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-220">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-221">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-222">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-223">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-224">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-225">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-226">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-227">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-228">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-229">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-230">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-231">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-232">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-233">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-235">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-235">Return Values</span></span>

- <span data-ttu-id="5a5c6-236">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE</span><span class="sxs-lookup"><span data-stu-id="5a5c6-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="5a5c6-237">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-241">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-242">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-243">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-243">Allowed From</span></span>

<span data-ttu-id="5a5c6-244">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-245">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-245">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="5a5c6-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="5a5c6-247">Inicie um pedido de ELIMINAÇÃO HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-249">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-249">Description</span></span>

<span data-ttu-id="5a5c6-250">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-251">Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-252">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="5a5c6-253">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-254">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-254">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-255">Os desenvolvedores são encorajados a usar *nx_web_http_client_delete_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-256">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-256">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-257">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-258">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-259">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-260">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="5a5c6-261">o recurso deve ser anulado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="5a5c6-262">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-263">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-264">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-265">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-266">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-267">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-268">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-269">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-270">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-271">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-273">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-273">Return Values</span></span>

- <span data-ttu-id="5a5c6-274">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE</span><span class="sxs-lookup"><span data-stu-id="5a5c6-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="5a5c6-275">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-279">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-280">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-281">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-281">Allowed From</span></span>

<span data-ttu-id="5a5c6-282">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-283">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-283">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="5a5c6-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="5a5c6-285">Inicie um pedido de ELIMINAÇÃO HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-286">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-286">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-287">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-287">Description</span></span>

<span data-ttu-id="5a5c6-288">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-289">Este serviço tenta enviar um pedido delete para o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-290">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *para nx_web_http_client_response_body_get para* recuperar a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="5a5c6-291">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-292">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-293">Este serviço substitui *nx_web_http_client_delete_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="5a5c6-294">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-295">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-295">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-296">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-297">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-298">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-299">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="5a5c6-300">o recurso deve ser anulado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="5a5c6-301">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-302">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-303">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-304">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-305">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-306">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-307">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-308">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-309">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-310">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-311">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-312">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-313">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-314">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-316">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-316">Return Values</span></span>

- <span data-ttu-id="5a5c6-317">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP DELETE</span><span class="sxs-lookup"><span data-stu-id="5a5c6-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="5a5c6-318">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-322">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-323">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="5a5c6-324">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-324">Allowed From</span></span>

<span data-ttu-id="5a5c6-325">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-326">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-326">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="5a5c6-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="5a5c6-328">Inicie um pedido http GET de texto simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-329">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-330">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-330">Description</span></span>

<span data-ttu-id="5a5c6-331">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-332">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-333">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-334">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-335">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-335">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-336">Os desenvolvedores são encorajados a usar *nx_web_http_client_get_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-337">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-337">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-338">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-339">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-340">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-341">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-342">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-343">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-344">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-345">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-346">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-347">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-348">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-349">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-351">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-351">Return Values</span></span>

- <span data-ttu-id="5a5c6-352">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="5a5c6-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="5a5c6-353">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-357">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-358">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-359">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-359">Allowed From</span></span>

<span data-ttu-id="5a5c6-360">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-361">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-361">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="5a5c6-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="5a5c6-363">Inicie um pedido http GET de texto simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-365">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-365">Description</span></span>

<span data-ttu-id="5a5c6-366">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-367">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-368">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-369">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-370">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-371">Este serviço substitui *nx_web_http_client_get_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="5a5c6-372">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-373">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-373">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-374">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-375">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-376">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-377">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-378">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-379">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-380">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-381">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-382">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-383">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-384">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-385">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-386">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-387">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-388">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-389">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-391">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-391">Return Values</span></span>

- <span data-ttu-id="5a5c6-392">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="5a5c6-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="5a5c6-393">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-397">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-398">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-399">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-399">Allowed From</span></span>

<span data-ttu-id="5a5c6-400">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-401">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-401">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="5a5c6-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="5a5c6-403">Inicie um pedido HTTPS GET encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-405">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-405">Description</span></span>

<span data-ttu-id="5a5c6-406">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-407">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-408">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-409">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-410">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-410">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-411">Os desenvolvedores são encorajados a usar *nx_web_http_client_get_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-412">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-412">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-413">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-414">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-415">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-416">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-417">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-418">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-419">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-420">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-421">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-422">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-423">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-424">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-425">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-426">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-428">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-428">Return Values</span></span>

- <span data-ttu-id="5a5c6-429">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="5a5c6-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="5a5c6-430">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-434">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-435">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-436">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-436">Allowed From</span></span>

<span data-ttu-id="5a5c6-437">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-438">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-438">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="5a5c6-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="5a5c6-440">Inicie um pedido HTTPS GET encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-441">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-442">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-442">Description</span></span>

<span data-ttu-id="5a5c6-443">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-444">Este serviço tenta obter o recurso especificado por "recurso" na instância do cliente HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-445">Se esta rotina voltar NX_SUCCESS, a aplicação pode então fazer várias chamadas para *nx_web_http_client_response_body_get()* para recuperar pacotes de dados correspondentes ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-446">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-447">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULO e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-448">Este serviço substitui *nx_web_http_client_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="5a5c6-449">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-450">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-450">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-451">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-452">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-453">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-454">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-455">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-456">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-457">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-458">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-459">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-460">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-461">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-462">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-463">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-464">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-465">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-466">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-467">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-468">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-470">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-470">Return Values</span></span>

- <span data-ttu-id="5a5c6-471">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de início do cliente HTTP GET</span><span class="sxs-lookup"><span data-stu-id="5a5c6-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="5a5c6-472">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-476">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-477">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-478">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-478">Allowed From</span></span>

<span data-ttu-id="5a5c6-479">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-480">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-480">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="5a5c6-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="5a5c6-482">Inicie um pedido de cabeça HTTP texto simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-483">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-484">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-484">Description</span></span>

<span data-ttu-id="5a5c6-485">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-486">Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-487">Se esta rotina voltar NX_SUCCESS, a aplicação pode então chamar *nx_web_http_client_response_body_get para* recuperar a resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="5a5c6-488">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-489">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-489">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-490">Os desenvolvedores são encorajados a usar *nx_web_http_client_head_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-491">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-491">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-492">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-493">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-494">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-495">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-496">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-497">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-498">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-499">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-500">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-501">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-502">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-503">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-505">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-505">Return Values</span></span>

- <span data-ttu-id="5a5c6-506">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD</span><span class="sxs-lookup"><span data-stu-id="5a5c6-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="5a5c6-507">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-511">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-512">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-513">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-513">Allowed From</span></span>

<span data-ttu-id="5a5c6-514">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-515">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-515">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="5a5c6-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="5a5c6-517">Inicie um pedido de cabeça HTTP texto simples</span><span class="sxs-lookup"><span data-stu-id="5a5c6-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-518">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-519">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-519">Description</span></span>

<span data-ttu-id="5a5c6-520">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-521">Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-522">Se esta rotina voltar NX_SUCCESS, a aplicação pode então chamar *nx_web_http_client_response_body_get para* recuperar a resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="5a5c6-523">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-524">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-525">Este serviço substitui *nx_web_http_client_head_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="5a5c6-526">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-527">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-527">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-528">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-529">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-530">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-531">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-532">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-533">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-534">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-535">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-536">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-537">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-538">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-539">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-540">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-541">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-542">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-543">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-545">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-545">Return Values</span></span>

- <span data-ttu-id="5a5c6-546">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD</span><span class="sxs-lookup"><span data-stu-id="5a5c6-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="5a5c6-547">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-551">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-552">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-553">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-553">Allowed From</span></span>

<span data-ttu-id="5a5c6-554">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-555">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-555">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="5a5c6-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="5a5c6-557">Inicie um pedido de CABEÇA HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-559">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-559">Description</span></span>

<span data-ttu-id="5a5c6-560">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-561">Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-562">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *nx_web_http_client_response_body_get para* recuperar a resposta do servidor correspondente ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-563">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-564">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-564">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-565">Os desenvolvedores são encorajados a usar *nx_web_http_client_head_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-566">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-566">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-567">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-568">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-569">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-570">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-571">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-572">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-573">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-574">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-575">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-576">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-577">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-578">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-579">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-580">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-582">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-582">Return Values</span></span>

- <span data-ttu-id="5a5c6-583">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD</span><span class="sxs-lookup"><span data-stu-id="5a5c6-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="5a5c6-584">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-588">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-589">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-590">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-590">Allowed From</span></span>

<span data-ttu-id="5a5c6-591">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-592">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-592">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="5a5c6-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="5a5c6-594">Inicie um pedido de CABEÇA HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-595">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-596">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-596">Description</span></span>

<span data-ttu-id="5a5c6-597">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-598">Este serviço tenta recuperar os metadados HEAD para o recurso especificado pelo ponteiro "recurso" na instância do cliente HTTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-599">Se esta rotina voltar NX_SUCCESS, a aplicação pode então ligar *nx_web_http_client_response_body_get para* recuperar a resposta do servidor correspondente ao conteúdo de recursos solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="5a5c6-600">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos GET de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="5a5c6-601">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-602">Este serviço substitui *nx_web_http_client_head_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="5a5c6-603">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-604">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-604">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-605">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-606">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-607">**server_port** Porta no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-608">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-609">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-610">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-611">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-612">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-613">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-614">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-615">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-616">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-617">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-618">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-619">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-620">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-621">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-622">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-624">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-624">Return Values</span></span>

- <span data-ttu-id="5a5c6-625">**NX_SUCCESS** (0x00) enviou com sucesso mensagem de pedido do cliente HTTP HEAD</span><span class="sxs-lookup"><span data-stu-id="5a5c6-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="5a5c6-626">**NX_WEB_HTTP_ERROR** (0x30000) Erro interno do cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="5a5c6-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Erro do cliente que comunica com o servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="5a5c6-630">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-631">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-632">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-632">Allowed From</span></span>

<span data-ttu-id="5a5c6-633">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-634">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-634">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="5a5c6-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="5a5c6-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="5a5c6-636">Alocar um pacote HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-637">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-638">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-638">Description</span></span>

<span data-ttu-id="5a5c6-639">Este serviço tenta alocar um pacote para o Cliente HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-640">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-640">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-641">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-642">**packet_ptr** Ponteiro para pacote atribuído.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="5a5c6-643">**wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="5a5c6-644">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-645">**NX_NO_WAIT** (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="5a5c6-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="5a5c6-647">**tempo limite em tiques** (0x00000001 através de 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-648">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-648">Return Values</span></span>

- <span data-ttu-id="5a5c6-649">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="5a5c6-650">**NX_NO_PACKET** (0x01) Sem pacote disponível</span><span class="sxs-lookup"><span data-stu-id="5a5c6-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="5a5c6-651">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="5a5c6-652">**NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="5a5c6-653">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-654">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-655">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-655">Allowed From</span></span>

<span data-ttu-id="5a5c6-656">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-657">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="5a5c6-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="5a5c6-659">Inicie um pedido HTTP POST</span><span class="sxs-lookup"><span data-stu-id="5a5c6-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-660">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-661">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-661">Description</span></span>

<span data-ttu-id="5a5c6-662">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-663">Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-664">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-665">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-666">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-666">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-667">Os desenvolvedores são encorajados a usar *nx_web_http_client_post_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-668">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-668">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-669">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-670">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-671">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-672">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="5a5c6-673">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-674">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-675">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-676">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-677">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-678">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-679">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-680">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-681">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-682">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-684">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-684">Return Values</span></span>

- <span data-ttu-id="5a5c6-685">**NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO</span><span class="sxs-lookup"><span data-stu-id="5a5c6-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="5a5c6-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-688">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-689">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-690">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-691">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-691">Allowed From</span></span>

<span data-ttu-id="5a5c6-692">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-693">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-693">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="5a5c6-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="5a5c6-695">Inicie um pedido HTTP POST</span><span class="sxs-lookup"><span data-stu-id="5a5c6-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-696">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-697">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-697">Description</span></span>

<span data-ttu-id="5a5c6-698">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-699">Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-700">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-701">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-702">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-703">Este serviço substitui *nx_web_http_client_post_start* ().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="5a5c6-704">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-705">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-705">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-706">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-707">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-708">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-709">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-710">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-711">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-712">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-713">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-714">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-715">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-716">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-717">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-718">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-719">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-720">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-721">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-722">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-723">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-725">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-725">Return Values</span></span>

- <span data-ttu-id="5a5c6-726">**NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO</span><span class="sxs-lookup"><span data-stu-id="5a5c6-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="5a5c6-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-729">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-730">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-731">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-732">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-732">Allowed From</span></span>

<span data-ttu-id="5a5c6-733">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-734">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-734">Example</span></span>

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="5a5c6-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="5a5c6-736">Inicie um pedido de HTTPS POST encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-737">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-737">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-738">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-738">Description</span></span>

<span data-ttu-id="5a5c6-739">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-740">Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-741">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-742">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-743">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-743">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-744">Os desenvolvedores são encorajados a usar *nx_web_http_client_post_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-745">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-745">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-746">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-747">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-748">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-749">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="5a5c6-750">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-751">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-752">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-753">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-754">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-755">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-756">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-757">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-758">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-759">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-760">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-761">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-763">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-763">Return Values</span></span>

- <span data-ttu-id="5a5c6-764">**NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO</span><span class="sxs-lookup"><span data-stu-id="5a5c6-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="5a5c6-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-767">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-768">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-769">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-770">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-770">Allowed From</span></span>

<span data-ttu-id="5a5c6-771">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-772">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-772">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="5a5c6-773">nx_web_http_client_post_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="5a5c6-774">Inicie um pedido de HTTPS POST encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-775">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-775">Prototype</span></span>

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-776">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-776">Description</span></span>

<span data-ttu-id="5a5c6-777">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-778">Este serviço tenta enviar um pedido DEM com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-779">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-780">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-781">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-782">Este serviço substitui *nx_web_http_client_post_secure_start* ().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="5a5c6-783">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-784">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-784">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-785">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-786">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-787">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-788">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-789">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-790">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-791">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-792">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-793">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-794">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-795">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-796">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-797">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-798">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-799">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-800">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-801">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-802">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-803">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-804">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-806">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-806">Return Values</span></span>

- <span data-ttu-id="5a5c6-807">**NX_SUCCESS** (0x00) enviaram com sucesso pedido de CORREIO</span><span class="sxs-lookup"><span data-stu-id="5a5c6-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="5a5c6-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-810">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-811">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-812">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-813">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-813">Allowed From</span></span>

<span data-ttu-id="5a5c6-814">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-815">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-815">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="5a5c6-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="5a5c6-817">Inicie um pedido HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-819">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-819">Description</span></span>

<span data-ttu-id="5a5c6-820">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-821">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-822">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-823">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-824">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-824">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-825">Os desenvolvedores são encorajados a usar *nx_web_http_client_put_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-826">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-826">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-827">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-828">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-829">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-830">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="5a5c6-831">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-832">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-833">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-834">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-835">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-836">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-837">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-838">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-839">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-840">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-842">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-842">Return Values</span></span>

- <span data-ttu-id="5a5c6-843">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="5a5c6-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-846">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-847">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-848">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-849">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-849">Allowed From</span></span>

<span data-ttu-id="5a5c6-850">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-851">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-851">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="5a5c6-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="5a5c6-853">Inicie um pedido HTTP PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-854">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-855">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-855">Description</span></span>

<span data-ttu-id="5a5c6-856">Este método é para **texto simples** HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="5a5c6-857">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTP no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-858">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-859">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-860">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-861">Este serviço substitui *nx_web_http_client_put_start* ().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="5a5c6-862">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-863">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-863">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-864">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-865">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-866">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-867">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-868">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-869">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-870">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-871">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-872">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-873">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-874">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-875">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-876">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-877">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-878">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-879">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-880">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-881">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-883">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-883">Return Values</span></span>

- <span data-ttu-id="5a5c6-884">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="5a5c6-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-887">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-888">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-889">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-890">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-890">Allowed From</span></span>

<span data-ttu-id="5a5c6-891">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-892">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-892">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="5a5c6-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="5a5c6-894">Inicie um pedido DE PD HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-895">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-896">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-896">Description</span></span>

<span data-ttu-id="5a5c6-897">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-898">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-899">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-900">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-901">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-901">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-902">Os desenvolvedores são encorajados a usar *nx_web_http_client_put_secure_start_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-903">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-903">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-904">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-905">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-906">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-907">**recurso** Ponteiro para cadeia URL para recurso para enviar para Server.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="5a5c6-908">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-909">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-910">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-911">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-912">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-913">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-914">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-915">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-916">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-917">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-918">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-919">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-921">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-921">Return Values</span></span>

- <span data-ttu-id="5a5c6-922">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="5a5c6-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-925">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-926">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-927">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-928">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-928">Allowed From</span></span>

<span data-ttu-id="5a5c6-929">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-930">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-930">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="5a5c6-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="5a5c6-932">Inicie um pedido DE PD HTTPS encriptado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-933">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-933">Prototype</span></span>

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-934">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-934">Description</span></span>

<span data-ttu-id="5a5c6-935">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-936">Este serviço tenta enviar um pedido PUT com o recurso especificado para o Servidor HTTPS no endereço IP fornecido e na porta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="5a5c6-937">Se esta rotina for bem sucedida, o código de aplicação deve escoar chamadas sucessivas para a rotina *nx_web_http_client_put_packet()* para enviar o conteúdo do recurso para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-938">Note que o string de recursos pode referir-se a um ficheiro local, por exemplo, "/index.htm" ou pode referir-se a outro URL, por exemplo, `http://abc.website.com/index.htm` se o SERVIDOR HTTP indicar que suporta pedidos PUT de referência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="5a5c6-939">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-940">Este serviço substitui *nx_web_http_client_put_secure_start*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="5a5c6-941">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-942">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-942">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-943">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-944">**ip_address** Endereço IP do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-945">**server_port** Porta TCP no servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-946">**recurso** Ponteiro para cadeia URL para recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="5a5c6-947">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-948">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-949">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-950">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-951">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-952">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-953">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-954">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-955">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-956">**total_bytes** Total de bytes de recursos sendo enviados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="5a5c6-957">Note que o comprimento combinado de todos os pacotes enviados através de chamadas subsequentes para *nx_web_http_client_put_packet()* deve ser igual a este valor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="5a5c6-958">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-959">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-960">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-961">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-962">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-964">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-964">Return Values</span></span>

- <span data-ttu-id="5a5c6-965">**NX_SUCCESS** (0x00) enviou com sucesso pedido PUT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="5a5c6-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Nome de utilizador demasiado grande para tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="5a5c6-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-968">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-969">NX_SIZE_ERROR (0x09) Tamanho total inválido de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="5a5c6-970">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-971">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-971">Allowed From</span></span>

<span data-ttu-id="5a5c6-972">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-973">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-973">Example</span></span>

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="5a5c6-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="5a5c6-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="5a5c6-975">Enviar o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-977">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-977">Description</span></span>

<span data-ttu-id="5a5c6-978">Este serviço tenta enviar o próximo pacote de conteúdo de recursos para o servidor HTTP para operações PUT e POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="5a5c6-979">Note que esta rotina deve ser chamada repetitivamente até que o comprimento combinado dos pacotes enviados seja igual ao "total_bytes" especificado na chamada *nx_web_http_client_put_start* ou *nx_web_http_client_post_start anteriores* (ou nas respetivas versões seguras).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="5a5c6-980">Este serviço também verifica uma resposta do servidor no caso de haver algum problema no estabelecimento da ligação HTTP (ou HTTPS).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-981">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-981">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-982">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-983">**packet_ptr** Ponteiro para o próximo conteúdo do recurso a ser enviado para o Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="5a5c6-984">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-985">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-986">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-988">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-988">Return Values</span></span>

- <span data-ttu-id="5a5c6-989">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="5a5c6-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está pronto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="5a5c6-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Recebeu código de erro do Servidor\*\*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="5a5c6-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="5a5c6-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Nome inválido e/ou senha</span><span class="sxs-lookup"><span data-stu-id="5a5c6-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="5a5c6-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) O servidor responde antes de o PUT estar completo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="5a5c6-995">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-996">NX_INVALID_PACKET (0x12) Pacote demasiado pequeno para cabeçalho TCP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="5a5c6-997">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-998">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-998">Allowed From</span></span>

<span data-ttu-id="5a5c6-999">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1000">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="5a5c6-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="5a5c6-1002">Definir transferência em pedaços para pedido HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1003">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1004">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1004">Description</span></span>

<span data-ttu-id="5a5c6-1005">Este serviço utiliza códigos de transferência em pedaços para enviar um pedido http(S) personalizado para o servidor especificado na chamada *nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect()* que previamente estabeleceu a ligação da tomada ao anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1006">Se a aplicação utilizar códigos de transferência em pedaços para enviar um pacote de dados de pedido, deve ligar para este serviço depois de ligar para *nx_web_http_client_request_packet_allocate*() e antes de ligar *nx_web_http_client_reqeust_packet_send* ().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1007">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1007">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1008">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1009">**chunk_size** Tamanho dos dados dos pedaços em octetos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="5a5c6-1010">**packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1011">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1011">Return Values</span></span>

- <span data-ttu-id="5a5c6-1012">**NX_SUCCESS** (0x00) com sucesso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="5a5c6-1013">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1014">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1014">Allowed From</span></span>

<span data-ttu-id="5a5c6-1015">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1016">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="5a5c6-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="5a5c6-1018">Adicione um cabeçalho personalizado a um pedido HTTP personalizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1019">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1020">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1020">Description</span></span>

<span data-ttu-id="5a5c6-1021">Este serviço adiciona um cabeçalho personalizado (sob a forma de nome de campo e valor) a um pedido HTTP personalizado criado com n *x_web_http_client_request_initialize()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="5a5c6-1022">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="5a5c6-1023">**Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1024">Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="5a5c6-1025">Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1026">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1026">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1027">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1028">**field_name** Cadeia de nomes de campo (por exemplo, "Tipo de Conteúdo").</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="5a5c6-1029">**name_length** Comprimento da corda de nome de campo em bytes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="5a5c6-1030">**field_value** Cadeia de valor de campo (por exemplo, "aplicação/fluxo de octetos").</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="5a5c6-1031">**value_length** Comprimento da cadeia de valor em bytes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="5a5c6-1032">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1033">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1034">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1036">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1036">Return Values</span></span>

- <span data-ttu-id="5a5c6-1037">**NX_SUCCESS** (0x00) Adição bem sucedida do cabeçalho a pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="5a5c6-1038">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1039">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1039">Allowed From</span></span>

<span data-ttu-id="5a5c6-1040">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1041">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="5a5c6-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="5a5c6-1043">Inicialize um pedido HTTP personalizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1044">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1045">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1045">Description</span></span>

<span data-ttu-id="5a5c6-1046">Este serviço cria um pedido HTTP personalizado e associa-o à instância do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-1047">Ao contrário do nx_web_http_client_get_start mais *simples()* (juntamente com os métodos de PUT, POST e as versões seguras associadas dessas API), o pedido personalizado não é enviado até que o serviço *nx_web_http_client_request_send()* seja chamado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="5a5c6-1048">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="5a5c6-1049">Isto permite pedidos HTTP personalizados destinados a aplicações específicas.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1050">Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="5a5c6-1051">Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_send))* para criar e enviar pedidos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="5a5c6-1052">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1052">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-1053">Os desenvolvedores são encorajados a usar *nx_web_http_client_request_initialize_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1054">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1054">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1055">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1056">**método** O método de pedido HTTP para usar.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="5a5c6-1057">As opções são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="5a5c6-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="5a5c6-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="5a5c6-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="5a5c6-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="5a5c6-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="5a5c6-1064">**recurso** Nome do recurso a ser transferido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="5a5c6-1065">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-1066">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-1067">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-1068">**input_size** Tamanho dos dados de entrada para PUT e POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="5a5c6-1069">Passe 0 para outras operações.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="5a5c6-1070">**transfer_encoding_trunked** Parâmetro reservado para futuro suporte de transferência com tronco.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="5a5c6-1071">**nome de utilizador** Nome de utilizador para recursos protegidos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="5a5c6-1072">**senha** Senha para recursos protegidos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="5a5c6-1073">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1074">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1075">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1077">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1077">Return Values</span></span>

- <span data-ttu-id="5a5c6-1078">**NX_SUCCESS** (0x00) Iniciação bem sucedida do pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="5a5c6-1079">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltavam algumas informações necessárias (por exemplo, input_size para PUT ou POST).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1081">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1081">Allowed From</span></span>

<span data-ttu-id="5a5c6-1082">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1083">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1083">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="5a5c6-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="5a5c6-1085">Inicialize um pedido HTTP personalizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1086">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1087">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1087">Description</span></span>

<span data-ttu-id="5a5c6-1088">Este serviço cria um pedido HTTP personalizado e associa-o à instância do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="5a5c6-1089">Ao contrário do nx_web_http_client_get_start mais *simples()* (juntamente com os métodos de PUT, POST e as versões seguras associadas dessas API), o pedido personalizado não é enviado até que o serviço *nx_web_http_client_request_send()* seja chamado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="5a5c6-1090">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="5a5c6-1091">Isto permite pedidos HTTP personalizados destinados a aplicações específicas.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1092">Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="5a5c6-1093">Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_send))* para criar e enviar pedidos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="5a5c6-1094">As cadeias de recursos, hospedeiros, nome de utilizador e palavra-passe devem ser terminadas com NULIDADE e o comprimento de cada cadeia corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-1095">Este serviço substitui *nx_web_http_client_request_initialize*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="5a5c6-1096">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1097">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1097">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1098">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1099">**método** O método de pedido HTTP para usar.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="5a5c6-1100">As opções são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="5a5c6-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="5a5c6-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="5a5c6-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="5a5c6-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="5a5c6-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="5a5c6-1107">**recurso** Nome do recurso a ser transferido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="5a5c6-1108">**resource_length** Comprimento de cadeia do recurso solicitado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="5a5c6-1109">**hospedeiro** Cadeia terminada por nulo do nome de domínio do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="5a5c6-1110">Esta cadeia é transmitida no campo do cabeçalho do anfitrião HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="5a5c6-1111">A corda do hospedeiro não pode ser nULA.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="5a5c6-1112">**host_length** Comprimento de corda do hospedeiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="5a5c6-1113">**input_size** Tamanho dos dados de entrada para PUT e POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="5a5c6-1114">Passe 0 para outras operações.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="5a5c6-1115">**transfer_encoding_trunked** Parâmetro reservado para futuro suporte de transferência com tronco.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="5a5c6-1116">**nome de utilizador** Ponteiro para o nome de utilizador opcional para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-1117">**username_length** Comprimento da corda do nome de utilizador para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="5a5c6-1118">**senha** Ponteiro para senha opcional para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="5a5c6-1119">**password_length** Comprimento da palavra-passe para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="5a5c6-1120">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1121">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1122">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1124">Return Values</span></span>

- <span data-ttu-id="5a5c6-1125">**NX_SUCCESS** (0x00) Iniciação bem sucedida do pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="5a5c6-1126">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Faltavam algumas informações necessárias (por exemplo, input_size para PUT ou POST).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1128">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1128">Allowed From</span></span>

<span data-ttu-id="5a5c6-1129">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1130">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="5a5c6-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="5a5c6-1132">Enviar pacote de dados de pedido HTTP(S) para servidor remoto</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1133">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1134">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1134">Description</span></span>

<span data-ttu-id="5a5c6-1135">Este serviço envia um pacote de dados de pedido HTTP(S) personalizado criado com *nx_web_http_client_request_packet_allocate* () para o servidor especificado na *chamada nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect,* que previamente estabeleceu a ligação da tomada ao anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1136">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1136">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1137">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1138">**packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="5a5c6-1139">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1140">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1141">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1143">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1143">Return Values</span></span>

- <span data-ttu-id="5a5c6-1144">**NX_SUCCESS** (0x00) Envio bem sucedido do pacote de dados de pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="5a5c6-1145">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1146">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1146">Allowed From</span></span>

<span data-ttu-id="5a5c6-1147">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="5a5c6-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="5a5c6-1150">Envie um pedido HTTP personalizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1152">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1152">Description</span></span>

<span data-ttu-id="5a5c6-1153">Este serviço envia um pedido HTTP personalizado criado com *nx_web_http_client_request_initialize()* para o servidor especificado no *nx_web_http_client_connect()* ou *nx_web_http_client_secure_connect()* ambos já estabeleceram previamente a ligação da tomada ao anfitrião remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="5a5c6-1154">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido utilizando o serviço ***nx_web_http_client_request_header_add().***</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="5a5c6-1155">Isto permite pedidos HTTP personalizados destinados a aplicações específicas.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1156">Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="5a5c6-1157">Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1158">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1158">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1159">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1160">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1161">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1162">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1164">Return Values</span></span>

- <span data-ttu-id="5a5c6-1165">**NX_SUCCESS** (0x00) Envio bem sucedido de pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="5a5c6-1166">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1167">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1167">Allowed From</span></span>

<span data-ttu-id="5a5c6-1168">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="5a5c6-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="5a5c6-1171">Obtenha o próximo pacote de dados de recursos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1172">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1173">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1173">Description</span></span>

<span data-ttu-id="5a5c6-1174">Este serviço recupera o próximo pacote de conteúdo do recurso solicitado pela *chamada anterior nx_web_http_client_get_start ou* *nx_web_http_client_get_secure_start().*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="5a5c6-1175">Devem ser feitas sucessivas chamadas para esta rotina até que seja recebida a situação de devolução do NX_WEB_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1176">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1176">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1177">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1178">**packet_ptr** Destino para ponteiro de pacotes que contenha conteúdo parcial de recursos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="5a5c6-1179">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1180">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1181">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1183">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1183">Return Values</span></span>

- <span data-ttu-id="5a5c6-1184">**NX_SUCCESS** (0x00) obter com sucesso do pacote do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="5a5c6-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP O pacote de obter do cliente está feito</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="5a5c6-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Cliente não está em modo get.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="5a5c6-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Comprimento do pacote inválido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="5a5c6-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) CÓDIGO DE ESTADO HTTP 100 Continuar</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="5a5c6-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP código de estado 101 Protocolos de comutação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="5a5c6-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) CÓDIGO DE ESTADO HTTP 201 Criado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="5a5c6-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP código de estado 202 Aceite</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="5a5c6-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) CÓDIGO DE Estado HTTP 203 Informação Não Autorizada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="5a5c6-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) CÓDIGO DE Estado HTTP 204 Sem Conteúdo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="5a5c6-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) CÓDIGO DE Estado HTTP 205 Redefinir Conteúdo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="5a5c6-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) CÓDIGO DE Estado HTTP 206 Conteúdo parcial</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="5a5c6-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) CÓDIGO DE ESTADO HTTP 300 Escolhas Múltiplas</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="5a5c6-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) CÓDIGO DE ESTADO HTTP 301 Movido Permanentemente</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="5a5c6-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) CÓDIGO DE ESTADO HTTP 302 Encontrado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="5a5c6-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) CÓDIGO DE Estado HTTP 303 Ver Outros</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="5a5c6-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) CÓDIGO de Estado HTTP 304 Não Modificado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="5a5c6-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) CÓDIGO de Estado HTTP 305 Use Proxy</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="5a5c6-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) CÓDIGO DE Estado HTTP 307 Reorientação Temporária</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="5a5c6-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) CÓDIGO DE Estado HTTP 400 Mau Pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="5a5c6-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) CÓDIGO DE Estado HTTP 401 Não Autorizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="5a5c6-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) CÓDIGO DE ESTADO HTTP 402 Pagamento necessário</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="5a5c6-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) CÓDIGO DE Estado HTTP 403 Proibido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="5a5c6-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) CÓDIGO DE ESTADO HTTP 404 Não Encontrado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="5a5c6-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) CÓDIGO DE Estado HTTP 405 Método não permitido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="5a5c6-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) CÓDIGO de Estado HTTP 406 Não Aceitável</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="5a5c6-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="5a5c6-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) CÓDIGO DE ESTADO HTTP 408 Prazo de saída</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="5a5c6-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) CÓDIGO DE ESTADO HTTP 409 Conflito</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="5a5c6-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) CÓDIGO de Estado HTTP 410 Desaparecido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="5a5c6-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) CÓDIGO DE ESTADO HTTP 411 Comprimento necessário</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="5a5c6-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) CÓDIGO de Estado HTTP 412 Pré-condição falhou</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="5a5c6-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP código de estado 413 Entidade de pedido demasiado grande</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="5a5c6-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP código de estado 414 Solicitar URL demasiado grande</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="5a5c6-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) CÓDIGO DE ESTADO HTTP 415 Tipo de Mídia Não Suportado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="5a5c6-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP código de estado 416 Intervalo solicitado não é satisfatório</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="5a5c6-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP código de estado 417 Expectativa falhou</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="5a5c6-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) CÓDIGO DE Estado HTTP 500 Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="5a5c6-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) CÓDIGO de Estado HTTP 501 Não implementado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="5a5c6-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) CÓDIGO DE ESTADO HTTP 502 Bad Gateway</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="5a5c6-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) CÓDIGO DE ESTADO HTTP 503 Serviço Indisponível</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="5a5c6-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) CÓDIGO DE ESTADO HTTP 504 Gateway Time-out</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="5a5c6-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) VERSÃO HTTP 505 HTTP não suportada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="5a5c6-1227">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1228">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1229">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1229">Allowed From</span></span>

<span data-ttu-id="5a5c6-1230">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1231">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="5a5c6-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="5a5c6-1233">Desateia a chamada para invocar ao processar os cabeçalhos HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1234">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1235">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1235">Description</span></span>

<span data-ttu-id="5a5c6-1236">Este serviço atribui uma chamada que será invocada sempre que o Cliente NetX Web HTTP processa um cabeçalho HTTP numa resposta recebida a partir de um servidor HTTP remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="5a5c6-1237">A chamada é invocada uma vez para cada cabeçalho na resposta à medida que é processada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="5a5c6-1238">O retorno permite que uma aplicação http cliente aceda a cada um dos cabeçalhos na resposta do servidor HTTP para tomar quaisquer ações desejadas para além do processamento básico que o Cliente Web HTTP NetX faz.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1239">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1239">Input Parameters</span></span>

<span data-ttu-id="5a5c6-1240">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="5a5c6-1241">**callback_function** Chamada invocada durante o processamento do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="5a5c6-1242">O retorno é invocado com o nome de campo e valor como cordas (e seus comprimentos).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="5a5c6-1243">Por exemplo, o cabeçalho "Content-Length: 100" faria com que a função fosse invocada com "Content-Length" para *field_name* e a cadeia "100" para *field_value*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1244">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1244">Return Values</span></span>

- <span data-ttu-id="5a5c6-1245">**NX_SUCCESS** (0x00) Atribuição bem sucedida de chamadas.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="5a5c6-1246">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1247">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1247">Allowed From</span></span>

<span data-ttu-id="5a5c6-1248">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1249">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1249">Example</span></span>

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="5a5c6-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="5a5c6-1251">Abra uma sessão de TLS para um servidor HTTPS para pedidos personalizados</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1252">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1253">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1253">Description</span></span>

<span data-ttu-id="5a5c6-1254">Este método **destina-se a HTTPS protegidos por TLS.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="5a5c6-1255">Este serviço abre uma sessão de TLS segura para um servidor HTTPS, mas não envia quaisquer pedidos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="5a5c6-1256">Os pedidos são criados com *n x_web_http_client_request_initialize()* e enviados *através nx_web_http_client_request_send()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="5a5c6-1257">Os cabeçalhos HTTP personalizados podem ser adicionados ao pedido utilizando *nx_web_http_client_request_header_add()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="5a5c6-1258">A utilização deste serviço permite que uma aplicação adicione qualquer número de cabeçalhos personalizados ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="5a5c6-1259">**Isto permite pedidos HTTP personalizados destinados a aplicações específicas.**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1260">Os \* métodos _start nx_web_http_client_ são fornecidos por conveniência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="5a5c6-1261">Todas estas funções utilizam esta rotina internamente (juntamente com *nx_web_http_client_request_initialize))* para criar e enviar pedidos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1262">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1262">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1263">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1264">**server_ip** Endereço IP do servidor HTTPS remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="5a5c6-1265">**server_port** Porta no servidor HTTPS remoto (por exemplo, 443 para HTTPS).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="5a5c6-1266">**tls_setup** Callback usado para configurar a configuração TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="5a5c6-1267">A aplicação define esta chamada de volta para inicializar a criptografia e credenciais TLS (por exemplo, certificados).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="5a5c6-1268">**wait_option** Define quanto tempo o serviço irá esperar pelo pedido de início do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="5a5c6-1269">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1270">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="5a5c6-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1272">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1272">Return Values</span></span>

- <span data-ttu-id="5a5c6-1273">**NX_SUCCESS** (0x00) Ligação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="5a5c6-1274">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Outro pedido já está em curso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1276">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1276">Allowed From</span></span>

<span data-ttu-id="5a5c6-1277">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1278">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1278">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="5a5c6-1279">API http e https servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="5a5c6-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="5a5c6-1281">Desa esta hora de chamada para recuperar a idade máxima e a data do URL</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1282">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1283">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1283">Description</span></span>

<span data-ttu-id="5a5c6-1284">Este serviço define o serviço de retorno invocado para obter a idade máxima e última data modificada do recurso especificado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1285">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1285">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1286">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1287">**cache_info_get** Ponteiro para a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="5a5c6-1288">**max_age** Ponteiro para a idade máxima de um recurso</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="5a5c6-1289">**dados** Ponteiro para a última data modificada devolvida.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1290">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1290">Return Values</span></span>

- <span data-ttu-id="5a5c6-1291">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="5a5c6-1292">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1293">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1293">Allowed From</span></span>

<span data-ttu-id="5a5c6-1294">Inicialização</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1295">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="5a5c6-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="5a5c6-1297">Enviar dados da função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1298">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1299">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1299">Description</span></span>

<span data-ttu-id="5a5c6-1300">Este serviço envia os dados no pacote fornecido da rotina de chamada da aplicação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="5a5c6-1301">Isto é normalmente usado para enviar dados dinâmicos associados a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="5a5c6-1302">Note que se esta função for utilizada, a rotina de retorno é responsável pelo envio de toda a resposta no formato adequado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="5a5c6-1303">Além disso, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1304">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1304">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1305">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1306">**data_ptr** Ponteiro para os dados a enviar.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="5a5c6-1307">**data_length** Número de bytes para enviar.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1308">Return Values</span></span>

- <span data-ttu-id="5a5c6-1309">**NX_SUCCESS** (0x00) enviou com sucesso dados do Servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="5a5c6-1310">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1311">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1311">Allowed From</span></span>

<span data-ttu-id="5a5c6-1312">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1313">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1313">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="5a5c6-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="5a5c6-1315">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1316">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1317">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1317">Description</span></span>

<span data-ttu-id="5a5c6-1318">Este serviço é utilizado na rotina de chamada do servidor HTTP(S) (definida pela aplicação) para gerar um cabeçalho de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="5a5c6-1319">A rotina de chamada do servidor é invocada quando o servidor HTTP responde a pedidos de OBTER, PUT e DELETE do Cliente que requerem uma resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="5a5c6-1320">Esta função retira a informação de resposta da aplicação e gera o cabeçalho de resposta apropriado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="5a5c6-1321">Consulte o *nx_web_http_server_create de* serviço para obter mais informações sobre a rotina de chamada do pedido do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="5a5c6-1322">Esta API está prevadida.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1322">This API is deprecated.</span></span> <span data-ttu-id="5a5c6-1323">Os desenvolvedores são encorajados a usar *nx_web_http_server_callback_generate_response_header_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1324">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1324">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1325">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1326">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="5a5c6-1327">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="5a5c6-1328">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1328">Examples:</span></span>
  - <span data-ttu-id="5a5c6-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="5a5c6-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="5a5c6-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="5a5c6-1332">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="5a5c6-1333">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="5a5c6-1334">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1335">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1335">Return Values</span></span>

- <span data-ttu-id="5a5c6-1336">**NX_SUCCESS** (0x00) Com sucesso criado cabeçalho HTML</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="5a5c6-1337">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1338">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1338">Allowed From</span></span>

<span data-ttu-id="5a5c6-1339">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1340">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1340">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="5a5c6-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="5a5c6-1342">Criar um cabeçalho de resposta numa função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1343">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1343">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1344">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1344">Description</span></span>

<span data-ttu-id="5a5c6-1345">Este serviço é utilizado na rotina de chamada do servidor HTTP(S) (definida pela aplicação) para gerar um cabeçalho de resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="5a5c6-1346">A rotina de chamada do servidor é invocada quando o servidor HTTP responde a pedidos de OBTER, PUT e DELETE do Cliente que requerem uma resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="5a5c6-1347">Esta função retira a informação de resposta da aplicação e gera o cabeçalho de resposta apropriado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="5a5c6-1348">Consulte o *nx_web_http_server_create de* serviço para obter mais informações sobre a rotina de chamada do pedido do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1349">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1349">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1350">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1351">**packet_pptr** Ponteiro um ponteiro de pacote atribuído para mensagem</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="5a5c6-1352">**status_code** Indicar o estado do recurso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="5a5c6-1353">Exemplos:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1353">Examples:</span></span>
  - <span data-ttu-id="5a5c6-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="5a5c6-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="5a5c6-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="5a5c6-1357">**status_code_length** Comprimento da cadeia do código de estado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="5a5c6-1358">**content_length** Tamanho do conteúdo em bytes</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="5a5c6-1359">**content_type** Tipo de HTTP, por exemplo, "texto/planície"</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="5a5c6-1360">**content_type_length** Comprimento de corda do tipo de conteúdo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="5a5c6-1361">**additional_header** Ponteiro para texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="5a5c6-1362">**additional_header_length** Comprimento do texto adicional do cabeçalho</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1363">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1363">Return Values</span></span>

- <span data-ttu-id="5a5c6-1364">**NX_SUCCESS** (0x00) Com sucesso criado cabeçalho HTML</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="5a5c6-1365">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1366">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1366">Allowed From</span></span>

<span data-ttu-id="5a5c6-1367">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1368">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1368">Example</span></span>

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="5a5c6-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="5a5c6-1370">Envie um pacote HTTP da função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1371">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1372">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1372">Description</span></span>

<span data-ttu-id="5a5c6-1373">Este serviço envia uma resposta completa do servidor HTTP a partir de uma chamada HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="5a5c6-1374">O servidor HTTP enviará o pacote com o NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="5a5c6-1375">O cabeçalho HTTP e os dados devem ser anexados ao pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="5a5c6-1376">Se o estado de devolução indicar um erro, a aplicação HTTP deve libertar o pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="5a5c6-1377">A chamada deve voltar NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="5a5c6-1378">Consulte *nx_web_http_server_callback_generate_response_header para* um exemplo mais detalhado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1379">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1379">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1380">**server_ptr** Ponteiro para bloco de controlo do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="5a5c6-1381">**packet_ptr** Ponteiro para o pacote para enviar</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1382">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1382">Return Values</span></span>

- <span data-ttu-id="5a5c6-1383">**NX_SUCCESS** (0x00) enviou com sucesso o pacote do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="5a5c6-1384">**NX_PTR_ERROR** (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1385">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1385">Allowed From</span></span>

<span data-ttu-id="5a5c6-1386">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1387">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1387">Example</span></span>

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="5a5c6-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="5a5c6-1389">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1390">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1391">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1391">Description</span></span>

<span data-ttu-id="5a5c6-1392">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="5a5c6-1393">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="5a5c6-1394">Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="5a5c6-1395">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1395">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-1396">Os desenvolvedores são encorajados a usar *nx_web_http_server_callback_response_send_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1397">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1397">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1398">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1399">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="5a5c6-1400">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="5a5c6-1401">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1402">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1402">Return Values</span></span>

- <span data-ttu-id="5a5c6-1403">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1404">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1404">Allowed From</span></span>

<span data-ttu-id="5a5c6-1405">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1406">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1406">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="5a5c6-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="5a5c6-1408">Enviar resposta da função de retorno</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1409">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1410">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1410">Description</span></span>

<span data-ttu-id="5a5c6-1411">Este serviço envia as informações de resposta fornecidas da rotina de retorno da aplicação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="5a5c6-1412">Isto é normalmente usado para enviar respostas personalizadas associadas a pedidos GET/POST.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="5a5c6-1413">Note que se esta função for utilizada, a rotina de retorno deve devolver o estado de NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="5a5c6-1414">As cadeias de cabeçalho, informação e additional_info devem ser terminadas com nulos e o comprimento de cada corda corresponde ao comprimento especificado na lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="5a5c6-1415">Este serviço substitui *nx_web_http_server_callback_response_send*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="5a5c6-1416">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1417">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1417">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1418">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1419">**cabeçalho** Ponteiro para a corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="5a5c6-1420">**header_length** Comprimento da corda do cabeçalho de resposta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="5a5c6-1421">**informação** Ponteiro para a cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="5a5c6-1422">**Information_length** Comprimento da cadeia de informação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="5a5c6-1423">**additional_info** Ponteiro para a cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="5a5c6-1424">**additional_info_length** Comprimento da cadeia de informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1425">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1425">Return Values</span></span>

- <span data-ttu-id="5a5c6-1426">**NX_SUCCESS** (0x00) enviou com sucesso a resposta do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1427">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1427">Allowed From</span></span>

<span data-ttu-id="5a5c6-1428">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1429">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1429">Example</span></span>

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="5a5c6-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="5a5c6-1431">Obtenha conteúdo do pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1432">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1433">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1433">Description</span></span>

<span data-ttu-id="5a5c6-1434">Este serviço tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="5a5c6-1435">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1436">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1436">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1437">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1438">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="5a5c6-1439">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="5a5c6-1440">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="5a5c6-1441">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="5a5c6-1442">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="5a5c6-1443">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1444">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1444">Return Values</span></span>

- <span data-ttu-id="5a5c6-1445">**NX_SUCCESS** (0x00) conteúdo satisfatório do servidor HTTP Obter</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="5a5c6-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="5a5c6-1447">**NX_WEB_HTTP_DATA_END** (0x30007) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="5a5c6-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Servidor tempo limite para obter o próximo pacote de conteúdo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="5a5c6-1449">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1450">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1451">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1451">Allowed From</span></span>

<span data-ttu-id="5a5c6-1452">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1453">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="5a5c6-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="5a5c6-1455">Obtenha conteúdo a partir do pedido/suporta comprimento de conteúdo zero comprimento</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1456">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1457">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1457">Description</span></span>

<span data-ttu-id="5a5c6-1458">Este serviço é quase idêntico ao *nx_web_http_server_content_get;;* tenta recuperar a quantidade especificada de conteúdo do pedido do CLIENTE POST ou PUT HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="5a5c6-1459">No entanto, trata os pedidos com contentamento comprimento de valor zero ('pedido vazio') como um pedido válido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="5a5c6-1460">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="5a5c6-1461">Este serviço substitui *nx_web_http_server_content_get*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="5a5c6-1462">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1463">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1463">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1464">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1465">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="5a5c6-1466">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="5a5c6-1467">**byte_offset** Número de bytes para compensar na área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="5a5c6-1468">**destination_ptr** Ponteiro para a área de destino para o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="5a5c6-1469">**destination_size** Número máximo de bytes disponíveis na área de destino.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="5a5c6-1470">**atual_size** Ponteiro para a variável de destino que será definida para o tamanho real do conteúdo copiado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1471">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1471">Return Values</span></span>

- <span data-ttu-id="5a5c6-1472">**NX_SUCCESS** (0x00) conteúdo HTTP bem sucedido obtém</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="5a5c6-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="5a5c6-1474">**NX_WEB_HTTP_DATA_END** (0x30007) Conteúdo de fim do pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="5a5c6-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Servidor tempo limite na obtenção do próximo pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="5a5c6-1476">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1477">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1478">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1478">Allowed From</span></span>

<span data-ttu-id="5a5c6-1479">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1480">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="5a5c6-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="5a5c6-1482">Obtenha o comprimento do conteúdo no pedido/suporta o comprimento do conteúdo de valor zero</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1483">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1484">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1484">Description</span></span>

<span data-ttu-id="5a5c6-1485">Este serviço tenta recuperar o comprimento do conteúdo HTTP no pacote fornecido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="5a5c6-1486">O valor de retorno indica o estado de conclusão bem-sucedido e o valor real do comprimento é devolvido no ponteiro de entrada content_length.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="5a5c6-1487">Se não houver conteúdo/comprimento de conteúdo HTTP = 0, esta rotina ainda devolve um estado de conclusão bem-sucedido e o ponteiro de entrada content_length aponta para um comprimento válido (zero).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="5a5c6-1488">Deve ser chamado a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create()*).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1489">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1489">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1490">**packet_ptr** Ponteiro para o pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="5a5c6-1491">Note que este pacote não deve ser divulgado pelo pedido notificar o retorno.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="5a5c6-1492">**content_length** Ponteiro para valor recuperado do campo Content Length</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1493">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1493">Return Values</span></span>

- <span data-ttu-id="5a5c6-1494">**NX_SUCCESS** (0x00) sucesso http servidor comprimento de conteúdo obter</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="5a5c6-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Formato de cabeçalho HTTP impróprio</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="5a5c6-1496">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1497">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1497">Allowed From</span></span>

<span data-ttu-id="5a5c6-1498">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1499">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="5a5c6-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="5a5c6-1501">Criar uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1502">Prototype</span></span>

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1503">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1503">Description</span></span>

<span data-ttu-id="5a5c6-1504">Este serviço cria uma instância http server, que funciona no contexto da sua própria linha ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="5a5c6-1505">As rotinas de *chamada de authentication_check* e *request_notify* de aplicações opcionais dão ao software de aplicação controlo sobre as operações básicas do Servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="5a5c6-1506">Este serviço é utilizado para criar servidores HTTP de texto simples e servidores HTTPS protegidos por TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="5a5c6-1507">Para ativar o HTTPS utilizando o TLS, consulte o *serviço nx_web_http_server_secure_configure()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1508">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1508">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1509">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1510">**http_server_name** Ponteiro para o nome do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="5a5c6-1511">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="5a5c6-1512">**server_port** Porta de escuta TCP para a instância do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="5a5c6-1513">**media_ptr** Ponteiro para a instância de media filex previamente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="5a5c6-1514">**stack_ptr** Ponteiro para a área da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="5a5c6-1515">**stack_size** Ponteiro para o tamanho da pilha de fio do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="5a5c6-1516">**authentication_check** Função ponteiro para a rotina de verificação de autenticação da aplicação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="5a5c6-1517">Se especificado, esta rotina é chamada para cada pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="5a5c6-1518">Se este parâmetro for NU, não será efetuada qualquer autenticação.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="5a5c6-1519">Este parâmetro está precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1519">This parameter is deprecated.</span></span> <span data-ttu-id="5a5c6-1520">Chame *nx_web_http_server_authenticate_check_set* em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="5a5c6-1521">**request_notify** Ponteiro de função para pedido de pedido de aplicação notificar rotina.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="5a5c6-1522">Se especificado, esta rotina é chamada antes do processamento do servidor HTTP do pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="5a5c6-1523">Isto permite que o nome do recurso seja redirecionado ou campos dentro de um recurso a ser atualizado antes de completar o pedido do Cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1524">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1524">Return Values</span></span>

- <span data-ttu-id="5a5c6-1525">**NX_SUCCESS** (0x00) o servidor HTTP com sucesso cria.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="5a5c6-1526">NX_PTR_ERROR (0x07) Inválido HTTP Servidor, IP, meios de comunicação, stack ou ponteiro de piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="5a5c6-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) A carga útil do pacote não é suficientemente grande para conter o pedido HTTP completo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1528">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1528">Allowed From</span></span>

<span data-ttu-id="5a5c6-1529">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1530">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="5a5c6-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="5a5c6-1532">Excluir uma instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1533">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1534">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1534">Description</span></span>

<span data-ttu-id="5a5c6-1535">Este serviço elimina uma instância do servidor HTTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1536">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1536">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1537">**http_server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1538">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1538">Return Values</span></span>

- <span data-ttu-id="5a5c6-1539">**NX_SUCCESS** (0x00) Com sucesso no servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="5a5c6-1540">NX_PTR_ERROR (0x07) Ponteiro do servidor HTTP Inválido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="5a5c6-1541">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1542">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1542">Allowed From</span></span>

<span data-ttu-id="5a5c6-1543">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1544">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="5a5c6-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="5a5c6-1546">Recuperar a localização e a duração dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1547">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1548">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1548">Description</span></span>

<span data-ttu-id="5a5c6-1549">Este serviço determina a localização do início dos dados dentro da atual entidade multipartidária nas mensagens do Cliente recebidas e o comprimento dos dados que não incluem a cadeia de limites.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="5a5c6-1550">Internamente, o servidor HTTP atualiza as suas próprias compensações para que esta função possa ser novamente chamada no mesmo datagrama do Cliente para mensagens com várias entidades.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="5a5c6-1551">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="5a5c6-1552">Note que NX_WEB_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="5a5c6-1553">Note também que o pedido não deve libertar o pacote apontado por packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="5a5c6-1554">Isto é feito internamente pelo servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="5a5c6-1555">Consulte *nx_web_http_server_get_entity_header para* mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1556">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1556">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1557">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="5a5c6-1558">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="5a5c6-1559">Note que o pedido não deve lançar este pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="5a5c6-1560">**available_offset** Ponteiro para compensar os dados da entidade a partir do ponteiro pré-final do pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="5a5c6-1561">**available_length** Ponteiro para o comprimento dos dados da entidade</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1562">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1562">Return Values</span></span>

- <span data-ttu-id="5a5c6-1563">**NX_SUCCESS** (0x00) recuperou com sucesso o tamanho e localização do conteúdo da entidade</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="5a5c6-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) O conteúdo dos marcadores multipartais internos do servidor HTTP já está encontrado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="5a5c6-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Erro interno do servidor</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="5a5c6-1566">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1567">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1567">Allowed From</span></span>

<span data-ttu-id="5a5c6-1568">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1569">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1569">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="5a5c6-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="5a5c6-1571">Recuperar o conteúdo do cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1572">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1573">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1573">Description</span></span>

<span data-ttu-id="5a5c6-1574">Este serviço recupera o cabeçalho da entidade no tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="5a5c6-1575">Internamente HTTP Server atualiza os seus próprios ponteiros para localizar a próxima entidade multipartida num datagrama do Cliente com vários cabeçalhos de entidade.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="5a5c6-1576">O ponteiro do pacote é atualizado para o próximo pacote onde a mensagem cliente é um datagrama de vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="5a5c6-1577">Note que NX_WEB_HTTP_MULTIPART_ENABLE devem ser habilitados a utilizar este serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="5a5c6-1578">Note também que o pedido não deve libertar o pacote apontado por packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1579">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1579">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1580">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="5a5c6-1581">**packet_pptr** Ponteiro para a localização do ponteiro do pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="5a5c6-1582">Note que o pedido não deve lançar este pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="5a5c6-1583">**entity_header_buffer** Ponteiro para localização para armazenar cabeçalho da entidade</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="5a5c6-1584">**buffer_size** Tamanho do tampão de entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1585">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1585">Return Values</span></span>

- <span data-ttu-id="5a5c6-1586">**NX_SUCCESS** (0x00) entidade recuperada com sucesso</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="5a5c6-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Campo de cabeçalho de entidade não encontrado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="5a5c6-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou para receber o próximo pacote para mensagem de cliente multipacket</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="5a5c6-1589">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1590">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="5a5c6-1591">NX_WEB_HTTP_ERROR (0x30000) Erro interno HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1592">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1592">Allowed From</span></span>

<span data-ttu-id="5a5c6-1593">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1594">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1594">Example</span></span>

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="5a5c6-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="5a5c6-1596">Desa esta hora de chamada para obter a data e hora de GMT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1597">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1598">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1598">Description</span></span>

<span data-ttu-id="5a5c6-1599">Este serviço define a chamada para obter data e hora DE GMT com um servidor HTTP previamente criado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="5a5c6-1600">Este serviço é invocado com o servidor HTTP está a criar um cabeçalho em respostas do servidor HTTP ao Cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1601">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1601">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1602">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="5a5c6-1603">**gmt_get** Ponteiro para retorno GMT</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="5a5c6-1604">**data** Ponteiro para a data recuperada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1605">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1605">Return Values</span></span>

- <span data-ttu-id="5a5c6-1606">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="5a5c6-1607">NX_PTR_ERROR (0x07) Pacote inválido ou ponteiro de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1608">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1608">Allowed From</span></span>

<span data-ttu-id="5a5c6-1609">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1610">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1610">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="5a5c6-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="5a5c6-1612">Desloque a chamada para lidar com o utilizador/senha inválido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1613">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1614">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1614">Description</span></span>

<span data-ttu-id="5a5c6-1615">Este serviço define a chamada invocada quando um nome de utilizador e palavra-passe inválidos é recebido num Pedido de Cliente obter, colocar ou apagar, seja por digestão ou autenticação básica.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="5a5c6-1616">O servidor HTTP deve ser previamente criado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1617">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1617">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1618">**server_ptr** Ponteiro para o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="5a5c6-1619">**invalid_username_password_callback** Ponteiro para chamada inválida do utilizador/passe</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="5a5c6-1620">**recurso** Ponteiro para o recurso especificado pelo cliente</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="5a5c6-1621">**client_address** Endereço do cliente</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1621">**client_address** Client address</span></span>
- <span data-ttu-id="5a5c6-1622">**request_type** Indica o tipo de pedido do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="5a5c6-1623">Pode ser:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1623">May be:</span></span>
  - <span data-ttu-id="5a5c6-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="5a5c6-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="5a5c6-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1627">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1627">Return Values</span></span>

- <span data-ttu-id="5a5c6-1628">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="5a5c6-1629">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1630">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1630">Allowed From</span></span>

<span data-ttu-id="5a5c6-1631">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1632">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1632">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="5a5c6-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="5a5c6-1634">Definir mapas MIME adicionais para HTML</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1635">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1636">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1636">Description</span></span>

<span data-ttu-id="5a5c6-1637">Este serviço permite ao desenvolvedor de aplicações HTTP adicionar tipos de MIME adicionais dos tipos de MIME predefinidos fornecidos pelo Servidor WEB HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="5a5c6-1638">Consulte *nx_web_http_server_get_type para lista* de tipos definidos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="5a5c6-1639">Quando um pedido de cliente é recebido, por exemplo, um pedido GET, o servidor HTTP analisa o tipo de ficheiro solicitado a partir do cabeçalho HTTP utilizando preferencialmente o conjunto de mapas MIME adicional e se não for encontrado, procura uma correspondência no mapa padrão do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="5a5c6-1640">Se não for encontrado qualquer correspondência, o tipo MIME predefine para "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="5a5c6-1641">Se a função de notificação de pedido estiver registada no servidor HTTP, o pedido de notificação de chamada pode ligar *nx_web_http_server_type_get_extended()* para analisar o tipo de ficheiro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1642">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1642">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1643">**server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="5a5c6-1644">**mime_maps** Ponteiro para uma matriz de mapa MIME</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="5a5c6-1645">**mime_map_num** Número de mapas MIME na matriz</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1646">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1646">Return Values</span></span>

- <span data-ttu-id="5a5c6-1647">**NX_SUCCESS** (0x00) conjunto de mapas MIME do servidor HTTP Server</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="5a5c6-1648">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1649">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1649">Allowed From</span></span>

<span data-ttu-id="5a5c6-1650">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1651">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1651">Example</span></span>

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="5a5c6-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="5a5c6-1653">Alocar um pacote HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1654">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1655">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1655">Description</span></span>

<span data-ttu-id="5a5c6-1656">Este serviço tenta atribuir um pacote para o servidor HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="5a5c6-1657">Note que se uma API do Servidor NetX ou HTTP subsequente utilizar este pacote como **entrada falhar**, como nx_packet_data_append ou \*\*nx_web_http_server_callback_packet_send, a aplicação é responsável pela libertação do pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1658">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1658">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1659">**server_ptr** Ponteiro para o bloco de controlo do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="5a5c6-1660">**packet_ptr** Ponteiro para pacote atribuído.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="5a5c6-1661">**wait_option** Define o tempo de espera em carrapatos se não houver pacotes disponíveis na piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="5a5c6-1662">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="5a5c6-1663">**NX_NO_WAIT** (0x00000000) A seleção NX_NO_WAIT faz com que o fio de chamada regresse imediatamente se o pedido não puder ser cumprido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="5a5c6-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) A seleção NX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor HTTP responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="5a5c6-1665">**O valor de tempo limite** (0x00000001 através de 0xFFFFFFFE) Selecionar um valor numérico (0x1-0xFFFFFFFE) especifica o número máximo de tempotaques para permanecer suspenso enquanto se aguarda a resposta do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1666">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1666">Return Values</span></span>

- <span data-ttu-id="5a5c6-1667">**NX_SUCCESS** (0x00) Atribuição de pacotes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="5a5c6-1668">**NX_NO_PACKET** (0x01) Sem pacote disponível</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="5a5c6-1669">**NX_WAIT_ABORTED** (0x1A) A suspensão solicitada foi abortada por uma chamada para *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="5a5c6-1670">**NX_INVALID_PARAMETERS** (0x4D) O tamanho do pacote não pode suportar o protocolo.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="5a5c6-1671">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1672">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1673">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1673">Allowed From</span></span>

<span data-ttu-id="5a5c6-1674">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1675">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="5a5c6-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="5a5c6-1677">Extrair o comprimento do conteúdo e definir o ponteiro para o início dos dados</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1678">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1679">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1679">Description</span></span>

<span data-ttu-id="5a5c6-1680">Este serviço extrai o comprimento do conteúdo do cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="5a5c6-1681">Também atualiza o pacote fornecido da seguinte forma: o ponteiro pré-final do pacote (início da localização do tampão do pacote para escrever) é definido para o conteúdo HTTP (dados) acabado de passar o cabeçalho HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="5a5c6-1682">Se o início do conteúdo não for encontrado no pacote atual, a função aguarda que o próximo pacote seja recebido utilizando a opção de espera NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="5a5c6-1683">Note que isto não deve ser chamado antes de chamar *nx_web_http_server_get_entity_header()* porque modifica o ponteiro pré-final do pacote para além do cabeçalho da entidade.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1684">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1684">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1685">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="5a5c6-1686">**packet_ptr** Ponteiro para ponter pacote para devolver o pacote com ponteiro pré-final atualizado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="5a5c6-1687">**content_length** Ponteiro para content_length extraído</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1688">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1688">Return Values</span></span>

- <span data-ttu-id="5a5c6-1689">**NX_SUCCESS** (0x00) comprimento de conteúdo HTTP encontrado e pacote atualizado com sucesso</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="5a5c6-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou à espera do próximo Pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="5a5c6-1691">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1692">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1692">Allowed From</span></span>

<span data-ttu-id="5a5c6-1693">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1694">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1694">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="5a5c6-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="5a5c6-1696">Receba o próximo pacote HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1697">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1698">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1698">Description</span></span>

<span data-ttu-id="5a5c6-1699">Este serviço devolve o próximo pacote recebido na tomada do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="5a5c6-1700">A opção de espera para receber um pacote é NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="5a5c6-1701">Note que, se for bem sucedido, a aplicação é responsável pela libertação do pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1702">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1702">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1703">**server_ptr** Ponteiro para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="5a5c6-1704">**packet_ptr** Ponteiro para pacote recebido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1705">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1705">Return Values</span></span>

- <span data-ttu-id="5a5c6-1706">**NX_SUCCESS** (0x00) recebeu com sucesso o próximo pacote HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="5a5c6-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) O tempo expirou à espera do próximo Pacote</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="5a5c6-1708">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1709">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1709">Allowed From</span></span>

<span data-ttu-id="5a5c6-1710">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1711">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="5a5c6-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="5a5c6-1713">Obtenha o parâmetro do pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1714">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1715">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1715">Description</span></span>

<span data-ttu-id="5a5c6-1716">Este serviço tenta recuperar o parâmetro HTTP URL especificado no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="5a5c6-1717">Se o parâmetro HTTP solicitado não estiver presente, esta rotina devolve um estado de NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="5a5c6-1718">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create).).*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1719">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1719">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1720">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="5a5c6-1721">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="5a5c6-1722">**param_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="5a5c6-1723">**param_ptr** Área de destino para copiar o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="5a5c6-1724">**param_size** Devolva o comprimento total dos dados do parâmetro (em bytes).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="5a5c6-1725">**max_param_size** Tamanho máximo da área de destino do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1726">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1726">Return Values</span></span>

- <span data-ttu-id="5a5c6-1727">**NX_SUCCESS** (0x00) O parâmetro do servidor HTTP com sucesso obtém</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="5a5c6-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Parâmetro especificado não encontrado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="5a5c6-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Parâmetro de pedido não devidamente terminado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="5a5c6-1730">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1731">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1732">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1732">Allowed From</span></span>

<span data-ttu-id="5a5c6-1733">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1734">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="5a5c6-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="5a5c6-1736">Obtenha consulta a partir do pedido</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1737">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1738">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1738">Description</span></span>

<span data-ttu-id="5a5c6-1739">Este serviço tenta recuperar a consulta de URL HTTP especificada no pacote de pedido fornecido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="5a5c6-1740">Se a consulta HTTP solicitada não estiver presente, esta rotina devolve um estado de NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="5a5c6-1741">Esta rotina deve ser chamada a partir do pedido da aplicação notificar a chamada especificada durante a criação do SERVIDOR HTTP *(nx_web_http_server_create).).*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1742">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1742">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1743">**packet_ptr** Ponteiro para pacote de pedido do cliente HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="5a5c6-1744">Note que o pedido não deve libertar este pacote.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="5a5c6-1745">**query_number** Número lógico do parâmetro a partir de zero, da esquerda para a direita na lista de consultas.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="5a5c6-1746">**query_ptr** Área de destino para copiar a consulta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="5a5c6-1747">**query_size** Devolução do tamanho dos dados de consulta (em bytes).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="5a5c6-1748">**max_query_size** Tamanho máximo do destino de consulta</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="5a5c6-1749">área.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1750">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1750">Return Values</span></span>

- <span data-ttu-id="5a5c6-1751">**NX_SUCCESS** (0x00) Consulta de servidor HTTP com sucesso obter</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="5a5c6-1752">**NX_WEB_HTTP_FAILED** (0x30002) Tamanho da consulta muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="5a5c6-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Consulta especificada não encontrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="5a5c6-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) Sem consulta no pedido do Cliente</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="5a5c6-1755">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1756">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1757">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1757">Allowed From</span></span>

<span data-ttu-id="5a5c6-1758">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1759">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="5a5c6-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="5a5c6-1761">Definir transferência em pedaços para resposta HTTP(S)</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1762">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1763">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1763">Description</span></span>

<span data-ttu-id="5a5c6-1764">Este serviço utiliza códigos de transferência em pedaços para enviar um pacote de dados de resposta HTTP(S) personalizado criado com *nx_web_http_server_response_packet_allocate*() ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1765">Se a aplicação utilizar códigos de transferência em pedaços para enviar um pacote de dados de resposta, deve ligar para este serviço depois de ligar para *nx_web_http_server_response_packet_allocate*() e antes de ligar *para nx_web_http_server_callback_packet_send*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1766">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1766">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1767">**client_ptr** Ponteiro para http bloco de controlo do cliente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="5a5c6-1768">**chunk_size** Tamanho dos dados dos pedaços em octetos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="5a5c6-1769">**packet_ptr** HTTP(S) solicitar ponteiro de pacote de dados.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1770">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1770">Return Values</span></span>

- <span data-ttu-id="5a5c6-1771">**NX_SUCCESS** (0x00) Conjunto bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="5a5c6-1772">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1773">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1773">Allowed From</span></span>

<span data-ttu-id="5a5c6-1774">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1775">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="5a5c6-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="5a5c6-1777">Configure um servidor HTTP para utilizar O TLS para HTTPS seguro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1778">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1778">Prototype</span></span>

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1779">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1779">Description</span></span>

<span data-ttu-id="5a5c6-1780">Este serviço configura uma instância do servidor NetX Web HTTP previamente criada para utilizar TLS para comunicações HTTPS seguras.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="5a5c6-1781">Os parâmetros são usados para configurar todas as sessões TLS possíveis com estado idêntico para que cada cliente HTTPS que chega experimente um comportamento consistente.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="5a5c6-1782">O número de sessões TLS é controlado utilizando o NX_WEB_HTTP_SESSION_MAX macro.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="5a5c6-1783">A tabela de rotina criptográfica (tabela cifrasumita) é partilhada entre todas as sessões de TLS, uma vez que contém apenas ponteiros de função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="5a5c6-1784">Os amortecedores de metadados e de montagem de pacotes são divididos igualmente entre todas as sessões de TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="5a5c6-1785">Se o tamanho do tampão não for igualmente divisível pelo número de sessões, o restante não será reutilizado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="5a5c6-1786">O certificado de identidade aprovado é utilizado por todas as sessões.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="5a5c6-1787">Durante a operação TLS, o certificado de identidade do servidor é lido apenas de modo a não ser necessárias cópias para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="5a5c6-1788">Os certificados fidedignos são adicionados a cada sessão de TLS no Servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="5a5c6-1789">Estes são utilizados para a autenticação do certificado cliente que é automaticamente ativado quando o espaço do certificado remoto é fornecido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="5a5c6-1790">O conjunto de certificados remotos e o tampão são partilhados por padrão entre todas as sessões TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="5a5c6-1791">Os certificados remotos são utilizados para a autenticação do certificado cliente que é automaticamente ativado quando a contagem de certificados remotos não é zero.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="5a5c6-1792">Devido à partilha do tampão, algumas sessões podem bloquear durante a validação do certificado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="5a5c6-1793">Para desativar a autenticação do certificado do cliente, passe NX_NULL para o parâmetro remote_certificates e um valor de 0 para o parâmetro remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="5a5c6-1794">Os valores de retorno incluirão quaisquer códigos de erro TLS resultantes de problemas na configuração das sessões TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1795">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1795">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1796">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="5a5c6-1797">**crypto_table** Ponteiro para a mesa de cifrasumita TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="5a5c6-1798">**metadata_buffer** Ponteiro para tampão de metadados criptográfico.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="5a5c6-1799">**metadata_size** Tamanho do tampão de metadados criptográficos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="5a5c6-1800">**packet_buffer** Tampão de remontagem do pacote TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="5a5c6-1801">**packet_buffer** Tamanho do tampão de pacote TLS – deve ser igual a (<tamanho do tampão TLS desejado\* NX_WEB_HTTP_SESSION_MAX).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="5a5c6-1802">**identity_certificate** Certificado de identidade do servidor TLS – será utilizado para todas as sessões do servidor HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="5a5c6-1803">**trusted_certificates** Ponteiro para a matriz de objetos NX_SECURE_X509_CERT, utilizados para validar certificados de clientes recebidos se a autenticação do certificado do cliente for ativada através da passagem de um valor não zero para o parâmetro *remote_certs_num.*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="5a5c6-1804">**trusted_certs_num** Número de certificados de confiança no conjunto *trusted_certificates.*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="5a5c6-1805">**remote_certificates** Ponteiro para a matriz de objetos NX_SECURE_X509_CERT, utilizados para os certificados de cliente de entrada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="5a5c6-1806">**remote_certs_num** Número de certificados remotos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="5a5c6-1807">Deve ser o número máximo de certificados esperados dos clientes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="5a5c6-1808">A autenticação do certificado do cliente é ativada automaticamente quando esta não é zero.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="5a5c6-1809">**remote_certificate_buffer** Tampão para conter certificados remotos de entrada de clientes se a autenticação do certificado do cliente estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="5a5c6-1810">remote_cert_buffer_size Tamanho do tampão de certificados remotos.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="5a5c6-1811">Deve ser igual a (<tamanho máximo esperado do certificado \* remote_certs_num).</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="5a5c6-1812">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1812">Return Values</span></span>

- <span data-ttu-id="5a5c6-1813">**NX_SUCCESS** (0x00) Iniciação bem sucedida da sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="5a5c6-1814">**NX_NOT_CONNECTED** (0x38) A tomada TCP subjacente já não está ligada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="5a5c6-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Um tipo de mensagem TLS recebido está incorreto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="5a5c6-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) Uma cifra fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="5a5c6-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) O processamento de mensagens durante o aperto de mão TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="5a5c6-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) Uma mensagem recebida falhou numa verificação de HASH MAC.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="5a5c6-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) Falhou um envio de tomadaS TCP subjacentes.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="5a5c6-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Uma mensagem recebida tinha um campo de comprimento inválido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="5a5c6-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) Uma mensagem ChangeCipherSpec recebida estava incorreta.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="5a5c6-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) Um certificado TLS de entrada é inutilizável para identificar o servidor TLS remoto.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="5a5c6-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) A cifra de chave pública fornecida pelo hospedeiro remoto não é suportada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="5a5c6-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) O anfitrião remoto não indicou cifrasuites que sejam suportadas pela pilha NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="5a5c6-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Uma mensagem TLS recebida tinha uma versão TLS desconhecida no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="5a5c6-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Uma mensagem TLS recebida tinha uma versão TLS conhecida mas não suportada no seu cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="5a5c6-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Uma atribuição interna de pacotes TLS falhou.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="5a5c6-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) O anfitrião remoto forneceu um certificado inválido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="5a5c6-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) O anfitrião remoto enviou um alerta indicando um erro e terminando a sessão TLS.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="5a5c6-1830">**NX_PTR_ERROR** (0x07) Tentou usar um ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1831">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1831">Allowed From</span></span>

<span data-ttu-id="5a5c6-1832">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1833">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1833">Example</span></span>

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a><span data-ttu-id="5a5c6-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="5a5c6-1835">Inicie o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1836">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1837">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1837">Description</span></span>

<span data-ttu-id="5a5c6-1838">Este serviço inicia uma instância http ou https anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="5a5c6-1839">Os servidores HTTPS partilham a mesma API que HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="5a5c6-1840">Para ativar o HTTPS utilizando o TLS num servidor HTTP, consulte o *serviço nx_web_http_server_secure_configure().*</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1841">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1841">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1842">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1843">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1843">Return Values</span></span>

- <span data-ttu-id="5a5c6-1844">**NX_SUCCESS** (0x00) Início do servidor HTTP Com sucesso</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="5a5c6-1845">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1846">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1846">Allowed From</span></span>

<span data-ttu-id="5a5c6-1847">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1848">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="5a5c6-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="5a5c6-1850">Parar o servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1851">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1852">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1852">Description</span></span>

<span data-ttu-id="5a5c6-1853">Este serviço para a instância do servidor HTTP anteriormente criado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="5a5c6-1854">Esta rotina deve ser chamada antes de eliminar uma instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1855">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1855">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1856">**http_server_ptr** Indicação para a instância do servidor HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1857">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1857">Return Values</span></span>

- <span data-ttu-id="5a5c6-1858">**NX_SUCCESS** (0x00) Paragem de servidor HTTP bem sucedida</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="5a5c6-1859">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1860">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1861">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1861">Allowed From</span></span>

<span data-ttu-id="5a5c6-1862">Fios</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1863">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="5a5c6-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="5a5c6-1865">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1866">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1867">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="5a5c6-1868">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1868">This service is deprecated.</span></span> <span data-ttu-id="5a5c6-1869">Os utilizadores são encorajados a utilizar o serviço *nx_web_http_server_type_get_extended()*.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="5a5c6-1870">Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento em *string_size* a partir do *nome* do tampão de entrada , normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="5a5c6-1871">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="5a5c6-1872">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="5a5c6-1873">Os mapas MIME padrão no Servidor HTTP Web NetX são:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="5a5c6-1874">html texto/html</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1874">html text/html</span></span>
- <span data-ttu-id="5a5c6-1875">texto/html</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1875">htm text/html</span></span>
- <span data-ttu-id="5a5c6-1876">texto txt/planície</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1876">txt text/plain</span></span>
- <span data-ttu-id="5a5c6-1877">gif imagem/gif</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1877">gif image/gif</span></span>
- <span data-ttu-id="5a5c6-1878">jpg imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="5a5c6-1879">ico imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1879">ico image/x-icon</span></span>

<span data-ttu-id="5a5c6-1880">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="5a5c6-1881">Consulte *nx_web_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1882">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1882">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1883">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="5a5c6-1884">**nome** Ponteiro para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="5a5c6-1885">**http_type_string** Ponteiro para a cadeia do tipo HTML extraída</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="5a5c6-1886">**string_size** Ponteiro para devolver comprimento de cadeia do tipo HTML extraído.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1887">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1887">Return Values</span></span>

- <span data-ttu-id="5a5c6-1888">**NX_SUCCESS** (0x00) Extração bem sucedida do tipo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="5a5c6-1889">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Padrão "texto/planície" devolvido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1891">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1891">Allowed From</span></span>

<span data-ttu-id="5a5c6-1892">Aplicação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1893">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1893">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="5a5c6-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="5a5c6-1895">Extrair o tipo de ficheiro do pedido do Cliente HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1896">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="5a5c6-1897">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1897">Description</span></span>

<span data-ttu-id="5a5c6-1898">Este serviço extrai o tipo de pedido HTTP no *http_type_string* tampão e o seu comprimento em *string_size* a partir do *nome* do tampão de entrada , normalmente o URL.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="5a5c6-1899">Se não for encontrado nenhum mapa MIME, este desrescume do tipo "texto/planície".</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="5a5c6-1900">Caso contrário, compara o tipo extraído com os mapas MIME padrão do servidor HTTP para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="5a5c6-1901">Os mapas MIME padrão no Servidor HTTP Web NetX são:</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="5a5c6-1902">html texto/html</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1902">html text/html</span></span>
- <span data-ttu-id="5a5c6-1903">texto/html</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1903">htm text/html</span></span>
- <span data-ttu-id="5a5c6-1904">texto txt/planície</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1904">txt text/plain</span></span>
- <span data-ttu-id="5a5c6-1905">gif imagem/gif</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1905">gif image/gif</span></span>
- <span data-ttu-id="5a5c6-1906">jpg imagem/jpeg</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="5a5c6-1907">ico imagem/x-ícone</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1907">ico image/x-icon</span></span>

<span data-ttu-id="5a5c6-1908">Se for fornecido, também procurará um conjunto definido pelo utilizador de mapas MIME adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="5a5c6-1909">Consulte *nx_web_http_server_mime_maps_addtional_set para* obter mais detalhes sobre os mapas definidos pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="5a5c6-1910">Este serviço substitui *nx_web_http_server_type_get*().</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="5a5c6-1911">Esta versão requer que os chamadores forneçam informações de comprimento à função.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1912">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1912">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1913">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="5a5c6-1914">**nome** Ponteiro para tampão para pesquisar</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="5a5c6-1915">**name_length** Comprimento do nome</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="5a5c6-1916">**http_type_string** Ponteiro para a cadeia do tipo HTML extraída</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="5a5c6-1917">**http_type_string_max_size** Tamanho do http_type_string tamanho do tampão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="5a5c6-1918">**string_size** Ponteiro para devolver a cadeia do tipo HTML extraída</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="5a5c6-1919">comprimento.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1920">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1920">Return Values</span></span>

- <span data-ttu-id="5a5c6-1921">**NX_SUCCESS** (0x00) Extração bem sucedida do tipo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="5a5c6-1922">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Padrão "texto/planície" devolvido.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1924">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1924">Allowed From</span></span>

<span data-ttu-id="5a5c6-1925">Aplicação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1926">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1926">Example</span></span>

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="5a5c6-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="5a5c6-1928">Detenda a função de retorno autenticado da digestão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1929">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1929">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1930">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1930">Description</span></span>

<span data-ttu-id="5a5c6-1931">Este serviço define a chamada invocada quando a digestão autenticada é realizada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1932">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1932">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1933">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="5a5c6-1934">**digest_authenticate_callback** Ponteiro para digerir chamada autenticada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1935">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1935">Return Values</span></span>

- <span data-ttu-id="5a5c6-1936">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="5a5c6-1937">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="5a5c6-1938">NX_NOT_SUPPORTED (0x4B) Digerir autenticado não habilitado</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1939">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1939">Allowed From</span></span>

<span data-ttu-id="5a5c6-1940">Aplicação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1941">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1941">Example</span></span>

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="5a5c6-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="5a5c6-1943">Detenda a função de retorno autenticado da digestão</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a5c6-1944">Prototype</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1944">Prototype</span></span>

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a><span data-ttu-id="5a5c6-1945">Description</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1945">Description</span></span>

<span data-ttu-id="5a5c6-1946">Este serviço define a chamada invocada quando é efetuada uma verificação autenticada.</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a5c6-1947">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1947">Input Parameters</span></span>

- <span data-ttu-id="5a5c6-1948">**http_server_ptr** Ponteiros para a instância do servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="5a5c6-1949">**authenticate_check_externded** Ponteiro para autenticar retorno de verificação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="5a5c6-1950">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1950">Return Values</span></span>

- <span data-ttu-id="5a5c6-1951">**NX_SUCCESS** (0x00) definiu com sucesso a chamada</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="5a5c6-1952">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a5c6-1953">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1953">Allowed From</span></span>

<span data-ttu-id="5a5c6-1954">Aplicação</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="5a5c6-1955">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a5c6-1955">Example</span></span>

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
