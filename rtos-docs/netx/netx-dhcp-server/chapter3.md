---
title: Capítulo 3 - Descrição dos serviços do Servidor Azure RTOS NetX DHCP
description: Este capítulo contém uma descrição de todos os serviços do Servidor Azure RTOS NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104826785"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="0d2f0-103">Capítulo 3 - Descrição dos serviços do Servidor Azure RTOS NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="0d2f0-104">Este capítulo contém uma descrição de todos os serviços do Servidor NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="0d2f0-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="0d2f0-106">**nx_dhcp_server_create**: *Criar uma instância do servidor DHCP*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="0d2f0-107">**nx_dhcp_set_interface_network_parameters**: *Definir opções do Servidor DHCP para parâmetros críticos de rede para interface especificada*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="0d2f0-108">**nx_dhcp_create_server_ip_address_list:** Criar *um conjunto de endereços IP disponíveis para atribuir à interface dos clientes DHCP*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="0d2f0-109">**nx_dhcp_clear_client_record**: *Remova o registo do Cliente na base de dados do Servidor*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="0d2f0-110">**nx_dhcp_server_delete**: *Eliminar uma instância DHCPServer*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="0d2f0-111">**nx_dhcp_server_start**: *Iniciar ou retomar o processamento do Servidor DHCP*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="0d2f0-112">**nx_dhcp_server_stop**: *Parar o processamento do servidor DHCP*</span><span class="sxs-lookup"><span data-stu-id="0d2f0-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="0d2f0-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="0d2f0-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="0d2f0-114">Criar uma instância do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-115">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="0d2f0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-116">Description</span></span>

<span data-ttu-id="0d2f0-117">Este serviço cria uma instância do Servidor DHCP com uma instância IP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d2f0-118">A aplicação deve certificar-se de que o pacote criado para o serviço ip create tem uma carga útil mínima de byte 548, não incluindo os cabeçalhos UDP, IP e Ethernet.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-119">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-119">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-120">**dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="0d2f0-121">**ip_ptr**: Indicação para a instância IP do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="0d2f0-122">**stack_ptr**: Localização da pilha do servidor do ponteiro DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="0d2f0-123">**stack_size**: Tamanho da pilha de servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="0d2f0-124">**input_address_list**: Ponteiro para a lista de endereços IP do Servidor</span><span class="sxs-lookup"><span data-stu-id="0d2f0-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="0d2f0-125">**name_ptr**: Ponteiro para o nome do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="0d2f0-126">**packet_pool_ptr**: Ponteiro para a piscina de pacotes do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-127">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-127">Return Values</span></span>

- <span data-ttu-id="0d2f0-128">**NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0d2f0-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Carga útil do pacote erro demasiado pequeno</span><span class="sxs-lookup"><span data-stu-id="0d2f0-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="0d2f0-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) A lista de opções do servidor está vazia</span><span class="sxs-lookup"><span data-stu-id="0d2f0-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="0d2f0-131">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="0d2f0-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="0d2f0-132">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0d2f0-133">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-134">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-134">Allowed From</span></span>

<span data-ttu-id="0d2f0-135">Aplicação</span><span class="sxs-lookup"><span data-stu-id="0d2f0-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="0d2f0-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="0d2f0-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="0d2f0-138">Criar uma piscina de endereços IP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-139">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="0d2f0-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-140">Description</span></span>

<span data-ttu-id="0d2f0-141">Este serviço cria um conjunto específico de endereços IP disponíveis para o servidor DHCP especificado para atribuir.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="0d2f0-142">Os endereços IP de início e fim devem corresponder à interface de rede especificada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="0d2f0-143">O número real de endereços IP adicionados pode ser inferior ao total dos endereços se a lista de endereços IP não for suficientemente grande (que é definida no parâmetro *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* configurável do utilizador).</span><span class="sxs-lookup"><span data-stu-id="0d2f0-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-144">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-144">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-145">**dhcp_ptr** Ponteiro para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="0d2f0-146">**iface_index**: Índice correspondente à interface de rede</span><span class="sxs-lookup"><span data-stu-id="0d2f0-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="0d2f0-147">**start_ip_address**: Primeiro endereço IP disponível</span><span class="sxs-lookup"><span data-stu-id="0d2f0-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="0d2f0-148">**end_ip_address**: O último do endereço IP disponível</span><span class="sxs-lookup"><span data-stu-id="0d2f0-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="0d2f0-149">**addresses_added**: Número de endereços IP adicionados à lista</span><span class="sxs-lookup"><span data-stu-id="0d2f0-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-150">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-150">Return Values</span></span>

- <span data-ttu-id="0d2f0-151">**NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0d2f0-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) O índice não corresponde a endereços</span><span class="sxs-lookup"><span data-stu-id="0d2f0-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="0d2f0-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST:**(0x99) Entrada de endereço inválido</span><span class="sxs-lookup"><span data-stu-id="0d2f0-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="0d2f0-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Endereços ilógicos de início/fim</span><span class="sxs-lookup"><span data-stu-id="0d2f0-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="0d2f0-155">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-156">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-156">Allowed From</span></span>

<span data-ttu-id="0d2f0-157">Aplicação</span><span class="sxs-lookup"><span data-stu-id="0d2f0-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="0d2f0-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="0d2f0-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="0d2f0-160">Remova o registo do Cliente da base de dados do Servidor</span><span class="sxs-lookup"><span data-stu-id="0d2f0-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="0d2f0-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-162">Description</span></span>

<span data-ttu-id="0d2f0-163">Este serviço limpa o registo do Cliente da base de dados do Servidor.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-164">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-164">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-165">**dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="0d2f0-166">**dhcp_client_ptr**: Ponteiro para o cliente DHCP para remover</span><span class="sxs-lookup"><span data-stu-id="0d2f0-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-167">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-167">Return Values</span></span>

- <span data-ttu-id="0d2f0-168">**NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0d2f0-169">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0d2f0-170">NX_CALLER_ERROR: (0x11) Não thread caller of service</span><span class="sxs-lookup"><span data-stu-id="0d2f0-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-171">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-171">Allowed From</span></span>

<span data-ttu-id="0d2f0-172">Aplicação</span><span class="sxs-lookup"><span data-stu-id="0d2f0-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-173">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="0d2f0-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="0d2f0-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="0d2f0-175">Definir parâmetros de rede para opções DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-176">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="0d2f0-177">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-177">Description</span></span>

<span data-ttu-id="0d2f0-178">Este serviço define valores predefinidos para parâmetros críticos de rede para a interface especificada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="0d2f0-179">O servidor DHCP incluirá estas opções na sua OFERTA e respostas ACK ao Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="0d2f0-180">Se os parâmetros de interface definidos pelo anfitrião em que um servidor DHCP está em funcionamento, os parâmetros ficarão incumpridos da seguinte forma: o router definido para o gateway de interface principal para o próprio servidor DHCP, o endereço do servidor DNS para o próprio servidor DHCP e a máscara de sub-rede para a mesma que a interface do servidor DHCP está configurada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-181">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-181">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-182">**dhcp_ptr**: Ponter para o bloco de controlo do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="0d2f0-183">**iface_index**: Índice correspondente à interface de rede</span><span class="sxs-lookup"><span data-stu-id="0d2f0-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="0d2f0-184">**subnet_mask**: Máscara de sub-rede para rede cliente</span><span class="sxs-lookup"><span data-stu-id="0d2f0-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="0d2f0-185">**default_gateway_address**: Endereço IP do router do cliente</span><span class="sxs-lookup"><span data-stu-id="0d2f0-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="0d2f0-186">**dns_server_address**: Servidor DNS para a rede do Cliente</span><span class="sxs-lookup"><span data-stu-id="0d2f0-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-187">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-187">Return Values</span></span>

- <span data-ttu-id="0d2f0-188">**NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="0d2f0-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) O índice não corresponde a endereços</span><span class="sxs-lookup"><span data-stu-id="0d2f0-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="0d2f0-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS:**(0xA3) Parâmetros de rede inválidos</span><span class="sxs-lookup"><span data-stu-id="0d2f0-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="0d2f0-191">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-192">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-192">Allowed From</span></span>

<span data-ttu-id="0d2f0-193">Aplicação</span><span class="sxs-lookup"><span data-stu-id="0d2f0-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-194">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="0d2f0-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="0d2f0-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="0d2f0-196">Excluir uma instância do Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-197">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0d2f0-198">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-198">Description</span></span>

<span data-ttu-id="0d2f0-199">Este serviço elimina uma instância do Servidor DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-200">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-200">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-201">**dhcp_ptr**: Ponteiro para uma instância do Servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-202">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-202">Return Values</span></span>

- <span data-ttu-id="0d2f0-203">**NX_SUCCESS:**(0x00) Servidor DHCP bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="0d2f0-204">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0d2f0-205">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="0d2f0-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="0d2f0-206">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-207">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-207">Allowed From</span></span>

<span data-ttu-id="0d2f0-208">Fios</span><span class="sxs-lookup"><span data-stu-id="0d2f0-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-209">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="0d2f0-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="0d2f0-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="0d2f0-211">Iniciar o processamento do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-212">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0d2f0-213">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-213">Description</span></span>

<span data-ttu-id="0d2f0-214">Este serviço inicia o processamento do Servidor DHCP, que inclui a criação de uma tomada UDP de servidor, ligação da porta DHCP e espera receber os pedidos do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-215">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-215">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-216">**dhcp_ptr**: Ponteiro para a instância DHCP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-217">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-217">Return Values</span></span>

- <span data-ttu-id="0d2f0-218">**NX_SUCCESS**: (0x00) Início do Servidor de Sucesso.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="0d2f0-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0d2f0-220">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0d2f0-221">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0d2f0-222">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="0d2f0-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-223">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-223">Allowed From</span></span>

<span data-ttu-id="0d2f0-224">Fios</span><span class="sxs-lookup"><span data-stu-id="0d2f0-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-225">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="0d2f0-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d2f0-226">See Also</span></span>

<span data-ttu-id="0d2f0-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="0d2f0-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="0d2f0-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="0d2f0-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="0d2f0-229">Para o processamento do servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="0d2f0-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="0d2f0-230">Prototype</span><span class="sxs-lookup"><span data-stu-id="0d2f0-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="0d2f0-231">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d2f0-231">Description</span></span>

<span data-ttu-id="0d2f0-232">Este serviço impede o processamento do Servidor DHCP, que inclui receber pedidos do Cliente DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0d2f0-233">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="0d2f0-233">Input Parameters</span></span>

- <span data-ttu-id="0d2f0-234">**dhcp_ptr**: Indicação para a instância do servidor DHCP.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0d2f0-235">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="0d2f0-235">Return Values</span></span>

- <span data-ttu-id="0d2f0-236">**NX_SUCCESS**: (0x00) Paragem DHCP bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="0d2f0-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP já começou.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="0d2f0-238">NX_PTR_ERROR: (0x16) Entrada inválida do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="0d2f0-239">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="0d2f0-240">NX_DHCP_PARAMETER_ERROR: (0x92) Entrada inválida sem ponte.</span><span class="sxs-lookup"><span data-stu-id="0d2f0-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0d2f0-241">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="0d2f0-241">Allowed From</span></span>

<span data-ttu-id="0d2f0-242">Fios</span><span class="sxs-lookup"><span data-stu-id="0d2f0-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0d2f0-243">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d2f0-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
