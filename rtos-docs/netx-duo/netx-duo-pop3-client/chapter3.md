---
title: Capítulo 3 - Descrição dos serviços de clientes POP3
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo POP3 (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825843"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="9d4d2-103">Capítulo 3 - Descrição dos Serviços de Clientes POP3</span><span class="sxs-lookup"><span data-stu-id="9d4d2-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="9d4d2-104">Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo POP3 (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="9d4d2-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="9d4d2-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="9d4d2-106">nx_pop3_client_create</span></span>

<span data-ttu-id="9d4d2-107">Criar uma instância de cliente POP3 para iPv4</span><span class="sxs-lookup"><span data-stu-id="9d4d2-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="9d4d2-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-109">Description</span></span>

<span data-ttu-id="9d4d2-110">Este serviço cria uma instância do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="9d4d2-111">Suporta apenas endereços de servidor IPv4 POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="9d4d2-112">Note que a aplicação do dispositivo deve primeiro criar uma instância IP e um pacote de piscina para o Cliente POP3 transmitir pacotes.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="9d4d2-113">Este pacote de piscina criado para ser utilizado exclusivamente pela tarefa do Cliente POP3 ou pelo mesmo conjunto de pacotes utilizado na criação de instância IP.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="9d4d2-114">O pool de pacotes também pode ser partilhado com o pool de pacotes do controlador Ethernet, mas isso tem a desvantagem de usar grandes pacotes cuja carga útil se destina a receber uma carga útil potencialmente grande para o Cliente POP3 enviar pacotes de mensagens POP3 relativamente pequenos para o servidor.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-115">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-115">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-116">**client_ptr** Ponteiro para o Cliente para criar</span><span class="sxs-lookup"><span data-stu-id="9d4d2-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="9d4d2-117">**APOP_authentication** Ativar a autenticação APOP</span><span class="sxs-lookup"><span data-stu-id="9d4d2-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="9d4d2-118">**ip_ptr Pointer** para a instância IP</span><span class="sxs-lookup"><span data-stu-id="9d4d2-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="9d4d2-119">**packet_pool_ptr** Ponteiro para piscina de pacotes de cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="9d4d2-120">**server_ip_address** Endereço IPv4 do servidor POP3</span><span class="sxs-lookup"><span data-stu-id="9d4d2-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="9d4d2-121">**server_port** Porta de servidor POP3</span><span class="sxs-lookup"><span data-stu-id="9d4d2-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="9d4d2-122">**client_name** Ponteiro para o nome do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="9d4d2-123">**client_password** Ponteiro para senha do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-124">Return Values</span></span>

- <span data-ttu-id="9d4d2-125">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="9d4d2-126">**estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX</span><span class="sxs-lookup"><span data-stu-id="9d4d2-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="9d4d2-127">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="9d4d2-128">NX_POP3_PARAM_ERROR (0xB1) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-129">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-129">Allowed From</span></span>

<span data-ttu-id="9d4d2-130">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="9d4d2-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="9d4d2-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="9d4d2-133">Criar uma instância de cliente POP3 para IPv4 ou IPv6</span><span class="sxs-lookup"><span data-stu-id="9d4d2-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="9d4d2-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-135">Description</span></span>

<span data-ttu-id="9d4d2-136">Este serviço cria uma instância do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="9d4d2-137">Suporta os endereços de servidor IPv4 e IPv6 POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="9d4d2-138">Consulte o serviço *de nx_pop3_client_create* previamente descrito para obter mais detalhes sobre o processo de criação do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-139">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-139">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-140">**client_ptr** Ponteiro para o Cliente para criar</span><span class="sxs-lookup"><span data-stu-id="9d4d2-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="9d4d2-141">**APOP_authentication** Ativar a autenticação APOP</span><span class="sxs-lookup"><span data-stu-id="9d4d2-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="9d4d2-142">**ip_ptr** Indicação para a instância IP</span><span class="sxs-lookup"><span data-stu-id="9d4d2-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="9d4d2-143">**packet_pool_ptr** Ponteiro para piscina de pacotes de cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="9d4d2-144">**server_ip_address** Endereço IPv6 ou IPv4 do servidor POP3 ou IPv4</span><span class="sxs-lookup"><span data-stu-id="9d4d2-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="9d4d2-145">**server_port** Porta de servidor POP3</span><span class="sxs-lookup"><span data-stu-id="9d4d2-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="9d4d2-146">**client_name**  Ponteiro para o nome do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="9d4d2-147">**client_password** Ponteiro para senha do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-148">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-148">Return Values</span></span>

- <span data-ttu-id="9d4d2-149">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="9d4d2-150">**estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX</span><span class="sxs-lookup"><span data-stu-id="9d4d2-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="9d4d2-151">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="9d4d2-152">NX_POP3_PARAM_ERROR (0xB1) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-153">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-153">Allowed From</span></span>

<span data-ttu-id="9d4d2-154">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="9d4d2-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="9d4d2-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="9d4d2-157">Excluir uma instância de cliente POP3</span><span class="sxs-lookup"><span data-stu-id="9d4d2-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-158">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="9d4d2-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-159">Description</span></span>

<span data-ttu-id="9d4d2-160">Este serviço elimina um Cliente POP3 previamente criado.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="9d4d2-161">Não que este serviço não apague a piscina de pacotes do Cliente POP3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="9d4d2-162">A aplicação do dispositivo deve eliminar este recurso separadamente se deixar de ter a sua utilização para o conjunto de pacotes.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-163">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-163">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-164">**client_ptr** Ponteiro para o Cliente para apagar</span><span class="sxs-lookup"><span data-stu-id="9d4d2-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-165">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-165">Return Values</span></span>

- <span data-ttu-id="9d4d2-166">**NX_SUCCESS** (0x00) Cliente eliminado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="9d4d2-167">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-168">Allowed From</span></span>

<span data-ttu-id="9d4d2-169">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="9d4d2-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="9d4d2-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="9d4d2-172">Excluir um item de correio especificado da gota de correio do Cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="9d4d2-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-174">Description</span></span>

<span data-ttu-id="9d4d2-175">Este serviço elimina o item de correio especificado da gota de correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="9d4d2-176">Destina-se a depois de descarregar o item de correio, embora alguns servidores POP3 possam apagar automaticamente os itens de correio depois de terem sido solicitados pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-177">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-177">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-178">**client_ptr** Ponteiro para a instância do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="9d4d2-179">**mail_index** Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-180">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-180">Return Values</span></span>

- <span data-ttu-id="9d4d2-181">**NX_SUCCESS** (0x00) Eliminar pedido de sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="9d4d2-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="9d4d2-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Carga de pacote de cliente demasiado pequena para pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="9d4d2-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="9d4d2-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="9d4d2-186">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-187">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-187">Allowed From</span></span>

<span data-ttu-id="9d4d2-188">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-189">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="9d4d2-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="9d4d2-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="9d4d2-191">Recuperar um item de correio especificado</span><span class="sxs-lookup"><span data-stu-id="9d4d2-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-192">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="9d4d2-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-193">Description</span></span>

<span data-ttu-id="9d4d2-194">Este serviço faz um pedido DEMÁ para recuperar um item de correio da gota de correio do Cliente especificada pelo índice mail_item.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="9d4d2-195">Depois de estivar um pedido DEMS, e receber uma resposta positiva do Servidor, o Cliente pode começar a descarregar a mensagem de correio utilizando o serviço *nx_pop3_client_mail_item_message_get.*</span><span class="sxs-lookup"><span data-stu-id="9d4d2-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="9d4d2-196">Note que o serviço também fornece o tamanho do item de correio solicitado extraído da resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-197">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-197">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-198">**client_ptr** Ponteiro para a instância do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="9d4d2-199">**mail_item** Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="9d4d2-200">**item_size** Ponteiro para o tamanho da mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="9d4d2-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-201">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-201">Return Values</span></span>

- <span data-ttu-id="9d4d2-202">**NX_SUCCESS** (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="9d4d2-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="9d4d2-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Carga de pacote de cliente demasiado pequena para pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="9d4d2-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="9d4d2-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="9d4d2-207">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-208">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-208">Allowed From</span></span>

<span data-ttu-id="9d4d2-209">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-210">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="9d4d2-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="9d4d2-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="9d4d2-212">Recuperar o número de artigos de correio na gota de correio</span><span class="sxs-lookup"><span data-stu-id="9d4d2-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-213">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="9d4d2-214">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-214">Description</span></span>

<span data-ttu-id="9d4d2-215">Este serviço faz um pedido de STAT para recuperar o número de itens de correio e o tamanho total dos dados de mensagens de correio da gota de correio do Cliente.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-216">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-216">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-217">**client_ptr** Ponteiro para a instância do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="9d4d2-218">**number_mail_item** Número de correio na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="9d4d2-219">**maildrop_total_size** Ponteiro para o tamanho de todas as mensagens de correio</span><span class="sxs-lookup"><span data-stu-id="9d4d2-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-220">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-220">Return Values</span></span>

- <span data-ttu-id="9d4d2-221">**NX_SUCCESS** (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="9d4d2-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="9d4d2-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Carga de pacote de cliente demasiado pequena para pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="9d4d2-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="9d4d2-225">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-226">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-226">Allowed From</span></span>

<span data-ttu-id="9d4d2-227">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-228">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="9d4d2-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="9d4d2-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="9d4d2-230">Recuperar a mensagem de envio de correio especificado</span><span class="sxs-lookup"><span data-stu-id="9d4d2-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="9d4d2-232">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-232">Description</span></span>

<span data-ttu-id="9d4d2-233">Este serviço recupera a mensagem de envio de correio, o tamanho da mensagem de correio e se for o último pacote na mensagem de correio.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="9d4d2-234">Se final_packet for NX_TRUE o pacote apontado por recv_packet_ptr é o pacote final na mensagem do envio de correio.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-235">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-235">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-236">**client_ptr** Ponteiro para a instância do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="9d4d2-237">**recv_packet_ptr** Pacote de dados de mensagens recebido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="9d4d2-238">**number_mail_item** Número de correio na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="9d4d2-239">**maildrop_total_size** Ponteiro para o tamanho de todas as mensagens de correio</span><span class="sxs-lookup"><span data-stu-id="9d4d2-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-240">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-240">Return Values</span></span>

- <span data-ttu-id="9d4d2-241">**NX_SUCCESS** (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="9d4d2-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Carga de pacote de cliente demasiado pequena para pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="9d4d2-243">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-244">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-244">Allowed From</span></span>

<span data-ttu-id="9d4d2-245">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-246">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="9d4d2-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="9d4d2-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="9d4d2-248">Recuperar o tamanho do item de correio especificado</span><span class="sxs-lookup"><span data-stu-id="9d4d2-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="9d4d2-249">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d4d2-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="9d4d2-250">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d4d2-250">Description</span></span>

<span data-ttu-id="9d4d2-251">Este serviço faz um pedido LIST para obter o tamanho do item de correio especificado.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d4d2-252">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d4d2-252">Input Parameters</span></span>

- <span data-ttu-id="9d4d2-253">**client_ptr** Ponteiro para a instância do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="9d4d2-254">**mail_item** Índice na gota de correio do cliente</span><span class="sxs-lookup"><span data-stu-id="9d4d2-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="9d4d2-255">**tamanho** Ponteiro para o tamanho da mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="9d4d2-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="9d4d2-256">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d4d2-256">Return Values</span></span>

- <span data-ttu-id="9d4d2-257">**NX_SUCCESS** (0x00) Artigo de correio recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d4d2-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="9d4d2-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Índice de envio de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="9d4d2-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Carga de pacote de cliente demasiado pequena para pedido pop3.</span><span class="sxs-lookup"><span data-stu-id="9d4d2-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="9d4d2-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) O servidor responde com estado de erro</span><span class="sxs-lookup"><span data-stu-id="9d4d2-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="9d4d2-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Entrada do índice de correio inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="9d4d2-262">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="9d4d2-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d4d2-263">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d4d2-263">Allowed From</span></span>

<span data-ttu-id="9d4d2-264">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="9d4d2-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="9d4d2-265">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4d2-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
