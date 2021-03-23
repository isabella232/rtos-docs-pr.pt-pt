---
title: Capítulo 3 - Descrição do cliente dos serviços do Cliente SMTP
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SMTP (listados abaixo) por ordem de utilização numa aplicação típica do Cliente SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825789"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="c04ec-103">Capítulo 3 - Descrição do cliente dos serviços do Cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="c04ec-104">Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SMTP (listados abaixo) por ordem de utilização numa aplicação típica do Cliente SMTP.</span><span class="sxs-lookup"><span data-stu-id="c04ec-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="c04ec-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **_NX_DISABLE_ERROR_CHECKING_** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="c04ec-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="c04ec-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="c04ec-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="c04ec-107">Criar uma instância de cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c04ec-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="c04ec-108">Prototype</span></span>

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="c04ec-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c04ec-109">Description</span></span>

<span data-ttu-id="c04ec-110">Este serviço cria uma instância do Cliente SMTP na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="c04ec-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c04ec-111">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c04ec-111">Input Parameters</span></span>

- <span data-ttu-id="c04ec-112">**client_ptr** Ponteiro para o bloco de controlo do cliente SMTP;</span><span class="sxs-lookup"><span data-stu-id="c04ec-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="c04ec-113">**ip_ptr** Indicação para a instância IP;</span><span class="sxs-lookup"><span data-stu-id="c04ec-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="c04ec-114">**packet_pool_ptr** Ponteiro para piscina de pacotes de clientes;</span><span class="sxs-lookup"><span data-stu-id="c04ec-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="c04ec-115">**nome de utilizador** Nome de utilizador rescindido nulo\*\* para autenticação</span><span class="sxs-lookup"><span data-stu-id="c04ec-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="c04ec-116">**senha** Senha terminada com nulo para autenticação</span><span class="sxs-lookup"><span data-stu-id="c04ec-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="c04ec-117">**from_address** Endereço do remetente sem efeito de nulidade</span><span class="sxs-lookup"><span data-stu-id="c04ec-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="c04ec-118">**client_domain** Nome de domínio rescindido nulo</span><span class="sxs-lookup"><span data-stu-id="c04ec-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="c04ec-119">**authentication_type** Tipo de autenticação do cliente.</span><span class="sxs-lookup"><span data-stu-id="c04ec-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="c04ec-120">Os tipos suportados são:</span><span class="sxs-lookup"><span data-stu-id="c04ec-120">Supported types are:</span></span>
  - <span data-ttu-id="c04ec-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="c04ec-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="c04ec-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="c04ec-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="c04ec-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="c04ec-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="c04ec-124">**server_address** Ponteiro para o endereço IP do servidor SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="c04ec-125">**server_port** Porta TCP do servidor SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="c04ec-126">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c04ec-126">Return Values</span></span>

- <span data-ttu-id="c04ec-127">**NX_SUCCESS** (0x00) SMTP Client criado com sucesso.</span><span class="sxs-lookup"><span data-stu-id="c04ec-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="c04ec-128">Estado de criação da tomada TCP</span><span class="sxs-lookup"><span data-stu-id="c04ec-128">TCP socket creation status</span></span>
- <span data-ttu-id="c04ec-129">NX_SMTP_INVALID_PARAM (0xA5) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c04ec-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="c04ec-130">NX_IP_ADDRESS_ERROR (0x21) Tipo de endereço IP inválido</span><span class="sxs-lookup"><span data-stu-id="c04ec-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="c04ec-131">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="c04ec-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c04ec-132">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c04ec-132">Allowed From</span></span>

<span data-ttu-id="c04ec-133">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="c04ec-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="c04ec-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c04ec-134">Example</span></span>

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="c04ec-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="c04ec-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="c04ec-136">Eliminar uma instância de cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="c04ec-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="c04ec-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="c04ec-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="c04ec-138">Description</span></span>

<span data-ttu-id="c04ec-139">Este serviço elimina uma instância do Cliente SMTP anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="c04ec-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c04ec-140">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c04ec-140">Input Parameters</span></span>

- <span data-ttu-id="c04ec-141">**client_ptr** Ponteiro para a instância do cliente SMTP.</span><span class="sxs-lookup"><span data-stu-id="c04ec-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="c04ec-142">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c04ec-142">Return Values</span></span>

- <span data-ttu-id="c04ec-143">**NX_SUCCESS** (0x00) Cliente eliminado com sucesso</span><span class="sxs-lookup"><span data-stu-id="c04ec-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="c04ec-144">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="c04ec-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c04ec-145">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c04ec-145">Allowed From</span></span>

<span data-ttu-id="c04ec-146">Fios</span><span class="sxs-lookup"><span data-stu-id="c04ec-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c04ec-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c04ec-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="c04ec-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="c04ec-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="c04ec-149">Criar e enviar um artigo de correio SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="c04ec-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="c04ec-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="c04ec-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="c04ec-151">Description</span></span>

<span data-ttu-id="c04ec-152">Este serviço cria e envia um artigo de correio SMTP.</span><span class="sxs-lookup"><span data-stu-id="c04ec-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="c04ec-153">O Cliente SMTP estabelece uma ligação TCP com o SMTP Server e envia uma série de comandos SMTP.</span><span class="sxs-lookup"><span data-stu-id="c04ec-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="c04ec-154">Se não forem encontrados erros, transmitirá a mensagem de correio para o Servidor.</span><span class="sxs-lookup"><span data-stu-id="c04ec-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="c04ec-155">Independentemente de o correio ser enviado com sucesso, terminará a ligação TCP e devolverá um estado indicando o resultado da transmissão de correio.</span><span class="sxs-lookup"><span data-stu-id="c04ec-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="c04ec-156">A aplicação pode ligar para este serviço para o número de mensagens de correio que precisar de enviar sem limite.</span><span class="sxs-lookup"><span data-stu-id="c04ec-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="c04ec-157">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="c04ec-157">Input Parameters</span></span>

- <span data-ttu-id="c04ec-158">**client_ptr** Ponteiro para cliente SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="c04ec-159">**recipient_address** Endereço do destinatário rescindido nulo.</span><span class="sxs-lookup"><span data-stu-id="c04ec-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="c04ec-160">**assunto** Texto de linha de assunto sem efeito nulo;.</span><span class="sxs-lookup"><span data-stu-id="c04ec-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="c04ec-161">**prioridade** Nível prioritário em que o correio é entregue</span><span class="sxs-lookup"><span data-stu-id="c04ec-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="c04ec-162">**mail_body** Ponteiro para mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="c04ec-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="c04ec-163">**mail_body_length** Tamanho da mensagem de correio</span><span class="sxs-lookup"><span data-stu-id="c04ec-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="c04ec-164">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="c04ec-164">Return Values</span></span>

- <span data-ttu-id="c04ec-165">**NX_SUCCESS** (0x00) Mail enviado com sucesso</span><span class="sxs-lookup"><span data-stu-id="c04ec-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="c04ec-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) Exemplo de cliente SMTP não inicializado para estado de sessão SMTP Resultado da sessão SMTP</span><span class="sxs-lookup"><span data-stu-id="c04ec-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="c04ec-167">NX_PTR_ERROR (0x07) Parâmetro de ponteiro inválido</span><span class="sxs-lookup"><span data-stu-id="c04ec-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="c04ec-168">NX_SMTP_INVALID_PARAM (0xA5) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="c04ec-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="c04ec-169">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="c04ec-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="c04ec-170">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="c04ec-170">Allowed From</span></span>

<span data-ttu-id="c04ec-171">Fios</span><span class="sxs-lookup"><span data-stu-id="c04ec-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="c04ec-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c04ec-172">Example</span></span>

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
