---
title: Capítulo 3 - Descrição funcional do Azure RTOS NetX LWM2M
description: Este capítulo contém uma descrição funcional de Azure RTOS NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826678"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="bd97e-103">Capítulo 3 - Descrição funcional do Azure RTOS NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="bd97e-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="bd97e-104">Este capítulo contém uma descrição funcional de Azure RTOS NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="bd97e-105">Inicialização do cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="bd97e-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="bd97e-106">O Cliente LWM2M é inicializado ***ligando*** nx_lwm2m_client_create serviço.</span><span class="sxs-lookup"><span data-stu-id="bd97e-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="bd97e-107">O Cliente LWM2M funciona no seu próprio fio e pode reportar alguns eventos à aplicação através da utilização de callbacks, ou através de métodos de chamada dos objetos personalizados implementados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="bd97e-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="bd97e-108">Além disso, as Sessões de Cliente LWM2M devem ser criadas chamando ***nx_lwm2m_client_session_create*** para permitir a comunicação com um ou mais servidores.</span><span class="sxs-lookup"><span data-stu-id="bd97e-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="bd97e-109">Uma sessão pode comunicar com dois tipos diferentes de servidores: um Servidor Bootstrap ou um Servidor LWM2M (Gestão de Dispositivos).</span><span class="sxs-lookup"><span data-stu-id="bd97e-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="bd97e-110">Sessão de servidor de botas</span><span class="sxs-lookup"><span data-stu-id="bd97e-110">Bootstrap Server Session</span></span>

<span data-ttu-id="bd97e-111">Uma sessão de comunicação com um Servidor Bootstrap é usada para fornecer informações essenciais no Cliente LWM2M para permitir ao Cliente LWM2M realizar a operação "Register" com um ou mais Servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="bd97e-112">Este tipo de servidor é utilizado durante os modos de bootstrap iniciado pelo cliente e iniciado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="bd97e-113">A aplicação pode iniciar uma sessão de Bootstrap ligando ***nx_lwm2m_client_session_bootstrap** _ ou _*_nx_lwm2m_client_session_bootstrap_dtls,_\*_ deve fornecer o endereço IP e o número de porta do servidor, e um ID opcional de instância de objeto de segurança.</span><span class="sxs-lookup"><span data-stu-id="bd97e-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="bd97e-114">A função _*_nx_lwm2m_client_session_bootstrap_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* estabelece uma ligação DTLS segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="bd97e-115">Se a operação Bootstrap for bem sucedida, o servidor Bootstrap deveria ter criado instâncias de objetos de segurança para os servidores Bootstrap e LWM2M e instâncias de objetos de servidor para os servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="bd97e-116">A aplicação deve utilizar estas informações para estabelecer uma sessão com o(s) Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="bd97e-117">Os dados bootstrap devem ser guardados para memória não volátil através da aplicação, a fim de configurar o Cliente LWM2M no próximo reinício do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="bd97e-118">Sessão de servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="bd97e-118">LWM2M Server Session</span></span>

<span data-ttu-id="bd97e-119">Uma sessão de comunicação com um Servidor LWM2M é utilizada para registo, gestão de dispositivos e ativação de serviços.</span><span class="sxs-lookup"><span data-stu-id="bd97e-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="bd97e-120">A aplicação pode registar o Cliente LWM2M num servidor chamando ***nx_lwm2m_client_session_register** _ ou _*_nx_lwm2m_client_session_register_dtls,_\*_ deve fornecer o endereço IP e o número de porta do servidor, e o ID do servidor curto que corresponde a uma Instância de Objeto de Servidor existente.</span><span class="sxs-lookup"><span data-stu-id="bd97e-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="bd97e-121">A função _*_nx_lwm2m_client_session_register_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_register_dtls_*\* estabelece uma ligação DTLS segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="bd97e-122">A aplicação pode desinscrevê-lo através do registo do Cliente LWM2M ligando para ***nx_lwm2m_client_session_deregister** _, e pedir ao cliente para enviar uma mensagem de 'Update' ligando para _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="bd97e-123">Chamada do Estado da Sessão</span><span class="sxs-lookup"><span data-stu-id="bd97e-123">Session State Callback</span></span>

<span data-ttu-id="bd97e-124">A aplicação regista uma chamada de retorno na criação de uma sessão que é chamada quando o estado da sessão é atualizado, a função de retorno NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK tem o seguinte protótipo:</span><span class="sxs-lookup"><span data-stu-id="bd97e-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="bd97e-125">São definidos os seguintes estados:</span><span class="sxs-lookup"><span data-stu-id="bd97e-125">The following states are defined :</span></span>

- <span data-ttu-id="bd97e-126">**NX_LWM2M_CLIENT_SESSION_INIT**: O estado inicial após a criação da sessão.</span><span class="sxs-lookup"><span data-stu-id="bd97e-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="bd97e-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: O cliente aguarda a expiração do temporizador 'Hold Off' ou da Bootstrap iniciado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="bd97e-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: O cliente enviou uma mensagem de 'Pedido' para o Servidor Bootstrap (Bota Iniciada pelo Cliente).</span><span class="sxs-lookup"><span data-stu-id="bd97e-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="bd97e-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: O cliente está a receber dados do Servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="bd97e-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="bd97e-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: O Servidor Bootstrap enviou uma mensagem 'Acabada'.</span><span class="sxs-lookup"><span data-stu-id="bd97e-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="bd97e-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: A sessão de botas falhou.</span><span class="sxs-lookup"><span data-stu-id="bd97e-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="bd97e-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: O cliente enviou uma mensagem de 'Registo' para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="bd97e-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: O cliente está registado no servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="bd97e-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: O cliente enviou uma mensagem de 'Actualização' para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="bd97e-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: O cliente enviou uma mensagem de 'Des-registo' para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="bd97e-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: O cliente está dessesc recenseado a partir do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="bd97e-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: O Servidor LWM2M está desativado.</span><span class="sxs-lookup"><span data-stu-id="bd97e-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="bd97e-138">Um 'Registo' será enviado após o termo do temporizador para desativação.</span><span class="sxs-lookup"><span data-stu-id="bd97e-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="bd97e-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: A operação de registo ou atualização do Servidor LWM2M falhou.</span><span class="sxs-lookup"><span data-stu-id="bd97e-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="bd97e-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: A instância do objeto do servidor correspondente ao Servidor LWM2M foi eliminada.</span><span class="sxs-lookup"><span data-stu-id="bd97e-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="bd97e-141">Em caso de erro, a aplicação pode recuperar a causa do erro chamando **_nx_lwm2m_client_session_error_get_**.</span><span class="sxs-lookup"><span data-stu-id="bd97e-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="bd97e-142">Gestão local de dispositivos</span><span class="sxs-lookup"><span data-stu-id="bd97e-142">Local Device Management</span></span>

<span data-ttu-id="bd97e-143">A aplicação pode aceder aos Objetos do Cliente LWM2M utilizando as funções de gestão de dispositivos locais.</span><span class="sxs-lookup"><span data-stu-id="bd97e-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="bd97e-144">São fornecidas as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="bd97e-144">The following functions are provided:</span></span>

- <span data-ttu-id="bd97e-145">***nx_lwm2m_client_object_read***: Leia os recursos de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="bd97e-146">***nx_lwm2m_client_object_discover***: Obtenha a lista dos recursos de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="bd97e-147">***nx_lwm2m_client_object_write***: Escreva recursos para uma instância de objeto</span><span class="sxs-lookup"><span data-stu-id="bd97e-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="bd97e-148">***nx_lwm2m_client_object_execute***: Efetuar a operação Executar num recurso de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="bd97e-149">***nx_lwm2m_client_object_create:*** Criar uma nova instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="bd97e-150">***nx_lwm2m_client_object_delete***: Eliminar uma instância de objeto existente.</span><span class="sxs-lookup"><span data-stu-id="bd97e-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="bd97e-151">***nx_lwm2m_client_object_get_next***: Implemente o próximo ID do Objeto pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="bd97e-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="bd97e-152">***nx_lwm2m_client_object_instance_get_next:*** Obtenha a próxima instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="bd97e-153">Informação sobre Recursos</span><span class="sxs-lookup"><span data-stu-id="bd97e-153">Resource Information</span></span>

<span data-ttu-id="bd97e-154">Ao ler e escrever para Objetos, um recurso é representado pela estrutura NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="bd97e-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="bd97e-155">Esta estrutura contém o ID do Recurso/Instância e o seu valor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="bd97e-156">A codificação do valor depende do seu tipo e da sua origem (aplicação ou rede).</span><span class="sxs-lookup"><span data-stu-id="bd97e-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="bd97e-157">A estrutura NX_LWM2M_RESOURCE tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="bd97e-158">**nx_lwm2m_resource_id**: O ID do Recurso ou da Instância.</span><span class="sxs-lookup"><span data-stu-id="bd97e-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="bd97e-159">**nx_lwm2m_resource_type**: O tipo de valor, ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="bd97e-160">**nx_lwm2m_resource_value**: O valor do Recurso depende do tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="bd97e-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="bd97e-161">São definidos os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bd97e-161">The following type of values are defined :</span></span>

- <span data-ttu-id="bd97e-162">**NX_LWM2M_RESOURCE_NONE:** Recursos vazios.</span><span class="sxs-lookup"><span data-stu-id="bd97e-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="bd97e-163">**NX_LWM2M_RESOURCE_STRING**: Um valor de cadeia UTF-8 sem fim armazenado em *nx_lwm2m_resource_stringdata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="bd97e-164">**NX_LWM2M_RESOURCE_INTEGER32**: Um valor inteiro de 32 bits armazenado em *nx_lwm2m_resource_integer32data*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="bd97e-165">**NX_LWM2M_RESOURCE_INTEGER64**: Um valor inteiro de 64 bits armazenado em *nx_lwm2m_resource_integer64data*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="bd97e-166">**NX_LWM2M_RESOURCE_FLOAT32**: Um valor flutuante de 32 bits armazenado em *nx_lwm2m_resource_float32data*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="bd97e-167">**NX_LWM2M_RESOURCE_FLOAT64**: Um valor flutuante de 64 bits armazenado em *nx_lwm2m_resource_float64data*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="bd97e-168">**NX_LWM2M_RESOURCE_BOOLEAN**: Um valor booleano armazenado em *nx_lwm2m_resource_booleandata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="bd97e-169">**NX_LWM2M_RESOURCE_OPAQUE**: Um valor opaco definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="bd97e-170">**NX_LWM2M_RESOURCE_OBJLNK**: Valor de ligação de objetos armazenado em *nx_lwm2m_resource_objlnkdata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="bd97e-171">**NX_LWM2M_RESOURCE_TLV**: Um valor codificado por TLV definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="bd97e-172">**NX_LWM2M_RESOURCE_TEXT**: Um valor codificado Plain-Text definido por *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="bd97e-173">**NX_LWM2M_RESOURCE_MULTIPLE**: Um recurso múltiplo definido por *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="bd97e-174">*nx_lwm2m_resource_multiple_ptr* é um ponteiro para uma série de **estruturas NX_LWM2M_RESOURCE** que contêm informações sobre cada Instância de Recursos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="bd97e-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: Um recurso múltiplo definido por *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="bd97e-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="bd97e-176">*nx_lwm2m_resource_multiple_ptr* é um ponteiro para um tampão codificado TLV.</span><span class="sxs-lookup"><span data-stu-id="bd97e-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="bd97e-177">As funções de conveniência são fornecidas para recuperar o valor e verificar o seu tipo, a aplicação nunca deve aceder diretamente ao campo *nx_lwm2m_resource_value* quando obter um valor de uma estrutura NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="bd97e-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="bd97e-178">São definidas as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="bd97e-178">The following functions are defined :</span></span>

- <span data-ttu-id="bd97e-179">***nx_lwm2m_resource_get_***: Obtenha um valor com o tipo dado.</span><span class="sxs-lookup"><span data-stu-id="bd97e-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="bd97e-180">***nx_lwm2m_resource_multiple_get_***: Obtenha um valor com o tipo dado a partir de um Recurso Múltiplo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="bd97e-181">O **NX_LWM2M_RESOURCE_IS_MULTIPLE** macro (tipo) pode ser utilizado para verificar se um tipo de recurso é um Recurso Múltiplo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="bd97e-182">Implementação de objetos</span><span class="sxs-lookup"><span data-stu-id="bd97e-182">Object Implementation</span></span>

<span data-ttu-id="bd97e-183">O Cliente LWM2M implementa os objetos obrigatórios OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3).</span><span class="sxs-lookup"><span data-stu-id="bd97e-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="bd97e-184">Outros objetos específicos do dispositivo devem ser implementados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="bd97e-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="bd97e-185">Duas estruturas de dados são usadas para definir um Objeto: a estrutura NX_LWM2M_OBJECT define a implementação do Objeto, incluindo o ID do Objeto e os métodos do objeto, e a estrutura NX_LWM2M_OBJECT_INSTANCE contém os dados de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="bd97e-186">A estrutura NX_LWM2M_OBJECT tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="bd97e-187">**nx_lwm2m_object_next:** O próximo objeto da lista.</span><span class="sxs-lookup"><span data-stu-id="bd97e-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="bd97e-188">**nx_lwm2m_object_id:** O ID do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="bd97e-189">**nx_lwm2m_object_read**: O método 'Ler', ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="bd97e-190">**nx_lwm2m_object_discover**: O método 'Descobrir', veja abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="bd97e-191">**nx_lwm2m_object_write**: O método 'Escrever', ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="bd97e-192">**nx_lwm2m_object_execute**: O método 'Executar', ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="bd97e-193">**nx_lwm2m_object_create**: O método 'Criar', ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="bd97e-194">**nx_lwm2m_object_delete**: O método 'Eliminar', ver abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="bd97e-195">**nx_lwm2m_object_instances**: A lista de casos de objetos terminados por NULOS.</span><span class="sxs-lookup"><span data-stu-id="bd97e-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="bd97e-196">A estrutura NX_LWM2M_OBJECT_INSTANCE tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="bd97e-197">**nx_lwm2m_object_instance_next:** A próxima instância da lista.</span><span class="sxs-lookup"><span data-stu-id="bd97e-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="bd97e-198">**nx_lwm2m_object_instance_id:** O ID da Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="bd97e-199">O Objeto deve implementar os métodos correspondentes às operações definidas pela Interface de Gestão de Dispositivos LWM2M: 'Ler', 'Descobrir', 'Escrever', 'Executar', 'Criar' e 'Eliminar'.</span><span class="sxs-lookup"><span data-stu-id="bd97e-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="bd97e-200">Os métodos 'Criar' e 'Eliminar' podem ser definidos para NU SE o objeto não suportar a criação dinâmica de instâncias.</span><span class="sxs-lookup"><span data-stu-id="bd97e-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="bd97e-201">O método 'Ler'</span><span class="sxs-lookup"><span data-stu-id="bd97e-201">The 'Read' Method</span></span>

<span data-ttu-id="bd97e-202">O método 'Ler' é utilizado para ler valores de recursos a partir de uma Instância de Objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="bd97e-203">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-204">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="bd97e-205">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="bd97e-206">**num_values:** O número de recursos a ler.</span><span class="sxs-lookup"><span data-stu-id="bd97e-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="bd97e-207">**values_ptr**: Ponteiro para uma série de NX_LWM2M_RESOURCE contendo os IDs dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="bd97e-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="bd97e-208">Na volta, a matriz é preenchida com os tipos e valores correspondentes.</span><span class="sxs-lookup"><span data-stu-id="bd97e-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="bd97e-209">O método 'Descobrir'</span><span class="sxs-lookup"><span data-stu-id="bd97e-209">The 'Discover' Method</span></span>

<span data-ttu-id="bd97e-210">O método 'Descobrir' é utilizado para recuperar a lista de todos os Recursos implementados por um Objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="bd97e-211">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-212">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="bd97e-213">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="bd97e-214">**num_resources_ptr**: No tamanho do tampão de destino, na saída o número de elementos escritos para o tampão.</span><span class="sxs-lookup"><span data-stu-id="bd97e-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="bd97e-215">**resources_ptr**: Ponteiro para o tampão de destino.</span><span class="sxs-lookup"><span data-stu-id="bd97e-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="bd97e-216">A informação de recursos é devolvida numa estrutura NX_LWM2M_RESOURCE_INFO definida da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="bd97e-217">**nx_lwm2m_resource_info_id:** A identificação do recurso.</span><span class="sxs-lookup"><span data-stu-id="bd97e-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="bd97e-218">**nx_lwm2m_resource_info_flags**: Veja abaixo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="bd97e-219">**nx_lwm2m_resource_info_dim**: A dimensão do Recurso Múltiplo se a bandeira NX_LWM2M_RESOURCE_INFO_MULTIPLE estiver definida.</span><span class="sxs-lookup"><span data-stu-id="bd97e-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="bd97e-220">O campo *nx_lwm2m_resource_flags* pode ter aos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bd97e-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="bd97e-221">0: Único recurso legível.</span><span class="sxs-lookup"><span data-stu-id="bd97e-221">0: Single readable resource.</span></span>

- <span data-ttu-id="bd97e-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE:** O recurso múltiplo, *nx_lwm2m_resource_info_dim* deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="bd97e-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="bd97e-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE:** Recurso executável ou não legível.</span><span class="sxs-lookup"><span data-stu-id="bd97e-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="bd97e-224">O método 'Escrever'</span><span class="sxs-lookup"><span data-stu-id="bd97e-224">The 'Write' Method</span></span>

<span data-ttu-id="bd97e-225">O método 'Escrever' é utilizado para atualizar ou substituir recursos de uma Instância de Objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="bd97e-226">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-227">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="bd97e-228">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="bd97e-229">**num_values:** O número de recursos para escrever.</span><span class="sxs-lookup"><span data-stu-id="bd97e-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="bd97e-230">**values_ptr**: Pontear os valores dos recursos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="bd97e-231">**write_op:** O tipo de operações de escrita.</span><span class="sxs-lookup"><span data-stu-id="bd97e-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="bd97e-232">As seguintes operações de escrita podem ser especificadas para o parâmetro *write_op:*</span><span class="sxs-lookup"><span data-stu-id="bd97e-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="bd97e-233">0 &mdash; Atualização Parcial: adição ou atualizações Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados,</span><span class="sxs-lookup"><span data-stu-id="bd97e-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="bd97e-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Instância de substituição: substitui a Instância do Objeto pelos novos valores de recursos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="bd97e-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Substituir Recurso: substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).</span><span class="sxs-lookup"><span data-stu-id="bd97e-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="bd97e-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: inicializa a instância de objeto recém-criada com os valores de recursos fornecidos (chamados do método *nx_lwm2m_object_create).*</span><span class="sxs-lookup"><span data-stu-id="bd97e-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="bd97e-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: chamado durante a sequência de Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="bd97e-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="bd97e-238">O método 'Executar'</span><span class="sxs-lookup"><span data-stu-id="bd97e-238">The 'Execute' Method</span></span>

<span data-ttu-id="bd97e-239">O método 'Executar' implementa a execução de um recurso de objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="bd97e-240">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-241">**object_ptr**: Ponteiro para a implementação do objeto</span><span class="sxs-lookup"><span data-stu-id="bd97e-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="bd97e-242">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="bd97e-243">**resource_id:** O ID do recurso.</span><span class="sxs-lookup"><span data-stu-id="bd97e-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="bd97e-244">**arguments_ptr**: Ponto a partir dos argumentos da operação de execução.</span><span class="sxs-lookup"><span data-stu-id="bd97e-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="bd97e-245">Pode ser NULO se *arguments_length* for zero.</span><span class="sxs-lookup"><span data-stu-id="bd97e-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="bd97e-246">**arguments_length:** A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="bd97e-247">A função deve voltar NX_LWM2M_NOT_FOUND se o ID do recurso não existir, ou NX_LWM2M_METHOD_NOT_ALLOWED se não apoiar a execução.</span><span class="sxs-lookup"><span data-stu-id="bd97e-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="bd97e-248">O método 'Criar'</span><span class="sxs-lookup"><span data-stu-id="bd97e-248">The 'Create' Method</span></span>

<span data-ttu-id="bd97e-249">O método 'Criar' implementa a criação de uma nova Instância de Objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="bd97e-250">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-251">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="bd97e-252">**instance_id**: A identificação do novo Exemplo.</span><span class="sxs-lookup"><span data-stu-id="bd97e-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="bd97e-253">**num_values**: O número de recursos para inicializar.</span><span class="sxs-lookup"><span data-stu-id="bd97e-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="bd97e-254">**values_ptr**: Pontear os valores dos recursos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="bd97e-255">**instance_ptr**: Ponteiro para o ponteiro de destino da instância criada.</span><span class="sxs-lookup"><span data-stu-id="bd97e-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="bd97e-256">**bootstrap**: Verdadeiro se chamado da sequência de botas.</span><span class="sxs-lookup"><span data-stu-id="bd97e-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="bd97e-257">O Objeto deve atribuir e rubricar uma nova instância do Objeto, utilizando a lista fornecida de valores de recursos.</span><span class="sxs-lookup"><span data-stu-id="bd97e-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="bd97e-258">O método 'Eliminar'</span><span class="sxs-lookup"><span data-stu-id="bd97e-258">The 'Delete' Method</span></span>

<span data-ttu-id="bd97e-259">O método 'Eliminar' implementa a supressão de uma instância de objeto, a função tem a seguinte definição:</span><span class="sxs-lookup"><span data-stu-id="bd97e-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="bd97e-260">Os parâmetros de entrada são definidos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="bd97e-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="bd97e-261">**object_ptr**: Ponteiro para a implementação do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="bd97e-262">**instance_ptr**: Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="bd97e-263">No sucesso, o Objeto deve divulgar os dados de Instância do Objeto e qualquer outro recurso atribuído pela instância.</span><span class="sxs-lookup"><span data-stu-id="bd97e-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="bd97e-264">Adicionar implementações e instâncias de objetos ao cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="bd97e-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="bd97e-265">A aplicação pode adicionar nova implementação de objeto ao Cliente LWM2M, ligando para o serviço ***nx_lwm2m_client_object_add.***</span><span class="sxs-lookup"><span data-stu-id="bd97e-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="bd97e-266">Se o Objeto não suporta a criação dinâmica de Instâncias, por exemplo, se for apenas um objeto de instância única, o campo *nx_lwm2m_object_instances* da estrutura do objeto deve apontar para a lista das estruturas de instâncias estáticas.</span><span class="sxs-lookup"><span data-stu-id="bd97e-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="bd97e-267">Se o Objeto suportar a criação de instâncias dinâmicas, *nx_lwm2m_object_instances* deve ser definido para NU E o serviço ***nx_lwm2m_client_object_create*** deve ser utilizado para chamar o método 'Criar' do objeto.</span><span class="sxs-lookup"><span data-stu-id="bd97e-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="bd97e-268">Exemplo da Aplicação ao Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="bd97e-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="bd97e-269">O código a seguir é um exemplo de uma simples Aplicação de Cliente LWM2M que implementa um dispositivo personalizado composto por um sensor de temperatura e um interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="bd97e-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="bd97e-270">O dispositivo permite que um servidor leia o valor do sensor de temperatura e o estado booleano do interruptor de luz e ligue/desligue o interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="bd97e-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
