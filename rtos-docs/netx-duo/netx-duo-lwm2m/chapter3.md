---
title: Capítulo 3 - Descrição funcional do Cliente LWM2M
description: Este capítulo contém uma descrição funcional do Cliente LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825939"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="21ef7-103">Capítulo 3 Descrição funcional do Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="21ef7-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="21ef7-104">Este capítulo contém uma descrição funcional do Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="21ef7-105">Inicialização do cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="21ef7-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="21ef7-106">O Cliente LWM2M é inicializado ***ligando*** nx_lwm2m_client_create serviço.</span><span class="sxs-lookup"><span data-stu-id="21ef7-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="21ef7-107">O Cliente LWM2M funciona no seu próprio fio e pode reportar alguns eventos à aplicação através da utilização de callbacks, ou através de métodos de chamada dos objetos personalizados implementados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="21ef7-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="21ef7-108">Além disso, as Sessões de Cliente LWM2M devem ser criadas chamando ***nx_lwm2m_client_session_create*** para permitir a comunicação com um ou mais servidores.</span><span class="sxs-lookup"><span data-stu-id="21ef7-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="21ef7-109">Uma sessão pode comunicar com dois tipos diferentes de servidores: um Servidor Bootstrap ou um Servidor LWM2M (Gestão de Dispositivos).</span><span class="sxs-lookup"><span data-stu-id="21ef7-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="21ef7-110">Sessão de servidor de botas</span><span class="sxs-lookup"><span data-stu-id="21ef7-110">Bootstrap Server Session</span></span>

<span data-ttu-id="21ef7-111">Uma sessão de comunicação com um Servidor Bootstrap é usada para fornecer informações essenciais no Cliente LWM2M para permitir ao Cliente LWM2M realizar a operação "Register" com um ou mais Servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="21ef7-112">Este tipo de servidor é utilizado durante os modos de bootstrap iniciado pelo cliente e iniciado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="21ef7-113">A aplicação pode iniciar uma sessão de Bootstrap ligando ***nx_lwm2m_client_session_bootstrap** _ ou _*_nx_lwm2m_client_session_bootstrap_dtls,_\*_ deve fornecer o endereço IP e o número de porta do servidor, e um ID opcional de instância de objeto de segurança.</span><span class="sxs-lookup"><span data-stu-id="21ef7-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="21ef7-114">A função _*_nx_lwm2m_client_session_bootstrap_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* estabelece uma ligação DTLS segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="21ef7-115">Se a operação Bootstrap for bem sucedida, o servidor Bootstrap deveria ter criado instâncias de objetos de segurança para os servidores Bootstrap e LWM2M e instâncias de objetos de servidor para os servidores LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="21ef7-116">A aplicação pode ligar para ***nx_lwm2m_client_session_register_info_get*** para obter informações do LWM2M Server(s) e utilizar estas informações para estabelecer uma sessão com o(s) Servidor(s) LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="21ef7-117">Os dados bootstrap devem ser guardados para memória não volátil através da aplicação para configurar o Cliente LWM2M no próximo reinício do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21ef7-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="21ef7-118">Sessão de servidor LWM2M</span><span class="sxs-lookup"><span data-stu-id="21ef7-118">LWM2M Server Session</span></span>

<span data-ttu-id="21ef7-119">Uma sessão de comunicação com um Servidor LWM2M é utilizada para registo, gestão de dispositivos e ativação de serviços.</span><span class="sxs-lookup"><span data-stu-id="21ef7-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="21ef7-120">A aplicação pode registar o Cliente LWM2M num servidor chamando ***nx_lwm2m_client_session_register** _ ou _*_nx_lwm2m_client_session_register_dtls,_\*_ deve fornecer o endereço IP e o número de porta do servidor, e o ID do servidor curto que corresponde a uma Instância de Objeto de Servidor existente.</span><span class="sxs-lookup"><span data-stu-id="21ef7-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="21ef7-121">A função _*_nx_lwm2m_client_session_register_*_ utiliza uma comunicação insegura, enquanto que _ *_nx_lwm2m_client_session_register_dtls_*\* estabelece uma ligação DTLS segura com o servidor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="21ef7-122">A aplicação pode desinscrevê-lo através do registo do Cliente LWM2M ligando para ***nx_lwm2m_client_session_deregister** _, e pedir ao cliente para enviar uma mensagem de 'Update' ligando para _*_nx_lwm2m_client_session_update_\*\*.</span><span class="sxs-lookup"><span data-stu-id="21ef7-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="21ef7-123">Chamada do Estado da Sessão</span><span class="sxs-lookup"><span data-stu-id="21ef7-123">Session State Callback</span></span>

<span data-ttu-id="21ef7-124">A aplicação regista uma chamada de retorno na criação de uma sessão que é chamada quando o estado da sessão é atualizado, a função de retorno **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** tem o seguinte protótipo.</span><span class="sxs-lookup"><span data-stu-id="21ef7-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="21ef7-125">typedef VOID \* (NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* session_ptr,UINT);</span><span class="sxs-lookup"><span data-stu-id="21ef7-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="21ef7-126">Os seguintes estados são definidos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-126">The following states are defined.</span></span>

| <span data-ttu-id="21ef7-127">Estado da Sessão &nbsp;</span><span class="sxs-lookup"><span data-stu-id="21ef7-127">Session&nbsp;State</span></span> | <span data-ttu-id="21ef7-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="21ef7-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="21ef7-130">O estado inicial após a criação da sessão.</span><span class="sxs-lookup"><span data-stu-id="21ef7-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="21ef7-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="21ef7-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="21ef7-132">O cliente está à espera da expiração do temporizador 'Hold Off' ou da Bootstrap iniciado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="21ef7-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="21ef7-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="21ef7-134">O cliente enviou uma mensagem de 'Pedido' para o Servidor Bootstrap (Bota Iniciada pelo Cliente).</span><span class="sxs-lookup"><span data-stu-id="21ef7-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="21ef7-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="21ef7-136">O cliente está a receber dados do Servidor Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="21ef7-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="21ef7-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="21ef7-138">O Servidor Bootstrap enviou uma mensagem "Acabada".</span><span class="sxs-lookup"><span data-stu-id="21ef7-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="21ef7-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="21ef7-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="21ef7-140">A sessão de botas falhou.</span><span class="sxs-lookup"><span data-stu-id="21ef7-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="21ef7-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="21ef7-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="21ef7-142">O cliente enviou uma mensagem de 'Registo' para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="21ef7-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="21ef7-144">O cliente está registado no Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="21ef7-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="21ef7-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="21ef7-146">O cliente enviou uma mensagem de 'Actualização' para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="21ef7-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="21ef7-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="21ef7-148">O cliente enviou uma mensagem de "des-registo" para o Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="21ef7-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="21ef7-150">O cliente está desscista do Servidor LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="21ef7-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="21ef7-152">O Servidor LWM2M está desativado.</span><span class="sxs-lookup"><span data-stu-id="21ef7-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="21ef7-153">Um 'Registo' será enviado após o termo do temporizador para desativação.</span><span class="sxs-lookup"><span data-stu-id="21ef7-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="21ef7-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="21ef7-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="21ef7-155">A operação de registo ou atualização do Servidor LWM2M falhou.</span><span class="sxs-lookup"><span data-stu-id="21ef7-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="21ef7-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="21ef7-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="21ef7-157">A instância do objeto do servidor correspondente ao servidor LWM2M foi eliminada.</span><span class="sxs-lookup"><span data-stu-id="21ef7-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="21ef7-158">Em caso de erro, a aplicação pode recuperar a causa do erro chamando ***nx_lwm2m_client_session_error_get***.</span><span class="sxs-lookup"><span data-stu-id="21ef7-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="21ef7-159">Gestão local de dispositivos</span><span class="sxs-lookup"><span data-stu-id="21ef7-159">Local Device Management</span></span>

<span data-ttu-id="21ef7-160">A aplicação pode aceder aos Objetos do Cliente LWM2M utilizando as funções de gestão de dispositivos locais.</span><span class="sxs-lookup"><span data-stu-id="21ef7-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="21ef7-161">São fornecidas as seguintes funções.</span><span class="sxs-lookup"><span data-stu-id="21ef7-161">The following functions are provided.</span></span>

| <span data-ttu-id="21ef7-162">Nome da função &nbsp;</span><span class="sxs-lookup"><span data-stu-id="21ef7-162">Function&nbsp;Name</span></span> | <span data-ttu-id="21ef7-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="21ef7-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="21ef7-165">Leia os recursos de uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="21ef7-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="21ef7-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="21ef7-167">Obtenha a lista dos recursos de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="21ef7-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="21ef7-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="21ef7-169">Escreva recursos para uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="21ef7-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="21ef7-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="21ef7-171">Execute a operação Executar num recurso de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="21ef7-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="21ef7-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="21ef7-173">Crie uma nova instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="21ef7-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="21ef7-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="21ef7-175">Elimine uma instância de objeto existente.</span><span class="sxs-lookup"><span data-stu-id="21ef7-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="21ef7-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="21ef7-177">Obtenha o próximo ID do objeto pelo Cliente LWM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="21ef7-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="21ef7-179">Obtenha a próxima instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="21ef7-180">Informação sobre Recursos</span><span class="sxs-lookup"><span data-stu-id="21ef7-180">Resource Information</span></span>

<span data-ttu-id="21ef7-181">Ao ler e escrever para Objetos, um recurso é representado pela estrutura NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="21ef7-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="21ef7-182">Esta estrutura contém o ID do Recurso/Instância e o seu valor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="21ef7-183">As seguintes funções são fornecidas para a definição de informações e valor dos recursos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="21ef7-184">Nome da função &nbsp;</span><span class="sxs-lookup"><span data-stu-id="21ef7-184">Function&nbsp;Name</span></span> | <span data-ttu-id="21ef7-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="21ef7-187">Definir informações de recursos: id de recursos e funcionamento: LEIA, WRITE, EXECUTÁVEL.</span><span class="sxs-lookup"><span data-stu-id="21ef7-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="21ef7-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="21ef7-189">Desaprova o valor do recurso como cadeia.</span><span class="sxs-lookup"><span data-stu-id="21ef7-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="21ef7-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="21ef7-191">Desajei o valor do recurso como inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="21ef7-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="21ef7-193">Desajei o valor do recurso como inteiro de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="21ef7-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="21ef7-195">Desaprova o valor do recurso como boia de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="21ef7-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="21ef7-197">Desaprova o valor do recurso como boia de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="21ef7-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="21ef7-199">Desaprova o valor do recurso como boolean.</span><span class="sxs-lookup"><span data-stu-id="21ef7-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="21ef7-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="21ef7-201">Desaprova o valor do recurso como ligação de objetos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="21ef7-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="21ef7-203">Desajei o valor do recurso como opaco.</span><span class="sxs-lookup"><span data-stu-id="21ef7-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="21ef7-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="21ef7-205">Desfie o valor do recurso como exemplo para vários recursos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="21ef7-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="21ef7-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="21ef7-207">Desfita a dimensão do recurso para o recurso múltiplo para descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="21ef7-208">As seguintes funções são fornecidas para obter informações e valor de recursos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="21ef7-209">Nome da função &nbsp;</span><span class="sxs-lookup"><span data-stu-id="21ef7-209">Function&nbsp;Name</span></span> | <span data-ttu-id="21ef7-210">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="21ef7-212">Obtenha informações sobre recursos: id de recursos e funcionamento: LEIA, ESCREVa, EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="21ef7-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="21ef7-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="21ef7-214">Obtenha o valor de um recurso de corda.</span><span class="sxs-lookup"><span data-stu-id="21ef7-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="21ef7-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="21ef7-216">Obtenha o valor de um recurso inteiro de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="21ef7-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="21ef7-218">Obtenha o valor de um recurso inteiro b4-Bit.</span><span class="sxs-lookup"><span data-stu-id="21ef7-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="21ef7-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="21ef7-220">Obtenha o valor de um recurso flutuante de 32 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="21ef7-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="21ef7-222">Obtenha o valor de um recurso flutuante de 64 Bits.</span><span class="sxs-lookup"><span data-stu-id="21ef7-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="21ef7-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="21ef7-224">Obtenha o valor de um recurso Boolean.</span><span class="sxs-lookup"><span data-stu-id="21ef7-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="21ef7-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="21ef7-226">Obtenha o valor de um recurso de ligação de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="21ef7-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="21ef7-228">Obtenha o valor de um recurso opaco.</span><span class="sxs-lookup"><span data-stu-id="21ef7-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="21ef7-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="21ef7-230">Obtenha a instância de recursos para vários recursos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="21ef7-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="21ef7-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="21ef7-232">Obtenha a dimensão do recurso para vários recursos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="21ef7-233">Implementação de objetos</span><span class="sxs-lookup"><span data-stu-id="21ef7-233">Object Implementation</span></span>

<span data-ttu-id="21ef7-234">O Cliente LWM2M implementa os objetos obrigatórios OMA LWM2M: Segurança (0), Servidor (1), Controlo de Acesso (2) e Dispositivo (3).</span><span class="sxs-lookup"><span data-stu-id="21ef7-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="21ef7-235">Outros objetos específicos do dispositivo devem ser implementados pela aplicação.</span><span class="sxs-lookup"><span data-stu-id="21ef7-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="21ef7-236">Duas estruturas de dados são usadas para definir um Objeto: a estrutura NX_LWM2M_CLIENT_OBJECT define a implementação do Objeto, incluindo o ID do Objeto e os métodos do objeto, e a estrutura NX_LWM2M_CLIENT_OBJECT_INSTANCE contém os dados de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="21ef7-237">São fornecidas as seguintes funções.</span><span class="sxs-lookup"><span data-stu-id="21ef7-237">The following functions are provided.</span></span>

| <span data-ttu-id="21ef7-238">Nome da função &nbsp;</span><span class="sxs-lookup"><span data-stu-id="21ef7-238">Function&nbsp;Name</span></span> | <span data-ttu-id="21ef7-239">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="21ef7-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="21ef7-241">Adicione a implementação do objeto ao Cliente LwM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="21ef7-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="21ef7-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="21ef7-243">Remova a implementação do objeto do Cliente LwM2M.</span><span class="sxs-lookup"><span data-stu-id="21ef7-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="21ef7-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="21ef7-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="21ef7-245">Adicione a instância do objeto ao Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="21ef7-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="21ef7-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="21ef7-247">Remova a instância do objeto do objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="21ef7-248">A função de retorno do método do objeto tem a assinatura apresentada abaixo.</span><span class="sxs-lookup"><span data-stu-id="21ef7-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="21ef7-249">O método 'Ler'</span><span class="sxs-lookup"><span data-stu-id="21ef7-249">The ‘Read’ Method</span></span>

<span data-ttu-id="21ef7-250">O método 'Ler' é utilizado para ler os valores de recursos a partir de uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="21ef7-251">Os parâmetros são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-252">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-252">Parameter</span></span> | <span data-ttu-id="21ef7-253">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-254">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-254">**operation**</span></span> | <span data-ttu-id="21ef7-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="21ef7-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="21ef7-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-256">**object_ptr**</span></span> | <span data-ttu-id="21ef7-257">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-258">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-259">Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="21ef7-260">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-260">**resource**</span></span> | <span data-ttu-id="21ef7-261">Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="21ef7-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="21ef7-262">Na volta, a matriz é preenchida com os respetivos tipos e valores.</span><span class="sxs-lookup"><span data-stu-id="21ef7-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="21ef7-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-263">**resource_count**</span></span> | <span data-ttu-id="21ef7-264">Apontando para o número de recursos a ler.</span><span class="sxs-lookup"><span data-stu-id="21ef7-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="21ef7-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-265">**args_ptr**</span></span> | <span data-ttu-id="21ef7-266">Parâmetro não-apoiado para leitura.</span><span class="sxs-lookup"><span data-stu-id="21ef7-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="21ef7-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-267">**args_length**</span></span> | <span data-ttu-id="21ef7-268">Parâmetro não-apoiado para leitura.</span><span class="sxs-lookup"><span data-stu-id="21ef7-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="21ef7-269">O método 'Descobrir'</span><span class="sxs-lookup"><span data-stu-id="21ef7-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="21ef7-270">O método 'Discover' é utilizado para recuperar a lista de todos os Recursos implementados por um Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="21ef7-271">Os parâmetros são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-272">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-272">Parameter</span></span> | <span data-ttu-id="21ef7-273">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-274">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-274">**operation**</span></span> | <span data-ttu-id="21ef7-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="21ef7-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="21ef7-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-276">**object_ptr**</span></span> | <span data-ttu-id="21ef7-277">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-278">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-279">Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="21ef7-280">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-280">**resource**</span></span> | <span data-ttu-id="21ef7-281">Ponteiro para uma série de NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="21ef7-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="21ef7-282">Na devolução, a matriz é preenchida com informações de recursos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="21ef7-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="21ef7-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-283">**resource_count**</span></span> | <span data-ttu-id="21ef7-284">Ponteiro para o número de recursos a descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="21ef7-285">Na devolução, este parâmetro deve ser atualizado como o verdadeiro valor.</span><span class="sxs-lookup"><span data-stu-id="21ef7-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="21ef7-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-286">**args_ptr**</span></span> | <span data-ttu-id="21ef7-287">Parâmetro não-americano para descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="21ef7-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-288">**args_length**</span></span> | <span data-ttu-id="21ef7-289">Parâmetro não-americano para descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="21ef7-290">O método 'Escrever'</span><span class="sxs-lookup"><span data-stu-id="21ef7-290">The ‘Write’ Method</span></span>

<span data-ttu-id="21ef7-291">O método 'Escrever' é utilizado para atualizar ou substituir recursos de uma Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="21ef7-292">Os parâmetros são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-293">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-293">Parameter</span></span>  | <span data-ttu-id="21ef7-294">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-295">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-295">**operation**</span></span> | <span data-ttu-id="21ef7-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="21ef7-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="21ef7-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-297">**object_ptr**</span></span> | <span data-ttu-id="21ef7-298">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-299">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-300">Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="21ef7-301">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-301">**resource**</span></span> | <span data-ttu-id="21ef7-302">Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="21ef7-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="21ef7-303">Na volta, a matriz é preenchida com os respetivos tipos e valores.</span><span class="sxs-lookup"><span data-stu-id="21ef7-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="21ef7-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-304">**resource_count**</span></span> | <span data-ttu-id="21ef7-305">Ponteiro para o número de recursos a descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="21ef7-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-306">**args_ptr**</span></span> | <span data-ttu-id="21ef7-307">Escreve bandeiras.</span><span class="sxs-lookup"><span data-stu-id="21ef7-307">Write flags.</span></span> |
| <span data-ttu-id="21ef7-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-308">**args_length**</span></span> | <span data-ttu-id="21ef7-309">A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-309">The length of the arguments.</span></span> |

<span data-ttu-id="21ef7-310">As seguintes operações de escrita podem ser especificadas para o parâmetro da *bandeira.*</span><span class="sxs-lookup"><span data-stu-id="21ef7-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="21ef7-311">Operação</span><span class="sxs-lookup"><span data-stu-id="21ef7-311">Operation</span></span> | <span data-ttu-id="21ef7-312">Ação</span><span class="sxs-lookup"><span data-stu-id="21ef7-312">Action</span></span> | <span data-ttu-id="21ef7-313">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="21ef7-314">0</span><span class="sxs-lookup"><span data-stu-id="21ef7-314">0</span></span> | <span data-ttu-id="21ef7-315">Atualização Parcial</span><span class="sxs-lookup"><span data-stu-id="21ef7-315">Partial Update</span></span> | <span data-ttu-id="21ef7-316">Adiciona ou atualiza Recursos fornecidos no novo valor e deixa outros Recursos existentes inalterados.</span><span class="sxs-lookup"><span data-stu-id="21ef7-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="21ef7-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="21ef7-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="21ef7-318">Substituir Instância</span><span class="sxs-lookup"><span data-stu-id="21ef7-318">Replace Instance</span></span> | <span data-ttu-id="21ef7-319">Substitui a Instância do Objeto pelos novos valores de recursos fornecidos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="21ef7-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="21ef7-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="21ef7-321">Substituir recursos</span><span class="sxs-lookup"><span data-stu-id="21ef7-321">Replace Resource</span></span> | <span data-ttu-id="21ef7-322">Substitui os Recursos pelos novos valores de recursos fornecidos (utilizados para substituir Múltiplos Recursos).</span><span class="sxs-lookup"><span data-stu-id="21ef7-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="21ef7-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="21ef7-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="21ef7-324">Criar Instância</span><span class="sxs-lookup"><span data-stu-id="21ef7-324">Create Instance</span></span> | <span data-ttu-id="21ef7-325">Inicializa a instância de objeto recém-criada com os valores de recursos fornecidos (chamados do método **_nx_lwm2m_object_create)._**</span><span class="sxs-lookup"><span data-stu-id="21ef7-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="21ef7-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="21ef7-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="21ef7-327">Escrita de Bootstrap</span><span class="sxs-lookup"><span data-stu-id="21ef7-327">Bootstrap Write</span></span> | <span data-ttu-id="21ef7-328">Chamado durante a sequência de Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="21ef7-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="21ef7-329">O método 'Executar'</span><span class="sxs-lookup"><span data-stu-id="21ef7-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="21ef7-330">O método 'Executar' implementa a execução de um recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="21ef7-331">Os parâmetros de entrada são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-332">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-332">Parameter</span></span>  | <span data-ttu-id="21ef7-333">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-334">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-334">**operation**</span></span> | <span data-ttu-id="21ef7-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="21ef7-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="21ef7-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-336">**object_ptr**</span></span> | <span data-ttu-id="21ef7-337">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-338">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-339">Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="21ef7-340">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-340">**resource**</span></span> | <span data-ttu-id="21ef7-341">Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="21ef7-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="21ef7-342">Na volta, a matriz é preenchida com os respetivos tipos e valores.</span><span class="sxs-lookup"><span data-stu-id="21ef7-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="21ef7-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-343">**resource_count**</span></span> | <span data-ttu-id="21ef7-344">Ponteiro para o número de recursos a descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="21ef7-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-345">**args_ptr**</span></span> | <span data-ttu-id="21ef7-346">Apontando para os argumentos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="21ef7-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-347">**args_length**</span></span> | <span data-ttu-id="21ef7-348">A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-348">The length of the arguments.</span></span>  |

<span data-ttu-id="21ef7-349">A função deve voltar **NX_LWM2M_CLIENT_NOT_FOUND** se o ID do recurso não existir, ou **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** se não apoiar a execução.</span><span class="sxs-lookup"><span data-stu-id="21ef7-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="21ef7-350">O método 'Criar'</span><span class="sxs-lookup"><span data-stu-id="21ef7-350">The ‘Create’ Method</span></span>

<span data-ttu-id="21ef7-351">O método 'Criar' implementa a criação de uma nova Instância de Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="21ef7-352">Os parâmetros de entrada são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-353">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-353">Parameter</span></span>  | <span data-ttu-id="21ef7-354">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-355">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-355">**operation**</span></span> | <span data-ttu-id="21ef7-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="21ef7-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="21ef7-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-357">**object_ptr**</span></span> | <span data-ttu-id="21ef7-358">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-359">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-360">Parâmetro não-americano.</span><span class="sxs-lookup"><span data-stu-id="21ef7-360">Unused parameter.</span></span> |
| <span data-ttu-id="21ef7-361">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-361">**resource**</span></span> | <span data-ttu-id="21ef7-362">Ponteiro para uma série de **NX_LWM2M_CLIENT_RESOURCE** contendo as identificações dos recursos para ler.</span><span class="sxs-lookup"><span data-stu-id="21ef7-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="21ef7-363">Na volta, a matriz é preenchida com os respetivos tipos e valores.</span><span class="sxs-lookup"><span data-stu-id="21ef7-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="21ef7-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-364">**resource_count**</span></span> | <span data-ttu-id="21ef7-365">Ponteiro para o número de recursos a descobrir.</span><span class="sxs-lookup"><span data-stu-id="21ef7-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="21ef7-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-366">**args_ptr**</span></span> | <span data-ttu-id="21ef7-367">Identificação de caso de objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-367">Object instance id.</span></span> |
| <span data-ttu-id="21ef7-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-368">**args_length**</span></span> | <span data-ttu-id="21ef7-369">A duração dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="21ef7-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="21ef7-370">O método 'Eliminar'</span><span class="sxs-lookup"><span data-stu-id="21ef7-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="21ef7-371">O método 'Eliminar' implementa a eliminação de uma instância de objeto, os parâmetros de entrada são definidos da seguinte forma.</span><span class="sxs-lookup"><span data-stu-id="21ef7-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="21ef7-372">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="21ef7-372">Parameter</span></span>  | <span data-ttu-id="21ef7-373">Descrição</span><span class="sxs-lookup"><span data-stu-id="21ef7-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="21ef7-374">**operação**</span><span class="sxs-lookup"><span data-stu-id="21ef7-374">**operation**</span></span> | <span data-ttu-id="21ef7-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="21ef7-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="21ef7-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-376">**object_ptr**</span></span> | <span data-ttu-id="21ef7-377">Ponteiro para a implementação do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="21ef7-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-378">**instance_ptr**</span></span> | <span data-ttu-id="21ef7-379">Ponteiro para a Instância do Objeto.</span><span class="sxs-lookup"><span data-stu-id="21ef7-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="21ef7-380">**recurso**</span><span class="sxs-lookup"><span data-stu-id="21ef7-380">**resource**</span></span> | <span data-ttu-id="21ef7-381">Parâmetro não-americano.</span><span class="sxs-lookup"><span data-stu-id="21ef7-381">Unused parameter.</span></span> |
| <span data-ttu-id="21ef7-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="21ef7-382">**resource_count**</span></span> | <span data-ttu-id="21ef7-383">Parâmetro não-americano.</span><span class="sxs-lookup"><span data-stu-id="21ef7-383">Unused parameter.</span></span> |
| <span data-ttu-id="21ef7-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="21ef7-384">**args_ptr**</span></span> | <span data-ttu-id="21ef7-385">Parâmetro não-americano.</span><span class="sxs-lookup"><span data-stu-id="21ef7-385">Unused parameter.</span></span> |
| <span data-ttu-id="21ef7-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="21ef7-386">**args_length**</span></span> | <span data-ttu-id="21ef7-387">Parâmetro não-americano.</span><span class="sxs-lookup"><span data-stu-id="21ef7-387">Unused parameter.</span></span> |

<span data-ttu-id="21ef7-388">No sucesso, o Objeto deve divulgar os dados de Instância do Objeto e qualquer outro recurso atribuído pela instância.</span><span class="sxs-lookup"><span data-stu-id="21ef7-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="21ef7-389">Exemplo da Aplicação ao Cliente LWM2M</span><span class="sxs-lookup"><span data-stu-id="21ef7-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="21ef7-390">O código a seguir é um exemplo de uma simples Aplicação de Cliente LWM2M que implementa um dispositivo personalizado composto por um sensor de temperatura e um interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="21ef7-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="21ef7-391">O dispositivo permite que um servidor leia o valor do sensor de temperatura e o estado booleano do interruptor de luz e ligue/desligue o interruptor de luz.</span><span class="sxs-lookup"><span data-stu-id="21ef7-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```