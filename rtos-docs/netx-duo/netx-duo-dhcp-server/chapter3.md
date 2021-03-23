---
title: Capítulo 3 - Descrição dos serviços de servidores Azure RTOS NetX Duo DHCP
description: Este capítulo contém uma descrição de todos os serviços do NetX Duo DHCP Server (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826107"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="2c131-103">Capítulo 3 - Descrição dos Serviços de Servidor Azure RTOS NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="2c131-104">Este capítulo contém uma descrição de todos os serviços do NetX Duo DHCP Server (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="2c131-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="2c131-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="2c131-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="2c131-106">nx_dhcp_server criar</span><span class="sxs-lookup"><span data-stu-id="2c131-106">nx_dhcp_server create</span></span>

<span data-ttu-id="2c131-107">Criar uma instância do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="2c131-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-109">Description</span></span>

<span data-ttu-id="2c131-110">Este serviço cria uma instância do Servidor DHCP com uma instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2c131-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c131-111">A aplicação deve certificar-se de que o pacote criado para o serviço ip create tem uma carga útil mínima de 548 byte, não incluindo os cabeçalhos UDP, IP e Ethernet.</span><span class="sxs-lookup"><span data-stu-id="2c131-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-112">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-112">Input Parameters</span></span>

- <span data-ttu-id="2c131-113">**dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="2c131-114">**ip_ptr** Indicação para a instância IP do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="2c131-115">**stack_ptr** Localização da pilha do servidor do ponteiro DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="2c131-116">**stack_size Tamanho da pilha do servidor DHCP** input_address_list ponteiro para a lista de endereços IP do Servidor</span><span class="sxs-lookup"><span data-stu-id="2c131-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="2c131-117">**name_ptr Pointer para o nome do servidor DHCP** packet_pool_ptr ponte de pacotes do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-118">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-118">Return Values</span></span>

- <span data-ttu-id="2c131-119">**NX_SUCCESS** (0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2c131-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2c131-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Carga útil do pacote erro demasiado pequeno</span><span class="sxs-lookup"><span data-stu-id="2c131-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="2c131-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) A lista de opções do servidor está vazia</span><span class="sxs-lookup"><span data-stu-id="2c131-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="2c131-122">NX_DHCP_PARAMETER_ERROR (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c131-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="2c131-123">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c131-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2c131-124">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-125">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-125">Allowed From</span></span>

<span data-ttu-id="2c131-126">Aplicação</span><span class="sxs-lookup"><span data-stu-id="2c131-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="2c131-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="2c131-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="2c131-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="2c131-129">Criar uma piscina de endereços IP</span><span class="sxs-lookup"><span data-stu-id="2c131-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-130">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="2c131-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-131">Description</span></span>

<span data-ttu-id="2c131-132">Este serviço cria um conjunto específico de interface de rede de endereços IP disponíveis para o servidor DHCP especificado para atribuir.</span><span class="sxs-lookup"><span data-stu-id="2c131-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="2c131-133">Os endereços IP de início e fim devem corresponder à interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="2c131-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="2c131-134">O número real de endereços IP adicionados pode ser inferior ao total dos endereços se a lista de endereços IP não for suficientemente grande (que é definida no parâmetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurável do utilizador).</span><span class="sxs-lookup"><span data-stu-id="2c131-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-135">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-135">Input Parameters</span></span>

- <span data-ttu-id="2c131-136">**dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="2c131-137">**iface_index** Índice correspondente à interface de rede</span><span class="sxs-lookup"><span data-stu-id="2c131-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="2c131-138">**start_ip_address** Primeiro endereço IP disponível</span><span class="sxs-lookup"><span data-stu-id="2c131-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="2c131-139">**end_ip_address** Último do endereço IP disponível</span><span class="sxs-lookup"><span data-stu-id="2c131-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="2c131-140">**addresses_added** Número de endereços IP adicionados à lista</span><span class="sxs-lookup"><span data-stu-id="2c131-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-141">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-141">Return Values</span></span>

- <span data-ttu-id="2c131-142">**NX_SUCCESS** (0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2c131-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2c131-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Índice não corresponde a endereços</span><span class="sxs-lookup"><span data-stu-id="2c131-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="2c131-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Entrada de endereço inválido</span><span class="sxs-lookup"><span data-stu-id="2c131-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="2c131-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Endereços ilógicos de início/fim</span><span class="sxs-lookup"><span data-stu-id="2c131-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="2c131-146">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-147">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-147">Allowed From</span></span>

<span data-ttu-id="2c131-148">Aplicação</span><span class="sxs-lookup"><span data-stu-id="2c131-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="2c131-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="2c131-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="2c131-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="2c131-151">Remova o registo do Cliente da base de dados do Servidor</span><span class="sxs-lookup"><span data-stu-id="2c131-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-152">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="2c131-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-153">Description</span></span>

<span data-ttu-id="2c131-154">Este serviço limpa o registo do Cliente da base de dados do Servidor.</span><span class="sxs-lookup"><span data-stu-id="2c131-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-155">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-155">Input Parameters</span></span>

- <span data-ttu-id="2c131-156">**dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="2c131-157">**dhcp_client_ptr Ponte para o Cliente DHCP para remover**</span><span class="sxs-lookup"><span data-stu-id="2c131-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-158">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-158">Return Values</span></span>

- <span data-ttu-id="2c131-159">**NX_SUCCESS** (0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2c131-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2c131-160">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2c131-161">NX_CALLER_ERROR (0x11) Não thread caller de serviço</span><span class="sxs-lookup"><span data-stu-id="2c131-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-162">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-162">Allowed From</span></span>

<span data-ttu-id="2c131-163">Aplicação</span><span class="sxs-lookup"><span data-stu-id="2c131-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="2c131-164">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="2c131-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="2c131-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="2c131-166">Definir parâmetros de rede para opções DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="2c131-168">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-168">Description</span></span>

<span data-ttu-id="2c131-169">Este serviço define valores predefinidos para parâmetros críticos de rede para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="2c131-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="2c131-170">O servidor DHCP incluirá estas opções na sua OFERTA e respostas ACK ao Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="2c131-171">Se os parâmetros de interface definidos pelo anfitrião em que um servidor DHCP está em funcionamento, os parâmetros ficarão incumpridos da seguinte forma: o router definido para o gateway de interface principal para o próprio servidor DHCP, o endereço do servidor DNS para o próprio servidor DHCP e a máscara de sub-rede para a mesma que a interface do servidor DHCP está configurada.</span><span class="sxs-lookup"><span data-stu-id="2c131-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-172">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-172">Input Parameters</span></span>

- <span data-ttu-id="2c131-173">**dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="2c131-174">**iface_index** Índice correspondente à interface de rede</span><span class="sxs-lookup"><span data-stu-id="2c131-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="2c131-175">**subnet_mask** Máscara de sub-rede para rede de clientes</span><span class="sxs-lookup"><span data-stu-id="2c131-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="2c131-176">**default_gateway_address** Endereço IP do router do cliente</span><span class="sxs-lookup"><span data-stu-id="2c131-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="2c131-177">**dns_server_address** Servidor DNS para a rede do Cliente</span><span class="sxs-lookup"><span data-stu-id="2c131-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-178">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-178">Return Values</span></span>

- <span data-ttu-id="2c131-179">**NX_SUCCESS** (0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2c131-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="2c131-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Índice não corresponde a endereços</span><span class="sxs-lookup"><span data-stu-id="2c131-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="2c131-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Parâmetros de rede inválidos</span><span class="sxs-lookup"><span data-stu-id="2c131-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="2c131-182">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-183">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-183">Allowed From</span></span>

<span data-ttu-id="2c131-184">Aplicação</span><span class="sxs-lookup"><span data-stu-id="2c131-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="2c131-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="2c131-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="2c131-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="2c131-187">Excluir uma instância do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-188">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2c131-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-189">Description</span></span>

<span data-ttu-id="2c131-190">Este serviço elimina uma instância do Servidor DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2c131-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-191">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-191">Input Parameters</span></span>

- <span data-ttu-id="2c131-192">**dhcp_ptr** Ponteiro para uma instância do Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-193">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-193">Return Values</span></span>

- <span data-ttu-id="2c131-194">**NX_SUCCESS** (0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="2c131-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="2c131-195">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2c131-196">NX_DHCP_PARAMETER_ERROR (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c131-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="2c131-197">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c131-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-198">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-198">Allowed From</span></span>

<span data-ttu-id="2c131-199">Fios</span><span class="sxs-lookup"><span data-stu-id="2c131-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2c131-200">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="2c131-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="2c131-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="2c131-202">Iniciar o processamento do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-203">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2c131-204">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-204">Description</span></span>

<span data-ttu-id="2c131-205">Este serviço inicia o processamento do Servidor DHCP, que inclui a criação de uma tomada UDP de servidor, ligação da porta DHCP e espera receber os pedidos do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-206">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-206">Input Parameters</span></span>

- <span data-ttu-id="2c131-207">**dhcp_ptr** Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="2c131-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-208">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-208">Return Values</span></span>

- <span data-ttu-id="2c131-209">**NX_SUCCESS** (0x00) Início do Servidor de Sucesso.</span><span class="sxs-lookup"><span data-stu-id="2c131-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="2c131-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="2c131-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2c131-211">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2c131-212">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c131-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2c131-213">NX_DHCP_PARAMETER_ERROR (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c131-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-214">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-214">Allowed From</span></span>

<span data-ttu-id="2c131-215">Fios</span><span class="sxs-lookup"><span data-stu-id="2c131-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2c131-216">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="2c131-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="2c131-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="2c131-218">Para o processamento do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="2c131-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="2c131-219">Prototype</span><span class="sxs-lookup"><span data-stu-id="2c131-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="2c131-220">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c131-220">Description</span></span>

<span data-ttu-id="2c131-221">Este serviço impede o processamento do Servidor DHCP, que inclui receber pedidos do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2c131-222">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="2c131-222">Input Parameters</span></span>

- <span data-ttu-id="2c131-223">**dhcp_ptr** Indicação para a instância do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="2c131-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="2c131-224">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="2c131-224">Return Values</span></span>

- <span data-ttu-id="2c131-225">**NX_SUCCESS** (0x00) Paragem DHCP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="2c131-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="2c131-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="2c131-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="2c131-227">NX_PTR_ERROR (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="2c131-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="2c131-228">NX_CALLER_ERROR (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="2c131-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="2c131-229">NX_DHCP_PARAMETER_ERROR (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="2c131-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2c131-230">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="2c131-230">Allowed From</span></span>

<span data-ttu-id="2c131-231">Fios</span><span class="sxs-lookup"><span data-stu-id="2c131-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2c131-232">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2c131-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
