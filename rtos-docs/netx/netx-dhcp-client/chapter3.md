---
title: Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX DHCP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826797"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="6d58f-103">Capítulo 3 - Descrição dos serviços de clientes Azure RTOS NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="6d58f-104">Este capítulo contém uma descrição de todos os serviços Azure RTOS NetX DHCP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="6d58f-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="6d58f-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="6d58f-106">**nx_dhcp_create**: *Criar uma instância DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="6d58f-107">**nx_dhcp_clear_broadcast_flag**: Clara bandeira de transmissão nas mensagens do Cliente</span><span class="sxs-lookup"><span data-stu-id="6d58f-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="6d58f-108">**nx_dhcp_delete**: *Eliminar uma instância DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="6d58f-109">**nx_dhcp_decline**: Enviar *mensagem de recusa para o servidor*</span><span class="sxs-lookup"><span data-stu-id="6d58f-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="6d58f-110">**nx_dhcp_force_renew**: *Enviar mensagem de renovação de força*</span><span class="sxs-lookup"><span data-stu-id="6d58f-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="6d58f-111">**nx_dhcp_packet_pool_set**: *Definir a piscina de pacotes do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="6d58f-112">**nx_dhcp_release**: Enviar *mensagem de desbloqueio para o servidor*</span><span class="sxs-lookup"><span data-stu-id="6d58f-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="6d58f-113">**nx_dhcp_reinitialize**: *Claros parâmetros da rede de clientes DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="6d58f-114">**nx_dhcp_request_client_ip**: *Especifique um endereço IP específico*</span><span class="sxs-lookup"><span data-stu-id="6d58f-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="6d58f-115">**nx_dhcp_send_request**: *Enviar mensagem DHCP para o servidor*</span><span class="sxs-lookup"><span data-stu-id="6d58f-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="6d58f-116">**nx_dhcp_server_address_get**: *Recuperar o endereço do servidor DHCP do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="6d58f-117">**nx_dhcp_set_interface_index**: *Especifique a interface da rede do Cliente*</span><span class="sxs-lookup"><span data-stu-id="6d58f-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="6d58f-118">**nx_dhcp_start**: *Iniciar o processamento do DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="6d58f-119">**nx_dhcp_state_change_notify**: *Notificar a aplicação da alteração do estado do DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="6d58f-120">**nx_dhcp_stop**: *Parar o processamento do DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="6d58f-121">**nx_dhcp_user_option_retrieve**: *Recuperar a opção DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="6d58f-122">**nx_dhcp_user_option_convert**: *Converter quatro bytes para ULONG*</span><span class="sxs-lookup"><span data-stu-id="6d58f-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="6d58f-123">Serviços de clientes dHCP específicos da interface:</span><span class="sxs-lookup"><span data-stu-id="6d58f-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="6d58f-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clara bandeira de transmissão nas mensagens do Cliente na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="6d58f-125">**nx_dhcp_interface_enable**: *Permitir que a interface execute o DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="6d58f-126">**nx_dhcp_interface_disable**: *Desative a interface para executar o DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="6d58f-127">**nx_dhcp_interface_decline**: *Enviar mensagem de declínio para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="6d58f-128">**nx_dhcp_interface_force_renew**: *Enviar uma mensagem de renovação de força na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="6d58f-129">**nx_dhcp_interface_reinitialize**: *Limpar os parâmetros da rede de clientes DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="6d58f-130">**nx_dhcp_interface_release**: *Enviar mensagem de desbloqueio para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="6d58f-131">**nx_dhcp_interface_request_client_ip**: *Especifique um endereço IP específico na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="6d58f-132">**nx_dhcp_interface_send_request**: *Enviar mensagem DHCP para o servidor na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="6d58f-133">**nx_dhcp_interface_server_address_get**: *Obtenha o endereço IP do servidor DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="6d58f-134">**nx_dhcp_interface_start**: *Inicie o processamento do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="6d58f-135">**nx_dhcp_interface_stop**: *Parar o processamento do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="6d58f-136">**nx_dhcp_interface_state_change_notify**: *Desa esta medida de chamada quando o estado de DHCP mudar na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="6d58f-137">**nx_dhcp_interface_user_option_retrieve**: *Recuperar a opção DHCP especificada na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="6d58f-138">Serviços ao cliente DAHCP se NX_DHCP_CLIENT_RESORE_STATE estiver definido:</span><span class="sxs-lookup"><span data-stu-id="6d58f-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="6d58f-139">**nx_dhcp_resume**: *Retomar estado de cliente DHCP previamente estabelecido*</span><span class="sxs-lookup"><span data-stu-id="6d58f-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="6d58f-140">**nx_dhcp_suspend**: *Suspender o processamento do estado do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="6d58f-141">**nx_dhcp_client_get_record**: *Criar um registo do estado do cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="6d58f-142">**nx_dhcp_client_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="6d58f-143">**nx_dhcp_client_update_time_remaining**: *Atualizar o tempo que resta no estado atual do DHCP*</span><span class="sxs-lookup"><span data-stu-id="6d58f-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="6d58f-144">Serviços específicos do cliente DHCP de interface se NX_DHCP_CLIENT_RESORE_STATE for definido:</span><span class="sxs-lookup"><span data-stu-id="6d58f-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="6d58f-145">**nx_dhcp_client_interface_get_record**: *Criar um registo do estado do Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="6d58f-146">**nx_dhcp_client_interface_restore_record**: *Restaurar um registo previamente guardado para o Cliente DHCP na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="6d58f-147">**nx_dhcp_client_interface_update_time_remaining**: *Atualizar o tempo restante no estado dhcp atual na interface especificada*</span><span class="sxs-lookup"><span data-stu-id="6d58f-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="6d58f-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="6d58f-148">nx_dhcp_create</span></span>

<span data-ttu-id="6d58f-149">Criar uma instância DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-150">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-151">Description</span></span>

<span data-ttu-id="6d58f-152">Este serviço cria uma instância DHCP para a instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="6d58f-153">Por predefinição, a interface primária está ativada para executar o DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="6d58f-154">A entrada de nomes, embora não utilizada na implementação NetX do Cliente DHCP, deve seguir os critérios RFC 1035 para os nomes dos anfitriões.</span><span class="sxs-lookup"><span data-stu-id="6d58f-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="6d58f-155">O comprimento total não deve exceder 255 caracteres, as etiquetas separadas por pontos devem começar com uma letra, e terminar com uma letra ou número, e podem conter hífens, mas nenhum outro carácter não alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="6d58f-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="6d58f-156">Se a aplicação quiser executar a DHCP outra interface registada com a instância IP (utilizando *nx_ip_interface_attach),* a aplicação pode chamar *nx_dhcp_set_interface_index* para executar o DHCP apenas nessa interface, ou *nx_dhcp_interface_enable* para executar DHCP nessa interface também.</span><span class="sxs-lookup"><span data-stu-id="6d58f-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="6d58f-157">Consulte a descrição destes serviços para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="6d58f-158">A aplicação deve certificar-se de que a carga útil do pacote do cliente DHCP pode suportar o tamanho mínimo da mensagem DHCP especificado pela Secção 2 (548 bytes de dados de mensagens DHCP mais cabeçalhos de estrutura de UDP, IP e rede física).</span><span class="sxs-lookup"><span data-stu-id="6d58f-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-159">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-159">Input Parameters</span></span>

- <span data-ttu-id="6d58f-160">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="6d58f-161">**ip_ptr** Ponteiro para instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="6d58f-162">**name_ptr** Ponteiro para o nome de anfitrião para a instância DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-163">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-163">Return Values</span></span>

- <span data-ttu-id="6d58f-164">**NX_SUCCESS** (0x00) DHCP bem sucedido criar</span><span class="sxs-lookup"><span data-stu-id="6d58f-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="6d58f-165">**NX_DHCP_INVALID_NAME** (0xA8) Nome de anfitrião inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="6d58f-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Carga útil demasiado pequena para mensagem DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="6d58f-167">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-168">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-168">Allowed From</span></span>

<span data-ttu-id="6d58f-169">**Fios,** Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="6d58f-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="6d58f-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="6d58f-172">Permitir que a interface especificada execute o DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d58f-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-174">Description</span></span>

<span data-ttu-id="6d58f-175">Este serviço permite a interface especificada para a execução do DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="6d58f-176">Por predefinição, a interface primária está ativada para o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="6d58f-177">Neste momento, o DHCP pode ser iniciado nesta interface, quer chamando *nx_dhcp_interface_start,* quer para iniciar o DHCP em todas as interfaces ativadas *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="6d58f-178">Note que a aplicação deve primeiro registar esta interface com a instância IP, utilizando *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="6d58f-179">Além disso, deve existir um 'registo' de interface do Cliente DHCP disponível para adicionar esta interface à lista de interfaces ativadas.</span><span class="sxs-lookup"><span data-stu-id="6d58f-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="6d58f-180">Por predefinição, NX_DHCP_CLIENT_MAX_RECORDS é definido para 1.</span><span class="sxs-lookup"><span data-stu-id="6d58f-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="6d58f-181">Desa esta opção para o número máximo de interfaces que se espera que sejam executadas em simultâneo com o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="6d58f-182">Normalmente, NX_DHCP_CLIENT_MAX_RECORDS será igual a NX_MAX_PHYSICAL_INTERFACES; no entanto, se um dispositivo tiver mais interfaces físicas do que espera executar o Cliente DHCP, pode guardar a memória definindo NX_DHCP_CLIENT_MAX_RECORDS para menos do que esse número.</span><span class="sxs-lookup"><span data-stu-id="6d58f-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="6d58f-183">Não há um para um mapeamento de interfaces físicas com registos de interface do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="6d58f-184">A diferença entre este serviço e *nx_dhcp_set_interface_index* é que este último define apenas uma interface única para executar DHCP, enquanto este serviço simplesmente adiciona a interface especificada à lista de interfaces do Cliente ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6d58f-185">Para desativar uma interface para DHCP, a aplicação pode ligar para o serviço *nx_dhcp_interface_disable.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-186">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-186">Input Parameters</span></span>

- <span data-ttu-id="6d58f-187">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-188">**interface_index** Índice de interface para ativar DHCP em</span><span class="sxs-lookup"><span data-stu-id="6d58f-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-189">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-189">Return Values</span></span>

- <span data-ttu-id="6d58f-190">**NX_SUCCESS** (0x00) DHCP bem sucedido</span><span class="sxs-lookup"><span data-stu-id="6d58f-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="6d58f-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Não há registo disponível para outra Interface a ser ativada para o DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-192">**Interface NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-193">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-194">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-195">Allowed From</span></span>

<span data-ttu-id="6d58f-196">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="6d58f-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="6d58f-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="6d58f-199">Desative a interface especificada para executar o DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d58f-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-201">Description</span></span>

<span data-ttu-id="6d58f-202">Este serviço desativa a interface especificada para a execução do DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="6d58f-203">Reinicia o Cliente DHCP nesta interface.</span><span class="sxs-lookup"><span data-stu-id="6d58f-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="6d58f-204">Para reiniciar o Cliente DHCP, a aplicação deve voltar a ativar a interface utilizando *nx_dhcp_interface_enable* e reiniciar o DHCP chamando *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-205">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-205">Input Parameters</span></span>

- <span data-ttu-id="6d58f-206">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-207">**interface_index** Índice de interface para desativar o DHCP em</span><span class="sxs-lookup"><span data-stu-id="6d58f-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-208">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-208">Return Values</span></span>

- <span data-ttu-id="6d58f-209">**NX_SUCCESS** (0x00) DHCP bem sucedido criar</span><span class="sxs-lookup"><span data-stu-id="6d58f-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="6d58f-210">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-211">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-212">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="6d58f-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="6d58f-213">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-214">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-214">Allowed From</span></span>

<span data-ttu-id="6d58f-215">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="6d58f-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="6d58f-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="6d58f-218">Definir a bandeira de transmissão DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="6d58f-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-220">Description</span></span>

<span data-ttu-id="6d58f-221">Este serviço define ou limpa a bandeira de transmissão o cabeçalho de mensagem DHCP para todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6d58f-222">Para algumas mensagens DHCP (por exemplo, DISCOVER) a bandeira de transmissão está definida para ser transmitida porque o Cliente não tem um endereço IP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="6d58f-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="6d58f-223">__clear_flag__</span></span>


- <span data-ttu-id="6d58f-224">**NX_TRUE** bandeira de emissão é apurada (pedido de resposta unicast)</span><span class="sxs-lookup"><span data-stu-id="6d58f-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="6d58f-225">**NX_FALSE** bandeira de transmissão é definida (pedido de resposta de transmissão)</span><span class="sxs-lookup"><span data-stu-id="6d58f-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="6d58f-226">Este serviço destina-se a Clientes DHCP que devem passar por um router para chegar ao Servidor DHCP, onde o router rejeita o encaminhamento de mensagens de transmissão.</span><span class="sxs-lookup"><span data-stu-id="6d58f-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-227">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-227">Input Parameters</span></span>

- <span data-ttu-id="6d58f-228">**dhcp_ptr** Ponteiro para bloco de controlo DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="6d58f-229">**clear_flag** Valor para definir a bandeira de transmissão para</span><span class="sxs-lookup"><span data-stu-id="6d58f-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-230">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-230">Return Values</span></span>

- <span data-ttu-id="6d58f-231">**NX_SUCCESS** (0x00) atualizou com sucesso a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="6d58f-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="6d58f-232">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-233">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="6d58f-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-234">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-234">Allowed From</span></span>

<span data-ttu-id="6d58f-235">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="6d58f-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="6d58f-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="6d58f-238">Desmarcar ou limpar a bandeira de transmissão na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="6d58f-240">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-240">Description</span></span>

<span data-ttu-id="6d58f-241">Este serviço permite que a aplicação do anfitrião do cliente DHCP desempecifique ou limpe a bandeira de transmissão nas mensagens do Cliente DHCP para o Servidor DHCP na interface especificada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="6d58f-242">Para mais detalhes consulte **nx_dhcp_clear_broadcast_flag**</span><span class="sxs-lookup"><span data-stu-id="6d58f-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-243">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-243">Input Parameters</span></span>

- <span data-ttu-id="6d58f-244">**dhcp_ptr** Ponteiro para bloco de controlo DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="6d58f-245">**interface_index** Índice de interface para definir a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="6d58f-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="6d58f-246">**clear_flag** Valor para definir a bandeira de transmissão para</span><span class="sxs-lookup"><span data-stu-id="6d58f-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-247">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-247">Return Values</span></span>

- <span data-ttu-id="6d58f-248">**NX_SUCCESS** (0x00) atualizou com sucesso a bandeira de transmissão</span><span class="sxs-lookup"><span data-stu-id="6d58f-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="6d58f-249">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-250">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-251">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-252">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-252">Allowed From</span></span>

<span data-ttu-id="6d58f-253">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-254">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="6d58f-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="6d58f-255">nx_dhcp_delete</span></span>

<span data-ttu-id="6d58f-256">Eliminar uma instância DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-257">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-258">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-258">Description</span></span>

<span data-ttu-id="6d58f-259">Este serviço elimina uma instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-260">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-260">Input Parameters</span></span>

- <span data-ttu-id="6d58f-261">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-262">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-262">Return Values</span></span>

- <span data-ttu-id="6d58f-263">**NX_SUCCESS** (0x00) DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="6d58f-264">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-265">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-266">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-266">Allowed From</span></span>

<span data-ttu-id="6d58f-267">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-268">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="6d58f-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="6d58f-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="6d58f-270">Enviar uma mensagem de renovação de força</span><span class="sxs-lookup"><span data-stu-id="6d58f-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d58f-271">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-272">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-272">Description</span></span>

<span data-ttu-id="6d58f-273">Este serviço permite que a aplicação do anfitrião envie uma mensagem de renovação de força em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6d58f-274">O Cliente DHCP deve estar num estado vinculado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="6d58f-275">Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.</span><span class="sxs-lookup"><span data-stu-id="6d58f-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="6d58f-276">Para enviar uma renovação de força numa interface específica quando várias interfaces estiverem habilitados a DHCP, utilize *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-277">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-277">Input Parameters</span></span>

- <span data-ttu-id="6d58f-278">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-279">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-279">Return Values</span></span>

- <span data-ttu-id="6d58f-280">**NX_SUCCESS** (0x00) enviaram com sucesso a renovação da força.</span><span class="sxs-lookup"><span data-stu-id="6d58f-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="6d58f-281">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-282">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-283">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-283">Allowed From</span></span>

<span data-ttu-id="6d58f-284">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-285">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="6d58f-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="6d58f-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="6d58f-287">Envie uma mensagem de renovação de força na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-289">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-289">Description</span></span>

<span data-ttu-id="6d58f-290">Este serviço permite que a aplicação anfitriã envie uma mensagem de renovação de força na interface de entrada, desde que essa interface tenha sido ativada para DHCP (ver *nx_dhcp_interface_enable).*</span><span class="sxs-lookup"><span data-stu-id="6d58f-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6d58f-291">O Cliente DHCP na interface especificada deve estar num estado VINculado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="6d58f-292">Esta função define o estado para RENOVAR de modo a que o Cliente DHCP tente renovar antes que o tempo limite T1 expire.</span><span class="sxs-lookup"><span data-stu-id="6d58f-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-293">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-293">Input Parameters</span></span>

- <span data-ttu-id="6d58f-294">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-295">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-295">Return Values</span></span>

- <span data-ttu-id="6d58f-296">**NX_SUCCESS** (0x00) enviaram com sucesso a renovação da força.</span><span class="sxs-lookup"><span data-stu-id="6d58f-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="6d58f-297">**Interface NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-298">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-299">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-300">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-300">Allowed From</span></span>

<span data-ttu-id="6d58f-301">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-302">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="6d58f-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="6d58f-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="6d58f-304">Desa estaladiço do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-305">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-306">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-306">Description</span></span>

<span data-ttu-id="6d58f-307">Este serviço permite que a aplicação crie o pool de pacotes do Cliente DHCP, passando um ponteiro para um pacote de pacotes previamente criado nesta chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="6d58f-308">Para utilizar esta funcionalidade, a aplicação do anfitrião deve definir NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="6d58f-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="6d58f-309">Quando definido, o serviço *nx_dhcp_create* não criará a piscina de pacotes do Cliente.</span><span class="sxs-lookup"><span data-stu-id="6d58f-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="6d58f-310">Note que a aplicação é recomendada para usar os valores padrão para a carga de pacote do cliente DHCP, definida como NX_DHCP_PACKET_PAYLOAD em *nx_dhcp.h* ao criar o pool de pacotes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-311">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-311">Input Parameters</span></span>

- <span data-ttu-id="6d58f-312">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-313">**packet_pool_ptr** Ponteiro para piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="6d58f-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-314">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-314">Return Values</span></span>

- <span data-ttu-id="6d58f-315">**NX_SUCCESS** (0x00) DHCP Pacote de pacotes de cliente está definido</span><span class="sxs-lookup"><span data-stu-id="6d58f-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="6d58f-316">**NX_NOT_ENABLED** (0x14) Serviço não está ativado</span><span class="sxs-lookup"><span data-stu-id="6d58f-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="6d58f-317">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-318">NX_DHCP_INVALID_PAYLOAD (0x9C) A carga útil é muito pequena</span><span class="sxs-lookup"><span data-stu-id="6d58f-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-319">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-319">Allowed From</span></span>

<span data-ttu-id="6d58f-320">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="6d58f-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-321">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="6d58f-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="6d58f-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="6d58f-323">Definir endereço IP solicitado para instância DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-324">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="6d58f-325">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-325">Description</span></span>

<span data-ttu-id="6d58f-326">Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na primeira interface ativada para DHCP no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="6d58f-327">Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="6d58f-328">Para definir o pedido de um IP específico para mensagens DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_request_client_ip.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-329">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-329">Input Parameters</span></span>

- <span data-ttu-id="6d58f-330">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-331">**client_ip_address** Endereço IP a pedido do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="6d58f-332">**skip_discover_message** Se for verdade, o Cliente DHCP envia mensagem de pedido</span><span class="sxs-lookup"><span data-stu-id="6d58f-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="6d58f-333">Se for falso, envia a mensagem Discover.</span><span class="sxs-lookup"><span data-stu-id="6d58f-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-334">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-334">Return Values</span></span>

- <span data-ttu-id="6d58f-335">**NX_SUCCESS** (0x00) Endereço IP solicitado está definido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="6d58f-336">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-337">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-338">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="6d58f-339">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-339">Allowed From</span></span>

<span data-ttu-id="6d58f-340">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-341">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="6d58f-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="6d58f-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="6d58f-343">Definir endereço IP solicitado para instância DHCP em interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-344">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="6d58f-345">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-345">Description</span></span>

<span data-ttu-id="6d58f-346">Este serviço define o endereço IP para o Cliente DHCP solicitar a partir do Servidor DHCP na interface especificada, se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="6d58f-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6d58f-347">Se a bandeira *skip_discover_message* estiver definida, o Cliente DHCP ignora a mensagem Discover e envia uma mensagem De pedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-348">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-348">Input Parameters</span></span>

- <span data-ttu-id="6d58f-349">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="6d58f-350">**Interface_index** Índice de interface para solicitar endereço IP em</span><span class="sxs-lookup"><span data-stu-id="6d58f-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="6d58f-351">**client_ip_address** Endereço IP a pedido do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="6d58f-352">**skip_discover_message** Se for verdade, o Cliente DHCP envia mensagem de pedido; senão envia a mensagem Discover.</span><span class="sxs-lookup"><span data-stu-id="6d58f-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-353">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-353">Return Values</span></span>

- <span data-ttu-id="6d58f-354">**NX_SUCCESS** (0x00) Endereço IP solicitado está definido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="6d58f-355">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-356">NX_PTR_ERROR (0x16) Inválido IP ou ponteiro DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="6d58f-357">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="6d58f-358">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-358">Allowed From</span></span>

<span data-ttu-id="6d58f-359">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-360">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="6d58f-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="6d58f-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="6d58f-362">Limpe os parâmetros da rede de clientes DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d58f-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-364">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-364">Description</span></span>

<span data-ttu-id="6d58f-365">Este serviço limpa os parâmetros da rede de aplicações do anfitrião (endereço IP, endereço de rede e máscara de rede) e limpa o estado do Cliente DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6d58f-366">É utilizado em combinação com *nx_dhcp_stop* e *nx_dhcp_start* para "reiniciar" a máquina estatal DHCP:</span><span class="sxs-lookup"><span data-stu-id="6d58f-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="6d58f-367">nx_dhcp_stop(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="6d58f-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="6d58f-368">nx_dhcp_reinitialize(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="6d58f-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="6d58f-369">nx_dhcp_start(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="6d58f-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="6d58f-370">Para reinitializar o Cliente DHCP numa interface específica quando várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_reinitialize.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-371">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-371">Input Parameters</span></span>

- <span data-ttu-id="6d58f-372">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-373">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-373">Return Values</span></span>

- <span data-ttu-id="6d58f-374">**DHCP NX_SUCCESS** (0x00) reinicializou com sucesso</span><span class="sxs-lookup"><span data-stu-id="6d58f-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="6d58f-375">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-376">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-376">Allowed From</span></span>

<span data-ttu-id="6d58f-377">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-378">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="6d58f-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="6d58f-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="6d58f-380">Limpe os parâmetros da rede de clientes DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="6d58f-381">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-382">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-382">Description</span></span>

<span data-ttu-id="6d58f-383">Este serviço limpa os parâmetros de rede (endereço IP, endereço de rede e máscara de rede) na interface especificada se essa interface estiver ativada para DHCP (ver *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="6d58f-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="6d58f-384">Consulte *nx_dhcp_reinitialize* para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-385">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-385">Input Parameters</span></span>

- <span data-ttu-id="6d58f-386">**dhcp_ptr** Ponteiro para instância DHCP previamente criada</span><span class="sxs-lookup"><span data-stu-id="6d58f-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="6d58f-387">**interface_index** Índice de interface para reinitializar.</span><span class="sxs-lookup"><span data-stu-id="6d58f-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-388">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-388">Return Values</span></span>

- <span data-ttu-id="6d58f-389">**interface NX_SUCCESS** (0x00) reinicializada com sucesso</span><span class="sxs-lookup"><span data-stu-id="6d58f-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="6d58f-390">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-391">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-392">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="6d58f-393">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-394">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-394">Allowed From</span></span>

<span data-ttu-id="6d58f-395">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-396">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="6d58f-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="6d58f-397">nx_dhcp_release</span></span>

<span data-ttu-id="6d58f-398">Liberação de endereço IP alugado</span><span class="sxs-lookup"><span data-stu-id="6d58f-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-400">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-400">Description</span></span>

<span data-ttu-id="6d58f-401">Este serviço liberta o endereço IP obtido a partir de um servidor DHCP enviando a mensagem RELEASE para esse servidor.</span><span class="sxs-lookup"><span data-stu-id="6d58f-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="6d58f-402">Em seguida, reinicia o cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="6d58f-403">Este serviço é aplicado a todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="6d58f-404">A aplicação pode reiniciar o Cliente DHCP chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="6d58f-405">Para libertar um endereço de volta para o servidor DHCP numa interface específica, utilize o serviço *nx_dhcp_interface_release*</span><span class="sxs-lookup"><span data-stu-id="6d58f-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-406">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-406">Input Parameters</span></span>

- <span data-ttu-id="6d58f-407">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-408">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-408">Return Values</span></span>

- <span data-ttu-id="6d58f-409">**NX_SUCCESS** (0x00) Lançamento DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="6d58f-410">**NX_DHCP_NOT_BOUND** (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="6d58f-411">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-412">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-413">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-413">Allowed From</span></span>

<span data-ttu-id="6d58f-414">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-415">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="6d58f-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="6d58f-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="6d58f-417">Liberar endereço IP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-418">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-419">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-419">Description</span></span>

<span data-ttu-id="6d58f-420">Este serviço liberta o endereço IP obtido a partir de um servidor DHCP na interface especificada e reinicia o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="6d58f-421">O Cliente DHCP pode ser reiniciado chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-422">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-422">Input Parameters</span></span>

- <span data-ttu-id="6d58f-423">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-424">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-424">Return Values</span></span>

- <span data-ttu-id="6d58f-425">**NX_SUCCESS** (0x00) Lançamento DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="6d58f-426">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-427">**NX_DHCP_NOT_BOUND** (0x94) O endereço IP não foi arrendado, pelo que não pode ser lançado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="6d58f-428">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-429">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="6d58f-430">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-431">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-431">Allowed From</span></span>

<span data-ttu-id="6d58f-432">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-433">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="6d58f-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="6d58f-434">nx_dhcp_decline</span></span>

<span data-ttu-id="6d58f-435">Recuse o endereço IP do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-436">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-437">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-437">Description</span></span>

<span data-ttu-id="6d58f-438">Este serviço declina um endereço IP alugado a partir do servidor DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6d58f-439">Se NX_DHCP_CLIENT_ SEND_ ARP_PROBE estiver definido, o Cliente DHCP enviará uma mensagem DECLINE se detetar que o endereço IP já está a ser utilizado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="6d58f-440">Consulte **as sondas ARP** no Capítulo Um para obter mais informações sobre a configuração da sonda ARP no Cliente DhCP NetX.</span><span class="sxs-lookup"><span data-stu-id="6d58f-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="6d58f-441">A aplicação pode usar este serviço para recusar o seu endereço IP se descobrir que o endereço está a ser utilizado por outros meios.</span><span class="sxs-lookup"><span data-stu-id="6d58f-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="6d58f-442">Este serviço reinicia o Cliente DHCP para que possa ser reiniciado chamando *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-443">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-443">Input Parameters</span></span>

- <span data-ttu-id="6d58f-444">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-445">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-445">Return Values</span></span>

- <span data-ttu-id="6d58f-446">**NX_SUCCESS** (0x00) Declínio enviado com sucesso</span><span class="sxs-lookup"><span data-stu-id="6d58f-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="6d58f-447">**NX_DHCP_NOT_STARTED** (0x96) A instância do DHCP ainda não começou</span><span class="sxs-lookup"><span data-stu-id="6d58f-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="6d58f-448">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-449">NX_CALLER_ERROR (0x11) Inválido deste serviço</span><span class="sxs-lookup"><span data-stu-id="6d58f-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-450">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-450">Allowed From</span></span>

<span data-ttu-id="6d58f-451">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-452">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="6d58f-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="6d58f-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="6d58f-454">Recuse o endereço IP do Servidor DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-455">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-456">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-456">Description</span></span>

<span data-ttu-id="6d58f-457">Este serviço envia a mensagem DECLINar para o servidor para recusar um endereço IP atribuído pelo servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="6d58f-458">Também reinicia o Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="6d58f-459">Consulte *nx_dhcp_decline* para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-460">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-460">Input Parameters</span></span>

- <span data-ttu-id="6d58f-461">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-462">**Interface_index** Índice de interface para recusar endereço IP</span><span class="sxs-lookup"><span data-stu-id="6d58f-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-463">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-463">Return Values</span></span>

- <span data-ttu-id="6d58f-464">**NX_SUCCESS** (0x00) Mensagem de declínio do DHCP enviada</span><span class="sxs-lookup"><span data-stu-id="6d58f-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="6d58f-465">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP não vinculado</span><span class="sxs-lookup"><span data-stu-id="6d58f-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="6d58f-466">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-467">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-468">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="6d58f-469">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-470">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-470">Allowed From</span></span>

<span data-ttu-id="6d58f-471">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-472">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="6d58f-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="6d58f-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="6d58f-474">Enviar mensagem DHCP para o Servidor</span><span class="sxs-lookup"><span data-stu-id="6d58f-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-475">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="6d58f-476">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-476">Description</span></span>

<span data-ttu-id="6d58f-477">Este serviço envia a mensagem DHCP especificada para o servidor DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="6d58f-478">Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6d58f-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="6d58f-479">O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para enviar o tipo de mensagem INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="6d58f-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="6d58f-480">Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.</span><span class="sxs-lookup"><span data-stu-id="6d58f-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-481">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-481">Input Parameters</span></span>

- <span data-ttu-id="6d58f-482">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-483">**dhcp_message_type** Pedido de mensagem (definido em *nx_dhcp.h)*</span><span class="sxs-lookup"><span data-stu-id="6d58f-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-484">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-484">Return Values</span></span>

- <span data-ttu-id="6d58f-485">**Mensagem** DHCP NX_SUCCESS (0x00) enviada</span><span class="sxs-lookup"><span data-stu-id="6d58f-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="6d58f-486">**NX_DHCP_NOT_STARTED** (0x96) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="6d58f-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensagem inválida para enviar</span><span class="sxs-lookup"><span data-stu-id="6d58f-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="6d58f-488">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="6d58f-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-489">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-489">Allowed From</span></span>

<span data-ttu-id="6d58f-490">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-491">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="6d58f-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="6d58f-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="6d58f-493">Envie mensagem DHCP para o Servidor numa interface específica</span><span class="sxs-lookup"><span data-stu-id="6d58f-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-494">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="6d58f-495">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-495">Description</span></span>

<span data-ttu-id="6d58f-496">Este serviço envia uma mensagem para o servidor DHCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6d58f-497">Para enviar uma mensagem RELEASE ou DECLINar, a aplicação deve utilizar os serviços *nx_dhcp[_interface]_release*() ou *nx_dhcp_interface_decline()* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6d58f-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="6d58f-498">O Cliente DHCP deve ser iniciado a utilizar este serviço, exceto para o envio do tipo de mensagem DHCP INFORM REQUEST.</span><span class="sxs-lookup"><span data-stu-id="6d58f-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="6d58f-499">Este serviço não se destina à aplicação de anfitrião para 'conduzir' a máquina estatal dhcp Client.</span><span class="sxs-lookup"><span data-stu-id="6d58f-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-500">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-500">Input Parameters</span></span>

- <span data-ttu-id="6d58f-501">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="6d58f-502">**Interface_index** Índice de interface para enviar mensagem</span><span class="sxs-lookup"><span data-stu-id="6d58f-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="6d58f-503">**dhcp_message_type** Pedido de mensagem (definido em *nx_dhcp.h)*</span><span class="sxs-lookup"><span data-stu-id="6d58f-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-504">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-504">Return Values</span></span>

- <span data-ttu-id="6d58f-505">**Mensagem** DHCP NX_SUCCESS (0x00) enviada</span><span class="sxs-lookup"><span data-stu-id="6d58f-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="6d58f-506">**NX_DHCP_NOT_STARTED** (0x96) Índice de interface inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="6d58f-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Tipo de mensagem inválida para enviar</span><span class="sxs-lookup"><span data-stu-id="6d58f-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="6d58f-508">**Interface NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) não ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-509">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-510">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="6d58f-511">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-512">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-512">Allowed From</span></span>

<span data-ttu-id="6d58f-513">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-514">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="6d58f-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="6d58f-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="6d58f-516">Obtenha o endereço IP do servidor DHCP do cliente DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-517">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="6d58f-518">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-518">Description</span></span>

<span data-ttu-id="6d58f-519">Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na primeira interface ativada para DHCP encontrado no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="6d58f-520">O chamador só pode utilizar este serviço depois de o Cliente DHCP estar ligado a um endereço IP atribuído pelo Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="6d58f-521">A aplicação de anfitrião pode usar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar o *nx_dhcp_state_change_notify* e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="6d58f-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="6d58f-522">Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="6d58f-523">Para encontrar o servidor DHCP numa interface específica quando várias interfaces estiverem ativadas para o Cliente DHCP, utilize o serviço *nx_dhcp_interface_server_address_get*</span><span class="sxs-lookup"><span data-stu-id="6d58f-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-524">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-524">Input Parameters</span></span>

- <span data-ttu-id="6d58f-525">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="6d58f-526">**server_address** Ponteiro para o endereço IP do servidor</span><span class="sxs-lookup"><span data-stu-id="6d58f-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-527">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-527">Return Values</span></span>

- <span data-ttu-id="6d58f-528">**NX_SUCCESS** (0x00) endereço do servidor DHCP devolvido</span><span class="sxs-lookup"><span data-stu-id="6d58f-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="6d58f-529">NX_PTR_ERROR (0x16) Ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="6d58f-530">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-531">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-531">Allowed From</span></span>

<span data-ttu-id="6d58f-532">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-533">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="6d58f-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="6d58f-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="6d58f-535">Obtenha o endereço IP do servidor DHCP do cliente DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-536">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="6d58f-537">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-537">Description</span></span>

<span data-ttu-id="6d58f-538">Este serviço recupera o endereço IP do servidor DHCP do cliente DHCP dhCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6d58f-539">O Cliente DHCP deve estar no estado de Bound.</span><span class="sxs-lookup"><span data-stu-id="6d58f-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="6d58f-540">Depois de iniciar o Cliente DHCP nessa interface, a aplicação anfitriã pode utilizar o serviço *nx_ip_status_check* para verificar se o endereço IP está definido, ou pode usar a chamada de alteração do estado do cliente DHCP e consultar o estado do Cliente DHCP é NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="6d58f-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="6d58f-541">Consulte *nx_dhcp_state_change_notify* para obter mais detalhes sobre a definição da função de retorno de mudança de estado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-542">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-542">Input Parameters</span></span>

- <span data-ttu-id="6d58f-543">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="6d58f-544">**Interface_index** Índice de interface para obter endereço IP</span><span class="sxs-lookup"><span data-stu-id="6d58f-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="6d58f-545">**server_address** Ponteiro para o endereço IP do servidor</span><span class="sxs-lookup"><span data-stu-id="6d58f-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-546">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-546">Return Values</span></span>

- <span data-ttu-id="6d58f-547">**NX_SUCCESS** (0x00) endereço do servidor DHCP devolvido</span><span class="sxs-lookup"><span data-stu-id="6d58f-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="6d58f-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-549">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP não vinculado</span><span class="sxs-lookup"><span data-stu-id="6d58f-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="6d58f-550">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="6d58f-551">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="6d58f-552">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-553">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-553">Allowed From</span></span>

<span data-ttu-id="6d58f-554">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-555">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="6d58f-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="6d58f-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="6d58f-557">Definir interface de rede para a instância DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="6d58f-559">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-559">Description</span></span>

<span data-ttu-id="6d58f-560">Este serviço define a interface de rede para a instância DHCP ligar ao Servidor DHCP quando executa o Cliente DHCP configurado para uma única interface de rede.</span><span class="sxs-lookup"><span data-stu-id="6d58f-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="6d58f-561">Por predefinição, o Cliente DHCP funciona na interface primária.</span><span class="sxs-lookup"><span data-stu-id="6d58f-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="6d58f-562">Para executar o DHCP num serviço secundário, utilize este serviço para definir a interface secundária como interface do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="6d58f-563">O pedido deve registar previamente a interface especificada para a instância IP utilizando o serviço *nx_ip_interface_attach.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="6d58f-564">Note que este serviço se destina a aplicações que pretendam executar o Cliente DHCP em apenas uma interface.</span><span class="sxs-lookup"><span data-stu-id="6d58f-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="6d58f-565">Para executar DHCP em várias interfaces consulte *nx_dhcp_interface_enable* para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-566">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-566">Input Parameters</span></span>

- <span data-ttu-id="6d58f-567">**dhcp_ptr** Ponteiro para o bloco de controlo DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="6d58f-568">**índice** Índice da interface da rede de dispositivos</span><span class="sxs-lookup"><span data-stu-id="6d58f-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-569">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-569">Return Values</span></span>

- <span data-ttu-id="6d58f-570">**NX_SUCCESS** interface (0x00) está definida com sucesso.</span><span class="sxs-lookup"><span data-stu-id="6d58f-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="6d58f-571">**interface de** rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="6d58f-572">**Interface NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) ativada para DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) Não há registo disponível para outro</span><span class="sxs-lookup"><span data-stu-id="6d58f-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="6d58f-574">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido</span><span class="sxs-lookup"><span data-stu-id="6d58f-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-575">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-575">Allowed From</span></span>

<span data-ttu-id="6d58f-576">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-577">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="6d58f-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="6d58f-578">nx_dhcp_start</span></span>

<span data-ttu-id="6d58f-579">Iniciar o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-580">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-581">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-581">Description</span></span>

<span data-ttu-id="6d58f-582">Este serviço inicia o processamento de DHCP em todas as interfaces ativadas para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="6d58f-583">Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="6d58f-584">Para verificar quando a instância IP está ligada a um endereço IP na interface do Cliente DHCP, utilize *nx_ip_status_check* para ver confirmar se o endereço IP é válido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="6d58f-585">Se existirem outras interfaces já em execução dhCP, este serviço não irá afetá-los.</span><span class="sxs-lookup"><span data-stu-id="6d58f-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="6d58f-586">Para iniciar o DHCP numa interface específica quando várias interfaces estiverem ativadas, utilize o serviço *nx_dhcp_interface_start.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-587">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-587">Input Parameters</span></span>

- <span data-ttu-id="6d58f-588">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-589">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-589">Return Values</span></span>

- <span data-ttu-id="6d58f-590">**NX_SUCCESS** (0x00) Início dhcp bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="6d58f-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="6d58f-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="6d58f-592">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-593">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-594">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-594">Allowed From</span></span>

<span data-ttu-id="6d58f-595">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-596">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="6d58f-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="6d58f-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="6d58f-598">Iniciar o processamento do DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-599">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-600">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-600">Description</span></span>

<span data-ttu-id="6d58f-601">Este serviço inicia o processamento de DHCP na interface especificada se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6d58f-602">Consulte *nx_dhcp_interface_enable*() para obter mais detalhes sobre como ativar uma interface para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="6d58f-603">Por predefinição, a interface primária é ativada para DHCP quando a aplicação *nx_dhcp_create.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="6d58f-604">Se não houver outras interfaces a executar o Cliente DHCP este serviço iniciará/retomará a linha do Cliente DHCP e (re)ativar o temporizador do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="6d58f-605">A aplicação deve utilizar *nx_ip_status_check* para verificar se um endereço IP é obtido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-606">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-606">Input Parameters</span></span>

- <span data-ttu-id="6d58f-607">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-608">**Interface_index** Índice sobre o qual iniciar o DhCP Client</span><span class="sxs-lookup"><span data-stu-id="6d58f-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-609">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-609">Return Values</span></span>

- <span data-ttu-id="6d58f-610">**NX_SUCCESS** (0x00) Início dhcp bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="6d58f-611">**NX_DHCP_ALREADY_STARTED** (0x93) A instância do DHCP já foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="6d58f-612">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-613">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="6d58f-614">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-615">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-615">Allowed From</span></span>

<span data-ttu-id="6d58f-616">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-617">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="6d58f-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="6d58f-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="6d58f-619">Definir função de retorno de mudança de estado DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-620">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="6d58f-621">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-621">Description</span></span>

<span data-ttu-id="6d58f-622">Este serviço regista a função de retorno especificado dhcp_state_change_notify para notificar uma aplicação de alterações do estado dhcp.</span><span class="sxs-lookup"><span data-stu-id="6d58f-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="6d58f-623">A função de retorno fornece o estado em que o Cliente DHCP se transferiu.</span><span class="sxs-lookup"><span data-stu-id="6d58f-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="6d58f-624">Seguem-se os valores associados aos vários estados da DHCP:</span><span class="sxs-lookup"><span data-stu-id="6d58f-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="6d58f-625">Estado</span><span class="sxs-lookup"><span data-stu-id="6d58f-625">State</span></span>                             | <span data-ttu-id="6d58f-626">Valor</span><span class="sxs-lookup"><span data-stu-id="6d58f-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="6d58f-627">BOTA \_ DE ESTADO NX DHCP \_ \_</span><span class="sxs-lookup"><span data-stu-id="6d58f-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="6d58f-628">1</span><span class="sxs-lookup"><span data-stu-id="6d58f-628">1</span></span>     |
| <span data-ttu-id="6d58f-629">\_NX DHCP \_ ESTADO \_ INIT</span><span class="sxs-lookup"><span data-stu-id="6d58f-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="6d58f-630">2</span><span class="sxs-lookup"><span data-stu-id="6d58f-630">2</span></span>     |
| <span data-ttu-id="6d58f-631">\_ \_ SELEÇÃO DO ESTADO NX DHCP \_</span><span class="sxs-lookup"><span data-stu-id="6d58f-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="6d58f-632">3</span><span class="sxs-lookup"><span data-stu-id="6d58f-632">3</span></span>     |
| <span data-ttu-id="6d58f-633">PEDIDO DE ESTADO NX \_ DHCP \_ \_</span><span class="sxs-lookup"><span data-stu-id="6d58f-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="6d58f-634">4</span><span class="sxs-lookup"><span data-stu-id="6d58f-634">4</span></span>     |
| <span data-ttu-id="6d58f-635">ESTADO \_ NX DHCP \_ \_ VINCULADO</span><span class="sxs-lookup"><span data-stu-id="6d58f-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="6d58f-636">5</span><span class="sxs-lookup"><span data-stu-id="6d58f-636">5</span></span>     |
| <span data-ttu-id="6d58f-637">NX \_ DHCP \_ ESTADO \_ RENOVAÇÃO</span><span class="sxs-lookup"><span data-stu-id="6d58f-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="6d58f-638">6</span><span class="sxs-lookup"><span data-stu-id="6d58f-638">6</span></span>     |
| <span data-ttu-id="6d58f-639">\_ \_ REENCADERNAÇÃO DO ESTADO DE NX DHCP \_</span><span class="sxs-lookup"><span data-stu-id="6d58f-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="6d58f-640">7</span><span class="sxs-lookup"><span data-stu-id="6d58f-640">7</span></span>     |
| <span data-ttu-id="6d58f-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="6d58f-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="6d58f-642">8</span><span class="sxs-lookup"><span data-stu-id="6d58f-642">8</span></span>     |
| <span data-ttu-id="6d58f-643">\_ \_ SONDAGEM DO ENDEREÇO DO ESTADO NX DHCP \_ \_</span><span class="sxs-lookup"><span data-stu-id="6d58f-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="6d58f-644">9</span><span class="sxs-lookup"><span data-stu-id="6d58f-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="6d58f-645">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-645">Input Parameters</span></span>

- <span data-ttu-id="6d58f-646">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-647">**dhcp_state_change_notify** Ponteiro da função de retorno de mudança de estado</span><span class="sxs-lookup"><span data-stu-id="6d58f-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-648">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-648">Return Values</span></span>

- <span data-ttu-id="6d58f-649">**NX_SUCCESS** (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="6d58f-650">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-651">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-652">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-652">Allowed From</span></span>

<span data-ttu-id="6d58f-653">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-654">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="6d58f-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="6d58f-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="6d58f-656">Definir função de retorno de alteração de estado DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-657">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="6d58f-658">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-658">Description</span></span>

<span data-ttu-id="6d58f-659">Este serviço regista a função de retorno especificado para notificar uma aplicação de alterações do estado dhcp.</span><span class="sxs-lookup"><span data-stu-id="6d58f-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="6d58f-660">Os argumentos de entrada funciton de retorno são o índice de interface e o estado para o quais o Cliente DHCP passou a essa interface.</span><span class="sxs-lookup"><span data-stu-id="6d58f-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="6d58f-661">Para obter mais informações sobre as funções de mudança de estado, consulte *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="6d58f-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-662">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-662">Input Parameters</span></span>

- <span data-ttu-id="6d58f-663">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-664">**dhcp_interface_state_change_notify** Ponteiro da função de retorno de aplicação</span><span class="sxs-lookup"><span data-stu-id="6d58f-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-665">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-665">Return Values</span></span>

- <span data-ttu-id="6d58f-666">**NX_SUCCESS** (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="6d58f-667">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-668">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-668">Allowed From</span></span>

<span data-ttu-id="6d58f-669">Threads, Inicialização</span><span class="sxs-lookup"><span data-stu-id="6d58f-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-670">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="6d58f-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="6d58f-671">nx_dhcp_stop</span></span>

<span data-ttu-id="6d58f-672">Para o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-673">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-674">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-674">Description</span></span>

<span data-ttu-id="6d58f-675">Este serviço impede o processamento de DHCP em todas as interfaces que iniciaram o processamento do DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="6d58f-676">Se não houver interfaces a processar o DHCP, este serviço suspenderá a linha do Cliente DHCP e inativará o temporizador do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="6d58f-677">Para parar o DHCP numa interface específica se várias interfaces estiverem ativadas para DHCP, utilize o serviço *nx_dhcp_interface_stop.*</span><span class="sxs-lookup"><span data-stu-id="6d58f-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-678">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-678">Input Parameters</span></span>

- <span data-ttu-id="6d58f-679">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-680">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-680">Return Values</span></span>

- <span data-ttu-id="6d58f-681">**NX_SUCCESS** (0x00) paragem de DHCP bem sucedida</span><span class="sxs-lookup"><span data-stu-id="6d58f-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="6d58f-682">**NX_DHCP_NOT_STARTED** (0x96) A instância do DHCP não começou.</span><span class="sxs-lookup"><span data-stu-id="6d58f-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="6d58f-683">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-684">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-685">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-685">Allowed From</span></span>

<span data-ttu-id="6d58f-686">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-687">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="6d58f-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="6d58f-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="6d58f-689">Parar o processamento do DHCP na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-690">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="6d58f-691">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-691">Description</span></span>

<span data-ttu-id="6d58f-692">Este serviço impede o processamento de DHCP na interface especificada se o DHCP já estiver iniciado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="6d58f-693">Se não houver outras interfaces a funcionar dhCP, o fio e o temporizador DHCP estão suspensos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-694">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-694">Input Parameters</span></span>

- <span data-ttu-id="6d58f-695">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-696">**Interface_index** Interface para parar o processamento do DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-697">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-697">Return Values</span></span>

- <span data-ttu-id="6d58f-698">**NX_SUCCESS** (0x00) paragem de DHCP bem sucedida</span><span class="sxs-lookup"><span data-stu-id="6d58f-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="6d58f-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP não começou.</span><span class="sxs-lookup"><span data-stu-id="6d58f-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="6d58f-700">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-701">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="6d58f-702">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-703">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-703">Allowed From</span></span>

<span data-ttu-id="6d58f-704">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-705">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="6d58f-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="6d58f-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="6d58f-707">Recupere uma opção DHCP da última resposta do servidor</span><span class="sxs-lookup"><span data-stu-id="6d58f-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-708">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="6d58f-709">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-709">Description</span></span>

<span data-ttu-id="6d58f-710">Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na primeira interface ativada para DHCP encontrada no registo do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="6d58f-711">Se for bem sucedido, os dados de opção são copiados para o tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-712">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-712">Input Parameters</span></span>

- <span data-ttu-id="6d58f-713">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="6d58f-714">**request_option** Opção DHCP, conforme especificado pelos RFCs.</span><span class="sxs-lookup"><span data-stu-id="6d58f-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="6d58f-715">Consulte a opção NX_DHCP_OPTION em *nx_dhcp.h*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="6d58f-716">**destination_ptr** Ponteiro para o destino para a cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="6d58f-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="6d58f-717">**destination_size** Ponteiro para o tamanho do destino e no retorno, o destino para colocar o número de bytes devolvidos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-718">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-718">Return Values</span></span>

- <span data-ttu-id="6d58f-719">**NX_SUCCESS** (0x00) Recuperação de opções bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6d58f-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="6d58f-720">**NX_DHCP_NOT_BOUND** (0x94) Cliente DHCP não vinculado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="6d58f-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) Não há interfaces ativadas para o DHCP</span><span class="sxs-lookup"><span data-stu-id="6d58f-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="6d58f-722">**NX_DHCP_DEST_TO_SMALL** (0x95) O destino é demasiado pequeno para manter a resposta.</span><span class="sxs-lookup"><span data-stu-id="6d58f-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="6d58f-723">**NX_DHCP_PARSE_ERROR** opção DHCP (0x97) não encontrada na resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="6d58f-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="6d58f-724">NX_PTR_ERROR (0x16) Ponteiro de entrada inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="6d58f-725">NX_CALLER_ERROR (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-726">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-726">Allowed From</span></span>

<span data-ttu-id="6d58f-727">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-728">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="6d58f-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="6d58f-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="6d58f-730">Recupere uma opção DHCP da última resposta do servidor na interface especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-731">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="6d58f-732">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-732">Description</span></span>

<span data-ttu-id="6d58f-733">Este serviço recupera a opção DHCP especificada a partir do tampão de opções DHCP na interface especificada, se essa interface estiver ativada para DHCP.</span><span class="sxs-lookup"><span data-stu-id="6d58f-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="6d58f-734">Se for bem sucedido, os dados de opção são copiados para o tampão especificado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-735">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-735">Input Parameters</span></span>

- <span data-ttu-id="6d58f-736">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-737">**Interface_index** Índice sobre o qual recuperar a opção especificada</span><span class="sxs-lookup"><span data-stu-id="6d58f-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="6d58f-738">**request_option** Opção DHCP, conforme especificado pelos RFCs.</span><span class="sxs-lookup"><span data-stu-id="6d58f-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="6d58f-739">Consulte a opção NX_DHCP_OPTION em *nx_dhcp.h*.</span><span class="sxs-lookup"><span data-stu-id="6d58f-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="6d58f-740">**destination_ptr** Ponteiro para o destino para a cadeia de resposta.</span><span class="sxs-lookup"><span data-stu-id="6d58f-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="6d58f-741">**destination_size** Ponteiro para o tamanho do destino e no retorno, o destino para colocar o número de bytes devolvidos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-742">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-742">Return Values</span></span>

- <span data-ttu-id="6d58f-743">**NX_SUCCESS** (0x00) Recuperação de opções bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="6d58f-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="6d58f-744">**NX_DHCP_NOT_BOUND** (0x94) endereço IP não atribuído</span><span class="sxs-lookup"><span data-stu-id="6d58f-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="6d58f-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Tampão é muito pequeno</span><span class="sxs-lookup"><span data-stu-id="6d58f-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="6d58f-746">**NX_DHCP_PARSE_ERROR** opção DHCP (0x97) não encontrada na resposta do Servidor.</span><span class="sxs-lookup"><span data-stu-id="6d58f-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="6d58f-747">NX_PTR_ERROR (0x16) Ponteiro DHCP inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="6d58f-748">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="6d58f-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="6d58f-749">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="6d58f-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-750">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-750">Allowed From</span></span>

<span data-ttu-id="6d58f-751">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-752">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="6d58f-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="6d58f-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="6d58f-754">Converter quatro bytes para ULONG</span><span class="sxs-lookup"><span data-stu-id="6d58f-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-755">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="6d58f-756">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-756">Description</span></span>

<span data-ttu-id="6d58f-757">Este serviço converte os quatro caracteres apontados por "option_string_ptr" num valor longo não assinado.</span><span class="sxs-lookup"><span data-stu-id="6d58f-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="6d58f-758">É especialmente útil quando os endereços IP estão presentes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-759">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-759">Input Parameters</span></span>

- <span data-ttu-id="6d58f-760">**option_string_ptr** Ponteiro para a cadeia de opções previamente recuperada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-761">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-761">Return Values</span></span>

- <span data-ttu-id="6d58f-762">**Valor** Valor dos quatro primeiros bytes.</span><span class="sxs-lookup"><span data-stu-id="6d58f-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-763">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-763">Allowed From</span></span>

<span data-ttu-id="6d58f-764">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-765">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="6d58f-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="6d58f-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="6d58f-767">Desace a função de retorno definido para adicionar opções fornecidas pelo utilizador</span><span class="sxs-lookup"><span data-stu-id="6d58f-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="6d58f-768">Prototype</span><span class="sxs-lookup"><span data-stu-id="6d58f-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="6d58f-769">Descrição</span><span class="sxs-lookup"><span data-stu-id="6d58f-769">Description</span></span>

<span data-ttu-id="6d58f-770">Este serviço regista a função de retorno especificado para adicionar opções fornecidas pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="6d58f-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="6d58f-771">Se a função de retorno especificado, as aplicações podem adicionar opções fornecidas pelo utilizador no pacote iface_index e message_type.</span><span class="sxs-lookup"><span data-stu-id="6d58f-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="6d58f-772">Na rotina do utilizador.</span><span class="sxs-lookup"><span data-stu-id="6d58f-772">In user’s routine.</span></span> <span data-ttu-id="6d58f-773">As aplicações devem seguir o formato de opções DHCP quando adicionar opções fornecidas pelo utilizador.</span><span class="sxs-lookup"><span data-stu-id="6d58f-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="6d58f-774">O tamanho total das opções do utilizador deve ser menor ou igual a user_option_length e atualizar o user_option_length como comprimento real das opções.</span><span class="sxs-lookup"><span data-stu-id="6d58f-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="6d58f-775">Volte NX_TRUE se adicionar opções com sucesso, caso contrário, volte NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="6d58f-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="6d58f-776">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="6d58f-776">Input Parameters</span></span>

- <span data-ttu-id="6d58f-777">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="6d58f-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="6d58f-778">**dhcp_user_option_add** Função de adicionar o ponteiro à opção do utilizador.</span><span class="sxs-lookup"><span data-stu-id="6d58f-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="6d58f-779">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="6d58f-779">Return Values</span></span>

- <span data-ttu-id="6d58f-780">**NX_SUCCESS** (0x00) Conjunto de chamadas bem-sucedidos.</span><span class="sxs-lookup"><span data-stu-id="6d58f-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="6d58f-781">NX_PTR_ERROR (0x16) Ponteiro inválido.</span><span class="sxs-lookup"><span data-stu-id="6d58f-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="6d58f-782">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="6d58f-782">Allowed From</span></span>

<span data-ttu-id="6d58f-783">Fios</span><span class="sxs-lookup"><span data-stu-id="6d58f-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="6d58f-784">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d58f-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
