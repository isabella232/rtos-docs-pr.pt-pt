---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo MQTT
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo MQTT (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825897"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="2b36b-103">Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="2b36b-104">Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo MQTT (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="2b36b-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="2b36b-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="2b36b-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2b36b-106">**nxd_mqtt_client_create Criar** *caso de cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="2b36b-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="2b36b-107">**nxd_mqtt_client_will_message_set** *Definir a mensagem de testamento*</span><span class="sxs-lookup"><span data-stu-id="2b36b-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="2b36b-108">**nxd_mqtt_client_client_login_set** *Definir nome de utilizador e palavra-passe do cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="2b36b-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="2b36b-109">**nxd_mqtt_client_connect** *Ligue o Cliente MQTT ao corretor*</span><span class="sxs-lookup"><span data-stu-id="2b36b-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="2b36b-110">**nxd_mqtt_client_secure_connect** *Ligue o cliente MQTT ao corretor com segurança TLS*</span><span class="sxs-lookup"><span data-stu-id="2b36b-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="2b36b-111">**nxd_mqtt_client_publish** *publicar uma mensagem através do corretor.*</span><span class="sxs-lookup"><span data-stu-id="2b36b-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="2b36b-112">**nxd_mqtt_client_subscribe** *Subscreva um tópico*</span><span class="sxs-lookup"><span data-stu-id="2b36b-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="2b36b-113">**nxd_mqtt_client_unsubscribe** *Desubscreva-se de um tópico*</span><span class="sxs-lookup"><span data-stu-id="2b36b-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="2b36b-114">**nxd_mqtt_client_receive_notify_set** *Definir mensagem MQTT receber notificar função de retorno*</span><span class="sxs-lookup"><span data-stu-id="2b36b-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="2b36b-115">**nxd_mqtt_client_message_get** *Recuperar uma mensagem do corretor*</span><span class="sxs-lookup"><span data-stu-id="2b36b-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="2b36b-116">nxd_mqtt_client_disconnect_notify_set *Definir desconexão de mensagens MQTT notificam a função de retorno* </span><span class="sxs-lookup"><span data-stu-id="2b36b-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="2b36b-117">**nxd_mqtt_client_disconnect** *Desligue o cliente MQTT do corretor*</span><span class="sxs-lookup"><span data-stu-id="2b36b-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="2b36b-118">**nxd_mqtt_client_delete** *Eliminar a instância do cliente MQTT*</span><span class="sxs-lookup"><span data-stu-id="2b36b-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="2b36b-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="2b36b-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="2b36b-120">Criar caso de cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="2b36b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-122">Description</span></span>

<span data-ttu-id="2b36b-123">Este serviço cria uma instância do Cliente MQTT na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="2b36b-124">A cadeia *client_id* é transmitida para o servidor durante a fase de ligação MQTT como o Identificador de *Cliente (ClientId)*.</span><span class="sxs-lookup"><span data-stu-id="2b36b-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="2b36b-125">Também cria os recursos necessários da ThreadX (linha de tarefa do Cliente MQTT, mutex, grupo de bandeira de evento e tomada TCP).</span><span class="sxs-lookup"><span data-stu-id="2b36b-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-126">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-126">Input Parameters</span></span>

- <span data-ttu-id="2b36b-127">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-128">**client_name** Cadeia de nome de cliente.</span><span class="sxs-lookup"><span data-stu-id="2b36b-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="2b36b-129">**client_id** Cadeia de identificação do cliente utilizada durante a fase de ligação.</span><span class="sxs-lookup"><span data-stu-id="2b36b-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="2b36b-130">O corretor MQTT utiliza este client_id para identificar exclusivamente um cliente.</span><span class="sxs-lookup"><span data-stu-id="2b36b-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="2b36b-131">**client_id_length** Comprimento da cadeia de identificação do cliente, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="2b36b-132">**ip_ptr** Ponteiro para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="2b36b-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="2b36b-133">**pool_ptr** Ponteiro para uma piscina de pacotes que o cliente MQTT usa para o seu funcionamento.</span><span class="sxs-lookup"><span data-stu-id="2b36b-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="2b36b-134">**stack_ptr** Área de pilha para o fio do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="2b36b-135">**stack_size** Tamanho da área da pilha, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="2b36b-136">**mqtt_thread_priority** A prioridade da Linha MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="2b36b-137">**memory_ptr** Precotado.</span><span class="sxs-lookup"><span data-stu-id="2b36b-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="2b36b-138">Já não é usado.</span><span class="sxs-lookup"><span data-stu-id="2b36b-138">Not used anymore.</span></span>
- <span data-ttu-id="2b36b-139">**memory_size** Precotado.</span><span class="sxs-lookup"><span data-stu-id="2b36b-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="2b36b-140">Já não é usado.</span><span class="sxs-lookup"><span data-stu-id="2b36b-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-141">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-141">Return Values</span></span>

- <span data-ttu-id="2b36b-142">**NXD_MQTT_SUCCESS** (0x00) criou com sucesso o cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="2b36b-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-144">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro da piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="2b36b-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Inválido irá tópicos de cadeia, will_retrain_flag ou valor will_QoS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-146">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-146">Allowed From</span></span>

<span data-ttu-id="2b36b-147">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-148">Example</span></span>

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="2b36b-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="2b36b-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="2b36b-150">Define a mensagem 'Testamento'</span><span class="sxs-lookup"><span data-stu-id="2b36b-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-151">Prototype</span></span>

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a><span data-ttu-id="2b36b-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-152">Description</span></span>

<span data-ttu-id="2b36b-153">Este serviço define o tópico de testamento opcional e enviará mensagem antes que o cliente se conecte ao servidor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="2b36b-154">O tópico deve ser a cadeia codificada UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2b36b-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="2b36b-155">A mensagem do testamento, se definida, é transmitida ao corretor como parte da mensagem CONNECT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="2b36b-156">Por isso, a aplicação que deseje utilizar a mensagem deve utilizar este serviço antes da ligação MQTT ser esclareça.</span><span class="sxs-lookup"><span data-stu-id="2b36b-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-157">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-157">Input Parameters</span></span>

- <span data-ttu-id="2b36b-158">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-159">**will_topic** UTF-8 codificado irá tópico cadeia.</span><span class="sxs-lookup"><span data-stu-id="2b36b-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="2b36b-160">O tópico deve estar presente.</span><span class="sxs-lookup"><span data-stu-id="2b36b-160">Will topic must be present.</span></span> <span data-ttu-id="2b36b-161">O chamador deve manter a will_topic corda válida até que a *chamada nx_mqtt_client_connect* seja feita.</span><span class="sxs-lookup"><span data-stu-id="2b36b-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="2b36b-162">**will_topic_length** Número de bytes na cadeia de tópicos de vontade</span><span class="sxs-lookup"><span data-stu-id="2b36b-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="2b36b-163">**will_message** Aplicação definida irá enviar mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="2b36b-164">Se a mensagem de testamento não for necessária, a aplicação pode definir este campo para *NX_NULL.*</span><span class="sxs-lookup"><span data-stu-id="2b36b-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="2b36b-165">**will_message_length** Número de bytes na cadeia de mensagens de testamento.</span><span class="sxs-lookup"><span data-stu-id="2b36b-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="2b36b-166">Se will_message estiver definido para NU, will_message_length deve ser definido para 0.</span><span class="sxs-lookup"><span data-stu-id="2b36b-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="2b36b-167">**will_retain_flag** Se o servidor publica a mensagem do testamento como uma mensagem retida.</span><span class="sxs-lookup"><span data-stu-id="2b36b-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="2b36b-168">Os valores válidos são *NX_TRUE* ou *NX_FALSE.*</span><span class="sxs-lookup"><span data-stu-id="2b36b-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="2b36b-169">**will_QoS** Valor QoS utilizado pelo servidor ao enviar mensagem de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="2b36b-170">Os valores válidos são 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="2b36b-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="2b36b-171">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-171">Return Values</span></span>

- <span data-ttu-id="2b36b-172">**NXD_MQTT_SUCCESS** (0x00) define com sucesso a mensagem de testamento.</span><span class="sxs-lookup"><span data-stu-id="2b36b-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="2b36b-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) as mensagens QoS de nível 2 não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="2b36b-174">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="2b36b-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Inválido irá tópicos de cadeia, will_retrain_flag ou valor will_QoS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-176">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-176">Allowed From</span></span>

<span data-ttu-id="2b36b-177">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-178">Example</span></span>

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="2b36b-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="2b36b-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="2b36b-180">Define o nome de utilizador e a palavra-passe do cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="2b36b-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-182">Description</span></span>

<span data-ttu-id="2b36b-183">Este serviço define o nome de utilizador e a palavra-passe, que é utilizado durante a fase de ligação MQTT para iniciar sessão com efeitos de autenticação.</span><span class="sxs-lookup"><span data-stu-id="2b36b-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="2b36b-184">O login do cliente MQTT com nome de utilizador e senha é opcional.</span><span class="sxs-lookup"><span data-stu-id="2b36b-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="2b36b-185">Nas situações em que o servidor necessita de um nome de utilizador e palavra-passe, o nome de utilizador e a palavra-passe devem ser definidos antes da ligação ser estabelecida.</span><span class="sxs-lookup"><span data-stu-id="2b36b-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-186">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-186">Input Parameters</span></span>

- <span data-ttu-id="2b36b-187">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-188">**nome de utilizador** Cadeia de nome de utilizador codificada UTF-8.</span><span class="sxs-lookup"><span data-stu-id="2b36b-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="2b36b-189">O chamador deve manter o nome de utilizador válido até que a *chamada nx_mqtt_client_connect* seja feita.</span><span class="sxs-lookup"><span data-stu-id="2b36b-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="2b36b-190">**username_length** Número de bytes na cadeia de nome de utilizador</span><span class="sxs-lookup"><span data-stu-id="2b36b-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="2b36b-191">**senha** Corda de senha.</span><span class="sxs-lookup"><span data-stu-id="2b36b-191">**password** Password string.</span></span> <span data-ttu-id="2b36b-192">Se a palavra-passe não for necessária, este campo pode ser definido para NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="2b36b-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-193">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-193">Return Values</span></span>

- <span data-ttu-id="2b36b-194">**NXD_MQTT_SUCCESS** (0x00) define com sucesso a mensagem de testamento.</span><span class="sxs-lookup"><span data-stu-id="2b36b-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="2b36b-195">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="2b36b-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Cadeia de nome de utilizador inválida ou a cadeia de senha.</span><span class="sxs-lookup"><span data-stu-id="2b36b-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-197">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-197">Allowed From</span></span>

<span data-ttu-id="2b36b-198">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-199">Example</span></span>

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="2b36b-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="2b36b-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="2b36b-201">Ligue o Cliente MQTT ao corretor</span><span class="sxs-lookup"><span data-stu-id="2b36b-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="2b36b-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-203">Description</span></span>

<span data-ttu-id="2b36b-204">Este serviço inicia uma ligação com o corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="2b36b-205">Primeiro liga uma tomada TCP e depois faz uma ligação TCP.</span><span class="sxs-lookup"><span data-stu-id="2b36b-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="2b36b-206">Assumindo que é bem sucedido, cria um temporizador se a funcionalidade MQTT manter viva estiver ativada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="2b36b-207">Em seguida, conecta-se com o servidor MQTT (corretor).</span><span class="sxs-lookup"><span data-stu-id="2b36b-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="2b36b-208">Note que este serviço cria uma ligação MQTT sem proteção TLS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="2b36b-209">Para criar uma ligação MQTT segura, o pedido utilizará o ***serviço nxd_mqtt_client_secure_connect().***</span><span class="sxs-lookup"><span data-stu-id="2b36b-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="2b36b-210">Após a ligação, se o cliente definir o *clean_session* para NX_FALSE, o cliente retransmite quaisquer mensagens armazenadas que ainda não tenham sido reconhecidas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-211">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-211">Input Parameters</span></span>

- <span data-ttu-id="2b36b-212">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-213">**server_ip** Endereço IP corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="2b36b-214">**server_port** Número da porta do corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-214">**server_port** Broker port number.</span></span> <span data-ttu-id="2b36b-215">A porta predefinida para MQTT é definida como **_NXD_MQTT_PORT_** (1883).</span><span class="sxs-lookup"><span data-stu-id="2b36b-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="2b36b-216">**keep_alive** O valor "manter vivo", em segundos, deve ser utilizado durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="2b36b-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="2b36b-217">O valor indica o tempo máximo entre duas mensagens de controlo MQTT enviadas ao corretor antes que o corretor o registe este cliente.</span><span class="sxs-lookup"><span data-stu-id="2b36b-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="2b36b-218">O valor 0 desliga a funcionalidade de manter-se viva.</span><span class="sxs-lookup"><span data-stu-id="2b36b-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="2b36b-219">**clean_session** Se o servidor deve iniciar esta sessão limpa.</span><span class="sxs-lookup"><span data-stu-id="2b36b-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="2b36b-220">As opções válidas são **_NX_TRUE_*_ ou _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="2b36b-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="2b36b-221">**wait_option** Tempo de espera de ligação.</span><span class="sxs-lookup"><span data-stu-id="2b36b-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-222">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-222">Return Values</span></span>

- <span data-ttu-id="2b36b-223">**NXD_MQTT_SUCCESS** (0x00) Ligação MQTT bem sucedida</span><span class="sxs-lookup"><span data-stu-id="2b36b-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="2b36b-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) O cliente já está ligado ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="2b36b-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="2b36b-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) não conseguiu ligar-se ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="2b36b-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="2b36b-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Servidor respondeu com erro</span><span class="sxs-lookup"><span data-stu-id="2b36b-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="2b36b-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="2b36b-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="2b36b-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="2b36b-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="2b36b-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="2b36b-235">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="2b36b-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-236">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-236">Allowed From</span></span>

<span data-ttu-id="2b36b-237">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-238">Example</span></span>

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="2b36b-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="2b36b-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="2b36b-240">Ligue o cliente MQTT ao corretor com a segurança TLS</span><span class="sxs-lookup"><span data-stu-id="2b36b-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-241">Prototype</span></span>

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="2b36b-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-242">Description</span></span>

<span data-ttu-id="2b36b-243">Este serviço é idêntico ao ***nxd_mqtt_client_connect*** exceto que a ligação passa pela camada TLS em vez de TCP.</span><span class="sxs-lookup"><span data-stu-id="2b36b-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="2b36b-244">Portanto, a comunicação entre o cliente e o corretor está assegurada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="2b36b-245">O *tls_setup* definido pelo utilizador é uma função de retorno que o cliente MQTT utiliza antes de fazer uma ligação ao cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="2b36b-246">O pedido deve rubricar o NetX Secure TLS, configurar parâmetros de segurança e carregar certificados relevantes para serem utilizados durante o aperto de mão TLS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="2b36b-247">O aperto de mão TLS real ocorre após a criação de uma ligação TCP na porta MQTT TLS do corretor (porta TCP padrão 8883).</span><span class="sxs-lookup"><span data-stu-id="2b36b-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="2b36b-248">Uma vez que o aperto de mão TLS seja bem sucedido, o pacote de controlo MQTT CONNECT é enviado via TLS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="2b36b-249">Para estabelecer ligações seguras, a biblioteca NetX Secure TLS deve estar disponível e o cliente MQTT NetX Duo deve ser construído com ***NX_SECURE_ENABLE*** definido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-250">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-250">Input Parameters</span></span>

- <span data-ttu-id="2b36b-251">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-252">**server_ip** Endereço IP corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="2b36b-253">**server_port** Número da porta do corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-253">**server_port** Broker port number.</span></span> <span data-ttu-id="2b36b-254">A porta predefinida para MQTT é indefinida como **_NXD_MQTT_TLS_PORT_** (8883).</span><span class="sxs-lookup"><span data-stu-id="2b36b-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="2b36b-255">**tls_setup** Função de retorno de configuração TLS fornecida pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="2b36b-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="2b36b-256">Esta função de retorno é invocada para configurar parâmetros de ligação ao cliente TLS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="2b36b-257">**keep_alive** O valor de manter vivo a ser usado durante a sessão.</span><span class="sxs-lookup"><span data-stu-id="2b36b-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="2b36b-258">O valor 0 desliga a funcionalidade de manter-se viva.</span><span class="sxs-lookup"><span data-stu-id="2b36b-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="2b36b-259">**clean_session** Se o servidor deve ou não iniciar esta sessão limpa.</span><span class="sxs-lookup"><span data-stu-id="2b36b-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="2b36b-260">As opções válidas são **_NX_TRUE_*_ ou _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="2b36b-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="2b36b-261">**wait_option** Tempo de espera de ligação.</span><span class="sxs-lookup"><span data-stu-id="2b36b-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-262">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-262">Return Values</span></span>

- <span data-ttu-id="2b36b-263">**NXD_MQTT_SUCCESS** (0x00) Conexão de cliente MQTT bem sucedida estabelecida via TLS.</span><span class="sxs-lookup"><span data-stu-id="2b36b-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="2b36b-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) O cliente já está ligado ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="2b36b-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="2b36b-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) não conseguiu ligar-se ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="2b36b-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="2b36b-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) O servidor respondeu com mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="2b36b-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="2b36b-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="2b36b-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="2b36b-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="2b36b-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="2b36b-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Código de resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b36b-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="2b36b-275">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido ou estrutura de endereço de corte.</span><span class="sxs-lookup"><span data-stu-id="2b36b-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="2b36b-276">NX_INVALID_PORT (0x46) A porta do servidor não pode ser 0.</span><span class="sxs-lookup"><span data-stu-id="2b36b-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="2b36b-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Erro do parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="2b36b-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread ainda não começou a funcionar.</span><span class="sxs-lookup"><span data-stu-id="2b36b-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-279">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-279">Allowed From</span></span>

<span data-ttu-id="2b36b-280">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-281">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-281">Example</span></span>

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="2b36b-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="2b36b-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="2b36b-283">Publique uma mensagem através do corretor</span><span class="sxs-lookup"><span data-stu-id="2b36b-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-284">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="2b36b-285">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-285">Description</span></span>

<span data-ttu-id="2b36b-286">Este serviço publica uma mensagem através do corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="2b36b-287">A publicação de mensagens QoS de nível 2 ainda não é suportada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-288">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-288">Input Parameters</span></span>

- <span data-ttu-id="2b36b-289">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-290">**topic_name** Tópico para publicar.</span><span class="sxs-lookup"><span data-stu-id="2b36b-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="2b36b-291">**topic_name_length** Comprimento do tópico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="2b36b-292">**mensagem** Ponteiro para o tampão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="2b36b-293">**message_length** Tamanho da mensagem, em bytes</span><span class="sxs-lookup"><span data-stu-id="2b36b-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="2b36b-294">**reter** Determina se o corretor deve reter a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="2b36b-295">**QoS** O valor QoS desejado: 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="2b36b-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="2b36b-296">**tempo limite** Valor de tempo limite</span><span class="sxs-lookup"><span data-stu-id="2b36b-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-297">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-297">Return Values</span></span>

- <span data-ttu-id="2b36b-298">**NXD_MQTT_SUCCESS** (0x00) Cliente MQTT bem sucedido criar</span><span class="sxs-lookup"><span data-stu-id="2b36b-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="2b36b-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno.</span><span class="sxs-lookup"><span data-stu-id="2b36b-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="2b36b-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Não conseguiu obter o pacote da piscina de pacotes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="2b36b-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) não comunicaram com o corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="2b36b-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) as mensagens QoS de nível 2 não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="2b36b-303">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="2b36b-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="2b36b-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Erro do parâmetro de entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-305">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-305">Allowed From</span></span>

<span data-ttu-id="2b36b-306">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-307">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-307">Example</span></span>

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="2b36b-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="2b36b-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="2b36b-309">Subscrever um tópico</span><span class="sxs-lookup"><span data-stu-id="2b36b-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-310">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="2b36b-311">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-311">Description</span></span>

<span data-ttu-id="2b36b-312">Este serviço subscreve um tópico específico.</span><span class="sxs-lookup"><span data-stu-id="2b36b-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="2b36b-313">A subscrição de mensagens QoS de nível 2 ainda não está suportada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-314">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-314">Input Parameters</span></span>

- <span data-ttu-id="2b36b-315">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-316">**topic_name** Tópico para publicar.</span><span class="sxs-lookup"><span data-stu-id="2b36b-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="2b36b-317">**topic_name_length** Comprimento do tópico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="2b36b-318">**QoS O nível QoS desejado:** 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="2b36b-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-319">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-319">Return Values</span></span>

- <span data-ttu-id="2b36b-320">**NXD_MQTT_SUCCESS** (0x00) subscreveu com sucesso o tema.</span><span class="sxs-lookup"><span data-stu-id="2b36b-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="2b36b-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) O cliente não está ligado ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="2b36b-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="2b36b-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="2b36b-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS nível 2messages não são suportados.</span><span class="sxs-lookup"><span data-stu-id="2b36b-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="2b36b-326">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="2b36b-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="2b36b-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name não está definido, ou topic_name_length é zero, ou QoS é valor é inválido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-328">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-328">Allowed From</span></span>

<span data-ttu-id="2b36b-329">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-330">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="2b36b-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="2b36b-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="2b36b-332">Cancelar a subscrição de um tópico</span><span class="sxs-lookup"><span data-stu-id="2b36b-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="2b36b-334">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-334">Description</span></span>

<span data-ttu-id="2b36b-335">Este serviço não se subscreve de um tópico.</span><span class="sxs-lookup"><span data-stu-id="2b36b-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-336">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-336">Input Parameters</span></span>

- <span data-ttu-id="2b36b-337">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-338">**topic_name** Tópico para cancelar a subscrição de.</span><span class="sxs-lookup"><span data-stu-id="2b36b-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="2b36b-339">**topic_name_length** Comprimento do tópico, em bytes.</span><span class="sxs-lookup"><span data-stu-id="2b36b-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-340">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-340">Return Values</span></span>

- <span data-ttu-id="2b36b-341">**NXD_MQTT_SUCCESS** (0x00) Com sucesso não subscrito do tópico.</span><span class="sxs-lookup"><span data-stu-id="2b36b-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="2b36b-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) O cliente não está ligado ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="2b36b-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="2b36b-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Incapaz de enviar mensagens ao corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="2b36b-346">NX_PTR_ERROR (0x07) Ponteiro do bloco de controlo MQTT inválido</span><span class="sxs-lookup"><span data-stu-id="2b36b-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="2b36b-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name não está definido, ou topic_name_length é zero.</span><span class="sxs-lookup"><span data-stu-id="2b36b-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-348">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-348">Allowed From</span></span>

<span data-ttu-id="2b36b-349">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-350">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="2b36b-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="2b36b-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="2b36b-352">Definir mensagem MQTT receber notificar função de retorno</span><span class="sxs-lookup"><span data-stu-id="2b36b-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-353">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="2b36b-354">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-354">Description</span></span>

<span data-ttu-id="2b36b-355">Este serviço regista uma função de retorno com o cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="2b36b-356">Ao receber uma mensagem publicada pelo corretor, o cliente MQTT armazena a mensagem na fila de receção.</span><span class="sxs-lookup"><span data-stu-id="2b36b-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="2b36b-357">Se a função de retorno estiver definida, a função de retorno é invocada para notificar a aplicação de que uma mensagem está pronta para ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="2b36b-358">A função de notificação de receção leva um ponteiro para o bloco de controlo do cliente MQTT, e uma *message_count* indicando o número de mensagens disponíveis na fila de receção.</span><span class="sxs-lookup"><span data-stu-id="2b36b-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="2b36b-359">Note que o número pode alterar-se entre a notificação recebida e quando a aplicação recupera estas mensagens, uma vez que novas mensagens podem ter chegado no intervalo.</span><span class="sxs-lookup"><span data-stu-id="2b36b-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-360">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-360">Input Parameters</span></span>

- <span data-ttu-id="2b36b-361">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-362">**receive_notify** A função de retorno fornecida pelo utilizador deve ser invocada ao receber uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-363">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-363">Return Values</span></span>

- <span data-ttu-id="2b36b-364">**NXD_MQTT_SUCCESS** (0x00) definir com sucesso a função de notificação de receção.</span><span class="sxs-lookup"><span data-stu-id="2b36b-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="2b36b-365">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-366">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-366">Allowed From</span></span>

<span data-ttu-id="2b36b-367">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-368">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-368">Example</span></span>

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="2b36b-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="2b36b-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="2b36b-370">Recupere uma mensagem do corretor</span><span class="sxs-lookup"><span data-stu-id="2b36b-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-371">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="2b36b-372">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-372">Description</span></span>

<span data-ttu-id="2b36b-373">Este serviço recupera uma mensagem publicada pelo corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="2b36b-374">Todas as mensagens recebidas são armazenadas na fila de receção.</span><span class="sxs-lookup"><span data-stu-id="2b36b-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="2b36b-375">A aplicação utiliza este serviço para recuperar estas mensagens.</span><span class="sxs-lookup"><span data-stu-id="2b36b-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="2b36b-376">Esta chamada não está a bloquear.</span><span class="sxs-lookup"><span data-stu-id="2b36b-376">This call is non-blocking.</span></span> <span data-ttu-id="2b36b-377">Se a fila de receção estiver vazia, este serviço retorna \***NXD_MQTT_NO_MESSAGE** _.</span><span class="sxs-lookup"><span data-stu-id="2b36b-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="2b36b-378">Uma aplicação que deseje ser notificada da mensagem recebida pode ligar para o serviço _ *_nxd_mqtt_client_receive_notify_set_*\* para registar uma função de retorno de receção.</span><span class="sxs-lookup"><span data-stu-id="2b36b-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="2b36b-379">O chamador precisa fornecer espaço de memória para a cadeia de tópicos e o corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="2b36b-380">Os tamanhos destes dois tampão são passados usando *topic_buffer_size* e *message_buffer_size*.</span><span class="sxs-lookup"><span data-stu-id="2b36b-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="2b36b-381">O número real de bytes na cadeia de tópicos e o corpo da mensagem são devolvidos em *atual_topic_length* e *atual_message_length*.</span><span class="sxs-lookup"><span data-stu-id="2b36b-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="2b36b-382">Se o comprimento do tópico ou o comprimento da massagem for maior do que o espaço do tampão fornecido, este serviço devolve o código de erro *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span><span class="sxs-lookup"><span data-stu-id="2b36b-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="2b36b-383">O pedido atribuirá um amortecedor maior e tentará novamente.</span><span class="sxs-lookup"><span data-stu-id="2b36b-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-384">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-384">Input Parameters</span></span>

- <span data-ttu-id="2b36b-385">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-386">**topic_buffer** Ponteiro para o local da memória onde a cadeia de tópicos é copiada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="2b36b-387">**topic_buffer_size** Tamanho do tampão tópico.</span><span class="sxs-lookup"><span data-stu-id="2b36b-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="2b36b-388">**atual_topic_length** Ponteiro para o local da memória onde o comprimento do tópico real é devolvido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="2b36b-389">**message_buffer** Ponteiro para o local da memória onde a cadeia de mensagens é copiada.</span><span class="sxs-lookup"><span data-stu-id="2b36b-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="2b36b-390">**message_buffer_size** Tamanho do tampão de mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="2b36b-391">**atual_message_length** Ponteiro para o local da memória onde o comprimento da mensagem é devolvido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-392">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-392">Return Values</span></span>

- <span data-ttu-id="2b36b-393">**NXD_MQTT_SUCCESS** (0x00) mensagem recuperada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="2b36b-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="2b36b-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Erro lógico interno</span><span class="sxs-lookup"><span data-stu-id="2b36b-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="2b36b-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) A fila de receção está vazia.</span><span class="sxs-lookup"><span data-stu-id="2b36b-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="2b36b-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Tampão de tópico ou tampão de mensagem é demasiado pequeno para o tópico ou para a mensagem.</span><span class="sxs-lookup"><span data-stu-id="2b36b-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="2b36b-397">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido, ip_ptr ou ponteiro de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="2b36b-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="2b36b-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer ou ponteiro topic_buffer é NULO</span><span class="sxs-lookup"><span data-stu-id="2b36b-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-399">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-399">Allowed From</span></span>

<span data-ttu-id="2b36b-400">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-401">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-401">Example</span></span>

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="2b36b-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="2b36b-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="2b36b-403">Definir desconexão de mensagens MQTT notificar função de retorno</span><span class="sxs-lookup"><span data-stu-id="2b36b-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="2b36b-405">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-405">Description</span></span>

<span data-ttu-id="2b36b-406">Este serviço regista uma função de retorno com o cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="2b36b-407">Quando o MQTT deteta a ligação ao corretor, chama esta função de notificação para alertar a aplicação.</span><span class="sxs-lookup"><span data-stu-id="2b36b-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="2b36b-408">Portanto, a aplicação pode usar esta função de retorno para detetar uma ligação perdida, e para ser capaz de restabelecer a ligação com o corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="2b36b-409">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-409">Input Parameters</span></span>

- <span data-ttu-id="2b36b-410">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="2b36b-411">**disconnect_notify** A função de retorno fornecida pelo utilizador deve ser invocada quando a MQTT detetar a ligação ao corretor se perder.</span><span class="sxs-lookup"><span data-stu-id="2b36b-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-412">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-412">Return Values</span></span>

- <span data-ttu-id="2b36b-413">**NXD_MQTT_SUCCESS** (0x00) definir com sucesso a função de notificação de desconexão.</span><span class="sxs-lookup"><span data-stu-id="2b36b-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="2b36b-414">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido.</span><span class="sxs-lookup"><span data-stu-id="2b36b-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-415">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-415">Allowed From</span></span>

<span data-ttu-id="2b36b-416">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-417">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="2b36b-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="2b36b-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="2b36b-419">Desconecte o cliente MQTT do corretor</span><span class="sxs-lookup"><span data-stu-id="2b36b-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-420">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2b36b-421">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-421">Description</span></span>

<span data-ttu-id="2b36b-422">Este serviço desliga o cliente do corretor.</span><span class="sxs-lookup"><span data-stu-id="2b36b-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="2b36b-423">Note que as mensagens na fila de receção são libertadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="2b36b-424">As mensagens com QoS 1 na fila de transmissão não são divulgadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="2b36b-425">Após a reconectação do cliente ao servidor, as mensagens QoS 1 podem ser processadas, a menos que o cliente se conecte ao servidor com *clean_session* bandeira definida para ***NX_TRUE***.</span><span class="sxs-lookup"><span data-stu-id="2b36b-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="2b36b-426">Se a ligação tiver sido feita com proteção de segurança TLS, este serviço fechará a sessão TLS antes de desligar a ligação TCP.</span><span class="sxs-lookup"><span data-stu-id="2b36b-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="2b36b-427">A chamada de desconexão da tomada TCP tem uma opção de espera definida por NXD_MQTT_SOCKET_TIMEOUT (carraças do temporizador).</span><span class="sxs-lookup"><span data-stu-id="2b36b-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="2b36b-428">O valor predefinido é NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="2b36b-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="2b36b-429">Para evitar uma suspensão indefinida no caso de a ligação de rede se perder ou o servidor não responder, defina esta opção para um valor finito.</span><span class="sxs-lookup"><span data-stu-id="2b36b-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-430">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-430">Input Parameters</span></span>

- <span data-ttu-id="2b36b-431">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-432">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-432">Return Values</span></span>

- <span data-ttu-id="2b36b-433">**NXD_MQTT_SUCCESS** (0x00) desligado com sucesso do corretor</span><span class="sxs-lookup"><span data-stu-id="2b36b-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="2b36b-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Não conseguiu obter o mutex MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="2b36b-435">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido</span><span class="sxs-lookup"><span data-stu-id="2b36b-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-436">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-436">Allowed From</span></span>

<span data-ttu-id="2b36b-437">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-438">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="2b36b-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="2b36b-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="2b36b-440">Eliminar a instância do cliente MQTT</span><span class="sxs-lookup"><span data-stu-id="2b36b-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b36b-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b36b-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="2b36b-442">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b36b-442">Description</span></span>

<span data-ttu-id="2b36b-443">Este serviço elimina a instância do cliente MQTT e liberta recursos internos.</span><span class="sxs-lookup"><span data-stu-id="2b36b-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="2b36b-444">Este serviço desliga automaticamente o cliente do corretor se ainda estiver ligado.</span><span class="sxs-lookup"><span data-stu-id="2b36b-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="2b36b-445">As mensagens ainda não transmitidas ou não foram reconhecidas são libertadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="2b36b-446">As mensagens recebidas mas não recuperadas pela aplicação também são divulgadas.</span><span class="sxs-lookup"><span data-stu-id="2b36b-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="2b36b-447">Se a ligação foi feita com proteção de segurança TLS, este serviço fecha a sessão TLS antes de desligar a ligação TCP.</span><span class="sxs-lookup"><span data-stu-id="2b36b-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="2b36b-448">Após a execlarção do cliente, uma aplicação que deseje utilizar o serviço MQTT precisa de criar uma nova instância.</span><span class="sxs-lookup"><span data-stu-id="2b36b-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b36b-449">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b36b-449">Input Parameters</span></span>

- <span data-ttu-id="2b36b-450">**client_ptr** Ponteiro para o bloco de controlo do cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b36b-451">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b36b-451">Return Values</span></span>

- <span data-ttu-id="2b36b-452">**NXD_MQTT_SUCCESS** (0x00) eliminou com sucesso o cliente MQTT.</span><span class="sxs-lookup"><span data-stu-id="2b36b-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="2b36b-453">NX_PTR_ERROR (0x07) Bloco de controlo MQTT inválido</span><span class="sxs-lookup"><span data-stu-id="2b36b-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b36b-454">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b36b-454">Allowed From</span></span>

<span data-ttu-id="2b36b-455">Fios</span><span class="sxs-lookup"><span data-stu-id="2b36b-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b36b-456">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b36b-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
