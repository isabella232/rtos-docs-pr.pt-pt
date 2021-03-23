---
title: Capítulo 4 - Azure RTOS NetX Duo DHCPv6 Serviços de clientes
description: Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCPv6 (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826072"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="71b7f-103">Capítulo 4 - Azure RTOS NetX Duo DHCPv6 Serviços de clientes</span><span class="sxs-lookup"><span data-stu-id="71b7f-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="71b7f-104">Este capítulo contém uma descrição de todos os serviços de clientes Azure RTOS NetX Duo DHCPv6 (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="71b7f-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="71b7f-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="71b7f-106">**nx_dhcpv6_client_create:** *Criar uma instância de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="71b7f-107">**nx_dhcpv6_client_delete:** *Eliminar uma instância de cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="71b7f-108">**nx_dhcpv6_create_ client_duid:** *Criar um DHCPv6 Client DUID*</span><span class="sxs-lookup"><span data-stu-id="71b7f-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="71b7f-109">**nx_dhcpv6 _add_client_ia:** *Adicionar um Endereço de Identidade do Cliente DHCPv6 (IA)*</span><span class="sxs-lookup"><span data-stu-id="71b7f-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="71b7f-110">**nx_dhcpv6 _create_client_ia:** *(Legacy Add a DHCPv6 Client Identity Address (IA))*</span><span class="sxs-lookup"><span data-stu-id="71b7f-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="71b7f-111">**nx_dhcpv6_create_client_iana:** *Criar uma Associação de Identidade de Cliente DHCPv6 para endereços não temporários (IANA)*</span><span class="sxs-lookup"><span data-stu-id="71b7f-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="71b7f-112">**nx_dhcpv6_get_client_duid_time_id:** *Obtenha o tempo ID do DHCPv6 Client DUID*</span><span class="sxs-lookup"><span data-stu-id="71b7f-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="71b7f-113">**nx_dhcpv6_client_set_interface:** *Definir a interface de rede do Cliente para comunicações com o Servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="71b7f-114">**nx_dhcpv6_get_IP_address:** *Obtenha o endereço IPv6 global atribuído ao cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="71b7f-115">**nx_dhcpv6_get_lease_time_data:** *Obtenha estadias de vida válidas e preferidas para o endereço IPv6 global do Cliente*</span><span class="sxs-lookup"><span data-stu-id="71b7f-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="71b7f-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Obtenha tempos de vida válidos e preferidos para o endereço IPv6 do cliente DHCPv6 por índice de endereço*</span><span class="sxs-lookup"><span data-stu-id="71b7f-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="71b7f-117">**nx_dhcpv6_get_iana_lease_time:** *Obter T1 e T2 na Associação de Identidade (IANA) arrendados ao Cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="71b7f-118">**nx_dhcpv6_get_other_option_data:** *Obtenha os dados de opção especificados, por exemplo, nome de domínio ou servidor de fuso horário*</span><span class="sxs-lookup"><span data-stu-id="71b7f-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="71b7f-119">**nx_dhcpv6_get_DNS_server_address:** *Obtenha o endereço DNS Server no índice especificado na lista de servidores DNS do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="71b7f-120">**nx_dhcpv6_get_time_accrued:** *Obtenha o tempo acumulado o arrendamento global de endereços IPv6 foi vinculado ao Cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="71b7f-121">**nx_dhcpv6_get_time_server_address:** *Obtenha o endereço do Servidor de Tempo no índice especificado na lista de servidores do tempo do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="71b7f-122">**nx_dhcpv6_get_valid_ip_address_count:** *Obtenha o número de endereços IPv6 atribuídos ao Cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="71b7f-123">**nx_dhcpv6_reinitialize:** *Reinitializar o DHCPv6 para reiniciar a máquina estatal DHCPv6 e reexecutar o protocolo DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="71b7f-124">**nx_dhcpv6_request_confirm:** *Enviar um pedido CONFIRMA para o Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="71b7f-125">**nx_dhcpv6_request_inform_request:** S *termine uma mensagem INFORM REQUEST para o Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="71b7f-126">**nx_dhcpv6_request_release:** *Enviar um pedido de LIBERTAÇÃO para o Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="71b7f-127">**nx_dhcpv6_request_option_DNS_server:** *Adicionar a opção de servidor DNS à opção de pedido de cliente em mensagens de pedido para o Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="71b7f-128">**nx_dhcpv6_request_option_FQDN:** *Adicionar a opção FQDN à opção cliente solicitar dados em mensagens de pedido ao Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="71b7f-129">**nx_dhcpv6_request_option_domain_name:** *Adicionar a opção nome de domínio à opção de pedido de cliente em mensagens de pedido ao Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="71b7f-130">**nx_dhcpv6_request_option_time_server:** *Adicionar a opção de servidor de tempo à opção cliente solicitar dados em mensagens de pedido ao Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="71b7f-131">**nx_dhcpv6_request_option_timezone:** *Adicione a opção de fuso horário à opção de pedido de dados do Cliente em mensagens de pedido ao Servidor*</span><span class="sxs-lookup"><span data-stu-id="71b7f-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="71b7f-132">**nx_dhcpv6_request_solicit:** *Enviar um pedido DHCPv6 SOLICIT a qualquer Servidor na rede cliente (transmissão)*</span><span class="sxs-lookup"><span data-stu-id="71b7f-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="71b7f-133">**nx_dhcpv6_request_solicit_rapid:** *Enviar um pedido DHCPv6 SOLICIT a qualquer Servidor na rede cliente (transmissão) com o conjunto de opções De Compromisso Rápido*</span><span class="sxs-lookup"><span data-stu-id="71b7f-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="71b7f-134">**nx_dhcpv6_resume:** *Retomar o processamento do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="71b7f-135">**nx_dhcpv6_start:** *Inicie a tarefa de thread do cliente DHCPv6. Note que isto não é equivalente a iniciar a máquina estatal DHCPv6 e não envia um pedido SOLICIT*</span><span class="sxs-lookup"><span data-stu-id="71b7f-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="71b7f-136">**nx_dhcpv6_stop:** *Parar a tarefa de thread do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="71b7f-137">**nx_dhcpv6_suspend:** *Suspender a tarefa de thread do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="71b7f-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="71b7f-138">**nx_dhcpv6_set_time_accrued:** *Dedibrar o tempo acumulado no contrato global de locação de endereços IPv6 do Cliente no registo do Cliente.*</span><span class="sxs-lookup"><span data-stu-id="71b7f-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="71b7f-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="71b7f-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="71b7f-140">Criar uma instância de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-141">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="71b7f-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-142">Description</span></span>

<span data-ttu-id="71b7f-143">Este serviço cria uma instância de cliente DHCPv6, incluindo funções de retorno.</span><span class="sxs-lookup"><span data-stu-id="71b7f-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-144">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-144">Input Parameters</span></span>

- <span data-ttu-id="71b7f-145">**dhcpv6_ptr** Ponteiro para bloco de controlo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="71b7f-146">**ip_ptr** Indicação para o cliente ip instância</span><span class="sxs-lookup"><span data-stu-id="71b7f-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="71b7f-147">**name_ptr** Ponteiro para nomear para a instância DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="71b7f-148">**packet_pool_ptr** Ponteiro para piscina de pacotes de cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="71b7f-149">**stack_ptr** Ponteiro para memória de pilha de cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="71b7f-150">**stack_size** Tamanho da memória da pilha de cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="71b7f-151">**dhcpv6_state_change_notify** Função de retorno do ponteiro invocado quando o Cliente inicia um novo pedido de DHCPv6 para o servidor</span><span class="sxs-lookup"><span data-stu-id="71b7f-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="71b7f-152">**dhcpv6_server_error_handler** Função de retorno do ponteiro invocado quando o Cliente recebe um estado de erro do servidor</span><span class="sxs-lookup"><span data-stu-id="71b7f-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-153">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-153">Return Values</span></span>

- <span data-ttu-id="71b7f-154">**NX_SUCCESS** (0x00) Sucesso cliente criar</span><span class="sxs-lookup"><span data-stu-id="71b7f-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="71b7f-155">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-156">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-157">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-157">Allowed From</span></span>

<span data-ttu-id="71b7f-158">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-160">See Also</span></span>

- <span data-ttu-id="71b7f-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="71b7f-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="71b7f-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="71b7f-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="71b7f-163">Excluir uma instância de cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-165">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-165">Description</span></span>

<span data-ttu-id="71b7f-166">Este serviço elimina uma instância de cliente DHCPv6 previamente criada.</span><span class="sxs-lookup"><span data-stu-id="71b7f-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-167">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-167">Input Parameters</span></span>

- <span data-ttu-id="71b7f-168">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-169">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-169">Return Values</span></span>

- <span data-ttu-id="71b7f-170">**NX_SUCCESS** (0x00) Eliminação bem sucedida do DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="71b7f-171">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-172">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-173">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-173">Allowed From</span></span>

<span data-ttu-id="71b7f-174">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-176">See Also</span></span>

- <span data-ttu-id="71b7f-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="71b7f-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="71b7f-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="71b7f-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="71b7f-179">Define a Interface de Rede do Cliente para DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-180">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="71b7f-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-181">Description</span></span>

<span data-ttu-id="71b7f-182">Este serviço define a interface de rede do Cliente para comunicar com o(s) Servidor(s) DHCPv6 ao índice de interface de entrada especificado.</span><span class="sxs-lookup"><span data-stu-id="71b7f-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-183">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-183">Input Parameters</span></span>

- <span data-ttu-id="71b7f-184">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-185">**interface_index** Índice indicando interface de rede</span><span class="sxs-lookup"><span data-stu-id="71b7f-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-186">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-186">Return Values</span></span>

- <span data-ttu-id="71b7f-187">**interface NX_SUCCESS** (0x00) definida com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="71b7f-188">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-189">NX_INVALID_INTERFACE (0x4C) Entrada do índice de interface inválida</span><span class="sxs-lookup"><span data-stu-id="71b7f-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-190">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-190">Allowed From</span></span>

<span data-ttu-id="71b7f-191">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-193">See Also</span></span>

- <span data-ttu-id="71b7f-194">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="71b7f-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="71b7f-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="71b7f-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="71b7f-197">Define o endereço de destino onde a mensagem DHCPv6 deve ser enviada para</span><span class="sxs-lookup"><span data-stu-id="71b7f-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="71b7f-199">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-199">Description</span></span>

<span data-ttu-id="71b7f-200">Este serviço define o endereço de destino para onde a mensagem DHCPv6 deve ser enviada.</span><span class="sxs-lookup"><span data-stu-id="71b7f-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="71b7f-201">Por predefinição está ALL_DHCP_Relay_Agents_and_Servers(FF02:1:2).</span><span class="sxs-lookup"><span data-stu-id="71b7f-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-202">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-202">Input Parameters</span></span>

- <span data-ttu-id="71b7f-203">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-204">**destination_address** Endereço de destino</span><span class="sxs-lookup"><span data-stu-id="71b7f-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-205">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-205">Return Values</span></span>

- <span data-ttu-id="71b7f-206">**interface NX_SUCCESS** (0x00) definida com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="71b7f-207">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-208">NX_DHCPV6_PARAM_ERROR (0xE93) Erro de paramentamento</span><span class="sxs-lookup"><span data-stu-id="71b7f-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-209">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-209">Allowed From</span></span>

<span data-ttu-id="71b7f-210">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-212">See Also</span></span>

- <span data-ttu-id="71b7f-213">nx_dhcpv6_client _create</span><span class="sxs-lookup"><span data-stu-id="71b7f-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="71b7f-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="71b7f-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="71b7f-216">Criar objeto DUID do cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-217">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="71b7f-218">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-218">Description</span></span>

<span data-ttu-id="71b7f-219">Este serviço cria o DuID do Cliente com os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="71b7f-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="71b7f-220">Se a entrada de tempo não for fornecida e o tipo duid indicar camada de ligação com o tempo, esta função fornecerá um tempo que inclui um fator de aleatoriedade para a singularidade.</span><span class="sxs-lookup"><span data-stu-id="71b7f-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="71b7f-221">Os tipos duid atribuídos pelo fornecedor (empresa) não são suportados.</span><span class="sxs-lookup"><span data-stu-id="71b7f-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-222">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-222">Input Parameters</span></span>

- <span data-ttu-id="71b7f-223">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-224">**duid_type** Tipo de DUID (hardware, empresa, etc)</span><span class="sxs-lookup"><span data-stu-id="71b7f-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="71b7f-225">**hardware_type** Hardware de rede, por exemplo, IEEE 802</span><span class="sxs-lookup"><span data-stu-id="71b7f-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="71b7f-226">**tempo** Valor utilizado na criação de identificador único</span><span class="sxs-lookup"><span data-stu-id="71b7f-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-227">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-227">Return Values</span></span>

- <span data-ttu-id="71b7f-228">**NX_SUCCESS** (0x00) Cliente BEM sucedido DUID criado</span><span class="sxs-lookup"><span data-stu-id="71b7f-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="71b7f-229">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-230">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="71b7f-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) tipo DUID desconhecido ou não suportado</span><span class="sxs-lookup"><span data-stu-id="71b7f-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="71b7f-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) tipo de hardware DUID desconhecido ou não suportado</span><span class="sxs-lookup"><span data-stu-id="71b7f-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-233">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-233">Allowed From</span></span>

<span data-ttu-id="71b7f-234">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-235">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-236">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-236">See Also</span></span>

- <span data-ttu-id="71b7f-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="71b7f-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="71b7f-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="71b7f-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="71b7f-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="71b7f-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="71b7f-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="71b7f-241">Adicionar uma Associação de Identidade ao Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-242">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="71b7f-243">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-243">Description</span></span>

<span data-ttu-id="71b7f-244">Este serviço é idêntico ao *serviço nx_dhcpv6_add_client_ia.*</span><span class="sxs-lookup"><span data-stu-id="71b7f-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="71b7f-245">Adiciona uma Associação de Identidade de Cliente preenchendo o registo do Cliente com os parâmetros fornecidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="71b7f-246">Para solicitar as horas máximas preferenciais e válidas, desa um determinado parâmetro ao infinito.</span><span class="sxs-lookup"><span data-stu-id="71b7f-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="71b7f-247">Para adicionar mais de um IA a um Cliente DHCPv6, desempate o NX_DHCPV6_MAX_IA_ADDRESS para um valor superior ao valor padrão de 1.</span><span class="sxs-lookup"><span data-stu-id="71b7f-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-248">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-248">Input Parameters</span></span>

- <span data-ttu-id="71b7f-249">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-250">**ipv6_address** Ponteiro para o bloco de endereços IP netx duo</span><span class="sxs-lookup"><span data-stu-id="71b7f-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="71b7f-251">**preferred_lifetime** Período de tempo antes de o endereço IP ser depreciado</span><span class="sxs-lookup"><span data-stu-id="71b7f-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="71b7f-252">**valid_lifetime** Período de tempo antes do endereço IP expirar</span><span class="sxs-lookup"><span data-stu-id="71b7f-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-253">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-253">Return Values</span></span>

- <span data-ttu-id="71b7f-254">**NX_SUCCESS** (0x00) Cliente bem sucedido IA adicionado</span><span class="sxs-lookup"><span data-stu-id="71b7f-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="71b7f-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Endereço DUPLICADO IA</span><span class="sxs-lookup"><span data-stu-id="71b7f-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="71b7f-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA excede o máximo que o Cliente IAs pode armazenar</span><span class="sxs-lookup"><span data-stu-id="71b7f-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="71b7f-257">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Endereço IA inválido (por exemplo, nulo) endereço ia em IA</span><span class="sxs-lookup"><span data-stu-id="71b7f-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="71b7f-259">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="71b7f-260">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-260">Allowed From</span></span>

<span data-ttu-id="71b7f-261">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-262">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-263">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-263">See Also</span></span>

- <span data-ttu-id="71b7f-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="71b7f-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="71b7f-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="71b7f-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="71b7f-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="71b7f-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="71b7f-268">Criar uma Associação de Identidade (Não Temporária) para o Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="71b7f-270">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-270">Description</span></span>

<span data-ttu-id="71b7f-271">Este serviço cria uma Associação de Identidade Não Temporária (IANA) a partir dos parâmetros fornecidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="71b7f-272">Para definir as vezes T1 e T2 no máximo (infinito) nos pedidos do Cliente DHCPv6, desajei estes parâmetros a NX_DHCPV6_INFINITE_LEASE.</span><span class="sxs-lookup"><span data-stu-id="71b7f-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="71b7f-273">Um cliente tem apenas um IANA.</span><span class="sxs-lookup"><span data-stu-id="71b7f-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-274">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-274">Input Parameters</span></span>

- <span data-ttu-id="71b7f-275">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-276">**IA_ident** Identificador único da Associação de Identidade</span><span class="sxs-lookup"><span data-stu-id="71b7f-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="71b7f-277">**T1** Quando o Cliente deve iniciar a renovação do endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="71b7f-278">**T2** Quando o Cliente deve iniciar o reencambido endereço DeVV6</span><span class="sxs-lookup"><span data-stu-id="71b7f-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-279">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-279">Return Values</span></span>

- <span data-ttu-id="71b7f-280">**NX_SUCCESS** (0x00) criou com sucesso o IANA</span><span class="sxs-lookup"><span data-stu-id="71b7f-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="71b7f-281">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-282">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-283">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-283">Allowed From</span></span>

<span data-ttu-id="71b7f-284">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-285">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-286">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-286">See Also</span></span>

- <span data-ttu-id="71b7f-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="71b7f-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="71b7f-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="71b7f-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="71b7f-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="71b7f-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="71b7f-291">Adicionar uma Associação de Identidade ao Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-292">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="71b7f-293">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-293">Description</span></span>

<span data-ttu-id="71b7f-294">Este serviço adiciona uma Associação de Identidade de Cliente preenchendo o registo do Cliente com os parâmetros fornecidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="71b7f-295">Para solicitar as horas máximas preferenciais e válidas, desa um determinado parâmetro ao infinito.</span><span class="sxs-lookup"><span data-stu-id="71b7f-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="71b7f-296">Para adicionar mais de um IA a um Cliente DHCPv6, desempate o NX_DHCPV6_MAX_IA_ADDRESS para um valor superior ao valor padrão de 1.</span><span class="sxs-lookup"><span data-stu-id="71b7f-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-297">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-297">Input Parameters</span></span>

- <span data-ttu-id="71b7f-298">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-299">**ipv6_address** Ponteiro para o bloco de endereços IP netx duo</span><span class="sxs-lookup"><span data-stu-id="71b7f-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="71b7f-300">**preferred_lifetime** Período de tempo antes de o endereço IP ser depreciado</span><span class="sxs-lookup"><span data-stu-id="71b7f-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="71b7f-301">**valid_lifetime** Período de tempo antes do endereço IP expirar</span><span class="sxs-lookup"><span data-stu-id="71b7f-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="71b7f-302">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-302">Return Values</span></span>

- <span data-ttu-id="71b7f-303">**NX_SUCCESS** (0x00) Cliente bem sucedido IA adicionado</span><span class="sxs-lookup"><span data-stu-id="71b7f-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="71b7f-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Endereço DUPLICADO IA</span><span class="sxs-lookup"><span data-stu-id="71b7f-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="71b7f-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA excede o máximo que o Cliente IAs pode armazenar</span><span class="sxs-lookup"><span data-stu-id="71b7f-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="71b7f-306">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Endereço IA inválido (por exemplo, nulo) endereço ia em IA</span><span class="sxs-lookup"><span data-stu-id="71b7f-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="71b7f-308">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="71b7f-309">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-309">Allowed From</span></span>

<span data-ttu-id="71b7f-310">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-311">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-312">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-312">See Also</span></span>

- <span data-ttu-id="71b7f-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="71b7f-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="71b7f-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="71b7f-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="71b7f-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="71b7f-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="71b7f-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="71b7f-317">Recupera o tempo ID do Cliente DUID</span><span class="sxs-lookup"><span data-stu-id="71b7f-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="71b7f-319">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-319">Description</span></span>

<span data-ttu-id="71b7f-320">Este serviço recupera o campo de identificação de tempo do Cliente DUID.</span><span class="sxs-lookup"><span data-stu-id="71b7f-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="71b7f-321">Se a aplicação tiver de ligar primeiro *nx_dhcpv6_create_client_duid,* para preencher o DUID do Cliente na instância do Cliente DHCPv6 ou terá um valor nulo para este campo.</span><span class="sxs-lookup"><span data-stu-id="71b7f-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="71b7f-322">A intenção é que a aplicação guarde estes dados e apresente o mesmo DuID do Cliente ao servidor, incluindo o campo de tempo, através de reboots.</span><span class="sxs-lookup"><span data-stu-id="71b7f-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-323">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-323">Input Parameters</span></span>

- <span data-ttu-id="71b7f-324">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-325">**time_id** Ponteiro para o campo de tempo DUID do cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-326">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-326">Return Values</span></span>

- <span data-ttu-id="71b7f-327">**NX_SUCCESS** (0x00) dados de locação IP recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-328">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-329">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-330">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-330">Allowed From</span></span>

<span data-ttu-id="71b7f-331">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-332">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-333">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-333">See Also</span></span>

- <span data-ttu-id="71b7f-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="71b7f-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="71b7f-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="71b7f-339">Recupera o endereço global do IPv6 do cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="71b7f-341">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-341">Description</span></span>

<span data-ttu-id="71b7f-342">Este serviço recupera o endereço IPv6 global do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="71b7f-343">Se o Cliente não tiver um endereço válido, é devolvido um estado de erro.</span><span class="sxs-lookup"><span data-stu-id="71b7f-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="71b7f-344">Se um Cliente tiver mais de um endereço IPv6 global, o endereço IPv6 primário é devolvido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-345">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-345">Input Parameters</span></span>

- <span data-ttu-id="71b7f-346">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-347">**ip_address** Ponteiro para endereço IPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-348">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-348">Return Values</span></span>

- <span data-ttu-id="71b7f-349">**NX_SUCCESS** (0x00) endereço IPv6 atribuído com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="71b7f-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) endereço IPv6 não é válido</span><span class="sxs-lookup"><span data-stu-id="71b7f-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="71b7f-351">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-352">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-353">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-353">Allowed From</span></span>

<span data-ttu-id="71b7f-354">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-355">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-356">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-356">See Also</span></span>

- <span data-ttu-id="71b7f-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="71b7f-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="71b7f-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="71b7f-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="71b7f-362">Recupera os dados do tempo de locação de endereços do cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-363">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="71b7f-364">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-364">Description</span></span>

<span data-ttu-id="71b7f-365">Este serviço recupera os dados globais do tempo de endereço do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="71b7f-366">Se o estado do endereço do Cliente IA for inválido, os dados de tempo são definidos para zero e um estado de conclusão bem-sucedido é devolvido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="71b7f-367">Se um Cliente tiver mais de um endereço IPv6 global, os dados de endereços ii primários são devolvidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-368">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-368">Input Parameters</span></span>

- <span data-ttu-id="71b7f-369">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-370">**T1** Ponteiro para IA abordar tempo de renovação</span><span class="sxs-lookup"><span data-stu-id="71b7f-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="71b7f-371">**T2** Ponteiro para o tempo de reencadernação do endereço ia</span><span class="sxs-lookup"><span data-stu-id="71b7f-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="71b7f-372">**preferred_lifetime** Ponteiro para o tempo quando o endereço ia é depreciado</span><span class="sxs-lookup"><span data-stu-id="71b7f-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="71b7f-373">**valid_lifetime** Ponteiro para o momento em que o endereço IA está expirado</span><span class="sxs-lookup"><span data-stu-id="71b7f-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-374">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-374">Return Values</span></span>

- <span data-ttu-id="71b7f-375">**NX_SUCCESS** (0x00) dados de locação financeira da IA recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-376">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-377">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-378">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-378">Allowed From</span></span>

<span data-ttu-id="71b7f-379">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-380">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-381">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-381">See Also</span></span>

- <span data-ttu-id="71b7f-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="71b7f-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="71b7f-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="71b7f-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="71b7f-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="71b7f-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="71b7f-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="71b7f-388">Recupere os dados do tempo de locação IANA do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="71b7f-390">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-390">Description</span></span>

<span data-ttu-id="71b7f-391">Este serviço recupera os dados globais do tempo de locação ia-NA do Cliente (T1 e T2).</span><span class="sxs-lookup"><span data-stu-id="71b7f-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="71b7f-392">Se nenhum dos endereços IA-NA do Cliente tiver um estado de endereço válido, os dados de tempo são definidos para zero e um estado de conclusão bem-sucedido é devolvido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="71b7f-393">Se um Cliente tiver mais de um endereço IPv6 global, os dados de endereços ii primários são devolvidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-394">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-394">Input Parameters</span></span>

- <span data-ttu-id="71b7f-395">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-396">**T1** Ponteiro a tempo para iniciar a renovação do arrendamento</span><span class="sxs-lookup"><span data-stu-id="71b7f-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="71b7f-397">**T2** Ponteiro a tempo para iniciar o reencaimento do arrendamento</span><span class="sxs-lookup"><span data-stu-id="71b7f-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-398">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-398">Return Values</span></span>

- <span data-ttu-id="71b7f-399">**NX_SUCCESS** (0x00) dados de locação IANA recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-400">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-401">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-402">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-402">Allowed From</span></span>

<span data-ttu-id="71b7f-403">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-404">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-405">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-405">See Also</span></span>

- <span data-ttu-id="71b7f-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="71b7f-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="71b7f-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="71b7f-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="71b7f-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="71b7f-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="71b7f-412">Recupere uma contagem dos endereços IA válidos do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-413">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="71b7f-414">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-414">Description</span></span>

<span data-ttu-id="71b7f-415">Este serviço recupera a contagem dos endereços IPv6 válidos do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="71b7f-416">Um endereço IPv6 válido está vinculado (atribuído) ao Cliente e registado na instância IP.</span><span class="sxs-lookup"><span data-stu-id="71b7f-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-417">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-417">Input Parameters</span></span>

- <span data-ttu-id="71b7f-418">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-419">**address_count** Ponteiro para a contagem de endereços para devolver</span><span class="sxs-lookup"><span data-stu-id="71b7f-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-420">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-420">Return Values</span></span>

- <span data-ttu-id="71b7f-421">**NX_SUCCESS** (0x00) dados de locação IANA recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-422">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-423">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-424">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-424">Allowed From</span></span>

<span data-ttu-id="71b7f-425">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-426">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="71b7f-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="71b7f-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="71b7f-428">Recupere os dados do Cliente IA por índice de endereço</span><span class="sxs-lookup"><span data-stu-id="71b7f-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-429">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="71b7f-430">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-430">Description</span></span>

<span data-ttu-id="71b7f-431">Este serviço recupera o endereço ia do Cliente e os dados de locação por índice de endereço.</span><span class="sxs-lookup"><span data-stu-id="71b7f-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="71b7f-432">Se for fornecido um índice inválido ou o endereço IPv6 nesse índice não for válido, o serviço devolve um estado de erro NX_DHCPV6_IA_ADDRESS_NOT_VALID.</span><span class="sxs-lookup"><span data-stu-id="71b7f-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-433">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-433">Input Parameters</span></span>

- <span data-ttu-id="71b7f-434">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-435">**address_index** Índice na tabela DHCPv6 IA</span><span class="sxs-lookup"><span data-stu-id="71b7f-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="71b7f-436">**ip_address** Ponteiro para endereço IPv6 para recuperar</span><span class="sxs-lookup"><span data-stu-id="71b7f-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="71b7f-437">**preferred_lifetime** Ponteiro para o tempo quando o endereço ia é depreciado</span><span class="sxs-lookup"><span data-stu-id="71b7f-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="71b7f-438">**valid_lifetime** Ponteiro para o momento em que o endereço IA está expirado</span><span class="sxs-lookup"><span data-stu-id="71b7f-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-439">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-439">Return Values</span></span>

- <span data-ttu-id="71b7f-440">**NX_SUCCESS** (0x00) dados da IANA recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Um índice inválido ou nenhum endereço IPv6 válido no índice fornecido</span><span class="sxs-lookup"><span data-stu-id="71b7f-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="71b7f-442">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-443">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-444">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-444">Allowed From</span></span>

<span data-ttu-id="71b7f-445">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-446">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-447">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-447">See Also</span></span>

- <span data-ttu-id="71b7f-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="71b7f-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="71b7f-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="71b7f-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="71b7f-452">Recupera o endereço do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="71b7f-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-453">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="71b7f-454">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-454">Description</span></span>

<span data-ttu-id="71b7f-455">Este serviço recupera os dados de endereços do servidor DNS IPv6 no índice especificado na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="71b7f-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="71b7f-456">Se a lista não contiver um endereço de servidor no índice, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="71b7f-457">O índice não pode exceder o tamanho da lista do Servidor DNS é especificado pela opção configurável do utilizador NX_DHCPV6_NUM_DNS_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="71b7f-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-458">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-458">Input Parameters</span></span>

- <span data-ttu-id="71b7f-459">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-460">**índice** Índice na lista do Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="71b7f-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="71b7f-461">**server_address** Ponteiro para o tampão de endereço do servidor</span><span class="sxs-lookup"><span data-stu-id="71b7f-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-462">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-462">Return Values</span></span>

- <span data-ttu-id="71b7f-463">**NX_SUCCESS** (0x00) Endereço recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="71b7f-464">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-465">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-466">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-466">Allowed From</span></span>

<span data-ttu-id="71b7f-467">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-468">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-469">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-469">See Also</span></span>

- <span data-ttu-id="71b7f-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="71b7f-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="71b7f-474">Recupera dados de opção DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-475">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="71b7f-476">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-476">Description</span></span>

<span data-ttu-id="71b7f-477">Este serviço recupera os dados de opção DHCPv6 a partir de uma mensagem DHCPv6 para o código de opção especificado.</span><span class="sxs-lookup"><span data-stu-id="71b7f-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-478">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-478">Input Parameters</span></span>

- <span data-ttu-id="71b7f-479">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-480">código **de opção** Código código código para que dados para recuperar</span><span class="sxs-lookup"><span data-stu-id="71b7f-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="71b7f-481">**tampão** Ponteiro para tampão para copiar dados para</span><span class="sxs-lookup"><span data-stu-id="71b7f-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="71b7f-482">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-482">Return Values</span></span>

- <span data-ttu-id="71b7f-483">**NX_SUCCESS** (0x00) Dados de opção recuperados com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="71b7f-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Código de opção desconhecido/não suportado</span><span class="sxs-lookup"><span data-stu-id="71b7f-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="71b7f-485">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-486">NX_DHCPV6_PARAM_ERROR (0xE93) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="71b7f-487">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-488">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-488">Allowed From</span></span>

<span data-ttu-id="71b7f-489">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-490">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-491">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-491">See Also</span></span>

- <span data-ttu-id="71b7f-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="71b7f-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="71b7f-496">Recupera tempo acumulado no contrato de arrendamento de endereços IP do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-497">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="71b7f-498">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-498">Description</span></span>

<span data-ttu-id="71b7f-499">Este serviço recupera o tempo acumulado no contrato de arrendamento de endereços IPv6 do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="71b7f-500">A função verifica todos os endereços IPv6 atribuídos ao Cliente para o primeiro endereço válido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="71b7f-501">Se não forem encontrados endereços válidos, é devolvido um valor zero pelo tempo acumulado.</span><span class="sxs-lookup"><span data-stu-id="71b7f-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-502">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-502">Input Parameters</span></span>

- <span data-ttu-id="71b7f-503">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-504">**time_accrued** Ponteiro para o tempo acumulado no arrendamento IP</span><span class="sxs-lookup"><span data-stu-id="71b7f-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-505">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-505">Return Values</span></span>

- <span data-ttu-id="71b7f-506">**NX_SUCCESS** (0x00) Tempo acumulado recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="71b7f-507">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-508">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-509">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-509">Allowed From</span></span>

<span data-ttu-id="71b7f-510">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-511">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-512">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-512">See Also</span></span>

- <span data-ttu-id="71b7f-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="71b7f-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="71b7f-518">Recupera o endereço do servidor de tempo</span><span class="sxs-lookup"><span data-stu-id="71b7f-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-519">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="71b7f-520">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-520">Description</span></span>

<span data-ttu-id="71b7f-521">Este serviço recupera os dados de endereços do servidor Time IPv6 no índice especificado na lista de Clientes.</span><span class="sxs-lookup"><span data-stu-id="71b7f-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="71b7f-522">Se a lista não contiver um endereço de servidor no índice, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="71b7f-523">O índice não pode exceder o tamanho da lista de Servidor de Tempo é especificado pela opção configurável do utilizador NX_DHCPV6_NUM_TIME_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="71b7f-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-524">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-524">Input Parameters</span></span>

- <span data-ttu-id="71b7f-525">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-526">**índice** Índice na lista do Servidor de Tempo</span><span class="sxs-lookup"><span data-stu-id="71b7f-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="71b7f-527">**server_address** Ponteiro para o tampão de endereço do servidor</span><span class="sxs-lookup"><span data-stu-id="71b7f-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-528">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-528">Return Values</span></span>

- <span data-ttu-id="71b7f-529">**NX_SUCCESS** (0x00) Endereço recuperado com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="71b7f-530">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-531">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-532">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-532">Allowed From</span></span>

<span data-ttu-id="71b7f-533">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-534">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-535">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-535">See Also</span></span>

- <span data-ttu-id="71b7f-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="71b7f-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="71b7f-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="71b7f-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="71b7f-541">Remova o endereço IP do Cliente da tabela IP</span><span class="sxs-lookup"><span data-stu-id="71b7f-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-542">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-543">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-543">Description</span></span>

<span data-ttu-id="71b7f-544">Este serviço reinicia o Cliente para reiniciar a máquina estatal DHCPv6 e re-executar o protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="71b7f-545">Isto não é necessário se o Cliente não tiver iniciado previamente a máquina estatal DHPCv6 ou tiver sido atribuído qualquer endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="71b7f-546">Os endereços guardados para o Cliente DHCPv6, bem como registados na instância IP, estão ambos limpos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="71b7f-547">A aplicação deve ainda iniciar o Cliente DHCPv6 utilizando o *serviço de nx_dhcpv6_start* e iniciar o pedido de atribuição de endereços IPv6 ligando para *nx_dhcpv6_request_solicit*.</span><span class="sxs-lookup"><span data-stu-id="71b7f-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-548">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-548">Input Parameters</span></span>

- <span data-ttu-id="71b7f-549">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-550">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-550">Return Values</span></span>

- <span data-ttu-id="71b7f-551">**endereço NX_SUCCESS** (0x00) removido com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="71b7f-552">**cliente NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 já está em execução</span><span class="sxs-lookup"><span data-stu-id="71b7f-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="71b7f-553">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-554">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-555">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-555">Allowed From</span></span>

<span data-ttu-id="71b7f-556">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-557">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-558">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-558">See Also</span></span>

- <span data-ttu-id="71b7f-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="71b7f-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="71b7f-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="71b7f-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="71b7f-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="71b7f-562">Processar o estado confirma do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-563">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-564">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-564">Description</span></span>

<span data-ttu-id="71b7f-565">Este serviço envia um pedido CONFIRMA.</span><span class="sxs-lookup"><span data-stu-id="71b7f-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="71b7f-566">Se for recebida uma resposta do Servidor, o Cliente DHCPv6 atualiza os seus parâmetros de locação com os dados recebidos.</span><span class="sxs-lookup"><span data-stu-id="71b7f-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-567">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-567">Input Parameters</span></span>

- <span data-ttu-id="71b7f-568">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-569">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-569">Return Values</span></span>

- <span data-ttu-id="71b7f-570">**NX_SUCCESS** (0x00) CONFIRMam mensagem enviada e processada com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="71b7f-571">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-572">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-573">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-573">Allowed From</span></span>

<span data-ttu-id="71b7f-574">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-575">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-576">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-576">See Also</span></span>

- <span data-ttu-id="71b7f-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="71b7f-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="71b7f-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="71b7f-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="71b7f-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="71b7f-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="71b7f-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="71b7f-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="71b7f-581">Processar o estado de PEDIDO INFORM do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-583">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-583">Description</span></span>

<span data-ttu-id="71b7f-584">Este serviço envia uma mensagem INFORM REQUEST.</span><span class="sxs-lookup"><span data-stu-id="71b7f-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="71b7f-585">Se uma resposta for recebida, Quando uma é recebida, a resposta é processada para determinar se é válida e o servidor concedeu o pedido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="71b7f-586">A instância do Cliente é então atualizada com as informações do servidor, conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="71b7f-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-587">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-587">Input Parameters</span></span>

- <span data-ttu-id="71b7f-588">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-589">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-589">Return Values</span></span>

- <span data-ttu-id="71b7f-590">**NX_SUCCESS** (0x00) INFORM REQUEST Mensagem criada e processada com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="71b7f-591">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-592">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-593">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-593">Allowed From</span></span>

<span data-ttu-id="71b7f-594">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-595">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-596">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-596">See Also</span></span>

- <span data-ttu-id="71b7f-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="71b7f-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="71b7f-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="71b7f-599">Adicionar servidor DNS ao pedido de opção DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-600">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-601">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-601">Description</span></span>

<span data-ttu-id="71b7f-602">Este serviço adiciona a opção de solicitar informações do servidor DNS ao pedido de opção DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="71b7f-603">Se a resposta do Servidor incluir dados do servidor DNS, o Cliente armazenará o servidor DNS se tiver espaço para o fazer.</span><span class="sxs-lookup"><span data-stu-id="71b7f-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="71b7f-604">O número de servidores DNS que o Cliente pode armazenar é determinado pela opção configurável NX_DHCPV6_NUM_DNS_SERVERS cujo valor padrão é 2.</span><span class="sxs-lookup"><span data-stu-id="71b7f-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-605">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-605">Input Parameters</span></span>

- <span data-ttu-id="71b7f-606">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-607">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-607">Return Values</span></span>

- <span data-ttu-id="71b7f-608">**NX_SUCCESS** (0x00) opção de servidor DNS está incluída</span><span class="sxs-lookup"><span data-stu-id="71b7f-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="71b7f-609">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-610">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-611">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-611">Allowed From</span></span>

<span data-ttu-id="71b7f-612">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-613">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-614">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-614">See Also</span></span>

- <span data-ttu-id="71b7f-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="71b7f-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="71b7f-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="71b7f-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="71b7f-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="71b7f-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="71b7f-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="71b7f-619">Adicionar opção de nome de domínio totalmente qualificado à lista de pedidos de opção</span><span class="sxs-lookup"><span data-stu-id="71b7f-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-620">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="71b7f-621">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-621">Description</span></span>

<span data-ttu-id="71b7f-622">Este serviço adiciona a opção de adicionar o Nome de Domínio Totalmente Qualificado ao pedido de opção DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="71b7f-623">Existem três opções para a opção FQDN:</span><span class="sxs-lookup"><span data-stu-id="71b7f-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="71b7f-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Atualizar o mapeamento de endereço FQDN-iPv6 para FQDN e endereço(es) utilizado pelo Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="71b7f-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Atualizar o mapeamento de endereço FQDN-iPv6 para FQDN e endereço(es) utilizado pelo Cliente para o servidor.</span><span class="sxs-lookup"><span data-stu-id="71b7f-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="71b7f-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Solicite que o servidor não efetue atualizações DNS em nome do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-627">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-627">Input Parameters</span></span>

- <span data-ttu-id="71b7f-628">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-629">**domain_name** Corda segurando o nome de domínio</span><span class="sxs-lookup"><span data-stu-id="71b7f-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="71b7f-630">**op** Tipo de opção FQDN a aplicar (ver lista acima)</span><span class="sxs-lookup"><span data-stu-id="71b7f-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-631">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-631">Return Values</span></span>

- <span data-ttu-id="71b7f-632">**NX_SUCCESS** (0x00) A opção FQDN está incluída</span><span class="sxs-lookup"><span data-stu-id="71b7f-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="71b7f-633">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-634">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-635">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-635">Allowed From</span></span>

<span data-ttu-id="71b7f-636">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-637">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-638">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-638">See Also</span></span>

- <span data-ttu-id="71b7f-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="71b7f-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="71b7f-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="71b7f-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="71b7f-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="71b7f-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="71b7f-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="71b7f-643">Adicione a opção de nome de domínio ao pedido de opção DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-644">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-645">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-645">Description</span></span>

<span data-ttu-id="71b7f-646">Este serviço adiciona a opção nome de domínio ao pedido de opção nas mensagens de pedido do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="71b7f-647">Se a resposta do Servidor incluir dados de nome de domínio, o Cliente armazenará as informações sobre o nome de domínio se o tamanho do nome de domínio estiver dentro do tamanho do tampão para manter o nome de domínio.</span><span class="sxs-lookup"><span data-stu-id="71b7f-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="71b7f-648">Este tamanho tampão é uma opção configurável (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) com um valor padrão de 30 bytes.</span><span class="sxs-lookup"><span data-stu-id="71b7f-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-649">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-649">Input Parameters</span></span>

- <span data-ttu-id="71b7f-650">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-651">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-651">Return Values</span></span>

- <span data-ttu-id="71b7f-652">**NX_SUCCESS** (0x00) conjunto de opção de nome de domínio</span><span class="sxs-lookup"><span data-stu-id="71b7f-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="71b7f-653">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-654">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-655">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-655">Allowed From</span></span>

<span data-ttu-id="71b7f-656">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-657">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-658">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-658">See Also</span></span>

- <span data-ttu-id="71b7f-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="71b7f-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="71b7f-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="71b7f-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="71b7f-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="71b7f-663">Definir dados do servidor de tempo como pedido opcional</span><span class="sxs-lookup"><span data-stu-id="71b7f-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-664">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-665">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-665">Description</span></span>

<span data-ttu-id="71b7f-666">Este serviço adiciona a opção de informação do servidor de tempo ao pedido de opção de solicitação de mensagens de pedido do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="71b7f-667">Se a resposta do Servidor incluir dados do servidor tim, o Cliente armazenará o servidor de tempo se tiver espaço para o fazer.</span><span class="sxs-lookup"><span data-stu-id="71b7f-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="71b7f-668">O número de servidores de tempo que o Cliente pode armazenar é determinado pela opção configurável</span><span class="sxs-lookup"><span data-stu-id="71b7f-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="71b7f-669">NX_DHCPV6_NUM_TIME _SERVERS cujo valor padrão é 1.</span><span class="sxs-lookup"><span data-stu-id="71b7f-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-670">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-670">Input Parameters</span></span>

- <span data-ttu-id="71b7f-671">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-672">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-672">Return Values</span></span>

- <span data-ttu-id="71b7f-673">**NX_SUCCESS** (0x00) Opção de servidor de tempo adicionada</span><span class="sxs-lookup"><span data-stu-id="71b7f-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="71b7f-674">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-675">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-676">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-676">Allowed From</span></span>

<span data-ttu-id="71b7f-677">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-678">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-679">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-679">See Also</span></span>

- <span data-ttu-id="71b7f-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="71b7f-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="71b7f-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="71b7f-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="71b7f-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="71b7f-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="71b7f-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="71b7f-684">Definir dados de fuso horário como pedido opcional</span><span class="sxs-lookup"><span data-stu-id="71b7f-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-685">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-686">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-686">Description</span></span>

<span data-ttu-id="71b7f-687">Este serviço adiciona a opção de solicitar informações de fuso horário ao pedido de opção Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="71b7f-688">Se a resposta do Servidor incluir dados de fuso horário, o Cliente armazenará a informação do fuso horário se o tamanho do fuso horário estiver dentro do tamanho do tampão para manter o fuso horário.</span><span class="sxs-lookup"><span data-stu-id="71b7f-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="71b7f-689">Este tamanho tampão é uma opção configurável (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) com um valor padrão de 10 bytes.</span><span class="sxs-lookup"><span data-stu-id="71b7f-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-690">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-690">Input Parameters</span></span>

- <span data-ttu-id="71b7f-691">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-692">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-692">Return Values</span></span>

- <span data-ttu-id="71b7f-693">**NX_SUCCESS** (0x00) opção de fuso horário adicionada</span><span class="sxs-lookup"><span data-stu-id="71b7f-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="71b7f-694">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-695">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-696">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-696">Allowed From</span></span>

<span data-ttu-id="71b7f-697">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-698">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="71b7f-699">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-699">See Also</span></span>

- <span data-ttu-id="71b7f-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="71b7f-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="71b7f-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="71b7f-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="71b7f-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="71b7f-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="71b7f-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="71b7f-704">Envie uma mensagem DE LIBERTAÇÃO DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-705">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-706">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-706">Description</span></span>

<span data-ttu-id="71b7f-707">Este serviço envia uma mensagem RELEASE na rede Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="71b7f-708">Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso.</span><span class="sxs-lookup"><span data-stu-id="71b7f-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="71b7f-709">Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="71b7f-710">A tarefa de thread do cliente DHCPv6 aguarda uma resposta de um Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="71b7f-711">Se um for recebido, verifica se a resposta é válida e armazena os dados para o registo do Cliente.</span><span class="sxs-lookup"><span data-stu-id="71b7f-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-712">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-712">Input Parameters</span></span>

- <span data-ttu-id="71b7f-713">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-714">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-714">Return Values</span></span>

- <span data-ttu-id="71b7f-715">**NX_SUCCESS** (0x00) Mensagem DE LIBERTAÇÃO enviada com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="71b7f-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Tarefa de cliente não iniciada</span><span class="sxs-lookup"><span data-stu-id="71b7f-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="71b7f-717">**endereço NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) não vinculado ao Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="71b7f-718">**NX_INVALID_INTERFACE** (0x4C) Não encontrados na tabela de endereços IP</span><span class="sxs-lookup"><span data-stu-id="71b7f-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="71b7f-719">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-720">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-721">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-721">Allowed From</span></span>

<span data-ttu-id="71b7f-722">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-723">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-724">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-724">See Also</span></span>

- <span data-ttu-id="71b7f-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="71b7f-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="71b7f-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="71b7f-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="71b7f-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="71b7f-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="71b7f-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="71b7f-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="71b7f-729">Enviar uma mensagem SOLICIT</span><span class="sxs-lookup"><span data-stu-id="71b7f-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-730">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-731">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-731">Description</span></span>

<span data-ttu-id="71b7f-732">Este serviço envia uma mensagem SOLICIT na rede.</span><span class="sxs-lookup"><span data-stu-id="71b7f-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="71b7f-733">Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso.</span><span class="sxs-lookup"><span data-stu-id="71b7f-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="71b7f-734">Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="71b7f-735">A tarefa de thread do cliente DHCPv6 aguarda uma resposta (uma mensagem DE ANÚNCIO) de um Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="71b7f-736">Se um for recebido, verifica se a resposta é válida, armazena os dados para o registo do Cliente e promove o Cliente ao estado REQUEST.</span><span class="sxs-lookup"><span data-stu-id="71b7f-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="71b7f-737">Se a opção 'Compromisso Rápido' estiver definida, o Cliente DHCPv6 irá diretamente para o estado de Bound se receber uma mensagem de anúncio do Servidor válido.</span><span class="sxs-lookup"><span data-stu-id="71b7f-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="71b7f-738">Consulte a descrição do serviço para *obter mais informações nx_dhcpv6_request_solicit_rapid.*</span><span class="sxs-lookup"><span data-stu-id="71b7f-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-739">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-739">Input Parameters</span></span>

- <span data-ttu-id="71b7f-740">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-741">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-741">Return Values</span></span>

- <span data-ttu-id="71b7f-742">**NX_SUCCESS** (0x00) Mensagem SOLICIT enviada com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="71b7f-743">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-744">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-745">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-745">Allowed From</span></span>

<span data-ttu-id="71b7f-746">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-747">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="71b7f-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="71b7f-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="71b7f-749">Envie uma mensagem SOLICIT com a opção Rapid Commit</span><span class="sxs-lookup"><span data-stu-id="71b7f-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-750">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-751">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-751">Description</span></span>

<span data-ttu-id="71b7f-752">Este serviço envia uma mensagem SOLICIT na rede com o conjunto de opções Rapid Commit.</span><span class="sxs-lookup"><span data-stu-id="71b7f-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="71b7f-753">Se a mensagem for enviada com sucesso, é devolvido um estado de sucesso.</span><span class="sxs-lookup"><span data-stu-id="71b7f-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="71b7f-754">Uma conclusão bem sucedida não significa que o Cliente recebeu uma resposta ou foi-lhe ainda concedido um endereço IPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="71b7f-755">A tarefa de thread do cliente DHCPv6 aguarda uma resposta (uma mensagem DE ANÚNCIO) de um Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="71b7f-756">Se um for recebido, verifica se a resposta é válida, armazena os dados para o registo do Cliente e promove o Cliente para o estado BOUND.</span><span class="sxs-lookup"><span data-stu-id="71b7f-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-757">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-757">Input Parameters</span></span>

- <span data-ttu-id="71b7f-758">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-759">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-759">Return Values</span></span>

- <span data-ttu-id="71b7f-760">**NX_SUCCESS** (0x00) Mensagem SOLICIT enviada com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="71b7f-761">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-762">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-763">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-763">Allowed From</span></span>

<span data-ttu-id="71b7f-764">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-765">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-766">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-766">See Also</span></span>

- <span data-ttu-id="71b7f-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="71b7f-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="71b7f-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="71b7f-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="71b7f-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="71b7f-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="71b7f-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="71b7f-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="71b7f-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="71b7f-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="71b7f-772">Retomar a tarefa do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-773">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-774">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-774">Description</span></span>

<span data-ttu-id="71b7f-775">Este serviço retoma a tarefa de thread do cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="71b7f-776">O estado atual do cliente DHCPv6 será processado (por exemplo, Ligado, Solicit)</span><span class="sxs-lookup"><span data-stu-id="71b7f-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-777">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-777">Input Parameters</span></span>

- <span data-ttu-id="71b7f-778">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-779">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-779">Return Values</span></span>

- <span data-ttu-id="71b7f-780">**NX_SUCCESS** (0x00) Cliente retomado com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="71b7f-781">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-782">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-783">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-783">Allowed From</span></span>

<span data-ttu-id="71b7f-784">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-785">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-786">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-786">See Also</span></span>

- <span data-ttu-id="71b7f-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="71b7f-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="71b7f-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="71b7f-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="71b7f-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="71b7f-790">nx_dhcpv6_set_ time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="71b7f-791">Define o tempo acumulado no contrato de arrendamento de endereços IP do Cliente</span><span class="sxs-lookup"><span data-stu-id="71b7f-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="71b7f-792">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="71b7f-793">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-793">Description</span></span>

<span data-ttu-id="71b7f-794">Este serviço define o tempo acumulado no endereço IP global do Cliente desde que foi atribuído pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="71b7f-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="71b7f-795">Isto só deve ser utilizado se um Cliente estiver atualmente vinculado a um endereço IPv6 atribuído.</span><span class="sxs-lookup"><span data-stu-id="71b7f-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-796">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-796">Input Parameters</span></span>

- <span data-ttu-id="71b7f-797">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="71b7f-798">**time_accrued** Tempo acumulado no arrendamento IP</span><span class="sxs-lookup"><span data-stu-id="71b7f-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-799">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-799">Return Values</span></span>

- <span data-ttu-id="71b7f-800">**NX_SUCCESS** (0x00) Tempo acumulado com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="71b7f-801">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-802">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-802">Allowed From</span></span>

<span data-ttu-id="71b7f-803">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-804">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-805">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-805">See Also</span></span>

- <span data-ttu-id="71b7f-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="71b7f-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="71b7f-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="71b7f-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="71b7f-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="71b7f-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="71b7f-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="71b7f-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="71b7f-811">Inicie a tarefa do Cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-812">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-813">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-813">Description</span></span>

<span data-ttu-id="71b7f-814">Este serviço inicia a tarefa do Cliente DHCPv6 e prepara o Cliente para executar o protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="71b7f-815">Verifica que a instância do Cliente tem informações suficientes (como um Cliente DUID), cria e liga a tomada UDP para enviar e receber mensagens DHCPv6 e ativa os temporizadores para manter o registo do tempo de sessão e quando o atual contrato de arrendamento IPv6 expirar.</span><span class="sxs-lookup"><span data-stu-id="71b7f-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-816">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-816">Input Parameters</span></span>

- <span data-ttu-id="71b7f-817">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-818">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-818">Return Values</span></span>

- <span data-ttu-id="71b7f-819">**NX_SUCCESS** (0x00) Cliente começou com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="71b7f-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Cliente em falta de opções necessárias</span><span class="sxs-lookup"><span data-stu-id="71b7f-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="71b7f-821">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-822">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-823">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-823">Allowed From</span></span>

<span data-ttu-id="71b7f-824">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-825">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-826">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-826">See Also</span></span>

- <span data-ttu-id="71b7f-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="71b7f-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="71b7f-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="71b7f-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="71b7f-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="71b7f-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="71b7f-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="71b7f-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="71b7f-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="71b7f-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="71b7f-832">Pare a tarefa do Cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-833">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-834">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-834">Description</span></span>

<span data-ttu-id="71b7f-835">Este serviço interrompe a tarefa do Cliente DHCPv6 e limpa as contagens de retransmissão, intervalos máximos de retransmissão, desativa a sessão e locação dos temporizadores de validade, e desvincula a porta de tomada do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="71b7f-836">Para reiniciar o Cliente, é necessário parar primeiro e reinitir opcionalmente o Cliente antes de iniciar outra sessão com qualquer servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="71b7f-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="71b7f-837">Consulte a secção Exemplo Pequeno para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="71b7f-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-838">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-838">Input Parameters</span></span>

- <span data-ttu-id="71b7f-839">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-840">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-840">Return Values</span></span>

- <span data-ttu-id="71b7f-841">**NX_SUCCESS** (0x00) Cliente parou com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="71b7f-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Linha de cliente não começou</span><span class="sxs-lookup"><span data-stu-id="71b7f-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="71b7f-843">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-844">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="71b7f-845">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-845">Allowed From</span></span>

<span data-ttu-id="71b7f-846">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-847">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-848">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-848">See Also</span></span>

- <span data-ttu-id="71b7f-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="71b7f-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="71b7f-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="71b7f-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="71b7f-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="71b7f-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="71b7f-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="71b7f-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="71b7f-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="71b7f-854">Suspender a tarefa do Cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="71b7f-855">Prototype</span><span class="sxs-lookup"><span data-stu-id="71b7f-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="71b7f-856">Descrição</span><span class="sxs-lookup"><span data-stu-id="71b7f-856">Description</span></span>

<span data-ttu-id="71b7f-857">Este serviço suspende a tarefa do cliente DHCPv6 e qualquer pedido que tenha sido no meio do processamento.</span><span class="sxs-lookup"><span data-stu-id="71b7f-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="71b7f-858">Os temporizadores são desativados e o estado do Cliente está definido para não funcionar.</span><span class="sxs-lookup"><span data-stu-id="71b7f-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71b7f-859">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="71b7f-859">Input Parameters</span></span>

- <span data-ttu-id="71b7f-860">**dhcpv6_ptr** Ponteiro para a instância do cliente DHCPv6</span><span class="sxs-lookup"><span data-stu-id="71b7f-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="71b7f-861">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="71b7f-861">Return Values</span></span>

- <span data-ttu-id="71b7f-862">**cliente NX_SUCCESS** (0x00) suspenso com sucesso</span><span class="sxs-lookup"><span data-stu-id="71b7f-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="71b7f-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Cliente não em funcionamento por isso não pode ser suspenso</span><span class="sxs-lookup"><span data-stu-id="71b7f-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="71b7f-864">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="71b7f-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="71b7f-865">NX_CALLER_ERROR (0x11) Deve ser chamado de fio</span><span class="sxs-lookup"><span data-stu-id="71b7f-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71b7f-866">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="71b7f-866">Allowed From</span></span>

<span data-ttu-id="71b7f-867">Fios</span><span class="sxs-lookup"><span data-stu-id="71b7f-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71b7f-868">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71b7f-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="71b7f-869">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b7f-869">See Also</span></span>

- <span data-ttu-id="71b7f-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="71b7f-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="71b7f-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="71b7f-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="71b7f-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="71b7f-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="71b7f-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="71b7f-873">nx_dhcpv6_stop</span></span>
