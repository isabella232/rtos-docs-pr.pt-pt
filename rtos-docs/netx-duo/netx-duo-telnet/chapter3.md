---
title: Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo Telnet
description: Este capítulo contém uma descrição de todos os Serviços Telnet Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825712"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="9d638-103">Capítulo 3 - Descrição dos serviços Azure RTOS NetX Duo Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="9d638-104">Este capítulo contém uma descrição de todos os Serviços Telnet Azure RTOS NetX Duo (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9d638-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="9d638-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="9d638-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="9d638-106">**nx_telnet_client_connect**: *Ligue um cliente Telnet com o endereço IPv4*</span><span class="sxs-lookup"><span data-stu-id="9d638-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="9d638-107">**nxd_telnet_client_connect**: *Ligue um cliente Telnet IPv6 com o endereço IPv6*</span><span class="sxs-lookup"><span data-stu-id="9d638-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="9d638-108">**nx_telnet_client_create**: *Criar um cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="9d638-109">**nx_telnet_client_delete**: *Eliminar um Cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="9d638-110">**nx_telnet_client_disconnect**: *Desconecte um Cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="9d638-111">**nx_telnet_client_packet_receive**: *Receber pacote via Cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="9d638-112">**nx_telnet_client_packet_send**: *Enviar pacote através do Cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="9d638-113">**nx_telnet_server_create**: *Criar um servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="9d638-114">**nx_telnet_server_delete**: *Eliminar um Servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="9d638-115">**nx_telnet_server_disconnect**: *Desconecte um Cliente Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="9d638-116">**nx_telnet_server_get_open_connection_count**: *Recuperar o número de ligações abertas*</span><span class="sxs-lookup"><span data-stu-id="9d638-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="9d638-117">**nx_telnet_server_packet_send**: *Enviar pacote através da ligação ao Cliente*</span><span class="sxs-lookup"><span data-stu-id="9d638-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="9d638-118">**nx_telnet_server_packet_pool_set**: *Definir a piscina de pacotes como piscina de pacotes Telnet Server*</span><span class="sxs-lookup"><span data-stu-id="9d638-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="9d638-119">**nx_telnet_server_start**: *Iniciar um Servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="9d638-120">**nx_telnet_server_stop**: *Parar um Servidor Telnet*</span><span class="sxs-lookup"><span data-stu-id="9d638-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="9d638-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="9d638-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="9d638-122">Ligue um cliente Telnet com endereço IPv4</span><span class="sxs-lookup"><span data-stu-id="9d638-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-123">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-124">Description</span></span>

<span data-ttu-id="9d638-125">Este serviço tenta ligar a instância do Cliente Telnet anteriormente criada ao Servidor no IP e na porta especificados utilizando um endereço IPv4 para o Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="9d638-126">Este serviço insere efetivamente o endereço IP do servidor ULONG num NXD_ADDRESS bloco de controlo e define a versão IP para 4 antes de ligar para o serviço *nxd_telnet_client_connect* descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="9d638-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-127">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-127">Input Parameters</span></span>

- <span data-ttu-id="9d638-128">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-129">**server_ip**: Endereço IPv4 do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="9d638-130">**server_port**: Porta de Servidor TCP (Telnet Server é a porta 23).</span><span class="sxs-lookup"><span data-stu-id="9d638-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="9d638-131">**wait_option**: Define quanto tempo o serviço vai esperar pela ligação do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="9d638-132">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="9d638-133">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-135">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-135">Return Values</span></span>

- <span data-ttu-id="9d638-136">**NX_SUCCESS:**(0x00) Ligação de cliente bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d638-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="9d638-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente já ligado.</span><span class="sxs-lookup"><span data-stu-id="9d638-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="9d638-138">NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="9d638-139">NX_IP_ADDRESS_ERROR: (0x21) Endereço IP inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="9d638-140">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-141">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-141">Allowed From</span></span>

<span data-ttu-id="9d638-142">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="9d638-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="9d638-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="9d638-145">Ligue um Cliente Telnet com endereço IPv6 ou IPv4</span><span class="sxs-lookup"><span data-stu-id="9d638-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-146">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-147">Description</span></span>

<span data-ttu-id="9d638-148">Este serviço tenta ligar a instância do Cliente Telnet anteriormente criada ao Servidor no IP especificado e na porta utilizando o endereço IPv6 do Telnet Server.</span><span class="sxs-lookup"><span data-stu-id="9d638-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="9d638-149">Este serviço pode ter um endereço IPv4 ou IPv6, mas deve ser contido na NXD_ADDRESS server_ip_address *variável.*</span><span class="sxs-lookup"><span data-stu-id="9d638-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-150">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-150">Input Parameters</span></span>

- <span data-ttu-id="9d638-151">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-152">**server_ip_address**: Endereço IP do Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d638-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="9d638-153">**server_port**: Porta de Servidor TCP (Telnet Server é a porta 23).</span><span class="sxs-lookup"><span data-stu-id="9d638-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="9d638-154">**wait_option**: Define quanto tempo o serviço vai esperar pela ligação do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="9d638-155">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="9d638-156">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-158">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-158">Return Values</span></span>

- <span data-ttu-id="9d638-159">**NX_SUCCESS:**(0x00) Ligação de cliente bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d638-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="9d638-160">**NX_TELNET_ERROR:**(0xF0) Erro de ligação do cliente.</span><span class="sxs-lookup"><span data-stu-id="9d638-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="9d638-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente já ligado.</span><span class="sxs-lookup"><span data-stu-id="9d638-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="9d638-162">NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="9d638-163">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="9d638-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="9d638-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-165">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-165">Allowed From</span></span>

<span data-ttu-id="9d638-166">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="9d638-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="9d638-168">nx_telnet_client_create</span></span>

<span data-ttu-id="9d638-169">Criar um Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-170">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="9d638-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-171">Description</span></span>

<span data-ttu-id="9d638-172">Este serviço cria uma instância do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-173">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-173">Input Parameters</span></span>

- <span data-ttu-id="9d638-174">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-175">**client_name**: Caso do Cliente.</span><span class="sxs-lookup"><span data-stu-id="9d638-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="9d638-176">**ip_ptr**: Indicação para a instância IP.</span><span class="sxs-lookup"><span data-stu-id="9d638-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="9d638-177">**window_size**: Tamanho da TCP receber janela para este Cliente.</span><span class="sxs-lookup"><span data-stu-id="9d638-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-178">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-178">Return Values</span></span>

- <span data-ttu-id="9d638-179">**NX_SUCCESS:**(0x00) O Cliente bem sucedido cria.</span><span class="sxs-lookup"><span data-stu-id="9d638-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="9d638-180">**NX_TELNET_ERROR:**(0xF0) A tomada cria erro.</span><span class="sxs-lookup"><span data-stu-id="9d638-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="9d638-181">NX_PTR_ERROR: (0x07) Cliente inválido ou ponteiro IP.</span><span class="sxs-lookup"><span data-stu-id="9d638-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-182">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-182">Allowed From</span></span>

<span data-ttu-id="9d638-183">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="9d638-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-184">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="9d638-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="9d638-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="9d638-186">Excluir um Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-187">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="9d638-188">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-188">Description</span></span>

<span data-ttu-id="9d638-189">Este serviço elimina uma instância do Cliente Telnet anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="9d638-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-190">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-190">Input Parameters</span></span>

- <span data-ttu-id="9d638-191">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-192">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-192">Return Values</span></span>

- <span data-ttu-id="9d638-193">**NX_SUCCESS:**(0x00) O Cliente bem sucedido apaga.</span><span class="sxs-lookup"><span data-stu-id="9d638-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="9d638-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Cliente ainda ligado.</span><span class="sxs-lookup"><span data-stu-id="9d638-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="9d638-195">NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="9d638-196">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-197">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-197">Allowed From</span></span>

<span data-ttu-id="9d638-198">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-199">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="9d638-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="9d638-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="9d638-201">Desligar um Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-203">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-203">Description</span></span>

<span data-ttu-id="9d638-204">Este serviço desliga uma instância do Cliente Telnet anteriormente ligada.</span><span class="sxs-lookup"><span data-stu-id="9d638-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-205">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-205">Input Parameters</span></span>

- <span data-ttu-id="9d638-206">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-207">**wait_option**: Define quanto tempo o serviço esperará pela desconexão do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="9d638-208">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="9d638-209">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-211">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-211">Return Values</span></span>

- <span data-ttu-id="9d638-212">**NX_SUCCESS:**(0x00) Desconexão do Cliente bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="9d638-213">**NX_TELNET_NOT_CONNECTED:**(0xF3) Cliente não ligado.</span><span class="sxs-lookup"><span data-stu-id="9d638-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="9d638-214">NX_PTR_ERROR: (0x07) Ponteiro do Cliente Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="9d638-215">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="9d638-216">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-216">Allowed From</span></span>

<span data-ttu-id="9d638-217">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-218">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="9d638-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="9d638-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="9d638-220">Receber pacote via Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-222">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-222">Description</span></span>

<span data-ttu-id="9d638-223">Este serviço recebe um pacote da instância do Cliente Telnet anteriormente ligada.</span><span class="sxs-lookup"><span data-stu-id="9d638-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-224">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-224">Input Parameters</span></span>

- <span data-ttu-id="9d638-225">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-226">**packet_ptr**: Ponte para o destino do pacote recebido.</span><span class="sxs-lookup"><span data-stu-id="9d638-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="9d638-227">**wait_option**: Define quanto tempo o serviço esperará pela receção do pacote do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="9d638-228">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="9d638-229">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-231">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-231">Return Values</span></span>

- <span data-ttu-id="9d638-232">**NX_SUCCESS:**(0x00) Pacote cliente bem sucedido receber.</span><span class="sxs-lookup"><span data-stu-id="9d638-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="9d638-233">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="9d638-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9d638-234">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-235">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-235">Allowed From</span></span>

<span data-ttu-id="9d638-236">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-237">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="9d638-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="9d638-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="9d638-239">Enviar pacote através do Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-241">Description</span></span>

<span data-ttu-id="9d638-242">Este serviço envia um pacote através da instância do Cliente Telnet anteriormente ligada.</span><span class="sxs-lookup"><span data-stu-id="9d638-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-243">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-243">Input Parameters</span></span>

- <span data-ttu-id="9d638-244">**client_ptr**: Ponteiro para o bloco de controlo do cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="9d638-245">**packet_ptr**: Ponter para o pacote a enviar.</span><span class="sxs-lookup"><span data-stu-id="9d638-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="9d638-246">**wait_option**: Define quanto tempo o serviço esperará pelo envio do pacote do Cliente Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="9d638-247">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="9d638-248">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-250">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-250">Return Values</span></span>

- <span data-ttu-id="9d638-251">**NX_SUCCESS:**(0x00) Pacote de cliente bem sucedido enviar.</span><span class="sxs-lookup"><span data-stu-id="9d638-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="9d638-252">**NX_TELNET_ERROR**: (0xF0) Enviar o pacote falhado – o chamador é responsável pela libertação do pacote.</span><span class="sxs-lookup"><span data-stu-id="9d638-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="9d638-253">NX_PTR_ERROR: (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="9d638-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="9d638-254">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-255">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-255">Allowed From</span></span>

<span data-ttu-id="9d638-256">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-257">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="9d638-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="9d638-258">nx_telnet_server_create</span></span>

<span data-ttu-id="9d638-259">Criar um Servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-260">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="9d638-261">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-261">Description</span></span>

<span data-ttu-id="9d638-262">Este serviço cria uma instância do Telnet Server na instância IP especificada.</span><span class="sxs-lookup"><span data-stu-id="9d638-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-263">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-263">Input Parameters</span></span>

- <span data-ttu-id="9d638-264">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="9d638-265">**server_name**: Nome da instância telnet Server.</span><span class="sxs-lookup"><span data-stu-id="9d638-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="9d638-266">**ip_ptr**: Ponteiro para a instância IP associada.</span><span class="sxs-lookup"><span data-stu-id="9d638-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="9d638-267">**stack_ptr**: Ponteiro para empilhar para o fio interno do Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d638-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="9d638-268">**sack_size:** Tamanho da pilha, bytes.</span><span class="sxs-lookup"><span data-stu-id="9d638-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="9d638-269">**new_connection:** Ponteiro de função de rotina de chamada de aplicação.</span><span class="sxs-lookup"><span data-stu-id="9d638-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="9d638-270">Esta rotina é chamada sempre que um novo pedido de ligação ao Cliente Telnet é detetado pelo Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d638-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="9d638-271">**receive_data:** Ponteiro de função de rotina de chamada de aplicação.</span><span class="sxs-lookup"><span data-stu-id="9d638-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="9d638-272">Esta rotina é chamada sempre que um novo dado do Cliente Telnet está presente na ligação.</span><span class="sxs-lookup"><span data-stu-id="9d638-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="9d638-273">Esta rotina é responsável pela libertação do pacote.</span><span class="sxs-lookup"><span data-stu-id="9d638-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="9d638-274">**end_connection:** Ponteiro de função de rotina de chamada de aplicação.</span><span class="sxs-lookup"><span data-stu-id="9d638-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="9d638-275">Esta rotina é chamada sempre que uma ligação telnet Cliente é desligada pelo Cliente ou o tempo de ligação do Cliente termina ("tempo de tempo de atividade" expira).</span><span class="sxs-lookup"><span data-stu-id="9d638-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="9d638-276">O Servidor também pode desligar-se através do serviço *nx_telnet_server_disconnect* descrito abaixo.</span><span class="sxs-lookup"><span data-stu-id="9d638-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-277">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-277">Return Values</span></span>

- <span data-ttu-id="9d638-278">**NX_SUCCESS:**(0x00) Servidor de sucesso criar.</span><span class="sxs-lookup"><span data-stu-id="9d638-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="9d638-279">NX_PTR_ERROR: (0x07) Inválido Servidor, IP, stack ou guiadores de chamadas de aplicação.</span><span class="sxs-lookup"><span data-stu-id="9d638-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-280">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-280">Allowed From</span></span>

<span data-ttu-id="9d638-281">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="9d638-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-282">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="9d638-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="9d638-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="9d638-284">Excluir um Servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-285">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="9d638-286">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-286">Description</span></span>

<span data-ttu-id="9d638-287">Este serviço elimina uma instância telnet server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="9d638-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-288">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-288">Input Parameters</span></span>

- <span data-ttu-id="9d638-289">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-290">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-290">Return Values</span></span>

- <span data-ttu-id="9d638-291">**NX_SUCCESS:**(0x00) Servidor de sucesso eliminar.</span><span class="sxs-lookup"><span data-stu-id="9d638-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="9d638-292">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="9d638-293">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-294">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-294">Allowed From</span></span>

<span data-ttu-id="9d638-295">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-296">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="9d638-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="9d638-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="9d638-298">Desligar um Cliente Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-299">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="9d638-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-300">Description</span></span>

<span data-ttu-id="9d638-301">Este serviço desliga um Cliente previamente ligado nesta instância do Telnet Server.</span><span class="sxs-lookup"><span data-stu-id="9d638-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="9d638-302">Esta rotina é normalmente chamada da função de retorno de dados de receção da aplicação em resposta a uma condição detetada nos dados recebidos.</span><span class="sxs-lookup"><span data-stu-id="9d638-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-303">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-303">Input Parameters</span></span>

- <span data-ttu-id="9d638-304">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="9d638-305">**logical_connection**: Ligação lógica correspondente à ligação do Cliente neste Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d638-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="9d638-306">O valor válido varia entre 0 e NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="9d638-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-307">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-307">Return Values</span></span>

- <span data-ttu-id="9d638-308">**NX_SUCCESS:**(0x00) Desconexão do servidor de sucesso.</span><span class="sxs-lookup"><span data-stu-id="9d638-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="9d638-309">**NX_TELNET_ERROR:**(0xF0) A desconexão do servidor falhou.</span><span class="sxs-lookup"><span data-stu-id="9d638-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="9d638-310">NX_OPTION_ERROR: (0x0A) Ligação lógica inválida.</span><span class="sxs-lookup"><span data-stu-id="9d638-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="9d638-311">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="9d638-312">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-313">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-313">Allowed From</span></span>

<span data-ttu-id="9d638-314">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-315">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="9d638-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="9d638-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="9d638-317">Número de devolução de ligações atualmente abertas</span><span class="sxs-lookup"><span data-stu-id="9d638-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="9d638-319">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-319">Description</span></span>

<span data-ttu-id="9d638-320">Este serviço devolve o número de Clientes Telnet atualmente ligados.</span><span class="sxs-lookup"><span data-stu-id="9d638-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-321">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-321">Input Parameters</span></span>

- <span data-ttu-id="9d638-322">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="9d638-323">**Connection_count**: Ponteiro para a memória para armazenar contagem de ligação</span><span class="sxs-lookup"><span data-stu-id="9d638-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-324">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-324">Return Values</span></span>

- <span data-ttu-id="9d638-325">**NX_SUCCESS:**(0x00) Conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="9d638-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="9d638-326">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="9d638-327">NX_CALLER_ERROR: (0x11) Inválido deste serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-328">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-328">Allowed From</span></span>

<span data-ttu-id="9d638-329">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-330">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="9d638-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="9d638-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="9d638-332">Enviar pacote através da ligação ao Cliente</span><span class="sxs-lookup"><span data-stu-id="9d638-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="9d638-334">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-334">Description</span></span>

<span data-ttu-id="9d638-335">Este serviço envia um pacote para a ligação ao Cliente nesta instância do Telnet Server.</span><span class="sxs-lookup"><span data-stu-id="9d638-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="9d638-336">Esta rotina é normalmente chamada da função de retorno de dados de receção da aplicação em resposta a uma condição detetada nos dados recebidos.</span><span class="sxs-lookup"><span data-stu-id="9d638-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-337">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-337">Input Parameters</span></span>

- <span data-ttu-id="9d638-338">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="9d638-339">**logical_connection**: Ligação lógica correspondente à ligação do Cliente neste Servidor.</span><span class="sxs-lookup"><span data-stu-id="9d638-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="9d638-340">O valor válido varia entre 0 e NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="9d638-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="9d638-341">**packet_ptr**: Ponteiro para o pacote recebido.</span><span class="sxs-lookup"><span data-stu-id="9d638-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="9d638-342">**wait_option**: Define quanto tempo o serviço irá esperar pelo envio do pacote Do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="9d638-343">As opções de espera são definidas da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9d638-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="9d638-344">**Valor de tempo limite**: (0x00000001 a 0xFFFFFFFE) Selecionar um valor numérico (1-0xFFFFFFFE) especifica o número máximo de temporizadores para permanecer suspenso enquanto se aguarda a resposta do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="9d638-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) A seleção TX_WAIT_FOREVER faz com que o fio de chamada suspenda indefinidamente até que o Servidor Telnet responda ao pedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="9d638-346">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-346">Return Values</span></span>

- <span data-ttu-id="9d638-347">**NX_SUCCESS:**(0x00) Envio de pacote bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="9d638-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="9d638-348">**NX_TELNET_FAILED:**(0xF2) A tomada TCP enviada falhou.</span><span class="sxs-lookup"><span data-stu-id="9d638-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="9d638-349">NX_OPTION_ERROR: (0x0A) Ligação lógica inválida.</span><span class="sxs-lookup"><span data-stu-id="9d638-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="9d638-350">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="9d638-351">NX_CALLER_ERROR: (0x11) Inválido de serviço.</span><span class="sxs-lookup"><span data-stu-id="9d638-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-352">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-352">Allowed From</span></span>

<span data-ttu-id="9d638-353">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-354">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="9d638-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="9d638-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="9d638-356">Conjunto previamente criado pool de pacotes como piscina Telnet Server</span><span class="sxs-lookup"><span data-stu-id="9d638-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-357">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="9d638-358">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-358">Description</span></span>

<span data-ttu-id="9d638-359">Este serviço define um conjunto de pacotes previamente criado como o pool de pacotes telnet Server se NX_TELNET_SERVER_USER_CREATE_PACKET_POOL for definida.</span><span class="sxs-lookup"><span data-stu-id="9d638-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="9d638-360">Também requer que não NX_TELNET_SERVER_OPTION_DISABLE ser definido de modo a que o Telnet Server precise de um pacote de piscina para transmitir opções telnet aos clientes telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="9d638-361">Isto permite que as aplicações criem o conjunto de pacotes em memórias diferentes, por exemplo, sem memória de cache, do que a pilha do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="9d638-362">Note que se esta função não verificar se o conjunto de pacotes do Telnet Server já está definido.</span><span class="sxs-lookup"><span data-stu-id="9d638-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="9d638-363">Se for chamado a um ponteiro de piscina telnet server não nulo, ele substituirá e substituirá a piscina de pacotes existente por um pacote de piscina apontado pelo ponteiro de entrada.</span><span class="sxs-lookup"><span data-stu-id="9d638-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-364">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-364">Input Parameters</span></span>

- <span data-ttu-id="9d638-365">**server_ptr**: Ponteiro para o bloco de controlo do servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="9d638-366">**packet_pool_ptr**: Ponteiro para piscina de pacotes previamente criada</span><span class="sxs-lookup"><span data-stu-id="9d638-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-367">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-367">Return Values</span></span>

- <span data-ttu-id="9d638-368">**NX_SUCCESS**: (0x00) Coloque a piscina com sucesso.</span><span class="sxs-lookup"><span data-stu-id="9d638-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="9d638-369">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-370">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-370">Allowed From</span></span>

<span data-ttu-id="9d638-371">Init, Threads</span><span class="sxs-lookup"><span data-stu-id="9d638-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-372">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="9d638-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="9d638-373">nx_telnet_server_start</span></span>

<span data-ttu-id="9d638-374">Iniciar um Servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-375">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="9d638-376">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-376">Description</span></span>

<span data-ttu-id="9d638-377">Este serviço inicia uma instância telnet server previamente criada.</span><span class="sxs-lookup"><span data-stu-id="9d638-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-378">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-378">Input Parameters</span></span>

- <span data-ttu-id="9d638-379">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-380">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-380">Return Values</span></span>

- <span data-ttu-id="9d638-381">**NX_SUCCESS**: (0x00) Começou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="9d638-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="9d638-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) Sem conjunto de piscina de pacotes</span><span class="sxs-lookup"><span data-stu-id="9d638-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="9d638-383">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-384">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-384">Allowed From</span></span>

<span data-ttu-id="9d638-385">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="9d638-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-386">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="9d638-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="9d638-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="9d638-388">Parar um Servidor Telnet</span><span class="sxs-lookup"><span data-stu-id="9d638-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="9d638-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="9d638-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="9d638-390">Descrição</span><span class="sxs-lookup"><span data-stu-id="9d638-390">Description</span></span>

<span data-ttu-id="9d638-391">Este serviço para uma instância do Telnet Server previamente criada e iniciou.</span><span class="sxs-lookup"><span data-stu-id="9d638-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="9d638-392">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="9d638-392">Input Parameters</span></span>

- <span data-ttu-id="9d638-393">**server_ptr**: Ponteiro para o bloco de controlo do Servidor Telnet.</span><span class="sxs-lookup"><span data-stu-id="9d638-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="9d638-394">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="9d638-394">Return Values</span></span>

- <span data-ttu-id="9d638-395">**NX_SUCCESS**: (0x00) Parou com sucesso</span><span class="sxs-lookup"><span data-stu-id="9d638-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="9d638-396">NX_PTR_ERROR: (0x07) Ponteiro do Servidor Inválido.</span><span class="sxs-lookup"><span data-stu-id="9d638-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="9d638-397">NX_CALLER_ERROR: (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="9d638-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="9d638-398">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="9d638-398">Allowed From</span></span>

<span data-ttu-id="9d638-399">Fios</span><span class="sxs-lookup"><span data-stu-id="9d638-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="9d638-400">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d638-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```