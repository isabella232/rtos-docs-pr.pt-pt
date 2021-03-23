---
title: Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo PTP
description: Este capítulo contém uma descrição de todos os serviços de clientes NetX Duo PTP por ordem alfabética.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2021
ms.locfileid: "104825802"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a><span data-ttu-id="74ff5-103">Capítulo 3 - Descrição dos Serviços de Clientes Azure RTOS NetX Duo PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-103">Chapter 3 - Description of Azure RTOS NetX Duo PTP Client Services</span></span>

<span data-ttu-id="74ff5-104">Este capítulo contém uma descrição de todos os serviços de clientes NetX Duo PTP (listados abaixo) por ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="74ff5-104">This chapter contains a description of all NetX Duo PTP client services (listed below) in alphabetical order.</span></span>

[!NOTE]
> <span data-ttu-id="74ff5-105">*Na secção **Valores de Retorno** nas seguintes descrições da função API, os valores em **BOLD** não são afetados pelo **NX_DISABLE_ERROR_CHECKING** definem que é utilizado para desativar a verificação de erros de API, enquanto os valores não arrojados são completamente desactivos.*</span><span class="sxs-lookup"><span data-stu-id="74ff5-105">*In the **Return Values** section in the following API function descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.*</span></span>

## <a name="nx_ptp_client_create"></a><span data-ttu-id="74ff5-106">nx_ptp_client_create</span><span class="sxs-lookup"><span data-stu-id="74ff5-106">nx_ptp_client_create</span></span>

<span data-ttu-id="74ff5-107">Criar uma instância de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-107">Create a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-108">Prototype</span></span>

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a><span data-ttu-id="74ff5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-109">Description</span></span>

<span data-ttu-id="74ff5-110">Este serviço cria uma instância do cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-110">This service creates an instance of the PTP client.</span></span>

<span data-ttu-id="74ff5-111">Note que a aplicação deve primeiro criar uma instância IP e um pacote de piscina para o cliente PTP transmitir pacotes.</span><span class="sxs-lookup"><span data-stu-id="74ff5-111">Note that the  application must first create an IP instance and a packet pool for the PTP client to transmit packets.</span></span> <span data-ttu-id="74ff5-112">Para o conjunto de pacotes, a aplicação pode utilizar o mesmo pacote de piscina na instância IP; ou pode criar uma piscina de pacotes dedicada para cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-112">For the packet pool, application may use the same packet pool in the IP instance; or it can create a dedicated packet pool for PTP client.</span></span>  <span data-ttu-id="74ff5-113">A abordagem dedicada à piscina de pacotes tem a vantagem de usar pequenos pacotes (128 bytes pacotes se o IPv6 for usado, ou 108 bytes apenas para IPv4).</span><span class="sxs-lookup"><span data-stu-id="74ff5-113">The dedicated packet pool approach has the advantage of using small packets (128 bytes packets if IPv6 is used, or 108 bytes for IPv4-only).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-114">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-114">Input Parameters</span></span>
* <span data-ttu-id="74ff5-115">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-115">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-116">**ip_ptr** Indicação para a instância IP</span><span class="sxs-lookup"><span data-stu-id="74ff5-116">**ip_ptr** Pointer to IP instance</span></span>
* <span data-ttu-id="74ff5-117">**interface_index** Índice de interface de rede PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-117">**interface_index** Index of PTP network interface</span></span>
* <span data-ttu-id="74ff5-118">**packet_pool_ptr** Ponteiro para piscina de pacotes de clientes</span><span class="sxs-lookup"><span data-stu-id="74ff5-118">**packet_pool_ptr** Pointer to client packet pool</span></span>
* <span data-ttu-id="74ff5-119">**thread_priority**  Prioridade do fio PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-119">**thread_priority**  Priority of PTP thread</span></span>
* <span data-ttu-id="74ff5-120">**thread_stack** Ponteiro para pilha de rosca</span><span class="sxs-lookup"><span data-stu-id="74ff5-120">**thread_stack** Pointer to thread stack</span></span>
* <span data-ttu-id="74ff5-121">**stack_size** Tamanho da pilha de fio</span><span class="sxs-lookup"><span data-stu-id="74ff5-121">**stack_size** Size of thread stack</span></span>
* <span data-ttu-id="74ff5-122">**clock_callback** Chamada do relógio PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-122">**clock_callback** PTP clock callback</span></span>
* <span data-ttu-id="74ff5-123">**clock_callback_data** Dados para a chamada do relógio</span><span class="sxs-lookup"><span data-stu-id="74ff5-123">**clock_callback_data** Data for the clock callback</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-124">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-124">Return Values</span></span>
* <span data-ttu-id="74ff5-125">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="74ff5-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Carga de pacote muito pequena</span><span class="sxs-lookup"><span data-stu-id="74ff5-126">**NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Packet payload too small</span></span>
* <span data-ttu-id="74ff5-127">**falha NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) na chamada do relógio</span><span class="sxs-lookup"><span data-stu-id="74ff5-127">**NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) Failure on clock callback</span></span>
* <span data-ttu-id="74ff5-128">**estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX</span><span class="sxs-lookup"><span data-stu-id="74ff5-128">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="74ff5-129">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-129">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
* <span data-ttu-id="74ff5-130">interface NX_INVALID_INTERFACE (0x4C) Inválida</span><span class="sxs-lookup"><span data-stu-id="74ff5-130">NX_INVALID_INTERFACE (0x4C) Invalid interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-131">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-131">Allowed From</span></span>
<span data-ttu-id="74ff5-132">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-133">Example</span></span>
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a><span data-ttu-id="74ff5-134">nx_ptp_client_delete</span><span class="sxs-lookup"><span data-stu-id="74ff5-134">nx_ptp_client_delete</span></span>

<span data-ttu-id="74ff5-135">Elimina uma instância de cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-135">Deletes a PTP client instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-136">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-136">Prototype</span></span>

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-137">Description</span></span>

<span data-ttu-id="74ff5-138">Este serviço elimina uma instância do cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-138">This service deletes an instance of the PTP client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-139">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-139">Input Parameters</span></span>
* <span data-ttu-id="74ff5-140">**client_ptr** Ponteiro para cliente PTP para apagar</span><span class="sxs-lookup"><span data-stu-id="74ff5-140">**client_ptr** Pointer to PTP client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-141">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-141">Return Values</span></span>
* <span data-ttu-id="74ff5-142">**NX_SUCCESS** (0x00) Cliente eliminado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-142">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
* <span data-ttu-id="74ff5-143">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-143">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-144">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-144">Allowed From</span></span>
<span data-ttu-id="74ff5-145">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-145">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-146">Example</span></span>
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a><span data-ttu-id="74ff5-147">nx_ptp_client_master_info_get</span><span class="sxs-lookup"><span data-stu-id="74ff5-147">nx_ptp_client_master_info_get</span></span>

<span data-ttu-id="74ff5-148">Obtenha informações do relógio principal.</span><span class="sxs-lookup"><span data-stu-id="74ff5-148">Get master clock information.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-149">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-149">Prototype</span></span>

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a><span data-ttu-id="74ff5-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-150">Description</span></span>
<span data-ttu-id="74ff5-151">Este serviço obtém informações do relógio principal.</span><span class="sxs-lookup"><span data-stu-id="74ff5-151">This service gets information of master clock.</span></span> <span data-ttu-id="74ff5-152">O bloco de controlo principal é passado para a aplicação do utilizador através da função de retorno do evento.</span><span class="sxs-lookup"><span data-stu-id="74ff5-152">The master control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-153">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-153">Input Parameters</span></span>
* <span data-ttu-id="74ff5-154">**master_ptr** Ponteiro para o relógio master PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-154">**master_ptr** Pointer to PTP master clock</span></span>
* <span data-ttu-id="74ff5-155">**endereço** Endereço do relógio principal</span><span class="sxs-lookup"><span data-stu-id="74ff5-155">**address** Address of master clock</span></span>
* <span data-ttu-id="74ff5-156">**port_identity** PtP master porto e identidade</span><span class="sxs-lookup"><span data-stu-id="74ff5-156">**port_identity** PTP master port and identity</span></span>
* <span data-ttu-id="74ff5-157">**port_identity_length** Comprimento da porta-mestre ptp e identidade</span><span class="sxs-lookup"><span data-stu-id="74ff5-157">**port_identity_length** Length of PTP master port and identity</span></span>
* <span data-ttu-id="74ff5-158">**prioridade1** Prioridade1 do relógio master PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-158">**priority1** Priority1 of PTP master clock</span></span>
* <span data-ttu-id="74ff5-159">**prioridade2** Prioridade2 do relógio master PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-159">**priority2** Priority2 of PTP master clock</span></span>
* <span data-ttu-id="74ff5-160">**clock_class** Classe de relógio master PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-160">**clock_class** Class of PTP master clock</span></span>
* <span data-ttu-id="74ff5-161">**clock_accuracy** Precisão do relógio master PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-161">**clock_accuracy** Accuracy of PTP master clock</span></span>
* <span data-ttu-id="74ff5-162">**clock_variance** Variação do relógio mestre PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-162">**clock_variance** Variance of PTP master clock</span></span>
* <span data-ttu-id="74ff5-163">**grandmaster_identity** Identidade do relógio grandmaster</span><span class="sxs-lookup"><span data-stu-id="74ff5-163">**grandmaster_identity** Identity of grandmaster clock</span></span>
* <span data-ttu-id="74ff5-164">**grandmaster_identity_length** Comprimento da identidade do grão-mestre</span><span class="sxs-lookup"><span data-stu-id="74ff5-164">**grandmaster_identity_length** Length of grandmaster Identity</span></span>
* <span data-ttu-id="74ff5-165">**steps_removed** Passos removidos do cabeçalho PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-165">**steps_removed** Steps removed from PTP header</span></span>
* <span data-ttu-id="74ff5-166">**time_source** A fonte do temporizador usado pelo relógio grandmaster</span><span class="sxs-lookup"><span data-stu-id="74ff5-166">**time_source** The source of timer used by grandmaster clock</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-167">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-167">Return Values</span></span>
* <span data-ttu-id="74ff5-168">**NX_SUCCESS** (0x00) Obtenha informações do relógio principal com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-168">**NX_SUCCESS** (0x00) Get master clock information successfully</span></span>
* <span data-ttu-id="74ff5-169">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-169">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-170">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-170">Allowed From</span></span>
<span data-ttu-id="74ff5-171">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-172">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a><span data-ttu-id="74ff5-173">nx_ptp_client_packet_timestamp_notify</span><span class="sxs-lookup"><span data-stu-id="74ff5-173">nx_ptp_client_packet_timestamp_notify</span></span>

<span data-ttu-id="74ff5-174">Notifique o cliente PTP da hora do pacote.</span><span class="sxs-lookup"><span data-stu-id="74ff5-174">Notify PTP client the timestamp of the packet.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-175">Prototype</span></span>

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-176">Description</span></span>
<span data-ttu-id="74ff5-177">Este serviço notifica o cliente PTP de que o pacote é transmitido com a hora de jogo.</span><span class="sxs-lookup"><span data-stu-id="74ff5-177">This service notifies the PTP client that packet is transmitted with timestamp.</span></span> <span data-ttu-id="74ff5-178">Este serviço foi concebido para o controlador de rede e invocado quando o pacote é transmitido.</span><span class="sxs-lookup"><span data-stu-id="74ff5-178">This service is designed for network driver and invoked when the packet is transmitted.</span></span> <span data-ttu-id="74ff5-179">A estamp de tempo é geralmente gerada por hardware.</span><span class="sxs-lookup"><span data-stu-id="74ff5-179">The timestamp is usually generated by hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-180">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-180">Input Parameters</span></span>
* <span data-ttu-id="74ff5-181">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-181">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-182">**packet_ptr** Ponteiro para pacote PTP que é transmitido</span><span class="sxs-lookup"><span data-stu-id="74ff5-182">**packet_ptr** Pointer to PTP packet that is transmitted</span></span>
* <span data-ttu-id="74ff5-183">**timestamp_ptr** Ponteiro para o tempotamp do pacote PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-183">**timestamp_ptr** Pointer to timestamp of PTP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-184">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-184">Return Values</span></span>
<span data-ttu-id="74ff5-185">Nenhum</span><span class="sxs-lookup"><span data-stu-id="74ff5-185">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-186">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-186">Allowed From</span></span>
<span data-ttu-id="74ff5-187">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-187">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-188">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-188">Example</span></span>
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a><span data-ttu-id="74ff5-189">nx_ptp_client_soft_clock_callback</span><span class="sxs-lookup"><span data-stu-id="74ff5-189">nx_ptp_client_soft_clock_callback</span></span>

<span data-ttu-id="74ff5-190">Implementação de software de um relógio PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-190">Software implementation of a PTP clock.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-191">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-191">Prototype</span></span>

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a><span data-ttu-id="74ff5-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-192">Description</span></span>
<span data-ttu-id="74ff5-193">Esta função de retorno serve como uma fonte de relógio de baixa resolução simulada para PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-193">This callback function serves as a simulated low resolution clock source for PTP.</span></span> <span data-ttu-id="74ff5-194">Esta rotina é fornecida como referência e não pode ser utilizada para a produção.</span><span class="sxs-lookup"><span data-stu-id="74ff5-194">This routine is provided as a reference and cannot be used for production.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-195">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-195">Input Parameters</span></span>
* <span data-ttu-id="74ff5-196">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-196">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-197">**operação** Operação de retorno, valores válidos são definidos como:</span><span class="sxs-lookup"><span data-stu-id="74ff5-197">**operation** Callback operation, valid values are defined as:</span></span>
  * <span data-ttu-id="74ff5-198">**NX_PTP_CLIENT_CLOCK_INIT** Inicialize o relógio.</span><span class="sxs-lookup"><span data-stu-id="74ff5-198">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="74ff5-199">**NX_PTP_CLIENT_CLOCK_SET** Definir a temperatura de corrente especificada por `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="74ff5-199">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="74ff5-200">**NX_PTP_CLIENT_CLOCK_GET** Devolva a hora atual para `time_ptr` .</span><span class="sxs-lookup"><span data-stu-id="74ff5-200">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="74ff5-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extraição de hora de `packet_ptr` . `time_ptr`</span><span class="sxs-lookup"><span data-stu-id="74ff5-201">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="74ff5-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Ajuste a corrente da hora de seqdós menos de *1* segundo.</span><span class="sxs-lookup"><span data-stu-id="74ff5-202">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="74ff5-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Marque o `packet_ptr` que requer notificar o cliente PTP da marca de tempo quando é transmitido.</span><span class="sxs-lookup"><span data-stu-id="74ff5-203">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="74ff5-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Atualize o temporizador suave.</span><span class="sxs-lookup"><span data-stu-id="74ff5-204">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="74ff5-205">Pode ser ignorado pelo relógio de hardware.</span><span class="sxs-lookup"><span data-stu-id="74ff5-205">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="74ff5-206">**time_ptr** Ponteiro para a marca de tempo.</span><span class="sxs-lookup"><span data-stu-id="74ff5-206">**time_ptr** Pointer to timestamp.</span></span>
* <span data-ttu-id="74ff5-207">**packet_ptr** Ponteiro para pacote.</span><span class="sxs-lookup"><span data-stu-id="74ff5-207">**packet_ptr** Pointer to packet.</span></span>
* <span data-ttu-id="74ff5-208">**callback_data** Ponteiro para dados de retorno opaco.</span><span class="sxs-lookup"><span data-stu-id="74ff5-208">**callback_data** Pointer to opaque callback data.</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-209">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-209">Return Values</span></span>
* <span data-ttu-id="74ff5-210">**NX_SUCCESS** (0x00) Operação com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-210">**NX_SUCCESS** (0x00) Operation successfully</span></span>
* <span data-ttu-id="74ff5-211">**NX_PTP_PARAM_ERROR** (0xD03) Parâmetro inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-211">**NX_PTP_PARAM_ERROR** (0xD03) Invalid parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-212">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-212">Allowed From</span></span>
<span data-ttu-id="74ff5-213">PTP interno</span><span class="sxs-lookup"><span data-stu-id="74ff5-213">PTP internal</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-214">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-214">Example</span></span>
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a><span data-ttu-id="74ff5-215">nx_ptp_client_start</span><span class="sxs-lookup"><span data-stu-id="74ff5-215">nx_ptp_client_start</span></span>

<span data-ttu-id="74ff5-216">Iniciar cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-216">Start PTP client.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-217">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-217">Prototype</span></span>

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a><span data-ttu-id="74ff5-218">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-218">Description</span></span>
<span data-ttu-id="74ff5-219">Este serviço inicia uma instância de cliente PTP previamente criada.</span><span class="sxs-lookup"><span data-stu-id="74ff5-219">This service starts a previously created PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-220">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-220">Input Parameters</span></span>
* <span data-ttu-id="74ff5-221">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-221">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-222">**client_port_identity_ptr** Ponteiro para a porta e identidade do cliente, pode ser NULO</span><span class="sxs-lookup"><span data-stu-id="74ff5-222">**client_port_identity_ptr** Pointer to client port and identity, it can be NULL</span></span>
* <span data-ttu-id="74ff5-223">**client_port_identity_length** Comprimento da porta e identidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="74ff5-223">**client_port_identity_length** Length of client port and identity.</span></span> <span data-ttu-id="74ff5-224">Deve ser 0 se client_port_identity_ptr for NULO ou NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span><span class="sxs-lookup"><span data-stu-id="74ff5-224">It must be 0 if client_port_identity_ptr is NULL or NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)</span></span>
* <span data-ttu-id="74ff5-225">**domínio** Domínio do relógio PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-225">**domain** PTP clock domain</span></span>
* <span data-ttu-id="74ff5-226">**transport_specific** 4 bits de transporte específicos</span><span class="sxs-lookup"><span data-stu-id="74ff5-226">**transport_specific** 4 bits of transport specific</span></span>
* <span data-ttu-id="74ff5-227">**event_callback** Função de retorno invocada no evento</span><span class="sxs-lookup"><span data-stu-id="74ff5-227">**event_callback** Callback function invoked on event</span></span>
* <span data-ttu-id="74ff5-228">**event_callback_data** Dados para a chamada do evento</span><span class="sxs-lookup"><span data-stu-id="74ff5-228">**event_callback_data** Data for the event callback</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-229">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-229">Return Values</span></span>
* <span data-ttu-id="74ff5-230">**NX_SUCCESS** (0x00) Cliente começou com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-230">**NX_SUCCESS** (0x00) Client successfully started</span></span>
* <span data-ttu-id="74ff5-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) cliente PTP já começou</span><span class="sxs-lookup"><span data-stu-id="74ff5-231">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="74ff5-232">**estado** Conclusão do estado das chamadas de serviço NetX Duo e ThreadX</span><span class="sxs-lookup"><span data-stu-id="74ff5-232">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
* <span data-ttu-id="74ff5-233">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-233">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-234">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-234">Allowed From</span></span>
<span data-ttu-id="74ff5-235">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-235">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-236">Example</span></span>
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a><span data-ttu-id="74ff5-237">nx_ptp_client_stop</span><span class="sxs-lookup"><span data-stu-id="74ff5-237">nx_ptp_client_stop</span></span>

<span data-ttu-id="74ff5-238">Pare o cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-238">Stop PTP client.</span></span>  <span data-ttu-id="74ff5-239">Depois de o cliente PTP ser parado, não processa pacotes de PTP, nem transmite pacotes ptp.</span><span class="sxs-lookup"><span data-stu-id="74ff5-239">After the PTP client is stopped, it does not process PTP packets, nor does it transmit PTP packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-240">Prototype</span></span>

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-241">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-241">Description</span></span>
<span data-ttu-id="74ff5-242">Este serviço para uma instância de cliente ptp previamente criada e iniciada.</span><span class="sxs-lookup"><span data-stu-id="74ff5-242">This service stops a previously created and started PTP client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-243">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-243">Input Parameters</span></span>
* <span data-ttu-id="74ff5-244">**client_ptr** Ponteiro para cliente PTP para parar</span><span class="sxs-lookup"><span data-stu-id="74ff5-244">**client_ptr** Pointer to PTP client to stop</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-245">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-245">Return Values</span></span>
* <span data-ttu-id="74ff5-246">**NX_SUCCESS** (0x00) Cliente parou com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-246">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>
* <span data-ttu-id="74ff5-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Cliente não começou</span><span class="sxs-lookup"><span data-stu-id="74ff5-247">**NX_PTP_CLIENT_NOT_STARTED** (0xD01) Client not started</span></span>
* <span data-ttu-id="74ff5-248">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-248">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-249">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-249">Allowed From</span></span>
<span data-ttu-id="74ff5-250">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-250">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-251">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-251">Example</span></span>
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a><span data-ttu-id="74ff5-252">nx_ptp_client_sync_info_get</span><span class="sxs-lookup"><span data-stu-id="74ff5-252">nx_ptp_client_sync_info_get</span></span>

<span data-ttu-id="74ff5-253">Obtenha informações de Sync.</span><span class="sxs-lookup"><span data-stu-id="74ff5-253">Get Sync information.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-254">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-254">Prototype</span></span>

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a><span data-ttu-id="74ff5-255">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-255">Description</span></span>
<span data-ttu-id="74ff5-256">Este serviço obtém informações da mensagem Sync.</span><span class="sxs-lookup"><span data-stu-id="74ff5-256">This service gets information of Sync message.</span></span> <span data-ttu-id="74ff5-257">O bloco de controlo Sync é passado para a aplicação do utilizador através da função de retorno do evento.</span><span class="sxs-lookup"><span data-stu-id="74ff5-257">The Sync control block is passed to user application through event callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-258">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-258">Input Parameters</span></span>
* <span data-ttu-id="74ff5-259">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-259">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-260">**bandeiras** Bandeiras na mensagem sync</span><span class="sxs-lookup"><span data-stu-id="74ff5-260">**flags** Flags in Sync message</span></span>
* <span data-ttu-id="74ff5-261">**utc_offset** Compensação entre TAI e UTC</span><span class="sxs-lookup"><span data-stu-id="74ff5-261">**utc_offset** Offset between TAI and UTC</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-262">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-262">Return Values</span></span>
* <span data-ttu-id="74ff5-263">**NX_SUCCESS** (0x00) Obtenha informações de Sincronização com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-263">**NX_SUCCESS** (0x00) Get Sync information successfully</span></span>
* <span data-ttu-id="74ff5-264">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-264">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-265">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-265">Allowed From</span></span>
<span data-ttu-id="74ff5-266">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-267">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-267">Example</span></span>
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a><span data-ttu-id="74ff5-268">nx_ptp_client_time_get</span><span class="sxs-lookup"><span data-stu-id="74ff5-268">nx_ptp_client_time_get</span></span>

<span data-ttu-id="74ff5-269">Obtenha a hora atual.</span><span class="sxs-lookup"><span data-stu-id="74ff5-269">Get current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-270">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-270">Prototype</span></span>

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-271">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-271">Description</span></span>
<span data-ttu-id="74ff5-272">Este serviço obtém o valor atual do relógio PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-272">This service gets the current value of the PTP clock.</span></span> <span data-ttu-id="74ff5-273">Está disponível independentemente do cliente PTP estar sincronizado com o relógio principal ou não.</span><span class="sxs-lookup"><span data-stu-id="74ff5-273">It is available no matter PTP client is synchronized with master clock or not.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-274">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-274">Input Parameters</span></span>
* <span data-ttu-id="74ff5-275">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-275">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-276">**time_ptr** Ponteiro para o tempo ptp</span><span class="sxs-lookup"><span data-stu-id="74ff5-276">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-277">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-277">Return Values</span></span>
* <span data-ttu-id="74ff5-278">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-278">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="74ff5-279">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-279">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-280">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-280">Allowed From</span></span>
<span data-ttu-id="74ff5-281">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-282">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-282">Example</span></span>
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a><span data-ttu-id="74ff5-283">nx_ptp_client_time_set</span><span class="sxs-lookup"><span data-stu-id="74ff5-283">nx_ptp_client_time_set</span></span>

<span data-ttu-id="74ff5-284">Desa um pouco de tempo.</span><span class="sxs-lookup"><span data-stu-id="74ff5-284">Set current time.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-285">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-285">Prototype</span></span>

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-286">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-286">Description</span></span>
<span data-ttu-id="74ff5-287">Este serviço define o valor atual do relógio PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-287">This service sets the current value of the PTP clock.</span></span> <span data-ttu-id="74ff5-288">Deve ser invocado antes do início do cliente PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-288">It must be invoked before PTP client starts.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-289">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-289">Input Parameters</span></span>
* <span data-ttu-id="74ff5-290">**client_ptr** Ponteiro para cliente PTP para criar</span><span class="sxs-lookup"><span data-stu-id="74ff5-290">**client_ptr** Pointer to PTP client to create</span></span>
* <span data-ttu-id="74ff5-291">**time_ptr** Ponteiro para o tempo ptp</span><span class="sxs-lookup"><span data-stu-id="74ff5-291">**time_ptr** Pointer to PTP time</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-292">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-292">Return Values</span></span>
* <span data-ttu-id="74ff5-293">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-293">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="74ff5-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) cliente PTP já começou</span><span class="sxs-lookup"><span data-stu-id="74ff5-294">**NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started</span></span>
* <span data-ttu-id="74ff5-295">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-295">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-296">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-296">Allowed From</span></span>
<span data-ttu-id="74ff5-297">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-297">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-298">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-298">Example</span></span>
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a><span data-ttu-id="74ff5-299">nx_ptp_client_utility_convert_time_to_date</span><span class="sxs-lookup"><span data-stu-id="74ff5-299">nx_ptp_client_utility_convert_time_to_date</span></span>

<span data-ttu-id="74ff5-300">Converter a hora do PTP para uma data e hora UTC.</span><span class="sxs-lookup"><span data-stu-id="74ff5-300">Convert PTP time to a UTC date and time.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-301">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-301">Prototype</span></span>

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-302">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-302">Description</span></span>
<span data-ttu-id="74ff5-303">Este serviço converte a hora ptp para uma data e hora UTC.</span><span class="sxs-lookup"><span data-stu-id="74ff5-303">This service converts PTP time to a UTC date and time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-304">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-304">Input Parameters</span></span>
* <span data-ttu-id="74ff5-305">**time_ptr** Ponteiro para o tempo ptp</span><span class="sxs-lookup"><span data-stu-id="74ff5-305">**time_ptr** Pointer to PTP time</span></span>
* <span data-ttu-id="74ff5-306">**compensar** Segundo offset assinado para adicionar o tempo ptp</span><span class="sxs-lookup"><span data-stu-id="74ff5-306">**offset** Signed second offset to add the PTP time</span></span>
* <span data-ttu-id="74ff5-307">**date_time_ptr** Ponteiro até à data resultante</span><span class="sxs-lookup"><span data-stu-id="74ff5-307">**date_time_ptr** Pointer to resulting date</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-308">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-308">Return Values</span></span>
* <span data-ttu-id="74ff5-309">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-309">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="74ff5-310">**Ponteiro até à data resultante** (0xD03) Parâmetro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-310">**Pointer to resulting date** (0xD03) Invalid input parameter</span></span>
* <span data-ttu-id="74ff5-311">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-311">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-312">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-312">Allowed From</span></span>
<span data-ttu-id="74ff5-313">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-313">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-314">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-314">Example</span></span>
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a><span data-ttu-id="74ff5-315">nx_ptp_client_utility_time_diff</span><span class="sxs-lookup"><span data-stu-id="74ff5-315">nx_ptp_client_utility_time_diff</span></span>

<span data-ttu-id="74ff5-316">Diff duas vezes PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-316">Diff two PTP times.</span></span>

### <a name="prototype"></a><span data-ttu-id="74ff5-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="74ff5-317">Prototype</span></span>

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a><span data-ttu-id="74ff5-318">Descrição</span><span class="sxs-lookup"><span data-stu-id="74ff5-318">Description</span></span>
<span data-ttu-id="74ff5-319">Este serviço calcula a diferença entre duas vezes PTP.</span><span class="sxs-lookup"><span data-stu-id="74ff5-319">This service computes the difference between two PTP times.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="74ff5-320">Parâmetros de Entrada</span><span class="sxs-lookup"><span data-stu-id="74ff5-320">Input Parameters</span></span>
* <span data-ttu-id="74ff5-321">**time1_ptr** Ponteiro para a primeira vez PTP</span><span class="sxs-lookup"><span data-stu-id="74ff5-321">**time1_ptr** Pointer to first PTP time</span></span>
* <span data-ttu-id="74ff5-322">**time2_ptr** Ponteiro para o segundo tempo ptp</span><span class="sxs-lookup"><span data-stu-id="74ff5-322">**time2_ptr** Pointer to second PTP time</span></span>
* <span data-ttu-id="74ff5-323">**result_ptr** Ponteiro para o resultado time1-time2</span><span class="sxs-lookup"><span data-stu-id="74ff5-323">**result_ptr** Pointer to result time1-time2</span></span>

### <a name="return-values"></a><span data-ttu-id="74ff5-324">Valores de devolução</span><span class="sxs-lookup"><span data-stu-id="74ff5-324">Return Values</span></span>
* <span data-ttu-id="74ff5-325">**NX_SUCCESS** (0x00) Cliente criado com sucesso</span><span class="sxs-lookup"><span data-stu-id="74ff5-325">**NX_SUCCESS** (0x00) Client successfully created</span></span>
* <span data-ttu-id="74ff5-326">NX_PTR_ERROR (0x07) Parâmetro de ponteiro de entrada inválido</span><span class="sxs-lookup"><span data-stu-id="74ff5-326">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="74ff5-327">Permitido a partir de</span><span class="sxs-lookup"><span data-stu-id="74ff5-327">Allowed From</span></span>
<span data-ttu-id="74ff5-328">Fios</span><span class="sxs-lookup"><span data-stu-id="74ff5-328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="74ff5-329">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74ff5-329">Example</span></span>
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```