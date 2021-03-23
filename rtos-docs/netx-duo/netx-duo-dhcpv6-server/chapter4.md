---
title: Capítulo 4 - Serviços de servidores Azure RTOS NetX Duo DHCPv6
description: Este capítulo contém uma descrição de todos os serviços NetX Duo DHCPv6Server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826029"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="212b5-103">Capítulo 4 - Serviços de servidores Azure RTOS NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="212b5-104">Este capítulo contém uma descrição de todos os serviços NetX Duo DHCPv6Server (listados abaixo).</span><span class="sxs-lookup"><span data-stu-id="212b5-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="212b5-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="212b5-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="212b5-106">nx_dhcpv6_server_create Criar *uma insísição de servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="212b5-107">nx_dhcpv6_server_delete Eliminar *uma insísição do servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="212b5-108">nx_dhcpv6_server_start Iniciar *a tarefa do servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="212b5-109">nx_dhcpv6_server_suspend suspender *a tarefa do servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="212b5-110">nx_dhcpv6_server_resume retomar *o processamento do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="212b5-111">nx_dhcpv6_server_suspend suspender *o processamento do cliente DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="212b5-112">nx_dhcpv6_create_dns_address Definir *o servidor DNS para pedidos de opção*</span><span class="sxs-lookup"><span data-stu-id="212b5-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="212b5-113">nx_dhcpv6_create_ip_address_range Criar *a gama de endereços IP para arrendar*</span><span class="sxs-lookup"><span data-stu-id="212b5-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="212b5-114">nx_dhcpv6_reserve_ip_address_range *Gama de endereços IP de reserva na lista de servidores*</span><span class="sxs-lookup"><span data-stu-id="212b5-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="212b5-115">nx_dhcpv6_set_server_duid *Definir o Servidor DUID para pacotes DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="212b5-116">nx_dhcpv6_add_ip_address_lease Adicionar *um registo de locação à tabela de servidores DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="212b5-117">Nx_dhcpv6_retrieve_ip_address_lease Recuperar *um registo de locação IP da tabela Server*</span><span class="sxs-lookup"><span data-stu-id="212b5-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="212b5-118">nx_dhcpv6_add_client_record Adicionar *um registo de cliente DHCPv6 à tabela do Servidor*</span><span class="sxs-lookup"><span data-stu-id="212b5-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="212b5-119">nx_dhcpv6_retrieve_client_record Recuperar *um registo de cliente da tabela do Servidor*</span><span class="sxs-lookup"><span data-stu-id="212b5-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="212b5-120">nx_dhcpv6_server_interface_set Definir *o índice de interface para os serviços do Servidor DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="212b5-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="212b5-121">nx_dhcpv6_server_option_request_handler_set *Definir o manipulador de pedidos de opção*</span><span class="sxs-lookup"><span data-stu-id="212b5-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="212b5-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="212b5-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="212b5-123">Definir o servidor DNS da rede</span><span class="sxs-lookup"><span data-stu-id="212b5-123">Set the network DNS server</span></span>

<span data-ttu-id="212b5-124">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="212b5-125">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-125">**Description**</span></span>

<span data-ttu-id="212b5-126">Este serviço carrega o Servidor DHCPv6 com o endereço do servidor DNS para a interface de rede Server DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="212b5-127">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-127">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-128">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-129">**dns_ipv6_address** Ponteiro para o servidor DNS</span><span class="sxs-lookup"><span data-stu-id="212b5-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="212b5-130">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-130">**Return Values**</span></span>

- <span data-ttu-id="212b5-131">**NX_SUCCESS** (0x00) DNS Serversaved para a instância do servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="212b5-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido</span><span class="sxs-lookup"><span data-stu-id="212b5-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="212b5-133">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-134">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-134">**Allowed From**</span></span>

<span data-ttu-id="212b5-135">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-135">Application Code</span></span>

<span data-ttu-id="212b5-136">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="212b5-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="212b5-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="212b5-138">Criar a lista de endereços IP do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-138">Create the Server IP address list</span></span>

<span data-ttu-id="212b5-139">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="212b5-140">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-140">**Description**</span></span>

<span data-ttu-id="212b5-141">Este serviço cria a lista de endereços IP especificada pelos endereços de início e fim do intervalo de endereços atribuível do Servidor.</span><span class="sxs-lookup"><span data-stu-id="212b5-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="212b5-142">Os endereços de início e de fim devem corresponder ao prefixo do endereço de interface do Servidor (deve estar no mesmo link que a interface Server DHCPv6).</span><span class="sxs-lookup"><span data-stu-id="212b5-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="212b5-143">O número de endereços realmente adicionados é devolvido.</span><span class="sxs-lookup"><span data-stu-id="212b5-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="212b5-144">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-144">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-145">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-146">**start_ipv6_address** Início de endereços para adicionar</span><span class="sxs-lookup"><span data-stu-id="212b5-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="212b5-147">**end_ipv6_address** Fim dos endereços para adicionar</span><span class="sxs-lookup"><span data-stu-id="212b5-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="212b5-148">\***addresses_added** Saída de endereços adicionados</span><span class="sxs-lookup"><span data-stu-id="212b5-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="212b5-149">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-149">**Return Values**</span></span>

- <span data-ttu-id="212b5-150">**NX_SUCCESS** (0x00) lista de endereços IP criada com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="212b5-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido</span><span class="sxs-lookup"><span data-stu-id="212b5-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="212b5-152">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-153">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-153">**Allowed From**</span></span>

<span data-ttu-id="212b5-154">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-154">Application Code</span></span>

<span data-ttu-id="212b5-155">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="212b5-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="212b5-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="212b5-157">Reserva especificada gama de endereços IP</span><span class="sxs-lookup"><span data-stu-id="212b5-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="212b5-158">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="212b5-159">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-159">**Description**</span></span>

<span data-ttu-id="212b5-160">Este serviço reserva o intervalo de endereços IP especificado pelos endereços de início e fim.</span><span class="sxs-lookup"><span data-stu-id="212b5-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="212b5-161">Estes endereços devem estar dentro do intervalo de endereços IP do servidor previamente criado.</span><span class="sxs-lookup"><span data-stu-id="212b5-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="212b5-162">Estes endereços não serão atribuídos a nenhum Cliente pelo Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="212b5-163">Os endereços de início e de fim devem corresponder ao prefixo do endereço de interface do Servidor (deve estar no mesmo link que a interface de rede Do Servidor DHCPv6).</span><span class="sxs-lookup"><span data-stu-id="212b5-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="212b5-164">O número de endereços realmente reservados é devolvido.</span><span class="sxs-lookup"><span data-stu-id="212b5-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="212b5-165">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-165">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-166">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-167">**start_ipv6_address** Início de endereços para reservar</span><span class="sxs-lookup"><span data-stu-id="212b5-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="212b5-168">**end_ipv6_address** Fim dos endereços para reservar</span><span class="sxs-lookup"><span data-stu-id="212b5-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="212b5-169">\***addresses_reserved** Número de endereços reservados</span><span class="sxs-lookup"><span data-stu-id="212b5-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="212b5-170">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-170">**Return Values**</span></span>

- <span data-ttu-id="212b5-171">**NX_SUCCESS** (0x00) Mensagem DE LIBERTAÇÃO criada e processada com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="212b5-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) É fornecido um endereço inválido</span><span class="sxs-lookup"><span data-stu-id="212b5-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="212b5-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Endereço inicial não encontrado na lista de endereços do Servidor.</span><span class="sxs-lookup"><span data-stu-id="212b5-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="212b5-174">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-175">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-175">**Allowed From**</span></span>

<span data-ttu-id="212b5-176">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-176">Application Code</span></span>

<span data-ttu-id="212b5-177">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="212b5-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="212b5-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="212b5-179">Criar a instância do Servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="212b5-180">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="212b5-181">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-181">**Description**</span></span>

<span data-ttu-id="212b5-182">Este serviço cria a tarefa do Servidor DHCPv6 com a entrada especificada.</span><span class="sxs-lookup"><span data-stu-id="212b5-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="212b5-183">Os manipuladores de retorno são entradas opcionais.</span><span class="sxs-lookup"><span data-stu-id="212b5-183">The callback handlers are optional input.</span></span> <span data-ttu-id="212b5-184">São necessários o ponteiro da pilha, a instância IP e a entrada do pacote.</span><span class="sxs-lookup"><span data-stu-id="212b5-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="212b5-185">A instância IP e a piscina de pacotes já devem ser criadas.</span><span class="sxs-lookup"><span data-stu-id="212b5-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="212b5-186">O utilizador é encorajado a ligar para nx_dhcpv6_server_option_request_handler_set para definir o manipulador de pedidos de opção.</span><span class="sxs-lookup"><span data-stu-id="212b5-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="212b5-187">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-187">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-188">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-189">**ip_ptr** Ponteiro para a instância IP</span><span class="sxs-lookup"><span data-stu-id="212b5-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="212b5-190">**name_str** Ponteiro para o nome do servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="212b5-191">**packet_pool_ptr** Ponteiro para a piscina de pacotes do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="212b5-192">**stack_ptr** Ponteiro para memória de pilha de servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="212b5-193">**stack_size** Tamanho da memória da pilha do servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="212b5-194">**dhcpv6_address_declined_handler** Ponteiro para o cliente declinar ou libertar o manipulador de mensagens</span><span class="sxs-lookup"><span data-stu-id="212b5-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="212b5-195">**dhcpv6_option_request_handler** Ponteiro para opções pedir opção handler</span><span class="sxs-lookup"><span data-stu-id="212b5-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="212b5-196">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-196">**Return Values**</span></span>

- <span data-ttu-id="212b5-197">**NX_SUCCESS** (0x00) Servidor retomado com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="212b5-198">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="212b5-199">NX_DHCPV6_PARAM_ERROR Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="212b5-200">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-200">**Allowed From**</span></span>

<span data-ttu-id="212b5-201">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-201">Application Code</span></span>

<span data-ttu-id="212b5-202">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="212b5-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="212b5-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="212b5-204">Eliminar o Servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="212b5-205">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="212b5-206">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-206">**Description**</span></span>

<span data-ttu-id="212b5-207">Este serviço elimina a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.</span><span class="sxs-lookup"><span data-stu-id="212b5-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="212b5-208">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-208">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-209">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-210">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-210">**Return Values**</span></span>

- <span data-ttu-id="212b5-211">**servidor NX_SUCCESS** (0x00) eliminado com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="212b5-212">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-213">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-213">**Allowed From**</span></span>

<span data-ttu-id="212b5-214">Fios</span><span class="sxs-lookup"><span data-stu-id="212b5-214">Threads</span></span>

<span data-ttu-id="212b5-215">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="212b5-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="212b5-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="212b5-217">Retomar a tarefa do servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="212b5-218">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="212b5-219">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-219">**Description**</span></span>

<span data-ttu-id="212b5-220">Este serviço retoma a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.</span><span class="sxs-lookup"><span data-stu-id="212b5-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="212b5-221">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-221">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-222">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-223">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-223">**Return Values**</span></span>

- <span data-ttu-id="212b5-224">**NX_SUCCESS** (0x00) Servidor retomado com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="212b5-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Servidor já está em execução</span><span class="sxs-lookup"><span data-stu-id="212b5-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="212b5-226">**estado** (variável) ThreadX e NetX Duo estado de erro</span><span class="sxs-lookup"><span data-stu-id="212b5-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="212b5-227">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-228">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-228">**Allowed From**</span></span>

<span data-ttu-id="212b5-229">Fios</span><span class="sxs-lookup"><span data-stu-id="212b5-229">Threads</span></span>

<span data-ttu-id="212b5-230">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="212b5-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="212b5-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="212b5-232">Suspender a tarefa do servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="212b5-233">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="212b5-234">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-234">**Description**</span></span>

<span data-ttu-id="212b5-235">Este serviço suspende a tarefa do Servidor DHCPv6 e qualquer pedido que o Servidor estava a processar.</span><span class="sxs-lookup"><span data-stu-id="212b5-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="212b5-236">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-236">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-237">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-238">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-238">**Return Values**</span></span>

- <span data-ttu-id="212b5-239">**NX_SUCCESS** (0x00) Servidor retomado com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="212b5-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Servidor ainda não foi iniciado</span><span class="sxs-lookup"><span data-stu-id="212b5-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="212b5-241">**Estado** (variável) ThreadX e Estado de erro da NetX Duo</span><span class="sxs-lookup"><span data-stu-id="212b5-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="212b5-242">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-243">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-243">**Allowed From**</span></span>

<span data-ttu-id="212b5-244">Fios</span><span class="sxs-lookup"><span data-stu-id="212b5-244">Threads</span></span>

<span data-ttu-id="212b5-245">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="212b5-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="212b5-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="212b5-247">Inicie a tarefa do Servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="212b5-248">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="212b5-249">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-249">**Description**</span></span>

<span data-ttu-id="212b5-250">Este serviço inicia a tarefa do Servidor DHCPv6 e lê o Servidor para processar pedidos de aplicação para receber mensagens do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="212b5-251">Verifica que a instância do Servidor tem informações suficientes (Server DUID), cria e liga a tomada UDP para enviar e receber mensagens DHCPv6, e ativa os temporizadores para manter o tempo de sessão e a expiração do aluguer de IP.</span><span class="sxs-lookup"><span data-stu-id="212b5-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-252">Antes de o Servidor DHCPv6 poder ser executado, a aplicação do anfitrião é responsável pela criação do intervalo de endereços IP a partir do qual o Servidor pode atribuir endereços IP.</span><span class="sxs-lookup"><span data-stu-id="212b5-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="212b5-253">É também responsável pela definição da interface Server DUID e DHCPv6 (ver *nx_dhcpv6_server_duid_set* e *nx_dhcpv6_server_interface_set* respectivamente.</span><span class="sxs-lookup"><span data-stu-id="212b5-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="212b5-254">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-254">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-255">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-256">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-256">**Return Values**</span></span>

- <span data-ttu-id="212b5-257">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Servidor já está em execução</span><span class="sxs-lookup"><span data-stu-id="212b5-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="212b5-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Servidor não tem endereços atribuíveis para arrendar</span><span class="sxs-lookup"><span data-stu-id="212b5-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="212b5-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Índice de endereço global não definido</span><span class="sxs-lookup"><span data-stu-id="212b5-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="212b5-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) Nenhum servidor DUID criado</span><span class="sxs-lookup"><span data-stu-id="212b5-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="212b5-262">**estado** (variável) ThreadX e NetX Duo estado de erro</span><span class="sxs-lookup"><span data-stu-id="212b5-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="212b5-263">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-264">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-264">**Allowed From**</span></span>

<span data-ttu-id="212b5-265">Fios</span><span class="sxs-lookup"><span data-stu-id="212b5-265">Threads</span></span>

<span data-ttu-id="212b5-266">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="212b5-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="212b5-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="212b5-268">Obtenha um arrendamento de endereço IP na tabela Do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="212b5-269">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="212b5-270">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-270">**Description**</span></span>

<span data-ttu-id="212b5-271">Este serviço recupera um registo de locação de endereço IP da tabela Server na localização do índice de tabela especificado.</span><span class="sxs-lookup"><span data-stu-id="212b5-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="212b5-272">Isto pode ser feito antes ou depois de recuperar os dados do registo do Cliente.</span><span class="sxs-lookup"><span data-stu-id="212b5-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="212b5-273">A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="212b5-274">Não faz diferença em que ordem os dados de locação IP e dados de registo do Cliente são guardados para memória nãovolárida.</span><span class="sxs-lookup"><span data-stu-id="212b5-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-275">Não é aconselhável copiar dados para ou a partir de tabelas do Servidor sem parar ou suspender primeiro o Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="212b5-276">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-276">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-277">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-278">**table_index** Índice de tabela para armazenar arrendamento em</span><span class="sxs-lookup"><span data-stu-id="212b5-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="212b5-279">**lease_IP_address** Ponteiro para endereço IP alugado ao Cliente</span><span class="sxs-lookup"><span data-stu-id="212b5-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="212b5-280">**T1** Cliente pediu tempo de renovação</span><span class="sxs-lookup"><span data-stu-id="212b5-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="212b5-281">**T2** Cliente solicitou tempo de reencadernação</span><span class="sxs-lookup"><span data-stu-id="212b5-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="212b5-282">**valid_lifetime** Arrendamento de clientes torna-se depreciado</span><span class="sxs-lookup"><span data-stu-id="212b5-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="212b5-283">**preferred_lifetime** Arrendamento de cliente torna-se inválido</span><span class="sxs-lookup"><span data-stu-id="212b5-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="212b5-284">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-284">**Return Values**</span></span>

- <span data-ttu-id="212b5-285">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Entrada de dados de locação IP inválida</span><span class="sxs-lookup"><span data-stu-id="212b5-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="212b5-287">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-288">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-288">**Allowed From**</span></span>

<span data-ttu-id="212b5-289">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-289">Application code</span></span>

<span data-ttu-id="212b5-290">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="212b5-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="212b5-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="212b5-292">Adicione um aluguer de endereço IP à tabela Do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="212b5-293">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="212b5-294">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-294">**Description**</span></span>

<span data-ttu-id="212b5-295">Este serviço carrega dados de locação IP de uma sessão anterior do Servidor DHCPv6 de memória não volátil para a tabela de locação do Servidor.</span><span class="sxs-lookup"><span data-stu-id="212b5-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="212b5-296">Isto não é necessário se o Servidor estiver em execução pela primeira vez e não tiver dados de locação prévia.</span><span class="sxs-lookup"><span data-stu-id="212b5-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="212b5-297">Se for esse o caso, a aplicação do anfitrião deve criar um intervalo de endereços IP para a atribuição de endereços IP, utilizando o serviço *nx_dhcpv6_create_ip_address_range.*</span><span class="sxs-lookup"><span data-stu-id="212b5-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="212b5-298">Os dados são suficientes para reconstruir um registo de arrendamento DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="212b5-299">O índice de tabela não precisa de ser especificado.</span><span class="sxs-lookup"><span data-stu-id="212b5-299">The table index need not be specified.</span></span> <span data-ttu-id="212b5-300">Se for definido para 0xFFFFFFFF (infinito) o Servidor DHCPv6 encontrará a próxima ranhura disponível para copiar os dados para.</span><span class="sxs-lookup"><span data-stu-id="212b5-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-301">O upload dos dados de locação IP deve ser feito antes de carregar os registos do Cliente; ambos devem ser feitos antes de (re)iniciar o Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="212b5-302">A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="212b5-303">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-303">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-304">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-305">**table_index** Índice de tabela para armazenar arrendamento em</span><span class="sxs-lookup"><span data-stu-id="212b5-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="212b5-306">**lease_IP_address** Ponteiro para endereço IP alugado ao Cliente</span><span class="sxs-lookup"><span data-stu-id="212b5-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="212b5-307">**T1** Cliente pediu tempo de renovação</span><span class="sxs-lookup"><span data-stu-id="212b5-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="212b5-308">**T2** Cliente solicitou tempo de reencadernação</span><span class="sxs-lookup"><span data-stu-id="212b5-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="212b5-309">**valid_lifetime** Arrendamento de clientes torna-se depreciado</span><span class="sxs-lookup"><span data-stu-id="212b5-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="212b5-310">**preferred_lifetime** Arrendamento de cliente torna-se inválido</span><span class="sxs-lookup"><span data-stu-id="212b5-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="212b5-311">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-311">**Return Values**</span></span>

- <span data-ttu-id="212b5-312">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) Não há espaço para mais dados de locação\*\*</span><span class="sxs-lookup"><span data-stu-id="212b5-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="212b5-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Os dados de locação não parecem estar ligados à interface do Servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="212b5-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Entrada de dados de locação IP inválida</span><span class="sxs-lookup"><span data-stu-id="212b5-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="212b5-316">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-317">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-317">**Allowed From**</span></span>

<span data-ttu-id="212b5-318">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-318">Application code</span></span>

<span data-ttu-id="212b5-319">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="212b5-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="212b5-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="212b5-321">Adicione um registo de Cliente à tabela do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="212b5-322">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="212b5-323">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-323">**Description**</span></span>

<span data-ttu-id="212b5-324">Este serviço copia os dados do Cliente de memória não volátil para a tabela do Servidor um registo de cada vez.</span><span class="sxs-lookup"><span data-stu-id="212b5-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="212b5-325">Isto só é necessário se o Servidor estiver a ser reiniciado e tiver dados do Cliente de uma sessão anterior para restaurar a memória.</span><span class="sxs-lookup"><span data-stu-id="212b5-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="212b5-326">Se um Servidor não tiver dados anteriores, o Servidor DHCPv6 rubricará a tabela cliente para poder adicionar registos de Clientes.</span><span class="sxs-lookup"><span data-stu-id="212b5-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="212b5-327">Não é necessário especificar o índice de tabela.</span><span class="sxs-lookup"><span data-stu-id="212b5-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="212b5-328">Se estiver definido para 0xFFFFFFFF (infinito) o Servidor DHCPv6 localizará a próxima ranhura disponível.</span><span class="sxs-lookup"><span data-stu-id="212b5-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="212b5-329">O Servidor DHCPv6 pode reconstruir um registo do Cliente a partir destes dados.</span><span class="sxs-lookup"><span data-stu-id="212b5-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-330">A aplicação do anfitrião DEVE carregar os dados de locação IP ANTES dos dados de gravação do Cliente.</span><span class="sxs-lookup"><span data-stu-id="212b5-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="212b5-331">Isto é de modo que internamente o Servidor DHCPv6 pode cruzar as tabelas de modo que cada registo do Cliente seja acompanhado com o seu registo de locação IP correspondente nas respetivas tabelas.</span><span class="sxs-lookup"><span data-stu-id="212b5-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="212b5-332">Consulte *nx_dhcpv6_add_ip_address_lease* para obter mais informações sobre o upload de dados de locação IP a partir da memória.</span><span class="sxs-lookup"><span data-stu-id="212b5-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-333">Dependendo do tipo DUID, nem todos os dados devem ser fornecidos.</span><span class="sxs-lookup"><span data-stu-id="212b5-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="212b5-334">Por exemplo, se um Cliente tiver um tipo DUID atribuído ao fornecedor, pode enviar zero para parâmetros DUID Link Layer (endereço MAC, tipo de hardware, tempo DUID).</span><span class="sxs-lookup"><span data-stu-id="212b5-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="212b5-335">A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="212b5-336">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-336">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-337">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-338">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-338">**Return Values**</span></span>

- <span data-ttu-id="212b5-339">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-340">**NX_ INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro\*\*</span><span class="sxs-lookup"><span data-stu-id="212b5-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="212b5-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) Não há slots vazios para adicionar outro registo do Cliente</span><span class="sxs-lookup"><span data-stu-id="212b5-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="212b5-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Endereço atribuído ao cliente não encontrado na tabela de locação do Servidor.</span><span class="sxs-lookup"><span data-stu-id="212b5-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="212b5-343">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-344">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-344">**Allowed From**</span></span>

<span data-ttu-id="212b5-345">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-345">Application code</span></span>

<span data-ttu-id="212b5-346">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="212b5-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="212b5-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="212b5-348">Recupere um registo de Cliente da tabela do Servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="212b5-349">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="212b5-350">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-350">**Description**</span></span>

<span data-ttu-id="212b5-351">Este serviço copia os dados essenciais da tabela de registos do Cliente do Servidor para armazenamento para memória não volátil.</span><span class="sxs-lookup"><span data-stu-id="212b5-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="212b5-352">O Servidor pode reconstruir um registo de Cliente adequado a partir desses dados no processo inverso (enviando dados para a tabela Do Servidor).</span><span class="sxs-lookup"><span data-stu-id="212b5-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="212b5-353">Independentemente do tipo DUID, nenhum dos ponteiros pode ser ponteiros NULO; os dados são inicializados a zero para todos os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="212b5-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="212b5-354">Por exemplo, se o tipo DUID do Cliente for Link Layer Plus Time, o número do fornecedor é devolvido como zero e o ID privado é uma cadeia vazia.</span><span class="sxs-lookup"><span data-stu-id="212b5-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="212b5-355">A capacidade de armazenar e recuperar dados entre o Servidor DHCPv6 e a memória não volátil é um requisito do protocolo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="212b5-356">Não faz diferença em que ordem os dados de locação IP e dados de registo do Cliente são guardados para memória nãovolárida.</span><span class="sxs-lookup"><span data-stu-id="212b5-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-357">Não é aconselhável copiar dados para ou a partir de tabelas do Servidor sem parar ou suspender primeiro o Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="212b5-358">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-358">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-359">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-360">**table_index** Índice na tabela de clientes do Server</span><span class="sxs-lookup"><span data-stu-id="212b5-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="212b5-361">**message_xid** ID de transação de servidor de cliente</span><span class="sxs-lookup"><span data-stu-id="212b5-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="212b5-362">**client_address** Endereço IPv6 alugado ao Cliente</span><span class="sxs-lookup"><span data-stu-id="212b5-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="212b5-363">**client_state** Estado do Cliente DHCPv6 (por exemplo, ligado)</span><span class="sxs-lookup"><span data-stu-id="212b5-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="212b5-364">**IP_lease_time_accrued** O tempo expirou no arrendamento já **dhcpv6_server_ptr** Pointer para o SERVIDOR DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-365">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="212b5-366">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-366">**Return Values**</span></span>

- <span data-ttu-id="212b5-367">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Dados DUID inválidos ou inconsistentes</span><span class="sxs-lookup"><span data-stu-id="212b5-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="212b5-369">**NX_PTR_ERROR** (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="212b5-370">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="212b5-371">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-371">**Allowed From**</span></span>

<span data-ttu-id="212b5-372">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-372">Application code</span></span>

<span data-ttu-id="212b5-373">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="212b5-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="212b5-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="212b5-375">Definir o índice de interface para a interface do Servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="212b5-376">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="212b5-377">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-377">**Description**</span></span>

<span data-ttu-id="212b5-378">Este serviço define a interface de rede na qual o Servidor DHCPv6 lida com pedidos do Cliente DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="212b5-379">Não que para versões do NetX Duo que não suportem multihome, o valor da interface está em incumprimento a zero.</span><span class="sxs-lookup"><span data-stu-id="212b5-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="212b5-380">O índice global de endereços é necessário para obter o endereço global do Servidor na sua interface DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="212b5-381">Isto é usado pela lógica DHCPv6 para garantir que endereços de locação e outros dados DHCPv6 estão em ligação com o Servidor DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="212b5-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="212b5-382">Isto deve ser chamado antes do início do servidor DHCPv6, mesmo para aplicações em dispositivos únicos domésticos ou sem suporte multihome.</span><span class="sxs-lookup"><span data-stu-id="212b5-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="212b5-383">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-383">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-384">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-385">**iface_index** Interface do servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="212b5-386">**ga_address_index** Índice de endereço global do Servidor na tabela de endereços ip do servidor</span><span class="sxs-lookup"><span data-stu-id="212b5-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="212b5-387">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-387">**Return Values**</span></span>

- <span data-ttu-id="212b5-388">**NX_SUCCESS** (0x00) Servidor com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="212b5-389">**NX_INVALID_INTERFACE** (0x4C) Interface não existe</span><span class="sxs-lookup"><span data-stu-id="212b5-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="212b5-390">NX_NO_INTERFACE_ADDRESS (0x50) O índice global excede os endereços IPv6 máximos de instância IP (NX_MAX_IPV6_ADDRESSES)</span><span class="sxs-lookup"><span data-stu-id="212b5-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="212b5-391">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-392">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-392">**Allowed From**</span></span>

<span data-ttu-id="212b5-393">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-393">Application code</span></span>

<span data-ttu-id="212b5-394">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="212b5-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="212b5-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="212b5-396">Desaprova o Servidor DUID para pacotes DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="212b5-397">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="212b5-398">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-398">**Description**</span></span>

<span data-ttu-id="212b5-399">Este serviço define o Servidor DUID e deve ser chamado antes da aplicação do anfitrião iniciar o Servidor.</span><span class="sxs-lookup"><span data-stu-id="212b5-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="212b5-400">Para os tipos DUID de camada de ligação e de ligação, a aplicação do anfitrião deve fornecer os dados de endereços de hardware e MAC.</span><span class="sxs-lookup"><span data-stu-id="212b5-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="212b5-401">Para os DUIDs de tempo de ligação, o ponteiro de tempo deve apontar para um tempo válido.</span><span class="sxs-lookup"><span data-stu-id="212b5-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="212b5-402">O número de segundos desde 1 de janeiro de 2000 é um valor típico de sementes.</span><span class="sxs-lookup"><span data-stu-id="212b5-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="212b5-403">Se o tipo de DuID do Servidor for a empresa, o tipo atribuído pelo fornecedor, o DUID será criado a partir das opções configuráveis do utilizador NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID e NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, e os valores de tempo e endereço MAC podem ser definidos como NU.</span><span class="sxs-lookup"><span data-stu-id="212b5-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="212b5-404">É da responsabilidade da aplicação anfitriã guardar os parâmetros DO SERVIDOR DUID para memória nãovolárida de modo a que utilize o mesmo DUID em mensagens para clientes entre reboots.</span><span class="sxs-lookup"><span data-stu-id="212b5-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="212b5-405">Este é um requisito do protocolo DHCPv6 (RFC 3315).</span><span class="sxs-lookup"><span data-stu-id="212b5-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="212b5-406">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-406">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-407">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-408">**duid_type** Tipo DHCPv6 Server DUID</span><span class="sxs-lookup"><span data-stu-id="212b5-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="212b5-409">**hardware_type** Tipo de hardware (por exemplo, Ethernet)</span><span class="sxs-lookup"><span data-stu-id="212b5-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="212b5-410">**mac_address_msw** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-411">**mac_address_lsw** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-412">**tempo** Valor temporal para DUID</span><span class="sxs-lookup"><span data-stu-id="212b5-412">**time** Time value for DUID</span></span>

<span data-ttu-id="212b5-413">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-413">**Return Values**</span></span>

- <span data-ttu-id="212b5-414">**servidor NX_SUCCESS** (0x00) suspenso com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="212b5-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Tipo DUID desconhecido ou não suportado</span><span class="sxs-lookup"><span data-stu-id="212b5-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="212b5-416">**NX_INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="212b5-417">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-418">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-418">**Allowed From**</span></span>

<span data-ttu-id="212b5-419">Código de aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-419">Application code</span></span>

<span data-ttu-id="212b5-420">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="212b5-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="212b5-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="212b5-422">Desajei o manipulador de pedido de opção para a instância do servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="212b5-423">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="212b5-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="212b5-424">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="212b5-424">**Description**</span></span>

<span data-ttu-id="212b5-425">Este serviço define o controlador de pedido de opção alargado DHCPv6 Server.</span><span class="sxs-lookup"><span data-stu-id="212b5-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="212b5-426">**Parâmetros de Entrada**</span><span class="sxs-lookup"><span data-stu-id="212b5-426">**Input Parameters**</span></span>

- <span data-ttu-id="212b5-427">**dhcpv6_server_ptr** Ponteiro para o servidor DHCPv6</span><span class="sxs-lookup"><span data-stu-id="212b5-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="212b5-428">**dhcpv6_option_request_handler_extended** Ponteiro para o controlador de pedido de opções alargadas</span><span class="sxs-lookup"><span data-stu-id="212b5-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="212b5-429">**Valores de devolução**</span><span class="sxs-lookup"><span data-stu-id="212b5-429">**Return Values**</span></span>

- <span data-ttu-id="212b5-430">**NX_SUCCESS** (0x00) Servidor retomado com sucesso</span><span class="sxs-lookup"><span data-stu-id="212b5-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="212b5-431">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="212b5-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="212b5-432">**Permitido a partir de**</span><span class="sxs-lookup"><span data-stu-id="212b5-432">**Allowed From**</span></span>

<span data-ttu-id="212b5-433">Código de Aplicação</span><span class="sxs-lookup"><span data-stu-id="212b5-433">Application Code</span></span>

<span data-ttu-id="212b5-434">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="212b5-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```