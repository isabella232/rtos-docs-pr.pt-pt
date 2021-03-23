---
title: Capítulo 3 - Descrição dos Serviços de ClienteS SNTP SNTP da Azure RTOS NetX Duo SNTP
description: Este capítulo contém uma descrição de todos os serviços do Cliente NetX Duo SNTP (listados abaixo) por ordem alfabética.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825747"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="3458a-103">Capítulo 3 - Descrição dos Serviços de ClienteS SNTP SNTP da Azure RTOS NetX Duo SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="3458a-104">Este capítulo contém uma descrição de todos os serviços do Cliente Azure RTOS NetX Duo SNTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="3458a-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="3458a-105">Na secção "Valores de Retorno" nas seguintes descrições da API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.</span><span class="sxs-lookup"><span data-stu-id="3458a-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="3458a-106">**nx_sntp_client_create**: *Criar o Cliente SNTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="3458a-107">**nx_sntp_client_delete**: *Eliminar o Cliente SNTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="3458a-108">**nx_sntp_client_get_local_time**: *Obtenha a hora do cliente SNTP local*</span><span class="sxs-lookup"><span data-stu-id="3458a-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="3458a-109">**nx_sntp_client_get_local_time_extended**: *Obtenha a hora do cliente SNTP local*</span><span class="sxs-lookup"><span data-stu-id="3458a-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="3458a-110">**nx_sntp_client_initialize_broadcast**: *Inicialize o cliente para a operação de transmissão IPv4*</span><span class="sxs-lookup"><span data-stu-id="3458a-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="3458a-111">**nxd_sntp_client_initialize_broadcast**: *Inicialize o cliente para a operação de transmissão IPv6 ou IPv4*</span><span class="sxs-lookup"><span data-stu-id="3458a-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="3458a-112">**nx_sntp_client_initialize_unicast**: *Inicialize o cliente para a operação unicast IPv4*</span><span class="sxs-lookup"><span data-stu-id="3458a-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="3458a-113">**nxd_sntp_client_initialize_unicast**: *Inicialize o cliente para a operação unicast IPv4 ou IPv6*</span><span class="sxs-lookup"><span data-stu-id="3458a-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="3458a-114">**nx_sntp_client_receiving_udpates**: *O Cliente está atualmente a receber atualizações válidas da SNTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="3458a-115">**nx_sntp_client_request_unicast_time**: *Enviar um pedido unicast diretamente para o Servidor NTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="3458a-116">**nx_sntp_client_run_broadcast**: *Executar o Cliente em modo de transmissão*</span><span class="sxs-lookup"><span data-stu-id="3458a-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="3458a-117">**nx_sntp_client_run_unicast**: *Executar o Cliente em modo unicast*</span><span class="sxs-lookup"><span data-stu-id="3458a-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="3458a-118">**nx_sntp_client_set_local_time**: *Definir o cliente SNTP na hora local*</span><span class="sxs-lookup"><span data-stu-id="3458a-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="3458a-119">**nx_sntp_client_set_time_update_notify**: *Desembaraque a chamada de atualização SNTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="3458a-120">**nx_sntp_client_stop**: *Pare a linha do cliente SNTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="3458a-121">**nx_sntp_client_utility_display_date_and_time**: *Mostrar tempo de NTP em segundos*</span><span class="sxs-lookup"><span data-stu-id="3458a-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="3458a-122">**nx_sntp_client_utility_msecs_to_fraction**: *Converter milissegundos para um componente de fração NTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="3458a-123">**nx_sntp_client_utility_usecs_to_fraction**: *Converter microsegundos num componente de fração NTP*</span><span class="sxs-lookup"><span data-stu-id="3458a-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="3458a-124">**nx_sntp_client_utility_fraction_to_usecs**: *Converter um componente de fração NTP em microsegundos*</span><span class="sxs-lookup"><span data-stu-id="3458a-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="3458a-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="3458a-125">nx_sntp_client_create</span></span>

<span data-ttu-id="3458a-126">Criar um Cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-127">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="3458a-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-128">Description</span></span>

<span data-ttu-id="3458a-129">Este serviço cria uma instância do Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-130">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-130">Input Parameters</span></span>

- <span data-ttu-id="3458a-131">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-132">**ip_ptr** Indicação para o cliente ip instância</span><span class="sxs-lookup"><span data-stu-id="3458a-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="3458a-133">**iface_index** Índice para interface de rede SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="3458a-134">**packet_pool_ptr** Ponteiro para piscina de pacotes de cliente</span><span class="sxs-lookup"><span data-stu-id="3458a-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="3458a-135">**leap_second_handler** Chamada para resposta de candidatura ao salto iminente em segundo lugar</span><span class="sxs-lookup"><span data-stu-id="3458a-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="3458a-136">**kiss_of_death_handler** Callback para resposta de aplicação para receber pacote kiss of Death</span><span class="sxs-lookup"><span data-stu-id="3458a-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="3458a-137">**random_number_generator** Chamada para serviço gerador de números aleatórios</span><span class="sxs-lookup"><span data-stu-id="3458a-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-138">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-138">Return Values</span></span>

- <span data-ttu-id="3458a-139">**NX_SUCCESS** (0x00) Criação de clientes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="3458a-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="3458a-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="3458a-141">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-142">interface de rede NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="3458a-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-143">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-143">Allowed From</span></span>

<span data-ttu-id="3458a-144">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="3458a-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="3458a-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="3458a-147">Excluir um Cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-148">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="3458a-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-149">Description</span></span>

<span data-ttu-id="3458a-150">Este serviço elimina uma instância do Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-151">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-151">Input Parameters</span></span>

- <span data-ttu-id="3458a-152">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-153">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-153">Return Values</span></span>

- <span data-ttu-id="3458a-154">**NX_SUCCESS** (0x00) Criação de clientes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="3458a-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="3458a-155">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-156">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-157">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-157">Allowed From</span></span>

<span data-ttu-id="3458a-158">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="3458a-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="3458a-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="3458a-161">Obtenha a hora local do Cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-162">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="3458a-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-163">Description</span></span>

<span data-ttu-id="3458a-164">Este serviço obtém a hora local do Cliente SNTP com uma entrada de chaveiro de opção para receber os dados em formato de mensagem de cadeia.</span><span class="sxs-lookup"><span data-stu-id="3458a-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="3458a-165">Este serviço é precotado.</span><span class="sxs-lookup"><span data-stu-id="3458a-165">This service is deprecated.</span></span> <span data-ttu-id="3458a-166">Os desenvolvedores são encorajados a migrar para *nx_sntp_client_get_local_time_extended*().</span><span class="sxs-lookup"><span data-stu-id="3458a-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-167">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-167">Input Parameters</span></span>

- <span data-ttu-id="3458a-168">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-169">**segundos** Ponteiro para segundos locais</span><span class="sxs-lookup"><span data-stu-id="3458a-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="3458a-170">**fração** Componente de fração de tempo local</span><span class="sxs-lookup"><span data-stu-id="3458a-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="3458a-171">**tampão** Ponteiro para tampão para escrever dados de tempo</span><span class="sxs-lookup"><span data-stu-id="3458a-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-172">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-172">Return Values</span></span>

- <span data-ttu-id="3458a-173">**NX_SUCCESS** (0x00) Criação de clientes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="3458a-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="3458a-174">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-175">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-176">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-176">Allowed From</span></span>

<span data-ttu-id="3458a-177">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="3458a-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="3458a-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="3458a-180">Obtenha o horário prolongado do Cliente SNTP local</span><span class="sxs-lookup"><span data-stu-id="3458a-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="3458a-182">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-182">Description</span></span>

<span data-ttu-id="3458a-183">Este serviço obtém o tempo sNTP cliente estendido local com uma entrada de chaveiro de opção para receber os dados em formato de mensagem de cadeia.</span><span class="sxs-lookup"><span data-stu-id="3458a-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-184">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-184">Input Parameters</span></span>

- <span data-ttu-id="3458a-185">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-186">**segundos** Ponteiro para segundos locais</span><span class="sxs-lookup"><span data-stu-id="3458a-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="3458a-187">**fração** Ponteiro para componente de fração</span><span class="sxs-lookup"><span data-stu-id="3458a-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="3458a-188">**tampão** Ponteiro para tampão para escrever dados de tempo</span><span class="sxs-lookup"><span data-stu-id="3458a-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="3458a-189">**buffer_size** Comprimento do tampão</span><span class="sxs-lookup"><span data-stu-id="3458a-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-190">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-190">Return Values</span></span>

- <span data-ttu-id="3458a-191">**NX_SUCCESS** (0x00) Criação de clientes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="3458a-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="3458a-192">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-193">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="3458a-194">NX_SIZE_ERROR (0x09) Verifique buffer_size falhar</span><span class="sxs-lookup"><span data-stu-id="3458a-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-195">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-195">Allowed From</span></span>

<span data-ttu-id="3458a-196">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-197">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="3458a-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="3458a-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="3458a-199">Inicializar o Cliente para operação de transmissão</span><span class="sxs-lookup"><span data-stu-id="3458a-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="3458a-201">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-201">Description</span></span>

<span data-ttu-id="3458a-202">Este serviço inicializa o Cliente para a operação de transmissão, definindo o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="3458a-203">Se os endereços multicast e de transmissão não forem nulos, o endereço multicast é selecionado.</span><span class="sxs-lookup"><span data-stu-id="3458a-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="3458a-204">Se ambos os endereços forem nulos, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="3458a-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="3458a-205">Note que isto suporta apenas endereços de servidor IPv4.</span><span class="sxs-lookup"><span data-stu-id="3458a-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-206">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-206">Input Parameters</span></span>

- <span data-ttu-id="3458a-207">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-208">**multicast_server_address** Endereço multicast SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="3458a-209">**broadcast_time_server** Endereço de transmissão de servidor SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-210">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-210">Return Values</span></span>

- <span data-ttu-id="3458a-211">**NX_SUCCESS** (0x00) Criação de Clientes bem sucedidos</span><span class="sxs-lookup"><span data-stu-id="3458a-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="3458a-212">**NX_INVALID_PARAMETERS** (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="3458a-213">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-214">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-215">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-215">Allowed From</span></span>

<span data-ttu-id="3458a-216">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-217">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="3458a-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="3458a-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="3458a-219">Inicializar o Cliente para a operação de transmissão IPv4 ou IPv6</span><span class="sxs-lookup"><span data-stu-id="3458a-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-220">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="3458a-221">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-221">Description</span></span>

<span data-ttu-id="3458a-222">Este serviço inicializa o Cliente para a operação de transmissão, configurando o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="3458a-223">Se os ponteiros de endereços de difusão e multicast não forem nulos, o endereço multicast é selecionado.</span><span class="sxs-lookup"><span data-stu-id="3458a-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="3458a-224">Se ambos os ponteiros de endereço forem nulos, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="3458a-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="3458a-225">Isto suporta os tipos de endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="3458a-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="3458a-226">Note que o IPv6 não suporta a transmissão, pelo que o ponteiro do endereço de transmissão está definido para IPv6, um erro é devolvido.</span><span class="sxs-lookup"><span data-stu-id="3458a-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-227">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-227">Input Parameters</span></span>

- <span data-ttu-id="3458a-228">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-229">**multicast_server_address** Endereço multicast do servidor SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="3458a-230">**broadcast_server_address** Endereço de transmissão de servidor SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-231">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-231">Return Values</span></span>

- <span data-ttu-id="3458a-232">**NX_SUCCESS** (0x00) Cliente iniciais com sucesso</span><span class="sxs-lookup"><span data-stu-id="3458a-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="3458a-233">NX_SNTP_PARAM_ERROR (0xD0D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="3458a-234">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-235">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="3458a-236">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-236">Allowed From</span></span>

<span data-ttu-id="3458a-237">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-238">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="3458a-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="3458a-240">Crie o Cliente SNTP para funcionar em unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="3458a-242">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-242">Description</span></span>

<span data-ttu-id="3458a-243">Este serviço inicializa o Cliente para a operação unicast, definindo o endereço IP do Servidor SNTP e rubricando parâmetros e intervalos de arranque SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="3458a-244">Note que isto suporta apenas endereços de servidor IPv4.</span><span class="sxs-lookup"><span data-stu-id="3458a-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-245">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-245">Input Parameters</span></span>

- <span data-ttu-id="3458a-246">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-247">**unicast_time_server** Endereço IP do servidor SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-248">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-248">Return Values</span></span>

- <span data-ttu-id="3458a-249">**NX_SUCCESS** (0x00) Cliente iniciais com sucesso</span><span class="sxs-lookup"><span data-stu-id="3458a-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="3458a-250">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="3458a-251">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-252">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-253">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-253">Allowed From</span></span>

<span data-ttu-id="3458a-254">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-255">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="3458a-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="3458a-257">Configurar o Cliente SNTP para funcionar em IPv4 ou IPv6 unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-258">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="3458a-259">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-259">Description</span></span>

<span data-ttu-id="3458a-260">Este serviço inicializa o Cliente para a operação unicast, configurando o endereço IP do SNTP Server e rubricando os parâmetros e intervalos de arranque SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="3458a-261">Isto suporta os tipos de endereços IPv4 e IPv6.</span><span class="sxs-lookup"><span data-stu-id="3458a-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-262">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-262">Input Parameters</span></span>

- <span data-ttu-id="3458a-263">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-264">**unicast_time_server** Endereço IP do servidor SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-265">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-265">Return Values</span></span>

- <span data-ttu-id="3458a-266">**NX_SUCCESS** (0x00) Cliente iniciais com sucesso</span><span class="sxs-lookup"><span data-stu-id="3458a-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="3458a-267">NX_INVALID_PARAMETERS (0x4D) Entrada inválida sem ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="3458a-268">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-269">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-270">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-270">Allowed From</span></span>

<span data-ttu-id="3458a-271">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-272">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="3458a-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="3458a-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="3458a-274">Indicar se o Cliente está a receber atualizações válidas</span><span class="sxs-lookup"><span data-stu-id="3458a-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="3458a-276">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-276">Description</span></span>

<span data-ttu-id="3458a-277">Este serviço indica se o Cliente está a receber atualizações SNTP válidas.</span><span class="sxs-lookup"><span data-stu-id="3458a-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="3458a-278">Se o lapso de tempo máximo sem uma atualização válida ou limite de atualizações inválidas consecutivas for ultrapassado, o estado de receção é devolvido como falso.</span><span class="sxs-lookup"><span data-stu-id="3458a-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="3458a-279">Note que o Cliente SNTP ainda está em execução e se a aplicação pretende reiniciar o Cliente SNTP com outro servidor unicast ou de difusão/multicast deve parar o Cliente SNTP utilizando o serviço *nx_sntp_client_stop,* reinitializar o Cliente utilizando um dos serviços de inicialização com outro servidor.</span><span class="sxs-lookup"><span data-stu-id="3458a-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-280">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-280">Input Parameters</span></span>

- <span data-ttu-id="3458a-281">**client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="3458a-282">**receive_status** Ponteiro para indicador se o Cliente está a receber atualizações válidas.</span><span class="sxs-lookup"><span data-stu-id="3458a-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-283">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-283">Return Values</span></span>

- <span data-ttu-id="3458a-284">**NX_SUCCESS** (0x00) Cliente recebeu com sucesso o estado de atualização</span><span class="sxs-lookup"><span data-stu-id="3458a-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="3458a-285">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-286">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-286">Allowed From</span></span>

<span data-ttu-id="3458a-287">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-288">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="3458a-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="3458a-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="3458a-290">Envie um pedido unicast diretamente para o Servidor NTP</span><span class="sxs-lookup"><span data-stu-id="3458a-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="3458a-291">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="3458a-292">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-292">Description</span></span>

<span data-ttu-id="3458a-293">Este serviço permite que a aplicação envie diretamente um pedido unicast para o servidor NTP assíncronamente a partir da tarefa de thread do Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="3458a-294">A opção de espera especifica quanto tempo esperar por uma resposta.</span><span class="sxs-lookup"><span data-stu-id="3458a-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="3458a-295">Se for bem sucedido, a aplicação pode utilizar outros serviços do Cliente SNTP para obter a última hora.</span><span class="sxs-lookup"><span data-stu-id="3458a-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="3458a-296">Consulte a secção **SNTP Asynchronous Unicast Requests** para mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="3458a-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-297">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-297">Input Parameters</span></span>

- <span data-ttu-id="3458a-298">**client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="3458a-299">**Wait_option** Opção de espera para resposta NTP em carraças tempor.</span><span class="sxs-lookup"><span data-stu-id="3458a-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-300">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-300">Return Values</span></span>

- <span data-ttu-id="3458a-301">**NX_SUCCESS** (0x00) Cliente envia e recebe com sucesso atualização unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="3458a-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Linha de cliente não começou</span><span class="sxs-lookup"><span data-stu-id="3458a-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="3458a-303">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-304">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-305">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-305">Allowed From</span></span>

<span data-ttu-id="3458a-306">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-307">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="3458a-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="3458a-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="3458a-309">Executar o Cliente em modo de transmissão</span><span class="sxs-lookup"><span data-stu-id="3458a-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-310">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="3458a-311">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-311">Description</span></span>

<span data-ttu-id="3458a-312">Este serviço inicia o Cliente no modo de transmissão onde aguardará para receber transmissões do servidor SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="3458a-313">Se for recebida uma mensagem SNTP de transmissão válida, o tempo limite de tempo do cliente SNTP para o lapso máximo sem uma atualização e contagem de mensagens inválidas consecutivas recebidas são reiniciadas.</span><span class="sxs-lookup"><span data-stu-id="3458a-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="3458a-314">Se um destes limites for ultrapassado, o Cliente SNTP define o estado do servidor para inválido, embora ainda espere receber atualizações.</span><span class="sxs-lookup"><span data-stu-id="3458a-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="3458a-315">A aplicação pode sondar a tarefa do Cliente SNTP para o estado do servidor, e se inválida parar o Cliente SNTP e reinitilizá-lo com outro endereço de transmissão SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="3458a-316">Também pode mudar para um servidor SNTP unicast.</span><span class="sxs-lookup"><span data-stu-id="3458a-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-317">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-317">Input Parameters</span></span>

- <span data-ttu-id="3458a-318">**client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-319">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-319">Return Values</span></span>

- <span data-ttu-id="3458a-320">**estado** -------- Estado de conclusão real</span><span class="sxs-lookup"><span data-stu-id="3458a-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="3458a-321">**cliente NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) já começou</span><span class="sxs-lookup"><span data-stu-id="3458a-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="3458a-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Cliente não inicializado</span><span class="sxs-lookup"><span data-stu-id="3458a-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="3458a-323">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-324">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-325">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-325">Allowed From</span></span>

<span data-ttu-id="3458a-326">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-327">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="3458a-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="3458a-329">Executar o Cliente em modo unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-330">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="3458a-331">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-331">Description</span></span>

<span data-ttu-id="3458a-332">Este serviço inicia o Cliente no modo unicast onde envia periodicamente um pedido unicast para o seu SNTP Server para uma atualização de tempo.</span><span class="sxs-lookup"><span data-stu-id="3458a-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="3458a-333">Se for recebida uma mensagem SNTP válida, o tempo limite de tempo do cliente SNTP para o lapso máximo sem atualização, o intervalo inicial de votação e a contagem de mensagens inválidas consecutivas recebidas são reiniciados.</span><span class="sxs-lookup"><span data-stu-id="3458a-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="3458a-334">Se um destes limites for ultrapassado, o Cliente SNTP define o estado do Servidor para inválido, embora ainda faça sondagem e aguarde para receber atualizações.</span><span class="sxs-lookup"><span data-stu-id="3458a-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="3458a-335">A aplicação pode sondar a tarefa do Cliente SNTP para o estado do servidor, e se inválida parar o Cliente SNTP e reinitilizá-lo com outro endereço unicast SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="3458a-336">Também pode mudar para um servidor SNTP de transmissão.</span><span class="sxs-lookup"><span data-stu-id="3458a-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="3458a-337">.</span><span class="sxs-lookup"><span data-stu-id="3458a-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-338">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-338">Input Parameters</span></span>

- <span data-ttu-id="3458a-339">**client_ptr** Ponteiro para o bloco de controlo do cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-340">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-340">Return Values</span></span>

- <span data-ttu-id="3458a-341">**NX_SUCCESS** (0x00) iniciou com sucesso o Cliente em modo unicast</span><span class="sxs-lookup"><span data-stu-id="3458a-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="3458a-342">**cliente NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) já começou</span><span class="sxs-lookup"><span data-stu-id="3458a-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="3458a-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Cliente não inicializado</span><span class="sxs-lookup"><span data-stu-id="3458a-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="3458a-344">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="3458a-345">NX_CALLER_ERROR (0x11) Inválido de serviço</span><span class="sxs-lookup"><span data-stu-id="3458a-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="3458a-346">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-346">Allowed From</span></span>

<span data-ttu-id="3458a-347">Fios</span><span class="sxs-lookup"><span data-stu-id="3458a-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-348">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="3458a-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="3458a-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="3458a-350">Desente o cliente SNTP local</span><span class="sxs-lookup"><span data-stu-id="3458a-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-351">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="3458a-352">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-352">Description</span></span>

<span data-ttu-id="3458a-353">Este serviço define o cliente SNTP local com o tempo de entrada, em formato SNTP, por exemplo, segundos e "fração" que é o formato para colocar frações de segundo em formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="3458a-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="3458a-354">Destina-se a atualizar o cliente SNTP local a partir de um cronometreiro independente, por exemplo, um relógio em tempo real.</span><span class="sxs-lookup"><span data-stu-id="3458a-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="3458a-355">O protocolo SNTP destina-se a atualizações de tempo SNTP para evitar que o tempo do relógio local se "deslove".</span><span class="sxs-lookup"><span data-stu-id="3458a-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="3458a-356">As atualizações de tempo do servidor SNTP podem ser, mas não se destinam a ser a única entrada para o cliente SNTP local se não houver um time keeper independente no dispositivo de aplicação.</span><span class="sxs-lookup"><span data-stu-id="3458a-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="3458a-357">Esta API também pode ser usada para dar ao Cliente SNTP um tempo base antes de iniciar a linha do Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="3458a-358">A hora local do Cliente SNTP é comparada com as atualizações recebidas para dados de tempo válidos.</span><span class="sxs-lookup"><span data-stu-id="3458a-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="3458a-359">Pela primeira vez atualização recebida, pode haver uma discrepância muito grande.</span><span class="sxs-lookup"><span data-stu-id="3458a-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="3458a-360">Portanto, existe uma opção para o Cliente SNTP ignorar a discrepância na primeira atualização.</span><span class="sxs-lookup"><span data-stu-id="3458a-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="3458a-361">Desta forma, o Cliente SNTP pode começar sem uma hora de base.</span><span class="sxs-lookup"><span data-stu-id="3458a-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="3458a-362">O tempo de entrada pode ser obtido a partir de tempos conhecidos de época (normalmente disponíveis na Internet) e são calculados como o número de segundos desde 1 de janeiro de 1900 (até 2036 quando uma nova 'época' será iniciada.</span><span class="sxs-lookup"><span data-stu-id="3458a-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-363">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-363">Input Parameters</span></span>

- <span data-ttu-id="3458a-364">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-365">**segundos** Componente de segundos da entrada do tempo</span><span class="sxs-lookup"><span data-stu-id="3458a-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="3458a-366">**fração** Componente de subsegundos no formato de fração SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-367">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-367">Return Values</span></span>

- <span data-ttu-id="3458a-368">**NX_SUCCESS** (0x00) definir com sucesso a hora local</span><span class="sxs-lookup"><span data-stu-id="3458a-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="3458a-369">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-370">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-370">Allowed From</span></span>

<span data-ttu-id="3458a-371">Inicialização</span><span class="sxs-lookup"><span data-stu-id="3458a-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="3458a-372">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="3458a-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="3458a-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="3458a-374">Desaveize a chamada de atualização SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-375">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="3458a-376">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-376">Description</span></span>

<span data-ttu-id="3458a-377">Este serviço configura a chamada para notificar a aplicação quando o Cliente SNTP recebe uma atualização de tempo válida.</span><span class="sxs-lookup"><span data-stu-id="3458a-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="3458a-378">Fornece a mensagem SNTP real e a hora local do Cliente SNTP (geralmente a mesma) em formato NTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="3458a-379">A aplicação pode utilizar os dados NTP diretamente ou ligar para o *serviço nx_sntp_client_utility_display_date_time* para converter o tempo em formato legível humano.</span><span class="sxs-lookup"><span data-stu-id="3458a-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-380">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-380">Input Parameters</span></span>

- <span data-ttu-id="3458a-381">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="3458a-382">**time_update_cb** Função de retorno do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-383">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-383">Return Values</span></span>

- <span data-ttu-id="3458a-384">**NX_SUCCESS** (0x00) configurar com sucesso o retorno</span><span class="sxs-lookup"><span data-stu-id="3458a-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="3458a-385">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-386">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-386">Allowed From</span></span>

<span data-ttu-id="3458a-387">Inicialização</span><span class="sxs-lookup"><span data-stu-id="3458a-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="3458a-388">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="3458a-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="3458a-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="3458a-390">Pare o fio do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="3458a-392">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-392">Description</span></span>

<span data-ttu-id="3458a-393">Este serviço para a linha do Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="3458a-394">As tarefas de thread do Cliente SNTP, que funciona em loop infinito, fazem uma pausa em cada iteração para libertar o controlo do estado do Cliente SNTP e permitem que as aplicações façam chamadas API no Cliente SNTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-395">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-395">Input Parameters</span></span>

- <span data-ttu-id="3458a-396">**client_ptr** Ponteiro para bloco de controlo do cliente SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-397">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-397">Return Values</span></span>

- <span data-ttu-id="3458a-398">**NX_SUCCESS** (0x00) Com sucesso parou a linha do cliente</span><span class="sxs-lookup"><span data-stu-id="3458a-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="3458a-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) linha de cliente SNTP não começou</span><span class="sxs-lookup"><span data-stu-id="3458a-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="3458a-400">NX_PTR_ERROR (0x07) Entrada inválida do ponteiro</span><span class="sxs-lookup"><span data-stu-id="3458a-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-401">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-401">Allowed From</span></span>

<span data-ttu-id="3458a-402">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-403">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="3458a-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="3458a-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="3458a-405">Converter uma linha de tempo NTP para data e tempo</span><span class="sxs-lookup"><span data-stu-id="3458a-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-406">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="3458a-407">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-407">Description</span></span>

<span data-ttu-id="3458a-408">Este serviço converte o cliente SNTP local para um formato de data de um ano e devolve a data no tampão fornecido.</span><span class="sxs-lookup"><span data-stu-id="3458a-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="3458a-409">O NX_SNTP_CURRENT_YEAR não precisa de ser o mesmo ano que o tempo atual do Cliente, mas deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="3458a-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-410">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-410">Input Parameters</span></span>

- <span data-ttu-id="3458a-411">**Ponteiro client_ptr para cliente SNTP**</span><span class="sxs-lookup"><span data-stu-id="3458a-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="3458a-412">**tampão** Ponteiro para tampão para a data da loja</span><span class="sxs-lookup"><span data-stu-id="3458a-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="3458a-413">**comprimento** Tamanho do tampão de entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-414">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-414">Return Values</span></span>

- <span data-ttu-id="3458a-415">**NX_SUCCESS** (0x00) Conversão bem sucedida</span><span class="sxs-lookup"><span data-stu-id="3458a-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="3458a-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) não NX_SNTP_CURRENT_YEAR definido ou não estabelecido tempo de cliente local</span><span class="sxs-lookup"><span data-stu-id="3458a-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="3458a-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Comprimento do tampão insuficiente</span><span class="sxs-lookup"><span data-stu-id="3458a-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="3458a-418">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-418">Allowed From</span></span>

<span data-ttu-id="3458a-419">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-420">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="3458a-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="3458a-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="3458a-422">Converter milissegundos para um componente de fração NTP</span><span class="sxs-lookup"><span data-stu-id="3458a-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-423">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="3458a-424">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-424">Description</span></span>

<span data-ttu-id="3458a-425">Este serviço converte os milissegundos de entrada para o componente da fração NTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="3458a-426">Destina-se a ser utilizado com aplicações que tenham um tempo base inicial para o Cliente SNTP, mas não em formato NTP segundos/fração.</span><span class="sxs-lookup"><span data-stu-id="3458a-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="3458a-427">O número de milissegundos deve ser inferior a 1000 para fazer uma fração válida.</span><span class="sxs-lookup"><span data-stu-id="3458a-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-428">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-428">Input Parameters</span></span>

- <span data-ttu-id="3458a-429">**milissegundos Milissegundos para converter**</span><span class="sxs-lookup"><span data-stu-id="3458a-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="3458a-430">**fração** Ponteiro para milissegundos convertidos em fração</span><span class="sxs-lookup"><span data-stu-id="3458a-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-431">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-431">Return Values</span></span>

- <span data-ttu-id="3458a-432">**NX_SUCCESS** (0x00) Conversão bem sucedida</span><span class="sxs-lookup"><span data-stu-id="3458a-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="3458a-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Erro de conversão de tempo para uma data</span><span class="sxs-lookup"><span data-stu-id="3458a-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="3458a-434">NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-435">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-435">Allowed From</span></span>

<span data-ttu-id="3458a-436">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-437">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="3458a-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="3458a-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="3458a-439">Converter microsegundos num componente de fração NTP</span><span class="sxs-lookup"><span data-stu-id="3458a-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-440">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="3458a-441">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-441">Description</span></span>

<span data-ttu-id="3458a-442">Este serviço converte os microsegundos de entrada para o componente da fração NTP.</span><span class="sxs-lookup"><span data-stu-id="3458a-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="3458a-443">Destina-se a ser utilizado com aplicações que tenham um tempo base inicial para o Cliente SNTP, mas não em formato NTP segundos/fração.</span><span class="sxs-lookup"><span data-stu-id="3458a-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="3458a-444">O número de microsegundos deve ser inferior a 1000000 para fazer uma fração válida.</span><span class="sxs-lookup"><span data-stu-id="3458a-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-445">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-445">Input Parameters</span></span>

- <span data-ttu-id="3458a-446">**microsegundos** Microsegundos para converter</span><span class="sxs-lookup"><span data-stu-id="3458a-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="3458a-447">**fração** Ponteiro para microsegundos convertidos em fração</span><span class="sxs-lookup"><span data-stu-id="3458a-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-448">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-448">Return Values</span></span>

- <span data-ttu-id="3458a-449">**NX_SUCCESS** (0x00) Conversão bem sucedida</span><span class="sxs-lookup"><span data-stu-id="3458a-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="3458a-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Erro de conversão de tempo para uma data</span><span class="sxs-lookup"><span data-stu-id="3458a-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="3458a-451">NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-452">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-452">Allowed From</span></span>

<span data-ttu-id="3458a-453">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-454">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="3458a-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="3458a-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="3458a-456">Converter um componente de fração NTP em microsegundos</span><span class="sxs-lookup"><span data-stu-id="3458a-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="3458a-457">Prototype</span><span class="sxs-lookup"><span data-stu-id="3458a-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="3458a-458">Descrição</span><span class="sxs-lookup"><span data-stu-id="3458a-458">Description</span></span>

<span data-ttu-id="3458a-459">Este serviço converte o componente de fração NTP de entrada em microsegundos.</span><span class="sxs-lookup"><span data-stu-id="3458a-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="3458a-460">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="3458a-460">Input Parameters</span></span>

- <span data-ttu-id="3458a-461">**fração para converter**</span><span class="sxs-lookup"><span data-stu-id="3458a-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="3458a-462">**microsegundos** Ponteiro para fração convertido em microsegundos</span><span class="sxs-lookup"><span data-stu-id="3458a-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="3458a-463">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="3458a-463">Return Values</span></span>

- <span data-ttu-id="3458a-464">**NX_SUCCESS** (0x00) Conversão bem sucedida</span><span class="sxs-lookup"><span data-stu-id="3458a-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="3458a-465">NX_SNTP_INVALID_TIME (0xD30) Entrada de dados inválidas da SNTP</span><span class="sxs-lookup"><span data-stu-id="3458a-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3458a-466">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="3458a-466">Allowed From</span></span>

<span data-ttu-id="3458a-467">Inicialização, Threads</span><span class="sxs-lookup"><span data-stu-id="3458a-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3458a-468">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3458a-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```