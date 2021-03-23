---
title: Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX POP3
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX POP3 (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826660"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="3974f-103">Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX POP3</span><span class="sxs-lookup"><span data-stu-id="3974f-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="3974f-104">Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX POP3 (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="3974f-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="3974f-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="3974f-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="3974f-106">nx_pop3_client_create: Criar *uma instância de cliente POP3*</span><span class="sxs-lookup"><span data-stu-id="3974f-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="3974f-107">nx_pop3_client_delete: *Eliminar uma instância de cliente POP3*</span><span class="sxs-lookup"><span data-stu-id="3974f-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="3974f-108">nx_pop3_client_ mail_item_get: *Eliminar um item de correio do Cliente a partir da gota de correio do Servidor*</span><span class="sxs-lookup"><span data-stu-id="3974f-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="3974f-109">nx_pop3_client_mail_item_get: Recuperar *um tamanho específico de mensagem de correio*</span><span class="sxs-lookup"><span data-stu-id="3974f-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="3974f-110">nx_pop3_client_mail_items_get: Obtenha *o número de artigos de correio em gota de correio*</span><span class="sxs-lookup"><span data-stu-id="3974f-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="3974f-111">nx_pop3_client_mail_item_message _get: *Descarregue uma mensagem de correio específica*</span><span class="sxs-lookup"><span data-stu-id="3974f-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="3974f-112">nx_pop3_client_mail_item_size_get: Obtenha *o tamanho de um item de correio específico*</span><span class="sxs-lookup"><span data-stu-id="3974f-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="3974f-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="3974f-113">nx_pop3_client_create</span></span>

<span data-ttu-id="3974f-114">Criar uma instância de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="3974f-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-115">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="3974f-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-116">Description</span></span>

<span data-ttu-id="3974f-117">Este serviço cria uma instância do Cliente POP3 e configura a sua configuração com os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="3974f-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-118">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-118">Input Parameters</span></span>

- <span data-ttu-id="3974f-119">**client_ptr**: Ponteiro para o Cliente para criar</span><span class="sxs-lookup"><span data-stu-id="3974f-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="3974f-120">**APOP_authentication**: Ativar a autenticação APOP</span><span class="sxs-lookup"><span data-stu-id="3974f-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="3974f-121">**ip_ptr**: Indicação para a instância IP</span><span class="sxs-lookup"><span data-stu-id="3974f-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="3974f-122">**packet_pool_ptr**: Ponteiro para piscina de pacotes de clientes</span><span class="sxs-lookup"><span data-stu-id="3974f-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="3974f-123">**server_ip_address**: endereço do servidor POP3</span><span class="sxs-lookup"><span data-stu-id="3974f-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="3974f-124">**server_port**: Porta de servidor POP3</span><span class="sxs-lookup"><span data-stu-id="3974f-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="3974f-125">**client_name**: Ponteiro para o nome do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="3974f-126">**client_password**: Ponteiro para a senha do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-127">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-127">Return Values</span></span>

- <span data-ttu-id="3974f-128">**NX_SUCCESS**: (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="3974f-129">**estado**: Conclusão do estado das chamadas de serviço NetX e ThreadX</span><span class="sxs-lookup"><span data-stu-id="3974f-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="3974f-130">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="3974f-131">NX_POP3_PARAM_ERROR: (0xB1) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3974f-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-132">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-132">Allowed From</span></span>

<span data-ttu-id="3974f-133">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-134">Example</span></span>

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="3974f-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="3974f-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="3974f-136">Excluir uma instância de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="3974f-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="3974f-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-138">Description</span></span>

<span data-ttu-id="3974f-139">Este serviço elimina um Cliente POP3 previamente criado.</span><span class="sxs-lookup"><span data-stu-id="3974f-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="3974f-140">Não que este serviço não apague a piscina de pacotes do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="3974f-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="3974f-141">A aplicação do dispositivo deve eliminar este recurso separadamente se deixar de ter a sua utilização para o conjunto de pacotes.</span><span class="sxs-lookup"><span data-stu-id="3974f-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-142">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-142">Input Parameters</span></span>

- <span data-ttu-id="3974f-143">**client_ptr**: Ponteiro para o Cliente para eliminar</span><span class="sxs-lookup"><span data-stu-id="3974f-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-144">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-144">Return Values</span></span>

- <span data-ttu-id="3974f-145">**NX_SUCCESS**: (0x00) Cliente eliminado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="3974f-146">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-147">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-147">Allowed From</span></span>

<span data-ttu-id="3974f-148">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="3974f-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="3974f-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="3974f-151">Excluir um item de correio especificado da gota de correio do Cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-152">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="3974f-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-153">Description</span></span>

<span data-ttu-id="3974f-154">Este serviço elimina o item de correio especificado da gota de correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="3974f-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="3974f-155">Destina-se a depois de descarregar o item de correio, embora alguns servidores POP3 possam apagar automaticamente os itens de correio depois de terem sido solicitados pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="3974f-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-156">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-156">Input Parameters</span></span>

- <span data-ttu-id="3974f-157">**client_ptr**: Indicação à instância do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="3974f-158">**mail_index**: Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-159">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-159">Return Values</span></span>

- <span data-ttu-id="3974f-160">**NX_SUCCESS**: (0x00) Eliminar pedido bem sucedido</span><span class="sxs-lookup"><span data-stu-id="3974f-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="3974f-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3974f-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="3974f-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3974f-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="3974f-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3974f-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3974f-165">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-166">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-166">Allowed From</span></span>

<span data-ttu-id="3974f-167">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="3974f-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="3974f-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="3974f-170">Recuperar um item de correio especificado</span><span class="sxs-lookup"><span data-stu-id="3974f-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-171">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="3974f-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-172">Description</span></span>

<span data-ttu-id="3974f-173">Este serviço faz um pedido DEMÁ para recuperar um item de correio da gota de correio do Cliente especificada pelo índice mail_item.</span><span class="sxs-lookup"><span data-stu-id="3974f-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="3974f-174">Depois de estivar um pedido DEMS, e receber uma resposta positiva do Servidor, o Cliente pode começar a descarregar a mensagem de correio utilizando o serviço *nx_pop3_client_mail_item_message_get.*</span><span class="sxs-lookup"><span data-stu-id="3974f-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="3974f-175">Note que o serviço também fornece o tamanho do item de correio solicitado extraído da resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="3974f-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-176">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-176">Input Parameters</span></span>

- <span data-ttu-id="3974f-177">**client_ptr**: Indicação à instância do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="3974f-178">**mail_item**: Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="3974f-179">**item_size**: Ponteiro para o tamanho da mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="3974f-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-180">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-180">Return Values</span></span>

- <span data-ttu-id="3974f-181">**NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3974f-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3974f-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="3974f-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3974f-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="3974f-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3974f-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3974f-186">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-187">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-187">Allowed From</span></span>

<span data-ttu-id="3974f-188">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="3974f-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="3974f-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="3974f-191">Recuperar o número de artigos de correio na gota de correio</span><span class="sxs-lookup"><span data-stu-id="3974f-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="3974f-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-193">Description</span></span>

<span data-ttu-id="3974f-194">Este serviço faz um pedido de STAT para recuperar o número de itens de correio e o tamanho total dos dados de mensagens de correio da gota de correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="3974f-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-195">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-195">Input Parameters</span></span>

- <span data-ttu-id="3974f-196">**client_ptr**: Indicação à instância do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="3974f-197">**number_mail_item**: Número de correio na escuta do correio do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="3974f-198">**maildrop_total_size**: Ponteiro para o tamanho de todas as mensagens de correio</span><span class="sxs-lookup"><span data-stu-id="3974f-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-199">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-199">Return Values</span></span>

- <span data-ttu-id="3974f-200">**NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3974f-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3974f-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="3974f-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3974f-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="3974f-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="3974f-204">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-205">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-205">Allowed From</span></span>

<span data-ttu-id="3974f-206">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-207">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="3974f-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="3974f-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="3974f-209">Recuperar a mensagem de envio de correio especificado</span><span class="sxs-lookup"><span data-stu-id="3974f-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-210">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="3974f-211">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-211">Description</span></span>

<span data-ttu-id="3974f-212">Este serviço recupera a mensagem de envio de correio, o tamanho da mensagem de correio e se for o último pacote na mensagem de correio.</span><span class="sxs-lookup"><span data-stu-id="3974f-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="3974f-213">Se `final_packet` for NX_TRUE o pacote apontado é o pacote final na `recv_packet_ptr` mensagem de envio de correio.</span><span class="sxs-lookup"><span data-stu-id="3974f-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-214">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-214">Input Parameters</span></span>

- <span data-ttu-id="3974f-215">**client_ptr**: Indicação à instância do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="3974f-216">**recv_packet_ptr**: Recebeu pacote de dados de mensagens</span><span class="sxs-lookup"><span data-stu-id="3974f-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="3974f-217">**number_mail_item**: Número de correio na escuta do correio do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="3974f-218">**maildrop_total_size**: Ponteiro para o tamanho de todas as mensagens de correio</span><span class="sxs-lookup"><span data-stu-id="3974f-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-219">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-219">Return Values</span></span>

- <span data-ttu-id="3974f-220">**NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3974f-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="3974f-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3974f-222">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-223">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-223">Allowed From</span></span>

<span data-ttu-id="3974f-224">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-225">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="3974f-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="3974f-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="3974f-227">Recuperar o tamanho do item de correio especificado</span><span class="sxs-lookup"><span data-stu-id="3974f-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="3974f-228">Prototype</span><span class="sxs-lookup"><span data-stu-id="3974f-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="3974f-229">Descrição</span><span class="sxs-lookup"><span data-stu-id="3974f-229">Description</span></span>

<span data-ttu-id="3974f-230">Este serviço faz um pedido LIST para obter o tamanho do item de correio especificado.</span><span class="sxs-lookup"><span data-stu-id="3974f-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3974f-231">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3974f-231">Input Parameters</span></span>

- <span data-ttu-id="3974f-232">**client_ptr**: Indicação à instância do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="3974f-233">**mail_item**: Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="3974f-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="3974f-234">**tamanho**: Ponteiro para o tamanho da mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="3974f-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="3974f-235">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3974f-235">Return Values</span></span>

- <span data-ttu-id="3974f-236">**NX_SUCCESS**: (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="3974f-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="3974f-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="3974f-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) A carga útil do pacote do cliente é demasiado pequena para o pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="3974f-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="3974f-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="3974f-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="3974f-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="3974f-241">NX_PTR_ERROR: (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="3974f-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3974f-242">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3974f-242">Allowed From</span></span>

<span data-ttu-id="3974f-243">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="3974f-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="3974f-244">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3974f-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
