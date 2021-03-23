---
title: Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo DHCP
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826119"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="2b28c-103">Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="2b28c-104">Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="2b28c-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="2b28c-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="2b28c-106">**nx_dhcp_create**: *Criar uma instância DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="2b28c-107">**nx_dhcp_clear_broadcast_flag**: *Clara bandeira de transmissão nas mensagens do Cliente*</span><span class="sxs-lookup"><span data-stu-id="2b28c-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="2b28c-108">**nx_dhcp_delete**: *Eliminar uma instância DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="2b28c-109">**nx_dhcp_force_renew**: *Enviar uma mensagem de renovação de força*</span><span class="sxs-lookup"><span data-stu-id="2b28c-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="2b28c-110">**nx_dhcp_packet_pool_set**: *Definir a piscina de pacotes do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="2b28c-111">**nx_dhcp_decline**: Enviar *mensagem de recusa para o servidor*</span><span class="sxs-lookup"><span data-stu-id="2b28c-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="2b28c-112">**nx_dhcp_release**: Enviar *mensagem de desbloqueio para o servidor*</span><span class="sxs-lookup"><span data-stu-id="2b28c-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="2b28c-113">**nx_dhcp_reinitialize**: *Claros parâmetros da rede de clientes DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="2b28c-114">**nx_dhcp_request_client_ip**: *Especifique um endereço IP específico*</span><span class="sxs-lookup"><span data-stu-id="2b28c-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="2b28c-115">**nx_dhcp_send_request**: *Enviar mensagem DHCP para o servidor*</span><span class="sxs-lookup"><span data-stu-id="2b28c-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="2b28c-116">**nx_dhcp_start**: *Inicie o processamento do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="2b28c-117">**nx_dhcp_stop**: *Parar o processamento do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="2b28c-118">**nx_dhcp_set_interface_index**: *Desa cos um pouco de interface para executar o Cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="2b28c-119">**nx_dhcp_server_address_get**: *Obtenha o endereço IP do servidor DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="2b28c-120">**nx_dhcp_state_change_notify**: *Desa esta medida de chamada quando o estado do DHCP mudar*</span><span class="sxs-lookup"><span data-stu-id="2b28c-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="2b28c-121">**nx_dhcp_user_option_retrieve**: *Recuperar a opção DHCP especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="2b28c-122">**nx_dhcp_user_option_convert**: *Converter quatro bytes para ULONG*</span><span class="sxs-lookup"><span data-stu-id="2b28c-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="2b28c-123">Serviços de clientes dHCP específicos da interface:</span><span class="sxs-lookup"><span data-stu-id="2b28c-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="2b28c-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clara bandeira de transmissão nas mensagens do Cliente na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="2b28c-125">**nx_dhcp_interface_enable**: *Permitir que a interface execute o DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="2b28c-126">**nx_dhcp_interface_disable**: *Desative a interface para executar o DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="2b28c-127">**nx_dhcp_interface_decline**: *Enviar mensagem de declínio para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="2b28c-128">**nx_dhcp_interface_force_renew**: *Enviar uma mensagem de renovação de força na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="2b28c-129">**nx_dhcp_interface_reinitialize**: *Limpar os parâmetros da rede de clientes DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="2b28c-130">**nx_dhcp_interface_release**: *Enviar mensagem de desbloqueio para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="2b28c-131">**nx_dhcp_interface_request_client_ip**: *Especifique um endereço IP específico na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="2b28c-132">**nx_dhcp_interface_send_request**: *Enviar mensagem DHCP para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="2b28c-133">**nx_dhcp_interface_server_address_get**: *Obtenha o endereço IP do servidor DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="2b28c-134">**nx_dhcp_interface_start**: *Inicie o processamento do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="2b28c-135">**nx_dhcp_interface_stop**: *Parar o processamento do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="2b28c-136">**nx_dhcp_interface_state_change_notify**: *Desa esta medida de chamada quando o estado de DHCP mudar na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="2b28c-137">**nx_dhcp_interface_user_option_retrieve**: *Recuperar a opção DHCP especificada na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="2b28c-138">Serviços ao cliente DAHCP se NX_DHCP_CLIENT_RESORE_STATE estiver definido:</span><span class="sxs-lookup"><span data-stu-id="2b28c-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="2b28c-139">**nx_dhcp_resume**: *Retomar estado de cliente DHCP previamente estabelecido*</span><span class="sxs-lookup"><span data-stu-id="2b28c-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="2b28c-140">**nx_dhcp_suspend**: *Suspender o processamento do estado do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="2b28c-141">**nx_dhcp_client_get_record**: *Criar um registo do estado do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="2b28c-142">**nx_dhcp_client_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="2b28c-143">**nx_dhcp_client_update_time_remaining**: *Atualizar o tempo que resta no estado atual do DHCP*</span><span class="sxs-lookup"><span data-stu-id="2b28c-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="2b28c-144">Serviços específicos do cliente DHCP de interface se NX_DHCP_CLIENT_RESORE_STATE for definido:</span><span class="sxs-lookup"><span data-stu-id="2b28c-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="2b28c-145">**nx_dhcp_client_interface_get_record**: *Criar um registo do estado do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="2b28c-146">**nx_dhcp_client_interface_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="2b28c-147">**nx_dhcp_client_interface_update_time_remaining**: *Atualizar o tempo restante no estado dhcp atual na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="2b28c-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="2b28c-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="2b28c-148">nx_dhcp_create</span></span>

<span data-ttu-id="2b28c-149">Criar uma instância DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-151">Description</span></span>

<span data-ttu-id="2b28c-152">Este serviço cria uma instância DHCP para a instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="2b28c-153">Por predefinição, a interface primária está ativada para executar o DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="2b28c-154">A entrada de nomes, embora não utilizada na implementação do NetX Duo do Cliente DHCP, deve seguir os critérios RFC 1035 para os nomes dos anfitriões.</span><span class="sxs-lookup"><span data-stu-id="2b28c-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="2b28c-155">O comprimento total não deve exceder 255 caracteres, as etiquetas separadas por pontos devem começar com uma letra, e terminar com uma letra ou número, e podem conter hífens, mas nenhum outro carácter não alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="2b28c-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="2b28c-156">Se a aplicação quiser executar a DHCP outra interface registada com a instância IP (utilizando *nx_ip_interface_attach),* a aplicação pode chamar *nx_dhcp_set_interface_index* para executar o DHCP apenas nessa interface, ou *nx_dhcp_interface_enable* para executar DHCP nessa interface também.</span><span class="sxs-lookup"><span data-stu-id="2b28c-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="2b28c-157">Consulte a descrição destes serviços para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="2b28c-158">A aplicação deve certificar-se de que a carga útil do pacote do cliente DHCP pode suportar o tamanho mínimo da mensagem DHCP especificado pela Secção 2 (548 bytes de dados de mensagens DHCP mais cabeçalhos de estrutura de UDP, IP e rede física).</span><span class="sxs-lookup"><span data-stu-id="2b28c-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-159">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-159">Input Parameters</span></span>

- <span data-ttu-id="2b28c-160">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="2b28c-161">**ip_ptr**: Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="2b28c-162">**name_ptr**: Ponteiro para o nome de anfitrião para a instância DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-163">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-163">Return Values</span></span>

- <span data-ttu-id="2b28c-164">**NX_SUCCESS**: (0x00) Cria o DHCP com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="2b28c-165">**NX_DHCP_INVALID_NAME:**(0xA8) Nome de anfitrião inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="2b28c-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Carga útil demasiado pequena para a mensagem DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="2b28c-167">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-168">Allowed From</span></span>

<span data-ttu-id="2b28c-169">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="2b28c-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="2b28c-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="2b28c-172">Permitir que a interface especificada execute o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="2b28c-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-174">Description</span></span>

<span data-ttu-id="2b28c-175">Este serviço permite a interface especificada para a execução do DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="2b28c-176">Por predefinição, a interface primária está ativada para o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="2b28c-177">Neste momento, o DHCP pode ser iniciado nesta interface, quer chamando *nx_dhcp_interface_start,* quer para iniciar o DHCP em todas as interfaces ativadas *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="2b28c-178">A aplicação deve primeiro registar esta interface com a instância IP, utilizando *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="2b28c-179">Além disso, deve existir um 'registo' de interface do Cliente DHCP disponível para adicionar esta interface à lista de interfaces ativadas.</span><span class="sxs-lookup"><span data-stu-id="2b28c-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="2b28c-180">Por predefinição, NX_DHCP_CLIENT_MAX_RECORDS é definido para 1.</span><span class="sxs-lookup"><span data-stu-id="2b28c-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="2b28c-181">Desa esta opção para o número máximo de interfaces que se espera que sejam executadas em simultâneo com o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="2b28c-182">Normalmente, NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; no entanto, se um dispositivo tiver mais interfaces físicas do que espera executar o Cliente DHCP, pode guardar a memória definindo NX_DHCP_CLIENT_MAX_RECORDS para menos do que esse número.</span><span class="sxs-lookup"><span data-stu-id="2b28c-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="2b28c-183">Não há um para um mapeamento de interfaces físicas com registos de interface do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="2b28c-184">A diferença entre este serviço e *nx_dhcp_set_interface_index* é que este último define apenas uma interface única para executar DHCP, enquanto este serviço simplesmente adiciona a interface especificada à lista de interfaces do Cliente ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="2b28c-185">Para desativar uma interface para DHCP, a aplicação pode chamar o</span><span class="sxs-lookup"><span data-stu-id="2b28c-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="2b28c-186">*nx_dhcp_interface_disable* serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-187">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-187">Input Parameters</span></span>

- <span data-ttu-id="2b28c-188">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-189">**interface_index**: Índice de interface para permitir a DHCP em</span><span class="sxs-lookup"><span data-stu-id="2b28c-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-190">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-190">Return Values</span></span>

- <span data-ttu-id="2b28c-191">**NX_SUCCESS**: (0x00) Ativar o DHCP com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="2b28c-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) Não há registo disponível para outra Interface a ser ativada para o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED:** Interface (0xA3) ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-194">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="2b28c-195">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-196">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-196">Allowed From</span></span>

<span data-ttu-id="2b28c-197">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-198">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="2b28c-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="2b28c-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="2b28c-200">Desative a interface especificada para executar o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="2b28c-201">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-202">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-202">Description</span></span>

<span data-ttu-id="2b28c-203">Este serviço desativa a interface especificada para a execução do DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="2b28c-204">Reinicia o Cliente DHCP nesta interface.</span><span class="sxs-lookup"><span data-stu-id="2b28c-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="2b28c-205">Para reiniciar o Cliente DHCP, a aplicação deve voltar a ativar a interface utilizando *nx_dhcp_interface_enable* e reiniciar o DHCP chamando *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-206">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-206">Input Parameters</span></span>

- <span data-ttu-id="2b28c-207">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-208">**interface_index**: Índice de interface para desativar o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-209">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-209">Return Values</span></span>

- <span data-ttu-id="2b28c-210">**NX_SUCCESS**: (0x00) Cria o DHCP com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="2b28c-211">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-212">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="2b28c-213">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="2b28c-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="2b28c-214">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-215">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-215">Allowed From</span></span>

<span data-ttu-id="2b28c-216">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-217">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="2b28c-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="2b28c-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="2b28c-219">Definir a bandeira de transmissão DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-220">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="2b28c-221">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-221">Description</span></span>

<span data-ttu-id="2b28c-222">Este serviço define ou limpa a bandeira de transmissão o cabeçalho de mensagem DHCP para todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="2b28c-223">Para algumas mensagens DHCP (por exemplo, DISCOVER) a bandeira de transmissão está definida para ser transmitida porque o Cliente não tem um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="2b28c-224">clear_flag valores:</span><span class="sxs-lookup"><span data-stu-id="2b28c-224">clear_flag values:</span></span> 

- <span data-ttu-id="2b28c-225">**NX_TRUE:** a bandeira de radiodifusão é apurada (pedido de resposta unicast)</span><span class="sxs-lookup"><span data-stu-id="2b28c-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="2b28c-226">**NX_FALSE:** é definida a bandeira de radiodifusão (pedido de resposta transmitida)</span><span class="sxs-lookup"><span data-stu-id="2b28c-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="2b28c-227">Este serviço destina-se a Clientes DHCP que devem passar por um router para chegar ao Servidor DHCP, onde o router rejeita o encaminhamento de mensagens de transmissão.</span><span class="sxs-lookup"><span data-stu-id="2b28c-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-228">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-228">Input Parameters</span></span>

- <span data-ttu-id="2b28c-229">**dhcp_ptr**: Ponteiro para bloco de controlo DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="2b28c-230">**clear_flag**: Valor para definir a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="2b28c-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-231">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-231">Return Values</span></span>

- <span data-ttu-id="2b28c-232">**NX_SUCCESS**: (0x00) Com sucesso colocar a bandeira</span><span class="sxs-lookup"><span data-stu-id="2b28c-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="2b28c-233">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-234">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-234">Allowed From</span></span>

<span data-ttu-id="2b28c-235">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="2b28c-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="2b28c-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="2b28c-238">Desmarcar ou limpar a bandeira de transmissão na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="2b28c-240">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-240">Description</span></span>

<span data-ttu-id="2b28c-241">Este serviço permite que a aplicação do anfitrião do cliente DHCP desempecifique ou limpe a bandeira de transmissão nas mensagens do Cliente DHCP para o Servidor DHCP na interface especificada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="2b28c-242">Para mais detalhes, **consulte nx_dhcp_clear_broadcast_flag.**</span><span class="sxs-lookup"><span data-stu-id="2b28c-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-243">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-243">Input Parameters</span></span>

- <span data-ttu-id="2b28c-244">**dhcp_ptr**: Ponteiro para bloco de controlo DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="2b28c-245">**interface_index**: Índice de interface para definir a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="2b28c-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="2b28c-246">**clear_flag**: Valor para definir a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="2b28c-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-247">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-247">Return Values</span></span>

- <span data-ttu-id="2b28c-248">**NX_SUCCESS**: (0x00) Com sucesso colocar a bandeira</span><span class="sxs-lookup"><span data-stu-id="2b28c-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="2b28c-249">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-250">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="2b28c-251">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-252">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-252">Allowed From</span></span>

<span data-ttu-id="2b28c-253">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-254">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="2b28c-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="2b28c-255">nx_dhcp_delete</span></span>

<span data-ttu-id="2b28c-256">Eliminar uma instância DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-258">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-258">Description</span></span>

<span data-ttu-id="2b28c-259">Este serviço elimina uma instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-260">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-260">Input Parameters</span></span>

- <span data-ttu-id="2b28c-261">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-262">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-262">Return Values</span></span>

- <span data-ttu-id="2b28c-263">**NX_SUCCESS:**(0x00) Eliminar o DHCP com sucesso.</span><span class="sxs-lookup"><span data-stu-id="2b28c-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="2b28c-264">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-265">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-266">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-266">Allowed From</span></span>

<span data-ttu-id="2b28c-267">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-268">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="2b28c-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="2b28c-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="2b28c-270">Enviar uma mensagem de renovação de força</span><span class="sxs-lookup"><span data-stu-id="2b28c-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="2b28c-271">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-272">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-272">Description</span></span>

<span data-ttu-id="2b28c-273">Este serviço permite que a aplicação do anfitrião envie uma mensagem de renovação de força em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="2b28c-274">O Cliente DHCP deve estar num estado vinculado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="2b28c-275">Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.</span><span class="sxs-lookup"><span data-stu-id="2b28c-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="2b28c-276">Para enviar uma renovação de força numa interface específica quando várias interfaces estiverem habilitados a DHCP, utilize *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-277">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-277">Input Parameters</span></span>

- <span data-ttu-id="2b28c-278">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-279">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-279">Return Values</span></span>

- <span data-ttu-id="2b28c-280">**NX_SUCCESS:**(0x00) Enviou com sucesso a renovação da força.</span><span class="sxs-lookup"><span data-stu-id="2b28c-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="2b28c-281">**NX_DHCP_NOT_BOUND:**(0x94) endereço IP do cliente não vinculado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="2b28c-282">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-283">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-284">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-284">Allowed From</span></span>

<span data-ttu-id="2b28c-285">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-286">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="2b28c-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="2b28c-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="2b28c-288">Envie uma mensagem de renovação de força na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-290">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-290">Description</span></span>

<span data-ttu-id="2b28c-291">Este serviço permite que a aplicação anfitriã envie uma mensagem de renovação de força na interface de entrada, desde que essa interface tenha sido ativada para DHCP (ver *nx_dhcp_interface_enable).*</span><span class="sxs-lookup"><span data-stu-id="2b28c-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="2b28c-292">O Cliente DHCP na interface especificada deve estar num estado VINculado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="2b28c-293">Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.</span><span class="sxs-lookup"><span data-stu-id="2b28c-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-294">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-294">Input Parameters</span></span>

- <span data-ttu-id="2b28c-295">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-296">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-296">Return Values</span></span>

- <span data-ttu-id="2b28c-297">**NX_SUCCESS:**(0x00) Enviou com sucesso a renovação da força.</span><span class="sxs-lookup"><span data-stu-id="2b28c-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="2b28c-298">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-299">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="2b28c-300">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-301">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-301">Allowed From</span></span>

<span data-ttu-id="2b28c-302">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-303">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="2b28c-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="2b28c-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="2b28c-305">Desa estaladiço do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-307">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-307">Description</span></span>

<span data-ttu-id="2b28c-308">Este serviço permite que a aplicação crie o pool de pacotes do Cliente DHCP, passando um ponteiro para um pacote de pacotes previamente criado nesta chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="2b28c-309">Para utilizar esta funcionalidade, a aplicação do anfitrião deve definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="2b28c-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="2b28c-310">Quando definido, o serviço *nx_dhcp_create* não criará a piscina de pacotes do Cliente.</span><span class="sxs-lookup"><span data-stu-id="2b28c-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="2b28c-311">A aplicação é recomendada para usar os valores padrão para a carga útil do pacote de cliente DHCP, definida como NX_DHCP_PACKET_PAYLOAD em *nxd_dhcp_client.h* ao criar o pool de pacotes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-312">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-312">Input Parameters</span></span>

- <span data-ttu-id="2b28c-313">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-314">**packet_pool_ptr**: Ponteiro para piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="2b28c-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-315">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-315">Return Values</span></span>

- <span data-ttu-id="2b28c-316">**NX_SUCCESS**: (0x00) DhCP Pacote de pacotes de clientes está definido</span><span class="sxs-lookup"><span data-stu-id="2b28c-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="2b28c-317">**NX_NOT_ENABLED**: (0x14) O serviço não está ativado</span><span class="sxs-lookup"><span data-stu-id="2b28c-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="2b28c-318">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) A carga útil é muito pequena</span><span class="sxs-lookup"><span data-stu-id="2b28c-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-320">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-320">Allowed From</span></span>

<span data-ttu-id="2b28c-321">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="2b28c-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-322">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="2b28c-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="2b28c-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="2b28c-324">Definir endereço IP solicitado para instância DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-325">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="2b28c-326">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-326">Description</span></span>

<span data-ttu-id="2b28c-327">Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na primeira interface ativada para DHCP no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="2b28c-328">Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="2b28c-329">Para definir o pedido de um IP específico para mensagens DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_request_client_ip.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-330">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-330">Input Parameters</span></span>

- <span data-ttu-id="2b28c-331">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-332">**client_ip_address**: Endereço IP a pedido do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="2b28c-333">**skip_discover_message:**</span><span class="sxs-lookup"><span data-stu-id="2b28c-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="2b28c-334">Se for verdade, o Cliente DHCP envia mensagem de pedido</span><span class="sxs-lookup"><span data-stu-id="2b28c-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="2b28c-335">Se for falso, envia a mensagem Discover.</span><span class="sxs-lookup"><span data-stu-id="2b28c-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-336">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-336">Return Values</span></span>

- <span data-ttu-id="2b28c-337">**NX_SUCCESS:**(0x00) Está definido o endereço IP solicitado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="2b28c-338">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) endereço IP NUDO solicitado</span><span class="sxs-lookup"><span data-stu-id="2b28c-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-340">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-340">Allowed From</span></span>

<span data-ttu-id="2b28c-341">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-342">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="2b28c-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="2b28c-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="2b28c-344">Definir endereço IP solicitado para instância DHCP em interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-345">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="2b28c-346">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-346">Description</span></span>

<span data-ttu-id="2b28c-347">Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na interface especificada, se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="2b28c-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="2b28c-348">Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-349">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-349">Input Parameters</span></span>

- <span data-ttu-id="2b28c-350">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="2b28c-351">**Interface_index**: Índice de interface para solicitar endereço IP em</span><span class="sxs-lookup"><span data-stu-id="2b28c-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="2b28c-352">**client_ip_address**: Endereço IP a pedido do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="2b28c-353">**skip_discover_message**: Se for verdade, o Cliente DHCP envia mensagem de pedido; senão envia a mensagem Discover.</span><span class="sxs-lookup"><span data-stu-id="2b28c-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-354">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-354">Return Values</span></span>

- <span data-ttu-id="2b28c-355">**NX_SUCCESS:**(0x00) Está definido o endereço IP solicitado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="2b28c-356">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-357">NX_PTR_ERROR: (0x16) Ponteiro IP inválido ou DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="2b28c-358">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-359">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-359">Allowed From</span></span>

<span data-ttu-id="2b28c-360">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-361">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="2b28c-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="2b28c-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="2b28c-363">Limpe os parâmetros da rede de clientes DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="2b28c-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-365">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-365">Description</span></span>

<span data-ttu-id="2b28c-366">Este serviço limpa os parâmetros da rede de aplicações do anfitrião (endereço IP, endereço de rede e máscara de rede) e limpa o estado do Cliente DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="2b28c-367">É utilizado em combinação com *nx_dhcp_stop* e *nx_dhcp_start* para "reiniciar" a máquina estatal DHCP:</span><span class="sxs-lookup"><span data-stu-id="2b28c-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="2b28c-368">Para reinitializar o Cliente DHCP numa interface específica quando várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_reinitialize.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-369">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-369">Input Parameters</span></span>

- <span data-ttu-id="2b28c-370">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-371">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-371">Return Values</span></span>

- <span data-ttu-id="2b28c-372">**NX_SUCCESS**: (0x00) DHCP reinibida com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="2b28c-373">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-374">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-374">Allowed From</span></span>

<span data-ttu-id="2b28c-375">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-376">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="2b28c-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="2b28c-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="2b28c-378">Limpe os parâmetros da rede de clientes DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="2b28c-379">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-380">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-380">Description</span></span>

<span data-ttu-id="2b28c-381">Este serviço limpa os parâmetros de rede (endereço IP, endereço de rede e máscara de rede) na interface especificada se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="2b28c-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="2b28c-382">Consulte *nx_dhcp_reinitialize* para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-383">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-383">Input Parameters</span></span>

- <span data-ttu-id="2b28c-384">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada</span><span class="sxs-lookup"><span data-stu-id="2b28c-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="2b28c-385">**interface_index**: Índice de interface para reinitializar</span><span class="sxs-lookup"><span data-stu-id="2b28c-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-386">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-386">Return Values</span></span>

- <span data-ttu-id="2b28c-387">**NX_SUCCESS:**(0x00) Interface reinicializada com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="2b28c-388">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-389">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-390">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="2b28c-391">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-392">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-392">Allowed From</span></span>

<span data-ttu-id="2b28c-393">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-394">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="2b28c-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="2b28c-395">nx_dhcp_release</span></span>

<span data-ttu-id="2b28c-396">Liberação de endereço IP alugado</span><span class="sxs-lookup"><span data-stu-id="2b28c-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-397">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-398">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-398">Description</span></span>

<span data-ttu-id="2b28c-399">Este serviço liberta o endereço IP obtido a partir de um servidor DHCP enviando a mensagem RELEASE para esse servidor.</span><span class="sxs-lookup"><span data-stu-id="2b28c-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="2b28c-400">Em seguida, reinicia o cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="2b28c-401">Este serviço é aplicado a todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="2b28c-402">A aplicação pode reiniciar o Cliente DHCP chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="2b28c-403">Para libertar um endereço de volta para o servidor DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="2b28c-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-404">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-404">Input Parameters</span></span>

- <span data-ttu-id="2b28c-405">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-406">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-406">Return Values</span></span>

- <span data-ttu-id="2b28c-407">**NX_SUCCESS**: (0x00) Libertação bem sucedida do DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="2b28c-408">**NX_DHCP_NOT_BOUND**: (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="2b28c-409">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-410">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-411">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-411">Allowed From</span></span>

<span data-ttu-id="2b28c-412">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-413">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="2b28c-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="2b28c-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="2b28c-415">Liberar endereço IP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-416">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-417">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-417">Description</span></span>

<span data-ttu-id="2b28c-418">Este serviço liberta o endereço IP obtido a partir de um servidor DHCP na interface especificada e reinicia o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="2b28c-419">O Cliente DHCP pode ser reiniciado chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-420">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-420">Input Parameters</span></span>

- <span data-ttu-id="2b28c-421">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-422">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-422">Return Values</span></span>

- <span data-ttu-id="2b28c-423">**NX_SUCCESS**: (0x00) Libertação bem sucedida do DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="2b28c-424">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-425">**NX_DHCP_NOT_BOUND**: (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="2b28c-426">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-427">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="2b28c-428">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-429">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-429">Allowed From</span></span>

<span data-ttu-id="2b28c-430">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-431">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="2b28c-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="2b28c-432">nx_dhcp_decline</span></span>

<span data-ttu-id="2b28c-433">Recuse o endereço IP do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-434">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-435">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-435">Description</span></span>

<span data-ttu-id="2b28c-436">Este serviço declina um endereço IP alugado a partir do servidor DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="2b28c-437">Se NX_DHCP_CLIENT_ SEND_ ARP_PROBE estiver definido, o Cliente DHCP enviará uma mensagem DECLINE se detetar que o endereço IP já está a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="2b28c-438">Consulte **as sondas ARP** no Capítulo Um para obter mais informações sobre a configuração da sonda ARP no Cliente DHCP da NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2b28c-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="2b28c-439">A aplicação pode usar este serviço para recusar o seu endereço IP se descobrir que o endereço está a ser utilizado por outros meios.</span><span class="sxs-lookup"><span data-stu-id="2b28c-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="2b28c-440">Este serviço reinicia o Cliente DHCP para que possa ser reiniciado chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-441">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-441">Input Parameters</span></span>

- <span data-ttu-id="2b28c-442">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-443">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-443">Return Values</span></span>

- <span data-ttu-id="2b28c-444">**NX_SUCCESS**: (0x00) Declínio enviado com sucesso</span><span class="sxs-lookup"><span data-stu-id="2b28c-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="2b28c-445">**NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado</span><span class="sxs-lookup"><span data-stu-id="2b28c-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="2b28c-446">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-447">NX_CALLER_ERROR: (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="2b28c-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-448">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-448">Allowed From</span></span>

<span data-ttu-id="2b28c-449">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-450">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="2b28c-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="2b28c-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="2b28c-452">Recuse o endereço IP do Servidor DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-453">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-454">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-454">Description</span></span>

<span data-ttu-id="2b28c-455">Este serviço envia a mensagem DECLINar para o servidor para recusar um endereço IP atribuído pelo servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="2b28c-456">Também reinicia o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="2b28c-457">Consulte *nx_dhcp_decline* para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-458">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-458">Input Parameters</span></span>

- <span data-ttu-id="2b28c-459">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-460">**Interface_index**: Índice de interface para recusar endereço IP</span><span class="sxs-lookup"><span data-stu-id="2b28c-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-461">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-461">Return Values</span></span>

- <span data-ttu-id="2b28c-462">**NX_SUCCESS**: (0x00) Mensagem de declínio dhcp enviada</span><span class="sxs-lookup"><span data-stu-id="2b28c-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="2b28c-463">**NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado</span><span class="sxs-lookup"><span data-stu-id="2b28c-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="2b28c-464">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-465">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-466">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="2b28c-467">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-468">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-468">Allowed From</span></span>

<span data-ttu-id="2b28c-469">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-470">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="2b28c-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="2b28c-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="2b28c-472">Enviar mensagem DHCP para o Servidor</span><span class="sxs-lookup"><span data-stu-id="2b28c-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-473">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="2b28c-474">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-474">Description</span></span>

<span data-ttu-id="2b28c-475">Este serviço envia a mensagem DHCP especificada para o servidor DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="2b28c-476">Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2b28c-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="2b28c-477">O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para enviar o tipo de mensagem INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="2b28c-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="2b28c-478">Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.</span><span class="sxs-lookup"><span data-stu-id="2b28c-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-479">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-479">Input Parameters</span></span>

- <span data-ttu-id="2b28c-480">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-481">**dhcp_message_type**: Pedido de mensagem (definido em *nxd_dhcp_client.h)*</span><span class="sxs-lookup"><span data-stu-id="2b28c-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-482">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-482">Return Values</span></span>

- <span data-ttu-id="2b28c-483">**NX_SUCCESS**: (0x00) Mensagem DHCP enviada</span><span class="sxs-lookup"><span data-stu-id="2b28c-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="2b28c-484">**NX_DHCP_NOT_STARTED:**(0x96) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="2b28c-485">**NX_DHCP_INVALID_MESSAGE:**(0x9B) Tipo de mensagem inválida para enviar</span><span class="sxs-lookup"><span data-stu-id="2b28c-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="2b28c-486">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="2b28c-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-487">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-487">Allowed From</span></span>

<span data-ttu-id="2b28c-488">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-489">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="2b28c-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="2b28c-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="2b28c-491">Envie mensagem DHCP para o Servidor numa interface específica</span><span class="sxs-lookup"><span data-stu-id="2b28c-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-492">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="2b28c-493">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-493">Description</span></span>

<span data-ttu-id="2b28c-494">Este serviço envia uma mensagem para o servidor DHCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="2b28c-495">Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2b28c-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="2b28c-496">O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para o envio do tipo de mensagem DHCP INFORM REQUEST.</span><span class="sxs-lookup"><span data-stu-id="2b28c-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="2b28c-497">Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.</span><span class="sxs-lookup"><span data-stu-id="2b28c-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-498">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-498">Input Parameters</span></span>

- <span data-ttu-id="2b28c-499">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="2b28c-500">**Interface_index**: Índice de interface para enviar mensagem</span><span class="sxs-lookup"><span data-stu-id="2b28c-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="2b28c-501">**dhcp_message_type**: Pedido de mensagem (definido em nxd_dhcp_client.h)</span><span class="sxs-lookup"><span data-stu-id="2b28c-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-502">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-502">Return Values</span></span>

- <span data-ttu-id="2b28c-503">**NX_SUCCESS**: (0x00) Mensagem DHCP enviada</span><span class="sxs-lookup"><span data-stu-id="2b28c-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="2b28c-504">**NX_DHCP_NOT_STARTED:**(0x96) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="2b28c-505">**NX_DHCP_INVALID_MESSAGE:**(0x9B) Tipo de mensagem inválida para enviar</span><span class="sxs-lookup"><span data-stu-id="2b28c-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="2b28c-506">**NX_DHCP_INTERFACE_NOT_ENABLED:** Interface (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-507">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-508">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="2b28c-509">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-510">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-510">Allowed From</span></span>

<span data-ttu-id="2b28c-511">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-512">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="2b28c-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="2b28c-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="2b28c-514">Obtenha o endereço IP do servidor DHCP do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-515">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="2b28c-516">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-516">Description</span></span>

<span data-ttu-id="2b28c-517">Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na primeira interface ativada para DHCP encontrado no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="2b28c-518">O chamador só pode utilizar este serviço depois de o Cliente DHCP estar ligado a um endereço IP atribuído pelo Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="2b28c-519">A aplicação de anfitrião pode usar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar o *nx _dhcp_state_change_notify* e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="2b28c-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="2b28c-520">Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="2b28c-521">Para encontrar o servidor DHCP numa interface específica quando várias interfaces estiverem ativadas para o Cliente DHCP, utilize o serviço *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="2b28c-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-522">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-522">Input Parameters</span></span>

- <span data-ttu-id="2b28c-523">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="2b28c-524">**server_address**: Ponteiro para o endereço IP do servidor</span><span class="sxs-lookup"><span data-stu-id="2b28c-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-525">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-525">Return Values</span></span>

- <span data-ttu-id="2b28c-526">**NX_SUCCESS:**(0x00) endereço do servidor DHCP devolvido</span><span class="sxs-lookup"><span data-stu-id="2b28c-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="2b28c-527">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-528">NX_PTR_ERROR: (0x16) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="2b28c-529">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-530">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-530">Allowed From</span></span>

<span data-ttu-id="2b28c-531">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-532">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="2b28c-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="2b28c-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="2b28c-534">Obtenha o endereço IP do servidor DHCP do cliente DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-535">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="2b28c-536">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-536">Description</span></span>

<span data-ttu-id="2b28c-537">Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="2b28c-538">O Cliente DHCP deve estar no estado de Bound.</span><span class="sxs-lookup"><span data-stu-id="2b28c-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="2b28c-539">Depois de iniciar o Cliente DHCP nessa interface, a aplicação anfitriã pode utilizar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar a chamada de alteração do estado do cliente DHCP e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="2b28c-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="2b28c-540">Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-541">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-541">Input Parameters</span></span>

- <span data-ttu-id="2b28c-542">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="2b28c-543">**Interface_index**: Índice de interface para obter endereço IP</span><span class="sxs-lookup"><span data-stu-id="2b28c-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="2b28c-544">**server_address**: Ponteiro para o endereço IP do servidor</span><span class="sxs-lookup"><span data-stu-id="2b28c-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-545">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-545">Return Values</span></span>

- <span data-ttu-id="2b28c-546">**NX_SUCCESS:**(0x00) endereço do servidor DHCP devolvido</span><span class="sxs-lookup"><span data-stu-id="2b28c-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="2b28c-547">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-548">**NX_DHCP_NOT_BOUND:**(0x94) Cliente DHCP não vinculado</span><span class="sxs-lookup"><span data-stu-id="2b28c-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="2b28c-549">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="2b28c-550">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="2b28c-551">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-552">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-552">Allowed From</span></span>

<span data-ttu-id="2b28c-553">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-554">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="2b28c-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="2b28c-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="2b28c-556">Definir interface de rede para a instância DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-557">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="2b28c-558">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-558">Description</span></span>

<span data-ttu-id="2b28c-559">Este serviço define a interface de rede para a instância DHCP ligar ao Servidor DHCP quando executa o Cliente DHCP configurado para uma única interface de rede.</span><span class="sxs-lookup"><span data-stu-id="2b28c-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="2b28c-560">Por predefinição, o Cliente DHCP funciona na interface primária.</span><span class="sxs-lookup"><span data-stu-id="2b28c-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="2b28c-561">Para executar o DHCP num serviço secundário, utilize este serviço para definir a interface secundária como interface do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="2b28c-562">O pedido deve registar previamente a interface especificada para a instância IP utilizando o serviço *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="2b28c-563">Este serviço destina-se a aplicações que pretendam executar o Cliente DHCP numa única interface.</span><span class="sxs-lookup"><span data-stu-id="2b28c-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="2b28c-564">Para executar DHCP em várias interfaces consulte *nx_dhcp_interface_enable* para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-565">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-565">Input Parameters</span></span>

- <span data-ttu-id="2b28c-566">**dhcp_ptr**: Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="2b28c-567">**índice**: Índice da interface da rede de dispositivos</span><span class="sxs-lookup"><span data-stu-id="2b28c-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-568">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-568">Return Values</span></span>

- <span data-ttu-id="2b28c-569">**NX_SUCCESS:**(0x00) A interface está definida com sucesso.</span><span class="sxs-lookup"><span data-stu-id="2b28c-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="2b28c-570">**NX_INVALID_INTERFACE:**(0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="2b28c-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED:** Interface (0xA3) ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) Não há registo disponível para outro</span><span class="sxs-lookup"><span data-stu-id="2b28c-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="2b28c-573">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="2b28c-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-574">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-574">Allowed From</span></span>

<span data-ttu-id="2b28c-575">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-576">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="2b28c-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="2b28c-577">nx_dhcp_start</span></span>

<span data-ttu-id="2b28c-578">Iniciar o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-579">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-580">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-580">Description</span></span>

<span data-ttu-id="2b28c-581">Este serviço inicia o processamento de DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="2b28c-582">Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="2b28c-583">Para verificar quando a instância IP está ligada a um endereço IP na interface do Cliente DHCP, utilize *nx_ip_status_check* para ver confirmar se o endereço IP é válido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="2b28c-584">Se existirem outras interfaces já em execução dhCP, este serviço não irá afetá-los.</span><span class="sxs-lookup"><span data-stu-id="2b28c-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="2b28c-585">Para iniciar o DHCP numa interface específica quando várias interfaces estiverem ativadas, utilize o serviço *nx_dhcp_interface_start.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-586">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-586">Input Parameters</span></span>

- <span data-ttu-id="2b28c-587">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-588">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-588">Return Values</span></span>

- <span data-ttu-id="2b28c-589">**NX_SUCCESS**: (0x00) Início dhcp bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="2b28c-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="2b28c-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2b28c-591">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-592">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-593">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-593">Allowed From</span></span>

<span data-ttu-id="2b28c-594">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-595">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="2b28c-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="2b28c-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="2b28c-597">Iniciar o processamento do DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-598">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-599">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-599">Description</span></span>

<span data-ttu-id="2b28c-600">Este serviço inicia o processamento de DHCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="2b28c-601">Consulte *nx_dhcp_interface_enable*() para obter mais detalhes sobre como ativar uma interface para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="2b28c-602">Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="2b28c-603">Se não houver outras interfaces a executar o Cliente DHCP este serviço iniciará/retomará a linha do Cliente DHCP e (re)ativar o temporizador do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="2b28c-604">A aplicação deve utilizar *nx_ip_status_check* para verificar se um endereço IP é obtido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-605">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-605">Input Parameters</span></span>

- <span data-ttu-id="2b28c-606">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-607">**Interface_index**: Índice sobre o qual iniciar o Cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-608">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-608">Return Values</span></span>

- <span data-ttu-id="2b28c-609">**NX_SUCCESS**: (0x00) Início dhcp bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="2b28c-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="2b28c-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2b28c-611">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-612">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2b28c-613">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-614">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-614">Allowed From</span></span>

<span data-ttu-id="2b28c-615">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-616">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="2b28c-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="2b28c-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="2b28c-618">Definir função de retorno de mudança de estado DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-619">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="2b28c-620">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-620">Description</span></span>

<span data-ttu-id="2b28c-621">Este serviço regista a função de retorno especificado dhcp_state_change_notify para notificar uma aplicação de alterações do estado dhcp.</span><span class="sxs-lookup"><span data-stu-id="2b28c-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="2b28c-622">A função de retorno fornece o estado em que o Cliente DHCP se transferiu.</span><span class="sxs-lookup"><span data-stu-id="2b28c-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="2b28c-623">Seguem-se os valores associados aos vários estados da DHCP:</span><span class="sxs-lookup"><span data-stu-id="2b28c-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="2b28c-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="2b28c-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="2b28c-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="2b28c-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="2b28c-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="2b28c-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="2b28c-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="2b28c-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="2b28c-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="2b28c-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="2b28c-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="2b28c-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="2b28c-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="2b28c-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="2b28c-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="2b28c-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="2b28c-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="2b28c-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-633">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-633">Input Parameters</span></span>

- <span data-ttu-id="2b28c-634">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-635">**dhcp_state_change_notify**: Ponteiro da função de retorno de mudança de estado</span><span class="sxs-lookup"><span data-stu-id="2b28c-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-636">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-636">Return Values</span></span>

- <span data-ttu-id="2b28c-637">**NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="2b28c-638">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-639">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-640">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-640">Allowed From</span></span>

<span data-ttu-id="2b28c-641">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-642">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="2b28c-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="2b28c-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="2b28c-644">Definir função de retorno de alteração de estado DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-645">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="2b28c-646">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-646">Description</span></span>

<span data-ttu-id="2b28c-647">Este serviço regista a função de retorno especificado para notificar uma aplicação de alterações do estado dhcp.</span><span class="sxs-lookup"><span data-stu-id="2b28c-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="2b28c-648">Os argumentos de entrada funciton de retorno são o índice de interface e o estado para o quais o Cliente DHCP passou a essa interface.</span><span class="sxs-lookup"><span data-stu-id="2b28c-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="2b28c-649">Para obter mais informações sobre as funções de mudança de estado, consulte *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="2b28c-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-650">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-650">Input Parameters</span></span>

- <span data-ttu-id="2b28c-651">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-652">**dhcp_interface_state_change_notify**: Ponteiro da função de chamada de aplicação</span><span class="sxs-lookup"><span data-stu-id="2b28c-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-653">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-653">Return Values</span></span>

- <span data-ttu-id="2b28c-654">**NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="2b28c-655">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-656">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-656">Allowed From</span></span>

<span data-ttu-id="2b28c-657">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="2b28c-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-658">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="2b28c-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="2b28c-659">nx_dhcp_stop</span></span>

<span data-ttu-id="2b28c-660">Para o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-661">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-662">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-662">Description</span></span>

<span data-ttu-id="2b28c-663">Este serviço impede o processamento de DHCP em todas as interfaces que iniciaram o processamento do DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="2b28c-664">Se não houver interfaces a processar o DHCP, este serviço suspenderá a linha do Cliente DHCP e inativará o temporizador do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="2b28c-665">Para parar o DHCP numa interface específica se várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_stop.*</span><span class="sxs-lookup"><span data-stu-id="2b28c-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-666">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-666">Input Parameters</span></span>

- <span data-ttu-id="2b28c-667">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-668">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-668">Return Values</span></span>

- <span data-ttu-id="2b28c-669">**NX_SUCCESS**: (0x00) paragem bem sucedida do DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="2b28c-670">**NX_DHCP_NOT_STARTED**: (0x96) A instância dhcp não começou.</span><span class="sxs-lookup"><span data-stu-id="2b28c-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="2b28c-671">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-672">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-673">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-673">Allowed From</span></span>

<span data-ttu-id="2b28c-674">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-675">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="2b28c-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="2b28c-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="2b28c-677">Parar o processamento do DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-678">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="2b28c-679">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-679">Description</span></span>

<span data-ttu-id="2b28c-680">Este serviço impede o processamento de DHCP na interface especificada se o DHCP já estiver iniciado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="2b28c-681">Se não houver outras interfaces a funcionar dhCP, o fio e o temporizador DHCP estão suspensos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-682">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-682">Input Parameters</span></span>

- <span data-ttu-id="2b28c-683">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-684">**Interface_index**: Interface para parar o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-685">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-685">Return Values</span></span>

- <span data-ttu-id="2b28c-686">**NX_SUCCESS**: (0x00) paragem bem sucedida do DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="2b28c-687">**NX_DHCP_NOT_STARTED**: (0x96) o DHCP não começou.</span><span class="sxs-lookup"><span data-stu-id="2b28c-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="2b28c-688">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-689">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2b28c-690">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-691">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-691">Allowed From</span></span>

<span data-ttu-id="2b28c-692">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-693">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="2b28c-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="2b28c-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="2b28c-695">Recupere uma opção DHCP da última resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="2b28c-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-696">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="2b28c-697">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-697">Description</span></span>

<span data-ttu-id="2b28c-698">Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="2b28c-699">Se for bem sucedido, os dados de opção são copiados para o tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-700">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-700">Input Parameters</span></span>

- <span data-ttu-id="2b28c-701">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="2b28c-702">**request_option**: Opção DHCP, conforme especificado pelos RFCs.</span><span class="sxs-lookup"><span data-stu-id="2b28c-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="2b28c-703">Consulte a opção NX_DHCP_OPTION em *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="2b28c-704">**destination_ptr**: Ponte para o destino para a cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="2b28c-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="2b28c-705">**destination_size**: Ponte para o tamanho do destino e no regresso, o destino para colocar o número de bytes devolvidos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-706">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-706">Return Values</span></span>

- <span data-ttu-id="2b28c-707">**NX_SUCCESS:**(0x00) Recuperação de opções bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="2b28c-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="2b28c-708">**NX_DHCP_NOT_BOUND:**(0x94) O Cliente DHCP não está vinculado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="2b28c-709">**NX_DHCP_NO_INTERFACES_ENABLED:**(0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="2b28c-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="2b28c-710">**NX_DHCP_DEST_TO_SMALL:**(0x95) O destino é demasiado pequeno para manter a resposta.</span><span class="sxs-lookup"><span data-stu-id="2b28c-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="2b28c-711">**NX_DHCP_PARSE_ERROR**: (0x97) Opção não encontrada na resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="2b28c-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="2b28c-712">NX_PTR_ERROR: (0x16) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="2b28c-713">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-714">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-714">Allowed From</span></span>

<span data-ttu-id="2b28c-715">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-716">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="2b28c-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="2b28c-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="2b28c-718">Recupere uma opção DHCP da última resposta do servidor na interface especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-719">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="2b28c-720">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-720">Description</span></span>

<span data-ttu-id="2b28c-721">Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na interface especificada, se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="2b28c-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="2b28c-722">Se for bem sucedido, os dados de opção são copiados para o tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-723">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-723">Input Parameters</span></span>

- <span data-ttu-id="2b28c-724">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-725">**Interface_index**: Índice para recuperar a opção especificada</span><span class="sxs-lookup"><span data-stu-id="2b28c-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="2b28c-726">**request_option**: Opção DHCP, conforme especificado pelos RFCs.</span><span class="sxs-lookup"><span data-stu-id="2b28c-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="2b28c-727">Consulte a opção NX_DHCP_OPTION: em *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="2b28c-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="2b28c-728">**destination_ptr**: Ponte para o destino para a cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="2b28c-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="2b28c-729">**destination_size**: Ponte para o tamanho do destino e no regresso, o destino para colocar o número de bytes devolvidos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-730">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-730">Return Values</span></span>

- <span data-ttu-id="2b28c-731">**NX_SUCCESS:**(0x00) Recuperação de opções bem sucedidas.</span><span class="sxs-lookup"><span data-stu-id="2b28c-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="2b28c-732">**NX_DHCP_NOT_BOUND:**(0x94) endereço IP não atribuído</span><span class="sxs-lookup"><span data-stu-id="2b28c-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="2b28c-733">**NX_DHCP_DEST_TO_SMALL:**(0x95) Tampão é muito pequeno</span><span class="sxs-lookup"><span data-stu-id="2b28c-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="2b28c-734">**NX_DHCP_PARSE_ERROR**: (0x97) A opção DHCP não encontrada na resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="2b28c-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="2b28c-735">NX_PTR_ERROR: (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="2b28c-736">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2b28c-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2b28c-737">NX_INVALID_INTERFACE: (0x4C) Interface de rede inválida</span><span class="sxs-lookup"><span data-stu-id="2b28c-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-738">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-738">Allowed From</span></span>

<span data-ttu-id="2b28c-739">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-740">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="2b28c-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="2b28c-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="2b28c-742">Converter quatro bytes para ULONG</span><span class="sxs-lookup"><span data-stu-id="2b28c-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-743">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="2b28c-744">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-744">Description</span></span>

<span data-ttu-id="2b28c-745">Este serviço converte os quatro caracteres apontados por "option_string_ptr" num valor longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="2b28c-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="2b28c-746">É especialmente útil quando os endereços IP são</span><span class="sxs-lookup"><span data-stu-id="2b28c-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="2b28c-747">presente.</span><span class="sxs-lookup"><span data-stu-id="2b28c-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-748">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-748">Input Parameters</span></span>

- <span data-ttu-id="2b28c-749">**option_string_ptr**: Ponteiro para a cadeia de opções previamente recuperada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-750">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-750">Return Values</span></span>

- <span data-ttu-id="2b28c-751">**Valor**: Valor dos quatro primeiros bytes.</span><span class="sxs-lookup"><span data-stu-id="2b28c-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-752">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-752">Allowed From</span></span>

<span data-ttu-id="2b28c-753">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-754">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="2b28c-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="2b28c-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="2b28c-756">Desace a função de retorno definido para adicionar opções fornecidas pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="2b28c-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="2b28c-757">Prototype</span><span class="sxs-lookup"><span data-stu-id="2b28c-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="2b28c-758">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b28c-758">Description</span></span>

<span data-ttu-id="2b28c-759">Este serviço regista a função de retorno especificado para adicionar opções fornecidas pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="2b28c-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="2b28c-760">Se a função de retorno especificado, as aplicações podem adicionar opções fornecidas pelo utilizador no pacote iface_index e message_type.</span><span class="sxs-lookup"><span data-stu-id="2b28c-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="2b28c-761">Na rotina do utilizador.</span><span class="sxs-lookup"><span data-stu-id="2b28c-761">In user’s routine.</span></span> <span data-ttu-id="2b28c-762">As aplicações devem seguir o formato de opções DHCP quando adicionar opções fornecidas pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="2b28c-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="2b28c-763">O tamanho total das opções do utilizador deve ser menor ou igual a user_option_length e atualizar o user_option_length como comprimento real das opções.</span><span class="sxs-lookup"><span data-stu-id="2b28c-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="2b28c-764">Volte NX_TRUE se adicionar opções com sucesso, caso contrário, volte NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="2b28c-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b28c-765">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2b28c-765">Input Parameters</span></span>

- <span data-ttu-id="2b28c-766">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2b28c-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="2b28c-767">**dhcp_user_option_add**: Função de adicionar a opção do utilizador ao utilizador.</span><span class="sxs-lookup"><span data-stu-id="2b28c-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="2b28c-768">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2b28c-768">Return Values</span></span>

- <span data-ttu-id="2b28c-769">**NX_SUCCESS**: (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="2b28c-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="2b28c-770">NX_PTR_ERROR: (0x16) Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="2b28c-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b28c-771">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2b28c-771">Allowed From</span></span>

<span data-ttu-id="2b28c-772">Fios</span><span class="sxs-lookup"><span data-stu-id="2b28c-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2b28c-773">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b28c-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

